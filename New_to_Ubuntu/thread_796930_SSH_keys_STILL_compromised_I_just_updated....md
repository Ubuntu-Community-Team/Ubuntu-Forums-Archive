---
title: "SSH keys STILL compromised? I just updated..."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by alecwh on 2008-05-16
Hello!

I have an account over at Launchpad, and I have an SSH key registered, so I can branch/upload projects that I use.

Anyway, I'm fairly certain that I have downloaded all the updates for the SSH bug, I've regenerated it with "ssh-keygen", and tried to upload it back to Launchpad. I get this error:

> This key is known to be compromised due to a security flaw in the software used to generate it, so it will not be accepted by Launchpad. See the full Security Notice for further information and instructions on how to generate another key.

What's wrong?

---

### Post by Xiong Chiamiov on 2008-05-17
I believe that all keys need to be regenerated, since they are all considered suspect since the vuln was found.

---

