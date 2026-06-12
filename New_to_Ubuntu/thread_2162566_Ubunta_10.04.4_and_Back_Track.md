---
title: "Ubunta 10.04.4 and Back Track"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by JohnnyCod on 2013-07-15
I had to reinstall, Ubuntu told me that I had no more room on "/" partition.  Even though install recommended 10 GB, I put 15 GB - anyway, it would not let me update anything.
So..new problem, on [http://www.backtrack-linux.org/wiki/index.php/Install_OpenCL](http://www.backtrack-linux.org/wiki/index.php/Install_OpenCL), it wants me to 

wget [http://developer.amd.com/Downloads/AMD-APP-SDK-v2.5-lnx64.tgz](http://developer.amd.com/Downloads/AMD-APP-SDK-v2.5-lnx64.tgz)
after I get it..
I try:  tar -xvzf AMD-APP-SDK-v2.5-lnx64.tgz
I get:  gzip: stdin: not in gzip format
        tar: Child returned status 1
        tar: Exiting with failure status due to previous errors
So I am stuck here.
My other problem, seems like everything I update needs, The Social-Engineer Toolkit (SET), everything fails to install when it gets to the toolkit.
So I go to [https://www.trustedsec.com/january-2013/set-artillery-moving-github/](https://www.trustedsec.com/january-2013/set-artillery-moving-github/)
Tells me to do this...

For those using Back|Track:
 cd /pentest/exploits/set
svn update
./set
select option number 1

It fails at svn update.  I get:  Skipped '.'

One site suggested I was not in the correct directory, did a pwd and seemed like I was were I was supposed to be.

Been working on this for 2 days now.  New to Ubuntu, but I really want to learn Ubuntu and Back Track.  

Would really appreciate your expert help.  :)



[COLOR=#ff0000]

[/COLOR]

---

### Post by MoebusNet on 2013-07-15
I'm not an expert, but this may be one problem for you:

Ubuntu 10.04 reached End-of-Life status back in May 9, 2013.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

That may be why you are not getting updates which could lead to other problems. If you can do so, using 12.04 would provide support until April 2017.

If you become convinced that you absolutely must use 10.04, might it make more sense to use it in a virtual machine like VirtualBox? That way at least your base OS would receive security updates.

Just some observations, hope this helps.

---

### Post by dannyboy79 on 2013-07-15
if you want to install openCL in back track and or mess around with penetration testing then why not just install the latest and greatest? [http://www.backtrack-linux.org/backtrack/kali-linux-has-been-released/](http://www.backtrack-linux.org/backtrack/kali-linux-has-been-released/)

[http://www.kali.org/](http://www.kali.org/)

From the creators of BackTrack comes Kali Linux, the most advanced and versatile penetration testing distribution ever created.

---

### Post by oldos2er on 2013-07-15
For Backtrack support, see [http://forums.kali.org/](http://forums.kali.org/)

---

### Post by JohnnyCod on 2013-07-15
Thanx guys!  I did not know about Kali.  I am gonna give it a try.  Again, thanx for your patience with us newbies.  :)  How do I close out this thread?

---

### Post by oldos2er on 2013-07-16
You can mark the thread 'Solved' by following the instructions in my signature.

---

