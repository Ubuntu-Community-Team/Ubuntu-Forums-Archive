---
title: "FireFox 3 Problem"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by cerealtx on 2008-06-17
This has been happening since i can remember in 2, and now still in 3, i think it has 2 deal with flash, sometimes while surfing my browser will just randomly close, any ideas?

---

### Post by kool_kat_os on 2008-06-17
that shouldnt happen

---

### Post by RomeReactor on 2008-06-17
Hi. Try running it from the terminal (Aplications-Accessories->Terminal) and write or paste:
```
firefox
```
Then press ENTER; if it crashes, see if it leaves any error messages there and post them here.

---

### Post by ladr0n on 2008-06-17
Which flash plugin are you using?

---

### Post by cerealtx on 2008-06-17
(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7040): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

---

### Post by locosmurf on 2008-06-17
well the problem may or may not be due to flash. Firefox sometimes will crash when it encounters a website that it cannot support, mostly an IE only site. do you browse sites that may be IE only?

---

### Post by cerealtx on 2008-06-17
er, nah these sites should be fine, its mostly sites with lots of flash thats why i connected the 2, like Myspace, youtube, ect ect

---

### Post by schnauzer93 on 2008-06-17
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888)

I get this bug, too. From what I've researched, it seems to be an issue with Flash itself, not Firefox. Installing the beta of Flash 10 seems to help the problem, but it still crashes on occasion.

---

### Post by Watchtow3r on 2008-06-17
bump: I have the same problem. For me it's also when I do flash things, mostly when I click on a Youtube video. I read that this may be because I have 2 flash plugins that conflict with each other. Sure enough, when I type about:plugins into the firefox address bar, under Shockwave Flash, I see this:              

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type                  	Description 	       Suffixes	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

The only problem is that I think they're part of the same package. I can't delete one without deleting the other. So, this may or may not be the problem. Either way I'm not really sure what to do. I tried downloading the GNASH flash player instead, but that player is horrible and won't even show videos with it (when I use it and click on Youtube videos, all I see is a blank space). Any help?

---

### Post by Canis familiaris on 2008-06-17
I recommend you use Opera

---

### Post by RomeReactor on 2008-06-17
It seems the problem is related to a bug; see [this thread]("http://ubuntuforums.org/showthread.php?t=749465") for more information, and a possible workaround in the last two comments of the second page.

---

### Post by Watchtow3r on 2008-06-17
> **Anurag_panda said:**
> I recommend you use Opera

thanks for helping.

---

