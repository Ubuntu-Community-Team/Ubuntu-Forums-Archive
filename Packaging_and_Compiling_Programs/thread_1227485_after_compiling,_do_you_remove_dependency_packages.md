---
title: "after compiling, do you remove dependency packages?"
date: 2009-07-30
forum: Packaging and Compiling Programs
---

### Post by PGScooter on 2009-07-30
Hi,

Sometimes I get careless and install a lot of packages (30 mb?) in order to compile a program and do not remove them after. If I do not plan on compiling that same program again (or a different version) in the future, is it important to remember to remove these packages? I'm not worried about disk space, more so of just keeping unnecessary packages around.

What do you do?

---

### Post by ibutho on 2009-07-30
I just keep the dependencies because I am not bothered about disk space.

---

### Post by PGScooter on 2009-07-31
hi ibutho,

Thanks for the reply. I think I was unclear. I put the "30mb" just to show that I mean a lot of packages, which was a bad idea cause maybe it was just one big package. My main concern is that there will be some sort of conflict between the packages that I do want to use. Can the clutter of having a lot of packages be bad even if space is not a concern?

---

### Post by ibutho on 2009-07-31
Most of the dependencies you install when compiling from source, are dev files (libraries) which are separate from your normal "applications", so they do not usually cause conflicts with other packages. I don't know whether "clutter" is considered bad, but remember that in the past most Linux users compiled their own software (and the disks then were a lot smaller at that time) and this wasn't classed as cluttering a system.

---

### Post by PGScooter on 2009-07-31
> **ibutho said:**
> Most of the dependencies you install when compiling from source, are dev files (libraries) which are separate from your normal "applications", so they do not usually cause conflicts with other packages. I don't know whether "clutter" is considered bad, but remember that in the past most Linux users compiled their own software (and the disks then were a lot smaller at that time) and this wasn't classed as cluttering a system.

ah, interesting stuff. Great, I am reassured now!

---

