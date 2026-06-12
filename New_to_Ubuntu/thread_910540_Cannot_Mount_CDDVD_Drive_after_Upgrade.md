---
title: "Cannot Mount CD/DVD Drive after Upgrade"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by klezfire on 2008-09-04
Hello, I am quite new to Ubuntu and all of linux for that matter however I am highly experienced with Windows. Anyways here is my problem... I tried to install Ubuntu 8.04 using the Live CD however I couldn't get it to load blah blah blah. So I used Ubuntu 7.10 (Fiesty) to install it on my computer and it was working "ok". My DVD Burner was working at this time. Anyways I proceeded to upgrade to Ubuntu 8.04 which is installed right now and working GREAT excpept the fact that when I go to use my DVD Drive it says this "Unable to mount location" "Cannot mount file". Any idea to why this isn't working, I have verified my DVD Drive is physically working because I can boot off from the Ubuntu 7.10 Disc. Any help would be greatly appreciated!

*Update* Not sure if this helps but if I click on the CD/DVD drive Icon it says "No media".
 
***I have posted this in Instalation and Upgrades, but because I am a newbie I thought that this should be in this section, sorry for the double post***

---

### Post by HunterA3 on 2008-09-04
Not sure if this is the best way to go about it, but I'd look in the /media directory and see what drives are listed. Then pull up the console and perform the following:

```
sudo mount /media/<name of drive>
```
Enter your root password and see what it tells you.

---

### Post by HunterA3 on 2008-09-04
Oh and if you've got multiple optical drives and they are listed with similar names I'd try this to identify the drive:

```
sudo eject <name of drive>
```

The one that opens is the drive you're talking to. :)

---

### Post by klezfire on 2008-09-04
That Gave me this:

klezfire@OX2L:~$ sudo mount /media/ "CD-RW/DVD±RW Drive"
mount: mount point CD-RW/DVD±RW Drive does not exist
klezfire@OX2L:~$ 



The name of the Drive is: "CD-RW/DVD±RW Drive" under Computer.

---

### Post by knattlhuber on 2008-09-04
The drive would rather have a name like cdrom0 or dvd0.

What does

```
ls /media -l
```

give you?

---

