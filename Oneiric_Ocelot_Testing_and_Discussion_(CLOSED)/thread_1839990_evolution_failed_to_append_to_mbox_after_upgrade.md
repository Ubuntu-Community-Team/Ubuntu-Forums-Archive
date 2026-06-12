---
title: "evolution failed to append to mbox after upgrade"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2011-09-06
After my upgrade to 11.10, whenever I send mail from evolution I get the following message:

The reported error was "Failed to append to mbox:///home/vic/.local/share/evolution/mail/local#Sent: Invalid folder URI 'mbox:///home/vic/.local/share/evolution/mail/local#Sent'
Appending to local 'Sent' folder instead.".

The messages do get sent so this is just an annoyance.  Any idea of how to point this to the right mailbox?

---

### Post by ajira86 on 2011-09-19
Hello, I had the same problem and fix with Evolution FAQ :

> 
[B]Error message "Failed to append to..." after sending message 
[/B]If  the error message "Your message was sent, but an error occurred during  post-processing. The reported error was "Failed to append to  mbox:///home/user/.local/share/evolution/mail/local#Sent: Cannot get  folder 'Sent': folder does not exist. Appending to local 'Sent' folder  instead."." is shown, you can fix the problem by editing your default  folder settings: 
Edit > Preferences > Mail Accounts > Edit > Defaults > Folder for sent messages. 
This  bug is fixed in Evolution versions higher than 3.0.2 (stable series)  and 3.1.3 (unstable development series). If this is not the case, please  add a comment to the corresponding [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=638307"). 


Source : [https://live.gnome.org/Evolution/FAQ](https://live.gnome.org/Evolution/FAQ)

---

### Post by rapiertg on 2011-09-19
Thanks a lot for this. I was struggling with this since dist-upgrading to oneiric.  The problem was that upgrade set it to some non existing folder/ none. Now it works.

---

