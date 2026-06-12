---
title: "Java on &quot;Live CD&quot; for Minecraft, and other issues"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by quadrplax on 2014-03-23
So, here is my situation: I have a pretty good laptop, except for the fact that the hard drive no longer works. I don't want to buy a new hard drive, so instead I installed Ubuntu on a 16GB flash drive, via the [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) installer. I set a persistent file storage (casper-rw). I then can boot into Ubuntu, and chose the run from this disk option. This takes me into the desktop. I can use it as normal. There are, however, problems eventually. The first problem is that after a few uses, (I use this USB on two computers by the way, if it matters) after selecting to boot from the boot or install menu, I get a "The system is running in low graphics mode" error. I don't have any mouse and can't seem to use the keys either, so I can't do anything about it and have to install Ubuntu from scratch again. This has made me have to reinstall three or four times. The next problem has only happened on the most recent reinstall, after a few uses I got a login screen when booting into the USB drive. If I logged on with the default user "ubuntu" with no password, it just took me back to the login screen. I added another user from the Ctrl+Alt+F1 terminal, but this user had no root access so I had to enter the password for "ubuntu" (blank) for a lot of things. This was OK, except for some things in the terminal it requires me to be "in the sudoers folder". I don't know how to do this, and I would have to do it with commands in the Ctrl+Alt+F1 terminal. Another big problem I have had is that whenever I try to open the casper-rw "hard drive", I get an error: "Unable to open /cow". This means I have a very limited storage space within /FileSystem. Lastly, when I do have things working, I cannot figure out how to install Java on Ubuntu! There are so many different methods and I can't figure out how to get any of them to work. What I want is Oracle JRE 7u51, to run Minecraft. One time I did get it to work somewhat and I was able to open the launcher with OpenJDK 7 (some thing I found in the Ubuntu store), however Minecraft gave error messages which, when I looked them up, I was suggested to reinstall Java! I don't know much about Ubuntu or Linux, and all I really want this for is browsing the web and Minecraft. I have even considered installing ChromeOS and hacking Minecraft onto that, it sounds much easier. Thank you for reading this long post, and help with all or some of these problems would be greatly appreciated! Thanks in advance.

EDIT: I'm running 32-bit Ubuntu 12.04.4 LTS, but I don't care if I need to run a different version, whatever works (it needs to be 32 bit though)

---

### Post by Impavidus on 2014-03-24
You created a live disk and you run a live session of Ubuntu. Live disks are great for testing hardware compatibility and fixing your system if it's really broken (best to keep one in your drawer), but as they lack some security features, cannot update certain components and have very limited storage available in their persistence file, they are not suited for long term usage. You could however use your live disk to create a full install on a different usb drive. Boot from the live disk, plug another usb drive in another usb port (at least 16GB, but better at least 32GB) and install to that second drive. As long as you don't install proprietary drivers or the hardware on your different compuers is compatible it should still be portable.

---

### Post by quadrplax on 2014-03-24
OK, I installed Ubuntu on a flash drive and now it is no longer a Live CD. Things seem to be working for the most part, but I still can't get Minecraft to run. I installed JRE 7u51 via this tutorial: [http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux) I did, however, get an error on step 14 (Type "/etc/profile"): If I do it without sudo, I get: "bash: /etc/profile: Permission denied" If I do it with sudo, I get: "sudo: /etc/profile: command not found". Does anyone know what the issue is? I've tried it in a root terminal and normal terminal. Do I need to set it to a specific directory or is the tutorial outdated or what?

EDIT: Forgot to mention, the problem is that I don't know how to open Minecraft.jar with JRE7, it doesn't show up in the program list for "open with"
EDIT2: "java -version" shows it as installed properly I think

---

### Post by quadrplax on 2014-03-24
Nevermind, I got it to work, I just had to launch the jar with "java -jar Minecraft.jar" from the terminal and then I could pin it to the quick launch. Thanks for the help [**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")!

---

