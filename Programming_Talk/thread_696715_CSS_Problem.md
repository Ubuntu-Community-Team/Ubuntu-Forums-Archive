---
title: "CSS Problem"
date: 2008-02-14
forum: Programming Talk
---

### Post by ben22 on 2008-02-14
Hi,

I try to create a two column layout with difs, with both difs having the same width. The problem is that the text is floating over the div and not breaking into a new line.

Any help out there????




[HTML]<html>
  <head>
    <title>style-Attribut</title>
    
    <style type="text/css">      
      body {        
      }
        


      div#left {
        float: left; 
        border: dashed silver;
        width: 49%;
        color:#000000;
  
        

        
      }
      
      div#right {
        border: dashed silver;
        float: right;
        color:#CC0000;
        width: 49%;

      }
      

    </style>
    
  </head>

  <body>
  

  
    <div id="left">
    
      <h1>Die Seite mit dem besonderen Element</h1>
      aber das folgende Element soll etwas Besonderes sein:</p>
      <p>Hier sind zwar zentrale Formatdefinitionen vorhanden,

       Unser Kopf ist rund, damit das Denken die RichtungRichtungdddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddd Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung Richtung  wechseln kann!
      </p>
    
    </div>
    
    <div id="right">
    
      <h1>Die Seite mit dem besonderen Element</h1>
      aber das folgende Element soll etwas Besonderes sein:</p>
      <p>Hier sind zwar zentrale Formatdefinitionen vorhanden,

       Unser Kopf ist rund, damit das Denken die Richtung wechseln kann!adsacvasdfasdfasdddddddddddddddddddddddddddddddddddddddddddddddddddasddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddUnser Kopf ist rund, damit das Denken die Richtung wechseln kann!adsacvasdfasdfasddddddddddddddddddddddddddddddddddddddddddddddddddd

      </p>
    
    </div>

  </body>

</html>[/HTML]

---

### Post by MCrittenden on 2008-02-14
When I copied and pasted into html file, it looked fine to me. The words with tons of d's goes out of the divs just because html keeps the words intact even if they're way too long for their container. Just don't make such long words and you should be alright. All of the other words stayed in the div's just fine.

---

### Post by ben22 on 2008-02-14
yes, but I need to break these words into new lines.

---

### Post by shawnhcorey on 2008-02-14
How about adding some scrollbars?

```
      div#left {
        float: left; 
        border: dashed silver;
        width: 49%;
        color:#000000;
        overflow: auto;      
      }
      
      div#right {
        border: dashed silver;
        float: right;
        color:#CC0000;
        width: 49%;
        overflow: auto;
      }

```

---

