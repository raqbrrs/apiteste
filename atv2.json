// =================================================================
// 1. GET LISTAR EQUIPAMENTOS (CAMINHO FELIZ)
// =================================================================

// Verifica se o Status HTTP é 200 (Sucesso)
pm.test("Status code é 200 OK", function () {
    pm.response.to.have.status(200);
});

// Verifica se a resposta é rápida (performance)
pm.test("Tempo de resposta menor que 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

// Verifica o formato e integridade dos dados retornados
pm.test("A resposta deve ser uma lista (Array) preenchida", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.be.an("array");
    pm.expect(jsonData.length).to.be.greaterThan(0);
});


// =================================================================
// 2. POST CADASTRAR EQUIPAMENTO (DESAFIO DO ALUNO)
// =================================================================

// Validação do Status Code para cadastro com sucesso
pm.test("Equipamento cadastrado com sucesso (Status 201)", function () {
    pm.response.to.have.status(201);
});

// Validação da estrutura do payload retornado
pm.test("Deve retornar os dados do equipamento criado com um ID válido", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
    pm.expect(jsonData.nome).to.equal("Cabo de Rede 5m");
    pm.expect(jsonData.patrimonio).to.equal("EEEP-CAB-102");
});


// =================================================================
// 3. POST EMPRESTAR EQUIPAMENTO (CAMINHO TRISTE)
// =================================================================

// Verifica se a API barrou o dado inválido (Nome menor que 3 caracteres)
pm.test("Status code deve ser 400 Bad Request", function () {
    pm.response.to.have.status(400);
});

// Verifica se a mensagem de erro da Regra de Negócio está correta
pm.test("Validar mensagem de erro descritiva", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.erro).to.equal("Nome do responsável inválido (mínimo 3 caracteres).");
});