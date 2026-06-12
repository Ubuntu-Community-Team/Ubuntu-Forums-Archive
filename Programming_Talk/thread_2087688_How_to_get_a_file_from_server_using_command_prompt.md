---
title: "How to get a file from server using command prompt"
date: 2012-11-24
forum: Programming Talk
---

### Post by Mohan1289 on 2012-11-24
hi guys

how can i download a file from server using commands??

what i want to say is i have to download a file from server which is at /home/krishna/**links** in the server

the servers ip is 10.40.70.68
my ip is 10.40.70.51

my user id in server is **mohan**
paswd is  *<snip>*

how can i obtain the links file using commands??
Any Suggestions please

---

### Post by MG&amp;TL on 2012-11-24
Which protocol? SSH, FTP, (HTTP)?

EDIT: please don't post your password!

---

### Post by Lars Noodén on 2012-11-24
Yes, which protocol?  If it is HTTP or anonymous FTP, then use lynx or wget.  If it is SSH then use sftp or scp.

---

### Post by Mohan1289 on 2012-11-24
> **Lars Noodén said:**
> Yes, which protocol?  If it is HTTP or anonymous FTP, then use lynx or wget.  If it is SSH then use sftp or scp.


it's ssh how can use sftp of scp??

---

### Post by Lars Noodén on 2012-11-24
Check the manual page for [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) for details, but the general usage is with the username and remote host:

```

[s]sftp -l user server.example.org/s]
sftp user@server.example.org

```

Inside sftp, put and get are your two main commands, but there are many others described in the manual page.

---

### Post by Mohan1289 on 2012-11-26
> **Lars Noodén said:**
> Check the manual page for [sftp]("http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html") for details, but the general usage is with the username and remote host:

```

sftp -l user server.example.org

```Inside sftp, put and get are your two main commands, but there are many others described in the manual page.

Pardon me but can you explain that to me by a example... 

What i have to do is download a certain file from the server and move it to my home folder..

how can i use sftp protocol in shell script?? i even tried from my terminal but no avail.. here is what it's saying

```


krishna@ubuntu:~$ sftp -l mohan 10.40.70.68
usage: sftp [-1246Cpqrv] [-B buffer_size] [-b batchfile] [-c cipher]
          [-D sftp_server_path] [-F ssh_config] [-i identity_file] [-l limit]
          [-o ssh_option] [-P port] [-R num_requests] [-S program]
          [-s subsystem | sftp_server] host
       sftp [user@]host[:file ...]
       sftp [user@]host[:dir[/]]
       sftp -b batchfile [user@]host
krishna@ubuntu:~$ sftp -l mohan 10.40.70.68 /home/mohan/link
usage: sftp [-1246Cpqrv] [-B buffer_size] [-b batchfile] [-c cipher]
          [-D sftp_server_path] [-F ssh_config] [-i identity_file] [-l limit]
          [-o ssh_option] [-P port] [-R num_requests] [-S program]
          [-s subsystem | sftp_server] host
       sftp [user@]host[:file ...]
       sftp [user@]host[:dir[/]]
       sftp -b batchfile [user@]host
krishna@ubuntu:~$ sftp -l mohan 10.40.70.68 : /home/mohan/link
usage: sftp [-1246Cpqrv] [-B buffer_size] [-b batchfile] [-c cipher]
          [-D sftp_server_path] [-F ssh_config] [-i identity_file] [-l limit]
          [-o ssh_option] [-P port] [-R num_requests] [-S program]
          [-s subsystem | sftp_server] host
       sftp [user@]host[:file ...]
       sftp [user@]host[:dir[/]]
       sftp -b batchfile [user@]host
krishna@ubuntu:~$ sftp -l mohan 10.40.70.68: /home/mohan/link
usage: sftp [-1246Cpqrv] [-B buffer_size] [-b batchfile] [-c cipher]
          [-D sftp_server_path] [-F ssh_config] [-i identity_file] [-l limit]
          [-o ssh_option] [-P port] [-R num_requests] [-S program]
          [-s subsystem | sftp_server] host
       sftp [user@]host[:file ...]
       sftp [user@]host[:dir[/]]
       sftp -b batchfile [user@]host
krishna@ubuntu:~$ sftp -o mohan 10.40.70.68: /home/mohan/link
command-line: line 0: Bad configuration option: mohan
Couldn't read packet: Connection reset by peer
krishna@ubuntu:~$ sftp -o 10.40.70.68 
usage: sftp [-1246Cpqrv] [-B buffer_size] [-b batchfile] [-c cipher]
          [-D sftp_server_path] [-F ssh_config] [-i identity_file] [-l limit]
          [-o ssh_option] [-P port] [-R num_requests] [-S program]
          [-s subsystem | sftp_server] host
       sftp [user@]host[:file ...]
       sftp [user@]host[:dir[/]]
       sftp -b batchfile [user@]host


```

---

### Post by spjackson on 2012-11-26
> **Mohan1289 said:**
> What i have to do is download a certain file from the server and move it to my home folder..

It sounds like scp would be better for this than sftp.
```

scp mohan@10.40.70.68:/path/to/remote/file  ~/

```
To use sftp, you could set up a batch file with cd and get commands, then do:
```

sftp -b name_of_batch_file mohan@10.40.70.68

```

---

### Post by Lars Noodén on 2012-11-26
Oops.  I wrote the wrong line.  -l does not work for sftp so it would work like this instead:

```

sftp mohan@server.example.org

```

---

### Post by Mohan1289 on 2012-11-26
> **Lars Noodén said:**
> Oops.  I wrote the wrong line.  -l does not work for sftp so it would work like this instead:

```

sftp mohan@server.example.org

```


I tried like this in a normal terminal

```

sftp mohan@10.40.70.68:/home/mohan/link

```

then it prompt me for the password?? can't i get the file without prompting for the password of mohan at the server?

---

### Post by Lars Noodén on 2012-11-26
To get a file without the password, you'll have to set up a web server or an Anonymous FTP server and then put the file in the directory that is published by the server.  Apache is by far the most common web server, but nginx is gaining in popularity.

---

### Post by Mohan1289 on 2012-11-26
> **Lars Noodén said:**
> To get a file without the password, you'll have to set up a web server or an Anonymous FTP server and then put the file in the directory that is published by the server.  Apache is by far the most common web server, but nginx is gaining in popularity.

how can i do that any INSTRUCTIONS?? please

---

### Post by nothingspecial on 2012-11-26
The best way to do that would be to set up keys

From your local machine

```
ssh-keygen
```

You can enter through the passphrase bit because if you use a passphrase then you will have to type it which defeats the object. Then

```
ssh-copy-id mohan@ip.address.of.server
```

You will have to type the servers password this time but after that you won't.

---

### Post by Mohan1289 on 2012-11-26
> **nothingspecial said:**
> The best way to do that would be to set up keys

From your local machine

```
ssh-keygen
```You can enter through the passphrase bit because if you use a passphrase then you will have to type it which defeats the object. Then

```
ssh-copy-id mohan@ip.address.of.server
```You will have to type the servers password this time but after that you won't.

i tried this but is it correct??
```

ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/krishna/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/krishna/.ssh/id_rsa.
Your public key has been saved in /home/krishna/.ssh/id_rsa.pub.
The key fingerprint is:
bc:27:80:fb:8c:5c:d0:46:18:0d:94:c8:27:d0:37:17 krishna@ubuntu
The key's randomart image is:
+--[ RSA 2048]----+
|.+ o++E.         |
|  = =oo          |
|   +.o.          |
|     + .         |
|    o + S        |
|     + . .       |
|    . . o .      |
|   . =   o       |
|    o o          |
+-----------------+


```

---

### Post by nothingspecial on 2012-11-26
yep, that looks good. Then

```
ssh-copy-id mohan@192.168.?.?
```

or what ever the ip address is.

---

### Post by Mohan1289 on 2012-11-26
> **nothingspecial said:**
> yep, that looks good. Then

```
ssh-copy-id mohan@192.168.?.?
```or what ever the ip address is.

This is what the output is 

```

 ssh-copy-id mohan@10.40.70.68
mohan@10.40.70.68's password: 
Now try logging into the machine, with "ssh 'mohan@10.40.70.68'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.


```

what should i do after this?

---

### Post by nothingspecial on 2012-11-26
That's right.

You should now be able to login or scp from that server without a password.

---

### Post by Mohan1289 on 2012-11-26
> **nothingspecial said:**
> That's right.

You should now be able to login or scp from that server without a password.

so can i download the file without being prompted for the password??

---

### Post by nothingspecial on 2012-11-26
yep

---

### Post by Mohan1289 on 2012-11-26
> **nothingspecial said:**
> yep


Thank you it's downloaded automatically thank you.. can you please explain me the use of ssh-keygen and then copying the id?

---

### Post by nothingspecial on 2012-11-26
You are creating a pair of keys. You send one to the server and you have one on your local machine. When you attempt to connect to the server via ssh (which includes scp) the server asks if you have a key. You show it your key and it checks it against the one you sent it. Because they match up, the server knows it's you and lets you in ...........


........ sort of.

Keys are generated with fancy random maths stuff and are much more secure than passwords. There is some information on the wiki

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Somewhere on this forum is a very good analogy that explains gpg, keys and all this stuff really well but I can't find it right now.

---

