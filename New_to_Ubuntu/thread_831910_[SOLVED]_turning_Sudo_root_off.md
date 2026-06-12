---
title: "[SOLVED] turning Sudo root off"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-17
Hi all,

The other day I used a command line with sudo in it, i can't remember what for now.

I just realised that I haven't turned off the Sudo root thing off..  how do I do this. I had this information somewhere but can't find it so i'm going into panic mode!

Thanks heaps!

---

### Post by _sphinx_ on 2008-06-17
just type ```
exit
```

---

### Post by Golem XIV on 2008-06-17
sudo is used just for the command that you entered, so you don't need to turn anything off.
If you're concerned about the system remembering the password, I think that it "stays" for 10 minutes (not sure exactly how much), after that time you have to input it again.

---

### Post by ibuclaw on 2008-06-17
By default, the sudo timestamp is set to 15 minutes. (The time until sudo times out and asks you for a password again).

So you should be OK!

But for future reference, you can run this command when you've finished running sudo (if so you wish).
```
sudo -K
```
The above command removes the timestamp, thus disabling your sudo "no password" privileges until you reactivate it again.

Regards
Iain

---

### Post by argail1980 on 2008-06-17
the terminal you used sudo in, will remember the password for 15 minutes or so, you don't have to turn it off. when the command was something like ```
sudo bash
``` or```
sudo xterm
```, then just enter exit or press Ctrl+D.

It's the same thing when you open an administrative application as synaptic. It will not prompt you for your password again for about 15 minutes, but you don't have to "turn it off"

---

### Post by ChameleonDave on 2008-06-17
> **scotcella said:**
> Hi all,

The other day I used a command line with sudo in it, i can't remember what for now.

I just realised that I haven't turned off the Sudo root thing off..  how do I do this. I had this information somewhere but can't find it so i'm going into panic mode!

Thanks heaps!

Relax.  It doesn't stay on.

---

### Post by scotcella on 2008-06-17
Whew!!!

Thanks guys!!

I feel better already...  still learning and always learning..  sometimes I feel like my questions are really dumb but getting there, learning something new everyday!

---

