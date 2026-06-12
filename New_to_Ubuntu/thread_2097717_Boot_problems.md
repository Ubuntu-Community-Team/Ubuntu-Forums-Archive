---
title: "Boot problems"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by fairy._.queen on 2012-12-24
Hi all!

I have tried installing Ubuntu 12.04 on a desktop pc (with no windows) and the installation went fine.
When I power on the pc, though, after it has recognised the HDDs, it stops and doesn't do anything more. It doesn't report things such as "Missing Operating System" and there is no line mentioning GRUB.
I suppose you need more information, but I need to know what exactly you need to help me - I'm much of a beginner.
Thanks in advance!

---

### Post by Wim Sturkenboom on 2012-12-24
How old or new the PC is ;) Hardware specs (motherboard, processor, memory, video card)? Is you BIOS and UEFI bios?

Based on harddisk activity, do you think it does a boot? If so, if you press <ctrl><alt><F1> (that is, control plus alt plus F1), do you get a prompt to login? Or does that combination does not do anything?

---

### Post by fairy._.queen on 2012-12-24
The pc is quite old (more or less 10 years).
Graphic card: NVIDIA GeForce FX 5200 VGA
Processor: Intel Pentium 3 2.8 GHz
The RAM is 512 Mb (not sure), I don't know the motherboard.

After pressing <ctrl><alt><F1> nothing happens. Thanks for replying!

---

### Post by Wim Sturkenboom on 2012-12-24
Although not sure, it might be your video card and you might need to modify the kernel boot line

Boot your system; at the end of the POST (or during the post), press <shift> and keep it pressed. You should get a boot menu and it should say something like Ubuntu on the first line (the second line probably mentions recovery mode). The first line is selected by default; press 'e'. A new screen appears; find the line that ends with 'quiet splash' and replace 'quiet splash' with 'nomodeset'. Press <ctrl>x (that is, control plus x) to boot.

Let us know how far you can get.

If 'nomodeset' fails, you can try 'text' instead. In that case you will be taken to a console where you can login (note that the password will not be echoed; just type it and press <enter>. To shutdown the system, type _sudo shutdown -h now_ and provide your password (again, it will not be echoed).

Again, let us know how far you can get; this is just to see if your system is able to boot at all.

---

### Post by squakie on 2012-12-24
Definetly try what Wim Sturkenboom has recommended, but also keep this in mind:  I used to have a 5200 in one of my old PCs, and I ended up getting a new card.  The 5200, even with nomodeset, just wasn't supported in the drivers in Linux, and as such did not "cooperate" very well.

---

### Post by fairy._.queen on 2012-12-25
Pressing shift doesn't cause anything to happen (the keyboard works because ctrl+alt+del works).
What does this mean?

---

### Post by fairy._.queen on 2012-12-27
Anyone?

---

### Post by Wim Sturkenboom on 2012-12-27
Not forgotten ;) But I'm a bit confused as to why <shift> does not work.

Does live mode work (boot from liveCD, choose 'try Ubuntu')?

You can try to check if grub (the boot loader) is installed in the MBR. Boot from the liveCD (or liveUSB). When booted, press <ctrl><alt>t (that is, control plus alt plus letter t) to open a terminal and paste the command below (in bold red) and press <enter>.

```

wim@i3-2120:~$ **[COLOR="Red"]sudo dd if=/dev/sda bs=512 count=1 |grep -i grub[/COLOR]**
1+0 records in
1+0 records out
512 bytes (512 B) copied, 5,745e-05 s, 8,9 MB/s
[COLOR="Blue"]Binary file (standard input) matches[/COLOR]

```
The rest of the above is the result of the command; if you don't get the last line (in blue), grub is not installed.

---

### Post by fairy._.queen on 2012-12-27
Ubuntu works from live CD and grub appears not to be installed. The output is:
```

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0,0107329 s, 47,7 kB/s

```

Thanks for replying!

---

### Post by Wim Sturkenboom on 2012-12-27
We can try to figure out if something is installed. If you open the filemanager (while running the liveCD), the left hand pane should show something like _xxxGB filesystem_ (xxxGB reflecting the size of your internal hard disk). Double click it and you should see directories like 'boot', 'etc', 'home' etc. Open 'home' and you should see the username that you specified when you installed.

If that is the case, grub is incorrectly installed and the rest5 of the installation is OK. You can try to fix it; someone else needs to help with that, but there is a bootrepair utility that you can install while running the liveCD (you should be able to find some instructions how to install it here on this forum or doa search on the web for the search terms 'yannbuntu bootrepair'). An alternative might be the supergrub disk.

If you can't find anything, a re-install is the only option.

---

### Post by audiomick on 2012-12-27
Info on boot repair here

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I would get straight on to that. If you can't make sense of it, follow the instructions to get the boot info and post that here so people can see the state of your system.

---

### Post by fairy._.queen on 2012-12-28
Using boot-repair worked!!!
Thank you all for your kind help!

---

