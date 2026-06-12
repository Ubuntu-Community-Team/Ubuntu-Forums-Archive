---
title: "Tracking down Ubuntu problem (sys freeze)"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by wariskampar on 2008-09-26
I experienced system freeze occasionally since I the first time I use Ubuntu 4 month ago. I noticed this problem always happen when I want to watch movie in TOTEM (sometimes VLC). Today, I tried to track the problem using --debug option in Terminal. Even though I do not get system freeze but I find this error message:

(totem:8067): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

Does anyone knows what is that? DO you think my system freeze related to this error message?

---

### Post by phidia on 2008-09-26
There is a possibly related bug report [here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg962890.html"). It's a new bug report so you might check back there occasionally. 

There are also a lot of [hits]("http://www.google.com/search?q=GStreamer-CRITICAL+**%3A+gst_object_unref%3A+assertion+%60object+!%3D+NULL%27+failed&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") from this string: 

"GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed" 
but weeding through them is going to be time consuming.

---

### Post by emperor on 2008-09-30
> **wariskampar said:**
> I experienced system freeze occasionally since I the first time I use Ubuntu 4 month ago. I noticed this problem always happen when I want to watch movie in TOTEM (sometimes VLC). Today, I tried to track the problem using --debug option in Terminal. Even though I do not get system freeze but I find this error message:

(totem:8067): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

Does anyone knows what is that? DO you think my system freeze related to this error message?

Do you have gstreamer0.10-pitfdll and w32codecs installed?

---

