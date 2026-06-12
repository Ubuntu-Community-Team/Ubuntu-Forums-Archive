---
title: "Linux is not stupid-user friendly :("
date: 2008-10-03
forum: New to Ubuntu
---

### Post by jholovacs on 2008-10-03
I did something dumb, and let 'chown -R www-data:www-data *' walk thru my /var directory instead of my /var/www directory.  Now my postfix won't work.

So I figure, no big deal, I will remove and reinstall postfix, it should create the dirs, set the permissions, all is well with the world.

Fast forward a couple of hours, some window-shattering screams of anguish and frustration, and several considerations of how far I could launch my computer out the window (I think I'm good for at least 40 ft), and now I accept the fact that I am an idiot and must ask for guidance.

Is there a way to:
1) make apt-get (or any of the apt apps) recreate/ reapply folders, ownerships, and permissions, and/or failing that, to
2) completely remove an app it installed, to include paths, etc so the next time through, and can start from the beginning?

It seems like this would be so easy to do, but I sure can't figure it out.

Please help!

-Jeremy

---

### Post by TheLions on 2008-10-03
2) try ```
sudo aptitude purge <app_name>
```

---

### Post by bodhi.zazen on 2008-10-03
Easiest way to fix is to either restore from backup or re-install.

---

### Post by jholovacs on 2008-10-03
yeah, that's what I seem to be leaning towards right now.  But this is why Windows is so much less scary;  with Windows, a program uninstall and reinstall fixes the problem unless your problem has nothing to do with the symptoms you're seeing.  In this case, I know the symptoms; I caused them, and I know exactly how it happened, yet I seem powerless to do anything about it.  It's very frustrating.

BTW, the purge was something I tried first... with no luck.

---

### Post by Orange_and_Green on 2008-10-03
Dear jholovacs,

right-clicking a package in Synaptic, then Properties->Installed files will give you a list of all the files installed by that pacakge. I suppose you could copy-paste those into a script that bulk-changes permissions for them and their parent directories...

Now, what those permissions should be, is a different question alright...

Maybe it's worth a try to:
1) save the files list (for postfix and any dependencies you are going to remove) somewhere;
2) uninstall postfix
3) paste the files list right after a rm command and raze them all
4) reinstall postfix

What do you think?

---

### Post by bodhi.zazen on 2008-10-03
> **jholovacs said:**
> with Windows, a program uninstall and reinstall fixes the problem < clip > 

LOL, that was not my experience with windows. Installing and removing software on Windows was more then once a real pain and often there are fragments of applications throughout the system, including the registry and who knows where else. Un-installation of applications is often a risky proposition.

---

### Post by hyper_ch on 2008-10-03
and you don't go in windows from a limited user account to an admin account and set all of c:\windows to read only...

---

