---
title: "$HOME/.dmrc file being ignored"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by winkeljames on 2008-09-03
Hey all,
 When I log onto ubuntu I get a window that says:
 User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.
  
 How do I fix this? I've tried going in through root and changing the permissions there to only have access to the files but can't change them. Any suggestions would be greatly appreciated.
Thanks

---

### Post by Sealbhach on 2008-09-03
Hi, I found another thread on the forum where someone had this problem and it got sorted by typing these commands in the terminal:
```

sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
```

Where you substitute "username" with your own username on Ubuntu.

See thread here:

[http://ubuntuforums.org/showthread.php?p=2307584#post2307584](http://ubuntuforums.org/showthread.php?p=2307584#post2307584)


.

---

### Post by Dreamerman on 2008-09-03
> **Sealbhach said:**
> Hi, I found another thread on the forum where someone had this problem and it got sorted by typing these commands in the terminal:
```

sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
```

Where you substitute "username" with your own username on Ubuntu.

See thread here:

[http://ubuntuforums.org/showthread.php?p=2307584#post2307584](http://ubuntuforums.org/showthread.php?p=2307584#post2307584)
.

I had the same problem last week. Used the above to fix. The first commands went ok but last 2 commands did not. Forgot the error code. Thereafter, I find that changed made under sudo seems to reset after reboot. For instance, I changed permissions for raw1394 under sudo but permissions resets itself after reboot. Not sure if it is related.

---

