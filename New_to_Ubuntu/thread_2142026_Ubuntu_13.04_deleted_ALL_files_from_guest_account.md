---
title: "Ubuntu 13.04 deleted ALL files from guest account"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by srikanthganta on 2013-05-04
[COLOR=#333333][FONT=Ubuntu Beta]It looks very strange and surprising for me...deleting ALL the files folders automatically. [/FONT]
[FONT=Ubuntu Beta]Ubuntu should at-least give a warning message when Guest Lo-gout/shut-down..like the disk space allocated for Guest is Formatted.[/FONT]
[FONT=Ubuntu Beta]I don't think any windows OS does like this..? for their guest accounts..automatically [/FONT][/COLOR]

---

### Post by deadflowr on 2013-05-04
Guest accounts create a temporary folder/file, which are as the name implies are temporary.
Once the session ends, the data disappears. 
Guest sessions are to be seen as one-shot uses.
Not like regular user accounts, which save sessions.

Added: If any data is still on the disk for the guest session, it is in the /tmp directory.

---

### Post by grahammechanical on 2013-05-04
Wouldn't you complain if a guest account user filled up your hard disk and you were unable to save an important document because of that?

---

### Post by srikanthganta on 2013-05-04
How come the latest versions of Ubuntu (13) are even NOT able to give a small popup message like.."Hi guest user please copy your data to safe place before logout/shutdown because your data is deleted permanently" ?

---

### Post by Champlin93 on 2013-05-04
You can create a new standard account with no password for your guests to use and store data on.  Personally I think there should be more options for the guest account like being able to store data permanently or disable guest accounts all together and there definitely should be a dialog box notifying users there data will not be stored on a guest account.

---

