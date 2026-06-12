---
title: "Suitable ssh client with session manager, port forwarding, ssh tunneling for lubuntu"
date: 2020-10-30
forum: New to Ubuntu
---

### Post by wugubee on 2020-10-30
Im surprised after moving to lubuntu 20.10, after researching there arent much ssh client full featured (maybe like securecrt for windows), moreover if qt based,

I need ssh client with session manager, port forwarding and ssh tunneling capability, 

What options do I have?
I was expecting to have it qt based, lightweight,

---

### Post by TheFu on 2020-10-30
Open the terminal you like. If you want Qt-based, then use a Qt-based terminal.
Type **ssh** with the options you want.
Use the ~/.ssh/config file to setup specific options as desired for specific client connections. Different ports, userids, keys, options. Infinite aliases for each connection are possible. No nd to remember anything but the alias, plus command completion knows about that file.  ssh,scp,sftp,rsync,sshfs,rdiff-backup,vim,x2go, ... anything based on ssh for the connection "just works".  But there isn't a GUI. sorry.

This is "the Unix way."

Power users will leverage **tmux** or **screen**, especially if there are dropped connections.

I find it frustrating that Windows doesn't all honor the ~/.ssh/config file for all ssh-based tools. Drives me crazy.  On Unix, that 1 file works for 50+ ssh-based tools.

---

### Post by wugubee on 2020-10-30
So ~/.ssh.config will satisfy most of the ssh needs? I just need to learn it more, right? But i heard the file is not able to store password?

And for reconnect dropped connection use tmux or screen, right?

---

### Post by TheFu on 2020-10-30
ssh-keys or ssh-certs should be used, never passwords.  Look for **ssh-keygen** and **ssh-copy-id** in these forums.

>  And for reconnect dropped connection use tmux or screen, right? 
Not exactly. They keep sessions even if your connection drops. Reconnect from anywhere and be back were you were, programs still running.

---

### Post by ActionParsnip on 2020-10-30
ssh itself will do that for you. If you want convenience then I suggest some BASH scripts that you can just call. Here is one I use to SSH tunnel to an SSH server:
```

ssh -L 5901:127.0.0.1:5901 user@serverip

```
I can now VNC to localhost:5901 and be on the remote server, securely

---

### Post by ActionParsnip on 2020-10-30
vinagre can also manage lots of different protocols and connect to them

---

### Post by wugubee on 2020-10-30
I probably gonna try asbru connection manager as a fork of pac manager....

---

### Post by TheFu on 2020-10-31
~/.ssh.config is incorrect.  Should be ~/.ssh/config

---

