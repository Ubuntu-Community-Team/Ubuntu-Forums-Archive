---
title: "Changing PC Name &amp; Resolving Host ~ Log File?"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Andavane on 2012-08-10
I have a machine I'll be using tomorrow which started getting problem "Unable to Resolve Host" when making updates. I shall be going through the options to see if the matter is resolved.

Meanwhile I point out that I had renamed my machine twice (sudo gedit /etc/hostname).

I think the renaming might have messed up the updating somehow. The trouble is I didn't note the previous names, so I wondered if there's a logfile somewhere which keeps a record.

My main machine is Lenovo X201i with Intel Chip. and I renamed it and it's downloading and installung updates just fine.

The one which doesn't update properly is Lenovo X121 E with the AMD chip.

---

### Post by NikTh on 2012-08-10
Hi , 
I am not sure if understood you problem correctly , but I know that If you change the name of machine from /etc/hostname , you must change accordingly and the name in /etc/hosts. Not the localhost , but the other. Next to 127.0.1.1
I hope this helps.
Thanks

---

### Post by spjackson on 2012-08-10
> **Andavane said:**
> 
Meanwhile I point out that I had renamed my machine twice (sudo gedit /etc/hostname).

I think the renaming might have messed up the updating somehow. The trouble is I didn't note the previous names, so I wondered if there's a logfile somewhere which keeps a record.

In terms of logging the change, I'm not sure that happens but several processes do log the current hostname to various files in /var/log. So you could do
```

sudo fgrep current_hostname /var/log/*

```substituting your current hostname for current_hostname. That should lead to to something you can search for to find old names.

A better bet, if you have etckeeper installed, is to diff against old versions. I think etckeeper is installed by default.

```

cd /etc
sudo bzr log hostname

```That should give you some revision numbers. You can then look at the changes.
```

sudo bzr diff hostname
sudo bzr diff hostname -r433 -r292

```for example.

EDIT: My mistake, etckeeper is not installed by default, so if you don't have it, then you are stuck with grepping the log files.

---

### Post by Andavane on 2012-08-12
> **NikTh said:**
> Hi , 
I am not sure if understood you problem correctly , but I know that If you change the name of machine from /etc/hostname , you must change accordingly and the name in /etc/hosts. Not the localhost , but the other. Next to 127.0.1.1
I hope this helps.
Thanks
Yes thank you, it certainly has helped.
What I did was change the name back in the hosts file, next to 127.0.1.1 as you say. 
The instructions I found for renaming the computer all say just "sudo gedit /etc/hostname" but it doesn't add that if you do this, you need to name it the same in hosts as well, otherwise it won't be able to resolve updates and I'll get "unable to resolve hostname".
 
It all seems fine now, except:


> **spjackson said:**
> In terms of logging the change, I'm not sure that happens but several processes do log the current hostname to various files in /var/log. So you could do
```

sudo fgrep current_hostname /var/log/*

```substituting your current hostname for current_hostname. That should lead to to something you can search for to find old names.

A better bet, if you have etckeeper installed, is to diff against old versions. I think etckeeper is installed by default.

```

cd /etc
sudo bzr log hostname

```That should give you some revision numbers. You can then look at the changes.
```

sudo bzr diff hostname
sudo bzr diff hostname -r433 -r292

```for example.

EDIT: My mistake, etckeeper is not installed by default, so if you don't have it, then you are stuck with grepping the log files.

Thank you, I haven't followed this procedure yet because what I did next was to go:

sudo apt-get update then
sudo apt-get upgrade.

All seemed to be going well as I wached the Terminal doing all its stuff. However to my surprise when I clicked the gear button top right it still told me "updates available". I repeated the Terminal procedure where it made a few small additions, however the top right gear bar continues to insist that updates are available. This is confirmed by attached doc below.

I wonder why, when I've updated via the Terminal, updates are still apparently available?

PS: When I type

sudo fgrep andavane-mini /var/log/* 

(andavane-mini is the name I reverted to) I get pages of text which is quite beyond me.

Te subject of this thread has changed, with the resolution (I think) of hostname but it's a 2-pronged question.

PPS: I take it etckeeper is a tracker of whatever goes on in etc?

---

### Post by NikTh on 2012-08-12
Hi , 
Open a terminal and do 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` and you will be fine with updates too. 
Mark _thread as solved_ by clicking on _Thread tools_ , if your problem solved.
Thanks

---

### Post by Andavane on 2012-08-13
> **NikTh said:**
> Hi , 
Open a terminal and do 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` and you will be fine with updates too. 
Mark _thread as solved_ by clicking on _Thread tools_ , if your problem solved.
Thanks
Yes indeed, thanks. It was the _dist_-upgrade that I was missing.
Another notch marked on the pole of understanding!

---

