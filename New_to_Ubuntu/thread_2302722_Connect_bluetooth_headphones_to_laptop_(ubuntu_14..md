---
title: "Connect bluetooth headphones to laptop (ubuntu 14.10)"
date: 2015-11-12
forum: New to Ubuntu
---

### Post by andrey34 on 2015-11-12
Hello, every body a bought a bluetooth headphones and tryed to connect to my computer, but I couldn't because my comuter didn't want to transmit voice to headphones. Then I went to google, and tryed to fix this problem, but there I was advised to install blueman, it didn't insall (only errors in terminal Not found 404.). Now I can't see bluetooth icon on the top of screen and can't connect my headphones.

Also for some reasons I can't enter to my configuration (right top corn, cogs->about this computer or System settings) I'm clicking to it but nothing happens. How can I fix all of this problems, could you help me?) Thanks.

---

### Post by sandyd on 2015-11-12
You are encountering the 404 errors because Ubuntu 14.10 has reached End Of Life and it's repositories have been archived.
Please see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) to see when releases become EOL.

That being said, it is possible to upgrade to a non EOL edition.
You would have to go through Ubuntu 15.04 (which reaches EOL in January), and then Ubuntu 15.10 if you wish to have a supported version of Ubuntu after January.

About debugging why the system settings don't work...
Try running
```

unity-control-center
```

Are there any errors that you get?
Was the control center working before following instructions to blueman?

---

### Post by andrey34 on 2015-11-13
Yes, control center worked before instructions to blueman. How can I upgrade my system without loosing any data? I have only one drive(

---

### Post by sandyd on 2015-11-14
> **andrey34 said:**
> Yes, control center worked before instructions to blueman. How can I upgrade my system without loosing any data? I have only one drive(

What does running the command output?
Also, what instructions did you follow to install blueman?

Side Note:
If you need it to work ASAP, it may be worth considering copying your data somewhere else and doing a reinstall.

---

