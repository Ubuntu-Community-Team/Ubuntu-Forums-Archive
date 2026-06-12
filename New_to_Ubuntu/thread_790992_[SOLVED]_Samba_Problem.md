---
title: "[SOLVED] Samba Problem???"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by sp00ner on 2008-05-11
Just today for some reason I cannot access my NAS or my Windows shared printer. I have not changed anything for quite a while. I have it setup so I get mounted to my NAS device on bootup. So today, I boot my laptop and click on the icon for the NAS device and it says permission denied??? I try manually mounting from the command line and it says 7337: Connection to nas failed SMB connection failed. So To check Samba I try printing to my Windows shared printer and it is not working either. doing a lsmod I do not see Samba or Smb (not sure what the module is actually called) but it does not look like it is running anymore. How could this happen? I havnt installed or tweaked anything in weeks because everything was working so good. I still cant trouble shoot this OS for beans cuz I just dont know that much about it. Any thoughts and/or help would be greatly appreciated. Thanks. :confused:

---

### Post by superprash2003 on 2008-05-11
to ensure samba is running sudo /etc/init.d/samba start

---

### Post by sp00ner on 2008-05-11
I ran that command and got this..

Starting Samba daemons                                                [ OK ]


But I still have the same problem. So i guess it is not a problem with Samba. Anything else I can check?

---

### Post by sp00ner on 2008-05-12
Bump...I'm going to bed. Will check back in the morning.

---

### Post by sp00ner on 2008-05-12
Bump.... I am on the verge of just re-installing completley, but I'll bump this a couple more times today before I resort to that :(

If I left out any crucial info let me know what you need and I'll do my best to post it, but I am at work now and for the next 8 hours.

---

### Post by sp00ner on 2008-05-14
Stangely enough, this problem went away as mysteriously as it appeared. Oh well, marking thread as solved.

---

