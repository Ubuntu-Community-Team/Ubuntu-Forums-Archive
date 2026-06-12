---
title: "How to get larger pointer - Gutsy"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by movrshakr on 2008-07-11
How can I increase the mouse pointer size both in the pre-login screen and after login?  Gutsy.

---

### Post by appi2012 on 2008-07-11
Go to System -> Preferences -> Appearence. Click on the cursor tab. I'm not sure if there's a slider to adjust the size, or different cursors with different sizes. From there it should be pretty easy

---

### Post by movrshakr on 2008-07-11
> **appi2012 said:**
> Go to System -> Preferences -> Appearence. Click on the cursor tab. I'm not sure if there's a slider to adjust the size, or different cursors with different sizes. From there it should be pretty easy

Is that going to also change the one on the pre-login screen?

---

### Post by movrshakr on 2008-07-11
> **appi2012 said:**
> Go to System -> Preferences -> Appearence. Click on the cursor tab. I'm not sure if there's a slider to adjust the size, or different cursors with different sizes. From there it should be pretty easy

At *System -> Preferences -> Appearance *there is no cursor tab.

---

### Post by benerivo on 2008-07-11
It's System -> Preferences -> Appearence > Customise button > Pointer

---

### Post by movrshakr on 2008-07-11
> **benerivo said:**
> It's System -> Preferences -> Appearence > Customise button > Pointer

OK, that worked.  Thanks.

Now how about how to change pointer size on the login screen (sometimes called "greeting screen?)

---

### Post by benerivo on 2008-07-11
I'm not too sure about how to get a 'users' cursor perference as the default on the login screen, as it is started by the root user (?). I would try logging in as root and changing the cursor preferences in there. You may be able to change root's cursor preferences without logging in as root by doing```
gksudo /usr/bin/gnome-appearance-properties
```

---

### Post by pmlxuser on 2008-07-11
> **movrshakr said:**
> At *System -> Preferences -> Appearance *there is no cursor tab.


->Mouse

---

### Post by movrshakr on 2008-07-11
In /usr/bin/gnome-appearance-properties, there is nothing about pointers/cursors at all.

---

### Post by paul101 on 2008-07-11
there was something in compiz for your mouse size...




your on your own, as i'm nowhere near a ubuntu pc :KS

---

### Post by movrshakr on 2008-07-11
> **pmlxuser said:**
> ->Mouse

???  No tab or anything there saying Mouse either ????

But the problem after login has been solved as indicated previously.  Now we are working on how to change the pointer size on the login screen.

Oh, I have no idea what compiz is or how it applies here.

---

### Post by benerivo on 2008-07-11
> **movrshakr said:**
> In /usr/bin/gnome-appearance-properties, there is nothing about pointers/cursors at all.

When you launch /usr/bin/gnome-appearance-properties, you should get the main appearance preferences window.

'[IMG]http://davehall.com.au/images/gnome-appearance.png[/IMG]'.

From here just go to customize button pointer, as you did before.

---

### Post by movrshakr on 2008-07-11
Shoot, that was obvious.  Sorry I didn't catch it 1st time.

However, I did it--set the size to largest--but it did not affect the pointer size that shows on the login screen.

---

### Post by benerivo on 2008-07-11
I've no more suggestions for this one, sorry. Are you sure you ran this with the sudo prefix, and restarted the pc?

---

### Post by Frak on 2008-07-11
I'm going to take a shot on this one and say that, to modify your log-in cursor, you'll have to edit the X server mouse scripts.

---

### Post by movrshakr on 2008-07-11
> **benerivo said:**
> I've no more suggestions for this one, sorry. Are you sure you ran this with the sudo prefix, and restarted the pc?
I thought I had, but went and repeated it consciously with the gksudo.  It popped up an error that it cannot start gnome-settings daemon.

---

### Post by movrshakr on 2008-07-11
I rebooted and repeated the alt-f2, 
gksudo /usr/bin/gnome-appearance-settings.  It asks for pwd, then nothing happens...no window appears.

later
$%^*&^I& it is 'properties' not 'settings'

wait

---

### Post by movrshakr on 2008-07-11
OK, confirm again, it returns an error
unable to start gnome-settings-daemon.

---

