---
title: "Kopete...again"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-11
Sorry for the new post but Kopete is driving me nuts.Beside the fact that I can't open a link with mozila (I had to install konqueror) I have another problem.If someone leaves a message and I click to see it, the system restarts (not totally, only to the welcome screen) so I have to login again.Any idea why?:confused::confused::confused::(:(

---

### Post by Troll_the_Great on 2008-06-11
Nobody?Does it exist an alternative to Kopete with a nice interface and the ability to use my built-in web cam?

---

### Post by p_quarles on 2008-06-11
Please don't bump a thread within 24 hours of the initial post.

I don't know about the crashing issue, but I can fix the web browser issue. You need to open up the KDE control interface (type "kcontrol" in a terminal or run dialogue) and change the name of the default web browser in there. With few exceptions, KDE applications will now respect that choice. You can set it to Firefox, Opera, or whatever you like.

---

### Post by Troll_the_Great on 2008-06-13
Does anybody know where kopete installs?I look in my home folder and that's no hidden folder named "kopete".I want to find it so I can delete it and then make a fresh installation.If I try from synaptic, when I reinstall it, it still has all my settings, so I need another way.

---

### Post by gr4nf on 2008-06-13
try:
```

sudo apt-get remove kopete

```

---

### Post by Troll_the_Great on 2008-06-13
Nope, doesn't work.When I reinstall it it still has all my settings.

---

### Post by adobrakic on 2008-06-13
have you tried

```

sudo apt-get purge kopete

```

---

### Post by Troll_the_Great on 2008-06-13
This doesn't work either.:(:(:(

---

### Post by stchman on 2008-06-13
> **Troll_the_Great said:**
> Sorry for the new post but Kopete is driving me nuts.Beside the fact that I can't open a link with mozila (I had to install konqueror) I have another problem.If someone leaves a message and I click to see it, the system restarts (not totally, only to the welcome screen) so I have to login again.Any idea why?:confused::confused::confused::(:(

I have problems too with opening an HTML link using a KDE app in Gnome.

When you installed Konquerer(KDE app) that probably fixed it.

I have looked in kcontrol and not found a way to open Firefox for HTML links.  Has anyone found a way?

---

### Post by stchman on 2008-06-13
> **Troll_the_Great said:**
> Nobody?Does it exist an alternative to Kopete with a nice interface and the ability to use my built-in web cam?

Most KDE apps install their config file under Gnome in

~/.kde

---

### Post by wootah on 2008-06-13
You are looking for 
```
sudo apt-get remove kopete --purge
```

This removes kopete AND its settings.

---

### Post by Troll_the_Great on 2008-06-13
Not really....:(

---

### Post by RiceMonster on 2008-06-13
> **Troll_the_Great said:**
> Does anybody know where kopete installs?I look in my home folder and that's no hidden folder named "kopete".I want to find it so I can delete it and then make a fresh installation.If I try from synaptic, when I reinstall it, it still has all my settings, so I need another way.

```
whereis kopete
```

Also, its configuration should be in ~/.kde as already mentioned.

---

### Post by wootah on 2008-06-13
> **RiceMonster said:**
> ```
whereis kopete
```Also, its configuration should be in ~/.kde as already mentioned.

Also, ```
dpkg -L kopete
```

---

### Post by Troll_the_Great on 2008-06-13
```
troll@My-precious:~$ whereis kopete
kopete: /usr/bin/kopete /usr/share/man/man1/kopete.1.gz
```
I found the settings in .kde but still no use.Now when I open, several windows open, with the message:"The selected buddy icon could not be opened. 
Please set a new buddy icon."
I have to click OK sever times and then it works.

---

### Post by yell0w on 2008-10-09
> **Troll_the_Great said:**
> ```
troll@My-precious:~$ whereis kopete
kopete: /usr/bin/kopete /usr/share/man/man1/kopete.1.gz
```
I found the settings in .kde but still no use.Now when I open, several windows open, with the message:"The selected buddy icon could not be opened. 
Please set a new buddy icon."
I have to click OK sever times and then it works.

I found the same error here on my kopete (version 4:3.5.10-0ubuntu1~hardy2 ) 
The problem is your account image file is missing (or of size zero in my case). 
The fix is Settings >> Configure >> Account >> choose account >> Modify >> Account Preferences >> Select Picture for the Buddy Icon >> choose another image/icon.
That should fix it.
Cheers :) 

See [https://bugs.kde.org/show_bug.cgi?id=156885](https://bugs.kde.org/show_bug.cgi?id=156885)

---

