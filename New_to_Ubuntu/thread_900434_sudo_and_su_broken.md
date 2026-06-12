---
title: "sudo and su broken"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by pyromanic123boom on 2008-08-25
I get two errors...

> X:~$ sudo
sudo: must be setuid root

> 
X:~$ su
Password: 
su: Authentication failure

I know my own user password, but not the root. Despite whatever I try with su, no passwords will go. As for sudo being broken, that's because I (without thinking) chowned the /usr/ directory. 

I've followed these other threads:
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)
[http://ubuntuforums.org/showthread.php?t=251358](http://ubuntuforums.org/showthread.php?t=251358)
And other searches on google. So far I've tried to use the live CD with no luck, and the recovery menu. When I add 

> -- single

To the end of my recovery mode kernel string, I go into recovery mode. But when I try to go to a root terminal from there, it asks me for the root password. Since I don't know the user password, and my user password doesn't work, I can't get it. Tried adding 

> -- single init=/bin/bash

To the end of the kernel line, which takes me to a root prompt. When I try to type anything, NOTHING shows up there. So I am forced to manually reset.

I can't get into practically anything in System-->Admin, because it tells me that I don't have access. So while I can still go on, I can't do anything in the terminal...or mount any external drives...or even make basic system changes. I really don't want to reinstall since I can't mount my external drive to transfer data. Any way to possibly override the root password at the recovery menu? Just a little bit desperate for any help here. Thanks

---

### Post by kellemes on 2008-08-25
Don't know how to fix sudo..

"su" by default will ask for the root-password, since there is no root-account setup/needed with Ubuntu you don't have it.
You don't need su.
If you need persistent super-user privileges you can "sudo -i"

Maybe there is an easy fix for sudo I don't know about, but I'd try reinstall and see it as a learning experience, don't experiment with permissions on system folders!

---

### Post by pyromanic123boom on 2008-08-25
Well whatever the reason, my default password doesn't work with su. And, like I said, sudo gives me "sudo: must be setuid root." So sudo -i wouldn't work. 

I am seriously considering reinstall, and yes, it would be heck of a learning experience. But I really would like to avoid the last option at all costs.

---

### Post by pyromanic123boom on 2008-08-25
Argh...to add to the list caused by this, I can't mount any external drives...hd, ipod, flash, etc etc. I get this standard error when I try to mount a drive:

[IMG]http://pyromanic.publichost.de/cannot-mount-volume-error.png[/IMG]

I am assuming this is a problem with HAL but did not have this the other day before I broke sudo. I am in a right state now and can hardly do anything worthwhile. Anyone?

---

### Post by pyromanic123boom on 2008-08-25
Is it possible to reinstall without removing any /home/ user data?

---

### Post by pyromanic123boom on 2008-08-25
I get two errors...


```
X:~$ sudo
sudo: must be setuid root
```


```
X:~$ su
Password:
su: Authentication failure
```

I know my own user password, and I used it with su before. Despite whatever I try with su, no passwords will go. As for sudo being broken, that's because I (without thinking) chowned the /usr/ directory.

I've followed these other threads:
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)
[http://ubuntuforums.org/showthread.php?t=251358](http://ubuntuforums.org/showthread.php?t=251358)
And other searches on google. So far I've tried to use the live CD with no luck, and the recovery menu. When I add

```
-- single
```

To the end of my recovery mode kernel string, I go into recovery mode. But when I try to go to a root terminal from there, it asks me for the root password. Since I don't know the user password, and my user password doesn't work, I can't get it. Tried adding
```

-- single init=/bin/bash
```

To the end of the kernel line, which takes me to a root prompt. When I try to type anything, NOTHING shows up there. So I am forced to manually reset.

I can't get into practically anything in System-->Admin, because it tells me that I don't have access. So while I can still go on, I can't do anything in the terminal...or mount any external drives...or even make basic system changes. I really don't want to reinstall since I can't mount my external drive to transfer data. Any way to possibly override the root password at the recovery menu? Just a little bit desperate for any help here. Thanks

---

### Post by zamadatix on 2008-08-25
uhh for some reason su and my pass doesnt work and su - then i type my pass says authentication failure to so i must be doing something wrong...

---

### Post by sisco311 on 2008-08-25
> **zamadatix said:**
> uhh for some reason su and my pass doesnt work and su - then i type my pass says authentication failure to so i must be doing something wrong...

In Ubuntu the root account is disabled by default.
su is for logging in as root.
To start a root shell you can use *sudo -i *or [I]sudo -s.
[/I][https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wgrant on 2008-08-25
su doesn't want your password - it wants the root password, which probably doesn't exist.

From a live CD or root shell (just add init=/bin/bash to the end of the kernel commandline, no single required):

```

chown root:root /usr/bin/sudo
chmod +s /usr/bin/sudo
```

---

### Post by pyromanic123boom on 2008-08-25
> **fujitsu said:**
> su doesn't want your password - it wants the root password, which probably doesn't exist.

From a live CD or root shell (just add init=/bin/bash to the end of the kernel commandline, no single required):

```

chown root:root /usr/bin/sudo
chmod +s /usr/bin/sudo
```

Ah! So I added the single when I didn't need to. Let me try that and I'll be back in 10 to post how it went. Thanks so far

---

### Post by pyromanic123boom on 2008-08-25
This is exactly what I do.

1. Boot, press ESC to enter menu.
2. 'e' at recovery, 'e' at kernel, and add 

```
init=/bin/bash
```

to the end of the line. Then I hit enter, and return, and press 'b' to boot.

3. so it loads up to a command prompt:

```
root@none:/#
```

Where I CANNOT type anything. Nothing I do makes any difference, so I've got to restart manually. 

Am I doing something wrong, or should I try something else? Live CD?

---

### Post by pyromanic123boom on 2008-08-25
Anyone? I can't mount my external harddrive or ipod or anything...

---

### Post by pyromanic123boom on 2008-08-25
Sudo is completely broken...any help?
I can't mount a damn thing..

---

### Post by t0p on 2008-08-25
Look back at fujitsu's advice, he tells you what to do from a live cd

---

### Post by pyromanic123boom on 2008-08-25
I am on the live cd now. when i open the terminal to type

```

$ sudo chown root:root /usr/bin/sudo

```

It just sort of blinks stupidly and doesn't do anything at all. Not even a readout. Just hung there.

So I try 

```

$ sudo chmod +s /usr/bin/sudo

```

Which is what fajisita said to do. But to no luck. It does exactly what chown did. Getting rather frustrated.

---

### Post by Sinkingships7 on 2008-08-25
If by 'blink stupidly' you mean that it just seemed to do nothing and presented you with another prompt, then it did what it was supposed to. It just changes ownership permissions. You won't see the result until you log back on and try sudo again.

---

### Post by pyromanic123boom on 2008-08-25
No not at all! I would have realized that it had worked had it done that. It just does 

ubuntu@ubuntu:~$ sudo chown root:root /usr/bin/sudo
[]

where the [] is the little black text cursor that just blinks black and white.
and so I closed it, restarted, and tried sudo where it gave me the same "must be setuid root" error.

---

### Post by xeth_delta on 2008-08-25
> **pyromanic123boom said:**
> No not at all! I would have realized that it had worked had it done that. It just does 

ubuntu@ubuntu:~$ sudo chown root:root /usr/bin/sudo
[]

where the [] is the little black text cursor that just blinks black and white.
and so I closed it, restarted, and tried sudo where it gave me the same "must be setuid root" error.

I am afraid that, unless I am missing something, you were simply changing the permissions of the file in the CD environment. To be able to change that on your machine environment, you have to chroot:
```
sudo chroot path_to_your_/_partition /bin/bash
```

Is your user account in the admin group? You can check that, and if needed make the changes in /etc/group from the liveCD. Let us know if you need pointers on how to do that.

---

### Post by pyromanic123boom on 2008-08-25
That's what I was just thinking a little bit ago, trying to chmod to my hd.
But your advice is more clear. Pretty sure there's only one user with the live cd, and they would be admin, I think. And I am admin on my machine. 

I am going to restart to clear things up and then I will try what you suggested in the live cd. Thanks so far

---

### Post by pyromanic123boom on 2008-08-26
Success! This is what I did to fix sudo:

1) go to the live cd terminal
2) chroot partion/here /bin/bash
3) sudo chown root:root /usr/bin/sudo
4) sudo chmod 4755 /usr/bin/sudo

restarted, tested sudo, and it worked. thanks to everyone in this thread who threw some little bits of advice out there. this has saved me a resinstall and a whole mess of my system. 

pyromanic

---

### Post by xeth_delta on 2008-08-26
> **pyromanic123boom said:**
> Success! This is what I did to fix sudo:

1) go to the live cd terminal
2) chroot partion/here /bin/bash
3) sudo chown root:root /usr/bin/sudo
4) sudo chmod 4755 /usr/bin/sudo

restarted, tested sudo, and it worked. thanks to everyone in this thread who threw some little bits of advice out there. this has saved me a resinstall and a whole mess of my system. 

pyromanic

you're most welcome! Don't forget to mark the thread as solved.
One more thing, though. What happened in the first place so that the /usr/bin/sudo had wrong permissions? It might just be a symptom of a bigger hidden problem.

---

### Post by pyromanic123boom on 2008-08-26
i feel dumb tonight...how do you mark it solved? i did look for that earlier.

oh and the reason why it ever got screwed up in the first place was because i got tired of use chown for every folder I couldn't do stuff in...so I did this

$ chown /usr

:oops: :oops: ](*,)

---

### Post by pyromanic123boom on 2008-08-26
unfortunately it looks as though i have another problem..

when i try to go to Users and Groups (because I assume my permissions are wrong since I can't mount my ipod,) it says 

> The configuration could not be loaded.
You are not allowed to access the system configuration.

---

### Post by xeth_delta on 2008-08-26
> **pyromanic123boom said:**
> i feel dumb tonight...how do you mark it solved? i did look for that earlier.

oh and the reason why it ever got screwed up in the first place was because i got tired of use chown for every folder I couldn't do stuff in...so I did this

$ chown /usr

:oops: :oops: ](*,)

Oh, no, no... That is not the way to do it and that might have affected a lot of things in there...

That's what sudo is used for, and that's why the Linux/Ubuntu security model works so well.

Anyway, those are directories to which only root/admin should have access (even if it's the same person, but has to use sudo or a separate root account).

For what other directories have you modified permissions?

---

### Post by xeth_delta on 2008-08-26
> **pyromanic123boom said:**
> unfortunately it looks as though i have another problem..

when i try to go to Users and Groups (because I assume my permissions are wrong since I can't mount my ipod,) it says

Hmm, please see my previous post. You might have affected permissions for a lot of files. not all of them are supposed to have the same types of permissions, or not even user/group... It's not only the root user that has ownership over them, but also some other special users and groups.

---

### Post by pyromanic123boom on 2008-08-27
Well I reinstalled all hal and dbus packages in synaptic, and cleaned up. So now everything works wonderfully and I am off listening to my ipod. Thank you very much for the help!

---

### Post by bodhi.zazen on 2008-08-27
> **pyromanic123boom said:**
> Well I reinstalled all hal and dbus packages in synaptic, and cleaned up. So now everything works wonderfully and I am off listening to my ipod. Thank you very much for the help!

FYI: In the future, you do not need to do this from a live CD. Just boot to recovery mode and select root shell ;)

I do not know how this happened, but you should not change permissions of system files. Learn to use sudo and gksu.

---

### Post by xeth_delta on 2008-08-27
> **bodhi.zazen said:**
> FYI: In the future, you do not need to do this from a live CD. Just boot to recovery mode and select root shell ;)

I do not know how this happened, but you should not change permissions of system files. Learn to use sudo and gksu.

bodhi.zazen, have a look at post #21, it was a mistake the OP did when changing permissions, as far as I can see.

To the OP, be aware, that if you changed permissions like that in system specific directories, you might now be slightly vulnerable. security is one of the reasons for keeping regular accounts off those system files and directories, so that in the unlikely case of an attack, only files in /home/user_name are affected. The reinstallation of those packages did indeed bring functionality back to your system, but only the files in those packages were restored to their initial state.

Anyway, glad you have your system back :)
Remember to mark the thread as solved if the problem is gone.

---

### Post by pyromanic123boom on 2008-08-27
> **bodhi.zazen said:**
> FYI: In the future, you do not need to do this from a live CD. Just boot to recovery mode and select root shell ;)

I do not know how this happened, but you should not change permissions of system files. Learn to use sudo and gksu.

Yeah, well, I am learning. First critical mistake I made.
Thanks though.

---

