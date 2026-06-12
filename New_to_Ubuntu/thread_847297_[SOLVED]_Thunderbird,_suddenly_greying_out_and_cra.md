---
title: "[SOLVED] Thunderbird, suddenly greying out and crashing today out the blue. Anyone el"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by philinux on 2008-07-02
Had to force quit 4 times. Disabled addons to get messages through, then still crashed opening some. 

Bugged it at launchpad as apport caught one.

---

### Post by finer recliner on 2008-07-02
maybe something in your personal settings is corrupt. 

try renaming your ~/.mozilla-thunderbird directory to something else temporarly, now recreate your account(s) and see if the problem goes away. you can rename your original .mozilla-thunderbird directory back to the original name if you want to recover your original settings/messages/addresses.

---

### Post by sydbat on 2008-07-02
This happened to me about two months ago. It turned out to be sound files when receiving messages. I can't remember where I saw the post (here or another forum), but it has to do with Thunderbird trying to access any sound file (even it's own) and having a big problem when doing so. Do you have any sound files enabled that you use when getting your messages? If so, disable them and see if that clears up the problem.

To do this, open Thunderbird and, as quickly as possible, stop incoming messages (as this is where the problem lies). Then go to Edit > Preferences > General tab and uncheck "Play Sound When Messages Arrive". Should keep it from crashing, if this is the problem.

---

### Post by philinux on 2008-07-02
It's the webmail addon, with it disabled no problem.

I've got proposed repo's active for testing it could be that.

---

### Post by philinux on 2008-07-03
Anyone else got this.

I've disabled check mail on start up for the hotmail account and got it running.

If I check mail on hotmail is greys out then have to force quit.

---

### Post by sydbat on 2008-07-03
I suspect it's something to do with Hotmail. Can you access Hotmail through Firefox? Maybe they upgraded something that changed a setting and you have to re-set it for proper download to email clients.

---

### Post by philinux on 2008-07-03
> **sydbat said:**
> I suspect it's something to do with Hotmail. Can you access Hotmail through Firefox? Maybe they upgraded something that changed a setting and you have to re-set it for proper download to email clients.

Yeah hotmail fine directly.

Usually when the webmail fails you get a "bad vibes" error message but never crashing TB.

---

### Post by sandy_marshall on 2008-07-03
I'm getting the same problem with having to force quit thunderbird regularly for last 3 days. I'm also using webmail addon for Hotmail and Gmail.

Disabled Gmail account but still getting problems.

---

### Post by philinux on 2008-07-03
If I enable logging for webmail it just hangs instead of greying out.

But, arrgghh, it dont produce any logs.

Running TB from terminal no good either.

---

### Post by sydbat on 2008-07-03
Do you dual-boot with Windows? If so, and you have TB installed in Windows, see if you have any problems there.

Also, which versions of Ubuntu and TB are you running? There might be an incompatibility with 32 or 64 bit.

---

### Post by philinux on 2008-07-03
> **sydbat said:**
> Do you dual-boot with Windows? If so, and you have TB installed in Windows, see if you have any problems there.

Also, which versions of Ubuntu and TB are you running? There might be an incompatibility with 32 or 64 bit.

I'm only running Hardy 64 bit. TB and webmail been fine since I installed hardy. Never had any bother. Only this week like some others have. version 2.0.0.14 (20080505)

---

### Post by sydbat on 2008-07-03
I'm out of ideas. Sorry. My guess is that you will have to get your Hotmail online for a bit until the Mozilla team get the bug figured out. You did report it, correct?

---

### Post by Efros on 2008-07-03
They were having problems with the hotmail part of the webmail addon the other day as microsoft had changed something to do with their website. I updated to this [Link]("http://thunderbird-webmail-extension.googlegroups.com/web/gmail-0-6-0b7.zip?gda=KyhNTUIAAACuiVRJBnHmnZfVFrMSrK4IeofiQ-SGo2Z3srX19mx0dWG1qiJ7UbTIup-M2XPURDT0yLkJ9HolR2-CXui1Oy_yR3EF-MqJXdm-zvpgwRZgvQ") and used webdav in the hotmail setup has worked fine ever since.

---

### Post by philinux on 2008-07-03
Got a back trace for the first time ever. I've raised a bug.
[https://bugs.launchpad.net/ubuntu/+bug/245296](https://bugs.launchpad.net/ubuntu/+bug/245296)

```
thunderbird
*** glibc detected *** /usr/lib/thunderbird/thunderbird-bin: double free or corruption (out): 0x0000000001cb0720 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fac0bd1a08a]
/lib/libc.so.6(cfree+0x8c)[0x7fac0bd1dc1c]
/usr/lib/thunderbird/libmozjs.so[0x7fac0f6d6fe5]
/usr/lib/thunderbird/libmozjs.so[0x7fac0f6907e1]
/usr/lib/thunderbird/libmozjs.so(JS_GC+0x2a)[0x7fac0f66811a]
/usr/lib/thunderbird/components/libgklayout.so[0x7fac009e7219]
/usr/lib/thunderbird/components/libgklayout.so[0x7fac009e5ea1]
/usr/lib/thunderbird/components/libgklayout.so[0x7fac009f592b]
/usr/lib/thunderbird/components/libgklayout.so[0x7fac009f59e7]
/usr/lib/thunderbird/libxpcom_core.so[0x7fac0f1f097e]
/usr/lib/thunderbird/libxpcom_core.so[0x7fac0f1f102a]
/usr/lib/thunderbird/libxpcom_core.so(PL_HandleEvent+0x19)[0x7fac0f1ecb39]
/usr/lib/thunderbird/libxpcom_core.so(PL_ProcessPendingEvents+0x4b)[0x7fac0f1ecddb]
/usr/lib/thunderbird/libxpcom_core.so[0x7fac0f1eebab]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x7fac0267dfe2]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7fac0cce0262]
/usr/lib/libglib-2.0.so.0[0x7fac0cce3516]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1b7)[0x7fac0cce37d7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x7fac0e284f03]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x7fac0267e395]
/usr/lib/thunderbird/components/libtoolkitcomps.so[0x7fac0176cf2e]
/usr/lib/thunderbird/thunderbird-bin[0x40781b]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7fac0bcc41c4]
/usr/lib/thunderbird/thunderbird-bin[0x4039a9]
======= Memory map: ========
00400000-00415000 r-xp 00000000 08:01 16457                              /usr/lib/thunderbird/thunderbird-bin
00615000-00617000 rw-p 00015000 08:01 16457                              /usr/lib/thunderbird/thunderbird-bin
00617000-01d4e000 rw-p 00617000 00:00 0                                  [heap]
403a7000-403a8000 ---p 403a7000 00:00 0 
403a8000-40ba8000 rw-p 403a8000 00:00 0 
40e1a000-40e1b000 ---p 40e1a000 00:00 0 
40e1b000-4161b000 rw-p 40e1b000 00:00 0 
41865000-41866000 ---p 41865000 00:00 0 
41866000-42066000 rw-p 41866000 00:00 0 
42066000-42067000 ---p 42066000 00:00 0 
42067000-42867000 rw-p 42067000 00:00 0 
42867000-42868000 ---p 42867000 00:00 0 
42868000-43068000 rw-p 42868000 00:00 0 
43068000-43069000 ---p 43068000 00:00 0 
43069000-43869000 rw-p 43069000 00:00 0 
43869000-4386a000 ---p 43869000 00:00 0 
4386a000-4406a000 rw-p 4386a000 00:00 0 
7fabf75c7000-7fabf75ce000 r-xp 00000000 08:01 11370                      /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fabf75ce000-7fabf77ce000 ---p 00007000 08:01 11370                      /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fabf77ce000-7fabf77cf000 rw-p 00007000 08:01 11370                      /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fabf77cf000-7fabf77ef000 r-xp 00000000 08:01 12692                      /usr/lib/thunderbird/components/libwallet.so
7fabf77ef000-7fabf79ee000 ---p 00020000 08:01 12692                      /usr/lib/thunderbird/components/libwallet.so
7fabf79ee000-7fabf79f0000 rw-p 0001f000 08:01 12692                      /usr/lib/thunderbird/components/libwallet.so
7fabf79f0000-7fabf79f4000 r-xp 00000000 08:01 685526                     /lib/libnss_dns-2.7.so
7fabf79f4000-7fabf7bf4000 ---p 00004000 08:01 685526                     /lib/libnss_dns-2.7.so
7fabf7bf4000-7fabf7bf6000 rw-p 00004000 08:01 685526                     /lib/libnss_dns-2.7.so
7fabf7bf6000-7fabf7bf8000 r-xp 00000000 08:01 685534                     /lib/libnss_mdns4_minimal.so.2
7fabf7bf8000-7fabf7df7000 ---p 00002000 08:01 685534                     /lib/libnss_mdns4_minimal.so.2
7fabf7df7000-7fabf7df8000 rw-p 00001000 08:01 685534                     /lib/libnss_mdns4_minimal.so.2
7fabf7df8000-7fabf7e00000 r-xp 00000000 08:01 12689                      /usr/lib/thunderbird/components/libmsgsmime.so
7fabf7e00000-7fabf7fff000 ---p 00008000 08:01 12689                      /usr/lib/thunderbird/components/libmsgsmime.so
7fabf7fff000-7fabf8000Killed

```

---

### Post by harperd on 2008-07-03
I've been having crashes (Thunderbird just dies within a second or two of starting up) or just hangs, usually when receiving new mail.

I don't have a Hotmail account nor Gmail. This has been happening regularly for the last month or so - it's getting to the stage that I'm considering moving to Evolution.

---

### Post by FreewareFan on 2008-07-03
> **philinux said:**
>  Only this week like some others have. version 2.0.0.14 (20080505)

Yep, same here with me.  Never had a problem with Thunderbird at all over the last 9 months or so, not until a couple of days ago.  Then for no reason, it just started crashing.  It didn't yell or scream, but just quietly went away after checking the mail accounts.  I did what you suggested, by disabling the webmail extension that I was using to get my hotmail messages, and what do you know?  All is well, once again.  

So, is it a problem with the webmail extension, or with the T-bird coding???

---

### Post by FreewareFan on 2008-07-03
UPDATE:  OK, after some checking, now that I know it's not just something to do with my system, I found out that if you update the Webmail Hotmail extension to version 1.2.17 the problem goes away.  So, if any of you that read this thread are having the same problems, just update to 1.2.17 and you'll be good to go.  One Note.... the auto updater within Thunderbird is not recognizing that there is an update for that extension, you'll have to go and do it manually....

---

### Post by philinux on 2008-07-04
Spotted the update on mozdev too. I kept trying the update in TB so decided to dig.

Anyway problem solved with 1.2.17

---

### Post by harperd on 2008-07-04
Not solved for me! The only add-on I have is 'contacts sidebar'

---

### Post by philinux on 2008-07-05
You need to raise a separate thread for your problem.
Cheers;

---

### Post by essexboyracer on 2008-07-05
A little help, if you cant remember how you got this the first time round and you are suffering the symptoms detailed above.

1. Check your version of the Webmail-Hotmail extn in Tools > Add Ons...

2. if it isn't 1.2.17 (mine was 1.2.15) go to the following URL and download to desktop (save link as...) version 1.2.17

[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

3. Drag the hotmail-1-2-17.xpi file INTO the add ons window within TB, and Install

4. Restart TB

I had the same problems as above, I have two Hotmail accounts in TB. The only thing that has changed for me is that it seems that Hotmail has added a NAG screen after you login (via Firefox) requesting that you upgrade your browser, yeah right...

---

### Post by lemmy15 on 2008-08-06
> **sydbat said:**
> This happened to me about two months ago. It turned out to be sound files when receiving messages. I can't remember where I saw the post (here or another forum), but it has to do with Thunderbird trying to access any sound file (even it's own) and having a big problem when doing so. Do you have any sound files enabled that you use when getting your messages? If so, disable them and see if that clears up the problem.

To do this, open Thunderbird and, as quickly as possible, stop incoming messages (as this is where the problem lies). Then go to Edit > Preferences > General tab and uncheck "Play Sound When Messages Arrive". Should keep it from crashing, if this is the problem.

Thank you!  I had also experienced problems with Thunderbird as I'd added a sound file for receiving messages which I used when I was using the Mozilla e-mail client before upgrading to ubuntu.

And ever since I'd disabled this I have had no problems with T-bird.  (And I do not use POP mail with my hotmail account.)

Thanks for mentioning it!

---

