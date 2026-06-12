---
title: "[SOLVED] What Version of Flash Player? &amp;quot;.tar.gz&amp;quot;? &amp;quot;.rmp&amp;quot;? &amp;quot;YUM&amp;quot;?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-03
I wanted to play some videos in YouTube. Unfortunately, it reports that I do not have Flash Player. i go to the site and it tells me that I have 3 versions to choose from for Linux. Do I get ".tar.gz", ".rmp", "YUM" or should I get all? And what do these mean? What are each version for?

^_^; Sorry if I am asking too many questions. Thanks for your time.

Sincerely,
RedStarYellowSun

---

### Post by SunnyRabbiera on 2008-09-03
actually none, its better to fetch flash from the repositories, if you need a package look here:
[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

download, double click and install

---

### Post by crispy_420 on 2008-09-03
tar.gz will be for you of you can the appropriate repo for it.

The others are for fedora/redhat.

---

### Post by SunnyRabbiera on 2008-09-03
> **crispy_420 said:**
> tar.gz will be for you of you can the appropriate repo for it.

The others are for fedora/redhat.

yeh but the tar is soso for beginners, medibuntu is another good option:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by RedStarYellowSun on 2008-09-03
> **SunnyRabbiera said:**
> actually none, its better to fetch flash from the repositories, if you need a package look here:
[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

download, double click and install

Comrade, if I have Pentium Centrino, I click the "i386" instead of the "amd64", right?

Thanks for the help!

Sincerely,
RedStarYellowSun

---

### Post by solaceinsilence9 on 2008-09-03
> **RedStarYellowSun said:**
> I wanted to play some videos in YouTube. Unfortunately, it reports that I do not have Flash Player. i go to the site and it tells me that I have 3 versions to choose from for Linux. Do I get ".tar.gz", ".rmp", "YUM" or should I get all? And what do these mean? What are each version for?

^_^; Sorry if I am asking too many questions. Thanks for your time.

Sincerely,
RedStarYellowSun

if you want to so it yourself then .tar.gz, but I just went to Applications>Add/Remove searched for "flash" and installed Macromedia Flash Plugin.

OR if you like terminal:

```
sudo apt-get install flashplugin-nonfree
```

just make sure you have the multiverse repository added to your sources.list if you dont, or not sure if you do try this in terminal:

```
sudo gedit /etc/apt/sources.list
```

and add

```
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
```

hope that helps some.

---

### Post by solaceinsilence9 on 2008-09-03
> **RedStarYellowSun said:**
> Comrade, if I have Pentium Centrino, I click the "i386" instead of the "amd64", right?

Thanks for the help!

Sincerely,
RedStarYellowSun

Im not Comrade, but yes use i386... amd64 is only for the AMD processor. You have an Intel Processor.

---

### Post by jemate18 on 2008-09-03
> **RedStarYellowSun said:**
> I wanted to play some videos in YouTube. Unfortunately, it reports that I do not have Flash Player. i go to the site and it tells me that I have 3 versions to choose from for Linux. Do I get ".tar.gz", ".rmp", "YUM" or should I get all? And what do these mean? What are each version for?

^_^; Sorry if I am asking too many questions. Thanks for your time.

Sincerely,
RedStarYellowSun

Check my post on installing flash player tgz
> [http://ubuntuforums.org/showthread.php?t=905806](http://ubuntuforums.org/showthread.php?t=905806)

---

### Post by coolbrook on 2008-09-03
> **solaceinsilence9 said:**
> amd64 is only for the AMD processor. You have an Intel Processor.

It is also for those using 64-bit Intel processors.

---

### Post by Tatty on 2008-09-03
> **coolbrook said:**
> It is also for those using 64-bit Intel processors.

+1

Amd64 is a generic name for modern x64 architecture, i believe this is because AMD brought out the first true x64 chips.

---

### Post by jemate18 on 2008-09-03
> **Tatty said:**
> +1

Amd64 is a generic name for modern x64 architecture, i believe this is because AMD brought out the first true x64 chips.

I agree to that.....:)

---

### Post by RedStarYellowSun on 2008-09-04
Thanks for the help, friends! 

Sorry if I offended you, solaceinsilence9.

Take care.

Sincerely,
RedStarYellowSun

---

### Post by crispy_420 on 2008-09-04
> **SunnyRabbiera said:**
> yeh but the tar is soso for beginners, medibuntu is another good option:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I agree with that but just wanted to explain what he would need if he went that route. Sometimes in the past the repo one just didn't work for some reason.

---

