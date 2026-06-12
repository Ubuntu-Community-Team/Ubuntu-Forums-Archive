---
title: "Installation questions"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Yewni on 2008-06-01
Here's my super-newbie question.

How in the world do you install software that isn't listed in the "Add/Remove" window.  I want to install "Fakenes" (a NES emulator) but can only get my hands on a .tar.gz file.  From my research, I believe that this is basically a .zip file with the info inside of it.  I don't know how to go about installing the data that is inside this .tar.gz file onto my computer.

Is there a simple, step by step guide that somebody has?  I've searched all over google for this, but can't seem to find anything.

Apologies for the newbie question here.

---

### Post by Joeb454 on 2008-06-01
Extract it, and let us know what is in the folder :) If there is a README you can just read that :)

---

### Post by SunnyRabbiera on 2008-06-01
actually if you want a decent NES emulator, try fceu/ gfceu.
Its in the repositories, here is a guide to use them:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Xiong Chiamiov on 2008-06-01
> **Yewni said:**
> 
Is there a simple, step by step guide that somebody has?  I've searched all over google for this, but can't seem to find anything.

[Why yes there is.]("http://monkeyblog.org/ubuntu/installing/") (you'll want the section entitled "from source")

> **Yewni said:**
> 
Apologies for the newbie question here.
None needed.  If you're trying to help yourself, we won't get frustrated with you, and even so, these are the nicest forums I've ever come across, so you'll have to work hard to make people angry.

---

### Post by Yewni on 2008-06-01
After extacting it there are some directories (build, docs, src, support) as well as some files: cbuild.c, Makefile, default.cbd).

---

### Post by Joeb454 on 2008-06-01
I think ZNes may be in the repo's :)

---

### Post by Yuki_Nagato on 2008-06-01
[http://www.control-escape.com/linux/lx-swinstall.html]("http://www.control-escape.com/linux/lx-swinstall.html")

Scroll down the page to find "Tar Balls."

Hopefully you will not have to compile from source.  There should be something similar to an installer inside of the extracted folder.

If there is no installer, try this:

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html")

---

### Post by SunnyRabbiera on 2008-06-01
> **Yewni said:**
> After extacting it there are some directories (build, docs, src, support) as well as some files: cbuild.c, Makefile, default.cbd).

that would be a source code application, that needs compiling.
Its best just to stick with the repositories, unless its something major.

---

### Post by Xiong Chiamiov on 2008-06-01
I'm not sure if you missed my post or not, but the basic syntax will be
```

./configure; sudo make; sudo make install

```
or
```

./configure; sudo make; sudo checkinstall

```
to create a .deb file and install it into apt.  The latter doesn't always work, and you'll need to make sure you have the "checkinstall" package installed first.
Make sure you keep the source folder around; later, if you want to uninstall it, you have to navigate to that folder and run
```

sudo make uninstall

```

@Yuki:
Aw, you're not an alien with mad computer skills?  How disappointing.

---

### Post by Yewni on 2008-06-01
Managed to find some stuff using the Synaptec add/remove software.  thanks so much for the help!

---

### Post by Joeb454 on 2008-06-01
No problem :) (on behalf of all the others in the thread of course).

And you can mark your thread as solved by clicking thread tools (at the top of this page) and then choosing "Mark Thread as Solved"

---

