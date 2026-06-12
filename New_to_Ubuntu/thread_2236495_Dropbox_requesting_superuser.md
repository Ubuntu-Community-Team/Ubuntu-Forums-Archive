---
title: "Dropbox requesting superuser"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by Primus1 on 2014-07-27
Hi, booted my computer today (Ubuntu 14.04 LTS)  and a box came up saying Dropbox was asking to be superuser. This has not happened before so I'm wondering if it's ok. I did not click 'Authenticate' instead I clicked 'Cancel'. The box closed and the computer seems to be running ok. I have attached a screen capture of the pop up box. If it happens again will it be ok to allow Dropbox next time? Wondering if it's a virus or something like that. Thanks.

---

### Post by kc1di on 2014-07-27
how was dropbox installed?

Try reinstalling it with the following terminal commands
```
sudo apt-get purge dropbox
sudo apt-get install nautilus-dropbox
```

alternatively you can open a filemanager as root and go to /usr/share/applications/dropbox and make sure the luncher command is ```
dropbox start -i
```

---

### Post by Primus1 on 2014-07-27
Thanks for your reply,

can't see any filemanager, opened 'search' and got no results for 'filemanager'

put this in the Terminal:

/usr/share/applications/dropbox

the result was:

bash: /usr/share/applications/dropbox: No such file or directory

must be doing something wrong.


Looking in ubuntu software manager seems I installed nautilus dropbox extension from there and it downloaded the proprietary dropbox binary.

Would it have been dangerous for me to have allowed dropbox the superuser it requested?

---

### Post by kc1di on 2014-07-27
file manager is Nuatilus in Ubuntu It where you navigate to your folders at. 

I believe you have to enter your root password to get dropbox to download and install after that you will not have to do that again. 
Cheers

---

### Post by Primus1 on 2014-07-29
Thanks kc1di

---

### Post by buzzingrobot on 2014-07-29
A quick Google query will uncover a number of posts, and potential solutions, to this issue.

Seems to be rather random, involving the Dropbox files not being installed in the user's home folder.  Might be worth just removing and reinstalling it.

---

### Post by vasa1 on 2014-07-29
I don't use Nautilus and so installed Dropbox following the instructions here: [https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

Everything is in my home folder.

---

### Post by buzzingrobot on 2014-07-29
The thumbnail shows /usr/bin/dropbox is requesting authorization.  Does it exist?

---

### Post by Primus1 on 2014-07-29
> **buzzingrobot said:**
> The thumbnail shows /usr/bin/dropbox is requesting authorization.  Does it exist?

Hi, I've been looking around this forum and it seems this issue has happened to others (sorry I didn't find this before i posted). There are some methods to sort it but they are too technical for me to understand. I may have to find an alternative to dropbox.

To answer your question does dropbox exist? Do you mean this in user/bin - see attached image:

---

### Post by vasa1 on 2014-07-29
> **Primus1 said:**
> ...
To answer your question does dropbox exist? Do you mean this in user/bin - see attached image:
Another way to convey that information could be to run ```
ls -al | grep dropbox
``` or ```
ls -alR | grep dropbox
```from the relevant folder and to post the output here between **code** tags.

---

### Post by buzzingrobot on 2014-07-29
I've installed Dropbox from dropbox.com and /usr/bin/dropbox does not exist.  The fact that it does exist in your install lends credence to the notion that this problem is caused by an irregular and occasional fault with the Dropbox installer, and that means it might, maybe, be corrected if you remove the package and then reinstall it.

---

### Post by Primus1 on 2014-07-29
I will try thanks. I have to finish now, will be back tomorrow. :)

---

