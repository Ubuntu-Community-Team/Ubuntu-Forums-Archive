---
title: "HOWTO: A clean fluxbox install."
date: 2005-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by dud on 2005-07-25
ATT: Look at the post below for the guide, as it seems silly to have a copy here now that I update the guide at [http://nix-dev.dudcore.net](http://nix-dev.dudcore.net) instead. :)

---

### Post by dud on 2005-07-26
This HOWTO can be in a more digestable wiki format over at 
[http://nix-dev.dudcore.net/HOWTO/UbuntuFlux](http://nix-dev.dudcore.net/HOWTO/UbuntuFlux)

Highly recommended to use this wiki instead of board, on account of better formatting options!

---

### Post by Gherald on 2005-07-28
[QUOTE=dud]This HOWTO can be in a more digestable wiki format over at 
[http://nix-dev.dudcore.net/HOWTO/UbuntuFlux](http://nix-dev.dudcore.net/HOWTO/UbuntuFlux)

Highly recommended to use this wiki instead of board, on account of better formatting options![/QUOTE]
Erm... that is one of the ugliest wikis I have ever seen... but ok.


I am looking for a guide to installing fluxbox 0.9.13 on hoary

0.9.13 has *huge* improvements over earlier versions, if you were unaware.

I am certainly willing to compile it manually, but I need the correct version of libstdc++ etc ...

Can anyone point me to a guide on "mixing software branches" so I cat get the libraries I need for the compile, while keeping hoary for the rest of the system ?  This would be fairly straightforward under [a certain other distribution](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=3).

---

### Post by dud on 2005-07-28
Always nice to start a request with an insult hehe... O_o

Anyhow, try looking into [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by bennyfactor on 2005-07-31
Hey, I used your tutorial. And after following everything, when I type startxdm at the console, I go to a screen with a gui login prompt (and a debian logo). After logging in, the screen goes black, and then back to the login screen.

I'm not sure how to proceed. I would like to mention that I had to create the directory ~/.fluxbox/ as well as the file ~/.xsession . 

Also, I even went through and redid all the sudo apt-get install commands to make sure I didn't miss some package or something, and I didn't. Any ideas on what I need to do?

Edit: Found the problem! It's exec, not Exec as you have listed as what to put into .xsession . I thought having a capital letter in a unix command looked kinda funny...

---

### Post by dud on 2005-07-31
[QUOTE=bennyfactor]Hey, I used your tutorial. And after following everything, when I type startxdm at the console, I go to a screen with a gui login prompt (and a debian logo). After logging in, the screen goes black, and then back to the login screen.

I'm not sure how to proceed. I would like to mention that I had to create the directory ~/.fluxbox/ as well as the file ~/.xsession . 

Also, I even went through and redid all the sudo apt-get install commands to make sure I didn't miss some package or something, and I didn't. Any ideas on what I need to do?

Edit: Found the problem! It's exec, not Exec as you have listed as what to put into .xsession . I thought having a capital letter in a unix command looked kinda funny...[/QUOTE]
 Oh, thanks a lot for figuring that one out! :D
Must have slipped my mind, you're very right about non-capitalizing exec.

My first thought was your video drivers being setup wrong.

I'll be sure to update the guide, thats excellent mate...

EDIT: BTW, apart from that, how did you like the guide? :)

---

