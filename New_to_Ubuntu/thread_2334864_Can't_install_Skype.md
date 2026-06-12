---
title: "Can't install Skype"
date: 2016-08-23
forum: New to Ubuntu
---

### Post by 0chk on 2016-08-23
Hello.
I'm  a total newbie who wants to see if I can work with Ubuntu. My issue is installing Skype.  I have Ubuntu 16.04 LTS and 64-bit system. I have enabled Canonical Partners. When I try to install from the Terminal I get a very long error message.  Here is a selection of screenshots. 
[ATTACH=CONFIG]270829[/ATTACH][ATTACH=CONFIG]270830[/ATTACH](Couldn't upload more, get error message"uploadin file failed")

Thank you

---

### Post by howefield on 2016-08-23
It is easier for others to help you if you post the actual terminal input/output between [code tags]("https://ubuntuforums.org/misc.php?do=bbcode") rather than posting images of the terminal.

What's the output of

```
cat /etc/apt/sources.list
```

---

### Post by 0chk on 2016-08-23
I'm sorry, but I'm totaly new to Linux and didn't udnerstand your feedback.
Terminal dispalyed more than a 100 Error messages and then a long list of "Failed to fetch".
I tried again and got:  
[U]E:  Could not open lock file /vab/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[/U]Thank you

---

### Post by grahammechanical on 2016-08-23
This is enclosed in code tags

```
[U]E:  Could not open lock file /vab/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/U]
```
It means that when you ran that command you did not put sudo in front of the command and therefore you where not requested to enter your user password. Certain tasks require us to be the administrator or "root" as it is called in Linux.

At the start of the block of text put the word code inside square brackets [ ]. At the end of the block of text put /code inside square brackets. We can do the same the word quote for a similar effect.

Regards

---

### Post by 0chk on 2016-08-23
Thank you.
I tryed again with puting sudo in front of the command.  it doesn't tell me about root anymore:) But doesn't work yet;_; 
The last line is ```
 E: Unable to fetch some archives, maybe run apt -get update or try with --fix-missing?
```.
I did run sudo apt-get update and it didn't help, sudo --fix-missing is an unrecognized option

---

### Post by banceu_sergiu_ione on 2016-08-23
> **0chk said:**
>  sudo --fix-missing is an unrecognized option

Its is ```
 sudo apt-get update --fix-missing
```

I suggest you run it using just apt and in order, first update after install, for whole install

```
 sudo apt update 
```
```
 sudo apt install skype 
```

---

### Post by 0chk on 2016-08-23
Thank you. After I run ```
sudo apt upgrade 
``` it told me >  266 pakages can be upgraded.  Run 'apt list --upgradable to see them..
I run ```
 sudo apt list --upgradable
``` and it showed me the list.
What do I do now?

---

### Post by banceu_sergiu_ione on 2016-08-23
You got that info after you had run apt update.
Run upgrade now 
```
 sudo apt upgrade 
```

---

### Post by 0chk on 2016-08-23
Tahnk you.  Did that, got the 
E: Unable to fetch some archives, maybe run apt -get update or try with --fix-missing?[COLOR=#000000]
Did the:
```

 sudo apt-get update --fix-missing
```[/COLOR]


[COLOR=#000000]```

 sudo apt update
```[/COLOR]
and ```
 sudo apt upgrade
``` again and got ```
 [COLOR=#000000][FONT=&amp]E: Unable to fetch some archives, maybe run apt -get update or try with --fix-missing?[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp].
Again.  
Hello, circle:)[/FONT][/COLOR]

---

### Post by Impavidus on 2016-08-23
Your server, iq.archive.ubuntu.com, gives a lot of http 403 errors. Something's wrong with that server and that's why you cannot download the updated packages. Try switching to a different server. Go to software & updates, select download from main server or find another server that works well.

---

### Post by banceu_sergiu_ione on 2016-08-23
Did you had a reboot after all the upgrades had been installed? After 266 packages for sure you need a reboot.
So, reboot/restart your pc,
 Once open back see if need same clean, open a terminal and run
```
 sudo apt-get autoclean 
```
```
 sudo ap-get autoremove 
```

After clean try run again update and upgrade. 

But, in mean time.. did you installed skype?

---

### Post by 0chk on 2016-08-24
Thank you, Impavidus.   It worked.  Thank you.

---

