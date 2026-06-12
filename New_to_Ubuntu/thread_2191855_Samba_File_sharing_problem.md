---
title: "Samba File sharing problem"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by lord_cedrich on 2013-12-04
I need help regarding my samba server i created a folder [ACT] for our database for multi user and this is what i did
1. sudo mkdir -p /home/server/ACT
2. sudo chown nobody.nogroup /home/server/ACT
3. then i edited the smb.conf

[ACT]
comment = ACT Server
path = /home/server/ACT
browseable = yes
guest ok = yes
read only = no
create mask = 0755

first its working even in multi user they can access the database without any problem then i decided to create a user accounts in samba
smbpasswd -a user then suddenly when the workstation tried to access the database, the database didnt work i didnt know whats wrong with it, the reason why i created a user in samba because i need to create a 
another folder with validusers so that there will be a restriction in my another folder. By the way my database is designed for 
multi users. I also tried to restart the smb service. I hope somebody could help me thanks.

---

### Post by bab1 on 2013-12-05
Post the output of these commands```
cat /etc/samba/smb.conf

sudo pdbedit -L
```

---

### Post by wlraider70 on 2013-12-05
have you check the permissions and ownership of the files?

ls -l should tell you

---

### Post by Morbius1 on 2013-12-05
@bab1, I know we have a non-spoken gentleman's agreement to stay out of each others way but I think the OP's set up is coming from this HowTo: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

Aside from a number of factual mistakes that have no real consequence it will in fact work as advertised - until you create a user with a samba password and require it's use somewhere.

It's a guest accessible writeable share and the ownership of the shared folder has been set to nobody:nogroup with no change to permissions. Depending on the client and how or when this share or other shares are accessed that client user may no longer be "nobody" since he is now "somebody".

My recommendation to other victims ... er ah .. users that want to have that particular kind of share in addition to others requiring credentials has been to add "force user = nobody" to the share definition. 

You and I often agree on the cause but disagree on the solution so I'll crawl back into the darkness again but I think that HowTo should either add a caveat or be taken down.

---

### Post by bab1 on 2013-12-05
> **Morbius1 said:**
> @bab1, I know we have a non-spoken gentleman's agreement to stay out of each others way but I think the OP's set up is coming from this HowTo: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

Aside from a number of factual mistakes that have no real consequence it will in fact work as advertised - until you create a user with a samba password and require it's use somewhere.

It's a guest accessible writeable share and the ownership of the shared folder has been set to nobody:nogroup with no change to permissions. Depending on the client and how or when this share or other shares are accessed that client user may no longer be "nobody" since he is now "somebody".

My recommendation to other victims ... er ah .. users that want to have that particular kind of share in addition to others requiring credentials has been to add "force user = nobody" to the share definition. 

You and I often agree on the cause but disagree on the solution so I'll crawl back into the darkness again but I think that HowTo should either add a caveat or be taken down.
+ 1 to all you say.  Considerate replies like yours are always welcome!

---

### Post by cid420 on 2013-12-06
this is how mine worked.

comment = Fileserver
path= /home/file/hdd
browsable = yes
writeable = yes
create mask = 0755
directory mask = 0755

this worked fine for me
I logged right into the network and was able to browse the network and able to pull from it and put things into it.

hope this works out for you.

Cid420

---

### Post by Morbius1 on 2013-12-06
Your share definition is a non sequitur as it solves another problem under a different set of circumstances not this one.

The requirements of the original poster is a share that allows everyone access without passing credentials and with the ability to modify all it's contents. He created the folder and set ownership to nobody:nogroup. This is the share he created: 
> [ACT]
comment = ACT Server
path = /home/server/ACT
browseable = yes
guest ok = yes
read only = no
create mask = 0755
This will work ( and if you read the original post it did in fact work just fine ) as long as he never ever adds a samba user ( or at least one that matches a Windows users user name ) or adds another share definition that requires authentication to access ( which he did ). Once he did that the remote user is no longer "nobody" ( which anonymous users default to ) and although Samba allowed that user in they will not be able to write because the Linux permissions won't allow it - only the user "nobody" can write.

He can keep exactly what he has in place - and the HowTo I believe he is following can be corrected - by adding one more line to his share definition:
> [ACT]
comment = ACT Server
path = /home/server/ACT
browseable = yes
guest ok = yes
read only = no
[COLOR=#0000cd]force user = nobody[/COLOR]
create mask = 0755

---

