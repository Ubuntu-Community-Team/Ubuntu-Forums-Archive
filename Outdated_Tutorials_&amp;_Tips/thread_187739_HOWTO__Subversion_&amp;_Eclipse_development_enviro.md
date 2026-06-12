---
title: "HOWTO : Subversion &amp; Eclipse development environment"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Cavalierski on 2006-06-03
[COLOR="Blue"]# All the modified or additional information will be updated on this post in order for everyone to get alwasys up-to date information.[/COLOR]

[COLOR="BLUE"]# After you've done this, some of you might need  tomcat5 + Apache2 set up. 
# I also wrote the article [**here**]("http://ubuntuforums.org/showthread.php?t=219985"), so please have a look.[/COLOR]

Here is the how-to for setting up the subversion client with eclipse and the server. Hope this will help you more productive coding :D 

First of all, regarding "Subversion"  For more detail, please refer to [http://en.wikipedia.org/wiki/Subversion_(software)](http://en.wikipedia.org/wiki/Subversion_(software))
Here is the snipet about the difference between CVS & Subversion.
> Subversion was created as a replacement for CVS. Its improvements include:
    * Atomic commits. Interrupted commit operations do not cause repository inconsistency or corruption.
    * Renamed/copied/moved/removed files retain full revision history.
    * Native support for binary files, with space-efficient binary-diff storage.
    * Directories are versioned. Entire directory trees can be moved around and/or copied very quickly, and retain full revision history.
    * Constant time branching and tagging.
    * Optimized repository accesses. This reduces unnecessary network traffic to the repository host.
    * Full MIME support - the MIME Type of each file can be viewed or changed, with the software knowing which MIME types can have their differences from previous versions shown.

"Eclipse" is a Integrated Development Environment which provides the platform of developing Java/C++ ..etc. You can add the support language by adding plugin.

Now let's get started to prepare the development environment for Ubuntu (Dapper).

**[COLOR="Red"][Client - Eclipse with plugin] [/COLOR]**
Assume that you have already installed eclipse & j2sdk1.5-sun.
If you face problem starting up the eclipse you can find the answer in this forum. Most likely it is related to "java_home". Just for the instant check```

cd /etc/eclipse
cat java_home
```
If you don't see  _/usr/lib/j2sdk1.5-sun/_ commented out in the first line, modify it. Mine looks like this..
```
ubuntu% cat java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun/
#/usr/lib/jvm/java-gcj
#/usr/lib/kaffe/pthreads
#/usr/lib/sablevm
#/usr/lib/fjsdk
#/usr/lib/j2se/1.5
#/usr/lib/j2se/1.4
#/usr/lib/j2sdk1.5-ibm
#/usr/lib/j2sdk1.4-ibm
#/usr/lib/j2sdk1.5-sun
#/usr/lib/j2sdk1.4-sun
```

Ok then , let's get started.
**Step1: Installing the plug-in (subclipse)**
Launch eclipse and go to : 
help->s/w updates ->find and install->search for new features
Then press "new remote site" and add "http://subclipse.tigris.org/update"
Then follow the instraction to install the plugin.

**Step2: Install library needed for subversion from eclipse**
```
sudo apt-get install libsvn-javahl
```

**Step3: Grance at subversion perspective**
Follow this then you can see the svn perspective :-D 
window->Opne Perspective-> Other->SVN Repository Explorer

If you already have subversion server running, you can access to it by right clicking svn repository explorer then 
new -> create remote folder

**[COLOR="Red"][Server - Subversion] [/COLOR]**
There are 2 simple ways to use subversion. One is using subversion function over WebDav and another is subversion server using specific protocol. First I'll explain about the WebDav way.

**Step1: Install subversion package [WebDav]**
```
 sudo apt-get install subversion subversion-helper-scripts subversion-tools 
sudo apt-get install apache2 libapache2-svn

```

**Step2: Create repository folder & bind it to subversion.**
```
sudo mkdir -p /var/local/svn
sudo svnadmin create --fs-type fsfs /var/local/svn
sudo chown -R www-data:www-data /var/local/svn
```

**Step3: Set configuration for apache2 subversion module**
```
sudo vi/etc/apache2/mods-enabled/dav_svn.conf
--
#Comment out the following 2 lines with your repo path
#DAV svn <-Comment out this
DAV svn

#SVNPath /var/lib/svn <-Comment out this
SVNPath /var/local/svn

&#65308;LimitExcept GET PROPFIND OPTIONS REPORT&#65310;
#Require valid-user <-Comment this if you don't need basic authentication
Options Indexes
Order allow,deny
allow from all
&#65308;/LimitExcept&#65310;


```

**Tip1 - Basic Authentication**
In order to use basic authentication for loging on to subversion server, you need to do the followings.
```
sudo vi/etc/apache2/mods-enabled/dav_svn.conf
# comment the following 4 lines
   [B]AuthType Basic
   AuthName "Subversion Repository"
   AuthUserFile /etc/apache2/dav_svn.passwd[/B]
  <LimitExcept GET PROPFIND OPTIONS REPORT>
    **Require valid-user**
    Options Indexes
    Order allow,deny
    allow from all
  </LimitExcept>

```
Then create the user account
```

#-m option for MD5 encryption of the password
sudo htpasswd2 -cm /etc/apache2/dav_svn.passwd cavalier1 
New password: ***** 
Re-type new password: *****
Adding password for user cavalier1
$ htpasswd -m /etc/apache2/dav_svn.passwd cavalier2
New password: *******
Re-type new password: *******
Adding password for user cavalier2

```
Now you can access to it with basic authentication.

**Tip2 - SSL access**
```

# Create ssl certificate
# certificate will be stored at /etc/apache2/ssl
sudo apache2-ssl-certificate

# Copy conf file for ssl
sudo cp /usr/share/apache2/config/default-443 /etc/apache2/sites-available

```
First conf file for port 80
```

# Edit conf file
sudo vim /etc/apache2/sites-available/default
--
#Comment following and set proper one
# NameVirtualHost *
NameVirtualHost *:80

# <VirtualHost *>
<VirtualHost *:80>

```
Ok then conf file for port 443 (ssl)
```

sudo vim /etc/apache2/sites-available/default-443
--
# Find the following lines and comment out and set the appropriate ones
# SSLCertificateFile    /etc/apache2/sites/::SERVERNAME::-ssl.crt
SSLCertificateFile    /etc/apache2/ssl/apache.pem

# SSLCertificateKeyFile /etc/apache2/sites/::SERVERNAME::-ssl.key
SSLCertificateKeyFile /etc/apache2/ssl/apache.pem

# ServerAdmin ::SERVERADMIN::
ServerAdmin Cavalierski

# ServerName ::SERVERNAME::
ServerName www.yourdomain.com

# DocumentRoot /var/vhosts/::VHOSTNAME::/htdocs-443
DocumentRoot /var/www

# <Directory /var/vhosts/::VHOSTNAME::/htdocs-443>
<Directory /var/www>

# ErrorLog /var/vhosts/::VHOSTNAME::/logs/error.log-443
ErrorLog /var/log/apache2/error.log-443

# CustomLog /var/vhosts/::VHOSTNAME::/logs/access.log-443 combined
CustomLog /var/log/apache2/error.log-443 combined

# I deleted the cgi lines as I don't need them. That's all for conf file.
--
# Enable ssl module
sudo a2enmod ssl
# Enable ssl config
sudo a2ensite default-443

# Open the port for ssl
sudo vim /etc/apache2/ports.conf
# Add the following line
Listen 443

```

Then reload the setting.
```
sudo /etc/init.d/apache2 reload

```
It's done. You can access to it with "http://your server name/svn".
or
If you've done ssl part "https://your server name/svn".:-D 
----
**Step1: Install subversion package[svn Server]**
```
 sudo apt-get install subversion subversion-helper-scripts subversion-tools 
```

**Step2: Create repository folder & bind it to subversion.**
# You can deploy your repository folder wherever you want. This is my case.

```
sudo mkdir -p /var/local/svn/projectx
sudo svnadmin create /var/local/svn/projectx
sudo chown -R username:usergroup /var/local/svn/projectx
```

**Step3: Set configuration for subversion server**
```
cd /var/local/svn/projectx/conf
sudo gedit  svnserve.conf
--
[general]
 anon-access = read
 auth-access = write
 password-db = passwd # This refer to passwd file in the same folder
 realm =Cavalier Repository
--
```

Ok then set the authentication for the access to the subversion server. In the same folder there is already the file named "passwd", all you need to do is edit this plain text file.

```
sudo gedit passwd
--
 [users]
username = password #<- you can modify here to whom you want to allow the access 
--
```

Setup for the subversion server is done :-D You can run it as a daemon by:
```
sudo /usr/bin/svnserve -d
```
or with "-r" option you can indicate the path to repos.
# With "-r" option like "svnserve -d -r /var/local/repos", your path to the repos is hidden. If you want to access to "/var/local/repos/xproject/trank" , from the client the address to access is "svn://your.svnserve.address/xproject/trank"
```
sudo /usr/bin/svnserve -d -r /root/svn/var/local/svn/your_repos
```

**[COLOR="Red"][Others][/COLOR]**
However you most likely want to run automatically at OS start up.
Then let's try to do it by the super server.

Super server is a program which start the service triggered by the client request. Super server watch the specified port and if there is a request listed on the conf file, it automatically start the program. This will reduce the use of CPU and even the service is down , it automatically start the service. (Often TELNET, POP which require stability are using super server)
# However the server such as HTTPD (Apache) which has frequent access BETTER NOT use super server.

**Step1: Install xinetd(Super server program) and set it up.**
```
sudo apt-get install xinetd
sudo gedit /etc/xinetd.d/svnserve
--
service svnserve
{
    disable         = no
    port            = 3690
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/bin/svnserve
    server_args    = -i -r /var/local/svn/your_repos
}
--

sudo gedit /etc/services
# modify the port "3690/tcp" line like this below
--
svnserve		3690/tcp	# Subversion protocol
--
```

After the configuration , restart xinetd :
```
sudo /etc/init.d/xinetd restart
```

**[COLOR="Red"][Workaround][/COLOR]**
Some people might face error such as "Malformed network data". Try following as a temporary solution.

[COLOR="Red"]#Before please check if you run svnserve with "-r" option like "svnserve -d -r /var/local/repos", your path to the repos is hidden. If you want to access to "/var/local/repos/xproject/trank" , from the client the address to access is "svn://your.svnserve.address/xproject/trank"[/COLOR]

1) Many case svnserve file under xinetd.d is misspelled. Please check it first.
2) If svnserve file seems ok + you are running svnserve locally, change the protocol to "file".
Use:
```
**file:**///localhost/var/local/svn/your_repos
```
instead of 
```
**svn:**//localhost/var/local/svn/your_repos
```

3)If your are runnin svnserve on different machine. Forget about xinetd and run as a daemon.
```
sudo rm /etc/xinetd.d/svnserve
sudo /etc/inited.d/xinetd restart
sudo /usr/bin/svnserve -d -r /root/svn/var/local/svn/your_repos
```

**[COLOR="Red"][Tips][/COLOR]**
You can alwasy check if the 3690 port is Listen status by 
```
netstat -n 
or
netstat -an|grep 3690
```

**[COLOR="Red"][Infos][/COLOR]**
Here you could get the additional good info from the community member.

[QUOTE=leo_m]Subclipse with javahl has problems...when I try to use file protocol to configure a remote host in subclipse, that url gets appended after the eclipse installation folder, e.g, if I specify file:///subversion_repositories/repository1, subclipse using javahl tries to go to /home/leo/eclipse/file/subversion_repositories/repository1, which is not a valid path, assume eclipse was installed at /home/leo/eclipse.  

it is better to use javasvn than the javahl: it can be configured in Windows|Preferences (and then choose settings for subclipse)[/QUOTE]

OK Done !!
Now I have subversion server & client for the productive open source development.. Enjoy coding:KS

---

### Post by mbeach on 2006-06-09
Just a couple of notes while following this:
- I had to run svnadmin with sudo
- the path for the xinetd svnserve conf file was "/etc/xinetd.d" (on my box anyway)
- the second "server" is supposed to be "server_args" I think 

on a personal opinion note, I question whether the user should be 'root'.  I created a user 'svn' and chown'ed the svn directory to svn and used user = svn in the svnserve conf file.  I'll post back if I run into issues.

Otherwise, thanks for the guide.  I only post this to help out the next person.

---

### Post by Cavalierski on 2006-06-11
Thanx mbeach, your points are all right.
I updated my original article. Thanx again for your feedback:p 

Regarding the user root, I suppose creating another user for it is more secure. However it shouldn't be a big problem I guess to use root account this time, shoud it?

[QUOTE=mbeach]Just a couple of notes while following this:
- I had to run svnadmin with sudo
- the path for the xinetd svnserve conf file was "/etc/xinetd.d" (on my box anyway)
- the second "server" is supposed to be "server_args" I think 

on a personal opinion note, I question whether the user should be 'root'.  I created a user 'svn' and chown'ed the svn directory to svn and used user = svn in the svnserve conf file.  I'll post back if I run into issues.

Otherwise, thanks for the guide.  I only post this to help out the next person.[/QUOTE]

---

### Post by thumper on 2006-06-12
If you use the name **svn** instead of **svnserve** then you don't need to edit your **/etc/services** file as svn is already in there with the appropriate port number.

I too created a svn system user (no home created) and did a chown on the repository directory.

Thanks for the HOW TO though, it started me on the right track.

---

### Post by aouie on 2006-06-14
If you are using subversion and eclipse (and subclipse), and would like to access a local repository using the file:// protocol then you need to install libsvn-javahl. Then start eclipse with "eclipse -vmargs -Djava.library.path=/usr/lib/jni/".
In the Eclipse menu Windows -> Preferences -> Team -> SVN and select JavaHL.
I am using eclipse 3.1 (custom installation) with subclipse 1.0.2 and libsvn and libsvn-javahl from the Dapper repositories.
Sincerely,
Aouie

---

### Post by hdpc on 2006-06-23
Hi all,

I am totally new with this.  I've just installed Ubuntu 6.06 a few days ago.  I wanted to play around with Subversion.

I follow all the steps above and I think I am doing everything correctly.
I did also created a svn account (with no home directory).
In Step 2:
  This is what I did, is this correct?
  sudo mkdir -p /var/local/svn/projects
  sudo svnadmin create /var/local/svn/projects
  sudo chown -R svn:svn /var/local/svn/projects

In Step 3:
  I did exactly the same, except I gave it a different Realm Repository.  How
  does this Realm name come into play?  Does this even matter?
  
  I also add a user and password to the passwd file.

I did install xinetd.
I edited /etc/xinetd.d/svnserve to be the following

service svnserve
{
    disable         = no
    port             = 3690
    socket_type  = stream
    protocol       = tcp
    wait            = no
    user            = sve
    server          = /usr/bin/svnserve
    server_args    = -i -r /var/local/svn/projects
}

and edited /etc/services to the following:
svnserve		3690/tcp	# Subversion protocol

I've restarted /etc/init.d/xinetd restart, is say it stop and started again after the command.

So I think I am doing everything correctly.  I have a few questions.
First how can I tell that the svnserve is running?

Secondly how can I access the svn repository. Is it svn://my.domainname/svn?  Can I put that url a browser address bar or File Explorer?

Thanks again for help.

---

### Post by Sam on 2006-06-23
I had problems using Subversion.

I've installed [Subversive](http://www.polarion.org/index.php?page=overview&project=subversive) which acts as Subversion and now I have no problems. Developers says that it's possible to use both together.

---

### Post by mattb1982 on 2006-06-25
Hi,

I've followed all of the instructions here, but I get a "Malformed network data" error when I try to create a new repository location from eclipse.  What's going wrong?  I'm using svn://localhost for my repository location.

---

### Post by Cavalierski on 2006-06-27
[QUOTE=hdpc]
So I think I am doing everything correctly.  I have a few questions.
First how can I tell that the svnserve is running?

Secondly how can I access the svn repository. Is it svn://my.domainname/svn?  Can I put that url a browser address bar or File Explorer?

Thanks again for help.[/QUOTE]

Hi, regarding your question,

A1) You can check if the server is listening the port or not by
```
netstat -n
```
If you run it as a daemon (with -d option), you can see it by
```
ps aux | grep svn
```

A2) If you want to access to svn server, you need svn client (CUI or GUI). You cannot use the service if you access to it by your browser (firefox?) as it doesn't understand the protocol.
 If you want to access CUI,
```
svn co svn://localhost/var/local/svn/xxx
```

I added article on the top post, please have a look:)

---

### Post by Cavalierski on 2006-06-27
[QUOTE=mattb1982]Hi,

I've followed all of the instructions here, but I get a "Malformed network data" error when I try to create a new repository location from eclipse.  What's going wrong?  I'm using svn://localhost for my repository location.[/QUOTE]

As a tentative solution, I updated the first post. Please have a look.

---

### Post by elemental666 on 2006-07-01
I keep getting this error when I try to view the repo:

```
sudo svn co svn://localhost/var/local/svn/projectx
svn: /var/local/svn/projectx/conf/svnserve.conf:9: Option expected

```

or from within Ecplise:

```

url:  svn://localhost/var/local/svn/projectx

Error validating location: "org.tigris.subversion.javahl.ClientException:
Malformed file
svn: /var/local/svn/projectx/conf/svnserve.conf:9: Option expected"

```

here's my svnserve.conf
```

ln
8  [general]
9   anon-access = read
10  auth-access = write
11  password-db = passwd # refers to passwd file in same folder
12  realm = Elemental Repository

```


Also found some corrections to be made to the OP:
[QUOTE=Cavalierski][COLOR="Blue"]
**[COLOR="Red"][Server - Subversion] [/COLOR]**
**Step1: Install subversion package**
```
sudo apt-get subversion subversion-helper-scripts subersion-tools
```
[/QUOTE]

should be

```
 sudo apt-get install subversion subversion-helper-scripts subversion-tools 
```

typos mainly..

---

### Post by elemental666 on 2006-07-01
Anyone?

---

### Post by leo_m on 2006-07-01
Regarding the subversion problem in svnserve.conf: kindly mention how you start the svnserve daemon...

Regarding the HOW-TO, a few points:

1.  It is better to create the new repository (svnadmin create) with --fs-type=fsfs.

2.  Subclipse with javahl has problems...when I try to use file protocol to configure a remote host in subclipse, that url gets appended after the eclipse installation folder, e.g, if I specify file:///subversion_repositories/repository1, subclipse using javahl tries to go to /home/leo/eclipse/file/subversion_repositories/repository1, which is not a valid path, assume eclipse was installed at /home/leo/eclipse.  

IMHO, it is better to use javasvn than the javahl: it can be configured in Windows|Preferences (and then choose settings for subclipse).

3.  svnserve -d should preferably be run with a -r as well, to specify the repository-root clearly; and to have consistent behaviour irrespective of which directory you were in when you ran this command.

4.  Where possible, even if access to a repository has been granted using [http://,](http://,) svn:// and file:///, then file:/// should be preferred over svn://, which should be preferred over http:// purely from a performance point of view.

---

### Post by Cavalierski on 2006-07-02
> **leo_m]1.  It is better to create the new repository (svnadmin create) with --fs-type=fsfs.[/QUOTE]

 After a subversion version 1.2, --fs-type=fsfs is a default if there is no option.

[QUOTE=leo_m]2.  Subclipse with javahl has problems...when I try to use file protocol to configure a remote host in subclipse, that url gets appended after the eclipse installation folder, e.g, if I specify file:///subversion_repositories/repository1, subclipse using javahl tries to go to /home/leo/eclipse/file/subversion_repositories/repository1, which is not a valid path, assume eclipse was installed at /home/leo/eclipse.  

IMHO, it is better to use javasvn than the javahl: it can be configured in Windows|Preferences (and then choose settings for subclipse).

3.  svnserve -d should preferably be run with a -r as well, to specify the repository-root clearly said:**
> http://,[/url] svn:// and file:///, then file:/// should be preferred over svn://, which should be preferred over http:// purely from a performance point of view.

Ok,I'll update the first post with this info, thanx.

---

### Post by vinodis on 2006-07-03
Excellent tutorial. what i wanted!
Thank you very much all.

---

### Post by thor918 on 2006-07-17
any chance anyone can make a howto that explains install of websvn with authentication?

---

### Post by Packard on 2006-07-17
Is there a way to encrypt the password in the passwd file when using svnserve? I read somewhere to encrypt it using perl but I tried that and it didn't work. It only accepts the password as it is saved in clear text in that passwd file.

I set up a few repositories for different users and they always have to send me their password unencrypted - that's a little weird.

---

### Post by Cavalierski on 2006-07-17
> **thor918 said:**
> any chance anyone can make a howto that explains install of websvn with authentication?

It's done. :) See the top post.

---

### Post by thor918 on 2006-07-18
hmm not sure if we understood each other,
I was talking about websvn
[http://websvn.tigris.org/](http://websvn.tigris.org/)



by the way,
the webdav stuff is interesting, 
I have svn currently set up as "xinetd(Super server program)", but I'm considering on doing the webdav way, 
because I can probably then set up a secure connection trough https (witch seems a little easier for users remotly than the svn+ssh connection).

---

### Post by Cavalierski on 2006-07-18
> **thor918 said:**
> hmm not sure if we understood each other,
I was talking about websvn
[http://websvn.tigris.org/](http://websvn.tigris.org/)


Ooops. :-? Ok websvn stuff is new to me and I'll try when I have time. Currently I'm busy at work developping applications though..

---

### Post by thor918 on 2006-07-20
> **Cavalierski said:**
> Ooops. :-? Ok websvn stuff is new to me and I'll try when I have time. Currently I'm busy at work developping applications though..

no problem :)
I have configurated webdav now.
It works perfect with authentication :D 
much better than using a svn+ssh connection to make it safe for remote users. I can access the svn from this url now : [https://myserver/svn/projectx](https://myserver/svn/projectx)
It also seems that I got the websvn working now. 

@Packard
Why not use webdav method instead. That way you can use htpasswd command to create hashed passwords that can be used in svn access.

---

### Post by Packard on 2006-07-20
For webdav it seems you need a http connection and a web server. That doesn't exist on the machines where I have the repositories unfortunately.

---

### Post by Cavalierski on 2006-07-20
> **Packard said:**
> For webdav it seems you need a http connection and a web server. That doesn't exist on the machines where I have the repositories unfortunately.

Hi, Packard.
As far as I know, subversion doesn't offer the encryption function for its config. However on the network by using its protocol, no text plain data is transmitted. Just on the server, you have plain text password which I also feel unconfortable.

At work I long before made the subversion server using webdav solution on Debian (PowerEdge1850) using basic authentication + SSL. It works pretty fine at least for 6 months I never reboot the server:) 

I enrich the first post about the basic authentication + ssl over webdav subversion server. Of course you need http server but it's not so complicated to set it up and easy to maintenance. So why don't you give it a try.

Good luch ;)

---

### Post by Cavalierski on 2006-07-21
I also made the thread how to set up tomcat5 + Apache2.
If you are interested in , please have a look.

[Tomcat5 + Apache2]("http://ubuntuforums.org/showthread.php?t=219985")

---

### Post by saracen on 2006-09-26
Why does subversion-tools automatically pull down Exim - a mail server?

---

### Post by Nicky726 on 2007-02-15
On my system (ubuntu edgy amd64 sun jdk 5.0 update 8 eclipse 3.2.1) this worked but ONLY WITHOUT the libraries installed. I did it as told in howto and after trying to use subclipse whole eclipse crashed. Then I removed libraries and now it's working. So if anyone has this problem try to uninstall libsvn-javahl

---

### Post by Innova on 2007-02-28
I have eclipse and the subclipse plugin installed.

Then I did sudo apt-get install libsvn-javahl

I restarted eclipse and tried to view the subversion perspective and eclipse crashed.  Any idea what the problem is?

Here is a link to the error log:  [http://utopiaprogramming.com/hs_err_pid8451.log](http://utopiaprogramming.com/hs_err_pid8451.log)

---

### Post by superiorWANG on 2007-03-23
I seem to be having the same problem as Innova -- maybe something has broken recently in the repository.  I tried the suggestion by Nicky726 - but this isn't really a solution, subclipse doesn't crash, but it also doesn't seem to have all the functionality.

Does anyone have any ideas as to how to resolve this problem?

Thanks!

---

### Post by Innova on 2007-03-23
I have it working now...but to be honest, I forgot what I did exactly to get it to work...I just kept pounding at it.

I think I started over from scratch...and installed all that I could through Eclipse's Software Updates.

---

### Post by glauber_md on 2007-05-24
> **elemental666 said:**
> I keep getting this error when I try to view the repo:

```
sudo svn co svn://localhost/var/local/svn/projectx
svn: /var/local/svn/projectx/conf/svnserve.conf:9: Option expected

```

or from within Ecplise:

```

url:  svn://localhost/var/local/svn/projectx

[B]Error validating location: "org.tigris.subversion.javahl.ClientException:
Malformed file
svn: /var/local/svn/projectx/conf/svnserve.conf:9: Option expected"[/B]
```

here's my svnserve.conf
```

ln
8  [general]
9   anon-access = read
10  auth-access = write
11  password-db = passwd # refers to passwd file in same folder
12  realm = Elemental Repository

```


**[COLOR="Red"]Verify the spaces before "anon-access" and so on...[/COLOR]** It made me crazy too :)

---

### Post by sandclock on 2008-06-02
Hi guys
this is a great tutorial. I have managed to get most of the part working but i am stuck at one point. Here is my situation.
1. I am trying to setup a local server on my lan for PHP development
2. I have managed to get it working as i can access [http://xxx.xxx.x.xx/(local](http://xxx.xxx.x.xx/(local) IP) from my lan.
3. i can also access [http://xxx.xxx.x.xx/svn](http://xxx.xxx.x.xx/svn) 
4. I am using eclipse and have installed it on all my boxes. Now i am stuck here i dont know how all my devs can work on the server [http://xxx.xxx.x.xx/](http://xxx.xxx.x.xx/) which i have setup and use svn
Thanks and regards
Nik

---

### Post by 1jackjack on 2008-07-16
if anyone is interested, i've just spent ages trying to configure the following setup:
-eclipse + java development
-pdt plugin (php development)
-subclipse

the solution i found was this:
-install the set of sun-java5 packages in synaptic (search sun-java5, and i installed bin,demo,jdk,jre,plugin)
-download eclipse 3.3.2 with PDT pre-installed from the PDT website (and simply unpack it and run it from that folder - no installation required)
-forget about subclipse, and install subversive (very similar i think) from within eclipse; help>software updates>find and install, and add these urls:
[http://download.eclipse.org/technology/subversive/0.7/update-site/](http://download.eclipse.org/technology/subversive/0.7/update-site/)
[http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/](http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/)

NOTE: the second one is for the connectors and it is a requirement...

This is not an ideal solution, but it works...

---

### Post by rajeshgubba on 2008-08-22
Hi,

I am using subclipse,
I have one doubt regarding the feature 'Merging'.

Can anybody tell me how to use this option in eclipse.
I tried this but the changes are not reflected..

i would like to changes done in trunk folder to branch folder??

help me...

---

### Post by 1jackjack on 2008-10-25
Some more information i have gathered as my requirements have changed (I now need to use 2 different versions of eclipse for some project compatibility reasons, as well as PDT for PHP development, CDT for C/C++ development and Subclipse for subversion). I hope this will be useful for someone:

IF NEED OLD VERSIONS OF ECLIPSE: [http://archive.eclipse.org/eclipse/downloads/](http://archive.eclipse.org/eclipse/downloads/)

PLUGINS (help>software>install>new remote location)

CDT (check [http://www.eclipse.org/cdt/downloads.php](http://www.eclipse.org/cdt/downloads.php))
[http://download.eclipse.org/tools/cdt/releases/ganymede](http://download.eclipse.org/tools/cdt/releases/ganymede) (for eclipse v3.4)
[http://download.eclipse.org/tools/cdt/releases/europa](http://download.eclipse.org/tools/cdt/releases/europa) (for eclipse v3.3)
[http://download.eclipse.org/tools/cdt/releases/callisto](http://download.eclipse.org/tools/cdt/releases/callisto) (for eclipse v3.2)
[http://download.eclipse.org/tools/cdt/releases/eclipse3.1](http://download.eclipse.org/tools/cdt/releases/eclipse3.1) (for eclipse v3.1)
[http://update.eclipse.org/tools/cdt/releases/new](http://update.eclipse.org/tools/cdt/releases/new) (for eclipse v3.0)

PDT (read PDT wiki CAREFULLY: [http://wiki.eclipse.org/PDT/Installation](http://wiki.eclipse.org/PDT/Installation))
FOR ECLIPSE 3.3:
-http://download.eclipse.org/tools/pdt/updates/
-and selecting 'Europa Discovery Site'
-and then later clicking 'Select Required' to resolve dependencies

SUBCLIPSE (check [http://subclipse.tigris.org/install.html](http://subclipse.tigris.org/install.html))
[http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x) (for eclipse v3.2+)
[http://subclipse.tigris.org/update_1.2.x](http://subclipse.tigris.org/update_1.2.x) (for eclipse v3.2+)
[http://subclipse.tigris.org/update_1.0.x](http://subclipse.tigris.org/update_1.0.x) (for eclipse v3.0/3.1)

---

### Post by Numer0bis on 2010-01-04
Thank you so much for this tutorial. I spend hours trying to set up an svn server on ubuntu 9.10  for java development at my school. Now it's finally working.

Best Regards

Numer0bis

---

### Post by Japhering on 2010-01-18
I have subversion and eclipse working for all my clients working from Linux (heron, ibex, jackalope, and koala.   

However, I have one trouble maker running eclipse from Win XP.  For him, everything in the repository opens in eclipse as read only.

Anyone have any ideas ?

Thanks

---

