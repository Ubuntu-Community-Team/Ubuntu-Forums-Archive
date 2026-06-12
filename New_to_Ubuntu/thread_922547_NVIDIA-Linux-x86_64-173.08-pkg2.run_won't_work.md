---
title: "NVIDIA-Linux-x86_64-173.08-pkg2.run won't work"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Juvencio on 2008-09-17
I need to install my NVIDIA-Linux-x86_64-173.08-pkg2.run driver
this is what i did and this is what i get !!!!!!!

open terminal:

 $ cd /lib/linux-restricted-modules

 $ sudo rm .nvidia*

no drivers in file. ok

downloaded the NVIDIA driver NVIDIA-Linux-x86_64-173.08-pkg2.run
Saved it on Desktop.

Log out. and Hit CTRL+ALT+F1

 $ sudo /etc/init.d/gdm stop

OK it stoped

 $ sudo apt-get install nvidia-settings

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-settings

OK something wrong !!!!

 $ sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run

sh: Can't open NVIDIA-Linux-x86_64-173.08-pkg2.run

pleas help me

---

### Post by Tatty on 2008-09-17
I would highly recommend installing your drivers from the repos with either System->Administration->Hardware Drivers,  or with envyNG.

---

### Post by Juvencio on 2008-09-17
> **Tatty said:**
> I would highly recommend installing your drivers from the repos with either System->Administration->Hardware Drivers,  or with envyNG.

Hardware Drivers won't install my diver on ubuntu 8 64 bit

envyNG? not sure about that one!

---

### Post by Tatty on 2008-09-17
> **Juvencio said:**
> Hardware Drivers won't install my diver on ubuntu 8 64 bit

envyNG? not sure about that one!

try installing envyng from the repos
```
sudo apt-get install envyng-gtk
```

Then use that to install the ATI driver, Often it works where the Hardware Drivers manager fails.

---

### Post by IanW on 2008-09-17
Tatty - Juvencio is trying to install _Nvidia_ drivers, not Ati.

Envy won't install "beta" drivers - it only offers the following Nvidia versions - 71.86.04 or 96.43.05 or 173.14.12

Juvencio - Did you change permissions on the *.run file to make it executable?
```
chmod a+x ./NVIDIA*.run
```

---

### Post by Juvencio on 2008-09-17
$ sudo apt-get install envyng-gtk

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
juvencio@juvencio-desktop:~$ 

whear is E: and why can't it find anything?

---

### Post by Juvencio on 2008-09-17
sorry about double post firefox or may i say ubuntu 8 64 bit is a bit stiky.

ubuntu 8 32 bit worked fine maybe is suld revert back to it!

what you think?

---

### Post by philinux on 2008-09-17
Open system>admin>software sources. and make sure the top 4 are ticked.

---

### Post by silverglade00 on 2008-09-17
E: means Error:. It is telling you what the error is. There are no drive letters in Linux.

---

### Post by Juvencio on 2008-09-17
> **IanW said:**
> Tatty - Juvencio is trying to install _Nvidia_ drivers, not Ati.

Envy won't install "beta" drivers - it only offers the following Nvidia versions - 71.86.04 or 96.43.05 or 173.14.12

Juvencio - Did you change permissions on the *.run file to make it executable?
```
chmod a+x ./NVIDIA*.run
```

chmod: cannot access `./NVIDIA*.run': No such file or directory

---

### Post by Juvencio on 2008-09-17
> **philinux said:**
> Open system>admin>software sources. and make sure the top 4 are ticked.

allredy ticked thanks!

---

### Post by Perfect Storm on 2008-09-17
I would also recomment the ENVY instead;

But if you want to installed it manually; note, every time the kernel get patch or upgraded you need to do it again.


```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo apt-get install build-essential xserver-xorg-dev linux-headers-`uname -r`

```

press <ctrl>+<alt>+<F1>
Now you're in CLI

```
cd <path of the nvidia file>
sudo /etc/init.d/gdm stop
sudo sh <nvidia file>
sudo nano /etc/X11/xorg.conf


```

Check if the driver have changed from nv to nvidia. If it aren't change it. You can always change it back if it doesn't work.

```
sudo /etc/init.d/gdm start
```

---

### Post by Juvencio on 2008-09-17
if i revert back to the 32 bit ubuntu, waht will i be missing in the 64 bit ubuntu?

---

### Post by nowshining on 2008-09-17
u downloaded to the desktop so:

chmod a+x /Desktop/NVIDIA*.run

u can use tab completion just press TAB


now cd to the desktop 

cd Desktop

then ./NV<tab key>

---

### Post by Perfect Storm on 2008-09-17
> **Juvencio said:**
> if i revert back to the 32 bit ubuntu, waht will i be missing in the 64 bit ubuntu?

Installing Nvidia is exactly the same as in 32-bit as 64-bit. So I can't see why you change.

---

### Post by Juvencio on 2008-09-17
**[COLOR="Red"]Artificial Intelligence[/COLOR]**

while that is doing its stuf. pleas can you explane what I'm doing?

sudo apt-get update && sudo apt-get upgrade
do i need to do this often?

sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
ok this one I was looking for! updating my nvidia-kernel-common.

sudo apt-get install build-essential xserver-xorg-dev linux-headers-`uname -r`
hu?

cd <path of the nvidia file>
sudo /etc/init.d/gdm stop
sudo sh <nvidia file>sudo nano /etc/X11/xorg.conf

I tryed CLI (what dose CLI stand for) and it says (No such file or directory)
this is my path, maybe thears somthig missing?
/home/juvencio/Desktop/linux/NVIDIA

sudo /etc/init.d/gdm start
dose this just chek if my driver have changed?

---

### Post by nowshining on 2008-09-17
cli = command line interface

did you go to a tty

ctrl+alt+f1-f6 and F7 to come back to a gui

stop gdm from there

cd /home/juvencio/Desktop/linux/

chmod + x NVIDIA-Linux-x86_64-173.08-pkg2.run

sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run

or

sudo ./NVIDIA-Linux-x86_64-173.08-pkg2.run

and follow the instructions :)

edit: then sudo /etc/init.d/gdm start and you should be back to a gui...

---

### Post by ethoxyethaan on 2008-09-17
Cd to the directory the file is in then:

```
sudo chmod +x NVIDIA-Linux-x86_64-173.08-pkg2.run
```

i believe you have no idea what you are doing and i suggest you follow this Helpme page and stop what your doing right now.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by Juvencio on 2008-09-17
> **nowshining said:**
> cli = command line interface

did you go to a tty

ctrl+alt+f1-f6 and F7 to come back to a gui

stop gdm from there


tty?

I logout then hit Ctrl+Alt+F1 or Ctrl+Alt+F1+F6+F7 (my poor fingers)

then

 & sudo /etc/init.d/gdm stop
Ill try that in about 15 min or so just wating for sudo apt update/upgrade

---

### Post by nowshining on 2008-09-17
u don't have to specifically logout - :) all running programs should continue to remain in RAM and running. ;)

---

### Post by Juvencio on 2008-09-17
> **ethoxyethaan said:**
> Cd to the directory the file is in then:

```
sudo chmod +x NVIDIA-Linux-x86_64-173.08-pkg2.run
```

i believe you have no idea what you are doing and i suggest you follow this Helpme page and stop what your doing right now.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I'v bean doing fine in the 32 bit Ubuntu
and I'v tride the NvidiaManual. it dose not work for me!
maybe its just an update or somthig I'm missing
following AI's advice seeing if it gets me anyware.
I speend a long time trying to solve my own problem befor asking a Q:
so not to waste you people's time (the people that help others on thear own time)

thank you to all of you
still trying to see if i will get it done.

---

### Post by phidia on 2008-09-17
The question/info missing from this thread IMO is what model nvidia card are you trying to get running? If it's an 8 or 9 series card eg(8400 to 9600) there are many threads in the forums about problems getting those configured in 8.04 and yes even envy fails for some reason (kernel bug?) to get them working.

I recently tried to help someone with the series nvidia card I'm referring to and he said he had tried everything. He upgraded to testing (ibex) and it works now.

I know not everyone with 8 & 9 series cards have problems but quite a few do.

Added: For that matter the System > Administration > Hardware Drivers tool is suppose to recognize and enable the driver for nvidia cards but it is failing to do that in many cases (specifically these 8 & 9 series cards I think).
Recommending envy or other methods doesn't allow this bug to get exposed appropriately.

---

### Post by Juvencio on 2008-09-17
> **nowshining said:**
> u don't have to specifically logout - :) all running programs should continue to remain in RAM and running. ;)

how do i get back all i now what to do is sudo reboot

---

### Post by phidia on 2008-09-17
> **Juvencio said:**
> how do i get back all i now what to do is sudo reboot

Try Alt+Ctrl+F7 that should bring you back.

---

### Post by Juvencio on 2008-09-17
> **phidia said:**
> The question/info missing from this thread IMO is what model nvidia card are you trying to get running? If it's an 8 or 9 series card eg(8400 to 9600) there are many threads in the forums about problems getting those configured in 8.04 and yes even envy fails for some reason (kernel bug?) to get them working.

I recently tried to help someone with the series nvidia card I'm referring to and he said he had tried everything. He upgraded to testing (ibex) and it works now.

I know not everyone with 8 & 9 series cards have problems but quite a few do.

Added: For that matter the System > Administration > Hardware Drivers tool is suppose to recognize and enable the driver for nvidia cards but it is failing to do that in many cases (specifically these 8 & 9 series cards I think).
Recommending envy or other methods doesn't allow this bug to get exposed appropriately.

2X Nvidia 7 gt series sly yes i know sly is not seported but i still run xp for my games and AutoCAD 2008

System > Administration > Hardware Drivers dose not show anything but i can't change my visual effects

in Ubuntu 8 32 bit the System > Administration > Hardware Drivers worked

---

### Post by Juvencio on 2008-09-17
ok 
> sudo /etc/init.d/gdm stop
commond not found.
Now that wont work and all I'v done is update Ubuntu

---

### Post by phidia on 2008-09-17
SLY? You mean SLI?? You have two cards..hmmm actually SLI does work in ubuntu according to posts in the multimedia & video forums, but I don't have that setup you should do a search in the forum there. I did a search for SLI [here]("http://ubuntuforums.org/search.php?searchid=48173922") are the results.

---

### Post by Juvencio on 2008-09-17
Hit CTRL+ALT+F1

> $ sudo /etc/init.d/gdm stop

OK it stoped

CD~ ok it worked

> 
$ sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run

yes yes yes it starts 

  ERROR: nvidia-installer must be run as root

oh what a let down ill cary on tomorrow its 10:30pm for me and i gota get up at 4am but ill maybe push it to 5am

---

### Post by nowshining on 2008-09-17
try this: sudo /bin/bash and insert ur pw, oow try to run the nvidia installer...and if it works make sure you exit the root prompt before restarting gdm..

---

### Post by Juvencio on 2008-09-18
[code]sudo /bin/bash[/QUOTE] works in my terminal when still in gdm.
but as soon as i enter the CL it can't find command!

I'll try to logout and see if I can get it right.

[ERROR] sudo: bin/bash: command not found
 [/QUOTE]
any ideas around or just keep hacking at it

PS howe can I thank you guys????????????

---

### Post by Perfect Storm on 2008-09-18
There's a medal in the right buttom of each post.

---

### Post by Juvencio on 2008-09-18
> **Tatty said:**
> I would highly recommend installing your drivers from the repos with either System->Administration->Hardware Drivers,  or with envyNG.

I looked up EnvyNG

I found what I'm looking for, problem solved!!!!!

How do I Install EnvyNG

EnvyNG remove
> sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy

Install EnvyNG
> sudo apt-get install envyng-gtk

find EnvyNG in Applications/System Tools

I found this at
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Thanks to Alberto Milone

Ubuntu is an ancient African word, meaning "humanity to others".
Ubuntu also means "I am what I am because of who we all are". 

=D>

---

### Post by TheLions on 2008-09-18
> **Juvencio said:**
> Hit CTRL+ALT+F1


OK it stoped

CD~ ok it worked



yes yes yes it starts 

  ERROR: nvidia-installer must be run as root

oh what a let down ill cary on tomorrow its 10:30pm for me and i gota get up at 4am but ill maybe push it to 5am

type this instead:

```
sudo su
```
```
./NVIDIA-Linux-x86_64-173.08-pkg2.run 
```

---

### Post by Juvencio on 2008-09-18
TheLions thanx that dose it

---

