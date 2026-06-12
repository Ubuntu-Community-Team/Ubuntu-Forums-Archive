---
title: "Audacious Plays Nothing"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by UserDemos on 2008-05-28
Hello everyone,

I've been using Ubuntu since 7.10 and have had no issue what so ever, even into 8.04, but suddenly, today, Audacious stopped playing anything what-so-ever. I clean re-installed using the --purge command when uninstalling first. Still nothing. Won't even play the files. Doesn't tell me how long they are, or displays 0:00, doesn't play anything, no sound of any kind either.

Everything else works: Audacity, VLC, MPlayer, etc. My Audigy card works with all of those programs as well. I've messed with the settings under Sound and tried several other fixes. Nothing.

Does anyone have any ideas? I'd really appreciate all the help I can get. Thank you all in advance. - Dimitre

---

### Post by diablo75 on 2008-05-28
> **UserDemos said:**
> Hello everyone,

I've been using Ubuntu since 7.10 and have had no issue what so ever, even into 8.04, but suddenly, today, Audacious stopped playing anything what-so-ever. I clean re-installed using the --purge command when uninstalling first. Still nothing. Won't even play the files. Doesn't tell me how long they are, or displays 0:00, doesn't play anything, no sound of any kind either.

Everything else works: Audacity, VLC, MPlayer, etc. My Audigy card works with all of those programs as well. I've messed with the settings under Sound and tried several other fixes. Nothing.

Does anyone have any ideas? I'd really appreciate all the help I can get. Thank you all in advance. - Dimitre

I've had some problems myself and am still working through them.  On my end, the problems I'm having are with applications that point their output sound towards ALSA, instead of Pulse Audio.  Are there advanced settings within Audacious you could modify to point the sound out towards another sound engine (preferably, Pulse Audio in this case)?

Also, check your volume levels.  I know you've probably not touched them, but I just discovered one of my PCM levels muted, which may have caused other things on my system to suddenly "break".

---

### Post by UserDemos on 2008-05-28
Thank you for the reply, but unfortunately, I think the problem is not with ALSA. Audacious was working with ALSA always.

I tried many files and they all display 0:00 as their time. It might be some codec problem, but I've looked and all seem to be installed correctly and working.

EDIT: Checked sound levels. No problems there. 

Any other ideas? - Dimitre

---

### Post by UserDemos on 2008-05-29
Anyone have any other ideas? Even a clean reinstall does not solve the problem. Audacious tells me that all my files are 0:00 long. I think it's a codec issue, but have no ideas where to go from here.

Anyone? - Dimitre

---

### Post by quelx on 2008-05-30
did you install **audacious-plugins**?

```
sudo apt-get install audacious-plugins
```

---

### Post by Speff on 2008-06-09
I gotta bring this back, I'm having the same problem as OP. I tried installing audacious-plugins, but it says its alread installed. I tried a clean install again but no dice, still not working

---

### Post by Speff on 2008-06-10
Bump, still not fixed. A note about this problem: when I run audacious from the command line, nothing is wrong with the output. When it comes to the point where I press 'play' it just acts as if I didnt do anything

---

### Post by philinux on 2008-06-10
This might help.
[http://www.linuxquestions.org/questions/slackware-14/audacious-wont-play-after-updating-to-12.1-645858/?](http://www.linuxquestions.org/questions/slackware-14/audacious-wont-play-after-updating-to-12.1-645858/?)

---

### Post by ImpressMe on 2008-06-10
> **UserDemos said:**
> Thank you for the reply, but unfortunately, I think the problem is not with ALSA. Audacious was working with ALSA always.

I tried many files and they all display 0:00 as their time. It might be some codec problem, but I've looked and all seem to be installed correctly and working.

EDIT: Checked sound levels. No problems there. 

Any other ideas? - Dimitre

Did you *try* his advice? I had this problem, switched from Autodetect to ALSA and it worked. Monkey around and see if switching settings away from ALSA to something else helps.

---

### Post by Speff on 2008-06-10
>  Originally Posted by Takla  View Post
I had exactly this problem in Debian Lenny (32 bit) after an upgrade of audacious. I deleted the audacious config in ~/.config/audacious and then it worked fine.

I found that this solution solved my problem. philinux, thanks alot for the link :)

---

### Post by UserDemos on 2008-08-07
Sorry for the late reply, but I work in theatre and tend to disappear for months at a time. Months later, I finally got around to playing with Audacious.

Thank you to Impress Me, philinux, and diablo75! It seemed to be a combination of problems from the upgrade. I deleted the ./config/audacious file, changed to ALSA from Default, and had to check the "detect file formats by extension" box. Problem solved somewhere along that path.

The help was sincerely appreciated! With a community like this, why would I ever consider going back! - Dimitre

---

