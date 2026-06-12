---
title: "admin user account password fail after auto login"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by zephonic on 2012-03-28
I'm on 11.10, all the latest updates from the software center, on an Asus N80Vb notebook. Weird recurring thing:

I always log in as the admin, got tired of having to enter password everytime so dove into 
system settings>user accounts>"user name" administrator.

To change login options you have to unlock with password, which I did, and I switched on automatic login, with password to none.

So far so good, but now I wanted to change it back. When I try to unlock to make changes, it asks for my password but will not acept it, saying: "Your authentication attempt was unsuccessful. Please try again."

I have not changed my PW. I tried to press enter without typing in the password, and that didn't work either.

I had the exact same problem a few months ago, sought advice[ here]("http://ubuntuforums.org/showthread.php?t=1914235"), but that didn't work either, so I just did a reinstall. I could do that again, but really don't wanna have to. 

Any help would be greatly appreciated. Thanks.

---

### Post by yetiman64 on 2012-03-28
> **zephonic said:**
> I'm on 11.10, all the latest updates from the software center, on an Asus N80Vb notebook. Weird recurring thing:

I always log in as the admin, got tired of having to enter password everytime so dove into 
system settings>user accounts>"user name" administrator.

**To change login options you have to unlock with password, which I did, and I switched on automatic login, with password to none.**

So far so good, but now I wanted to change it back. When I try to unlock to make changes, it asks for my password but will not acept it, saying: "Your authentication attempt was unsuccessful. Please try again."

I have not changed my PW. I tried to press enter without typing in the password, and that didn't work either.

I had the exact same problem a few months ago, sought advice[ here]("http://ubuntuforums.org/showthread.php?t=1914235"), but that didn't work either, so I just did a reinstall. I could do that again, but really don't wanna have to. 

Any help would be greatly appreciated. Thanks.In doing the bolded you have removed your user account password, add that to the fact Ubuntu locks the root account, you now have no way to authenticate (raise privileges) as your sudo password is your user account password (you just removed it with setting the autologin password to none).

[[COLOR=Blue]--This thread--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1940971") sounds similar to your situation, the instructions in posts 2 and 3 may help you, note if it fails check the drives are remounted read/write, and retry.

---

### Post by zephonic on 2012-03-28
Thanks for your reply. I did try the steps described in thread you linked [a few months back]("http://ubuntuforums.org/showthread.php?t=1914235"), but to no avail. I did not try remounting the drives, so I'll give that a whack tomorrow.

> **yetiman64 said:**
> In doing the bolded you have removed your user  account password, add that to the fact Ubuntu locks the root account,  you now have no way to authenticate (raise privileges) as your sudo  password is your user account password (you just removed it with setting  the autologin password to none).


How come you cannot disable PW required login without messing up root access? Seems like a fairly major oversight to me. Or is there another way to do that?

On my Macs I can use admin account without PW prompt on startup. PW's only required when you want to install stuff or change things at system level.

---

### Post by yetiman64 on 2012-03-28
> **zephonic said:**
> ...How come you cannot disable PW required login without messing up root access? Seems like a fairly major oversight to me. Or is there another way to do that? 

You **can** set autologin without turning off the password altogether, just set autologin and leave the password alone. You will boot in automatically directly to your desktop but you still need passwords for system changes (just like you mention with Macs)

We can't help here if you are asking to turn off all password prompts, this site supports Canonical's security model, It seems that is not what you are asking though. 

Ubuntu's security policy is to lock the root account and use the command "sudo" to raise an applications privileges. I can see how some people would see that as an inconvenience or being "locked out of their computer" (both misconceptions imo, remembering only 1 password is convenient to me and the use of "sudo -i" to maintain a root shell while working, works for me). [[COLOR=Blue]Further reading on Rootsudo[/COLOR]]("https://help.ubuntu.com/community/RootSudo").

This is primarily in the interests of new starters unfamiliar to Ubuntu and Linux in general. Remember, to err is human, to totally foul up requires the root/sudo password. Running anything as root without needing to is dangerous territory in Linux.

> **zephonic said:**
> On my Macs I can use admin account without PW prompt on startup. PW's only required when you want to install stuff or change things at system level.Different system, different security policies, is all I can say. See comments in first paragraph regarding autologin (it does work, but don't blank out the password).

---

### Post by TonyNorfolk on 2012-03-28
Hi, I am a new user and I did this so I understand how frustrating it can be.  This may work for you.
 
Create another user Admin from within your current one that you can't set the password for (I called it Temp), and then set a password for ithis new account.  Log out and log in with your new admin account.  Open Users and set a password for you old account.  That should give you the option to set a new password without requiring to enter the old one.
 
Please let me know if this works for you
 
Tony

---

### Post by yetiman64 on 2012-03-28
> **TonyNorfolk said:**
> ...Create another user Admin from within your current one that you can't set the password for (I called it Temp)...

The OP's current user password gives,
> "Your authentication attempt was unsuccessful. Please try again."To add a new user to the system (even temporarily) requires root privileges, they can't be gained as the sudo password is gone for the current admin account. 

This will need to be fixed from a root prompt during boot up (the OP may need to mount the drives read/write to get the commands linked earlier to work). It unfortunately cannot be repaired from "within" the system. Hopefully the OP will have some good luck this time around :). Cheers.

---

### Post by zephonic on 2012-03-28
So I have been trying to boot into recovery mode, but no dice. 

Holding shift does nothing.

Pressing F2 brings up the boot device selection menu.

Pressing Escape launches the BIOS menu,


I have done this before, but can't remember how I did it. Computer is an Asustek NV80b laptop. Anyone?

---

### Post by yetiman64 on 2012-03-28
> **zephonic said:**
> ...Holding shift does nothing....
Pressing (and holding down) the shift key just after the BIOS POST screens (power on self test screens) is how to bring up the grub2 menu.  That is the first step to getting into a recovery console, so I'm a bit surprised that failed. It may take a few attempts, timing wise, to get it right.

---

### Post by munezz on 2012-03-29
You can open a new admin account and delete the old one......................when deleting it will ask whether you want to keep the old files give it a yes and problem solved.

---

### Post by yetiman64 on 2012-03-29
@ munezz,
> **zephonic said:**
> I'm on 11.10, all the latest updates from the software center, on an Asus N80Vb notebook. Weird recurring thing:

I always log in as the admin, got tired of having to enter password everytime so dove into 
system settings>user accounts>"user name" administrator.

[B]To change login options you have to unlock with password, which I did, and I switched on automatic login, with password to none.
[/B] 
[B]So far so good, but now I wanted to change it back. When I try to unlock to make changes, it asks for my password but will not acept it, saying: "Your authentication attempt was unsuccessful. Please try again."
[/B] 
I have not changed my PW. I tried to press enter without typing in the password, and that didn't work either.


I had the exact same problem a few months ago, sought advice[ here]("http://ubuntuforums.org/showthread.php?t=1914235"), but that didn't work either, so I just did a reinstall. I could do that again, but really don't wanna have to. 

Any help would be greatly appreciated. Thanks.

> **yetiman64 said:**
> The OP's current user password gives,> "Your authentication attempt was unsuccessful. Please try again."                      To add a new user to the system (even temporarily) requires root privileges, they can't be gained as the sudo password is gone for the current admin account. 

This will need to be fixed from a root prompt during boot up (the OP may need to mount the drives read/write to get the commands linked earlier to work). It unfortunately cannot be repaired from "within" the system. Hopefully the OP will have some good luck this time around :). Cheers.

> **munezz said:**
> You can open a new admin account and delete the old one......................when deleting it will ask whether you want to keep the old files give it a yes and problem solved.

The command adduser in terminal or the graphical equivalent require the use of the sudo password to raise privileges to add the "new" admin account. [B]sudo is NOT working as is stated in the OPs first post.
[/B]

---

### Post by munezz on 2012-03-29
> **yetiman64 said:**
> @ munezz,

The command adduser in terminal or the graphical equivalent require the use of the sudo password to raise privileges to add the "new" admin account. [B]sudo is NOT working as is stated in the OPs first post.
[/B]

Oops sorry about that#-o...................I faced a similar problem some days ago but I could change the password going to Grub menu..................even though I was not prompted for a password during Login which I was not comfortable with..................so I made a new admin account and deleted the old one.

---

### Post by yetiman64 on 2012-03-29
> **munezz said:**
> Oops sorry about that#-o...................I faced a similar problem some days ago but I could change the password going to Grub menu..................even though I was not prompted for a password during Login which I was not comfortable with..................so I made a new admin account and deleted the old one.

That's ok munezz, sounds as though your sudo password was working even if you weren't prompted for a password (autologin happens to be what the OP was setting up when he blanked the password altogether - causing the problem now that needs resetting). 

This would explain why you could "repair" the admin account password by setting up a new account, sudo was actually working in your case :).

Thanks and cheers, yetiman64

**Edit2:** regarding the question to me in post 13, to keep the thread on topic, I have responded briefly in PM to munezz. No continued tech support will be given via PM. But if a new thread is posted munezz is welcome to PM me a link to it (if there are further issues). Cheers All.

---

### Post by munezz on 2012-03-29
> **yetiman64 said:**
> That's ok munezz, sounds as though your sudo password was working even if you weren't prompted for a password (autologin happens to be what the OP was setting up when he blanked the password altogether - causing the problem now that needs resetting). 

This would explain why you could "repair" the admin account password by setting up a new account, sudo was actually working in your case :).

Thanks and cheers, yetiman64

@ yetiman64 All said and done there is one more thing I'd like to know..................what is the difference between Keyring Password and regular password...:neutral:

---

### Post by Krytarik on 2012-03-29
> **yetiman64 said:**
> That's ok munezz, sounds as though your sudo password was working even if you weren't prompted for a password ... This would explain why you could "repair" the admin account password by setting up a new account, sudo was actually working in your case.
Actually, it seems like *munezz* just did the very thing you are trying to accomplish with the OP ;-) :
> **munezz said:**
> I faced a similar problem some days ago but **I could change the password going to Grub menu** ... even though I was not prompted for a password during Login

---

### Post by yetiman64 on 2012-03-29
> **Krytarik said:**
> Actually, it seems like *munezz* just did the very thing you are trying to accomplish with the OP ;-) :

Yes, now you point that out, that sounds right, only he was left with no password prompts and doing the admin account swap "fixed" it. :)

Now we've just got to get the OP to find his way into the grub boot menu, if he can I'm sure he'll be able to fix his setup as well.

@ OP, after you manage to get into the root console and fix the password, as per the linked instructions from post 2, have a check of munezz's other thread [[COLOR=Blue]--here--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948998") . you will only need to follow this if you actually change the password and the keyring plays up as a result, if you restore the old one exactly as it was you can most likely ignore this step.

---

### Post by zephonic on 2012-03-29
> **yetiman64 said:**
> Pressing (and holding down) the shift key just after the BIOS POST screens (power on self test screens) is how to bring up the grub2 menu.  That is the first step to getting into a recovery console, so I'm a bit surprised that failed. It may take a few attempts, timing wise, to get it right.


I give up. I tried to get it right for 30+ minutes yesterday, and again now. I can't get into Recovery Mode. Any other suggestions before I bite the bullet and do a complete OS reinstall?

---

### Post by CharlesA on 2012-03-29
I thought you could get into recovery mode by booting off the livecd too. I might be wrong tho, because it's been a while since I've tried.

---

### Post by yetiman64 on 2012-03-29
> **zephonic said:**
> I give up. I tried to get it right for 30+ minutes yesterday, and again now. I can't get into Recovery Mode. Any other suggestions before I bite the bullet and do a complete OS reinstall?

One thought left for me, there are 2 shift keys. Did you try both of them out ?

It is possible you may have a faulty key. Rare as it may be, a dodgy "6" key has caused me strange problems with passwords in the past (intermittently worked, and near drove me mad trying to use the machine).

If you have tried them both to no avail, then that is very unfortunate and does sound to me like a reinstall scenario. Though I would wait a day or two and "bump" the thread once daily in case someone else has different knowledge that may help.

@ CharlesA I just saw your post while drafting, are you referring to chrooting into the broken install to fix it from a live cd ? That may very well work.

---

### Post by CharlesA on 2012-03-29
> **yetiman64 said:**
> 
@ CharlesA I just saw your post while drafting, are you referring to chrooting into the broken install to fix it from a live cd ? That may very well work.

Probably. I just checked and there wasn't an option for recovery mode off the 11.10 livecd.

I had to get into the grub menu on my new server and had to hook up a different keyboard to get it to show up.

---

### Post by yetiman64 on 2012-03-29
> **CharlesA said:**
> ...I had to get into the grub menu on my new server and had to hook up a different keyboard to get it to show up.
That is interesting.

OP, you mentioned earlier your machine is a Asustek NV80b laptop. Do you have a USB keyboard you can plug in and try the "normal" procedures mentioned earlier ?

---

### Post by CharlesA on 2012-03-29
> **yetiman64 said:**
> That is interesting.

OP, you mentioned earlier your machine is a Asustek NV80b laptop. Do you have a USB keyboard you can plug in and try the "normal" procedures mentioned earlier ?
Indeed. It might have been my PC though, because I had to hook up a different keyboard just to get into the BIOS (wired USB vs wireless) and the same thing applied to recovery mode - it wouldn't recognize the keypresses or something. *shrugs*

---

### Post by zephonic on 2012-03-29
> **CharlesA said:**
> I thought you could get into recovery mode by booting off the livecd too. I might be wrong tho, because it's been a while since I've tried.

Not sure what a liveCD is. I downloaded UB11.10 and have it on a USB flashdrive. Would that help?

> **yetiman64 said:**
> 
OP, you mentioned earlier your machine is a Asustek NV80b laptop. Do you have a USB keyboard you can plug in and try the "normal" procedures mentioned earlier ?

Only Apple keyboards...

---

### Post by CharlesA on 2012-03-29
> **zephonic said:**
> Not sure what a liveCD is. I downloaded UB11.10 and have it on a USB flashdrive. Would that help?

They are basically the same thing.

Not sure if an Apple keyboard would work or not.

---

### Post by yetiman64 on 2012-03-29
As CharlesA notes live-cd and live-usb are "basically the same" - the same install image is put onto different media only.

> **zephonic said:**
> ...Only Apple keyboards...

If the Apple keyboard is usb I'd tend to give it a try, though not sure it will work, but you only need the shift key on it to register and the rest can be input from the laptop once you're in (it is a bit of "a shot in the dark" - just hope it works).

If it doesn't there may be a more complex method, previously mentioned, that is to do a chroot into the broken install from the live usb. We'll see if you can get in the easy way first :-).

---

### Post by zephonic on 2012-04-01
Hi all,

thanks for your advice and suggestions, it is appreciated. Since I had nothing of real importance on this computer, I decided to just reinstall the OS.

In spite of it all, it is pretty awesome to install OS from a USB drive and be done with the whole thing in <15 minutes. =D>

---

