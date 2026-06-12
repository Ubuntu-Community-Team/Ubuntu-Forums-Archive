---
title: "Login in KDE session messes up gtk settings."
date: 2014-08-09
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2014-08-09
Hello all!

I needed to run a test in my user using kde, so I switched to kde. However, when I switched back, the theme looks kde-style I have to go to KDE System Settings to change the icon theme to ubuntu-mono-light, the kde theme to gtk, the gtk tab of kde appearance to Radiance, the cursor to DMZ-White, etc. Yet all the menus are compact, like in kde. Why does kde do this to me? Can I revert back without uninstalling kde, reinstalling ubuntu, or a similar method.

I thank you all in advance.

-Jonathan

---

### Post by vasa1 on 2014-08-14
> **Jonathan Precise said:**
> Hello all!

I needed to run a test in my user using kde, so I switched to kde. However, when I switched back, the theme looks kde-style I have to go to KDE System Settings to change the icon theme to ubuntu-mono-light, the kde theme to gtk, the gtk tab of kde appearance to Radiance, the cursor to DMZ-White, etc. Yet all the menus are compact, like in kde. Why does kde do this to me? Can I revert back without uninstalling kde, reinstalling ubuntu, or a similar method.

I thank you all in advance.

-JonathanHow did you "switch" to kde? What did you start with? Anyway, I've come across issues similar to yours and got the impression that Kubuntu settings are "sticky".

---

### Post by Jonathan Precise on 2014-08-14
I started with the vanilla Ubuntu (Unity DE), and installed kubuntu-desktop as one of my users needed KDE. I needed to run a test under my user using kde, so on my login screen, where it had the Ubuntu icon, I clicked it, and selected KDE. Logged in, ran the test, logged back out, clicked the K icon, selected Ubuntu, logged in, and the settings in kubuntu stuck.

Why are those settings "Sticky"? Is there a way to fix it?

---

### Post by Jonathan Precise on 2014-08-14
Update: I have filed a bug report for it. (See #[lpbug]1226847[/lpbug])

---

### Post by vasa1 on 2014-08-14
> **Jonathan Precise said:**
> Update: I have filed a bug report for it. (See #[lpbug]1226847[/lpbug])
I suspect you'll get a bit-of-stick for using 13.04 which is [EOL]("lists.ubuntu.com/archives/ubuntu-announce/2014-January/000178.html").

As for why Kubuntu settings are "sticky", I don't know. My uneducated guess is that some file is modified as a consequence of installation and that that modified file isn't restored to the original when one switches desktops. Which is why I prefer to not mix DE's and caution people who ask about such ventures.

I guess someone with a virtual system at their disposal could nail this issue.

---

### Post by Jonathan Precise on 2014-08-16
Sorry. I am running trusty. Forgot to mention in bug report.

---

### Post by vasa1 on 2014-08-16
> **Jonathan Precise said:**
> Sorry. I am running trusty. Forgot to mention in bug report.
Then you could amend this:```


---------------
1) Description: Ubuntu 13.04
Release: 13.04
---------------
```

---

### Post by Jonathan Precise on 2014-08-16
The bug was originally reported in ubuntu 13.04, but now I have upgraded and it persists. How does one edit the description?

---

### Post by Jonathan Precise on 2014-08-16
Update: I found out how. Description updated.

---

### Post by JKyleOKC on 2014-08-17
Back to your question about what makes KDE sticky...

While I don't use KDE, and consequently this is just a wild guess, in my own system there are some hidden files in my home directory that include "session" lists, which control parts of the login sequence depending on which of three or four listed sessions is at the top of the list. There's also another hidden file that includes a setting for "save current session automatically" when logging out.

I'd look for something similar in the several dozen hidden files that live in $HOME; you can list them with "ls -la" (the "l" argument gives a detailed listing and the "a" shows hidden files in addition to the normal ones). You can examine each using your favorite text editor (I like leafpad but gedit or kate will also work) to try to find the one that's making KDE themes sticky.

Hope this helps!

---

### Post by Jonathan Precise on 2014-08-17
Thanks JKyleOKC! Shall get to it when I can.

---

