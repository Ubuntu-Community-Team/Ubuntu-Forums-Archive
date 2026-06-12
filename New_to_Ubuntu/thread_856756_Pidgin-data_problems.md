---
title: "Pidgin-data problems"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by MikeMa$$ey on 2008-07-11
Hey everyone! I am new.  I am new to Linux and Ubuntu, I have played with Fedora a little and that is about it.  Now I can install and run apps with no problem, I am really green with the command line so if the solution to my problem needs to be addressed in the CL please write out what I need to do.  OK here is my problem

I am running Ubuntu 8.04 on an AMD Athalon 3200+ 64bit, 1G memory and 200G of HDD.  

I installed the OS with no problems and ran the updates.  As some of the updates were installing some were still being downloaded and the computer rebooted before they finished.  Now when I try to finish the updates I lock up trying to get pidgin-data.  The computer slowly dies trying to retrieve this file.  

I have tried running the repair console, no joy.  Unchecking the update and finishing the rest, no joy.  and looking for a way to stop synaptic from attempting to aquire this file but I dont know the app that well.  Any Ideas?  Any help will be great.

Massey

---

### Post by ChameleonDave on 2008-07-12
So you want to do a general update of the computer, and this software package is getting in the way?

Just remove the package.  You can do this in Synaptic, or else you can use this command in the terminal:

```

sudo apt-get remove pidgin pidgin-data

```

It will want to remove a few other things too (which depend on this package).  Don't worry, just remove them.

Then do your update again (making sure to refresh the list of packages).

Once you have done that, you can turn your attention to Pidgin, if you really want to use it.

---

### Post by MikeMa$$ey on 2008-07-12
thanks for the help but it didnt work.  I get an error saying this.
E: The package pidgin-data needs to be reinstalled, but I cant find an archive for it.

This is starting to really piss me off.  Is there a manual way to remove the entire application or can I restore it from my installation CD?

Massey

---

### Post by ChameleonDave on 2008-07-12
> **MikeMa$$ey said:**
> thanks for the help but it didnt work.  I get an error saying this.
E: The package pidgin-data needs to be reinstalled, but I cant find an archive for it.

This is starting to really piss me off.  Is there a manual way to remove the entire application or can I restore it from my installation CD?

Massey
OK, make sure that Synaptic is closed.

Go to the terminal and do this:

```

sudo dpkg --force-all --remove pidgin pidgin-data
sudo apt-get update && sudo apt-get -f install

```

The second command is to fix the system after pidgin and pidgin-data are force-removed.  Depending on what is causing this, there may still be errors.

If the package still refuses to be removed, we can get even more heavy-handed.

---

### Post by MikeMa$$ey on 2008-07-12
so far that appears to have worked.  I am going to try things out like installing EVE-Online and see if it will work now


Thanks alot and if I need ya again I will let you know.

Massey

---

### Post by MikeMa$$ey on 2008-07-12
OK good to go pidgin is gone and my updates were able to run.  Now I just need to configure my Radeon 9800pro to run Open GL and 3D graphics so I can play EVE-Online.

Massey

---

### Post by ChameleonDave on 2008-07-12
> **MikeMa$$ey said:**
> OK good to go pidgin is gone and my updates were able to run.  Now I just need to configure my Radeon 9800pro to run Open GL and 3D graphics so I can play EVE-Online.

Massey
OK, great.  Pidgin will probably install correctly at this point, if you want it. (It is a great instant messenger.)

Perhaps you could use the "Thread Tools" menu to mark this issue as solved.

---

