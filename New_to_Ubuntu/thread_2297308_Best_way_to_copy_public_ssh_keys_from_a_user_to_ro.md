---
title: "Best way to copy public ssh keys from a user to root?"
date: 2015-10-02
forum: New to Ubuntu
---

### Post by Raner on 2015-10-02
I have previously used the method "ssh-copy-id" to copy public keys to computers that I want to be able to log in to from my current computer. But I cannot specify that the remote user that I log in to is root because some machines do not allow root ssh access (you instead have to elevate to root once you are logged in). I want the remote machine's root user to have my machine's public key, but I thought that a mere copying of the remote (non-root) user's .ssh directory may overwrite files in the remote root's .ssh directory. What is best method for transferring my machine's public key from the remote user to the remote root? (Or should I be doing something else entirely here and there is an easier method altogether?)

---

### Post by cariboo on 2015-10-02
The safest way to use ssh is not to allow root to ssh. The way you are doing it now, escalating privileges once ssh'd in, is already is the safest. I opt for safety over ease of use every time.

---

### Post by tgalati4 on 2015-10-02
I use *seahorse* to move my keys around.  Don't know how it will work with pushing keys to a root account on a machine that doesn't support root login.

An alternative is to create a user account on the remote machine and give it sudoer privileges. Then move the keys to the user account and use that for admin work.

---

### Post by SeijiSensei on 2015-10-02
I've usually just copied $HOME/.ssh/id_rsa.pub to /root/.ssh/authorized_keys on the remote machine.  You need root privileges on the remote to do this, of course.

---

### Post by Raner on 2015-10-04
Thanks for the replies.

My use case is that I have a cron job  that runs as root but it connects to a remote machine. The normal user  on this machine can connect to the remote machine already (the remote  machine's keys were transferred to the normal user by ssh-copy-id), but  the same cannot be done for root. I am not too familiar with the layout  of the .ssh directory and its files, but I guessed that if I just copied  the the normal users /home/.ssh folder into roots /home/root/.ssh  folder, important things may be overwritten.

I am beginning to  think that if I knew what each file represented in the .ssh folder more I  could work this out a bit better and perhaps only transfer the needed  information. That will be my next step here!

@SeijiSensei: did you mean copy the id_rsa.pub from the remote machine to  the root on the machine that I want to be able to access the remote  machine? Or from the user on the (non-remote) machine to the root on the  same (non-remote) machine?

---

### Post by SeijiSensei on 2015-10-04
Copy id_rsa.pub from $HOME/.ssh/ on the client machine to /root/.ssh/authorized_keys on the remote server.  The authorized_keys file consists of all the public keys, one per line, that are permitted to log in as root on the server without a password.

---

### Post by Lars Noodén on 2015-10-05
> **SeijiSensei said:**
> The authorized_keys file consists of all the public keys, one per line, that are permitted to log in as root on the server without a password.

The full format is described in the manual page for [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) in the section on "Authorized_keys File Format", in case you want to read what all the options are.  It is possible to add parameters to a public key so that it will only be accepted when coming from a particular ip number or network or when used in conjunction with a particular command.  That last bit is very useful, if you are insisting as logging in as root, but needs a lot of attention to detail to get set up.  Hopefully the keys do have a passphrase.  But if they don't, locking them down to a particular command lowers the risk.

---

