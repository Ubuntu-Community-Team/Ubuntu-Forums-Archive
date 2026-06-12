---
title: "How To: Install torrentflux-b4rt on Hardy 8.04"
date: 2008-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by delta4000 on 2008-07-03
[FONT="Arial"]This tutorial is for Hardy Heron 8.04 Server and aims to get you up and running with a torrentflux-b4rt server in a very short time!

Start by installing Ubuntu with the **LAMP **option selected

```
cd /var/www 
```
If your behind a proxy and havn't already set up your export...
```
export http_proxy = [enter your proxy here]:[port]/
```
```
wget http://gunblade.fakap.net/doc/torrentflux-b4rt_1.0-beta2.tar.bz2
```
So, so far we've gone and got the tar containing torrentflux-b4rt and stuck it in our default web root /var/www.

```
tar xjvf torrentflux-b4rt_1.0-beta2.tar.bz2
```

This unzips our archive.
personally I now rename the new folder from 
*torrentflux-b4rt_1.0-beta2*to something a little nicer like *torrentflux*
```
mv torrentflux-b4rt_1.0-beta2 torrentflux
```
 but thats optional...

now we need to install quite a few libraries for everything to work nicely...
```
sudo apt-get install php5-cli php5-gd libxml-dom-perl libxml-simple-perl libthreads-shared-perl libdigest-sha1-perl libhtml-parser-perl zip unzip unrar transmission-cli phpmyadmin
```

let that churn away for a bit then run setup.php from a web browser of your choice from the torrentflux/html folder.

When it gets the part where it asks what user name and password to use for the database, copy the username provided (or enter a new one) open a new tab and go to the phpmyadmin page ([http://[your](http://[your) box ip]/phpmyadmin), log in using your root username and pwd and click on privileges. add a new user, give it sufficient privileges and click save. 

I just gave it full access to everything. This isn't required and you can just keep flicking between the two tabs trying to connect until you've found the required permissions and it works...

when the setup is finished it'll give you a log in screen. the user and password you enter here is going to be your superadmin account! so don't forget it!

And thats it!
[/FONT]

---

### Post by FireFreek on 2010-08-17
I tried this on both 8.10 and 10.04, and i always get stuck at the part where you have to go to the phpmyadmin page. There is no phpmyadmin page or directory in the /var/www folder. Does anyone know why?

---

### Post by steve2112 on 2010-08-19
you have to create it

---

### Post by aliasmcname on 2010-08-21
This will install phpmyadmin for you:

```
sudo apt-get install phpmyadmin
```If you then point your browser at > http://<machinename>/phpmyadmin you will be able to use the interface to manage a mysql installation.

Oh, and the reason you won't see a phpmyadmin directory is that there is an html-rewrite that catches all requests to that imaginary directory

-Alias

---

### Post by CycleGeek on 2011-07-30
I'm having some vexing issues trying to get torrentflux-b4rt to download anything.  For some reason the only status when I start a torrent is

Connecting to Peers

I'm pretty sure I opened up the ports on my router - but for some reason I think BitTornado isn't doing anything.

---

