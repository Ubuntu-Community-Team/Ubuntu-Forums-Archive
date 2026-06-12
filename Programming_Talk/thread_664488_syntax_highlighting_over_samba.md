---
title: "syntax highlighting over samba"
date: 2008-01-11
forum: Programming Talk
---

### Post by xdaiana on 2008-01-11
Hello all,

does anybody know about a syntax highlighting editor which i can use over samba? I already tried kate and amaya, seems those can't handle smb links.

The exact situation: I want to edit html/asp code direct from a windows machine over the local network on my ubuntu machine for running it on the same windows. 

Thank you,
Daiana

---

### Post by [h2o] on 2008-01-11
Hmm, if the file is openable by the application, then syntax highlighting should work without problem.

I have never had any problem editing files over samba _if the share has been setup properly_.

---

### Post by xdaiana on 2008-01-11
well, with the settings i have now i can open the file with gedit, but under kate i get this error:

Could not start process Unable to create io-slave:
klauncher said: Unknown protocol 'smb'.

---

### Post by [h2o] on 2008-01-11
Then the problem is with the KDE kio-slaves. I have no solution to that though. But if gedit works then why don't use that? It has syntax-highlighting.

---

### Post by xdaiana on 2008-01-11
yes, that should be true, it seems indeed to be kde-related. 
kate is just my favourite editor and that's why it was my first choice. but under this circumstances i have to use gedit. i'm ashamed... i wasn't aware of the syntax highlighting facility because (obviously) it doesn't support asp. thanx a lot for the quick answer

---

### Post by popch on 2008-01-11
Many applications appear to be unable to locate or store files on directories accessedthrough SMB. Try mounting the SMB shares in your client. They are then just parts of the file system hierarchy and can be used by any application, I believe.

---

### Post by KCPokes on 2008-01-11
> **popch said:**
> Many applications appear to be unable to locate or store files on directories accessedthrough SMB. Try mounting the SMB shares in your client. They are then just parts of the file system hierarchy and can be used by any application, I believe.

The best approach, IMO.  Use smbfs to set up mounts on your client, which will connect on boot.  At that point they are local and it wouldn't matter what application you are using.

---

### Post by xdaiana on 2008-01-11
yes, it worked on the mounted share.

thanx to all of you!

---

