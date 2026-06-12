---
title: "ubuntu's security?"
date: 2009-07-03
forum: Recurring Discussions
---

### Post by thomz92 on 2009-07-03
hey

i told my friend about the way you can reset/change your password by booting into recovery mode. I thought this was a good thing about ubuntu, but my friend made me start to wonder. He said that anybody could steal your computer, change the password, log in, get on the internet, and visit websites such as banking websites and if the previous user pushed "remember my password", he could use paypal or whatever in the previous users account. Is this true?

---

### Post by Tibuda on 2009-07-03
Physical access = root access no matter what is your system, and how you tweak your system.

---

### Post by steeleyuk on 2009-07-03
Thats why its important to physically secure computers. You could encrypt everything on the disk and that would deter 99.9% of potential thieves, but there is still the risk as long as physical access can be gained.

---

### Post by thomz92 on 2009-07-03
right... but thats not the case with windows, is it? You can't actually log in as them in windows, right? (yes, this was another windows vs. linux arguement between us)

---

### Post by Tibuda on 2009-07-03
> **thomz92 said:**
> right... but thats not the case with windows, is it? You can't actually log in as them in windows, right? (yes, this was another windows vs. linux arguement between us)

Read my reply again:

> Physical access = root access **no matter what is your system**, and how you tweak your system. 

You can just insert a Ubuntu Live CD in a Windows computer, and you'll be able to read all files in the partition, including cookie files to log in into your websites.

To avoid it, you could disable boot from CD and add a BIOS password. But it is not hard to disable BIOS password if you have physical access to the computer.

---

### Post by james.paige on 2009-07-03
There are plenty of password changers for windows machines.

"Active Password Changer" is one of them.

Again, if someone has physical access to your machine then they can always get in or get your data.

---

### Post by monsterstack on 2009-07-03
> **thomz92 said:**
> right... but thats not the case with windows, is it? You can't actually log in as them in windows, right? (yes, this was another windows vs. linux arguement between us)

You can do exactly the [same thing]("http://pubs.logicalexpressions.com/Pub0009/LPMArticle.asp?ID=305") [logicalexpressions.com] on Windows, too.

If you're really worried about it, set a GRUB password. And encrypt your hard drive too if you like.

---

### Post by Tibuda on 2009-07-03
> **monsterstack said:**
> If you're really worried about it, set a GRUB password. And encrypt your hard drive too if you like.

A GRUB password will not protect you from booting a Live CD. Disabling booting from external devices, and a BIOS password will avoid it. But it will not protect you from reseting the BIOS password in the hardware. An encrypted file system is the best solution, but people can crack it using brute force, or they can [use violence until you tell the password]("http://xkcd.com/538/").

---

### Post by thomz92 on 2009-07-03
ok. i wasn't really worried about it, but i wanted to make sure that linux wasn't less secure than windows in that respect. thanks

---

### Post by SunnyRabbiera on 2009-07-03
> **thomz92 said:**
> right... but thats not the case with windows, is it? You can't actually log in as them in windows, right? (yes, this was another windows vs. linux arguement between us)

Windows is as vulnerable in this case as Linux is, both can be bypassed quite easily during the boot up sequence if one knows what to do.
But one can put up a BIOS and GRUB password too to bypass this weakness.

---

### Post by juancarlospaco on 2009-07-03
[B]-Grub Password
-BIOS Password
-Encrypted /HOME
-Use Seahorse
-Disable Boot from CD/USB/Net
-Ultra Strong Passwords
-Solder the Battery to the Board
-Enable SELinux[/B]

---

### Post by bodhi.zazen on 2009-07-03
> **juancarlospaco said:**
> [B]-Grub Password
-BIOS Password
-Encrypted /HOME
-Use Seahorse
-Disable Boot from CD/USB/Net
-Ultra Strong Passwords
-Solder the Battery to the Board
-Enable SELinux[/B]

None of that helps with physical access and all that is easily defeated (with the exception of an encrypted home, but if the system is not encrypted, and encrypted home only is limited).

You need to fully encrypt your system.

---

### Post by juancarlospaco on 2009-07-03
> **bodhi.zazen said:**
> 
You need to fully encrypt your system.

Its Vulnerable too :)

---

### Post by bodhi.zazen on 2009-07-03
It is vulnerable but it is as good as it gets and fare superior to any other option. The only know vulnerability has to be run within a fe minutes of turning your compute off.

If you turn the commuter off yourself you are good to go.

By far the vulnerability is :

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

