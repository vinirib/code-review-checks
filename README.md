<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Code Review Checklist.md</title>
      <link rel="stylesheet" href="https://stackedit.io/style.css" />
   </head>
   <body class="stackedit">
      <div class="stackedit__left">
         <div class="stackedit__toc">
            <ul>
               <li>
                  <a href="#code-review-checklist">Code Review Checklist</a>
                  <ul>
                     <li><a href="#coesão">Coesão</a></li>
                     <li><a href="#encapsulamento">Encapsulamento</a></li>
                     <li><a href="#coerência">Coerência</a></li>
                     <li><a href="#herança">Herança</a></li>
                     <li><a href="#concorrência">Concorrência</a></li>
                     <li><a href="#segurança">Segurança</a></li>
                     <li><a href="#exceções">Exceções</a></li>
                     <li><a href="#documentação">Documentação</a></li>
                     <li><a href="#testes-unitários">Testes Unitários</a></li>
                     <li><a href="#testes-funcionais">Testes Funcionais</a></li>
                  </ul>
               </li>
            </ul>
         </div>
      </div>
      <div class="stackedit__right">
      <div class="stackedit__html">
         <h1 id="code-review-checklist">Code Review Checklist</h1>
         <h2 id="coesão">Coesão</h2>
         <ul>
            <li>classe possui apenas uma responsabilidade?</li>
            <li>método possui apenas uma responsabilidade?</li>
            <li>existe probabilidade dessa implementação crescer?</li>
            <li>existe possibilidade de propagação de mudança?</li>
            <li>métodos privados escondem lógica procedural?</li>
            <li>existe regra de negócio e infraestrutura na mesma classe?</li>
            <li>DRY: existe código duplicado?</li>
            <li>IoC (tell, don’t ask): podemos reduzir acoplamento passando parâmetros mais apropriados?</li>
         </ul>
         <h2 id="encapsulamento">Encapsulamento</h2>
         <ul>
            <li>existe invocação em cadeia (chamada com mais de um “ponto”, e.g. <code>carro.getMotor().ligar()</code> )?</li>
            <li>intimidade inapropriada: existe classe/método com dependência de detalhes de implementação de outra classe?</li>
            <li>modelo anêmico: existe definição de estado e/ou comportamento de um objeto implementado fora de sua classe?</li>
         </ul>
         <h2 id="coerência">Coerência</h2>
         <ul>
            <li>existem abreviações em nomes de variáveis, métodos ou classes?</li>
            <li><em>magic numbers</em>: existem números sem descrição do que representam (comuns em condições e iterações)?</li>
            <li>os nomes de classes são substantivos, representando coisas e não ações?</li>
            <li>os nomes de métodos são verbos, representando ações e não coisas?</li>
            <li>os nomes de <em>booleanos</em> são predicativos, indicando estado?</li>
            <li>nome condiz com implementação?</li>
         </ul>
         <h2 id="herança">Herança</h2>
         <ul>
            <li>pré e pós condições das super classes atendidas?<br>
               <em>Obs: pré condições representam os parâmetros passados em um construtor/método, ao passo que pós condições representam seus retornos. Uma subclasse não pode, em <em>nenhuma</em> hipótese, restringir os parâmetros e retornos da super classe.</em>
            </li>
         </ul>
         <h2 id="concorrência">Concorrência</h2>
         <ul>
            <li>existem atributos inseguros? <em>Obs: atributos inseguros são atributos de classe que podem, acidentalmente, ser manipulados ao mesmo tempo por requests diferentes. Deve-se (1) evitar atributos de classe nessas circunstâncias ou (2) utilizar o locking disponível pela linguagem.</em></li>
         </ul>
         <h2 id="segurança">Segurança</h2>
         <ul>
            <li>todos os campos de formulários são tratados com whitelist?</li>
            <li>todas as credenciais armazenadas são criptografadas?</li>
            <li>possuímos informações sensitivas em arquivos de log (e.g. número de CC com CVC)?</li>
         </ul>
         <h2 id="exceções">Exceções</h2>
         <ul>
            <li>existe algum catch vazio?</li>
            <li>é utilizada <code>Exception</code> genérica para erro de negócio?</li>
            <li>existe algum catch tratando <code>Exception</code> genérica indevidamente?</li>
         </ul>
         <h2 id="documentação">Documentação</h2>
         <ul>
            <li>existe javadoc para todas as classes e métodos públicos?</li>
            <li>existem TODO ou FIXME?</li>
            <li>existem logs suficientes no código para auxiliar acompanhamento e debug?</li>
            <li>os níveis de logs estão apropriados?</li>
            <li>todas as exceções possuem logs?</li>
         </ul>
         <h2 id="testes-unitários">Testes Unitários</h2>
         <ul>
            <li>todos os métodos foram testados para <em>null safe</em>?</li>
            <li>todos os fluxos de sucesso e de exceção foram cobertos?</li>
            <li>os testes estão genéricos demais?</li>
            <li>existem mocks desnecessários?</li>
            <li>existem testes falsos? <em>(pode ser detectado por testes de mutação)</em></li>
         </ul>
         <h2 id="testes-funcionais">Testes Funcionais</h2>
         <ul>
            <li>Todos os requisitos funcionais estão cobertos?</li>
            <li>Todos os fluxos de exceção estão cobertos?</li>
         </ul>
      </div>
   </body>
</html>

