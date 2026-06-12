---
title: "[SOLVED] Login window crashes"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by k33bz on 2008-10-26
I wanted to change my login window, but when I pull up the management tool to do so, it crashes. I ran it in the terminal to see what I could see and this is what I get:
```
keebler@k33bz-mobile:~$ gksu /usr/sbin/gdmsetup
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failedgdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[19281]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

```


some how it fixed itself, not sure how

---

