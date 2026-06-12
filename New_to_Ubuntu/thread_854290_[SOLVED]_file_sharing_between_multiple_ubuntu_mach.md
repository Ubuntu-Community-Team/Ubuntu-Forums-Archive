---
title: "[SOLVED] file sharing between multiple ubuntu machines"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-09
well i have been using ubuntu long enough now, so i figure its time to learn how to setup filesharing


right now i can go to "Places-Network"  and i can see "Windows Network" with our only windows computer showing up


but how can i make all of our ubuntu computers show up?


EDIT: i suppose i should be more specific


i have one computer with Ubuntu 7.10
two computers with Ubuntu 8.04 
one computer with Fluxbunutu 7.10
and one computer with windows vista (dont care about filesharing with this one though)

---

### Post by harsh_ on 2008-07-09
The easiest way is to use FTP by using vsftp (very secure file transfer protocol)

install it by using;
sudo apt-get install vsftpd
(d stands for deamon)
the 2 aspects are vsftpd.conf and the vsftpd command... Other help abt this is available on other threads here itself... It is the easiest and reliable way to file transfer/sharing.....

---

### Post by bobbob1016 on 2008-07-09
Two questions:
Are you running Hardy on both of the Ubuntu machines?
Do you want to share Ubuntu to Ubuntu only or Ubuntu to Windows and Ubuntu to Ubuntu?

Edit:  I just saw your edit.  You should use NFS then.  NFS is a Unix filesharing standard, and is much easier to get all the Ubuntu's talking on.  It does require some editing text files, but nothing major.  Open a terminal and type "sudo gedit /etc/exports" on the machine you want to share the files from.  I have a freenas machine with NFS setup, and it's /etc/exports file has "/path/to/directory/ -alldirs -network 192.168.0.0 -mask 255.255.255.0" without quotes for each share.  Change -network to 192.168.1.0 if your router is 192.168.1.1, and if your router is 192.168.2.1 change it to -network 192.168.2.0 and so on.  If you only want them shared to one machine, just put it's IP address in.  Then from Ubuntu you can mount it.  Just type "sudo mount [server_address]:/mnt/shared /mnt/gemensamt/ -o rw,hard,intr", [server_address] is the machine sharing the folder, /mnt/shared is where it is mounted ON THE SERVER, /mnt/gemensamt is where it is mounted ON THE LOCAL MACHINE.

---

### Post by tjwoosta on 2008-07-09
> Two questions:
Are you running Hardy on both of the Ubuntu machines?
Do you want to share Ubuntu to Ubuntu only or Ubuntu to Windows and Ubuntu to Ubuntu? 

i have one computer with Ubuntu 7.10

two computers with Ubuntu 8.04

one computer with Fluxbunutu 7.10

and one computer with windows vista (dont care about filesharing with this one though)

---

### Post by superprash2003 on 2008-07-09
if its a linux only network then you could install NFS and use it.. if you want vista too then you gotta use samba

---

### Post by tjwoosta on 2008-07-09
ok ,  i guess im gonna need a little help with this

i installed "nfs-common" and "nfs-kernal-server"  on all the machines


now this is my /etc/exports on the machine that i want to share files from

```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

```

what do i need to do in order to share theese directories with every computer on my network?   
~/Music
~/Videos
~/Pictures
~/Downloads
~/torrent

also is there a way to use a password? (if not no big deal)


then what do i need to do to the machines that i want to access the files from

by the way my router is 192.168.1.1 but the internal ip for all the computers seems to constantly change

---

### Post by louieb on 2008-07-09
I used the lan ip settings of my router to assign the same IP to the same PC each time it boots.  
Then I installed open-ssh-server on each of my Ubuntu machines. 
After that go to places connect to server. give it the ip and a name to call it.  Then you can use Nautilus  to navigate that machines files just like you were logged in. Uses sftp to transfer files from computer to computer.

NFS is pretty slick too just a little harder to set up but once setup a little easier to use.

---

### Post by billgoldberg on 2008-07-09
**Forget** all other posts.

Sharing files between  ubuntu machines is easy, to easy almost.

Link to the guide on my blog;

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

Seriously, 2 minutes setup.

---

### Post by tjwoosta on 2008-07-09
ok, this looks like it could be much easier

> by the way my router is 192.168.1.1 but the internal ip for all the computers seems to constantly change 

ok i guess i was wrong here   (all the ip's stay the same except for my laptop, which is the only one with wireless)

how do make my local IP consistent?  

as far as i remember it used to always stay the same, but then one day stuff started just messing up  (like my port forwarding) and i was like what the hell

ever since then i cant use port forwarding because my ip is always different ever time it login


here are some screenshots of my router setup  (hopefully what i need to do is in one of theese pics)

---

### Post by halitech on 2008-07-09
click on the network applet (near to the clock) and select the "Manual configuration" option and enter in the IP address you want it to be all the time. That should allow you to use your port forwarding again as well.

---

### Post by tjwoosta on 2008-07-09
> click on the network applet (near to the clock) and select the "Manual configuration" option and enter in the IP address you want it to be all the time. That should allow you to use your port forwarding again as well.

hahaha ..

its amazing all the little things i miss


thanks

---

### Post by tjwoosta on 2008-07-09
> 
Forget all other posts.

Sharing files between ubuntu machines is easy, to easy almost.

Link to the guide on my blog;

[http://linuxowns.wordpress.com/2008/...ntu-computers/](http://linuxowns.wordpress.com/2008/...ntu-computers/)

Seriously, 2 minutes setup.
 

ok it was only about two minutes setup but it wont work

it just keeps saying connection timed out ever time i try to connect (it never even asks for the password)

---

### Post by kcnnc on 2008-07-10
NFS is easy to setup if you are the administrator. But it seems there is no user side tools to do that like in Windows.

Say user1 want to share his /home/user1/Desktop/myshare folder. Can user1 right click on the folder in Nautilus as say "share this"?

Also how does user2 find out about this user1 share. Can the share be browsed?

These user don't know how to go to terminal and do export or mount.

Anyone using a solution for such a user base?

---

### Post by HyperHacker on 2008-07-10
> **billgoldberg said:**
> **Forget** all other posts.

Sharing files between  ubuntu machines is easy, to easy almost.

Link to the guide on my blog;

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

Seriously, 2 minutes setup.This didn't quite work for me as I have no "connect to server" in the Places menu, but after installing openssh, I was able to use scp which works just as well.

---

