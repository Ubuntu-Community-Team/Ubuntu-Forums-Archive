---
title: "How do you reduce an ISO image size to burn onto a DVD???"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-16
Ubunterso,

I have a collection of family videos that I want to burn onto a DVD. When I right clicked on the folder they are in it says size is 4.0 GB.

I use DeVeDe to produce an ISO image to burn to DVD.

When the image creation process was over, DeVeDe creaded an ISO image that was 14.3 GB! Wow....

So I can't burn this to a Single (just 1) DVD......

Who out there can tell me what I need to do to make this happen? Meaning everything to only 1 DVD!!!

Thanks! Very Much!

P.S. Files in folder are avi format

---

### Post by binbash on 2008-11-16
you can click adjust disk usage BUT it will loose a lot of quality.WHen adding the video navigate to advance options , disable ac3 sound, reducing final size also make it smaller.After that click adjust disk usage.


OR

You can split the video before adding to devede and you can create 2 dvds with better quality

---

### Post by Steve1961 on 2008-11-16
You could also try using k9copy which should shrink the iso to a standard dvd size

---

### Post by suomalainen on 2008-11-16
I don't have k9copy. If I were to install it how would the process look exactly?

Thanks

---

### Post by binbash on 2008-11-16
I dont think k9copy will work for shrinking at this case because you dont have a dvd structure.THO i didnt use k9copy since i dont have kde installed.

---

### Post by suomalainen on 2008-11-16
> **binbash said:**
> you can click adjust disk usage BUT it will loose a lot of quality.WHen adding the video navigate to advance options , disable ac3 sound, reducing final size also make it smaller.After that click adjust disk usage.


I cannot see "AFTER THAT CLICK ADJUST DISK USAGE". Where is this feature????

---

### Post by Steve1961 on 2008-11-16
I'm not in front of my main computer now so this is from memory.  Just launch k9copy and open the iso - I think it can read direct from an iso, but if not also install gmountiso.  Then select the full dvd and hit the backup button.  That's basically it.  here's alink:

[http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/)

---

### Post by binbash on 2008-11-16
image : 

[http://img393.imageshack.us/img393/2820/test1am2.png](http://img393.imageshack.us/img393/2820/test1am2.png)

---

### Post by suomalainen on 2008-11-16
Steve1961,

The link you sent me containing the instructions states the following:

"Keep in mind that after creating a DVD, k9copy will not remove the temporary files, so remember to remove them manually."

Do you know where these temporary files are located???

Thanks again.

---

### Post by Steve1961 on 2008-11-16
> **suomalainen said:**
> Steve1961,

The link you sent me containing the instructions states the following:

"Keep in mind that after creating a DVD, k9copy will not remove the temporary files, so remember to remove them manually."

Do you know where these temporary files are located???

Thanks again.

By default I think they're created in ~/k9copy but check in the options menu to make sure.  Basically it creates a dvd folder that needs to be deleted once you've finished.

---

### Post by Efros on 2008-11-16
I would mount the iso and then use dvdshrink under wine, works flawlessly.

---

### Post by Steve1961 on 2008-11-16
> **Efros said:**
> I would mount the iso and then use dvdshrink under wine, works flawlessly.

shouldn't need to mount the iso, and I've found that k9copy has now reached a stage of maturity where I would rate it as much better and more reliable than dvdshrink - which is no longer being developed.  In fact, the reason I moved to k9copy about 6 months ago was because dvdshrink had issues the encryption of some DVDs

---

### Post by suomalainen on 2008-11-16
Steve1961,

Sorry for this rather stupid question but I cannot find the file/folder where K9Copy is located.

Would you mind showing me.... Sorry.....

---

### Post by suomalainen on 2008-11-16
P.S.

Steve1961,

Are we talking about "Output Directory" here???

If so, I created it on my desktop, for easy removal....

See attach.

---

### Post by Steve1961 on 2008-11-16
> **suomalainen said:**
> P.S.

Steve1961,

Are we talking about "Output Directory" here???

If so, I created it on my desktop, for easy removal....

See attach.


Yep, that's the one.

---

### Post by Efros on 2008-11-16
Had a quick rifle through k9copy looks pretty good, dvdshrink would still have worked and as the query was about home videos encryption wouldn't have been an issue. Still next time I have an iso or a dvd to be copied I'll give k9copy a whirl.

---

