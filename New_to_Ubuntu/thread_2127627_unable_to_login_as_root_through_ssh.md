---
title: "unable to login as root through ssh"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by khoshalar on 2013-03-20
Helloes,

I am unable to login as root through ssh, when logging in using ssh-key and when it prompts to enter the 
user ,If I enter "root" it says -- Please login as the user "ubuntu" rather than "root". and the screen closes automatically.
I  tried making an entry manually as the following line was not there, in  /etc/ssh/ssh_config  saying,
PermitRootLogin yes

But its still the same.,please help.,thanks in advance.,

---

### Post by arpanaut on 2013-03-20
The root user is disabled in Ubuntu by default.
Try logging in as the admin user you set up on install and use sudo to gain "root" privileges.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by khoshalar on 2013-03-20
thanks for the quick reply,

But I am using su - ,to login as root,,
However I want to login as root directly ,using ssh, and I am trying to login to aws ec2 instance using putty ,ssh private key,
so now what I am going thru is,
in the first login prompt I have to enter "ubuntu" as username ,then su -,to gain root access,
can i directly ,give "root" in the login prompt,
this is a test server,so there is no issues with logging in as root,

---

### Post by arpanaut on 2013-03-20
You should be able to enable the root user, but due to forum policy I am unable to assist.
Did you read the entire page I linked to?
From that information you should be able to figure it out.

---

### Post by lisati on 2013-03-20
> **khoshalar said:**
> thanks for the quick reply,

But I am using su - ,to login as root,,
However I want to login as root directly ,using ssh, and I am trying to login to aws ec2 instance using putty ,ssh private key,
so now what I am going thru is,
in the first login prompt I have to enter "ubuntu" as username ,then su -,to gain root access,
can i directly ,give "root" in the login prompt,
this is a test server,so there is no issues with logging in as root,

As arpanaut points out, forum policy doesn't allow us to give instructions on logging on as root. You might want to think of this as a safety precaution to help prevent new users accidentally putting themselves in a position to seriously break their system.

The information you have asked for is provided in the link arpanaut provided: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by khoshalar on 2013-03-20
Yes I read the link, and I see that it explains about sudo entries and creating root password using ,sudo passwd root,

I have already set this root password , what I am looking is with the ssh key ,when i try to login to the server, and enter the username as "root" , it comes back saying  
 Please login as the user "ubuntu" rather than "root"

so can I enter the username as "root" in the ssh login prompt as it is authorized with ssh key,( besides this is a test server i deployed and I am only trying reduce few steps and try to login as root in the first go)   

I also checked in /etc/ssh/sshd_config (earlier I only mentioned /etc/ssh/ssh_config) and the entry is -- PermitRootLogin yes


thanks,

---

### Post by khoshalar on 2013-03-20
hi,
thats ok,

many thanks for the suggestions tho.,

---

