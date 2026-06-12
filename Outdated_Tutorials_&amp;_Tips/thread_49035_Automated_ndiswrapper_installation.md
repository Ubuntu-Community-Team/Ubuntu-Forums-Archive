---
title: "Automated ndiswrapper installation"
date: 2005-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Nequeo on 2005-07-14
Greetings,

As everyone reading this probably knows, many wireless cards will not work by default in Ubuntu without a program called ndiswrapper. Some distros ship with ndiswrapper and many common wireless drivers pre-installed. Ubuntu doesn't, for what I think are primarily philosophical reasons. 

So... I've been working on a script that will automatically install ndiswrapper and then suck the windows drivers needed by ndiswrapper off the driver cd that shipped with the card. 

I've subsequently learnt that someone is working on a graphical tool to do this, which will probably be included in Breezy. So I've stopped developing my own script. But while we wait for Breezy, I figure I may as well present what I've already done, in the hope it may help someone.

KNOWN ISSUES WITH THE SCRIPT:

* Currently it only detects the x86 CD, not AMD64 or PowerPC. This is a trivial problem to fix, I just need to know the first 32 characters of the 'md5sum.txt' file in the root directory of the install CD of those other architectures. 

* The script only searches /cdrom/, which probably corresponds to the master drive. So if you have multiple cdroms, you'd need to make sure that's where you put the CDs it asks for. 

* If you don't have a driver cd, you can still use the script. You just need to download and unzip the latest windows drivers for your card somewhere, then edit the script and search for 'path = '. Then change '/cdrom/' on the same line to match the directory where you unzipped the drivers. 

Alright... Here we go:

Download the script here:
[http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py](http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py)

If it opens as a text file in Firefox, just go to File--->Save Page As. 

If you're new to Linux, I'd suggest saving it onto your desktop. 

Now we need to mark the script as executable. You can either do this over the command line... But if you know how, you won't need my instructions to do that.

Otherwise, right click on the file on your desktop, select 'properties', then click on the permisssions tab and click on 'execute'. Then click on close.

Now open a terminal. You can right click on the desktop and select 'Open Terminal'. In the terminal type in

```

$ cd Desktop
$ sudo ndiswrapper_wrapper.py

``` 

Type in your password... and then that's it. The script *should* do the rest, so long as you insert the cds it asks for.
 
If for some reason the script doesn't work, there's plenty of help on these forums about configuring ndiswrapper by hand.

Cheers!

---

