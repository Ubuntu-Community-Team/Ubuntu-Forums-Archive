---
title: "Lightning as Default Calendar"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-06
is there a way to achieve this with oneiric?

---

### Post by kyleabaker on 2011-09-11
I'd like to help you, but I'm not familiar with the Calendar application Lightning. Do you have anymore details and a link?

---

### Post by walt.smith1960 on 2011-09-11
> **kyleabaker said:**
> I'd like to help you, but I'm not familiar with the Calendar application Lightning. Do you have anymore details and a link?

I think this is what alexvy13 is referring to:
[http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

---

### Post by kyleabaker on 2011-09-11
> **walt.smith1960 said:**
> I think this is what alexvy13 is referring to:
[http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

I think you're right. Not familiar with that client. o.O

---

### Post by effenberg0x0 on 2011-09-11
Well, I may have some partial input in this. Please keep in mind I am a locked away mental patient eventually allowed to use a PC. So it wouldn't be wise to try any of the following procedures.

**The Easy Part**
- Lightning is not compatible with Thunderbird 7.0. However, if you lurk to [http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/) , you can get a Lighning xpi file that does work with Thunderbird 7.0. Also get gdata-provider if you plan on using Google Services (tasks, etc).

- Go to Thunderbird / Tools / Addons / Install AddOn from file, install the xpi, restart Thunderbird. Great, you have a calendar. Yey.

**The Problem**
- Then you need to integrate it to the time/date thing in Ubuntu. You would need evolution-mirror to do that easily. It talks to evolution dataserver, even if you don't have evolution installed. That way, you will have it integrated with the clock/date thing. However, the official version of evolution-mirror at [https://addons.mozilla.org/af/thunderbird/addon/evolution-mirror/](https://addons.mozilla.org/af/thunderbird/addon/evolution-mirror/) won't work with Thunderbird 7.0 too. And I can't find any alpha/beta version of evolution-mirror anywhere. That's where I'm stuck.

If anyone has a tweak to make that work, even partially, I am very interested / willing to help debug it. I'm seriously considering making minor changes to evolution-mirror version restrains and giving it a go.

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by FishRCynic on 2011-09-13
> **effenberg0x0 said:**
>  However, if you lurk to [http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/) , you can get a Lighning xpi file that does work with Thunderbird 7.0. Also get gdata-provider if you plan on using Google Services (tasks, etc).

- Go to Thunderbird / Tools / Addons / Install AddOn from file, install the xpi, restart Thunderbird. Great, you have a calendar. Yey.



the link changes as per build created the link [http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/)  will get you to the directory above the directory (or folder if you prefer) to download the latest build

use at your own risk. (it worked for me)

---

### Post by pressureman on 2011-09-13
> **effenberg0x0 said:**
> - Lightning is not compatible with Thunderbird 7.0. However, if you lurk to [http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/tinderbox-builds/comm-beta/linux64-xpi-linux64/1315716041/) , you can get a Lighning xpi file that does work with Thunderbird 7.0. Also get gdata-provider if you plan on using Google Services (tasks, etc).

Actually it is compatible - I use it every day. The Oneiric Lightning packages were a little buggy recently on TB 7.0, but that was resolved by Chris Coulson (the package maintainer) and it's been smooth sailing since then.

---

### Post by effenberg0x0 on 2011-09-13
Cool, the TB + Lightning part is OK.

But I'm still stuck at part two. How to make evolution dataserver talk to Thunderbird 7. Once that is fixed, Thunderbird will be properly integrated. 

I can't find evolution-mirror development site / developer or an updated version. 

Regards,
Effenberg

---

### Post by EgoGratis on 2011-09-13
> **effenberg0x0 said:**
> Cool, the TB + Lightning part is OK.

But I'm still stuck at part two. How to make evolution dataserver talk to Thunderbird 7. Once that is fixed, Thunderbird will be properly integrated. 

I can't find evolution-mirror development site / developer or an updated version. 

Regards,
Effenberg

[http://mikeconley.ca/blog/2011/08/11/fiddling-with-an-eds-provider-for-lightning-calendar/](http://mikeconley.ca/blog/2011/08/11/fiddling-with-an-eds-provider-for-lightning-calendar/)

---

### Post by akai_kenshi on 2011-10-08
Am I to understand that Evolution was replaced by Thunderbird with no way to integrate a Lightning calendar into the desktop with the date/time applet?

That's rather vexing, and a regression I would say.

---

### Post by SushiR on 2011-10-08
Just this:
```
sudo apt-get install xul-ext-lightning
```
That's all, folks!

---

