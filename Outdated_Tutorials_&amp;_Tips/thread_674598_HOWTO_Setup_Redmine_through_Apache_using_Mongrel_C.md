---
title: "HOWTO: Setup Redmine through Apache using Mongrel Clusters"
date: 2008-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by xethm55 on 2008-01-21
I came accross redmine in a search for an integrated content management system for me to use for projects I have in development ( I will refrain from any shameful plugs ).   I had some strict criteria:[LIST]
[*]Needed to integrate well with SVN ( chosen revision control)
[*]Needed to have the following Modules:[LIST]
[*]Wiki
[*]Issue Tracker
[*]User Authentication[/LIST] 
[*]Needed to have a unified theme between all modules[/LIST]I tried many solutions (Mantis, FlySpray, Bugzilla, dokuwiki, pmwiki, TikiWiki, MediaWiki, and more) however none of them seemed to fit the  criteria.  That is until I happen upon RedMine. It was every thing I wanted and more. However I was put off by there not being a lot of guides to setup redmine to work through apache in ubuntu.

So, being that I just went through about a week of trial and error setting up redmine, a content management system, to run on Ubuntu, I decided that I should write a guide on the process for future reference ( I am prone to memory loss ) and for others who desire it.  This is a lengthy guide - I tried to be very detailed - so you might want to set aside a few hours to do this.

First things first lets get the disclaimers out of the way.  I am not in any way responsible for any negative effects this may cause to your computer, you, your walls and/or material possessions, or other people around you.  You follow this guide at your own risk.  I will try to help out when I can and remember to check. 
[SIZE=3][B]
Installation Guide Part I: Redmine, the Basics:[/B][/SIZE]
( Composed from the referenced sites at the bottom )

The following assumes that you have a command line install of Ubuntu [Gutsy], that you want to install redmine in /home/redmine, and have it be the default website apache serves.

Install all the packages needed from the repositories:
```
sudo apt-get install libmysql-ruby mysql-server subversion apache2 ruby rubygems irb ri rdoc ruby1.8-dev build-essential phpmyadmin rake libapache2-mod-fastcgi
```When that command finishes, issue the following command to install Ruby on Rails and Mongrel (this took me a long time to figure out)
```
sudo gem install rails mongrel mongrel_cluster daemons --include-dependencies
```If the installer asks what versions to install, Install the following versions:[LIST]
[*]Rails 2.0.2 (Ruby)
[*]Mongrel Web Server 1.1.3
[*]Mongrel_Cluster 1.0.5
[*]Daemons 1.0.9[/LIST]Once that is complete, we need to create symbolic links in /usr/bin for the mongrel scripts. Assuming that your gems installed in the same location, issue the following commands:

```
sudo ln -s /var/lib/gems/1.8/bin/mongrel_rails /usr/bin/mongrel_rails
sudo ln -s /var/lib/gems/1.8/bin/rails /usr/bin/rails
sudo ln -s /var/lib/gems/1.8/bin/mongrel_cluster_ctl /usr/bin/mongrel_cluster_ctl
```Now that we have access to the scripts (gets rid of that annowing path export !) and ruby on rails is setup, we need to get the latest version of redmine
```
sudo svn co [http://redmine.rubyforge.org/svn/trunk](http://redmine.rubyforge.org/svn/trunk) /home/redmine
```Now that you have the source, you will need to do a little setup in MySQL.  

So fire up phpmyadmin ( You could do this from the command line, but why would you ) by going to the following address in a web browser:
```
http://localhost/phpmyadmin
```(You would need to replace localhost with the server address if you are doing this remotely)
 
From the main phpmyadmin page, go to Privileges, then click on Add New User.

Enter a username (I used redmine) and a password (or generate one) you just need to remember it / write it down

Click on “Create database with same name and grant all privileges”

Click Go ( lower right of page – might need to scoll down ).

Now that we have a dabase created, we need to add that to the redmine configuration.

We need to create a database configuration from the exsisting example file. So, issue the following commands:
```
cd /home/redmin/config
sudo cp database.example.yml database.yml
```Now the database.yml file needs to be edited, so enter the following (you could use any command line editor)
```
sudo nano database.yml
```Change the section (below) so that it reflects the username and database you setup with phpmyadmin
Password also needs to be entered in plain text
```
production:[INDENT]adapter: mysql
database: redmine
host: localhost
username: root
password:[/INDENT]
```so, for example mine looks like this (since I used redmine as user / db):
```
production:[INDENT]adapter: mysql
database: redmine
host: localhost
username: redmine
password: [chosen password][/INDENT]
```Now that we have the database setup and configured, we need to write a base set of tables to it. To do this, issue the following command.
```
sudo rake db:migrate RAILS_ENV="production"
```If the stars aligned properly, this should spit out a bunch of database table creation logs and exit without errors.  
Now those databases need to be populated with default data so issue the following command if the previous one completed successfully:
```
sudo rake redmine:load_default_data RAILS_ENV="production"
```If that completes successfully issue the following command to start the test web server:
```
sudo ruby script/server -e production
```Now, cross your fingers and you should be able to access your new redmine install via:
```
[http://localhost:3000]("http://localhost:3000/")
```Replacing localhost with address of server
The default login information is:
```
Username: admin
Password: admin
```After changing the admin password (Administration->Users), I suggest that you go and create a new account (Administration->Users-New) then logout and log back in with new account.

Then go to Administration->users and lock the admin account.

[SIZE=3]** Installation Guide Part II:  Apache Mongrels**[/SIZE]

Now we need to setup the mongrel clusters for redmine.  From the base redmine install directory (/home/redmine for me) issue the following command:
```
cd /home/redmine
sudo mongrel_rails cluster::configure -e production -p 8000 -N 3 -c /home/redmine --user www-data --group www-data
```This should return that the mongrel cluster was successfully written.  Now that we have a configuration setup, we should attempt to start the mongrel cluster, by issuing the following command (must be within your redmine directory ex /home/redmine):
```
sudo mongrel_rails cluster::start
```You should see that mongrel cluster was started on ports 8000,8001,8002.  At this point, you should be able to access the redmine install at 
```
[http://localhost:8000]("http://localhost:8000/")
```Now for the fun part, setting up apache to work with redmine. 

Apache needs to be able to read and write files in the redmine install.  Changing the ownership of the files will accomplish this, so issue the following command:
```
sudo chown -R www-data:www-data /home/redmine
```Since the user and group apache uses is www-data.  Now  the .htaccess file in the redmine/public folder needs to be setup.  Issue the following commands (assuming  you are still in your redmine directory):

```
cd /home/redmine/public
sudo nano .htaccess
```Replace this whole file with the following ( worked for me atleast ):
```
# General Apache options
AddHandler fastcgi-script .fcgi
AddHandler fcgid-script .fcgi
AddHandler cgi-script .cgi
Options +FollowSymLinks +ExecCGI

RewriteEngine On
RewriteRule ^$ index.html [QSA]
RewriteRule ^([^.]+)$ $1.html [QSA]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ dispatch.fcgi [QSA,L] 

ErrorDocument 500 "<h2>Application error</h2>Rails application failed to start properly"

```Save and exit.  This is the original file with all the if statements removed and only the sections that are needed left.  Now that we have a presumably working .htaccess file, we need to modify the apache configuration. Go to the apache2 configuration directory and open apache2.conf, by issuing the following commands:
```
cd /etc/apache2
sudo nano apache2.conf
```With apache2.conf open, we need to modify the following two lines (located about half way through the file around line 180):
```
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
```Change the two include lines to be:
```
# Include module configuration:
Include /etc/apache2/mods-available/*.load
Include /etc/apache2/mods-available/*.conf
```This is not really preferred, since it loads all the apache modules, however, I did not want to go through the process of elimination to find the correct ones to enable. 
Now we need to create a new site.  So go into the sites available and modify the default site.  Issue the following command:
```
cd /etc/apache2/sites-available
sudo nano default
```Replace the contents of this file with the following:
```
<VirtualHost *>[INDENT]ServerAdmin email@example.com
ServerName redmine.example.com
ServerAlias example.com

RewriteEngine On

# Redirect all non-static requests to cluster
RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f
RewriteRule ^/(.*)$ balancer://redminecluster%{REQUEST_URI} [P,QSA,L]
[/INDENT]</VirtualHost>

<Proxy balancer://redminecluster>[INDENT]BalancerMember [http://127.0.0.1:8000]("http://127.0.0.1:8000/")
BalancerMember [http://127.0.0.1:8001]("http://127.0.0.1:8001/")
BalancerMember [http://127.0.0.1:8002]("http://127.0.0.1:8002/")
[/INDENT]</Proxy>
```Save and exit.  Now we need to open the proxy up to requests.  To do this, we need to edit the proxy.conf file in the mods-available directory. So, issue the following commands;
```
cd /etc/apache2/mods-available
sudo nano proxy.conf
```The following lines (around line 9 ) need to be modified.
```
Order deny,allow
Deny from all
```The lines need to be modified to the following:
```
Order allow,deny
Allow from all
```Save and exit.  Again, this is not a preferred way of doing things,  This should be modified to only allow connections from apache to redmine, I did not want to take the time to do that.  Now, apache should be all setup.  Apache needs to be restarted to get it working, so issue the following command:
```
sudo /etc/init.d/apache2 restart
```Hopefully you should see that the restart went ok.  If that is the case, you should be able to access redmine remotely in a web browser.  Now, if the planets align and you wish really hard, You should see redmine appear when browsed to the server without specifying the port.

[SIZE=3]** Installation Guide Part III: The Reboot**[/SIZE]

There is one more problem, the setup will not work if the computer is restarted unless you start the mongrel cluster manually.  To a get mongrel to start at boot, we need to link redmine’s configuration for the cluster in /etc/mongrel_cluster.  To do this, issue the following commands:
```

sudo mkdir /etc/mongrel_cluster
cd /etc/mongrel_cluster
sudo ln -s /home/redmine/config/mongrel_cluster.yml /etc/mongrel_cluster/redmine.yml
```Doing an:
```
ls -al
```should show that you now have a symbolic link to redmines mongrel cluster configuration.   
Now, we need to copy over the mongrel startup script to init.d  to do this, issue the following commands:
```
cd /etc/init.d
sudo cp /var/lib/gems/1.8/gems/mongrel_cluster-1.0.5/resources/mongrel_cluster /etc/init.d/
sudo chmod +x /etc/init.d/mongrel_cluster
```Now that we have the init script we need to tell it to boot on startup.  To do the issue the following command:
```
sudo /usr/sbin/update-rc.d -f mongrel_cluster defaults
```That should be it.  Mongrel_cluster and redmine should startup on boot, automagically.

[SIZE=3]** References:**[/SIZE][INDENT][COLOR=Blue][http://www.redmine.org/wiki/redmine/HowTo_run_Redmine_with_a_Mongrel_cluster](http://www.redmine.org/wiki/redmine/HowTo_run_Redmine_with_a_Mongrel_cluster)
[http://mongrel.rubyforge.org/docs/mongrel_cluster.html](http://mongrel.rubyforge.org/docs/mongrel_cluster.html)
[http://www.redmine.org/wiki/redmine/RedmineInstall](http://www.redmine.org/wiki/redmine/RedmineInstall)
[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)
[http://www.redmine.org/wiki/redmine/Download](http://www.redmine.org/wiki/redmine/Download)
[http://wiki.rubyonrails.org/rails/pages/RailsOnCentos5](http://wiki.rubyonrails.org/rails/pages/RailsOnCentos5)
[http://rubyforge.org/forum/message.php?msg_id=27821](http://rubyforge.org/forum/message.php?msg_id=27821)
[http://bitnami.org/stack/redmine]("http://bitnami.org/")[/COLOR]       

[/INDENT]-xethm55

---

### Post by yawnster on 2008-09-18
Hey bud,

I followed your guide, the installation works fine over port 8000 directly, however I am not sure what to do with the /etc/apache2/sites-available/default file.. Currently I have SVN setup in there, I also want to keep a normal webserver running also.. thus I have tried this..

```
NameVirtualHost *

<VirtualHost *>
        ServerName  www.octogo.co.uk
        ServerAlias     octogo.co.uk
        ServerAdmin admin@octogo.co.uk

        DocumentRoot /home/alex/Webserver
        <Directory />
                Options FollowSymLinks
                AllowOverride Nonehttp://192.168.1.2:8000/
        </Directory>
        <Directory /home/alex/Webserver/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/chttp://192.168.1.2:8000/gi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

<VirtualHost *>

        ServerAdmin admin@octogo.co.uk 
        ServerName dev.octogo.co.uk
        RewriteEngine On 

        # Redirect all non-static requests to cluster
        RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f 
        RewriteRule ^/(.*)$ balancer://redminecluster%{REQUEST_URI} [P,QSA,L] 

</VirtualHost>

<Proxy balancer://redminecluster>

        BalancerMember http://127.0.0.1:8000 
        BalancerMember http://127.0.0.1:8001 
        BalancerMember http://127.0.0.1:8002 

</Proxy>


<Location /svn>
     DAV svn
     SVNParentPath /var/subversion/
     AuthType Basic
     AuthName "GLMWNetwork subversion repository"
     AuthUserFile /etc/subversion/passwd
     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
  </Location>

```

The www. root works, but the dev. does not.. And I am unsure of how to progress now.. 

I can go to 192...2:8000 and it will produce a working copy of redmine.. But going to dev.octogo.co.uk produces a dead page..

As you may have guessed I am by no means an expert apache user.. Sorry :(

Thanks in advance for any suggestions, Alex.

---

### Post by Titan8990 on 2008-10-01
I know this is a bit late but you can make two virtual hosts on the same website page like that. In any other distro (you would be configuring httpd.conf) and that would be fine but debain and its children are a bit different.

You must make a second file in /etc/apache2/sites-available. Then you need to put the information supplied in it.

After that create a symbolic link from that file to /etc/apache2/sites-enabled.

Restart apache and your virtual server should be up and running.


Also, want to give a thanks to the OP. I struggled with getting my Redmine site up for quite a while before finding this guide. It is rock solid. I was too late to click the "thanks".

Too bad a couple days ago my boss said "I want this to run in IIS where I'm confortable." So now my rock solid Redmine site is going to be a flaky piece of crap.

---

### Post by bwilhiteforex on 2008-10-08
When I go to do rake, I get this message:

rake aborted!
/home/redmine/config/environment.rb:12: syntax error, unexpected tCONSTANT, expecting kDO or '{' or '('
require File.join(File.dirname(__FILE__), 'boot')

Any idea how to fix it?  I think that maybe this has something to do with the symlinks we installed...?

---

### Post by xethm55 on 2008-10-09
bwilhiteforex:
I do not think it has to do with the symlinks.  I would say it is an actual error in the environment.rb file.  I would suggest doing
```
svn update
```
in the /home/redmine directory

---

### Post by psynode on 2008-10-09
A few things i noticed, i wouldnt bother with the gems for alot of redmine dependencies i would just install:

```
apt-get install rails mongrel mongrel-cluster
```
Then create your mongrel cluster:
```
cd /path/to/redmine
sudo mongrel_rails cluster::configure -e production -p 8000 -N 3 -c /path/to/redmine --user www-data --group www-data
mv /path/to/redmine/config/mongrel_cluster.yml /etc/mongrel-cluster/sites-enabled/redmin.domainname.com.yml

```
then just restart the mongrel cluster using:
```
 /etc/init.d/mongrel-cluster restart 
```

A better way to do the apache configuration is by using proxypass, you will need the following modules enabled in apache2 using the following commands:

```
a2enmod proxy
a2enmod proxy_http
a2enmod proxy_balancer
```

and the apache configuration:

```
<VirtualHost *:80>
    ServerAdmin [email]webmaster@somedomain.com[/email]
    ServerName redmine.sitesuite.net
    ErrorLog /var/log/apache2/redmine.domain.com.error.log
    LogLevel warn

    CustomLog /var/log/apache2/redmine.domain.com.access.log combined
    ServerSignature On
    <Proxy balancer://redmine>
        BalancerMember [http://127.0.0.1:8001](http://127.0.0.1:8001) keepalive=on max=2 retry=30
        BalancerMember [http://127.0.0.1:8002](http://127.0.0.1:8002) keepalive=on max=2 retry=30
        BalancerMember [http://127.0.0.1:8003](http://127.0.0.1:8003) keepalive=on max=2 retry=30
        BalancerMember [http://127.0.0.1:8004](http://127.0.0.1:8004) keepalive=on max=2 retry=30
        BalancerMember [http://127.0.0.1:8005](http://127.0.0.1:8005) keepalive=on max=2 retry=30
    </Proxy>
    <Location />
        SetHandler balancer-manager
        Order allow,deny
        Allow from all
    </Location>
    ProxyPass / balancer://redmine/
    ProxyPassReverse / balancer://redmine/
    ProxyPreserveHost on
</VirtualHost>
```

---

### Post by ikarus2k on 2008-11-15
A few sidenotes:

1. Don't forget to grant privileges to the database user - redmine (I had to do it manually) when creating

2. At *sudo rake db:migrate RAILS_ENV="production"*, I got this error:
*no such file to load -- openssl*

After installing libopenssl-ruby (as indicated [here]("http://www.redmine.org/boards/2/topics/show/1366#message-1384")), it went fine:
```
sudo apt-get install libopenssl-ruby
```

---

### Post by mojoguy on 2008-12-27
Many thanks to xethm55 and the others who have posted to this thread.  I have used it several times now to install and set up redmine (first on VMs, then on dedicated hardware).  I never could have done it without you!

Each time it gets a wee bit easier.

Thanks again!

---

### Post by mojoguy on 2008-12-28
Anyone have any recommendations for setting up Redmine to receive and process emails?  

I have a Redmine email account set up on our Exchange server.  Redmine uses this account to send emails.  Curious about how to set Redmine up to receive emails.  

I have no access to the exchange server besides setting up the email account.  

Thoughts?

---

### Post by icecaster on 2009-01-23
im having problems getting my svn repos running in a subfolder....

my apache conf looks as follows




```

<VirtualHost *:80>

PerlLoadModule Apache::Redmine

    <Location /svn>
	SetHandler None
    	DAV svn
   	SVNParentPath /home/subversion
    	AuthType Basic
    	AuthName SVN
  	Require valid-user

	PerlAccessHandler Apache::Authn::Redmine::access_handler
	PerlAuthenHandler Apache::Authn::Redmine::authen_handler

	RedmineDSN "DBI:mysql:database=redmine;host=localhost" 
	RedmineDbUser "root" 
	RedmineDbPass "pass" 

    </Location>

    <Location /svn-private>
    	DAV svn
    	SVNParentPath "/home/subversion" 
	SVNListParentPath on
    	Order deny,allow
    	Deny from all
    	# only allow reading orders
    	<Limit GET PROPFIND OPTIONS REPORT>
    	  #Allow from localhost
	Allow from All
    	</Limit>
    </Location>

    <Proxy balancer://redmine>
        BalancerMember http://127.0.0.1:8001 keepalive=on max=2 retry=30
        BalancerMember http://127.0.0.1:8002 keepalive=on max=2 retry=30
        BalancerMember http://127.0.0.1:8003 keepalive=on max=2 retry=30
    </Proxy>
    <Location />
       SetHandler balancer-manager
       Order allow,deny
       Allow from all
       ProxyPass  balancer://redmine/
       ProxyPassReverse  balancer://redmine/
   </Location>

</VirtualHost>

```


When i comment "ProxyPass" svn works fine 
when its uncommented redmine goves me a 404-error

any ideas?

---

### Post by frostbite7217 on 2009-02-27
I'm having trouble getting the rails app to load on boot.  After following the instructions to the letter, I am able to start and stop the mongrel_cluster with 'sudo /etc/init.d/mongrel_cluster start' and 'stop' but after loading them into update-rc.d, it does not start on boot.  I have updated /etc/init.d/mongrel_cluster to add the path before the conf dir, and I have tried changing it to various users including root, and www-data.  I have also setup the mongrel user that is originally has defined.  I have verified permissions on the conf directory and on the pid directory.

Is there something I am missing here?

---

### Post by 4tro on 2009-03-26
be sure to have a look at passenger (mod_rails)
[http://www.modrails.com/](http://www.modrails.com/)

you can start using it from the point where you're done installing redmine,
and after that you won't need the proxy entries in apache vhosts.
only point the vhost to the public directory of redmine

also mongrel and mongrel_cluster and daemon from the gem install aren't needed then

post your experiences, because i'm curious how this works for other people

=)

---

### Post by CR34M3 CR4CK3R on 2009-04-15
After struggling for a while with the mongrel clusters I decided to give it a skip and try Passenger. After a little bit of modding I now have my wiki (MediaWiki powered) and redmine running on the same Apache2 server.

Good call I think. ;)

Thanks to 4tro for mentioning passenger.

---

### Post by shahjapan on 2009-04-24
Following URL might help you out,

to setup the redmine on ubuntu.....

[http://www.drinkingbird.net/blog/articles/2008/02/27/setting-up-a-redmine-site-on-ubuntu](http://www.drinkingbird.net/blog/articles/2008/02/27/setting-up-a-redmine-site-on-ubuntu)

---

