---
title: "Revisioner source code manager"
date: 2008-08-25
forum: Programming Talk
---

### Post by sorcererx84 on 2008-08-25
Hi everyone. I am working on a new source code manager called Revisioner. Basically you can register local code branches (bzr, git, svn, hg) and update them all at once using Revisioner. Think of it as an update manager for source code. Currently I am working on the CLI version. After it is finished, I will start writing the GTK+ GUI. Revisioner is written in Python and I hope that in the future other people can use the revisioner library to add VCS support in their Python code.

If you think you might have a use for Revisioner I would really appreciate your feedback. Keep in mind that it is currently in pre-pre-alpha stage and I can guarantee you things will break regularly. If you still want to help you can install the package from my PPA at [http://launchpad.net/~hkaju/+archive](http://launchpad.net/~hkaju/+archive) or check out the current source code with bzr.

Please submit your bug reports to the [Launchpad bug tracker]("http://bugs.launchpad.net/revisioner") and feel free to discuss it in this thread.

---

### Post by SeanHodges on 2008-08-26
Sounds very cool, I haven't checked it out yet but this looks like something I could find very useful.

Thanks for the heads-up.

---

### Post by SeanHodges on 2008-08-27
I had a play with revisioner last night, looks very promising. My testing was against Subversion, Git and Bazaar (which are the VCS' I use most).

I've applied some fixes to a branch that I have uploaded to Launchpad, and submitted a couple of bugs that I didn't get time to look at.

Thanks again

---

### Post by sorcererx84 on 2008-08-27
Hi Sean! I merged your changes and commited fixes for those bugs. Thank you for your feedback :)

---

