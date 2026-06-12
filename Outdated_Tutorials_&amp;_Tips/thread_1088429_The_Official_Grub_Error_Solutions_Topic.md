---
title: "The Official Grub Error Solutions Topic"
date: 2009-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Somiac on 2009-03-06
Okay, So here will be my first major contribution to these forums. I know I don't know the answer to each, but I am going to make this a post with Scenario's of each of the GRUB Error's and the answer to fixing it all in one post in order!

My few days being here I've seen about five people ask about Error 21, and a few others so I decided to compile one major post that will have multiple solutions to each one.
[I]
If you know a solution to a GRUB error, then please reply with the error number, the scenario in which it occurred, Operating systems that were involved and how you fixed it.[/I]

So I will start with Error 21, and if you guys have anything to add, please reply to this topic and I will update this main post with each Error in their order for other users to easily find each one and their answer.

Some of you members may also say just go to the WIKI page, but if you're like me I'm too lazy to go read those and prefer a direct answer from someone or a quick easy to read fix and don't want all the explanation of why or whats going on, if I care about that I will read why it happened later, but right now I just want it FIXED! 

And Thus this Topic was born, And would also be cool if it would be stickied so all people with these errors can just be referred to it.

Again I only know the fix to Error 21 as that's the only one I know of but if you have had others and/or know the fix to other ones please reply or PM me with the answer and scenario in which it happens and I will update this topic with it!

[CENTER][FONT="Palatino Linotype"][COLOR="SeaGreen"][SIZE="5"]*** ERROR LOG SOLUTION START ***[/SIZE][/COLOR][/FONT][/CENTER]


[COLOR="Red"][SIZE="4"]**Error 21:**[/SIZE][/COLOR]

[COLOR="Navy"]**Scenario 1:**
You just installed Ubuntu on your External Hard Drive, while your internal Hard drive still has Windows on it, and you are trying to do a dual boot when the Ex. Hard Drive is connected.

Everything seems Great except one Problem, when you unplug your External Hard drive and turn your Computer on it gives you this dreadful Error.

**Solution:**
All you need to do is boot into Ubuntu, have your LiveCD inside your cd drive. Goto the SHELL and type in
sudo grub-install /dev/sdb

Once that is complete, it should only take a second, Restart your computer and reboot into Windows, the quickest way without using your windows CD is either downloading one of these two programs:
[fixmbr](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)
[EasyBCD](http://neosmart.net/dl.php?id=1) (scroll to the bottom and download link is in blue button).

I used the second link, but all you need to do is run it, or in EasyBCD's case goto "Manage BootLoader" and click "Write MBR" (make sure the "reinstall Bootloader radio button is checked")

And that should fix your problem![/COLOR]

---

### Post by utnubuuser on 2009-03-06
Hi --  great.

one thing,  these colors are hard on the eyes.

---

### Post by Sef on 2009-03-06
Moved to Tips and Tutorials.   Added Tags.

---

### Post by Somiac on 2009-03-07
Fixed colors.Still hoping people that have dealt with other errors can contribute the solutions and such :)

---

### Post by Elfy on 2009-03-07
Great to see that you have added yourself to the list of helpful people - but can I suggest that you make it more generic and possibly use code tags etc [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

```
sudo grub-install /dev/sdb
```

would fail here :)

---

