---
title: "'x' key on keyboard activates xkill!"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by lauribuntu on 2013-02-25
G'day.

I have an unusual problem I can't find a solution to.

I updated my other desktop computer this afternoon(12.04 32 bit plain-jane ubuntu) which has been running fine for months BTW..

I continued working, surfing the web mainly, and some time later Firefox seemed to corrupt. I was trying to type a email message and misspelt 'next'; 'net'.

I attempted to correct the spelling mistake and insert the 'x' pressed 'x' on the K/B, and next thing the tell-tale [SIZE=3]'**x'**[/SIZE] cursor of **xkill **appeared and was xkill was running!  As soon as I clicked on the email (web-based) Firefox closed.

Opened FF again home page appeared (google) typed an 'x' in the search box, same thing happened, xkill running clicked on page killed FF.

Tried this again on the desktop, killed GNOME.

Restarted computer, same thing again.

Shutdown again deleted my K/B shortcut CNTRL-ALT-X for xkill, rebooted again, same thing again.

This time shutdown, tried a new keyboard/mouse combo - same thing.

Help please! This is weird!

Thanks

~L.

---

### Post by matt_symes on 2013-02-25
Hi

Can you post the output of

```
ls -l /etc/dconf/profile/
```and

```
whoami
```Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

Can you post the output of

```
ls -l /etc/dconf/profile/
```and

```
whoami
```Kind regards

Sure thing Matt; as long as  I don't type an 'x'!

ls -l /etc/dconf/profile
total 4
-rw-r--r--  1 root root 9 Sep 24   2011 gdm

whoami
lauricat

thanks matt.

~L

---

### Post by matt_symes on 2013-02-25
Hi

I'm wondering if the setting are in the dconf profile.

```
grep -R kill /etc/dconf/profile/*
```

See if that returns anything.

Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

I'm wondering if the setting are in the dconf profile.

```
grep -R kill /etc/dconf/profile/*
```See if that returns anything.

Kind regards

G'day Matt.

Tried that returned nothing back.

Still the same problem.

Thanks

~L.

---

### Post by matt_symes on 2013-02-25
Hi

Let's make 100% sure of the dconf setting

```
sudo mv /etc/dconf/profile{,.old}
```

```
sudo reboot
```

How does that work ? It can always be reverted.

Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

Let's make 100% sure of the dconf setting

```
sudo mv /etc/dconf/profile{,.old}
``````
sudo reboot
```How does that work ? It can always be reverted.

Kind regards

G'day Matt.

Tried all that - no output after the first part (ie just back to the prompt - but no changes.

I still have the 'x' character killing everything!

Thanks once again.

~L.

---

### Post by matt_symes on 2013-02-25
Hi

You're right. This is an odd one and may take some tracking down.

can we do the same with your gconf setting next.

```
mv ~/.gconf{,.old}
```

```
sudo reboot
```

Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

You're right. This is an odd one and may take some tracking down.

can we do the same with your gconf setting next.

```
mv ~/.gconf{,.old}
``````
sudo reboot
```Kind regards

G'day again Matt.

Tried that - seems fixed!

I notice my close, minimise, maximise have shifted back to the left hand side (I had them on the right, I run GNOME 3 instead of UNITY.

So what did I actually do? Re-intialize my config file?

What might have caused this?

Thanks very much!

Laurie.

Thanks

~L.

---

### Post by matt_symes on 2013-02-25
Hi

Put you dconf setting back.

```
sudo mv /etc/dconf/profile.old /etc/dconf/profile
```

Then 

```
grep kill ~/gconf.old
```

Post back on last command.

Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

Put you dconf setting back.

```
sudo mv /etc/dconf/profile.old /etc/dconf/profile
```Then 

```
grep kill ~/gconf.old
```Post back on last command.

Kind regards

OK Matt here is the output of the last command:

grep: /home/lauricat/gconf.old: No such file or directory

NOTE: Before your last post with these instructions I went in and changed gconf ;
like this;

“**close,maximize,minimize:**” to “**:minimize,maximize,close**” 

in apps/metacity/general.

I hope i did not muck things up!

Thanks again.

~L.

---

### Post by matt_symes on 2013-02-25
Hi

I have really no idea how that happened if grepping did not find it.

Clean up by deleting the old gconf folder

```
rm -r ~/gconf.old
```I would have loved to track down the reason why but I'm glad it's fixed :)

Kind regards

---

### Post by lauribuntu on 2013-02-25
> **matt_symes said:**
> Hi

I have really no idea how that happened if grepping did not find it.

Clean up by deleting the old gconf folder

```
rm -r ~/gconf.old
```I would have loved to track down the reason why but I'm glad it's fixed :)

Kind regards

Just did that - "No such file or directory"

Thanks anyway.

~L.

---

