---
title: "Installing Displaylink Software"
date: 2021-06-23
forum: New to Ubuntu
---

### Post by jackdusty on 2021-06-23
Hi,

Trying to install the Displaylink Software but having terrible trouble (See screenshot) - as yet I dont have the Linux experience to get around this - can any kind sole please take a look and tell me what I am doing wrong - I need to get my external monitors working as a matter of urgency.

Thanks in advance of your help


Jack

---

### Post by monkeybrain20122 on 2021-06-23
First of all you need to make the .run file executable, just right click it, choose Properties > Permission and check the box allowed to run

Since you have already cd to the Downloads folder where the .run file is, you just do

```

sudo ./displaylink-driver-5.4.0-55.153.run
```


Just a note for sudo here, while drivers usually needed to be installed into the system, sudo is probably required in this instance. But if you are installing third party software, mostly you can just install in your $HOME and sudo is not needed. There are many online tutorials that abuse sudo, which can be a security risk when you install third party software.

P.S common external monitors usually  don't need any third party driver in Linux. Am I missing something?

---

### Post by jackdusty on 2021-06-25
OK the attached picture is what I get when I try your suggestion.

What I am trying to do is attach my HP Probook via a Dell 6000 Docking station to a keyboard, mouse, camera, headphones and two monitors. The Dell website says this is possible because the D6000 is a universal dock and can I add it works with Windows 10 fine. I am following these instructions from the Displaylink website:-

 [https://support.displaylink.com/knowledgebase/articles/1944022-how-to-install-displaylink-software-on-ubuntu-20-0](https://support.displaylink.com/knowledgebase/articles/1944022-how-to-install-displaylink-software-on-ubuntu-20-0)

This is really blowing my mind now trying to get them working for a week, this may be a make or break for Ubuntu for me. - Some did suggest upgrading the firmware on the dock and I have done that but it made no difference.

Can someone help please

---

### Post by monkeybrain20122 on 2021-06-25
Yeah but your .run file was in Downloads from our first screenshot, so

```
cd ~/Downloads


sudo ./displaylink-driver-5.4.0-55.153.run
```

Also don't forget to make the .run file executable first.

---

### Post by jackdusty on 2021-06-25
Oh God what have I done now ?

---

### Post by monkeybrain20122 on 2021-06-25
capital D in 'Downloads'. Linux is case sensitive

Edited: so maybe you mistyped the name of the .run file too, that's why you keep getting command not found. Make sure you get the capital and small letters right.

---

### Post by jackdusty on 2021-06-26
Wuppee It working many thanks  for all your help and patience

---

### Post by swapnilkhandagale on 2021-07-15
I have installed displaylink-driver-5.4.0-55.153 but It is not detecting any of the monitors, When I tried to connect monitors directly it got connected but while using Docking station it failed not sure where I messed up. Can you please help

---

### Post by mgknp1101 on 2021-07-19
[COLOR=#000000][INDENT]Edited: so maybe you mistyped the name of the .run file too, that's why you keep getting command not found.how to create website in php framework install CodeIgniter like to configure project is that [al-baik ]("https://www.al-baik.com/")for client but dont get how to configure xampp in linux ubuntu ???????? [/INDENT]
[/COLOR]

---

### Post by ahpitre on 2021-07-22
Be warned that DisplayLink driver does not work if your computer uses UEFI secure boot. Display Link company only provides an unsigned driver, unsigned drivers are not loaded when booting LINUX in UEFI secure boot mode. I've been having this issue for more than 1 year, tried many flavors of LINUX, attempted some steps to sign the driver, to compile/add driver to the kernel, etc., results are the same (doesn't work).

For those who ask what is Display Link and why it's needed, Display Link driver allows many docking stations to use multiple monitors (for example I have a Plugable 3.0 USB Type C docking station). Many docking stations do not enable multi-display capabilities thru firmware, rather, they use the Display Link driver. On Windows 10 it works out of the box w/o issues (I have it in my Dell work laptop and my personal Lenovo IdeaPad). Too bad as this precludes me from using Linux.

---

