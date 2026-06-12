---
title: "Uninstall Ubuntu"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by redpepper on 2008-07-07
How do I uninstall Ubuntu Feisty Fawn. I want to go back to win XP Home.

---

### Post by overdrank on 2008-07-07
> **redpepper said:**
> How do I uninstall Ubuntu Feisty Fawn. I want to go back to win XP Home.

HI and this link can help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
What are the issues you are having with Ubuntu maybe we can help?

---

### Post by Dr Small on 2008-07-07
What problems were you having with Ubuntu? I am sure we would be more that happy to assist you with whatever difficulties you were encountering on Ubuntu.

But anyhow, there is no real "uninstall" for Ubuntu. You basically have to wipe the hard drive clean, or delete the linux partition.

---

### Post by neurostu on 2008-07-07
To remove ubuntu and install windows:
```

boot the windows install cd

```
then install!

Thats it!

---

### Post by Yuki_Nagato on 2008-07-07
If Windows is not currently on your computer, (and you want to start with a fresh Windows Installation) then run this program first:

_[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")_

It is the ultimate defragmentation program.  It turns your hard drive into one big government-proof zero.

(The defragmentation part was sarcasm.  DO NOT run DBAN as defragmentation as it will wipe your entire hard drive.)

---

### Post by Dr Small on 2008-07-07
[quote=Yuki_Nagato]Does a bit of advice sound fishy? Type "man XXX" to access the manual for the command in question.[/quote]
```
$ man dban
No manual entry for dban
```

Ok. Now I know your advice is fishy! :D

---

### Post by redpepper on 2008-07-08
The main issues:  I am not very comp. literate at all.  Not much ex. with command lines.  I just read part of the uninstall page and I like the idea of hiding the grub menu, having a security vault, and chaining two op. systems together.  So you all have talked me into keeping it.  

So here is the problem - In following the directions I had at the time when I first bought the computer (Dell XPS-410 @4300rpm) I wound up in the multi-verse, universe, restricted area at the command line and typed in a 4 line long coded widget in an attempt to down load plug-ins so the Totem movie player would work and instead created a glitch labeled "major failure of software management occurred".  In pressing the Esc. button during the boot process I re-installed back to factory settings and the glitch was gone.  

Now the print size on anything I read is very small as are the size of the boxes(drop-downs).  I need to enlarge the size of the print on boot-up at least two sizes bigger so it is readable. 

Also, the sound is now almost inaudible even with the volume control turned to max.  (also upon re-instillation).

Totem still wont work.  But the glitch is gone :) :guitar: :)

furthermore, I want to buy a Spanish speaking course and it is only compatible with Windows.  How will I install it without Windows??  (an overlay of some type??).

So - print, sound and Totem and the rest con come later.

This is why I wanted to dump feisty - but un-installing really sounds more difficult. 

Thanks for everybodys response and I will get back to you asap.

---

### Post by nothingspecial on 2008-07-08
Try a fresh install of Gutsy or Hardy.

---

### Post by ad_267 on 2008-07-08
> **redpepper said:**
> The main issues:  I am not very comp. literate at all.  Not much ex. with command lines.  I just read part of the uninstall page and I like the idea of hiding the grub menu, having a security vault, and chaining two op. systems together.  So you all have talked me into keeping it.  

So here is the problem - In following the directions I had at the time when I first bought the computer (Dell XPS-410 @4300rpm) I wound up in the multi-verse, universe, restricted area at the command line and typed in a 4 line long coded widget in an attempt to down load plug-ins so the Totem movie player would work and instead created a glitch labeled "major failure of software management occurred".  In pressing the Esc. button during the boot process I re-installed back to factory settings and the glitch was gone.  

Now the print size on anything I read is very small as are the size of the boxes(drop-downs).  I need to enlarge the size of the print on boot-up at least two sizes bigger so it is readable. 

Also, the sound is now almost inaudible even with the volume control turned to max.  (also upon re-instillation).

Totem still wont work.  But the glitch is gone :) :guitar: :)

furthermore, I want to buy a Spanish speaking course and it is only compatible with Windows.  How will I install it without Windows??  (an overlay of some type??).

So - print, sound and Totem and the rest con come later.

This is why I wanted to dump feisty - but un-installing really sounds more difficult. 

Thanks for everybodys response and I will get back to you asap.

Uninstalling isn't really difficult at all. If you put in the Windows install CD it should be able to just install over the whole drive which will remove Ubuntu. Make sure you back up any data you want to keep first.

It sounds like you went in a over your head there. You can easily enable repositories by going to Settings - Repositories in Synaptic Package Manager. To download nearly all of the plugins you need you can just install the ubuntu-restricted-extras package and totem should work fine.

To change the fonts size try going to System - Preferences - Appearance - Fonts and change the font sizes there.

To increase sound volume try going to Applications - Accessories - Terminal and run alsamixer and then use your arrow keys to move along and increase volumes.

What is the windows application you need to use? The program wine is used to run Windows applications in Linux. You can see if an application will work here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by aktiwers on 2008-07-08
For video I recommend VLC player.

Go to Applications = Add/remove
and search for: Vlc

Then mark it for installation.

For sound, I also say try alsamixer like suggested.. play with the different stuff in there(master, PCM, etc..) with your keyboard arrows.

For printer, look in System = Administration = Printing and see if it finds it there.

Also you might need codec for video and such. Go to Add/remove again and search for: restricted
Then install the "Ubuntu restricted extras" package and see if that fixes it

---

