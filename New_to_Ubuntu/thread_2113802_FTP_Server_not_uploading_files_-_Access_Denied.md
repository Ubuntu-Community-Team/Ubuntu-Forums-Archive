---
title: "FTP Server not uploading files - Access Denied"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by whitebakecase on 2013-02-08
I want to run a small forum from a home PC.
I have a server PC and a client machine on the LAN on static IP's, but with no forwarding to allow ftp yet, just http at the moment (I dont think.. correct me if I'm wrong... that I need forwarding yet as both machines are on the LAN, this is only for WAN traffic, right?)

I have ubuntu server 12.04 LTS with LAMP, ufw (open to http and ssh) and proftpd running.

I also have a client win8 machine using "Coffee Cup" ftp client

I'm serving phpbb3 and want to change the forum template.  I can access the forum and its admin panel from the web so I know that part is set up correct.

I have downloaded a style just to test with, which is unzipped on the client machine.

I connect using the name "ftpuser" and the pass "ftpuser" on the client software.

I can connect to the server and can see all directories, using the 'up a level' until i run out of parents and can see (what I think) is the root directory

From there, I select the 'phpbb3' folder which has a chain symbol on it?
I can then see "bob/etc/phpbb3/styles" and its contents, which are the two default themes.

I drag the new theme "Alpha" across to this folder, and it sits happily in the server window with the other two themes.  So I click 'upload' to apply the changes.

Now I go back up a level to the phpbb3 folder, and click it to go back in again, and the two default styles are there but not my new one.

I check the logs and see "Ftp response 550 on create directory 'Alpha'- Access Denied"

I have googled til I am blue in the face, but 'm a windows tech by trade so all these terminal commands are a bit out of my league.  I'm new to linux, I have worked out the text editor and basic installation of packages, but I dont really understand all the 'permissions' stuff and the general structure of the OS.  

I also tried using "vsftpd" and adjusting the config file as advised on a few different forums, but that would not let me connect to the server at all.

I've done my best but I'm stuck for a direction now, please go easy on me

kind regards neil

---

### Post by whitebakecase on 2013-02-09
bump?

---

### Post by CharlesA on 2013-02-09
Why not just use sftp instead of regular ftp to upload the files to the web server?

---

### Post by whitebakecase on 2013-02-09
> **CharlesA said:**
> Why not just use sftp instead of regular ftp to upload the files to the web server?

.... mainly because i've never heard of it , the only options i'd seen around the web were vsftpd and proftpd... i'm very new to the ftp and linux experience (goes off to google sftp clients)

---

### Post by whitebakecase on 2013-02-09
while i think about it, as far as securing the server goes, can you guys recommend a simple way or package to make the server as secure as possible without too much fuss? so far ive added ufw and removed my index.html file as recommended by others, but thats it. i'm not tooooo concerned as its only a small forum and theres not really any sensitive information on it, but i dont want to get complacent, ive already had somebody remote desktop me from ukraine by my own silliness and not using passwords, what worries me now is those chancers, bedroom hackers, who may be much more literate with linux than i am, who might compromise the forum for nothing more than fun, let alone gain access to my other machines on the network. i'm on a vm superhub, using no-ip to provide a host and redirect to my ip

---

### Post by CharlesA on 2013-02-09
> **whitebakecase said:**
> .... mainly because i've never heard of it , the only options i'd seen around the web were vsftpd and proftpd... i'm very new to the ftp and linux experience (goes off to google sftp clients)

SFTP uses SSH, and if you already have SSH installed, it is far easier to deal with and more secure than trying to set up a seperate FTP server just to upload updates and whatnot.

I tend to use either Filezilla in Linux or Windows and WinSCP in Windows.

> **whitebakecase said:**
> while i think about it, as far as securing the server goes, can you guys recommend a simple way or package to make the server as secure as possible without too much fuss? so far ive added ufw and removed my index.html file as recommended by others, but thats it. i'm not tooooo concerned as its only a small forum and theres not really any sensitive information on it, but i dont want to get complacent, ive already had somebody remote desktop me from ukraine by my own silliness and not using passwords, what worries me now is those chancers, bedroom hackers, who may be much more literate with linux than i am, who might compromise the forum for nothing more than fun, let alone gain access to my other machines on the network. i'm on a vm superhub, using no-ip to provide a host and redirect to my ip

The only thing I can really suggest is to make sure you are using a strong password or use keys for SSH if you make it accessible from the internet. More info is [here]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html").

I found some pages talking about Apache security, but they were pretty advanced and you can find the majority by googling "securing apache2" so I will leave you with the [Ubuntu documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") and [this link]("http://secure-ubuntu-server.blogspot.com/2009/07/howto-hardening-your-apache-and-php-on_07.html").

---

### Post by whitebakecase on 2013-02-13
> **CharlesA said:**
> I tend to use either Filezilla in Linux or Windows and WinSCP in Windows.

Thanks for all your help, finally got it working using winscp, had some issues to start with over permissions but once I'd updated those on the server I could access the drive from the client, far enough to change the themes anyway

> **CharlesA said:**
> use keys for SSH if you make it accessible from the internet

I've no intention of ever allowing access to the drive across the net, I'll do all my updating from the local client, but a good thought all the same

Thanks all for your help, I've no doubt I'll be back here again soon. Kudos to you all

---

