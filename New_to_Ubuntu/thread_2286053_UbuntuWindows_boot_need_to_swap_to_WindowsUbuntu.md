---
title: "Ubuntu/Windows boot need to swap to Windows/Ubuntu"
date: 2015-07-09
forum: New to Ubuntu
---

### Post by makem2 on 2015-07-09
Clean install of Windows 7 Ultimate. Clean install of Ubuntu 14.04 LTS.

Computer boots to grub which offers Windows 7 last in the list amongst other options.

I would like to have a double line pair of choices: Windows 7 followed by Ubuntu (nice and simple) with a default if no selection of Windows 7 (for HWMBO)

I opened the page 'GrubHowto/ChangeDefaultOS' in Ubuntu documentation:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Immediately I hit a problem! The file menu.lst or menu.1st does not exist in my /boot/grub/ directory. I do have a grub.cfg which I presume would be the file to edit although I see a warning about editing. However, I don't want to start off on the wrong foot so to speak.

Guidance/pointer to the correct source for making the change I require please.
[h=1][/h]

---

### Post by Vladlenin5000 on 2015-07-09
Hi and welcome.

The tutorial you linked is very old and refers to a Grub version that has been updated years ago.

[URL="http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order"]http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order

[/URL]

---

### Post by makem2 on 2015-07-09
Thank you.

I have been learning to use Linux a few weeks and have noticed that most help is written by those who assume the reader knows as much or close to that of the writer. I find this a pain :(

In this case for example, I install the suggested editing software which installs correctly I assume and then I am left at the terminal prompt. No suggestion as to how to start the installed softwae so another hunt starts. This appears to be common in Linux and I think would tend to put new users off unless they really (like me) want not to be beaten lol.

---

### Post by Vladlenin5000 on 2015-07-09
There was a time when you had to learn the same things but for another OS, wasn't it? You weren't born with innate knowledge of that other OS, were you?
That said, and assuming you're using the standard Ubuntu, the new software you installed is accessible like any other: In your launcher (left bar) at the top there's an Ubuntu icon. Click there and search using the first letters of the program's name. In other desktop environments you should find the classic "start" menu.

---

### Post by makem2 on 2015-07-09
I know exactly what you mean and that is why I persist. In Linux there needs to be (well for me anyway) a lot of terminal work which although I started when the first home computers were first available and programmed in machine code, assembler and BASIC among other languages on ARM machines, being mollycoddled by Windows has made me expect more spoon feeding which I know is wrong. It was a bad day when I 'had' to swap to Windows.

---

### Post by Vladlenin5000 on 2015-07-09
Currently you can install and manage almost everything in Ubuntu without typing commands. However, such possibilities are deeply rooted in the DE you're using. Knowing that the people ijn this forum tend to - correctly - give instructions that are independent of the DE and/or third-party apps/tools. You guessed it: Terminal ;-)

Conversely, there are still lots of network management in Windows for which there are no GUIs. Yes, terminal again...

---

