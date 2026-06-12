---
title: "HowTo have a multilingual dictionary via command lines"
date: 2007-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by xyz on 2007-02-12
Hi everyone,

For command lines' fans, I found this cute little trick on the French Ubuntu forum.
[Originally posted by **alteo_gange.**]("http://forum.ubuntu-fr.org/viewtopic.php?id=80544") Thanks!


You'll need a ./bin/bash script adapted to your own language!
On the Williams College Libraries' site, you'll find just about any language abbreviations in the world.
[Williams College Libraries]("http://www.williams.edu/library/guides/languages.php")

So here we go! You need to put your script(s) in /usr/local/bin
In a terminal, run:
```
sudo gedit /usr/local/bin/en2fr
```
The "en2fr" will obviouly allow you to translate an English word to its French equivalent. It proves to be quite practical to translate, for instance, words in the 'man' pages; however, you can also type "grandmother" and get a decent translation!

For KDE users:
```
$ kdesu kate /usr/local/bin/en2fr
```
Then copy/paste this:
> #!/bin/bash
w3m http://www.wordreference.com/fr/Translation.asp?enfr=$1

into it.

Make it executable...in a terminal, run:
```
 sudo chmod 755 /usr/local/bin/en2fr
```
You can also Right click on the file > Properties > Permissions > Execute

So now you'll be able to use a new command line: *en2fr*
```
$ en2fr English_word_to be_translated
```

*To get out of it, press q and y.*

_English > Spanish - en2es_
```
#!/bin/bash
w3m http://www.wordreference.com/es/translation.asp?tranword=$1
```
_Spanish > English_ - es2en
```
#!/bin/bash
w3m http://www.wordreference.com/es/en/translation.asp?spen=$1
```
_English > Italian_ - en2it
```
#!/bin/bash
w3m http://www.wordreference.com/it/translation.asp?enit=$1
```
_Italian > English_ - it2en
```
#!/bin/bash
w3m http://www.wordreference.com/it/en/translation.asp?iten=$1
```
_English > German_ - en2de
```
#!/bin/bash
w3m http://www.dict.cc/?s=$1
```
_German > English_ - de2en
```
#!/bin/bash
w3m http://www.dict.cc/?s=$1
```
_English > Turk_ - en2tr
```
#!/bin/bash
w3m http://www.seslisozluk.com/?word=$1&go_search=Search
```
_Turk > English_ - tr2en
```
#!/bin/bash
w3m http://www.seslisozluk.com/?word=$1&go_search=Search
```
_German > Turk_ - de2tr
```
#!/bin/bash
w3m http://www.seslisozluk.com/?word=$1&go_search=Search
```
_Turk > German_ - tr2de
```
#!/bin/bash
w3m http://www.seslisozluk.com/?word=$1&go_search=Search
```

To adjust the scrips to your own language needs:
Use the web search engine you usually use and, in the search space, just type a word; for instance, "mundo" (Portugese for world for those who wouldn't know). It can be any word.

Then create a file:
```
#!/bin/bash
w3m url
```
making sure you replace 'url'  with the url of your search and change the 'mundo' in the url to '$1'.

---

### Post by bodhi.zazen on 2007-03-05
Nice How-to

This thread has been added to the UDSF wiki.

[Multilingual_dictionary_via_command_line](http://doc.gwos.org/index.php/Multilingual_dictionary_via_command_line)

One quick question though, Your very first bash script has > #!/bin/bash
**w3m** http://www.wordreference.com/fr/Translation.asp?enfr=$1

All the rest of the scripts have no w3m. Is this correct?

---

### Post by PaulFXH on 2007-03-05
Very nice. Just what I needed.
But, I need some other languages and, in particular, Portuguese.
Can you tell me if, and how, it is possible to use the same script but for other languages?
Also, what is the significance of this:
> On the Williams College Libraries' site, you'll find just about any language abbreviations in the world.
Williams College Libraries
I had thought this may have allowed me to use the same technique for others languages but it seems not.
Thanks for any help
Paul

---

### Post by xyz on 2007-03-09
Language abbreviations are simply what you need for the script to work: fr = French; it = Italian; de = German and so on.

I've been in touch with **alteo_gange** about this:
Use the web search engine you usually use and, in the search space, just type a word; for instance, "mundo" (Portugese for 'world' for those who wouldn't know). It can be any word.

Then create a file:
```
#!/bin/bash
w3m url
```
making sure you replace 'url'  with the url of your search and change the 'mundo' in the url to '$1'.

---

### Post by bodhi.zazen on 2007-03-09
Thanks for updating the wiki :)

---

### Post by PaulFXH on 2007-03-09
Thanks to xyz for the reply.
As it happens I'm a long way from my home computer right now and the computer I have here does not have Linux installed.
Therefore, I can't test your suggestion at the moment.

Nevertheless, I am a little puzzled.
Here's what I did:
1. I chose the word "mulher" (Portuguese for "woman")
2. I put this word into the search space of Google
3. I picked the second of the 28 million search results which gave me this url "www.planetadamulher.com.br"
4. From what I understand, I should therefore change the second line of the script to "wm3 www.planetada$1.com.br"

What puzzles me is that this line in no way resembles the equivalent lines in the scripts for the other languages, all of which appear to be references to dictionaries.

Have I missed out on something?

Thanks
Paul

---

