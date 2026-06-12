---
title: "I need help setting up my ubuntu how i want on my server."
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Trainergames on 2012-07-01
Ok i have a Dell Poweredge 1600SC server,and i will be moving in with some friends in a month,and i want the server to be ready by then,i have it up and running with the latest verison of ubuntu,now all i need to do is setup the OS,but i am a total ubuntu noob i ave barly ever used it,which is why i need some help.

Ok the way i want to set it up is,i am going to hook up the server to my TV using a VGA cable,and i want use it as a HTPC,but i also want to set it up so that if i am out of town,and i need something off my server i can type in my IP(and mabye a port if i need to)then put in a password,and then have it allow me access to my files on my server.

Any and all help would be greatly appreciated.

---

### Post by rai4shu2 on 2012-07-01
For TV, I suppose you'll want to start with [Mythbuntu]("http://www.mythbuntu.org/") (although I'm not sure how well that will work out with an ATI Rage). Then you can setup a file server whatever way you feel like will work best for your needs.

See [https://help.ubuntu.com/12.04/serverguide/file-servers.html](https://help.ubuntu.com/12.04/serverguide/file-servers.html)

---

### Post by Trainergames on 2012-07-02
> **rai4shu2 said:**
> For TV, I suppose you'll want to start with [Mythbuntu]("http://www.mythbuntu.org/") (although I'm not sure how well that will work out with an ATI Rage). Then you can setup a file server whatever way you feel like will work best for your needs.

See [https://help.ubuntu.com/12.04/serverguide/file-servers.html](https://help.ubuntu.com/12.04/serverguide/file-servers.html)

Does mythbuntu install just like ubuntu?
Also any advice on the best easy way to setup a file server? Cause like i said i have barly ever used unbuntu and linux,and have no idea what i am doing lol

---

### Post by Cheesehead on 2012-07-02
> **Trainergames said:**
> i am going to hook up the server to my TV using a VGA cable,and i want use it as a HTPC

Depends on the TV. If the TV is fairly new and has a VGA-in, then it should already work. Have you already tried?


> **Trainergames said:**
> i also want to set it up so that if i am out of town,and i need something off my server i can type in my IP(and mabye a port if i need to)then put in a password,and then have it allow me access to my files on my server.

Servers connected to the internet are likely to be constantly probed. Mine has about 2000 attempts on an average day. Think security, or your system will be compromised!

Use openssh-server. See [https://help.ubuntu.com/community/SSH/](https://help.ubuntu.com/community/SSH/) for detailed instructions. Pretty much any other service you want to use can be tunnelled through your ssh connection. 
   Do not use the default port (22). Change it to something else.
   Do not use mere password protection on a machine open to the internet. Setup keys. It's not difficult. Disable root ssh access.
   Consider secondary defenses: fwknockd, fail2ban, and/or a limited-access account, etc.

---

