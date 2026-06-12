---
title: "[HOWTO]Prelinking  - Make programs load faster!"
date: 2006-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Josh1 on 2006-10-05
Thanks to jdong for his guide [here]("http://ubuntuforums.org/showthread.php?t=1971"). This is a more basic guide, explaining how to do step by step, enjoy.
At the moment this guide is just for dapper.

**_Step 1:_ Enable Universal Reposteries**
Enter Terminal (Applications>Accessories>Terminal), and type in:
```

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

```

And scroll down and find:
```

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

```
And take out the # if it is there. Save and close gedit.
Now, reopen terminal and type in:
```
sudo apt-get update
```

**_Step 2:_ Installing Prelink**
In terminal, type in:
```

sudo aptitude install prelink

```
This will Install prelinking.

**_Step 3:_ Enabling Prelinking**
Type into terminal:
```
sudo gedit /etc/default/prelink
```
And then scroll down to the link that read:
[oode]PRELINKING=unknown[/code]
And change this to:
```
PRELINKING=yes
```
This will enable prelinking.

**_Step 4:_ Starting prelinking, and getting it to run once a day.**
NOTE: This first prelink may take a while. After this, it will take a minute or so.
Type into terminal:
```
sudo /etc/cron.daily/prelink
```

**_Step 5: [OPTIONAL]_ Getting Prelinking to run after every apt-get**:
Type into terminal:
```
sudo gedit /etc/apt/apt.conf
```
Then add in:
```
DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}
```

Thanks for reading my first howto, if you have liked it and was helpful, please reply back.

CREDITS:
Original thread, thanks to jdong for his guide[here]("http://ubuntuforums.org/showthread.php?t=1971").
Thanks to intangible's for his guide [here]("http://ubuntuforums.org/showthread.php?t=45810").
Thanks to henriquemaia for pointing out my mistake in step 6.

Changelog:
October 5th 2006: First published.

---

### Post by henriquemaia on 2006-10-05
Thanks for the Howto!

The speed gain in loading programs is that noticeable?

---

### Post by Josh1 on 2006-10-05
> **henriquemaia said:**
> Thanks for the Howto!

The speed gain in loading programs is that noticeable?

Thanks. :).
Yes, I have noticed a slight amount of increase for opening of programs when you open programs, and I have done a bit of searching and it appears to be quite beneficial. ;).
- Josh

---

### Post by henriquemaia on 2006-10-05
I have followed your howto, but there's an error on step 5.

You should type the command:

```
**sudo gedit /etc/apt/apt.conf**
```and then add:

** DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}** to the newly created/edited apt.conf file.

Apart from that, the HowTo is great. Thanks.

---

### Post by Josh1 on 2006-10-05
> **henriquemaia said:**
> I have followed your howto, but there's an error on step 5.

You should type the command:

```
**sudo gedit /etc/apt/apt.conf**
```and then add:

** DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}** to the newly created/edited apt.conf file.

Apart from that, the HowTo is great. Thanks.

Fixed, how could I have messed that up?
Cheers,
Josh

---

