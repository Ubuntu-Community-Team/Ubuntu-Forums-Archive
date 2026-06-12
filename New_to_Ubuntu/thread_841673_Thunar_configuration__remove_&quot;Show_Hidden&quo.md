---
title: "Thunar configuration | remove &quot;Show Hidden&quot;"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by EXCiD3 on 2008-06-26
So i'm locking down some desktops for student use at a school and I was wondering if there is any way for me to remove/disable this option for certain accounts? ive looked through the config files in the /home folder and found nothing. Anyone know of a way to do this or some other work around?

---

### Post by Hospadar on 2008-06-26
you shouldn't really worry too much about showing/hiding hidden files.  The only hidden files a non-admin account would have access to are just configuration files that, if severly tampered with to the point of causing disfunction would either result in:
a) the program going back to default settings due to its inability to read its config file
or
b) you might have to end up just wiping their home directory of hidden files and let the programs that need them generate a new set.  I don't know of any programs that won't operate just fine without any config files.

That said, it might be wise on your part to keep a stock set of files that would normally get put into a new user account handy so you can quickly restore an account to the a priori functionality if someone botches something.

I don't know of any way to disable the option to see configuration files in any file browser, and even if you did manage to do it, students would still be able to read and write to those files either through a terminal or text editor or any other program really.  You could disable read access to them, but that would only serve the purpose of making a lot of apps non-functional as they attempt to read and write their configurations.

The only thing I can think of is maybe writing a script and making a cron job to go back into everybody's user account every night or something and setting their thunar preferences to hide hidden files.  Obviously they'd be able to turn it back on, but it might help them steer away from screwing stuff up.  I'm of the opinion however that if they want to look at all that stuff, good for them, they might learn some more about the machine they use.

Really the only thing you need to worry about is that they don't have sudo privileges (i.e. they arn't in the "admin" group)

If you had some files that you didn't want them to change (let's say a web browser config that activates parental controls to block out teh pronz, you could make that file read only, which would maybe not allow them to save some settings, but with some testing, you could probably ensure everything worked out fine)

---

### Post by EXCiD3 on 2008-06-26
Thanks for the idea about the cron job, that will work fine. My thinking was, we dont want the kids playing with configuring their login, instead they should actually be "working" ;) I've already got several config files that are added to the new accounts when they are created because they are stored in a separate directory instead of /home like the local users since im using NIS and NFS. None of the accounts except the administrator will be in the admin group anyways so not to worry about that. I've also set kiosk mode in XFCE...i *think*... i created the file like the wiki page said but im not sure how to test it and see if its working correctly ([http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-kiosk-mode](http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-kiosk-mode)) I set all of the options to NONE so hopefully that wont be a problem. I'm also creating separate menu.xml files for the kids to use because they dont need access to the settigns applications.

For filtering we are just going to use Squid on the server we have NIS and NFS running on. That should be good enough unless someone has a better recommendation. Thanks for your help!

---

