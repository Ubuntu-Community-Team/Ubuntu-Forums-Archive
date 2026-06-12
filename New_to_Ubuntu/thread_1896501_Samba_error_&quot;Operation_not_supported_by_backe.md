---
title: "Samba error &quot;Operation not supported by backend&quot;"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Zachary123 on 2011-12-17
Attempting to build a HTPC with Mythbuntu on an old desktop I found at my dads house!

I installed Mythbuntu and it runs fine although the specs for this desktop are far from great. So far I have gotten mythmote on my Android phone and successfully tied it into the frontend to get it working.  I have also loaded video and audio files onto the hard drive and have played both through the frontend.  

Now my next challenge is to properly set up Samba so I can transfer files from my laptop to the DVR via the network. I've read many other posts online and even watched some great videos on YouTube but I keep running into the same error.

I have created the sharing folder and can see it from my laptop but when I drag and drop a video it does not work.
I get an error saying that the "operation is not supported by the backend".
Here are some log's for what I have done.  Italic is input and Bold is output

Edit the folder:

*sudo nano /etc/samba/smb.conf*

[I][shaare]
comment = Ubuntu File server share
path = /shaare
browseable = yes
guest ok = yes
read only = no
create mask = 7777
directory mask = 7777[/I]

After this I made the path:

*sudo mkdir shaare*

Then changed the read/write:

*sudo chmod 777 shaare*

And checked:

*ls -l *

**drwxrwxrwx 2 root root 4096 2011-12-16 23:31 shaare**


Is this enough or have I missed a vital part to making this work?

Please let me know if I have left any details out and thanks in advance.

-Z

---

