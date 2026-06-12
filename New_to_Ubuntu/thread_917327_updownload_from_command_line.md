---
title: "up/download from command line"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by sfong15 on 2008-09-11
I'm working on a VPS 8.04.1 server playing around learning.   From time to time I want to print text file being edited by nano, I think there isn't way to do that right?

What's the easiest way to download a file from server to desktop for printing without leaving command line?   Same for uploading a file from desktop to server without the trouble of starting filezilla?

---

### Post by Pro-reason on 2008-09-11
Well, to download stuff, you use “wget”.

But are we talking about FTP here?

---

### Post by Ntweat on 2008-09-11
if u r using ssh then i would suggest using the comman scp it works both ways... that is sending to server as well downloading.... syntax

```
scp <file name of file on ur comp with path> <login>@<server:<file on server with path>
```

---

### Post by y@w on 2008-09-11
Not quite sure what you're trying to do here.. but if you're using SSH from the desktop you're trying to copy the files to and you're working with small files you could always just copy-paste using the mouse.. Not exactly ground-breaking, but definitely an option. Just do 'cat filename' and open in an editor.

---

### Post by lswb on 2008-09-11
Well, you should be able to print directly from the command line with the "lp" command. man lp for the options. 

For transferring files between 2 systems there are lots of options, I like ssh and sshfs for linux systems. With sshfs on your local system, you can log into a ssh server and basically set up a mount point that points to a directory on the server. Then you can just copy files back and forth with the normal cp and other cli commands.

---

### Post by Ntweat on 2008-09-11
well... if u use SSH if u can leave the terminal u can always use X server forwarding.... i opens any application u want .... the application will be on server but u will see it on ur comp... so jst copy and paste

---

### Post by Pro-reason on 2008-09-11
If you're using FTP, you can log on with this:
```

ftp *username*@*site*

```
Obviously replacing the words in *italics* with the appropriate names.

That will start an FTP shell.  Type “help” for available commands.  (You'll mostly want “put” and “get”.)

---

### Post by sfong15 on 2008-09-12
> **Ntweat said:**
> if u r using ssh then i would suggest using the comman scp it works both ways... that is sending to server as well downloading.... syntax

```
scp <file name of file on ur comp with path> <login>@<server:<file on server with path>
```

Thanks what if I am logged in already, so how I download a file onto my local PC desktop (which is a Mac).

Heard that curl does something similar right?

---

