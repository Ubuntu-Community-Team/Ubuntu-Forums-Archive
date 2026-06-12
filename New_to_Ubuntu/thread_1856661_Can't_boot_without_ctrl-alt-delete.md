---
title: "Can't boot without ctrl-alt-delete"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by djk21108 on 2011-10-08
Hi everyone. I'm having the issue outlined in this thread.

[http://fixunix.com/ubuntu/389330-boot-hangs-indefinitely-until-ctrl-alt-del-pressed.html](http://fixunix.com/ubuntu/389330-boot-hangs-indefinitely-until-ctrl-alt-del-pressed.html)


I can boot normally as long as I hit ctrl-alt-delete like a madman during boot up. 

If I don't, I see a lot of processes starting up and [OK] next to the ones that worked.

The boot up stops at random processes every time unless I hit ctrl-alt-delete. 

Any ideas as to what's going on?

---

### Post by djk21108 on 2011-10-08
Anyone have similar issues?

---

### Post by hansdown on 2011-10-08
Hi djk21108.

Which version of ubuntu are you running?

---

### Post by drs305 on 2011-10-08
I have seen several other users with this same issue but don't recall having seen a solution.

[LIST=1]
[*]When you first boot, do you see the Grub 2 menu? 
[*]After you CTRL-ALT-DEL, do you have a Grub menu that waits until you to select an input?
[*]If the answer to both is yes, is the selection that is booting the same in both cases (is the same line highlighted)?
[/LIST]
From a Grub 2 perspective, the only thing that comes to mind is if the automatic and manual selections are different (different kernels, different kernel options, etc).

---

### Post by Quackers on 2011-10-08
I've not seen this before, personally.
If you turn off the machine and leave it for a minute then press the power button and then while it's booting keep tapping the shift key (or if that doesn't work tap the Esc key) it should bring up the grub menu. 
The top item should be Ubuntu and it should be highlighted.
Press the "e" key and a new screen will appear.
With the arrow keys navigate the cursor to the end of the line which currently ends with "quiet splash" and using the backspace key delete those two words.
Then press ctrl + X to boot.
You will see lots of lines of text scroll by. If it stops make a note of the last couple of lines of text. 
That will give us a clue as to what's getting it stuck - maybe :-)

EDIT see above 2 posts. Typically nobody answers then 3 of us appear at once :-)

---

### Post by Lisiano on 2011-10-08
<--- Not an expert.
(Assuming you use Ubuntu 11.04)
First of, could you post a few logs, press Alt+F2 and copy paste```
gnome-system-log
```
Find the boot, dmesg and kernel logs. Check that they aren't blank.
If they aren't then click anywhere inside the log and press Ctrl+A and Ctrl+C. Now either press the little **#** (hash) button on the message reply and paste the logs inside the [ code ] tags or upload the logs to [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

Also a few questions:
1) What version of Ubuntu are you using (9.04, 9.10, ..., 11.10, ... 7.10... etc) and what flavor (Ubuntu, Kubuntu, Lubuntu, Xubuntu, etc)
2) Did this problem appear recently? If so, did you install or update anything before this problem appeared?
3) Do you have a LiveCD/USB and does it show the same problem?

EDIT: 
[quote=Quackers]EDIT see above 2 posts. Typically nobody answers then 3 of us appear at once[/quote]
Make that 4 of us.

---

### Post by djk21108 on 2011-10-08
Everyone,

Thanks for all the input. I am on 11.10 beta actually. 

This is a recent issue. When I hit ctrl+alt+delete it takes me to a purpleish menu where I can start Ubuntu or start it in Recovery mode.

Even when I start in recovery mode, nothing seems to change, I just boot up into regular Ubuntu.

Any ideas what I should try first? Couldn't find any logs.

---

### Post by djk21108 on 2011-10-08
So when I hit ctrl alt delete I get to the grub menu.

There I select start ubuntu kernel 3.0.x.x (recovery mode)

Then I'm brought to another gui where I select resume boot as normal.

In the case where I don't hit ctrl-alt-delete a lot of times i get a fail on this line of text:

load fallback graphics devices [fail]

---

### Post by drs305 on 2011-10-08
I don't have a solution. Unless you have posted another thread, there are at least a few other users who are having the same problem. I don't know which Ubuntu release they were using and don't have links, but if you search there are other thread(s) within the past month or so which may help.

---

### Post by djk21108 on 2011-10-09
Anyone have any other advice?

---

### Post by QLee on 2011-10-09
[QUOTE=djk21108]Anyone have any other advice?[/QUOTE]
In your first post you cited a link, if your trouble is the one mentioned there it might be a good idea to post both, /etc/fstab and the results of blkid -c /dev/null, because that's what the problem was there, a filesystem mounted twice at boot, once RO and once RW which caused a fsck fail.

---

