---
title: "Fuser high CPU usage"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by InsertNameHere on 2011-10-19
Hi, for some reason fuser is always running itself (seemingly randomly)

Here it is in top (CPU usage is generally high):
 2749 root      20   0  7516  836  668 S   63  0.0   0:02.13 fuser

I tried killing it with kill 9 and that didnot work

Here's syslog entries showing fuser


Oct 20 05:49:03 anger kernel: grsec: failed fork with errno ENOMEM by /bin/fuser[fuser:2749] uid/euid:0/0 gid/egid:0/0, parent /usr/bin/find[find:2744] uid/euid:0/0 gid/egid:0/0
Oct 20 05:49:03 anger kernel: last message repeated 4 times
Oct 20 05:49:03 anger kernel: grsec: more alerts, logging disabled for 10 seconds

Here's a search for fuser in cron

root@anger:/etc# grep -r "fuser" *
bash_completion.d/fuse:have fusermount &&
bash_completion.d/fuse:_fusermount()
bash_completion.d/fuse:complete -F _fusermount fusermount
grep: blkid.tab: No such file or directory
cron.d/php5:09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
grep: fonts/conf.d/30-defoma.conf: No such file or directory
root@anger:/etc#

and 

this line apparantly is running it


09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

what would happen if I turn that off?

By the way, I have a few thousands of zombie processes running when fuser is running.

Also is this amount of RAM usage normal for a server:
root@anger:/etc/cron.d# free -m
             total       used       free     shared    buffers     cached
Mem:         15983      15704        278          0        274      12203
-/+ buffers/cache:       3226      12756
Swap:          510          0        510

I'm only running a few srcds instances which shouldn't be RAM intensive.

Thanks

---

### Post by grazer on 2011-10-20
We have the same problem.  This is the content of /etc/cron.d/php5 on 11.10:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
```

And this is the content on 11.04:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete
```

Spot the difference?

The 11.10 version runs fuser for each PHP session file, thus using all the CPU when there are hundreds of sessions.

---

### Post by TrevorBradley on 2011-10-23
Looking at my own logs, I believe this is the cause of my computer to nearly hard crash three times in the past three days - black screen, apache process killed as well as my Minecraft process, though this last time ssh and mythbackend stayed up.  

Pouring through my syslog, this appears to be the culprit.  I'm switching back to the 11.04 version to see if it fixes it.

EDIT: specifically, my offending syslog lines were:

> Oct 23 16:39:01 alexandria CRON[29029]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/de
v/null \; -delete)
Oct 23 16:39:11 alexandria kernel: [153263.109183] fuser invoked oom-killer: gfp_mask=0x40d0, order=0, oom_adj=0, oom_score_adj=0
Oct 23 16:39:11 alexandria kernel: [153263.109191] fuser cpuset=/ mems_allowed=0
Oct 23 16:39:11 alexandria kernel: [153263.109196] Pid: 6005, comm: fuser Tainted: P            3.0.0-12-generic-pae #20-Ubuntu
Oct 23 16:39:11 alexandria kernel: [153263.109199] Call Trace:
Oct 23 16:39:11 alexandria kernel: [153263.109209]  [<c10ead55>] dump_header.isra.7+0x85/0xc0
Oct 23 16:39:11 alexandria kernel: [153263.109214]  [<c10eafac>] oom_kill_process+0x5c/0x80
Oct 23 16:39:11 alexandria kernel: [153263.109218]  [<c10eb39f>] out_of_memory+0xbf/0x1d0
Oct 23 16:39:11 alexandria kernel: [153263.109223]  [<c10ef293>] __alloc_pages_nodemask+0x6c3/0x6e0
Oct 23 16:39:11 alexandria kernel: [153263.109229]  [<c1121c6b>] allocate_slab+0xbb/0xd0
Oct 23 16:39:11 alexandria kernel: [153263.109232]  [<c1121ca7>] new_slab+0x27/0x110
Oct 23 16:39:11 alexandria kernel: [153263.109236]  [<c1122674>] ? deactivate_slab+0x34/0x70
Oct 23 16:39:11 alexandria kernel: [153263.109241]  [<c1544e0d>] __slab_alloc.constprop.65+0xbf/0x191
Oct 23 16:39:11 alexandria kernel: [153263.109245]  [<c1541009>] ? copy_signal+0x2c/0x205
Oct 23 16:39:11 alexandria kernel: [153263.109249]  [<c1122b05>] kmem_cache_alloc+0x135/0x140

---

### Post by kongo09 on 2011-11-04
Any further insights on this? One one of our servers, fuser regularly takes 9999% of CPU and we quickly ramp up to thousands of zombie processes. At the same time, our jvm runs out of memory (at 16GB). That was not the case on Ubuntu 10.10 we were running before (at 8GB RAM, same setup, same tasks).

People seem to take out the fuser part: [http://ubuntuforums.org/showthread.php?t=1862472](http://ubuntuforums.org/showthread.php?t=1862472)

---

### Post by gedrox on 2011-11-14
> **grazer said:**
> We have the same problem.  This is the content of /etc/cron.d/php5 on 11.10:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
```And this is the content on 11.04:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete
```Spot the difference?

The 11.10 version runs fuser for each PHP session file, thus using all the CPU when there are hundreds of sessions.
Did anyone actually try changing this CRON command back so it doesn't run fuser command?

---

### Post by TrevorBradley on 2011-11-14
I did remove fuser from cron (using the suggestion above) soon after I last posted and waited a few days to see if it was effective... the problem vanished completely.

---

### Post by greggatghc on 2011-12-29
> **TrevorBradley said:**
> I did remove fuser from cron (using the suggestion above) soon after I last posted and waited a few days to see if it was effective... the problem vanished completely.

Same thing here.  There is also a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387)

More people should put their voice there so it gets fixed.

---

### Post by robinkc on 2013-05-02
Saved my life too.

> **greggatghc said:**
> Same thing here.  There is also a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387)

More people should put their voice there so it gets fixed.

---

### Post by coffeecat on 2013-05-02
Old thread closed.

---

