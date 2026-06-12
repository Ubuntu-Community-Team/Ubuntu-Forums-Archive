---
title: "Deleted desktop folder"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by mkremer on 2008-11-17
Guys, I'm kinda new to Ubuntu and I have done something not so smart.
Somehow I deleted the desktop folder, now it takes stuff from /home/username/ and puts in the desktop. It's funny because on navigating on the folders I have the Desktop one, but it leads to /home/username/. How can I re-create the desktop folder?

One more detail, I turned the starting sound off, but it still plays on I log in, is this a bug from 8.10?

thanx in advance.

---

### Post by skyel on 2008-11-17
I guess 
mkdir /home/user/Desktop 
ought to do it....or you can always try the adduser/useradd command for more options on how to do it check the man pages

---

### Post by mkremer on 2008-11-17
the mkdir didn't seem to work out.
I don't know what the adduser/useradd command is, but I will check it.
thanks.

---

### Post by mkremer on 2008-11-17
I didn't really succeded with the adduser/useradd command thing, can someone help me out with it?

---

### Post by nothingspecial on 2008-11-17
I just created a new user, logged in, made some directories in the desktop then deleted it. I logged out and in again and made a new directory ~/Desktop then did mkdir a1 a2 a3 and they appeared on the desktop. This should solve your problem.

When skyel posted mkdir /home/usr/Desktop did you type his instructions exactly. When he says "user" he means your user name, what ever it is. So if it`s bob type mkdir /home/bob/Desktop.

---

### Post by mkremer on 2008-11-17
I did it, but  when I go to /home/user/desktop it takes me to /home/user.
and on the file browser on "places" I see the desktop item, but it takes me to /home/user/ which is not listed under "Places"

very strange

---

### Post by mkremer on 2008-11-17
And making a new directory on ~/Desktop simply created a folder on /home/user/ called desktop, and this folder was added to my desktop (with all the other items from /home/user)

---

### Post by nothingspecial on 2008-11-17
Type ```
cd
```

Then type ```
mkdir ~/Desktop
```

I might be wrong but it seems like you`ve got users within users within directories within users at the moment.

---

### Post by mkremer on 2008-11-17
I've found on the forum something that worked to somebody else,
nano ~/.config/user-dirs.dirs

and then

change XDG_DESKTOP_DIR="$HOME/" 
to XDG_DESKTOP_DIR="$HOME/Desktop" 

the point now is that I don't know how to save it! I've edited it but I don't know how to save it, I'm sorry, it seems very stupid...

thanx in advance.

---

### Post by mkremer on 2008-11-17
Changing nano for gedit did the trick.


Now that my desktop cleaness is saved any ideas about the sound issue?

---

### Post by nothingspecial on 2008-11-17
I hope it works. In nano you save with Ctrl + O.
I am not sure about those instructions. They may solve your problem but as my sig says, I`m no expert. I have to sleep now. Good luck.

---

### Post by mkremer on 2008-11-17
Thanx man, the desktop issue is gone now.
I just gotta check the sound thing out.

---

