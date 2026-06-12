---
title: "Updates on shutdown"
date: 2010-04-07
forum: Programming Talk
---

### Post by shark1997 on 2010-04-07
How would I change the shutdown script to allow for automatic updates on shutdown? Would i use bash?

Thanks in advance

--------------------
[SIZE="7"][FONT="Lucida Console"][COLOR="Cyan"]Ubuntu is awesome[/COLOR][/FONT][/SIZE]

---

### Post by tookyourtime on 2010-04-07
I think from this post ([http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)) you can run a bash script on shutdown as described.

Your script would look something like this:
```

echo yourpassword | sudo -S apt-get -y update
echo yourpassword | sudo -S apt-get -y dist-upgrade

```

Someone else will have to help with using sudo in a script without having the password in the file.

---

### Post by jflaker on 2010-04-07
```

echo yourpassword | sudo -S apt-get -y update&&echo yourpassword | sudo -S apt-get -y dist-upgrade
```

make it a one liner

---

