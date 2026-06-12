---
title: "[SOLVED] /home partition - is it worth it?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-11-01
I've been thinking about moving my /home to it's own partition, but before I start this somewhat risky procedure, I want to know a little more about what the benefits are.

In the articles I've read, it always says that having a /home partition means that you can do a clean install instead of an upgrade without losing about losing your files or settings.  I understand that the files in the /home partition would still be there, but which settings exactly is it referring to?

I'm assuming that any extra packages that I have installed (games, XAMMP, AWN, VLC, etc.) would have to be installed again, and my settings for these packages would be lost.

Is there anyone who has done this and can give me a little clearer idea of the advantages?  I dual boot, would having a /home partition have any advantage over simply copying my /home folder to the windows partition, doing a clean install, and copying it back to the /home folder?

Thanks for your time.

---

### Post by JMorg on 2008-11-01
Well, I would personally say it's worth it mainly because of the file system security. It's a lot easier to back up /home if it has its own separate partition in my opinion, and if a portion of your file system goes down it's a lot easier to diagnose and restore rather than wiping the whole system because you have no other directory to fall back on. For example, I would recommend having a /(root), /home, and /var partitions for this very reason. But If you aren't worried about data loss or ease of backup then there would be no need I suppose :)

---

### Post by Cl0ud9 on 2008-11-01
Creating a seperate /home partition is simple. I used [this guide]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") and didn't run into any problems. 

Yes you would have to install all of your extra aps if you did a clean install, but you could always just upgrade. A big advantage is that you can boot multiple Linux distributions with all of them using the same /home. So you would have access to all of your files no matter what distribution you were using.

If you created a separate /home partition and did a clean install, you would not lose anything in /home.

---

### Post by Sealbhach on 2008-11-01
Yes definitely worth it. I upgraded to 8.10 and after I reinstalled Thunderbird all my emails were there, I didn't have to reconfigure the SMTP and POP etc. Definitely recommend it.


.

---

### Post by Pro-reason on 2008-11-01
I think it's worth setting up a separate /home partition if you are installing Ubuntu.  However, I don't think it's worth it if everything is already up and working.  If your current system is fine, just leave it.  It is not particularly hard to make a back-up of your home directory.

Open a terminal and type “ls -a ~”.  That will show you all the hidden directories and files that are currently in your home directory.  They contain your personal settings for your browser, your e-mail clients, your game scores, etc, etc.

---

### Post by tubasoldier on 2008-11-01
a separate /home partition is worth more than you could imagine.
Go for it. Make a backup first.

---

### Post by Mazza558 on 2008-11-01
Absolutely. A /home partition means you can reinstall as much as you want and still have all your documents ready to use.

---

### Post by bobpress on 2008-11-01
It is definitely worth it.  I have experimented with new releases or updates which break the graphic desktop.  Yes, you lose any additional software you have installed, but it is fairly easy to get it back.  You need to generate a list of installed packages and use it to reinstall packages.  Use [these instructions]("http://ubuntuforums.org/showthread.php?t=261366") to create a list routinely along with a backup of your data and then restore the list after reinstalling or upgrading.  Be sure to select the partition which has your home directory as /home and do not format it.  As already said, your email setting and other settings will be there after a reinstall.

---

### Post by stoogiebuncho on 2008-11-01
Thanks for all the advice.  I might not do it just yet, but maybe before 9.04 comes out so I can do a clean install then.  I've been upgrading for the past few releases, and though it's gone very smoothly for me, I feel like it would be good to clean things out every now and then.

---

### Post by nhasian on 2008-11-01
good call.  wait until 9.04 then you can use EXT4 filesystem.

---

### Post by ugm6hr on 2008-11-01
> **stoogiebuncho said:**
> I dual boot, would having a /home partition have any advantage over simply copying my /home folder to the windows partition, doing a clean install, and copying it back to the /home folder?

It is quicker (no need to copy everything back).

Plus, if you dual-boot, it is easier to find documents in /home from Windows if you have a separate partition (using fs-driver) - no need to mount your / partition at all.

> I'm assuming that any extra packages that I have installed (games, XAMMP, AWN, VLC, etc.) would have to be installed again, and my settings for these packages would be lost.

Additional packages - need to be reinstalled (just as with an upgrade) - see bobpress link.

But most apps have their settings within /home - hence once installed, everything just works as you had before (which can be a blessing in disguise if you were hoping to start from scratch after a botch-up!)

---

