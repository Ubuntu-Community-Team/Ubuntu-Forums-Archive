---
title: "Can't find packages in Software Center"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by JHawk56 on 2012-12-23
I have trouble finding packages in Ubuntu Software Center even after adding the right repositories.

When I installed Skype, (can't remember if I was using Ubuntu 12.10 or 12.04 at the time) I added the Canonical partners repository, but still could not find Skype in Software Center. I ended up installing it from the terminal.

I am now running 11.10 on one PC, and I added the Opera browser deb repository. I still couldn't find Opera via Software Center, so I installed it via Synaptic.

When looking for packages in Software Center, I've tried using search as well as browsing the package categories. Am I doing something wrong? Is there some step I should take after adding a repository?

The only times I have ben able to install packages via Software Center is when they were present in the default repositories. Well, with one exception. When I installed Skype with 11.10, I found it via Software Center's search, even though the repository was not present. I was given the option of adding the repository with a single click, then install it with another. Very nice feature!

---

### Post by Frogs Hair on 2012-12-23
When adding new sources update the repository either by reloading synaptic or running the following with synaptic closed. ```
sudo apt-get update
```

As for Opera, the source will be added after installing the .deb from their website. Download the .deb double click and open with the software center. Once installed it will update automatically. 

[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by NikTh on 2012-12-23
Hi , 
except what  [Frogs Hair]("http://ubuntuforums.org/member.php?u=1024576") said ( which is absolutely right) , you can also try this command 

```
sudo update-software-center
``` to update the software center database. Above command usually is not needed , 
only the ```
sudo apt-get update
``` is definitely needed , but some times maybe the database wants an update for several reasons. 

Thank you.

---

### Post by JHawk56 on 2012-12-23
Thanks to both of you for the helpful tips!

> **Frogs Hair said:**
> When adding new sources update the repository either by reloading synaptic or running the following with synaptic closed. ```
sudo apt-get update
```That explains how I got it through Synaptic; I did a relaod in Synaptic.

As for Opera, the source will be added after installing the .deb from their website. Download the .deb double click and open with the software center. Once installed it will update automatically. 

[http://www.opera.com/download/](http://www.opera.com/download/)Cool. What I did was add the repository "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free" to Software Center Other Sources using the "Add" button, then installed via the terminal. I found this helpful:
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by andrew.46 on 2012-12-25
If you are interested in escaping the froth and bubble of a gui search you could try something like the following:

```

andrew@corinth:~$ **[COLOR="Red"]apt-cache search[/COLOR]** smplayer
smplayer - complete front-end for MPlayer and MPlayer2
smplayer-translations - complete front-end for MPlayer and MPlayer2 - translation files
smplayer-themes - complete front-end for MPlayer - icon themes

```

Just a different way of accomplishing the same end.

---

### Post by JHawk56 on 2012-12-25
@ andrew.46: Thanks!

---

