---
title: "Make Firefox the Default Browser!"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by eXCeSS on 2006-06-21
After seriously looking for a long time I figured I'd post this here so I could help other newbies (I've only completely switched since a few days ago!) get Konqueror from opening all my Gaim and Konversation links!


Open terminal > Put in:
```
sudo update-alternatives --config x-www-browser
```

Then type in the number next to Firefox. For me it was 2.
That's it! :D

---

### Post by AngryKidJoe on 2006-06-22
Thanks. Was looking up how to do that.

---

### Post by -Chi.0 on 2006-06-27
Thanks, This is something that every one should check out :KS

---

### Post by aysiu on 2006-06-27
Seems odd to have to invoke *sudo* in order to change a default application.

Shouldn't application defaults be user-specific?

---

### Post by onlysolution on 2006-06-27
Or you could just (in Gnome) go to System->Preferences->Prefered Applications to set your default browser, mail, and terminal program on a per-user basis.

---

### Post by Bosonator on 2006-06-27
Thanks. I don't know why that's so difficult. I tried to do it within the KDE system settings, but it didn't stick. Oh well... problem solved!

---

### Post by jonifen on 2006-06-28
Excellent, I've been looking to do that myself too...

Now I've gotta find out how to make Thunderbird my default mail application!! Selecting "email file" through the right click menu on a file just opens it up in KMail :(

---

### Post by Downtown on 2006-07-02
Thanks a lot.  This was really bothering me that it kept opening Konqueror when I didn't want it to.

---

### Post by mandragor on 2006-07-04
Thanks for this one!

Isn't the fact that this is needed really a bug?

---

### Post by Robert Leithe on 2006-08-17
> **onlysolution said:**
> Or you could just (in Gnome) go to System->Preferences->Prefered Applications to set your default browser, mail, and terminal program on a per-user basis.

Hi, I've been trying to set Opera as my default browser, and been following your description as stated above. However, when I click a link in an e-mail (KMail), Konqueror opens. What gives?

Sincerely
Robert Leithe

---

### Post by AlanB66 on 2009-03-02
> **Robert Leithe said:**
> Hi, I've been trying to set Opera as my default browser, and been following your description as stated above. However, when I click a link in an e-mail (KMail), Konqueror opens. What gives?

Sincerely
Robert Leithe

Robert,

In a terminal (shell), navigate to $HOME/.local/share/applications.
Then, run: gedit opera.desktop
Look for the Exec= line and it probably has:
  Exec=konqueror %u
Change this to:
  Exec=opera %u

Save and close this file and you should be golden.

---

### Post by Vesukka on 2011-07-23
Allright, tried all of these, but:

On Preferred Applications I have **firefox** and **Chromium Web Browser** (with these names). Firefox appears as default, that can be seen also when I run 'sudo update-alternatives --config x-www-browser', but firefox has no icon on it while Chromium has.

Firefox has also disappeared from 'Browse the Web' (icon on Unity when you click the Ubuntu logo) and got replaced by Chromium.

When I do an application search on unity, I get two Firefoxes. In my .local/share/applications/ are shortcuts 'Firefox' and 'Firefox Web Browser' which doesn't appear when I do a search in Unity.

Seems like I've managed to crap up my icons or my icons settings somehow.

---

### Post by Vesukka on 2011-07-23
Hmm... It seems like deleting shortcuts from .local/share/applications/ and letting Ubuntu recreate them fixed the problem.

Now I got my 'Firefox Web Browser' back working. It appeared in Preferred Applications and as Unity's Browse the Web shortcut.

---

