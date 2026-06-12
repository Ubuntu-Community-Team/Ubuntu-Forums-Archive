---
title: "stack smashing detected"
date: 2023-01-08
forum: New to Ubuntu
---

### Post by rajeshraoshindhe on 2023-01-08
I am working with an aws instance, linux OS. I tried the following command line:
```
scp     -i     xyz.pem     path/of/filename/on/ubuntu/machine     [email]ec2-user@xx.xx.xx.xx[/email]:destination/folder/on/aws/instance
```
wiith the intention of transferring the file. But it threw an error log as follows.

```
*** stack smashing detected ***: terminated   lost connection
```

This kind of error never happened before. I have used the above command line many times successfully in the past.
Error logs like this appear when I log into the aws instance, while using some commands like "ls"  too.  Also I am unable to upload files also from my ubuntu m/c into the aws instance m/c also since then.
May I know what is this problem and how to overcome it ?

Thanks

---

### Post by malusdomestica314 on 2023-01-23
This error is basically caused when the system detects that a program is causing a buffer overflow and shuts that program down.

Obviously, since a simple ‘ls’ shouldn’t cause that to happen, I would say something is badly wrong with the hardware of the AWS instance you’re working on, and the least painful way of dealing with it is to replace the instance.

I would say to make a clone of your system disk and make a new EC2 instance using that cloned EBS volume as the system disk of the new instance. Then see if the issue reproduces on the new instance, if it doesn’t, then shut down the old instance and use the new one.

If it does reproduce on the new instance, then investigation would be next steps.

---

