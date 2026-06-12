---
title: "[SOLVED] Upgrade to Flash Player 9"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Mel_K on 2008-05-12
Hi, 
I need to upgrade my flash player to version 9 as many sites that I use are now telling me to do so.

According to Synaptic, I already have the plugin version 9.0.124 installed.

According to Adobe's version test, I have version LNX 7.0.25.0 

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507)

What next?  Should I un-install and then re-install via Synaptic?
Many thanks!

---

### Post by SunnyRabbiera on 2008-05-12
well if its working then you should not worry.

---

### Post by MaindotC on 2008-05-12
If for some reason its not working, try installing the package of restricted extras that includes the latest version of Flash:

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Mel_K on 2008-05-12
No, Flash isn't working on most sites at all.  Usually, it get a message asking me to upgrade to the latest version.

I have just tried to get the restricted extras and this is the outcome:

[INDENT]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
me@me-desktop:~$ [/INDENT]

What should I try now?

---

### Post by MaindotC on 2008-05-12
You need to enable the multiverse repository.  Open up Synaptic Package Manager, click "Edit" then click "Repositories".  Check the box that says multiverse, then reload the repositories, search for the package, and install.

---

### Post by aysiu on 2008-05-12
The first time you installed Flash (before it was Flash 9), what method did you use?

---

### Post by Mel_K on 2008-05-12
Previously, I had Flash Player 7.

In synaptic, I unchecked the multiverse, then re-checked it and also checked the source code (it didn't have a full check mark)
Then it looked for updates.

I restarted my machine and found the flash 9.0.124- which now had a star next to the grey box.
I marked it for upgrade and all is working well.

Many thanks

---

### Post by MaindotC on 2008-05-12
Be sure to give me a star!

---

