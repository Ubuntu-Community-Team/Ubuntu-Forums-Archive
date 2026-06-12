---
title: "kernel module programming: how to get rid of a stubborn /proc entry?"
date: 2008-12-01
forum: Programming Talk
---

### Post by Cracauer on 2008-12-01
There doesn't seem to be a kernel programming subforum, so let me try here.

During the uptime of my system I had a bad module on there that didn't properly unregister it's /proc entry. Namely VMWare, vmnet.ko as included with vmware 6.0 and 6.5 doesn't unregister /proc/vmnet properly in 2.6.26.  As a result I had multiple /proc/vmnet files (all on the same name) after I repeatedly tried to make it run.

I clean up things with a module that does this:

```

void
cleanup_module()
{
  int ret = 0;
  remove_proc_entry("vmnet", NULL);
  printk("FOO: removing resulted in %d\n", ret);
}

```

This gets rid of all of them, but not the last, there's still one /proc/vmnet left :confused:

So, what's going on there? Why is one left?

And why does remove_proc_entry not return any kind of error code? Is there any kind of diagnostic mechanism that I can ask from the kernel as to why it won't remove the sucker?

Is there some `lsof` for /proc files?

%%

Also, I have vmblock.ko stuck in the kernel with a ref count of 3. But all other vmware modules are gone and no vmware processes are running. Any idea what couple be blocking that one?

---

### Post by dwhitney67 on 2008-12-01
Have you tried rebooting to see if the files go away?

What were your issues with VMware?  I am currently using VMware Server 2.0 (and previously 2.0-pre-release), and I had no issues with VMware.

The only thing noteworthy is that VMware mildly complains (more of a heads-up notification) that the kernel (2.6.24.22-generic) was compiled with GCC 4.2.3, yet GCC 4.2.4 is installed on my system.

---

### Post by Cracauer on 2008-12-01
> **dwhitney67 said:**
> Have you tried rebooting to see if the files go away?



Over my dead body :)

Of course that will work, but I really don't want to reboot this thing. If I did I could just go back to kernel 2.6.24, which worked fine (when I verified that 2.6.26 did what I want I only compiled/installed vmware, which is usually sufficient).

> **dwhitney67 said:**
> 

What were your issues with VMware?  I am currently using VMware Server 2.0 (and previously 2.0-pre-release), and I had no issues with VMware.



2.6.26 disables VMware 6.0<something>. Then I went with vmware-any-any-117d (couldn't fine 117e which seems to exist). That one seems to have left the bad /proc entry, apparently because of the way if uses the proc_root argument when removing /proc files which seems to have changed semantics in 2.6.26.

Upgrading to vmware-6.5 I can install (without vmware-any-any) but not run. This seems to be due to the messed up /proc.

> **dwhitney67 said:**
> 

The only thing noteworthy is that VMware mildly complains (more of a heads-up notification) that the kernel (2.6.24.22-generic) was compiled with GCC 4.2.3, yet GCC 4.2.4 is installed on my system.

This is all on gcc-4.1.2, both the installed kernel and the module.


I think all the above is fine, except that the Linux kernel doesn't give any kind of error code from removing /proc entries. That's pretty lousy, IMHO.

---

### Post by mmix on 2008-12-01
[http://www.ibm.com/developerworks/linux/library/l-proc.html](http://www.ibm.com/developerworks/linux/library/l-proc.html)

```
extern void *remove_proc_entry(
   const char            *name,
   struct proc_dir_entry *parent);
```

HTH

---

### Post by Cracauer on 2008-12-01
> **mmix said:**
> [http://www.ibm.com/developerworks/linux/library/l-proc.html](http://www.ibm.com/developerworks/linux/library/l-proc.html)

```
extern void *remove_proc_entry(
   const char            *name,
   struct proc_dir_entry *parent);
```

HTH

As I did in the first post...

---

### Post by mmix on 2008-12-02
> **Cracauer said:**
> As I did in the first post...

```
remove_proc_entry("vmnet", **NULL**);
```

> 
[http://www.ibm.com/developerworks/linux/library/l-proc.html](http://www.ibm.com/developerworks/linux/library/l-proc.html)

To remove a file from /proc, use the remove_proc_entry  function. To use this function, provide the file name string as well as the location of the file in the /proc filesystem (its parent). 

---

### Post by Cracauer on 2008-12-02
> **mmix said:**
> ```
remove_proc_entry("vmnet", **NULL**);
```

That's my change, there was procfs_root in there before my change. It worked for the additional files but not the last one.

---

