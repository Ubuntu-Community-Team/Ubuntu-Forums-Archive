---
title: "quanta installation problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by cyb3rd4wn on 2008-04-27
i run kubuntu 7.04 with gnome installed.
i'm trying to install quanta 3.0. first got an error about X include fines and headers, and fixed it.
now when i run ./configure i get:

```
checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!
```


also detailed instruction about installing quanta would be great since i really don't want to mess this up

thanks

---

### Post by ammofreak on 2009-01-25
Hi cyb3rd4wn: am having same problem with Quanta Plus. Been searching for step-by-step instructions on install but no success so far. Will post if i find it. Am running Ubuntu Desktop 8.10. :)

---

### Post by snova on 2009-01-25
First of all, Quanta is in the repos... do you need to build from source?

Secondly, should you continue this route, install the **libqt3-headers** and **libqt3-mt-dev** packages.

(Of course, I'm on Intrepid, so the package names might not line up...)

---

### Post by ammofreak on 2009-01-26
Hi cyb3rd4wn: finally figured it out. There is a package manager one uses to load programs in linux. For my distro ( Ubuntu Desktop 8.10), i go to System, Administration, and then Synaptic Package Manager. There is a list of all the packages. Ubuntu Gnome has over 26,000 packages listed, Quanta Plus included. Apparently, this method is the way to go because it makes the relationships with other packages one might need to run the main package. In this case, Quanta Plus needed several other packages to run properly or with full features. There was one package missing though, but all one has to do is download the tarball, go back into the package manager, hit File, and then hit the Add Downloaded Packages, etc. Hope this helped you...Cheers

Updating: the above works, however, for me, i am having the problem with Quanta not recognizing the Cervisia plugin. Keeps telling me it isn't installed when it is. Any help on this one would be greatly appreciated...Cheers

---

### Post by Cerox Rex on 2009-02-03
> **ammofreak said:**
> 

Updating: the above works, however, for me, i am having the problem with Quanta not recognizing the Cervisia plugin. Keeps telling me it isn't installed when it is. Any help on this one would be greatly appreciated...Cheers

having same problem

I get this error when starting Cervisia!

> The CVS Managment (Cervisia) plugin could not be loaded. 
Possible reasons are:

-CVS Managment (Cervisia) is not installed
- the file kde3/libcervisiapart.la is not installed or is not reachable.

As i know i have Cervisia installed or at leat Adept says so. I looked in the /etc/kde3 folder and the /etc kde4 folder and couldnot locate > libcervisiapart.la

Any Ideas on how to solv this? as i'm kinda new to Ubuntu ;)

EDIT: I'v done a complete search on my system for libcervisiapart.la, and its nowhere to be found.

---

### Post by jcslzr on 2010-02-21
Hola,

Did you find the solution for the Quanta missing applications?

Regards,
Carlos

---

### Post by darkstaar on 2010-02-21
Quanta Plus uses the version 3 (not version 4) of these apps. I'm not certain if you'll even find version 3 of these applications any more.

---

### Post by kamakazi20012 on 2012-05-05
Obviously others who have downloaded this application have got it to working with all the plug-ins (by reading the reviews).  I'm looking to see if I can find a solution.  

According to Quanta Pro, I'm missing Cervisia (which is installed), Konsole & an XSLT plug-in.  I installed all add-ons available during the initial install tonight and these files are still missing.  I separately downloaded Konsole and an XSLT editor in hopes it will work.  I'll keep trying and once I find a solution I will post here.  Unless someone else has already found one.

---

### Post by kamakazi20012 on 2012-05-05
Installed KXSLTDbg from the software center and that solved the issue with that plug in.  Konsole didn't change anything...it's still in the wild blue yonder (missing) as well as Cervisia.  Thought I'd let others know.  Still looking at how to install the other plug-ins.

---

