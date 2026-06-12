---
title: "Lazarus - Free Pascal Source Directory not found"
date: 2008-03-20
forum: Programming Talk
---

### Post by aidave on 2008-03-20
After grabbing "lazarus" with apt-get, I cant get the Environment to recognize the Freepascal source directory.  I set it to:

/usr/lib/fpc/2.2.0/units/i386-linux

Which looks correct but it wont accept that.

---

### Post by Fbot1 on 2008-03-20
This maybe what you want:
[http://www.lazarus.freepascal.org/modules.php?op=modload&name=FAQ&file=index&myfaq=yes&id_cat=2#q63](http://www.lazarus.freepascal.org/modules.php?op=modload&name=FAQ&file=index&myfaq=yes&id_cat=2#q63)

Seems a little strange, did it come like that?

---

### Post by aidave on 2008-03-20
Not sure how to resolve it from that info.

Yes it is a clean install via apt-get.  Havent touched a thing.  Upon first start of Lazarus, it gave that warning.  Yet I can't find what directory it should be set to... 

Now it says "system.ppu" not found.  "Make sure fpc is installed correctly and fpc.cfg points to the right directory"

---

### Post by Fbot1 on 2008-03-21
It seems to be a packaging issue.
[INDENT][https://answers.launchpad.net/ubuntu/+question/16174](https://answers.launchpad.net/ubuntu/+question/16174)[/INDENT]
Alternatively, you could use the deb on sourceforge.
[INDENT][http://sourceforge.net/project/showfiles.php?group_id=89339](http://sourceforge.net/project/showfiles.php?group_id=89339)[/INDENT]

---

### Post by aidave on 2008-03-21
Thanks for the info and help!

I tried "sudo apt-get install fpc" and that downloaded and installed freepascal 2.2

Set the dir to: "/usr/lib/fpc/2.2.0/units/i386-linux/"

However, still nothin... hmm... should I uninstall and then use the deb?

---

### Post by Fbot1 on 2008-03-21
> **aidave said:**
> Thanks for the info and help!

I tried "sudo apt-get install fpc" and that downloaded and installed freepascal 2.2

Set the dir to: "/usr/lib/fpc/2.2.0/units/i386-linux/"

However, still nothin... hmm... should I uninstall and then use the deb?

It's worth a try.

---

### Post by raydeen on 2008-04-20
I just had this same problem. For some reason fpc-src isn't in the repos (or I didn't see it at any rate). I downloaded the .deb for that one , installed it and the errors went away.

---

### Post by MEDuLa on 2008-05-30
Try:

/usr/share/fpcsrc/

It worked for me.

(This is my first post :biggrin:)

---

### Post by andrew_66cz on 2008-06-24
Just install "fpc","fpc-sources" and "fpc-utils" using sinaptic for example. Somebody forgot to add it into package :(

---

### Post by swampdweller on 2008-06-29
Yes, if you're an Ubuntu dummy like me, ignore all that confusing stuff and just do as Andrew says.  Lazarus fails to mark some parts of Free Pascal on which it nonetheless relies.  So, in Synaptic, if you're installing Lazarus, just make sure you also scroll up to the FPs and check everything having to do with Free Pascal.  Perhaps that's overkill, but it's simple enough that I was able to do it even with my little pea-sized brain.

---

### Post by gobuntu on 2008-07-09
> **aidave said:**
> After grabbing "lazarus" with apt-get, I cant get the Environment to recognize the Freepascal source directory.  I set it to:

/usr/lib/fpc/2.2.0/units/i386-linux

Which looks correct but it wont accept that.

Go to System/Administration/Synaptics Package Manager

There, click SEARCH and in search window type fpc (for Free Pacal Compiler).

You have to be connected to web. Then you Mark-For-Installation all you find about fpc, including the fpc-source 

Install those, of course.:)

---

### Post by kva on 2008-07-20
I have installed both lazarus and fpc, and lazarus works fine :D,
however the component is limited, i cannot find component for serial communication..does anybody have the component ?

Thanks.

---

### Post by DGambrinus on 2008-08-24
Synapse has componants for serial communication called Synaser. If you have used their libraries before it is pretty similar. If not, look into the TBlockSerial class..
[http://synapse.ararat.cz/doku.php]("http://synapse.ararat.cz/doku.php")

I haven't used Synaser in FPC yet but I have used it in Delphi and I have used their TCP componants in FPC so I am confident that it will work fine cross-platform...

---

### Post by jkorten on 2010-03-18
In fact the directory path you need to enter in the "Environment->Options" bar for the "FPC Source" entry must contain the whole path - which for ubuntu at this point is /usr/share/fpcsrc/2.2.4/

I assume this version number will change and as you update your fpcsrc you will need to bump this version number.

Hope this helps.

Regards,

Jerry

---

### Post by liamsacc on 2011-07-18
> **swampdweller said:**
> Yes, if you're an Ubuntu dummy like me, ignore all that confusing stuff and just do as Andrew says. Lazarus fails to mark some parts of Free Pascal on which it nonetheless relies. So, in Synaptic, if you're installing Lazarus, just make sure you also scroll up to the FPs and check everything having to do with Free Pascal. Perhaps that's overkill, but it's simple enough that I was able to do it even with my little pea-sized brain.
 
 
 
:p**I agree!! Im a newbie on this too and after having many attempts and lookups on forums, this is a popular problem, in software centre , via 'Provided by Ubuntu' searched for FPC and installed all the apps  , at last!!! **
 
**'Hello World works' *next...* database connections!!! :guitar:**

---

