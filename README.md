# Projeto GraphQL

Este projeto proporcionou a aprendizagem de diversos conceitos fundamentais, destacando-se:

## GraphQL

GraphQL é uma ferramenta poderosa para realizar chamadas RPC, permitindo consultas flexíveis que trazem apenas os dados necessários. Isso resulta em economia de recursos e maior objetividade nas chamadas.

- **Type:**
  - Representa o modelo de dados. Aqui, descrevemos os atributos que o modelo deve ter.

- **Input:**
  - Refere-se à entrada de dados para o type. É utilizado para especificar o que será inserido no type.

- **Query:**
  - Operação de busca de dados. Definimos o que queremos trazer e de onde queremos trazer.

- **Mutation:**
  - Operação de alteração de dados. Descrevemos o que queremos modificar.

- **Resolver:**
  - Funciona como um orquestrador. Aqui, definimos as funções, especificando o que elas são e o que elas farão.

## Exemplo de query: 

```
query [queryCategories (nome de função, não é atrelado ao código diretamente)] {
  [categories (nome atrelado ao programa, foi definido no código e exposto para execução)] {
    id (tudo aqui é opcional, você decide o que precisa e manda trazer se a query tiver essa info, claro)
    name
    description
  }
}
```

## Exemplo de mutation:

```
mutation [createCourse  (nome de função, não é atrelado ao código diretamente)] {
  [createCourse (nome atrelado ao programa, foi definido no código e exposto para execução)]([input: {
      name: "TRICAMPEÃO DA LIBERTADORES NO RS",
      description: "SÓ TEM UM, IMORTAL",
      categoryId: 1
    } (Os parametros aqui vão depender da implementação, se são obrigatórios, quantos são, etc.)]) {
    id (tudo aqui é opcional, você decide o que precisa e manda trazer se a query tiver essa info, claro)
    name
    description
  }
```

## Dados encadeados:
  - Dentro das queries, caso haja uma relação definida podemos buscar sem precisar fazer uma nova função, exemplo nessa query eu estou buscando os dados de categoria dentro de uma query de curso sem ter necessáriamente mexido na função de busca de cursos, isso ocorre porque fizemos uma função de relacionamento pode ser invocada contanto que haja relação entre as tabelas, no caso, o course sempre tera um category_id que é o elo entre as entidades

```
query queryCoursesWithCategories{
  courses {
    id
    name
    description
    category{
      id
      name
    }
  }
}
```
