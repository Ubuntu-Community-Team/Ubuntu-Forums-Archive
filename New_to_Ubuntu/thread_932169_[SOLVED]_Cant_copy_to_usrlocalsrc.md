---
title: "[SOLVED] Cant copy to usr/local/src"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by bestseclub on 2008-09-28
Okay,im kinda new to Linux.
I just read a tut on how to compile tar.gz.Thats not the problem.The problem is i cant copy/move anything to the usr/local/src folder.I tried to change the folder properties,but it says im not "the owner" so im not allowed to change the properties.
Thats all kinda weird.Im the owner of the PC.So what should i do?Should i change my login settings or something?
PS.Im using Gutsy.
PPS.Thanks.

---

### Post by christophski on 2008-09-28
You need to run you filemanager as root user. If you are running GNOME then you should press Alt+F2 and type:
gksu nautilus

It will ask you for your password and then you will be able to paste to any directory in that window.

---

### Post by ad_267 on 2008-09-28
Have a read of this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Press Alt+F2 and run "gksu nautilus" and enter your password. This will open a file browser as the root user.

Also why are you copying something to /usr/local/src? You shouldn't need to do that. And hopefully you know that most applications you don't need to compile, you can install them from the package managers. See [installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by Jim! on 2008-09-28
Do you mean you dont have permission to copy and paste certain files? If that's the case you might be able to just right click on the file> properties> permissions and then change folder access. Just a suggestion:)

---

### Post by bestseclub on 2008-09-28
Woah!I think i just posted this like few minutes ago!Yowza.
Anyway,thanks guys.Ill type those commands.Im almost shure it will work. :)

---

### Post by shifty_powers on 2008-09-28
any particular reason your are using gutsy? nevermind....

linux works on a security model that users owners aqnd permissions for files and accounts etc... so your account has a home folder. you are the "owner" of that folder and have the permissions to open it, read it, write to it, delete it etc...

now, the root folder is different. (the root folder is the stuff outside of your accounts home folder essentially). for security, you do not autmoatically have the permissions necessary to alter stuff in the root file structure. (this makes it a lot harder to write viruses and malware for linux btw).

if you want to do things in the root folders, ubuntu has a concept called the superuser, otherwise known as sudo. this gives you temporary permissions for root to do what you want. be careful with it, as it is very powerful :D

to use it, there are a couple of ways. if you are doing something on the command line you can use sudo in front, so that

```
apt-get update
```

becomes

```
sudo apt-get update
```

it will then ask you for your password, and then carry out the command.

you can also do this:

```
sudo nautilus
```

which will open the file browser with full root permissions. just be careful what you do with it, and don't delete things fi you're not sure what they do :D

hope that helps and have a look at my sig, there is a great guide, psychocats, to ubuntu that will be a big help, trust me :D

---

### Post by jemate18 on 2008-09-28
if you want it in the terminal then
```
sudo cp fileToCopy /usr/src/fileToCopy
```

then type your password and hit enter:

---

### Post by bestseclub on 2008-09-28
Hey,thanks.Guess Linux doesnt have too many viruses.

---

### Post by shifty_powers on 2008-09-28
nope. that is not to say that a virus for linux is impossible, or that none exist, just they are veyr, very, very rare.

there is anti-virus for linux, but tbh, i only ever use it to prevent passing a virus onto another windows user, as never come across anything that has affected me :D

---

### Post by bestseclub on 2008-09-28
Cool...

---

### Post by shifty_powers on 2008-09-28
heh, yep, linux has it's advantages :D

---

### Post by bestseclub on 2008-09-28
More stable,faster,less viruses.What more can you wish for?-to run Windows applications and games.Thats all i think that makes people stick with Windows.
Okay this is going off topic.I just tried the Alt+F2 method and it worked.Guess this problem is solved.

---

### Post by shifty_powers on 2008-09-28
cool, go to the top, go to thread tools, and mark the thread as solved :D

---

