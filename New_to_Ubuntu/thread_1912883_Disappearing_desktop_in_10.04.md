---
title: "Disappearing desktop in 10.04"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Zenrunner92 on 2012-01-21
This has been my second attempt to install a dual boot Ubuntu alongside Win 7 on my laptop (U7300 processor, 4GB RAM, brand new 80GB SSD).  The first time, I made the mistake of loading the proprietary Nvidia driver as suggested by Ubuntu's Hardware wizard, which rendered both operating systems inoperable---I had to use my Win7 repair disk to fix it so that I could boot into Win7 again, from where I had to erase the Ubuntu partition and then reinstall it manually with the Live CD.

This time everything was going well for several hours and I thought I was finally in the clear.  I did not try to install the Nvidia driver...but after loading all the security updates and a few of the "recommended" ones, I did upgrade the kernel to 2.6.38 (I have another computer, an Atom netbook running 10.04 which has been on 2.6.38 without any problems for several months now).  Everything was going well until:

1. Wanting to create a 3rd desktop panel, I right clicked on one of my panels and chose "Add New Panel."  

2. Nothing happened.  So I did it again.

3. This time the 3 screenlets I had parked on the right edge of my screen moved to the left, as if a new panel had been added there.  But there was none, and no amount of left or right clicking on that strip of empty desktop space had any effect.

4. I tried to do "Add New Panel" one more time, at which the system froze/crashed.  Had to do a hard restart.

5. With the hard restart, I am still able to boot into Win7 but now when I try to boot into Ubuntu, I just get a blank desktop: no screenlets, no panels, just the default desktop background.  

Please tell me there's a way for me to revert or restore or do something OTHER than have to reinstall Ubuntu a THIRD bloody time! ](*,)](*,)](*,)

---

### Post by sanderd17 on 2012-01-21
You could delete all gnome settings and start over again (if you're willing to do this).

When you boot, go to the first terminal by pressing CTRL+ALT+F1 (to go back to the GUI screen, you'll have to press CTRL+ALT+F7).

There you can log in as your regular user (if your password contains numbers, don't use the numpad but the numbers on your pain keyboard part).

Now you can delete the settings by removing some settings folders. I don't know exactly where the right setting is, but I would first try with the gconf settings:

```

rm -r ~/.gconf*

```

If that doesn't work, try deleting the .gnome2 and the .local directory

```

rm -r ~/.gnome2
rm -r ~/.local

```

---

### Post by Zenrunner92 on 2012-01-21
Thanks, but what would be my next step after typing in each of those commands---reboot?  I guess what I'm wondering about is how I would go about generating new versions of those files that I'd be deleting...or does Ubuntu do that automatically as soon as it removes the existing ones?

---

### Post by Zenrunner92 on 2012-01-21
a tangential question: would I gain any significant benefits, in either performance or stability, by downloading and installing a 64 bit version of Ubuntu instead of the 32 bit version on the Live CD?  My laptop runs Win 7 64 bit but only takes a max of 4GB of RAM, so currently with the 32 bit Ubuntu only 2.9GB is usable/recognized...

I thought I'd read somewhere that the 64 bit version might actually be LESS stable...?

---

### Post by Sigma1 on 2012-01-21
Hello,
If your desktop appears to have disappeared completely, then you may, possibly, be booting into a GNOME user-defined session without realising it, in which case Alt + Right Click will enable you to put things back on the taskbar. This might be enough. (Check also, when you boot, that you are not booting into something other than "ubuntu", "ubuntu classic", "ubuntu 2d" or whatever.)
If you remove your .gnome2 and .gconf settings folders, then I imagine they will get regenerated anyway, but if you're not happy with that, you can always just rename them, i.e. instead of
```
rm -r ~/.gconf*
rm -r ~/.gnome2
rm -r ~/.local
```
then something like
```
mv ~/.gconf/ ~/.gconf-old/
mv ~/.gnome2/ ~/.gnome2-old/
mv ~/.local/ ~/.local-old/
```
That way, if something were to go wrong, you just rename them back to what they were before, then things at least won't be any the worse! That is:
```
mv ~/.gconf-old/~/.gconf/ 
mv ~/.gnome2-old/ ~/.gnome2/
mv ~/.local-old/ ~/.local/
```
Can't help with the 64bits question. From what I've read a 64bit computer will run faster with a 64bit Ubuntu.

---

### Post by Zenrunner92 on 2012-01-21
Well, I followed Sander17's instructions and after restarting, got it to boot up again just fine...WHEW!  

I now have to reconfigure the panels on the desktop since all the shortcut icons that I had put on the two panels have disappeared, but at least all the software is still there and I am spared having to reinstall Ubuntu for the 3rd time.

At this point I will do everything I can to avoid having another episode like this, so no 64 bit Lucid for me...need time to recover and recuperate, LOL

Thanks so much for your help, much appreciated!

---

### Post by sanderd17 on 2012-01-22
@sigma1: indeed, moving them instead of removing might be safer, but those settings aren't very important anyway. So most of the time they end up unused afterwards.

If you would have to reset important settings (like grub settings), a move instead of a remove is always preferred.

> **Zenrunner92 said:**
> a tangential question: would I gain any significant benefits, in either performance or stability, by downloading and installing a 64 bit version of Ubuntu instead of the 32 bit version on the Live CD?  My laptop runs Win 7 64 bit but only takes a max of 4GB of RAM, so currently with the 32 bit Ubuntu only 2.9GB is usable/recognized...

I thought I'd read somewhere that the 64 bit version might actually be LESS stable...?

The stability issues of 64-bit are all gone in the last years. So the only reason to prefer 32-bit over 64-bit is when you don't want to download it again, or if you have an old 32-bit-only compatible processor.

---

### Post by Zenrunner92 on 2012-01-22
> **sanderd17 said:**
> 
The stability issues of 64-bit are all gone in the last years. So the only reason to prefer 32-bit over 64-bit is when you don't want to download it again, or if you have an old 32-bit-only compatible processor.

So no more incompatibility issues or lack of driver support, esp. with Flash?  I must admit most of the Google research I've done about this issue has been gotten from 2-5 year old postings...

I've also gotten the impression that the 64 bit version of Ubuntu is more reliable in the latest 11.04/10 distros rather than in 10.04...what's your take on that?

---

### Post by sanderd17 on 2012-01-22
> **Zenrunner92 said:**
> So no more incompatibility issues or lack of driver support, esp. with Flash?  I must admit most of the Google research I've done about this issue has been gotten from 2-5 year old postings...

I've also gotten the impression that the 64 bit version of Ubuntu is more reliable in the latest 11.04/10 distros rather than in 10.04...what's your take on that?

10.04 is probably on the edge for good flash support. But for other things, it's the same.

---

