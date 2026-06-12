---
title: "need some help"
date: 2007-11-04
forum: Programming Talk
---

### Post by hockey97 on 2007-11-04
Hi I followed a tutorial to config my postfix and get a e-mail system up and running. in those steps , their was one step asking to mod the rc.config file which I didn't have so I google rc.config  and I got sysv-rc-conf  ubuntu package and after it installed my computer soon forzed, I then restarted my computer and now when ubuntu 7.10 starts to load well it shows the ubuntu logo and a loading bar, and within 3 or 5 sec I then get loaded into busybox text interface. 

I don't know how to get my computer system back and up again.

is their a way to turn it off?  I was told their is a way to turn it off  

any idea how I could get it back to normal??

---

### Post by CptPicard on 2007-11-04
Great going, you hosed the machine's init system by installing some variant Ubuntu doesn't use -- moral: don't blindly follow docs that may have been written for some other distribution ;)

Anyway, it's well possible you're FUBAR, but you should try to first get rid of the package and reinstall Ubuntu's own init scripts, which seem to live in the "initscripts" package.

Now, how you're going to get a shell on that box is an interesting question on its own... can you do this from the busybox one?

---

### Post by hockey97 on 2007-11-04
lol wow, don't scare me lol hahah.

well it downloaded the package from ubuntu packages.com google ubuntu packages it's the frist site that comes up.

the tutorial was based on ubuntu 7.10 - 7.04 

well just right now I can only load into busybox. 

that's really it I can't go pass that when I get a ubuntu graphic with a loading bar the loading bar stops like 1 inch from where that orange stuff starts in the loading bar.

then popup's a text heading saying busybox 1.1.7 ubuntu 7.10 

I don't really know what to do, but was told that thier is a way to trun busybox off and boot into the desktop, but they didn't know how but heard that you can.

I don't even know if the package installed yet, it was like past half-way done where the installing stoped and the computer froze.

So I did a warm boot  and that's what I get and still am getting that,

thank god I had windows xp installed and had my comptuer system dual boot.
otherwise I would not be able to make these postings.

I don't know anything really about busybox I mean commandwise.
I know it's a embeded utility but like 70 utilities build it in.

so I would need you to tell me the commands if you want me to do anything in that interface thing. 

Urrghh

---

### Post by hockey97 on 2007-11-04
is their a way where I can download the inti files from the internet and have it automaticly installed so it overrides the new changes???

I don't understand how I got busybox loaded up or booted up.

---

### Post by FXEF on 2007-11-04
Busybox is an utility tool set for embedded Linux. You don't need busybox with Ubuntu. You need to un-install busybox. I'm really not sure what's booting up on your system. If you can not un-install busybox, the simplest solution may be to re-install Ubuntu.

Busybox web site:  [http://www.busybox.net](http://www.busybox.net)

---

### Post by hockey97 on 2007-11-04
wel when ubuntu 7.10 starts to boot you know when the loading bar and the ubuntu logo shows while booting or loading ubuntu.

well when that shows for like 4 or 5 secs the loading bar stops and their is some delay and then the loading bar and logo thing dissappears and then comes up some text saying busybox and ubuntu 7.10 and ash 
.

then I see a text interface where I can type help for commands  I don't see sudo, I see wget command, I can download stuff.

I swear after I go thought this stuff, I will smack that person that had that tutorial ,  lol :)

---

### Post by geirha on 2007-11-05
Do you happen to have a link to the tutorial you followed?

---

### Post by hockey97 on 2007-11-05
yes I have a link the problem it's on the ubuntu server, lol I am right now running windows xp, I have the setup in a dual boot of ubuntu and windows xp.

the ubunut it only loads busybox I can't get pased that to my ubuntu system.

so for me to really give what site it was I can't give a link or anything right now.

but I rember finding it in a google search for mail server system.

or maybe I searched for postfix mail server system.

I even tried finding the website again using windows xp and faild.

I also have done alot of work on my website on ubuntu server.

so if I have to reinstall ubuntu urrgh!! lol 

if I do have to reinstall can't I just install the new files and replace the recent ones that been last changed??

urrgghhh!!! lol:mad: lol

---

### Post by hockey97 on 2007-11-06
Do you think I could downloaad software to mount my ubuntu file system and then manually delete the files or somthing?

---

### Post by smartbei on 2007-11-07
Yes, you could download [http://www.fs-driver.org/](http://www.fs-driver.org/)

This lets you access ext2/3 filesystems from windows. Careful when deleting the files though.

You could also use a livecd.

---

### Post by hockey97 on 2007-11-07
Do you think by using that I could use sudo or the package manger.

If so then I could just remove the last package I downloaded and installed, otherwise it  will get messy, lol .

---

### Post by hockey97 on 2007-11-07
Any Ideas on how to delete the files or packages??

I man using windows and did install that software suggested in te above posts.

I now have access to the filesystem of the ubuntu server thing. Now need to know how to delete the files could I do it with the terminal or the package manager??

---

### Post by CptPicard on 2007-11-07
You can't run the package manager without booting into Linux... and I can't really think of a way to run the manager from some kind of an external installation.. it's probably doable but would be complex.

Your best bet is probably backing up your data and reinstalling, it's quicker. Even better if you've got your /home on a separate partition.. otherwise you could try doing an install on top of what you've got already, but just make sure you don't erase your partitions -- just put the stuff on top of what is already there. Make backups anyway.

---

### Post by hockey97 on 2007-11-08
I have /home on the same partition as ubuntu.

ok well  I just might only save my webpages I will copy it on my windows xp, and reinstall the whole thing again.

urrgghhh I hate this part lol.

ok well I am going to reinstall it

and just take all the website stuff on my windows xp and the later after the reinstallation I will then transfer it.

I only have ubuntu 6.10 on a cd.

ok well I am on my way to the reinstallation.

---

