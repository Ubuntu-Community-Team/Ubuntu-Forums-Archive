---
title: "Networking"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by 1overzero on 2008-10-13
I am a new Ubuntu user and missing something obvious I'm sure. I want to mount Shares permanently. I have found the commands in a posted page but part of the instructions ask that I create a file and name it .smbcredentials. How do I create this file? I have internet access and was able to access shared folders until I restarted the Ubuntu. The link I am trying to use is 'https://help.ubuntu.com/community/MountWindowsSharesPermanently'

---

### Post by porchrat on 2008-10-13
If you could post the link to the thread that you are referring to that would help us understand what you are trying to do?

Also if you are trying to run a share with a windows machine you are going to need to install samba.

---

### Post by porchrat on 2008-10-14
OK thank you for the private message, however it is much better for you if you reply in this thread as then more than one person can help you, and they may have (and probably do have) other ideas and suggestions.

However let me answer your question simply.  In order to create a file you use the "touch" command.  The guide you are using tells you to place this .smbcredentials file in the home directory of the primary user (I would presume that is you).  So to do that navigate to your home directory and use this command:

```
touch .smbcredentials
```

note that you can also create a directory with the command "mkdir".

Another way to do it (without the console) is to go to "Places" --> "Home Folder" and then when the navigation window opens right click in the navigation window and select "create file" --> "text file".

---

