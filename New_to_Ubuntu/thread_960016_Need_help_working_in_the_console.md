---
title: "Need help working in the console"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by RLuck on 2008-10-27
:confused:Trying to set up compiz - this is what I get.  Looks simple.

> -desktop:/$ /usr/bin/compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image reens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.format
GConf backend: There is an ***unsupported value*** at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can contioue properly.


Just go into and delete the ***unsupported value*** But Bob can't seem to do it.

Can someone help - like 1, 2, 3, very simple steps 'babe in the woods'  on the console.

Thanks Bob

---

### Post by cdaringe on 2008-10-27
Hello

That's peculiar.  Oh well.  Let's try.

```
sudo gconf-editor

```

this opens the config editor.  i actually have an app link to it in my Application menu ->  System tools -> Config. Editor

Either way, the terminal command above should suffice.

Browse to the path as requested by your error.  Check your input in that field.  I attached a screenshot to show you what mine looks like.  you may want to replicate my duplicate value.

let me know how it works :)

---

### Post by RLuck on 2008-10-27
Thanks cdaringe  

I tried everything I could think of - but nothing seemed to clear the entry.the only thing showing is a pair of brackets  []   I tried deleting them, entering 0 and  'none'  -  no luck 

I'll lay that aside for now and return some other day  -  but without your post I doubt if I would have ever even found the 'unsupported value'  lol

Bob

---

### Post by cdaringe on 2008-11-04
hmmm...that really is bizarre.  did you install compizconfig settings manager (ccsm)?

---

