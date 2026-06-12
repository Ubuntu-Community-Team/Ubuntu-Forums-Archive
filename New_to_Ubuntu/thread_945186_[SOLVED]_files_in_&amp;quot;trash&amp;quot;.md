---
title: "[SOLVED] files in &amp;quot;trash&amp;quot;"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-10-12
Whenever I delete any files from Ubuntu, they first go into the Trash bin. After a few days or weeks, when I am sure I don't need those files,I empty the trash, which cleans out the trash bin, or so I thought.

I just discovered another hidden receptacle for trash. It is in
/root/.local/share/Trash/files
To my amazement I noticed that this folder, "files", contains over 50,000 items and it is using up over 1.5 Gigabytes of my hard drive space.

I took a look at some of the files in this folder and practically all of them are broken links, or folders that I have deleted from Ubuntu, or desktop configuration files that I don't need. I remember deleting a lot these files myself.

Why is there this trash repository on my computer?  It appears that most of the stuff that I deleted from my computer and then from the trash bin ends up here, in a hidden folder called .local.

I am tempted just to delete all of this stuff, but where would it go? I hope not back into the Ubuntu Trash folder. 

I would like to get rid of this 2.5 Gigabytes of useless data; as far as I can tell it serves no useful purpose on my computer.

I am sending this note to anyone who understands this trash system better than I do. I would like to simply delete all of this useless data, but I am not sure if I should.

Your comments and/or advice would bwe appreciated.

JBA2337

---

### Post by OutOfReach on 2008-10-12
That's the root trash, the trash that goes there is when you delete files as root. (*sudo*)

---

### Post by expatCM on 2008-10-12
To delete those files it is not just a matter of highlight and delete.  You need to highlight and then press Shift Delete ... then they are removed from the system.

Lots of information at this tutorial
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by JBA2337 on 2008-10-13
:):):)
Thank you! Your help is much appreciated. I went to the link that you suggested, and the article answered practically all of my questions. 

In addition to the two "Trash" folders that I found in my Ubuntu installation, there is also a folder called /Recycled. This appears to be nothing but junk files also. Is it safe to delete permanently everything that is in /Recycled  ?

By the way, why does Ubuntu have so many places where it stores deleted or obsolete items?

(1) Trash folder on the desktop
(2) /root/.local/share/Trash
(3) /home/username/.local/share/Trash
(4) /Recycled

It's a pain to have to keep checking all these places, and keeping them cleaned out.

JBA2337

---

### Post by expatCM on 2008-10-13
The icon on the desktop is basically a link to the /home/username/.local directory trash.  So in context a separate trash bin is kept for each normal user on a machine.

The trash for Root is kept at arms length simply because Root has all the power and so anything removed by Root is also kept so that only Root can see it and subsequently kill it..

I may be mistaken but the /Recycled directory is a remnant from Windows data where a Windows program places a directory for the files that have been deleted before they are removed from the computer.  I think you can safely delete this directory as long as you are not dual booting.  I do not have these Recycled folders but also I do not use Windows at all.

---

