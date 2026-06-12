---
title: "dd process (continued)"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by wittelw on 2008-11-18
Just got bit tonight by a runaway dd process and couldn't post to [http://ubuntuforums.org/showthread.php?t=706804](http://ubuntuforums.org/showthread.php?t=706804) since it is archived so am continuing here.

What I found was the following (64-bit Intrepid):

1) dd is running after startup, but sleeping (as shown in System Monitor)
2) dd was started with the following command line (seems legit):

 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg

3) My syslog had grown to > 690MB and was filled with the following (just did a tail -n 4000 syslog because the GUI log viewer hangs when started):

```
Nov 18 19:02:40 waltwld5 kernel: [73477.481061] bad: scheduling from the idle thread!
Nov 18 19:02:40 waltwld5 kernel: [73477.481075] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
Nov 18 19:02:40 waltwld5 kernel: [73477.481079] 
Nov 18 19:02:40 waltwld5 kernel: [73477.481081] Call Trace:
Nov 18 19:02:40 waltwld5 kernel: [73477.481094]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 18 19:02:40 waltwld5 kernel: [73477.481101]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 18 19:02:40 waltwld5 kernel: [73477.481106]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 18 19:02:40 waltwld5 kernel: [73477.481115]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 18 19:02:40 waltwld5 kernel: [73477.481124]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 18 19:02:40 waltwld5 kernel: [73477.481131]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 18 19:02:40 waltwld5 kernel: [73477.481136] 
Nov 18 19:02:40 waltwld5 kernel: [73477.488138] bad: scheduling from the idle thread!
Nov 18 19:02:40 waltwld5 kernel: [73477.488149] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
Nov 18 19:02:40 waltwld5 kernel: [73477.488153] 
Nov 18 19:02:40 waltwld5 kernel: [73477.488154] Call Trace:
```

I don't have any idea what started this off, but it ended up taking down my machine (once I tried to launch the GUI System Log) and I had to hold down the power button to reboot.

If anyone knows what might have caused this (and even better how to prevent it in the future) I'd appreciate a heads-up :)

---

### Post by bscbrit on 2008-11-19
I'm wondering if the system got confused over the way that you entered the command line.  You should, according to the man page, use the following format for 'if' and 'of':
```
 if=/path/to/file of=path/to/another/file
```

You omitted the '='. Perhaps the system read the command line that you entered using if, of, and the 2 specified paths each as separate arguments?

---

