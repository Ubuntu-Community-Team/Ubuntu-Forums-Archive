---
title: "Getting Downloads to Work"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by dalew on 2008-05-01
Downloading software in Ubuntu seems easy, but getting it to do anything seems impossible.  Example: I have downloaded GoogleEarthLinux.bin to the Desktop.  Clicking on it brings up the message "There is no application installed for this file type". What do I have to do to get Google Earth to work? I'm probably doing something fundamentally wrong, but it's not obvious and, as a reasonably computer-literate engineer, I'm feeling somewhat frustrated.  I'm using Hardy Heron Ubuntu 08.04.

Thanks in advance.

---

### Post by Monicker on 2008-05-01
Ack. Got that wrong. Must have misremembered.

Anyhoo, take a look here:

[http://earth.google.com/support/bin/answer.py?hl=en&answer=44713]("http://earth.google.com/support/bin/answer.py?hl=en&answer=44713")


At one time they had their instructions for linux more prominently displayed.  Now you have to dig around for them a bit.


This might also help:
[https://help.ubuntu.com/community/GoogleEarth]("https://help.ubuntu.com/community/GoogleEarth")

---

### Post by dalew on 2008-05-01
Thanks, Monicker.

Brain now engaged, and the application seems to have installed OK.  However, clicking on the icon (or starting from terminal) causes the machine to re-boot.  At the moment, everything to do with Google Earth is located in my home directory, rather than in root, so I'll sleep on it (it's 1 AM in the UK) and try tomorrow.

Incidentally, while the local Ubuntu Help does mention executables in various places, there is no reference to them or binary files in the obvious topic of "Adding, Removing and Updating Applications".  An opportunity for improvement, perhaps?

Anyway, once again, thanks for your help.

---

### Post by Tatty on 2008-05-01
It is not normal to install software in ubuntu by downloading an executable file.  

The vast majority of software is in the repositories so you should install via synaptic package manager.  Google earth is in there, it might be better for you to uninstall the one you have installed and re-install from the repos, this makes for a much cleaner and easier to maintain system.

But if you do want to install this binary file as root then you need to preface your command with sudo to gain superuser powers.

```
sudo sh GoogleEarthLinux.bin
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  this might help.

---

