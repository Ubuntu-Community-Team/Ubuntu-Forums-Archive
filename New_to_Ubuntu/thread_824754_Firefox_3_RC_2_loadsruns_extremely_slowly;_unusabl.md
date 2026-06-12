---
title: "Firefox 3 RC 2 loads/runs extremely slowly; unusable"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by CA_Warren on 2008-06-10
Firefox 3 RC 2 came to me via the update manager the other night (not sure if this was userland-wide or not, I have some less-usual repo's active), and it's unfathomably slow. As in many minutes simply to load, and freeze-age when attempting to do anything in it (even select it to view Help->About).

Here's the only output from the CLI when running it:

```
GCJ PLUGIN: thread 0x805f158: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f158: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f158: NP_GetValue
GCJ PLUGIN: thread 0x805f158: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f158: NP_GetValue return
GCJ PLUGIN: thread 0x805f158: NP_GetValue
GCJ PLUGIN: thread 0x805f158: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f158: NP_GetValue return
```


It seems to hang for a long while after the following lines of stack trace:

```
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 49
fcntl64(49, F_SETFD, FD_CLOEXEC)        = 0
setsockopt(49, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
connect(49, {sa_family=AF_INET, sin_port=htons(16001), sin_addr=inet_addr("127.0.0.1")}, 16   
```


Any help would be much appreciated - this is puzzling me. I'd be happy to send anyone the full stack trace who's interested - the forums won't let me upload it as an attachment (too big).

Running on Kubuntu 8.04 w/KDE 3.5x, Compaq x1000 w/Intel Centrino processor.

---

### Post by hyper_ch on 2008-06-10
I'd delete the urlclassifier.sqlite file in the profile and restart ff.

---

### Post by CA_Warren on 2008-06-10
Thanks for the reply.

Tried deleting urlclassifier.sqlite, still behaving the same. Any other thoughts?

---

### Post by jsoreno on 2008-06-10
Is there any remedy of that?help would be much apreciated. . thank you. .

---

### Post by hyper_ch on 2008-06-10
nope, no other idea

---

### Post by jeremy on 2008-06-10
You could try renaming ~/.mozilla and starting ff. You can always delete the new  ~/.mozilla that ff will create when it starts and rename the old one back.

---

### Post by CA_Warren on 2008-06-10
The plot thickens - tried renaming ~/.mozilla, but it didn't fix the issue. Takes just as long to start/do anything.

So this is an installation issue, not something to do with my extensions/profile. Very strange.

Will update as I continue to try more things.

---

### Post by n1ywb on 2008-06-12
Ditto this problem. It's EXTREMELY annoying. FF takes FOREVER to load, and FOREVER to do anything once loaded. I'm falling back to FF 2 in the meantime, it does not seem to be affected.

I've deleted ~/.mozilla and /etc/firefox-3.0, uninstalled all firefox related packages, reinstalling the vanilla ff3 package, all to no avail.

It looks like it might be a sound related problem, possibly some ESD call that takes forever to time out? Take a look at this GDB output... This is the only thread that seems to be hung up on something.

(gdb) bt
#0  0xb7f70410 in __kernel_vsyscall ()
#1  0xb7f51c38 in connect () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f5174a in ?? () from /usr/lib/libesd.so.0
#3  0xb5f51e82 in esd_open_sound () from /usr/lib/libesd.so.0
#4  0xb625ff66 in ?? () from /usr/lib/libgnome-2.so.0
#5  0xb625ff87 in gnome_sound_connection_get () from /usr/lib/libgnome-2.so.0
#6  0xb634bb45 in ?? () from /usr/lib/libgnomeui-2.so.0
#7  0xb6c41b20 in ?? () from /usr/lib/libgobject-2.0.so.0
#8  0xb6c43916 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#9  0xb6c43c59 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#10 0xb6969837 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7810418 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#12 0xb781a6f7 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#13 0xb76aa09c in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#14 0xb76abf18 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#15 0xb76ae736 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#16 0xb7667a3b in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#17 0xb7667afb in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#18 0xb7668660 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#19 0xb7668670 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#20 0xb766928c in ?? () from /usr/lib/xulrunner-1.9/libxul.so
---Type <return> to continue, or q <return> to quit---
#21 0xb715e919 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#22 0xb73b5101 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#23 0xb73b23f5 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#24 0xb73b8651 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#25 0xb78dd12a in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#26 0xb78ac717 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#27 0xb782dc06 in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#28 0xb76bd89e in ?? () from /usr/lib/xulrunner-1.9/libxul.so
#29 0xb7112688 in XRE_main () from /usr/lib/xulrunner-1.9/libxul.so
#30 0x08049033 in ?? ()
#31 0xb7ce4450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#32 0x08048cc1 in ?? ()

---

### Post by murjam on 2008-07-11
I have absolutely same problems on Xubuntu 8.04 IBM X41. Does anybody have more ideas?

---

### Post by n1ywb on 2008-07-11
My problem was that my loopback network interface was broken.

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/240337](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/240337)

I found a typo in my /etc/network/interfaces file that was preventing it from coming up. After I fixed the typo and restarted networking, and verified that my loopback interface was working OK, firefox started working again.

---

### Post by murjam on 2008-07-12
Thank You, n1ywb!! My /etc/network/interfaces file was a bit messed and I got an error when typed
```
sudo ifup lo
```
Now it is fixed and FF3 runs well \\:D/

---

