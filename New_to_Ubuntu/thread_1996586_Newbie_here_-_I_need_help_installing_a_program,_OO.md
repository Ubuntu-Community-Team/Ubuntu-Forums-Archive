---
title: "Newbie here - I need help installing a program, OOF2."
date: 2012-06-04
forum: New to Ubuntu
---

### Post by bkama1 on 2012-06-04
Hi all, I hope I'm posting this in the appropriate place. I've been trying to get this program [OOF2]("http://www.ctcms.nist.gov/oof/") installed and working properly for the past few days. I've encountered many errors and between installing different packages and trying random stuff I've either fix most of the errors or made them worse.

I believe I've installed the program correctly and it builds and installs without any apparent errors but after trying to install the latest version of pygtk I get this message. 

"ImportError: No module named pygtk."

The full traceback is attached to this post. I'd just like to know what could be the possible problem. I downloaded pygtk-2.24.0 and followed the directions and installed it without any errors.

**Additional information:**

I have Ubuntu 12.04 LTS Installed. 

Link to prerequisites for this program: [http://www.ctcms.nist.gov/oof/oof2/index.html#requirements](http://www.ctcms.nist.gov/oof/oof2/index.html#requirements)

To install the prerequisites for this program they said to simply run these commands: 

   sudo apt-get remove graphicsmagick-libmagick-dev-compat    
sudo apt-get install python-gtk2-dev    
sudo apt-get install libgnomecanvas2-dev
sudo apt-get install libmagick++-dev    
sudo apt-get install liblapack-dev
[SIZE=2]
[/SIZE]These commands say that everything is fine and updated. I was still getting some other errors when running OOF2 so I though I'd try to install some of the packages individually. One of them being pygtk..now that's broken :( .

I'm really unfamiliar with installing stuff on Ubuntu. Any and all help would be appreciated!!!

---

### Post by Senior_Buckethead on 2012-06-04
hi there, 
when you open terminal and run the application from that, what error messages do you get?
You can copy and paste with your mouse the output and post it here.

---

### Post by bkama1 on 2012-06-05
Traceback (most recent call last):
  File "/usr/local/bin/oof2", line 38, in <module>
    oof.run()
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/oof.py", line 641, in run
    front_end(no_interp)  # all non-parallel menu items are executed here.
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/oof.py", line 357, in front_end
    import pygtk
ImportError: No module named pygtk

I realize that the problem is with my pygtk module. Not OOF itself. So I'm assuming I really messed up something when I attempted to update pygtk. I'm only guessing right now that python can't recognize pygtk for some reason? From my understanding a lot of things rely on pygtk so they wouldn't be working if it wasn't installed.

---

