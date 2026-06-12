---
title: "I can't scape from ubuntu."
date: 2023-06-08
forum: New to Ubuntu
---

### Post by satori-1 on 2023-06-08
I installed the latest version lts and for some reason unity gives the error that my license is not valid,
even though I couldn't even open the program,
I have installed and reinstalled both the system and the program and now I can't escape from ubuntu,
it doesn't work program to generate a usb boot,
I understand that you have to learn about linux and things like that but not having information about it or not having access to it is frustrating even
 if you are willing to learn there is nowhere to start.

but back to the topic is there any solution to the fact that I can not boot? 
I have tested with the terminal, even trying to install other programs to boot and nothing works.

---

### Post by guiverc on 2023-06-08
It may help if you're specific. 

Ubuntu 22.04 LTS Desktop is the *latest LTS *release, with many  [*flavors*]("https://ubuntu.com/download/flavours") available, but Ubuntu Unity wasn't yet an official *flavor* (it was a *respin*).

Are you saying you added the [Unity Desktop (`ubuntu-unity-desktop`)]("https://packages.ubuntu.com/jammy/ubuntu-unity-desktop") to your Ubuntu 22.04 LTS System?  or used the Ubuntu Unity *respin* ?  or something else?  (ie. *are you talking instead about a game engine?*)

Currently its unclear what you're talking about when you reference Unity?  (The Ubuntu Desktop of that name? ie. Unity 7? even the phone/Qt based version being Unity 8?) Either way Unity wasn't a *official flavor* [before 22.10]("https://ubuntuunity.org/blog/ubuntu-unity-becomes-an-official-flavor/") and no *official *LTS yet exists.

---

### Post by yancek on 2023-06-08
In addition to answering the questions above about exactly what you are doing, did you download an Ubuntu iso file?  From what site and which one?  What 'program' are you referring to?  What license?  What 'program' could you not open?  Did you successfully write the Ubuntu iso to the usb and were you able to successfully boot it?  I assume so as you indicate you 'installed' the system.  What problem do you have trying to boot the usb?  Did you write the iso to a usb and use that to boot and install or did you use a DVD?  Are you not able to access the BIOS firmware that you accessed previously?

Information on installing and using Ubuntu is widely available on the internet.  See the links below.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://people.ubuntu.com/~lyz/ubuntu-docs/ubuntu-user-guide.pdf](http://people.ubuntu.com/~lyz/ubuntu-docs/ubuntu-user-guide.pdf)

---

### Post by satori-1 on 2023-06-08
Well,
sorry if I didn't make myself understood well, 
I don't speak English natively, 
with unity I was referring to the 3d engine to create video games I'm a design student, 
and I do know what unity desktop is, it's just that out of desperation I forgot to differentiate them, 
I downloaded the iso from the original ubuntu page, ubuntu 22.04 LTS then I couldn't enter unityhub because it was showing a license error,
and I decided to install the latest non-LTS version for some reason 
I couldn't due to an error that was showing when trying to install version 23.04 ubuntu, and continue using ubuntu 22.04 LTSand then I decided to try to boot my usb to try another operating system and the native ubuntu program to boot a usb wouldn't let me select the flash drive and then yes, 
but now it wouldn't let me select the iso and there is no apparent information on how to fix it, I tried to reinstall the program with the console and nothing happened :P 
I installed other programs to boot like balena or unetbootin but none of them worked for some reason, and well that's all.

Sorry for the syntax errors :c

---

### Post by grahammechanical on 2023-06-08
The web site for the Unity 3D gaming development platform offers versions for Ubuntu 18.04 LTS and Ubuntu 20.04 LTS. It may be that Unity Editor and Unity Hub is not yet compatible with Ubuntu 22.04 LTS. Even though it latest version is called Unity 22 LTS.

Ubuntu uses the Gnome Desktop Environment and there is four years of Gnome Desktop development between Ubuntu 20.04 and Ubuntu 22.04. The Gnome Desktop Environment changes over time. 

Regards

---

### Post by douglas.e.ryan on 2023-06-08
Would the Unity Flatpak help in this case? Of course, he'd need to be willing to setup Flatpaks.

---

### Post by satori-1 on 2023-06-08
I will try, 
although in reality the post is more to know what other options I have to boot since I cannot try other distros or install dual boot 
with any operating system because for some reason the creator of bootable disks in usb does not work, 
download an application called deepin boot creator, 
and although I boot when I enter, select the usb in the bios, the system unknow error appears.
 I looked for a tutorial and I had to use the ls command and then see which partition I could use, 
but both partitions that were created throw the error system unknow, 2 partitions <hd0> and another <hd1>
Obviously if I could use unity it would be a plus to stay in ubuntu until I can boot the usb and dual boot with another system,
 is it that or have to find someone with a usb or someone to format the drive if the problem persists

---

### Post by satori-1 on 2023-06-08
I installed unity flatpak and if it works thank god, for some reason it's throwing ubuntu errors I sent the log, at least it works, 
it stays bugged in the bar next to networks but it worksO:), 
that's good... I guess, al At least it will help me until I fix everything.

---

