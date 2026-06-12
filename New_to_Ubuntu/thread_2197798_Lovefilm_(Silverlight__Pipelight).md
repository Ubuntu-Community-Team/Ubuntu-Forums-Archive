---
title: "Lovefilm (Silverlight / Pipelight)"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by teresa_maude on 2014-01-05
Hi All,

I am new to Ubuntu have loaded it onto an old PC as a dual boot. I am about to build a media PC for my lounge and was hoping to load Ubuntu but I can't get Lovefilm to work. I've searched the forum but a lot of the posts seem quite old. Is there any way to get lovefilm to work?

Sorry if I've missed the answer elsewhere, thanks in advance.

---

### Post by monkeybrain20122 on 2014-01-05
Don't know what lovefilm is, so googled "lovefilm Ubuntu" some old threads came up. Apparently the problem is that silverlight doesn't work in Linux.

So piplelight should work. It works for Netflix.
[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by sammiev on 2014-01-05
Is [this]("http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html") what you are looking for?

---

### Post by Bucky Ball on 2014-01-05
> **sammiev said:**
> Is [this]("http://http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html") what you are looking for?

I'm getting the old 'server not found' at that link ...

---

### Post by monkeybrain20122 on 2014-01-05
sammiev

Your link 404. 

You meant [http://www.omgubuntu.co.uk/2013/01/how-to-watch-lovefilm-redbox-instant-or-netflix-on-ubuntu](http://www.omgubuntu.co.uk/2013/01/how-to-watch-lovefilm-redbox-instant-or-netflix-on-ubuntu)
But that is old. Instead of installing a seperate desktop app for each (basically a Windows version of Firefox running in wine) pipelight should work for all of them in a native Linux browser (Firefox or Chrome)

---

### Post by uRock on 2014-01-05
The link has an extra http in it. [http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html](http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html)

---

### Post by SeijiSensei on 2014-01-05
sammiev left the colon out after http.  [That link]("http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html") points to a different solution, one similar to netflix-desktop which uses WINE to run a browser with Silverlight installed.

Lovefilm is Amazon's UK service.  I haven't yet tried pipelight as a solution for Amazon Instant.  [I haven't had much success]("http://ubuntuforums.org/showthread.php?t=2181765") using hal for Instant any more either.  If pipelight works for Amazon Instant, it probably works for Lovefilm as well.  However I don't think Amazon uses Silverlight for DRM purposes, so it may not help for Lovefilm.

---

### Post by monkeybrain20122 on 2014-01-05
> **SeijiSensei said:**
> 
Lovefilm is Amazon's UK service.  I haven't yet tried pipelight as a solution for Amazon Instant.  [I haven't had much success]("http://ubuntuforums.org/showthread.php?t=2181765") using hal for Instant any more either.  If pipelight works for Amazon Instant, it probably works for Lovefilm as well.  However I don't think Amazon uses Silverlight for DRM purposes, so it may not help for Lovefilm.

If it is not silverlight it is probably flash with drm. Pipelight lets you install Windows flash so it will probably work too.
[http://fds-team.de/cms/pipelight-installation.html#section_2_3](http://fds-team.de/cms/pipelight-installation.html#section_2_3)

Since Windows flash in wine loads slower than the native Linux version and something don't work (like some buttons) it is good to be able to enable it only when needed and use native flash otherwise. The easiest way to implement the switching for Firefox would be to use galternatives (in the repo) (a gui for update-alternatives)

P.S. You may also need to get a user agent switcher for the browser.

---

### Post by SeijiSensei on 2014-01-05
I just installed pipelight with only Silverlight added and was able to watch a movie at Amazon Instant.  Hooray!  I thought about installing Flash for Windows, since it is being maintained while the Linux version is not, but I wondered how updates are handled.  It doesn't appear to be required for Amazon, though.

I didn't have to change my User Agent string either.

This is using a puny Atom 330, though the machine has NVIDIA Ion graphics, and my Flash player has hardware acceleration enabled.  From this description of pipelight [on the webupd8 page]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html"), I'm guessing the acceleration works with Silverlight-protected media as well:

> When you open a page with a Silverlight application the library will send all commands from the browser through a pipe to the Windows process and act like a bridge between your browser and Silverlight. The used pipes do not have any big impact on the speed of the rendered video since all the video and audio data is not sen[t] through the pipe. Only the initialization parameters and (sometimes) the network traffic is sen[t] through them.

---

### Post by sammiev on 2014-01-05
> **SeijiSensei said:**
> sammiev left the colon out after http.  [That link]("http://www.webupd8.org/2013/01/watch-lovefilm-and-redbox-videos-in.html") points to a different solution, one similar to netflix-desktop which uses WINE to run a browser with Silverlight installed.

Lovefilm is Amazon's UK service.  I haven't yet tried pipelight as a solution for Amazon Instant.  [I haven't had much success]("http://ubuntuforums.org/showthread.php?t=2181765") using hal for Instant any more either.  If pipelight works for Amazon Instant, it probably works for Lovefilm as well.  However I don't think Amazon uses Silverlight for DRM purposes, so it may not help for Lovefilm.

Sorry, My bad. Should have caught that. :(

---

### Post by J_Me on 2014-01-05
Yep lovefilm works, I followed this [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html) Also I needed to install UAControl(for firefox) and added a user agent to the custom panel. Great work guys

---

### Post by teresa_maude on 2014-01-16
Hi all,

Sorry about the delay been snowed under with work & only just had a chance to try all your suggestions. THANK YOU finally got it working.:) You are all wonderful!

---

### Post by oldos2er on 2014-01-16
Would you please mark the thread 'Solved' under Thread Tools? Thanks!

---

### Post by krainey2106 on 2014-01-16
re: Netflix and Silverlight/Pipelight, I have tried the procedure in WEB UPD8 several times and it hangs up, with assorted kinds of error messages or just a freeze.  I suspect some kind of conflict with older versions (Netflix worked for me under 13.04).  Can anyone suggest a way of cleaning out the old conflicting installs and getting a clean start?

Thanks
KDR

---

### Post by krainey2106 on 2014-01-16
Re: Netflix and Silverlight/Pipelight, based on the comment below, I tried watching a film on Amazon.  It works, but Netflix does not.  Any clues?

Thanks,
KDR

---

### Post by monkeybrain20122 on 2014-01-16
> **krainey2106 said:**
> re: Netflix and Silverlight/Pipelight, I have tried the procedure in WEB UPD8 several times and it hangs up, with assorted kinds of error messages or just a freeze.  I suspect some kind of conflict with older versions (Netflix worked for me under 13.04).  Can anyone suggest a way of cleaning out the old conflicting installs and getting a clean start?

Thanks
KDR

Close all your browsers.

```
pipelight-plugin --disable silverlight
```

If you have used sudo to enable it, use sudo as well to disable it.

and then 

remove the folder .wine-pipelight

and then

```
pipelight-plugin --enable silverlight
```

---

### Post by krainey2106 on 2014-01-24
[monkeybrain20122]("http://ubuntuforums.org/member.php?u=1843403"), Thank you!!  The above recommended sequence worked for me to enable Netflix viewing in FireFox, but, so far, not in Chrome.  I still have not been able to get Xfinity to work using flash (see my latest post on global frustration with video providers).  Again, thank you for the Netflix silverlight help.

---

### Post by monkeybrain20122 on 2014-01-24
> **krainey2106 said:**
> [monkeybrain20122]("http://ubuntuforums.org/member.php?u=1843403"), Thank you!!  The above recommended sequence worked for me to enable Netflix viewing in FireFox, but, so far, not in Chrome.  I still have not been able to get Xfinity to work using flash (see my latest post on global frustration with video providers).  Again, thank you for the Netflix silverlight help.

Never mind Chrome, it won't work after April anyway as google is going to drop support to ALL NNAPI plugins for Linux on Chrome/Chromium after April (so nothing but pepper flash will work after that, by "nothing" I mean even quicktime, windows media plugin etc)

---

### Post by krainey2106 on 2014-01-25
Thank you again monkeybrain20122!  I did get Crome to work for Xfinity using the WEB UPD8 procedure for flash; still now luck with Firefox and Xfinity.  ButI have been ready to drop chrome/chromium anyway because it dropped igoogle and the search engine is just a vending machine at this point.  Any recommendations for bowsers?  Is Firefox all alone?

---

