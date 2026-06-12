---
title: "Beginner Boot problem"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by martynJ on 2008-11-03
Hi

I'm new to Ubuntu, and everything was going fine until I tried to log in one time and get the error "Your session only lasted less than 10 seconds. 

Error details...

```
/etc/gdm/Xsession: 192: ls: Beginning session setup...
/etc/gdm/Xsession: 192: ls: not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
exec: 206: x-terminal-emulator: not found

```
safe GNOME works ok.

Looking at /etc/gdm/Xsession, line 192 relates to iterating over sessions. Unfortunately I'm not familiar with that scripting language!

Have googled for hours for relative information but haven't found anything that relates (that I can understand anyway).

Thanks in advance for any assistance.

Martyn

---

### Post by martynJ on 2008-11-03
Why is my heading not in bold and everyone elses is?

---

### Post by martynJ on 2008-11-03
Further information...

I had **exactly** the same problem on a new laptop a month ago ~ again it just happened randomly. I posted here to no result and eventually reinstalled ubuntu. I don't want to do that now as I have spent a week configuring the machine. :( 

Trying to dig deeper, the startup appears to fail when running the Xsession script here...

```
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi

```

Does anybody know how to delete the session or reset the session to default?

Desperate here! And frankly not loving ubuntu at the moment!

Thanks

Martyn

---

### Post by pastalavista on 2008-11-03
Reboot in 'recovery mode' and select the option 'xfix' or 'repair xorg' depending on your version.

---

### Post by martynJ on 2008-11-03
Thanks Pastalavista

The only rescue mode I can find (except safe-mode) is on the live CD-ROM. Unfortunately F4 (rescuing a broken system) doesn't do anything (in fact only F1 help works). Pressing F4 help in F1 mode returns the following...

"There is no dedicated rescue mode on this CD. etc etc"

Is this the 'rescue mode' I need to run xfix ?

Thanks 

Martyn

---

### Post by pastalavista on 2008-11-03
When GRUB (boot loader) starts, in the list of kernls, each kernel also has a recovery mode boot option just below the normal boot. NOT the live CD, but the hard disk installation. When the boot screen loads, press the down arrow once to select "recovery mode" which is written at the end of the heading.

---

### Post by martynJ on 2008-11-03
Hi Pastalavista

Thanks for the info. That boot menu was on the screen for such a short time (one second) that I didn't realise it was a menu!

Unfortunately xFix didn't change or cure the problem.

Regards

Martyn

---

### Post by martynJ on 2008-11-03
Any further suggestions, for what must surely be a fairly common occurrence (I've had same error on two completely different computers)! I've wasted a day, and am losing the will to live!

Thanks 

Martyn

---

### Post by martynJ on 2008-11-03
Bump!

---

