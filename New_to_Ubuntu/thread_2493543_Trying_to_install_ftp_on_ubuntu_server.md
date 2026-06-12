---
title: "Trying to install ftp on ubuntu server"
date: 2023-12-18
forum: New to Ubuntu
---

### Post by polaatx on 2023-12-18
Hello, I'm a newbie to terminal and linux.
I want to install ftp on an Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-91-generic x86_64)remote server.
I used the following tutorial [https://ubuntu.com/server/docs/service-ftp](https://ubuntu.com/server/docs/service-ftp)
I ran the following code
```
sudo apt install vsftpd
```
And it looked like it did a bunch of things.
But now I don't see anything installed. I mean there are no new directories. This is all there is in my root:

```



root@server-45------:~# dir
Pictures database docker-compose.yml snap storage



```
Any help would be appreciated.

---

### Post by Holger_Gehrke on 2023-12-18
The directory you're showing is not the root directory, it's the home-directory of the user 'root' aka '/root/'. Any changes produced by installing any package would not show up there. If you look at the [list of files in the vsftpd package]("https://packages.ubuntu.com/jammy/amd64/vsftpd/filelist"), you'll see what files where installed where. Among the things installed where the manual pages for vsftpd and for the configuration file vsftpd.conf. Read them using 'man 8 vsftpd' and 'man 5 vsftpd.conf'.

**But** while you followed the installation-instructions, you probably didn't read the important warning at the beginning. It basically means: **don't use FTP** for anything unless you don't care or it's a server inside a protected LAN. All credentials are transmitted unencrypted and are easily intercepted by hackers. Use SFTP as provided by OpenSSH instead.

Holger

---

### Post by polaatx on 2023-12-19
> **Holger_Gehrke said:**
> The directory you're showing is not the root directory, it's the home-directory of the user 'root' aka '/root/'. Any changes produced by installing any package would not show up there. If you look at the [list of files in the vsftpd package]("https://packages.ubuntu.com/jammy/amd64/vsftpd/filelist"), you'll see what files where installed where. Among the things installed where the manual pages for vsftpd and for the configuration file vsftpd.conf. Read them using 'man 8 vsftpd' and 'man 5 vsftpd.conf'.


Hello @Holger_Gehrke thanks you very much for your attention.

I am really shocked to hear that all this time I've been using an account just called 'root' and not the real root. This login info was given to me by the person I paid to install docker for me because I couldn't figure it out. Then he disappeared and it's been a huge time investment to try to figure out how to use ssh. Took me half a day yesterday just to figure out how to edit a config file in docker.

Anyway, in order to use vsftpd I have to edit vsftpd.conf. But to do that I need to get to it in /etc/ folder. But to do that I need to login as the REAL root user, correct?

How do I do that? If there is already a user name 'root' and that's why I put into putty login, so then what would the login for the real root is? I'm really confused and I apologize in advance for asking questions that must sound very stupid to you.

---

### Post by The Cog on 2023-12-19
You are confusing the **user** root with the root **directory**. 

USER root is the ultimate all-powerful administrator of the machine. Also the creator of all other users, including the account you log in with immediately after installing.

The root DIRECTORY is the top of the directory tree, and every file on the system resides in this directory, or in directories placed in the root directory (or in directories in directories etc.). 
[https://www.geeksforgeeks.org/linux-directory-structure/](https://www.geeksforgeeks.org/linux-directory-structure/)

A user's **home** directory is where that users keeps all their files, settings etc. For most users, that's in directories placed inside the home directory. That can be a source of confusion. **The** home directory is /home, and that is where each user's individual directory is placed. For instance, **my** home directory might be /home/TheCog. I think Windows has a directory C:\users that serves the same purpose as /home.

The odd one out is root's home directory, which is placed directly into the root directory. The root directory is **/**. Root's home directory is **/root**, a directory inside the root directory. Confusing. It would help if the root user had a different username, but that's history.

---

### Post by TheFu on 2023-12-19
> **polaatx said:**
> Hello, I'm a newbie to terminal and linux.
I want to install ftp on an Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-91-generic x86_64)remote server.
I used the following tutorial [https://ubuntu.com/server/docs/service-ftp](https://ubuntu.com/server/docs/service-ftp)
I ran the following code
```
sudo apt install vsftpd
```
And it looked like it did a bunch of things.
But now I don't see anything installed. I mean there are no new directories. This is all there is in my root:

```



root@server-45------:~# dir
Pictures database docker-compose.yml snap storage



```
Any help would be appreciated.

a) we were all new at some point.
b) noobs shouldn't be trying to install and use docker servers. But whaterver.
c) nobody - N-O-B-O-D-Y - should be using plan FTP since around 2002. It isn't safe.  Use sftp instead. I'll provide commands below.
d) noobs shouldn't be using the root account, especially on Ubuntu.  Ubuntu is built around using sudo with your normal account, not the root account.

First, purge docker and that plain FTP server from your system. You don't want/need either.

To install sftp-server, run these commands.
```
sudo apt update
sudo apt install ssh-server fail2ban

```
That's it.  We can layer on more security later, but with just that, you can use almost any Linux file manager to use sftp:// URLs for access into the remote system.

ssh is the core tool here.  with ssh installed, we gain ssh, scp, sftp, by default.  They are enabled an use the same port, which is 22/tcp by default.  When we installed fail2ban too, that tool setup brute force dynamic firewalling, so if someone anywhere has the wrong credentials, they won't be allowed more than a few attempts before being banned for an hour. I think 1 hour is the default.  I always change that to a week, but that's men.  ssh/sftp support using passwords for logins, but that's a pain and humans are known for being really bad at creating secure passwords.  ssh-keys or ssh-certs are the way to have more secure connections that are also more convenient.  Right?  That never happens. 10000x better security AND more convenient too?  It only takes 2 commands to setup ssh-keys between 2 systems. .... then 1 command to add additional remote systems.  Let me know if you are interested in that.  ssh-keys work with all ssh-based connections/tools, so setting them up makes about 50 other ssh-based tools easier AND more secure as well.

sftp is available on every networked OS.  
[LIST]
[*]Windows - use **WinSCP** or **Filezilla**
[*]Android use **Ghost Commander**
[*]Linux and all Unix-like OSes, use any ssh-based tool you like or the file manager after you install the "ssh-client" package.  sftp comes with that.
[/LIST]

Instead of ssh-server and ssh-client, I usually install the "ssh" metapackage, which includes both those and a few others.
Tools that use ssh ...
ssh, scp, sftp, rsync, x2go, sshfs, vim, ssh-tunnel and a bunch of others. Each with a purpose and use.  Or you can setup an ssh tunnel manually that any TCP-based traffic can be sent through.  ssh is how Unix systems communicate.  You don't need to "master" is. Just need to use it and understand that using passwords is a liability. 
[LIST]
[*]Use ssh-keys.
[*]Don't use the root account.
[*]Don't use plain FTP - E-V-E-R.  If you need to transfer files and don't care about security, use HTTP.   There are 1-line HTTP servers for quick needs with ZERO security, like plain FTP.
[*]If you need to transfer files and can't use ssh-based tools, use **wormhole**.
[/LIST]

That about covers it.

oh, and 1 more thing.  Learn the basics of Unix ASAP.  Skills in Unix build on prior skills, so jumping to intermediate or advanced topics means you'll struggle 10x longer than just working through a beginning course first, then strong beginner, then intermediate, then strong intermediate, and finally advanced level stuff - like docker.  A good beginner book that can be worker through, 1 chapter per day is [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  I used this book (free download) for my beginner Linux classes. We did 1 chapter a week with just 2 hours of lecture and about 4 hrs of homework.  In 12 weeks, the students had a good grasp of beginning concepts and commands.  With effort, 1 chapter a day is doable.

---

### Post by polaatx on 2023-12-19
> **The Cog said:**
> You are confusing the **user** root with the root **directory**. 

USER root is the ultimate all-powerful administrator of the machine. Also the creator of all other users, including the account you log in with immediately after installing.

The root DIRECTORY is the top of the directory tree, and every file on the system resides in this directory, or in directories placed in the root directory (or in directories in directories etc.). 
[https://www.geeksforgeeks.org/linux-directory-structure/](https://www.geeksforgeeks.org/linux-directory-structure/)

A user's **home** directory is where that users keeps all their files, settings etc. For most users, that's in directories placed inside the home directory. That can be a source of confusion. **The** home directory is /home, and that is where each user's individual directory is placed. For instance, **my** home directory might be /home/TheCog. I think Windows has a directory C:\users that serves the same purpose as /home.

The odd one out is root's home directory, which is placed directly into the root directory. The root directory is **/**. Root's home directory is **/root**, a directory inside the root directory. Confusing. It would help if the root user had a different username, but that's history.

Hello @The Cog

Many thanks for the explanation. Finally it occurred to me to do  cd /  and suddenly I'm in this directory:```


root@server-my-ip:~# cd /
root@server-my-ip:/# dir
bin   etc   lib32   lost+found  mnt   root  snap      sys  var
boot  home  lib64   man         opt   run   srv       tmp
dev   lib   libx32  media       proc  sbin  swapfile  usr



```

So now I realize that when I login, I'm in the HOME directory of root user. But to get to get to root directory I need to go one directory DOWN and then use cd to go back to root's home directory. 

Did I get the story correct?

---

### Post by polaatx on 2023-12-19
Hello @TheFu
thanks for the response. 
I agree noobs shouldn't mess with docker or root but I ran out of choices. I'm a photographer. Wanted to host my own photos on a program called photoprism that only runs on docker. Hired someone to install it for me. Just got tired of paying and paying and getting screwed by the guy disappearing on me over and over. Finally I realized I need to learn this I don't want to give up on using photoprism. A couple of nights ago some dude on Fiverr wanted $50 just to add 5 lines to my docker yml file. Once I figured out how to use vi I realized it was 30 seconds worth of work. He wanted $50 for 30 seconds of bother. So you see sometimes people get pulled into this world not because they want to (I mean ssh drives me crazy!!!) but because they have to. 

You're the second person who tells me not to use ftp and use sftp instead.
But just wondering: Why if vsftp so insecure, Wikipedia says it is the "default" ftp server of ubuntu? I mean Ubuntu should not use something that's not secure, should they? [https://en.wikipedia.org/wiki/Vsftpd#:~:text=vsftpd%2C%20(or%20very%20secure%20FTP,Slackware%20and%20RHEL%20Linux%20distributions](https://en.wikipedia.org/wiki/Vsftpd#:~:text=vsftpd%2C%20(or%20very%20secure%20FTP,Slackware%20and%20RHEL%20Linux%20distributions).

About installing ssl-server you recommended: could this by any chance ever affect my docker installation? Docker is very important to me becuase on it runs my photo mgmt app.

---

### Post by TheFu on 2023-12-19
> **polaatx said:**
>  
So now I realize that when I login, I'm in the HOME directory of root user. But to get to get to root directory I need to go one directory DOWN and then use cd to go back to root's home directory. 

Did I get the story correct?

Yes.

/root == ~root == $HOME (when logged in as root)  == ~/ (when logged in as root)

For non-root accounts assuming typical single-human Linux, 
/home/{username} == ~username == $HOME  (when logged in as username)  == ~/ (when logged in as username)

All the same places.

The location for $HOME and ~ are read from the passwordd DB at login.  The password DB can be either /etc/passwd or LDAP or some other PAM-configured directory like NIS or NIS+ or an identity management tool.  If you are running a single-human (there are always 20-100 users on any Unix/Linux system) system, the it is almost 100% the accounts are configured in the /etc/passwd text file.  Take a look at it.  It is a simple text file with fields separated by a ':' character.    The fields/file is explained in the manpage for it.  Run
```
$ man -s 5 passwd
```
for that information. It is fairly short, simple and shows what a userid is all about.

But you shouldn't be logging in a root, ever, ok, almost never, 99.9999% of the time, logging in a root is a bad idea.   [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  I think remote root access is blocked by default and trying to run a desktop as root causes all sorts of problems.

---

### Post by The Cog on 2023-12-19
Firstly, O.M.G. "dir" worked! I had no idea that was there. In the *nix world we use ls instead, but it looks like it takes the same arguments. Live and learn. But that's irrelevant.

It looks like you are logging in as user root. That's generally frowned on for local use - too many accidents, like running with scissors. But in this case it's a remote server, so not something you would do every day.

You are kind of right, except most people think of the root directory as the top of the tree, not the bottom. More like a family tree than a vegetable tree. So you are changing **up** out of root's home (/root) to change into the root directory (/)hen changing back **down** into root's home directory with the command "cd", which by default takes you to your home directory. Another oddity, with the root being at the top of the tree.

> Why if vsftp so insecure, Wikipedia says it is the "default" ftp server of ubuntu?
The Ubuntu repositories (like an app store) use FTP to deliver their packages when you install or upgrade. People sometimes ask why use FTP. But this is a bit of a special case. It's public data, no login required. Open for the world to read, so no issues with protecting privacy, and no password that might be stolen/abused. It's read-only, so nobody can upload or change anything. And the data is all digitally signed, so even of it was hacked, people would just see corrupted files that won't install.

---

### Post by polaatx on 2023-12-19
@TheFu,  Hi there, I really appreciate all the info and I'm taking to heart your recommendation NOT to login as root. I checked out the passwd file and I was shocked to see how many usernames are already in the system. Something like 25 or 30, most of the related to the system. 
Anyway, I'm working on creating a new sudo user. 
But here's an issue: the person who installed docker for me, put the docker yml file in the home directory of the root. 
1. Will I be able to get that directory when I'm a sudo user?  
2. Or better yet, possible or advisable to set my home directory same as the home directory of the root user? 
I hope I make sense.

---

### Post by polaatx on 2023-12-19
@TheCog 
I get it now. It's default for repositories but that doesn't mean Ubuntu is recommending ftp for using it for your own files. See when I saw the word default, I interpreted that as being a endorsement of ftp. 
Anyway, sftp will be my goal once I figure out how to become an sudo user.

---

### Post by polaatx on 2023-12-19
@TheFu, hi,  I was able to create a new sudo user and will not be logging in as root, as you recommended. 
However, now I don't know how to the docker yml file I need to edit. 
As I explained earlier, this file resides in the home directory of root user. Can I get into there when I'm logged in as a sudo user?

---

### Post by TheFu on 2023-12-19
> **polaatx said:**
>  
I agree noobs shouldn't mess with docker or root but I ran out of choices. I'm a photographer. Wanted to host my own photos on a program called photoprism that only runs on docker. Hired someone to install it for me. Just got tired of paying and paying and getting screwed by the guy disappearing on me over and over. Finally I realized I need to learn this I don't want to give up on using photoprism. A couple of nights ago some dude on Fiverr wanted $50 just to add 5 lines to my docker yml file. Once I figured out how to use vi I realized it was 30 seconds worth of work. He wanted $50 for 30 seconds of bother. So you see sometimes people get pulled into this world not because they want to (I mean ssh drives me crazy!!!) but because they have to. 

You're the second person who tells me not to use ftp and use sftp instead.
But just wondering: Why if vsftp so insecure, Wikipedia says it is the "default" ftp server of ubuntu? I mean Ubuntu should not use something that's not secure, should they? [https://en.wikipedia.org/wiki/Vsftpd#:~:text=vsftpd%2C%20(or%20very%20secure%20FTP,Slackware%20and%20RHEL%20Linux%20distributions](https://en.wikipedia.org/wiki/Vsftpd#:~:text=vsftpd%2C%20(or%20very%20secure%20FTP,Slackware%20and%20RHEL%20Linux%20distributions).

About installing ssl-server you recommended: could this by any chance ever affect my docker installation? Docker is very important to me becuase on it runs my photo mgmt app.

When you pay someone to help with computers, think of them more like a medical doctor. You aren't paying the doctor to hand you a pill, you are paying for the 10+ yrs of school, the decades of experience, and their ability to here what you say, interpret that into what your mean and what is possible, then provide a solution.  

Sadly, I think you should have paid more, since that person was just trying to get the money as quickly as possible, not do the best job.  
a) the root account should not be used for docker.  If it is, that removes 80+% of the security that Linux Containers provide.
b) docker default security runs as root (i.e. privileged mode), which is also a huge security issue.  It is possible to override the default setting, but I decided not to use docker. I use lxc instead.
c) just because something is possible, that doesn't make it a good idea.

I'm a photographer hobbyist.  I only have about 100K photos, so my organization requirements are very limited compared to that of a professional. I use some custom perl CGI code that I modified over the decades to support my specific needs, like 1-click GPS locations.  This CGI script doesn't like lots of browsers, which doesn't bother me, since I can make it work with my main browser when something breaks.  It doesn't have **any** javascript, which I consider to be an abomination, so it doesn't have slick transformations.  I've looked at other webapps for this stuff.  
Years ago, I was burned after I put all sorts of metadata about the photos into a separate database, then wasn't able to get any of that data back out when it was time to change programs.  From that point on, I've insisted that metadata be stored inside the files and that any extra information be retained in plain text files which sit with the photos.

FTP has been a problem since at least 2002.  Yet Linux books still cover how to set that service up when nobody should be using it.

Also, Ubuntu Repos are accessed using HTTP or HTTPS and have been for at least 10 yr, perhaps 20.  I don't know. I just know that around 2010, I setup a local apt-cache and it is 100% http.  I haven't used plain FTP in over a decade, perhaps 2.

Plain FTP has a specific command language.  sftp mirrors that exact language for a reason. It was designed to be a drop in replacement.
The same goes for scp which was designed to be a drop-in replacement for rcp.  If you ever wondered by the default prompt in Linux is what it is ... that's because scp uses exactly that format ... and so does rsync.  It is extremely helpful.

I have no idea what an "ssl-server" is.  We've been talking about sftp-server here.

---

### Post by polaatx on 2023-12-20
> **TheFu said:**
> When you pay someone to help with computers, think of them more like a medical doctor. You aren't paying the doctor to hand you a pill, you are paying for the 10+ yrs of school, the decades of experience, and their ability to here what you say, interpret that into what your mean and what is possible, then provide a solution.  

Sadly, I think you should have paid more, since that person was just trying to get the money as quickly as possible, not do the best job.  
a) the root account should not be used for docker.  If it is, that removes 80+% of the security that Linux Containers provide.
b) docker default security runs as root (i.e. privileged mode), which is also a huge security issue.  It is possible to override the default setting, but I decided not to use docker. I use lxc instead.
c) just because something is possible, that doesn't make it a good idea.

I'm a photographer hobbyist.  I only have about 100K photos, so my organization requirements are very limited compared to that of a professional. I use some custom perl CGI code that I modified over the decades to support my specific needs, like 1-click GPS locations.  This CGI script doesn't like lots of browsers, which doesn't bother me, since I can make it work with my main browser when something breaks.  It doesn't have **any** javascript, which I consider to be an abomination, so it doesn't have slick transformations.  I've looked at other webapps for this stuff.  
Years ago, I was burned after I put all sorts of metadata about the photos into a separate database, then wasn't able to get any of that data back out when it was time to change programs.  From that point on, I've insisted that metadata be stored inside the files and that any extra information be retained in plain text files which sit with the photos.

FTP has been a problem since at least 2002.  Yet Linux books still cover how to set that service up when nobody should be using it.

Also, Ubuntu Repos are accessed using HTTP or HTTPS and have been for at least 10 yr, perhaps 20.  I don't know. I just know that around 2010, I setup a local apt-cache and it is 100% http.  I haven't used plain FTP in over a decade, perhaps 2.

Plain FTP has a specific command language.  sftp mirrors that exact language for a reason. It was designed to be a drop in replacement.
The same goes for scp which was designed to be a drop-in replacement for rcp.  If you ever wondered by the default prompt in Linux is what it is ... that's because scp uses exactly that format ... and so does rsync.  It is extremely helpful.

Hi @TheFu, glad to here you're a photog too. All your points are well-taken. I am grateful about all the knowledge I'm gaining about the dangers of using root and now realize how careless the person we hired was. 

> I have no idea what an "ssl-server" is.  We've been talking about sftp-server here.

I was referring to the code you provided here earlier:

```
[COLOR=#000000][FONT=&quot]sudo apt update
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo apt install ssh-server fail2ban[/FONT][/COLOR]
```

Probably not, but I thought I ask you to be sure: could installing this affect the running of the docker?

---

### Post by TheFu on 2023-12-20
> **polaatx said:**
>  
I was referring to the code you provided here earlier:

```
[COLOR=#000000][FONT=&quot]sudo apt update
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo apt install ssh-server fail2ban[/FONT][/COLOR]
```

Probably not, but I thought I ask you to be sure: could installing this affect the running of the docker?

Being correct about details matters.  ssl-server isn't anything I know.  ssh-server is different.  Actually, most versions of SSL (the encryption protocol) have been hacked. HTTPS which was SSL-based 20 yrs ago moved to TLS-based encryption long ago.  I think TLS v1.3 is current after TLS v1.2 was cracked by multiple state actors.  TLS v1.3 has been around long enough that it has probably been cracked, though I haven't seen any announcements. I know v1.4 was being worked on, but don't think it has been released.
Some SSL/TLS history: [https://en.wikipedia.org/wiki/Version_history_for_TLS/SSL_support_in_web_browsers](https://en.wikipedia.org/wiki/Version_history_for_TLS/SSL_support_in_web_browsers)

Anyway, we're talking about ssh and sftp. Neither TLS nor SSL are used in it, though I can understand the confusion.

I don't know anything about docker. I use lxc which is different and has more secure defaults, but not as good marketing.

---

