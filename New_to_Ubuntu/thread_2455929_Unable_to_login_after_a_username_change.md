---
title: "Unable to login after a username change"
date: 2020-12-30
forum: New to Ubuntu
---

### Post by sunreaver on 2020-12-30
Hi all,

I changed my username as follows:
1. Created 'temporary':
```
sudo adduser temporary
```

2. Added it to sudo group:
```
sudo adduser temporary sudo
```

3.Changed oldUsername to a new:
```
sudo usermod -d newUsername oldUsername
```

4.Changed home folder:
```
sudo usermod -d newHomeDir -m newUsername
```

After I restarted the machine and:
- my newUsername doesn't appear on the login screen
- oldUsername is on the login screen, and it doesn't accept my password
- I can login only to the temporary user
- when I list users with ```
cat /etc/passwd
``` I get:
```
temporary:x:1001:1001:,,,:/home/temporary:/bin/bash
```
```
newUsername:x:1000:1000:oldUsername,,,:/home/newUsername:/bin/bash
```

What should I do to fix this?

Thanks!

---

### Post by yancek on 2020-12-31
Your command to add the user temporary to sudo group doesn't look right.  Take a look at the instructions at the link below.  When you created the new user temporary, you should have been prompted to create a password for that user, were you and did you?

 [https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu](https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu)

---

### Post by sunreaver on 2020-12-31
Thank you. I forgot to mention that, I created the password for 'temporary', and I have no problem with this user. 

My problem is that I cannot login to the user that I was renaming.

I guess the issue is that I have 'oldUsernane' in here ```
[COLOR=#000000][FONT=&amp]newUsername:x:1000:1000:oldUsername,,,:/home/newUsername:/bin/bash[/FONT][/COLOR]
```but I don't know how to get rid of it.

So if my 'oldUsernane' was 'john' and the new name 'david', now this line in ```
[COLOR=#000000][FONT=&quot]cat /etc/passwd[/FONT][/COLOR]
``` looks like this ```
[COLOR=#000000]david:x:1000:1000:john,,,:/home/david:/bin/bash[/COLOR]
```

---

### Post by TheFu on 2020-12-31
check the group membership.

---

### Post by sunreaver on 2020-12-31
There's no group or user with my old name. I logged as root and if I check with cat /etc/passwd, I have 2 users: the renamed one 'david' and 'temporary', but when I check root home directory, I have 'john' and 'temporary'. I think at this point I'll just reinstall Ubuntu.

---

### Post by TheFu on 2021-01-01
> **sunreaver said:**
> There's no group or user with my old name. I logged as root and if I check with cat /etc/passwd, I have 2 users: the renamed one 'david' and 'temporary', but when I check root home directory, I have 'john' and 'temporary'. I think at this point I'll just reinstall Ubuntu.

Why?  I never use usermod.  Just edit the passwd and group files directly, with their shadow files too.  They aren't complex. The fields are clearly spelled out in the manpages for each file. They only need to be consistent. I find changing a userid quick and trivial this way.  Make the edits quickly, so that sudo checks don't prevent changes.

You can always boot off Ubuntu Install / Try Ubuntu, mount the storage/partition with /etc/ and edit the files if too slow. Those files just need to be "consistent."  Editing is much easier than trying to remember commands and options for me.  There is no reason the username's HOME must match the username. It is not required, only helps humans. Computers don't care. They always lookup the answer using getent() or **getent passwd** or **getent group**

BTW, use the 'id' command to see fully the group membership for any userid.

---

### Post by Impavidus on 2021-01-01
But do make sure that the home directory mentioned in /etc/passwd matches the name of the actual directory. You haven't told us yet what that is.

The only old username left in your /etc/passwd is in the comment field. That shouldn't be much of a problem.

---

### Post by Tadaen_Sylvermane on 2021-01-01
Seems like an awful complicated process. Why didn't you just add a new user with proper groups, chown -R and rename the entire /home /"$USER" dir and move on with life? Are you trying to save the uid / gid?

---

