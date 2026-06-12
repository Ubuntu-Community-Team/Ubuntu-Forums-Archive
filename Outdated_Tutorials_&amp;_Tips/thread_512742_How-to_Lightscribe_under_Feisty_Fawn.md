---
title: "How-to: Lightscribe under Feisty Fawn"
date: 2007-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Peter76 on 2007-07-29
First of all, a lot of info for this howto comes from this thread: [http://ubuntuforums.org/showthread.php?t=106197](http://ubuntuforums.org/showthread.php?t=106197) , especially the post by Loveyoung.
But there's some more to it, and I thought it would be nice to have all the info in one How-To...

So here we go....

First download "Lightscribe System Software" and "Lightscribe Simple Labeler" from [www.lightscribe.com](www.lightscribe.com) .

Now, System -> Administration -> Users and Groups, and make a group "wheel" and add any users that you want to be able to use the Lightscribe software to this group.
Or in a terminal:

```
sudo addgroup wheel
sudo adduser username wheel
```

where username is the name of the user you want to add to this group.

Install alien, libpng3 and libqt3-mt through Synaptic, or in a terminal:

```
sudo aptitude install alien libpng3 libqt3-mt
```

Now in a terminal, cd to the directory where you saved the lightscribe software and issue the following command:

```
sudo alien -i --scripts lightscribe-1.8.13.1-linux-2.6-intel.rpm
```

It will quit complaing about it's license file... To solve:

```
sudo gunzip /usr/share/doc/lightscribeLicense.rtf.gz
``` 

Now again

```
sudo alien -i --scripts lightscribe-1.8.13.1-linux-2.6-intel.rpm
```

And it should finish its installation without trouble...

Time to install the Labeler software:

```
sudo alien -i lightScribeSimpleLabeler-1.4.128.1-linux-2.6-intel.rpm
```

Everything should now be installed under /opt/lightscribeApplications/ . To do a test run of Simple Labeler: 

```
cd  /opt/lightscribeApplications/SimpleLabeler/
./SimpleLabeler
```

If it does't work, the output given here should point you in the right direction to fix it ( or post here ). I get some X errors, but they don't seem to do any harm.

You also should install Lacie Lightscribe Labeler frome here: [http://www.lacie.com/support/drivers/driver.htm?id=10094](http://www.lacie.com/support/drivers/driver.htm?id=10094) . This will give you some options Simple Labeler hasn't. In a terminal, cd to the directory where you dowloaded it and:

```
 sudo alien -i 4L-1.0-r6.i586.rpm 
```

To do a test run:

```
4L-gui
```

It installs a manual as well under /usr/4L/doc

Now only use the menu editor to add an entry for Simple Labeler and 4L in your Applications menu and you are done.

Hope this was helpfull and please post any comments or suggestions

Peter

---

### Post by Greyhair on 2007-07-30
Thank you      ):P       

Works a treat........\\:D/

---

### Post by struess on 2007-08-03
thanks for taking the time to do this.  i just got an hp dvd1040 and want to fire up lightscribe asap.

unfortunately, on 64-bit feisty, alien gets stubborn and won't install.  i don't know of another way to convert the rpms to debs or to install lightscribe from the rpms straight up... any suggestions?

---

### Post by Peter76 on 2007-08-03
I don't think you can use those rpm's on 64-bit; what I understand of it, is that they have to be compiled for 64-bit to work.... But I'm not really a specialist on that subject.

Good luck

---

### Post by Turgurlas on 2007-08-06
Thanks Man you were a Great help! :)

---

