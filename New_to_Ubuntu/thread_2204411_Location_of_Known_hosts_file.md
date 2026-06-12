---
title: "Location of Known_hosts file?"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by Mazdat on 2014-02-08
Hi,

Running Ubuntu 13.10. I am getting the message "host verification key failed" when trying to SSH into a raspberry pi on my network. I know I need to either edit or delete the known_hosts file but for the life of me I cannot find that file using nautilus. I know that people will say "oh, it's at ~/.ssh/known_hosts" but I cannot locate a .ssh folder anywhere nor will a search on nautilus reveal any file called known_hosts or any directory called .ssh. The frustrating thing is that I've done this before but heck, after searching through dozens of directories manually I am at my wits end. Someone can surely help this newbie...Thanks.

---

### Post by Iowan on 2014-02-08
I presume you've tried (from a terminal):
```
ls ~/.ssh
```
SSH works to access other machines?

---

### Post by Mazdat on 2014-02-08
Thanks. Just put that into the terminal and it returns "known_hosts". What does that mean? That the known hosts file is empty? Is there a command that will delete the known hosts file from the terminal? I recall deleting that file in the past and managed to SSH fine after that. Just wish I'd made a note of where the file is hiding :mad:

ETA: just found a folder with various SSH files (binary and text) under etc/ssh but no known_hosts file in it.

---

### Post by Iowan on 2014-02-08
That command just lists the contents of the ~/.ssh directory. Had it not existed, the command would have complained:
```
ls: cannot access ~/.ssh: No such file or directory
```
To verify what's in the file, try:
```
cat ~/.ssh/known_hosts
```
If you REALLY want to delete it:
```
rm ~/.ssh/known_hosts
```
To make a backup version instead:
```
mv ~/.ssh/known_hosts ~/.ssh/known_hosts.bak
```

---

### Post by Mazdat on 2014-02-08
You, sir/madam, are a star. God bless Iowa!

---

### Post by The Cog on 2014-02-08
FYI, file and directories who's names begin with a dot are normally hidden. So to see .ssh in nautilus you must enable showing hidden files/folders. That's in a menu somewhere, or Ctrl-H will toggle it. In the command line, [FONT=Courier New]ls[/FONT] won't show hidden files but [FONT=Courier New]ls -l[/FONT] will.

Edit:
Not [FONT=Courier New]ls -l[/FONT] , it's [FONT=Courier New]ls -a[/FONT] that also shows hidden files.

---

### Post by Mazdat on 2014-02-08
my sanity has been restored. thank you.

---

### Post by Lars Noodén on 2014-02-08
If you know that you changed the key on the remote host then you can safely remove it from your known_hosts file.  However, there's no need to nuke the whole file or even to edit it manually.  The tool [ssh-keygen](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh-keygen.1.html) can be used to automatically remove a selected key from the known_hosts file.  To remove 192.168.1.1 you'd do the following:

```

ssh-keygen -R 192.168.1.1

```

It then extracts the key to ~/.ssh/known_hosts.old where the removed keys are accumulated.  That does have to be manually cleared.

---

