---
title: "how to consolidate files from multiple laptops to one"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by jaredhaddock on 2012-10-05
ok , i have three laptops all with ubuntu full install .i want to move the files in my home  folders from the two i wish to wipe reinstall and sell to the one i wish to keep.i have about two hundred gb, of media between the two i wish to move to new laptop wish fresh install . what is the easiest way to do this ,is there a wire i can connect between the two and mount one drive from the other and simply copy,do i have to archive and email everything to myself? i was cosidering using cloud and dropbox but that would take forever ,besides i dont wanna sync all three .please tell me there is a way to do this without spending money on external hard drive

---

### Post by Wim Sturkenboom on 2012-10-05
My solution: external HD
Reason: it does not sound like you have backups (but I might be wrong)

Alternative, but I don't have experience with it so I might be wrong, is an ethernet cable and the program *rsync*.

---

### Post by mathfreak123 on 2012-10-05
Please note: I might have written a lot, but I have tried my best to keep everything short. If you have any questions, please feel free to ask away! Also, it's a good idea to wait for someone else to come and confirm what I say and perhaps offer a better solution. :D

If all three of your laptops are under your home network, you can [look into vsftpd.]("http://ubuntuforums.org/showthread.php?t=218630") It's what I use when I have to move files back and forth, and it's safe enough to use as long as you're transferring files in your own home network.

I would say the most important instructions go up to this line:

> Vsftpd will now always start automatically when your computer starts.

You only have to install and configure vsftpd for the computer you'll be sending all the files to.

You also have to open up a port in the firewall for vsftpd. You can do this easily by installing Firestarter:
```
sudo apt-get install firestarter

```

Once firestarter is installed, go ahead and click System -> Administration -> Firestarter. If it's your first time, you can follow a short, quick dialog box. Click on the "Policy" tab in Firestarter afterwards. Choose "Inbound traffic policy" from the dropdown menu next to "Editing." Right-click the white area underneath "Allow service" line, and add a new rule. Choose "FTP" under the "Name" dropdown. You can add in additional options if you want more security (such as which computers are allowed to use this port, etc. etc.). Then click "Add." You can then apply the policy by clicking the green check at the top of the window, and you're set.

In the HOWTO I linked to, scroll down to "Connect from Ubuntu/Debian (or any Gnome desktop)" in the first post and follow the instructions there to connect your two computers to the one that will be receiving the files. After that, you can just drag and drop!

---

