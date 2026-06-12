---
title: "php5 problem?"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by freddo63 on 2013-02-20
I reckon this is a fairly specific problem, so I'm opening a new thread, and so far I haven't seen anything that applies to me since I'm not on a server. I tried to open the following link [http://novoportal.celesc.com.br/portal/](http://novoportal.celesc.com.br/portal/) and I get the following warning

Warning: require_once(/srv/www/htdocs/portal/libraries/import.php):  failed to open stream: No such file or directory in  /srv/www/htdocs/portal/includes/framework.php on line 45  Fatal error: require_once(): Failed opening required  '/srv/www/htdocs/portal/libraries/import.php'  (include_path='.:/usr/share/php5:/usr/share/php5/PEAR') in  /srv/www/htdocs/portal/includes/framework.php on line 45 

I was able to access this site only moments before. I've just updated java through apt-get and am not sure if that has affected it. On a side-note I was updating Java because a dialog box popped up and told me that my java version was insecure, and asked me whether I wanted to block it, update it, or to remind me later. Is this normal on Ubuntu? I'm new to Ubuntu, and am a little unsure of how safe it is, in terms of having everything updated properly and whether or not I can get "hacked." I'm only concerned because I recently had some bank account issues (which had nothing to do with my computer or Ubuntu), so now I want to make sure I'm playing on the safe side. 

Also I've got Ubuntu 12.04

---

### Post by rushikesh988 on 2013-02-20
I am not good at server platforms but it seems that your import.php file is lost try 
> touch /srv/www/htdocs/portal/libraries/import.php 
and also check if the specified path is correct or not (I mean that folders.

if it says not found 
then try to copy that file **import.php**(which you might have in your project ) to that folder .

---

### Post by freddo63 on 2013-02-20
Like I said I'm not on a server, just my own personal laptop for personal use. I tried the touch command, but it said no such file or directory. I have no idea where I would get said import.php file because I don't have any "project." is this a server side problem? As in, the server which hosts the site I'm trying to access had the problem? Because it seems to have resolved on its own. However, I would like to know whether these kinds of things can ever be on the client side (such as my personal laptop) as opposed to server side (the site of which I'm trying to access, as shown from the link).

---

