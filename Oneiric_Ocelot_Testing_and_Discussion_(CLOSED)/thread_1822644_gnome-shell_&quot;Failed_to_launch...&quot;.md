---
title: "gnome-shell &quot;Failed to launch...&quot;"
date: 2011-08-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zonum on 2011-08-10
Hello all,

Using gnome-shell, I cannot get the System Settings to run.  Everytime I attempt from either my name on the upper right, and select "System Settings" or Activities->Applications->System Settings, I keep getting a notification at the bottom of the screen that says:

"Failed to launch 'System Settings" Not Found"

Any ideas?  I am up to date as of 8/10/2011

---

### Post by Quackers on 2011-08-11
Yes, I'm seeing the same thing except for the error message. I don't get one. It just won't start.

---

### Post by Harry33 on 2011-08-11
That application is working fine here on all three setups I use:
- 64-bit Nvidia
- 64-bit ATI
- 32-bit Intel

They are all up to date ATM and I have Gnome-shell on all of them (Unity purged).

---

### Post by Quackers on 2011-08-11
I'm on 64 bit and nvidia-current, running gnome-shell.
It all seems odd at the moment :-)

---

### Post by Harry33 on 2011-08-11
> **Quackers said:**
> I'm on 64 bit and nvidia-current, running gnome-shell.
It all seems odd at the moment :-)

I you want to try, you could purge gdm and switch solely to lightDM.
Gdm may break gnome-settings-daemon.
However themes should also work badly then.

---

### Post by cbowman57 on 2011-08-11
Quackers, the nvidia-current from Ubuntu was buggy the other day.  I had to use the 280.13 from x-org-edgers to get it to run right.

---

### Post by Quackers on 2011-08-11
Ok thanks guys, that gives me some ideas to work with :-)

---

### Post by cbowman57 on 2011-08-11
Yeah, it was driving me buggy.  Unusual that Ubuntu & x-org-edgers both have a 280.13 available, but there is a difference.  The official one wouldn't cooperate with my shell at all.

Hope it fixes the problem for you.

---

### Post by dino99 on 2011-08-11
> **cbowman57 said:**
> Yeah, it was driving me buggy.  Unusual that Ubuntu & x-org-edgers both have a 280.13 available, but there is a difference.  The official one wouldn't cooperate with my shell at all.

Hope it fixes the problem for you.

is that problem been reported ?

---

### Post by zonum on 2011-08-13
I took care of this issue by:

sudo apt-get purge gnome-shell

then re-intalled gnome-shell:

sudo apt-get install gnome-shell

Thanks for the replies...

---

