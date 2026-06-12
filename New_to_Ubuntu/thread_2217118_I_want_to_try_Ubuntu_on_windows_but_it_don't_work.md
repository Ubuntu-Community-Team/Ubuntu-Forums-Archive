---
title: "I want to try Ubuntu on windows but it don't work"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by bobby14 on 2014-04-15
Hello everyone :)

I'm a Windows XP user and I want to try Linux Ubuntu on windows but it don't work.

I tried with :

- LinuxLive USB Creator
- UNetbootin
- Wubi

I have not tried with VirtualBox because I have only 2gb ram.

When I start the computer, I chose the usb in the boot menu and it seems to start Ubuntu (I see the Ubuntu purple screen with Ubuntu logo but after a moment it freeze with a distorted picture of the last website a visited on Windows...bizarre.    ... and same thing with Wubi.

Is it possible it doesn't work because I have dual boot (Windows XP on disc C and D)  ?

Thanks in advance!
Bobby

P.S.  Sorry for my english, I speak french... hope it's not too bad... ;)

---

### Post by oldfred on 2014-04-15
Wubi is being discontinued. Last supported version is 12.04 as it does not work with the new gpt partitioning that all new UEFI systems have.
But I would not install wubi inside XP as wubi does rely on the Windows boot loader and the under lying NTFS file system. It is just one very large file inside Windows.

Often the type of issue you are having is related to video. What video card/chip do you have?
Also what CPU?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 To install Ubuntu, boot from the DVD & press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

Your English is fine.
But if more comfortable there is a French forum.
      
 French Forums
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

---

### Post by bobby14 on 2014-04-16
Thanks! oldfred ... I had set Nomodeset and it works.

I have another question :) ... How to enable the multiverse in Ubuntu 12.04 ?... I saw some video tutorials on the old version but I don't find it in the 12.04.

Thanks again !

---

### Post by oldfred on 2014-04-16
I use synaptic which shows all the repositories and you can add or subtract them. It is old school over Software Center.

sudo apt-get install synaptic

I looks like that same screens I see in synptic are in Software & Updates in System Settings.

---

### Post by bobby14 on 2014-04-16
I don't see Software and Updates in System Settings.[IMG]Screenshot from 2014-04-16 21:15:19[/IMG]

---

### Post by bobby14 on 2014-04-16
I want to insert an image... add an image from Url ?... I don't understand.

---

### Post by jmbell on 2014-04-16
I found this: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine). It suggests that Multiverse  can be enabled by using the *add-apt-repository* command. If your release is 'precise', you could write the following (or just the first two) into a terminal: 

```

sudo add-apt-repository "deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse multiverse"
sudo add-apt-repository "deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse" 
sudo add-apt-repository "deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse"
sudo add-apt-repository "deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse"
```

Depending on your location, you should replace 'us.' by another country  code, referring to a mirror server in your region.

Also...don't forget to retrieve the updated package lists:  ```
 sudo apt-get update 
```

Hope that helps!

---

### Post by oldfred on 2014-04-16
jmbell's suggestion will work.

I think I was in 14.04 and they created a new Software & updates icon.
Beside synaptic it also is in Ubuntu Software Center, edit, Software Sources.

You can attach screen shots with Go Advanced Editor and paper clip icon in edit panel.

---

### Post by bobby14 on 2014-04-16
The codes seems to work...not sure, when trying to install flash it don't ask to enable multiverse like before but I can't get flash installed to watch videos.
 

 I don't see edit in Ubuntu Software Center.

---

### Post by oldfred on 2014-04-16
If you move cursor all they way to the top panel, do file, edit, view & help appear?
I use flashback/fallback which is the old menu system with Ubuntu and it only has menus.

Just booted into ISO, and it is in the top panel, you have to mouse over top panel to see those menu items.

---

### Post by jmbell on 2014-04-16
I usually avoid gui package managers and the software center...just a matter of personal preference. What do you get when you use the following command in a terminal? (Hope I'm not stepping on your toes, oldfred!)
```
 sudo apt-get install flashplugin-installer 
```
You might also want to install** flashplugin-nonfree-extrasound** as well.

Cheers!

---

### Post by bobby14 on 2014-04-16
At the top of Ubuntu desktop I see (with the mouse over) File-Edit-View-Go-Help but I don't see Software Sources in Edit.
 And I have nothing at the top of Software Center panel (with the mouse over).

---

### Post by jmbell on 2014-04-16
Did you click on the software center window first? The top menu usually reflects the program currently selected. Just a thought.

---

### Post by bobby14 on 2014-04-16
Sorry jmbell I just saw your message.
 

 I have tried your code but it don't work and I would like to show you the terminal message but the message is in french ???... I don't why... the Ubuntu desktop is in english.

---

### Post by jmbell on 2014-04-16
To change your locale (the language used by the terminal), follow these instructions: [http://noldgxpert.blogspot.com/2012/06/how-do-i-change-language-via-terminal.html](http://noldgxpert.blogspot.com/2012/06/how-do-i-change-language-via-terminal.html), run the command I posted, and post the output. You'll probably need to type ```
 bash 
``` into a terminal or log off and log back on to make your settings permanent.

---

### Post by bobby14 on 2014-04-16
I click on the Ubuntu Software Center icon on left over Ubuntu One... is it the right button ?
 &#8230; it show the window as the picture I sent... but no Edit on the top window panel.

---

### Post by bobby14 on 2014-04-16
Here the message I get:

ubuntu@ubuntu:~$ LC_ALL=C bash
ubuntu@ubuntu:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 flashplugin-installer : Depends: libnspr4-0d but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$

---

### Post by monkeybrain20122 on 2014-04-16
Are you on Wubi? forget it. Make a real install and get rid of XP, it is out of support, dead. You don't run an up to date OS inside a dead one and people really shouldn't try to help you IMO

---

### Post by jmbell on 2014-04-16
I actually meant for you to click the software center window itself. But if that doesn't help you find the edit software sources described by oldfred, give this command a shot:
```
sudo apt-get clean && sudo apt-get update && sudo apt-get install -f && sudo apt-get install flashplugin-installer 
```
If it works, let us know. If not, post the output.

---

### Post by oldfred on 2014-04-16
I logged into Unity and this shows menu on very top panel.

---

