---
title: "Problem with Free Pascal"
date: 2007-06-13
forum: Programming Talk
---

### Post by Jagunço on 2007-06-13
Hello everyone.

I'm trying to use Free Pascal here, but the mouse is behaving weird. When I open a console and execute fp, the mouse works for a few clicks (2 or 3) and then stops working on the program.
I also cannot select text when fp is running. When I press SHIFT+ARROW the cursor doesn't move.
One more thing: when I compile a program and something goes wrong, the "window" showing the defective lines is gone!:shock:

Perhaps I should install Lazarus...

Can anyone help me?

Thanks a lot.

---

### Post by HackingYodel on 2007-06-14
Hi Jagunço,

I'm afraid I have some bad news.  The mouse issue with Free Pascal and Debian/Linux is known and has been reported. [http://www.freepascal.org/probs.var](http://www.freepascal.org/probs.var)  It may take awhile to fix.

I don't know how comfortable you are with the command line, but I've done all of my Free Pascal tinkering with Vim/Emacs and the **fpc** command to compile the programs.  

I haven't installed Lazarus yet because it's not in the Ubuntu repositories and I personally don't like going outside of them.  Have you tried over at the Free Pascal forums?  Somebody over there may be running Lazarus on Ubuntu.

Hope that helped!

---

### Post by samjh on 2007-06-14
You can use the previous version of Free Pascal.  The FP IDE works with that.

The FP IDE and Debian issue is only with the current version 2.0.4.

Here's the link to 2.0.0 for Linux:
[http://sourceforge.net/project/showfiles.php?group_id=2174&package_id=2252&release_id=327601](http://sourceforge.net/project/showfiles.php?group_id=2174&package_id=2252&release_id=327601)

---

