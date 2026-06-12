---
title: "internal and external ip adddress"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-23
i am using my college wifi to upload files ... when i use filezilla i get this error ECONNREFUSED - Connection refused by server .. i guess its due to the two different ip addresses assigned to my computer by the college server .. any one pls suggest how to solve this problem

---

### Post by d4m1r on 2012-03-23
Not a whole lot of information to go off of...What version of Ubuntu? What browser and version?

Can you post a screenshot of the error?

---

### Post by vivekpandey1991 on 2012-03-23
> **d4m1r said:**
> Not a whole lot of information to go off of...What version of Ubuntu? What browser and version?

Can you post a screenshot of the error?
i use ubuntu 10.10 .. and what has browser to do with the problem of filezilla.. anyways i use firefox..

---

### Post by roger_1960 on 2012-03-23
Hi

If you are able to browse the web, but not upload to somewhere (outside the college?) using FTP it seems likely that the college server has the necessary ports closed to prevent this type of action.  Perhaps best to ask the college IT admin.

---

### Post by beanhead on 2012-03-23
you can use netcat to transfer files over port 80 (web) if you want. 
$man nc

---

