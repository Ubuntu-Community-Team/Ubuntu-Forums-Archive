---
title: "total noob here problem trying to backup data from an unbootable laptop"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by noobie96 on 2012-09-19
hi as I have said in the title of this thread and in my profile name I am a total noob here and have no idea in what to do so can you please tell me in easy steps how to fix my problem. I have made a Live CD and have put it into my laptop which has worked because it is running however it won't let me backup my HD everytime I try to access it I get a message saying:

"Unable to Mount location

dbus error org.freedesktop.dbus.error.noreply: did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

to me this is absolute jibberish and so are the pages where people fix this problem I just don't understand.

and as I am new to using ubuntu I'm also not too sure in how to backup my files as well.

If someone can help me step by step I would greatly appreciate it!!!

and sorry wise and intelligent ubuntu users for my total lack of knowledge

---

### Post by Bashing-om on 2012-09-19
noobie96; Hi ! Welcome to the forum.

 No need to apologize for ignorance; We were all once upon a time . Believe me when I say none of us were born knowing what we know. 

 To retrieve your data; Try an easy way thus:

From your live cd open the file manager (in 12.04 is the folder icon top of the launcher),
            - file systems are in the left pane- click to explore-->
insert usb thumb drive into usb port and open it,
drag and drop the files you want from the file manager window to the usb device's window.
                               Hopefully that is all there is to it <==BDQ

---

### Post by noobie96 on 2012-09-20
thanks for responding however I cant see any of my files as I cant access my HD is says it is "unable to mount it" so how do I fix this so I can see what files I am backing up?

---

### Post by cogier on 2012-09-20
From the error message is seems that the hard disk has failed. If possible I would try another drive in your laptop to make sure.

---

### Post by drmrgd on 2012-09-20
I would concur with cogier that your disk might be failing or dead since it seems that it's not responding to the kernel.  Just to be sure, would you might posting how you're trying to mount it in order to make sure there's no syntax error there?

Also, is this a Windows drive or a Linux drive?  I would recommend using an error checking utility to verify the integrity of the file system.  What you use depends on what you've got - it's best to use Windows tools with Windows drives and Linux tools with Linux drives.

---

### Post by Bartender on 2012-09-20
> **noobie96 said:**
> I have made a Live CD and have put it into my laptop **which has worked because it is running** however it won't let me backup my HD everytime I try to access it I get a message saying:

Do you mean the laptop works fine if you just boot normally, but it's not working with a LiveCD?

---

