---
title: "sbackup config gui won't load"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by wxturtle on 2008-11-10
Installed Simple Backup .10.4 (or whatever the latest version is now) a couple times-- the Config GUI will not open; it flashes a window, then a starting notification hangs in the bar, then nothing happens.

Running it in the terminal does this:

> 
colin@DESKTOP:~$ gksu simple-backup-config

(simple-backup-config:32618): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(simple-backup-config:32618): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

Any ideas how to interpret this?

---

### Post by Paqman on 2008-11-11
Looks pretty broken. Try reinstalling it in Synaptic.

---

### Post by wxturtle on 2008-11-11
> **Paqman said:**
> Looks pretty broken. Try reinstalling it in Synaptic.

Have done repeatedly.

Nothing.

---

