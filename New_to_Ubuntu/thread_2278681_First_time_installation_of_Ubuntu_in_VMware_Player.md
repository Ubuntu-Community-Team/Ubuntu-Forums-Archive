---
title: "First time installation of Ubuntu in VMware Player"
date: 2015-05-18
forum: New to Ubuntu
---

### Post by david391 on 2015-05-18
Hey guys, first post here and thanks in advance.

I'm new to ubuntu and trying to run it in a VM using VMware Player and ubuntu version 14.04.2. I get it loaded up and it recognizes the operating system just fine in the VM, however it takes me to a black installation screen telling me to wait while vmwareplayer is loaded onto the system and to wait for the GUI - however nothing ever happens. It prompts me to enter user name and password in the command line as an option. I'm not really sure what to put in here - the username and password for my ubuntu account will not work. Anyways, sorry for the noob question and appreciate any answers.

I added an attachment of the screen displayed if that helps - assuming this forum doesn't let you upload directly.

---

### Post by sandyd on 2015-05-18
The easy install method for VMWare can be problematic at times. That being said, during the new virtual machine wizard, you should have specified a user/password to be used with easy install. That user/password should allow you to login.

To skip easy install, choose "I will install the operating system later", and then mount the Ubuntu ISO to the VM's CDROM drive after the wizard is done.

---

