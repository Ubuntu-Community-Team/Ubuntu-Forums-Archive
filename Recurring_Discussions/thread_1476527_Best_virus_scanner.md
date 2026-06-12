---
title: "Best virus scanner?"
date: 2010-05-07
forum: Recurring Discussions
---

### Post by Zanven on 2010-05-07
I would like suggestions on the best virus scanner for Linux. The purpose is to scan items before moving them to my windows partition.

ClamAV seems to be garbage and won't update. 

When I was newer to Linux (still am quite new) I couldn't figure how to get avast for linux to start via command but only from menu thus preventing me from starting it at start up. 
And now on my new system I can't get it to work at all. It displays "An error occured in avast! engine: Invalid argument" when I try to open it.

So what are your thoughts

---

### Post by jerenept on 2010-05-07
klamav... much better imo than avast- Klamav is a kde frontend to clamav and it updates the virus database automatically.

---

### Post by Zanven on 2010-05-08
OK, thanks. I put Klamav on my laptop and it never updated correctly but it works fine on my desktop for some reason.

---

### Post by Roasted on 2010-05-08
I do not believe ClamAV will update the actual GUI application due to the fact that tends to be locked down from the repos. Perhaps if you found a PPA for it you could get the updated versions of ClamAV on the go.

ClamAV however does automatically update the virus definitions frequently.

IMO it's the best virus scanner out there. The newer version that comes standard in 10.04 even supports auto-scanning based on a schedule.

---

### Post by dcstar on 2010-05-08
> **Zanven said:**
> I would like suggestions on the best virus scanner for Linux. The purpose is to scan items before moving them to my windows partition.

ClamAV seems to be garbage and won't update. 
.......

Rubbish. Clamav updates and works fine if it is installed correctly.

One of the associated packages is freshclam, which does all the updating automatically, is it actually installed?

---

### Post by WorMzy on 2010-05-08
Indeed, ClamAV checks for updates once an hour if left with default settings. You can increase/decrese this amount by running sudo dpkg-reconfigure clamav-freshclam

---

### Post by Zanven on 2010-05-19
In options there is the section for archive types and "Scan ___ using :" which is blank which I assume is to use an external program to scan archive files.
Without putting something there does KlamAV scan archive files recursively?

---

### Post by RogerDavis on 2010-05-21
KLAMAV is more than a little confusing because of what it doesn't say.  I need to know:

- Does it need to be started as a "startup" program by me or by my setting, or does it do this on it's own?  I can't see any indication it's loaded and running.

- Once it's running, however it's started, is it acting as a resident program, watching all incoming downloads, web pages, etc?

---

### Post by kentechy on 2010-05-21
> **Zanven said:**
> I would like suggestions on the best virus scanner for Linux. The purpose is to scan items before moving them to my windows partition.

ClamAV seems to be garbage and won't update. 

When I was newer to Linux (still am quite new) I couldn't figure how to get avast for linux to start via command but only from menu thus preventing me from starting it at start up. 
And now on my new system I can't get it to work at all. It displays "An error occured in avast! engine: Invalid argument" when I try to open it.

So what are your thoughts

I like BitDefender and it is free.  Get BitDefender for Unices here:  

[http://www.bitdefender.com/site/Downloads/browseEvaluationVersion/2/80/](http://www.bitdefender.com/site/Downloads/browseEvaluationVersion/2/80/)

---

### Post by dcstar on 2010-05-22
> **RogerDavis said:**
> 
........
- Once it's running, however it's started, is it acting as a resident program, watching all incoming downloads, web pages, etc?

There is NO NEED whatsoever to do **any** of these things, this is not Windows.

---

### Post by Zanven on 2010-05-22
> **dcstar said:**
> There is NO NEED whatsoever to do **any** of these things, this is not Windows.

I need it for scanning things before I put them on my windows system. So in essence I am using for windows.

---

### Post by WorMzy on 2010-05-22
If you're using Firefox, you can use an extension known as [Download Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/26/") to run clamscan for every download. That's what I do. It's configured so that after every download it runs

```
/usr/bin/gnome-terminal
```

with the following arguments:

```
--window-with-profile=hold -x clamscan -v -l /home/wormzy/Clamscan_Firefox_Results --move=/home/wormzy/.infected %1
```

This opens a gnome-terminal with a profile I've made which keeps the terminal open after it's finished. It makes the terminal run clamscan to scan the downloaded file (%1), and if it finds an infection, moves the file to my home folder which ext4 and cannot be accessed from windows, therefore eliminating the threat before it has a chance to do anything. It also puts the results of the scan into a log file (Clamscan_Firefox_Results).

Feel free to use this if you want. You'll need to modify it so it uses your home, not mine, and you'll also need to create a folder called ".infected" in your home folder, otherwise the scan will error due to the folder not existing.

I don't think there's any point of having it scan every webpage you visit though. If you accidentally trigger a windows virus while browsing, it won't do anything because you're not on Windows.

---

### Post by bodhi.zazen on 2010-05-22
moved to recurring discussions.

---

### Post by Kay The Bantu on 2010-05-22
i have also installed KlamAv personally and it works and updates without any hitch. but if it isn't for you, you could always go for the free version of AVG Linux [http://free.avg.com/gb-en/download.prd-afl]("http://free.avg.com/gb-en/download.prd-afl")

---

### Post by WorMzy on 2010-05-22
There's also [Avast]("http://www.avast.com/linux-home-edition"). I use it on Windows, and it gets the job done.

---

### Post by RogerDavis on 2010-06-15
I have KlamAV installed, and it starts each time I start the system.  However, it leaves a file open every startup of (apparently) its startup log or something...

Anyway, how do I get this to not appear and still start the program, or make it go away automatically after it's started?

Also, if I close this window manually, it doesn't stop the program (does it)?

Thanks!

---

### Post by WorMzy on 2010-06-15
KlamAV is just a KDE front end for clamav. Opening it and closing it doesn't make any difference to the underlying clamav daemon. You need to make it so that the daemon will run at start up if you want it to be constantly running; you can do that by running ```
sudo dpkg-reconfigure clamav
```

Not sure what you mean by the file, but you can probably turn off logging somewhere. Look in /etc for clamav conf files, I think they're under /etc/defaults/clamav

---

