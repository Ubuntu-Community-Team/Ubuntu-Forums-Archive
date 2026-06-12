---
title: "apt-get update is still large"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by vasa1 on 2012-04-27
Anyone else on **12.04** notice that [FONT="Courier New"]sudo apt-get update[/FONT] results in about **12.6 MB** being "fetched"? I thought these large updates were due to the transition process but it's still happening:
The top three fetches from an update this morning were:```

http://archive.ubuntu.com precise/main i386 Packages	[1,274 kB]                                                             
http://archive.ubuntu.com precise/universe i386 Packages	[4,796 kB]                                                         
http://archive.ubuntu.com precise/universe Sources	[5,019 kB]                                                    
```

---

### Post by plucky on 2012-04-27
> **vasa1 said:**
> Anyone else on **12.04** notice that [FONT="Courier New"]sudo apt-get update[/FONT] results in about **12.6 MB** being "fetched"? I thought these large updates were due to the transition process but it's still happening:
The top three fetches from an update this morning were:```

http://archive.ubuntu.com precise/main i386 Packages	[1,274 kB]                                                             
http://archive.ubuntu.com precise/universe i386 Packages	[4,796 kB]                                                         
http://archive.ubuntu.com precise/universe Sources	[5,019 kB]                                                    
```

apt-get update downloads the index files from the repositories,the only way to reduce the amount of data is to disable the repositories that you don't need, but the problem with doing that is that the software from those repositories will not be updated.

My 12.04 index files download is 14.6Mb.

It only installs the updates when you run ```
sudo apt-get upgrade
``` and it actually downloads and installs the .deb files.Depending on the number of updates,this download is usually a lot larger than the previous one.

Good Luck

---

### Post by vasa1 on 2012-04-27
> **plucky said:**
> apt-get update downloads the index files from the repositories,the only way to reduce the amount of data is to disable the repositories that you don't need, but the problem with doing that is that the software from those repositories will not be updated.

My 12.04 index files download is 14.6Mb.

It only installs the updates when you run ```
sudo apt-get upgrade
``` and it actually downloads and installs the .deb files.Depending on the number of updates,this download is usually a lot larger than the previous one.

Good Luck
Apt-get upgrade is not the issue. It's the apt-get-update part. When on 11.10, the update files were mostly a few kB, IIRC.

---

### Post by IWantFroyo on 2012-04-27
Things are changing quickly with 12.04. It's not a surprise to me that this much data is used doing this.

By my memory, it's always like this after a big upgrade.

---

### Post by vasa1 on 2012-04-27
> **IWantFroyo said:**
> Things are changing quickly with 12.04. It's not a surprise to me that this much data is used doing this.

By my memory, it's always like this after a big upgrade.
Okay, so maybe things will settle down in a few days.

---

### Post by farrinux on 2012-04-27
> **IWantFroyo said:**
> Things are changing quickly with 12.04. It's not a surprise to me that this much data is used doing this.

By my memory, it's always like this after a big upgrade.

I'd second that I haven't upgraded but I see the same large  files in 11.10.  Took about 3 minutes compared to a normal 1 minute or less.

---

### Post by TBABill on 2012-04-27
You can probably expect some big updates for a month or two periodically as they squash bugs and stabilize the release further.

---

### Post by silversword411 on 2012-05-29
It's a bug, started April 24th and is a PITA for me. 

[http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big](http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big)

Guess it's my fault for using Ubuntu for my primarly linux distro, my bandwidth usage has spiked (50+ servers downloading 10+MB every hour adds up fast, let me assure you), hopefully it gets patched soon :/

---

### Post by Old_Grey_Wolf on 2012-05-29
> **silversword411 said:**
> 
Guess it's my fault for using Ubuntu for my primarly linux distro, my bandwidth usage has spiked (50+ servers downloading 10+MB every hour adds up fast, let me assure you), hopefully it gets patched soon :/

With that many servers, why not set up your own Local Ubuntu Repository Mirror so you only download once.

---

### Post by silversword411 on 2012-05-29
> **Old_Gray_Wolf said:**
> With that many servers, why not set up your own Local Ubuntu Repository Mirror so you only download once.

Yeah...I know that's an option, but then I need to setup and maintain another local something. If it doesn't get fixed soon I may have to go thru that tedious process for all my servers <sigh>

---

### Post by uRock on 2012-05-29
> **silversword411 said:**
> It's a bug, started April 24th and is a PITA for me. 

[http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big](http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big)

Guess it's my fault for using Ubuntu for my primarly linux distro, my bandwidth usage has spiked (50+ servers downloading 10+MB every hour adds up fast, let me assure you), hopefully it gets patched soon :/

Why are you running updates hourly? Have you created a bug report?

---

### Post by alphacrucis2 on 2012-05-29
> **uRock said:**
> Why are you running updates hourly? Have you created a bug report?

There's a launchpad bug report linked to on the askubuntu question. Running hourly updates does seem a bit excessive though.

---

### Post by Warpnow on 2012-05-29
Hourly updates goes so much further than excessive..

---

### Post by jtarin on 2012-05-29
[http://muzso.hu/2011/01/05/how-to-turn-off-automatic-updates-in-ubuntu](http://muzso.hu/2011/01/05/how-to-turn-off-automatic-updates-in-ubuntu)

[http://blog.bravi.org/?p=493](http://blog.bravi.org/?p=493)

---

### Post by uRock on 2012-05-29
I see the bug report now, thanks. If I were running servers, then I would be running updates weekly at the most frequent. I think Old_Gray_Wolf has the best idea for such a situation.

---

### Post by vasa1 on 2012-08-07
Fixed: [https://bugs.launchpad.net/launchpad/+bug/1001780](https://bugs.launchpad.net/launchpad/+bug/1001780)

---

