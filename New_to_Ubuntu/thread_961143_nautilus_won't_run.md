---
title: "nautilus won't run"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-10-28
Every time I try to run Nautilus, either in a normal Terminal or in a Root Terminal, I get the same message, and nautilus does not run. I tried reinstalling all the nautilus programs using Synaptic Package Manager, but that did no good. Does anyone have any idea how to fix Nautilus?  

JBA2337

Here is what I get when I try to run nautilus from a terminal prompt:

username@home #$   nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:7081): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7081): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7081): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7081): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
username@home #$

---

### Post by Malta paul on 2008-10-28
You could try 'Alt F2' enter 'gksudo nautilus' 
Careful you are now in permanent root! :)

---

### Post by cyberfin on 2008-10-28
I invite you to take a look at this thread which deals with the same issue:

[http://ubuntuforums.org/showthread.php?t=927195]("http://ubuntuforums.org/showthread.php?t=927195")

It's not solved but if we keep on bumpin' they can't ignore us forever!

G'day.

---

### Post by JBA2337 on 2008-10-28
To: cyberfin 

Thank you for your help.
Also, the previous writer, malta paul, suggested that I press 'Alt F2' and then enter 'gksudo nautilus'. This works.

Maybe someone else will come up with a permanent solution, and let us know. 

JBA2337

---

