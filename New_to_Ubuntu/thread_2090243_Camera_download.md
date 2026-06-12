---
title: "Camera download"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by mike acker on 2012-12-01
how do i designate which app should open when I connect my Camera?

I want it to activate Gwenview but it activates Shotwell :confused:

---

### Post by mikewhatever on 2012-12-01
You can select it in System Settings->Details->Removable Media.

---

### Post by mike acker on 2012-12-01
> **mikewhatever said:**
> You can select it in System Settings->Details->Removable Media.

cool . that seems to work .

i have set it to DO NOTHING as to this point I have not found a camera down-loader that I like...  

so far everything i've tried attempts to process everything on the camera card -- which is a waste of time -- i have 977 images on camera right now 976 of which have already been downloaded . 

and no: we don't delete images off the camera after download .

hopefully i can figure out where it mounts the camera so i can do the download using Krusader just based on shoot date

---

### Post by mikewhatever on 2012-12-02
Running **df -h | grep ^/** in a terminal window should show where everything is mounted.

---

### Post by Wim Sturkenboom on 2012-12-02
> **mikewhatever said:**
> Running **df -h | grep ^/** in a terminal window should show where everything is mounted.

I guess mount will also do the trick ;)

// Edit
Ah, I see; your command cleans up irrelevant stuff; clever :)

---

