---
title: "Flash on Firefox on Wine"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by cshin9 on 2012-05-02
I installed Firefox on Wine and then installed Adobe Flash Player. It started crashing whenever I went to a site with flash content. Then I uninstalled Firefox then reinstalled it. The same thing happened. Is there a way to get Flash Player on Firefox on Wine without it crashing?

P.S. I have Flash on native Firefox, but I just want to see if I can do have it on Wine.

---

### Post by kimda on 2012-05-02
It could be the version you are installing, According to this page the latest flashplayer isn't very stable so I would install the previous version if you want to run it under Wine. 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3903](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3903)

If you really want to work with the Windows version of Firefox then you could also install Windows in a virtual machine on VirtualBox,.

---

### Post by lovinglinux on 2012-05-02
Type **about:config** in the address bar, then type **dom.ipc.plugins.enabled** in the filter, then double-click the resulting preference to make it false. Try to watch a video again.

Keep in mind you need to make sure the browser and ther plugin have the same architecture.

---

### Post by cshin9 on 2012-05-18
They are of the same architecture. It still keeps crashing, though, so I had to uninstall it again. YouTube videos work when I opt into the HTML5 beta, but some videos are still unavailable in WebM b/c they're commercial.

---

### Post by lovinglinux on 2012-05-19
> **cshin9 said:**
> They are of the same architecture. It still keeps crashing, though, so I had to uninstall it again. YouTube videos work when I opt into the HTML5 beta, but some videos are still unavailable in WebM b/c they're commercial.

If you are looking for a YouTube solution, get [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/), which I develop.

---

