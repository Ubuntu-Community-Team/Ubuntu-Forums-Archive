---
title: "firefox upgrade gone slightly awry"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by mystmaiden on 2012-12-18
I had to break out my computer that is still running lucid while I do some repairs on my precise box but the firefox browser is so out of date that I downloaded and (sort of) installed firefox 17. Where I am now - I still have firefox 3.6 on applications but in my home directory is a firefox folder. If I open it I can run firefox 17 from there. I tried using the instructions I found online for putting an icon on the desktop but they did not work.

I do not have any particular need for ff 3.6 it can go if needs be. Is there any way to make ff 17 the default browser at this point?

I checked out the firefox mega thread but its...so mega!! I couldn't find the answer.

Also I did try to install firefox 12 using the instructions found in the beginning of the mega thread it went through all the steps and just aborted at the last one...

thanks
mystmaiden

---

### Post by snowpine on 2012-12-18
Run the update manager (or the terminal commands below) and you will get the current Firefox.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

reference: [http://packages.ubuntu.com/lucid/firefox](http://packages.ubuntu.com/lucid/firefox)

---

### Post by mystmaiden on 2012-12-19
Thank you, snowpine, for the reply.

I ran those two commands exactly just now but firefox did not change, nothing changed that I can see. Is there another step? Those two commands were also part of the original four commands I used to try and get firefox 12 working. I still have the ff 17 in my home directory, would just deleting that help?

Also I just discovered that even though I can run ff 17 from the file in my home folder, it will not stream videos. It just sits there or the video window disappears.

---

### Post by snowpine on 2012-12-19
The following commands will compare your installed Firefox version to the version(s) available in your software sources:

```
sudo apt-get update
apt-cache policy firefox
```

---

### Post by mystmaiden on 2012-12-19
```
mystmaiden@hal:~$ apt-cache policy firefox
firefox:
  Installed: 3.6.24+build2+nobinonly-0ubuntu0.10.04.1
  Candidate: 18.0~b4+build1-0ubuntu0.10.04.1~mfn1
  Version table:
     18.0~b4+build1-0ubuntu0.10.04.1~mfn1 0
        500 http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ lucid/main Packages
     17.0.1+build1-0ubuntu0.10.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
 *** 3.6.24+build2+nobinonly-0ubuntu0.10.04.1 0
        100 /var/lib/dpkg/status
     3.6.3+nobinonly-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ lucid/main Packages

```
Problem is, even 3.6.3 is too old a version to be helpful...

---

### Post by snowpine on 2012-12-19
Yes, but look carefully at the 'apt-cache policy firefox' results. You have 18.0 beta available because you have added the 'firefox-next' PPA (I do not recommend) and also 17.0 stable available through the official Ubuntu repositories.

I recommend that you remove the firefox-next from your software sources (IIRC in 10.04 this is under System, Administration, Software Sources), then:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

or if you don't want to do a full upgrade for whatever reason:

```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by mystmaiden on 2012-12-19
Thank you so much for the help, I did as you suggested and removed firefox next and was able to install ff 17. I don't seem to be able to stream videos on firefox now. Is this an issue others have had?

mystmaiden

---

### Post by snowpine on 2012-12-19
What format are the videos? If they are Adobe Flash then see here:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by mystmaiden on 2012-12-19
I can not stream any video at all at this point (youtube, hulu or dramafever. After searching around it looks like the combination of ff 17 and adobe 11 flash don't work with an older cpu. One source gives instructions to drop back to adobe 10 but I am pretty sure that won't work for my paid sites like dramafever and hulu. I'm wondering if I need to drop back to an older firefox instead - something between 3.6 and 17.

---

### Post by snowpine on 2012-12-19
Does your computer meet the hardware requirements for Adobe Flash Plugin?

[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

I am not an Ubuntu user but I have seen some "how to get flash working on old hardware" posts on these forums, if you look around a little. :) You can also (if possible) download the video to your hard drive first and then watch it with mplayer, that always gives me much better framerate than the streaming browser plugin on old hardware.

---

### Post by mystmaiden on 2012-12-19
Thanks for the replies, snowpine. I'm having more issues than just flash though. My system meets the requirements for flash just fine but I can not stream flash or any other video since the upgrade to firefox 17. I need to go back several rungs on the firefox ladder to get everything working again. I know that firefox 14 also does not work because I installed precise side by side with lucid and got the same results. Nor does dropping back to adobe 10 solve the issue.

---

### Post by snowpine on 2012-12-19
I'd suggest starting a new thread about the Flash problem, because we have some real Flash experts on these forums. (I personally avoid it like the plague ;))

There used to be a Firefox plugin called Flash Aid that helped with this but I'm not sure whether it is still being maintained these days.

---

### Post by vasa1 on 2012-12-19
> **snowpine said:**
> ...
There used to be a Firefox plugin called Flash Aid that helped with this but I'm not sure whether it is still being maintained these days.
[http://ubuntuforums.org/showpost.php?p=12178649&postcount=300](http://ubuntuforums.org/showpost.php?p=12178649&postcount=300)

---

