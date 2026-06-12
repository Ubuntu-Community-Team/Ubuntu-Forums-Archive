---
title: "Kubuntu 13.10 doesn't boot after hard shutdown"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by Asaltu on 2014-02-07
Hi, first of all I would like to tell you that I am using Kubuntu for over 2 years now, but I just use it as it is. I do my updates and upgrades regularly, and I know my way using command lines by following instructions online, but I'm for sure not a pro, so please handle me with care :D

So about my problem: I have a Compaq 6720s running Kubuntu 13.10. A couple of days ago the computer completely froze, and all I could do was shutting it down the hard way. After trying to boot it again, the boot process seemed to be hanging at the flashing Kubuntu logo. I left it for almost an hour, but nothing happened.

I tried restarting a couple of times, but it keeps on hanging at the same flashing Kubuntu picture.

I also tried booting from my Live USB and CD, but that gives the same problem. I don't mind re-installing Kubuntu again, but I only know how to do that with the Live USB or CD, and as that doesn't seem to work, I don't know how to re-install it.

I also noticed that at startup I don't see the grub menu anymore, don't know if that has to do with it.

If anyone could give me some advise on what I could try to get my machine up and running again, that would be greatly appreciated!!

---

### Post by Bashing-om on 2014-02-07
Asaltu; Hi ! Welcome to the forum >

OK, we can not at this time rule out hard ware failure !
Try this:
Boot your liveDVD up in another machine to insure it is good ( remember, one must reset the boot priority in bios).
If the liveDVD is good ->
Reset the boot priority in your machine and insure it too boots to -> "try ubuntu" mode.

All good ? -> run the "check and repair file system" tool in "GParted" or elsewhere. All good ?

Finally, from the liveUSB (RE-)install grub to the booting hard drive.

Reboot; Does  (k)ubuntu now boot up ?

[INDENT][INDENT]great place to start
[/INDENT][/INDENT]

---

### Post by Asaltu on 2014-02-08
First of all: Thanks for the help

> Boot your liveDVD up in another machine to insure it is good ( remember, one must reset the boot priority in bios).
Check, this works
> Reset the boot priority in your machine and insure it too boots to -> "try ubuntu" mode.
Check, Kubuntu Live Mode starts up
> run the "check and repair file system" tool in "GParted" or elsewhere. All good ?
I ran the check: no errors.
> Finally, from the liveUSB (RE-)install grub to the booting hard drive.
Grub re-installed

>  Reboot; Does  (k)ubuntu now boot up ?
Kubuntu does not boot up. Now it hangs at this message:

error: invalid environment block
Press any key to continue..._

But after pressing a key, nothing changes, and the message stays on screen: Booting does not resume. Any ideas on what to do next?

---

### Post by Bashing-om on 2014-02-08
Asaltu; Well shucks !

Let's see if we can isolate the problem to the file system or as a graphics issue.
Try this:

Boot to the grub menu, (k)ubuntu "normal" kernel highlighted, 'e' key for edit mode;
Boot parameters screen -> arrow down and across and replace "quiet splash" - and all after with the term "text" -with out the quotes-;
ctl+x to continue the boot process to a terminal (TTY1) login (textual);
Log in here and enter password when asked ( no response to the screen, security reasons).

What now returns from terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
We want to know what graphics card is installed, and what driver (if any at all ) is loaded.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Asaltu on 2014-02-08
After replacing *quiet splash $vt_handoff* with *text* and ctrl-x I do not get into a terminal login. Instead I see the following:

   Booting a command list
error: invalid environment block.
 Press any key to continue..._

And again, no reaction to a key press...

EDIT:
I meanwhile figured out the following:

When in the Grub menu I choose &#8220;Advanced options for Kubuntu&#8221; and then choose &#8220;*Kubuntu, with linux 3.11.0-12-generic&#8221; *instead of &#8220;*Kubuntu, with linux 3.11.0-14-generic&#8221;, *that (first mentioned) version seems to start up without problems.

When choosing *Kubuntu, with linux 3.11.0-13-generic* it does not load. It just shows *Loading Linux 3.11.0-14-generic*, and stops there

The older version seems to work perfectly fine, and I can use it (Yeey!)

One questions remains though: 
Do I have to worry that the 3.11.0-14 version doesn&#8217;t work? Or should I still attempt to fix it? And if yes, how? (Ok that were 3 questions in stead of 1 :))

---

### Post by sandyd on 2014-02-08
That sounds like a env issue with grub

Boot to the grub menu - and press 'e' to edit the default entry.

Then, find the below, and remove them from the file using backspace
```

save_env recordfail
```

Press control+X to boot

---

### Post by Asaltu on 2014-02-09
Hi sandyd,
thanks for jumping in.

I can't find the specific line 
```
save_env recordfail
```

what I see after pressing 'e' to the default entry is

```

setparams 'Kubuntu'

recordfail[INDENT]load_video
gfxmode $linux_gfx_mode
insmode gzio
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
    search --no floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci\1,msdos1 13f7b934-5781-4900-ac83-ecf01c962e96[/INDENT]
[INDENT]else
    search --no-floppy --fs-uuid --set=root 13f7b934-5781-4900-ac83-ecf01c962e96
fi
linux      /boot/vmlinuz-3.11.0-14-generic root=/dev/sdb1 ro     quiet splash $vt_handoff[/INDENT]

```

---

### Post by sandyd on 2014-02-10
try removing the line with 'recordfail'

---

