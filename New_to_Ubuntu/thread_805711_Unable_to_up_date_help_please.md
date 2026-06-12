---
title: "Unable to up date help please"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by wetsocksmell on 2008-05-24
Hi can anyone please help with my sons PC
I was installing the updates but i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks for any help

---

### Post by PmDematagoda on 2008-05-24
Please realise that you are posting in the wrong forum section, this section(and I quote) is to:-
> Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.

Your post will be moved.

---

### Post by PmDematagoda on 2008-05-24
About the problem, do as the error message suggests and run:-
```
sudo dpkg --configure -a
```
from a terminal and see if that solves your problem.

---

### Post by PmDematagoda on 2008-05-24
@OP(wetsocksmell):- Did you even try the command I've given previously before starting the duplicate thread?

---

### Post by forrestcupp on 2008-05-24
It's good to pay attention to the error messages and if they give you a solution, do it.  But you just always need to keep in mind that any command that deals with the system is probably going to need **sudo**.

---

### Post by Jadd on 2008-05-24
Wow, a thread with no silly [ubuntu] prefix! Much nicer.

---

### Post by wetsocksmell on 2008-05-24
Sorry this is in the wrong place i'm not sure where to post it.
I tryed "sudo dpkg --configure -a" before i posted i should of said sorry.
Nothing happen but tryed again and got this:

 dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys

Does it mean reinstall the whole OS?

---

### Post by wetsocksmell on 2008-05-24
> **Jadd said:**
> Wow, a thread with no silly [ubuntu] prefix! Much nicer.

Well there wasn't a [Noob!] prefix :)

---

### Post by playme123 on 2008-05-24
im also having problems updating, I click on the update icon, then update manager comes up, then i click on install updates and it looks like its going to work then it sort of just hangs and there is no more activity.  I done what was suggested above in the terminal and its made no difference.  These updates have installed fine on me main pc but not on this blooody laptop

---

### Post by PmDematagoda on 2008-05-24
Since it is cupsys causing the problem, try reinstalling it with:-
```
sudo apt-get install --reinstall cupsys
```

Then see if that fixes the problem, if not, post the full error message here.

---

### Post by PmDematagoda on 2008-05-24
> **playme123 said:**
> im also having problems updating, I click on the update icon, then update manager comes up, then i click on install updates and it looks like its going to work then it sort of just hangs and there is no more activity.  I done what was suggested above in the terminal and its made no difference.  These updates have installed fine on me main pc but not on this blooody laptop

Give:-
```
sudo apt-get upgrade
```
a try.

---

### Post by forrestcupp on 2008-05-24
> **playme123 said:**
> im also having problems updating, I click on the update icon, then update manager comes up, then i click on install updates and it looks like its going to work then it sort of just hangs and there is no more activity.  I done what was suggested above in the terminal and its made no difference.  These updates have installed fine on me main pc but not on this blooody laptop

Also, it's not a good idea to just go running commands if that isn't what is needed.  The other guy actually had an error output telling him to run that command.

So try doing the upgrade from the terminal like PmDematagoda said.  If that doesn't work, maybe it would help to try changing servers.  To do that, go to System->Administration->Software Sources, and change the server in the box that says 'Download from:'.  Then doing the upgrade from the terminal will either work, or give you an error output to figure out what's going on.

---

### Post by playme123 on 2008-05-24
> **PmDematagoda said:**
> Give:-
```
sudo apt-get upgrade
```
a try.

thanks mate that worked a treat:) did try doing it in the terminal but ended up with the wrong commands

---

### Post by wetsocksmell on 2008-05-24
I backed up all my sons files and done a fresh install.
All works fine now.A long wayround i'm sure but it's done now.
Thanks for the replies.

---

