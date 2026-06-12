---
title: "&quot;laptop battery critically low&quot; not true"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by shevin on 2011-10-20
I have upgraded to 11.10 , recently when I unplug my charger , even though it shows it is 100% charged, it says "laptop battery critically low , it will supsend blah blah"

and it wont suspend if I hit cancel .and battery is fine but ubuntu think it the battery is low .

I have toshiba sattelite laptop

---

### Post by Peter09 on 2011-10-22
I have had this problem on my HP machine, wonders if it was my battery, but looks like its a bug.

---

### Post by Gadgetech on 2011-10-25
This sounds like an issue that came up previously on my MSI Wind. I haven't installed 11.10 on it yet, so I don't know if it's the same issue. Here's the thread:
[http://ubuntuforums.org/showthread.php?p=9230036]("http://ubuntuforums.org/showthread.php?p=9230036")

For 11.10, you'll need to use dconf-editor instead of gconf-editor. If you don't already have dconf-editor installed, you can install it with
```
sudo apt-get install dconf-tools
```

---

### Post by shevin on 2011-11-04
bump , help plz

---

### Post by shevin on 2011-11-05
> **Gadgetech said:**
> This sounds like an issue that came up previously on my MSI Wind. I haven't installed 11.10 on it yet, so I don't know if it's the same issue. Here's the thread:
[http://ubuntuforums.org/showthread.php?p=9230036]("http://ubuntuforums.org/showthread.php?p=9230036")

For 11.10, you'll need to use dconf-editor instead of gconf-editor. If you don't already have dconf-editor installed, you can install it with
```
sudo apt-get install dconf-tools
```

there are not the same things inside dconf and gconf editors , so when I run dconf I dnot see the field that was mentioned in that post

---

### Post by crjackson on 2011-11-05
I too have this problem and no answers...

---

### Post by Script Warlock on 2011-11-06
same here. i took the battery out and plug my laptop to ac.

---

### Post by shevin on 2011-11-07
someone help us

---

### Post by crjackson on 2011-11-08
bump

---

### Post by tgyorgyi on 2011-11-17
Hi, the same option is there in dconf-editor as well, only different place:

Here is a [suggestion from Launchpad]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190") (comment #94):

> 1. sudo apt-get install dconf-tools
2. dconf-editor
3. Navigate to the 'org.gnome.settings-daemon.plugins.power' section
4. Uncheck 'use-time-for-policy'

I still get a popup when unplugging the power but I just hit Cancel and everything works fine. Before I did this, it would hibernate/turn off/whatever no matter what I did.

It makes sense to read the comments before and especially after, it works for some, not for others. It seems that if you had this problem before 11.10, this will work again, but if the problem popped up with the upgrade to 11.10 and did not exist before, then you might have a different issue for which this fix is not working.

EDIT: I was looking for a workaround for a friend. Meanwhile she tried this on her MSI notebook. It works fine, she is not even getting a false message like the poster on Lauchpad. Works exactly like when we fixed in under Natty with the help of gconf-editor.

---

