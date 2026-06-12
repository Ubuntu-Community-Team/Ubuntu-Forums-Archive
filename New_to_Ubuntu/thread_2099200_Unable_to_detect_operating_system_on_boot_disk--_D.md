---
title: "Unable to detect operating system on boot disk-- Dell Inspiron 2500"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Luvthecheat on 2012-12-28
I have an old Dell Inspiron 2500 that previously ran Windows XP but is now completely wiped. I have correctly set up my boot CD and have enabled my cd drive as a boot device but I am unable to boot from the disk. I have never done anything like this and have tried this many different ways but haven't been successful yet. Anyone know what the problem might be?

---

### Post by adityamagadi on 2012-12-28
are you sure that you have created a bootable CD?

---

### Post by Luvthecheat on 2012-12-28
I burned the file image to disc (I tried cd and dvd and neither worked) and tried it on my desktop an they both worked fine

---

### Post by Bashing-om on 2012-12-28
Luvthecheat; Hi ! Welcome to the forum.

Instructions to verify the .iso image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also instruction to burn the .iso as an "image" NOT data to disk:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

When the install disk is verified, boot up the disk to the greeter screen with two options;
a) Try ubuntu
b) install ubuntu

Choose to "try ubuntu" -> do you boot to the desk top ? Do all your devices work as expected?

Please advise of the results.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Luvthecheat on 2012-12-28
I verified it, all was well... my inspiron doesn't even acknowledge the fact that the CD is bootable and I can't get past "Select your operating system," which only lists Windows XP, which it does not even have.
Thank you for your rapid help!

---

### Post by Horbo on 2012-12-29
Some computers (all of mine, I think) now seem to have a seperate boot device selection menu, and ignore the boot order set in BIOS.

What I mean is (for example) I have a laptop that I press F2 to enter BIOS, set the CD to boot before the hard disk, the save and reboot but the hard disk STILL boots, not the CD.

There is another key, F12, that I can press when the computer is turned on which gives a boot selection menu - there I am given the option of choosing hard disk, CD, or USB as the divice to boot from this time.

You may have something similar.

If all else fails, install Plop: [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)
It will boot before anything else, and let you choose which device to boot from.

---

