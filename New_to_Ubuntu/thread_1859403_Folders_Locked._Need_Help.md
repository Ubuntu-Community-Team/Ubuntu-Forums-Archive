---
title: "Folders Locked. Need Help"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by ought-6 on 2011-10-13
I installed Ubuntu 11.04 on to a 150 gb external hard drive. I am using this to recover data from other hard drives on different computers. I plug my HD in and tell the computer to boot from my external HD. I set the login so Ubuntu will just load straight to the desktop. However once in the desktop, all of my folders are locked and it says I do not own them. How can I change the settings so that I have access to my files/folders every time I login? I am tired of manually unlocking each file with Nautilus.

Thanks,
G

---

### Post by rburkartjo on 2011-10-13
oug 
Try this:

1. Open up a Terminal and type: sudo nautilus /home/**your username here**/Desktop
2. Right-click the folder with the padlock.
3. Go to the Permissions tab.
4. Check the settings to make sure you (as a normal user) have access to create and delete the files.

---

### Post by varunendra on 2011-10-14
> **rburkartjo said:**
> oug 
Try this:

1. Open up a Terminal and type: sudo nautilus /home/**your username here**/Desktop
2. Right-click the folder with the padlock.
3. Go to the Permissions tab.
4. Check the settings to make sure you (as a normal user) have access to create and delete the files.
A couple of thoughts -
Firstly, for any GUI application (like nautilus), gksu or gksudo should be used instead of sudo. Secondly, if nautilus is opened with root access (due to sudo or gksu), padlocks won't appear since user will have full access to them in that case.

If it is a case of ownership (which seems most probable), I would recommend to simply change the ownership of user's entire home folder and all of its contents. A single step command to do so - 
```
sudo chown -Rc <user-ID> /home/<user-ID>
```

For example, if my home folder is /home/varun, I'll have to use - *sudo chown -Rc varun /home/varun*. The switch -R implements the command recursively on all the subfolders and files, and the -c switch will display the changes made. If the files and directories are already owned by him, the -c switch won't display any lines since no changes would be made.

---

### Post by ought-6 on 2011-10-14
Awesome. Thank you both for the replies. I used the command line sudo chown -Rc and it opened up all of my stuff. Much appreciated. I'm slowly migrating over from windows with no prior linux knowledge so it is a challenge. I look up as much as I can, but sometimes there are no forums or documents for these little things.

---

### Post by varunendra on 2011-10-15
Thanks for the confirmation :) It always feels good to hear one.

For new users who migrate from windows, a dual boot with windows is the recommended path. The underlying formula is - try out different distros and versions and choose the one that suits you most (keep doing this as your experience grows), then use Linux for everything you can do on it. Switch to windows only for those tasks which can't be done on Linux or that you don't yet know how to do on it.

Just about an year ago, it all looked gibberish to me, but now makes much more sense than the ways I was used to earlier when I was a windows-only user. How much you like it and how soon you start liking it mostly depends upon your specific requirements, and the desire to find better and flexible ways to meet them.

---

### Post by Canaryguy on 2011-12-06
Thanks this worked for me. I had some folders in my external hard disk but I could not delete them because it said that I was not the owner but I just opened nautilus from the terminal using sudo and I went then to the hard disk and I could delete them.

---

