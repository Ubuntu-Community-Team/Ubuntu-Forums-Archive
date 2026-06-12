---
title: "[SOLVED] SSH into my computer - not letting me now"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by melbs on 2008-08-15
I am using VMware (thanks for suggestions from here :) )to SSH into my desktop computer from my lap top. Everything worked fine earlier but then I reinstalled ubuntu on my desktop computer and now when I try to SSH into it, it gives me "Warning: Remote Host Identification has changed!" It has some more lines about maybe someone is "doing something nasty" and about the "host key" being changed, etc. I assume this is because I reinstalled unbuntu on that computer. How can I get my SSH to work now? THANKS!

---

### Post by maddog39 on 2008-08-15
Try running this command from a terminal, or in nautilus in your home directory View > Show Hidden Files and delete the .ssh directory and try again.
```

rm -rf ~/.ssh

```

---

### Post by melbs on 2008-08-15
Of course, it worked :)

Another follow up question after I did the SSH ip address is gave me:

[INDENT]```
The authenticity of host 'xxx.xxx.x.xxx (xxx.xxx.x.xxx)' can't be established.
RSA key fingerprint is [...numbers:and:colons:....].
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'xxx.xxx.x.xxx1' (RSA) to the list of known hosts.
melissa@xxx.xxx.x.xxx's password: 
```
[/INDENT]
(x's = my ip)

After I did "yes" it worked (and this happened when I did it the first time too) but is that supposed to happen? What does that mean? Just curious.

---

### Post by The Cog on 2008-08-16
It means that SSH can't be sure you have connected to the machine you wanted to. This is (of course) that we don't recognise its certificate because we've never seen it before. 

It's like meeting someone for the first time and they say:
> I'm Brian, and to make sure you always know its me in future, I will always use this secret password..
Yeah fine, you can be sure it's the same guy next time you meet him by making a note of the password, but how do you know this is **really** Brian to start with? 

The prompt lets you know that SSH has no evidence that it has connected to the computer you wanted to.

---

### Post by melbs on 2008-08-18
Thanks for the explanation.

---

