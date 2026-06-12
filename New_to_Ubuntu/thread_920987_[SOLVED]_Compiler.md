---
title: "[SOLVED] Compiler"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by P13808 on 2008-09-15
I looked on the GCC website for a compiler to run n ubuntu.  I go to download off the ftp, but I don't know what to download.

Is there a .deb file for a compiler?

---

### Post by Whiffle on 2008-09-15
sudo apt-get install build-essential 

should do it.

---

### Post by Offramp on 2008-09-15
> **P13808 said:**
> I looked on the GCC website for a compiler to run n ubuntu.  I go to download off the ftp, but I don't know what to download.

Is there a .deb file for a compiler?
Hi,

Have you tried the package manager.  I just did a search of mine for gcc and found a few variants of the compiler (although only gcc was installed)

Cheers

---

### Post by P13808 on 2008-09-15
Any way without using the repository.  I don't have internet on ubuntu.  Have to move with a flash drive from a windows.

---

### Post by Whiffle on 2008-09-15
Here ya go:

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

You'll need all the ones with the big red dot, should be able to find a download link if you click on them at the bottom of the page it brings up.

---

### Post by Offramp on 2008-09-15
> **P13808 said:**
> Any way without using the repository.  I don't have internet on ubuntu.  Have to move with a flash drive from a windows.
Hi,

I am reasonably new to this, but when I had to set up ndiswrapper I also did not have internet access for my linux machine.  I used [Ubuntu Package]("http://packages.ubuntu.com/hardy/devel/") site to get the required .deb files and installed from there.  There might be a quicker way (LiveDVD?) but this worked for me,

Cheers

---

### Post by P13808 on 2008-09-15
So I go through each one and download the red ots within each red dot and so on?

---

### Post by nowshining on 2008-09-15
yes the red dots are the necessary ones. :) it's a pain I know.... but alas build-essential is on the installCD/DVD and should ask for the CD when going thry synaptic, if not we'll have to add the CD as a repo..

I know gutsy does this...

edit: as for build-essential - you'll have quite a week esp. on dialup cause you gotta go thru every lib, etc.. and get all dependencies and so forth.. :) Have fun.

---

### Post by P13808 on 2008-09-15
Wait, could i add it off my ubuntu install cd?

---

### Post by cariboo on 2008-09-15
If I remember correctly build-essential is on the LiveCD, no need to have internet access to install it.

Jim

---

### Post by Offramp on 2008-09-15
In the package manager (8.04) there is an option to add the CD to the list of repositories.  If the packages are on the CD then I would assume that this would enable you to install from the CD.

Cheers

---

### Post by P13808 on 2008-09-15
Okay, that will probably be much easier then.  Now how do I mark this solved?

---

### Post by nowshining on 2008-09-15
thread tools - mark as solved.

---

