---
title: "[SOLVED] Configuration Problem - DPKG was interrupted"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by webbooknovice on 2008-08-19
Dear all, I am a novice user of Linux products and recently took the plunge and purchased a Elonex Webbook from Carphone warehouse. I had a great deal of difficulty setting up the T-Mobile Dongle to work with the unit, but eventually got there. I tried to stop a software upload and now keep getting the following error messages:- 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache >open(failed) pls report.

Any help to resolve this matter would be gratefully received. I'm not sure how to manually enter the command.

Thanks

Andy

---

### Post by Perfect Storm on 2008-08-19
Close synpatic and/or add/remove.

Open the terminal;

```
sudo dpkg --configure -a
```

---

### Post by webbooknovice on 2008-08-19
> **webbooknovice said:**
> Dear all, I am a novice user of Linux products and recently took the plunge and purchased a Elonex Webbook from Carphone warehouse. I had a great deal of difficulty setting up the T-Mobile Dongle to work with the unit, but eventually got there. I tried to stop a software upload and now keep getting the following error messages:- 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache >open(failed) pls report.

Any help to resolve this matter would be gratefully received. I'm not sure how to manually enter the command.

Thanks

Andy
Many thanks for the quick response. Have input as suggested and get the reply 'Requested operation requires superuser priv'. Any further ideas. Thanks for taking the time and trouble to help resolve this. Andy

---

### Post by ace007 on 2008-08-19
You added the sudo command in front of the dpkg command? Then it asked for your password? Is your profile the administrator?

If your profile does not have administrator privileges then you cannot run the command, but I can tell you, that command is the one you want.

---

### Post by webbooknovice on 2008-08-19
> **ace007 said:**
> You added the sudo command in front of the dpkg command? Then it asked for your password? Is your profile the administrator?

If your profile does not have administrator privileges then you cannot run the command, but I can tell you, that command is the one you want.

__________________________________________________________________________

Thanks. I am the sole user of the Elonex Webbook. Any ideas as to how I assign administrator privs to my profile. Sorry to hassle. Andy

---

### Post by webbooknovice on 2008-08-19
Dear all, many thanks for your help. all sorted now. Great support!  Andy

---

