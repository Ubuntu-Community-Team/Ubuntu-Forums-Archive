---
title: "problem installing libmono-system-data2.0-cil when upgrading from gutsy to hardy"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by b_ron on 2008-05-10
During upgrading from gutsy to hardy, there was a problem with installing some packet.  I did not know what to do, so I just ignored it.  Well, after the upgrade, my update manager says that I have a distribution update: libmono-system-data2.0-cil.

I click Install Upgrade and I get a window telling me an error occurred and that
[I]
E: /var/cache/apt/archives/libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb: failed to stat (dereference) existing symlink `/usr/lib/mono/2.0/System.Data.dll'[/I]

Then a few seconds passes by and another window pops up and says "Not all changes and updates succeeded."  Then the terminal results display

[I](Reading database ... 131119 files and directories currently installed.)
Preparing to replace libmono-system-data2.0-cil 1.2.4-6ubuntu6.1 (using .../libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb) ...
Unpacking replacement libmono-system-data2.0-cil ...
dpkg: error processing /var/cache/apt/archives/libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/lib/mono/2.0/System.Data.dll': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/I]

Please help.

---

### Post by park8b156 on 2008-05-10
I get this alot. I don't know a real fix besides waiting a few hours and try again.  Thats what I do then it works. You may have to do this a few times.

---

### Post by b_ron on 2008-05-14
The past several days when I have turned my computer on, I go to the update manager, and I click to install "libmono-system-data2.0-cil" and the result is the same.  The same errors occur.

I have also left the computer on for awhile, walked away for hours, came back and went to the update manager to install again.  Still no results.  The same errors occur.

Please help.

---

