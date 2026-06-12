---
title: "success !!! But :)"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by its_jon on 2008-08-16
After comming back to try Ubuntu several times over the past 5 year or so I have finally got an install that likes my PC and has got itself onto the net first time !

Plus...... I managed to solve problems straight away using the download managing system..... Well done everyone ! My penguin wings are starting to flap for the first time :)

Just one issue......

I have a terratec DMX 6fire sound card and front module.....

No sound unfortunatly..... I typed terratec into the package/driver download tool with no success (worked for nvidea though :) )... terratec dont provide a linux driver that I can see.

Can someone point me in the right direction please .... thanks and thanks everyone who offered help in the past ! :)

---

### Post by Shazaam on 2008-08-16
Looks like you have a fixable project in front of you. I found a few links that might help (should be portable to Ubuntu)....
[http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2005-03/1588.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2005-03/1588.html)
[http://alsa.opensrc.org/Envy24Control](http://alsa.opensrc.org/Envy24Control)
[http://linux.die.net/man/1/envy24control](http://linux.die.net/man/1/envy24control)
[http://lists.linuxaudio.org/pipermail/linux-audio-user/2003-February/002433.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2003-February/002433.html)
Here is a link from the opensuse forums about 5.1-
[http://forums.opensuse.org/archives/sf-archives/hardware/347247-terratec-dmx-6fire-24-96-a.html](http://forums.opensuse.org/archives/sf-archives/hardware/347247-terratec-dmx-6fire-24-96-a.html)

---

### Post by its_jon on 2008-08-16
Thanks for hunting those links out....

They all look as though they apply.... trouble is I don't have a clue how to apply the info or hunt out what is relative to my problem.

:oops:

The last major problem I had with Ubuntu was getting the dreaded sagem eagle/fast 800 modem to work..... It took a huge ammount of help from everyone ..... 

Is it possible that a driver may become available soon through the add/remove applications tool ? :s

---

### Post by Shazaam on 2008-08-16
You can use the Synaptic Package Manager to install alsa-tools (and the gui).  Envy24Control is part of alsa-tools.
You can probably not count on a linux driver unless the manufacturer writes one.

---

### Post by its_jon on 2008-08-16
cool .....

I installed the 

Envy24Control selections.....

How do I enable them now ?
...
.
.
.
.
thanks :)

---

### Post by its_jon on 2008-08-17
OK :)

I got the sound working after a reboot or two...... how I don't know.

so..... somethings working.... but not all the time.

I rebooted into ubuntu and the sound has gone again ..... I have not changed the sound settings at all as I was delighted with the result when it worked !.....

It now looks as though ubuntu is possibly loading the wrong drivers at times on boot.... 

how do I fix this ?]

thanks :)

---

### Post by billgoldberg on 2008-08-17
Try installing 

asoundconf-gtk

using synaptic, or if you want using the terminal

```
sudo apt-get install asoundconf-gtk
```

Hold down "alt + f2" and type

asoundconf-gtk

a little box shoud appear, see if you can select another sound card.

If you pick yours, the change will be immediate.

It's worth a shot.

---

### Post by its_jon on 2008-08-17
I installed (or activated ?) via the terminal 

sudo apt-get install asoundconf-gtk

typed my password - it appeared to install then
nothing happened with the sound.
then I typed alt F2 .... nothing happened again.
I then typed alt F2 in a terminal and got..... 5Q
 
5Q ???

no sound yet..... its odd though that it did work perfectly prior to my recent reboot...

---

### Post by its_jon on 2008-08-18
Maybe I ahave some mixer config wrong ?

in:-

system/preferences/sound

ALSA is selected for everything and in the "default mixer tracks" field my soundcard is selected -Terratek 6fires (ALSA Mixer)

Which device should be selected under that ?


And then in:-

applications/sound and video/

I have a selection of sound tools one bieng "Envy24 control" how should this be set ?

I think I have all the right stuff loaded into ubuntu but maybe ubuntu is not loading it at boot ?

---

### Post by its_jon on 2008-08-18
Fixed.... I hope :)

System/prefs/default soundcard

It was set to a sound card that is not actually installed ??

changing it fixed the issue......

As a web developer I have been used to a combination of notetab and windows commander / total commander with  ftp ability

I have already found Quanta which looks very good on first sight (need to make the interface a bit bigger though as my rez is high - cant find the setting)

I did install a grey windowed FTP gadget which is not to my tastes... can anyone recommend a better FTP thing ?

Looks like I'lll be starting to work on Linux :)

thanks for the help 

John
Scotland

---

### Post by cariboo on 2008-08-18
Their are several ftp clients in the repositories personally I use gftp-gtk, Ive also tried Filezilla, I like both of them but I find Filezilla a little bit busy. For a Windows Commander/Total Commander have a look at mc or gnome-commander. All are installable using Add/Remove Programs, Synaptic Package Manager and of course the command line.

Jim

---

### Post by Joeb454 on 2008-08-18
What's wrong with the plain old command-line ftp client ;)

---

### Post by its_jon on 2008-08-18
> **cariboo907 said:**
> Their are several ftp clients in the repositories personally I use gftp-gtk, Ive also tried Filezilla, I like both of them but I find Filezilla a little bit busy. For a Windows Commander/Total Commander have a look at mc or gnome-commander. All are installable using Add/Remove Programs, Synaptic Package Manager and of course the command line.

Jim

Thanks for the suggestions ... I will hunt them out.

As for the command line :) I have to hold my hands up, it's not my scene.
Although my first computer was an Acorn Electron running BBC Basic I missed out the tos/amiga/386/486 days and came back into win/95/98 so I only associate a command line with emergences.
Have been following Linux closely over the past years though.... Probably parallel with XP now in usability for someone like me and probably UBUNTU has a more intuitive learning curve for a complete newb!
I have always been fully aware of the power of Linux but its now that.....for me..... the Linux GNU etc community has picked up so much momentum M$ have no chance or rebounding after the Vista fiasco no matter how much money they throw at a successor.....

Having said all that:-

this is the only Linux install (many ubuntu attempts) that I have got fully working ! ...... IMHO the ability to jumpstart a Linux install by utilizing settings from a M$ installation appears to have been key to the success of my current UBUNTU OS..

Getting more manufacturers to discover the 'usability' of Ubuntu as a IMPROVEMENT over XP and supply (and promote) more modern pre configured Linux systems will be key over coming years.... Its going to happen by the looks of things.... I am finding this Ubuntu install 100% rock solid stable and extreemly intuitive (apart from the hardware detection and driver issues with my sound card - but that is of course partially a M$ forced problem as we know)

---

### Post by its_jon on 2008-08-18
Gnome Commander..... Great !

hi Honey Im Home...... Superb, I just got my armchair back :)

I like the gFTP as well... will come in handy but gCommander will be used most :)

I don't use Photoshop as extensively as I used to so Gimp will have to do the job.... Looks a lot better than I remember it though !

for fun I write music using the XP notation program Sibelius .... anything similar for Debian ? or in development ? its niche I know.

Once I get set up I can start contributing .....and damn, I want to see this flavor succeed !
Again...well done with the advances in Ubuntu everyone :KS

---

### Post by Shazaam on 2008-08-20
Look here....
[http://www.linux-sound.org/](http://www.linux-sound.org/)

---

