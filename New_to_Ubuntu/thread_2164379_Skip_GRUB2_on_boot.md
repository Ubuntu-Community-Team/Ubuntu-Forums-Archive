---
title: "Skip GRUB2 on boot"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by 34H8CTY on 2013-07-31
Hi, I'm brand new to Ubuntu and enjoying the experience so far.
I am wondering if there is any way that I can skip the GRUB 2 screen on start up though.
I get that it will time out and choose to boot Ubuntu anyhow, but I really don't need the option for things like Ubuntu Advanced options when I'm just starting my computer for the day.

Thanks, Joss!

---

### Post by deadflowr on 2013-07-31
if you open the file /etc/default/grub, you find a line

GRUB_TIMEOUT=10

change that to 0, and the grub menu should not show anymore.

Note, you need to be as root to edit that file, so be careful, and run
```
gksu gedit /etc/default/grub
```
Do the edit and save and then close gedit.
Then run
```
sudo update-grub
```
Which will update all changes made to grub.

---

### Post by grahammechanical on 2013-07-31
There is something also you should know. If a Grub 2.0 menu is appearing it means that there is another OS on the system. By setting the Grub time out to zero you will not be able to select that other OS. I hope you have another method of loading it.

Regards

---

### Post by mansonfan78 on 2013-07-31
If Grub is set to hidden and you need to access it on a on-time basis, pressing the shift key just before your computer boots to the hard drive (after POST) should show the grub menu.

---

### Post by 34H8CTY on 2013-08-01
@deadflowr: I tried to run this, but it's asking for an administrative password - I'm not sure what that is, I used my normal password (the only one I've selected on this install), any hints as to find work out what it is? ie. is there a default one or some way to change it?

@grahammechanical: When Grub shows, the listings are:

[LIST]
[*]Ubuntu
[*]Advanced options for Ubuntu
[*]Memory test (memest86+)
[*]Memory test (memtest86+, serial console 115200)
[/LIST]
Are all of these supposed to be there? I understood that I was installing Ubuntu instead of my old Windows 8 OS.

@mansonfan78: When you say 'hidden' is that achieved by setting the timeout to 0, or is that when it just normally doesn't show?

---

### Post by mansonfan78 on 2013-08-01
> **34H8CTY said:**
> @deadflowr: I tried to run this, but it's asking for an administrative password - I'm not sure what that is, I used my normal password (the only one I've selected on this install), any hints as to find work out what it is? ie. is there a default one or some way to change it?

@grahammechanical: When Grub shows, the listings are:

[LIST]
[*]Ubuntu 
[*]Advanced options for Ubuntu 
[*]Memory test (memest86+) 
[*]Memory test (memtest86+, serial console 115200) 
[/LIST]
Are all of these supposed to be there? I understood that I was installing Ubuntu instead of my old Windows 8 OS.

@mansonfan78: When you say 'hidden' is that achieved by setting the timeout to 0, or is that when it just normally doesn't show?

If you only have one user account it would, by default, have to be an administrator, so just use your normal password.   
Your Grub listings are correct.  And yes, when I said "hidden" I meant any time the menu doesn't show, including setting the timeout to 0.

---

### Post by 34H8CTY on 2013-08-01
Okay, good to know.
One problem though, my normal login password is not working for the administration password. How do I fix this?

---

### Post by 34H8CTY on 2013-08-03
I've figured out that my password doesn't work for gksu, but it does for sudo.
That said, I've edited the file and run the update, but now Grub shows up and just sits there - it doesn't time out.

Any other suggestions?

---

### Post by deadflowr on 2013-08-03
> **34H8CTY said:**
> I've figured out that my password doesn't work for gksu, but it does for sudo.
That said, I've edited the file and run the update, but now Grub shows up and just sits there - it doesn't time out.

Any other suggestions?

In Ubuntu 13.04 they changed the gksu-properties
so open a terminal and run
```
gksu-properties
```
then change the authentication from su to sudo.

Edit: What parts of the grub file did you edit?

---

### Post by 34H8CTY on 2013-08-04
Ah, this change has now worked, I can now access gksu with my password - thanks!

I changed 'GRUB_TIMEOUT=10' to '=0' as suggested in previous instructions - haven't changed anything else.

---

### Post by 34H8CTY on 2013-08-07
Actually, whilst trying to fix another issue, I killed the installation completely.
I ended up re-installing, now all is working better than before. And Grub screen doesn't show at all.

Thanks for your assistance.

---

