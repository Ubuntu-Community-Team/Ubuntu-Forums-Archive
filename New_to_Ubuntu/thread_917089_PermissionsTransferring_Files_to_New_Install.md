---
title: "Permissions/Transferring Files to New Install"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by wmichaelb on 2008-09-11
Hi, I finished building a new machine, and installed Hardy. To transfer my old files from 7.04, I burned a CD with the contents of the home file on my old machine. But when I transferred them to the new machine,they showed up locked. I tried the chown command, but to no avail. How can I unlock them so that I can use them as new files? Or alternatively, delete them and transfer them in an unlocked way?
Thanks in advance,
- Michael B. in Cincinnati

---

### Post by hubie on 2008-09-11
How did you copy all the files?  Did you tar them up first?  If so (and this is the easiest way to do this kind of copy), when you untar on the new system, you can set the [FONT="Fixedsys"]-p[/FONT] option to keep the permissions the same as they were before.

If you didn't use tar, how did chown fail?  What message did it return?  Did you run it from sudo?

chown will change the user (don't forget to change the group as well, so if your account is bob, you would run 

[FONT="Fixedsys"]sudo chown -R bob:bob *[/FONT]

where the [FONT="Fixedsys"]-R[/FONT] is there to run recursively so that it will crawl down all the directories.

If you want to change the read/write permissions, you also need to run chmod.  You run it the same way as chown.

---

### Post by wmichaelb on 2008-09-12
First, Hubie, thanks for responding!

Per this link:

[link]("http://ubuntuforums.org/showthread.php?t=917001&highlight=change+permissions")

I did this:

sudo chown username: /home/username
chmod 755 ~/ && chmod 644 ~/.dmrc
sudo shutdown -r now

From your message, I note that I did not use the -R flag.
So I went back to terminal and did this:

sudo chown -R username:username *

and the system executed that. Then I went on and typed:

sudo chmod -R username:username *

but the system failed to run that command, and fed back:

chmod: invalid mode: `mike:mike'

At this point, the files I've transferred all show the 
"locked" icon, although I can read them. When I try to 
save an Open Office document into one of them, I get
the messages:

Error saving the document Untitled1: home/username/Computers/test.odt
does not exist

And then:

Error saving the document Untitled1: General Error. General Input/Output
Error.

I never tar'd the files in the first place; there were only 300 MB or so,
so I simply dumped them onto a CD, walked across the room, put the CD
in the drive, and started copying files. 

It wouldn't be the end of the world if I had to reinstall; I don't have 
much on the system yet. But if it's possible to fix this with the command
line, that would save a lot of time. 

There may be another related problem. When I tried to save my test file
from Write and clicked on "Save as" and "browse", it showed a bunch of 
system files in my /home/username directory, although Nautilus doesn't 
show them when I navigate to that directory. I added a sound card to the
system after installation, and did some command line stuff to install the
correct driver for that. The sound card is working fine, but I may have
put some things in the wrong directory?????

Thanks in advance for any help or insight you can offer.

---

### Post by wolfen69 on 2008-09-12
```
sudo chmod -R ug+w /home/mike
```

---

### Post by dagoth_pie on 2008-09-12
The locked icon (i think) means that they are owned by root, theres probably a way to use the chown command on the directory and change all the files so they are owned by your user account, however I dont know it, you could chown every file or look into finding a way to do it to all the files in one command, or if you think itd be easier, you could use:
gksu nautilus
command to get into the folder with root access, then either change the files over to your user account, or delete them, then copy them accross in a tar file

---

### Post by wolfen69 on 2008-09-12
> **dagoth_pie said:**
> The locked icon (i think) means that they are owned by root, theres probably a way to use the chown command on the directory and change all the files so they are owned by your user account, however I dont know it, you could chown every file or look into finding a way to do it to all the files in one command, or if you think itd be easier, you could use:
gksu nautilus
command to get into the folder with root access, then either change the files over to your user account, or delete them, then copy them accross in a tar file

the reason they are locked is because files on a cd are read only. ubuntu keeps the read only attributes when copied over.

---

### Post by dagoth_pie on 2008-09-12
> **wolfen69 said:**
> the reason they are locked is because files on a cd are read only. ubuntu keeps the read only attributes when copied over.

Oh ok, I wouldn't have thought that the actual file permissions would have been changed they just wouldn't have been writable for the reason of the cd not being writable, but ohwell, you learn something new every day, I've always use my lan for transfers so I've never needed to use a cd like this

---

