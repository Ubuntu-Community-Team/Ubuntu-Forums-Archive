---
title: "Chown command"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by ex-para on 2013-09-19
forbes@forbes-Satellite-Pro-2100:~$ sudo chown -R www:www /var/www/example.com/public_html
[sudo] password for forbes: 
chown: invalid user: `www:www'
forbes@forbes-Satellite-Pro-2100:~$

Can anyone please tell me why this command will not work.

---

### Post by Impavidus on 2013-09-19
Do the user and group "www" exist? If not, you either asked for the wrong user and group or you forgot to create them.

---

### Post by ex-para on 2013-09-19
I think so as it comes afer this command
sudo mkdir -p /var/www/example.com/public_html
Thanks for the reply.

---

### Post by Lars Noodén on 2013-09-19
You can see the info about the user *www* using the [id](http://manpages.ubuntu.com/manpages/raring/en/man1/id.1.html) utility.

```

id www
id forbes

```

If there is no such user, it will say so and you can then add it using the regular methods for adding a user.

---

### Post by ex-para on 2013-09-19
forbes@forbes-Satellite-Pro-2100:~$ sudo chown -R www:www /var/www/example.com/public_html
[sudo] password for forbes: 
chown: invalid user: `www:www'
forbes@forbes-Satellite-Pro-2100:~$ id www
id: www: No such user
forbes@forbes-Satellite-Pro-2100:~$ id forbes
You are correct no user, what I am trying to do is move a website that I host myself onto another computer and as it is more than six years since I built the site and used a laptop as a server I have forgot how to get it on the internet. I am copying commands from a Howto so how do I get a user.

---

### Post by Lars Noodén on 2013-09-19
If you are the only user on the new system you could just give ownership of that directory to yourself and not worry about adding another user.  

Otherwise, to create a user and group, use [adduser](http://manpages.ubuntu.com/manpages/raring/en/man8/adduser.8.html)

```

sudo adduser www

```

Of course there is also a way to do that with the GUI but it varies from distro to distro.

---

### Post by ex-para on 2013-09-19
Ok thanks, I will have to leave now and try it later and then see how it goes

---

### Post by Azdour on 2013-09-19
Hi,

Are you following a set of instructions?

Could the instructions be wrong and that www should be www-data?

---

### Post by ex-para on 2013-09-20
I am having trouble what I should have in the root var after making the requested change
Step One&#8212; Create a New Directory

The first step in creating a virtual host is to a create a directory where we will keep the new website&#8217;s information. 

This location will be your Document Root in the Apache virtual configuration file later on. By adding a -p to the line of code, the command automatically generates all the parents for the new directory. 
sudo mkdir -p /var/www/example.com/public_html


Change the root extension to match the directory that we made in Step One. If the document root is incorrect or absent you will not be able to set up the virtual host.
 server {
        listen   80; ## listen for ipv4; this line is default and implied
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6

        root /var/www/example.com/public_html;
        index index.html index.htm;

        # Make site accessible from [http://localhost/](http://localhost/)
        server_name example.com;


}

---

### Post by Lars Noodén on 2013-09-20
[mkdir -p](http://manpages.ubuntu.com/manpages/raring/en/man1/mkdir.1.html) will make a directory including any parent directories that it needs.  

But about the virtual host, which web server have you installed?  nginx or Apache2?

---

### Post by ex-para on 2013-09-20
Thank you, nginx.

---

### Post by Lars Noodén on 2013-09-20
Ok.  And just to be sure, you did install nginx using the package manager? (Software Center, synaptic, or apt-get)  That will make sure that the scripts and configuration files are in the expected locations and do the expected things.  It will also mean that the documentation for Ubuntu will apply.  

[https://www.digitalocean.com/community/articles/how-to-install-nginx-on-ubuntu-12-04-lts-precise-pangolin](https://www.digitalocean.com/community/articles/how-to-install-nginx-on-ubuntu-12-04-lts-precise-pangolin)

There is also an online [list of configuration directives](http://nginx.org/en/docs/dirindex.html), so anything you find or add to the configuraiton file(s) can be looked up there.  

The default location for the first virtual host's configuration will be */etc/nginx/sites-available/default*

So if you have made a document root for your virtual host,

```

sudo mkdir -p /var/www/example.com/public_html
sudo cp /etc/nginx/sites-enabled/default /etc/nginx/sites-enabled/default.orig

```

then the configuration file should point to it.  Specifically, the configuration directive [root](http://nginx.org/en/docs/http/ngx_http_core_module.html#root) should point to it.

```

root  /var/www/example.com/public_html

```

Which guide or tutorial are you trying to follow?

---

### Post by ex-para on 2013-09-20
How To Set Up nginx Virtual Hosts (Server Blocks) on Ubuntu 12.04 LTS

[https://www.digitalocean.com/community/articles/how-to-set-up-nginx-virtual-hosts-server-blocks-on-ubuntu-12-04-lts--3](https://www.digitalocean.com/community/articles/how-to-set-up-nginx-virtual-hosts-server-blocks-on-ubuntu-12-04-lts--3)

---

### Post by Lars Noodén on 2013-09-20
Thanks.  That guide makes the point that you have to have nginx reload the configuration file any time you change it, or else the changes won't take effect.

```

sudo service nginx reload

```

You can also use the same [service](http://manpages.ubuntu.com/manpages/raring/en/man8/service.8.html) utility to restart, stop or start nginx.

---

### Post by ex-para on 2013-09-20
Thanks again I will now digest all this and then have another attempt.

---

### Post by Lars Noodén on 2013-09-20
I have a couple more things to suggest.  

After a while, if you later decide to make a lot of changes you can open a terminal and keep a live, real-time display of the error logs:

```

tail -f /var/log/nginx/error.log

```

But before you get that far, you might want to use check the configuration file for correct syntax. (substitute 'default' for the right file)

```

/usr/sbin/nginx -t -c /etc/nginx/sites-enabled/default 

```

That will check the designated file for correct syntax and report any errors to the screen.

---

### Post by ex-para on 2013-10-06
I am still trying to sort my server out and now followed another Howto [http://www.youtube.com/watch?v=hlyKRQcqgFo](http://www.youtube.com/watch?v=hlyKRQcqgFo)
And having properly install nginx again the basic tuning below will be OK for me if I just exacly what I should do.
 
Basic tuning
If all you want to do is serve some static pages to your LAN, you can probably stop here. Nginx is up with a basic configuration in place and all of your website's files are located in/usr/share/nginx/html. You can edit the default*index.html*file or drop your own stuff in there and it will be instantly visible.

---

### Post by Lars Noodén on 2013-10-06
I checked out the video.  There is one concern that at about 0:50 where the instructions are to add a foreign repository to your system. Effectively that gives root access on your machine to whoever is running the site ftp.hosteurope.de.  Looking at the subsquent parts of the video, that chane was not needed for the rest of the demo.  Regular package installation instructions should work for nginx without adding foreign repositories.

About the HTML files, he uses sudo a lot to get around the permission problem.  That works too, but chown on those directories might be easier, since it only needs to be done once.  nginx puts the [document root in a strange location](http://manpages.ubuntu.com/manpages/raring/en/man7/hier.7.html) but if it runs, it runs.  /var/www would have been more appropriate.

---

### Post by ex-para on 2013-10-06
Thank you, could you please tell me how I can achieve */var/www with what I have now got.

---

### Post by Lars Noodén on 2013-10-06
Sure.  If you make the directory and chown it, 

```

sudo mkdir /var/www/
sudo chown forbes /var/www/

```

then you'll need to edit the configuration file (assuming you're using the original, default virtual host)

```

sudo nano -w /etc/nginx/sites-enabled/default 

```

The [-w is to prevent long lines from wrapping](http://manpages.ubuntu.com/manpages/raring/en/man1/nano.1.html), just in case.  

Inside the configuration file, you are interested in the line which sets DocumentRoot remove /usr/share/nginx/html and put in /var/www

```

        root /var/www

```

Then, if there are no typos, reload the configuration file.

```

sudo nginx -t
sudo service nginx reload

```

nginx shouldbe ready to go, serving files from the new location.

---

### Post by ex-para on 2013-10-07
Root remove, sorry but I am unable to find this  /usr/share/nginx/html to change it. There are some that are simular but not the same.

---

### Post by Lars Noodén on 2013-10-07
Right. I don't recall what version he ran in the video, but /usr/share/nginx/html is what I have on 13.10beta.  You might have /usr/share/nginx/www instead.  The part to base your search on is the left-hand column, where it starts with "root" and then is followed with a path.  Whatever the path might be gets swapped out for the new value you provide.

---

### Post by Lars Noodén on 2013-10-07
By the way, it never hurts to make a back up copy of a configuration file before you change it.  It is much easier to restore from a last-known-good copy than to try to work backwards through any changes you might have made.

---

### Post by ex-para on 2013-10-07
As I dont have this computer added to the port forward yet is there anyway I could check if the what has been done is working.

---

### Post by Lars Noodén on 2013-10-07
If you're sitting at the same computer you can access it by going to [http://localhost/](http://localhost/) in your browser.

If you're sitting on the same LAN but not the same computer, you can access it by the local IP address in your browser.  

Once you verify that it is running by either of those methods, you can set up the port forwarding from your external IP for ports 80 (http) and 443 (https).  The https components are off by default, though.  

If you are sitting at the server or else logged in via ssh, you can watch the logs real time while you do your tests.  Open two terminals (or ssh twice) and then run [tail](http://manpages.ubuntu.com/manpages/raring/en/man1/tail.1.html) to watch them.  

```

tail -f /var/log/nginx/access.log

```

and 

```

tail -f /var/log/nginx/error.log

```

The error log should be quiet until there are errors to report...
However, I'm finding my error log suspiciously quiet.

---

### Post by ex-para on 2013-10-07
I think I have trouble as I get 403 Forbidden in local host.

---

### Post by Lars Noodén on 2013-10-07
Just to go through the list,

/var/www should exist, maybe it also has your own version of index.html

/etc/nginx/sites-enabled/default should have a line "root /var/www;"

and the configuration tested and then reloaded in nginx

```

sudo nginx -t && sudo service nginx restart

```

---

### Post by Lars Noodén on 2013-10-07
[403](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) means that the file is there but reading it is not allowed.  Have you set the permissions for /var/www/index.html ?

```

sudo chmod -R u=rwX,g=rwX,o=rX /var/www/

```

Note there is a capital X not a lowercase x.

---

### Post by ex-para on 2013-10-08
I checked it over but apart from the root bit may be i dont know what I am looking for. I did a 12.4 re-install before I installed the latest nginx so instead of forbes I put prince as the password was differant.

So this is what ai have.


# You may add here your
# server {
#       ...
# }
# statements for each of your virtual hosts to this file

##
# You should look at the following URL's in order to grasp a solid understanding
# of Nginx configuration files in order to fully unleash the power of Nginx.
# [http://wiki.nginx.org/Pitfalls](http://wiki.nginx.org/Pitfalls)
# [http://wiki.nginx.org/QuickStart](http://wiki.nginx.org/QuickStart)
# [http://wiki.nginx.org/Configuration](http://wiki.nginx.org/Configuration)
#
# Generally, you will want to move this file somewhere, and start with a clean
# file but keep this around for reference. Or just disable in sites-enabled.
#
# Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
##

server {
        #listen   80; ## listen for ipv4; this line is default and implied
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6

        root /var/www;
        index index.html index.htm;

        # Make site accessible from [http://localhost/](http://localhost/)
        server_name localhost;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to index.html
                try_files $uri $uri/ /index.html;
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules

                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
        }

        location /doc/ {
                alias /usr/share/doc/;
                autoindex on;
                allow 127.0.0.1;
                deny all;
        }

        # Only for nginx-naxsi : process denied requests
        #location /RequestDenied {
                # For example, return an error code
                #return 418;
        #}

        #error_page 404 /404.html;

        # redirect server error pages to the static page /50x.html
        #
        #error_page 500 502 503 504 /50x.html;
        #location = /50x.html {
        #       root /usr/share/nginx/www;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        # 
        #location ~ \.php$ {
        #       fastcgi_split_path_info ^(.+\.php)(/.+)$;
        #       # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
        #
        #       # With php5-cgi alone:
        #       fastcgi_pass 127.0.0.1:9000;
        #       # With php5-fpm:
        #       fastcgi_pass unix:/var/run/php5-fpm.sock;
        #       # With php5-fpm:
        #       fastcgi_pass unix:/var/run/php5-fpm.sock;
        #       fastcgi_index index.php;
        #       include fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #       deny all;
        #}
}


# another virtual host using mix of IP-, name-, and port-based configuration
#
#server {
#       listen 8000;
#       listen somename:8080;
#       server_name somename alias another.alias;
#       root html;
#       index index.html index.htm;
#
#       location / {
#               try_files $uri $uri/ /index.html;
#       }
#}


# HTTPS server
#
#server {
#       listen 443;
#       server_name localhost;

---

### Post by Lars Noodén on 2013-10-08
I'm puzzled that you are getting a 403 error if the permissions for /var/www were set correctly.  Do you mind showing the last few lines of the error log?

```

tail -n 5 /var/log/nginx/error.log

```

And just to double-check what about the file permissions?

```

ls -l /var/www/

```

---

### Post by ex-para on 2013-10-08
prince@prince-Satellite-Pro-2100:~$ 
prince@prince-Satellite-Pro-2100:~$ 
prince@prince-Satellite-Pro-2100:~$ tail -n 5 /var/log/nginx/error.log
2013/10/07 19:02:17 [error] 868#0: *2 rewrite or internal redirection cycle while internally redirecting to "/index.html", client: 127.0.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost"
2013/10/07 19:05:12 [error] 868#0: *3 directory index of "/var/www/" is forbidden, client: 127.0.0.1, server: localhost, request: "GET / HTTP/1.1", host: "localhost", referrer: "http://ubuntuforums.org/showthread.php?t=2175430&page=3"
2013/10/08 10:57:07 [error] 881#0: *1 directory index of "/var/www/" is forbidden, client: 127.0.0.1, server: localhost, request: "GET / HTTP/1.1", host: "localhost"
2013/10/08 10:57:07 [error] 881#0: *1 rewrite or internal redirection cycle while internally redirecting to "/index.html", client: 127.0.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost"
2013/10/08 10:57:07 [error] 881#0: *2 rewrite or internal redirection cycle while internally redirecting to "/index.html", client: 127.0.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost"
prince@prince-Satellite-Pro-2100:~$ ls -l /var/www/
total 0
prince@prince-Satellite-Pro-2100:~$ 

Sorry to be a trouble.

---

### Post by Lars Noodén on 2013-10-08
By default, nginx does not allow visitors to browse directories.  An index file must be provided, usually *index.html* or an access denied error occurs.  

```

 2013/10/08 10:57:07 [error] 881#0: *1 directory index of "/var/www/" is forbidden, client: 127.0.0.1, server: localhost, request: "GET / HTTP/1.1", host: "localhost"

```

That and output from **ls** show that the document root (/var/www/) does not have any file named *index.html*   Its absence is the cause of the error.  

You can make an *index.html* for that directory with [bluefish](http://bluefish.openoffice.nl/), it's in the repository, or hand craft one with gedit, vi, emacs or nano.  Try adding that file and the error should go away when you load the URL again.

---

### Post by ex-para on 2013-10-08
I maybe wrong but I thought that the index.html holds all the files/information regarding the website and in windows notepad is used. In Linux I tried gedit but it was not to good so I used the web libreoffice. The index.html file is among the nginx files and when I open it I get welcome to ngnix. So do I use bluefish to have the editer for index.html and putting my website info in it.

---

### Post by Lars Noodén on 2013-10-08
The contents of *index.html* vary.  At the top, the document root, it is the usual starting point for visitors arriving at your web site.  It holds whatever you decide it should hold for that given directory. For the top level (document root) in your web site, it may well contain information about the site and link to various other files.  In lower directories it will hold something else.  

LibreOffice can also be used to make web pages.  That was a good find.  There are many ways to get an HTML document onto your machine, I tend to use emacs-nox with [tidy](http://manpages.ubuntu.com/manpages/raring/en/man1/tidy.1.html).  

The important thing in this case is that an *index.html* file is present in each of the web server's directories because nginx does not display directory contents by default.  That setting can of course be changed by turning [autoindex](http://nginx.org/en/docs/http/ngx_http_autoindex_module.html#autoindex) **on** for a given directory and its subdirectories.  It's fine to leave it off, though.

---

### Post by ex-para on 2013-10-11
I am not getting to far with nginx server, I can get the localhost without the error although it is a bit different  [B](Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.
For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.
Thank you for using nginx.)[/B]
I was able to get Bluefish OK and I can see what it is, bur I just don't really know what to do with it plus the fact I cant get permissions  for anything. When I last got this site on to internet five years a ago I was able to delete Welcome to Nginx and put all my details in place of the welcome and I was able to edit the site OK when I needed to change it. I think I used Tidy to get a tick on the page to say it had no errors. Have you any more suggestions please.

---

### Post by Lars Noodén on 2013-10-14
In that case I wouldn't worry about Bluefish and would stick with LibreOffice if that is what works.  

About writing to the directory, setting the permissions as suggested above is about all I can think of.

---

### Post by ex-para on 2013-11-14
Finally got the web site working again on another computer. In short I changed the contents of Welcome to Nginx for the contents of my site and nothing else at all.

---

### Post by Lars Noodén on 2013-11-14
Good that it's working.

---

