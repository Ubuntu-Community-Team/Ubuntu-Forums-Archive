---
title: "get a text"
date: 2009-01-01
forum: Programming Talk
---

### Post by davidtuti on 2009-01-01
Hi,

I have a very long text without carriage return like:

```

ize=-1>Resultados <b>1</b> - <b>10</b> de <b>hermas bolena</b>  (<b>0.07</b> segundos)&nbsp;</font></td></tr></table><div id=res><p><font color="#cc0000" class=p>Quizás quiso decir: </font><a href="/custom?hl=es&amp;client=google-coop-np&amp;cof=FORID:11%3BAH:left%3BL:http://www.google.com/coop/intl/es/images/custom_search_sm.gif%3BLH:65%3BLP:1%3BBGC:%23f7f8fc%3BVLC:%23663399%3BGALT:%23009900%3BDIV:%23a7a6a6%3B&amp;ad=w9&amp;cx=003284578463992023034:lraatm7pya0&amp;adkw=AELymgWpiI3ffTqEb_xlTxgtMMwdNRsUtwR7V-b8kzLEoC-I4U1M5pO7feaDi-o3sTOFC2M4zgBSn2HFxiCVWbgmUplbWBdDG2yFNUIDeJ5AKwTu-G5c9T4&amp;oe=ISO-8859-1&amp;sa=X&amp;oi=spell&amp;resnum=0&amp;ct=result&amp;cd=1&amp;q=hermanas+bolena&amp;spell=1" class=p><b><i>hermanas</i></b> bolena</a>&nbsp;&nbsp;<br><div><ol style="margin:0;padding:0;list-style:none"><table align=right><tr><td align=left><a href="http://www.google.com/coop/cse/?hl=es" target=_top><img src="/images/poweredby_transparent/poweredby_FFFFFF.gif" alt=Google border=0></a><br><span style="font-size:9px;font-weight:bolder;color:#000000">&nbsp;Búsqueda personalizada</span></td></tr></table><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/peliculas/the-other-boleyn-girl-1121.html" target=_top class=l>Las <em>hermanas Bolena</em> (2008) - El Séptimo Arte</a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>16 Nov 2007 <b>...</b> Sinopsis de la película Las <em>hermanas Bolena</em> (The Other Boleyn Girl), fotos, cartel, trailer, reparto, crítica y más.<br><span class=a>www.elseptimoarte.net/peliculas/the-other-boleyn-girl-1121.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php?topic=9274.0" target=_top class=l>Las <em>hermanas Bolena</em></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std><div class="f">6 entradas&nbsp;-&nbsp;Última entrada:&nbsp;6 Ago 2008</div>El padre y el tíode las dos <em>hermanas Bolena</em>, Ana y María, empujados por el ambicioso deseo de mejorar el nivel social y el poder de la <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php?topic=9274.0</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/-the-boleyn-inheritance--la-posible-secuela-de--las-hermanas-bolena--3902.html" target=_top class=l>'The Boleyn Inheritance' la posible secuela de 'Las <em>Hermanas</em> <b>...</b></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>1 Jun 2008 <b>...</b> Según los rumores surgidos en los últimos días habrá una más que posible secuela de 'Las <em>Hermanas Bolena</em>', cinta estrenada este año con más <b>...</b><br><span class=a>www.elseptimoarte.net/-the-boleyn-inheritance--la-posible-secuela-de--las-<wbr><b>hermanas</b>-<b>bolena</b>--3902.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php/topic,2699.0.html" target=_top class=l>'Las <em>hermanas Bolena</em>' - Trailer en Español</a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std><div class="f">16 entradas&nbsp;-&nbsp;Última entrada:&nbsp;2 Ago 2007</div>La veterana actriz dará vida a la mamá de las <em>hermanas Bolena</em> (Johansson y Portman), quienes se disputan el corazón del rey Enrique VIII <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php/topic,2699.0.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php/topic,8152.0.html" target=_top class=l>las <em>hermanas bolena</em></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>Autor, Tema: las <em>hermanas bolena</em> (Leído 330 veces) <b>...</b> quisiera saber si la pelicula de las <em>hermanas Bolena</em> (the other boleyn girl) ya estreno en mexio o <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php/topic,8152.0.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/usa-29-2-mar--will-ferrell-con--semi-pro--se-impone-a-las-herman

```

I've saw that the search patter is always:

<a href="http://www.elseptimoarte.net/foro/index.php?topic=9274.0">

Begins with <a href="  and ended with ">

And I would like to have : [http://www.elseptimoarte.net/foro/index.php?topic=9274.0](http://www.elseptimoarte.net/foro/index.php?topic=9274.0).

I would like to do with sed becausa I'm trying to learning this command.

I do:

sed "s/<a href=\([^ ]*\)\".*$/var1=\1/" filename

But doesn't works!. Anything could you say me how it's the sentence and why doesn't vorks?

Many thanks and sorry for my english!

---

### Post by ghostdog74 on 2009-01-01
if you have PHP.
```

<?php


$string = <<< EOF
ize=-1>Resultados <b>1</b> - <b>10</b> de <b>hermas bolena</b>  (<b>0.07</b> segundos)&nbsp;</font></td></tr></table><div id=res><p><font color="#cc0000" class=p>Quizás quiso decir: </font><a href="/custom?hl=es&amp;client=google-coop-np&amp;cof=FORID:11%3BAH:left%3BL:http://www.google.com/coop/intl/es/images/custom_search_sm.gif%3BLH:65%3BLP:1%3BBGC:%23f7f8fc%3BVLC:%23663399%3BGALT:%23009900%3BDIV:%23a7a6a6%3B&amp;ad=w9&amp;cx=003284578463992023034:lraatm7pya0&amp;adkw=AELymgWpiI3ffTqEb_xlTxgtMMwdNRsUtwR7V-b8kzLEoC-I4U1M5pO7feaDi-o3sTOFC2M4zgBSn2HFxiCVWbgmUplbWBdDG2yFNUIDeJ5AKwTu-G5c9T4&amp;oe=ISO-8859-1&amp;sa=X&amp;oi=spell&amp;resnum=0&amp;ct=result&amp;cd=1&amp;q=hermanas+bolena&amp;spell=1" class=p><b><i>hermanas</i></b> bolena</a>&nbsp;&nbsp;<br><div><ol style="margin:0;padding:0;list-style:none"><table align=right><tr><td align=left><a href="http://www.google.com/coop/cse/?hl=es" target=_top><img src="/images/poweredby_transparent/poweredby_FFFFFF.gif" alt=Google border=0></a><br><span style="font-size:9px;font-weight:bolder;color:#000000">&nbsp;Búsqueda personalizada</span></td></tr></table><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/peliculas/the-other-boleyn-girl-1121.html" target=_top class=l>Las <em>hermanas Bolena</em> (2008) - El Séptimo Arte</a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>16 Nov 2007 <b>...</b> Sinopsis de la película Las <em>hermanas Bolena</em> (The Other Boleyn Girl), fotos, cartel, trailer, reparto, crítica y más.<br><span class=a>www.elseptimoarte.net/peliculas/the-other-boleyn-girl-1121.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php?topic=9274.0" target=_top class=l>Las <em>hermanas Bolena</em></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std><div class="f">6 entradas&nbsp;-&nbsp;Última entrada:&nbsp;6 Ago 2008</div>El padre y el tíode las dos <em>hermanas Bolena</em>, Ana y María, empujados por el ambicioso deseo de mejorar el nivel social y el poder de la <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php?topic=9274.0</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/-the-boleyn-inheritance--la-posible-secuela-de--las-hermanas-bolena--3902.html" target=_top class=l>'The Boleyn Inheritance' la posible secuela de 'Las <em>Hermanas</em> <b>...</b></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>1 Jun 2008 <b>...</b> Según los rumores surgidos en los últimos días habrá una más que posible secuela de 'Las <em>Hermanas Bolena</em>', cinta estrenada este año con más <b>...</b><br><span class=a>www.elseptimoarte.net/-the-boleyn-inheritance--la-posible-secuela-de--las-<wbr><b>hermanas</b>-<b>bolena</b>--3902.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php/topic,2699.0.html" target=_top class=l>'Las <em>hermanas Bolena</em>' - Trailer en Español</a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std><div class="f">16 entradas&nbsp;-&nbsp;Última entrada:&nbsp;2 Ago 2007</div>La veterana actriz dará vida a la mamá de las <em>hermanas Bolena</em> (Johansson y Portman), quienes se disputan el corazón del rey Enrique VIII <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php/topic,2699.0.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/foro/index.php/topic,8152.0.html" target=_top class=l>las <em>hermanas bolena</em></a></h2><table border=0 cellpadding=0 cellspacing=0><tr><td class="j"><div class=std>Autor, Tema: las <em>hermanas bolena</em> (Leído 330 veces) <b>...</b> quisiera saber si la pelicula de las <em>hermanas Bolena</em> (the other boleyn girl) ya estreno en mexio o <b>...</b><br><span class=a>www.elseptimoarte.net/foro/index.php/topic,8152.0.html</span><nobr></nobr></div></td></tr></table></div><li><div class=g><h2 class=r><a href="http://www.elseptimoarte.net/usa-29-2-mar--will-ferrell-con--semi-pro--se-impone-a-las-herman';
EOF;

$string = strip_tags($string,"<a>");
$string = preg_split("/<a\s+href=/",$string);
foreach ($string as $k=>$v){
  if( strpos($v,"http://www.elseptimoarte.net/foro/index.php") !== FALSE) {    
    $v=preg_replace("/target.*/smi","",$v);
    print $v."\n";                
  }
} 


```

run it on command line:
```

# php5 test.php
"http://www.elseptimoarte.net/foro/index.php?topic=9274.0"
"http://www.elseptimoarte.net/foro/index.php/topic,2699.0.html"
"http://www.elseptimoarte.net/foro/index.php/topic,8152.0.html"


```

---

### Post by davidtuti on 2009-01-01
Many thanks!

But something cand say me with a sed command

---

### Post by ghostdog74 on 2009-01-01
Please use the more suitable tools for the job. If you know of other languages like Python or Perl/Ruby which has equivalent HTML parsing capabilities, then use them. That's all i have to say, unless this is some kinda homework where restriction had been placed on using sed.

---

### Post by lloyd_b on 2009-01-01
I agree with ghostdog74 - 'sed' is *not* the right tool for the job.  The primary purpose of 'sed' is to *edit* streams, not the kind of text extraction you are trying to do.

If you insist on doing it with basic console utilities (which should be available on any *nix system):
```
cat filename | tr '<' '\n' | tr '>' '\n' | grep href | cut -d '"' -f2
```

What this does is convert the angle brackets ("<" and ">") into newlines, so each element is on a line by itself, searches for the "href", and then uses "cut" to extract the portion in quotation marks.

Lloyd B.

---

### Post by ghostdog74 on 2009-01-01
> **lloyd_b said:**
> 

```
cat filename | tr '<' '\n' | tr '>' '\n' | grep href | cut -d '"' -f2
```


```

awk '/<a\ href=\"http:\/\/www.elseptimoarte.net\/foro/{  print $1" "$2 }' RS=">" file

```

all the above tools used can be substituted with just awk.

---

