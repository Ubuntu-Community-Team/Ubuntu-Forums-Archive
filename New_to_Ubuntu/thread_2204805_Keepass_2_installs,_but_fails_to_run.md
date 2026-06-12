---
title: "Keepass 2 installs, but fails to run"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by chris-burmajster on 2014-02-10
Hello Everybody,

I installed Keepass 2 via Synaptic and it appears to have installed, but when I run it, it fires up briefly, then disappears. I have uninstalled and re-installed. I 'ducked' the issue (via DuckDuckgo) and tried a couple of suggestions that involved adding ppas and re-installing, but all to no avail. It still fires up briefly and then disappears. I'm running Ubuntu 13:10 32 bit on a Dell Dimension 3100 with 2Gb of RAM and a 2Tb HDD.

If anybody could advise me where I went wrong, I'll be grateful!

Many thanks,

Chris

---

### Post by howefield on 2014-02-10
Try opening it via a terminal...

```
keepass2
```

you may get some errors that will help identify the problem.

Not sure if there is a relationship, but I use Keepassx, works a treat.

---

### Post by chris-burmajster on 2014-02-10
Thank you howefield. I tried your suggestion and got this:

```
SendMessage (67108902, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0xbfb96aa0)
SendMessage (0, 0x1204, (nil), 0xbfb96aa0)
SendMessage (0, 0x1203, 0x1, 0xbfb96aa0)
SendMessage (0, 0x1204, 0x1, 0xbfb96aa0)
SendMessage (0, 0x1203, 0x2, 0xbfb96aa0)
SendMessage (0, 0x1204, 0x2, 0xbfb96aa0)
SendMessage (0, 0x1203, 0x3, 0xbfb96aa0)
SendMessage (0, 0x1204, 0x3, 0xbfb96aa0)
SendMessage (0, 0x1203, 0x4, 0xbfb96aa0)
SendMessage (0, 0x1204, 0x4, 0xbfb96aa0)
SendMessage (67108902, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0xbfb97580)
SendMessage (0, 0x1204, (nil), 0xbfb97580)
SendMessage (0, 0x1203, 0x1, 0xbfb97580)
SendMessage (0, 0x1204, 0x1, 0xbfb97580)
SendMessage (0, 0x1203, 0x2, 0xbfb97580)
SendMessage (0, 0x1204, 0x2, 0xbfb97580)
SendMessage (0, 0x1203, 0x3, 0xbfb97580)
SendMessage (0, 0x1204, 0x3, 0xbfb97580)
SendMessage (0, 0x1203, 0x4, 0xbfb97580)
SendMessage (0, 0x1204, 0x4, 0xbfb97580)
[xcb] Too much data requested from _XRead
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
cli: ../../src/xcb_io.c:736: _XRead: Assertion `!xcb_xlib_too_much_data_requested' failed.
Stacktrace:

  at (wrapper managed-to-native) System.Windows.Forms.X11Keyboard.XCreateFontSet (intptr,string,intptr&,int&,intptr) <0xffffffff>
  at System.Windows.Forms.X11Keyboard.CreateOverTheSpotXic (intptr,intptr) <0x000af>
  at System.Windows.Forms.X11Keyboard.CreateXic (intptr,intptr) <0x000c7>
  at System.Windows.Forms.X11Keyboard.CreateXicForWindow (intptr) <0x00027>
  at System.Windows.Forms.X11Keyboard.FocusIn (intptr) <0x0008f>
  at System.Windows.Forms.XplatUIX11.SetFocus (intptr) <0x000a3>
  at System.Windows.Forms.XplatUI.SetFocus (intptr) <0x0001a>
  at System.Windows.Forms.ContainerControl.SendControlFocus (System.Windows.Forms.Control) <0x00083>
  at System.Windows.Forms.Form.SetVisibleCore (bool) <0x0059b>
  at KeePass.Forms.MainForm.SetVisibleCore (bool) <0x000ab>
  at System.Windows.Forms.Control.set_Visible (bool) <0x00029>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.set_Visible (bool) <0xffffffff>
  at System.Windows.Forms.Application.RunLoop (bool,System.Windows.Forms.ApplicationContext) <0x0020b>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext) <0x0004f>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form) <0x00037>
  at KeePass.Program.Main (string[]) <0x00977>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    /usr/bin/cli() [0x80eb88c]
    [0xb779740c]
    [0xb7797424]
    /lib/i386-linux-gnu/libc.so.6(gsignal+0x4f) [0xb758baff]
    /lib/i386-linux-gnu/libc.so.6(abort+0x143) [0xb758f083]
    /lib/i386-linux-gnu/libc.so.6(+0x27857) [0xb7584857]
    /lib/i386-linux-gnu/libc.so.6(+0x27907) [0xb7584907]
    /usr/lib/i386-linux-gnu/libX11.so.6(_XRead+0x10a) [0xb5c9dc9a]
    /usr/lib/i386-linux-gnu/libX11.so.6(XListFontsWithInfo+0x38c) [0xb5c7ff9c]
    /usr/lib/i386-linux-gnu/libX11.so.6(+0x70771) [0xb5cd7771]
    /usr/lib/i386-linux-gnu/libX11.so.6(XCreateOC+0x5d) [0xb5c8c41d]
    /usr/lib/i386-linux-gnu/libX11.so.6(XCreateFontSet+0x7a) [0xb5c80aea]
    [0xb31d27c0]
    [0xb31d2620]
    [0xb31d1880]
    [0xb31d1610]
    [0xb31d1590]
    [0xb31d14cc]
    [0xb31d1423]
    [0xb31090ac]
    [0xb392c05c]
    [0xb392ba9c]
    [0xb399a542]
    [0xb399a4e4]
    [0xb392abdc]
    [0xb392a980]
    [0xb392a620]
    [0xb688af70]
    [0xb688b2df]
    /usr/bin/cli() [0x80664a0]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

---

