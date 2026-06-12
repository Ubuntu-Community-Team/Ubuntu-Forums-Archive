---
title: "I neeed help!!!!!!"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by abbalooga on 2008-10-30
OMG!!!

ok.. calm down..  right

so i jut installed ubuntu 7.10 on my ps3.  and  NO MP3!!!!!

i managed to install pidgin after 2 hours of trouble.. so i started to look into the mp3 plrblem..  and


OH NO!!! i uninstalled rhythmbox to try and re-isntall it hoping this would fix it..  but..   IT WONT RE_INSTALL... it says it is not compatable with powerpc.. and i CANNOT install ubuntu-restricted-extras or whatever the stupid thing is called.. it just doesnt exsist..   and i can never ever get sudo apt install thingy to work.. i followall instructions and it ALWASY returns cannot rind "___" package or whatever...



CAN ANY1 HELP MEE!!!!!!

thankyou.. from mr noob

---

### Post by bumanie on 2008-10-30
Go to system --> Administration  --> Software sources and click the first four check boxes and make sure that the cd-rom is unchecked. The go to Third party and click the two canonical check boxes. The go to terminal and > sudo apt-get update Synaptic package manager and add/remove should now work.

---

### Post by hyper_ch on 2008-10-30
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by alwez_loner on 2008-10-30
Take a deep breath.... and relax...

go to the Synaptic Manager and follow these instructions to install music player and the codecs.

[http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/](http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/)

---

### Post by por100pre1 on 2008-10-30
First, relax. Use Terminal (Applications> Accessories> Terminal)and then try this:

```
sudo apt-get install -f
```

---

### Post by mkvnmtr on 2008-10-30
On my G4 I found it much easier to get restricted extras on 8.04 for powerpc. There is no reason to be on 7.10 since support has ended for that distro.

---

### Post by abbalooga on 2008-10-31
Alllll i needed to do was tick those 4boxes and away she went.. cheers guys!!


and yes.. descriptve titles will be included in future problem asking..

thanx guys.. linux would be impossible to learn without ur help

---

### Post by stephanvaningen on 2008-10-31
Please tag as [solved] (using option in top-right on screen),


thanks!

---

