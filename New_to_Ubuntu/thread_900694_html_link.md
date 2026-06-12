---
title: "html link"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by muted1987 on 2008-08-25
hey this is a really stupid question but ive forgotten

how do you set up a link in html to a file on my computer so it can be downloaded form browser?

---

### Post by zamadatix on 2008-08-25
i dont quite get what oyu mean. you cn link a html page to a file in your computer but it can only be accessed from that computer. if you want to share a fiel with a computer in your netwrok you can jsut put it in hte shared network folder.

---

### Post by finer recliner on 2008-08-25
```
<a href="http://domain.com/">Click here!</a>
```

---

### Post by muted1987 on 2008-08-25
zamadatix i am trying to setup a webserver using apache (first time no expireince) and just wanted to check if i could access files

---

### Post by zamadatix on 2008-08-25
ahh that helps alot. never did a server myself but you might get a quick answer bye googleing an apahce help guide and trying to find it there. if not someone in the forums will know.

---

### Post by muted1987 on 2008-08-25
i have had a look around and there all jargon to me lol . basically all i want is to be able to access my filesystem from my webserver so i can download stuff from anywhere in the world and was told apache was the best way to go

---

### Post by zamadatix on 2008-08-25
[http://www.bluereef.net/support/serverbasics/upload.html](http://www.bluereef.net/support/serverbasics/upload.html) in this is imanager is that what oyu were looking for? or do you want to use your server ot downlod the files?

---

### Post by muted1987 on 2008-08-25
i would like to use my server

---

### Post by pyromanic123boom on 2008-08-25
I think this [http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php](http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php) is what you're looking for. 
Because the guide is written for windows, follow this as well. [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

---

### Post by zamadatix on 2008-08-25
why dont you use remote desktop on your computer (not the server unless oyu have to use the server)?

---

### Post by pyromanic123boom on 2008-08-25
A server makes more sense than remote desktop, because you would have to remember stupid little things. A server you can access from virtually anywhere, easily from a friend's computer or at a public computer.

---

### Post by muted1987 on 2008-08-25
> **pyromanic123boom said:**
> A server makes more sense than remote desktop, because you would have to remember stupid little things. A server you can access from virtually anywhere, easily from a friend's computer or at a public computer.

yup thats pretty much why im setting a server up 

i have the server setup to the point where someone outside lan can get in to see the index.html which is bog standard hello for the time being.tahts when tutorials get a bit over the head

---

### Post by OffAxis on 2008-08-25
> basically all i want is to be able to access my filesystem from my webserver so i can download stuff from anywhere in the world and was told apache was the best way to go
If there's only a few static files on your machine that you want to get to, then yes, apache is the way to go, but if you want access to your filesystem (like a terminal client) then you'll need to set up an ssh or remote desktop server daemon.

---

### Post by zamadatix on 2008-08-25
i looked at them and see what you mean.(btw your post made me want a server so im using my 3rd computer as one) i couldnt reeally find it in gogle (VERY rare) and couldnt even get it to return exactly what it was you are looking to do... so i always find antying i search for in google ill keep going.

---

### Post by pyromanic123boom on 2008-08-25
Yeah I'd use apache to do the job...I don't know anything about VNC in linux though.

---

### Post by pyromanic123boom on 2008-08-25
I remember setting up a PSP MP3 RSS feeder with an apache server..worked wonderfully.

---

### Post by muted1987 on 2008-08-25
ok i think its time to try to put into words what i want


my goal : to setup a server that can access my files anywhere in the world so far all i got is that bloomin it works but i can change this.

have a login authentication so that only i or someone with the uname/pword combo can access them.

---

### Post by zamadatix on 2008-08-25
you can try a apche forum like [http://www.apachefreaks.com/]("http://www.apachefreaks.com/") and they might be able to get you help faster than this forum

---

### Post by pyromanic123boom on 2008-08-25
No it's really not that confusing. Well...a little..ha.

If you don't mind compiling and a bit of tinkering, go here:
[http://webdesign.about.com/cs/apache/a/aainstallapache.htm](http://webdesign.about.com/cs/apache/a/aainstallapache.htm)

This might shed some more light on it, but it's basically the same type of article.
[http://linuxgazette.net/issue12/server.html](http://linuxgazette.net/issue12/server.html)

This is just for localhost and I forget how to make it public..

---

### Post by OffAxis on 2008-08-25
why not just use open ssh ?

sudo apt-get install openssh

(for the client and server)

and here's some docs:
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

that'll give you full access to your machine from anywhere (just forward the appropriate port through your firewall)

---

### Post by pyromanic123boom on 2008-08-25
> **OffAxis said:**
> why not just use open ssh ?

sudo apt-get install openssh

(for the client and server)

and here's some docs:
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

that'll give you full access to your machine from anywhere (just forward the appropriate port through your firewall)

wow i am stupid...lol i saw that earlier. nice point

---

