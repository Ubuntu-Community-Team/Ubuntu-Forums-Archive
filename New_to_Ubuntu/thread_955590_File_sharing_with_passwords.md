---
title: "File sharing with passwords"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Buntubailey on 2008-10-22
Hello,

I have been trying to set up my server and have managed to create a RAID5 array and install the server with samba, open ssh and print server, then I installed webmin. I am trying to configure it so when I access the shares from a windows machine it asks for user and password, I have managed to make it do this but for some reason the only username and password it will accept to access the shares is the root(administrator). When I try to log in with any of the users I have created windows tells me logon failed or I don't have sufficient priveliges. I have made sure that the unix users and samba users are the same, and in webmin, I have set in the samba section that all users should be able to connect with their username and password. It even says in the samba share list that all the shares are read/writable to everyone but I am finding when I try to connect from a windows machine that it rejects me everytinme unless I logon with root credentials.

Is there anyone who could help me out on this matter I am pulling my hair out,

Thanks in advance,

Buntubailey.

---

### Post by Thelasko on 2008-10-22
You know that Samba usernames and passwords are completely different than system usernames and passwords, right?  You have to setup Samba usernames and passwords separately.

---

