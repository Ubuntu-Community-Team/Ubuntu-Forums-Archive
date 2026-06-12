---
title: "[SOLVED] ssh with certificates in a script"
date: 2008-11-24
forum: Programming Talk
---

### Post by ldevil on 2008-11-24
I'm trying to set up a script to connect from one vm to another with ssh and copy a file. This works fine when I start the script as root, but it is not working when I start the script during logon:

smylink in "/etc/rc2.d/" to a script in "/etc/init.d/" that starts up 5 scripts that need to run. Those scripts are located in "/home/aslca/scripts/".

The script is run as root according to "whoami" but still I get an error saying the keys would not match.

Any ideas?

edit: Today I'm really great - got it working myself :)

copied key to home dir of root, now it seems to work

---

