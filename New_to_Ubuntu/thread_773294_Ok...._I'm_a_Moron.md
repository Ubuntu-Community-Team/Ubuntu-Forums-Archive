---
title: "Ok.... I'm a Moron"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by IBeLeeB on 2008-04-28
Greetings all. A few months ago, I downloaded and installed Ubuntu.  I did several things, including store a few important things, while exploring. Then, for family reasons, I have not had my computer on for some time. And now, I cannot remember username or password. Any suggestions? I REALLY need to retrieve at least one file before I blow it all away and start again.

---

### Post by daimaru on 2008-04-28
just insert a live cd (ubuntu or other distro) and copy your files. you should be able to access all your stuff unless you encrypted your filesystem. that should work.

one more question is it a dual boot XP and ubuntu?? if so use the program explore2fs in windows and just copy your files to your windows partition.

---

### Post by dokdoom on 2008-04-28
There's a way to blank out your password using a ubuntu live CD. Google that and you should be good to go.

---

### Post by Tatty on 2008-04-28
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

That should do it for you.

---

### Post by damis648 on 2008-04-28
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below... #-o
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
13. Bow down to me....

found at: [http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

---

### Post by damis648 on 2008-04-28
oh well i thought that the recovery console needed a root password but i guess not... if so then tatty's method is better

---

### Post by GoCool on 2008-04-28
> **damis648 said:**
> 1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below... #-o
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
13. Bow down to me....

found at: [http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

I love my ubuntu community. Great minds with helping nature but with a sense of humor. Ubuntians, you rock. :guitar:

---

### Post by anewguy on 2008-04-28
Hey, it's MISTER Moron to you!  I'm just a putz.:)

---

