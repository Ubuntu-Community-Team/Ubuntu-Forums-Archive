---
title: "Read-only file system in scripts during boot"
date: 2008-02-17
forum: Programming Talk
---

### Post by TrevorP on 2008-02-17
<BACKGROUND>
I run a local apt-cache server, and to enable computers on the network to use it i add a file in /etc/apt/apt.conf.d/ with an Acquire::http::Proxy directive to point apt at the cache. This all works fine, but I have some machines that move to other networks. When this happens, they cant find the cache (it is only available on this local network), and thus cant update. Removing the directive works fine, they can then update, and I need to add it back when the computers come back to this network.

I'd like an automated solution to disable/enable the cache.
</BACKGROUND>

I wrote some years ago a script installed in /etc/network/if-up.d/ to detect the presence/absence of the cache, and write/remove the proxy directive. The problem is (and always was) that this script didn't work on startup. Testing the script now, it generates a "Read-only file system" error when trying to write to the file in /etc/apt/apt.conf.d/.

At that point in boot (so far as I can tell) the file system is mounted as rw, and it is a read only error, not a permissions error, so this one has me stumped.

So, does anyone know how to get this script to be able to write a file during boot? or why it doesn't/can't write the file?

Another solution: if i can detect the machine is booting, I can exit the script, and have another bootscript do the job for me. How do I detect that the machine is booting?

Additionally, is if-up.d the appropriate place to put the script? will it re run every time the network cable is replugged (without rebooting the machine)?

TIA

---

