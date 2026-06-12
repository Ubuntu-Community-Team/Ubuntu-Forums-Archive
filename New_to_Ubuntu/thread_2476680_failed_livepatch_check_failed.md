---
title: "failed: livepatch check failed:"
date: 2022-07-02
forum: New to Ubuntu
---

### Post by billy3xs on 2022-07-02
Livepatch is on

[https://wiki.ubuntu.com/Kernel/Livepatch#](https://wiki.ubuntu.com/Kernel/Livepatch#)



Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information.


~$ canonical-livepatch status
last check: 22 minutes ago
kernel: 5.4.0-121.137-generic
server check-in: [COLOR=#ff0000]failed: livepatch check failed[/COLOR]: POST request to "https://livepatch.canonical.com/v1/client/3b8063f7c2bd4fc390ccd717e262a106/updates" failed
patch state: &#10003; no livepatches needed for this kernel yet
tier: updates (Free usage; This machine beta tests new patches.)

So I don't know what I can do in livepatch wiki
please help

---

### Post by billy3xs on 2022-07-02
Ok, I signed up for Ubuntu Advantage and now livepatch is ok...

---

