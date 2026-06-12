---
title: "Need Flash player plug in for Miro"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-07-16
I am running Ubuntu 12.04 on a 64 bit machine
I am also running Mira 5.0 to stream shows like Ted.com and Wimp.com
To accomplish this I am told that I need Flash for this
I apparently have flash as Veetle works fine on Firefox and it is indicated
as installed in the software centre.
Might it be just a function of Miro that it is not finding the plug-in
or do I need to download the plug-in again

Any help would be appreciated

---

### Post by bobsan on 2012-07-16
Sorry for the bad news According to this link Miro doesn't support flash in Linux.

[http://tinyurl.com/737ad7z](http://tinyurl.com/737ad7z)

But the thread is 2 year old, maybe there has been some recent changes, you may get more updated info from Miro's forum or mailing list. Good luck.

P.S. Maybe I am missing something, but you can watch ted.com and wimp.com just from the browser. Why use Miro for that?

---

### Post by Norman Thom on 2012-07-16
Bobsan:

Just to see if I can

---

### Post by Sealbhach on 2012-07-16
I found [this]("http://www.linuxquestions.org/questions/linux-newbie-8/has-anyone-been-able-to-get-flash-player-to-work-in-miro-945911/"), worth a try.

---

### Post by pqwoerituytrueiwoq on 2012-07-16
> **Sealbhach said:**
> I found [this]("http://www.linuxquestions.org/questions/linux-newbie-8/has-anyone-been-able-to-get-flash-player-to-work-in-miro-945911/"), worth a try.
based on what i see in that thread try this
```
sudo ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/
```

---

