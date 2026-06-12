---
title: "Installing Webmin on Dapper Server"
date: 2006-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by crmanski on 2006-06-12
**What is Webmin?**
Webmin is an excellent web-based interface to your *nix based machines([www.webmin.com](www.webmin.com)). There are no webmin packages in the latest release "Dapper". This is how I installed webmin on my Dapper server...
*Edit Jul 15 2006: as of July 2006 webmin.com has a testing deb for the full webmin package. You can use this, but you will have to enable the root user. Following the instructions below will avoid enabling the root account.*

1. Install SSH
```
sudo apt-get install ssh
```

2. Enable the universe and multiverse repositories in the /etc/apt/sources.list ([https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto))

3. To make this easier use a ssh client like Putty(Win32) or a Term on another machine that has a GUI and copy/paste these commands or you can just re-type them...

Below is the source I just happened to use. If it is not working go to: [http://prdownloads.sourceforge.net/webadmin/webmin-1.350.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.350.tar.gz) and find a working mirror.

**Where to install Webmin?**
At this point you should note that the directory that you are currently in  will be the directory that webmin gets installed into. I don't mind it being in /home/MyAdminAccount/webmin, but if you want it somewhere else now is the time to change to that directory. 

Doing something like this would put your installation in /opt/webmin ```
sudo su
``` ```
mkdir /opt/webmin
``` and then ```
cd /opt/webmin
``` 

**Now Download the Webmin archive..**.
```
wget http://easynews.dl.sourceforge.net/sourceforge/webadmin/webmin-1.350.tar.gz

```
```
gzip -cd webmin-1.350.tar.gz | tar xvf -
```

```
sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules

```
```
cd webmin*

```
```
./setup.sh
```

Basically just hit enter and choose SSL and the auto start the service at boot
Web server port (default 10000): (Feel Free to change this)
Login name (default admin):
Login password: AReallyGoodONE
Password again: AReallyGoodONE
Use SSL (y/n): y
Start Webmin at boot time (y/n): y

Now you can login with the user/password that you set at the [https://IpAddressOfYourMachine:10000](https://IpAddressOfYourMachine:10000)

---

### Post by examancer on 2006-06-12
Great information. Worked perfect. Thanks a lot for taking the time to write out these instructions.

---

### Post by rizzo on 2006-06-13
this is awesome.  Just what I was looking for.  THANKS!!

---

### Post by rso on 2006-06-22
nice how to!

Do you know how to manage apache2 with webmin?
In this default install it is all adapted to apache 1.

Ciao
Richard

---

### Post by blkish on 2006-06-22
good how-to

it's a shame there is no webmin package for debian/ubuntu any more. great admin tool when correctly secured.

blkish

---

### Post by crmanski on 2006-06-22
[QUOTE=rso]nice how to!

Do you know how to manage apache2 with webmin?
In this default install it is all adapted to apache 1.

Ciao
Richard[/QUOTE]
Basically just click on config and change everything you see that says "apache" to "apache2"
There are two other items...
"File or directory to add virtual servers to"
/etc/apache2/sites-available
"Directory to create links in for new virtual servers"
/etc/apache2/sites-enabled

I attached a screenshot of my config page to this post...

---

### Post by yang_hui1986527 on 2006-06-23
nice how-to 
thank you!

---

### Post by rso on 2006-06-25
I did it and it worked, but after recompiling the kernel and rebooting I cannot connect anymore. Do I have to redo everything or am I missing something here?

Thanks for your help.

---

### Post by crmanski on 2006-06-25
[QUOTE=rso]I did it and it worked, but after recompiling the kernel and rebooting I cannot connect anymore. Do I have to redo everything or am I missing something here?

Thanks for your help.[/QUOTE]

It sounds like the service didn't start up. I would try...
```
sudo /etc/init.d/webmin start
```
...and see what happens.

---

### Post by sewmyheadon on 2006-06-26
Thanks crmanski for the tutorial.  Worked like a charm!

---

### Post by Thiesen on 2006-06-28
Very nice howto... but just one thing... that install script wants to install Webmin in my "/home/my_account_here/webmin-1.280"... shouldn't it be installed somewhere else??

Weeeee... it worked... nice stuff... :-)

---

### Post by DirtDart on 2006-06-29
Your guide worked like a charm!  Thanks for the info.


Anyone know why there isn't a package for webmin for ubuntu ?

---

### Post by blkish on 2006-06-29
[QUOTE=DirtDart]Your guide worked like a charm!  Thanks for the info.


Anyone know why there isn't a package for webmin for ubuntu ?[/QUOTE]

The maintainer of the Debian package orphaned it (stopped maintaining) some time ago, and it's since been removed from the Debian/Ubuntu repositories.

Hopefully someone willstep up to maintain the package again, but it won't be in the repos again until that happens.

blkish

---

### Post by nameiwantistaken on 2006-06-29
Anyone else having problems with this running again when you boot.  I have to reinstall it every time.

---

### Post by knowmad on 2006-07-01
It appears to me that webmin has made it back into the repository...
Any one know the story behind this?

nameiwantistaken,
Try uninstalling it completely and installing the one from synaptic, it should have all the plugins too!

Let us know your results!

---

### Post by nameiwantistaken on 2006-07-01
Done and done before I made the post.  I downloaded it directly from their site to start with.  Same result.

---

### Post by lonetree on 2006-07-04
[QUOTE=nameiwantistaken]Done and done before I made the post.  I downloaded it directly from their site to start with.  Same result.[/QUOTE]


When was it make available in the repositories? I tried last week and I wasn't there still, or have I not added the correct repositories entry? Please help

regards,

---

### Post by crmanski on 2006-07-04
[QUOTE=nameiwantistaken]Anyone else having problems with this running again when you boot.  I have to reinstall it every time.[/QUOTE]

Does the file:  /etc/init.d/webmin
get created during the installation?

If yes then maybe it is not executable. To test this type 
```
sudo /etc/init.d/webmin start
```
in a terminal. If it says something like "permission denied" then make the file executable...
```
sudo chmod 740 /etc/init.d/webmin
```

---

### Post by crmanski on 2006-07-04
[QUOTE=Thiesen]Very nice howto... but just one thing... that install script wants to install Webmin in my "/home/my_account_here/webmin-1.280"... shouldn't it be installed somewhere else??

Weeeee... it worked... nice stuff... :-)[/QUOTE]

I suppose it would be a good idea.  If you cd as root to /root or /opt before running wget then you could have it out of the way. Mine has been running in ~/webmin for a couple years now with no problem. It is my personal machine though.

---

### Post by crmanski on 2006-07-04
Just a heads-up. There is a new release of webmin that > Fixed a security hole that would allow a remote attacker to view any file on the system

If you are running version 1.280 or less you should update.  The easiest way I find is to login to webmin, click on  "Webmin Configuration", then "Upgrade Webmin". I usually check off "Delete old version's directory after upgrade?" since I do not like the have multiple webmin directories hanging around.

---

### Post by jimdhall2 on 2006-07-04
THANK YOU, THANK YOU, THANK YOU!!!!!  Nice job, your instructions worked like a charm!!!

---

### Post by xchrisday on 2006-07-09
error message:

E: Couldn't find package libauthen-pam-perl

Any ideas, have checked over repos, will check again.

Edit: working, my bad, such a newbie I couldnt follow a guide on enabling repos :p

Fantastic guide, thanks for your help

---

### Post by h3mlock on 2006-07-10
Is webmin in the repositories now?  I can't seem to find it there.

---

### Post by blkc4us on 2006-07-12
I did install it, accessed it but it seems that everything is not linked properly. It can only access the system. Everything else is broken link. Do you have any idea what went wrong.

I installed Apache2, mysql, php, perl, samba, smbfs and then webmin

---

### Post by jimp180 on 2006-07-12
Hi all I just installed webmin from the tarball (webmin-1.290.tar.gz) and like others I'm reading about, after rebooting webmin wont start. Has anyone figured this out yet?

> **crmanski said:**
> Does the file:  /etc/init.d/webmin
get created during the installation?

Yes
> If yes then maybe it is not executable. To test this type 

Code:
sudo /etc/init.d/webmin start
No errors doing this just returns to prompt as if it has started but the it isn't. if I do 
```
sudo /etc/init.d/webmin restart
```
I get
```
Stopping Webmin server in /tmp/webmin-1.290
/etc/webmin/stop: line 4: kill: (4941) - No such process

```

Any Ideas?

---

### Post by jimp180 on 2006-07-12
ok I was just looking over what I posted and I see the problem,
> Stopping Webmin server in [COLOR="DarkOrange"]/tmp/webmin-1.290[/COLOR]
 of course it can't start or stop anything in tmp since its been wiped on boot 
NOW what do I do?

---

### Post by jimp180 on 2006-07-12
Ok this is fixed 
here is the solution for anyone that went the same path as I did.
If you downloaded the tarball to your /tmp directory and Unpacked it then entered the /tmp/webmin-1.290 and ran```
./setup.sh
``` follow those steps again except this time when you enter the webmin-1.290 directory run this instead ```
./setup.sh /usr/local/webmin
```this will install it in /usr/local/webmin instead of /tmp/webmin-1.290 (which gets wiped when you reboot) since you allready had it installed it will find the config file and update with new directory info.
Hope this helps someone

---

### Post by SlowYaRoll on 2006-07-12
During my usual dedicated Linux surfing time, I went to webmin's homepage.  Guess what.  THEY HAVE A DEB PACKAGE FOR WEBMIN!!!

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

I believe this is something fairly new for them, as such there are no instructions on how to install the deb package. . .but who really needs those.  :D

---

### Post by jimp180 on 2006-07-12
> **SlowYaRoll said:**
> During my usual dedicated Linux surfing time, I went to webmin's homepage.  Guess what.  THEY HAVE A DEB PACKAGE FOR WEBMIN!!!

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

I believe this is something fairly new for them, as such there are no instructions on how to install the deb package. . .but who really needs those.  :D
If you install with the package:
Don't forget to change your root password to something useful before you install the package because if my memory serves me right the packages setup webmin using the current root user pass combination and Ubuntu 6.06 dosent set a root password on install or sets one nobody knows so you will either not be able to login to your webmin or anybody will be able to login to your webmin.

---

### Post by blkc4us on 2006-07-13
Thanks for the tutorial. You're great!

---

### Post by kileen on 2006-07-13
Download the .deb package from [www.webmin.com/download](www.webmin.com/download). Use your file browser and point to the saved file. Right click and use the installer option. The installer will run and install webmin. It will end with a message saying how to use it on [http://yourhostname:10000](http://yourhostname:10000) with root user name and password.

BUT Ubuntu has no root user so in terminal mode use this command:
 
 $ sudo /usr/libexec/webmin/changepass.pl /etc/webmin root your-new-password

YES it is /usr/libexec/webmin....and not /usr/share/webmin...as documented elsewhere in forum.

---

### Post by rmwarriner on 2006-07-19
I used the deb package and it worked well. Just in case anyone isn't familier with installing a deb, use the following cmd (assuming su access):

To install .deb file:
dpkg -i <package filename>.deb

To uninstall .deb file:
dpkg -r <package name>

I know this is mentioned in any number of places, but it is nice for those who don't know to have the info together with where it applies (rather than having to run another search).

You can set up su by doing this at the command line:

sudo passwd root -> give your sudo password -> change the root password

This will allow access to the actual root account. I realize Ubuntu probably frowns on this type of thing, but there are times when one needs the actual root account. 

One problem (or not) is that when you access something from one of the gnome (I am not sure if this happens in KDE, I use Gnome) menus (i.e. System -> Network), the admin prompt requires *your* password. It seems to retain sudo requirement for those things (if someone knows how to change this that would be great). Of course you can still go to the command line and do everything.

I noticed webmin uses dhcpcd (I think it was) for DNS/DHCP stuff. I am currently using dnsmasq, is there a way to tell webmin to use that instead? 

Also, how does webmin compare to ISPConfig? Thats probably a noob question, so sorry if I offend anyone's sensibilities.

Robert

---

### Post by tivolieselet on 2006-07-20
yes I have now installed it. but I can only get it working if Iam local, NOT from another pc, over the internett. ? anyone?

---

### Post by SlowYaRoll on 2006-07-23
Oh my little grasshopper. . .if only you took the time to login to webmin, go to WEBMIN CONFIGURATION, then go to IP ACCESS CONTROL and select Allow from all addresses, then hit save.  That should do the trick for you.

"I had no clue as to why the frisbe got bigger and bigger. . . and then it hit me"
:)

---

### Post by WheelDweller on 2006-07-25
Does the .deb they offer not work?

---

### Post by crmanski on 2006-07-25
> **WheelDweller said:**
> Does the .deb they offer not work?
Personally, I have not tried it. The deb they offer should work, but you have to enable the root account, which is disabled by default. I prefer my method :D

---

### Post by TonyD on 2006-08-03
thanks .it works great.

thanks for the effort and time putting it together.

may the force be wth you

---

### Post by SlowYaRoll on 2006-09-01
> **SlowYaRoll said:**
> Oh my little grasshopper. . .if only you took the time to login to webmin, go to WEBMIN CONFIGURATION, then go to IP ACCESS CONTROL and select Allow from all addresses, then hit save.  That should do the trick for you.

"I had no clue as to why the frisbe got bigger and bigger. . . and then it hit me"
:)
Here's another way to install webmin, which is very simple.  This should apply to all Ubuntu versions, but then again, I'm still very new to Linux.

Download the webmin DEB file from Webmin's website.
  ([http://www.webmin.com](http://www.webmin.com))
  ([http://www.webmin.com/download.html](http://www.webmin.com/download.html))

Go to the directory where you've downloaded the DEB file.
  (i.e. cd /home/usernamehere/Desktop/)

Run the dpkg --install command on the DEB file you've downloaded.
  (i.e. sudo dpkg --install webmin_1.290.deb)

----This will take a few moments to install----

At this point, webmin is installed and running.  You may access Webmin via your web browser.
  ([http://localhost:10000)](http://localhost:10000)).

You'll be prompted for a username and password.  By default, Webmin copies your system's root password as the Webmin root password.  Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
  sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.

---

### Post by kpm on 2006-09-21
When I follow these instructions, I get the same error... perhaps 
```
user@server:~$ wget http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb
--21:10:45--  http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb
           => `webmin_1.300_all.deb'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,056        --.--K/s

21:10:45 (108.76 KB/s) - `webmin_1.300_all.deb' saved [12056]

user@server:~$ ls
webmin_1.300_all.deb
user@server:~$ sudo dpkg --install webmin_1.300_all.deb
Password:
dpkg-deb: `webmin_1.300_all.deb' is not a debian format archive
dpkg: error processing webmin_1.300_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 webmin_1.300_all.deb
```
So maybe something is wrong with the package since 1.290??

---

### Post by Silver Surfer on 2006-10-01
> **kpm said:**
> When I follow these instructions, I get the same error... perhaps 
```
user@server:~$ wget http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb
--21:10:45--  http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb
           => `webmin_1.300_all.deb'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,056        --.--K/s

21:10:45 (108.76 KB/s) - `webmin_1.300_all.deb' saved [12056]

user@server:~$ ls
webmin_1.300_all.deb
user@server:~$ sudo dpkg --install webmin_1.300_all.deb
Password:
dpkg-deb: `webmin_1.300_all.deb' is not a debian format archive
dpkg: error processing webmin_1.300_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 webmin_1.300_all.deb
```
So maybe something is wrong with the package since 1.290??

I get the exact same error.  I just installed a new LAMP server and updated all the packages too.  Trying to get webmin installed gives me the above error.

---

### Post by blkish on 2006-10-02
hi all,

the problem is in the link you are asking wget to retrieve.

-- quick fix:

```
wget http://kent.dl.sourceforge.net/sourceforge/webadmin/webmin_1.300_all.deb
dpkg -i webmin_1.300_all.deb
```



-- explanation:

the link in question

[http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb) 

takes you to the sourceforge download mirrors page for the file, from which you must then choose a mirror from which to download the actual file.

so wget downloads an html file rather than a .deb package, and dpkg objects about the file type.

this is often a confusion when downloading files from sourceforge with wget.

good luck

blkish

---

### Post by hellmet on 2006-10-12
thanks a ton bro...

---

### Post by goatcatcher on 2006-11-09
Thanks for this how-to - works a treat.

But is it possible to run webmin under a different virtual host?

Eg: I have [www.mydomain.com](www.mydomain.com) pointing to my website
and admin.mydomain.com pointing to a different webroot, available only within the local network, where phpmyadmin and awstats are located. Both are on the same IP address.

Webmin has installed inself under [www.mydomain.com:10000](www.mydomain.com:10000), but I'd rather it was something like admin.mydomain.com/webmin

Any ideas?

---

### Post by crmanski on 2006-11-09
I'm pretty sure you can. I have not done it. If you want to access it from port 80 you would have to setup a reverse proxy in that virtual hosts config in apache.

This code might do it if you have mod proxy html enabled...

```
	 
<IfModule mod_proxy.c>
	ProxyRequests Off
	<Proxy *>
		Order deny,allow
		Allow from all
	</Proxy>
	ProxyPreserveHost On
	ProxyPass /webmin https://YourIP:10000/
	ProxyPassReverse /webmin https://YourIP:10000/
</IfModule>

```

This page talks about apache proxying in detail...
[http://www.wlug.org.nz/ApacheReverseProxy](http://www.wlug.org.nz/ApacheReverseProxy)

> **goatcatcher said:**
> Thanks for this how-to - works a treat.

But is it possible to run webmin under a different virtual host?

Eg: I have [www.mydomain.com](www.mydomain.com) pointing to my website
and admin.mydomain.com pointing to a different webroot, available only within the local network, where phpmyadmin and awstats are located. Both are on the same IP address.

Webmin has installed inself under [www.mydomain.com:10000](www.mydomain.com:10000), but I'd rather it was something like admin.mydomain.com/webmin

Any ideas?

---

### Post by Abhi Kalyan on 2006-11-13
is it true that webmin has been added to the official repository's? cause am not able to get it from there.
Waiting for a reply.
Thank you guys once again
Sincerely
Abhi Kalyan

---

### Post by crmanski on 2006-11-13
If you go to [http://packages.ubuntu.com/webmin](http://packages.ubuntu.com/webmin) you will see what versions of ubuntu have the webmin package available

---

### Post by Abhi Kalyan on 2006-11-13
thank you crmanski,
will do

---

### Post by ronnieredd on 2007-01-20
Debian and Ubuntu:
Make sure you change the default port in webmain right away. There are other things that like that port and it may break your webmin install. (Some LDAP thingy I think) 

I also found that if I leave it as is, and install/setup usermin (which runs on port 20000 by default, something breaks on webmin and it won't respond on port 10000 anymore. 
If you try to re-install or uninstall/re-install you may get an error that says something to the effect "port 10000 already in use" (Someone who's having that problem feel free to correct that last entry) 

Here's a couple of commands that may come in useful:
**sudo fuser -n tcp 10001**
This should output something like:
10000/tcp:            5543
(List which process is using tcp port 10000)
From here you can just do 
sudo kill 5543
Then you should be able to install or re-install webmin)
For more socket info you can:
**netstat -l | less**
(display listening server sockets)
(hit the "space key" to move down a page and hit the "q" key to quit)

---

### Post by be4truth on 2007-03-25
This is pretty cool, Works out of the box. Thanks a lot!:popcorn:

---

### Post by hockey97 on 2007-04-09
HI I been going through these post's and I have ubuntu 6.10 and installed webmin but get errors also their was one package that was not found to install it was the 1st package that was supposed to be install  if you look on page 1 where sudo apt-get install right after that the 1st package that package was not found so it never installed.

I also got this error...

root@something..:/home/aaron# dpkg -i webmin_1.330_all.deb
Selecting previously deselected package webmin.
(Reading database ... 108400 files and directories currently installed.)
Unpacking webmin (from webmin_1.330_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
root@somthing...:/home/aaron# sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libauthen-pam-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libauthen-pam-perl has no installation candidate
root@something...:/home/aaron# sudo apt-get install  libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnet-ssleay-perl is already the newest version.
libpam-runtime is already the newest version.
openssl is already the newest version.
perl is already the newest version.
perl-modules is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not going to be installed
          Depends: libmd5-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@something...:/home/aaron# sudo apt-get -f install  libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done

libnet-ssleay-perl is already the newest version.
libpam-runtime is already the newest version.
openssl is already the newest version.
perl is already the newest version.
perl-modules is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not going to be installed
          Depends: libmd5-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or spec

I really need some help on getting it installed and running.

---

### Post by Forum Joe on 2007-04-10
Thanks for this tutorial.  It's been most useful, and works well but I'm having some problems.

First of all, I'm running a Fiesty Fawn beta, (and it's default LAMP server) but I think most things should still work.  The problem I'm getting is the same as a couple of other people in this thread:

**Problem:**Webmin doesn't restart when the server restarts.

After I've installed webmin, I can connect to it fine, and configure away to my hearts content.  However, if I restart my server and then try to connect it the same way I did previously, I cannot establish a connection on port 10000.  Now, if I ssh to my server and execute setup.sh again, I can connect fine.  All good.

Now, in the main webmin config section, there's also a section at the bottom "start at boot time" with options of yes and no, this is set to no.  If I try to set it to "yes" through the web interface, I get an error message "Failed to open /etc/rc.d/init.d/webmin for writing : Bad file descriptor"

Now, there's no such directory /etc/rc.d/init.d/webmin, so I don't know why it's trying to write there.  Very strange, a bug in the webmin code?
Anyway, I created that folder, and clicked the button, it wrote a file "webmin" without an error.  However, this doesn't fix anything, and webmin still doesn't start on boot.

Any ideas?
(note: I'm pretty much a newbie when it comes to Ubuntu, so I'm sure it's something simple.)

---

### Post by crmanski on 2007-04-10
I have not tried fiesty out yet, so I am not sure of the init setup. I think it uses something else now. In edgy I noticed that there was a /etc/init.d/rc.local present. If that is in feisty how about adding this to the end of that file...

```
/etc/webmin/start
```

---

### Post by crmanski on 2007-04-11
hockey97,
I wonder if you could post the contents of your /etc/apt/sources.list? I'm wondering if the correct repositories are enabled.

---

### Post by SlowYaRoll on 2007-05-01
> **Forum Joe said:**
> Thanks for this tutorial.  It's been most useful, and works well but I'm having some problems.

First of all, I'm running a Fiesty Fawn beta, (and it's default LAMP server) but I think most things should still work.  The problem I'm getting is the same as a couple of other people in this thread:

**Problem:**Webmin doesn't restart when the server restarts.

After I've installed webmin, I can connect to it fine, and configure away to my hearts content.  However, if I restart my server and then try to connect it the same way I did previously, I cannot establish a connection on port 10000.  Now, if I ssh to my server and execute setup.sh again, I can connect fine.  All good.

Now, in the main webmin config section, there's also a section at the bottom "start at boot time" with options of yes and no, this is set to no.  If I try to set it to "yes" through the web interface, I get an error message "Failed to open /etc/rc.d/init.d/webmin for writing : Bad file descriptor"

Now, there's no such directory /etc/rc.d/init.d/webmin, so I don't know why it's trying to write there.  Very strange, a bug in the webmin code?
Anyway, I created that folder, and clicked the button, it wrote a file "webmin" without an error.  However, this doesn't fix anything, and webmin still doesn't start on boot.

Any ideas?
(note: I'm pretty much a newbie when it comes to Ubuntu, so I'm sure it's something simple.)


I'm a linux newb too.  I started using Debian about a year and a half ago.  If I remember correctly, Debian based distros (which Ubuntu is) use /etc/rc2.d as the startup directory.  Have you tried this?  You may have to manually create the link to start up webmin

```
cd /etc/rc2.d
```
```
sudo ln -s /etc/init.d/webmin S99webmin
```

Then restart the server and see if webmin starts for you

```
sudo shutdown now -r
```

I hope that helps.  

Let me know if it works

---

### Post by unique_leader on 2007-09-09
how to config proxy squid,iptables, router in webmin . i'm newbie please give me a tutorial

---

### Post by SlowYaRoll on 2007-09-10
I'm not sure this is the best place to ask for a tutorial on squid, iptables, and router as this is just a HOWTO / Help section for getting Webmin up and running.

There is a tutorial for Squid
[http://ubuntuforums.org/showthread.php?t=320733&highlight=squid](http://ubuntuforums.org/showthread.php?t=320733&highlight=squid)

If you do some googling, you'll find stuff for other things.
IP TABLES
[http://rimuhosting.com/howto/firewall.jsp](http://rimuhosting.com/howto/firewall.jsp)
[http://www.linuxquestions.org/questions/showthread.php?t=546689](http://www.linuxquestions.org/questions/showthread.php?t=546689)

Never hurts to explore as it'll give you a better understanding so you won't really need a HOWTO guide for that specific tool.  It's sort of like driving a car. . .as long as you know how, it doesn't really matter what sort of car it is.

Egadz. . .I think I just pulled a RTFM without saying RTFM  I'll now go ask for forgiveness
:(

---

### Post by carthage on 2009-01-20
thx a lot for this great how to. I've try this on intrepid and it works just fine.

PS:first you have to add third party repository to do this sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules ;)

---

### Post by Longun on 2010-07-21
Great guide.  Saves stuffing a bloated GUI on a server install but helps people like me who are still learning the command line.

---

### Post by SlowYaRoll on 2010-07-26
Yowsers. . .almost forgot about this thread.  The webmin deb has improved greatly since the beginning of this thread.  You don't have to do as much mucking around.  Simply download the deb to the server then try to install it.  It'll fail due to some dependency issues but once you resolve those, it's good to go.

---

### Post by hfraz on 2010-08-03
> Here's a couple of commands that may come in useful:
**sudo fuser -n tcp 10001**
This should output something like:
10000/tcp:            5543
(List which process is using tcp port 10000)
From here you can just do 
sudo kill 5543
Then you should be able to install or re-install webmin)
For more socket info you can:
**netstat -l | less**
(display listening server sockets)
(hit the "space key" to move down a page and hit the "q" key to quit)

thank you so very much..

after removing webmin, I was unable to reinstall. Killing the process tied to this port worked like a charm. Thanks again.

---

