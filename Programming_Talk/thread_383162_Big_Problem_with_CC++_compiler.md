---
title: "Big Problem with C/C++ compiler"
date: 2007-03-12
forum: Programming Talk
---

### Post by AndrewElmore on 2007-03-12
Hi, so I have a problem with trying to get gcc/g++ to work.

So I've gone on various forum pages looking at how to get a compiler on to your system, this is what i've come up with.

sudo apt-get install build-essential

That gets to a point then says "package build-essential is not available"...

So then I go into Synaptic Package Manager, and true enough it's not there!

Any suggestions as to where it could be, or where I can find another compiler????

Also, because of this problem, I can't actually build/add any programs either :(

Maybe I should mention that I don't have my wireless internet working yet.  Just in case that's the problem.

Thanks
Andrew

---

### Post by Game_Ender on 2007-03-12
You will need the Internet to be able to find the package.  The "build-essential" package is definitely in the repos.

---

### Post by g3k0 on 2007-03-12
You will probably need to enable some repos too.  You can do this via one of the options in synaptic.  You will need internet to get it though.  I don't think its on the CD.. but I may be wrong about that.

---

### Post by Game_Ender on 2007-03-12
No you won't its in the main repository.

---

### Post by hod139 on 2007-03-13
The build-essential package is on the install CD.  You should be able to put the CD into the computer and I believe a GUI autostarts asking if you want to install anything.  If not, you will have to manually add the CD to your /etc/apt/sources.list.

---

