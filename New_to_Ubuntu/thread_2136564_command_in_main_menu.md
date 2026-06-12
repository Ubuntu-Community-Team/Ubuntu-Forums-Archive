---
title: "command in main menu"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by tdubster on 2013-04-18
Hi,

I use pidgin and pidgin-sime to connect to lync at my workplace.

Currently there is a bug where you need to type a command before launching Pidgin for it to logon.

So I need to type in terminal:

~$ export NSS_SSL_CBC_RANDOM_IV=0 pidgin

for it to logon correctly.

I am trying to make this available through the pidgin "shortcut" (excuse my windownese) using main menu to edit it, however I can't seem to get it going correctly.  I always seem to get don't know child command or similar.

Can anyone help?

Thanks

---

### Post by steeldriver on 2013-04-18
It should be possible using the 'env' command in your .desktop file

```
Exec=**env** NSS_SSL_CBC_RANDOM_IV=0 pidgin
```

See here -->  [https://help.ubuntu.com/community/EnvironmentVariables#Launching_desktop_application_with_an_environment_variable](https://help.ubuntu.com/community/EnvironmentVariables#Launching_desktop_application_with_an_environment_variable)

Regards

---

### Post by tdubster on 2013-04-24
Thanks for your reply.  Seems to have done the trick with a bit of playing around.

Just to clarify for those using main menu specifically.

You need to select:

Type: Application in Terminal

Command: env NSS_SSL_CBC_RANDOM_IV=0 pidgin


I assume main menu defaults the Exec= part for you and the export command isn't required.

THanks

---

### Post by tdubster on 2013-05-06
For anyone searching this.  It has changed slightly in ubuntu 13.04.

You need to have the command as: 

export NSS_SSL_CBC_RANDOM_IV=0 pidgin

Cheers

---

