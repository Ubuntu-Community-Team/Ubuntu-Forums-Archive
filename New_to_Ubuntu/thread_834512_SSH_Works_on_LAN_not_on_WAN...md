---
title: "SSH: Works on LAN not on WAN.."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by dpippin on 2008-06-19
SSH: Works on LAN not on WAN it gives me access denied.

I have Hardy 8.04 server edition.
I'm having trouble logging into SSH via the WAN side.  The problem is when I enter the domain name or IP address from an outside computer it connects and asks for user name and than password (like normal).  However it says the password is wrong and disconnects me after three unsuccessful tries.  It's the same user name and password I'm using on SSH on the LAN side which works.  I've been pulling my hair out and can't figure out what is wrong.  THANKS for helping me out.

SOLVED/Update:  Update I guess there is someone else on my network running a SSH client on port 22.  Even though I have port 22 forwarded to my servers local ip address it doesn't seem to matter it still logons to the other machine running the SSH Server.  It fooled me because it was working on port 22 from the LAN side.

---

