---
title: "[SOLVED] Help! after I log in,  the screen goes blank :("
date: 2008-08-06
forum: New to Ubuntu
---

### Post by endtheembargo on 2008-08-06
I broke my computer! I have a toshiba satellite A135 laptop that had feisty installed on it. When I upgraded to hardy 8.04, I lost all sound. I searched the forums to see if anyone else had experienced this, and I couldn't find anyone specifically, but there were folks w/ sound issues.

So I ended up copy and pasting some code into the terminal that I thought would fix the problem and now I can't even get into the computer. And unfortunately, because I am such a novice, and this was weeks ago, I don't know what the code was.

Now what happens when I turn on the computer is if starts to boot as usual. It says "grub loading stage 1.5" and the the ubuntu graphic pops up and it loads and then it prompts me to login w/ my username and password. Once I do that the computer just sits there forever.

Can anyone help! This is what I get for not knowing what I'm doing :(

---

### Post by tuxxy on 2008-08-06
Can you open a terminal by pressing CTRL + ALT + F1

---

### Post by endtheembargo on 2008-08-06
yep. what should I type in?

---

### Post by tuxxy on 2008-08-06
Well if you are having problems logging into any sort of GUI you could try reconfigure the xorg and follow the process through, you may need a reboot and to renable your videocard driver.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by philinux on 2008-08-06
> **tuxxy said:**
> Well if you are having problems logging into any sort of GUI you could try reconfigure the xorg and follow the process through, you may need a reboot and to renable your videocard driver.

```
sudo dpkg-reconfigure xserver-xorg
```

That does not work on Hardy now. It only configures keyboard and mouse. Assuming he is running Hardy

Reboot and when grub comes up press escape. Choose the recovery mode option. It's the second one down.

A menu will pop up, choose xfix then reboot.

---

### Post by endtheembargo on 2008-08-06
I got into it, but unfortunately I didn't understand it... It asked me several questions about reconfiguring my keyboard, which I didn't understand. I tried to guess my way through, and it eventually kicked me back to the terminal and said;

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.org.conf.20080806114326"

---

### Post by endtheembargo on 2008-08-06
yay! I'm back in, thank you. But now, I'm back to having no sound AND the computer won't recognize the wireless internet connection. What should I do? (should this be a new thread?)

---

### Post by philinux on 2008-08-06
> **endtheembargo said:**
> yay! I'm back in, thank you. But now, I'm back to having no sound AND the computer won't recognize the wireless internet connection. What should I do? (should this be a new thread?)

Yes absolutely, mark this one solved.

Start a thread for each problem it gets very confusing otherwise.
Make sure you include your full system specs and the version of ubuntu you're running. As you can see there are different fixes.

---

