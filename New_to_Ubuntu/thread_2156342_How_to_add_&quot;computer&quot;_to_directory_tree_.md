---
title: "? How to add &quot;computer&quot; to directory tree in either the &quot;Places&quot; menu or Krusader?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-21
I'd like to be able to see the files on a DVD I've got in the drive. And I see no option in Krusader or File Manager to add it to the directory tree (in the left-hand pane) of either GUI.

---

### Post by gordintoronto on 2013-06-21
What version of Ubuntu are you using? It sounds like you might be using Kubuntu, but I can't be sure.

On my (several) versions of Ubuntu, when I insert a DVD, it appears on the desktop, and double-clicking on it makes it open in the file manager. And when I open Nautilus, it appears in the top-left of the windows, with an icon indicating that it can be ejected.

---

### Post by jps2012 on 2013-06-22
gordintoronto: I'm on Ubuntu 12.04. No other partitions on the machine.

---

### Post by jps2012 on 2013-06-22
[**[COLOR=#000000]gordintoronto[/COLOR]**]("http://ubuntuforums.org/member.php?u=507940"): I'm confused--that's a better answer to your question. I'm a noob, so take the following to mean I don't truly understand what I have on this box: I'm on 12.04, but I think the desktop environment is Xbuntu (if that's even possible). The system menu gives me this option: "about Xfce" 

Clicking on it yields "version 4.8, distributed by Xbuntu." 

But "lsb_release -a" at the command line says "Ubuntu 12.04.2 LTS"

---

### Post by jps2012 on 2013-06-22
Another thing I don't understand is whether I'm on KDE, Unity or Gnome (or if that's a nonsensical statement). I suspect Unity may be a branch of Gnome. Anyone ... feel free to correct me if I'm wrong. It would help me sort out what applications are going to work (when I download them).

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]jps2012; Hi !

Let me see what I can do to lessen the state of confusion before addressing the DVD issue.

[/COLOR]> [COLOR=#000000]But "lsb_release -a" at the command line says "Ubuntu 12.04.2 LTS"[/COLOR][COLOR=#000000]
relates what "kernel" is presently being used.
xfce is but one of many desk top environments that may be employed to have a graphical interface with that kernel. xubuntu = the ubuntu kernel + the xfce DE + a few additional packages.

DVD: is this the only DVD you are experiencing a problem with ? Do you know what should be on this disk(s) ? Maybe like you are trying to boot a Windows' boot disk or some such, expecting linux to recognize the Windows' boot structure ?

As a sure test of the DVD drive ... can you boot up a liveDVD of 'buntu ? Then we will see what else can be seen.
[/COLOR][INDENT=2][COLOR=#000000]
where there are solutions there are no problems  [/COLOR][/INDENT]

---

### Post by jps2012 on 2013-06-22
Thank you, Bashing-om. [[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1111508")That helps me understand what I'm looking at. I appreciate your taking the time to spell it out. I'm still not sure if I'm in a Gnome environment ... Unity ... KDE or so on (therefore when I go to the software center to find applications that might help me manage the system itself, and seen an app that says it's for Gnome ... I'm not sure whether it will work). 

I have a photo CD in the DVD drive, but "computer" doesn't show up in Places or in the directory tree in Krusader. Right now I can't even eject it. I bought this computer--an Intel Macbook--with only Ubuntu installed, and the keyboard isn't mapped to the standard Mac layout. I THINK that shouldn't affect the eject button, but I do know the eject button isn't working. (Remapping the keyboard is one of MANY adjustments I'm looking at, once I sort out these other issues.)

---

### Post by jps2012 on 2013-06-22
Bashing-om: Your message clued me in to the fact that I DON'T have a boot disk for 12.04--in case I ravage the system with all the guesswork I'm doing. I'm downloading it now, and if I get to the point where I can FIND a DVD in the file structure, I'll be able to burn a DVD (I hope).

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]jps2012;
We are here to help you over any rough spots.

Eject a DVD ,,, is not done manually.. the system is trying to protect you !
While the system will "automount" the DVD in the DVD drive, It has no way to know when you are done with that disk or what action you want to take. You MUST, I do emphasize you must, "(un)mount that device when you have completed what ever you are doing -> either from the file manager (krusader)... I do not run the kde environment so not at all familiar with specifics; In krusader I would think on the left pane is all the file systems that the system has access to, right clicking on the associated icon results in options, One of the options is something like "safely remove" or maybe "eject". There may also exist an icon on the desk top. Right clicking on this icon will also yield options, among which is to permit the device to be ejected.
I highly suggest at this point to follow that procedure, "safely remove" the disk then (re-)insert the disk in the DVD drive, one should see that disk on both the file manager and the desk top. Else there is a problem; either with the disk or in your configuration to recognize removable media.

Not to confuse you more, if you know the "mount point" and device ID ... one may perform the "unmount" operation from the command line.

To explore what desk top you have, let us start with a terminal command ->
key combo ctl+alt+t yields a terminal: -> type:
[/COLOR]```
apt-cache policy ubuntu-desktop
```will be a place to start looking.[INDENT=2]
making progress[/INDENT]

---

### Post by gordintoronto on 2013-06-22
This is definitive: you are using Xubuntu. I dual-boot my computer, and Xubuntu 13.04 is what I am using as I write this, but you are using an older version.

If you click on Accessories/File Manager, it should start Thunar. Help/About should confirm this. If you have a DVD loaded, it should appear in the top-left portion of Thunar, click on it and you will see the folders and files.

Krusader is a KDE (Kubuntu) program, but you are not using KDE or Kubuntu. The computer is not using Unity or Gnome. It is possible that any of those options are available at logon, via a drop-down option.

Generally, Gnome applications work in Xubuntu. KDE applications also work, but when you install the first one (Krusader!) a lot of other stuff also gets installed.

Your DVD should appear on the desktop. You can right-click it and select "eject."

You should not need to understand anything about "mount points" at this stage.

I hope this helps.

---

### Post by jps2012 on 2013-06-22
gornintornonto and bashing-om: That moves me along nicely. I hadn't considered I wouldn't be allowed to just eject the disk directly with the button, the way I would on a Mac. I will have to follow your instructions (I realize there's a difference of opinion about the best next steps, but I can sort through it) Monday evening. I had to leave the computer at a friend's house to have OSX installed on one of the partitions (booting from a USB port, due to the stuck CD--but I'm going to forward the guy these messages; he also didn't know how to eject the disk; and I realize THAT brings up questions about competence, but I'm praying ...). 

I will write again Monday evening, when I have the computer back. Thank you very much for the help.

---

