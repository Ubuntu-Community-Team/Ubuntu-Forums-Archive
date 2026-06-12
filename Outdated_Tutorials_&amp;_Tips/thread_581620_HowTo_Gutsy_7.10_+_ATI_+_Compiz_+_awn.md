---
title: "HowTo: Gutsy 7.10 + ATI + Compiz + awn"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Goshawk on 2007-10-19
Hi,
This is a simple howTo to make your ati card working on ubuntu gutsy 7.10.

[SIZE=5]Install the ATI driver

[/SIZE] First of all you have to install the restricted ati driver. to do so go to
** System->Administration->Restricted Drivers Manager**
and enable the proprietary ATI driver, The package manager will download some packages from the internet, then it will ask for a reboot. **Reboot your pc**.

When the computer starts, login and see again the Restricted Drivers Manager, you should see something like this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46866&stc=1&d=1192813886[/IMG]

[SIZE=5]Install XGL

[/SIZE]Now you can install XGL to make compiz working doing these simple steps:
```
sudo aptitude install xserver-xgl compizconfig-settings-manager
```Now you can press CTRL+ALT+BACKSPACE to restart the X daemon or just reboot your machine. When X will be up you will use Xgl and compiz will be enabled by default.
To customize the active plugins go to:
** System->Preferences->Advanced Desktop Effects Settings**
A new window will be prompted and you can enable the plugins. here is a list of plugins that will make you life easier (and cool):[LIST]
[*]enhanced zoom desktop
[*]desktop cube
[*]expo
[*]rotate cube
[*]show desktop
[*]viewport switcher
[*]widget layer
[*]animations
[*]cube reflection
[*]fading windows
[*]window decoration
[*]window previews
[*]jpeg
[*]png
[*]svg
[*]text
[*]cube caps
[*]dbus
[*]regex matching
[*]scale window title filter
[*]scale window title filter
[*]video playback
[*]scale addons
[*]inotify
[*]glib
[*]resize info
[*]crash handler
[*]application switcher
[*]extra wm actions
[*]group and tab windows
[*]move window
[*]place windows
[*]scale
[*]snapping windows
[*]resize window[/LIST]But you can also enable all plugins if you are brave.

[SIZE=6]Installing awn
[SIZE=2]To install [awn]("http://njpatel.blogspot.com/2007/10/01-01.html") edit your** /etc/apt/sources.list** and add
[SIZE=2] ```
deb http://repo.freecreations.info/ubuntu gutsy freeverse
```[/SIZE][/SIZE][/SIZE]Then do:
```
sudo aptitude update && sudo aptitude install avant-window-navigator awn-core-applets awn-manager
```And then you will have awn installed, you can start it from
**Applications->Accessories->Avant-window-navigator**
To make it loaded by default at startup go to
**System->Preferences->Sessions**
Click on **add** and type:
name: awn
command: avant-window-navigator

This howto is finished, have a nice day!

---

### Post by Vorin on 2007-10-28
didn't work for me

[http://img233.imageshack.us/img233/5573/awnfailvc0.png](http://img233.imageshack.us/img233/5573/awnfailvc0.png)

---

### Post by TwiceOver on 2007-10-28
> **Vorin said:**
> didn't work for me

[http://img233.imageshack.us/img233/5573/awnfailvc0.png](http://img233.imageshack.us/img233/5573/awnfailvc0.png)u'

You will need to update your repository list before downloading.

sudo apt-get update

---

### Post by Vorin on 2007-10-28
working perfectly, thank you for your timely response.

---

### Post by teishu on 2007-10-31
good tut ! Thanks mate

---

### Post by studo77 on 2007-10-31
Does this not work in 64bit?

I get this on apt-get update:
```
http://repo.freecreations.info/ubuntu/dists/gutsy/freeverse/binary-amd64/Packages.gz 404 Not Found
```

404 Not Found

Any help, please.

---

### Post by Harry789 on 2007-10-31
Is this new 7.10 restricted driver manager catching the latest ATI driver or is it the old 8.40 ?

What version of ATI driver is installed with the above process?

---

### Post by studo77 on 2007-11-01
> **Harry789 said:**
> Is this new 7.10 restricted driver manager catching the latest ATI driver or is it the old 8.40 ?

What version of ATI driver is installed with the above process?

It is not latest 8.42.3 if that is your question. Not too sure about the actual version, but my guess is the 8.40 as in Feisty.

---

### Post by linuxrotta on 2007-11-01
I finally got this working, I have a Mobility Radeon x700 card. 
This is what I did  to get compiz working:

* Install the latest driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html). I installed the version 8.42.3

*After restarting, which took a while, i ran the following command:
sudo aptitude install xserver-xgl compizconfig-settings-manager

*Restarted again, and now compiz works perfect:guitar:

My only problem now it is that it takes about 3 min to boot up  my computer.
Does anyone have a solution to this?

---

### Post by dragonlor20 on 2007-11-01
> **linuxrotta said:**
> I finally got this working, I have a Mobility Radeon x700 card. 
This is what I did  to get compiz working:

* Install the latest driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html). I installed the version 8.42.3

*After restarting, which took a while, i ran the following command:
sudo aptitude install xserver-xgl compizconfig-settings-manager

*Restarted again, and now compiz works perfect:guitar:

My only problem now it is that it takes about 3 min to boot up  my computer.
Does anyone have a solution to this?


This page should fix your long boot time. From what I have seen it is due to the system trying to load the usplash at the wrong resolution. [http://ubuntuforums.org/showthread.php?p=3686238#post3686238](http://ubuntuforums.org/showthread.php?p=3686238#post3686238)

---

### Post by Goshawk on 2007-11-03
> **studo77 said:**
> Does this not work in 64bit?

I get this on apt-get update:
```
http://repo.freecreations.info/ubuntu/dists/gutsy/freeverse/binary-amd64/Packages.gz 404 Not Found
```

404 Not Found

Any help, please.

Sorry no amd64 support in this repo yet. We are working for it :)

---

### Post by Unicast on 2007-11-03
This is nice, thank you!

---

### Post by derbouka on 2007-11-03
Hello, I've followed this HowTo, but I'm getting this:
```
$ awn-applet-activation

** (awn-applet-activation:8799): WARNING **: You need to provide a uid for this applet

```
Does anyone know how to solve this?

---

### Post by Donnie Darko on 2007-11-04
how do I install into my sources list?
To install awn edit your /etc/apt/sources.list and add
Code:

deb [http://repo.freecreations.info/ubuntu](http://repo.freecreations.info/ubuntu) gutsy freeverse

---

### Post by Goshawk on 2007-11-04
> **derbouka said:**
> Hello, I've followed this HowTo, but I'm getting this:
```
$ awn-applet-activation

** (awn-applet-activation:8799): WARNING **: You need to provide a uid for this applet

```
Does anyone know how to solve this?

why are you running awn-applet-activation and not avant-window-navigator?

---

### Post by Donnie Darko on 2007-11-04
Can anyone tell me how to add to the sources list????
I don't undertand what I do with this
/etc/apt/sources.list

---

### Post by Goshawk on 2007-11-04
> **Donnie Darko said:**
> Can anyone tell me how to add to the sources list????
I don't undertand what I do with this
/etc/apt/sources.list


just do
```
sudo gedit /etc/apt/sources.list
```

and then add the line described in the howTo to enable the freecreations repository.

---

### Post by derbouka on 2007-11-04
> **Goshawk said:**
> why are you running awn-applet-activation and not avant-window-navigator?Because I thought that that was the program that I should run..](*,)
Ok, the problem was that I hadn't the compiz running.. 

Now it's working, but I believe that it should have some visual popup or something, saying why it couldn't run..
I tried to run it from the "Accessories > Avant Window Manager", and I didn't get any information about the problem..
Only when I run it from the console, I could see what the problem was:
```
$ avant-window-navigator 
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```

---

### Post by kidguayas on 2007-11-04
I wonder how to install awn in a Amd64 my ATI card is a All-in-Wonder pro X600
One more thing how can I install the  drivers from ATI the latest version. I am kind of new this if anyone knows about a tutorial could you let me know

Any help please
Thanks

---

### Post by Goshawk on 2007-11-17
> **kidguayas said:**
> I wonder how to install awn in a Amd64 my ATI card is a All-in-Wonder pro X600
One more thing how can I install the  drivers from ATI the latest version. I am kind of new this if anyone knows about a tutorial could you let me know

Any help please
Thanks

If you want amd64 support please add this line to your sources.list:
deb-src [http://repo.freecreations.info/ubuntu](http://repo.freecreations.info/ubuntu) gutsy freeverse

and then do:
apt-get source avant-window-navigator
cd avant-window-navigator-"version"
debuild

then email me all the packages created at [email]vincenzo.ampolo@gmail.com[/email] . I'll add to the repo....

---

### Post by broadbeans on 2008-04-13
Thanks, AWN works perfectly for me. I have ATI Xpress 200 on a Athlon 64 MSI RS480 mobo.  Compiz has already been enabled via another HOWTO.  :guitar:

However, I can't get the curves to work as it does not allow me to enter -1 for the bar angle.  Any ideas?

---

