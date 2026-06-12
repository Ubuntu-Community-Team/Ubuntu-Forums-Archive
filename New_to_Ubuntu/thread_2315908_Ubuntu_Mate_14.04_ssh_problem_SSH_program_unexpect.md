---
title: "Ubuntu Mate 14.04 ssh problem: SSH program unexpectedly exited"
date: 2016-03-03
forum: New to Ubuntu
---

### Post by uhuala on 2016-03-03
Hello, this is my first install of ubuntu and I am running into a problem ssh'ing into a particular server. When I do Places --> connect to server and use the shh type, I'm getting the error "SSH program unexpectedly exited". This seems to only be happening on one server, others are working fine.

I can ssh into the server via the terminal, but I would like to have a gui. Could someone help me get to the bottom of this?

---

### Post by TheFu on 2016-03-03
Turn up logging and compare the results between the terminal client and the GUI client. Is the GUI program actually installed?

I'm confused - why would anyone want a GUI for ssh?  It isn't like ~/.ssh/config would be any easier.

I'd check the name resolution - verify that both directions know the names correctly. May need to clean out the known_hosts files.

---

### Post by uhuala on 2016-03-04
How do I turn up logging? I'm not sure how to do what you're asking.

By the way, I've had this exact same problem when trying to access the same server from a machine with scientific linux installed. I'm not sure what to make of this.

---

### Post by TheFu on 2016-03-04
The way to get more logging is different for every program.  The manpage for each program should have instructions.

$ man ssh

```
SSH(1)                    BSD General Commands Manual                   SSH(1)

NAME
     ssh â OpenSSH SSH client (remote login program)
...
     -v      Verbose mode.  Causes ssh to print debugging messages about its
             progress.  This is helpful in debugging connection, authenticaâ
             tion, and configuration problems.  Multiple -v options increase
             the verbosity.  The maximum is 3.
....
```
Something like that will work on the server-side --- that's a little harder to explain and I'm in a hurry today (google debugging ssh-server) ... don't use a GUI tool for ssh - won't have any CLUE how to turn up logging on it, but look for it in the manpage, help, online docs.  You'll probably need to know the real name for the program - not just what the menu displays.

---

### Post by uhuala on 2016-03-04
I don't have control over the server, so I'm not sure I can "debug" it.

I only want the gui for file transfer purposes; I need to parse through hundreds of images and it's a bit easier if I can occasionally click on them to see what they are.

---

### Post by TheFu on 2016-03-05
Unix systems are setup so that end-users can run pretty much anything they want.  You can run the sshd server as a normal user, just not on the default port.

From the sshd manpage:
```
     -D      When this option is specified, sshd will not detach and does not
             become a daemon.  This allows easy monitoring of sshd.

     -d      Debug mode.  The server sends verbose debug output to standard
             error, and does not put itself in the background.  The server
             also will not fork and will only process one connection.  This
             option is only intended for debugging for the server.  Multiple
             -d options increase the debugging level.  Maximum is 3.
```

I'd use -p, -D, -ddd on the server-side to start a new sshd that can be watched when running.  The port chosen has to be unused and over 1024.

---

### Post by steeldriver on 2016-03-05
Perhaps the particular server is configured to allow SSH terminal sessions, but disallow SFTP (which I believe what is going on under the hood when you use nautilus's "Connect to server ..." feature)

---

### Post by uhuala on 2016-03-07
> **steeldriver said:**
> Perhaps the particular server is configured to allow SSH terminal sessions, but disallow SFTP (which I believe what is going on under the hood when you use nautilus's "Connect to server ..." feature)

I have been able to connect using winscp on windows without any problem.

---

### Post by steeldriver on 2016-03-07
Well I seem to be able to reproduce the behavior simply by commenting  out the sftp server in /etc/ssh/sshd_config and restarting the service -  I can still log in to a terminal session via SSH,but attempting to  sftp://localhost from nautilus results in an error (see attachment)

FWIW I am also able to connect via WinSCP still - even if I uncheck its "SCP fallback" option. Not sure what's going on there.

---

