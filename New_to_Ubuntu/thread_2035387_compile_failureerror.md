---
title: "compile failure/error"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by oscillator on 2012-07-30
[http://pastebin.com/iLvUtTwy](http://pastebin.com/iLvUtTwy)

I've just tried to compile xchat after running the ./configure command, and got some funky errors, which can be viewed in the link above (you need to scroll to the bottom to see the errors). 
If anyone could help with this I would be very grateful, as I know I could just download this via the repos or software centre.

Thanks.

---

### Post by kd5mkv on 2012-07-30
You can try this site:
[http://www.linuxfromscratch.org/blfs/view/cvs/xsoft/xchat.html](http://www.linuxfromscratch.org/blfs/view/cvs/xsoft/xchat.html)

something about patch, but I would try the required libraries first.
Your missing something to complete compiling. goodluck!

---

### Post by oscillator on 2012-07-30
Hmm  I can't install GLib-2.32.4 as it doesn't seem to exist, lower case form brings up no results from pressing tabs twice either. I have no idea how to install the patch either if I need to as it just link to a html page, would I need to right click and save as etc?

---

### Post by oscillator on 2012-07-30
Actually I think I'm just gonna leave this compiling business alone and install xchat from the repositories, do I need to do 'purge xchat.....' or something to delete all the things I've made from the ./configure command?

---

### Post by kd5mkv on 2012-07-30
I have tired those type lib before and it is like falling dominos, maybe the repository version would get you moving? I have gotten things from Debian packages, usually stable works. Or launchpad PPA may have a newer
version in deb. file.

---

### Post by kd5mkv on 2012-07-30
If your compile failed dont worry. The repo version will open every time.

---

### Post by oldos2er on 2012-07-30
> **oscillator said:**
> [http://pastebin.com/iLvUtTwy](http://pastebin.com/iLvUtTwy)

I've just tried to compile xchat after running the ./configure command, and got some funky errors, which can be viewed in the link above (you need to scroll to the bottom to see the errors). 
If anyone could help with this I would be very grateful, as I know I could just download this via the repos or software centre.

Thanks.

I get a blank page when clicking your pastebin link.

Assuming you're missing some dependencies, try running ```
sudo apt-get build-dep xchat
``` first.

---

