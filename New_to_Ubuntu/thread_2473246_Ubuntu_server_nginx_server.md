---
title: "Ubuntu server nginx server"
date: 2022-03-29
forum: New to Ubuntu
---

### Post by comspiracies on 2022-03-29
Right I've started to use ubuntu server to begin a website. I've installed nginx server a and if I log in to my ubuntu  server and type in IP I get a sourse file basic web page but on my windows laptop via browe nothing..I've uninstalls nginx and tryed apache2 same thing can't show index page.. Do you need nginx or apache2 to run a website while using unbuntu server? Is so I want to use nginx as I hear its better.. ... I've ufw allow full and tried http/https plus port 80 and port forwarded 443 and 80 .. I also have reset firewall before and disabled to try work out problem &#128515;

---

### Post by comspiracies on 2022-03-29
I've also looked at lemp and lamp tutorials

---

### Post by QIII on 2022-03-29
Are you running this internally on a LAN?  Do you have an off-site dedicated server?  A virtual private server?

What instructions/tutorials did you use to set up your LEMP server?

---

### Post by TheFu on 2022-03-29
> **comspiracies said:**
> Right I've started to use ubuntu server to begin a website. I've installed nginx server a and if I log in to my ubuntu  server and type in IP I get a sourse file basic web page but on my windows laptop via browe nothing..I've uninstalls nginx and tryed apache2 same thing can't show index page.. Do you need nginx or apache2 to run a website while using unbuntu server? Is so I want to use nginx as I hear its better.. ... I've ufw allow full and tried http/https plus port 80 and port forwarded 443 and 80 .. I also have reset firewall before and disabled to try work out problem &#128515;

Either nginx or apache work fine, but you have to configure the site to allow non-local clients.  This is a security thing.
The files for each various http named server are in /etc/{web-server}/sites-available/

nginx uses the 'allow' line (it has to be placed correctly) in the per-site config file.

apache has a few different techniques.
```
                Order allow,deny
                allow from all

```
is one. 
For an internal website here, I have:
```
        <Directory /export/www/vhosts/nepal/ >
                Options +Indexes +FollowSymLinks +MultiViews +Includes
                AllowOverride None
                [B]Order allow,deny
                allow from all
[/B]                DirectoryIndex index.html
        </Directory>
```
Simple. It is a little photo gallery for use by the family using CGI.
The 
```
        <RequireAny>
....
        </RequireAny>
```
block is another.  Which makes more sense depends whether you are trying to whitelist remote access or allow the world.  My nextcloud server is LAN-only, so it is the whitelist type:
```
        <RequireAny>
               Require ip 10.1.10
               Require ip 172.22.22
               Require ip 172.22.21
               Require all granted
        </RequireAny>

```
I have a few subnets at home and don't want the world to have access.

There are 20,000 websites with other examples on the internet. Just be certain to look at examples for the version of the web server you are using.  apache.org is anther location, especially if the apache version isn't the latest (Ubuntu never provides the latest), so reading the documentation for specific versions is very helpful if you need that detail level.

---

### Post by comspiracies on 2022-03-30
I'm running the Ubuntu server 20.4 I believe on my hp z400

---

### Post by comspiracies on 2022-04-01
Hmmm&#8230; 

can't reach this page

```
The connection was reset.
Try:


Checking the connection
[Checking the proxy and the firewall]("https://ubuntuforums.org/chrome-error://chromewebdata/#buttons")
Running Windows Network Diagnostics

ERR_CONNECTION_RESET
```

can anyone help

---

### Post by TheFu on 2022-04-01
> **comspiracies said:**
> [h=1]Hmmm… can't reach this page[/h][COLOR=#101010][FONT=system-ui]The connection was reset.[/FONT][/COLOR]
[COLOR=#101010][FONT=system-ui][/FONT][/COLOR][COLOR=#101010][FONT=system-ui][COLOR=var(--edge-primary-text-color)]Try:[/COLOR]

[LIST]
[*]Checking the connection
[*][Checking the proxy and the firewall]("https://ubuntuforums.org/chrome-error://chromewebdata/#buttons")
[*]Running Windows Network Diagnostics
[/LIST]

[COLOR=var(--edge-secondary-text-color)]ERR_CONNECTION_RESET[/COLOR]

[/FONT][/COLOR]
can anyone help

I don't have any idea what this is about. When posting, please provide context.

---

### Post by comspiracies on 2022-04-06
I've used lemp and i have a HP z400 workstation as a install

---

### Post by comspiracies on 2022-04-06
Is there a file or something i need to do i cant get pass the nginx part..to carry on the Kemp install..

---

### Post by TheFu on 2022-04-06
Look at the log files for each part of the stack.  They are usually in /var/log/ somewhere.

---

