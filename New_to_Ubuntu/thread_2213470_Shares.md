---
title: "Shares"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by pieter-boks on 2014-03-26
I am new to Ubuntu desktop 13.10 and Ubuntu server 13.10. I have loaded each OS on two different laptops on the same WIFi connection at Home. Both OS's loaded well and seem to be working.
I am trying to create shares from the desktop to the server, I have installed Samber on both machines and the samba config tool on the desktop. I have created the shares and can browse to them, however, I can only mount them is I tick the folder sharing menu (guest access), otherwise I keep getting a dialogue box saying windows shares and asking for a domain name that I do not have.
The Questions:
1. is there a better way to do this, or am I completely off track.
2. There seems to be a permission problem with these shares only working with guest ticked.
3. How do I solve this 
Thank you for your time.

Pieter

---

### Post by Kirboosy on 2014-03-27
On the server you will only need the samba package. From there you can configure the server by editing the following file

```
nano /etc/samba/smb.conf
```

Here is an example of my Samba configuration on my server. I have appended this to the very bottom of my file
```
[House Files] #Name of the share
        comment = Media Files # You can explain the share further if you wish.
        browseable = true # Do you want your share to broadcast accross the network for all to see? Turn this to false if you want it to be more hidden from view
        path = /data # Simply type the absolute path of the folder you want to share
        guest ok = true # If you turn this to no then every person trying to access the share will have to authenticate with a valid username and password
        read only = false # Do you want your users to be able to make changes to the files or only be able to read it? If you want them to only read this should be set to true.
```

The complete and very thorough documentation on this file and all the parameters can be found here: [smb.conf]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

My setup is very open and not very secure. My mentality is, if I let you on my network I don't care if you have access to my samba share.

Your client laptop once you get everything configured properly should be able to see it under "Network"

Hope that helps!
~Caboose

PS Everytime you make a change to smb.conf you should restart the samba service with the command ```
sudo service smbd restart
```

---

### Post by pieter-boks on 2014-03-27
To Caboose885

Thanks a lot for the answer, This helped me a lot.

Thanks for your time

Pieter

---

### Post by Kirboosy on 2014-03-27
If this has solved your problem please mark your thread as solved! (Under "Thread Tools" above the first post in the top right corner)

Glad to of help!
~Caboose

---

