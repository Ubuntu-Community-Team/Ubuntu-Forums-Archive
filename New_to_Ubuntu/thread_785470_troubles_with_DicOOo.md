---
title: "troubles with DicOOo"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-07
[ATTACH]69116[/ATTACH]
Yeah, trying to install American English spell check (Computer still thinks I'm in Canada...).  Cannot maximize it (tried to by right clicking and maximize cannot be selected).
Anyway is there another way to install spell check on open office without using dicOOo?

---

### Post by bluefrog on 2008-05-07
that is a bug indeed. will see if a bug report has been made (100% chance yes).
In the mean time
[http://lingucomponent.openoffice.org/download_dictionary.html](http://lingucomponent.openoffice.org/download_dictionary.html)

---

### Post by germclown on 2008-05-14
I just figured this one out today (pieced it together from other threads/websites). My Open Office kept crashing every time I tried to install through the DicOOo wizard.

Look for myspell or wamerican, wcanadian, wbritish in synaptic. I installed the myspell british english and the wcanadian 'huge' dictionary. No messing with OO wizards and they both worked as soon as I started a fresh writer session. I didn't need to do anything but install them with synaptic.

I don't know how thorough the myspells are, but the wcanadian came in four sizes from small to huge, so I'm assuming I got a pretty comprehensive dictionary.

Myspell apparently has no canadian english, but you can get american from both myspell and wamerican.

Hope this is what you're looking for...

---

### Post by mano cazalet on 2008-05-14
when the dictoo window is that small the workaround is to disable compiz and then you will be able to install the dictionaries.

this is a bug, already reported and confirmed

---

### Post by sam_delta on 2008-05-14
```
sudo apt-get install language-support-en
```

sam

---

### Post by SonicSteve on 2008-06-03
> **fontenot_1031 said:**
> [ATTACH]69116[/ATTACH]
Yeah, trying to install American English spell check (Computer still thinks I'm in Canada...).  Cannot maximize it (tried to by right clicking and maximize cannot be selected).
Anyway is there another way to install spell check on open office without using dicOOo?

You've likely fixed this by now but just incase you haven't. 
 Disable desktop effects (compiz). Then dicOOo will work properly.
System> preferances> appearance> visual effects > click none 

Retry dicOOo and it will likely work for you, thus allowing easy dictionary installations.

---

