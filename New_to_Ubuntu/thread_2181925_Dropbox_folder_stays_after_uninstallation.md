---
title: "Dropbox folder stays after uninstallation"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by Ashley_Perrin on 2013-10-19
Hi, I have Ubuntu dual booted with windows 7 on my netbook and I installed Dropbox on Ubuntu. I have a lot of stuff on my Dropbox and it started filling up space fast. So I stopped the sync and uninstalled Dropbox and will use the Dropbox website instead from now on. However, the Dropbox folder in my home folder remains. Is it safe to delete this folder and it not delete things off my Dropbox? I'm scared to delete it because I have a lot of photos on my Dropbox and work that I need for college and can't afford to lose. So am I safe to delete the Dropbox folder in my home folder without anything going missing in my dropbox account? It doesn't have the green tick by the files like it usually does but I just want to make sure that these files are a copy of my dropbox and not my actual dropbox. Please let me know if you don't understand, I'm bad at explaining things.
Thank you.

---

### Post by iloutzu on 2013-10-19
Hi Ashley,

If you've uninstalled Dropbox from Ubuntu, it should be safe to remove the folder from Ubuntu without this affecting your data.

Just to make double-sure, you can also unlink the Ubuntu account/machine from the Dropbox website first (go to Account Settings > Security, where it lists all the devices that have access to Dropbox, unlink the penguin :) ).

---

### Post by newb85 on 2013-10-19
How did you go about uninstalling Dropbox?  Software Center does a simple uninstall, but it takes a purge to remove the config files and content for software thus the difference between
```
sudo apt-get remove dropbox
```
and
```
sudo apt-get purge dropbox
```

---

### Post by Ashley_Perrin on 2013-10-19
> **iloutzu said:**
> Hi Ashley,

If you've uninstalled Dropbox from Ubuntu, it should be safe to remove the folder from Ubuntu without this affecting your data.

Just to make double-sure, you can also unlink the Ubuntu account/machine from the Dropbox website first (go to Account Settings > Security, where it lists all the devices that have access to Dropbox, unlink the penguin :) ).

I unlinked it. I know it seemed like an obvious question but I have only just got Ubuntu today and I didn't want to hate it because it's quite cool. Thanks for your help :)

---

### Post by Ashley_Perrin on 2013-10-19
> **newb85 said:**
> How did you go about uninstalling Dropbox?  Software Center does a simple uninstall, but it takes a purge to remove the config files and content for software thus the difference between
```
sudo apt-get remove dropbox
```
and
```
sudo apt-get purge dropbox
```

Thank you for your help :) I went through the Software Center. I'm a newbie to Ubuntu and I don't know much about it but have heard good things. Should I type that code into the terminal?

---

### Post by ajgreeny on 2013-10-19
> **Ashley_Perrin said:**
> Thank you for your help :) I went through the Software Center. I'm a newbie to Ubuntu and I don't know much about it but have heard good things. Should I type that code into the terminal?
Yes, you type one of those commands in the terminal.  I suggest the **purge** command for a cleaner removal, though that command will still not remove anything that the application had added to your /home, so you will need to do that manually afterwards.

I don't use the software-centre, I always use synaptic package manager, as it is much more flexible and has many more options for dealing with packages that the software-centre, and allows you to purge (remove completely) a package, which I can not find a way to do in software-centre, perhaps mainly because I have not bothered to search for a way to do that.

---

### Post by Ashley_Perrin on 2013-10-19
> **ajgreeny said:**
> Yes, you type one of those commands in the terminal.  I suggest the **purge** command for a cleaner removal, though that command will still not remove anything that the application had added to your /home, so you will need to do that manually afterwards.

I don't use the software-centre, I always use synaptic package manager, as it is much more flexible and has many more options for dealing with packages that the software-centre, and allows you to purge (remove completely) a package, which I can not find a way to do in software-centre, perhaps mainly because I have not bothered to search for a way to do that.

I typed the purge command into the terminal and it said it can't find the dropbox package. Does that mean everything has gone for sure and not linked?

---

### Post by ajgreeny on 2013-10-20
In 12.04 the package is not called dropbox but nautilus-dropbox and that installs the binary dropbox direct from dropbox itself, so we might be giving you false information.  I do not use dropbox so have no real idea how to uninstall it totally, I'm afraid, but as long as you have unlinked your folder in /home you should be safe to remove any files from that folder.

As always, make sure you have backups, just in case.

---

### Post by Ashley_Perrin on 2013-10-20
> **ajgreeny said:**
> In 12.04 the package is not called dropbox but nautilus-dropbox and that installs the binary dropbox direct from dropbox itself, so we might be giving you false information.  I do not use dropbox so have no real idea how to uninstall it totally, I'm afraid, but as long as you have unlinked your folder in /home you should be safe to remove any files from that folder.

As always, make sure you have backups, just in case.

Thanks for this information. I make sure it was unlinked and uninstalled and deleted a floder that I didn't need and that folder hasn't been removed from my dropbox so all is good. I want to say thank you to everyone for your help and support, I'm really greatful that people got back to me so quickly so I could get it sorted. Thanks again

---

### Post by iloutzu on 2013-10-20
You shouldn't worry too much if you've uninstalled Dropbox in the Software Center, Ashley (which is similar to the remove command). What purge does is also remove the configuration settings from the system, except for the hidden .dropbox folder in your home (mine is about 22 MB for a 3.4 GB Dropbox folder with several thousands of files in it). After the uninstall you can delete /.dropbox manually.

As long as you've unlinked the Ubuntu install from the Dropbox website, you should be fine to remove the local files.

---

### Post by Ashley_Perrin on 2013-10-20
> **iloutzu said:**
> You shouldn't worry too much if you've uninstalled Dropbox in the Software Center, Ashley (which is similar to the remove command). What purge does is also remove the configuration settings from the system, except for the hidden .dropbox folder in your home (mine is about 22 MB for a 3.4 GB Dropbox folder with several thousands of files in it). After the uninstall you can delete /.dropbox manually.

As long as you've unlinked the Ubuntu install from the Dropbox website, you should be fine to remove the local files.

I've removed the folder manually and nothing on Dropbox has been removed which is good. I only worried so much because I switched from Windows 7 to Ubuntu yesturday and haven't got used to it yet. When you uninstall dropbox in Windows it takes the folder with it which is why I got so confused and worried,I thought I done something wrong.

---

### Post by newb85 on 2013-10-20
According to the man file for apt-get:
> purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).
Does that not apply to configuration files stored in the /home directory?  I was under the impression that it did...

@Ashley_Perrin: please excuse my sloppiness in that my commands had the wrong package name for nautilus-dropbox.

---

### Post by ajgreeny on 2013-10-20
> **newb85 said:**
> According to the man file for apt-get:

Does that not apply to configuration files stored in the /home directory?  I was under the impression that it did...

@Ashley_Perrin: please excuse my sloppiness in that my commands had the wrong package name for nautilus-dropbox.

No, nothing in your /home is ever touched in any way by apt-get, synaptic, dpkg, software-centre or aptitude.  It would be very silly if files were removed in such package removal, as many people would lose data that was perhaps very important to them.

---

### Post by newb85 on 2013-10-21
After a little more digging, it looks like the purge option only removes config files stored in system directories (such as /etc) but not those in /home directories. (You're right, ajgreeny.  Not that I'm surprised by that...)

Methinks the statement "any configuration files are deleted" in the man page is a bit misleading.  Where would one go about recommending that page be clarified?

---

