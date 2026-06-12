---
title: "HOWTO: XFCE4 with no Gnome"
date: 2005-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2005-04-30
I've seen posts about getting down to XFCE4 after install but what I wanted was just XFCE4 from the start. Nothing else. I found a sight in French that had the info I needed so I thought I'd redo it for you all here.

This is geared towards an x86 install. If you are installing on a PPC system, the acpi stuff may not work for you. Actually, it may not work on an x868 system either. It all depends on your hardware.

This is short and sweet as I figure if this is what you're looking for, you probably don't need too much hand-holding.

(I should add that after completeing this, I had what I wanted but it turned out that I actually had no idea how much I'd miss Gnome. So, I'm back to the normal install.)

Boot with the CD inserted. At the initial prompt, type "server" and presss enter. This will get you your bare (or bare-ish) install. Once the install is complete and you are logged in, change your sources.list to include the universe, multiverse and, optionally, MPlayer repositories. Instructions are [here](http://ubuntuguide.org/#extrarepositories).

(NOTE: In those instructions you will see a line that reads
```
sudo gedit /etc/apt/sources.list
``` 
Since you did the "server" version of the install, you won't have gedit available to you. You can use either vi or nano. So replace that line with either
```
sudo nano /etc/apt/sources.list
```
or
```
sudo vi /etc/apt/sources.list
``` 
If you're new to Linux, you'll probably find nano a lot easier to use than vi.)

Then do

```
sudo apt-get update
```

Once that is done, do

```
sudo apt-get install x-window-system-core xfce4 synaptic gnome-sudo gdm acpi acpid powermanagement-interface mozilla-firefox
``` 

Firefox is not at all necessary but most people seem to want it so I threw it in there. Take it out if you want.

Reboot and you will have a very bare install using XFCE4 without Gnome. From there just apt-get your way to your own little custom Xubuntu. (I said it!)

---

### Post by benplaut on 2005-05-01
[QUOTE=SFN]<snip>
Reboot and you will have a very bare install using XFCE4 without Gnome. From there just apt-get your way to your own little custom **BLEEP**. (I said it!)[/QUOTE]

 [-X  that's a bad word!  [-X   O:) 



 :roll:

---

### Post by Rodrigo on 2005-05-22
Thaks for the how to!, I'll try it right away!!!

---

### Post by Brian McConnell on 2005-05-23
I just did a fresh install on both a G5 ppc and a Celeron 700mhz box. Both are exactly what I wanted. I had previously executed this with warty, but with much less efficiency.
The gdm instead of xdm is a nice touch.
right on.

---

### Post by meki on 2005-05-23
thanks!!!
working great!  ;-)

---

### Post by nicholaspaul on 2005-05-31
I have a PIII 733MHz/128 RAM/ 3.4 HD system running xcfe4 with no Gnome, and I did it just like you said :) I just had to install ssh, samba and beepMediaPlayer and I have my own **Xubuntu** that only takes up 606 Mb. I love it! Perfect for just playing mp3s and nothing else. And I can control it from any other computer in the house (another PIII/700  Ubuntu machine, a Powerbook and a P4 with Windows XP)

Whats wrong with **Xubuntu**?! Sounds like a great spinoff to me! Is it **really** a bad word?

---

### Post by SFN on 2005-06-01
> Whats wrong with Xubuntu?! Sounds like a great spinoff to me! Is it really a bad word? 

No, not really. Mr. Shuttleworth had said in an interview that he liked the idea of an "XFCE-buntu". People quickly latched on to the idea and started referring to it as Xubuntu. Eventually, a thread about the idea of Xubuntu was started here. Then a second. Then a third. As always happens when new ideas are presented, some people got bent out of shape. Not just here but in other forums as well. The Ubuntu community though, in its (so far) typical fashion, didn't get too rattled. It was a pretty interesting exchange. (That is, for me, what makes Ubuntu kick large amounts of butt - open dialogue, helpful suggestions, good people.)

Check out the threads here: [http://ubuntuforums.org/search.php?searchid=861177](http://ubuntuforums.org/search.php?searchid=861177)

---

### Post by Brian McConnell on 2005-06-01
[QUOTE=SFN]No, not really. Mr. Shuttleworth had said in an interview that he liked the idea of an "XFCE-buntu". People quickly latched on to the idea and started referring to it as Xubuntu. Eventually, a thread about the idea of Xubuntu was started here. Then a second. Then a third. As always happens when new ideas are presented, some people got bent out of shape. Not just here but in other forums as well. The Ubuntu community though, in its (so far) typical fashion, didn't get too rattled. It was a pretty interesting exchange. (That is, for me, what makes Ubuntu kick large amounts of butt - open dialogue, helpful suggestions, good people.)

Check out the threads here: [http://ubuntuforums.org/search.php?searchid=861177](http://ubuntuforums.org/search.php?searchid=861177)[/QUOTE]

I'd say Xubuntu sounds like a crappy name, but a great idea as far as XFCE+Ubuntu. There again, I don't like the "first letter adoption to names" thing that seems so popular with GNU/Linux programs ala Kubuntu or what have you.
I have that 700mhz Celeron with 384mb RAM box and without this thread, I'd not know what to do with it ;)
An .iso of this nature for both x86 and PPC is certainly useful.

---

### Post by nicholaspaul on 2005-06-02
Oh, I always thought the naming convention of most linux things was pretty silly - like the self-referenced abbreviations! Too funny. But thats the way it is. Personally I think Xubuntu would just be in keeping with that convention. C'est la Vie.

But then i thought OSX sounded like Oh yes sex....

---

### Post by pdk001 on 2005-06-02
thanks for tip, i will try it later

---

### Post by benplaut on 2005-06-03
so... Xubuntu would be pronounced "zoo-boon-too"?

---

### Post by SFN on 2005-06-07
[QUOTE=benplaut]so... Xubuntu would be pronounced "zoo-boon-too"?[/QUOTE]

Using the existing (admittedly silly) naming scheme, yes.

Although I have to say I have a preference for X-buntu. It's got that whole skateboarding/snowboarding/BMXing vibe only in a completely dorky way. \\:D/

---

### Post by penvzila on 2005-06-08
No, it would be pronounced !-ubuntu.

---

### Post by benplaut on 2005-06-08
[QUOTE=penvzila]No, it would be pronounced !-ubuntu.[/QUOTE]

so... "ding-ubuntu"?  :razz:

---

### Post by drewxhawaii on 2005-06-11
this is exactly what i want, however, i have a problem.

i keep getting:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb) MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


help!

---

### Post by iammike on 2005-06-11
[QUOTE=drewxhawaii]this is exactly what i want, however, i have a problem.

i keep getting:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb) MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


help![/QUOTE]
 Go here...

[http://www.ubuntuforums.org/showthread.php?p=208396#post208396](http://www.ubuntuforums.org/showthread.php?p=208396#post208396)

---

### Post by drewxhawaii on 2005-06-11
[QUOTE=iammike]Go here...

[http://www.ubuntuforums.org/showthread.php?p=208396#post208396](http://www.ubuntuforums.org/showthread.php?p=208396#post208396)[/QUOTE]
[IMG]http://www.preschooldays.com/upload/images/heart.gif[/IMG]

---

### Post by craigevil on 2005-08-10
Great guide. Xfce is awesome. It is much faster than Gnome or KDE and uses way less ram. 

Add Rox-filer as the file/background manager and you have a great desktop. That is fast and will work on a low resource system.

---

### Post by celluloid on 2005-09-06
[QUOTE=craigevil]Great guide. Xfce is awesome. It is much faster than Gnome or KDE and uses way less ram. 

Add Rox-filer as the file/background manager and you have a great desktop. That is fast and will work on a low resource system.[/QUOTE]
 How do you "Add Rox-filer as the file/background manager"?

Sorry.. n00b here :)

---

### Post by John.Michael.Kane on 2005-09-09
Have any of you been able to get synaptic working

---

### Post by SFN on 2005-09-09
I haven't used XFCE4 in a while but back when I wrote this, doing:

```
gksudo synaptic
``` 

in a terminal would do the trick. I'd hope that hasn't changed.

As for getting it to work from menus, dealing with getting menus the way I wanted them in XFCE was one of the things that sent me back to Gnome. Not that I'm knocking XFCE for it. I was just way too lazy for that.

---

### Post by John.Michael.Kane on 2005-09-09
Edit: i got it going it's not gksudo synaptic just sudo synaptic 

thanks

---

### Post by xequence on 2005-09-09
Xubuntu sounds cool. Like the rush song, Xanadu or however its spelled ;)

But one thing... Dont you have to enable the extra repositories before using apt-get?

---

### Post by SFN on 2005-09-09
[QUOTE=xequence]Dont you have to enable the extra repositories before using apt-get?[/QUOTE]

Yes. The instructions for doing that are in original post.

---

### Post by Rxke on 2005-09-12
Hi, SFN, 

thanks, worked flawlessly !

Some remarks, though:

you say ```
gedit /etc/apt/....
``` but there is no gedit, if you use the server install. Use vi instead.
For people that don't know vi, like me, type ```
vimtutor
``` which is a nice tutorial on Vi(m), better for newbies than the manpages (IMHO)

Then, since I run this on a ppc arc: there is no install candidate for acpi, acpid.

---

### Post by SFN on 2005-09-12
[QUOTE=Rxke]you say ```
gedit /etc/apt/....
``` but there is no gedit, if you use the server install. Use vi instead.[/QUOTE]

Doh! You're right. vi or nano. I'll update the original post.

[QUOTE=Rxke]Then, since I run this on a ppc arc: there is no install candidate for acpi, acpid.[/QUOTE]

I'll update to reflect that as well. Thanks for the feedback.

---

### Post by miniml on 2005-09-17
OMG, this is exactly what I was looking for. Have done a clean install today with this method, and it works like a charm. Thanks alot!

---

### Post by miniml on 2005-09-18
How to configure sound in Xfce? (I followed your guide for Xfce without Gnome using server install).

In ALSA mixer i got both PCM and master unmuted and set to 90. So, what's the problem, I don't hear any sound? Is there some tutorial? In default ubuntu everything works out-of-the-box.

I followed the guide from ubuntuguide.org also.

I checked with ogg123, and I get following error:
```
Error: Cannot open device esd.
```

BTW, I got mpd + mpc + gmpc configured and installed and it plays without error, I just can't hear any sound.

---

### Post by vr04 on 2005-09-18
Say, how about "Ubun**tuX**."

...

Sorry, please don't kill me.  :-#

---

### Post by picpak on 2005-10-13
[QUOTE=vr04]Say, how about "Ubun**tuX**."

...

Sorry, please don't kill me.  :-#[/QUOTE]

Taken.

[http://www.ubuntux.org/](http://www.ubuntux.org/)

---

### Post by zeca_pedra on 2005-10-14
I did a new installation following this article and ... WOW! Incredible how my machine is running fast now!
It loads all the system in about 30 seconds and looks great!
I already knew XFCE4 but never had the time to work around it and learn how to use it, so I have 2 or 3 little issues:

1) I installed synaptic but I can't see it in the menu nor running it from the command line :-( which it's bizarre 'cause I've also installed gnomebaker and this is correctly appearing in that same menu
2) I want to change from single click in the file manager to open files with double click but I can't figure it out how to change this

Well, I think probably more issues will arise while I'm learning how to deal with XFCE but I must tell you:

THANK YOU very much for this great how-to, XFCE looks great, it's really fast and, for my purposes, I think I'll stick with it for a while

Zeca

---

### Post by SFN on 2005-10-14
[QUOTE=zeca_pedra]1) I installed synaptic but I can't see it in the menu nor running it from the command line :-( which it's bizarre 'cause I've also installed gnomebaker and this is correctly appearing in that same menu[/QUOTE]

I just did a new install in Breezy and I have noticed that same thing about Synaptic in the menu. That is odd but it can easily be added manually to the iconbar.

Right-click anywhere on the iconbar. Choose "Add new item". The first text box is for the icon. Type in "/usr/share/pixmaps/synaptic.png". In the "Command:" text box, type in "gksudo synaptic". Uncheck the box that says "Attach menu to launcher". Also, adjust the "Position" item at the top of the window to place the icon where you want it on the toolbar. When you're done, click Close.

(I originally had instructions here for adding Synaptic to the menu but that doesn't seem to work. Not sure why. Probably the same issue that prevents it from being added to the menu automatically. At this point, it can be run from the iconbar shortcut or by typing "gksudo synaptic" in either the "Run Program" item at the top of the menu or the command line.)

As for it not starting from the command line, I'm not having that problem. Are you starting by typing in "gksudo synaptic"? If not, try that. It should work.

[QUOTE=zeca_pedra]2) I want to change from single click in the file manager to open files with double click but I can't figure it out how to change this[/QUOTE]

I have no idea on that one. I'll see what I can find. Should anyone else know the answer, feel free to post it here.

[QUOTE=zeca_pedra]THANK YOU very much for this great how-to, XFCE looks great, it's really fast and, for my purposes, I think I'll stick with it for a while

Zeca[/QUOTE]

Glad you like it. I just posted a new HOWTO about doing this in Breezy. Only some minor changes but one of those changes will get your USB drives automounted. That HOWTO is [here]("http://ubuntuforums.org/showthread.php?t=75971").

---

### Post by matthew on 2005-10-14
It is not officially announced yet, but the name is Xubuntu and the package does exist.

[https://wiki.ubuntu.com/Xubuntu]("https://wiki.ubuntu.com/Xubuntu")

[http://packages.ubuntu.com/breezy/misc/xubuntu-desktop]("http://packages.ubuntu.com/breezy/misc/xubuntu-desktop")

---

### Post by SFN on 2005-10-14
Oh. Well, that's great!

I'll check out the dev list and see if I can help in any way. I probably can't as my skills are somewhat, er, poor - but you never know.

Thanks for the info!

---

### Post by mctavish on 2005-10-14
zeca_pedra, if you cannot see synaptic in your menu it might be because you don't have the package gksu installed. The xubuntu-desktop package doesn't install this. The menu item for synaptic needs gksudo to show up.

If this is the case, the 2 options are 1, run sudo synaptic from a terminal, or 2 install gksu and you should see the menu item appear.

---

### Post by rady on 2005-11-04
Cheer!! Thank you for that tip. I can refresh my Pentium 166 64MB with xfce. I cannot use Xterminal besides it located icon on menu.  Anyone can tell me or missing any package install? :rolleyes:

---

