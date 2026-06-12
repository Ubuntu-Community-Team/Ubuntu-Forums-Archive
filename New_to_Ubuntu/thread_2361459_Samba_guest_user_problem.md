---
title: "Samba guest user problem"
date: 2017-05-16
forum: New to Ubuntu
---

### Post by seloram on 2017-05-16
Hi there, I¡m new using Ubuntu and Samba (I'm not sure if this is the correct thread for Samba's issues) and I have to do something it's not working at all. I have to create a folder and give access  to a two groups, the first one must be able to write and execute, the second to write, and the guest only to read.
This is my .conf file:

[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of

   workgroup = WORKGROUP
   server string = Samba Server %v
   netbios name = profeubuntu
   security = user
   map to guest = bad user
   guest account = nobody
   dns proxy = no


and the shared folder:

[usertest]
path = /samba/test
valid users = @group1 @group2
guest ok = yes
writable = no
write list = @group1
browsable = yes

I can only get in with the users in @group1 and @group2 groups, but I don't know how to configure a guest account and how it Works, because Windows always ask me for a user and pass and to put nobody and the pass I have given to it doesn't work. 

Could you somebody just to write down a simple example to allow guest's and a user to Access to the same folder with diferent access permits? guest only read, the user writes...

Thanks a lot...

---

