---
title: "2 Home folders and Dropbox"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Primus1 on 2012-10-31
Hi I have 12.10 installed. When upgrading from 10.04 I chose to keep my files. I have tried to install Dropbox from the Software Centre but it freezes and does not install properly.  There was a Dropbox folder on the old 'home'  from my old ubuntu and I suppose that is the reason for the conflict. I have now deleted everything in the old 'home' folder (it would no let me delete the old 'home' folder though. 
Is there a way to delete the old 'home' folder?
I tried to install Dropbox again but it still freezes.

---

### Post by MG&amp;TL on 2012-11-01
Having the old home directory around shouldn't affect system applications.

What happens if you copy-paste:

```
sudo apt-get install nautilus-dropbox
```

into a terminal?

---

### Post by Primus1 on 2012-11-01
When I started my computer today a box came up saying "Dropbox is running from an unsupported location"

I just give you this information before I use your terminal suggestion. I have tried installing and installing again with no success.



This is the result from your suggestion:

david@david-MS-7592:~$ sudo apt-get install nautilus-dropbox
[sudo] password for david: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
david@david-MS-7592:~$



.

---

### Post by MG&amp;TL on 2012-11-01
Right...well first we need to fix the *dpkg *error.

Run:

```
sudo dpkg --configure -a 
```


then see what happens. :)

---

### Post by Primus1 on 2012-11-01
Oh, I thought we had it there for a moment. The result your input was it downloaded Dropbox again and installed it. Then the Dropbox notification said it needed to restart Nautilus, I pressed restart but nothing happened and I waited ... so I figured I would restart the computer as that must restart Nautilus. A notification came up as before "Dropbox is coming from an unsupported location" something like that. Here is the code:

.
david@david-MS-7592:~$ sudo dpkg --configure -a
[sudo] password for david: 
Setting up nautilus-dropbox (1.4.0-3) ...

Downloading Dropbox... 100%to share and store your files online. Want to learn mUnpacking Dropbox... 100%ropbox.com/
Please restart all running instances of Nautilus, or you will experience problems. i.e. nautilus --quit
Dropbox installation successfully completed! You can start Dropbox from your applications menu.
david@david-MS-7592:~$ 


.

---

### Post by MG&amp;TL on 2012-11-01
Just quitting and restarting nautilus would have done it...but the more the better.

Okay, I don't really understand the error message (dropbox, be more helpful!). Does dropbox work now, or what?

---

### Post by Primus1 on 2012-11-01
> **MG&TL said:**
> Just quitting and restarting nautilus would have done it...but the more the better.

Okay, I don't really understand the error message (dropbox, be more helpful!). Does dropbox work now, or what?


Yes, it has my dropbox files in the computers dropbox folder and I dragged a file in and I checked on my Tablet and it has synced and put it on there too, all very smooth and no problems. It wanted me to link it to an account, that seemed to be the problem, now it's fine. I will see if it works tomorrow when I start the computer but it looks to be sorted now.

Thanks for staying with me through this, much appreciated :)

---

### Post by MG&amp;TL on 2012-11-01
> **Primus1 said:**
> Yes, it has my dropbox files in the computers dropbox folder and I dragged a file in and I checked on my Tablet and it has synced and put it on there too, all very smooth and no problems. It wanted me to link it to an account, that seemed to be the problem, now it's fine. I will see if it works tomorrow when I start the computer but it looks to be sorted now.

Thanks for staying with me through this, much appreciated :)

Not a problem. Just hope it keeps working. :)

---

