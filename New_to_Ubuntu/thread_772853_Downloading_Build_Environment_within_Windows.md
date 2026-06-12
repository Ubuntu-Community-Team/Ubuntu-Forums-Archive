---
title: "Downloading Build Environment within Windows"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by lorienjohnson on 2008-04-28
Hello! I've successfully installed 8.04! Cheers, applause, etc.

I'm now trying to install the drivers for my Realtek 8185. I have two tutorials, one for ndiswrapper and one for installing the Realtek 8187 driver. 

Both require downloading build environments. For example, the ndiswrapper tutorial has the following:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

However, I require the internet in order to download those. I do not have access to a wired connection.

From where do I download the necessary files from a website/etc with my working wireless connection in Windows?

Thanks!

---

### Post by lorienjohnson on 2008-04-29
Are these even available to download from a standard website, or must they be downloaded from within Linux?

---

### Post by lorienjohnson on 2008-05-03
bump - Any ideas at all?

---

### Post by SunnyRabbiera on 2008-05-03
sure, you can get most of what you need from this page:
[here]("http://packages.ubuntu.com/")
from windows you can download all these packages and then you can install them into your ubuntu when you boot into it.
Juat make sure to grab all the needed dependencies, there is no real easy way to do this (yet) but you should be able to get what you need from the site I linked you.
I know I had a hell of a time getting wireless to work for my other computer but when it works it works.

---

