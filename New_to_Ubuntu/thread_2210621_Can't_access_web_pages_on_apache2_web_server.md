---
title: "Can't access web pages on apache2 web server"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by D_2 on 2014-03-11
I can't access any web page that is on my ubuntu 13.10 server, I get the error 
[h=1]Not Found[/h] The requested URL /rentals was not found on this server.
 Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.


I have checked my router port forwarding and that is correct, I even deleted the port settings and recreated them, this didn't work, I even uninstalled apache2 and reinstalled it, this didn't work. I can access the pages if I use the internal IP address of 192.168.x.x but if I use the one that I have through DYNDNS then it doesn't work. I have made sure my external IP is correct with DYNDNS and I have even tried to access the pages using my external IP/webpage and that doesn't work. What else can I do to allow me to get to my web pages using my [www.registered](www.registered) name.com again. This did work, I am wondering if a update or upgrade broke something.

any help please.

---

### Post by tfrue on 2014-03-12
Have you created the virtual website with apache and enabled it?

EDIT: Sorry, I re-read what you have posted and you wouldn't be able to access it if it wasn't enabled lol. Anyway, will you post the output of:
```
cat /etc/apache2/sites-enabled/<yoursite>
```

Thanks

---

### Post by D_2 on 2014-03-12
the /etc/apache2/sites-enabled/ directory is empty, is there something that needs to be in that directory, or is there a configuration script that can be run to set things up correctly seeing as I deleted apache2 and reinstalled it.

---

### Post by tfrue on 2014-03-12
Here is a link to the Ubuntu 13.10 server guide that does a good job explaining Apache2:
[https://help.ubuntu.com/13.10/serverguide/httpd.html](https://help.ubuntu.com/13.10/serverguide/httpd.html)

Here is link from the Apache2 website on virtual host configurations:
[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

Here are virtual host examples:
[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

 If you can't make sense of this, since it's a bit overwhelming, I will go over a basic set up. I would also like to point out that you will not be able to copy /etc/apache2/sites-available/default, the file is actually named "000-default.conf" so you would actually type: cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mynewsite.conf

This is what the "000-default.conf" file looks like:
```

chris@ubuntu:~$ cat /etc/apache2/sites-available/000-default.conf 
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

```

You need to make "#ServerName www.example.com" look like -> ServerName <DYNDNS FQDN>. So basically delete the "#" and replace "example.com" with your DYNDNS FQDN.(Fully Qualified Domain Name)

You can edit the DocumentRoot and ServerAdmin options, but you don't have to; the only thing to note is that you will need to put your web files in the /var/www/ directory.

Just a tid bit of information, if you would like a certain html file open when someone tries to go to your site, meaning when someone types your FQDN in the address bar, you need to edit the /etc/apache2/mods-available/dir.conf file. 

Here is what it looks like:
```

<IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

```

So let's say that you want to serve /var/www/main.html as the file that will be your main page, you would insert "main.html" infrot of "index.html". So the "dir.conf" file would look like:
```

<IfModule mod_dir.c>
    DirectoryIndex [COLOR=#0000ff]main.html[/COLOR] index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

```

Chris

---

### Post by tfrue on 2014-03-12
After you do all this, you need to enable the new virtual host configuration and reload the web server, so type:
```

sudo a2ensite mynewsite.conf
sudo service apache2 reload
sudo service apache2 restart

```

You may not have to do the restart command, but it never hurts.

Chris

---

### Post by D_2 on 2014-03-12
Thank you for your help on this tfure, I have done the steps you said starting with the cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mynewsite.conf and also editing that one line for the server name and I am still getting the same error. Is there something else I can do to fix my problem.

---

### Post by tfrue on 2014-03-13
Were you able to successfully run the "sudo a2ensite mynewsite.conf?

Will you post the output of (You can copy and paste into a terminal):
```
ls -ll /etc/apache2/sites-available/;ls -ll /etc/apache2/sites-enabled/;cat /etc/apache2/sites-enabled/*.conf;a2query -s
```

What this will do is execute four different commands. First being a long listing ( ls -ll ) of the sites-available directory, the second is the same but of the /sites-enabled/ directory, the third will "cat" the contents of any file in the /sites-enabled/ directory that has ".conf", and the last will query apache2 for the sites that are enabled.

Chris

---

### Post by D_2 on 2014-03-13
Here is what it says, I did give up on this and formatted the server and reinstalled ubuntu and I am still getting the same error. Is there any way I can check the steps that requests are going like if I were to type in my doman name.com and watch where it goes from my system back to my web server and where it goes from there, am I having some strange issue with my router, or what, if I type in the local IP address for that system the default web page does come up so the apache web server is working to a point, but where is that error coming up or why


```
total 12
-rw-r--r-- 1 root root 1327 Jul 24  2013 000-default.conf
-rw-r--r-- 1 root root 6432 Jul 20  2013 default-ssl.conf
total 0
lrwxrwxrwx 1 root root 35 Mar 12 22:22 000-default.conf -> ../sites-available/000-default.conf
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com]("http://www.example.com")

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
000-default (enabled by site administrator)
```

---

### Post by newbie2244 on 2014-03-13
Which version of UBuntu are you running? I recently downloaded & installed Ubuntu 12.04 and it did not include Apache. Try  ```
sudo apt-get install apache2
```. Your webpage mountpoint is at /var/www. Once you download it,  test it by typing   127.0.0.1 as the url in your browser. Then test for  localhost configuration by using "localhost' as the url. If apache is enabled, you'll get the mesg "It Works!".

---

### Post by D_2 on 2014-03-13
I downloaded the latest version of server 13.10.  If I type in the local IP 192.168.x.x the "It Works" does show up. but not if I go to [www.my_domain_name.com](www.my_domain_name.com) I get the original error message it does add a /UI at the end, not sure why if I use the domain name not if I type in the local IP address

---

### Post by tfrue on 2014-03-13
You're still not creating the new site from the 000-default website, and you're also not enabling the new site. You only have the default web site, 000-default, enabled and it is not set up to use the domain name you have.

You should be able to copy/paste these commands into your terminal.

Again, type:
```

sudo cp /etc/apache2/sites-available/000-default /etc/apache2/sites-available/dyndns.conf

```
That will take the default configuration and create a new config file that you can use while retaining the default.

We will then need to edit that file, so use your favourite text editor ( I use vim), and open the /etc/apache2/sites-available/dyndns.conf. Type:
```

sudo vim /etc/apache2/sites-available/dyndns.conf

```

This will open the file, and you can now make changes. We want to uncomment the ServerName option so we can define how we want that Virtual host to respond. So delete the pound/hastag ( # ) infront of SeverName, and change the [www.example.com](www.example.com) to the dyndns domain name you were provided with.

Save the file, and then we will need to enable the new Virtual host, and reload the web server.

To do those things, type:
```

sudo a2ensite dyndns.conf;sudo a2dissite 000-default;sudo service apache2 reload

```
What that does is enable our new virtual host, dyndns.conf, then disables the default virtual host, 000-default, and reloads the web server so we are working with clean and updated configurations.

Hope this helps.
Chris

---

### Post by D_2 on 2014-03-13
Ok I have done the steps you have requested, I am still getting the same error message. Also now that I have reinstalled the server I can't copy the web files back onto the server using sumba, I have done chmod 777 -R www and it wont let me copy files onto the server using Windows, any ideas, I thought I might have to change owner but it wont let me change it, I might be using the command wrong. I also hate to have that directory all open to everyone like I have, but that is all I know how to get access to it.

---

### Post by newbie2244 on 2014-03-13
I'm looking at your "code" listing  and you did not uncomment "www.example.com". [br]f you visit the home page for [url]apache.org[/u] access their docs on configuration, you will find the answer to your problems. Essentially you need to customize the **httpd.conf** file for your applications/web pages.[/br] 
[list] One good reason to read those docs is because they discuss security issues. (I don't know if you want to actually host web pages on your system for the general public, but if that was your intent, you NEED TO address security for your system.) 
[*] AFter you browse through the apache docs, another useful site to visit is [xampp.org](xampp.org) out of Germany. [/*] 
[/list]
 You might want to download xampp as well. The community support out of the apache friends org is outstanding.  If you decide to do this, you will have to stop the apache2 instance currently running on your system But that's a few steps dpwn the road. Its been a while since I configured apache but maybe we can work on this together. [br]BTW, how long have you been using Ubuntu - Linux?[/br] Don't give up. A month or two down the road and you will be an expert on httpd.conf.  [/br][br]Regards[/br]

I'm looking at your "code" listing  and you did not uncomment "www.example.com". [br]f you visit the home page for [url]apache.org[/u] access their docs on configuration, you will find the answer to your problems. Essentially you need to customize the **httpd.conf** file for your applications/web pages.[/br] 
[list] One good reason to read those docs is because they discuss security issues. (I don't know if you want to actually host web pages on your system for the general public, but if that was your intent, you NEED TO address security for your system.) 
[*] AFter you browse through the apache docs, another useful site to visit is [xampp.org](xampp.org) out of Germany. [/*] 
[/list]
 You might want to download xampp as well. The community support out of the apache friends org is outstanding.  If you decide to do this, you will have to stop the apache2 instance currently running on your system But that's a few steps dpwn the road. Its been a while since I configured apache but maybe we can work on this together. [br]BTW, how long have you been using Ubuntu - Linux?[/br] Don't give up. A month or two down the road and you will be an expert on httpd.conf.  [/br][br]Regards[/br]

[br]if you visit the home page for [url]apache.org[/u] access their docs on configuration, you will find the answer to your problems. Essentially you need to customize the **httpd.conf** file for your applications/web pages. ----------This sentence was somehow cut out of my previous message. For some reason the [br] [/br] tags are not working properly. Sorry.

I'm actually working on this problem right now. I may have suggested that you do not need to customize other config files for apache2. That is not the case. But you can customize httpd.conf in addition to the apache2.conf for your own specific user needs. WIll get back to you.  Sorry about any unintentional misrepresentation and regards to all other posters on this thread.

---

### Post by D_2 on 2014-03-13
I have this all solved now, I can access the default index.htm page using both the mydomain.com and [www.mydomain.com](www.mydomain.com) with out error. Firefox and chrome still have an issue (I guess it is cashed) they both give me the errors, but if I use my cell phone or Safari it does work and gives me the correct web page. Now to find out why Samba isn't letting me put my files back on the server now that the directory and files have the 777 permissions.

---

### Post by Iowan on 2014-03-13
> **D_2 said:**
> I have this all solved now,...Remember to mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") before you leave. :)

---

### Post by D_2 on 2014-03-13
Thank you for reminding me Lowan, I was wanting to check a few things out before making it solved.

---

### Post by tfrue on 2014-03-13
> **newbie2244 said:**
> I'm actually working on this problem right now. I may have suggested that you do not need to customize other config files for apache2. That is not the case. But you can customize httpd.conf in addition to the apache2.conf for your own specific user needs. WIll get back to you.  Sorry about any unintentional misrepresentation and regards to all other posters on this thread.

Actually in Ubuntu, there is not an httpd.conf. That is debain and possibly different distro's of Linux, Ubuntu uses apache2.conf, just for future reference.

Glad to hear that your problems are solved! You may need to edit the share you have defined in the /etc/samba/smb.conf to allow others or disallow others. I would help you their too if you would like.

---

### Post by newbie2244 on 2014-03-14
Actually if you look into the dir /etc/apache2 there is an httpd.conf file , although its empty. Its  up to the user to custom  configure apache2 .

Actually if you look into the dir /etc/apache2 there is an httpd.conf file , although its empty. Its  up to the user to custom  configure apache2 . The conf files are all linked.

---

### Post by Doug S on 2014-03-14
> **newbie2244 said:**
> Actually if you look into the dir /etc/apache2 there is an httpd.conf file , although its empty. Its  up to the user to custom  configure apache2 . The conf files are all linked.No, do not use httpd.conf. For the OP, running 13.10 that file will not be there. For you, it is there for legacy reasons only, and you are running some version that was part way through getting rid of it.

---

