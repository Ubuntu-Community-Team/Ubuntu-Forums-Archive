---
title: "Bandwidth throttling for downloads"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by frimilden on 2008-08-24
Is there any way to throttle bandwidth while downloading? I mainly download from usenet and use hellanzb but the Bandwidth throttling that hella offers is not true throttling it only stops the download for X amount of time then continues, I am after something that will allow me to specify X amount of KB/s for the duration of my downloading and actually only allows that amount instead of stoping to 0 then continuing a few seconds later for a minute then back to 0 and so on, if you get what I mean? 

I am using Ubuntu 8.04.

---

### Post by gmoney on 2008-08-29
I wouldn't consider myself an expert on bandwidth throttling per se, but I did just watch a video on the topic yesterday.  Here's a link:

[http://revision3.com/tekzilla/willitboot/](http://revision3.com/tekzilla/willitboot/)

The stuff on bandwidth throttling starts at around 1 min 5 seconds into the video.

You can throttle bandwidth through your router, as well as through stand alone applications.  Depending on what type of router you have (specifically it has to have QOS [Quality of Service] settings), you can throttle upstream bandwidth, device priority, ethernet priority, and software application priority.

I've personally never tried any applications for bandwidth throttling, but if you'd like a good place to see some applications for linux, check out the "external links" section of this Wikipedia entry:

[http://en.wikipedia.org/wiki/Bandwidth_throttling](http://en.wikipedia.org/wiki/Bandwidth_throttling)

---

### Post by Boozkachu on 2008-12-17
Try trickle.

```
sudo apt-get install trickle
```

To throttle PAN newsreader to 1000kbps you simply do

```
trickle -s -d 1000 pan
```

---

### Post by mangurt on 2008-12-17
I don't know if this will help you out, but you can use SABnzbd ([www.sabnzbd.org](www.sabnzbd.org))  It's pretty much like hellanzb, but uses firefox as an interface.  You can set the bandwidth limit in SABnzbd to limit your bandwidth (I usually have mine set to 175K/sec so my wife doesn't get mad that the internet is slow.

---

### Post by newbuntuxx on 2008-12-17
Its best to use your router for this stuff. What type of router do you have? You can install this firmware to have more control over your router: [www.dd-wrt.com](www.dd-wrt.com) (i hope your router is supported)

---

### Post by madmak on 2008-12-18
Iv been searching for a way to do this aswell because im using my mobile as a modem and as soon as i start to download a file in firefox it takes ages to load any pages because the download is using all my bandwidth speed the whole 46KB/sec lol i usualy end up leaving the pc till the downloads finished but it would be nice if i could control my download speed so i could still browse, i did find an addon for firefox called "Firefox Throttle" but its only supported by wind0wz

---

### Post by frimilden on 2009-06-25
> **frimilden said:**
> Is there any way to throttle bandwidth while downloading? I mainly download from usenet and use hellanzb but the Bandwidth throttling that hella offers is not true throttling it only stops the download for X amount of time then continues, I am after something that will allow me to specify X amount of KB/s for the duration of my downloading and actually only allows that amount instead of stoping to 0 then continuing a few seconds later for a minute then back to 0 and so on, if you get what I mean? 

I am using Ubuntu 8.04.

Another age old bump....

[Sabnzbd+]("http://www.sabnzbd.org/") does this and so very much more. For anyone that has/had the same problem I did then this is for sure the absolute route to take to fix the issue and also get a client that blows hellanzb out of the water (no offense to the Hellanzb fans out there). 

Sabnzbdplus has a great community. much like this fine Ubuntu community that is very active. They are very active in creating user scripts and these scripts are great. They also are there to answer and help with any and all questions rather sharpish. So for anyone that is looking for a great Usenet client that has all the features and then some than check this one out. :popcorn:

If I am not mistaken it can also be found in the repos and installed from there. Do check out all the nice skins as well :KS

---

