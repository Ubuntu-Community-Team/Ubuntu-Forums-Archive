---
title: "Bash Script, Multiple Servers"
date: 2006-09-23
forum: Programming Talk
---

### Post by SuperMike on 2006-09-23
Imagine this scenario. You have 10 Ubuntu servers with SSH running on them. Root logins over SSH are disabled, but sudo and su are enabled once you login with a weaker ID like your own username. Routinely on a daily basis, you need to run the same set of a series of commands (commands that change every day) on each of the 10 servers. As well, you may need to use the "scp" command to securely download files across the servers over SSH. Use of the "scp" command often requires knowledge of the root password.

The way the process is handled now is to do this manually, one at a time. The problem is because we don't understand how to feed SSH, su, or sudo a public/password key file such that we don't have to keep typing in passwords all the time.

Can you indicate a way to automate this so that, without user interaction, we can run one master script and it connects to all 10 servers, uses scp to copy down files, run some commands on each server, and disconnects?

---

### Post by toojays on 2006-09-23
Read the man pages for ssh and ssh-keygen to learn how to set up your systems so you don't need to enter a password for SSH.

Read the man page for the sudoers file to find out about how to setup sudo so it doesn't need a password.

---

