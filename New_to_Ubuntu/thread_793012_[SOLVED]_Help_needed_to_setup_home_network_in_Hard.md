---
title: "[SOLVED] Help needed to setup home network in Hardy"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by naggis on 2008-05-13
My desktop runs only xp and my laptop runs dual boot xp and Hardy. Both pcs connect to the internet without any problem. The 2 xp systems can see and share folders. Is there a tutorial to help setting up a network or file sharing in Hardy to allow the folders on the desktop to be seen? I am new to ubuntu and enjoying the non Windows environment and finding out how things work here. But I do need a bit of help if anyone can offer it.
Thanks in anticipation.

---

### Post by bluefrog on 2008-05-13
in ubuntu open your file explorer (nautilus), right click on a folder and select sharing option.

---

### Post by plucky on 2008-05-13
> Is there a tutorial to help setting up a network or file sharing in Hardy to allow the folders on the desktop to be seen?



See [this link](https://help.ubuntu.com/community/SettingUpSamba) for a little bit more on sharing.

Good Luck

---

### Post by naggis on 2008-05-13
I tried to allow a file to be shared as suggested but the dialogue gave the following error message 
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
I am logged in as the administrator as far as I know so what could be the problem do you think?

---

### Post by bluefrog on 2008-05-13
you must add your user to the sambashare group

---

### Post by tmcelveen on 2008-05-13
I had the same problem...

Go to System->Administration->Users and Groups->Select Manage Groups
Scroll down to sambashare, click properties and add yourself as a group member

Then log off and log back on. Should work fine!

---

### Post by naggis on 2008-05-13
The problem with trying to create a share was solved by rebooting. This sorted out the whole problem and I can now see and access all the files in the shared xp folder on the desktop, from my laptop.
So thanks for the help folks

---

### Post by mapes12 on 2008-05-13
Hi 

Please could you mark your success by marking the thread as SOLVED.

This will help others find solutions to the same problem

You will find the option under "Thread Tools" at the top of your thread. As the thread owner only you can do this.

Many thanks.

Mark :)

---

### Post by c.k.chappell on 2008-05-13
If I am having similar issues but cannot resolve, do I add a new post to a "solved" thread or start a new one?

---

