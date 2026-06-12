---
title: "What if I forget my password?"
date: 2008-08-19
forum: Recurring Discussions
---

### Post by garyed on 2008-08-19
I was just asked this question by a friend of mine who's thinking about installing Ubuntu & I didn't know the answer. I'm the only one with administrator priviliges on all my computers so if I forgot my password am I 
up a creek. Would there be a way to boot the live CD & reset it or would I have to do a complete reinstall?

---

### Post by iaculallad on 2008-08-19
> **garyed said:**
> I was just asked this question by a friend of mine who's thinking about installing Ubuntu & I didn't know the answer. I'm the only one with administrator priviliges on all my computers so if I forgot my password am I 
up a creek. Would there be a way to boot the live CD & reset it or would I have to do a complete reinstall?

Login using Recovery Mode, then:

```
passwd your_username
```

---

### Post by garyed on 2008-08-19
> **iaculallad said:**
> Login using Recovery Mode, then:

```
passwd your_username
```

I'm not sure I understand.
Do you mean from Grub select the recovery option? 
Will it then prompt me to enter a new password?

---

### Post by Ocxic on 2008-08-19
yes choose the recovery option.

then you have to type in "passwd your_username" (press enter) to change your password.

---

### Post by aysiu on 2008-08-19
More details here (with screenshots):
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by garyed on 2008-08-19
Thanks to everyone for all the info.
It does seem like the recovery option is a security risk though.

---

### Post by aysiu on 2008-08-19
> **garyed said:**
> Thanks to everyone for all the info.
It does seem like the recovery option is a security risk though.
Not really. Physical security is the best security of all. If someone is able to reboot your computer and select boot options, *and* she knows what she's doing, she can do pretty much whatever she wants. I have a guide [here](http://www.psychocats.net/ubuntucat/how-to-reset-a-windows-xp-password-with-ubuntu/) for resetting a Windows XP administrator password with a Ubuntu CD.

You can reset the password in Mac OS X by booting into its recovery mode, too, by just holding down Cmd-S during bootup.

---

### Post by t0p on 2008-08-20
> **garyed said:**
> Thanks to everyone for all the info.
It does seem like the recovery option is a security risk though.

If an unauthorized user has physical access to any pc - be it running Linux, Windows, OSX, whatever - he will be able to gain access.  So if you have sensitive material on your computer, encrypt it.  There are various utilities for creating encrypted directories and filesystems, and I believe the alternate-install CD gives an option to encrypt the entire hard disk.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by Too Late on 2008-08-20
> **MarkieB said:**
> surely in principle, a computer with a password-protected BIOS, an 'unopenable' case, a BIOS set not to boot from cd[/floppy], plus in the case of ubuntu **comment the recovery mode option in /boot/grub/menu.lst**, is resistant to access for as long as the passwords + case resist brute force?
:idea: No, you can press 'e' or 'c' to manually boot from grub.

edit: But there seems to be a password feature in grub, too.

---

### Post by t0p on 2008-08-20
> **MarkieB said:**
> surely in principle, a computer with a password-protected BIOS, an 'unopenable' case, a BIOS set not to boot from cd[/floppy], plus in the case of ubuntu comment the recovery mode option in /boot/grub/menu.lst, is resistant to access for as long as the passwords + case resist brute force?

In principle, you're probably right.  In practice, I've never heard of an unopenable computer case. If someone wants to get at your hard disk, they will.  But they won't crack encryption unless they have access to a super-computer.

---

### Post by mcduck on 2008-08-20
> **MarkieB said:**
> surely in principle, a computer with a password-protected BIOS, an 'unopenable' case, a BIOS set not to boot from cd[/floppy], plus in the case of ubuntu comment the recovery mode option in /boot/grub/menu.lst, is resistant to access for as long as the passwords + case resist brute force?

Sure, in priciple. But practically speaking I've never even seen a case that wouldn't pop open with just about any tool you can find. After that all BIOS passwords and such are meaningless.

Anyway, even in that kind of setup I wouldn't recommend removing the recovey mode from Grub. Grub can use password protection for it, if you want to secure it. Of course before that would be any use you'd also need to take all the other steps mentioned here (like finding the case that any 12-year old can't open with a pen & rubberband.. :D)

---

### Post by aysiu on 2008-08-20
*Resistant* would be the key would there. I would rephrase it to be that adding in a password-protected BIOS, etc. would be a good way to *slow down* someone compromising your computer. Of course, if she can just steal your computer, she'll have all the time in the world to pry open your case and reset the BIOS.

It's all about making sure untrustworthy folks do not have physical access to your computer.

---

### Post by LowSky on 2008-08-20
Aysiu, thanks for that link to reseting Windows passwords form Ubuntu, very handy! I needed that for my sister's laptop.

Password protecting is actually a very insecure way to protect anything.
There is an old saying that goes, "Locks keep honest people from stealing." A real thief knows how to get at anything they want.

---

### Post by egwest on 2008-08-20
> **t0p said:**
> In principle, you're probably right.  In practice, I've never heard of an unopenable computer case. If someone wants to get at your hard disk, they will.  But they won't crack encryption unless they have access to a super-computer.


Resetting the BIOS on desktops is simple. unplug the computer, remove the case, pop out the battery, plug the computer back in and boot up. Then shut down and put the battery back and and put everything back together. BIOS is now reset back to factory settings.

Nothing is ever one hundred percent secure, there is always someone who knows a way around any problem, all you can do is make it harder for them to get access.

---

### Post by LaRoza on 2008-08-20
> **MarkieB said:**
> surely in principle, a computer with a password-protected BIOS, an 'unopenable' case, a BIOS set not to boot from cd[/floppy], plus in the case of ubuntu comment the recovery mode option in /boot/grub/menu.lst, is resistant to access for as long as the passwords + case resist brute force?

No. You are forgetting other ways of getting passwords (keyloggers, webcams and social engineering leap to mind)

---

### Post by LaRoza on 2008-08-20
> **aysiu said:**
> Not really. Physical security is the best security of all. If someone is able to reboot your computer and select boot options, *and* she knows what she's doing, she can do pretty much whatever she wants. I have a guide [here](http://www.psychocats.net/ubuntucat/how-to-reset-a-windows-xp-password-with-ubuntu/) for resetting a Windows XP administrator password with a Ubuntu CD.

You can reset the password in Mac OS X by booting into its recovery mode, too, by just holding down Cmd-S during bootup.

Can you do that in Vista as well?

---

### Post by aysiu on 2008-08-20
> **LaRoza said:**
> Can you do that in Vista as well?
I've never tried it on Vista (I don't have access to a Vista computer), but the [chntpw homepage](http://home.eunet.no/~pnordahl/ntpasswd/) seems to indicate it works for Vista as well.

---

### Post by LaRoza on 2008-08-20
> **aysiu said:**
> I've never tried it on Vista (I don't have access to a Vista computer), but the [chntpw homepage](http://home.eunet.no/~pnordahl/ntpasswd/) seems to indicate it works for Vista as well.

I will try it and let you know (eventually) Not worth a reboot at the moment.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by mcduck on 2008-08-21
> **LaRoza said:**
> Can you do that in Vista as well?

Even if you can't, you still get full access to all files and contents of the computer with any live-CD.. ;)

---

