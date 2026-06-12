---
title: "Help: pbuilder error on kill in makefile"
date: 2007-07-27
forum: Packaging and Compiling Programs
---

### Post by frafu on 2007-07-27
Hello, 


I am trying to build a debian package with pbuilder. However, the building process stops on this line of the makefile: 
kill -1 `pidof gconfd-2 
with an operation not permitted error. 

Is this a problem of privileges? If so, how can I solve it? I am already calling pbuilder with sudo. 



If I manually remove the kill command from the makefile, pbuilder succeeds in building the debian package; and the debian package also works when I install it on my system. 

So I thought to put the kill command into the postinst. Do I get it right: postinst contains commands that are executed at the end of the installation of the debian package; I suppose after copying the files to the system and configuring them? 

But I don't know how to make pbuilder use the debian/postinst. Do I have to add some dh_* under binary-arch into debian/rules? 


I have tried without much success to search for a solution in the forums and google.

Many thanks in advance. 

Francesco

---

### Post by Hendrixski on 2007-08-02
Hey, sorry this is 5 days after the fact... hope you check up on this.

You can remove that line from your makefile and then have to create a new tar.gz  which isn't advisable (unless you're doing this for personal use, or short term prototyping).

You can create a dpatch to remove that line using sed, dpatch runs before anything else does.

If you have a postinst file it should automatically run if you're using "sudo pbuilder --build whatever.dsc" to get into pbuilder.

---

### Post by frafu on 2007-08-03
Thanks for your reply, especially the tip about dpatch. 

Meanwhile I have managed to call the kill command from the postinst script. (I have removed it manually from the makefile)

Now I have a new problem: I would like to start the installed software (called mousetweaks) automatically after the installation. So I call it with absolute path from the postinst script, but it does not start. However it starts when I launch it manually from the Applications menu in gnome. 

Could it be that it does not start because gdebi is called as root, but mousetweaks needs services that run in the users gnome session (namely atspi)? If that is the case, how can I start mousetweaks from the postinst script; not as root, but as the user of the gnome session where gdebi has been called? 


A few more lines about the background if you are interested: 

MouseTweaks is for a GSoC probably targeted for gutsy. 
[http://ubuntuforums.org/showthread.php?t=494037](http://ubuntuforums.org/showthread.php?t=494037)
I thought I could make it available as debian package for testing in the forum and especially learn a bit about packaging along the way. . 

Here is the authors blog: 
[http://gerdk.blogspot.com/](http://gerdk.blogspot.com/)
(I am not the author of the source.) 

Francesco

---

### Post by Hendrixski on 2007-08-07
I don't recall any applications launching after I installed them.  That may be dangerous.

I know that what actually happens in the deb is that they create some temporary directories, then when the postinst scripts are all done, they copy those directories into the real ones.  So perhaps you're trying to call it when it doesn't exist yet.

Good luck on the rest of your project :-) looks like it's fun and all.

---

### Post by frafu on 2007-08-09
Thanks for the advice about not automatically starting an application after installation and for the explanation about the temporary directory during a debian package installation. 

Francesco

---

