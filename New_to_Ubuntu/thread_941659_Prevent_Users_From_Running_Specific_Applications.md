---
title: "Prevent Users From Running Specific Applications"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by EarloftheWest on 2008-10-08
I want to give other users in my home access to my laptop running Ubuntu.
I don't want them surfing the web however. It's ok for them to run Rhythmbox to play media streams however.
How do I prevent them running Firefox when they are logged in under their user name?
Thanks in advance.

---

### Post by Titan8990 on 2008-10-08
You could try changing the ownership of firefox to yourself and then set file permissions on it so that you are the only user that can execute it.

---

### Post by sdennie on 2008-10-08
You should be able to edit the panel to only list the applications you want them to have access to with their user.  I recommend dragging the applications you want them to have access to directly onto the panel and then completely remove the Application/Places/System menu.  Then, hit Alt-F2 and type gconf-editor.  Navigate to /apps/panel/global and check locked_down and disable the Alt-F2 run key.  Also go to /desktop/gnome/lockdown and check the relevant options to lock down.  That should make that user extremely limited in what they are able to run.

---

### Post by jerome1232 on 2008-10-08
> **Titan8990 said:**
> You could try changing the ownership of firefox to yourself and then set file permissions on it so that you are the only user that can execute it.

I would take that further and do this.

On my system the executable for firefox is actually located at /usr/lib/firefox-3.0.3/firefox.sh

You could create a new group called... runprogram (i'm just using that as an example change it to whatever) add users you want to be able to run firefox to that group then remove execute permissions for everyone but people in that group. You of course have to logout then back in for new groups to take effect.

```
sudo -i
groupadd runprogram
adduser user runprogram
chown root:runprogram /usr/lib/firefox-3.0.3/firefox.sh
chmod o-x /usr/lib/firefox-3.0.3/firefox.sh
exit
```

---

