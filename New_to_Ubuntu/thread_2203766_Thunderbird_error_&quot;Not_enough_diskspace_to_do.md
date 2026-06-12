---
title: "Thunderbird error &quot;Not enough diskspace to download new message&quot;"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Naushad_Khan on 2014-02-05
Hello Everyone,

I have Ubuntu 12.04 OS with Thunderbird installed, now i am getting msg "Not enough diskpace to download new messages" What could be the problem.

Regards,
Naushad Khan

---

### Post by bc.haynes on 2014-02-05
Please post the result of :
```
df -h
```

---

### Post by Impavidus on 2014-02-05
The problem could be that you have run out of disk space. Try some of these suggestions: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Naushad_Khan on 2015-01-26
naushad@Naushad-Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        29G  8.8G   18G  33% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            891M  4.0K  891M   1% /dev
tmpfs           181M  1.2M  179M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            901M  748K  901M   1% /run/shm
none            100M   68K  100M   1% /run/user

---

### Post by deadflowr on 2015-01-26
Hmm, perhaps try clearing the cache.
Open Thunderbird go to Edit >> Preferences.
go to The Advanced tab.
go to the DiskSpace section.
click on the Clear Now button.

See if that helps any.

---

### Post by nerdtron on 2015-01-26
Perhaps your Mailbox itself is full? Check the email server if your account already exceeded limits?

---

### Post by Impavidus on 2015-01-26
Wait a moment, almost a year has passed since the original post and you are still stuck with the same problem, and yet didn't come back earlier to reply? A full disk error makes the computer practically unusable.

Let's also have a look at the output from```
df -i
```

---

