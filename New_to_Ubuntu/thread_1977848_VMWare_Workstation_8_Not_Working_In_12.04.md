---
title: "VMWare Workstation 8 Not Working In 12.04"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by chase321 on 2012-05-10
Hello,
I upgraded to 12.04 and now my vmware workstation is not working, i found how to fix it... but i'm no pro when it comes to patching...

[http://communities.vmware.com/message/2034437](http://communities.vmware.com/message/2034437)  <--- this is the forum with the fix

i do not understand what they are saying, if someone could maybe clear this up for me, that would be great!

---

### Post by PhantomTurtle on 2012-05-10
[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/]("http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/")(from the second post in the forum). Run the patch and the .sh file and that should fix it. Also this should be done after you run the .patch and .sh files. If you run into problems then try running those scripts with root privileges by using the sudo command.

---

### Post by chase321 on 2012-05-12
i get this error:

chase@Chase-Linux:~$ sudo '/home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch' 
diff: source802//vmnet-only/filter.c: No such file or directory
diff: source/vmnet-only/filter.c: No such file or directory
/home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: 2: /home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: ---: not found
/home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: 3: /home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: +++: not found
/home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: 4: /home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: @@: not found
/home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: 8: /home/chase/Desktop/Vmware Workstation Patch/vmware3.2.0.patch: Syntax error: "(" unexpected
 
And, if i try with the other file first it says that the patch file is missing

---

### Post by PhantomTurtle on 2012-05-12
See this thread for installing a .patch file - [http://ubuntuforums.org/archive/index.php/t-979404.html]("http://ubuntuforums.org/archive/index.php/t-979404.html").

---

### Post by chase321 on 2012-05-13
again, i'm not sure i understand what they are doing since it is not for the same patch i am using...

This is the site that i have downloaded the patch and fix from --> [http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/)

---

