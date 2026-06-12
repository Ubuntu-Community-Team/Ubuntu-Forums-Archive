---
title: "How to set up old mn720 wireless card"
date: 2009-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by z.s.tar.gz on 2009-03-29
There are many threads around on how to set up the microsoft mn-720 wireless card, but they are old and outdated.

Note: B43 does not work well with this particular card (to the best of my knowledge) and therefor you will have to use ndiswrapper.


1. **Ndiswrapper**

If you have wired internet: 

You will need ndiswrapper, so run the following in terminal:
```
sudo apt-get install ndiswrapper-utils
```

If you don't have wired internet:

Intrepid: 
You need [this](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1ubuntu1_all.deb)
You also need one of these: [Intel](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) [AMD](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_amd64.deb)

Hardy:
You need [This](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)
You also need one of these: [Intel](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) [AMD](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb)

You should end up with two packages: ndiswrapper-common and ndiswrapper-utils. Put these in a folder named "ndiswrapper" on your desktop.

Now that you (hopefully) have the appropriate .deb files, you can install both of them at once with:
```

cd ~/Desktop/ndiswrapper
sudo dpkg -i *.deb

```

2. **Drivers**

Now that you have ndiswrapper installed, you need the drivers. The drivers are scattered obscurely throughout the internet, so for the sake of simplicity I have a link [here](http://www.mediafire.com/?nnnykj2x4zo), and have also attached the zip file.

Extract the zip to a file called "mn720-ankh" on the desktop.

3. **Installing**

This is the easy part. Just run:
```
cd ~/Desktop/mn720-ankh
sudo ndiswrapper -i mn720-ankh.inf
```


Just reboot and that's it. Your old wireless card is now good to go.

Note: If you can't get the card to work after a reboot, try running:
```
sudo modprobe ndiswrapper
```

Did this help you out? Did it not? Leave some feedback if you be so kind

---

### Post by dmizer on 2009-03-30
Please attach the zip file directly. The link does not work.

---

### Post by z.s.tar.gz on 2009-03-31
Ok. Sorry, I didn't get the zip posted, my power went out and I wasn't even aware this tread was posted until now.

So, let me finish real quick...

---

### Post by BigBig5 on 2009-10-12
It didn't work for me.

---

