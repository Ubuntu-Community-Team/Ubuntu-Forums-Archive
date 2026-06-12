---
title: "Anaphraseus - computer assisted translations for OOo"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by bwebb on 2008-09-12
Is there anyone out there familiar with **Anaphraseus** – the computer assisted translation tool for Open Office WP? It seems that it could be a very useful tool for translators and linguists.

I installed the extension on my Open Office word processor but I cannot set it up since I get the error message: OpenBasic error in 'Reading exceeds EOF.' Line 25

I'm quite new to Linux... so, I'm still going through trial and error.

Any suggestions?

Here's more info about Anaphaseus:
[http://www.fanaticattack.com/2008/turn-openofficeorg-into-a-lean-mean-cat-machine-with-anaphraseus.html](http://www.fanaticattack.com/2008/turn-openofficeorg-into-a-lean-mean-cat-machine-with-anaphraseus.html)

---

### Post by SunnyRabbiera on 2008-09-12
is this a add on for Open office?
This may be a java issue, but lets see what kind of thing we are dealing with here.

---

### Post by bwebb on 2008-09-12
Yup, it is an add-on to OOo WP.

---

### Post by SunnyRabbiera on 2008-09-12
I would suggest in synaptic removing the open jdk packages and installing normal java.
If you are unsure how to work synaptic, it is very simple.
If you need directions just ask, synaptic is located under system> administration > synaptic

---

### Post by bwebb on 2008-09-12
After installing the add-on to the OOo's Word Processor, I get an error when I try to set up the Anaphraseus. The error window is "BASIC runtime error. Reading exceeds EOF."

The macros and dialogs window opens up and shows me a line where the problem seems to be. This is the line I see:
Line Input #iFile, S

What should I do?

---

### Post by bwebb on 2008-09-16
Not sure what I did but it seems to work now. Just have to figure out how to use it.

---

### Post by esperantisto on 2008-10-02
I think, this article may be useful: [http://www.fanaticattack.com/2008/turn-openofficeorg-into-a-lean-mean-cat-machine-with-anaphraseus.html](http://www.fanaticattack.com/2008/turn-openofficeorg-into-a-lean-mean-cat-machine-with-anaphraseus.html)

It contains almost a full description of workflow (as Anaphraseus does not have too many features so far :) )

---

### Post by lion9 on 2010-04-12
I have received the same mistake. Guys, any ideas?

---

### Post by lion9 on 2010-04-12
It seems that deleting "anaphraseus" folder from .openoffice/3/user/ helped to manage the problem. Now I am able again to create TMs and choose them from the existing ones.

---

### Post by little_penguin on 2010-04-28
Deleting the folder worked for me too. Thanks.

---

