---
title: "Netbeans and network shares"
date: 2011-07-01
forum: Programming Talk
---

### Post by Macrotus on 2011-07-01
Hi all

I'm not quite sure is this the right place for this thread, moderators can move it to the right place.

So, my question is about Netbeans and Windows network shares. I have Windows Server 2008 R2 installed on our server, and there is our http-server (IIS 7.5) running. I'd like to develop websites with Netbeans because I can't get Notepad++ installed on Ubuntu. My problem is that I can't see or access the network shares with Netbeans IDE 7.0. I've connected to the server (Places -> Connect to a server or something like that, I use an another language..) and I can access to the files and others from Places menu. 

Any solutions? 

By the way, I'm running Ubuntu 10.04 LTS and Netbeans 7.0.

---

### Post by Zugzwang on 2011-07-01
If you have mounted your SMB share, it should occur somewhere as a sub-folder of ~/.gvfs - Search in there using Netbeans.

---

### Post by Macrotus on 2011-07-06
Thanks. I mounted them in /mnt/sharename. Btw, I can't write whit my normal account, but when I log in as root I can. How I can give rights to my normal account? It's a mounted Windows SMB share..

---

### Post by Macrotus on 2011-07-06
I solved the problem when I added gid and uid parameters to the query and chowned these folders before mounting.

---

