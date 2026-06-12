---
title: "scp command - connection refused"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-01-21
I wish to automate a daily activity of uploading a specific file to a specific location at mywebsite. On google searching I found scp is command to get my work done
but when I run scp I get following output. 

```
scp myfile.pdf *myusername*@ftp.*mywebsite*.com:/Path/which/I/want/
ssh: connect to host ftp.*mywebsite*.com port 22: Connection refused
lost connection

```

Here I have deliberately changed my my username,website name and file path for security reason. In actual command I am using correct username, ftp server name and path.

Can anyone please help me find what is going wrong?

thanks in advance.

---

### Post by justleen on 2014-01-21
Most likely there is no SSH server running on the remote host, or on a different port number, or its blocked by a firewall.
- ping the machine (to test connectivety)
- see if there is a ssh deamon running ```
~$ ps -ef |grep sshd
root       457     1  0 07:32 ?        00:00:00 /usr/bin/sshd -D
```

- run the same command but add "-vvv"  to get more verbose output.


edit: Just noticed you are connecting to "ftp.mywebsite.com". Most likely you can only use FTP to your site. Check with your hosting provider is SSH is available

---

### Post by sujitrjadhav on 2014-01-21
> **justleen said:**
> Most likely there is no SSH server running on the remote host, or on a different port number, or its blocked by a firewall.
- ping the machine (to test connectivety)
- see if there is a ssh deamon running ```
~$ ps -ef |grep sshd
root       457     1  0 07:32 ?        00:00:00 /usr/bin/sshd -D
```

- run the same command but add "-vvv"  to get more verbose output.


edit: Just noticed you are connecting to "ftp.mywebsite.com". Most likely you can only use FTP to your site. Check with your hosting provider is SSH is available

ping 

infocafe@devils-home:~/Desktop$ ping ftp.mywebsite.com
PING ftp.*mywebsite*.com (??.??.??.??) 56(84) bytes of data.
64 bytes from ftp.*mywebsite*.com (??.??.??.??): icmp_seq=1 ttl=46 time=271 ms
64 bytes from ftp.*mywebsite*.com (??.??.??.??): icmp_seq=2 ttl=46 time=270 ms
64 bytes from ftp.*mywebsite*.com (??.??.??.??): icmp_seq=3 ttl=46 time=271 ms



ps -ef |grep sshd
root      2685     1  0 21:09 ?        00:00:00 /usr/sbin/sshd -D
infocafe 14170 13431  0 21:52 pts/2    00:00:00 grep --color=auto sshd

scp -vvv myfilename.pdf [EMAIL="myusername@ftp.mywebsite.com"]myusername@ftp.mywebsite.com[/EMAIL]:/path/which/i/want/
Executing: program /usr/bin/ssh host ftp.mywebsite.com, user myusername, command scp -v -t /path/that/i/want/
OpenSSH_6.2p2 Ubuntu-6ubuntu0.1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ftp.mywebsite.com [??.???.???.??] port 22.
debug1: connect to address ??.???.???.?? port 22: Connection refused
ssh: connect to host ftp.mywebsite.com port 22: Connection refused
lost connection

---

### Post by sandyd on 2014-01-21
Do you have a firewall running?

---

### Post by sujitrjadhav on 2014-01-21
How do I check it? I think I have ufw installed. One more thing- When I connect to my website using filezilla it is using a different port no- not port no 22

---

### Post by justleen on 2014-01-21
the ps -ef |grep sshd, did you do that on your local machine, or on the remote? (should be remote)
Do you have shell access at all to that machine, or just FTP access?

I'm pretty confident the remote side is not accepting connections on port 22 / ssh..

---

### Post by sujitrjadhav on 2014-01-21
My web host have given me ftp user name and ftp address. By remote machine you mean server of webhost? I can not run that command on server. Is there any else way to check it? If, like you say, ssh is not enabled on remote machine and only ftp option is available then what is command that I can use to achieve my goal- automate uploading a file to a ftp address using linux commandline.

---

### Post by GrouchyGaijin on 2014-01-21
I'm just curious, do you have an ssh key set up?

I have an scp script that connect to my host set up as:

```



scp -P 18765 -r ~/Pictures/Phoca_upload/* username@host.com:public_html/destination/directory


```

My host uses port 18765 and I have a key in my ~/.ssh directory and a corresponding key on the server.

---

### Post by sujitrjadhav on 2014-01-21
To be honest I do not understand these protocols and have no knowledge about networking and these file transfer protocols. I really do not know whether I am using correct command or not. I am using filezilla every day to get my work done. I quick connect with filezilla and manually upload the file to desired address. I wish to automate the job by creating a bash script. So I Googled and found scp command. I do not know if that command is the correct command in the scenario or not.

---

### Post by sujitrjadhav on 2014-01-21
What I have is a ftp username, a ftp server address. What command I may use  to automate the same task of file transfer as I have a fixed file name with fixed local path and fixed remote path?

---

### Post by GrouchyGaijin on 2014-01-21
Well I am _**not**_ an expert, so anyone who is please correct me but the way I understand it and the way I have it set up on my system is:

I generated an ssh public/private key pair on my system and the private key is in my ~/.ssh directory.
I uploaded the public key to my hosting company through their control panel.
When I connect the SFTP client matches the keys and I am allowed in.

Usually I use lftp to upload via script.

---

### Post by GrouchyGaijin on 2014-01-21
> **sujitrjadhav said:**
> What I have is a ftp username, a ftp server address. What command I may use  to automate the same task of file transfer as I have a fixed file name with fixed local path and fixed remote path?

It is my understanding that with regular ftp, not SFTP or FTPS, your credentials are being sent in clear text.

---

### Post by sujitrjadhav on 2014-01-21
> **GrouchyGaijin said:**
> I'm just curious, do you have an ssh key set up?

I have an scp script that connect to my host set up as:

```



scp -P 18765 -r ~/Pictures/Phoca_upload/* username@host.com:public_html/destination/directory


```

My host uses port 18765 and I have a key in my ~/.ssh directory and a corresponding key on the server.


I checked my local machine home directory it has subdirectory .ssh with a file known_hosts. I used filezilla to check my remote machine home directory and found that there is no such directory at remote machine.

---

### Post by sujitrjadhav on 2014-01-21
I logged in cpanel and found that there is Manage SSH Key option in cpanel. There I have two options - Generate a new key and import key. What do I have to do to set up ssh?

---

### Post by GrouchyGaijin on 2014-01-21
You can either generate a key on your local machine and then import the public key into the control panel or you can make a key from their control panel and then copy the private key to local machine.
Does your hosting company have a FAQ or read me on SSH access?
Just curious, are you using SiteGround, by any chance?

---

### Post by sujitrjadhav on 2014-01-21
Nope. I am not using siteground. I generated ssh keys at server using cpanel and downloaded both private and public keys. But how do I import them on local machine?

---

### Post by sujitrjadhav on 2014-01-21
It seems solution to my problem is wput and scp

---

### Post by GrouchyGaijin on 2014-01-21
> **sujitrjadhav said:**
> It seems solution to my problem is wput and scp

If that works for you cool.

Here is how I do it:
```

$ ls -ld ~/.ssh
drwx------ 3 john john 4096 Jan  9 00:11 /home/john/.ssh

```
This means I can create and delete files as the owner, but the group and others can do nothing.
My private key is inside the ~/.ssh directory

I usually use lftp to upload to the server.  Lftp looks for keys in the ~/.ssh directory by default.

Here is the script I use to upload photos from my computer to the desired directory on the server:

```

#!/bin/bash 
read -p " Press the [Enter] key continue..."  
LCD="/path/to/directory/on/my/machine"
RCD="/path/to/directory/on/the/server" 
#DELETE="--delete"
lftp -c "set ftp:list-options -a;
open -u <user_name>,pass -p <port_number> sftp:/hosting_company.com;
lcd $LCD;
cd $RCD;
mirror --reverse \
       $DELETE \
       --verbose \
       --exclude-glob a-dir-to-exclude/ \
       --exclude-glob a-file-to-exclude \
       --exclude-glob a-file-group-to-exclude* \
       --exclude-glob other-files-to-exclude"
mv /the/uploaded/images/from/my/local/disk/to/external/drive/for/storage/


```

---

### Post by sujitrjadhav on 2014-01-21
Thanks very much GrouchyGaijin all others for patiently helping me so much. I talked with support team of my webhost and I was told that ssh was not enabled for my account. Further, I have found that solution to my problem is in wput command. I successfully tested it and created a bash script to automate upload task that I have to perform everyday.

---

