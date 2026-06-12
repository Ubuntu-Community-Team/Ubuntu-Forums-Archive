---
title: "HOWTO install Gizmo (similar to Skype but sip open standard)"
date: 2005-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by celticmonkey on 2005-08-26
Gizmo ([http://www.gizmoproject.com](http://www.gizmoproject.com)) has just released their sip phone client as an alpha for linux. I've installed it and it seems to work. Obviously, it's an alpha, not a complete project, but I was able to make a call. It didn't seem to import my contact list and it can't be minimized to an icon like Gaim or Skype. Nevetheless, it looks promising. Early adopters may want to check it out. It didn't seem to cause any instability to ubuntu.

Gizmo is a sipphone client that uses an open standard like linphone. It's like Skype. You can buy credit to call old-school landlines or buy a real number so landlines can call your computer.

Here's an interesting quote from Google Talk's webside: ([http://www.google.com/talk/developer.html):](http://www.google.com/talk/developer.html):)
"... we are working closely with Earthlink and Sipphone to federate EarthLink's Vling service and Sipphone's Gizmo Project with the Google Talk service as quickly as possible, while offering the best possible user experience."

I've used Gizmo in Windows(tm) and it appears to have a more extensive list of call in numbers for sale than Skype, although I only see the call out feature in the linux alpha. (For landlines I mean.)

Here's how you can install it if you want to test it:


```
$ wget -c http://www.gizmoproject.com/download/bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
$ wget -c http://www.gizmoproject.com/download/libsipphoneapi_0.78.20050817.1-1_i386.deb
$ wget -c http://www.gizmoproject.com/download/gizmo_0.8.0.6-1_i386.deb
$ sudo dpkg -i bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
$ sudo dpkg -i libsipphoneapi_0.78.20050817.1-1_i386.deb
$ sudo dpkg -i gizmo_0.8.0.6-1_i386.deb
```

---

### Post by varunus on 2005-08-26
Those debs seem meant for debian and linspire...do they install without complaints?  Do they work?  I know some debian debs depend on a newer libc6 and can break Ubuntu...

---

### Post by rwabel on 2005-08-26
[QUOTE=varunus]Those debs seem meant for debian and linspire...do they install without complaints?  Do they work?  I know some debian debs depend on a newer libc6 and can break Ubuntu...[/QUOTE]
 works fine!

---

### Post by celticmonkey on 2005-08-26
The alpha release is in fact for debian and linspire. The notes above are for the debian install (even though one of the deb packages is weirdly named linspire.) It is a bit crazy downloading an untested alpha product for debian and installing it in ubuntu. It's not even a beta yet. I should have written PROCEED AT YOUR OWN RISK somewhere. Nevertheless, I installed it as above and it works as well an alpha can be expected to. The install doesn't cause any broken packages or unresolved dependencies. I haven't noticed any problems with ubuntu since.

---

### Post by lao_V on 2005-08-27
I get the following error:

vishal@sheep:~/Downloads$ gizmo
Debug: gizmo_prefs_init
Debug: gizmo_core_init
Debug: gizmo_gtk_stock_init: Loading 64 images
sipphoneapi_new: sipapi ptr: 137098352
Segmentation fault

Anyone know why?

---

### Post by traherom on 2005-08-28
Wow... I was going to post almost the exact same thing yesterday, but I couldn't get on the forums. :)

Yep, it works fine, by the way.

---

### Post by Weav on 2005-08-28
I've got Gizmo up and running is there anyway to connect to google's talk server? Since googletalk does not run in linux yet.

Thanks

---

### Post by idn on 2005-08-28
This app looks amazing, no moe messing around trying to get skype to work on my PC and it uses SIP! 

I will try it when I get home, does it use gtk or qt?

---

### Post by gsuveg on 2005-08-28
i cant register  a new account with linux client. anyone have idea why ?
it write: 
...
Debug: on_login_button_clicked
Debug: anim start
Debug: registration_cb: Success: 1  Msg:
Debug: gizmo_account_new: new account w/ id: 0
Debug: gizmo_account_new: Set user_agent_id: 0
Debug: login_thread_do
Debug: login_cb: Success: 0  Msg: Login failed! We could not validate your username and password!
Debug: anim stop
Debug: gizmo_account_destroy
Debug: gizmo_core_cleanup

---

### Post by idn on 2005-08-30
Awesome piece of software

---

### Post by rykel on 2005-09-03
[QUOTE=lao_V]I get the following error:

vishal@sheep:~/Downloads$ gizmo
Debug: gizmo_prefs_init
Debug: gizmo_core_init
Debug: gizmo_gtk_stock_init: Loading 64 images
sipphoneapi_new: sipapi ptr: 137098352
Segmentation fault

Anyone know why?[/QUOTE]

i have exactly the same error!

the debs installed just fine, but i get seg fault when i try to run gizmo... see this:

[B][INDENT]rykel@ubuntu:~$ gizmo
(gizmo:27329): Gdk-WARNING **: locale not supported by Xlib
(gizmo:27329): Gdk-WARNING **: cannot set locale modifiers
Debug: gizmo_prefs_init
Debug: gizmo_core_init
Debug: gizmo_gtk_stock_init: Loading 64 images
sipphoneapi_new: sipapi ptr: 137014752
Segmentation fault
[/INDENT][/B]

perhaps our libc++ (?) or watever is of the wrong version??

btw, do u know if i can use Linphone to connect to my Gizmo account, so tat people can still call me in the meantime? (just like using Gaim to connect to Google Talk)

---

### Post by Jad on 2005-09-04
I've install it, and it's running, the only main problem is you cannot login, the screen will stuck at loading user interface process, I've contact Gizmo support, and they promised to fix this bug in their next release.

just note guys to keep sending your reports to gizmo project support, we really should appreciate their work to have linux version, one last thing consider it's alpha version.

---

### Post by picturesqueweb on 2005-09-14
I'm running it here (KDE) with no problems at all.

---

### Post by sickdude on 2005-09-15
[QUOTE=][/QUOTE]
 i have it running and it looks very good. 

to bad that most people dont use this, and skype is more popular, dont know if you can phone skype users? anyway i hope googletalk will use this in anyway that way i can (google)talk to winblowz users :p

---

### Post by rwabel on 2005-09-15
[QUOTE=sickdude]i have it running and it looks very good. 

to bad that most people dont use this, and skype is more popular, dont know if you can phone skype users? anyway i hope googletalk will use this in anyway that way i can (google)talk to winblowz users :p[/QUOTE]
 no it's not possible to call sykpe users via the skype network, only over the PSTN gateway. But JaJah claims to be able, but they've not yet a linux version out

---

### Post by cvmostert on 2006-02-24
My problem is that most people I know use only MSN and Skype if i am lucky... so my hope of using something line gizmo or gnomemessenger is short sighted..

---

### Post by idn on 2006-02-26
Yeah I am the same, it would be great if all my non techie friends switched away from msn and jabber, but thats not going to happen any time soon :(

---

### Post by LordMau on 2006-08-07
hi trying out the latest gizmo at this time on dapper but keep running into this message when running the terminating:

```
snd_mixer_selem_get_capture_volume_range: Assertion `elem' failed.

```

a quick google shows that some users install the OSS version of the libsipphoneapi package on gizmo's site in leiu of the ALSA. So far I have to use aoss to make it run, but I' curious why the supposedly more apt alsa version of libsipphoneapi fails.

---

### Post by tomjennings on 2009-03-28
> **idn said:**
> Awesome piece of software

Just FYI, on this very old thread -- now, March 2009, the binary for download from gizmoproject is 2 years old (nov 2007), and it does not install on 64-bit arches. Nothing but silence in gizmo forums on new binaries. Mac, win updates this very month.

So it appears that gizmo has abandoned linux.

---

