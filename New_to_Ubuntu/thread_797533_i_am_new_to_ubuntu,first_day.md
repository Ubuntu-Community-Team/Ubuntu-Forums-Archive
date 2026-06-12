---
title: "i am new to ubuntu,first day"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by mchokoelle on 2008-05-17
Hi,i want to ask a simple,yet hard question.How can i play games and specialy,how can i play the game priston tale?plz just tell me what to klick,and not to explain,because i am just 10 and i wont understand a word of what you are talking.I will be very thankful and i will do as much as i can to return the favor.

---

### Post by iKevin on 2008-05-17
Hi There 

Welcome to ubuntu!  I don't play this game but, as far as I can remember, this is a DirectX game.  You may be able to run that game under wine.  I am sure someone else will come along and post a better answer regarding wine emulation and DirectX.

---

### Post by mchokoelle on 2008-05-17
Hi,i want to ask a simple,yet hard question.How can i play games and specialy,how can i play the game priston tale?plz just tell me what to klick and download,but dont explain,because i am just 10 and i wont understand a word of what you are talking.I will be very thankful and i will do as much as i can to return the favor.

---

### Post by Bloch on 2008-05-17
Hi Mchokoelle;

Priston Tale is a game designed for a computer with Microsoft Windows. Basically there are 3 common types of computers:
Microsoft windows
Apple Mac OS X
Ubuntu and other Linux 

Games and other stuff that work on one generally don't work on another. 

The Xbox and PLayStation are also computers. They are specially made to play games.

Ubuntu has some games made for it. If you want to install Planet Penguin Racer or glTron come back and ask again and I or someone else will reply.

---

### Post by jbrown96 on 2008-05-17
Stop trolling. Posting the same question multiple times isn't going to help. Wine is the program you're looking for, available in synaptic, but it doesn't look like its supported

---

### Post by hyper_ch on 2008-05-17
jbrown96:
Posting in multiple forums isn't trolling....

However posting the same question in multiple forums doesn't help.

As it's your first day with ubuntu, you should first have some reading to understand it a bit more.... star here

[http://www.psychocats.net](http://www.psychocats.net)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

That should give you a few clues for now.

---

### Post by Canis familiaris on 2008-05-17
Well there are lots of Open SOurce games like Nexuiz, OpenArena, etc. in Ubuntu. You can install them using Add/Remove.
Also using Add/Remove install wine. Many games can pretty well in WINE especially Half Life series run exceptionally well. 
To know Games working you could google search: <GAME NAME> + WINE appdb.
If it is Platinum/Gold then you would be able to play it easily.
For Games which do not run in WINE try [Cedega]("http://www.cedega.com/") or [Crossover Games]("http://www.codeweavers.com/products/cxgames/")
Keep in mind both are commercial solutions and you have to pay for them. WINE is free though.
Happy Gaming!:guitar:

---

### Post by Victormd on 2008-05-17
Well, trying to keep it simple...
Don't expect to run games designed for windows under ubuntu. There is a program for ubuntu called WINE that can be used to run some windows programs/games and there is a site for WINE with a list of programs that will work. Unfortunately, Priston Tale is listed as "garbage" which means that it won't work with ubuntu. You can find the list [here]("http://appdb.winehq.org/") and as for Priston tale, [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2597") are the ratings under WINE.

There are other alternatives to do this, such as, using Virtualbox, but that might get a bit complicated. Let us know if you want to give it a shot and we can help...

---

### Post by xjgnsdof on 2008-05-17
I'm a gamer, and I just dual boot into Windows for the graphics-intensive games that I like to play; there's no way Crysis will run in Ubuntu. Running games in WINE is far too technical for a noob like yourself; hell, I can barely figure it out, and I've been using Ubuntu for a year. Besides, it takes less time to boot into XP, especially if you ran your installation disc through nLite before installing.

Playing PSX ROMs through PCSX is quite simple: add it from Synaptic or "Add/Remove" (preferably the latter), plug in your controller, and get going. It's an easy way to get started with gaming.

I heard that you can play Call of Duty 4; you're going to have to Google the instructions for that, though. Again, with hard drives as big and cheap as they are, you might as well just dual-boot.

---

### Post by mchokoelle on 2008-05-17
well if you have time to help me,we can talk in local chat(since i dont know how to install skype or messenger or anything else,but thats another thing)tell me the name of the site that holds a local chat...lets just say yahoo, and just tell me what to klick or download.If you dont have time,then lets just try to talk trough here.

---

### Post by BlackDragonBE on 2008-05-17
Hi there,

I'm afraid it doesn't work in ubuntu, I checked wine's application database and it doesn't run very well. (rated as garbage)

---

### Post by PmDematagoda on 2008-05-17
At mchokoelle:- Please do not start duplicate threads on the same issue/topic, just one thread in the appropriate section will be more than enough.

---

### Post by Bloch on 2008-05-17
Cut the kid some slack - he/she is only 10.

At least I hope you're not pretending to be 10 just to get help mchokoelle. That would be a mean trick.

---

### Post by Victormd on 2008-05-17
> **mchokoelle said:**
> well if you have time to help me,we can talk in local chat(since i dont know how to install skype or messenger or anything else,but thats another thing)tell me the name of the site that holds a local chat...lets just say yahoo, and just tell me what to klick or download.If you dont have time,then lets just try to talk trough here.

I guess it's better through here, that way everyone can help.
First we need to know whether virtualbox will work, or if you'll need to dual-boot.

How 3D intensive are the graphics in the game, do you know?

If the game requires 3D resources, than virtualbox won't work, and you'll need to dual-boot. Either way, you will need a licensed Windows installation CD.

One thing I noticed is that the game was tested under an older version of WINE and you might want to try to install with the newer version before doing anything else (this would be the quickest). If so, lets start with that.
1. Open the terminal and copy and paste the following codes
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
```
sudo apt-get update
```
```
sudo apt-get install wine
```
Now you can try to install your game by opening the CD and double clicking on the setup.exe or browse to the folder with the installation and double-click the installation file. This should start the install.

You can get some helpful information [here]("http://www.winehq.org/site/howto")

---

### Post by mchokoelle on 2008-05-17
but first,i need to download the virtualbox,right?sorry for the dumb question,but can you give me a link?

---

### Post by hyper_ch on 2008-05-17
mchokeoelle:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Victormd on 2008-05-17
> **mchokoelle said:**
> but first,i need to download the virtualbox,right?sorry for the dumb question,but can you give me a link?

Yes, but my suggestion is to try with WINE first because it's faster (and you'll have 3D support).

If that doesn't work, then use virtualbox but keep in mind that you won't have full resources of your graphics card...

If you finally decide to go with virtualbox, you can download it [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by mchokoelle on 2008-05-17
what is platform?is it means the that you need to put the version you corrently use?if so,how can i know what version i use?my big brother installed ubuntu,and then he have gone on a vacacion,witch means that i am alone.

---

### Post by Victormd on 2008-05-17
You can find out the version by opening the terminal window and typing
```
cat /etc/issue
```

---

### Post by mchokoelle on 2008-05-17
Debian GNU/Linux 4.0 \n \l
so witch do i need to klick?i got to go sleep soon,so we might talk tomorrow,is that ok?

---

### Post by Victormd on 2008-05-17
then you would download the "debian 4.0 i386"
Do you have a Windows CD? If not, then virtualbox will not do you any good...

---

### Post by mchokoelle on 2008-05-18
i might not have the disk.but why do  you need the disk?

---

### Post by Sef on 2008-05-18
> i might not have the disk.but why do you need the disk? 

To make a virtualbox with Windows, you need the CD.

---

### Post by mchokoelle on 2008-05-18
does it means that i need to format the computer?or when i turn on the computer,will it be more complicated???if i download virtualbox,will it wreck my computer???these questions are very important,beacuse this computer is important for my dad because he is working with this computer and it have very valuable information.

---

### Post by mchokoelle on 2008-05-18
i think i know where is  the windows disk.but it is far away and i am not sure if i can get it.anyway,why do you need the disk???

---

### Post by mchokoelle on 2008-05-18
oops,sorry,i meant is it gonna harm the computer?

---

### Post by Victormd on 2008-05-18
> **mchokoelle said:**
> oops,sorry,i meant is it gonna harm the computer?

Virtual box will not harm your computer (considering you follow all the installation instructions correctly).
You will need anywhere from 4 to 8Gb free HD space and the Windows CD.
After you install Virtualbox, you will create a "virtual HD" to which you will install a "virtual windows", that way, you'll be able to run Windows as a program inside ubuntu, so no:
1. you will not have to format your HD;
2. it will not harm your computer (considering you follow all the installation instructions correctly); and
3. it will take a while for it to be installed (~1hr)

Did you ever try Wine? This will be much faster and easier (considering it works with the newer version)...

---

### Post by mchokoelle on 2008-05-18
well...i can get the disk,my brother returned erlier,but he wont help me with ubuntu(cant explain you now)but now,i can get into his apartment and get the disk,but only in one condicion:that i wont screw up the computer
if i screw up........

---

### Post by mchokoelle on 2008-05-20
wine? does it needs windows cd???i have the cd,but i cant get it.i can have the cd after 3 days or more.

---

