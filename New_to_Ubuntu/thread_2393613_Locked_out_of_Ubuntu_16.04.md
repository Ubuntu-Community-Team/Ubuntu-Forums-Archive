---
title: "Locked out of Ubuntu 16.04"
date: 2018-06-05
forum: New to Ubuntu
---

### Post by climbah on 2018-06-05
Hi folks, 

I have an installation of Ubuntu 16.04 on a dual boot machine.

Today I went to log in and it wont accept my password.

I tried following this guild, [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I ran
```
mount -o rw,remount
```

then 
```
is /home
```

According to the tutorial the users should be listed and from there you can reset the password. However, no user is listed at all....

I tried creating a new user, giing it a passowrd and restarting, I can not log into this user either.

Any ideas on things to try? See images attached

[IMG]http://www.istpd.com/assets/images/tmp/startup-3.jpg[/IMG]

Then I made the new user
[IMG]http://www.istpd.com/assets/images/tmp/startup-1.jpg[/IMG]

Does anyone have any tips on how to salvage this machine?

Thanks

---

### Post by Impavidus on 2018-06-06
Do you have a separate /home partition? In that case, the users won't be shown when you run "ls /home" in recovery mode, as the /home partition hasn't been mounted. It will just show an empty directory. You could first mount your /home directory, then run "ls /home" to see your username, or try```
grep 1000 /etc/passwd
```which will also show your username, or just type your username from memory.

You created a new user, mike2, but mike2's home directory is hidden when you try to log in, because the /home partition is mounted on top of it. The /home partition gets mounted automatically during normal boot, but not when booting into recovery mode. Because it's hidden, login fails. After you fixed your original login, you should delete user mike2. Use recovery mode to delete mike2's home directory.

---

