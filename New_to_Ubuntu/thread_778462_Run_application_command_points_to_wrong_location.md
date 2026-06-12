---
title: "Run application command points to wrong location"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by PacifistWarMachine on 2008-05-02
I just installed MATLAB R12 for Linux and let the installer set up symbolic links. It must have got confused though because hitting alt-f2 and typing matlab gives the error:
> **"Could not open location 'file:///home/barker/matlab'**
The location or file could not be found.

Anyway it is supposed to run 'file:///usr/local/matlab7/bin/matlab', so how do I get the command matlab to point to the right location

thanks

---

### Post by Xiong Chiamiov on 2008-05-02
Do you know where the matlab bin file is?

Try creating a soft link from /usr/local/matlab... to /usr/bin, but name it, say, matlab2.  Then run that and see what happens.

---

### Post by PacifistWarMachine on 2008-05-02
Thanks, its all good now. I didnt realise ubuntu kepted all the links in /usr/bin.

---

### Post by Xiong Chiamiov on 2008-05-02
There are actually a few different locations for executables files like that.  /usr/bin and /usr/sbin are the ones that come to mind, but I can never remember them all.

Hmm, I think the other two are /usr/local/bin and /usr/local/sbin ?  It doesn't matter too much, as long as you know one.

---

