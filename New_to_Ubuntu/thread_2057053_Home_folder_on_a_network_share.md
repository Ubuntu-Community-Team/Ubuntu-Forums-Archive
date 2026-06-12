---
title: "Home folder on a network share?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by cmo999 on 2012-09-12
Is it possible to change what my home folder is? 

ie instead of /home/username could I make it a network share?

I have a network including 2 computers running Ubuntu, and currently I am using Unison to mirror the home folders, and it occurred to me that this is a waste of space to have everything twice, as I am not concerned about redundancy at this time.

So I would like to be able to use the same Home folder from either computer by making it a network share on one of them.

It's easy to do this using Windows but I'm fairly new to Ubuntu, is it doable?

Thanks!!!

---

### Post by androssofer on 2012-09-13
> **cmo999 said:**
> 
instead of /home/username could I make it a network share?

 is it doable?


yes

but it appears finding out how is tough! 

LDAP, autofs and nfs would be the technologies needed to do it. Look into them and you should find more info.

And if you achieve it and feel like it, put a step by step into this thread for future generations to learn how!

---

### Post by audiomick on 2012-09-13
> **cmo999 said:**
> It's easy to do this using Windows but I'm fairly new to Ubuntu, is it doable?


Once again, Linux is not the same as Windows. The significant difference is that your /home/username folder not only has all your data in it, but pretty much all of you user config files. Enable "view hidden files" in your file manager to see them.

I gather the 2 computers are running the same version of Ubuntu, and have the same user account(s) set up. If you are mirroring the /home/username folders, then all the setup stuff you do on one computer should just appear automagically on the other. This may be exactly what you want. On the other hand, if you get to the point where you, for instance, decide to try out a version upgrade on one machine to see if it works properly before doing the second one, the mirroring may not be what you want anymore. If you are using one /home folder for multiple installs, the more divergent the installs are, the more likely you are to have problems.

Anyway, the way I would go would be setting up a common data folder and storing everything to there rather than the default location in /home/user. This folder would live on one machine (or on a NAS device). Accessing it through the net would be a simple matter via nfs or whatever.


A further refinment would be to use symlinks. I haven't actually used symlinks myself, but have read of a number of user who use them. The process seems to be to install with a small /home folder, have a large data partition that can be accessed from multiple installs and re-used if a fresh install becomes necessary, and use symlinks in /home/user to point to it. As I said, I haven't got into that. I just save manually by using the "save as" option, or I change the default storage path in my applications.

To sum it up: I would not share or mirror a /home/user folder as a matter of course unless I had a specific reason for doing exactly that. I would keep all my data in a central Data folder and leave the /home/user folders alone. This has the added advantage that if some config file gets completely messed up on one machine, the other one will still work and still have a version of the config file that is ok.

---

