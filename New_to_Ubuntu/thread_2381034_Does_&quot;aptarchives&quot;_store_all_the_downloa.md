---
title: "Does &quot;apt/archives&quot; store all the downloaded packages and depends?"
date: 2017-12-25
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-25
When I install the *package* does the *package* and all its *dependencies* get downloaded to 'archive' folder? If that is the case, I plan to backup 'archive' folder. I plan to use those downloaded packages when I am installing OS without Internet. Will this strategy work? 

I did play with Synaptic tool. It does not search all repos 

Thanks

---

### Post by #&amp;thj^% on 2017-12-25
> **wrongusername2 said:**
> When I install the *package* does the *package* and all its *dependencies* get downloaded to 'archive' folder? If that is the case, I plan to backup 'archive' folder. I plan to use those downloaded packages when I am installing OS without Internet. Will this strategy work? 

I did play with Synaptic tool. It does not search all repos 

Thanks
This may help in understanding (the post by Eliah Kagan): [https://askubuntu.com/questions/531978/why-are-there-deb-files-in-var-cache-apt-archives](https://askubuntu.com/questions/531978/why-are-there-deb-files-in-var-cache-apt-archives)

BTW: Synaptic** "will"** search All added Repos && PPA's && CD Media if you point it to it. ;)
 If you have all the appropriate packages in your media that you are installing from, then the package**_ apt-offline _**should be able to install them just as well as any application your installing with it.

apt-offline would/could generate you an archive file or a folder with all the data. That data can be copied on a removable media. The removable media can be attached back to the disconnected Debian box at home and installed. (e.g. "apt-offline install /tmp/apt-offline.zip")

More Here: [https://debian-administration.org/article/648/Offline_Package_Management_for_APT](https://debian-administration.org/article/648/Offline_Package_Management_for_APT)

---

### Post by wrongusername2 on 2017-12-26
> **1fallen said:**
> 
BTW: Synaptic** "will"** search All added Repos && PPA's && CD Media if you point it to it. ;)
If you have all the appropriate packages in your media that you are installing from, then the package**_ apt-offline _**should be able to install them just as well as any application your installing with it.

apt-offline would/could generate you an archive file or a folder with all the data. That data can be copied on a removable media. The removable media can be attached back to the disconnected Debian box at home and installed. (e.g. "apt-offline install /tmp/apt-offline.zip")

More Here: [https://debian-administration.org/article/648/Offline_Package_Management_for_APT](https://debian-administration.org/article/648/Offline_Package_Management_for_APT)
Thanks for responding.

I read several articles on apt-get. I understand Synaptic will look is inside PPA but my problem is I am not yet good at identifying the PPA itself :-)
Yesterday I used this command for downloading few packages. Then I disabled my  internet and installed, and re-enabled internet and installed it again. When I ran the installer for second time, it did not do much. 

Instead of disabling internet I think could have used **apt-offline** :-)  I will use it next time.

Fyi: I used this cmd for downloading decencies (got this from one of the forum)
```
[COLOR=#000000][FONT=Arial]$ apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests --no-conflicts --no-breaks --no-replaces --no-enhances --no-pre-depends <your-package-here> | grep "^\w" | sort -u)
[/FONT][/COLOR]
```

---

### Post by #&amp;thj^% on 2017-12-26
You have taken on a challenging task for a newer user, so kudo's. :KS

Also You can get a list of the packages dependencies with:

```
find *deb -exec dpkg -f {} Depends \;
```
You will have to be in that path of your stored media in the terminal. EG:  "cd /YOURBACKEDUP>DEBS" Then run that command.

---

