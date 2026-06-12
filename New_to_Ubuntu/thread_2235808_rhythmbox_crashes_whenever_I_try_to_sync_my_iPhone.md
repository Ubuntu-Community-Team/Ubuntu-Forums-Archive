---
title: "rhythmbox crashes whenever I try to sync my iPhone"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by wrenchir on 2014-07-23
I got my iphone mounted just fine, and when I open rhythmbox I can see it listed under devices and I can look at the music that's already on it. But, whenever I try to sync it, after the dialog box that shows the graphics about how much space will be used, rhythmbox closes itself. 
I tried opening rhythmbox using the terminal, and right after it opens up it spits out these error messages:

[INDENT](rhythmbox:5438): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

(rhythmbox:5438): GLib-GObject-CRITICAL **: object SoupServer 0x2b3f8a0 finalized while still in-construction

(rhythmbox:5438): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
Unable to open ~/.mtpz-data for reading, MTPZ disabled.libitdbprep: itdb_iphone_start_sync called with uuid=a21f53221f57269fc21dfa9ba199fce4daa4084f
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

(rhythmbox:5438): Rhythmbox-CRITICAL **: playlist_track_added: assertion 'track != NULL' failed

(rhythmbox:5438): Rhythmbox-CRITICAL **: playlist_track_added: assertion 'track != NULL' failed

** (rhythmbox:5438): CRITICAL **: itdb_splr_validate: assertion 'at != ITDB_SPLAT_UNKNOWN' failed

(rhythmbox:5438): GLib-WARNING **: (/build/buildd/glib2.0-2.40.0/./glib/gerror.c:381):g_error_new_valist: runtime check failed: (domain != 0)

(rhythmbox:5438): Rhythmbox-WARNING **: Could not write database to iPod: Unsupported checksum type

[/INDENT]
I don't know what any of that means, is there any way to make my iphone play nice with ubuntu? There is [a thread]("http://ubuntuforums.org/showthread.php?t=1885131&highlight=rhythmbox+crashes+sync+iPhone") really similar to this from 2011, but the conclusion they all came to was that there's nothing to be done about this. I was hoping that, because three years have passed, a solution might be available now.

---

### Post by MidnightGrey on 2014-07-23
Hi,

What version is your iPhone?

this line: (rhythmbox:5438): Rhythmbox-WARNING **: Could not write database to iPod: Unsupported checksum type

Suggest to me that your iPhone is one of the newer versions which prevents any software from syncing to your device except for Apple's own iTunes.
This is a form of DRM and there is little you can do about it except to install iTunes.

---

### Post by wrenchir on 2014-07-24
Yeah, my phone is a 5s. Is there an easy way to insall iTunes on ubuntu? Or do I have to dual boot and use windows when I want to sync my phone?

---

### Post by MidnightGrey on 2014-07-25
If you dont want to use windows. You can install iTunes via WINE or playonlinux.
I do not use iTunes in linux so i am not to familiar with the options available.

---

### Post by Vladlenin5000 on 2014-07-25
> **MidnightGrey said:**
> If you dont want to use windows. You can install iTunes via WINE or playonlinux.
I do not use iTunes in linux so i am not to familiar with the options available.

Don't bother to try this. At best you'll end up with a glorified media player, just another one. It won't let you sync or even access the store.
Bottom line: If you really need it install Windows in a VM or dual boot.

---

