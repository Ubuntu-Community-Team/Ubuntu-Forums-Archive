---
title: "from windows to linux"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by killersnowgoon on 2008-07-18
up until about a month ago, i had been using windows my whole life. i did everything i could to optimize my computer; cleaned out registry, defraged almost every day, spyware and virus scans, basically i'm pretty anal about having my comp be at its full performance. now im using linux, and theres no registry, no need to defrag, no viruses. dont get me wrong, i love that, but is there anything i *should* be doing to clean/optimize?

---

### Post by Barrucadu on 2008-07-18
Not that I can think of, fsck is run every 30 boots, which fixes any fragmentation on your disks. The only thing I could think of is to clean out your home folder often if you feel the urge to clean something :lol:

---

### Post by schauerlich on 2008-07-18
Nothing off the top of my head, Linux is pretty self sufficient. :) Welcome and enjoy the ride.

On a side note, isn't defragging every day a bit much? Seems like you'd wear out your hard drive and not do much good. Once a month, maybe... But I digress.

---

### Post by hyper_ch on 2008-07-18
You could wax and polish your computer ;)

---

### Post by Canis familiaris on 2008-07-18
One thing comes to my mind:
```
sudo apt-get autoremove
```
It will remove all the uneeded dependencies.

---

### Post by Canis familiaris on 2008-07-18
> **hyper_ch said:**
> You could wax and polish your computer ;)

If you mean opening and cleaning the cabinet from dust cowebs, then:
+1

If you are joking
:lolflag:

---

### Post by hansdown on 2008-07-18
Hi killersnowgoon. Welcome to a new and beautiful world. Ubuntu rocks, and if you need help, just cruise these forums for seriously helpfull tips or post a question and the good people here will help. Welcome again.

---

### Post by t0p on 2008-07-18
> **hyper_ch said:**
> You could wax and polish your computer ;)

My former gf used to do that.  But now, it's all grimy. and I don't know how to rectify this.  I shoulda paid more attention..

---

### Post by hyper_ch on 2008-07-18
or get/take her back ;)

---

### Post by kpkeerthi on 2008-07-18
> **Barrucadu said:**
> Not that I can think of, fsck is run every 30 boots, which fixes any fragmentation on your disks. 

Does fsck do defragmentation? I thought it doesn't. Correct me if I'm wrong.

---

### Post by sujoy on 2008-07-18
ya i doubt it too. i guess it checks the filesystem for errors and corrects them, (thus maybe solving any problem caused by fragmentation), but AFAIK it doesn't defrag

---

### Post by schauerlich on 2008-07-18
> **kpkeerthi said:**
> Does fsck do defragmentation? I thought it doesn't. Correct me if I'm wrong.

I don't believe it does.

---

### Post by philinux on 2008-07-18
> **kpkeerthi said:**
> Does fsck do defragmentation? I thought it doesn't. Correct me if I'm wrong.

It just reports how much as a %. It doesn't run every 30 boots exactly. The frequency is determined upon installation and depends on the disk/partition size IIRC.

[http://www.itworld.com/nls_unixfrag040929](http://www.itworld.com/nls_unixfrag040929)

---

### Post by MrWES on 2008-07-18
Maybe you need a new gf..no?

---

### Post by jmmL on 2008-07-18
On the topic of defragmentation, as far as i understand, the ext-type of filesystems don't really need defragmenting - not anywhere near as much as NTFS / FAT do at least. So if you're using ext2 or 3, then it shouldn't be a problem. (These are the default filesystems for ubuntu)

This might be a little outside of what you mean but if you want to "optimise" your experience then you could try running this attached script. It's the first one i wrote, and i plan to run it everyday (although i only wrote it yesterday!). It does 4 things:

1. Checks for updates
2. Installs the updates
3. Removes unnecessary packages
4. Cleans out residual config files

Here's the code:
[PHP]
#! /bin/bash
# Created by Jamie Lawler 17/7/08. Feel free to do /whatever/ you want with this script.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
string="Apt-getting is all done!"
echo $string [/PHP]

Place the file in your home directory ( /home/USERNAME/ )
You'll probably need to make it executable, and you can do this by running
```
 sudo chmod +x ~/apt.sh 
```
in a terminal.

To run the file, simply type
```
 ./apt.sh 
```

Hope this has helped!

---

### Post by damis648 on 2008-07-18
> **jmmL said:**
> On the topic of defragmentation, as far as i understand, the ext-type of filesystems don't really need defragmenting - not anywhere near as much as NTFS / FAT do at least. So if you're using ext2 or 3, then it shouldn't be a problem. (These are the default filesystems for ubuntu)

This might be a little outside of what you mean but if you want to "optimise" your experience then you could try running this attached script. It's the first one i wrote, and i plan to run it everyday (although i only wrote it yesterday!). It does 4 things:

1. Checks for updates
2. Installs the updates
3. Removes unnecessary packages
4. Cleans out residual config files

Here's the code:
[PHP]
#! /bin/bash
# Created by Jamie Lawler 17/7/08. Feel free to do /whatever/ you want with this script.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
string="Apt-getting is all done!"
echo $string [/PHP]

Place the file in your home directory ( /home/USERNAME/ )
You'll probably need to make it executable, and you can do this by running
```
 sudo chmod +x ~/apt.sh 
```
in a terminal.

To run the file, simply type
```
 ./apt.sh 
```

Hope this has helped!

Actually, you might want to throw in
```
sudo apt-get clean
```
which will delete all cached packages, whereas "autoclean" will remove only what is necessary. Other than that, great script!

---

### Post by scottuss on 2008-07-18
I have to say it is very nice not to have to worry about defrag and anti-virus etc. I'm so security concious (paranoid!) that I would spend hours tweaking and adjusting my security software in Windows. Now on Ubuntu, I configure my firewall once after install and never worry about anything else! (Well, I try not to! :lolflag:)

---

### Post by schauerlich on 2008-07-18
> **scottuss said:**
> I have to say it is very nice not to have to worry about defrag and anti-virus etc. I'm so security concious (paranoid!) that I would spend hours tweaking and adjusting my security software in Windows. Now on Ubuntu, I configure my firewall once after install and never worry about anything else! (Well, I try not to!)

Most would say you don't even need the firewall. Welcome to Linux. :)

---

### Post by paul101 on 2008-07-18
. . . you could open your computer up and give it a hoover



the amount of dust that collects (especially if the pc is on the floor and / or has lotts of fans) is astonishing

---

### Post by scottuss on 2008-07-18
> **EDavidBurg said:**
> Most would say you don't even need the firewall. Welcome to Linux. :)

Even though I'm out of the Windows security mindset, I'd argue a firewall is a good idea (not critical) but a good idea regardless of platform.

---

### Post by hyper_ch on 2008-07-18
> **scottuss said:**
> Now on Ubuntu, I configure my firewall once after install and never worry about anything else! (Well, I try not to! :lolflag:)
As long as you don't have services running there's no point in configuring the firewall (iptables) differently than the standard settings.

> **EDavidBurg said:**
> Most would say you don't even need the firewall. Welcome to Linux. :)
Well, a firewall is already installed... it just doesn't do any filtering ;)

> **scottuss said:**
> Even though I'm out of the Windows security mindset, I'd argue a firewall is a good idea (not critical) but a good idea regardless of platform.
When you strat installing services you might want to secure them. E.g. a ssh-server could be protected by a firewall... same goes for apache, mysql, samba, ..... question is what do you install and what do you need,....

security is an ongoing process.

---

### Post by scottuss on 2008-07-18
Exactly, I configure the firewall that is installed by default to actually do something :)

---

### Post by killersnowgoon on 2008-07-18
thanks for all the help guys. especially the script. :)

---

### Post by hyper_ch on 2008-07-18
have a look at [http://www.linuxcommand.org](http://www.linuxcommand.org) --> and you'll learn how to write a lot more powerful scripts (that can become quite handy)

---

### Post by Vorian Grey on 2008-07-18
> **killersnowgoon said:**
> up until about a month ago, i had been using windows my whole life. i did everything i could to optimize my computer; cleaned out registry, defraged almost every day, spyware and virus scans, basically i'm pretty anal about having my comp be at its full performance. now im using linux, and theres no registry, no need to defrag, no viruses. dont get me wrong, i love that, but is there anything i *should* be doing to clean/optimize?

Yeah, Ubuntu is down right boring, ain't it? Nothing to do but get stuff done. Too bad more companies don't buy into Linux. Instead of wasting a lot a time on the above stuff for Windows, they too could get stuff done.

---

