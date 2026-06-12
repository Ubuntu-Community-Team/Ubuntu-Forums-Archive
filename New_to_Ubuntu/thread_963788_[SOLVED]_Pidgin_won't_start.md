---
title: "[SOLVED] Pidgin won't start"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by lolwhites on 2008-10-30
Since upgrading, I can't get Pidgin to start. When I try to run it in a terminal I get this:

> *** glibc detected *** pidgin: munmap_chunk(): invalid pointer: 0xb7d3db61 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75b23f4]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb77ebc06]
/usr/lib/libglib-2.0.so.0(g_string_free+0x5c)[0xb780800c]
/usr/lib/pidgin/nautilus.so[0xb6f0f27a]
/usr/lib/libpurple.so.0(purple_marshal_VOID__POINTER+0x28)[0xb7734713]
/usr/lib/libpurple.so.0(purple_signal_emit_vargs+0x168)[0xb77342d5]
/usr/lib/libpurple.so.0(purple_signal_emit+0x81)[0xb7734167]
/usr/lib/libpurple.so.0(purple_blist_update_buddy_status+0xd5)[0xb76ebd38]
/usr/lib/libpurple.so.0(purple_prpl_got_user_status+0x16e)[0xb7729e6d]
/usr/lib/purple-2/libjabber.so.0(jabber_presence_parse+0x14f5)[0xb6351d07]
/usr/lib/purple-2/libjabber.so.0(jabber_process_packet+0xbf)[0xb6341fc3]
/usr/lib/purple-2/libjabber.so.0[0xb634ed6d]
/usr/lib/libxml2.so.2[0xb7432238]
/usr/lib/libxml2.so.2(xmlParseChunk+0x619)[0xb743f189]
/usr/lib/purple-2/libjabber.so.0(jabber_parser_process+0xa0)[0xb634ef72]
/usr/lib/purple-2/libjabber.so.0[0xb6342953]
/usr/lib/libpurple.so.0[0xb773df0a]
pidgin[0x80ad7bf]
/usr/lib/libglib-2.0.so.0[0xb781a6fd]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb77e36f8]
/usr/lib/libglib-2.0.so.0[0xb77e6da3]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2)[0xb77e72c2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7af23a9]
pidgin(main+0xc78)[0x80caaaf]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7559685]
pidgin[0x806d8b1]

I can give the memory map too if it helps, but it's kinda long!

---

### Post by zzHanks on 2008-10-31
Hi.
I don't have a solution, but if you're going to use it for MSN you can download aMSN and use that instead.

Hope this helps.

---

### Post by lolwhites on 2008-10-31
No, I want to be able to use Google Talk and Yahoo too. I've found it works when run as sudo, but obviously it's not very safe!

---

### Post by coolbrook on 2008-10-31
What versions of Ubuntu and Pidgin are you running?  Have you tried removing and re-installing Pidgin?  Perhaps something has been corrupted.

---

### Post by lolwhites on 2008-10-31
Using version 2.5.2. Have tried removing and reinstalling several times to no effect.

However, it runs fine if I log in on my wife's account (same machine)

---

### Post by ezramorris on 2008-10-31
> **lolwhites said:**
> Using version 2.5.2. Have tried removing and reinstalling several times to no effect.

However, it runs fine if I log in on my wife's account (same machine)

Try this from a terminal:

```
cd ~
mv .purple .purple_old
```

This will reset your settings.

---

### Post by Gonzalo_VC on 2008-10-31
[COLOR="Navy"]I have (from the repository) version 2.4.1, how can I update to 2.5.2?
Thanks![/COLOR]

---

### Post by ezramorris on 2008-10-31
> **Gonzalo_VC said:**
> [COLOR="Navy"]I have (from the repository) version 2.4.1, how can I update to 2.5.2?
Thanks![/COLOR]

Hi,
Really, you should start a new thread, as this is not a related issue, however, there are several ways to do this, assuming you are using Hardy:
- Upgrade to Intrepid,
- Use the [_Ubuntu Backports repository_]("https://help.ubuntu.com/community/UbuntuBackports"), pin it down so not everything uses that, then install specifying the version,
- or download ([_i386_]("http://packages.ubuntu.com/hardy-backports/i386/pidgin/download")|[_amd64_]("http://packages.ubuntu.com/hardy-backports/amd64/pidgin/download")) and install the .deb file manually.

The third method is probably the easiest.

---

### Post by lolwhites on 2008-11-01
I moved .purple as ezamorris suggested and it started OK. However, as soon as I start adding accounts it freezes and "greys out".

---

### Post by lolwhites on 2008-12-29
Bump.

Can anyone help me sort this?

---

### Post by Tom--d on 2008-12-29
> **Gonzalo_VC said:**
> [COLOR="Navy"]I have (from the repository) version 2.4.1, how can I update to 2.5.2?
Thanks![/COLOR]

Enable Ubuntu Backports in Software Sources under Updates.

---

### Post by lolwhites on 2008-12-29
In my case, the problem doesn't seem to be with the version on Pidgin. It works fine when I log onto the same machine as a different user, although the program's settings appear to be the same.

I've even tried copying the .purple folder from another home directory into my own, but to no avail.

Edit: Solved. The problem was with the permissions in .gnome2/nautilus-sendto - for some reason I couldn't write to it.

---

### Post by ezramorris on 2008-12-30
> **lolwhites said:**
> Edit: Solved. The problem was with the permissions in .gnome2/nautilus-sendto - for some reason I couldn't write to it.

I'm glad you got this sorted. Please mark this thread as 'solved'. Thanks.

---

