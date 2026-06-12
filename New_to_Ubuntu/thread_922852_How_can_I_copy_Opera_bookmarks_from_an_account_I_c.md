---
title: "How can I copy Opera bookmarks from an account I can't log in to?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by MightyFrog on 2008-09-17
I'm having lots of problems that began in a thread here [http://ubuntuforums.org/showthread.php?t=922684]("http://ubuntuforums.org/showthread.php?t=922684"). At this point, I'd rather just do a clean install of Ubuntu. (Well, I'd rather use Windows, but that's not an option my boss has given me for this computer.) Since I'm the only one in the office who a) has worked with Linux a little and b) has the time to do so, there's no one available to help. I'm at a point where I can log in to the admin account in GNOME failsafe mode (did I get that right?). I cannot log in to gnet, the one other user account on the system; it gets as far as the desktop background and stops. The only thing I'd really like to recover are my bookmarks in Opera, but I can't copy them. When I'm logged in as admin and navigate to home/gnet and show hidden files, I can see the .opera directory there, but there's an x over it. If I try to open the directory, I get an error saying I don't have the necessary permissions. I thought the whole point of the admin account was to allow, you know administration of other accounts. What can I do here? Thanks.

---

### Post by KIAaze on 2008-09-18
I never used the admin account.
But theoretically, sudo should allow you to do whatever you want.

Try the following:
```
sudo chmod -R 755 /home/gnet/.opera/
```

It should set the following permissions on the .opera folder and all its contents:
```
rwxr-xr-x
```
Which means:
*read/write/execute for the user gnet
*read/execute for users of the group gnet
*read/execute for all users

---

