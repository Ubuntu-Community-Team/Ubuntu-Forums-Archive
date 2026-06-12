---
title: "GIT Push Trouble"
date: 2010-10-16
forum: Programming Talk
---

### Post by huangyingw on 2010-10-16
Hello,
    I had difficulty at git push back to samba shared folder.
    Bellowing is my git push command output:
    ```
huangyingw@Ubuntu10:~/myproject/git/demo$ git push origin --all
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 314 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
error: insufficient permission for adding an object to repository database ./objects

fatal: failed to write object
error: unpack failed: unpack-objects abnormal exit
To /media/smb/myproject/git/demo/
 ! [remote rejected] master -> master (n/a (unpacker error))
error: failed to push some refs to '/media/smb/myproject/git/demo/'

```
    Where, /media/smb is my remote samba shared.
    Bellowing is my ls command output:
```
huangyingw@Ubuntu10:~/myproject/git/demo$ ls -al /media/smb/myproject/git/demo/objects/
total 0
drwxrwxrwx 35 nobody nogroup 0 2010-10-15 22:37 .
drwxrwxrwx  7 nobody nogroup 0 2010-10-10 04:35 ..
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 03
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 0b
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:37 11
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 20
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 21
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 26
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 05:25 2c
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:52 37
drwxr-xr-x  2 nobody nogroup 0 2010-10-15 22:37 3a
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 3c
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 4b
drwxrwxrwx  2 nobody nogroup 0 2010-10-15 22:28 4f
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 51
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 55
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 5a
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 05:25 64
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 67
drwxrwxrwx  2 nobody nogroup 0 2010-10-15 22:37 69
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 74
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:52 7a
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 ae
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 b0
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 c1
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 05:25 cc
drwxrwxrwx  2 nobody nogroup 0 2010-10-15 22:28 e1
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:40 e2
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 e3
drwxrwxrwx  2 nobody nogroup 0 2010-10-15 22:37 e5
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 e6
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:37 e9
drwxrwxrwx  2 nobody nogroup 0 2010-10-15 22:28 fb
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 info
drwxrwxrwx  2 nobody nogroup 0 2010-10-10 04:35 pack

```
     I found that there is one line with only read right:```
drwxr-xr-x  2 nobody nogroup 0 2010-10-15 22:37 3a
```
     So, I ran this command again:```
sudo chmod -R 777 /media/smb/myproject/git/demo/objects/
```
     And it works. All of the files/dir were changed to 777 rights.Everything should be ok, but in fact it's not.
     After I run command "git push origin --all"
     There would again be one directory with only drwxr-xr-x right. And the just run command git push failed due to insufficient permission.

---

### Post by StephenF on 2010-10-16
NFS is mentioned to work in documentation which reading between the lines suggests that there are issues with Samba, but whatever.

The command "git remote show origin" will indicate the fetch and push URLs*. If you are currently modifying the files directly try the file:// protocol instead.

* Git stretches the definition of URL to the extent that /path/to/file counts as one.

---

### Post by huangyingw on 2010-10-16
> **StephenF said:**
> NFS is mentioned to work in documentation which reading between the lines suggests that there are issues with Samba, but whatever.

The command "git remote show origin" will indicate the fetch and push URLs*. If you are currently modifying the files directly try the file:// protocol instead.

* Git stretches the definition of URL to the extent that /path/to/file counts as one.
Let me summarize your suggestion to clear my doubts:
1:there might be some issue, using samba with git push?
2: Instead, we should use NFS share?
3: I will have a try with file:// protocol.

---

### Post by StephenF on 2010-10-16
It's clearly just a file permissions problem. How you go about solving it is rather dependent on your network architecture and needs which you have not yet specified.

For instance, if you are setting this up for multiple users a git-server would be a better option with ssh for write access to deter malicious commits.

If this is for backing up purposes an off-site solution would be preferable (in case of fire or theft) which also rules out Samba as the best choice.

---

### Post by huangyingw on 2010-10-16
> **StephenF said:**
> It's clearly just a file permissions problem. How you go about solving it is rather dependent on your network architecture and needs which you have not yet specified.

For instance, if you are setting this up for multiple users a git-server would be a better option with ssh for write access to deter malicious commits.

If this is for backing up purposes an off-site solution would be preferable (in case of fire or theft) which also rules out Samba as the best choice.
Well, my situation is that, I only use git to sync code within home PC. Sometimes, I would write code at A PC, and sometimes at B PC, while, I have too many git repositories that it would be a mass of work to set up git-server one by one for them? 
Whatever should I choose?

---

### Post by StephenF on 2010-10-17
Have you tried
```
git push file:///media/smb/myproject/git/demo/ --all
```

If it works update the remote origin section in .git/config accordingly.

Edit: 
You can tell Samba to inherit directory permissions by adding to your smb.conf
```

inherit permissions=yes

```

---

### Post by huangyingw on 2010-10-18
> **StephenF said:**
> Have you tried
```
git push file:///media/smb/myproject/git/demo/ --all
```

If it works update the remote origin section in .git/config accordingly.

Edit: 
You can tell Samba to inherit directory permissions by adding to your smb.conf
```

inherit permissions=yes

```
Well, thank you for help me. Using the file:/// protocol, git push still failed. And I have updated in the smb.conf with inherit permissions=yes, and re-mount smb share, chmod -R 777, and all the works done, my git push still failed..
However, if using root login to "git push", it works:(:(. While in root right, I could not launch some application like kdiff3:(:(...

---

### Post by Seq on 2010-10-18
> **huangyingw said:**
> Well, my situation is that, I only use git to sync code within home PC. Sometimes, I would write code at A PC, and sometimes at B PC, while, I have too many git repositories that it would be a mass of work to set up git-server one by one for them? 
Whatever should I choose?

If it is just you, there is no need for git server. You can push and pull to a remote git repo using ssh. It is much easier than mucking about with a *nix VCS on a *nix filesytem system through the lowest-common-denominator of filesystem features supported by CIFS.

URI syntax is: "ssh://[user@]host.xz[:port]/path/to/repo.git/"

---

### Post by huangyingw on 2010-10-18
> **Seq said:**
> If it is just you, there is no need for git server. You can push and pull to a remote git repo using ssh. It is much easier than mucking about with a *nix VCS on a *nix filesytem system through the lowest-common-denominator of filesystem features supported by CIFS.

URI syntax is: "ssh://[user@]host.xz[:port]/path/to/repo.git/"
Not a good idea, for I have many local git repositories, setting up one by one on remote side is a tedious work for me...
BTW, what is *nix VCS?

---

### Post by Seq on 2010-10-18
> **huangyingw said:**
> Not a good idea, for I have many local git repositories, setting up one by one on remote side is a tedious work for me...

Sorry, I assumed you had these repos you're pushing to over samba were on another Linux machine that you were sharing with samba. If that was the case, you *already* have them set up.

> **huangyingw said:**
> BTW, what is *nix VCS?

Sorry, Version control system for (linux|bsd|unix). Git.

---

### Post by huangyingw on 2010-10-19
> **Seq said:**
> Sorry, I assumed you had these repos you're pushing to over samba were on another Linux machine that you were sharing with samba. If that was the case, you *already* have them set up.



Sorry, Version control system for (linux|bsd|unix). Git.
Thanks. To prevent any mis-understanding, explain my design at home:)
My repositories structure is: all of them under folder myproject, both at "client" and "server" side. So, I just share this folder with samba. And, at my "client" side, after init and commit, I will clone --bare back to the remote samba share. And remote add origin "samba server".
So, next time, all I need to do is just a simple git push --all...

---

