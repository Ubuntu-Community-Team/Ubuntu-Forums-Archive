---
title: "Does anyone know ??"
date: 2006-06-20
forum: Programming Talk
---

### Post by SteffJay on 2006-06-20
Does anyone know how to auto-start **Verlihub** in Dapper  :confused:

---

### Post by SteffJay on 2006-06-22
Here is the answer:

**Verlihub Auto-Boot script**

**nano -w /etc/init.d/verlihub**
add a line: **/usr/local/bin/verlihub**
ctrl+x to save the file
at the nano prompt press enter
Close Terminal

then open new terminal:

root@server:# **cd /etc/init.d**

(copy/paste to terminal) **chmod +x /etc/init.d/verlihub**

(copy/paste to terminal) **sudo update-rc.d verlihub start 51 S .**   <<<(dont forget the . )

(copy/paste to terminal) **update-rc.d verlihub defaults**

root@server:/home/(yourname)# **ls -la /usr/local/bin**
total 452
drwxr-xr-x 2 root root   4096 2006-06-20 09:44 .
drwxr-xr-x 9 root root   4096 2006-06-18 19:22 ..
-rwxr-xr-x 1 root root 407562 2006-06-20 09:43 verlihub
-rwxr-xr-x 1 root root    831 2006-06-20 09:44 verlihub_config
-rwxr-xr-x 1 root root    664 2006-06-20 09:44 vh_getcfg
-rwxr-xr-x 1 root root   2737 2006-06-20 09:44 vh_getdb
-rwxr-xr-x 1 root root   7477 2006-06-20 09:44 vh_install
-rwxr-xr-x 1 root root   1031 2006-06-20 09:44 vh_regnick
-rwxr-xr-x 1 root root    423 2006-06-20 09:44 vh_restart
-rwxr-xr-x 1 root root   2169 2006-06-20 09:44 vh_runhub
-rwxr-xr-x 1 root root    975 2006-06-20 09:44 vh_setup
-rwxr-xr-x 1 root root   1422 2006-06-20 09:44 vh_trigger
root@server:/home/(yourname)#

Reference:   **[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)**

---

### Post by Meserias on 2007-11-24
**SteffJay** I try to make what you suggest on Ubuntu 7.10 but with [COLOR="Red"]no [/COLOR]luck it's simply doesn't start it self. Do you now a good solution to make VerliHub to start automatically even without to make login.:confused:

---

### Post by herates on 2008-07-11
its too late but u have to use the command vh_run instead of verlihub

---

