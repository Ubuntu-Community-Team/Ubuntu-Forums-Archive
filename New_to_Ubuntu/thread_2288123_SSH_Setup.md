---
title: "SSH Setup"
date: 2015-07-24
forum: New to Ubuntu
---

### Post by impost0r on 2015-07-24
[FONT=verdana]Hey commnuity,

first of all I am very sorry, I am 100% sure that there is already an existing post online, but I am simply unable to find one so far.

Here is my problem: I am new to linux and I just set up Ubuntu Gnome (DualBoot). Everything is working so far and I recently got the Idea to install SSH in order to connect to my vServer (a vServer I rent from some cool hoster, so it is not located in my own network!). Connecting via Putty on Windows works without any problem, but if I try to connect via Ubuntu it gives me the following error message:

> ssh: Could not resolve hostname XXX.XXX.XXX.XXX:XXXX: Name or service not known

I have already googled this error message, but everything is just about some local network..
Can anyone provide me a link to solve this problem?

Thanks
**imp**[/FONT]

---

### Post by sgian on 2015-07-24
Both computers need to have the ssh software installed.  Perhaps the vServer doesn't have the same ssh software?  Since Putty works, why not install the linux version of Putty?  I just checked and it is in the software center for Ubuntu 14.04 LTS, but I don't know if it is available for the newer versions of Ubuntu.

---

### Post by SeijiSensei on 2015-07-24
> ssh: Could not resolve hostname XXX.XXX.XXX.XXX**:XXXX**: Name or service not known 

Are you trying to connect on some port other than the standard 22?  If so, that isn't the correct syntax for the SSH client.  Use
```
ssh -p port_number hostname
```

---

### Post by Bucky Ball on 2015-07-24
Putty works fine in Ubuntu and is in the Software Centre if that is not what you are already using.

Have you got the required SSH software in your local install? If the server end is working ok with Windows then I'd suspect something might be missing at your end in Ubuntu. Don't know what is installed by default re. ssh in Ubuntu so see if you have openssh-client installed.

PS: Filezilla is also in the repos and is great for sftp/ftp stuff. :)

---

### Post by ajgreeny on 2015-07-24
Here's a good place to start trying to figure out what is wrong with your SSH settings.
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

This page is really just links to other more detailed pages about the complete business of SSH but I suggest you read as many of them as you can manage.

And good luck!

---

