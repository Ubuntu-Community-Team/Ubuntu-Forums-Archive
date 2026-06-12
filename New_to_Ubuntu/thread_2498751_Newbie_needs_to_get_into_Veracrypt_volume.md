---
title: "Newbie needs to get into Veracrypt volume"
date: 2024-06-26
forum: New to Ubuntu
---

### Post by snudgeo on 2024-06-26
Hi everyone. Having used M$ Windows for many years, I finally switched to Ubuntu and am running v22.04.4 LTS Frankly, I am still baffled by not knowing quite how it all works. However, I urgently need some info from a veracrypt volume, created on Windows a long time ago.
I initially installed the software, but had a great deal of difficulty getting into the volume. After many tries and half an hour inputting the info, it worked! I have accessed the volume several times since, but always with great difficulty and after wasting lots of valuable time.
Today, no matter what I do it doesn't want to work. I input the passphrase + my ubuntu passphrase, all to no avail.
Would some kind soul suggest a solution please?

I should have added, the message I get is "VeraCrypt not responding"

I get the following when I try to update. Could this be anything to do with my issue?

Hit:1 [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:3 [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:5 [https://ppa.launchpadcontent.net/tualatrix/next/ubuntu](https://ppa.launchpadcontent.net/tualatrix/next/ubuntu) jammy InRelease   
Hit:6 [https://ppa.launchpadcontent.net/unit193/encryption/ubuntu](https://ppa.launchpadcontent.net/unit193/encryption/ubuntu) jammy InRelease
Err:7 [https://ppa.launchpadcontent.net/tualatrix/next/ubuntu](https://ppa.launchpadcontent.net/tualatrix/next/ubuntu) jammy Release
  404  Not Found [IP: 2620:2d:4000:1::81 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/tualatrix/next/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by currentshaft on 2024-06-26
How did you install Veracrypt? What version are you using? Have you tried running it from command-line to see if any console errors appear? The apt errors are likely not related, but you should probably remove those third party PPAs from /etc/apt/sources.list, especially if you don't know what they do.

---

### Post by snudgeo on 2024-06-26
I installed from the VeraCrypt webpage, installing the latest version 1.26.7
I laboured through a very long set of commands. In the result was a syntax error relating to the symbol ( in the password. Unexpected apparently. Could this be the problem?

---

### Post by currentshaft on 2024-06-27
> **snudgeo said:**
> I installed from the VeraCrypt webpage, installing the latest version 1.26.7
I laboured through a very long set of commands. In the result was a syntax error relating to the symbol ( in the password. Unexpected apparently. Could this be the problem?

Without knowing the set of commands you used, it is not possible to say with certainty.

---

### Post by 0f4d0335 on 2024-06-27
It appears a PPA has been removed as a public repository. [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

If you relied on a script from this repository, you may have lost access if you removed the script. You can lookup the user and contact them for the scripts you were using.

---

### Post by snudgeo on 2024-07-03
Thanks everyone. I have clearly made a mess of my first foray into Linux. Maybe I'll start again from scratch and try to make a better job it next time.

---

