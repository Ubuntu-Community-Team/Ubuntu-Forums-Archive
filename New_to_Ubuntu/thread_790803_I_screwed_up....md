---
title: "I screwed up..."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by TheBluntNinja on 2008-05-11
Ok, my hard drive died last week, and I decided instead of going back to windows, I'd try out Ubuntu.  I heard about beryl, and wanted to install that.  Well, I did, but I was unable to activate my desktop effects.  I decided to follow this little tutorial, and at the point where it tells me to reboot is where (after I rebooted), I can't load anything graphical.  Ubuntu looks like it's loading, and then all of a sudden my screen turns off (I'm on a laptop).  Is there anything anyone can do to help me?  It's kind of important, as I'm a student at the end of a semester with 2 papers I wrote on Open Office on that computer...

---

### Post by nynoah on 2008-05-11
do you have a live cd?  If so, boot up under the live cd.  Then copy your paper from the mounted hard drive to a flash drive.  After that is done and your important file like that is safe then we can start on the rest.

---

### Post by TheBluntNinja on 2008-05-11
Alright, I did that.  I'm on the Live CD right now.

---

### Post by nynoah on 2008-05-11
so you backed up your school work correct.  Are there any other files that are needed too?  If so back them up too.  You will not be able to use your disk drive because it locks the Ubuntu disk in it while you are on the live cd.  So you need an external HD or flash drive.

---

### Post by TheBluntNinja on 2008-05-11
Yup, I did what you said-- backed up my important files.  Everything left is settings and games (which I kind of want to get rid of, anyway).

---

### Post by nynoah on 2008-05-11
Once that is done, start doing this.

when you are logging in. Get into your grub menu and type this into it.

sudo dpkg-reconfigure xserver-xorg

then set your driver to vesa. Go through all the promts and just agree with them all and reboot. This should get you back to a generic driver. When that is done and you are back on your desktop, then you can activate your proprietary graphics drivers again.

---

### Post by lswest on 2008-05-11
Also, you installed Beryl? that project was merged with compiz to form compiz-fusion and comes pre-installed in Ubuntu as of 7.10, so if you tried installing beryl, i'd suggest a fresh install, and then set up your graphics drivers (if you need any) then just enable desktop effects under the "visual effects" tab of your appearance settings (system-->preferences-->appearance)

---

### Post by TheBluntNinja on 2008-05-11
Yeah, that's actually what I did at first.  I was getting the error "Desktop Effects Could Not Be Enabled," which is why I went to follow the instructions on that tutorial.

---

### Post by nynoah on 2008-05-11
always download everything that you can from synaptic.  Because if it comes from synaptic, it is meant to work on your computer correctly.

---

### Post by TheBluntNinja on 2008-05-11
Wow, thank you so much!  It worked just as you said it would.  I am very relieved, and will hesitate to do anything in the future if I don't know what I'm doing.  That brings me to my next thing... are there any good books you would suggest on beginning to use Linux?  I went to my campus's bookstore, and all I could find were some incredibly dense $40 books that when I opened already soared way above my head.  Thanks, again!

---

### Post by tylermoody on 2008-05-11
You don't need a book to learn linux. The books you'll find in a Barnes & Noble or Borders are out-of-date before they hit the shelves. Read the forums here and learn about the parts of the system that interest you. Read through a set of instructions and google any of the commands you don't recognize. Go to a site like del.icio.us and search for 'linux beginner'. The results will have a lot of general information that other people have found useful.

---

