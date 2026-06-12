---
title: "Command equivalent to yum provides in Ubuntu"
date: 2020-06-20
forum: New to Ubuntu
---

### Post by warronfrench on 2020-06-20
I am new to Ubuntu, and I am running **Ubuntu 20.04 LTS** (***focal***).

I am working on installing and configuring the product **mailman**. One of the commands was to add some lines to the file **/etc/aliases** and then execute newaliases.  I did that and discovered that the command expected the file /etc/postfix/main.cf.  

I executed the "Ubuntu equivalent" command for RHEL-variants' command:
```
yum provides /etc/postfix/main.cf*
```

The command that I specifically used was:
```
apt-file search  /etc/postfix/main.cf*
```
The result did not provide me with the name of a package, as I know would occur with the RHEL-variant command.  So, I decided to check for the existing of the file within /etc/postfix.  I found the file /etc/postfix/main.cf.proto, which I believe should have been found and the package name provided.

Did I do something wrong or is the command output on Ubuntu not at all like the command used in Red Hat Enterprise Linux (RHEL), Scientific Linux, or CentOS?

Thanks,
Warron

---

### Post by ActionParsnip on 2020-06-21
Could also try packages.ubuntu.com to verify your findings too

---

### Post by NM5TF on 2020-06-21
Hi Warron...

in short, the answer is yes..you might find some interesting reading here....

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/)

and more specific to your question might be found here....

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora)

tommy

---

### Post by oldrocker99 on 2020-06-21
Apt is very different from yum, which is very different from pacman or yay.

Your best bet is to read the apt manpage.

---

