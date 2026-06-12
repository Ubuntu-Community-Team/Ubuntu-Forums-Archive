---
title: "Missunderstanding in Ubuntu instalation"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by tomislav.nikolic00 on 2014-06-19
Not sure where this should go, so Begginers Section it is.

I just wiped my drive to install Ubuntu. It's working really good. The only downside is, I didn't really want to wipe my entire drive.

I had ubuntu installed previously, and while installing 14.04 it asked me what to do with it. I decided to select the option saying, delete ubuntu 13.10 and install Ubuntu 14.04, with a warning underneath it saying that it will delete all my Ubuntu programs, documents, blahblah. However, it didn't say a thing about wiping the entire freakin drive where I had tons of other stuff on my Windows partition.

So um, after two years of using Ubuntu, I don't think I'm coming back anymore. Not gonna risk my windows-only-compatible-non-replacable software and video games for a linux distro that only just looks good. Will still use linux tho. Not that anybody would care. Anyhow, I would like someone who knows his way around the forums and bug reporting, to suggest the change in the installer, or something. Or don't, I don't really care. I just care bout my data, just like anybody would.

Peace out.

---

### Post by Matthew_Smith on 2014-06-19
It probably deleted the windows partition and made it all Ubuntu. Next time click "manage partitions" and keep the windows partition as it is. Did you notice your Ubuntu drive getting bigger?

---

### Post by sudodus on 2014-06-19
I'm really sorry that this happened to you. A bug is reported about this issue, and we are many people who are very concerned, because things like this happen way too often. See this link

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

The safe way is to 

1. always ***back up*** the whole system or at least all important data before editing partitions and/or installing operating systems,

2. always use ***Something else*** at the partitioning window instead of the automatic install options, unless you intend to use the whole drive.

---

### Post by sudodus on 2014-06-19
If you want to try, there are two tools, that might help you recover at least some of the files:

***Testdisk***, which tries to restore the previous file system, and

***PhotoRec***, which can recover files without any file system.

See this link [http://www.cgsecurity.org/wiki/](http://www.cgsecurity.org/wiki/)

---

### Post by PondPuppy on 2014-06-19
+1 for Testdisk. It's saved files from drives of mine that nothing else would recognize.

---

### Post by Mark Phelps on 2014-06-19
> with a warning underneath it saying that it will delete all my Ubuntu programs, documents, blahblah. However, it didn't say a thing about wiping the entire freakin drive where I had tons of other stuff on my Windows partition.

Actually -- it DID -- if you had read it closely, you would have seen the phrase "... all other files." -- which means, ALL other files, including those in other partitions.

Admittedly, it's not very clear, and lots of folks don't bother to read the details, and it COULD be better worded -- and there is a bug report open on it, but that's little consolation when everything you have gets erased.

---

