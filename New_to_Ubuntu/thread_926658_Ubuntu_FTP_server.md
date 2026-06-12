---
title: "Ubuntu FTP server"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by FransB on 2008-09-22
Dear Ubuntu Community :D 

I have a few questions about a Ubuntu FTP server,

First Question:
what is the best FTP server for a company (50-100 employees) but i think its used by 1-8 man

2nd Question:
Can i use the normal desktop ubuntu version or do i need the server version, id rather have graphical interface so i think the Desktop Ubuntu is better for me ( if possible ).


Thanks for all your help :D.

greetz,

Frans

(a linux newbie :P)

---

### Post by Orange_and_Green on 2008-09-22
Hello Frans,

You can install the server edition, then type
```
sudo apt-get install ubuntu-desktop
```
at the prompt and it will give you a graphical environment:popcorn:

If I were you, I'd install the server edition. During installation it will ask you what servers you want to set up (ftp, mail, dhcp, dns...), autoinstall and do a basic auto-configure.

Have lots of fun with your server:)

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

### Post by FransB on 2008-09-22
> **Orange_and_Green said:**
> Hello Frans,

You can install the server edition, then type
```
sudo apt-get install ubuntu-desktop
```
at the prompt and it will give you a graphical environment:popcorn:

If I were you, I'd install the server edition. During installation it will ask you what servers you want to set up (ftp, mail, dhcp, dns...), autoinstall and do a basic auto-configure.

Have lots of fun with your server:)


ow ok thx alot, but it hasn't has high priority at the moment, i think i will wait for ubuntu 8.10 :p. with building the ftp server.


Another question (im very noobie in building servers :oops:)

How can i add files to that FTP server do i have to put them in a sort of map or something else?


Frans

---

### Post by Sef on 2008-09-22
>  ow ok thx alot, but it hasn't has high priority at the moment, i think i will wait for ubuntu 8.10 :razz:. with building the ftp server.

Once difference is that Hardy Heron server will be supported until April 2013; Intrepid Ibex will only be supported until April 2010.

---

### Post by Orange_and_Green on 2008-09-22
I second Sef 120%. For servers, the main issue **definitely** is stability and security, not glittery shiny new features. By now, I think Hardy is "stable" enough to entrust it with a (corporate!) server, but if you had asked this question 4 months ago you might even have wanted to consider Gutsy (7.10)... or Dapper (6.06);)

I surfed the internet and found a few guides for setting up ftp servers. These are the first hits which seem helpful to me:

[http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
(Kudos to frodon for posting this extensive guide)
[URL="http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux"]
http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux[/URL]

Have fun :)

---

### Post by FransB on 2008-09-22
> **Orange_and_Green said:**
> I second Sef 120%. For servers, the main issue **definitely** is stability and security, not glittery shiny new features. By now, I think Hardy is "stable" enough to entrust it with a (corporate!) server, but if you had asked this question 4 months ago you might even have wanted to consider Gutsy (7.10)... or Dapper (6.06);)

I surfed the internet and found a few guides for setting up ftp servers. These are the first hits which seem helpful to me:

[http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
(Kudos to frodon for posting this extensive guide)
[URL="http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux"]
http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux[/URL]

Have fun :)

ow ok :).

then ill just try hardy :P. so now i can go testing virtual :p. 

Thanks for all your help all :) Sef and Orange :D .


Greetz

Frans

---

### Post by FransB on 2008-09-22
Sorry For the Double post,

but when installing the Server i dont see FTP, or is it the Samba File server (but that was a SMB server i thought)?

Picture:

[IMG]http://i34.tinypic.com/15fisgi.png[/IMG]

---

### Post by Orange_and_Green on 2008-09-22
No, no, Samba has nothing to do with ftp (Samba is about sharing files, printers and resources within the local network).

I was under the impression there was an "FTP" entry for the server installer too... Oh well, I guess you will just have to proceed to "Volgende" without installing any server now and add the FTP server later via apt-get...:)

Happy installing:KS

NOTE: I have found a [site]("http://www.linux-magazin.de/heft_abo/ausgaben/2008/01/ein_affenzirkus") claiming that installing the "LAMP" server will "collaterally" install an ftp server as well but I cannot confirm this... In theory, a LAMP server should comprise only Apache with php, and MySQL...

---

### Post by billgoldberg on 2008-09-22
I would just install the normal Ubuntu version if you need a GUI.

Setting up a ftp server shouldn't be that hard.

I'm sure google will have enough guides:

[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=ubuntu+set+up+ftp+server](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=ubuntu+set+up+ftp+server)

---

### Post by FransB on 2008-09-22
Doesnt matter :) i accidently did POSTRESQL :P.

but i will see where i end xD. installing the User interface now :).

Volgende is next in dutch (my language :P). 

Thanks for all the help :D


im going to love this community <3

And ubuntu is a nice alternative 
A: because its free
B: Linux <3 :p

---

### Post by taqkavar on 2008-09-22
Just use gproftpd on a regular ubuntu installation.
It is very easy to setup and maintain and takes very little resources. After you are done setting it up, you can just exit the GUI and let the server run.

---

### Post by FransB on 2008-09-23
> **taqkavar said:**
> Just use gproftpd on a regular ubuntu installation.
It is very easy to setup and maintain and takes very little resources. After you are done setting it up, you can just exit the GUI and let the server run.

But i also can run Gproftpd on the ubuntu server with the ubuntu GUI. :D

going to try this today.

---

### Post by jonabyte on 2008-10-01
So I followed the first link (to setup vsftpd), which seemed simple enough, but I got this after I restarted the ftp:

```

 * Stopping FTP server: vsftpd 
No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd  

```

Not sure what happened, any ideas?

---

### Post by Bachstelze on 2008-10-01
This is normal. You tried to resart vsftpd while it was not running in the first place, so you get a warning. It should be running now.

---

### Post by jonabyte on 2008-10-01
Sorry, wasn't clear enough. This same error happens even after I do the restart command again...and again.

---

