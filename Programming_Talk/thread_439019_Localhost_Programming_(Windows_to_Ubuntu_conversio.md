---
title: "Localhost Programming (Windows to Ubuntu conversion)"
date: 2007-05-10
forum: Programming Talk
---

### Post by mickbw on 2007-05-10
Hi,  

I am a Linux noob but fairly accomplished doing web development in Windows.  I am having an issue setting up my web development environment in a manner I am used to. 

I use Eclipse for my coldfusion development IDE.  In windows I specified the folder which could be used as the default web directory so i could just type [http://localhost](http://localhost) and the default page would display.  My development would be done on the files in that folder.  Only when the pages were tested in the localhost environment would I move them to the remote host for my page.  

I am not allowed to edit the files from the /var/www folder in Eclipse.  I understand that if I logged in as root I would be able to do this, but obviously I don't want to do that.  Is there a way to set the permissions on that /var/www folder to allow the Eclipse IDE to make changes to those files but still keep the access restrictions from outside that IDE.  

Thanks,

Michael
[http://jobsearchlog.com](http://jobsearchlog.com)

---

### Post by bobbocanfly on 2007-05-10
Not sure but from reading that i think you just need to make the folder writable

```
sudo chmod a+w /var/www
```

---

### Post by ohgod on 2007-05-10
I don't think so...You could change the permissions or ownership on your /var/www/ directory, but that'll change it for everything (not just Eclipse).

Is that a problem, though?  If you're not using the same box for your production environment, I don't see a big problem with changing the permissions.

*EDIT:  I agree with bobbocanfly .

---

### Post by mickbw on 2007-05-10
> sudo chmod a+w /var/www

Well that seems pretty easy.  

Now I just need to set up SVN.

Thanks

---

### Post by Mathiasdm on 2007-05-10
I'd like to advise RapidSVN for that purpose ;-) It does its job very well.
On the other hand, I'd love to see TortoiseSVN on Linux. There's something like it for KDE, but not for Gnome :(

---

### Post by mickbw on 2007-05-10
Thanks very much.  I will take a look into RapidSVN.

---

### Post by slavik on 2007-05-10
[http://localhost/~username/](http://localhost/~username/)

make sure that the account 'username' has a public_html directory in his home directory :)

---

### Post by Wim Sturkenboom on 2007-05-11
I usually more-or-less use slavik's approach.

As an alternative, you can add yourself to the group that has the correct permissions on /var/www (on my slackbox that's group nobody); just check the ownerships. But there might be security implications.

---

### Post by mickbw on 2007-05-11
That is a simpler solution.  Please don't hate me, but this was something so easy to do in Windows that I never thought about it in a long time.  

Hey, I will learn.  Thanks for the help.

Michael

---

### Post by pmasiar on 2007-05-11
> **mickbw said:**
> Please don't hate me, but this was something so easy to do in Windows that I never thought about it in a long time.  

Hey, I will learn.  l

Obviously it was simpler - in Windows, you run as superuser all the time. That is exactly what you want to avoid and why you switched to Linux. :-)

BTW with Vista, it will be same on Windows as on Linux: you should not run as superuser, and think about permissions once a while...

---

