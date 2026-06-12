---
title: "Youtube Videos"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by jonathan71381 on 2014-04-18
Okay, so I downloaded Ubuntu 14.04 and love it so far, but it tells me to update adobe flash to watch a youtube video.  I downloaded from the site, but it did not work.  I am continually being told to update adobe flash.  Does anyone know what to do?

---

### Post by monkeybrain20122 on 2014-04-18
Don't download from  Adobe's site. In Ubuntu install most things from the repository. Just install ubuntu-restricted-extras, that will install flash and other media codecs.

---

### Post by Christopher on 2014-04-18
> **jonathan71381 said:**
> Okay, so I downloaded Ubuntu 14.04 and love it so far, but it tells me to update adobe flash to watch a youtube video.  I downloaded from the site, but it did not work.  I am continually being told to update adobe flash.  Does anyone know what to do?

This helped me.

[http://ubuntuforums.org/showthread.php?t=2216082#top]("http://ubuntuforums.org/showthread.php?t=2216082#top")

---

### Post by andrew.46 on 2014-04-19
And for an easier way to view YouTube videos (no advertising, no crazy comments etc) have a look at smtube...

---

### Post by buzzingrobot on 2014-04-19
> **jonathan71381 said:**
> Okay, so I downloaded Ubuntu 14.04 and love it so far, but it tells me to update adobe flash to watch a youtube video.  I downloaded from the site, but it did not work. 

That's the browser producing the 'update Flash' notices. 

Linux distributions, including Ubuntu, maintain software packages intended for installation on that distribution on servers called repositories.  Those packges will be installed correctly on your system. Differences do exist between different Linux distributions.  Software offered directly for download by a vendor -- Flash in this case -- does not account for those difference and is often not packaged for any specific distribution, but simply provided as an archive, leaving it up to the user to manually put all the pieces in the correct places.

---

