---
title: "[SOLVED] enable num lock at startup"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by ricardisimo on 2008-07-05
I don't even remember how I did this when I was on Ubuntu (Feisty) but I remember it was quick and easy. No such luck on KDE. I just want the number keypad enabled from the word go. How do I do that? Thanks in advance.

P.S. - I'm on Hardy

---

### Post by rbprogrammer on 2008-07-05
Hahaha, you know what? I'd like to know th answer to that too.

I'm on my mac now so I would not be able to check, but I remember hearing about a program in the repositories that can allow you to enable and disable numlock via command line.  My thought is that if you are able to find out what the name of that program is called, then it might be easy to write a little bash script that will run at startup.

The name should be something like "numx" or "numlockx" something along those lines.  But if you're able to find it out, keep me posted.

---

### Post by drs305 on 2008-07-05
You can install numlockx and it will take care of it.

synaptic or 
```
sudo aptitude install numlockx
```

Added:

I did find this note regarding numlockx and kubuntu, although I can't verify it:
```

In KDE don't use numlockx, rather set it in the Control Centre under 'Peripherals' -> 'Keyboard'.

```
Comes from this thread: [http://ubuntuforums.org/showthread.php?p=4994692](http://ubuntuforums.org/showthread.php?p=4994692)

---

### Post by ricardisimo on 2008-07-05
Oops! This is a tad embarrassing... From [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) --->
> Enabling NumLock in KDE (as used in Kubuntu)
From the K Menu, launch System Settings and click on Keyboard (Edgy users: K Menu -> System Settings -> Keyboard and Mouse -> Keyboard). You can see in the middle section the options for "NumLock on KDE Startup", where you can choose to Turn On, Turn Off, or Leave Unchanged. Select "Turn On" to turn NumLock on at startup.
Many thanks to the kind folks in the IRC Ubuntu channels.

---

### Post by ricardisimo on 2008-07-08
There is still one odd thing here: the num lock indicator on the keyboard doesn't light up at start, even though num lock is definitely on and working. Furthermore, if I press "Num Lock" on the keyboard, the light does come on, but then the numbers keypad stops working.

It's a tad confusing. I suppose I'll get over it, but there should be a way to correct this, no?

---

### Post by editrix on 2008-07-08
> **ricardisimo said:**
> There is still one odd thing here: the num lock indicator on the keyboard doesn't light up at start, even though num lock is definitely on and working. Furthermore, if I press "Num Lock" on the keyboard, the light does come on, but then the numbers keypad stops working.

It's a tad confusing. I suppose I'll get over it, but there should be a way to correct this, no?

I have the same problem. I assume it's a bug in KDE, since the light comes on when I boot into Gnome. As to whether they'll fix it--my understanding is they're too busy with kde4 to spend time on kde3.

---

### Post by luvr on 2008-11-09
Perhaps [*"Hardy Heron 8.04: Turning NumLock On"*]("http://ubuntuforums.org/showthread.php?t=780693") might help?

Something is not quite right about how the NumLock LED and the NumLockon/off status are handled, but in the linked post, I explain how I could circumvent this issue.

---

