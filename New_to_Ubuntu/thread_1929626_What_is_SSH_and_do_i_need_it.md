---
title: "What is SSH and do i need it?"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by EzioAuditore on 2012-02-22
Well Hello everyone,

The title says it all. SSH to me is some sort of remote desktop connection type thing ( correct me if i'm wrong ). 

Thing is, I don't do such stuffs and have no need of it. And the fact that its running at every system startup ( sshagent running in system monitor ) kind of bugs me as it poses potential security threats (i might be wrong though ).

What  I just want is to completely disable it. Googled but didn't get any satisfactory result.

How do I go about it folks? Ubuntu 10.10 here.

Thanks.

---

### Post by cheatos on 2012-02-22
Well, it isn't exactly a remote desktop, you just get a command-line of the machine you log in to.
It can be pretty useful though, if you want to download a large file from a computer or something.

I can't say anything about the security issues with ssh but I don't think they're very high as long as you have a good password.

If I'm wrong, please someone correct me.

---

### Post by EzioAuditore on 2012-02-22
Well thanks for the reply cheatos.

As i said, no current plans on using it. So, how to disable it?

---

### Post by roelforg on 2012-02-22
If you didn't instal sshd, it's already off.

---

### Post by Bachstelze on 2012-02-22
> **EzioAuditore said:**
> 
Thing is, I don't do such stuffs and have no need of it. And the fact that its running at every system startup ( sshagent running in system monitor ) kind of bugs me as it poses potential security threats (i might be wrong though ).

You are wrong, it does not pose any security threat.

---

### Post by EzioAuditore on 2012-02-22
> **roelforg said:**
> If you didn't instal sshd, it's already off.

I didn't. Thanks you.:)

> **Bachstelze said:**
> You are wrong, it does not pose any security threat.

I thought there could be some vulnerability that could allow people to break into my system, well but that's wrong though. Thanks for the correction. ;)

I think this can be marked as 'SOLVED' now.

---

### Post by haqking on 2012-02-22
> **Bachstelze said:**
> You are wrong, it does not pose any security threat.

[s]so you think that having a running remote administration tool such as SSH running when you dont need it is not a potential security issue then ?[/s]

Edit: i see it is just the agent running and not the server ;-)

---

