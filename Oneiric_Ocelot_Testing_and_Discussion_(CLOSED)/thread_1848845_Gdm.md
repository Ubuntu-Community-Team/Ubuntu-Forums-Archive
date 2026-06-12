---
title: "Gdm"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wedderburn on 2011-09-23
Any idea when the GDM package is going to see a update?

---

### Post by dino99 on 2011-09-23
lightdm is the default now with gnome3

---

### Post by wedderburn on 2011-09-23
> **dino99 said:**
> lightdm is the default now with gnome3
and I'm sticking with most of the gnome stack that and LightDM prevents laptop booting up :\

---

### Post by dino99 on 2011-09-23
have you tried to purge/reinstall lightdm ?

---

### Post by jerrrys on 2011-09-23
this is what got installed yesterday; what do you have?

[ATTACH]202780[/ATTACH]

---

### Post by garvinrick4 on 2011-09-23
Notice below not installed in oneiric. On upgrade gdm is most likely still installed, just reconfigure to use lightdm. Or as I have read in your post if you want gdm here is version now.
Can find as .deb in launchpad I am sure with a google or two with latest version. Have not used in oneiric, I use lightdm.
ctrl/alt/F1
```
sudo dpkg-reconfigure lightdm
```use tab key, arrows and enter to choose lightdm as default.
```
sudo stop gdm
``````
sudo /etc/init.d/lightdm restart
``````
Package: gdm                             
New: yes
State: not installed
Version: 3.0.4-0ubuntu10
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 7,598 k
Depends: libaccountsservice0 (>= 0.6.8), libc6 (>= 2.4), libcairo2 (>= 1.10.0),
         libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libdbus-1-3 (>=
         1.0.2), libdbus-glib-1-2 (>= 0.88), libfontconfig1 (>= 2.8.0),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0
         (>= 2.27.4), libgtk-3-0 (>= 3.0.0), libpam0g (>= 0.99.7.1),
         libpango1.0-0 (>= 1.14.0), libupower-glib1 (>= 0.9.0), libwrap0 (>=
         7.6-4~), libx11-6, libxau6, libxdmcp6, libxrandr2 (>= 2:1.2.99.3),
         debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.28.1-2), upstart-job,
         adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1),
         accountsservice (>= 0.6.12), gnome-session-bin, kbd | console-tools,
         udev (>= 166-0ubuntu4)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: libpam-gnome-keyring, locales, uswsusp, gnome-power-manager,
          gnome-mag, gnome-orca, gok
Conflicts: gdm
Breaks: usplash, usplash
Provides: x-display-manager
Description: GNOME Display Manager
 GDM provides the equivalent of a "login:" prompt for X displays: it asks for a
 login and starts X sessions. 
 
 It provides all the functionality of XDM, including XDMCP support for managing
 remote displays, and extends it with the ability to start X servers on demand. 
 
 The greeter is written using the GNOME libraries and hence looks like a GNOME
 application - even to the extent of supporting themes! 
 
 This package contains the next generation GDM, which was developed using the
 technologies on which GNOME 3 is based.

rick@rick-test:~$ 

```

---

### Post by garvinrick4 on 2011-09-23
```
Package: lightdm                         
New: yes
State: installed
Automatically installed: no
Version: 0.9.7-0ubuntu1
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 414 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6,
         libpam-runtime (>= 0.76-14), libpam-modules, adduser, dbus
PreDepends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg, unity-greeter | lightdm-greeter
Conflicts: liblightdm-gobject-0-0, liblightdm-gobject-0-0, liblightdm-qt-0-0,
           liblightdm-qt-0-0, lightdm
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: [https://launchpad.net/lightdm](https://launchpad.net/lightdm)

```
```
rick@rick-test:~$
Package: unity-greeter                   
New: yes
State: installed
Automatically installed: no
Version: 0.0.8-0ubuntu1
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@canonical.com>
Uncompressed Size: 217 k
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk-3-0
         (>= 3.0.0), libindicator3-6, liblightdm-gobject-1-0 (>= 0.9.2),
         libpango1.0-0 (>= 1.14.0), libx11-6
Recommends: lightdm
Conflicts: unity-greeter
Provides: lightdm-greeter
Description: Unity Greeter
 The greeter for the Unity desktop.
Homepage: https://launchpad.net/unity-greeter
```

---

### Post by wedderburn on 2011-09-23
> **jerrrys said:**
> this is what got installed yesterday; what do you have?

[ATTACH]202780[/ATTACH]

i've got version: 3.0.4-0ubuntu10 atm yours seems a bit out of date actually.

the latest one should be 3.1.92 or something along those lines.

---

### Post by garvinrick4 on 2011-09-23
Yes wedderbum here they are in .deb if want latest build.
[https://launchpad.net/ubuntu/+source/gdm/3.0.4-0ubuntu11/+build/2803062](https://launchpad.net/ubuntu/+source/gdm/3.0.4-0ubuntu11/+build/2803062)

---

### Post by jerrrys on 2011-09-23
> **wedderburn said:**
> i've got version: 3.0.4-0ubuntu10 atm yours seems a bit out of date actually.

the latest one should be 3.1.92 or something along those lines.

My mistake. I looked at 10o4 synaptic.  Looking at 11.10 synaptic shows the same as you (3.0.4-0ubuntu10).

---

### Post by jbicha on 2011-09-23
GDM is a difficult package to update as Debian & Ubuntu carry a lot of patches against it (and our patches aren't the same). Since LightDM is now the Ubuntu default and seems to work better for what we need it for, maybe we'll drop some of the GDM patches. Don't expect GDM 3.2 to be in the Ubuntu 11.10 archives though.

---

### Post by SATA on 2011-09-30
> **jbicha said:**
> GDM is a difficult package to update as Debian & Ubuntu carry a lot of patches against it (and our patches aren't the same). Since LightDM is now the Ubuntu default and seems to work better for what we need it for, maybe we'll drop some of the GDM patches. Don't expect GDM 3.2 to be in the Ubuntu 11.10 archives though.

Soo.. its a case of, "we dont use it as default in our distro so you cant have it" ?

---

### Post by jbicha on 2011-09-30
SATA, that's awfully unfair. We have a GDM 3.2 package but it crashes as soon as it starts. So, which would you prefer, a working GDM 3.0 that's been tested for 6 months or a broken 3.2? And it's not like we didn't do any work this cycle; Ubuntu 11.04 shipped 2.32, so 3.0 is still an upgrade.

---

### Post by SATA on 2011-09-30
> **jbicha said:**
> Don't expect GDM 3.2 to be in the Ubuntu 11.10 archives though.

I agree, unfair now that I have all the info that was previously omitted.

Where can one get the 3.2 source and / or package to test / patch

---

### Post by jbicha on 2011-09-30
I have some code at [https://code.launchpad.net/~jbicha/ubuntu/oneiric/gdm/3.2-WIP](https://code.launchpad.net/~jbicha/ubuntu/oneiric/gdm/3.2-WIP) The changelog isn't fully accurate. There's been a few of us working on it but we haven't figured it out yet. As I said in the previous post, GDM 3.2 is currently unusable on Debian/Ubuntu.

---

### Post by SATA on 2011-10-02
I assume your referring to when gdm-binary loads, and just sits there with the spinner ?

---

### Post by tista on 2011-10-02
> **jbicha said:**
> I have some code at [https://code.launchpad.net/~jbicha/ubuntu/oneiric/gdm/3.2-WIP](https://code.launchpad.net/~jbicha/ubuntu/oneiric/gdm/3.2-WIP) The changelog isn't fully accurate. There's been a few of us working on it but we haven't figured it out yet. As I said in the previous post, GDM 3.2 is currently unusable on Debian/Ubuntu.

Hi jbicha,

Thanks for your patchworks and debian dir!! :)
But unfortunately I couldn't build it on LP...
[https://launchpadlibrarian.net/81526868/buildlog_ubuntu-oneiric-i386.gdm_3.2.0+git20110929.d1610f2-0ubuntu1~tista3_FAILEDTOBUILD.txt.gz]("https://launchpadlibrarian.net/81526868/buildlog_ubuntu-oneiric-i386.gdm_3.2.0+git20110929.d1610f2-0ubuntu1~tista3_FAILEDTOBUILD.txt.gz")

Please point me out what's wrong with it?
Or could I help you devs a bit?

cheers.

---

### Post by SATA on 2011-10-03
OK i can get GDM to compile and show the greeter (Keyboard and everything works as they should)

Just crashes on login / starting the session

---

### Post by jbicha on 2011-10-03
SATA, what did you do differently to get it to show the greeter?

---

### Post by SATA on 2011-10-03
in the logs, it was complaining about ck-get-display wor whatever the script is, so i symlinked it to the location gdm was looking for,

and in /etc/pam.d i symlinked system-auth to gdm. That gave me a greeter

---

### Post by SATA on 2011-10-03
This error occurs on attempt to log-on
```

gdm-welcome][2443]: AccountsService-WARNING: SetLanguage call failed: running '/usr/share/language-tools/set-language-helper' failed: no output
gdm-welcome][2443]: pam_unix(gdm-welcome:session): session opened for user gdm by (uid=0)
gdm-welcome][2443]: pam_ck_connector(gdm-welcome:session): nox11 mode, ignoring PAM_TTY :0
gdm-simple-slave[2424]: GLib-CRITICAL: g_sequence_get: assertion `!is_end (iter)' failed
gdm-simple-slave[2424]: CRITICAL: gdm_session_direct_set_environment_variable: assertion `value != NULL' failed
gdm-simple-slave[2424]: GLib-CRITICAL: g_sequence_get: assertion `!is_end (iter)' failed
gdm-simple-slave[2424]: CRITICAL: gdm_session_direct_set_environment_variable: assertion `value != NULL' failed
gdm-simple-slave[2424]: GLib-CRITICAL: g_sequence_get: assertion `!is_end (iter)' failed
gdm-password][2512]: PAM unable to dlopen(pam_cracklib.so): /lib/security/pam_cracklib.so: cannot open shared object file: No such file or directory
gdm-password][2512]: PAM adding faulty module: pam_cracklib.so
gdm-password][2512]: pam_unix(gdm-password:session): session opened for user rdavies by (uid=0)
gdm-welcome][2443]: pam_unix(gdm-welcome:session): session closed for user gdm
gdm-simple-slave[2424]: GLib-CRITICAL: g_sequence_get: assertion `!is_end (iter)' failed
gdm[2523]: ******************* START **********************************
gdm[2523]: [Thread debugging using libthread_db enabled]
gdm[2523]: [New Thread 0xb762ab70 (LWP 2427)]
gdm[2523]: 0x00d54416 in __kernel_vsyscall ()
gdm[2523]: #0  0x00d54416 in __kernel_vsyscall ()
gdm[2523]: #1  0x0011ea2b in waitpid () from /lib/i386-linux-gnu/libpthread.so.0
gdm[2523]: #2  0x08068a0d in crashlogger_get_backtrace () at gdm-signal-handler.c:196
gdm[2523]: #3  gdm_signal_handler_backtrace () at gdm-signal-handler.c:223
gdm[2523]: #4  0x08068e29 in signal_handler (signo=<optimized out>) at gdm-signal-handler.c:251
gdm[2523]: #5  signal_handler (signo=11) at gdm-signal-handler.c:232
gdm[2523]: #6  <signal handler called>
gdm[2523]: #7  0x080580b8 in get_session_command_for_name (name=0x0, command=0xbfdd21ac) at gdm-session-direct.c:657
gdm[2523]: #8  0x0805cb0a in get_session_command (session=0x87fa930) at gdm-session-direct.c:2308
gdm[2523]: #9  gdm_session_direct_start_session (session=0x87fa930, service_name=0x87fead8 "gdm-password") at gdm-session-direct.c:2472
gdm[2523]: #10 0x08062099 in start_session (slave=0x87dc000) at gdm-simple-slave.c:468
gdm[2523]: #11 0x08062130 in on_greeter_session_stop (greeter=0x87fa850, slave=0x87dc000) at gdm-simple-slave.c:1004
gdm[2523]: #12 0x00a4014c in g_cclosure_marshal_VOID__VOID () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #13 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #14 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #15 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #16 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #17 0x080517a4 in on_conversation_stopped (session=0x87fa8c0, service_name=0x880c640 "gdm-welcome", welcome_session=0x87fa850) at gdm-welcome-session.c:824
gdm[2523]: #18 0x00a40a43 in g_cclosure_marshal_VOID__STRING () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #19 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #20 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #21 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #22 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #23 0x08057711 in _gdm_session_conversation_stopped (session=0x87fa8c0, service_name=0x881d038 "gdm-welcome") at gdm-session.c:751
gdm[2523]: #24 0x0805b7d5 in worker_exited (job=0x87d7560, code=0, conversation=0x880c590) at gdm-session-direct.c:1800
gdm[2523]: #25 0x00a40443 in g_cclosure_marshal_VOID(int0_t) () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #26 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #27 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #28 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #29 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: #30 0x0805d48c in session_worker_job_child_watch (pid=2443, status=0, job=0x87d7560) at gdm-session-worker-job.c:115
gdm[2523]: #31 0x0056d172 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: #32 0x0057125f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: #33 0x00571990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: #34 0x00571f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: #35 0x0804d8fd in main (argc=1, argv=0xbfdd2d84) at simple-slave-main.c:259
gdm[2523]: 
gdm[2523]: Thread 2 (Thread 0xb762ab70 (LWP 2427)):
gdm[2523]: #0  0x00d54416 in __kernel_vsyscall ()
gdm[2523]: No symbol table info available.
gdm[2523]: #1  0x0011da8b in read () from /lib/i386-linux-gnu/libpthread.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #2  0x0056d50b in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #3  0x005985f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #4  0x00116d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #5  0x006f90ce in clone () from /lib/i386-linux-gnu/libc.so.6
gdm[2523]: No symbol table info available.
gdm[2523]: Backtrace stopped: Not enough registers or memory available to unwind further
gdm[2523]: 
gdm[2523]: Thread 1 (Thread 0xb782b720 (LWP 2424)):
gdm[2523]: #0  0x00d54416 in __kernel_vsyscall ()
gdm[2523]: No symbol table info available.
gdm[2523]: #1  0x0011ea2b in waitpid () from /lib/i386-linux-gnu/libpthread.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #2  0x08068a0d in crashlogger_get_backtrace () at gdm-signal-handler.c:196
gdm[2523]:         estatus = <optimized out>
gdm[2523]: 
gdm[2523]:         pid = <optimized out>
gdm[2523]: #3  gdm_signal_handler_backtrace () at gdm-signal-handler.c:223
gdm[2523]: 
gdm[2523]: #4  0x08068e29 in signal_handler (signo=<optimized out>) at gdm-signal-handler.c:251
gdm[2523]: 
gdm[2523]: #5  signal_handler (signo=11) at gdm-signal-handler.c:232
gdm[2523]: 
gdm[2523]: 
gdm[2523]: #6  <signal handler called>
gdm[2523]: No symbol table info available.
gdm[2523]: #7  0x080580b8 in get_session_command_for_name (name=0x0, command=0xbfdd21ac) at gdm-session-direct.c:657
gdm[2523]: 
gdm[2523]:         filename = <optimized out>
gdm[2523]: #8  0x0805cb0a in get_session_command (session=0x87fa930) at gdm-session-direct.c:2308
gdm[2523]:         res = <optimized out>
gdm[2523]:         command = 0x0
gdm[2523]:         session_name = 0x0
gdm[2523]: #9  gdm_session_direct_start_session (session=0x87fa930, service_name=0x87fead8 "gdm-password") at gdm-session-direct.c:2472
gdm[2523]:         impl = 0x87fa930
gdm[2523]:         conversation = 0x87f4920
gdm[2523]: 
gdm[2523]:         program = <optimized out>
gdm[2523]: 
gdm[2523]: #10 0x08062099 in start_session (slave=0x87dc000) at gdm-simple-slave.c:468
gdm[2523]: 
gdm[2523]: 
gdm[2523]: #11 0x08062130 in on_greeter_session_stop (greeter=0x87fa850, slave=0x87dc000) at gdm-simple-slave.c:1004
gdm[2523]: No locals.
gdm[2523]: #12 0x00a4014c in g_cclosure_marshal_VOID__VOID () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #13 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #14 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #15 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #16 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #17 0x080517a4 in on_conversation_stopped (session=0x87fa8c0, service_name=0x880c640 "gdm-welcome", welcome_session=0x87fa850) at gdm-welcome-session.c:824
gdm[2523]:         conversation_session = 0x87fa8c0
gdm[2523]: #18 0x00a40a43 in g_cclosure_marshal_VOID__STRING () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #19 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #20 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #21 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #22 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #23 0x08057711 in _gdm_session_conversation_stopped (session=0x87fa8c0, service_name=0x881d038 "gdm-welcome") at gdm-session.c:751
gdm[2523]: 
gdm[2523]: #24 0x0805b7d5 in worker_exited (job=0x87d7560, code=0, conversation=0x880c590) at gdm-session-direct.c:1800
gdm[2523]:         impl = 0x87fa8c0
gdm[2523]: #25 0x00a40443 in g_cclosure_marshal_VOID(int0_t) () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #26 0x00a3ec3c in g_closure_invoke () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #27 0x00a519f0 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #28 0x00a5a787 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #29 0x00a5a8f3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #30 0x0805d48c in session_worker_job_child_watch (pid=2443, status=0, job=0x87d7560) at gdm-session-worker-job.c:115
gdm[2523]: 
gdm[2523]: #31 0x0056d172 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #32 0x0057125f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #33 0x00571990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #34 0x00571f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
gdm[2523]: No symbol table info available.
gdm[2523]: #35 0x0804d8fd in main (argc=1, argv=0xbfdd2d84) at simple-slave-main.c:259
gdm[2523]:         main_loop = 0x87d97a0
gdm[2523]:         context = <optimized out>
gdm[2523]:         connection = 0x0
gdm[2523]:         slave = 0x87dc000
gdm[2523]: 
gdm[2523]:         signal_handler = 0x87d5c50
gdm[2523]: 
gdm[2523]: A debugging session is active.
gdm[2523]: 
gdm[2523]: 	Inferior 1 [process 2424] will be detached.
gdm[2523]: 
gdm[2523]: Quit anyway? (y or n) [answered Y; input not from terminal]
gdm[2523]: ******************* END **********************************

```

---

### Post by SATA on 2011-10-03
> **SATA said:**
> in the logs, it was complaining about ck-get-display wor whatever the script is, so i symlinked it to the location gdm was looking for,

and in /etc/pam.d i symlinked system-auth to gdm. That gave me a greeter

/usr/libexec/
```

root@Bosstop:/etc/pam.d# ls -l /usr/libexec/
total 3616
lrwxrwxrwx 1 root root     45 2011-10-04 11:23 ck-get-x11-display-device -> /usr/lib/ConsoleKit/ck-get-x11-display-device

```

/etc/pam.d
```

root@Bosstop:/etc/pam.d# ls -l /etc/pam.d
total 128
-rw-r--r-- 1 root root  197 2009-11-24 04:11 atd
-rw-r--r-- 1 root root  384 2010-09-03 22:21 chfn
-rw-r--r-- 1 root root   92 2010-09-03 22:21 chpasswd
-rw-r--r-- 1 root root  581 2010-09-03 22:21 chsh
-rw-r--r-- 1 root root 1281 2011-10-03 08:51 common-account
-rw-r--r-- 1 root root 1393 2011-10-03 08:51 common-auth
-rw-r--r-- 1 root root 1593 2011-10-03 08:51 common-password
-rw-r--r-- 1 root root 1557 2011-10-03 08:51 common-session
-rw-r--r-- 1 root root 1510 2011-10-03 08:51 common-session-noninteractive
-rw-r--r-- 1 root root  531 2010-08-25 11:01 cron
-rw-r--r-- 1 root root   69 2010-10-01 22:39 cups
-rw-r--r-- 1 root root  648 2010-09-14 01:48 gdm
-rw-r--r-- 1 root root  495 2010-09-14 01:48 gdm-autologin
-rw-r--r-- 1 root root  643 2011-10-04 11:21 gdm-fingerprint
-rw-r--r-- 1 root root  802 2011-10-04 11:21 gdm-password
-rw-r--r-- 1 root root  764 2011-10-04 11:21 gdm-smartcard
-rw-r--r-- 1 root root  314 2011-10-04 11:21 gdm-welcome
-rw-r--r-- 1 root root   56 2010-06-07 16:17 gnome-screensaver
-rw-r--r-- 1 root root  648 2011-09-07 18:28 lightdm
-rw-r--r-- 1 root root  495 2011-09-07 18:28 lightdm-autologin
-rw-r--r-- 1 root root 4585 2011-02-21 13:07 login
-rw-r--r-- 1 root root   92 2010-09-03 22:21 newusers
-rw-r--r-- 1 root root  520 2010-08-17 14:47 other
-rw-r--r-- 1 root root   92 2010-09-03 22:21 passwd
-rw-r--r-- 1 root root  105 2010-08-26 15:35 polkit-1
-rw-r--r-- 1 root root  168 2010-07-10 04:40 ppp
-rw-r--r-- 1 root root   84 2010-09-17 04:13 samba
-rw-r--r-- 1 root root  454 2011-08-14 21:23 smtp
-rw-r--r-- 1 root root 1272 2011-01-07 23:21 sshd
-rw-r--r-- 1 root root 2305 2010-09-03 22:21 su
-rw-r--r-- 1 root root  119 2010-09-01 08:38 sudo
lrwxrwxrwx 1 root root    3 2011-10-04 12:18 system-auth -> gdm

```

---

### Post by SATA on 2011-10-03
I am pleased to announce, that I now have GDM 3.2 logging me in!

I'l edit this soon and upload a youtube video.

[IMG]http://ubuntuone.com/5NP7z57bGa7Af904xbfqpK[/IMG]

Here are my sources and generated deb files: [gdm.tar.gz]("http://ubuntuone.com/1Y7NI5cc0jjwytjxPV6Y9T")

---

### Post by tista on 2011-10-04
> **SATA said:**
> I am pleased to announce, that I now have GDM 3.2 logging me in!

I'l edit this soon and upload a youtube video.

[IMG]http://ubuntuone.com/5NP7z57bGa7Af904xbfqpK[/IMG]

Here are my sources and generated deb files: [gdm.tar.gz]("http://ubuntuone.com/1Y7NI5cc0jjwytjxPV6Y9T")

Hi SATA,

You dd it?! :P
OK... I would port yours and try to build on Launchpad...

Thanks a lot!!

regards.

**EDIT**
I suppose this patch to be needed?:
[http://paste.ubuntu.com/702194/]("http://paste.ubuntu.com/702194/")
Because I didn't think we usually have any file named "/var/lib/gdm/.gconf" on oneiric...

---

### Post by SATA on 2011-10-04
> **tista said:**
> Hi SATA,

You dd it?! :P
OK... I would port yours and try to build on Launchpad...

Thanks a lot!!

regards.

**EDIT**
I suppose this patch to be needed?:
[http://paste.ubuntu.com/702194/]("http://paste.ubuntu.com/702194/")
Because I didn't think we usually have any file named "/var/lib/gdm/.gconf" on oneiric...

yeah on mine i just created the file to install the deb, then deleted it after it installed.

It is still buggy, for example, starts on tty1 and causes some strange locale issues (Might have been my system doing it though). Ive also noticed that sometimes it'll start in fallback mode, and log into Gnome3 in fallback mode. Not sure as to why.

Good luck! :guitar:

---

### Post by jbicha on 2011-10-05
SATA, I wasn't able to duplicate your success. I symlinked the two files you mentioned but that still wasn't enough to get the greeter to load.

---

### Post by tista on 2011-10-05
> **SATA said:**
> yeah on mine i just created the file to install the deb, then deleted it after it installed.

It is still buggy, for example, starts on tty1 and causes some strange locale issues (Might have been my system doing it though). Ive also noticed that sometimes it'll start in fallback mode, and log into Gnome3 in fallback mode. Not sure as to why.

Good luck! :guitar:

@SATA,

Yeah I understood the situations... ;)
Now I'm retrying upload to launchpad. and agreed that this version sometimes forces me to fall back to greeter suddenly... but anyway simple gtk greeter works on oneiric, and hopefully I wanna run "gnome-shell-ish" greeter as well... :P

cheers.

**EDIT**
OK... finished launchpad build.. :)
so ready for those who wants bleeding edge trials...
but now it seems to improve gtk simple greeter only.
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

---

### Post by SATA on 2011-10-05
> **jbicha said:**
> SATA, I wasn't able to duplicate your success. I symlinked the two files you mentioned but that still wasn't enough to get the greeter to load.

Try my deb's or Tista's repo. The package was updated by myself to auto-symlink those files.

---

### Post by jbicha on 2011-10-05
"Could not update ICEAuthority file /var/lib/gdm/.ICEauthority"

---

### Post by SATA on 2011-10-06
> **jbicha said:**
> "Could not update ICEAuthority file /var/lib/gdm/.ICEauthority"

have you tried removing this file then trying again ?

---

### Post by jbicha on 2011-10-06
That file doesn't exist nor does the folder, so I created the folder and chown'd it to gdm:gdm but that still didn't help.

---

### Post by SATA on 2011-10-06
are you running from a compilation you've made? or the DEB files I posted (Tista's PPA works fine too)

---

### Post by jbicha on 2011-10-06
I'm running from tista's PPA since my main computer is amd64 (and your deb's were i386).

---

### Post by SATA on 2011-10-06
> **jbicha said:**
> I'm running from tista's PPA since my main computer is amd64 (and your deb's were i386).

Please clear out the /var/log/gdm directory, then try starting gdm
once it fails, please post to pastebin the contents of the logfiles.

---

### Post by jbicha on 2011-10-06
It worked this time; maybe my previous attempts to get gdm to run were messing it up.

---

### Post by tista on 2011-10-06
@jbicha, 

Finally it works? ;)

But unfortunately we only confirm that simple-greeter got to run... and I didn't track that issue down yet.. Yeah as far as I know this gdm 3.2 might have some error on DBus, so 100% fails to kick ibus and more apps as startup apps.. :S

And then, it must be run with "gdm-shell" session via "gnome-shell --gdm-mode" to show up the gnome-shell-ish new greeter, but it didn't yet as well.

If you had much time after finishing your hard work for official release, please continue to fix gdm 3.2 again! ;)

cheers.

---

### Post by SATA on 2011-10-06
> **tista said:**
> @jbicha, 

Finally it works? ;)

But unfortunately we only confirm that simple-greeter got to run... and I didn't track that issue down yet.. Yeah as far as I know this gdm 3.2 might have some error on DBus, so 100% fails to kick ibus and more apps as startup apps.. :S

And then, it must be run with "gdm-shell" session via "gnome-shell --gdm-mode" to show up the gnome-shell-ish new greeter, but it didn't yet as well.

If you had much time after finishing your hard work for official release, please continue to fix gdm 3.2 again! ;)

cheers.

Really?
Mine starts up with the simple greeter, I drop to a console, run sudo restart gdm

and I come up with the shell gdm.

---

### Post by tista on 2011-10-06
> **SATA said:**
> Really?
Mine starts up with the simple greeter, I drop to a console, run sudo restart gdm

and I come up with the shell gdm.

OMG... :S

mine had some error like this:
```
(gnome-shell:3250): GdmGreeter-WARNING **: GDM_GREETER_DBUS_ADDRESS not set
    JS ERROR: !!!   Exception was: Error: Error invoking GdmGreeter.open_connection: GDM_GREETER_DBUS_ADDRESS not set
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Error invoking GdmGreeter.open_connection: GDM_GREETER_DBUS_ADDRESS not set")@gjs_throw:0
()@/usr/share/gnome-shell/js/gdm/loginDialog.js:748
LoginDialog()@/usr/share/gnome-shell/js/gdm/loginDialog.js:727
_createGDMSession()@/usr/share/gnome-shell/js/ui/main.js:95
start()@/usr/share/gnome-shell/js/ui/main.js:223
@<main>:1
"'
    JS ERROR: !!!     message = '"Error invoking GdmGreeter.open_connection: GDM_GREETER_DBUS_ADDRESS not set"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Error invoking GdmGreeter.open_connection: GDM_GREETER_DBUS_ADDRESS not set
```

regards.

---

### Post by tista on 2011-10-06
@SATA,

I could run gdm-shell!! :P

Yeah we seem to fix the session file:
```
/usr/share/gnome-session/sessions/gdm-shell.session
```

before:
```
IsRunnableHelper=bash -c 'gnome-shell --help | grep -q gdm-mode && /usr/lib/[color=red]gdm[/color]/gnome-session-check-accelerated'
```

after:
```
IsRunnableHelper=bash -c 'gnome-shell --help | grep -q gdm-mode && /usr/lib/[color=red]gnome-session[/color]/gnome-session-check-accelerated'
```

ASAP I would commit this fix to my PPA... ;)

cheers.

---

### Post by SATA on 2011-10-06
Great News!

I dont know what part that file plays. But i have updated mine.

Although mine didnt have the bash -c etc in it,
just /usr/lib/gdm/gnome-session-check-accelerated
Updated it to /usr/lib/gnome-session/gnome-session-check-accelerated

---

### Post by tista on 2011-10-06
> **SATA said:**
> Great News!

I dont know what part that file plays. But i have updated mine.

Although mine didnt have the bash -c etc in it,
just /usr/lib/gdm/gnome-session-check-accelerated
Updated it to /usr/lib/gnome-session/gnome-session-check-accelerated

Yeah its git upstream fix:
[http://git.gnome.org/browse/gdm/commit/?id=64e6b10f98fe7226a2f41807268dae3afa80236d]("http://git.gnome.org/browse/gdm/commit/?id=64e6b10f98fe7226a2f41807268dae3afa80236d")

and I've merged latest git sources to my PPA... ;)
stay tuned!!

Best regards.

**EDIT**
OK... my latest 3.2.0-sata-0ubuntu1~tista3 had been finished to build on LP...
So please give it a try.

---

### Post by SATA on 2011-10-06
Works as expected on my laptop

Issues i've noticed with GDM 3.2:
[LIST]
[*]Crashes when switching TTYs
[*]Starts on TTY1 or TTY8 (Never TTY7)
[*]Doesnt kill plymouth when it starts
[*]Automatic Keyring unlocking doesnt work (Works fine with other Display Managers)
[*]Sometimes crashes when logging in (Respawns as it should)
[/LIST]

Thats all I can think of that needs fixing.

We've done well folks! :lolflag:

---

### Post by RavisPohan on 2011-10-06
> **tista said:**
> 
OK... my latest 3.2.0-sata-0ubuntu1~tista3 had been finished to build on LP...
So please give it a try.

Thanks for the work on packaging GDM.

Mine just drops me to the default wallpaper with no greeter at all. Reverting that line fixes it to the point that I get the gtk-greeter back. I'm running an up-to-date 64-bit Oneiric install.

---

### Post by tista on 2011-10-06
> **RavisPohan said:**
> Thanks for the work on packaging GDM.

Mine just drops me to the default wallpaper with no greeter at all. Reverting that line fixes it to the point that I get the gtk-greeter back. I'm running an up-to-date 64-bit Oneiric install.

@RavisPohan,

Which gnome-shell version did you run with? Today gdm-shell greeter needs css file for theming, and it should be contained within gnome-shell theme directory (usually the path to /usr/share/gnome-shell/theme).

And gdm-shell greeter also requires GPU performance and compatibilities same as gnome-shell since the engine is gs. If your GPU couldn't run gs, then it means your greeter had to fallback to simple-greeter...

cheers.

---

### Post by RavisPohan on 2011-10-07
> **tista said:**
> @RavisPohan,

Which gnome-shell version did you run with? Today gdm-shell greeter needs css file for theming, and it should be contained within gnome-shell theme directory (usually the path to /usr/share/gnome-shell/theme).

And gdm-shell greeter also requires GPU performance and compatibilities same as gnome-shell since the engine is gs. If your GPU couldn't run gs, then it means your greeter had to fallback to simple-greeter...

cheers.

The css file is there, and my gnome-shell version is 3.20 (** 3.2.0+git20111005.ac678f63-0ubuntu1~11.10~ricotz0**). I've been running gnome-shell for over a year with no issues apart from the obvious occasional bugs

---

### Post by tista on 2011-10-07
> **RavisPohan said:**
> The css file is there, and my gnome-shell version is 3.20 (** 3.2.0+git20111005.ac678f63-0ubuntu1~11.10~ricotz0**). I've been running gnome-shell for over a year with no issues apart from the obvious occasional bugs

Haven't any clue... :S

and above git fix must be needed on oneiric I think. since the helper didn't exist into gdm directory. so if you had succeeded by reverting this fix, I think it might be something wrong... :sad:

finally gdm-shell is the special mode of gnome-shell, so we obviously need gnome-shell are running "before" gdm-shell was kicked... yep, "gnome-shell --gdm-mode".

does SATA and/or jbicha have any ideas? :P

cheers.

---

### Post by tista on 2011-10-07
Hi guys,

I've updated the package with this patch:
[http://git.gnome.org/browse/gdm/commit/?id=ea366b1a582bbd886ec7da5d9f59b415d074164f]("http://git.gnome.org/browse/gdm/commit/?id=ea366b1a582bbd886ec7da5d9f59b415d074164f")

And if you guys want change/customize gdm wallpaper, give this a try:
[http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/]("http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/")
It seems to be OK on oneiric and gdm-3.2.0! ;)

Then, today gdm 3.2 got to use only default Adwaita gdm-shell theme, damned!! so we might have to apply our own favorite gtk3 theme by replacing original Adwaita theme directory... :/ For example, original one is placed in /usr/share/gnome-shell/theme, so renamed it something like "theme.org" and so, and make symlink from desired theme directory to that path. I'm pretty sure that I could change the gdm theme to my favorite elementary-borderless theming!! :) Why? yeah I hate Adwaita at all....

So now I have a wishlist that gdm 3.2 would be better to get the "non-hackish" way to change gdm-shell theming and wallpaper... How? umm... the first I think "dconf-editor" and/or something like that, then if could, "gnome-tweak-tool" did like changing gnome-shell theming...

Regards.

---

### Post by RavisPohan on 2011-10-08
> **tista said:**
> Haven't any clue... :S

and above git fix must be needed on oneiric I think. since the helper didn't exist into gdm directory. so if you had succeeded by reverting this fix, I think it might be something wrong... :sad:

finally gdm-shell is the special mode of gnome-shell, so we obviously need gnome-shell are running "before" gdm-shell was kicked... yep, "gnome-shell --gdm-mode".

does SATA and/or jbicha have any ideas? :P

cheers.

Seemed to be fixed by recent update. Must be something in there, since reinstalling didn't help before. Anyway, thanks.

---

### Post by Corbelius on 2011-10-08
> **tista said:**
> Hi guys,

I've updated the package with this patch:
[http://git.gnome.org/browse/gdm/commit/?id=ea366b1a582bbd886ec7da5d9f59b415d074164f]("http://git.gnome.org/browse/gdm/commit/?id=ea366b1a582bbd886ec7da5d9f59b415d074164f")

And if you guys want change/customize gdm wallpaper, give this a try:
[http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/]("http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/")
It seems to be OK on oneiric and gdm-3.2.0! ;)

Then, today gdm 3.2 got to use only default Adwaita gdm-shell theme, damned!! so we might have to apply our own favorite gtk3 theme by replacing original Adwaita theme directory... :/ For example, original one is placed in /usr/share/gnome-shell/theme, so renamed it something like "theme.org" and so, and make symlink from desired theme directory to that path. I'm pretty sure that I could change the gdm theme to my favorite elementary-borderless theming!! :) Why? yeah I hate Adwaita at all....

So now I have a wishlist that gdm 3.2 would be better to get the "non-hackish" way to change gdm-shell theming and wallpaper... How? umm... the first I think "dconf-editor" and/or something like that, then if could, "gnome-tweak-tool" did like changing gnome-shell theming...

Regards.

Everything seems to works well with GDM 3.2, but there is a problem with the locales. All my system is in english, but i use the italian language, this the error in .xsession-errors log: 

```
(process:12184): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
```

With the default GDM in Oneiric (3.0.4) this not happen.

---

### Post by tista on 2011-10-08
> **Corbelius said:**
> Everything seems to works well with GDM 3.2, but there is a problem with the locales. All my system is in english, but i use the italian language, this the error in .xsession-errors log: 

```
(process:12184): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
```

With the default GDM in Oneiric (3.0.4) this not happen.

Hi Corbelius,

Yep, it's known issue... :sad:
I didn't have any ideas today, but our mate SATA knew it already and jbicha, too.. I hope. so we might fix it within codes/patches...

Then if you set "LC_ALL" into .profile, the situation got to change? perl always notify me the lack of definition in LC_ALL locales... :S

cheers.

---

### Post by Corbelius on 2011-10-09
> **tista said:**
> 

Then if you set "LC_ALL" into .profile, the situation got to change? perl always notify me the lack of definition in LC_ALL locales... :S

cheers.

What .profile file?

Ciao

---

### Post by tista on 2011-10-09
> **Corbelius said:**
> What .profile file?

Ciao

Ciao Corbelius,

I meant "$HOME/.profile". ;)

And unfortunately I'm using en_US locales for system widely, so ASAP I would try to run gdm with other locales...
 
Oh dinner time.  Buon appetito! :P

Ciao.

---

### Post by tista on 2011-10-09
@Corbelius,

Just now I'm tracking the locales issue down...
So I could set the locale properly in both gnome-shell and gdm-shell.

* Install the locales from "Language Support".
* Set it as "System-wide Locale".
* Restart PC and Login.

That's all. ;)

Please check your environments out.

Ciao.

---

### Post by Corbelius on 2011-10-11
> **tista said:**
> @Corbelius,

Just now I'm tracking the locales issue down...
So I could set the locale properly in both gnome-shell and gdm-shell.

* Install the locales from "Language Support".
* Set it as "System-wide Locale".
* Restart PC and Login.

That's all. ;)

Please check your environments out.

Ciao.

No, don't work. Anyway, i have a strange locale setted in GNOME Control Center (see the attachment).

---

### Post by tista on 2011-10-11
> **Corbelius said:**
> No, don't work. Anyway, i have a strange locale setted in GNOME Control Center (see the attachment).

@Corbelius,

OMG... it's pity... :sad:

So one thing.
Today oneiric's control-center has "User Accounts" as well, and it also has language setting.
Please check it whether correct locale were showed or not.

ciao. ;)

---

### Post by Corbelius on 2011-10-13
> **tista said:**
> @Corbelius,

OMG... it's pity... :sad:

So one thing.
Today oneiric's control-center has "User Accounts" as well, and it also has language setting.
Please check it whether correct locale were showed or not.

ciao. ;)

"oneiric's control-center" is the GNOME Control Center, and no, dont' work :/
I think the problem is one of the countless patches inserted into the GDM.
Ciao ;)

---

