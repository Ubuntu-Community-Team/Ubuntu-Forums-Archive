---
title: "Url java"
date: 2013-06-20
forum: Programming Talk
---

### Post by Greenbald on 2013-06-20
Someone know how can i get the information from this link [http://api.mymemory.translated.net/get?q=Hello%20World!&langpair=en|it](http://api.mymemory.translated.net/get?q=Hello%20World!&langpair=en|it) in line command in java? I want to take the [COLOR=#000000]Ciao mondo! from the content. i did it this way : 

[/COLOR]BufferedReader in = new BufferedReader(new InputStreamReader(url.openStream()));[COLOR=#000000]
[/COLOR]inputLine = in.readLine();
inputLine.substring(35, inputLine.indexOf("\"", 35)); 

I'm thinking if have a way to get this information like accessing a variable, but in this case, accessing a "[COLOR=#000000]translatedText".

Thanks![/COLOR]

---

