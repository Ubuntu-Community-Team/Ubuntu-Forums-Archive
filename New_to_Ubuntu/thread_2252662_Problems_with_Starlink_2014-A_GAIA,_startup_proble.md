---
title: "Problems with Starlink 2014-A: GAIA, startup problem."
date: 2014-11-13
forum: New to Ubuntu
---

### Post by angusord on 2014-11-13
I have Starlink (the astrometry software package) installed on Ubuntu 14.04. The software currently runs with no problems, however, every time I launch GAIA from the terminal I am presented with an error message in a window, once the message is dismissed GAIA launches with no problems.

The error message is as follows:

```


[FONT=arial]couldn't open "/home/angusord/.skycat/[/FONT][FONT=arial]tclhttpd.default": permission denied[/FONT]
[FONT=arial]couldn't open "/home/angusord/.skycat/[/FONT][FONT=arial]tclhttpd.default": permission denied[/FONT]
[FONT=arial]    while executing[/FONT]
[FONT=arial]"open $Config(AuthDefaultFile) w 0660"[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"if {[info exists Config(Auth)]} {[/FONT]
[FONT=arial]    foreach {var val} $Config(Auth) {[/FONT]
[FONT=arial]    if {[string match user,* $var]} {[/FONT]
[FONT=arial]        # encrypt the password[/FONT]
[FONT=arial]        set salt [..."[/FONT]
[FONT=arial]    (file "/home/angusord/star-2014A/[/FONT][FONT=arial]lib/tclhttpd3.5.1/auth.tcl" line 72)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"source /home/angusord/star-2014A/lib/[/FONT][FONT=arial]tclhttpd3.5.1/auth.tcl"[/FONT]
[FONT=arial]    ("package ifneeded httpd::auth 2.0" script)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"package require httpd::auth"[/FONT]
[FONT=arial]    (file "/home/angusord/star-2014A/[/FONT][FONT=arial]lib/gaia4.4.5/SampClient.tcl" line 113)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"source /home/angusord/star-2014A/lib/[/FONT][FONT=arial]gaia4.4.5/SampClient.tcl"[/FONT]
[FONT=arial]    (in namespace eval "::" script line 1)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"namespace eval :: $auto_index($name)"[/FONT]
[FONT=arial]    (procedure "auto_load" line 13)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"auto_load $name [uplevel 1 {::namespace current}]"[/FONT]
[FONT=arial]    (autoloading "samp::SampClient")[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"if {$ret != 0} {[/FONT]
[FONT=arial]        dict append opts -errorinfo "\n    (autoloading \"$name\")"[/FONT]
[FONT=arial]        return -options $opts $msg[/FONT]
[FONT=arial]    }"[/FONT]
[FONT=arial]    (procedure "::unknown" line 1)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"samp::SampClient \#auto -agents $agents  -metadata [array get meta]"[/FONT]
[FONT=arial]    (procedure "::gaia::Gaia::init_samp_" body line 13)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"init_samp_"[/FONT]
[FONT=arial]    (object "::.gaia1" method "::gaia::Gaia::init" body line 97)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"init"[/FONT]
[FONT=arial]    (object "::.gaia1" method "::util::TopLevelWidget::call_[/FONT][FONT=arial]init" body line 2)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"::.gaia1 call_init"[/FONT]
[FONT=arial]    (in namespace inscope "::util::TopLevelWidget" script line 1)[/FONT]
[FONT=arial]    invoked from within[/FONT]
[FONT=arial]"namespace inscope ::util::TopLevelWidget {::.gaia1 call_init}"[/FONT]
[FONT=arial]    ("after" script)

[/FONT]
```

I have had a few minor problems with the software and suspect that this may be the issue. I am using the 2014 A version of Starlink.

Thanks,

Angus

---

### Post by jtarin on 2014-11-14
> **angusord said:**
> 
[FONT=arial]couldn't open "/home/angusord/.skycat/[/FONT][FONT=arial]tclhttpd.default": permission denied[/FONT]
[FONT=arial]couldn't open "/home/angusord/.skycat/[/FONT][FONT=arial]tclhttpd.default": permission denied[/FONT]


Does the file  "/home/angusord/.skycat/tclhttpd.default" .....exist?

---

### Post by angusord on 2014-11-24
It does exist, similar problems have been occurring with other files required by GAIA which also exist.

---

