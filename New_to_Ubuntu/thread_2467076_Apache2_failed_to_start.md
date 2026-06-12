---
title: "Apache2 failed to start"
date: 2021-09-15
forum: New to Ubuntu
---

### Post by fausto99 on 2021-09-15
Yesterday I installed Apache and got the “it works” page using localhost in my browser. Today it wont start. Being new to Linux I don't have the first idea on where to start. I've tried removing and re-installing Apache using the Muon Package Manager but no joy.

Any suggestions on where to start?

---

### Post by ActionParsnip on 2021-09-15
What is the output of:
```

ps -ef | grep apache | grep -v apache
apt-cache policy apache2
lsb_release -a
uname -a

```
Thanks

---

### Post by guiverc on 2021-09-15
Question also appears to be asked here - [https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727](https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727)

---

### Post by fausto99 on 2021-09-15
```
ricobasso@D620-02:~$ apt-cache policy apache2
apache2:                                                                     
  Installed: 2.4.46-4ubuntu1.1                                               
  Candidate: 2.4.46-4ubuntu1.1                                               
  Version table:                                                             
 *** 2.4.46-4ubuntu1.1 500                                                   
        500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu hirsute-security/main amd64 Packages
        100 /var/lib/dpkg/status                                             
     2.4.46-4ubuntu1 500                                                     
        500 http://gb.archive.ubuntu.com/ubuntu hirsute/main amd64 Packages  
ricobasso@D620-02:~$ lsb_release -a                      
No LSB modules are available.                                                
Distributor ID: Ubuntu                                                                                                       
Description:    Ubuntu 21.04                                                                                                 
Release:        21.04                                                                                                        
Codename:       hirsute
ricobasso@D620-02:~$ uname -a
Linux D620-02 5.11.0-34-generic #36-Ubuntu SMP Thu Aug 26 19:22:09 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
ricobasso@D620-02:~$ ^C
ricobasso@D620-02:~$ 


```

is this what you needed to see?

---

### Post by fausto99 on 2021-09-15
yes . why are there two Lubuntu fora?

---

### Post by grahammechanical on 2021-09-15
> yes . why are there two Lubuntu fora? 				

The Ubuntu forum has support and discussion sections not only for Ubuntu users but also for users of Linux distributions based on Ubuntu but with a different desktop environment. There is even a section for other operating systems. And there are several sections for specialist categories.

The developers of other distributions based on Ubuntu (we call them Ubuntu flavours) sometimes like to provide their own support channel. It all depends upon how many people are actually involved in helping to develop that distribution as to whether they have the resources to do this.

Your problem is not connected especially to the desktop environment that you are using. It is not a Lubuntu or a Ubuntu issue but an Apache2 issue. Which brings an end to my involvement in this problem.

Regards

---

### Post by fausto99 on 2021-09-16
What was the purpose of asking me to run this code?

---

### Post by deadflowr on 2021-09-16
What code?
You mean the code in post #2?
I would think it's to see some very basic information about the system and the apache2 version installed.

That said if you use the systemctl command as posted in the lubuntu forum thread it might show something useful.
You can use the status option like
```
systemctl status apache2
```

---

### Post by TheFu on 2021-09-16
After running, 
```
sudo systemctl status apache2
```
You can run 
```
journalctl -xe
```
to see any failures.

Typically, failures to start are due to incorrect modification of a vhost file or some other apache settings in /etc/apache2/
or incorrect directory permissions where ever the files are stored.  Incorrect file and directory permissions are an excellent way to have a system be hacked.

Running a web server isn't exactly something that someone new to Unix-like OSes should be doing.  It is fine, provided the service isn't available outside the LAN. We all start learning somewhere, but skipping over basic Unix skills and running a web server is a mistake if the intent is to make a website for the internet.

---

### Post by fausto99 on 2021-09-16
> Running a web server isn't exactly something that someone new to Unix-like OSes should be doing.  It is fine, provided the service isn't available outside the LAN. We all start learning somewhere, but skipping over basic Unix skills and running a web server is a mistake if the intent is to make a website for the internet.

that's not my intention at all. I have a trainer bike in my garage where I run an app called Fulgaz. It uses some sort of mp4 file which streams video to my Apple TV + TV and this controls the drag and tilt of the trainer bike according to the terrain in the video. It's very good but my internet connection is poor.

 My garage is a fair way from my house and I can't have permanent cabling (mains or ethernet) to it. So, the plan is to d/l the mp4 files and stream them locally from a laptop as the Apple TV has very limited storage. I want to re-purpose an old not very powerful laptop, hence the idea to install a light version of Linux (lubuntu). I need Samba to get files on and off a Windows PC and I need Apache to stream to the Apple TV. 

That's it. The laptop will only be on my LAN with very restricted sharing.

---

### Post by fausto99 on 2021-09-27
I think I was having hardware problems. The ethernet connection was intermittent and there was a lot of disc noise. I decided to start again with a new hdd and a quick re-tinning of the ethernet socket and adjacent SM chips on the MB. I then installed Lubuntu to an empty disc, then installed samba and apache2 after an update and upgrade. All is now working except:

I wanted to follow what I thought was the convention that, as I download new rides (usually on my W10 PC), I would write them to a Fulgaz folder in my home folder on the laptop. (That's where the samba share was set up and working). 


I tried renaming the var/www/html folder to html.old and pointed a new html shortcut/folder to my home/fulgaz folder (which has all the ride mp4s in it). Should have worked to my mind - it didn't. I got 403 Forbidden on both machine browsers. I changed ownership and group of the html link folder back and forth from user to root, but it made no difference. 

Does Apache not like links? What the rule here?

---

### Post by SeijiSensei on 2021-09-27
Often symlinks are disabled unless you specify "[FollowSymLinks]("https://httpd.apache.org/docs/current/mod/core.html#options")" like this:
```

<VirtualHost *:80>
[stuff]
<Directory "/var/www/html">
     Option FollowSymLinks
<Directory>
[stuff]
</VirtualHost>

```
You can also make this change by putting a file called .htaccess in the /var/www/html directory with simply the line
```
FollowSymLinks
```

---

### Post by TheFu on 2021-09-27
Linking to files in a HOME directory is generally a bad idea for apache.  There is another method designed for exactly this purpose - the public_html option in apache. Look that up and use it instead.

BTW, samba shares from a HOME that aren't using the very specific [Homes] samba config section are a bad idea. In the last few weeks, we had a guy in these forums will all sorts of issues because he'd decided to share a directory from his HOME using some GUI config tool.  Bad idea.  For everything Samba, configure the server using the /etc/samba/smb.conf file - unless you seek future problems.
```
[homes]
  comment = Home Directories
  hosts allow =  172.22.22.0/24  
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
is a valid stanza for allowing each user to connect to their HOME directory using samba from other systems.  Add that to the bottom of the 
/etc/samba/smb.conf  and restart the daemon.  Probably need to change the IP address subnet for your network. Easy.

For apache ... [https://httpd.apache.org/docs/2.4/howto/public_html.html](https://httpd.apache.org/docs/2.4/howto/public_html.html) Just make the files readable by the apache user ... www-data ... I think. That would probably mean making whatever directory you choose to have the file inside have 755 permissions and the files would need 644 permissions.  However, you should be aware that "streaming" mp4 files isn't as easy as making them available on a web server.  There are specific "streaming" servers ... which know how to let clients move forward and backwards and limit how much data they send to be network-nice.  But it might be fine for your needs. Won't know until you try.

---

### Post by fausto99 on 2021-09-28
SeijiSensei, I'm sure the FollowSymLinks statement is there and enabled but I will check again. I think it was in /etc/apache2/sites-enabled/000-default.conf  if I have I remembered correctly...
There are so many ways and so many locations for configuration settings and I'm easily confused... 

TheFu, I've got a lot of reading to do before I understand your warnings and advice.  However, it all does seem a bit OTT, considering I will be the only user and the system is only powered up for maybe two or three 90 minute bike trainer sessions a week.

p.s I found this [https://priyankacool10.wordpress.com/2012/07/21/how-to-configure-public_html-folder-in-home-dirctory-same-as-varwww-in-apache2/](https://priyankacool10.wordpress.com/2012/07/21/how-to-configure-public_html-folder-in-home-dirctory-same-as-varwww-in-apache2/)

which seems to be relevant. Is this the way to go?

---

### Post by TheFu on 2021-09-28
> **fausto99 said:**
>  
TheFu, I've got a lot of reading to do before I understand your warnings and advice.  However, it all does seem a bit OTT, considering I will be the only user and the system is only powered up for maybe two or three 90 minute bike trainer sessions a week.
 

Apache should be managing files in /var/....  it is a permissions, owner and group thing.
Users should manage files in their HOME directories. Also an owner and permissions thing.
Doing something else, is a bad idea and there will be problems in the future if you ignore this, especially as someone new.

Apache has a built-in method to allow all users to have websites, with files from their HOME directories. It was 1 line, in 1 config file, last time I used it.  Heck, I think I have it here for an internal-only website.

To enable it is 2 commands:
```
sudo a2enmod userdir
sudo systemctl restart apache2
```

Now the URL [http://example.com/~thefu/file.html](http://example.com/~thefu/file.html) will be translated to the file path /home/thefu/public_html/file.html
Simple and better for you since you'll be managing files in your ~/public_html/ directory as a normal user. Just ensure that the permissions allow "other" read access to the directory and files.

---

### Post by fausto99 on 2021-09-29
> **TheFu said:**
> Apache should be managing files in /var/....  it is a permissions, owner and group thing.
Users should manage files in their HOME directories. Also an owner and permissions thing.
...
Now the URL [http://example.com/~thefu/file.html](http://example.com/~thefu/file.html) will be translated to the file path /home/thefu/public_html/file.html
Simple and better for you since you'll be managing files in your ~/public_html/ directory as a normal user. Just ensure that the permissions allow "other" read access to the directory and files.

Ok, thanks. Will have another look on the spare system when I get a mo. Have been doing far too much sys admin and not enough riding lately :biggrin:

---

### Post by fausto99 on 2021-09-30
> **TheFu said:**
> Apache has a built-in method to allow all users to have websites, with files from their HOME directories. It was 1 line, in 1 config file, last time I used it.  Heck, I think I have it here for an internal-only website.

To enable it is 2 commands:
```
sudo a2enmod userdir
sudo systemctl restart apache2
```

Now the URL [http://example.com/~thefu/file.html](http://example.com/~thefu/file.html) will be translated to the file path /home/thefu/public_html/file.html
Simple and better for you since you'll be managing files in your ~/public_html/ directory as a normal user. Just ensure that the permissions allow "other" read access to the directory and files.

I've uninstalled and re-installed apache, then mv all my mp4 files into /home/userdir/public_html

Now, running "sudo a2enmod userdir"  gives ERROR: Module /home/userdir does not exist

How have I mis-interpreted your post? What is a module in this context?

---

### Post by fausto99 on 2021-10-02
Bump

---

