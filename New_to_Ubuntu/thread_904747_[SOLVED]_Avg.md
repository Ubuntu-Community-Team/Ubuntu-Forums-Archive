---
title: "[SOLVED] Avg"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bj218 on 2008-08-29
I am unable to update AVG. When I clk on update I get a message "you do have permission to execute". When I enter my Ubuntu PW I get a message Authentication invalid PW. What can I do to get AVG up to date?

---

### Post by WRDN on 2008-08-29
It sounds as though you need root privileges, so open the Terminal and type:

```
sudo avg
```

I don't use the program, so am not entirely sure of the application name. If it is in one of the menu's, then right click on one, select "Edit Menu", find AVG and right click on the entry. Select Properties, and the application name is listed in the text box for "Command:".

---

### Post by nicedude on 2008-08-29
I would uninstall AVG unless you are using it to scan a windows partition and if so you could just use AVG in windows to do so. Linux right now is immune to virus attacks as there are zero viruses in the wild that can affect it ( I have read there are like 40 proof of concepts in labs etc but compare that to 40,000 that are in the hands of script kiddies everywhere and you see the danger factor for Ubuntu is nill ). That is why for Ubuntu all the virus scanners can only find windows viruses and so for the most part they are not needed as you can simply scan windows from windows, the one exception I know of is if you are running a linux OS email server and want something to scan all the mail for windows viruses then you need it.

It was hard for me to get used to not having AV running all the time but now I don't even miss it at all :-)

---

### Post by SunnyRabbiera on 2008-08-29
Right there is little need to have antivirus on a linux system unless you run a mailserver or something like that, but its more for the protection of windows computers then yours.

---

### Post by emshains on 2008-08-29
> **nicedude said:**
> I would uninstall AVG unless you are using it to scan a windows partition and if so you could just use AVG in windows to do so. Linux right now is immune to virus attacks as there are zero viruses in the wild that can affect it ( I have read there are like 40 proof of concepts in labs etc but compare that to 40,000 that are in the hands of script kiddies everywhere and you see the danger factor for Ubuntu is nill ). That is why for Ubuntu all the virus scanners can only find windows viruses and so for the most part they are not needed as you can simply scan windows from windows, the one exception I know of is if you are running a linux OS email server and want something to scan all the mail for windows viruses then you need it.

It was hard for me to get used to not having AV running all the time but now I don't even miss it at all :-)

Its hard to scan windows from windows, if a virus is corrupting the boot files, or in any other way interrupting the boot up or just making the scanning process just as slow as HELL!

---

### Post by jamesrfla on 2008-08-29
The only reason why you would need AVG is to scan a windows partition or if you are sharing files between two windows computers with Ubuntu in the middle and want to scan for virus before you pass it to the other windows computer. Other than that you don't need it.

---

### Post by Orwell on 2008-08-29
Some people say that you could possibly use AV in Ubuntu to 'protect your Windows-using friends'...

IMO it's a good thing when your Windows friends catch one of the many nasties out there because you can then point to how great Ubuntu is in comparison!

Just a thought...

---

### Post by bruce89 on 2008-08-29
> **Orwell said:**
> Some people say that you could possibly use AV in Ubuntu to 'protect your Windows-using friends'...

IMO it's a good thing when your Windows friends catch one of the many nasties out there because you can then point to how great Ubuntu is in comparison!

Just a thought...

That's a bad way to do something that I find odious anyway.

---

### Post by iansane on 2008-08-29
I used avg for linux to scan my windows partition because it worked while windows was not booted  but would not work from windows while it was booted, so there's one good reason to have a updated avg on linux.

Sometimes the way to get a virus is to get it while it is sitting still. No processes are running at all if the partition or drive is not booted up. I used kapersky on windows with usb adapter to succesfull clean other peoples hard drives before and that worked well too.

---

### Post by bj218 on 2008-08-31
I am currently running a multi boot sys. I have Ubuntu and Mint on one drive and WindowsXP Pro. on another drive. I have used AVG on Windows for a long time. If avg is not necessary on Linux systems how do I remove it, I also have been using the ZoneAlarm firewall for a long time on Windows do I need something like this for my Linux systems?

---

### Post by lisati on 2008-08-31
Here's the solution to update difficulties, as taken from the AVG forums, the documentaion, and posts on these forums:

> Add your Ubuntu user to the avg user group, then log off, then log on again.

That's all you need to do, no messing around with sudo or gksudo. Google is your friend.

EDIT: See [here]("http://ubuntuforums.org/showthread.php?t=889552")

---

### Post by JazonEsti on 2008-08-31
What I did was before create a launcher then edited it so that it launches as 
```
gksudo avg
```
(or just add gksudo before whatever launches it)

Works everytime.

---

### Post by billgoldberg on 2008-08-31
> **bj218 said:**
> I am currently running a multi boot sys. I have Ubuntu and Mint on one drive and WindowsXP Pro. on another drive. I have used AVG on Windows for a long time. If avg is not necessary on Linux systems how do I remove it, I also have been using the ZoneAlarm firewall for a long time on Windows do I need something like this for my Linux systems?

You normally don't need an firewall running in Ubuntu, unless you are running some kind of server.

If that is the case I suggest you use UFW. It is command line only, but there is a great GUI for it in the form of a .deb file (double click to install) [here]("http://gufw.tuxfamily.org/index.html").

--

Just to toss it in here, if you need to scan a window partition because it can't start or is running too slow, you can just use a clamav live cd.

No need to dirty up your Ubuntu installation with something like AVG.

---

### Post by bj218 on 2008-09-02
How do I remove AVG? I also have been using ZONEALARM on my windows system
for a long time, is there a firewall program for Linux?

---

### Post by bj218 on 2008-09-04
How do I remove AVG from Ubuntu?

---

### Post by gandaran on 2008-09-04
> **bj218 said:**
> How do I remove AVG from Ubuntu?

what type of package you installed? was it a .deb, then open synaptic, look for it and mark for complete removal and click the apply button.
did you updated avg? the code for updating is **sudo avggui** it opens a root avg gui.

---

### Post by oldos2er on 2008-09-04
> **bj218 said:**
> How do I remove AVG? I also have been using ZONEALARM on my windows system
for a long time, is there a firewall program for Linux?

 You've been shown how to uninstall AVG. Ubuntu comes with a firewall, iptables, already installed.

---

### Post by mikewhatever on 2008-09-04
> **bj218 said:**
> How do I remove AVG from Ubuntu?

sudo dpkg -P -R avg75fld <- in terminal, or use Synaptic instead.

---

### Post by bj218 on 2008-09-07
> **gandaran said:**
> what type of package you installed? was it a .deb, then open synaptic, look for it and mark for complete removal and click the apply button.
did you updated avg? the code for updating is **sudo avggui** it opens a root avg gui.

The synaptic package mgr. worked great thanks.

---

