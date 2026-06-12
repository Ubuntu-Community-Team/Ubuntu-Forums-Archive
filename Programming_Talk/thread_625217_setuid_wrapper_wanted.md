---
title: "setuid wrapper wanted"
date: 2007-11-27
forum: Programming Talk
---

### Post by mssever on 2007-11-27
I have a Ruby script that must run as root in order to do its job. However, it will be called from Apache (which is responsible for controlling access to the script). Since it would be foolish to run Apache as root, it appears that running my script setuid root is the best option. I understand the security implications of setuid programs and believe that I've adequately addressed them in my script.

The problem I'm up against is this: apparently the kernel ignores the setuid bit on executable text files (such as Ruby scripts). So, I need a setuid C wrapper that will call my Ruby script as root. While C is a language I'd like to learn sometime, I don't know it now. This seems like it should be a trivial program for a C programmer to write. Would somebody be kind enough to throw one together for me (or point me to one that already exists)?

Specs:[LIST]
[*]The wrapper should accept one command-line argument, an IPv4 address
[*]The call for my script should be hard coded for security reasons (except for the IP address which will be passed unmodified to the script).
[*]Ideally, the wrapper should make sure that it can only be run by root or www-data (uid 33 on my box)[/LIST]

---

### Post by mssever on 2007-11-28
After a tip I got on #ruby-lang on freenode, I added the following to my sudoers file:
```
www-data    ALL = NOPASSWD: /path/to/my/script
```This allows me to call the script with sudo from within apache without ever facing a password prompt. It works great.

---

