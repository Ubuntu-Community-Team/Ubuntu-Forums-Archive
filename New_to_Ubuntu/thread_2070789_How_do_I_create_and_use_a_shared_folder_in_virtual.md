---
title: "How do I create and use a shared folder in virtualbox with an ubuntu Guest OS?"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by Codeless on 2012-10-13
I'm afraid I need someone to explain exactly what I need to do because I'm not good at this stuff. This is what I have done so far.

Installed ubuntu Guest OS using virtualbox
Installed guest additions
Virtualbox > settings > shared folders > created "Shared" (C:\Users\...\Shared)

Logged into ubuntu Guest OS
created folder on desktop called Shared
opened terminal
sudo mkdir /media/Shared (no error)
sudo mount -t vboxsf Shared /media/Shared (no error)

What did I do, did I do something wrong, how do I transfer files? I need an idiots set of instructions please.

I intend to use ubuntu guest OS as a sandbox area for internet browsing - as a way to protect my host OS from malware. Ideally I want to save a state with all this set up and launch that state to use the internet, transfer files, restore state. 

Thank you

---

### Post by Codeless on 2012-10-13
wait I got it work... thanks anyway

---

