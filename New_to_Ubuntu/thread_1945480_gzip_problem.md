---
title: "gzip problem"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by jiangchongyi on 2012-03-23
Hello,everyone,
 
 
I failed to extract a tar.gz file . 
 
The system noted that :

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
 
How can I solve the problem?  Any hlep will be appreciated!

---

### Post by Kevin McCready on 2012-03-23
What are you actually trying to do? I've found I rarely need to unzip stuff, and if I do the file manager (I use Dolphin) does it for me.

If I'm trying to install new programs I use the terminal which I invoke by ctrl-alt-t, then 
```
sudo apt-get update
sudo apt-get install [the program I want]
```

I make sure Synaptic is closed and in fact I don't use Synaptic for installing new software.

Hope this helps.

---

