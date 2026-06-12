---
title: "Restart fails after 12.04 update"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Zornicator on 2013-05-04
I installed 12.04 on a Thinkpad w530 with Windows 7 preinstalled. I was prompted to install updates, I did so, and then restarted.

Now when I go select "Restart", things proceed as before, I am prompted to choose how I want to boot, but then the screen goes black and nothing else happens (I have left it like this for maybe half an hour and nothing happens). Ultimately I press and hold the power button until it powers down.

Thanks for your time!

---

### Post by Stonecold1995 on 2013-05-04
How many times have you tried booting up?  My brother's computer would sometimes do this, he will occasionally have to boot 3 or 4 times before it actually starts up correctly.

If not, can you get into recovery mode without the screen going blank (when it asks you how to boot I assume you're talking about GRUB)?

---

### Post by BluNova on 2013-05-05
I would reinstall ubuntu, it seems its broken. On the live cd you can copy the files from your hardrive (they will be stored in /home/<username>) to an external harddrive or cd

---

### Post by Zornicator on 2013-05-05
I've done it several times (more than 4). What should I do in recovery mode? Or were you just checking that it will do recovery mode?

I should also mention, since I didn't say it explicitly above, that it did everything perfectly well before the updates.

---

### Post by Bashing-om on 2013-05-05
Zornicator; Hi !

Did you install a proprietary graphics driver on your system; Maybe the update broke the driver ??

Can you boot up ubuntu from the grub menu into "recovery mode" ??

If so we can look at your card and driver see if a graphics driver is at fault.
[INDENT=2]
just my thought

[/INDENT]

---

### Post by Zornicator on 2013-05-05
Bashing-om, I can boot into recovery mode, how do I look at my card and driver?

---

### Post by Bashing-om on 2013-05-05
Zornicator;

That is a good sign //before we go to the trouble of mounting in recovery mode to read and and write mode// Please see if you are able to boot up an earlier kernel from that grub menu. If you can boot up an earlier kernel, post the output - between code tags- of terminal codes;
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```

I suspect in "recovery mode" all that will be seen for a driver is the "vesa" (fall-back driver) (??).[INDENT=2]
regards

[/INDENT]

---

### Post by Zornicator on 2013-05-05
This problem has ceased without my doing anything. Thanks for your help.

If anyone has the patience, please have a look at my other pressing concern (WICD intermittent connection/"bad password" error):

[http://ubuntuforums.org/showthread.php?t=2142147](http://ubuntuforums.org/showthread.php?t=2142147)

---

