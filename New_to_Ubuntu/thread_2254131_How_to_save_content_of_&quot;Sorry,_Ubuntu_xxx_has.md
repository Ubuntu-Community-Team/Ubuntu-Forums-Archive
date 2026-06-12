---
title: "How to save content of &quot;Sorry, Ubuntu xxx has experienced an internal error.&quot;?"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by f(fanta) on 2014-11-25
How can I save the content of the window reporting an internal error? (see attached screenshot). Or perhaps the content is already somewhere in a file? (I am using Ubuntu 14.10).

Thanks!

---

### Post by ibjsb4 on 2014-11-25
Check for hidden file in /var/crash/.

If you remove that file, it will reset apport.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by f(fanta) on 2014-11-25
Mmmm... I don't find such a file in /var/crash. There is a _usr_bin_signon-ui.1000.crash which has the right date and time to be relevant, but its content is not what I see in the window reporting the internal error (see screenshot of my previous post). I would like to dump the content of that window. In the /var/crash directory I have this:

[FONT=courier new]> ls -laF
total 73108
drwxrwsrwt  2 root     whoopsie     4096 nov 25 12:40 ./
drwxr-xr-x 13 root     root         4096 ott 22 21:20 ../
[COLOR=#b22222]-rw-r-----  1 fanta    whoopsie  3044102 nov 25 12:37 _usr_bin_signon-ui.1000.crash[/COLOR]
-rw-r-----  1 fanta    whoopsie   441799 nov 23 10:19 _usr_lib_gimp_2.0_plug-ins_selection-to-path.1000.crash
-rw-rw-r--  1 fanta    whoopsie        0 nov 23 10:19 _usr_lib_gimp_2.0_plug-ins_selection-to-path.1000.upload
-rw-------  1 whoopsie whoopsie        0 nov 23 13:47 _usr_lib_gimp_2.0_plug-ins_selection-to-path.1000.uploaded
-rw-r-----  1 fanta    whoopsie 68885203 nov 24 11:29 _usr_lib_jvm_java-8-oracle_jre_bin_java.1000.crash
-rw-rw-r--  1 fanta    whoopsie        0 nov 24 11:29 _usr_lib_jvm_java-8-oracle_jre_bin_java.1000.upload
-rw-------  1 whoopsie whoopsie        0 nov 24 11:30 _usr_lib_jvm_java-8-oracle_jre_bin_java.1000.uploaded
-rw-r-----  1 fanta    whoopsie  2473553 nov 25 12:37 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.crash
-rw-rw-r--  1 fanta    whoopsie        0 nov 24 10:02 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.upload
-rw-------  1 whoopsie whoopsie        0 nov 24 10:03 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.uploaded
[/FONT]

---

### Post by deadflowr on 2014-11-25
When you click close, as long as you do not uncheck the send report, the report is send to the developers.
Nothing else need be done, unless prompted to do so.

Anyway the error report for the hud is at the bottom
> [COLOR=#000000][FONT=courier new]w-r----- 1 [/FONT][/COLOR][COLOR=#ff0000][FONT=courier new]fanta whoopsie 2473553 nov 25 12:37 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.crash[/FONT][/COLOR][COLOR=#000000][FONT=courier new][/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]-rw-rw-r-- 1 fanta whoopsie 0 nov 24 10:02 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.upload[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]-rw------- 1 whoopsie whoopsie 0 nov 24 10:03 _usr_lib_x86_64-linux-gnu_hud_hud-service.1000.uploaded[/FONT][/COLOR]

---

