---
title: "SIGABRT error when triying to run"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by thommyy on 2012-01-30
hi,
I'm getting this error when I try to run one windows application, if anyone have advice I would be grateful


* Assertion at domain.c:1482, condition `mono_defaults.monotype_class != 0' not met


Native stacktrace:

        mono() [0x80e126c]
        [0xa5040c]
        [0xa50416]
        /lib/i386-linux-gnu/libc.so.6(gsignal+0x4f) [0x13dc8f]
        /lib/i386-linux-gnu/libc.so.6(abort+0x175) [0x1412b5]
        mono() [0x82146d7]
        mono() [0x8214753]
        mono() [0x814c645]
        mono() [0x8060c50]
        mono(mono_main+0x297) [0x80ba117]
        mono() [0x805990f]
        /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3) [0x129113]
        mono() [0x80599d5]

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

Aborted

---

### Post by mikechant on 2012-01-31
Which windows application is this?

---

### Post by thommyy on 2012-01-31
it's some application we use on faculty for learning programing, "verifikator". Thing is i use linux 90% of my time, and almost all thing i need to do i can do in linux, and when i need to study programming i need to change to windows.

---

### Post by mikechant on 2012-02-01
What version of mono are you running?
You can find out by running the command
```
mono --version
```
in a terminal.

If the version is less than 2.10.5 then you could try upgrading mono, e.g by using the monoxide ppa - see:

[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

If it still doesn't work, the current version is 2.10.8 but it looks like you might have to build that from source at present.

Also see this page:
[http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)

and note the following warning:
> Backport Packages

Mono is considered a "core framework" in Ubuntu, meaning it has many applications depending upon it (roughly 40 applications). Due to this, the chance of one of those applications breaking** due to unexpected changes in their underlying framework is considered too high to risk an update.

As a result, Mono cannot officially be backported in Ubuntu. 


As you are licensed to run windows, an alternative would be to run your application under windows running in a VM under Linux. This will be more convenient than rebooting and the application should run perfectly, but you will need to make the effort of installing windows into the VM.

**Note: breakage might include F-Spot package - but it can be fixed by another ppa.

---

### Post by thommyy on 2012-02-01
I have mono version 2.10.5. Thanks for advice, i think i will just run that app under windows in VM. That's probably the easiest way...

---

