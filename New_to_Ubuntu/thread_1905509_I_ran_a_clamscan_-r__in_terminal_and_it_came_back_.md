---
title: "I ran a clamscan -r / in terminal and it came back with 55 infected files how do I fi"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by euclid1219 on 2012-01-07
----------- SCAN SUMMARY -----------
Known viruses: 1308115
Engine version: 0.97.3
Scanned directories: 35867
Scanned files: 179489
Infected files: 55
Total errors: 701
Data scanned: 7395.45 MB
Data read: 13316.74 MB (ratio 0.56:1)
Time: 2484.645 sec (41 m 24 s)

after the scan I tried the commands sudo add-apt-repository ppa:ubuntu-clamav/ppa; sudo apt-get update; sudo apt-get -y install clamav clamtk; sudo freshclam none could remove infected files what is the command to remove infected files from terminal after scan

I even tried --remove to the clamscan or clamdscan command-line from [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

how do I get rid of them?

---

### Post by Guilden_NL on 2012-01-07
Are you running as Super User?  That's the first thing that comes to mind since it isn't moving the files as expected.

Other than that, I am out of ideas. I haven't used Clam in years, I didn't like it.  BitDefender is my personal choice, but I recognize that you might be running on light/old HW that defines your use of ClamAV. So not criticizing your use of Clam.

---

### Post by euclid1219 on 2012-01-07
Super User?
light/old HW?

please explain what these are?

---

### Post by Paqman on 2012-01-07
> **euclid1219 said:**
> how do I get rid of them?

I would be very, very careful before doing so. ClamAV is not a partcularly good AV scanner, and will report a lot of false positives. Do not automatically remove things just because it flags them, doing so could well break your system.

Install a different AV scanner (Avast, Bitdefender, AVG) and run the scan again. If any of the same files are flagged, post them here and we'll see if it looks safe to remove them.

Don't worry though, it's *extremely* unlikely that you've got an actual infection on your system. There are no known Linux viruses in the wild at the moment, so if your software is up-to-date then you're protected. Anything ClamAV is going to detect will be either a false positive or something harmless to Linux that's sitting in a cache. The vast majority of people using desktop Linux don't use an AV suite, and stay perfectly safe just through keeping their mahcine updated and safe browsing habits.

[More about Linux security here.]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by khelben1979 on 2012-01-07
Hmm.. Windows viruses can easily get into your hard disc, and so I use my ClamScan software to remove it and I have never experienced that it has damaged anything in my Linux system, in the process.

Other than that I have never experienced that any Linux virus or trojan have caused any problems on my Linux system, but I think you can trust the ClamScan software as long as you avoid running it as full root user.

Removing viruses has a purpose even on a Linux system.

---

### Post by euclid1219 on 2012-01-07
thanks guys I will take your advice and look into Avast

---

### Post by sammiev on 2012-01-07
> **euclid1219 said:**
> thanks guys I will take your advice and look into Avast

Avast is great but I must give Bitdefender a +1 as well. :)

---

### Post by khelben1979 on 2012-01-08
"Linux operating systems have been considered less vulnerable than Windows systems for many years but the myth that they are immune to virus attack is completely false." - [source]("http://www.bitdefender.com/business/antivirus-for-unices.html").

Seems to me they are ready to say that Linux is beginning to get as vulnerable to viruses as Windows. Better go for another company which got the facts straight, I think. I understand that they just want to make money.

---

### Post by Paqman on 2012-01-08
> **khelben1979 said:**
> I understand that they just want to make money.

This. Technically what they're saying is correct. Linux systems aren't invulnerable. But that doesn't mean there are a lot of threats either.

Linux antivirus does serve a useful role, it's good for protecting networks from Windows malware. If that's important to you, then by all means use it. But I don't think there's any need for every standalone Linux desktop to have an AV suite installed.

---

### Post by euclid1219 on 2012-02-14
I just bought Avast Internet security they say they don't service linux ubuntu operating system

so How are linux users using Avast?

---

### Post by sammiev on 2012-02-14
> **euclid1219 said:**
> I just bought Avast Internet security they say they don't service linux ubuntu operating system

so How are linux users using Avast?

You could have got Avast for free and people who use it on linux use it to protect files and so on that they move from a linux OS to a windows OS. As I share a lot of items between friends that use windows I feel better knowing that I'm not giving them a virus or so on from my linux OS computer. :)

---

### Post by winh8r on 2012-02-14
If anyone chooses to use it then it is here:

[http://www.avast.com/linux-home-edition]("http://www.avast.com/linux-home-edition")


once installed use the command 

```
avastgui
```

if you need a GUI rather than command line

---

