---
title: "is 8.04 beta? nothing works the same--frustrated!!!!"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by nightrider.36 on 2008-06-07
Packages don't install right

tried to install KINO and got this message:
[FONT="Courier New"][FONT="Comic Sans MS"]dpkg:failed to open package into file '/var/lib/dpkg/available' for reading: No such file or directory...[/FONT]

I have absolutely no clue what to do with that message nor do I have the time to figure it out. The same message was displayed for other apps I tried to install using synaptic.  I didn't see these issues in 7.04 or 7.10 (which I'm returning to until they get 8.04 fixed).

---

### Post by Victormd on 2008-06-07
The message you got simply says that it can't find a file or directory called "/var/lib/dpkg/available"

Have you installed the upgrades for 8.04?

---

### Post by Bodsda on 2008-06-07
if updates aren't the problem just create the folder see if that works

```
sudo touch /var/lib/dpkg/available
```

ty to Maestro for pointing out its a file not folder

---

### Post by Maestro23 on 2008-06-07
On my system, /var/lib/dpkg/**available** is a file.

---

### Post by rraj.be on 2008-06-07
Try this

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rraj.be on 2008-06-07
Try this.It should surelly help you 


```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by iaculallad on 2008-06-07
Try this:

```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

Then do you apt-get steps again:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nightrider.36 on 2008-06-07
> **Victormd said:**
> The message you got simply says that it can't find a file or directory called "/var/lib/dpkg/available"

Have you installed the upgrades for 8.04?

yes. There are only three updates that the UPDATE MANAGER is asking for and those are for EVOLUTION, which I don't use. And it's a good thing because when I click on INSTALL UPDATES, I get a progress bar that says "reading package information" and then it disappears--basically, nothing happens.

---

### Post by rraj.be on 2008-06-07
Try that with the terminal .

Type the commands give above in a terminal thus it will show  you the error exactly

---

### Post by Victormd on 2008-06-07
> **nightrider.36 said:**
> yes. There are only three updates that the UPDATE MANAGER is asking for and those are for EVOLUTION, which I don't use. And it's a good thing because when I click on INSTALL UPDATES, I get a progress bar that says "reading package information" and then it disappears--basically, nothing happens.

Do you have the extra software sources selected? If not, they're under SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and select all 4...
Then, open the terminal and type:
```
sudo apt-get update
```
```
sudp apt-get upgrade
```
If you haven't updated yet, this should give you quite an update list... Also, there have been recent kernel updates that you can access through the update manager...

---

### Post by iaculallad on 2008-06-07
> **nightrider.36 said:**
> Packages don't install right

tried to install KINO and got this message:
[FONT="Courier New"][FONT="Comic Sans MS"]dpkg:failed to open package into file '/var/lib/dpkg/available' for reading: No such file or directory...[/FONT]



What about trying to fix your KINO problem first: Then maybe this could help fix your other three updates error:


```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

Then redo your update and upgrade.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nightrider.36 on 2008-06-07
> **Bodsda said:**
> if updates aren't the problem just create the folder see if that works

```
sudo touch /var/lib/dpkg/available
```

ty to Maestro for pointing out its a file not folder

Thank you, this worked like a champ. I just read about "TOUCH" on Wikipedia, what a powerful command.  There's so much to UNIX that I don't know--part of my frustration. Thanks again.

---

