Como solicitado, elaborei um documento estruturado resumindo os principais pontos, desafios e obstáculos enfrentados pela turma na Avaliação de Projeto TP2 (Técnicas de Programação II).

---

# Resumo Analítico: Avaliação TP2 – Técnicas de Programação II

## 1. Visão Geral da Avaliação

A Avaliação TP2 focou na implementação de uma API RESTful utilizando Node.js e MongoDB, com o desafio adicional de aplicar rigorosamente os conceitos de **Clean Architecture, princípios SOLID, TDD (Test-Driven Development) e semântica JavaScript**. Os alunos foram desafiados a transcender a simples funcionalidade (CRUD) e elevar a qualidade arquitetural do código.

## 2. Dificuldades e Desafios Observados

A análise dos repositórios revelou que, embora a maioria tenha compreendido a lógica funcional (tarefas de agendamento e adoção), a transição para padrões de engenharia de software de alto nível apresentou obstáculos significativos:

* **Dificuldade em Desacoplar Lógica (MVC vs. Clean Architecture):** O desafio de isolar as regras de negócio em *Use Cases* e o acesso a dados em *Repositories* foi o ponto de maior atrito. A maioria dos alunos manteve o padrão MVC tradicional, resultando em controladores sobrecarregados (violação do SRP - Single Responsibility Principle).
* **Gestão de Assincronia e Estabilidade:** A implementação de operações assíncronas gerou riscos técnicos. Muitos projetos sofreram com *crashes* por falta de blocos `try/catch` em consultas ao Mongoose ou erros de "duplo envio de cabeçalhos" (`ERR_HTTP_HEADERS_SENT`) devido à ausência de `return` após respostas HTTP.
* **Semântica RESTful:** Houve uma confusão persistente entre ações e recursos, resultando em rotas que incluíam verbos na URL (ex: `/create`, `/delete/:id`), em vez de utilizar o verbo HTTP apropriado (POST, DELETE) sobre o recurso base.
* **Ausência de TDD:** A falta total de suítes de testes (Jest) foi o elo mais fraco. O TDD, se aplicado, teria prevenido erros básicos de sintaxe e lógica que tornaram algumas APIs inoperantes.

## 3. Dilemas Técnicos e Éticos

Durante o processo de correção, surgiram pontos críticos que demandaram um rigor pedagógico diferenciado:

* **Identificação de Plágio:** Detectou-se uma "assinatura de erro" em submissões distintas. Alunos compartilharam não apenas estruturas, mas erros sintáticos idênticos e logicamente improváveis de ocorrerem por coincidência (como o uso de métodos inexistentes `findByAndUpdate` ou erros idênticos na lógica de negação `!`), invalidando a autoria individual em diversos casos.
* **Qualidade da Revisão de Código:** Houve uma carência quase unânime de processos de *Code Review* e uso de *Git Flow* (branches para tarefas), o que dificultou a rastreabilidade da evolução lógica do projeto.
* **Rigidez vs. Equilíbrio Pedagógico:** Surgiu o dilema de como penalizar a falta de arquitetura sem desmotivar o sucesso operacional. Optou-se por recompensar o funcionamento robusto (estabilidade) enquanto se aplicaram deduções claras pela ausência dos padrões arquiteturais exigidos.

---

### Conclusão e Próximos Passos

A turma demonstrou um excelente domínio funcional da linguagem e do *framework* Express. O próximo salto qualitativo exigirá que os alunos abandonem a zona de conforto do padrão MVC monolítico. A transição para o padrão **Repository** e a implementação obrigatória de testes automatizados são os pilares que transformarão a entrega funcional em um produto de engenharia de software escalável.

---

### Sugestão para o Discente

Para elevar o nível de suas entregas, recomendo que o foco de estudos para a próxima etapa seja:

1. **Isolamento da Camada de Dados:** Criar *Repositories* que abstraiam totalmente o Mongoose.
2. **Testes como Guia:** Utilizar o Jest antes da escrita do controlador para definir o comportamento esperado.
3. **Refinamento Semântico:** Limpar URLs, removendo verbos e privilegiando substantivos e métodos HTTP.

Este documento consolida o desempenho da turma e servirá como base para as orientações das próximas etapas pedagógicas.

---

> **Nota do Professor Auxiliar:** O documento foi estruturado para refletir tanto o sucesso técnico da maioria dos discentes quanto a necessidade urgente de adoção de boas práticas de engenharia, servindo como um guia para melhorias futuras.
