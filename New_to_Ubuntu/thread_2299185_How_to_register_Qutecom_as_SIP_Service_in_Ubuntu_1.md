---
title: "How to register Qutecom as SIP Service in Ubuntu 14.04"
date: 2015-10-16
forum: New to Ubuntu
---

### Post by Syam_Kumar on 2015-10-16
Hi Team,

I am new to Ubuntu and recently i had installed Qutecom from Ubuntu software center to use this as SIP tool to calls from the system and now i am trying to configure and integrate Telify with Qutecom so that i can make calls by clicking the contacts on webpages. So when try this i get an error message as no Service Protocol detected so can any one let me know how to set Qutecom as an default SIP service for making calls.


Thanks in advance,
Syam

---

### Post by sandyd on 2015-10-16
You need to associate a file handler:

See [http://kb.mozillazine.org/Register_protocol#Linux](http://kb.mozillazine.org/Register_protocol#Linux) (Firefox)

---

### Post by Syam_Kumar on 2015-10-19
i tried the above url but no luck. when i am try this command at the terminal i am getting the following error

command: gconftool-2 -s /desktop/gnome/url-handlers/foo/command '/path/to/app %s' --type String

error: "GConf-WARNING **: Client failed to connect to the D-BUS daemon:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.Error setting value: No D-BUS daemon running"


Also i had changed the path to my application where it is installed but still getting the same error.My command looks like this

"gconftool-2 -s /desktop/gnome/url-handlers/sip/command '/usr/share/applications/QuteCom %s' --type String" 

can you let me know if there is any error in the command line

---

### Post by sandyd on 2015-10-20
Use the instructions below those (Firefox 3.5 and above)

---

### Post by Syam_Kumar on 2015-10-21
> **sandyd said:**
> Use the instructions below those (Firefox 3.5 and above)

I tried to associate the protocol with Firefox but still this is not working.

---

