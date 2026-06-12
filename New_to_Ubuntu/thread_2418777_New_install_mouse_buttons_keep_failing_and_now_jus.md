---
title: "New install mouse buttons keep failing and now just a black screen on boot"
date: 2019-05-11
forum: New to Ubuntu
---

### Post by thomasanderson777 on 2019-05-11
Hi,

Incredibly frustrated with how Windows 10 is, I thought I'd just download Ubuntu and be done with it.

I used Red Hat Linux at university years ago, and dabbled with Ubuntu years and years ago. The last time was three years ago, I didn't like the interface by that time though so I tried Linux Mint, which led to many difficulties on my cursed machine, a Toshiba Satellite. So I went back to Windows, but now I decided I don't care about the interface, I just want something that works.

Somewhere along the line, Ubuntu appears to have stopped working. First, the touchpad buttons don't work (although they don't on Windows 10 so could be hardware failure). The mouse works up to a point and then the mouse clicks just stop doing anything. You can <ALT><TAB> through windows and still type in the terminal, but eventually the time will come where I can't do anything as the mouse doesn't click. So I have to power the machine off and on again to complete installation of whatever I am installing at the time (NordVPN and Arduino). This happens about every 5-10 minutes.

Now, thanks to turning the machine off without powering down properly, I just get a black screen that says

```
error: failing reading sector 0x802 from 'hd0'
Entering rescue mode...
grub rescue>
```

I knew there would be some things I would need to tweak but constant crashing until it was rendered unusable within the space of a few hours was not what I expected! &#2029;Can anybody advise to what may be causing this rapid descent?

---

### Post by Autodave on 2019-05-11
Can we have some specs on the machine please?  When you say that the mouse stops working: are you talking about the mouse pad?  Did you try an external mouse?

---

### Post by xyloid2 on 2019-05-11
The best thing to provide us would be logs, specifically journalctl logs. 
If you can access the internet through the machine, 

    $ journalctl | nc termbin.com 9999

paste the output of this command.

---

