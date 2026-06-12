---
title: "Login Window won't stay open"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-13
Hey guys, Ubuntu Hardy here...

I can't seem to open the Login Window.  I want to customize my login window.

I click on "Login Window" under "system - administration" but it only opens for a split second then closes.  The file that the login window refers to is: gdmsetup in "usr/sbin."

Anybody have an idea how I can get that open and why it keeps closing?

---

### Post by RussW210 on 2008-09-13
When I try to open the Login Window from the terminal by typing sudo /usr/sbin/gdmsetup I get the following message int he terminal:

"Segmentation fault"

Hmm...

---

### Post by RussW210 on 2008-09-13
Anybody?

---

### Post by Higgo on 2008-10-14
Did you ever get this sorted out? I have the same problem however I do not receive any error messages from the terminal. However the syslog reports:

Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async) 

Using Hardy 64

---

### Post by Madmoose on 2008-11-12
As of today 11/11/07 I'm having this issue.

Did 8.10 fix this issue?

Thanks moose

---

### Post by Tatty on 2008-11-12
> **Higgo said:**
> Did you ever get this sorted out? I have the same problem however I do not receive any error messages from the terminal. However the syslog reports:

Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed 
Oct 14 19:05:03 desktop gdmsetup[23388]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async) 

Using Hardy 64

This is a slightly different problem to the OP problem as if it was segfaulting then it would report it in the terminal.

Segfaults can be caused by either programming errors or hardware problems.  It is quite often because of failing RAM.

---

### Post by Higgo on 2008-11-13
Well the problem just went away...


Not sure what happened. Everything is running sweet again.

---

### Post by Glubbdubdribian on 2008-11-14
I have exactly the same problem - keeps coming up with segmentation fault. I'll reboot now and say if it goes away..


... yep, working again.. seems this can just be solved by rebooting :)

---

### Post by mbsimcity on 2009-01-26
I am encountering this issue with 8.04.1 and kernel 2.6.24-23.  Exact same symptoms as what Russ mentioned.  Unfortunately, rebooting did nothing for me.

After posting this message I found this [http://ubuntuforums.org/archive/index.php/t-927195.html]("http://ubuntuforums.org/archive/index.php/t-927195.html").  Interestingly, people noticed that if they removed the blank CD from their drive the problem went away.  So I checked my drive, and sure enough I had a DVD-R disk sitting there.  Removed it, closed the drive, and *poof* no more errors.

---

### Post by Cresho on 2009-02-28
thanks....i was about to reinstall and removing my blank cd after burning with k3b ...fixed the problem.

not sure if k3b is to blame...i never seen this problem before and had tons of blank cd's in the drive.  

thanks...

---

### Post by heminder on 2009-03-11
that's strange, i was having this exact same problem...

```
heminder@Haspire:~$ gksu /usr/sbin/gdmsetup
gdmsetup[6669]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failedgdmsetup[6669]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[6669]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[6669]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

```

i removed a blank CD, which was in my drive, and it loaded fine...

---

### Post by AndrewB on 2009-04-01
What a crazy bug. I too had the same problem. Removed the CD and it'sworking again.

---

### Post by sanz on 2009-06-27
Tks a hell lot!

I happened to have one blank disk in my cdrom, which i'd almost forgot it there. remove it, the gdmsetup dialogue is back.

what a funny bug

---

### Post by krow436 on 2009-06-27
That is a funny bug lol.  Did you ever submit it in a bug report?  It doesn't seem like a critical problem, but almost a little embarrassing.  I can't even really think of how the two could possibly be related haha.

---

