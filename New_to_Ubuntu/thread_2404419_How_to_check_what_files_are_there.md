---
title: "How to check what files are there"
date: 2018-10-23
forum: New to Ubuntu
---

### Post by sajjad2500 on 2018-10-23
I am new to Ubuntu I just got a task that on hosting there is a ubuntu  16.10 running and I need to see which data is there when I ask the hosting provider he gave me only ssh access by user name and password so i wrote ls -sh to see the list of files available there that seems very few files so can anyone help me is there anything I am missing because I have to move all data and the way I am seeing its only few mb data.

---

### Post by TheFu on 2018-10-24
Welcome to the forums.

Support for 16.10 ended in 2017.  Sorry.   That release has more than a few remote attacks and the system has ZERO hope of being secured.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) shows currently supported releases.  If you need more than 6 months of support, choose an LTS. Either 18.04 or 16.04 would be best.

As for basic Unix/Linux commands, there are many tutorials and free online classes available.  Without knowing what "data" you are supposed to move, it would be impossible to suggest where it might be on the system.  I suspect you are in over your head.

---

### Post by Impavidus on 2018-10-24
16.10 is indeed old, so let's get those files and copy them somewhere safe. There is the find command to find files, but it's far too complex to explain every detail of find in a post here. Search for a tutorial. There may also be hidden files, with a name starting with a dot. ls will list them if you use ls -a. If you have ssh access, you should be able to use rsync to get those files.

---

### Post by lbcunha1 on 2018-10-27
> **sajjad2500 said:**
> I am new to Ubuntu I just got a task that on hosting there is a ubuntu  16.10 running and I need to see which data is there when I ask the hosting provider he gave me only ssh access by user name and password so i wrote ls -sh to see the list of files available there that seems very few files so can anyone help me is there anything I am missing because I have to move all data and the way I am seeing its only few mb data.

Hi Guy,
If you have ssh access you should have ftp access too. In order to work with files a ftp client is more efficient than the terminal. Would be [Filezilla]("https://filezilla-project.org/") a trial? 

Regards

---

### Post by TheFu on 2018-10-27
> **lbcunha1 said:**
> Hi Guy,
If you have ssh access you should have ftp access too. In order to work with files a ftp client is more efficient than the terminal. Would be [Filezilla]("https://filezilla-project.org/") a trial? 

Regards

Plain FTP should have been killed off in 1995 with rlogin and telnet. Please don't use it over the internet with any credentials.  Anonymous, fine.  Logins, NEVER.

However, sftp should be included with ssh access and all the other ssh-based tools should work.

---

