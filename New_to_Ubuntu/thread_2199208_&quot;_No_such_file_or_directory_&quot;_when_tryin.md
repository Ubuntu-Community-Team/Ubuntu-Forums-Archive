---
title: "&quot; No such file or directory &quot; when trying to compile downloaded files"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by blippple on 2014-01-12
So I'm sure this is a small question to ask, right now I'm trying to download and install files from the internet using the " wget " command in terminal. I've done that successfully, and the next steps I am told are to compile it.

             However , I cannot compile it because my computer gives me a " No such file or directory " error when I do so. What should I type to download it, so that I can compile it ?

---

### Post by egeezer on 2014-01-12
You'll often need to use sudo (command) in order to access some files and directories.

---

### Post by llamabr on 2014-01-12
I do not think it's a matter of sudo.  Maybe if you copy/paste what you're doing, from the wget, to the compile, we can point out where you're going wrong.

Also, why use wget?  I assume you're downloading these from a webpage -- just let firefox download them for you.

---

### Post by Dave_L on 2014-01-12
Are you new to Ubuntu? Are these applications not available through the normal Ubuntu repositories, i.e., not installable using the Software Center or Synaptic?

---

### Post by Impavidus on 2014-01-13
+1 to Dave_L's comment.

When you download something from the internet there is no standard recipe for installing it. It depends on how the creator of the package decided to package it. What are the instructions? What kind of file is it? If it's an archive &#8211; like .zip, .tar.gz (or .tgz), .tar.bz2 &#8211; what's inside? I don't think there is any problem with how you downloaded it. Maybe you just forgot to enter the right directory in the terminal.

And don't use sudo yet, it doesn't work against "No such file or directory" errors. It often works agains "Permission denied" errors, but first make sure you understand why you have to use it. If you use sudo as a magical way to make things happen whenever you get some kind of error &#8211; and I admit, I did so too on a few occasions in the first months I used Linux &#8211; it doesn't offer you the protection from yourself that it is supposed to give you.

---

