---
title: "Xlib record extension and Tkinter conflict?"
date: 2008-02-29
forum: Programming Talk
---

### Post by nanotube on 2008-02-29
Hi everyone

I am coming up against a problem that seems to be due to a conflict
between the Xlib record extension and Tkinter.

I have the event hooking code using python-xlib record running in
thread, and it works fine - until the tkinter gui comes up, at which
point it seems that no events get through to the recording thread, but
instead are backed up somewhere. when the gui closes, all the events
suddenly pile through to the xlib event recorder.

I am not very familiar with this whole event loop deal in X, so I am not
sure how to proceed.

The code is for a sourceforge-hosted open source project,
pykeylogger, which I'm trying to port to linux (with the help of another guy).

Here's the link to the CVS repository for the linuxport branch, please
take a look, or even check the code out and try running it so you can
see what is happening...

[http://pykeylogger.cvs.sourceforge.net/pykeylogger/pykeylogger/?pathrev=linuxport](http://pykeylogger.cvs.sourceforge.net/pykeylogger/pykeylogger/?pathrev=linuxport)

I am using the latest python-xlib release (0.14), python 2.5, on ubuntu
7.04 (feisty).

Any comments, hints, or suggestions would be appreciated! if you need me to clarify anything about the code structure etc., let me know.

P.S. I have posted this same question on python-xlib-users mailing list, but not sure if I'll get any replies, since it seems to be rather low-volume...  For your reference, here's a link to the thread in the list archive: [http://sourceforge.net/mailarchive/forum.php?thread_name=47C5D04F.3050406%40gmail.com&forum_name=python-xlib-users](http://sourceforge.net/mailarchive/forum.php?thread_name=47C5D04F.3050406%40gmail.com&forum_name=python-xlib-users)

---

### Post by nanotube on 2008-03-01
bump...

---

### Post by nanotube on 2008-03-03
bump again...?
are there any tkinter experts out here? i do strongly suspect it has something to do with tkinter not properly releasing events, or interfering somehow with the other thread...

---

### Post by nanotube on 2008-03-03
still need help...! :)

---

### Post by nanotube on 2008-03-05
bump?

---

### Post by nanotube on 2008-03-07
never mind, after teasing at it and playing around for a while, i figured out what the problem was. 

if anyone is curious, it had nothing to do with tkinter conflicting with xlib... just that the onkeydown function was not exiting when it was calling the gui (which didn't use to cause problems under win with the pyhook module, probably because that one ran the onkeydowns in separate threads...)

so look forward to a linux-capable release of pykeylogger soon (if you care), after i refactor the code some more.

and if you were counting... yes, i just made 6 posts into a thread all by myself, and it was all for nothing. :)

---

