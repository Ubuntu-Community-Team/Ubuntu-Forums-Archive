---
title: "[SOLVED] Flashing neo freerunner"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by tradet on 2008-10-06
Sigh. New to linux and ubuntu and now I want to flash the openmoko phone, turns out I "surprisingly" got stuck, fast.

Trying to follow [this guide]("http://wiki.openmoko.org/wiki/Flashing_the_Neo_FreeRunner"). I've downloaded [these files]("http://downloads.openmoko.org/releases/Om2008.9/") and [this]("http://wiki.openmoko.org/wiki/NeoTool") is probably a good idea. Turns out when I was supposed to [download]("http://users.on.net/~antisol/neotool") it I got sent to a page with the code to it. Not sure what to do so I opened gedit, pasted it there and saved it.

Now the first problem is: how shall I open the file? Doubleclick leaves nothing,
```
sudo ./neotool
```
or
```
sudo ./home/treeman/neo/neotool
```
where my file is located doesn't work.

Now I'm a bit scared of doing something wrong so I'm taking it slow...

Also I understand I should write a few lines when flashing.
```
dfu-util -a kernel -R -D /path/to/uImage
```
And then I'll just change to the files I want to flash with? It'll be a [few files]("http://downloads.openmoko.org/releases/Om2008.9/").

But if I should use the gui version of it, the NeoTool, what should I do then?

Hope I'm being clear enough, really appreciate some help here.

---

### Post by tradet on 2008-10-07
Anyone?

---

### Post by tradet on 2008-10-07
Ok nevermind I think I got it.
```
sudo chmod +x /file/path/neotool
```
To make executable, the tool did the rest.

---

