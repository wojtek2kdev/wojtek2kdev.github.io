---
layout: post
title: Projektowanie systemu za pomocą kodu.
categories: 
 - automatyzacja
 - projektowanie
comments: true
---

Każdy programista w swojej karierze, prędzej czy później, będzie miał do czynienia z projektowaniem architektury systemu, czy to dla biznesu, czy na użytek organizacji open source. Zazwyczaj projekt taki wygodnie jest opisać przy pomocy [diagramów UML](https://pl.wikipedia.org/wiki/Unified_Modeling_Language), na przykład przy pomocy [draw.io](https://draw.io). 

Tworzymy wizualnie, z gotowych klocków, pewną strukturę opisującą abstrakcyjne zasady działania naszego systemu, powiązania komponentów, przepływ komend, zdarzeń i danych. W wyniku dostajemy plik graficzny lub dokument w formacie html lub innym. 

Wszystko ładnie, pięknie, ale.. Co jeżeli chcemy, aby inni członkowie zespołu pracujący nad systemem, mieli możliwość **szybkiego** modyfikowania planu projektu w razie potrzeb? W taki sposób, aby zmiany w architekturze były nanoszone przy pomocy **pull requestów** i **dyskusji** programistów. W takim przypadku modyfikowanie dokumentów w zewnętrznym serwisie staje się niewygodne i wolne.

Możemy zautomatyzować taki proces przy pomocy [PlantUML](https://plantuml.com). Jest to program, który przy pomocy prostego [DSL'a](https://pl.wikipedia.org/wiki/Język_dziedzinowy) wygeneruje nam diagramy UML. 

Wystarczy skorzystać z servera proxy PlantUML. Pierw musimy utworzyć plik reprezentujący nasz diagram UML (zazwyczaj z rozszerzeniem .puml) i zakodować w nim potrzebne informacje. Następnie kopiujemy URL do **raw** naszego pliku. Po tym tworzymy w repozytorium plik **markdown** (może być również opis pull requesta), w którym umieszczamy znacznik zdjęcia.
```
![alt_text](link)
```
W miejsce linku wpisujemy adres: 

<p style="word-break: break-word;">http://www.plantuml.com/plantuml/proxy?src=</p>

Na końcu odnośnika doklejamy adres do naszego pliku. Cały proces obrazuje poniższy diagram sekwencyjny:

![](https://i.imgur.com/rYn1NLE.png)

Przykład działania:

1. Link do kodu przykładowego diagramu klas ze strony PlantUML.
<a href='https://pastebin.com/raw/Wt17gk7F' style='word-break: break-word;'>https://pastebin.com/raw/Wt17gk7F</a>

2. Artykuły na tym blogu są generowane na podstawie plików markdown, więc po prostu wstawiam tu zdjęcie, które zostanie wygenerowane przez server proxy. Link:

<p style='word-break: break-word;'>http://www.plantuml.com/plantuml/proxy?src=https://pastebin.com/raw/Wt17gk7F</p>

![](http://www.plantuml.com/plantuml/proxy?src=https://pastebin.com/raw/Wt17gk7F)

Gotowe. Teraz aby zmienić diagram, wystarczy zmodyfikować plik źródłowy, a zdjęcie samo się odświeży. Dzięki temu mechanizmowi możemy dynamicznie dokonywać zmian w architekturze systemu dzięki prostym commitom do kodu, który reprezetuje dany diagram UML.

