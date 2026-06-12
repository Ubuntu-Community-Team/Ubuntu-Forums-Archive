---
title: "HOWTO: Find newer/more packages"
date: 2004-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by jayclark on 2004-10-29
I think we all want newer packges that have plenty of fixes and adds ons. Such as Gdesklets. A lot has happen in with Gdesklets since the version already in the depositories. Or just want to have the latest and the greatest. Go to 

[http://www1.apt-get.org/](http://www1.apt-get.org/) (its a search engine for depositories.) 

Click on- Search for a package

Select your arch for your pc. In my case for a Pentium 3 I choose i386.

Then search for the package you want.

Now we need to add the repository to you sources list.

Open the terminal and type sudo vi /etc/apt/sources.list 
You'll see some text with sources. I always add new sources one line below the last one. 
To do this type i, put to cursor to where you want the source at (it really dosen't matter where but as I said I perfer the below the last source)
Then add the soruce such as 

deb [http://j.portalier.free.fr/debian](http://j.portalier.free.fr/debian) testing main

Now press esc. Then type this to write and save the file :wq 
This will bring you back to the main console screen.

Now we need to get the package information off the server you can do this by sudo apt-get update or with synaptic by clicking reload. 

Now you have newer packages for that file you want or that package that you need. Have fun.

*Note some of these packages are bleeding edge and they could have bugs and might cause instability try to only use packages you know to be stable.

---

### Post by cacofonix on 2004-10-29
Thanks for the tip Jay :) I think the Pentium 3 is 686 processor

---

### Post by jayclark on 2004-10-29
Really? I always though it was i386. Learn something new everyday  :)

---

### Post by jdong on 2004-10-29
i686's are Pentium PROs and up. Check your **uname -a** output to be sure.

---

### Post by flygmaskin on 2004-10-29
Just remember that using unofficial repositories increases the risk of your system being borked.

---

### Post by jayclark on 2004-10-29
Thanks for pointing that out. I though I added that to the how to, I only use it for software packages such as gaim, wine, etc. I never use it to upgrade anything that deals with the inner layers of the os. Pentium 3's are i686. But as some say that i386 and i686 isn't a big difference when it comes to packages. I don't know, but I don't like to mix packages of different arch.

---

### Post by jdong on 2004-10-30
mixing arches has no bad side effects; the problems result when the .deb's are compiled against different library versions.

---

### Post by securitybreach on 2004-11-10
[QUOTE=jayclark]Pentium 3's are i686. But as some say that i386 and i686 isn't a big difference when it comes to packages. I don't know, but I don't like to mix packages of different arch.[/QUOTE]

I have a P3 1.13ghz and my uname -a lists : 
Linux securitybreach 2.6.8.1-3-[COLOR=Blue]386[/COLOR] #1 Tue Oct 12 12:41:57 BST 2004 [COLOR=DarkRed]i686[/COLOR] GNU/Linux. This seems odd to me.

---

### Post by allen on 2004-11-10
[QUOTE=securitybreach]I have a P3 1.13ghz and my uname -a lists : 
Linux securitybreach 2.6.8.1-3-[COLOR=Blue]386[/COLOR] #1 Tue Oct 12 12:41:57 BST 2004 [COLOR=DarkRed]i686[/COLOR] GNU/Linux. This seems odd to me.[/QUOTE]
 you are on a kernel compiled for i386 arch but are on an i686 processor. 

you can upgrade to i686 by typing...

sudo apt-get install linux-686 

... in the command line for minor (if any) speed improvements.

---

### Post by securitybreach on 2004-11-10
Thanx for the quick response

---

