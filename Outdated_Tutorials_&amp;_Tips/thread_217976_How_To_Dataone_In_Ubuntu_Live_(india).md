---
title: "How To Dataone In Ubuntu Live (india)"
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by tux21 on 2006-07-17
QUESTION : i have ubuntu live cd.. and got dataone connection.... Plz tell me how to manually confire dataone.. ihave the IP adress and other things but where to enter the username and passsword/.... plz help..

ans: 

here is how.

first u have to download

freshmeat.net/redir/rp...3.8.tar.gz

unzip it

tar -xvzf rp-pppoe-3.8.tar.gz

store that unzipped folder rp-pppoe-3.8 in a windows partition or linux

partition. Don not use floppy disk as space requirement more.


in ubuntu live cd

1.open terminal applications->accessories->terminal

2.type <sudo su> to become root (withount < >)

3.do <apt-cdrom add>. and follow instructions.

4.do <apt-get install cpp>

5.do <apt-get install gcc>

6.do <apt-get install make>

7.do <apt-get install g++>

say Y to all questions.

now all requirements are met !

just mount the drive where u have that folder rp-pppoe-3.8

go inside it and do :

chmod 777 go

and then

./go

thats it.

i am posting this from ubuntu live dapper drake cd !!

i hope u know how to mount drives ?

DNS VALUE is 61.1.96.69

and 61.1.96.71

set firewall option to 1

---

