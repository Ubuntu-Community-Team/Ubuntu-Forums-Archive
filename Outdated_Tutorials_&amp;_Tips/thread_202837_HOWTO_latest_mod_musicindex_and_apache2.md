---
title: "HOWTO: latest mod_musicindex and apache2"
date: 2006-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by duffydack on 2006-06-24
This applies to most versions of ubuntu.  If there are issues with older versions, let me know.
(This is from scratch)

First off, install apache2 and its headers
sudo apt-get install apache2 apache2-threaded-dev

install needed headers for audio support
sudo apt-get install libmad0-dev libid3tag0-dev libogg-dev libvorbis-dev libflac-dev libarchive-dev

get latest mod_musicindex source (as of this howto it is 1.2.5)
wget [www.parisc-linux.org/~varenet/musicindex/mod_musicindex-1.2.5.tar.gz](www.parisc-linux.org/~varenet/musicindex/mod_musicindex-1.2.5.tar.gz)

tar xvf mod_musicindex-1.2.5.tar.gz
cd mod_musicindex-1.2.5
sudo ./configure
sudo make install

sudo pico /etc/apache2/httpd.conf 
and add the following line then close/save
LoadModule musicindex_module /usr/lib/apache2/modules/mod_musicindex.so

some files need to be accessible under "/musicindex" on the webserver and the README says you can add an alias in apache to do this, but its never worked for me so i do this method instead.  Just remember you need to do this whenever you upgrade the module in case somethings changed
  
#remove older version if you have one, first.
sudo rm -rf /var/www/musicindex

sudo cp -R /usr/local/share/mod_musicindex /var/www/musicindex

sudo pico /etc/apache2/sites-enabled/000-default
scroll to the bottom and find </VirtualHost> and copy and paste these lines starting directly above it, save and close

Alias /music "/home/duffydack/music"
<Directory "/home/duffydack/music">
    Options		Indexes MultiViews FollowSymlinks
    AllowOverride	Indexes
# Can be overriden in .htaccess
    MusicIndex		On +Stream +Download +Search -Rss -Tarball
    MusicSortOrder      album disc track artist title length bitrate freq filetype filename uri
    MusicFields		title artist album length bitrate
    MusicPageTitle	MusicPage
    MusicDefaultCss	musicindex.css
# Can only be set in apache configuration
    MusicDefaultDisplay	HTML
    MusicIndexCache	file://tmp/musicindex
    MusicIceServer	[ice.domain.my]:8000
    MusicCookieLife	300
    MusicDirPerLine	3
</Directory>


Obviously replace /home/duffydack/music to where-ever your music is.

Next, its advisable to change the port apache2 is using.
sudo pico /etc/apache2/ports.conf
change 80 to something else,  77 for example.  Save and close

sudo /etc/init.d/apache2 restart
now try it out.  [http://localhost/music/](http://localhost/music/)
or if you changed the port ie: [http://localhost:77/music/](http://localhost:77/music/)

[B]Password protecting your site
------------------------------[/B]
sudo htpasswd2 -c /etc/apache2/passwords duffydack
of course change "duffydack" to something you want.
enter a password when prompted

sudo pico /etc/apache2/sites-enabled/000-default
at the top with the /var/www directives, you want it to look like this

DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride AuthConfig
		AuthType Basic
		AuthName "Restricted Access"
		AuthUserFile /etc/apache2/passwords
		Require user duffydack  
	</Directory>
	

sudo /etc/init.d/apache2 restart
and test it.

---

### Post by duffydack on 2006-07-02
**Installing ICECAST to handle streaming.  Good for setting limits on listeners if you have low upstream, and using with HTTPS**

sudo apt-get install icecast2

now edit the icecast.xml file
sudo pico /etc/icecast2/icecast.xml

at the top you`ll see
<clients>100</clients>
set it to 1 or 2 or however many listeners you`d like.

scroll down a bit and find <authentication>

now set better passwords than whats there.  "hackme" isnt the best to have!

<authentication>
        <source-password>hackme</source-password>
        <relay-password>hackme</relay-password>
        <admin-user>admin</admin-user>
        <admin-password>hackme</admin-password>
    </authentication> 

now find <hostname>localhost</hostname>  and change localhost to the hostname of your computer.

directly underneath <hostname> you`ll see where to set the port to use, looks like this.
I personally use 8001 rather than the default 8000.  Set it as the first port like so.  Leave this part totally if you want to use 8000.

    <!-- You may have multiple <listener> elements -->
    <listen-socket>
        <port>8001</port>
        <!-- <bind-address>127.0.0.1</bind-address> -->
        <!-- <shoutcast-mount>/stream</shoutcast-mount> -->
    </listen-socket>
    <!--
#    <listen-socket>
#        <port>8001</port>
#    </listen-socket>
#    -->

 
now save/exit

make a link to your mp3`s for icecast to use like this
cd /usr/share/icecast2/web
sudo ln -s /home/duffydack/music/ music

now edit apache site config and add your icecast server details like this
sudo pico /etc/apache2/sites-enabled/000-default

scroll to bottom where you have (similar to) this, and set **MusicIceServer** option.

Alias /music "/home/duffydack/music"
<Directory "/home/duffydack/music">
Options Indexes MultiViews FollowSymlinks
AllowOverride Indexes
# Can be overriden in .htaccess
MusicIndex On +Stream +Download +Search -Rss -Tarball
MusicSortOrder album disc track artist title length bitrate freq filetype filename uri
MusicFields title artist album length bitrate
MusicPageTitle MusicPage
MusicDefaultCss musicindex.css
# Can only be set in apache configuration
MusicDefaultDisplay HTML
MusicIndexCache file://tmp/musicindex
**MusicIceServer :8000**
MusicCookieLife 300
MusicDirPerLine 3
</Directory>

:8000 means the icecast server is on the same computer as the webserver, using port 8000.  If its not, then change it to the hostname:port of your icecast2 server.  eg: server:8000 or server:8001

To allow icecast to be started you need to enable the service like so.
sudo pico /etc/default/icecast2
At the bottom, change Enabled=false to Enabled=true
save/exit

restart your apache and icecast to let the changes take effect
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/icecast2 restart

---

### Post by teet on 2006-07-04
>  sudo cp &#8211;R /usr/local/share/mod_musicindex /var/www/musicindex 

This command doesn't work for me as I do not have a folder called mod_musicindex in /usr/local/share.  Also, I don't have a folder named musicindex in /var/www.

I think this is the only thing holding me back from getting it to work.  Thanks in advance for your help.

-teet

Edit:  Figured it out...the dash on the -R was wrong...something screwed up when copying & pasting.

---

### Post by teet on 2006-07-04
New Problem.

> 
Forbidden

You don't have permission to access /music/ on this server.
Apache/2.0.55 (Ubuntu) mod_musicindex/1.0.2 Server at localhost Port 80


I now get this error message when I open up firefox and go to localhost/music (I am on localhost right now).

-teet

---

### Post by duffydack on 2006-07-05
[QUOTE=teet]New Problem.

I now get this error message when I open up firefox and go to localhost/music (I am on localhost right now).

-teet[/QUOTE]

obvious question, do you have permissions to the music folder in general?  have to ask!
Are you setting this up with or without user/pass protection?  Icecast or not..  attach your apache site config if you like

---

### Post by duffydack on 2006-07-05
.

---

### Post by PoisoN2003 on 2006-07-05
Great Tut thx man i love it :)
but how can i change the look of the streaming music?
(the html page) maybe change colors and stuff or get a diffrent template

---

### Post by duffydack on 2006-07-05
[QUOTE=PoisoN2003]Great Tut thx man i love it :)
but how can i change the look of the streaming music?
(the html page) maybe change colors and stuff or get a diffrent template[/QUOTE]

the musicindex folder thats in /var/www (if you used my tut to the full) has files for editing.

---

