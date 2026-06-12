---
title: "Make user settings permanent (delete settings on logoff)"
date: 2010-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lhabjane on 2010-12-06
If you want to create a user that resets settings of logoff (gnome settings, firefox passwords, files on desktop) - you just need to add one script to GDM directory.

1. Create new user (not administrator!), set its rights, name it 'public' for example **(dont forget to also change username in scripts below!)** and set it to "autologin"

2. Login to this user - change it's settings as desired

3. Login back to the administrator rights user
and run as admin (with sudo):
```

cd /home/
tar -pcvf /home/public.tar.gz public
```

this file contains user settings that will be restored everytime when user "public" logins

then, create login script like this:

```
gedit /etc/gdm/PostLogin/Default
```

paste this:
```
#!/bin/sh

#Clean login for user 'public'
if [ "$USER" = "public" ]
then
	rm -rf /home/public

	tar -pxvf /home/public.tar.gz -C /home/

	echo "$USER `date` logged on CLEAN" >> /var/log/cleanlogin.log
fi
```

save file, and set its rights:

```
chmod +x /etc/gdm/PostLogin/Default
```

And that's it!
Tested on Ubuntu 10.10

---

