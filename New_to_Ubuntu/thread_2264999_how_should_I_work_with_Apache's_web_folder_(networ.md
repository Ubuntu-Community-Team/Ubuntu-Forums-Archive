---
title: "how should I work with Apache's web folder (network sharing permissions)?"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by stupidquestion on 2015-02-11
I need to put my web files under /var/www/ which is the web root. I'd like to do my editing in Windows and save them under the web folder. So, I tried sharing /var/www/ via the GUI, but it tells me 'could not change the permissions of folder'. If I change the permissions of www to 777, and tried sharing again, I get error that sharing folder we don't own is restricted, 'ask the administrator to add the line "usershare owner only=false" to the [global] section of the smb.conf to allow this'. 

Before I go ahead with this, is this a safe approach, or is there a better way? The site is not live and I'm just working with it. Thanks.

---

### Post by nerdtron on 2015-02-12
1. You can't change ownership/permissions of folders (like /var/www) if you are not the owner of those files. Simply put, you need to be root to change the file owned by root.

2. Changing the files to permission 777 is bad idea. A longer explanation can be available but in short, 777 permissions is not advisable anywhere.

To circumvent on this problem, (I do the lazy way). Upload the files from window  to your home folder in Ubuntu. Then log in to the Ubuntu Server and move the files yourself to the /var/www folder.
like this:
```
 sudo mv /home/stupidquestion/webpage_folder /var/www/html/ 
```

---

### Post by stupidquestion on 2015-02-13
OK I tried sharing my home folder, but I'm getting "access denied" when I enter my correct Ubuntu credentials in Windows. I reported that in a separate topic:
[http://ubuntuforums.org/showthread.php?t=2265168&p=13227439](http://ubuntuforums.org/showthread.php?t=2265168&p=13227439)

---

### Post by nerdtron on 2015-02-13
> **stupidquestion said:**
> OK I tried sharing my home folder, but I'm getting "access denied" when I enter my correct Ubuntu credentials in Windows. I reported that in a separate topic:
[http://ubuntuforums.org/showthread.php?t=2265168&p=13227439](http://ubuntuforums.org/showthread.php?t=2265168&p=13227439)

Honestly i haven't tried sharing a folder from Ubuntu to windows. I just installed ssh server on Ubuntu
```
sudo apt-get install openssh-server
```

Then you use Filezilla to upload files to your home folder.

---

