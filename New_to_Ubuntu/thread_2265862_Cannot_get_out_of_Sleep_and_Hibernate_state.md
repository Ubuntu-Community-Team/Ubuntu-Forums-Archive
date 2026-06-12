---
title: "Cannot get out of Sleep and Hibernate state"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by Alain_Dang on 2015-02-18
Hi,
I have deployed successfully lubuntu 14.04 on my netbook ASUS eee pc 1201 HA
Most of the functions keys are running fine (Fn+Fx).
However when I use the Sleep or Hibernate function, I don't know how to get out of this state. I tried many buttons and even Power button.
I would appreciate any help on this issue.
Thanks in advance.
Alain.

---

### Post by bapoumba on 2015-02-18
Sorry for a stupid question : have you tried the space bar ? This is how my own lubuntu wakes up from hibernation.

---

### Post by Alain_Dang on 2015-02-19
I think I have hit all keys but I will try again and let you know.
Can you tell me if you have the same netbook and same lubuntu release ?
Thanks for your quick reply.

---

### Post by bapoumba on 2015-02-19
Nope, very old vaio laptop running 14.10. It did hibernate with 14.10 and I used to wake it up with the space bar.
You are most welcome, not sure this is going to help you though :)

---

### Post by Alain_Dang on 2015-02-26
The space bar does not work to wake up the netbook.
I tested each single button, combination of buttons and even the power button
And I have not found anything related to the keyboard in the BIOS setup.
I believe I have to live with this.

---

### Post by yetimon_64 on 2015-02-26
> **Alain_Dang said:**
> ...I believe I have to live with this.

Have a look at [[COLOR=#0000ff]--this link--[/COLOR]]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks"), the section titled "Asus Eee 1201HA" down the page a bit. It is for Lucid (10.04), and as such is old, but has mention of grub options for use with that model of "eee pc".
 
Hope it helps, good luck.

---

### Post by Alain_Dang on 2015-02-26
Thanks yetimon, I have already applied the information on this page.
It has permitted to enable some function keys that didn't work before such as Volume -/+ , screen disable (fn-F7).
But the sleep mode fn-F1 is not working and worse the wake-up is not working.
Thanks anyway for your help.

---

### Post by Jakey_TheSnake on 2015-02-26
If the power button isn't 'waking it up' from sleep, how are you going from your attempted suspend state to powered on again?

---

### Post by Alain_Dang on 2015-02-27
I have to force the shutdown (hold power button until the machine stops) and restart.
On restart the system raises 2 errors messages - I don't really behind the impact behind these errors.
If I am lucky then a clean shutdown / restart fix the problem (no more error message)

---

### Post by Jakey_TheSnake on 2015-02-27
Are you sure the machine is actually getting into the 'sleep' state? What indicates that it's unable to wake from sleep, rather than not able to go to sleep?

When you hibernate, does the machine power down fully? If not, it's not getting into the hibernate state properly - which probably means your issues aren't with waking up.

What are the error messages?

See if the information in this post is relevant to you: [http://ubuntuforums.org/showthread.php?t=1661070&p=10570374#post10570374](http://ubuntuforums.org/showthread.php?t=1661070&p=10570374#post10570374)

---

