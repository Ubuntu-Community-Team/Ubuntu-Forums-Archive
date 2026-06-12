---
title: "Explain how patch scripts work"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by movrshakr on 2008-11-03
In another forum, I see posts by people that include "patch scripts."  Can someone help me understand these (examples below)--not the specific content, but how you employ them (make them 'do their magic'), how they work?

I assume the minus lines will be deleted and the plus lines will be added, but what do the --- and +++ lines mean?  The @@ lines?

========= BEGIN EXAMPLE 1 ===============================
--- init.d.orig/ntp	2008-11-03 16:09:40.000000000 +0000
+++ init.d/ntp	2008-11-03 15:57:43.000000000 +0000
@@ -37,6 +37,11 @@
 			log_failure_msg "user \"$RUNASUSER\" does not exist"
 			exit 1
 		fi
+                ntpdate-debian
+                if [ $? -eq 0 ]
+                  then
+                    hwclock --systohc
+                fi
   		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --startas $DAEMON -- -p $PIDFILE -u $UGID $NTPD_OPTS
 		log_end_msg $?
   		;;
========= BEGIN EXAMPLE 2 =============================
--- if-up.d.orig/ntpdate	2008-11-03 16:07:12.000000000 +0000
+++ if-up.d/ntpdate	2008-11-03 15:55:04.000000000 +0000
@@ -23,10 +23,17 @@
 	OPTS="-b"
 fi
 
-invoke-rc.d --quiet ntp stop || true
-
-/usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null
-
-invoke-rc.d --quiet ntp start || true
+invoke-rc.d --quiet ntp status
+if [ $? -eq 0 ]
+  then
+    # Note: ntpdate-debian & the hwclock will be performed by the rc.d script.
+    invoke-rc.d --quiet ntp restart || true
+else
+    /usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null
+    if [ $? -eq 0 ]
+      then
+        hwclock -systohc
+    fi
+fi
 
 ) &
========= END EXAMPLE 2 ===============================

---

### Post by conscious on 2008-11-03
What you posted are diff files. They are generated with the **diff** command and applied with the **patch** command.

For the description of the diff file format, see e.g. [this page]("http://www.chemie.fu-berlin.de/chemnet/use/info/diff/diff_3.html"), especially "unified format" section.

---

### Post by movrshakr on 2008-11-03
Thanks...I think!

Sometimes the power of linux is frustrating.  Now I see another whole day of studying the doc at the link you gave and figuring it all out.

---

### Post by Cypher on 2008-11-03
As a very simple explanation, the processing of "patching" a file basically allows you to alter it in a KNOWN way.

The diff that is used as an input to the patch program is the delta between what you have and what someone else (the person who gave you the diff file) has. When the diff is applied, your file and the other person's file will now be the exact same thing.

Diff'ing/Patch'ing is predominently used with code and very effectively in the Linux Kernel development. This allows a developer to submit changes to a particular codebase without having to transmit the ENTIRE file. As long as the person applying the patch is using the SAME file from which the developer began their changes, the patch will apply.

---

