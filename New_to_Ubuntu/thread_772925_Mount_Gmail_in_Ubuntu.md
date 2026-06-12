---
title: "Mount Gmail in Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by MadsRH on 2008-04-28
Hi
I've heard that it is possible to mount your Gmail account as a drive in Linux.
Can anyone provide me with a linux-newbie guide to do this? :confused:

I was hoping that it was as simple as finding it in Add/Remove programs, but no :(

---

### Post by bmac on 2008-04-28
I think this will help...

[http://ubuntuforums.org/showthread.php?t=768282&highlight=ssl+gmail](http://ubuntuforums.org/showthread.php?t=768282&highlight=ssl+gmail)

---

### Post by kostkon on 2008-04-28
> **MadsRH said:**
> Hi
I've heard that it is possible to mount your Gmail account as a drive in Linux.
Can anyone provide me with a linux-newbie guide to do this? :confused:

I was hoping that it was as simple as finding it in Add/Remove programs, but no :(
You'll need to install the *gmailfs* package. Just search for it in *Synaptic* and then install it.

---

### Post by sdennie on 2008-04-28
I was able to get it working doing the following:

```

sudo apt-get install gmailfs
cp /etc/gmailfs/gmailfs.conf ~/.gmailfs.conf
chmod 600 ~/.gmailfs.conf

```

Then, edit the file ~/.gmailfs.conf to give it your username and password for gmail.  After that, I was able to mount it using:

```

mkdir gmail
mount.gmailfs none gmail

```

---

### Post by xtigma on 2008-04-28
[SIZE="3"][FONT="Courier New"]Hey Hello. that sounds interesting. I will try it as soon as anyone answer me something.

Does it open in Firefox, Nautilus or Thunderbird (or any mail program as Evolution) ?

Thanks in advance.[/FONT][/SIZE]

---

### Post by michael2706 on 2008-04-28
sorry for the noob question, but what does mounting your gmail actually do differently than just setting the account up in evolution? i.e., whats the point of doing it?

---

### Post by sdennie on 2008-04-28
That will mount it as if it's a hard drive so, you'll be able to treat it just like a disk in nautilus or the terminal.

---

### Post by MadsRH on 2008-04-28
vor -> That is a really great guide :) It looks like it is working, but when I try to copy files I get a Python error and I get these weird email with the subject "b=1209420390 x=0 q=__g__linux_fs_3" :confused:

---

### Post by sdennie on 2008-04-28
Those e-mails are normal actually.  It's treating your  gmail account as a disk but, doing it by sending yourself e-mails.  You should be able to make a gmail filter to automatically archive and mark as read emails with that have that "__g__linux_fs_3" string in the subject.

Unfortunately, I'm not sure what the python error is.  Things seem to be working fine for me so far.

---

### Post by asgard_command on 2008-04-28
There is also a Firefox extension called Gspace which makes it very easy to use your gmail space as a file system storage area in this way.
I haven't tried it under Firefox 3 yet so can't confirm whether it is yet compatible with that.

---

### Post by DJiNN on 2008-04-30
+1 for gspace, it's a great FF addon. Works well, but i'm having a problem keeping the email account details, and have to re-input them everytime i restart the browser. Apart from that, it works fine.

---

### Post by Mortuis on 2008-05-23
> **vor said:**
> I was able to get it working doing the following:

```

sudo apt-get install gmailfs
cp /etc/gmailfs/gmailfs.conf ~/.gmailfs.conf
chmod 600 ~/.gmailfs.conf

```

Then, edit the file ~/.gmailfs.conf to give it your username and password for gmail.  After that, I was able to mount it using:

```

mkdir gmail
mount.gmailfs none gmail

```

I tried following these instructions, but when I try the last line I get: "HTTP Error 400: Bad Request"

Any idea how to fix this?

---

### Post by t0p on 2008-05-23
Another vote for **gspace** here!! To be honest, I haven't even tried *gmailfs*... but gspace was so easy to set up, and is so easy to use, I think it'll do me okay!

---

### Post by Maestro23 on 2008-05-23
+1 for Gspace.  Great Add-on.:guitar:

---

### Post by avacomputers on 2009-12-03
> **sdennie said:**
> I was able to get it working doing the following:

```

sudo apt-get install gmailfs
cp /etc/gmailfs/gmailfs.conf ~/.gmailfs.conf
chmod 600 ~/.gmailfs.conf

```

Then, edit the file ~/.gmailfs.conf to give it your username and password for gmail.  After that, I was able to mount it using:

```

mkdir gmail
mount.gmailfs none gmail

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gmailfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gmailfs has no installation candidate

---

