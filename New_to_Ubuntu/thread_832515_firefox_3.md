---
title: "firefox 3"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by nemesis8601 on 2008-06-17
Does anyone know how to install firefox 3 so the terminal command works? I've tried installing it through Synaptic but it gives me Gran Paradiso Alpha 8 (development version). When I went to the mozilla website to download firefox 3, I ended up getting a compressed folder .tar.bz2 source code. I installed it per the instructions on the Mozilla website, removed Firefox 2, but now I can't use the terminal command "firefox &" to start the program. To use Firefox 3 I have to go to the folder where the .tar.bz2 files were extracted and run the "firefox" file. Is there a shortcut to installing that I don't know about?

Thanks!

---

### Post by rraj.be on 2008-06-17
```
sudo apt-get install firefox
```


But this too will install what version is updated in synaptic.

Its good to run this after an update

```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by RomeReactor on 2008-06-17
Hi. Take a [look here]("http://ubuntuforums.org/showthread.php?t=832407"). You don't really install the version of Firefox  downloaded from their site; you just run it from the folder. You can make a launcher for it if you wish: right-click on the top panel, select 'Add to Panel...' and 'Custom Application Launcher'. Then, assuming you have the firefox folder in your desktop, fill it out like this:

* Type: Application

* Name: Firefox 3

* Command: /home/YOUR_USERNAME_HERE/Desktop/firefox/firefox

* Comment: (leave empty if you want).

Press the 'spring' icon to select the firefox icon by navigating to the 'firefox/icons' folder.

---

### Post by nemesis8601 on 2008-06-17
Ok, I've made a shortcut for Firefox in the top toolbar and it works fine. Is there a terminal command I can use to open Firefox? Also, is there a recommended folder to store the extracted files? This is the first time I've installed something using source code so I'm pretty confused about what's actually happening.

---

### Post by RomeReactor on 2008-06-17
> **nemesis8601 said:**
> Is there a terminal command I can use to open Firefox?
The same one you entered in the 'Command' section of the launcher.

> Also, is there a recommended folder to store the extracted files? This is the first time I've installed something using source code so I'm pretty confused about what's actually happening.
You can put it anywhere you want. Just make sure it's within your home folder, preferably somewhere it won't get deleted by accident. You can hide the folder by renaming it **.firefox** (notice the dot at the beginning of the name); you would then need to modify the launcher you've just made to reflect the name change of the folder. If the command was:
```
/home/YOUR_USERNAME_HERE/Desktop/firefox/firefox
```
you would need to change it to:
```
/home/YOUR_USERNAME_HERE/Desktop/**.firefox**/firefox
```

---

### Post by nemesis8601 on 2008-06-17
The command section of the launcher is pretty long. Is there a shortcut I can use?

---

### Post by Happy_Man on 2008-06-17
...nope, not really. That's a filepath, so you'd kind of have to create a softlink, stick that somewhere, and then use that, which is too much work to be justified, IMO.

---

### Post by aysiu on 2008-06-17
Maybe this will help:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by nemesis8601 on 2008-06-17
Happy_Man, is there no 'firefox &' command for v. 3 because it's not released yet in Synaptic? When I installed v. 2, the terminal command was included.

---

### Post by ibuclaw on 2008-06-17
Not true, it's been in hardy-proposed for about 5 hours now, just enable the repository, install **only** firefox, then disable it again.

Regards
Iain

---

### Post by nemesis8601 on 2008-06-17
tinivole, I haven't upgraded from Gutsy to Hardy; would the hardy-proposed repository work?

---

### Post by Happy_Man on 2008-06-17
No, it wouldn't. Gutsy may not actually be getting Firefox 3 though the repos, so that method wouldn't work. Honestly, RomeReactor's method is easiest, though if you want to do something about this, create a softlink (shortcut) to the "firefox" file in the tarball extract you downloaded from the Firefox website, rename it to "firefox", and then stick in /usr/bin. This may or may not work, but hey, so long as you backup the actual /usr/bin/firefox before trying, but if you're so bent on having it like that...

---

### Post by ibuclaw on 2008-06-17
Not without trying to upgrade your whole system, no.

But I have made a small implementation on how to achieve it using pinning [here.]("http://ubuntuforums.org/showthread.php?t=831915")

It should work just fine, but I have not gotten round to testing it myself yet.
So it's probably best not to try it if you don't know what your doing. (As a measure, if you don't understand it, don't run it).

Regards
Iain

---

### Post by nemesis8601 on 2008-06-19
To me it seems the best fix would be to install hardy (which may resolve other unrelated problems I've been having), and see how it goes, since Gutsy won't be supported forever. Thanks for the tips guys!

---

### Post by aysiu on 2008-06-19
> **nemesis8601 said:**
> To me it seems the best fix would be to install hardy (which may resolve other unrelated problems I've been having), and see how it goes, since Gutsy won't be supported forever. Thanks for the tips guys!
That's one way to do it. I think what I linked to in post #8 is a lot easier and quicker.

---

