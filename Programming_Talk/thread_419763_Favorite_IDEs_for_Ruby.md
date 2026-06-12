---
title: "Favorite IDEs for Ruby?"
date: 2007-04-23
forum: Programming Talk
---

### Post by Ubuntist on 2007-04-23
Subject says all.

---

### Post by DC@DR on 2007-04-23
There're quite a few Eclipse-based IDE for Ruby development, such as: RDT, Radrails...Just google around and you'll find it :-)

---

### Post by rekahsoft on 2007-04-23
check out the the netbeans ruby modules...they are still in development but they are looking good...

---

### Post by caLt on 2007-04-23
> **rekahsoft said:**
> check out the the netbeans ruby modules...they are still in development but they are looking good...

I agree.

Check out [_this page_]("http://blogs.sun.com/tor/category/Ruby") for some of its features.

---

### Post by Ubuntist on 2007-04-24
Thanks, everybody.

I've tried to install netbeans from Synaptic.  Part way through, I get a message saying
> This package is an installer package, it does not actually contain the
NetBeans IDE.  You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
[http://www.netbeans.info/downloads/all.php?b_id=2323](http://www.netbeans.info/downloads/all.php?b_id=2323) 

Select the English(en) tgz Download Archive Distribution 82.8 MB
[http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1](http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1)

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort]As instructed, I download the tgz file and put it in /tmp with root.root ownership:
> /tmp$ ls -l net*
-rwxrwxrwx 1 root root 86781802 2007-04-24 12:59 netbeans-5.5.tar.gz
and then hit return in the Synaptic window.  But Synaptic keeps throwing the same message back at me.

If I close Synaptic and restart it, it claims that netbeans is installed, yet typing `netbeans' at a command prompt doesn't work:
> /tmp$ netbeans
The program 'netbeans' is currently not installed.  You can install it by typing:
sudo apt-get install netbeans5.5
Make sure you have the 'multiverse' component enabled
bash: netbeans: command not found
And, yes, the multiverse is enabled.

Any ideas?

---

### Post by desheikh on 2007-04-24
Hi,

If you want ruby support you need the netbeans 6 preview
[http://wiki.netbeans.org/wiki/view/MilestoneDownloads]("http://wiki.netbeans.org/wiki/view/MilestoneDownloads")

Have installed but havnt tested yet thought reviews seem good! 
Another popular ide is radrails, which is what i usually use.

---

### Post by the.dark.lord on 2007-04-26
If you use OS X, you might consider using Smultron. It's one of the best IDEs I've seen to date.

[http://smultron.sourceforge.net](http://smultron.sourceforge.net)

---

### Post by emperon on 2007-04-26
I am using Vim with rails plugin. It is really nice if you can use vim  (and you should use vim so that your coding will be much faster)

---

