---
title: "[SOLVED] New password not working"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-23
I just set a new password and when I try to log into my account, it won't work. None of the old ones wil work, either.

What can I do?

TIA.

---

### Post by Potatoj316 on 2008-07-23
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below... #-o 
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.

For future refrence google is your friend.  I had no idea how to do this either.  I spend 25 sec in google before finding the page that had this in it using this search "ubuntu change forgotten password"

I should have just posted this link
[http://www.google.com/search?hl=en&q=ubuntu+change+forgotten+password](http://www.google.com/search?hl=en&q=ubuntu+change+forgotten+password)

---

### Post by Joeb454 on 2008-07-23
Instead of that you could just boot into recovery mode (the 2nd option on the Grub Menu) and the when that's loaded the root prompt run ```
passwd <user>
``` where <user> is your username, follow the instructions and type reboot :)

Thereby cutting out 10 steps from the post above ;)

---

### Post by sisco311 on 2008-07-23
From the grub menu select the recovery mode.
from the root shell:
```
passwd *username*
exit
```
select the resume normal boot option.

---

### Post by Potatoj316 on 2008-07-23
I think the first 3 steps there are the most important.  But like I said I really dont know what im talking about, I asked google.

---

### Post by Joeb454 on 2008-07-23
Oh yes, the first 3 steps are definitely worth a try. But I think the rest is overcomplicating it just a little ;)

---

### Post by mczonie on 2008-07-23
> **Joeb454 said:**
> Instead of that you could just boot into recovery mode (the 2nd option on the Grub Menu) and the when that's loaded the root prompt run ```
passwd <user>
``` where <user> is your username, follow the instructions and type reboot :)

Thereby cutting out 10 steps from the post above ;)

OK. What exactly is a grub menu?

Sorry, but I'm a total newbie here.

---

### Post by Troll_the_Great on 2008-07-23
> OK. What exactly is a grub menu?

Sorry, but I'm a total newbie here.
The Grub menu is the menu that appears when you boot.It looks like:
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Memtest86
Windows XP (if you have dual boot with windows)

PS:mine shows up automatically

---

### Post by sisco311 on 2008-07-23
> **mczonie said:**
> OK. What exactly is a grub menu?

Sorry, but I'm a total newbie here.


 When the computer first starts up, you have a few seconds to push esc to go into GRUB.
(If doesn't shows up by default)

> Ubuntu 8.04, kernel 2.6.24-19-generic
[B]Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
[/B]Ubuntu 8.04, memtest86+

---

### Post by Joeb454 on 2008-07-23
It shows up by default if you have a dual boot. If not then it's hidden

---

### Post by mczonie on 2008-07-23
> **Troll_the_Great said:**
> The Grub menu is the menu that appears when you boot.It looks like:
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 recovery mode
Memtest86
Windows XP (if you have dual boot with windows)

OK, but when I see that, how do I select recovery mode? That menu goes away pretty fast.

---

### Post by sisco311 on 2008-07-23
Also the reboot (after the password was changed) is unnecessary.
*init 2* will do the trick.:twisted:

---

### Post by Joeb454 on 2008-07-23
We're dealing with a newcomer here, lets not delve into init options ;)

And just keep hitting the down arrow key before the menu comes up, then it should cancel the timer and you can scroll up (or down) to the correct option :)

---

### Post by sisco311 on 2008-07-23
> **mczonie said:**
> OK, but when I see that, how do I select recovery mode? That menu goes away pretty fast.
use the arrow keys(up/down) and the Enter (Return)

---

### Post by Troll_the_Great on 2008-07-23
> OK, but when I see that, how do I select recovery mode? That menu goes away pretty fast.
You can go to System-Administration-StartUp-Manager and from the "Timeout" option you can chose haw many second do you have before it boots automatically the default option.

---

### Post by Joeb454 on 2008-07-23
Startup Manager would need to be installed first though ;)

It's in the repo's so you can install it from synaptic et al.

---

### Post by Troll_the_Great on 2008-07-23
> **Joeb454 said:**
> Startup Manager would need to be installed first though ;)

It's in the repo's so you can install it from synaptic et al.

Lol, forgot about that.:)
Thanks.

---

### Post by mczonie on 2008-07-23
> **Troll_the_Great said:**
> The Grub menu is the menu that appears when you boot.It looks like:
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Memtest86
Windows XP (if you have dual boot with windows)

PS:mine shows up automatically

There were two different recovery modes. One I think was "Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode" and the other was the same, but I think the number at the end was 16 instead of 19.

Anyway, I don't remember which one I went into, (I think it was 19) but I reset my password and then pressed Ctrl+alt+delete to get out. That restarted the computer and it asked me for a password and user name like usual. I entered my username and new password and now I'm in.

Am I out of root now?

---

### Post by Joeb454 on 2008-07-23
Yes, the recovery mode boots into root by default (so you can fix system-wide things).

If you're booting into you're normal system and logged in as yourself, you're no longer root :D

You can also mark your thread as solved from thread tools at the top of this page :)

Edit: See [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) for more info

---

### Post by mczonie on 2008-07-23
> **Joeb454 said:**
> Yes, the recovery mode boots into root by default (so you can fix system-wide things).

If you're booting into you're normal system and logged in as yourself, you're no longer root :D

You can also mark your thread as solved from thread tools at the top of this page :)

Edit: See [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) for more info

Thanks. Just out of curiosity, why were there two different options for recovery mode? There were also two different options for generic mode, too.

---

### Post by Joeb454 on 2008-07-23
They're differnet kernel versions.

I have -19 and -18 in my list currently :)

---

