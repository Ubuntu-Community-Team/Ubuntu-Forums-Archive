---
title: "HOWTO: Ubuntu CLI versions &amp; Framebuffer Programs"
date: 2008-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Vivaldi Gloria on 2008-08-07
[COLOR="Blue"]**Contents**[/COLOR]

[COLOR="Blue"]**PART A. CLI versions of Ubuntu**[/COLOR]
*Do you know that there are four different versions of cli-only ubuntu?*

[COLOR="Blue"]**PART B. CLI Resources**[/COLOR]
*Pages every cli fan should know about.*

[COLOR="Blue"]**PART C. Framebuffer Programs**[/COLOR]
*Watch videos without running X at all!*

--------------------------------------------------------------------------

CLI = Command Line Interface

Note that I have only tried the things I write below with Hardy. They may be different for other ubuntu versions, they may not work at all.

Additions, corrections, and questions are welcomed.

---

### Post by Vivaldi Gloria on 2008-08-07
[COLOR="Blue"]**PART A. CLI versions of Ubuntu**[/COLOR]

Different command line versions of ubuntu:

**(1)** The alternate desktop cd (with the F4 option) available from [[COLOR="Sienna"]download[/COLOR]]("http://www.ubuntu.com/getubuntu/download")

**(2)** Minimal CD available from [[COLOR="Sienna"]MinimalCD[/COLOR]]("https://help.ubuntu.com/community/Installation/MinimalCD")

**(3)** Server CD available from [[COLOR="Sienna"]download[/COLOR]]("http://www.ubuntu.com/getubuntu/download")

**(4)** Ubuntu Jeos available from [[COLOR="Sienna"]jeos[/COLOR]]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")


**[COLOR="Blue"]Comments[/COLOR]**

**[COLOR="Blue"](1) and (2)[/COLOR]**
As far as I can tell (1) and (2) install the same basic ubuntu CLI version. I really like this version. It has no server stuff. Useful as a base system for a custom system build. For example install openbox or another gui (see [[COLOR="Sienna"]LowMemSystems[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems")). Or just use it as is. Good for old boxes. I use one in an old computer to practice command line and listen to music using MOC. The minimal CD (2) is only ~10MB. The install of (2) takes longer than (1) because it downloads everything from the net. So use (2) if you have a decent connection. 

This cli system has all the drivers in the ubuntu desktop cd and they have the same hardware support.

To install a cli system using (1) press F4 at the boot menu and choose "Install a command line system". (The xubuntu alt CD also has this feature. I didn't check the kubuntu alt cd). To install a cli system using (2) write "cli" at the boot options. 

I tried to install (1) in 96MB systems but they all failed. There seems to be a [[COLOR="Sienna"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959") in the Hardy installer which makes it impossible to install on systems with less than 128MB RAM.

On a side note, I've seen a couple of computers in which all regular ubuntu CDs failed for some reason but the minimal cd (2) worked. So it may be helpful in installation problems.

**[COLOR="Blue"](3)[/COLOR]** contains server programs. Don't install this unless you are making a server. Having non-used server programs on a destop computer is bad on at least three accounts: 

a) Takes space 
b) Updates take more time & bandwidth 
c) Security: no point in programs which may listen to ports.

The desktop and server versions have different kernels. See this page for a list of [[COLOR="Sienna"]differences[/COLOR]]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel").

Ubuntu specs page says that server edition requires a minimum of 128MB of RAM. To learn more about the server edition go to [[COLOR="Sienna"]serveredition[/COLOR]]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

**[COLOR="Blue"](4)[/COLOR]** This version is a very light version which has hardly any drivers or apps on it. Do NOT install it in a computer because it won't recognize your hardware. This version is supposed to be run in a virtual sytem like vmware, virtualbox, KVM etc. "This combination of reduced size and optimised performance ensures that Ubuntu JeOS Edition delivers a highly efficient use of server resources in large virtual deployments." See [[COLOR="Sienna"]this[/COLOR]]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") and [[COLOR="Sienna"]that[/COLOR]]("https://help.ubuntu.com/community/JeOS") for more info.


**Ubuntu Installation Guides:** [[COLOR="Sienna"]Installation[/COLOR]]("https://help.ubuntu.com/community/Installation")

**Ubuntu Installation on Low Memory Systems:** [[COLOR="Sienna"]LowMemSystems[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems")


.

---

### Post by Vivaldi Gloria on 2008-08-07
[COLOR="Blue"]**PART B. Resources**[/COLOR]

**[COLOR="Blue"]1.[/COLOR]** Comprehensive guides at [[COLOR="Sienna"]TLDP[/COLOR]]("http://tldp.org/guides.html"). Start with "Bash Guide for Beginners" and "GNU/Linux Command-Line Tools Summary".

**[COLOR="Blue"]2.[/COLOR]** Linux commands and shell basics: [[COLOR="Sienna"]help.ubuntu[/COLOR]]("https://help.ubuntu.com/8.04/basic-commands/C/") - [[COLOR="Sienna"]linuxdevcenter[/COLOR]]("http://www.linuxdevcenter.com/linux/cmd/") - [[COLOR="Sienna"]linuxcommand.org[/COLOR]]("http://www.linuxcommand.org/") - [[COLOR="Sienna"]pixelbeat[/COLOR]]("http://www.pixelbeat.org/cmdline.html") - [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=777147") - [[COLOR="Sienna"]101[/COLOR]]("http://www.ahinc.com/linux101/toc.html") 

See also [[COLOR="Sienna"]Malicious Commands[/COLOR]]("http://ubuntuforums.org/announcement.php?f=73") and [[COLOR="Sienna"]System Info[/COLOR]]("http://ubuntuforums.org/showthread.php?t=842307")

**[COLOR="Blue"]3.[/COLOR]** Cheat Sheets - Quick Reference Cards:

[[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=683871") - [[COLOR="Sienna"]fosswire[/COLOR]]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/") - [[COLOR="Sienna"]fosswire[/COLOR]]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/") - [[COLOR="Sienna"]debian[/COLOR]]("http://people.debian.org/~debacle/refcard/") - [[COLOR="Sienna"]tuxfiles[/COLOR]]("http://www.tuxfiles.org/linuxhelp/linuxtips.html") - [[COLOR="Sienna"]digilife[/COLOR]]("http://www.digilife.be/quickreferences/quickrefs.htm") - [[COLOR="Sienna"]scottklarr[/COLOR]]("http://www.scottklarr.com/tag/cheat-sheets/")

**[COLOR="Blue"]4.[/COLOR]** What can you use a low spec system for? Some ideas: [[COLOR="Sienna"]old[/COLOR]]("http://www.dailycupoftech.com/2007/09/17/put-that-old-computer-to-good-use/") - [[COLOR="Sienna"]kmandla1[/COLOR]]("http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/") - [[COLOR="Sienna"]kmandla2[/COLOR]]("http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/")

**[COLOR="Blue"]5.[/COLOR]** OS for old computers: [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575456") - [[COLOR="Sienna"]floppy[/COLOR]]("http://www.linuxlinks.com/Distributions/Floppy/")

**[COLOR="Blue"]6.[/COLOR]** About installing Ubuntu on low mem systems: [[COLOR="Sienna"]LowMemSystems[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems") - [[COLOR="Sienna"]psychocats[/COLOR]]("http://www.psychocats.net/ubuntu/minimal") - [[COLOR="Sienna"]miniRAM[/COLOR]]("http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html")

**[COLOR="Blue"]7.[/COLOR]** Urukrama's openbox [[COLOR="Sienna"]guide[/COLOR]]("http://urukrama.wordpress.com/openbox-guide/").

**[COLOR="Blue"]8.[/COLOR]** Server apps at ubuntu community docs: [[COLOR="Sienna"]servers[/COLOR]]("https://help.ubuntu.com/community/Servers")

**[COLOR="Blue"]9.[/COLOR]** To change bootup and console resolution (framebuffer) see [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=258484"). To change font, encoding etc. use the command

```
sudo dpkg-reconfigure console-setup
```

**[COLOR="Blue"]10.[/COLOR]** Unicode in bash shell: [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=869824")

**[COLOR="Blue"]11.[/COLOR]** Lists of command line programs: [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=387598") - [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=833627") - [[COLOR="Sienna"]without-X[/COLOR]]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/")

**[COLOR="Blue"]12.[/COLOR]** Every cli user should know about screen: [[COLOR="Sienna"]wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/GNU_Screen") - [[COLOR="Sienna"]tutorial[/COLOR]]("http://jmcpherson.org/screen.html") - [[COLOR="Sienna"]reference[/COLOR]]("http://aperiodic.net/screen/quick_reference") - [[COLOR="Sienna"]manual[/COLOR]]("http://www.delorie.com/gnu/docs/screen/screen_toc.html")

**[COLOR="Blue"]13.[/COLOR]** Linux Filesystem Hierarchy

A very good [[COLOR="Sienna"]video[/COLOR]]("http://www.archive.org/details/HampshireLinuxUserGroup_15")
Filesystem Hierarchy Standard: [[COLOR="Sienna"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") and [[COLOR="Sienna"]Official[/COLOR]]("http://www.pathname.com/fhs/")
TLDP Howto: [[COLOR="Sienna"]html[/COLOR]]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html") and [[COLOR="Sienna"]pdf[/COLOR]]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf")
Other FH Resources: [[COLOR="Sienna"]1[/COLOR]]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview")  [[COLOR="Sienna"]2[/COLOR]]("http://freeos.com/articles/3102/")  [[COLOR="Sienna"]3[/COLOR]]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html")  [[COLOR="Sienna"]4[/COLOR]]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")

**[COLOR="Blue"]14.[/COLOR]** Security. [[COLOR="Sienna"]bodhi.zazen[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812") - [[COLOR="Sienna"]bodhi.zazen2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=919472") - [[COLOR="Sienna"]debian[/COLOR]]("http://www.debian.org/doc/manuals/securing-debian-howto/") - [[COLOR="Sienna"]tldp[/COLOR]]("http://tldp.org/HOWTO/Security-HOWTO/index.html") - [[COLOR="Sienna"]sectools[/COLOR]]("http://sectools.org/") - [[COLOR="Sienna"]Iptables[/COLOR]]("https://help.ubuntu.com/community/IptablesHowTo")

**[COLOR="Blue"]15.[/COLOR]** Some general references:

[[COLOR="Sienna"]help.ubuntu.com/[/COLOR]]("https://help.ubuntu.com/")
[[COLOR="Sienna"]ubuntuguide.org/[/COLOR]]("http://ubuntuguide.org/")
[[COLOR="Sienna"]doc.ubuntu.com/ubuntu/serverguide/C/[/COLOR]]("http://doc.ubuntu.com/ubuntu/serverguide/C/")
[[COLOR="Sienna"]www.debian-administration.org/[/COLOR]]("http://www.debian-administration.org/")
[[COLOR="Sienna"]www.debian.org/doc/[/COLOR]]("http://www.debian.org/doc/")
[[COLOR="Sienna"]www.debian.org/doc/user-manuals[/COLOR]]("http://www.debian.org/doc/user-manuals")
[[COLOR="Sienna"]tldp.org[/COLOR]]("http://tldp.org")
[[COLOR="Sienna"]www.howtoforge.com/[/COLOR]]("http://www.howtoforge.com/")
[[COLOR="Sienna"]bash.cyberciti.biz/[/COLOR]]("http://bash.cyberciti.biz/")
[[COLOR="Sienna"]www.debianhelp.co.uk/[/COLOR]]("http://www.debianhelp.co.uk/")
[[COLOR="Sienna"]rute[/COLOR]]("http://rute.2038bug.com/index.html.gz")
[[COLOR="Sienna"]aboutdebian[/COLOR]]("http://www.aboutdebian.com/")
[[COLOR="Sienna"]ubuntu-server-guide-part-1[/COLOR]]("http://ubuntuland.nireblog.com/post/2008/04/09/ubuntu-server-guide-part-1")
[[COLOR="Sienna"]ubuntu-server-guide-part-2[/COLOR]]("http://ubuntuland.nireblog.com/post/2008/04/10/ubuntu-server-guide-part-2")
[[COLOR="Sienna"]ubuntu-server-guide-part-3[/COLOR]]("http://ubuntuland.nireblog.com/post/2008/04/13/ubuntu-server-guide-part-3")

---

### Post by Vivaldi Gloria on 2008-08-07
[COLOR="Blue"]**PART C. Framebuffer Programs**[/COLOR]

This list consists (mostly) of terminal programs which use framebuffer to show images, web pages, videos etc. You can do all these without using X at all!

**[COLOR="Blue"]1.[/COLOR]** To enable mouse support in the terminal install gpm:
```

sudo apt-get install gpm
```

Then edit
```

sudo nano /etc/udev/rules.d/40-permissions.rules
```

and add the following line to the end:

```
KERNEL=="mice",           MODE="0666"
```

and restart.

You can select text to copy and middle-click to paste. This also works between different terminals. For example select a text in tty1, then press (ctrl+)alt+F3 and middle-click to paste in tty3.

To enable mouse support in nano edit the /etc/nanorc file and comment out the line "set mouse". "When enabled, mouse clicks can be used to place the cursor, set the mark (with a double click), and execute shortcuts."


**[COLOR="Blue"]2.[/COLOR]** links2 is a webbrowser which can use framebuffer:
```

sudo apt-get install links2
```

Now start with

```
links2 -g
```

to get the graphical version.

On a side note, see also surfraw which is a frontend to various web search pages including wikipedia & google.

[http://surfraw.alioth.debian.org/](http://surfraw.alioth.debian.org/)


**[COLOR="Blue"]3.[/COLOR]** To see images install fbi:

```
sudo apt-get install fbi
```

Then use for example
```

fbi *.jpg
```

in a directory with images.


**[COLOR="Blue"]4.[/COLOR]** To read pdf also use fbi which needs imagemagick to show pdf files:
```

sudo apt-get install fbi imagemagick
```

Now 

```
fbi file.pdf
```

will do the job.

Another program is fbgs - "poor man's PostScript/pdf viewer for the linux framebuffer console" which also works quite good.

Note that there is a good command line pdf maniplation program: pdftk.


**[COLOR="Blue"]5.[/COLOR]** You can use mplayer (or mplayer-nogui) to watch videos:
```

sudo apt-get install mplayer
```

Now I can watch videos with

```
mplayer -vo fbdev -fs -vf scale=1280:-3 FileName
mplayer -vo fbdev -fs -vf scale=-3:1024 FileName
```

Use the first one if the width of the video is larger than the height. Otherwise, use second. I have an alias in .bashrc so I don't have to remember them.

My framebuffer resolution is 1280x1024. Change the commands above for your resolution accordingly.


**[COLOR="Blue"]6.[/COLOR]** I cannot get vlc and xine to work with framebuffer. In theory they should work. When I try to use vlc with one of

```
vlc video_file
vlc --vout fb video_file
```

something weird happens. It plays the video as ascii animation. It uses only the text console! It's really fun. You've got to see it to believe it.

But there is a problem. I don't know how to stop the video! To stop I goto ALT+F2 console and kill vlc from there. This leaves the original terminal (ALT+F1) in a weird state so to get it back use the command
```

reset
```


**[COLOR="Blue"]7.[/COLOR]** There are good music players around. I prefer MOC (Music On Console). It plays everything and you can change the config file to your liking. It even uses themes. (Note that you install the package named "moc" but you start it with "mocp").

I don't know any music player which uses framebuffer.


**[COLOR="Blue"]8.[/COLOR]** For terminal programs in general see the links given in Part B-11 of this howto.

---

### Post by chronographer on 2008-08-07
Well thanks for this, I never know you could use a mouse at the command prompt! I do now, and may enable it if I need it in the future...

---

### Post by Joeb454 on 2008-08-07
Moved to Tutorials & Tips

---

### Post by hyper_ch on 2008-08-07
I'd add [http://www.linuxcommand.org](http://www.linuxcommand.org) to the list :)

And I also like the FOSSwire command line and ubuntu cheat sheets... very useful to get a short summary of the most used commands.

---

### Post by Vivaldi Gloria on 2008-08-07
> **chronographer said:**
> Well thanks for this, ...

You're welcome.

> **hyper_ch said:**
> I'd add [http://www.linuxcommand.org](http://www.linuxcommand.org) to the list :)

And I also like the FOSSwire command line and ubuntu cheat sheets... very useful to get a short summary of the most used commands.

Thanks hyper_ch. Added them.

---

### Post by sisco311 on 2008-08-07
the mplayer package comes with a GUI(at least in hardy).
is sufficient to install mplayer-nogui

---

### Post by Vivaldi Gloria on 2008-08-07
> **sisco311 said:**
> is sufficient to install mplayer-nogui

Yes. I have mplayer-nogui from medibuntu repos in one of my computers and it works OK with the framebuffer.

Edit: Added to Part C.

---

### Post by trash on 2008-09-03
sweet thanks!
About Moc though, there is no man pages so how on earth does it work??

when i run moc all i get is 'can be found in the following 2 packages and then whants to install about 40mb of files? this can't be the best option lol

---

### Post by Vivaldi Gloria on 2008-09-03
> **trash said:**
> sweet thanks!
About Moc though, there is no man pages so how on earth does it work??

when i run moc all i get is 'can be found in the following 2 packages and then whants to install about 40mb of files? this can't be the best option lol

The name of the package is moc but the executable is mocp. See

```
man mocp
```

Start with "mocp" and press "h" to get help. To exit press "Q", that is SHIFT+q. 

If you only press "q" then it will detach moc and continue playing. To stop it retype "mocp" and exit using shift+q.

---

### Post by trash on 2008-09-03
> **Vivaldi Gloria said:**
> The name of the package is moc but the executable is mocp. See

```
man mocp
```

Start with "mocp" and press "h" to get help. To exit press "Q", that is SHIFT+q. 

If you only press "q" then it will detach moc and continue playing. To stop it retype "mocp" and exit using shift+q.

OHHHH of course mocp, how silly of me:lolflag:

Thanks!

---

### Post by Vivaldi Gloria on 2008-09-03
> **trash said:**
> OHHHH of course mocp, how silly of me:lolflag:

Thanks!

You're welcome. Not silly of you because it's a bit unexpected. I guess they didn't use "moc" because there's already another app caled moc. I added a note to howto.

Cheers.

---

### Post by trash on 2008-09-03
Oh that reminds me:
```
sudo nano /etc/udev/rules.d/40-permission.rule
```
should be..
```
sudo nano /etc/udev/rules.d/40-permissions.rules
```

cheers:)

---

### Post by Vivaldi Gloria on 2008-09-03
40-permissions.rules corrected. Thanks.

---

### Post by Jose Catre-Vandis on 2008-09-16
> **Vivaldi Gloria said:**
> 
Note that xubuntu alt CD doesn't contain this feature

It does for 8.04.1, I am typing from it now :)

---

### Post by Vivaldi Gloria on 2008-09-17
> **Jose Catre-Vandis said:**
> It does for 8.04.1, I am typing from it now :)

You're right mate. Just verified it. Thanks. Edited the OP accordingly.

---

### Post by markp1989 on 2009-05-20
> **Vivaldi Gloria said:**
> [COLOR="Blue"]**PART C. Framebuffer Programs**[/COLOR]

This list consists (mostly) of terminal programs which use framebuffer to show images, web pages, videos etc. You can do all these without using X at all!

**[COLOR="Blue"]1.[/COLOR]** To enable mouse support in the terminal install gpm:
```

sudo apt-get install gpm
```

Then edit
```

sudo nano /etc/udev/rules.d/40-permissions.rules
```

and add the following line to the end:

```
KERNEL=="mice",           MODE="0666"
```

and restart.

You can select text to copy and middle-click to paste. This also works between different terminals. For example select a text in tty1, then press (ctrl+)alt+F3 and middle-click to paste in tty3.

To enable mouse support in nano edit the /etc/nanorc file and comment out the line "set mouse". "When enabled, mouse clicks can be used to place the cursor, set the mark (with a double click), and execute shortcuts."


**[COLOR="Blue"]2.[/COLOR]** links2 is a webbrowser which can use framebuffer:
```

sudo apt-get install links2
```

Now start with

```
links2 -g
```

to get the graphical version.

On a side note, see also surfraw which is a frontend to various web search pages including wikipedia & google.

[http://surfraw.alioth.debian.org/](http://surfraw.alioth.debian.org/)


**[COLOR="Blue"]3.[/COLOR]** To see images install fbi:

```
sudo apt-get install fbi
```

Then use for example
```

fbi *.jpg
```

in a directory with images.


**[COLOR="Blue"]4.[/COLOR]** To read pdf also use fbi which needs imagemagick to show pdf files:
```

sudo apt-get install fbi imagemagick
```

Now 

```
fbi file.pdf
```

will do the job.

Another program is fbgs - "poor man's PostScript/pdf viewer for the linux framebuffer console" which also works quite good.

Note that there is a good command line pdf maniplation program: pdftk.


**[COLOR="Blue"]5.[/COLOR]** You can use mplayer (or mplayer-nogui) to watch videos:
```

sudo apt-get install mplayer
```

Now I can watch videos with

```
mplayer -vo fbdev -fs -vf scale=1280:-3 FileName
mplayer -vo fbdev -fs -vf scale=-3:1024 FileName
```

Use the first one if the width of the video is larger than the height. Otherwise, use second. I have an alias in .bashrc so I don't have to remember them.

My framebuffer resolution is 1280x1024. Change the commands above for your resolution accordingly.


**[COLOR="Blue"]6.[/COLOR]** I cannot get vlc and xine to work with framebuffer. In theory they should work. When I try to use vlc with one of

```
vlc video_file
vlc --vout fb video_file
```

something weird happens. It plays the video as ascii animation. It uses only the text console! It's really fun. You've got to see it to believe it.

But there is a problem. I don't know how to stop the video! To stop I goto ALT+F2 console and kill vlc from there. This leaves the original terminal (ALT+F1) in a weird state so to get it back use the command
```

reset
```


**[COLOR="Blue"]7.[/COLOR]** There are good music players around. I prefer MOC (Music On Console). It plays everything and you can change the config file to your liking. It even uses themes. (Note that you install the package named "moc" but you start it with "mocp").

I don't know any music player which uses framebuffer.


**[COLOR="Blue"]8.[/COLOR]** For terminal programs in general see the links given in Part B-11 of this howto.

wheni try to run mplayer , i get an error "/dev/fb0 permission denied" 


how do i give my self permission ?

Thanks Markp1989

edit: VLC plays , the video is make up of random letters and numbers of different colours?

is that how its ment to look?

---

### Post by flangemonkey on 2009-09-10
I had the same problem with fbi on 8.10 Intrepid, to get fbi to work in a non root account the user must be added to the 'video' group.

I used vigr and there is a GUI app for this too, but this should work too, 
```
sudo usermod -a -G video username
```
(replace username with the username of the account you are adding)

hth

Phill

---

### Post by bamboosso on 2010-12-07
Hello,  Small CLI linux is exactly what I need for my small Compulab CM-iAM PC board. Unfortunately I don't have cdrom, and i was unable to run ubuntu-10.10-alternate-i386.iso from USB stick. There was a problem with detecting cdrom (correct, no cdrom in place), and installation didn't go forward. I created USB version using same tool as for normal desktop image.  Is it possible to run alternate installation from USB?  Thanks for help.  Best regards  Maciek

---

