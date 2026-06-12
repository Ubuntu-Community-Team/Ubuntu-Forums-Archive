---
title: "Getting .html.erb formatting to work"
date: 2009-02-18
forum: Programming Talk
---

### Post by benson2788 on 2009-02-18
I am having some difficulties getting scribes and gedit to recognize any .html.erb rails files as such, and give them some syntax highlighting.  

I tried the tutorials at both [http://ubuntuforums.org/showthread.php?t=469300](http://ubuntuforums.org/showthread.php?t=469300) and at [http://robzon.aenima.pl/2007/10/ubuntu-710-rails-gedit-and.html](http://robzon.aenima.pl/2007/10/ubuntu-710-rails-gedit-and.html) , but I could not get the system to recognize .html.erb files.  .rhtml files worked fine, but .html.erb, the newer format, doesn't want to cooperate. Any file ending in erb is recognized, at least by nautilus, as a application/x-extension-erb mimetype.  There is no Overide.xml in my local mimetypes folder, nor anything else I immediately can find. 

Is there any accepted way to get this done in ubuntu 8.10?  I would appreciate anything you could offer me.  I would really like to get to use scribes for this, but at the moment I have to fall back on good old vim.  Thank you all very much.

---

### Post by rharriso on 2009-02-19
I've had a lot of trouble getting html.erb files to work as well.

You should try Komodo Edit, its not as heavy as other IDE's but it has a couple for features that gedit.

---

### Post by Tibuda on 2009-02-19
Make sure your erb file mimetype is the same as in the rhtml.lang. I mean this line:```
<property name="mimetypes">text/rhtml</property>
```
To manage mimetypes, you can install [assogiate]("apt:assogiate"), or just change the rhtml.lang to the mimetype you see in nautilus.

---

