---
title: "nautilus help"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-13
Where is there documentation on how to tailor nautilus?

Specifically I'd like to set the "open" menu items and the right click menu items to be commandlines of my choice. This would include adding new file extensions/mimetypes.
Also how to get at environment variables from a nautilus script.

Is there doc for programmers/developers for setting up the nautilus environment that explains how to do the above?

Thanks,
Norm

---

### Post by JC Cheloven on 2008-05-13
Check in synaptic if you have installed libgnomevfs2-common. If you don't, just catch it.

---

### Post by NormR2 on 2008-05-13
I don't have internet connection from Ubuntu.
How can I get it (libgnomevfs2-common) from Windows? 

What is libgnomevfs2-common?

What do you mean by  > just catch it??

---

### Post by NormR2 on 2008-05-13
I looked in the package manager and I have libgnomevfs2-common and several other libgnomevfs2-... packages.

If that has what you see when you do help from nautilus, it doesn't begin to answer my questions. It's very simple.

---

### Post by nick_h on 2008-05-13
Have a look at the [G-Script](http://g-scripts.sourceforge.net/) site.  The FAQ will give you a starting point to writing your own nautilus scripts.

---

### Post by NormR2 on 2008-05-13
thanks for the reply.

My question isn't about writing scripts, its about how to put my own items in the right click context menu. What I'd like is for there to be different, unique items in the menu for each mimetype/extension. I've tried to change the commands for an existing extension(RSS) and had trouble, so I tried adding a new extension(nss) and still have the same kind of problems. When new applications are added to nautilus, it lists them by the first string on the commandline. I'm writing java tools, so all my commands are identified as being 'java' in the RC context menu. I've found the desktop config files and gone into them to change the comment that describes the command so I can make a descriptive name for each commandline vs having them all defined as 'java'.

What I'm looking for is some doc that will tell me all about how this works instead of my having to hack this and that and see what happens as a result.


I have some scripts that I've written that work fine. That's not the problem. The problem with scripts is that all of them are shown, not just the ones for the type of file that is being worked on.

---

