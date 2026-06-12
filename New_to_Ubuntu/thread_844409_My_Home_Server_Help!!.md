---
title: "My Home Server Help!!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-06-29
I have installed apache and webmin. Now I want to have my web site in my home folder to be the first page I get when I type my IP address of my server. Also is their a web mail application with a mail server that Ubuntu has or some sort of a web proxy that only allows you to visit ubuntuforums.org?

---

### Post by hyper_ch on 2008-06-29
(1) apache base path is /var/www --> put your homepage in there

(2) webmail --> have a look at squirrelmail (I think it's easy to setup)... horde would be another option

(3) squid is a proxy server...you could configure it to only allow access to ubuntuforums.org

---

### Post by jamesrfla on 2008-06-29
Thanks for the help hyper_ch. I tried to put my web page in /var/www but the paste option was whited out. Any ideas?

---

### Post by spiderbatdad on 2008-06-29
create a folder in you home directory called anything_you_want. Inside that folder put a file called "index.html."

As root copy the file /etc/apache2/sites-available/default to a file called /etc/apache2/site-available/my_site.

Edit the root document in my_site to point to the folder in your home directory. Run a2dissite /etc/apache2/sites-available/default & a2ensite /etc/apache2/sites-available/my site

[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by hyper_ch on 2008-06-29
/var/www is owned by root... simple and dirty hack would be:

```

sudo chowin USER.USER -R /var/www

```
where USER is your username... thne you can copy stuff into it

---

### Post by jamesrfla on 2008-06-29
hyper_ch the command didn't work. It said command not found. spiderbatdad I get what you said up to the part of As root copy the file /etc/apache2/sites-available/default to a file called /etc/apache2/site-available/my_site. I find the default file but not the other file. How do you login as root?

---

### Post by hyper_ch on 2008-06-29
sorry,

```

chown

```

would be correct ;)

---

### Post by jamesrfla on 2008-06-29
Yeah it worked this time and my web site is up and running internally. In the future it will be working outside my network. I will try on my spare time to get squid to work and squirrelmail. Thanks for all the help!!:guitar:

---

### Post by cariboo on 2008-06-29
Instead of changing ownership why not just create a symlink  to your file. In a terminal

```
cd /var/www
sudo ln -s /home/<user>/<directory>/index.html index.html
```

where /home/<user>/<directroy> is where your file is located in your home directory. That way if you make any changes to you file you don't have to change permissions or ownerships. and the changes will show up instantly, when you reload the page.

Jim

---

### Post by hyper_ch on 2008-06-29
apache doesn't like symlinks by default... you'll have to set it to accept that ;)

---

### Post by jamesrfla on 2008-06-29
Is Squid used for blocking web sites throughout a LAN network or is it used as a web proxy server?

---

### Post by cariboo on 2008-06-29
I've been doing it for years just using the default config files, mind I've only got it setup for internal usage, so I'm not to worried about security.

Jim

---

### Post by jamesrfla on 2008-07-04
I think I am ready to set up up my mail server. Any suggestions for what mail server I should get? I want it to be able to do POP3 and a web mail interface with the mail server? Which web mail interface is the best? Also I was looking at the Synaptic Package Manager and I saw that everything was installed. Is it me or is it supposed to look like that? Last thing is hyper_ch recommended a proxy server. I probably should of explained more but I am looking for a web proxy server that will allow me to view blocked web pages behind a proxy server. Dose Linux have something like that?

---

### Post by hyper_ch on 2008-07-04
postfix --> mta
squirrelmail --> webmail
courier-imap --> imap server (why do you want pop3 if you can have imap?)
procmail --> local delivery agent

---

### Post by jamesrfla on 2008-07-04
What is the difference between pop3 and IMAP?

---

### Post by hyper_ch on 2008-07-04
well, you know what a pop3 server does? you know what an imap server does?

---

### Post by jamesrfla on 2008-07-04
I am guessing they both do the same thing. I went ahead and did some research and found five different mail servers that will do what I want it to do. 1. Citadel 2. Hexamail 3. Meldware Mail 4. QmailToaster and last 5. Zimbra. I just don't know what one to pick???

---

### Post by hyper_ch on 2008-07-04
well, pop3 and imap are different ;)

---

### Post by jamesrfla on 2008-07-04
I think I am going to go with Citadel mail server. It looks nice and will do what I want it to do. Just to make it easier I put my unanswered questions on the bottom. Thanks for all the help!!

I was looking at the Synaptic Package Manager and I saw that everything was installed. Is it me or is it supposed to look like that? I am looking for a web proxy server that will allow me to view blocked web pages behind a proxy server. Dose Linux have something like that?

---

### Post by jamesrfla on 2008-07-04
Okay I need help installing this Citadel mail server. I went to hear [http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian) and tried that but it didn't work. Now I can't even get updates fir my Ubuntu computer. Next I went hear [http://www.citadel.org/doku.php/faq:installation:compile_debs](http://www.citadel.org/doku.php/faq:installation:compile_debs) and that didn't work too. The the last thing I tried was this [http://debian.citadel.org/ubuntu/hardy/](http://debian.citadel.org/ubuntu/hardy/) I did all the updated files and i386.deb files. It wouldn't let me do the server package and some other ones. The error message was Dependency is not satisfiable: libdb4.3. Any ideas or other ways to install this mail server?

---

### Post by jamesrfla on 2008-07-04
I went to this forum [http://ubuntuforums.org/showthread.php?t=708383](http://ubuntuforums.org/showthread.php?t=708383). I went through it okay but when I got to sudo apt-get update I got a whole bunch of errors. I get a bunch of 404 not found. Are the Ubuntu update servers down? Any ideas?

---

### Post by jamesrfla on 2008-07-09
I got my mail server to work so hears my last question. I installed Webmin and want to access it outside my network. I know it is risky and I have to port forward some ports. The only reason I want to use it on the internet is for the HTTP Tunnel. If their is another program that can do HTTP Tunneling through the web browser and is encrypted I would like to know. If I can't find or hear about a HTTP Tunnel with those capabilities I will have to forward the ports for Webmin. Webmin uses https so I know I have to port forward port 443 but in the web browser it shows as [https://ip](https://ip) address:10000/. Do I need to port forward port 10000 as well?

---

### Post by jamesrfla on 2008-08-02
You can ignore everything else on this page except this post. What is the difference between apache2 and apacheSSL? I know all the data for apacheSSL is encrypted. Can I have like my home page (192.168.1.4) to be just regular HTTP and the rest to be HTTPS? Are their any other apache versions?

---

