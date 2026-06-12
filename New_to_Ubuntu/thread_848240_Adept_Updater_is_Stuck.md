---
title: "Adept Updater is Stuck"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by prann on 2008-07-03
Using Kubuntu with KDE 4 the Adept Updater keeps getting stuck at "preparing upgrade of sun-java6-bin" and never gets past that. It just hangs. Any thoughts?

---

### Post by Xzallion on 2008-07-03
It may be a bug with Adept, try to update in the terminal with ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```Let us know if that works.

---

### Post by piousp on 2008-07-03
Try changing the server from which you get your updates. Thats done via Adept (K Menu - System )

---

### Post by swisscow on 2008-07-03
Seem to remember that you have to accept a licence agreement with Java. Could be you need to click something. Can you (can't remember) open a details screen and see if a licence agreement is waiting?

---

### Post by prann on 2008-07-03
> **Xzallion said:**
> It may be a bug with Adept, try to update in the terminal with ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```Let us know if that works.

after get update I get:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by prann on 2008-07-03
> **swisscow said:**
> Seem to remember that you have to accept a licence agreement with Java. Could be you need to click something. Can you (can't remember) open a details screen and see if a licence agreement is waiting?

I remember seeing that, but even at full screen I can't down to hit Accept or Ok or whatever is down there.

---

### Post by PhailQuail on 2008-07-03
I've encountered this error on Ubuntu using Synaptic a few months ago, sadly I can't remember how I fixed it, but I assume I did, as I don't have that error anymore.

---

### Post by swisscow on 2008-07-03
> **prann said:**
> I remember seeing that, but even at full screen I can't down to hit Accept or Ok or whatever is down there.

Try using sudo apt-get package name, I think that makes it easier

---

### Post by Xzallion on 2008-07-03
> **prann said:**
> after get update I get:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

then run that code, then run update and upgrade.  That errors just saying that it was interrupted (when it hung) and that code lets it check to make sure nothings broken.

> **prann said:**
> I remember seeing that, but even at full screen I can't down to hit Accept or Ok or whatever is down there.

Try the "page up" and "page down" keys, I think they scroll it so that you can click the buttons.

---

### Post by prann on 2008-07-03
> **Xzallion said:**
> then run that code, then run update and upgrade.  That errors just saying that it was interrupted (when it hung) and that code lets it check to make sure nothings broken.

Geez, I am hitting a brick wall with every turn. Tried: dpkg --configure -a
and get "dpkg: requested operation requires superuser privilege"

> **Xzallion said:**
> Try the "page up" and "page down" keys, I think they scroll it so that you can click the buttons.

And the other way, after I hit Show Details, I see <OK> at the bottom of the license agreement but there is no way to TAB to it or arrow over to it, pressing enter nothing happens.

I think I am about to start over and reinstall.

---

### Post by ajgreeny on 2008-07-03
It has to be ```
sudo dpkg --configure -a
```which then runs as root.  Give that a try and I think all will be well, and you should then be able to run ```
sudo apt-get upgrade
```

---

### Post by Xzallion on 2008-07-03
And the other way, after I hit Show Details, I see <OK> at the bottom of the license agreement but there is no way to TAB to it or arrow over to it, pressing enter nothing happens.

I think I am about to start over and reinstall.[/QUOTE]

If it isn't the page up and down buttons, it might have been the arrow keys.  Its been awhile since I've had to install Java.

---

### Post by prann on 2008-07-03
Thanks for all the help, but I gave up and reinstalled Kubuntu and everything works fine now.

---

### Post by Xerolooper on 2008-11-07
I had the same problem and ran the commands listed earlier in this thread rebooted once and ran them again. The second time I got a similar looking liscence box and was able to page down/arrow down to bottom tab over once to Ok and hit enter. This took me to a second box that I had to tab over to Yes and then hit enter again. All updates complete thank you for posting this was a fustrating error. below is a recap.
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
I kept getting errors so I rebooted
sudo apt-get update
This gave me an error so I ran:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
[Tab] [Enter]
[Tab] [Enter]
Then it finished.

---

