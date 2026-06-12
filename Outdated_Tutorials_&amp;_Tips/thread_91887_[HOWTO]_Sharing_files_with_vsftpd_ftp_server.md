---
title: "[HOWTO] Sharing files with vsftpd ftp server"
date: 2005-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by merinda on 2005-11-18
Vsftpd is the most easy ftp server to setup. 

Installing vsftpd:
```

sudo apt-get install vsftpd

```

The configuration file for vsftpd is located in /etc/vsftpd.conf. The default configuration is a little bit paranoid, not so usable for file sharing. So use this configuration instead:
```

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=samurai
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

```

Don't forget to backup before you use this configuration.
```

sudo cp /etc/vsftpd.conf /root/

```

Now we must make writable directory for anonymous user.
```

cd /home/ftp
sudo mkdir opendir
sudo chmod 777 opendir/

```

Ok, I explain this. In my local system, I have user named 'samurai'. With this configuration, I can log into ftp server with local user, that is 'samurai'. 'samurai' can go anywhere, create files, delete files, etc as long as he has sufficient permission.

With this configuration I can log into ftp server with anonymous user ( without username and password ). After logging in, the anonymous user jailed in /home/ftp directory ( pointed by anon_root ). I can't go outside. I can download files from /home/ftp directory but not create, delete anything from this directory. But I can write and delete files in opendir. If I write files in opendir or upload files in opendir, the files automatically belong to 'samurai' user.

To run this server:
```

sudo /etc/init.d/vsftpd start

```
To stop it:
```

sudo /etc/init.d/vsftpd stop

```
To restart it:
```

sudo /etc/init.d/vsftpd restart

```

Now it is usable for file sharing, right?!!!!

---

### Post by Ozitraveller on 2005-11-20
Is is necessary to make any changes to /etc/inetd/inetd.conf?
 
e.g
ftp stream tcp nowait root /usr/sbin/tcpd /usr/sbin/vsftpd

---

### Post by merinda on 2005-11-20
I use vsftpd here as standalone daemon so I don't touch inetd.conf.

Before configuring vsftpd itself, you must decide whether to run it as a standalone d&#230;mon or by way of a super-server, inetd or xinetd. In previous versions of vsftpd, its developer recommended using it with xinetd due to xinetd's logging and access-control features. However, vsftpd versions 1.2 and later have native support for most of those features. For this reason, Evans now recommends that vsftpd be run as a standalone d&#230;mon. In addition, a performance cost is associated with using inetd or xinetd. The cost isn't warranted if your system is to be a dedicated FTP server or if you anticipate FTP comprising a significant percentage of your system's activity.

---

### Post by Ozitraveller on 2005-11-20
[quote=merinda]I use vsftpd here as standalone daemon so I don't touch inetd.conf.
 
Before configuring vsftpd itself, you must decide whether to run it as a standalone dæmon or by way of a super-server, inetd or xinetd. In previous versions of vsftpd, its developer recommended using it with xinetd due to xinetd's logging and access-control features. However, vsftpd versions 1.2 and later have native support for most of those features. For this reason, Evans now recommends that vsftpd be run as a standalone dæmon. In addition, a performance cost is associated with using inetd or xinetd. The cost isn't warranted if your system is to be a dedicated FTP server or if you anticipate FTP comprising a significant percentage of your system's activity.[/quote]
 
Thanks Merinda. 
 
I was surprised at how simple it was to install and setup! <5mins!!
 
In the long run it could be a standalone server, but at the moment I'm just trying things out.
 
Would it be possible to add some example upload and down ftp session output to this howto?

---

### Post by Nano on 2005-11-22
I wouldn't suggest to set write_enable=YES unless you explain people what it does.

:)

---

### Post by merinda on 2005-11-25
```

I wouldn't suggest to set write_enable=YES unless you explain people what it does.

```

He he, I should have to write that this is for sharing files where you can read and write. As I remembered, the default configuration can get you share files with people, only it's very limited. Only anonymous.

```

Would it be possible to add some example upload and down ftp session output to this howto?

```

I don't understand your statement.

---

### Post by GuruMadMat on 2005-11-28
i get this error
```

    SmartFTP v1.5.990.26
    Resolving host name "192.168.2.100"
    Connecting to 192.168.2.100 Port: 21
    Connected to 192.168.2.100.
220 Welcome to blah FTP service.
    USER anonymous
331 Please specify the password.
    PASS (hidden)
500 OOPS: vsftpd: refusing to run with writable anonymous root
500 OOPS: child died
    Cannot login waiting to retry (30s)...
    Server closed connection


```


and my conf file is this
```

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=gurumadmat
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/var/www


```

can someone make me a good config file?
i want to log on from anywhere with my local username and password

and how do i change the port to 25001 ?

---

### Post by bierpullen on 2005-11-28
Thanks
This is great !!!
Works !!!! =D>  

------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu](http://www.antarctica-rbak.nl/ubuntu)

---

### Post by Phrostay on 2005-12-02
This was an awesome guide!!! I had so much trouble with proftpd & was pulling my hair out, all I wanted to do was share files & samba wasn't very happy with my macintosh. vsftpd was working in minutes :D. However I have a iMac G5. Using the finder to connect to my Ubuntu machine (Command K) it mounts in NFS format and I cannot place files into the Ubuntu FTP directory even though I issued a "chmod 777". The only way for me to access the Ubuntu machine is through Transmit an FTP client for Mac OS X. I'm at a loss  :confused: but thanks for this great guide anyway.

---

### Post by ruffneck on 2005-12-02
This is a nice little guide. I've been using vsftpd for sometime now myself and I like it. 

One thing I will mention is that if you want to share with people not on your local network i.e. someone over the internet (a friend etc.), you would have to forward ports 20-21 through your router (if you have one) and then open up those ports on your ubuntu box to recieve the connection. A safer way (not taking into consideration [ip spoofing]("http://www.webopedia.com/TERM/I/IP_spoofing.html")) is to get the ip address of the friend and only allow incoming connections on the above said ports from that paritcular ip.

---

### Post by kasemodz on 2006-01-17
Alright I tried setting up my vsftpd and whenever I tried to connect it would always give me this error. > The connection was refused when attempting to contact xxx.xxx.xx.xxx Here is my config file. I tried other ports but would get the same problem.
> # Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_612=YES
chown_uploads=YES
chown_username=admin
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/media/hda4/ftp

---

### Post by vav on 2006-01-30
I tried running vsftpd and it ran ok for ftp connections.

However, I heard that ftp logins send passwords in cleartext, so they are available to a sniffer.

I went through the documentation and found three options, ssl_enable=YES, force_local_logins_ssl=YES and force_local_data_ssl=YES. I put these into vsftpd.conf and restarted the ftp server as has been given in the howto. But now from a remote computer it just says Connection refused, whether I try ftp or sftp.

What could be the problem?

--vav

---

### Post by GabrielWolff on 2006-02-24
When trying to open vsftpd through the terminal I get
```
gabriel@ubuntu:~$ sudo vsftpd
500 OOPS: could not bind listening IPv4 socket
gabriel@ubuntu:~$
```

Whatwhat?

G

---

### Post by jjjjjjj on 2006-02-24
I have copied the example exactly and only changing the samurai to my user.
I cannot download files from the internet using internet explorer.
Using Passive makes no difference. 
I have stopped, started, restarted and reloaded.  All to no avail.
:(
But i did learn the start | stop | restart AND reload options for 
sudo /etc/init.d/vsftpd *option*

---

### Post by saads on 2006-03-20
1) What if i want to share folders that are not under /var/ftp?  Can I just symlink to them?

2) And how can I enable secure ftp on this setup (SSL)?

---

### Post by SK1 on 2006-04-03
After reading the HOW-To for VSFTPD I am still having trouble understanding some of the concepts. As I am a relative Linux newbie, I am finding it difficult understand the various guides on VSFTPD that are out there.

I have installed VSFTPD and can start and stop the server as well as connect to it anonymously. However, I am not sure how I setup the server to:

1) Disallow anonymous access
2) Allow access to specific (external) users only. (In this regard, how and where to setup the users i.e. are the users added as local users in the OS?)
3) Set passwords for the users
4) Set a common FTP directory for all users that is on a different hard disk than the one on which the Ubuntu OS is installed
5) Allow users read access only

I would greatly appreciate help with regard to to the above questions.

---

### Post by baalho on 2006-04-07
my ftp server is running fine, using the code posted in the howto.
here is what i want to do, can you suggest a code for it.
1. I want to disable anonymous access (i think i just have to comment out that part).
2. I only want user to download, no upload (i might be able to manage that)
3. I want to create a username and password (no clue how to do it)
4. I am behind a router, I have forwarded port on my router. What do i do in Ubantu.
5. I want the user to have access to certain directory in my fat32 mount (no clue how to do that)
6. All the access will be from friend on the internet, so no need to have local access.
7. my friend uses windows, so do i just give him my real ipaddress and he can put [ftp://ipadd](ftp://ipadd) on internet explore. My friend is as much a noob as i am and only uses windows.
thanks for any help.

---

### Post by earth_walker on 2006-04-11
I set up vsftpd to play around with anonymous ftp. Everything worked fine, except that now I want to turn it off. However, no matter what I do, [ftp://localhost](ftp://localhost) is still showing the contents of the ftp directory. I have:

1. disabled both anonymous and local user settings in vsftpd.conf and /etc/init.d/vsftpd restart

2. /etc/init.d/vsftpd stop

3. uninstalled vsftpd completely using synaptic.

However, [ftp://localhost](ftp://localhost) still shows my ftp directory, and System=>Services shows that vsftpd is active, and vsftpd is still in /etc/init.d/. However, typing vsftpd in the command line says command not found.

I've secured my system by disabling the port forwarding to the server, but i'm confused as to why [ftp://localhost](ftp://localhost) is still working. Any help?

---

### Post by malcolmb on 2006-04-14
For one of the errors that GuruMadMat posted on and that i got as well: 

> 500 OOPS: vsftpd: refusing to run with writable anonymous root
500 OOPS: child died
    Cannot login waiting to retry (30s)...
    Server closed connection

I fixed the same error when i got it by on the last line of the posted conf file to:

anon_root=/home/ftp/

(added the ending / )

edit: infact it wasn't that at all, i just logged on with my regular user name and password instead of trying to do it using anonymous with no password

---

### Post by airtonix on 2006-07-19
**GuruMadMat,** I think you need to have> anon_root=/home/ftpin your vsftp.conf file(the dir get created when you create the ftp user in system admin.),  and then in the folder of one of your local users put a symlink to /var/www

** Earth_walker**, well since you didnt use the command ine method of removing vsftp, you wouldn;t be able to tell if the server actually was stoppped. one way is to > pgrep vsftp this will show an id of some sort, that is related to the program you query for. 
To kill the program, > sudo killall vsftpd.

** Others,**
Users are controlled through the usual process of adding a user to the system, via the system menu -> users and user groups....just like in windows use management with the my-computer-management snap-in.

To share a particluar harddrive or a folder, make a symlink to it.
easist way to do this (that i can think of right now) is :
[LIST=1]
[*]alt+f2
[*]gksudo nautilus /home/ftp
[*]then shift+alt drag the icon of the folder/drive you want to share into the /home/ftp folder.
[*]check your permissions on the links....[/LIST]

---

### Post by MikkelM on 2006-07-26
Smart. Thanks dude :)

---

### Post by BatteryCell on 2006-08-03
> **Phrostay said:**
> This was an awesome guide!!! I had so much trouble with proftpd & was pulling my hair out, all I wanted to do was share files & samba wasn't very happy with my macintosh. vsftpd was working in minutes :D. However I have a iMac G5. Using the finder to connect to my Ubuntu machine (Command K) it mounts in NFS format and I cannot place files into the Ubuntu FTP directory even though I issued a "chmod 777". The only way for me to access the Ubuntu machine is through Transmit an FTP client for Mac OS X. I'm at a loss  :confused: but thanks for this great guide anyway.

Um, I dont know if your still wondering but once you have your samba up (and your connected to atleast one computer) its pretty easy to add others, for windows just mount a new network drive and for mac, well, do the same thing.  Windows mounting is described in [http://www.ubuntuforums.org/showthread.php?t=202605&page=8&highlight=samba+howto]("http://www.ubuntuforums.org/showthread.php?t=202605&page=8&highlight=samba+howto") (as well how to set samba up) and here is mac:
[http://www.owlnet.rice.edu/FAQ/cache/129.html]("http://www.owlnet.rice.edu/FAQ/cache/129.html")
I beleive that to make it run at startup you have to do that in your user profile, though my sister doesnt let me use her comp. except in dire concequences...

---

### Post by treborblack on 2006-08-30
i'm sure i've followed the instructions to the letter, but i cant connect and to the best of my knowledge it aint even running

i type sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                        [ ok ]

this would make you believe its running but nothing shows up on ksysguard i cant connect. it was a clean install and i've never installed a firewall.

any ideas what i must have done wrong

---

### Post by treborblack on 2006-08-30
on rebooting the computer

this outpit regarding the server comes up which i've photographed

---

### Post by K.Mandla on 2006-10-02
Thanks for the howto. This proved useful for [a lightweight FTP server in a live CD environment]("http://www.ubuntuforums.org/showthread.php?t=268121").

However, in my case I wanted to disallow anonymous logins, and allow only local users to log in (in other words, I had to add user accounts for the logins to the FTP service).

In case that's what you're after, this is what my vsftpd.conf file looked like. ...

```
listen=YES

local_enable=YES
userlist_enable=YES
userlist_deny=NO

chroot_local_user=YES
chroot_list_enable=YES

anonymous_enable=NO
anon_root=/home/ftp/
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO

write_enable=YES

force_dot_files=YES
dirmessage_enable=YES

xferlog_enable=YES
dual_log_enable=YES

connect_from_port_20=YES

ascii_upload_enable=YES
ascii_download_enable=YES

ftpd_banner=Welcome to the FTP server.

secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```
There are a couple of other quirks in there -- I like the dotted up directories included by default, and the dual log option makes a log at /var/log/vsftpd.log -- but otherwise I *think* this should work for just about anyone.

Don't forget to make lists of approved users in vsftpd.user_list and vsftpd.chroot_list.

Cheers! :)

---

### Post by Kardelen on 2006-10-02
I have done as told in first msg, and get connected with gFTP via anonymous account. Then I wanted to upload sth. It created the directory, however, couldn't create the file. Here is the message:

```
STOR /upload/(25342)Dune_25fps_2CD_Turkce_SubRip_DiVXPlanet/Dune CD1 TR.srt

553 Could not create file.
Loading directory listing /upload/(25342)Dune_25fps_2CD_Turkce_SubRip_DiVXPlanet from server (LC_TIME=en_AU.UTF-8)
```

How could I resolve the problem?

---

### Post by john_spiral on 2006-10-03
Hi,

I've got vsftpd going on my local network (2 machines) one ubuntu one DSL (damm small linux) machine.

I can ftp small binary files from the ubuntu machine down onto the DSL machine but the ftp server (runnig under Ubuntu) gives the following error on a large 700 meg .iso file:

550 Failed to open file?

any ideas if there is a large file config section?

Same problem even if I open an ftp session on the server (ubuntu machine)

thanks

John

---

### Post by barret on 2007-02-01
> **K.Mandla said:**
> Thanks for the howto. This proved useful for [a lightweight FTP server in a live CD environment]("http://www.ubuntuforums.org/showthread.php?t=268121").

However, in my case I wanted to disallow anonymous logins, and allow only local users to log in (in other words, I had to add user accounts for the logins to the FTP service).

In case that's what you're after, this is what my vsftpd.conf file looked like. ...

```
listen=YES

local_enable=YES
userlist_enable=YES
userlist_deny=NO
[B]
chroot_local_user=YES
chroot_list_enable=YES[/B]

anonymous_enable=NO
anon_root=/home/ftp/
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO

write_enable=YES

force_dot_files=YES
dirmessage_enable=YES

xferlog_enable=YES
dual_log_enable=YES

connect_from_port_20=YES

ascii_upload_enable=YES
ascii_download_enable=YES

ftpd_banner=Welcome to the FTP server.

secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```
There are a couple of other quirks in there -- I like the dotted up directories included by default, and the dual log option makes a log at /var/log/vsftpd.log -- but otherwise I *think* this should work for just about anyone.

Don't forget to make lists of approved users in vsftpd.user_list and vsftpd.chroot_list.

Cheers! :)

Check out the man page for vsftpd:

[I]chroot_list_enable
    If activated, you may provide a list of local users who are placed in a chroot() jail in their home directory upon login. **The meaning is slightly different if chroot_local_user is set to YES.** In this case, the list becomes a list of users which are NOT to be placed in a chroot() jail. By default, the file containing this list is /etc/vsftpd.chroot_list, but you may override this with the chroot_list_file setting.

    Default: NO 
chroot_local_user
    If set to YES, local users will be (by default) placed in a chroot() jail in their home directory after login. Warning: This option has security implications, especially if the users have upload permission, or shell access. Only enable if you know what you are doing. Note that these security implications are not vsftpd specific. They apply to all FTP daemons which offer to put local users in chroot() jails.

    Default: NO [/I]

So if you have both set to YES, whatever local user that logs in can view every folder/file on your system. I set chroot_local_user to NO and now it locks the user to their home directory. Other than that thanks for the config file, definitely helped.

---

### Post by danielprice on 2007-02-15
Hi all,
As a bit of a newb to linux, I was wondering what was the best way to get vsftpd to start at boot-up, preferably before a user even logs into the system. Is this even possible?

Thanks.

---

### Post by talkin on 2007-05-07
Thanx for this how-to. But i have such trouble:
      I've directrory "ubload" for  upload at the /home/ftp/. My vsftpd.conf is exactly the same as this howto's is. But if someone uploads directory with some files to my "upload" directory, then this directory and all files in it beginn belong to user named "ftp" with "nogroup" group which doesn't even exist.  So I've to change file mode manually to even read files in that directory. But it works fine if f_**iles**_ are uploaded to "upload". Such files belong to me, and there're no problems with reading & writing them.
      I've read "man vsftpd.conf" but couldn't find anything to solve such problem (may be i missed something :) )
      Any suggestions? :confused:

---

### Post by CLI-Linux on 2007-06-08
Also, remember you need to include the:

```

anon_other_write_enable=YES

```

as stated above.

I found out you can't delete anything over ftp unless this is included.


Also, any ideas on how to change permissions automatically on upload?  Right now, the read/write/execute is only for the uploading user.  Is there any way to automatically have it read/execute for groups and others?

******EDIT**********
Again, answered my own question here.  Using "local_umask=022" made sure everything that uploaded was readable.

---

### Post by CLI-Linux on 2007-06-08
> **danielprice said:**
> Hi all,
As a bit of a newb to linux, I was wondering what was the best way to get vsftpd to start at boot-up, preferably before a user even logs into the system. Is this even possible?

Thanks.

You could use sysv-rc-conf.  This is like a Debian version of the chkconfig on Fedora.  Personally, I haven't used it, but I hear it has perks over chkconfig.  Right now, I use Webmin.  I know that the fun of Linux is in the CLI.  But being an ease-of-use kinda guy, I like that Webmin handles all of my servers (except vsftp unfortunately) and most of the System options from a web interface.  Saves a lot of time.  Also, I think by default VSFTP starts at boot up.

---

### Post by Leonin on 2007-07-09
Ok, I have done what it says in the Howto, but I cant login. 
Im using gFTP to try my FTP. but everytime I get connection refused. Any ideas. Oh and while im at it, is there a easy way to show what IP im having?

---

### Post by moon2js on 2007-09-26
> **Phrostay said:**
> This was an awesome guide!!! I had so much trouble with proftpd & was pulling my hair out, all I wanted to do was share files & samba wasn't very happy with my macintosh. vsftpd was working in minutes :D. However I have a iMac G5. Using the finder to connect to my Ubuntu machine (Command K) it mounts in NFS format and I cannot place files into the Ubuntu FTP directory even though I issued a "chmod 777". The only way for me to access the Ubuntu machine is through Transmit an FTP client for Mac OS X. I'm at a loss  :confused: but thanks for this great guide anyway.

In case anyone else tries to FTP with the Mac Finder, you won't be able to upload. (You'll only get "cannot be modified" whereas any other client will work fine). I've been trying to figure out why it doesn't work and it turns out the Apple software has a design flaw so a third-party client is necessary (unless you want to dig into the Terminal).

---

### Post by leninkster on 2007-10-06
> **malcolmb said:**
> For one of the errors that GuruMadMat posted on and that i got as well: 



I fixed the same error when i got it by on the last line of the posted conf file to:

anon_root=/home/ftp/

(added the ending / )

edit: infact it wasn't that at all, i just logged on with my regular user name and password instead of trying to do it using anonymous with no password

The real problem is there seems to be a bug in VSFTPD.

The line that causes all the errors is CONNECT_FROM_PORT_(ANYTHING)=??

remove the line completely and the problem magically disappears.

It seems to do the same thing if you have any of these directives in the file too
CHOWN_UPLOADS
LOCAL_ENABLE  (or any other local settings If anonymous enable is set to yes)

---

### Post by galv on 2007-11-23
Is this tutorial still valid for Gutsy?

Thanks

---

### Post by gigaferz on 2007-12-08
[http://ubuntuforums.org/showthread.php?t=218630&highlight=vsftp](http://ubuntuforums.org/showthread.php?t=218630&highlight=vsftp)

try that first, they show a workaround for gutsy, the comeback an edit your file for setting it up lik ethis, 
if you do not edit the config file, you will need to log in to the server computer with username and password of that computer,

oops my bad, actually i was thinking of freenx, but yes it should work.

---

### Post by Mike V on 2008-02-15
hi, I have like three days trying to set up vsftpd with no little or no success at all, Im trying to do the following:

user anonymous: read several folders, but dont write anything, I will mount the folders like you explained earlier.
my local user: full access to /home/user name

I reached this configuration so far:
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=mike
idle_session_timeout=300
data_connection_timeout=120
ftpd_banner=Welcome to Mike's FTP server
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/home/mike
force_dot_files=YES
hide_ids=YES
max_per_ip=1
max_clients=6
pasv_min_port=1025
pasv_max_port=1125

with this I can connect locally, (ftp localhost) and it works, but right now Im not in my home and I cant access the server, the connection is working because I can see my page and access to my box via ssh and scp, any advice? Im I doing something wrong?

Thnx in advance folks

---

### Post by Niklas Schröder on 2008-02-18
But after it's all set up, how do I use an FTP client like FileZilla to access/upload/download files?  And can I use a similar configuration to host a web page?

---

### Post by Dr_Snapid on 2008-04-13
Is it possible to view stats on users? I'd like to see each user's transfer in MB, last session etc. Is there any way of doing this?

---

### Post by nickr1977 on 2008-07-01
I am having trouble when uploading media files. .mov, .m4v.  The upload works fine, but the download, I get a 550 failed to open error.

Anyone have any ideas? I have the setup as totally anonymous and it should be working but it is not.

Any ideas?

Thanks,

---

### Post by Sn3ipen on 2008-07-10
How can i add more users?

---

### Post by chronographer on 2008-07-10
I found that most errors, 550 possibly included are related to permissions, check that these are set correctly including who owns the shared folders.

---

### Post by jmac05r1 on 2008-08-19
ok, I followed this "how to" my question is, how do I use it? Iam semi new to linux.  I am trying to connect from my work pc to my home server using vsftpd, I have some files on my work pc that I would like to put on my server.  I have installed and configured VSFTPD onto my server box.  Can someone please help? My work pc I have tried vsftp username@ipaddress? May someone please help me.????

---

### Post by Dr_Snapid on 2008-08-19
If you want to send files to your FTP server you need a FTP client. If you use X then you may want to try gftp. (sudo apt-get install gftp) Use the work IP address as the host, your username and your password and click connect. From there on it's pretty simple. You must have set up port forwarding at work though so your port 21 goes to the server's internal IP in the network.

You can also FTP from the command line.

---

### Post by jmac05r1 on 2008-08-19
by using ftp, that is not secured correct?? Iam trying to do all this secured.

---

### Post by Dr_Snapid on 2008-08-19
> **jmac05r1 said:**
> by using ftp, that is not secured correct?? Iam trying to do all this secured.
No ftp is not a secure protocol. Secure ftp is very confusing for beginners because sftp and ftp-ssl are not the same. Personally I just encrypt my data using encrypted compression (zip) and then transfer the encrypted files over unsecured ftp. The data is just as safe IMHO

---

### Post by jmac05r1 on 2008-08-20
> **Dr_Snapid said:**
> No ftp is not a secure protocol. Secure ftp is very confusing for beginners because sftp and ftp-ssl are not the same. Personally I just encrypt my data using encrypted compression (zip) and then transfer the encrypted files over unsecured ftp. The data is just as safe IMHO


By doing that, passwords and username are still sent non encrypted. The only thing that is secured is the data that you send encrypted.

---

### Post by Dr_Snapid on 2008-08-20
> **jmac05r1 said:**
> By doing that, passwords and username are still sent non encrypted. The only thing that is secured is the data that you send encrypted.

yep, thats right. so if someone sniffs you user/pass, they will get access to the ftp server, but not to your data. not as good as a secure connection, of course.

---

### Post by jmac05r1 on 2008-08-20
> **Dr_Snapid said:**
> yep, thats right. so if someone sniffs you user/pass, they will get access to the ftp server, but not to your data. not as good as a secure connection, of course.

yep, very true, but in my case I have files all over the place. "Not a good habit" Dont have alot of time to put my files in a truecrypt container or something close to the matter thats why I like to use sftp or scp. 

By the way I finally have scp working correctly on any windows box.  This is how I have it going, I first googled pscp or putty, ither one will take you to the download page of pscp.exe and putty.exe..  [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

download pscp.exe and put it to a drive that your cmd defaults to.. example. On your windows box click, start, run, type cmd, if your in your C: then put pscp.exe into your C:.  Once installed open your command prompt type in pscp.exe -scp username@ipaddres:/your/file C:     and everything should work fine. if you want to move a file from a windows box use the command " pscp.exe -scp filename username@ipaddress:/where/to/put/it"  use pscp.ex -scp -r if moving a folder.  

From there you will be moving files from and to your server fully secured.

---

### Post by DeaDWiZ on 2008-08-30
I have a problem.When i go to download files from another computer i get this error:
> &#65279;Could not read from transfer socket: ENOBUFS - Out of memory

I have free ram so i do not think that is a ram problem..
> $free -m
             total       used       free     shared    buffers     cached
Mem:           503        380        123          0          2         74
-/+ buffers/cache:        303        200
Swap:          321         78        243


---

### Post by rogers45 on 2008-11-23
Great guide thanks!

But i have one qustion wen the anonnumous user uppload files i cant not got this file in the ftp server,

The file belongs to user ftp? How to fix this?

//Regards Roger

> opendir. If I write files in opendir or upload files in opendir, the files automatically belong to 'samurai' user

---

### Post by rlischer on 2009-02-12
Thanks for this!  Worked like a charm.

---

