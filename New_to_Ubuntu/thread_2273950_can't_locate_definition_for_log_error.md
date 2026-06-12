---
title: "can't locate definition for log error"
date: 2015-04-16
forum: New to Ubuntu
---

### Post by nick180 on 2015-04-16
I ran sudo apt-get update

After fetching packages the following is listed... and this was also present at the previous run of update a few days back.

Fetched 3,601 kB in 23s (153 kB/s)                                             
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DF9B28CA252A784
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
nick@base1268-ubuntu:~$ 

can anyone suggest how or even if I can make the PUBKEY available please...?
and how to remove one of the duplicate source lists for google chrome ....?

---

### Post by ian-weisser on 2015-04-16
See [http://askubuntu.com/questions/308760/w-gpg-error-http-ppa-launchpad-net-precise-release-the-following-signatures](http://askubuntu.com/questions/308760/w-gpg-error-http-ppa-launchpad-net-precise-release-the-following-signatures) for several ways to fix the key error.

To fix the duplicate sources.list entry, edit the file to remove one of the duplicate lines.
sources.list is owned by root, so remember to use sudo.
Since you must use sudo, it's safer to use a terminal-based editor (like nano).
Example: sudo nano /etc/apt/sources.list

If you use nano, use the arrow keys to navigate, just like you would expect.
After you complete the edit, do CTRL+x to save and exit.

---

