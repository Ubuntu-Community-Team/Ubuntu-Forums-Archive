---
title: "HOWTO: Get Plugins to work in Opera 8.50"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by cowlip on 2005-10-14
Hi, the etch deb that Opera has doesn't have all the opera-motif-wrappers, so plugins won't work.  Make sure you have that Breezy/etch deb installed beforehand.

So go to opera.com/download and check "download in .tar.gz". Extract it. 

cd opera-8.50-20050916.5-shared-qt.i386-en/plugins/ 

then do this in the terminal:

sudo mv operamotifwrapper-* /usr/lib/opera/8.50-20050916.6/plugins/ 

then do this:

sudo apt-get install openmotif libmotif3 lesstif2 motif-clients

and the plugin warning dialog should go away

---

### Post by laltopi on 2005-10-14
Can you also post howto get opera in the first place?

---

### Post by cowlip on 2005-10-14
OK, well I would just add this to /etc/apt/sources.list with nano

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch nonfree

And then sudo apt-get install opera

---

### Post by Roybotnik on 2005-10-15
Hi there, dunno if this is related or not but is there a way to use the mplayer plugin in opera?  I followed this guide but im not sure what exactly it was supposed to do =).  I would rather use opera than firefox since firefox crashes so much, but alas I have no multimedia playback for it.  Also btw, when I tried apt-getting openmotif and motifclients, the packages weren't found(I have all the repos enabled).

---

### Post by cowlip on 2005-10-15
[QUOTE=Roybotnik]Hi there, dunno if this is related or not but is there a way to use the mplayer plugin in opera?  I followed this guide but im not sure what exactly it was supposed to do =).  I would rather use opera than firefox since firefox crashes so much, but alas I have no multimedia playback for it.  Also btw, when I tried apt-getting openmotif and motifclients, the packages weren't found(I have all the repos enabled).[/QUOTE]

yes they should have a dash between them...

also it's because people in the breezy development forum said that an opera plugin warning never went away, so flash et al wouldn't work.

(i don't know about mplayer)

---

### Post by Roybotnik on 2005-10-15
[QUOTE=cowlip]yes they should have a dash between them...

also it's because people in the breezy development forum said that an opera plugin warning never went away, so flash et al wouldn't work.

(i don't know about mplayer)[/QUOTE]

Hmm.  Well flash and adobe reader seem to be working, but none of my other mozilla/firefox plugins do(mplayer, java).   Also I was able to get motif-clients put putting a dash in...but openmotif can't be found(also tried searching for open motif in synaptic, no luck).

---

### Post by phend-one on 2005-10-16
What's this "breezy etch deb" you are referring to? I'm not catching it. :confused:

---

### Post by cowlip on 2005-10-17
[QUOTE=phend-one]What's this "breezy etch deb" you are referring to? I'm not catching it. :confused:[/QUOTE]
Well, the breezy .deb seems to be the one for a Debian version called "etch"

if plugins are working ok, then you don't need to worry abou this post :)  Java is a separate issue, though.

---

### Post by phend-one on 2005-10-17
Oh, you mean the file that you download using the dropdown box on the Opera.com website?

"opera_8.50-20050916.6-shared-qt_en_etch_i386.deb"

I can't install Opera using the above repository. Is it down? It seems opera.com is down as well? Maybe it's just my connection?


I have both:
"opera_8.50-20050916.6-shared-qt_en_etch_i386.deb"
"opera-8.50-20050916.6-shared-qt.i386-en.tar.gz"

but when I try to: "sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb", it gives me a bunch of errors saying there's some stuff missing and the installation is aborted?

Any help on this?

---

### Post by Lars A E on 2005-10-17
try the static deb-package. It will not give you any trouble.

---

### Post by cowlip on 2005-10-17
Yeah opera.com was down for me too...

---

### Post by JulesH on 2005-10-17
Well, I tried to get the static 'etch' on Opera ftp site but it isn't there. Where has anyone got this from? Opera http site doesn't have it, at least as far as I can se....

Jules

---

### Post by Lars A E on 2005-10-17
[QUOTE=JulesH]Well, I tried to get the static 'etch' on Opera ftp site but it isn't there. Where has anyone got this from? Opera http site doesn't have it, at least as far as I can se....

Jules[/QUOTE]

Goto [http://www.opera.com/download/]("http://www.opera.com/download/") and choose "Other/Static DEB" in the distro menu.

---

### Post by Roybotnik on 2005-10-17
Hmm, well I followed this guide because I thought it might make my firefox plugins work in opera (since it supports them but they just weren't working).  Unfortunately, now all I get when I start up is a window saying I need to reinstall motif.  I didn't have that problem before following this guide o_O.  Also as I said previously...can't find any 'openmotif' package.....

---

### Post by desperado666 on 2005-10-17
[http://ubuntuforums.org/showthread.php?t=74667](http://ubuntuforums.org/showthread.php?t=74667)

This Howto should be made sticky

---

### Post by muszek on 2005-10-17
> 
sudo apt-get install openmotif libmotif3 lesstif2 motif-clients

E: Couldn't find package openmotif

which repository should I add?

EDIT: howto from the previous post (#15) worked for me.

---

### Post by phend-one on 2005-10-18
^Might be in Universe or Multiverse.

I just uncommented them in /etc/X11/xorg.conf

Make sure you do a "sudo apt-get update" after you enable the repository.

---

### Post by lognok on 2005-10-19
sudo apt-get install openmotif libmotif3 lesstif2 motif-clients

results in: Couldn't find package openmotif

instead remove openmotif and try again.

sudo apt-get install libmotif3 lesstif2 motif-clients

this works for me. Opera opens op without motif-plugin error, but now the text in the menus are all messed up, they look like something that belongs in XP....

---

### Post by lognok on 2005-10-19
forgot to tell that I use the static version of opera. The etch version will give a motif-error at start-up despite 'sudo apt-get install libmotif3 lesstif2 motif-clients'. Cheers :)

---

### Post by cowlip on 2005-10-19
OK well I'm sorry, all I know is it did work for me

---

### Post by lognok on 2005-10-19
No don't be sorry, it works for me as well, just had to do a little tweeking to get there, but now I've got Java and Flash running and it's great.

Thanks....

---

### Post by mcpish on 2005-10-20
has anyone been able to get mplayer plugin working?  I got Flash and Java working thanks to the advice here.

So far I love Opera, much faster than Firefox

---

### Post by mcpish on 2005-10-20
has anyone been able to get mplayer plugin working?  I got Flash and Java working thanks to the advice here.

So far I love Opera, much faster than Firefox

---

### Post by nrwilk on 2005-11-21
[QUOTE=mcpish]has anyone been able to get mplayer plugin working?  I got Flash and Java working thanks to the advice here.

So far I love Opera, much faster than Firefox[/QUOTE]
I'd like to know too.  I just tried it, and I like it a lot better than firefox (which is crazy, because I'm a big firefox user).

---

### Post by Rob2687 on 2005-11-22
Doesn't seem to work on 8.51 :(

---

### Post by Alpha_toxic on 2005-11-24
Oddly enough it worked for me too, but I havn't time yet to install java so perhaps there will be more problems there. But for now it works, lets hope it stays that way[-o<

---

### Post by Mark76 on 2006-02-21
> Hi, the etch deb that Opera has doesn't have all the opera-motif-wrappers, so plugins won't work. Make sure you have that Breezy/etch deb installed beforehand.

So go to opera.com/download and check "download in .tar.gz". Extract it.

cd opera-8.50-20050916.5-shared-qt.i386-en/plugins/ 

Where exactly does that last bit go?
:confused:

---

### Post by mechatronic on 2006-04-09
Hhm, It doesn't work with Opera 8.54. I had solved it before in FC but now when I come to Ubuntu, I've forgot it. :)
So I cant use plug-in with Opera. :-(

---

