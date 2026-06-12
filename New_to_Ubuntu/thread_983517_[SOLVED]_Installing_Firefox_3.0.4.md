---
title: "[SOLVED] Installing Firefox 3.0.4"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Jeenyus on 2008-11-15
I am trying to upgrade to the newest version of Firefox which I downloaded from the Mozilla website.  I downloaded the firefox-3.0.4.tar.bz2 file, moved it to /usr/local/src, extracted it with tar xvf firefox-3.0.4.tar.bz2, however when i ran the "./configure" command I get and error saying "no such file or directory"

Anyone have any idea what is going on?

Thank you!

---

### Post by shifty_powers on 2008-11-15
erm, the latest firefox is 3.0.4 is it not?

certainly is on my machine. what version of ubuntu are you using?

hacve you checked in your current firefox?

---

### Post by Jeenyus on 2008-11-15
I am on 8.04 and I have Firefox 3.0.2

---

### Post by shifty_powers on 2008-11-15
ah, ok.

well it updates to 3.0.4 in 8.10.

if you wait a week or two i belive it will be in the repositories for hardy.

---

### Post by taurus on 2008-11-15
You don't build firefox.  You download it, unpack it, and then run it.  Therefore, you might want to move your firefox-3.0.4.tar.bz2 to /opt

```
sudo mv firefox-3.0.4.tar.bz2 /opt
cd /opt
sudo tar xvjf firefox-3.0.4.tar.bz2
cd firefox
./firefox
```

---

### Post by Jeenyus on 2008-11-15
> **taurus said:**
> You don't build firefox.  You download it, unpack it, and then run it.  Therefore, you might want to move your firefox-3.0.4.tar.bz2 to /opt

```
sudo mv firefox-3.0.4.tar.bz2 /opt
cd /opt
sudo tar xvjf firefox-3.0.4.tar.bz2
cd firefox
./firefox
```

Thank you, worked like a charm!

---

### Post by taurus on 2008-11-15
You can create a launcher to launch the new version of firefox, 3.0.4, in the upper panel if you wish.  Then, you don't have to run it from a terminal everytime you want to use it.  Just one click and off it goes...

---

### Post by ciscosurfer on 2008-11-15
> **shifty_powers said:**
> erm, the latest firefox is 3.0.4 is it not?

certainly is on my machine. what version of ubuntu are you using?

hacve you checked in your current firefox?[COLOR=Navy]The latest FF release on [mozilla.com]("http://www.mozilla.com/en-US/"), as of today, Nov. 15, 2008, is v3.0.4 for Linux.
[/COLOR] 
> **shifty_powers said:**
> ah, ok.

well it updates to 3.0.4 in 8.10.

if you wait a week or two i belive it will be in the repositories for hardy.[COLOR=Navy]The latest release in the repos for Intrepid (as of today, Nov. 15, 2008, as far as I can tell, is v3.0.3 (which is the version I'm running on Intrepid).  You can confirm this also by going to [packages.ubuntu.com]("http://packages.ubuntu.com").

I'm sure the repos will update very soon though. The v3.0.4 tarball was released on Nov. 12, 2008.

But yes, you can download any version you'd like right now and follow [taurus]("http://ubuntuforums.org/member.php?u=43398")' directions. 
[/COLOR]

---

### Post by oldsoundguy on 2008-11-15
Don't know if this works for you, but I have used the method:

(after installing the ubuntuzilla version at sourceforge.net)
(there is also a thread here in the forums on it.)

gksudo firefox & in CLI (terminal)

Firefox will open but under the help column the "update" will no longer be grayed out.  Hit the update, and update and re-boot.  Then shut down and next time you re-open you will have the updated version.

Do the same for Thunderbird. (gksudo thunderbird &)

(or any other Mozilla product you wish to use!)

as to launch .. using Gnome ... drag and drop the icons to the panel, either top or bottom. (I like that better than placing them on the desktop.)

---

### Post by VladNistor on 2008-11-17
Firefox 3.04 is in the repository. Run the update manager to get it.

---

