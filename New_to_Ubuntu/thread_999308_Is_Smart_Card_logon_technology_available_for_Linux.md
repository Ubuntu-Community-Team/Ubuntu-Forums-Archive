---
title: "Is Smart Card logon technology available for Linux Ubuntu?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by suomalainen on 2008-12-01
Ubunteros,

After researching the net, I wanted to learn/ask if anyone is currently using smart card technology to protect their Linux Ubuntu systems.

Here is a link which sums up what I'm looking for:

[http://www.dekart.com/products/access_control/logon/](http://www.dekart.com/products/access_control/logon/)

I'd like to have such protection, but more so one that works in tandem with BIOS because I have a number of mobile racks and internal hard drives in my PC.

My fear is that a solution not working along side with bios will allow mobile racks to be removed and internal drives compromised based on my current configuration...

All and any comments/feedback appreciated.

---

### Post by ibuclaw on 2008-12-01
Best advice I could give is for yuo to look into the **libpam** packages in the repository, they offer a wide range of access level granting, from usb flash devices to fingerprints... though I've never set one up myself, so unless someone else posts to give you some light into it, you are on your own to look it up.

Regards
Iain

---

### Post by suomalainen on 2008-12-01
tinivole,

Thanks for the follow-up! Prior to deployment, I want to ascertain the success of integrating the required hardware. I.E. what others have done.... Particularly as regards driver requirements and the like. Also, I want to know more about any possible SIM requirements. As you may know, some SIM's with less than 3volt specs. will be fried so the readers are equally important in this equation as well....

I don't want to reinvent the wheel. Rather run with what is already working and tested.

Thanks

---

### Post by SunnyRabbiera on 2008-12-01
well it might not have much yet i bet smart cars can work in linux thanks to its diverse kernel.

---

### Post by suomalainen on 2008-12-01
You might be right but time doesn't afford me expense for research and development at the moment....

---

### Post by ushills on 2008-12-04
An alternative is to encrypt the home partition with luks by installing crypt-setup.

You can then place a keyfile on a usb thumb drive instead of a password.

---

