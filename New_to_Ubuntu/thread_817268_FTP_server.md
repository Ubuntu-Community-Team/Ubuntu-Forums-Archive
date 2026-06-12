---
title: "FTP server"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-06-03
Hi,

At the university where I work I have been asked to make a file, which is ca 1.5 GB in size, available for download to various people.

The file won't fit on our web server (we are only allocated 200 MB).

I do however have full control over a computer (currently without any OS), which has a static IP address (i.e. it has been assigned one public IP address by the uni, as has every computer in their entire network).

I have recently been very impressed by Ubuntu and wondered if I could use it to help me here. I though about making my own web server or FTP server to offer this file for download.

Does this sound like a good idea?
Is it possible on a normal installation of Ubuntu?
Which is better web / ftp?
Can anyone point me in the direction of a howto, to help with the installation and configuration?
Is there anything else I need to take into consideration (security for example)?

Greatly appreciate any help.

---

### Post by ruffEdgz on 2008-06-03
1. Sure, but you don't want to do something that you aren't totally comfortable with. The more sensitive the data, the harder it will be for you to play with it, understand the set up and so on...

2. Yes it is possible with a normal installation of Ubuntu :D

3. Both are fine but you will need to make which ever one you want secure so not everyone can access the information (using some kind of authentication).

4. [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

5. Firewalls and protection is always key to making a server which will be talking to the world or even your local area. It's always wise to read up on ways to create more secure connections and how other people are securing their ftp servers and so on, so forth...

Hope that helps :D

---

### Post by Jim_in_Germany on 2008-06-03
Excellent, thank you very much.
This is exactly what I was looking for. 
The files in question are only photos so security isn't a major issue, so I guess I will go ahead, install Ubuntu and an FTP server and have a good play around.
Cheers
Jim

---

### Post by wwusnobrdr on 2008-06-03
I agree either should work for you.  I like having a web server, just copy files to the /var/www directory and you can link them to people.  Also an FTP server is easy to setup as well. I suggest getting proftp and gproftp (sp?) for GUI configuration.  Apache is super easy to setup!

---

### Post by Jim_in_Germany on 2008-06-04
Yeah, cheers for that. 
I decided to go for the Apache option in the end as it really was a piece of cake to set up and configure. It also makes life easy that our uni gives every computer a fixed ip address.
When I've got a bit more time I'll probably put the server into a virtual machine just for an added bit of security.

---

