---
title: "A very simple nessus installation"
date: 2005-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by harman on 2005-04-17
Hi All,

After searching for nessus in this forum, and finding nothing concrete, i found nesseus installation very simple :

1. sudo apt-get install nessusd nessus nessus-plugins

During the installation, it will ask you to create a Certificate, accept defaults, change location, state, etc if you like.

2. sudo update-rc.d nessusd defualts

3. /etc/init.d/nessusd start

4. sudo nessus-adduser

Now, when you come to "policy for this user" read the man page for nessus-adduser. I wanted to be able to scan any host i please so i said "default accept". As i said, read man nessus-adduser

5. /etc/init.d/nessud restart

6. Go a shell, and type "nessus"

7. If you do not know how to use the window that pops up, well this little guide is not for you  :) 

HTH
Harman

---

### Post by Mizike789 on 2005-05-03
Hi!  I registered just to say "thank you" for posting this guide.

Thank you.

 :)

---

### Post by jiyuu0 on 2005-05-04
sudo update-rc.d nessusd defaults

i tried restart... nessusd doesn't start by default...
any idea?

---

### Post by jiyuu0 on 2005-05-04
found the solution

sudo ln -s /etc/init.d/nessusd /etc/rc2.d/S20nessusd

---

### Post by seekyrr on 2005-06-08
Thanks for the nessus install tips.  I do have one follow up question.

I get this error trying to register my server.

sudo nessus-fetch --register XXXXXXXXXXXXXXXXXX

Unknown error while decoding HTTP response  (http error code = 1208493298)


Any help would be much appreciated.

John

EDIT.

Still got error when I tried again.  Rebooted and did update command.  Now getting all the plugins. Seems fixed.

---

### Post by SkEaToN on 2005-06-09
i am ending in a loop trying to enter a login name and pass at "sudo nessus-adduser"

Login : test
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****


does anybody know why?

---

### Post by Nimefurahi on 2005-06-10
Harman,

Your instructions worked flawlessly for me. Thank you. Nessus is up and running.

After running Nessus against this Ubuntu system, I feel compelled to share an observation, and it's simply that, an observation. This comment is certainly not meant to "bash" other distributions. We have so many distributions and various "flavors" of Linux to choose from, all of which are superb and sport their various strengths and weaknesses. But I only want to share my smile with Nessus users of what initially appears to be a rock-solid Ubuntu (Debian-flavored) distribution...

There is a certain irony in that so many of the "net security" distributions seem to display a certain disposition toward vulnerability. I know. It sounds incredible, but (and please forgive me for posting names of truely superb distributions) there are some like Auditor, Operator, Knoppix STD, Phlak, LAS, and so many others that seem to fail my Nessus test of impenetrabilty. Honest! So many distributions meant to serve network security seem to have beaucoup port flaws of their own. I'm dumbfounded! They fail my Nessus expectations. For me it's like wearing rain boots with holes in their soles. I might as well go barefooted. (May I add at this point that if users are looking for a "hardened" Linux distribution, you may want to check out Trustix, or just stay right here with Ubuntu).

Not so with Ubuntu. I first fell in love with it's idealogy, it's universality, its community and humanism. I wasn't necessarily looking for a Debian-based Linux distribution built like the Rock of Gibraltar, but this "out-of-the-box" Ubuntu distro scored the highest results by my criterion when scanned with Nessus. Can you believe it!?

Kudos to the Ubuntu development team. Hackers, beware of my Ubuntu!

Once again Harman, thanks for making the Nessus installation so simple.

Nimefurahi

---

### Post by Wardhog on 2005-07-31
[QUOTE=Nimefurahi]
 this "out-of-the-box" Ubuntu distro scored the highest results by my criterion when scanned with Nessus. [/QUOTE]

Could you share with us what you found?  Ie.  What were some potentially unwise default settings, what was good?  Are there any potentially exploitable services running by default?

I'm interested in this, but haven't yet got off my butt to use Nessus.

---

### Post by Res on 2005-09-23
Hi, I am  new to Ubuntu but I have read many posting regarding Nessus and I was able to install it on my own. However I can not get it to start automatically when I reboot. I tried using "sudo ln -s /etc/init.d/nessusd /etc/rc2.d/S20nessusd
" and that command run fine but when I reboot, nessusd is still not running. I have to manually start it before I can use the Nessus client.

I am running Nessus 2.2.5 (I have to install this with the "sh nessus.sh" command -- found at Nessus website, because using apt-get install nessus only installed an older version (version 2.2.3, which has issues with plugins updates)

Would appreciate any help. Thanks.


- Res

---

### Post by eifersucht on 2005-09-23
i got this with the first instruction (sudo apt-get install nessusd nessus nessus-plugins)

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and i dont know what is it or how to fix it

---

### Post by HercuLeeZ on 2005-09-24
[QUOTE=harman]Hi All,

After searching for nessus in this forum, and finding nothing concrete, i found nesseus installation very simple :

1. sudo apt-get install nessusd nessus nessus-plugins

During the installation, it will ask you to create a Certificate, accept defaults, change location, state, etc if you like.

2. sudo update-rc.d nessusd defualts

3. /etc/init.d/nessusd start

4. sudo nessus-adduser

Now, when you come to "policy for this user" read the man page for nessus-adduser. I wanted to be able to scan any host i please so i said "default accept". As i said, read man nessus-adduser

5. /etc/init.d/nessud restart

6. Go a shell, and type "nessus"

7. If you do not know how to use the window that pops up, well this little guide is not for you  :) 

HTH
Harman[/QUOTE]
 Hey there,

Great thead, awesome idea harman.

I encountered a couple of spellinging mistakes in your commands, so I just wanted to post the command sequence I used, just to ensure the absolute beginner can get nessus on there machine.  They are as follows:

[B]$ sudo apt-get install nessusd nessus nessus-plugins
$ sudo update-rc.d nessusd defaults
$ sudo  /etc/init.d/nessusd start
$ sudo nessus-adduser
$ sudo /etc/init.d/nessusd restart
$ nessus[/B]

Thanks again harman, keep up the good work.

Herc

---

### Post by majikstreet on 2005-09-24
[QUOTE=eifersucht]i got this with the first instruction (sudo apt-get install nessusd nessus nessus-plugins)

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and i dont know what is it or how to fix it[/QUOTE]
 This basically means that you stopped another installation (apt-get) and you just have to do 
```

sudo dpkg --configure -a

```

and then re-run sudo apt-get ........

hope that works for you.. (never used nessus)

---

### Post by stanz on 2007-12-11
> **SkEaToN said:**
> i am ending in a loop trying to enter a login name and pass at "sudo nessus-adduser"

Login : test
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****


does anybody know why?

Being new to nessus myself--here's what I found so far....
I ran into the same--but as the poster said "read the man pages".
```
man nessus-adduser
```> Authentification type: The  authentification  method  the  client will use. The recommended
 method is &#8220;cipher&#8221;. However, if you compiled nessusd  without the cipher support or if you are using a Nessus  client which does not support the cipher layer, you&#8217;ll have to use &#8220;plaintext&#8221;

Also, I find now:
> 
Login : test
 Authentication (pass/cert) [pass] :

IS asking for password OR certificate, the [pass] is default-accept by pressing enter.
This is what I did without finishing **R**eading**T**he**F**ine**M**anual.

I hope this helps.  :guitar:

---

### Post by OneTrueOverlord on 2008-12-08
Thanks, this helps a lot:guitar:

---

### Post by ambigiousop on 2009-06-01
Does anybody have experience with installing a good Nessus web interface? There are a bunch out there like in the link below bit was wondering if anybody prefers one over the other.

[http://inprotect.sourceforge.net/](http://inprotect.sourceforge.net/)

---

### Post by ritm0o on 2009-06-05
> **SkEaToN said:**
> i am ending in a loop trying to enter a login name and pass at "sudo nessus-adduser"

Login : test
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****
Authentication (pass/cert) [pass] : *****


does anybody know why?
ok
now ur login id : xyz
Authentication (pass/cert) [pass]: now u press CTRL +D and u see like this
Authentication (pass/cert) [pass] : Login password : NOW u put password
and retype password 
then window like this
Login             :xyz
Password        : ****
DN                : 
Rules             : 

Is that ok ? (y/n)  now press (y)
user added 
=D>DONE

---

### Post by ritm0o on 2009-06-05
> **stanz said:**
> Being new to nessus myself--here's what I found so far....
I ran into the same--but as the poster said "read the man pages".
```
man nessus-adduser
```Also, I find now:

IS asking for password OR certificate, the [pass] is default-accept by pressing enter.
This is what I did without finishing **R**eading**T**he**F**ine**M**anual.

I hope this helps.  :guitar:
Authentication (pass/cert) [pass] :  			 		NOW PRESS CTRL +D ur problem solve\\:D/

---

### Post by piju on 2009-06-30
> **jiyuu0 said:**
> sudo update-rc.d nessusd defaults

i tried restart... nessusd doesn't start by default...
any idea?

or you can use sysv-rc-conf to select for auto start on selected run level

---

### Post by Merc248 on 2009-07-26
I don't know if anyone's noticed, but Nessus is NOT free for those looking to deploy this for their work.  I work in a small research lab and had to figure out what the hell to do with Nessus, since we only had the 30 day trial.  Well, what I found out was that there's a fork of Nessus called OpenVAS which does the same thing, except it's totally open source and they provide free upgrades for whatever purpose you might have.  They forked a few years ago, right after Tenable decided to make Nessus a totally closed source application.

LINK: [http://www.openvas.org/](http://www.openvas.org/)

---

