---
title: "Install Lubuntu without a mouse (inside the GUI)"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Luis_Estevez on 2014-04-23
Hello, this is my first post at this forum. Sorry, my English is not so good, because I speak Spanish. I'm an absolute begginer using Linux. I'm testing different distros on an old computer without PS/2 or USB mouse (only serial mouse). I've installed Puppy Linux 5.5 and Ubuntu 10.04 on this machine, and both run Ok. But I'd like to install Lubuntu 10.04. When the booting process (from the Live CD of Lubuntu) finish, there's an icon with the caption "Install Lubuntu", but I can't select it, because the mouse doesn't work. The question is: How can I select this option pressing keys? I've installed Ubuntu using the keyboard, and after I've activated the mouse using "inputattach", but in Lubuntu I don't find a method to select installation option with the keyboard. Thank you very much.

---

### Post by QIII on 2014-04-23
Hello!

[This]("https://help.ubuntu.com/community/SerialMouseHowto") is very old, but it might still work.  Give it a try and let us know.  If it doesn't work, someone may have a better answer.

Cheers!

---

### Post by mörgæs on 2014-04-23
The [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") installs with only keyboard commands. 

10.04 is out of support, so go for 14.04.

---

### Post by Luis_Estevez on 2014-04-25
> **QIII said:**
> Hello!

[This]("https://help.ubuntu.com/community/SerialMouseHowto") is very old, but it might still work.  Give it a try and let us know.  If it doesn't work, someone may have a better answer.

Cheers!

Yes, it Works! Thank you very much! I've used the Live CD (10.04 version), and inside the GUI, I've activated the terminal (with the keyboard), and after used the command "sudo ubiquity". That's all. I can't use the ISO's listed in the section "alternate install", because after the 10.04 version, all need CMOV and PAE (and my processor hasn't them). Version 10.04 hasn't "alternate install". Thank you very much for your help.

---

### Post by mörgæs on 2014-04-25
Good, please mark the thread 'solved'.
Are you aware of the the risk of running an unsupported version?

---

### Post by Luis_Estevez on 2014-04-26
> **mörgæs said:**
> Good, please mark the thread 'solved'.
Are you aware of the the risk of running an unsupported version?

Yes, I am, but I use this old computer disconnected from Internet, only to play music. I can't install new versions of Lubuntu (after 10.04) because this computer hasn't CMOV and PAE. Recently, I configured my Sound Blaster AWE 64 ISA with success. :) I'm learning with tutorials. Thank you.

---

