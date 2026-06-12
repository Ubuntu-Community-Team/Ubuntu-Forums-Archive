---
title: "how can I change the classic desktop font size?"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdurham on 2011-09-09
thanks for any suggestions

---

### Post by howefield on 2011-09-09
Try the Universal Access application.

There are a few threads on this elsewhere in "Ubuntu +1 (Oneiric Ocelot)" you could have a look at, eg.

[http://ubuntuforums.org/showthread.php?t=1779999](http://ubuntuforums.org/showthread.php?t=1779999)

---

### Post by robert shearer on 2011-09-09
As howefield says Applications>System tools>System settings>Universal Access>seeing            which gives a system-wide text size.

however, many applications via their edit>preferences  allow text size adjustments.

Just checked my most often used apps,    Terminal, Ffox/Chromium, Gedit, Office Writer and all have text size selection.

---

### Post by mdurham on 2011-09-09
> **robert shearer said:**
> As howefield says Applications>System tools>System settings>Universal Access>seeing            which gives a system-wide text size.

however, many applications via their edit>preferences  allow text size adjustments.

Just checked my most often used apps,    Terminal, Ffox/Chromium, Gedit, Office Writer and all have text size selection.
Thanks for the replies but this isn't what I asked for. I want to change the **desktop font size**. 
Using the "system-wide text size" doesn't change the desktop font size. Apparently the desktop isn't included in "system wide". Very strange.
Cheers, Mike

---

### Post by fjgaude on 2011-09-09
Three of the font types and sizes can be changed with the **dconf-editor**. You get that editor by installing **dconf-tools**.

In that editor you go to:

**org/gnome/desktop/applications/interface**

From there you see the fonts.

Install the tools:

```
sudo apt-get install dconf-tools
```

Have fun!

---

### Post by mdurham on 2011-09-09
> **fjgaude said:**
> Three of the font types and sizes can be changed with the **dconf-editor**. You get that editor by installing **dconf-tools**.

In that editor you go to:

**org/gnome/desktop/applications/interface**

From there you see the fonts.

Install the tools:

```
sudo apt-get install dconf-tools
```

Have fun!

Thanks fjgaude but no use. The settings do not affect the desktop font size.
Cheers, Mike

---

### Post by Alwimo on 2011-09-09
sudo apt-get install gnome-tweak-tool 

I remember a text size changer in there.

---

### Post by mdurham on 2011-09-10
> **Alwimo said:**
> sudo apt-get install gnome-tweak-tool 

I remember a text size changer in there.
You are correct Alwimo, there is a a size changer in there. Unfortunately, it doesn't change the desktop font size.

---

### Post by Xgen on 2011-09-10
Perhaps dconf --> org --> gnome --> nautilus --> desktop --> font?

---

### Post by mdurham on 2011-09-10
> **Xgen said:**
> Perhaps dconf --> org --> gnome --> nautilus --> desktop --> font?

Not perhaps Xgen but definitely. My sanity is returning, thanks.

---

### Post by shuttleworthwannabe on 2011-09-10
the short answer is no you can't change font size in ubuntu vanilla---but you can if you install gnome-tweak-tool as suggested above.

---

### Post by morryis on 2011-09-10
It does not work for desktop font size, see [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/822999]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/822999")

---

### Post by robert shearer on 2011-09-10
> **mdurham said:**
> Thanks for the replies but this isn't what I asked for. I want to change the **desktop font size**. 
Using the "system-wide text size" doesn't change the desktop font size. Apparently the desktop isn't included in "system wide". Very strange.
Cheers, Mike

Ahem, what you asked for was "how can I change the **classic desktop font size**?"

However, you now amend to **desktop font size** but say that the system-wide text size does not apply to the desktop.

After you make the system-wide text size change most text will change size immediately but for the desktop you need to **log-out and log-in again** to make it take effect.....:)

---

### Post by mdurham on 2011-09-10
> **robert shearer said:**
> After you make the system-wide text size change most text will change size immediately but for the desktop you need to **log-out and log-in again** to make it take effect.....:)

That's true, **most** text will change size, but not the desktop text (classic or not).

---

### Post by mdurham on 2011-09-10
> **morryis said:**
> It does not work for desktop font size, see [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/822999]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/822999")

Thanks for that morryis, so I'm not going mad!
Cheers, Mike

---

### Post by robert shearer on 2011-09-15
> **mdurham said:**
> That's true, **most** text will change size, but not the desktop text (classic or not).

Using Classic no-effects here and assure you that I can change the desktop font size using..... Applications>System tools>System settings>Universal Access>seeing which gives a system-wide text size.

then logging out and back in again to make it take effect for the desktop text.

---

### Post by mdurham on 2011-09-15
> **robert shearer said:**
> Using Classic no-effects here and assure you that I can change the desktop font size using..... 

Thanks for that Robert but, that affects all other font sizes not just the desktop font and it's limited to 'small' 'normal' and 'large' whatever that means. In the past we have been able to set different sizes for desktop, documents, window title etc. It seems that we can't do that anymore which is a step backwards I would say.
Cheers, Mike

---

### Post by robert shearer on 2011-09-15
> **mdurham said:**
> Thanks for that Robert but, that affects all other font sizes not just the desktop font and it's limited to 'small' 'normal' and 'large' whatever that means. In the past we have been able to set different sizes for desktop, documents, window title etc. It seems that we can't do that anymore which is a step backwards I would say.
Cheers, Mike

Yeah, that affects all other **system** font sizes but individual applications **can have their fonts customized.**

I guess the rationale is that someone needing visual assistance would choose a consistent font size for everyday system-wide usage.
(why have some big, some small, and some just right, unless you're Goldilocks ??)

The current method is a one-stop shop setting and thus friendly to new users.

Customizing font size on a per application basis makes sense especially for documents, terminal etc.

Seems that the Ubuntu font is default and it would be nice to be able to change that but hey Ubuntu is setting itself up as a brand so that sort of lock-down  is to be expected.

I don't see the problem here as the default behaviour is sensible and useable for most.

Sure it is a loss of options compared to Gnome2 but inveterate tweakers must have realised long ago that Windows,Mac, and now Ubuntu are all moving to multi-platform consistency in their look and feel.

Kubuntu and XFCE still have lots of options and Gnome3/Unity are bound to add more options as they mature.:)

---

