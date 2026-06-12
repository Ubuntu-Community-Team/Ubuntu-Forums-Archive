---
title: "Remmina Remote Desktop Client"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by alabamatoy on 2013-03-17
Works fine under my account, wont connect under wifes account.  I have made her account administrator, still wont work.  Under my account, it connects instantly.  Under hers, it just sits there.

TIA....

---

### Post by uc50_ic4more on 2013-03-17
Are you using VNC or an SSH tunnel? If it's the latter, you could have everything from username to certificate issues when attempting to use your wife's account rather than your own. If you're "just" using VNC then I guess I can only suggest doing the obvious: double and triple checking protocols, passwords, ports, etc.

Also, I wonder if you could try using a VNC command line client (sorry, I don't know of a good one off-hand) from your wife's account to see if any coherent error messages are spat out that might point us in the right direction.

Can you use Remmina successfully from your own account even after a failed attempt from your wife's account? I have mistakenly set some VNC *servers* (x11vnc) to terminate after the initial connection is closed. This resulted in much frustration, wasted time and a feeling of stupidity after I had figured out what I'd done!

Does the target machine run a SSH server? If so, can you log into the target machine from both accounts?

---

### Post by alabamatoy on 2013-03-19
Please delete this question.  I had accidentally set the client for a display resolution that the server could not provide.

---

