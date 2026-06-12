---
title: "Backup Packages"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by mebss on 2012-02-22
Hi !

I am about to reinstall Kubuntu on my laptop (had a little problem :s [http://ubuntuforums.org/showthread.php?p=11710212#post11710212](http://ubuntuforums.org/showthread.php?p=11710212#post11710212) ) and I wanted to know if there is a way to list, or to backup all the currently installed packages so I can reinstall them easily once I'm done.
Even just an automaticaly generated text list would be usefull, at least I would be sure not to forget one.

Thanks !

EDIT : Due to the problem mentionned above, I have no graphic inteface xD

---

### Post by yetiman64 on 2012-02-22
You can do the listing of your packages with dpkg (should work in kde like unity).

```
sudo dpkg --get-selections > /path/to/file/<filename>
```alter "/path/to/file/<filename>" to define what the output file (your list of packages) is called and where it is stored on your filesystems.


To update a newly installed sysem use,

```
sudo dpkg --set-selections < /path/to/file/<filename>
``` alter the path and filename to match the first code above.

followed by,

```
sudo apt-get install dselect
```and 

```
sudo dselect
```dselect when used correctly will download and install all the previously installed packages as defined by your list.

---

### Post by mebss on 2012-02-22
Nice, thank you!
Just a question, will it also list the system updates or just the packages I installed myself?

---

### Post by yetiman64 on 2012-02-22
> **mebss said:**
> Nice, thank you!
Just a question, will it also list the system updates or just the packages I installed myself?
It will list **everything** installed as far as I am aware up to the point you used the command.

I'm not sure about this next bit, but it would probably be wise to revert/uninstall any ppa's/proprietary drivers before using this. They could then be re-added to the new install after using dselect, I would advise you to wait for confirmation if you feel it is necessary.

I have used the method above successfully with Ubuntu, but I did take the precaution of removing ppas and proprietary drivers first, before doing the install listing initially.

---

### Post by mebss on 2012-02-22
Hmm nice to know that.
As you said it would "be wise to revert/uninstall any ppa's/proprietary drivers before" proceeding.
But how do I do that and why would it be bad if I don't?
Or maybe I can chose which packets to install or not before running dselect (maybe by editing the file)?

---

### Post by yetiman64 on 2012-02-22
> **mebss said:**
> Hmm nice to know that.
As you said it would **"be wise to revert/uninstall any ppa's/proprietary drivers before" **proceeding.
But how do I do that and why would it be bad if I don't?
Or maybe I can chose which packets to install or not before running dselect (maybe by editing the file)?

I actually said,

> ..it would **probably** be wise to revert...*_As I indicated, I'm not sure it is entirely necessary_* I just used that approach as a precautionary measure. Maybe it would have been easier for me to leave the ppas in place and install all their gpg keys and details in the new install, did an update and run dselect. Will have to test that out next time I need to use it. 

Wait for further opinion on that from others here (maybe consider removing the [SOLVED] tag on the thread to garner more views on the main forum).

I would avoid your suggestion of removing packages from the list directly, could leave you with a broken new install if you break a dependency of another package you leave in when doing so. That possibility is known as "dependency hell", and yes it can get messy to the point of being easier to do a reinstall.

Good luck and cheers for now. yetiman64

---

### Post by mebss on 2012-02-23
All right, thank you very much yetiman64 ;D

Waiting for other replies ^^.

---

