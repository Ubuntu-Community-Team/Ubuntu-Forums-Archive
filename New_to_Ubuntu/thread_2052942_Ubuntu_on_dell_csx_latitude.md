---
title: "Ubuntu on dell csx latitude"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by Not install on 2012-09-04
Hi guys I'm trying to install ubuntu 12.04 for the last week but it's a no go

Why is it doing this I have installed Ubuntu on many machines in the past 

It's just on this screen heres the link          [http://i.imgur.com/5Qoof.jpg](http://i.imgur.com/5Qoof.jpg)   For the last hour and does this all the time does not get past this from the love cd

Now I am frustrated

I have tried no apci and modeset=1 and also Pci=Nomsi

But nothing what's wrong here helppppppppppp please

Using dell latitude csx laptop

---

### Post by Not install on 2012-09-04
Can anyone help me here please there's lots of experts here it's still on that screen

---

### Post by black veils on 2012-09-04
please be patient, people are in different time-zones, and ultimately are using their free time to help on the forums.


try using the mini.iso instead to install:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


you can see what happens, in this video, choose the desktop you want during install:
[http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main](http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main)


EDIT:

do you know what ram you have?

if it is **512mb - 1gb**, you should use the **xubuntu** or **lubuntu** desktop choice, lubuntu is lighter and may be necessary.

if it is **256mb**, you should install** bodhi linux** [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

[I]
you will want to do this tweak after the system is installed:[/I]

To change swappiness into a more sensible value, open the Terminal and copy-paste:
```
gksudo gedit /etc/sysctl.conf
```(replace gedit in the code, with the text editor on your system, like leafpad)

press Enter key

Scroll to the bottom of the text file and add your swappiness parameter to override the default, so copy/paste the following lines:
```
#
# Decrease swap usage to a workable level
vm.swappiness=10
```Close the text file and reboot your computer.

After the reboot, check the new swappiness value:
open the Terminal and copy-paste:
```

cat /proc/sys/vm/swappiness
```press Enter key

Now it should be the chosen new value.

---

### Post by Not install on 2012-09-04
> **black veils said:**
> please be patient, people are in different time-zones, and ultimately are using their free time to help on the forums.


try using the mini.iso instead to install:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


you can see what happens, in this video, choose the desktop you want during install:
[http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main](http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main)


EDIT:

do you know what ram you have?

if it is **512mb - 1gb**, you should use the **xubuntu** or **lubuntu** desktop choice, lubuntu is lighter and may be necessary.

if it is **256mb**, you should install** bodhi linux** [http://www.bodhilinux.com/](http://www.bodhilinux.com/)


Thank you will try the points suggested

---

### Post by Not install on 2012-09-05
Guys the mini Ubuntu is not nstalling I need help I got the desktop 12.04

But it just hangs

Even tried Linux mint not installing is something wrong with the dell latitude csx that keeps it from installing Linux?

Do I have to tweak it or something I never had this happen before what's going on its nuts please help all I want to do is install Ubuntu on this laptop

---

### Post by Hadaka on 2012-09-05
Hi, I've had this same issue with several Dell laptops when trying to load 12.04.
providing you have correctly burned your 12.04 LTS iso package, press F2 on boot,
go into bios...disable the wireless pci setting. Then from a wired connection, try to
load again, IF it loads correctly, then enter ->

```
lspci -nnk | grep -iA2 net 
```

this wil give you the information on the wireless card to install the correct drivers.
good luck.

---

### Post by Not install on 2012-09-05
> **Hadaka said:**
> Hi, I've had this same issue with several Dell laptops when trying to load 12.04.
providing you have correctly burned your 12.04 LTS iso package, press F2 on boot,
go into bios...disable the wireless pci setting. Then from a wired connection, try to
load again, IF it loads correctly, then enter ->

```
lspci -nnk | grep -iA2 net 
```

this wil give you the information on the wireless card to install the correct drivers.
good luck.

Oh is the pci setting on the dell laptop  affecting the way Ubuntu desktop 12.04 is installing freezing at install point?

Hadika are you saying to install by disable wireless what the wired connection for I thought buntu desktop 12.04 does not need a Nernst connection? Am I right can you explain a bit further on your helpful answer thanks

Why would. Need a wired connection?

---

### Post by black veils on 2012-09-05
wireless drivers or lack of, can cause problems during installing Ubuntu

---

### Post by Not install on 2012-09-05
> **black veils said:**
> wireless drivers or lack of, can cause problems during installing Ubuntu

Oh ok thanks but do I have to be connected wired to the internet to nstall ubuntu as suggested by Haida?

---

### Post by Bashing-om on 2012-09-05
I have not had a problem prior to the newer kernels with installing with no internet connection...... however the newer kernel installs have the option to do the needed updates, and install the non-propriatary drivers during the installation. If you try to install with out a internet connection ......suggest be sure these options are not enabled.

Another consideration, some of those old dells only has a 10 gig hard drive ..are you good in that respect now?
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Hadaka on 2012-09-05
Hi the reason i suggested having a wired connection was not for the initial loading
of 12.04, but for loading the correct driver if that was in fact what was 
causing your problem. Most older dells require the b43 driver, on first load you
will sometimes get an error requesting that driver,other times the error doesnt
display. It just hangs with the 4 lights blinking...forever. also with a successful load
of the 12.04 you will then need all the updates and security releases. These updates
many times "fix" alot of issues that cause problems. It is possible to load correct
wireless drivers without an internet connection,but it at some point you will need
to load all the updates anyway. If you continue to have problems loading you might
want to consider loading ubuntu 11.10, it loads without hanging up even if the b43 dirver
is missing, atleast this has been my experience with  a few older dell laptops.

---

### Post by Bashing-om on 2012-09-06
+1 Hadaka !
[INDENT]BDQ
[/INDENT]

---

### Post by Not install on 2012-09-06
> **Bashing-om said:**
> +1 Hadaka !
[INDENT]BDQ
[/INDENT]

Hi in respects to your suggestions there is no pci settings in the bios?

Please help I'm getting lost

---

### Post by Hadaka on 2012-09-06
Hi, to find your pci status in bios...

when booting up press F2
at bios screen .. arrow down to onboard devices
press enter at onboard devices
arrow down to miniPCI status
press enter
left arrow to OFF
press enter
press esc key
arrow right to save/exit

do the opposite to turn it back on after you load.

---

### Post by Not install on 2012-09-06
> **Hadaka said:**
> Hi, to find your pci status in bios...

when booting up press F2
at bios screen .. arrow down to onboard devices
press enter at onboard devices
arrow down to miniPCI status
press enter
left arrow to OFF
press enter
press esc key
arrow right to save/exit

do the opposite to turn it back on after you load.

Had aka are you sure this option s in my bios?

---

### Post by Hadaka on 2012-09-06
Hi, lets rewind here, your original post was that the screen freezes with the 4
blinking lights when you try to load 12.04. A very common reason for this  with dell
is caused by the wireless card needing the correct driver. Turning off the card was a
suggestion for a "possible" resolution to your problem. Trouble shooting a problem
has to start somewhere, your issue could be caused by something not related to the
wireless card. Now you are having difficulty navigating in bios. If...you do even have 
a pci-wireless card it will show up in bios. I would suggest you go online and download
a users manual for your laptop to verify what possible configuration your model has.
when you are at the point where you want to throw your computer against the wall,
this is a good thing, it means you are trying and while doing so,you are learning.

---

### Post by Not install on 2012-09-06
> **Hadaka said:**
> Hi, lets rewind here, your original post was that the screen freezes with the 4
blinking lights when you try to load 12.04. A very common reason for this  with dell
is caused by the wireless card needing the correct driver. Turning off the card was a
suggestion for a "possible" resolution to your problem. Trouble shooting a problem
has to start somewhere, your issue could be caused by something not related to the
wireless card. Now you are having difficulty navigating in bios. If...you do even have 
a pci-wireless card it will show up in bios. I would suggest you go online and download
a users manual for your laptop to verify what possible configuration your model has.
when you are at the point where you want to throw your computer against the wall,
this is a good thing, it means you are trying and while doing so,you are learning.

That's right but there's no wireless card to begin with so it brings us back to why it will not install nstead of going on a wild goose chase the problem I'm having is why it will not install

---

### Post by Not install on 2012-09-06
> **Not install said:**
> That's right but there's no wireless card to begin with so it brings us back to why it will not install nstead of going on a wild goose chase the problem I'm having is why it will not install

Ok guys I managed to start the live cd  using the no modest By pressing f6 then crossing no mode set

But can anyone explain what it's doing at the moment it has got ata2 complete drdy and son on is this normal as I have only used the GUI method of installing before and this is new to me I don't exactly know what's going on here

Can anyone please explain

At the moment it stop at ata2eh complete then loops at the same message again is it installing or something wrong here?

Because I'm going to turn the laptop off because I think it's just going in a loop and nothing installing the same message eh complete?..

---

