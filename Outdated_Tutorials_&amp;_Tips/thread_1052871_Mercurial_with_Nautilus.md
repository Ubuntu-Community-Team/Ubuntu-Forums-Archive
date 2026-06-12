---
title: "Mercurial with Nautilus"
date: 2009-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by binarymutant on 2009-01-28
I keep a Mercurial repository on my server so that I can easily keep track of changes to my files and have them readily accessible for any computer. Many of my favorite applications also use Mercurial as a distribution method and for managing source code. Even though my heart belongs to the command-line, my new tablet laptop demands more from the graphical interface. So here is a quick tip to get started working with Mercurial graphically.

[IMG]http://img144.imageshack.us/img144/7714/screenshotqn0.png[/IMG]
The Nautilus extension is not included in the Ubuntu repositories but there is a Personal Package Archive (PPA) available that does have it [1].
In order to access the PPA start the Synaptic Package Manager from the System->Administration menu on the panel. From inside Synaptic select Settings->Repositories on the menu bar. In the new window change to the Third-Party Software tab and click the add button. Finally, copy/paste this into the newest window 
```
deb [http://ppa.launchpad.net/gpoo/ubuntu](http://ppa.launchpad.net/gpoo/ubuntu) hardy main
```
The deb source can be added as well
```
deb-src [http://ppa.launchpad.net/gpoo/ubuntu](http://ppa.launchpad.net/gpoo/ubuntu) hardy main
```
Once the PPA is added just reload Synaptic and install 
```
nautilus-mercurial-tortoisehg mercurial-tortoisehg mercurial mercurial-common
```
Restart Nautilus using this command from the terminal
```
nautilus -q
```
Now the right click menu has a new menu called Mercurial. **No more typing**
> hg clone [http://code.suckless.org/hg/dwm](http://code.suckless.org/hg/dwm) :) 

In order to clone a remote repository just right click in the desired folder and select Mercurial->Create Clone from the menu. The mercurial-tortoisehg window has many advance options but to clone a remote repository simply add the remote's url to the Source Path input box and click the clone button.

[IMG]http://img292.imageshack.us/img292/2895/screenshothgclonehomecabh1.png[/IMG]

Now it is easy to create, synchronize, merge, and commit files to Mercurial repositories. All from a right click menu :)

---

### Post by ramonhimera on 2009-03-02
I followed thr steps u gave but i dont get any of the packages showing up in the package manager after adding the repositories and refreshing the list.

Btw, I actually already installed mercurial/tortoisehg using the instructions at [http://bitbucket.org/tortoisehg/stable/wiki/nautilus](http://bitbucket.org/tortoisehg/stable/wiki/nautilus) but i dont seem to get any mercurial/tortoise options in nautilus.

Which is how i ended up on this thread.

Any help greatly appreciated.
:(

---

### Post by ramonhimera on 2009-03-02
No worries - i realized that i am running Ubuntu Intrepid and when i installed using apt-get it got a lower version of Mercurial (1.0.1 or summat) instead of 1.1.2. I downloaded and installed version 1.1.2 fpr i386 and then followed the instructions at the link: [http://bitbucket.org/tortoisehg/stable/wiki/nautilus](http://bitbucket.org/tortoisehg/stable/wiki/nautilus)  and i now have Mercurial options in Nautilus.

Phew!

Hope this helps someone.

---

### Post by ahold on 2009-05-11
Welcome !

Is there available repository for Ubuntu Jaunty ?
I'm thinking about this integration, with nautilus.


Regards

---

### Post by binarymutant on 2009-05-11
The PPA above works with Jaunty as well. :)

---

### Post by yquemener on 2009-07-28
Is there a way to suggest this package inclusion in the official ubuntu repositories ? They already offer several GUI for mercurial but none of them is really usable...

---

### Post by binbash on 2009-07-28
Works great on Karmic

---

### Post by cipi.ro on 2009-11-03
Works on Karmic as well but only with the debian packages for Intrepid (not Hardy)

---

### Post by ardinotow on 2010-04-02
Please help me, 
After followed the instruction here I got TortoiseHg menu when I right clicking any folder. But, the problem is if I click one menu under TortoiseHg menu there is nothing happen (no GUI showed at all). What should I do?

---

### Post by Steven_B on 2010-07-23
> **ardinotow said:**
> Please help me, 
After followed the instruction here I got TortoiseHg menu when I right clicking any folder. But, the problem is if I click one menu under TortoiseHg menu there is nothing happen (no GUI showed at all). What should I do?

I had the same problem, which is a result of using the intrepid package with a lucid version of nautilus and/or mercurial.  This tutorial is now out of date - TortoiseHg is now included in the Universe repositories:

```
sudo apt-get install tortoisehg-nautilus
```

---

