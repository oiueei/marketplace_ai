# marketplace_ai

### Goals

- Pesquisar produtos por "Processamento de Linguagem Natural";
- Permitir eligir mais rapidamente quando existe uma quantidade enorme de parâmetros em diferentes produtos ou serviços, ou itens;
- Permitir uma solução rápida e barata de AI a webs de e-commerce, intranets e marketplaces;

# Problema

**Quem nunca ficou perdido na hora de comprar um celular novo? Ou um laptop? Tantos modelos, cada uno com diferentes características, um tem mais disso, outro tem isso mais não aquilo. O problema é que pesquisar por páginas web, mesmo as lojas de e-commerce más populares de mundo, a partir de uns filtros ou uma pequisa, que leva uma lista de opções, dar o clique em um dos itens, ir a outra página com todos os detalhes... Isso que parecia tão incrível, agora se o comparamos com o poder da AI, passa a parece coisa pré-histórica.**

Trabalho para um grupo que disponibiliza para seus usuários uma bolsa de cargas e caminhões. Resumidamente funciona assim, cada dia, centenas de milhares de ofertas de cargas que tem que ser recolhidas no ponto e entregues em outro lugar são oferecidas em uma plataforma online onde dezenas de milhares de empresas de transporte buscam entre estas cargas las mais interessantes para cargar seus caminhões. O sistema funciona como qualquer marketplace. Com pesquisas por origem e destinos, e filtrando por medidas, pesos, e outras características de mercância ou de tipos de caminhão.

Com um agravante importante: diferentemente de um livro, ou aparato eletrônico, para citar dois exemplos, um cargamento de mercadoria ofertada é único. O primeiro transportador que contatar e fechar negócio vai ter carga, o segundo que chamar vai ficar sem nada. Então o dilema é, se buscar pouco vai ter negócio, mas talvez não o melhor possível, se demorar muito pesquisando, quando se finalmente se decidir por algo, talvez esta já não esteja disponível.

# Proposta

Este projeto busca resolver este problema utilizando o Gemini. La ideia basicamente é aceder a todas las cargas disponíveis em um formato JSON, por exemplo, e através do método FEW SHOT ensinar o Gemini o que significa cada parâmetro e assim possibilitar que por texto natural cada usuário possa buscar as cargas mais adequadas as suas preferências ou especialidade.

>  **Exemplos de consultas possíveis:**
- Buscar cargamentos com origem em Barcelona.
- Buscar cargamentos com origem cerca de Barcelona e destino cerca de Madri.
- Buscar cargamentos com carga completa ou FTL (full truckload), ou seja, mais de 10 toneladas.
- Buscar cargamentos para LTL (less than truckload), ou seja, algumas cargas pequenas, menos de 5 toneladas cada uma, por exemplo.

# Few shots

| ID | From | To | Distance | Duration | Date | Type of truck | Length | Weight | Contact |
|---|:--------------------------------|:-------------------------------- |----:|----:|----|:------------------ |----:|----:|-----------------------------|
| 1 | ES-28001 Madrid | ES-01001 Vitoria-Gasteiz | 354 km | 4h 58m | 09/05 | Box | 0,1t | 2m | +34 756 56 45 |
| 2 | ES-33001 Oviedo | ES-31001 Pamplona | 449 km | 6h 40m | 10/05 | Temperature Controlled | 1,5t | 6m | +34 769 59 87 |
| 3 | ES-28001 Madrid | ES-15001 Coruña | 592 km | 8h 9m | 10/05 | Tautliner | 24t | 13,6m | +34 741 00 23 |

### Ensinar o Gemini que significa eso

- **"ES-28001 Madrid"**  => **"ES"** de Espanha e o **"28001""** é o CEP e **"Madrid"** é a cidade
- A primeira localidade (**"From"**) é onde o caminhão carga a mercadoria
- A segunda localidade (**"To"**) é onde o caminhão descarga a mercadoria
- **"Distance"** é a distância em quilômetros entre o ponto de carga e de descarga
- **"Date"** é a data de carga
- **"Truck"** é o tipo de caminhão
- **"Length"** e Weight são o peso e a medida da carga
- **"Contact"** é o telefone para chamar e negociar o preço e as condições

# Roadmap
- Aceder ao conteúdo de um JSON de exemplo: **Done!**
- Convertê-lo em Dataframe: **Done!**
- Testar o método de "embedding" para comparar consultas com uma coluna do conteúdo: **Done!**
- Embeddar todo o conteúdo: **Done!**
- Ensinar o Gemini que significa cada coisa: **In progress**
- Aceder ao conteúdo desde uma JSON API: **Backlog**
- Criar um chat bot para interação: **Backlog**
