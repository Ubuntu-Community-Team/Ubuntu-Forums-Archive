---
title: "iTunes?"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-07
Is itunes supported by Ubuntu?

If so,where can I get it?

If not, is there a program with the same functionality?

---

### Post by mcduck on 2012-10-07
No, it's not. Apple only makes versions of iTunes for Windows and OS X.

...and you are not going to find any program with *exactly the same* functionality. However there are plenty of different music players available, and even the one installed by default (Rhythmbox or Banshee, depending on your Ubuntu version) is a decent one. If you are looking for some specific features the default application doesn't have, just ask and people should be able to recommend you another application.

---

### Post by will1982 on 2012-10-07
Ah, yes, Rythmbox.

Thanks for the help :D

Edit: Will it recognize my Ipod?

---

### Post by 1clue on 2012-10-07
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by mcduck on 2012-10-07
> **will1982 said:**
> Ah, yes, Rythmbox.

Thanks for the help :D

Edit: Will it recognize my Ipod?

yes, it should work just fine with your iPod. At least it works for most models.

---

### Post by DuckHook on 2012-10-07
Wine "works" with a bronze rating, which means that iTunes is basically unworkable. You would be pulling your hair out try to make it work and it would crash with regular frequency. The only method that worked for me was running iTunes from Windows inside a VM. It is literally the only program that I still have Windows installed for. Once I upgrade to an Android device, I will be able rid myself of the last vestiges of Windows.

> If not, is there a program with the same functionality?

Older Apple OSes are supported better than new ones because the Linux-sphere has had more time to reverse-engineer the various system calls and tweak the drivers. Apple's strategy of continual upgrades makes newer iPods/iPhones very difficult to support. You can try a set of utilities from Paul McEnery that worked up to relatively recently. Not knowing your exact Apple OS it is impossible to tell what success you will have. McEnery's stuff can be added via PPA to your Ubuntu distro through:

[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

---

### Post by will1982 on 2012-10-07
Thanks for the great help everyone!

---

### Post by jingaling on 2012-10-07
If I were you I would run Windows in a VM (Virtual Machine)with iTunes installed that way. iTunes is notorious for not playing well with Ubuntu under WINE.

AS previously stated though, Rhythmbox/Banshee should be fine - I've used the both in the past and they're great. [Floola]("http://www.floola.com/home/") is usually my go to iPod manager though. It's available for all three OS's.

Jing

---

### Post by Pilot6 on 2012-10-07
iTunes works under Playonlinux quite well.

---

### Post by will1982 on 2012-10-07
> **Pilot6 said:**
> iTunes works under Playonlinux quite well.

I'll give it a try.

I just wanna load up my iPod and stuff. I have a Windows machine, so it's not critical or anything.

---

### Post by czgirb on 2012-10-08
> **Pilot6 said:**
> iTunes works under Playonlinux quite well.

For you ... maybe
For me! Sorry! it can not. Even the 7.x version.

My advice: it's better for us to stick with the compatible ones.
Rhythmbox, Banshee, Amarok, etc.

---

### Post by mike acker on 2012-10-08
the one I really like is MusicBee -- but that is Windows only

hopefully I'll get RDP working so I can just keep my windows box around and control it from my ubox

---

### Post by 1clue on 2012-10-08
Your rdp isn't just automatically working?

Linux has a great RDP client, IMO it's better than the Windows one.  I've never had to do anything with it to make it work.  You might want to investigate the command line options so you get a good screen size and shared folders.

---

### Post by josephmills on 2012-10-08
how to get Itunes 10 on Ubuntu 
go download itunes ten 

[Itunes 10 32bit](http://appldnld.apple.com/iTunes10/041-1633.20110607.FvP5t/iTunesSetup.exe)

[Itunes 10 64bit](http://appldnld.apple.com/iTunes10/041-1634.20110607.4EPY6/iTunes64Setup.exe)


open terminal add playonlinux 
```
sudo apt-get install playonlinux
```

after installed open it 

Now set it up (the auto prompt will tell you what to do)
[img]http://ubuntuforums.org/attachment.php?attachmentid=225269&stc=1&d=1349707045[/img]
after microsoft fonts are installed. You should be all set up and ready to install itunes 

Click on Install then multimedia, then make sure that testing is checked (see img)
[img]http://ubuntuforums.org/attachment.php?attachmentid=225270&stc=1&d=1349707045[/img]

[img]http://ubuntuforums.org/attachment.php?attachmentid=225271&stc=1&d=1349707045[/img]


Now follow the instructions that are on the page. it will lead to a part that asks you where the itunes.exe file is (the one that you downloaded above) Pick browse and go find that file then open it. (see pic) then press next. 


[img]http://ubuntuforums.org/attachment.php?attachmentid=225272&stc=1&d=1349707045[/img]


After pressing next a couple of times you will see a install options page. please make sure that you **UNCHECK** "Automatically update itunes and other applications" I also unchecked "Use Itunes as default application".press next 
Make sure that auto run is turned off for the next question. in fact you can press next till you get to the end. Then go have fun with itunes. 



[img]http://ubuntuforums.org/attachment.php?attachmentid=225273&stc=1&d=1349707045[/img]
hope this helps

---

