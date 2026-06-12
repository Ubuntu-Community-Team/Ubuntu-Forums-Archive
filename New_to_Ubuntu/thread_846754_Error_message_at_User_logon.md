---
title: "Error message at User logon"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Thunderchild01 on 2008-07-01
Help please.

When I log on using the second of two user log ons, I get the following error message:

*User’s $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User’s $HOME Directory must be owned by user and not writable by other users. * 

Can someone please tell me what I have done wrong and how to fix?

Cheers:confused::confused:

---

### Post by dominiquec on 2008-07-01
Check the ownership of the directory.  It should belong to the same UID as your login name.  You can do that by typing "ls -ld".

---

### Post by django0909 on 2008-07-01
Looks to me like both users are trying to use the same home directory. You can alter this with the 'usermod' command. If you run 'man useradd' in a terminal it should give you info on how to do use the 'usermod' command. Sorry I can't give any more help right now, I'm not on my Ubuntu desktop.

Hope that helps!

---

### Post by Thunderchild01 on 2008-07-02
> **dominiquec said:**
> Check the ownership of the directory.  It should belong to the same UID as your login name.  You can do that by typing "ls -ld".

Thanks for the quick replies and suggestions guys.

When I type in this command I get the following value:

[I]drwxr-xr-x 36 newuser newuser 4096 2008-07-02 19:58 .
newuser@Thunderchild01-ubuntu:~$[/I]

"newuser" and "Thunderchild01" being the new user id that is returning the error at logon and "Thunderchild01" being the administrators's logon or first user created when I installed Hardy.

Is this what I am supposed to be seeing?

I am a newbie really nervous about invoking any of the switches under usermod. If I want to fix my problem I guess I am going to have to take the Heron by the horns - so to speak but am not sure which switch I should be using.

---

### Post by drs305 on 2008-07-02
Log on as the second user. Then run the following commands.If you can't sudo, you will have to boot from grub to the recovery mode to a command line to run them:

This will change permissions and then reboot. Substitute your second user's username (log-on name) if it is not "*newuser*". Only files owned by the second user will be changed, including that user's home and that user's /home/.dmrc file:
```

sudo chmod 644 /home/*newuser*/.dmrc
sudo chown *newuser*: /home/*newuser*/.dmrc
sudo chmod 755 /home/*newuser*
sudo chown *newuser*: /home/*newuser*
sudo shutdown -r now

```

---

### Post by Thunderchild01 on 2008-07-02
Thank you drs305!! 

That fixed it.

One very happy newbie

---

