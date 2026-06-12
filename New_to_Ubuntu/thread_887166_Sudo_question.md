---
title: "Sudo question"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by lapubell on 2008-08-11
I have been working on setting up the ultimate Openbox configuration for my laptop.  I'm almost there!

Everything is looking great and I've got most everything configured, but one thing that my machine is missing is the automated suspend to RAM thing that worked great in both gnome and kde.

I found a script that works great (and blazing fast) to suspend, and my machine wakes up great.  The only issue is that I need to have root permissions to run the script.  I want to set this command to a hot key, and be able to close my lid and have it work, but right now I have to put in the kdesu password, and then it suspends perfectly.

Is there a way to make this ONE command work as root without the prompt?  I know about setting the sudoers file to NOPASSWORD, but I don't want to do that, just make this one script run as root automatically.

Thanks in advance!

---

### Post by sillyxone on 2008-08-11
I'm not a KDE user so I'm not sure, but can you edit /etc/acpi/lid.sh and call the script from there? I think this way when you close the lid, the system will run lid.sh as root, and thus will call your script as root too.

---

