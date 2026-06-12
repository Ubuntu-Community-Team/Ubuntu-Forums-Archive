---
title: "Configuring ttf-mscorefonts-installer problem"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-04-22
[SIZE=3]Just doing a fresh install of 12.04 Beta.

After running the following code I'm presented with a EULA and at the bottom there is <ok>

I'm unable to do anything. I've pressed, Enter, etc, but I'm stuck on the screen. If I close the terminal I'm greeted with a message that says "There is still a process running"

I have no prompt so what do I do?

[/SIZE]```
[SIZE=3]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/SIZE]
```[SIZE=3]

Thanks[/SIZE]

---

### Post by grahammechanical on 2012-04-22
This is happening because you agreed to install the restricted extras as part of the install of Ubuntu and we now get Microsoft's core fonts set which we have to accept the EULA to.

Did you try clicking the OK? Just checking. If we do not accept that EULA then the install cannot proceed. You can of course install without those restricted extras which can be installed later from the Software Centre.

At least it will get 12.04 up and running.

I have installed 12.04 several times over the last couple of weeks for testing purposes and did not notice this problem.

Regards.

---

### Post by Curtis6767 on 2012-04-22
[SIZE=3]Yes, I clicked <Ok> but that doesn't do anything.

I'm trying to run this: 


```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```[/SIZE][SIZE=3]

I think I'm getting that because those core fonts haven't completed their download.

I don't need the fonts, at least I don't think I do. When I've tried to remove them, I get an error saying they don't exist so they obviously can't be removed.

I found this link but have no idea if this pertains to my issue plus it's several years old. [http://ubuntuforums.org/showpost.php?p=7902019&postcount=33](http://ubuntuforums.org/showpost.php?p=7902019&postcount=33)

Thanks

Adding this: I've tried to run apt-get update but got the following message.






[/SIZE][SIZE=3]
[/SIZE]

---

### Post by Krytarik on 2012-04-22
To fix the "ttf-mscorefonts-installer" issue, please see this guide:

[http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html](http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html)

Thereafter, to fix the issue with the missing GPG key, just run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```Regards.

---

### Post by Curtis6767 on 2012-04-22
> **Krytarik said:**
> To fix the "ttf-mscorefonts-installer" issue, please see this guide:

[http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html](http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html)

Thereafter, to fix the issue with the missing GPG key, just run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```Regards.

Thanks for posting that code. Saves me the trouble.

I went around the world several times trying to find the fix and entering all kinds of commands that did not work until I stumbled on a Ubuntu Forums post from November 2010 that had the same fix as you supplied.

Something I did borked the Update Manager but after running that keyserver code, I guess, the Update Manager started working. One of the updates was the TTF fonts along with a regular user agreement with a convenient check box so no more issues with that, I hope.

Thanks for your help. Marking this thread solved.

---

### Post by schulwitz on 2012-11-25
The solution posted above is totally unnecessary.

Just hit the <TAB> key and then hit <ENTER>.

---

### Post by johniexi on 2012-11-28
> **schulwitz said:**
> The solution posted above is totally unnecessary.

Just hit the <TAB> key and then hit <ENTER>.

thanx, this really works for me.

---

### Post by stofferx on 2013-01-10
Thanks a lot for this simple solution

---

### Post by Makiani on 2013-01-13
Thanks!  I would never have guessed it would have such a simple solution!  So glad I read far enough to see the easy option...  Have only been using Ubuntu for a few days and enjoying playing with the terminal...

---

### Post by southpaw118 on 2013-05-20
oh yea!!! saved me loads of time.

---

### Post by eatabean on 2014-05-12
> **schulwitz said:**
> The solution posted above is totally unnecessary.

Just hit the <TAB> key and then hit <ENTER>.


Laughing my tiddies off at this! All these proposed solutions... hahahaha :P Nice to meet a real expert .. Thanks!

---

### Post by oldos2er on 2014-05-12
Old thread closed.

---

