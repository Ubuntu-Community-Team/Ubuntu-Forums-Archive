---
title: "AWS Joomla installation"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by Dave_Metzler on 2014-05-16
I am attempting to install Joomla on an instance of Ubuntu Tasty 14.04. I have tried several tutorials to arrive at this point. 
I have installed Apache and when I enter the public DNS I am greeted with the default page. 
I have installed (correctly I think) Joomla at /var/www/joomla (directions in this video with some modification for 14.04 ([https://www.youtube.com/watch?v=ZzDG45AbCWE](https://www.youtube.com/watch?v=ZzDG45AbCWE))
I have accessed myphpadmin and added users per the video directions.
I have copied /etc/apache2/sites-available **000-default.conf** and placed a file in the same folder called **joomla.conf**
    I have a feeling this is wrong

I attempt to go to my DNS/joomla and get 
[h=1]Not Found[/h][COLOR=#000000][FONT=Times New Roman]The requested URL /joomla was not found on this server.[/FONT][/COLOR]
[HR][/HR][FONT=Times New Roman][SIZE=3][COLOR=#000000]Apache/2.4.7 (Ubuntu) Server at ec2-54-186-28-232.us-west-2.compute.amazonaws.com Port[/COLOR][/SIZE][/FONT]




[B]see attachment for /var/www/joomla setup

see attachment for AWS security group



[/B][FONT=arial][SIZE=3][COLOR=#000000] would appropriate any help here. absolute beginner probably isn't a simple enough description of my understanding[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=arial] of this stuff




[/FONT][/COLOR][ATTACH=CONFIG]253223[/ATTACH]
[ATTACH=CONFIG]253224[/ATTACH]

---

### Post by kira_belka2 on 2014-05-16
Hi..
well.. 
is apache started?
post output of > service apache2 status
next one.
remove your "joomla"config.
Look if you 'll just copy unmodifiled default.conf. 
you 'll get just duplicate of your default.host.
you have to edit your joomla.conf in following maniere:
first, set server name. set root directory. 
and it's no good idea to create one vhost in root directory of another vhost.

---

### Post by Habitual on 2014-05-18
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/joomla.conf

edit /etc/apache2/sites-available/joomla.conf and use *something like* this:
```
<VirtualHost *:80>
ServerName 
ServerAdmin email@domain.com
ServerAlias www.domain.com

DocumentRoot /var/www/joomla/
    <Directory /var/www/joomla/>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

test syntax in /etc/apache2/sites-available/joomla.conf with
```
apache2ctl -S
```
if it says "Syntax OK" then restart apache2
```
service apache2 restart
```

If all goes well, navigate to [http://ec2-54-186-28-232.us-west-2.compute.amazonaws.com/joomla](http://ec2-54-186-28-232.us-west-2.compute.amazonaws.com/joomla)
If not, read carefully the "a2" commands (and follow their links for more info) at [http://ec2-54-186-28-232.us-west-2.compute.amazonaws.com/](http://ec2-54-186-28-232.us-west-2.compute.amazonaws.com/)
```
They are activated by symlinking available configuration files from their respective *-available/ counterparts. These should be managed by using our helpers a2enmod, a2dismod, a2ensite, a2dissite, and a2enconf, a2disconf . See their respective man pages for detailed information. 

```

Please let us know.

---

### Post by jt_wdrw on 2014-12-27
i had to install joomla to   
var/www/html/joomla        
to not see the connection page

---

