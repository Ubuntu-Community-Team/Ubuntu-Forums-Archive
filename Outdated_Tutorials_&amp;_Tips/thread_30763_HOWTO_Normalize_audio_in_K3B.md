---
title: "HOWTO: Normalize audio in K3B"
date: 2005-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by jaegen on 2005-04-30
After being frustrated by waiting for K3B to decode all my files, and only then telling me it can't find normalize ](*,) , I figured out how to get it to work (quite simple actually).  

For some reason Ubuntu's repositories contain a "normalize-audio" package instead of just "normalize", and the binary is even called "normalize-audio" (even though "man normalize-audio" returns a description of the "normalize" command), so you have to create a symbolic link called "normalize" for K3B to find it properly:

```
sudo apt-get install normalize-audio
cd /usr/bin
sudo ln -s normalize-audio normalize
```
Then run K3B, select Settings-Configure K3b..., click "Programs" on the left, and click the "Search" button.  "/usr/bin/normalize" should show up under the "normalize" heading.  Now just make sure you turn off "On th fly" in the options for burning, and it will let you select "Normalize volume levels" on the Advanced tab.

Good Luck,

Jaegen

---

### Post by Karlos on 2005-04-30
I use audacity ... much more fun

---

### Post by Autoclamp on 2006-06-09
Should anyone be checking, this works on Dapper Drake, and works well!

Great, concise little HowTo.

---

### Post by dpm on 2006-06-27
Note that the "**[COLOR=Black]Normalize volume levels[/COLOR]**" option in the CD audio project properties can only be activated if "**On the fly**" (under the "Writing" tab) is [COLOR=Red]**deactivated**[/COLOR].

And in Dapper, you will need the **libk3b2-mp3** from the repos to create an audio CD from mp3 files.

Cheers.

---

