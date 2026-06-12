---
title: "Integrate Bugzilla, SVN and MediaWiki"
date: 2010-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by jucas_lo on 2010-02-03
This integration has been done based on the guides posted on [http://oss.segetech.com/bugzilla-svn-wiki.html]("http://oss.segetech.com/bugzilla-svn-wiki.html") . Then to handle common authentication i'm using the guides posted in [http://www.serdarbulut.com/2008/11/mediawiki-and-apache-authentication-integration.html]("http://www.serdarbulut.com/2008/11/mediawiki-and-apache-authentication-integration.html ") and [ http://www.raskas.be/blog/2006/11/17/mediawiki-remote-user-authentication/comment-page-1/ ]("http://www.raskas.be/blog/2006/11/17/mediawiki-remote-user-authentication/comment-page-1/"). 

The installation assumes a Linux PC with Ubuntu 9.04 

**[SIZE="4"]Dependencies[/SIZE]**

Install the following packages from the repositories using synaptic or apt-get 

 ```
apache2-prefork
 apache2-prefork-dev
 libmysqlclient15-dev
 mysql
 subversion
 mediawiki
 viewvc
 perl
 libapache2-mod-php5
 libapache2-svn
 imagemagick 
```

Download bugzilla from [http://www.bugzilla.org/download/#oldstable]("http://www.bugzilla.org/download/#oldstable") , we need version 3.0.x since we are going to apply some patches that only work with this version. 

There is a bug in the mod_auth_mysql package form the Ubuntu repositories so you should download it from [http://sourceforge.net/projects/modauthmysql/files/]("http://sourceforge.net/projects/modauthmysql/files/") . Be sure to get the latest version (3.0.0 at the time of writing). 

**[SIZE="4"]Configuring MySQL[/SIZE]**

Since Mediawiki and Bugzilla use mysql we need to configure it prior to installing either of them. 

```
 mysql -uroot -p&lt;root-password&gt; mysql
 GRANT SELECT, INSERT, UPDATE, DELETE, INDEX, ALTER,
   CREATE, LOCK TABLES, CREATE TEMPORARY TABLES, DROP,
   REFERENCES ON bugs.* TO bugs@localhost
   IDENTIFIED BY '&lt;bugs-password&gt;';
 FLUSH PRIVILEGES;

```

**[SIZE="4"]Installing mod_auth_mysql[/SIZE]**

We need to compile directly the module to allow apache to authenticate users using a database. The instructions given here follow the directions given in [URL="https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649"]https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649 
[/URL]
```
 cd &lt;directory where mod_auth_mysql-3.0.0.tar.gz resides&gt;
 wget http://www.bleb.org/software/mod_auth_mysql-3.0.0-apache-2.2.3.patch
 tar zxf mod_auth_mysql-3.0.0.tar.gz
 sudo apt-get --purge remove libapache2-mod-auth-mysql
 cd mod_auth_mysql-3.0.0
 patch &lt; ../mod_auth_mysql-3.0.0-apache-2.2.3.patch
 sed -i 's|#include &lt;mysql.h&gt;|#include &lt;mysql/mysql.h&gt;|' mod_auth_mysql.c
 apxs2 -c -lmysqlclient -lm -lz mod_auth_mysql.c
 apxs2 -i mod_auth_mysql.la
 sudo echo 'LoadModule mysql_auth_module /usr/lib/apache2/modules/mod_auth_mysql.so' &gt; /etc/apache2/mods-available/auth_mysql.load
 sudo a2enmod auth_mysql
```

**[SIZE="4"]Installing Bugzilla[/SIZE]**

To install bugzilla untar the previously downloaded package to /var/www/bugzilla and set permissions 

```
 tar xvzf bugzilla-3.0.9.tar.gz /var/www/
 cd /var/www/bugzilla
 chown -R root:root . *

```

Then from the same directory run the setup script 

 ```
./checksetup.pl --check-modules

```

Then using apt-get and the hints given by the script install all the dependencies. Note however that the script will suggest a lot of optional packages, but you only need a handful of packages to make it work. 

After installing all dependencies run again the script: 

```
 ./checksetup.pl
```

Then modify the localconfig file located in /var/www/bugzilla/localconfig 

```
 sudo nano /var/www/bugzilla/localconfig

```

The only setting we need to change is the $db_pass. This password should match the password for the bugs user in the mysql database configured before. 

```
 ./checksetup.pl
```

The script will ask for some information about the administrator, email, real name and password. then we need to configure apache to work with Bugzilla. 

Create a new file on /etc/apache2/conf.d/bugzilla.conf 

```
 sudo nano /etc/apache2/conf.d/bugzilla.conf

```
The copy and paste the following on that file: 

 ```
<Directory /var/www/bugzilla>
        AuthType Basic
        AuthUserFile /dev/null
        AuthName "Project Management Server"
        AuthBasicAuthoritative Off
        AuthMySQLEnable On
        AuthMySQLAuthoritative On
        AuthMySQLDB bugs
        AuthMySQLUser bugs
        AuthMySQLPassword <bugs-password>
        AuthMySQLUserTable profiles
        AuthMySQLNameField login_name
        AuthMySQLPasswordField cryptpassword
        require valid-user
        AddHandler cgi-script .cgi
        Options +Indexes +ExecCGI
        DirectoryIndex index.cgi
        AllowOverride Limit
 </Directory>
```

Then restart apache 

```
 sudo /etc/init.d/apache2 restart
```

[B][SIZE="4"]Configuring Bugzilla
[/SIZE][/B]

Now go to [http://localhost/bugzilla]("http://localhost/bugzilla") and then to parameters to configure bugzilla. The only needed parameters are the maintainer mail address and urlbase which should contain the URL of the bugzilla installation (in this case it will be [HTML]&lt;host&gt;/bugzilla/[/HTML]). It also recommended to setup the mailing system so users can create accounts and get notified of new bugs using through e-mail. 

You should also go to Parameters -> User Authentication, and then put auth_env_email = REMOTE_USER and user_info_class = env, to enable authentication through apache.

**[SIZE="4"]Patches[/SIZE]**

In order to be able to link the three applications from Bugzilla a small patch needs to be done. 

Please edit the file located in /var/www/bugzilla/Bugzilla/Template.pm. 

After line 311 you should see something like this: 

    ```
# Color quoted text
    $text =~ s~^(&gt;.+)$~<span class="quote">$1</span>~mg;
    $text =~ s~&lt;/span &gt;\n<span class="quote">~\n~g;
 </span>

```
Please add the following lines after the previous paragraph: 

   ```
 # BugID:
    $text =~ s~\b(BugID:)\s?(\d+)\b
              ~$1 . " " . get_bug_link($2,$2)~egox;
    # VCS:
    $text =~ s~\b(VCS:)\s?([0-9A-Za-z_/\-.]*)\b
              ~$1 &lt;a href=\"/cgi-bin/viewvc.cgi/$2\"&gt;$2&lt;/a&gt;~igx;
    # Wiki:
    $text =~ s~\b(Wiki:)\s?([A-Za-z_\-:]*)\b
              ~$1 &lt;a href=\"/wiki/index.php/$2\"&gt;$2&lt;/a&gt;~igx;
```

**[SIZE="4"]Configuring SVN[/SIZE]**

To test the correct installation of the Subversion repository we should now create a testing repository 

 ```
export SVNROOT=/var/www/svnroot/
 sudo svnadmin create $SVNROOT
 sudo chmod -R a+w $SVNROOT/db $SVNROOT/locks
```

The create a sample project and verify that there are no errors: 

 ```
[HTML]cd
 mkdir -p prj/trunk
 mkdir -p prj/tags
 mkdir -p prj/branches
 svn import prj file://$SVNROOT/prj -m "Initial repository layout."
 rm -rf prj
 svn co file://$SVNROOT/prj
 cd prj/trunk
 mkdir -p test
 echo foo &gt; foo
 echo bar &gt; test/bar
 svn add foo test
 svn ci -m "Imported sources."
 cd ../..[/HTML]
```


**[SIZE="4"]ViewVC[/SIZE]**

Now we need to configure ViewVC. 

First edit the file located in /usr/lib/viewvc/viewvc.py. 

In line 984 you should see the following: 

```
 _re_rewrite_email = re.compile('([-a-zA-Z0-9_.\+]+)@(([-a-zA-Z0-9]+\.)+[A-Za-z]{2,4})')
```

After that add: 

 _```
re_buglink = re.compile('(BugID:)\s?(\d+)', re.M)
 _re_vcslink = re.compile('(VCS:)\s?([0-9A-Za-z_/\-.]*)', re.M)
 _re_wikilink = re.compile('(Wiki:)\s?([A-Za-z_\-:%]*)', re.M)
 
 def bug_linkify(m):
    url = """&lt;a href="/bugzilla/show_bug.cgi?id=%s"&gt;%s&lt;/a&gt;"""
    ref = m.group(1)
    bug = m.group(2)
    text = ref + " " + url&nbsp;% (bug, bug)
    return text
 
 def vcs_linkify(m):
    url = """&lt;a href="/cgi-bin/viewvc.cgi/%s/"&gt;%s&lt;/a&gt;"""
    ref = m.group(1)
    vcs = m.group(2)
    text = ref + " " + url&nbsp;% (vcs, vcs)
    return text
 
 def wiki_linkify(m):
    url = """&lt;a href="/wiki/index.php/%s"&gt;%s&lt;/a&gt;"""
    ref = m.group(1)
    wiki = m.group(2)
    text = ref + " " + url&nbsp;% (wiki, wiki)
    return text

```
Then in line 1013 you should see this: 

 ```
html = re.sub(_re_rewrite_email, r'&lt;a href="mailto:\1@\2"&gt;\1@\2&lt;/a&gt;', html)

Add after that the following lines: 

 html = re.sub(_re_buglink, bug_linkify, html)
 html = re.sub(_re_vcslink, vcs_linkify, html)
 html = re.sub(_re_wikilink, wiki_linkify, html)
```

Now edit the configuration file located in /etc/viewvc/viewvc.conf 

Change this line (line 72): 

```
 cvs_roots = cvs: /home/cvsroot

```
To: 

 ```
#cvs_roots = cvs: /home/cvsroot
```

Then change line 80 from: 

 ```
svn_roots = 
```

To: 

```
 svn_roots = svnroot: /var/www/svnroot
```

Finally change line 105 from: 

```
 default_root = 

```
To: 

```
 default_root = svnroot

```
Now in order to test the results so far go to [http://localhost/cgi-bin/viewvc.cgi ]("http://localhost/cgi-bin/viewvc.cgi")

Finally add the following file to configure apache to work with the SVN repository. 

/etc/apache2/conf.d/svnrepo.conf: 

 ```
<Location /svn>
        DAV svn
        SVNParentPath /var/www/svnroot/
        SVNListParentPath On
 
        AuthType Basic
        AuthUserFile /dev/null
        AuthName "Project Management Server"
        AuthBasicAuthoritative Off
 
        AuthMySQLEnable On
        AuthMySQLAuthoritative On
        AuthMySQLDB bugs
        AuthMySQLUser bugs
        AuthMySQLPassword &lt;bugs-password&gt;
        AuthMySQLUserTable profiles
        AuthMySQLNameField login_name
        AuthMySQLPasswordField cryptpassword
        require valid-user
 </Location>
 
 &lt;Location /cgi-bin/viewvc.cgi/&gt;
        AuthType Basic
        AuthUserFile /dev/null
        AuthName "Project Management Server"
        AuthBasicAuthoritative Off
 
        AuthMySQLEnable On
        AuthMySQLAuthoritative On
        AuthMySQLDB bugs
        AuthMySQLUser bugs
        AuthMySQLPassword &lt;bugs-password&gt;
        AuthMySQLUserTable profiles
        AuthMySQLNameField login_name
        AuthMySQLPasswordField cryptpassword
        require valid-user
 &lt;/Location&gt;

```[/HTML]
Restart apache and test again the site. 
```

 sudo /etc/init.d/apache2 restart
```

[SIZE="4"]**Configuring MediaWiki **[/SIZE]

After installing mediakiki from the repos, some patches and configuration must be made to integrate mediawiki with the other tools. 

First modify or create in case it did not exist the file /etc/apache2/conf.d/mediawiki.conf with the following contents: 

 ```
[HTML]# Uncomment this to add an alias.
 # This does not work properly with virtual hosts..
 Alias /wiki /var/lib/mediawiki
 
 &lt;Directory /var/lib/mediawiki/&gt;
        #Athorization using Bugzilla
        AuthType Basic
        AuthUserFile /dev/null
        AuthName "Project Management Server"
        AuthBasicAuthoritative Off
 
        AuthMySQLEnable On
        AuthMySQLAuthoritative On
        AuthMySQLDB bugs
        AuthMySQLUser bugs
        AuthMySQLPassword &lt;bugs-password&gt;
        AuthMySQLUserTable profiles
        AuthMySQLNameField login_name
        AuthMySQLPasswordField cryptpassword
        require valid-user
 
        #General Options
        Options +FollowSymLinks
        AllowOverride All
        order allow,deny
        allow from all
 &lt;/Directory&gt;
 
 # some directories must be protected
 &lt;Directory /var/lib/mediawiki/config&gt;
        Options -FollowSymLinks
        AllowOverride None
 &lt;/Directory&gt;
 &lt;Directory /var/lib/mediawiki/upload&gt;
        Options -FollowSymLinks
        AllowOverride None
 &lt;/Directory&gt;
[/HTML]
```

Now go to [http://localhost/wiki](http://localhost/wiki) and configure Mediawiki. 

From the Ubuntu Documentation [https://help.ubuntu.com/community/MediaWiki]("https://help.ubuntu.com/community/MediaWiki") 
> Note however that the final form is NOT your root or user password, but the password for the root mysql account (blank by default). Lastly, move the config files as requested to prevent anyone else from changing these settings: 

```
sudo mv /var/lib/mediawiki/config/LocalSettings.php /etc/mediawiki/LocalSettings.php sudo chmod 600 /etc/mediawiki/LocalSettings.php 
sudo rm -Rf /var/lib/mediawiki/config/LocalSettings.php 

```

Now we need to change the LocalSettings.php to enable Apache authentication, add the following lines at the the end of /etc/mediawiki/LocalSettings.php: 

```
 # Apache::mod_auth integration
 require_once('Auth_remoteuser.php');
 $wgAuth = new Auth_remoteuser();
 # Disable anonymous edits
 $wgGroupPermissions['*']['edit'] = false;

```
Now download the Auth_remoteuser extension and put it in /usr/share/mediawiki-extensions/Auth_remoteuser.php.

Then simply enable the extension with:

```
 sudo mwenext Auth_remoteuser.php

```
**[SIZE="4"]Rich Editor Extension[/SIZE]**

To install FCKeditor extension on wikipedia do the following:

 ```
wget "http://mediawiki.fckeditor.net/nightly/svn/mediawiki_fckeditor_ext_N.zip"
 unzip mediawiki_fckeditor_ext_N.zip
 sudo mv extensions/FCKeditor/ /usr/share/mediawiki-extensions/
 sudo ln -s /usr/share/mediawiki-extensions/FCKeditor/FCKeditor.php /etc/mediawiki-extensions/extensions-available/FCKeditor.php
 sudo mwenext FCKeditor.php
 sudo ln -s /usr/share/mediawiki-extensions/FCKeditor/ /var/lib/mediawiki/extensions/

```
Then edit the file /etc/mediawiki/LocalSettings.php, change the following line:

 ```
# If PHP's memory limit is very low, some operations may fail.
 ini_set( 'memory_limit', '20M' );
```

To
```

 # If PHP's memory limit is very low, some operations may fail.
 ini_set( 'memory_limit', '32M' );
```

---

