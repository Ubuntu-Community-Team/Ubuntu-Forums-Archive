---
title: "Ubuntu Oneiric Final ISO Testing"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jibel on 2011-10-10
The release of Oneiric is due this week and candidate images are ready for testing on the [ISO tracker]("http://iso.qa.ubuntu.com/"). As usual we'll be asking everyone on the QA team to participate in the image testing to ensure we have good test coverage. 

The procedures for testing ISO images and reporting results are explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) 

Sync the images and post your test results on the tracker at [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)  

You may have accounts on the tracker from last time. Please register if you are new to this.  Please let us know if you have any questions.  We will coordinate testing in #ubuntu-testing on freenode. Please, go there often to see what others are testing or what needs to be tested. 

Thank you very much for your help and happy testing!

---

### Post by kansasnoob on 2011-10-10
I see all of the images are rebuilding this AM :)

I let my Ubuntu upgrade test complete while I slept and it worked perfectly.

---

### Post by kansasnoob on 2011-10-11
Just a quick bump. I see the very first of the 20111011 images are beginning to appear this AM.

Please keep watching (and refreshing):

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

No telling how many rebuilds there will be, that's the fun part :D

---

### Post by kansasnoob on 2011-10-12
I noticed some confusion on one of the mailing lists about using zsync, and since I find the forums easy to use I'm going to post "**How I manage my images with zsync**" here :)

Needless to say you must have zsync installed:

```
sudo apt-get install zsync
```

I think most folks know how to find the daily images and the link to the iso-testing images is listed in this thread. Using zsync depends greatly on **location and name**.

If I were to run zsync in the terminal without specifying a location it just looks directly in your home directory, but I'd guess most of us use the Downloads folder. Lets use "ls" to look at my directory structure:

```
lance@lance-VIA-desktop:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
lance@lance-VIA-desktop:~$ ls Downloads
lost+found  Lubuntu  Ubuntu  Xubuntu
lance@lance-VIA-desktop:~$ ls Downloads/Ubuntu
oneiric-alternate-i386.iso  oneiric-desktop-i386.iso.zs-old
oneiric-desktop-i386.iso
lance@lance-VIA-desktop:~$ ls Downloads/Lubuntu
oneiric-alternate-i386.iso         oneiric-desktop-i386.iso
oneiric-alternate-i386.iso.zs-old  oneiric-desktop-i386.iso.zs-old
lance@lance-VIA-desktop:~$ ls Downloads/Xubuntu
oneiric-desktop-i386.iso  oneiric-desktop-i386.iso.zs-old

```

You'll notice that I have sub-folders in Downloads for each flavor of ubuntu, a closer look will reveal why. The daily (and testing) images all share the same basic iso **names**:

oneiric-alternate-i386.iso
oneiric-desktop-i386.iso

And since I cross-test all flavors at one time or another I need to tell zsync the proper location to find the existing old or partial image. I prefer just using the "cd" command to change directories. In this example I'm working on Lubuntu:

```
lance@lance-VIA-desktop:~$ cd Downloads/Lubuntu
lance@lance-VIA-desktop:~/Downloads/Lubuntu$ ls
oneiric-alternate-i386.iso         oneiric-desktop-i386.iso
oneiric-alternate-i386.iso.zs-old  oneiric-desktop-i386.iso.zs-old
lance@lance-VIA-desktop:~/Downloads/Lubuntu$ 

```

Note: I only ran the "ls" command to **see** what's there (and to show you) :)

Do you get the **location** thing? If I want to return to the home directory I just **cd** again:

```
lance@lance-VIA-desktop:~/Downloads/Lubuntu$ cd
lance@lance-VIA-desktop:~$ 

```

Easy peasy, eh? But in this example I just want to zsync the Ubuntu desktop image from here:

[http://iso.qa.ubuntu.com/qatracker/info/7039](http://iso.qa.ubuntu.com/qatracker/info/7039)

So I copy the zsync link, open a terminal, and "cd" to Downloads/Ubuntu. Then just paste the link into the terminal:

```
lance@lance-VIA-desktop:~$ cd Downloads/Ubuntu
lance@lance-VIA-desktop:~/Downloads/Ubuntu$ zsync http://cdimage.ubuntu.com/daily-live/20111012/oneiric-desktop-i386.iso.zsync
#################### 100.0% 302.4 kBps DONE     

reading seed file oneiric-desktop-i386.iso: ****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read oneiric-desktop-i386.iso. Target 93.0% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/20111012/oneiric-desktop-i386.iso:
#################### 100.0% 415.2 kBps DONE      

verifying download...checksum matches OK
used 678031360 local, fetched 51718183
lance@lance-VIA-desktop:~/Downloads/Ubuntu$ 

```

Note: the daily image web page lacks the word zsync at the beginning of the DL link so you must type zsync into the terminal before pasting the DL link.

Now, you'll notice that it says "checksum matches OK" and I've never had that fail, but I do a lot of testing and I need to keep track of which image is which so I still always:

```
lance@lance-VIA-desktop:~/Downloads/Ubuntu$ md5sum oneiric-desktop-i386.iso
c396dd0f97bd122691bdb92d7e68fde5  oneiric-desktop-i386.iso
```

Then I actually keep a word document named "md5sums" like this:

> 6ddd6f57842a170c7fbb2cb60c7de097  oneiric-desktop-i386.iso
&#65279;6ddd6f57842a170c7fbb2cb60c7de097 (lubuntu 20111010.1)

338524faf8f1c855034b27b88a60519a  oneiric-desktop-i386.iso
&#65279;338524faf8f1c855034b27b88a60519a (ubuntu 20111010.1)

40cc858904a4c9d70ca26f20468fe197  oneiric-desktop-i386.iso
&#65279;40cc858904a4c9d70ca26f20468fe197 (xubuntu 20111010.1)

cc3f01df904da8e774fa04d289348543  oneiric-desktop-i386.iso
&#65279;cc3f01df904da8e774fa04d289348543 (ubuntu 20111011)

32141e7ae581591a29142d0dcc1ecc29  oneiric-desktop-i386.iso
&#65279;32141e7ae581591a29142d0dcc1ecc29 (lubuntu 20111011)

48778dba5fa74c582b1e49a5bce73263  oneiric-desktop-i386.iso
&#65279;48778dba5fa74c582b1e49a5bce73263 (xubuntu 20111011)


The newest I'm adding is here, I just use copy-n-paste from the terminal and from the DL link:

> c396dd0f97bd122691bdb92d7e68fde5  oneiric-desktop-i386.iso
&#65279;c396dd0f97bd122691bdb92d7e68fde5 (ubuntu 20111012)

Notice that I used a "label" of (ubuntu 20111012), the terminal output itself indicates whether it's a "desktop" or "alternate" image, and I always "pull" the date stamp from here:

> [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)**[COLOR="Red"]20111012[/COLOR]**/oneiric-desktop-i386.iso.zsync

If there is a rebuild today of that image it will be "20111012**.1**", a second rebuild would be "20111012**.2**", etc.

I also always use the date stamp to label my CD's so I can keep track of them :)

One more thing about the importance of the iso **name**. What if the newest image you have is the Beta 2? It would be named something like:

> ubuntu-11.10-beta2-desktop-i386.iso

But the testing image is named:

> oneiric-desktop-i386.iso

So I would use either "cp" to copy the existing beta2 image and give it a new name:

Note: do not use "sudo" in your home folder or you may hose the permissions!

```
cp ubuntu-11.10-beta2-desktop-i386.iso oneiric-desktop-i386.iso
```

Or to just rename it without keeping the original you'd use "mv":

```
mv ubuntu-11.10-beta2-desktop-i386.iso oneiric-desktop-i386.iso
```

I hope this is helpful to someone :)

Also I did this somewhat hurriedly so I hope I didn't make any huge mistakes.

---

