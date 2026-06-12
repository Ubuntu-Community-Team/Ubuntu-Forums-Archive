---
title: "Creating a Kernel Branch"
date: 2009-02-17
forum: Programming Talk
---

### Post by Spenser_Gilliland on 2009-02-17
Hi,

I'm working on developing some kernel drivers for the FPGA hardware I'm using in my research.  I'd like to create a branch of the Linux Kernel on my personal git server and have it consistently be in sync with latest version. How would one go about setting up such a repo? I'm using gitosis to admin the git server and it is doing a great job hosting my other repos.

Spenser

---

### Post by the_unforgiven on 2009-02-17
Just clone Linus' repo from:
git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
and setup a daily cron job to pull changes from it - using *git pull*.

---

