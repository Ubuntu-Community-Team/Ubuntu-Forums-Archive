---
title: "flash wont work?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by runnerdi7 on 2008-05-09
I tried installing it as the instructions say, but nothing. any suggestions?  I had it working when i used linux a while ago, on this pc?

---

### Post by diablo75 on 2008-05-09
Well, we can't really tell you where you might have gone wrong without seeing the actual instructions you followed.... so here's some new ones:

Click Applications>Add/Remove

Change the filter to say "All Available Applications" and then search for "restricted".

Check off the Ubuntu Restricted Extras package, and then click apply.

This will also install Java, some MS-fonts, video codecs... probably a couple other knick-knacks I can't think of right now, but flash is included with this as well and that's all that really matters.

Let us know what happens!

:popcorn:

---

### Post by dorkdork777 on 2008-05-09
Your question is a little vague. What version of Ubuntu are you running? Which variant? (Ubuntu, Kubuntu, Xubuntu...?) What do you mean by 'nothing' - does it lock up? Does it refuse to install with an error message?

If the above instructions don't work, it would be helpful to know these things.

---

### Post by ubuntu-freak on 2008-05-09
> **runnerdi7 said:**
> I tried installing it as the instructions say, but nothing. any suggestions?  I had it working when i used linux a while ago, on this pc?

 
Execute this command in the Terminal:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
Then restart Firefox. Take a look at my [sticky](http://ubuntuforums.org/showthread.php?t=766683) also.
 
Nathan

---

### Post by Rick Z on 2008-05-09
what version of ubuntu are you running?  I believe on 7.10 and 8.04 you just need to enable the extra resportories (run apt-get update) and open up firefox and visit any site that needs the flash (youtube.com) and you should received a notification to install the add-on.  Next just follow the screen.

This might help.

[https://help.ubuntu.com/8.04/](https://help.ubuntu.com/8.04/)

---

### Post by runnerdi7 on 2008-05-09
the sudo line worked, thanks for the help!

---

### Post by ubuntu-freak on 2008-05-09
> **runnerdi7 said:**
> the sudo line worked, thanks for the help!

 
No problem. :-)

---

