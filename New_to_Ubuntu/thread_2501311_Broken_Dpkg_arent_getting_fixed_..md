---
title: "Broken Dpkg arent getting fixed ."
date: 2024-10-01
forum: New to Ubuntu
---

### Post by jimzeb on 2024-10-01
I am having an issue in updating and upgrading ubuntu because of this.

```
sudo apt install --fix-broken
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
9 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libcups2t64:amd64 (2.4.7-1.2ubuntu7.3) ...
dpkg: error processing package libcups2t64:amd64 (--configure):
 too-long line or missing newline in '/var/lib/dpkg/info/libcups2t64:amd64.trigg
ers'
dpkg: dependency problems prevent configuration of cups-ipp-utils:
 cups-ipp-utils depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-ipp-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-ppdc:
 cups-ppdc depends on libcups2t64 (>= 2.3~b6); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-ppdc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-coNo apport report written because the error
 message indicates its a followup error from a previous failure.
                                                                No apport report
 written because the error message indicates its a followup error from a previou
s failure.
          No apport report written because MaxReports is reached already
                                                                        No appor
t report written because MaxReports is reached already
                                                      No apport report written b
ecause MaxReports is reached already
                                    No apport report written because MaxReports 
is reached already
                  No apport report written because MaxReports is reached already
                                                                               N
o apport report written because MaxReports is reached already
                                                             re-drivers (--confi
gure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 2.4.7-1.2ubuntu7.3); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-ppdc; however:
  Package cups-ppdc is not configured yet.
 cups depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-bsd:
 cups-bsd depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-bsd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-client:
 cups-client depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcupsimage2t64:amd64:
 libcupsimage2t64:amd64 depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package libcupsimage2t64:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on libcups2t64 (= 2.4.7-1.2ubuntu7.3); however:
  Package libcups2t64:amd64 is not configured yet.


dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcups2t64:amd64
 cups-ipp-utils
 cups-ppdc
 cups-core-drivers
 cups
 cups-bsd
 cups-client
 libcupsimage2t64:amd64
 cups-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What am i not doing?

---

### Post by ian-weisser on 2024-10-01
The next step is suggested in your output.

> **jimzeb said:**
> ```

Setting up libcups2t64:amd64 (2.4.7-1.2ubuntu7.3) ...
dpkg: error processing package libcups2t64:amd64 (--configure):
 **too-long line or missing newline** in '/var/lib/dpkg/info/libcups2t64:amd64.triggers'
dpkg: dependency problems prevent configuration of cups-ipp-utils:

```

Look at the content of that file.

```
cat /var/lib/dpkg/info/libcups2t64:amd64.triggers
```

If that file has an obvious newline problem, and you know how to fix it, then do so.

Else show us the complete contents of that file. Proper formatting is critical, as we need to see where the missing newline should be.

---

