---
title: "apt-get install error"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by HybridTheory on 2008-06-07
I have a big problem when I try to install things using the terminal I get this error unable to fetch some archives, maybe run apt-get update or try with --fix-missing. So I try both when I use apt-get update I get the same error same with --fix-missing is there any way to fix this? thanks

---

### Post by iaculallad on 2008-06-07
> **HybridTheory said:**
> I have a big problem when I try to install things using the terminal I get this error unable to fetch some archives, maybe run apt-get update or try with --fix-missing. So I try both when I use apt-get update I get the same error same with --fix-missing is there any way to fix this? thanks

In your terminal:

```
sudo apt-get install --fix-missing
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by HybridTheory on 2008-06-07
```
sudo apt-get install --fix-missing
sudo apt-get update && sudo apt-get upgrade
```[/QUOTE]

This didnt work I still get the Failed to Fetch error

---

### Post by iaculallad on 2008-06-07
> **HybridTheory said:**
> 
This didnt work I still get the Failed to Fetch error

Try to post the full error description so we could look at it.

---

### Post by rraj.be on 2008-06-07
try this  

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by HybridTheory on 2008-06-07
> **rraj.be said:**
> try this  

```
sudo apt-get update
sudo apt-get install build-essential
```

that one also failed to work and the only error its giving me is "Ubable to fech some archives, maybe run apt-get update or try with --fix-missing?" and a long list of every thing it tried to install

---

### Post by Oldsoldier2003 on 2008-06-07
> **HybridTheory said:**
> that one also failed to work and the only error its giving me is "Ubable to fech some archives, maybe run apt-get update or try with --fix-missing?" and a long list of every thing it tried to install

please show us the results of ```
cat /etc/apt/sources.list
```

---

### Post by rraj.be on 2008-06-07
Just check whether you have enabled all repositories.

You might have disabled them.

---

### Post by HybridTheory on 2008-06-07
> **rraj.be said:**
> Just check whether you have enabled all repositories.

You might have disabled them.

That might be a problem Lol because that stuff isn't there I'm doing a full remaster of ubuntu so I fully removed every thing to do with  gnome and all the ubuntu apps and such but none of that stopped apt-get install until I installed XDM and started up Enlightenment and now in xterm i cant install any thing which I find odd...here is what i got from the cat command

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted unive
rse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted u
niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

# dunnewind e17 repository for Ubuntu Hardy

deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) hardy e17

# Remastersys

deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

---

### Post by rraj.be on 2008-06-07
Then enable it by going to 

system -->synaptic package manager

then 

 settings  -->repositaries.

select all check boxes available there  [hope now you know what are the things that you had disbaled and what should you enable]

---

### Post by HybridTheory on 2008-06-07
> **rraj.be said:**
> Then enable it by going to 

system -->synaptic package manager

then 

 settings  -->repositaries.

select all check boxes available there  [hope now you know what are the things that you had disbaled and what should you enable]

I didn't fool with that stuff and as I said I removed all that as its unneeded for the most part or so I think :(

---

### Post by rraj.be on 2008-06-07
You may think so.

But it may contain the system dependency sources.

forgive me if i a wrong.

---

