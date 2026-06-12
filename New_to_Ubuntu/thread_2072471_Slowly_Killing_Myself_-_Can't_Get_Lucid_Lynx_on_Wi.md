---
title: "Slowly Killing Myself - Can't Get Lucid Lynx on Windows 7 HP"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by MoToast on 2012-10-17
I am seriously about ready to shoot myself.

This worked so easily once...a long time ago...

But now I am Window's ***** and can't seem to do anything about it.

So - my problem:

I do the usual, stick in the live CD, boot from it, use the newb method of just saying "install side by side" and just keep clicking till I'm through.

Now I restart...straight to Windows.  No grub, no nothing but Windows.

So - there is this hot thing called EasyBCD.  Yeah - I bust out that sucker and try virtually every combination of grubs, partitions, MBR re-writes, etc...everything I can think of and read online.  Now Grub shows up but none of the linux options actually load ubuntu they just complain about not having something...I don't have something...ITS LINUX.  

I'm totally going to cry now and wet myself unless someone who is big and strong can please, please tell me a cookie cutter way to get this done.

One thing to note, this HP comes standard with an EFI partition, big ol C drive with Windows, and a recovery partition.  It is also a solid state drive if that matters.

Lastly, I've also toyed with creating my own partitions using the demo part of the live CD and then installing and still couldn't get it to work.

I am a sad, desperate puppy with nothing to eat but dirt and Windows.  Help me Ubu-Wan - you're my only hope!

Cheers

PS: I have system recovery disks so I can try just about anything...with this install issue.  Also, my computer is a HP h9-1270t.

---

### Post by Bashing-om on 2012-10-18
MoToast; Hi ! Welcome to the forum.

You are not the first with these woes of UEFI.
Here are links to ease your pain, and get ubie installed !
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29](https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29)
[https://gitorious.org/tianocore_uefi_duet_builds/pages](https://gitorious.org/tianocore_uefi_duet_builds/pages)

It can be done, many have managed. Look over the docs and if still with problems, By all means post back.[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by shreepads on 2012-10-18
Did you get the 32-bit or the 64-bit Live CD?

---

### Post by Cheesemill on 2012-10-18
Does 10.04 actually support UEFI systems?

I'm not sure if it does.

---

### Post by MoToast on 2012-10-19
Holy Mother of God - that worked!

Dude - you just save me thousands of dollars in blood pressure medication.

Thanks!

---

### Post by MoToast on 2012-10-19
Oh - and I had to use 12.04

Not my favorite but will do

---

