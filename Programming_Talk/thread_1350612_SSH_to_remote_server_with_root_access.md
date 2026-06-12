---
title: "SSH to remote server with root access"
date: 2009-12-09
forum: Programming Talk
---

### Post by chancekang on 2009-12-09
Hey guys,

I don't know if it is ok to post this question here, but I did not find a better sub-forum to ask this question, so....



To describe my question, I found it may be easier to describe a scenario here:

There are two machines. Server A and Server B, both of them are linux server. 
I have enabled ssh on Server B, what I wanna do is to use scp to copy files from Server A to Server B. The issue is that the specific folder on server B that I want to copy to needs root access. Locally on server B, I can either use root account or use sudo to do the copy. However, I found that it seems to be not possible to use sudo with scp command. If possible, I would rather not use root account in my scp command. 

The question is: is there any other ways I can do this without root account? Thanks a lot!

---

### Post by cdenley on 2009-12-09
You can use key authentication to authenticate as root rather than setting a root password. This would be safer, but I still wouldn't call this safe. Another alternative would be to create a cron script on the server to copy the files from somewhere you do have permission to write to. Of course, you can always change permissions so YOU can write files where you need to. What kind of files are you trying to transfer?

---

