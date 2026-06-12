---
title: "[SOLVED] VSFTPD -- minor help (just not working)"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by josh6847 on 2008-05-28
I am currently running Ubuntu 7.10 and have vsftpd installed. The root directory takes me to /opt/lampp, although in the conf file local_root=/

So, I changed that to the directory I want (/home), but it still does not place me there when logged in (it takes me to /opt/lampp). Also, I tried just adding a welcome message and that does not show up either when logged in to the FTP (neither through command line or ftp client). When I made these changes vsftpd was stopped and then I proceeded to restart when I was finished making changes.

Can someone help?

Thanks,

Josh

---

### Post by Monicker on 2008-05-28
Do you possibly have multiple vsftpd.conf files?  Are you sure the one you are editing is the one which is actually being used?

What does this show?

```
ps -ef|grep vsftp
```

---

### Post by deadtom on 2008-05-28
How are you logging in? Anonymously or as yourself? The entry to set up the anonymous root is this:

*anon_root=/where/ever*

See if you have this entry as it may still be pointing to /opt/lampp.

If you're logging in as yourself, and I know this is is really basic but I'll mention it to cover all the bases here, are you restarting vsftpd after you make the changes to vsftpd.conf?

---

### Post by josh6847 on 2008-05-28
Shows only one vsftpd process running...

1000  7927  7910   0  16:53  pts/1   00:00:00   grep   vsftpd

Another weird thing is that I can't stop vsftpd by using the following command --> sudo /etc/init.d/vsftpd stop

I can still connect to the FTP even if I run the above command.

It's trippy because I never specified for vsftpd's root to be in /opt/lampp, it just did that...It worked out because I was developing a PHP project at the time which worked perfectly so I didn't have to do any configurations but now I just want to change the root dir for personal use. Should I just try using proftp or something?

Thanks for the help.

Josh

---

### Post by deadtom on 2008-05-28
*$sudo killall vsftpd*

Then try to restart it again from init.d. If it won't let you start it again rename your vsftpd.conf to something else and do:

*$sudo dpkg-reconfigure vsftpd* to reconfigure it from scratch. Or simply remove and install it again.

---

### Post by josh6847 on 2008-05-29
K got it. There was also a file vsftpd.conf~ even though nothing was opened. I just deleted it and then restarted vsftpd.

Thanks guys.

---

