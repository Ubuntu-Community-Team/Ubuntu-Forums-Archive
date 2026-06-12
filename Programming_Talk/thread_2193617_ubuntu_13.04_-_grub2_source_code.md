---
title: "ubuntu 13.04 - grub2 source code?"
date: 2013-12-13
forum: Programming Talk
---

### Post by squakie on 2013-12-13
Does anyone know where to find the source code - if it's publicly available - for grub2?  I have no clue if I could even begin to follow it, but something has come up that leaves me curious and I'd like to check that code to see if a suspicion may be correct.

Thanks.

---

### Post by oldfred on 2013-12-13
This has direct links. But when I looked I had no idea what to do.
 Grub2 2.00 released June 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyODA](http://www.phoronix.com/scan.php?page=news_item&px=MTEyODA)

---

### Post by steeldriver on 2013-12-13
If you enable the appropriate deb-src in your /etc/apt/sources.list (it's in the universe repo I think - but check with apt-cache) you can download it directly

```
apt-get source grub2
```

This should also apply any patches required to bring the source in line with the current binary deb on your system

Or am I misunderstanding your question?

---

### Post by squakie on 2013-12-14
Going to try all of that real soon here early a.m. since I'm still up.  Indeed, I'd like the actual source code for grub2 as delivered in Ubuntu.  The reason:  trying to help on another post where the save-selected options have been added to grub2 yet it doesn't show it on reboot.  I *think* I have it narowed down to where the grub.cfg command savedefault (I think that was it - I would need to look again) must not be saving things correctly.  The saved selection should be in /boot/grub/grubenv file, and indeed the very first option from the grub menu seems to go there by default when you have the saving enabled.  The restoration of that value to the menu seems to work, since I hard-coded it in grubenv and the menu entry was highlighted.  This makes me think the save itself isn't actually working - perhaps the grub.cfg  keyword is incorrect, perhaps the code isn't doing it.  If I can even follow it at all maybe I can trace something.  Personally I have no need for it - my grub menu works just fine for me.  It just sounded interesting in the thread so I decided to experiment and try it out.

As a word of caution:  changing the contents of /boot/grub/grubenv using an editor like gedit just to test apparently isn't a good idea - everytime I boot now grub throws out an error about some block size being too small and then it takes the proverbial "forever" for it to boot (ok, maybe a couple of minutes ;) ).

Thought as long as I've go my system screwed up I might as well try to figure this out for the other person's thread.  Going to reload anyway due to a hard disk "upgrade" (nothing big like I would like, but it least it will be a little bigger than what I'm running).

---

### Post by squakie on 2013-12-14
Interesting turn of events - found a grub program "command" save_env - which I assume probably stands for save environment - like perhaps the /toob/grub/grubenv file?   I thought what the heck - try it, my system is screwed right now anyway.  So I put it in 2 places in /boot/grub/grub.cfg itself to test it:

- in the default entry for Ubuntu normal boot.  Putting it here resulted in 2 of the "environment block too small messages" - I suspect this may have something to do with the entire problem.

- in the entry for my small Windows XP boot.  Putting it there resulted in some sort of error with "magik" in it and all I could do was press any key, wait for a while, then get the boot menu back.  So, not sure what's going on there.

Still haven't been able to get the source.  I've been looking through some of the config files in /etc/grub.d - especially the 20_xxxxxx one - that's where I found one of the functions declared and it uses that save_env "command" to the program.

Not sure it's all worth it - I'm not sure how many people even have tried to use this.

---

### Post by squakie on 2013-12-14
> **oldfred said:**
> This has direct links. But when I looked I had no idea what to do.
 Grub2 2.00 released June 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyODA](http://www.phoronix.com/scan.php?page=news_item&px=MTEyODA)

It is a wee bit difficult to make much sense of it.  I did find where it loads in the environment variables from the grubenv file, and where it also saves them (I was right - it's the save_env command in grub.cfg).  That also has the error message for environment block too small - I need to look at that to see how they determine what that size should be, etc..  That would definetly cause the default selection not to be saved. 

You know, if I was as sharp as I was years ago I could figure this all out pretty quick.  Those days are LONG gone, so it's muddle time ;)

---

