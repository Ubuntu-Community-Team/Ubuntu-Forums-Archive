---
title: "PC Freezes whilst attempting to install"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by molescroft on 2008-11-16
Joined today as have been trying, for several hours now, to install Ubuntu 8.10 as a dual boot with Vista. Every time I get the CD booting, I get the usual options (although slightly different than the screenshots in the installation guide). Immediately after this menu shows, I get the screen up asking me to select language - after choosing English,the spalsh screen appears. I choose install, the cd drive whirrs, the Ubuntu logo comes up with what appears to be a progress bar below it, then nothing, nada, zip!

Any ideas?

Thx

---

### Post by N74JW on 2008-11-16
Hi,

I would try a different CD, if you haven't already.

I had a similar issue with a disc that would not get past that particular point without freezing.  I burned a new CD and it was fine from there.

---

### Post by boof1988 on 2008-11-16
> **molescroft said:**
> Joined today as have been trying, for several hours now, to install Ubuntu 8.10 as a dual boot with Vista. Every time I get the CD booting, I get the usual options (although slightly different than the screenshots in the installation guide). Immediately after this menu shows, I get the screen up asking me to select language - after choosing English,the spalsh screen appears. I choose install, the cd drive whirrs, the Ubuntu logo comes up with what appears to be a progress bar below it, then nothing, nada, zip!

Any ideas?

Thx

Here's a couple ideas...

[LIST=1]
[*]When you boot to LiveCD use the option (I can't remember the exact words) that lets you test the CD integrity.
[*]If the CD has some errors after the test, then burn the CD again at a lower speed (if possible).
[/LIST]

Also... about how long do you wait as the drive is running after you choose ***Install***?

---

### Post by N74JW on 2008-11-16
...

---

### Post by molescroft on 2008-11-16
Sorry guys, done all of that!

CD integrity good, md5sum ok.

As a matter of interest (if not heresy!), Open Suse doesn't seem to want to play either.

If I start my laptop, I am given the choice of Windows Vista or Ubuntu - just nothing happens if I choose Ubuntu.

HELP!!!!

---

### Post by smooth3006 on 2008-11-16
im having the same issue with 8.10. 8.04 boots fine though and ive burned several different cd's. it must be a bug in the new build, maybe a kernel issue too ?

---

### Post by Crafty Kisses on 2008-11-16
What are your system specs? It really depends you might be better off with Xubuntu or something to that nature, a lighter interface. You can also use the alternate CD installer, which is a text-based installer, it's really easy.

---

### Post by smooth3006 on 2008-11-16
> **Codename said:**
> What are your system specs? It really depends you might be better off with Xubuntu or something to that nature, a lighter interface. You can also use the alternate CD installer, which is a text-based installer, it's really easy.

i honestly think it is a bug with 8.10. my new laptop handles 8.04 with no issues.

---

### Post by cariboo on 2008-11-16
Have any of you tried any of the startup options available by pressing F4 or F6?

Jim

---

### Post by Tatty on 2008-11-16
At the boot screen press F6 and then remove the words "quiet" and "splash" from the end of the boot string.

This should give you some verbose output as to what is happening, it might yeild some clues.

---

### Post by XebraTech on 2008-11-16
> **smooth3006 said:**
> i honestly think it is a bug with 8.10. my new laptop handles 8.04 with no issues.
I agree.  I just burned a new CD of 8.10 and it hangs forever.  Note that 8.04  installs flawlessly.

I found that if you hit the return key, it will make the progress bar move.  Make it go all the way to the right and then back all the way to the left, then hit it once to make it go back to the right and it'll fire up.  During install I had to keep hitting the return every now and again to get it to fire back up again.  Finally installed completely and it's running fine.  Something is definitely up I'd say, otherwise, it'll just sit there until the end of time.

Note that after install, it still hangs on that specific spot, do hold the return key down maneuver and it'll finally boot all the way up.  REALLY strage this one is.

Running on an HP dv6000.

Anybody else have a clue what is going on here?  I'll try the F4/F6 to see if it comes back with something.

---

### Post by smooth3006 on 2008-11-17
> **XebraTech said:**
> I agree.  I just burned a new CD of 8.10 and it hangs forever.  Note that 8.04  installs flawlessly.

I found that if you hit the return key, it will make the progress bar move.  Make it go all the way to the right and then back all the way to the left, then hit it once to make it go back to the right and it'll fire up.  During install I had to keep hitting the return every now and again to get it to fire back up again.  Finally installed completely and it's running fine.  Something is definitely up I'd say, otherwise, it'll just sit there until the end of time.

Note that after install, it still hangs on that specific spot, do hold the return key down maneuver and it'll finally boot all the way up.  REALLY strage this one is.

Running on an HP dv6000.



Anybody else have a clue what is going on here?  I'll try the F4/F6 to see if it comes back with something.

i just installed 8.04 with no issues at all, it's rock solid. i say its a bug with 8.10. funny thing is i also have a hp pavilion dv6000. :)

---

### Post by WKnew on 2008-11-23
Your question was posted 5-days ago so you may have already found this answer.

I have an HP Pavilion dv6910us and the livecd and/or an install would not progress past the bouncing progress bar during boot unless I held down the ctrl key or space bar, etc. to keep boot going.

Found this somewhere on the forum a couple of weeks ago. It seems to be working well for me.

You can add the "hpet=disable" to the kernel line within your /boot/grub/menu.lst. This should fix the "key to boot" issue.

---

### Post by smooth3006 on 2008-11-23
> **WKnew said:**
> Your question was posted 5-days ago so you may have already found this answer.

I have an HP Pavilion dv6910us and the livecd and/or an install would not progress past the bouncing progress bar during boot unless I held down the ctrl key or space bar, etc. to keep boot going.

Found this somewhere on the forum a couple of weeks ago. It seems to be working well for me.

You can add the "hpet=disable" to the kernel line within your /boot/grub/menu.lst. This should fix the "key to boot" issue.

thanks ill try that

---

