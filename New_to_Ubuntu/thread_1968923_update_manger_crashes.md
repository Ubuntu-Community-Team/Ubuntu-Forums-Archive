---
title: "update manger crashes"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by johnnybevo on 2012-04-29
how do i fix this.

E: Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by plucky on 2012-04-29
> **johnnybevo said:**
> how do i fix this.

E: Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```
gksudo gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
```

And  post the contents to the forum

---

### Post by corrytonapple on 2012-04-29
What version of Ubuntu are you running?
If you want to update in the downtime, and this may even tell you if there is an underlying issue, go to the terminal and type:
```

sudo apt-get update && sudo apt-get upgrade

```
Your password will be invisible, as it is a security measure

---

### Post by johnnybevo on 2012-04-29
This what i get

b-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main

---

### Post by johnnybevo on 2012-04-29
> **corrytonapple said:**
> What version of Ubuntu are you running?
If you want to update in the downtime, and this may even tell you if there is an underlying issue, go to the terminal and type:
```

sudo apt-get update && sudo apt-get upgrade

```
Your password will be invisible, as it is a security measure

ubuntu 12.04 lts 64bit

this is what i get when i enter code in the terminal

E: Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
E: The list of sources could not be read.

---

### Post by johnnybevo on 2012-04-29
is there a way to set all back to default maybe.
The synaptic crashes also and the update manager.

Thinking about going back to 11.10 anyway because of the issue with the nvidia drivers in 12.04

---

### Post by johnnybevo on 2012-04-29
Got it fixed.
Here is the solution.
Thanks for your help


Open a terminal and type (or copy and paste)

Code:
sudo sed -i 's/b-src/deb/g' /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
Enter your password. It will not be echoed to the screen.

Then type 

Code:
sudo apt-get update
__________________

---

