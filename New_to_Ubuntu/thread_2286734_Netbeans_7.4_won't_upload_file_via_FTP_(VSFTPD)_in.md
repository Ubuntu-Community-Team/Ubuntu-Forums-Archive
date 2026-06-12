---
title: "Netbeans 7.4 won't upload file via FTP (VSFTPD) in to Ubuntu Server"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by cezar_k on 2015-07-14
Hi Guys,

I recently installed a Ubuntu Server 14.04 on my Raspberry PI 2 Model B and everything works fine,
The major issues starts while trying I'm trying to deploy a PHP file from Netbeans 7.4 IDE to remote server using FTP.
First I set up a remote connection for a super user in NetBeans and remote directory as **/var/www** and it kept giving me **550 Permission denied **every time I tried to upload it.
This issue seems to be very common so I tried to change the permissions and ownership to that folder as recommended in a similar post, it didn't solve it.
Second, I created new user called **guest ** and new directory  **/home/guest/project **with the following permissions and ownership:

[B]chown -R guest project
chmod -R u+rX project

[/B]here is the output of** ls -l **command: *drwxrwxr-x 2 guest guest 4096 Jan  1 00:34 project*


And its still give me **550 Permission denied **every time Im trying to upload the file from Netbeans.

Here is the full output from the Netbeans:

220 (vsFTPd 3.0.2)
USER guest
331 Please specify the password.
PASS ******
230 Login successful.
TYPE I
200 Switching to Binary mode.
CWD /home/guest/project
250 Directory successfully changed.
PWD
257 "/home/guest/project"
CWD /home/guest/project
250 Directory successfully changed.
PASV
227 Entering Passive Mode (192,xxx,x,xx,240,98).
STOR index.php.new
550 Permission denied.
PASV
227 Entering Passive Mode (192,xxx,x,xx,30,248).
STOR index.php.new
550 Permission denied.
PASV
227 Entering Passive Mode (192,xxx,x,xx,235,102).
STOR index.php.new
550 Permission denied.
DELE index.php.new
550 Permission denied.
QUIT
221 Goodbye.


Summary
====================
Failed:
file      index.php     550 Permission denied.
Runtime: 37 ms, processed: 0 file(s), 0 KB


Can anyone please help me solve it? thank you

---

