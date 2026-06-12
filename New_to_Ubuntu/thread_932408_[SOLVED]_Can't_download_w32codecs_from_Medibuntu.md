---
title: "[SOLVED] Can't download w32codecs from Medibuntu"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by timlowell on 2008-09-28
I've been trying to get the w32codecs file from Medibuntu for two days, and it doesn't work.  It gets a few percent in and then resets, tries a few more gets, and then it tells me that it is unable to fetch it.  Am I doing something wrong, or is the Medibuntu site just overwhelmed with requests?

---

### Post by inxygnuu on 2008-09-28
I don't know very much about "Medibuntu:confused:", but it can be one of these causes:
1)You have some sort of problem with your internet. (modem, router, server etc...)
2. The file no longer exists and the loading bars are just It tryng to find the file.
3)too many requests/site or server is down
4)download link
5)other:confused:

---

### Post by Elfy on 2008-09-28
Well medibuntu is working here, are you sure the sources are correct. Does an apt-get update work ok for you

```
sudo apt-get update
```

If there is an error post it please.

---

### Post by Jose Catre-Vandis on 2008-09-28
I had trouble with medibuntu earlier on today, but it seems OK now, so it might have been out for a while.

---

### Post by timlowell on 2008-09-28
The connection is fine.  Every other application that connects to the internet works.

Medibuntu is a site that houses all kinds of packages for running media applications.  It stands for Multimedia, Entertainment & Distractions In Ubuntu.  You are supposed to be able to get the W32Codecs from there so you can run WMV and other proprietary formats in Ubuntu, but I can't ever get it to finish downloading the file.  I was hoping somebody with some inside knowledge knew what was going on.  Thanks.

---

### Post by Elfy on 2008-09-28
Have you been able to get anything from medibuntu or is it just w32codecs causing you a problem.

Run this and post the output please

```
sudo apt-get update &&sudo apt-get install w32codecs
```

---

### Post by timlowell on 2008-09-28
I've tried sudo apt-get update, and nothing changes.  It still doesn't work.

---

### Post by Elfy on 2008-09-28
Go to the medibuntu site and see if you get it ok as a deb file then

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by timlowell on 2008-09-28
It still starts, runs for a while, then stops, with the message: 

could not connect to packages.medibuntu.org:80 (88.191.82.11) connection timed out

That's after it has already downloaded up to 25% of the file.  It gets that far, resets back to 0% and starts over, then after 10 or 12 tries, I get the above timeout message.  The download speed is highly variable when it is connected, from 11 Kb/s down to a few hundred Bytes/second, down to zero.  If it stays at zero long enough, that's when it starts over.

I tried downloading this file on my Windows PC, and I get similar results.  It runs for a while, stops, and then freezes, and I have to restart it.  It looks like something is constantly resetting the download, like it is trying to prevent this file from being downloaded.  As I understand it, these Codecs are proprietary, and Ubuntu is really not supposed to be using them, so I'm wondering if some outside agent is monitoring these downloads and shutting them down.  I mean, it's only a 14 MB file, and I should be able to download that in less than a minute.  So far, it's been two days and no luck.

---

### Post by Elfy on 2008-09-28
No it's nothing sinister - I've just downloaded the hardy w33 codec - 20 secs or so.

If you can't download it from either buntu or windows then I would suggest that it is probably at your end.

Just out of interest which version of buntu are you trying to get it for and I'll d/l that specific one.

---

### Post by timlowell on 2008-09-28
I am using Hardy Heron 8.04.  Thanks.

---

### Post by mc4man on 2008-09-28
Medibuntu has been up and down all weekend. Same thing happened to me setting up Intrepid. You could just keep trying as it changes almost min. to min. Right now it's down. (3:12 est.) So either keep trying every few minutes 

or go here and dl. 3rd one down , the .deb
[http://debian-multimedia.org/pool/main/w/w32codecs/](http://debian-multimedia.org/pool/main/w/w32codecs/)


Edit: and now it's back up 3:45 est.

---

### Post by timlowell on 2008-09-28
Thanks.  I got the codecs file, but I'm still having problems getting the dependency files.  I guess I'll just have to wait until the server is more stable.

---

### Post by timlowell on 2008-09-28
OK, next question, where do I put the codecs file I downloaded so that the apt-get install process won't try to download it from medibuntu?

---

### Post by timlowell on 2008-09-28
I got it working!!!  Thanks for all the help.  Gotta love these forums.

---

### Post by steveneddy on 2008-09-28
Please mark this as solved.

:)

---

