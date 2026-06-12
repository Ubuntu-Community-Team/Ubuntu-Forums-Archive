---
title: "Web Sever Downloads Files are Corrupt"
date: 2015-02-19
forum: New to Ubuntu
---

### Post by Todd_Nopper on 2015-02-19
Newbie to Ubuntu/Linux.  Installed 14.1 server on VMWare 5.5, and have installed and configured vsftpd, Apache, MySQL, PHP, and setup a couple virtual web servers – all good.
 
The problem is when I connect to the web server (anonymous web user) links to “xlsx” or “docx” files technically work but the downloaded file is always corrupt, “The file is corrupt and cannot be opened” – pdf’s are good.  If I use WinSCP (sftp) and download the files they are good to go.  The folders the files are in all have the same permissions set.
 
Any suggests or a place to look for logs?
 
Thanks in advance,

---

### Post by mastablasta on 2015-02-19
virtual inside virtual? how are you opening the files? using MS Word/Excell?

---

### Post by Todd_Nopper on 2015-02-19
Excuse my poor grammar I meant to say I setup multiple virtual websites on the server, i.e. test.domain.local and sample.domain.local.
 
And yes using MS Word/Excel to open the files, they are corrupt when I choose &#8220;Open&#8221; or if I &#8220;Save&#8221; and then open from the folder.  But if I download using WinSCP or even Dreamweaver (both connecting using sftp) they open fine.  I'm using Windows 8 and have tried IE, FF, and GC.
 
I mention the &#8220;sftp&#8221; because I think that may have something to do with it.  When I setup vsftpd I configured it to force SSL with these settings I found in an online &#8220;How To&#8221;:
 
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
 
For that I&#8217;m using a self-signed SSL certificate.
 
Once I have a the bugs worked out I would like to secure the website (https) and before I go live I&#8217;ll purchase the certificate but at the moment I&#8217;m trying to learn as much as I can about Ubuntu.

---

### Post by mastablasta on 2015-02-20
well I am still a bit new to certificates as well.

but one thing is a bit odd - you are forcing SSL transfer, yet you are using HTTP to access the site. does that work?

in any case what is your goal with this site? what do you plan to do with documents? have you looked at any other tools that might better provide what you need?

for example I (actually my wife) sell an e-book in online shop. and we have it setup that when they purchase it - a download link appears. when they download it the information form the one that purchased it is entered into the book. so it's kind of personalised edition. anyway all this is done via various PHP based tools. and there is no sFTP used but there is SSL for the purchase.

---

### Post by Holger_Gehrke on 2015-02-20
Try to compare the files downloaded through http and ftp. Is the defective file of a different length ? You also might want to take a look at the http-headers, either through some kind of browser-extension or by using wget with the '-S' option. Might be a wrong content-type (if the web-server transmits the file as some kind of text, for example).

And by by the way, what you are using is not sftp but ftps. sftp is ftp tunneled through ssh, ftps is ftp with ssl or tls.

---

### Post by Todd_Nopper on 2015-02-20
**mastablasta**
 
Yes everything on the site worked fine except links to excel and word documents.  But yes I thought the same so setup another virtual web site using HTTPS and have the same problem with that.
 
Right know this site is hosted on a Windows server 2003 and the idea is to eventually move it to a Ubuntu server for performance and security reasons.  The site(s) are a company intranet and employee portal.  They use PHP to generates reports pulling data from the accounting software which is running MS-SQL, then there are options to download those in excel format.  Those needed minor tweaking but they are all working on the Ubuntu server and much faster too.
 
When I find time I&#8217;ll try setting it up again from scratch without the sFTP (or figure out how to remove that) and see if it works then.  Then at least I&#8217;ll know that sFTP is actually causing the issue.
 
 

 
**Holger_Gehrke**
 
I verified the files are the same length either way, from the website link or from WinSCP/Dreamweaver.
 
Using Chrome&#8217;s developer tools to &#8220;View Response Headers&#8221; I get the following:
 
Pragma: no-cache
Date: Fri, 20 Feb 2015 15:39:09 GMT
Content-Encoding: gzip
Server: Apache/2.4.10 (Ubuntu)
X-Powered-By: PHP/5.5.12-2ubuntu4.2
Vary: Accept-Encoding
Content-Type: text/html
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Connection: Keep-Alive
Keep-Alive: timeout=5, max=100
Content-Length: 1491
Expires: Thu, 19 Nov 1981 08:52:00 GMT
200 OK
 
The &#8220;Content-Type: text/html&#8221; is the same as on my working the IIS server.
 
And yes I am using sftp, obviously I need to do some more reading (thought it was SSL) as I think ftps is what I to use to make this as secure as possible - thanks.
 


Folks, I think I will close this post, do some more reading and start from scratch.

---

### Post by Holger_Gehrke on 2015-02-20
> **Todd_Nopper said:**
> 
I verified the files are the same length either way, from the website link or from WinSCP/Dreamweaver.
 
Try actually comparing the files. 'cmp' can tell you where and in what way(s) the files differ. On Windows there's a similar command line tool named - I think - 'comp'.

> **Todd_Nopper said:**
> 
Using Chrome’s developer tools to “View Response Headers” I get the following:
 
Pragma: no-cache
Date: Fri, 20 Feb 2015 15:39:09 GMT
Content-Encoding: gzip
Server: Apache/2.4.10 (Ubuntu)
X-Powered-By: PHP/5.5.12-2ubuntu4.2
Vary: Accept-Encoding
Content-Type: text/html
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Connection: Keep-Alive
Keep-Alive: timeout=5, max=100
Content-Length: 1491
Expires: Thu, 19 Nov 1981 08:52:00 GMT
200 OK
 
The “Content-Type: text/html” is the same as on my working the IIS server.
 
And yes I am using sftp, obviously I need to do some more reading (thought it was SSL) as I think ftps is what I to use to make this as secure as possible - thanks.
 

Those are the headers of a normal web-page. The headers for one of the downloads are what I meant. 

And sftp is in many ways superior to ftps. For one thing it only needs one fixed port while ftps needs one fixed port (for the control channel) and one random port (for the data channel), like ftp, which makes it a nightmare for firewall administration. Also sftp always encrypts everything, with ftps it's a matter of configuration whether or not the data will be encrypted and whether or not it will continue using encryption after authentication. And you can use public keys with sftp without too much hassle and completely do away with passwords. The only way to do something similar with ftps is requiring certificates on the client ...

---

### Post by mastablasta on 2015-02-21
well i only setup maybe 5 or 6 pages on Apache, but i never ran into this issue before. so it's hard for me to tell what is wrong wothout more information.

if you go from scratch here is some reading:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)

in any case at the moment it seems to me only your downloads are the issue, so if we can figure out why and how this is happening there could be a very simple solution to that.

---

