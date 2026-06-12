---
title: "How to copy file from external server to my local machine via CLI???"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2011-09-15
Hi,

I am logged into (ssh@ via CLI) one of my organizations servers that is hosted down the street.

I need to:

1) Copy the file on the server to my laptop
2) Edit the file
3) Upload the new file from my laptop to the server again.


I believe I can upload the file with the scp command, yes?

But I don't know how to do step one (copy file from server to my computer).

Does anyone know how to do this??

I want to do this via CLI because Filezilla is giving me problems.

Thanks,
Chris

---

### Post by nothingspecial on 2011-09-15
You do it with scp

```
scp /path/to/file user@ip_of_laptop:
```

Or you could just edit it on the server.

---

### Post by haqking on 2011-09-15
> **pcvchriskmg said:**
> Hi,

I am logged into (ssh@ via CLI) one of my organizations servers that is hosted down the street.

I need to:

1) Copy the file on the server to my laptop
2) Edit the file
3) Upload the new file from my laptop to the server again.


I believe I can upload the file with the scp command, yes?

But I don't know how to do step one (copy file from server to my computer).

Does anyone know how to do this??

I want to do this via CLI because Filezilla is giving me problems.

Thanks,
Chris


scp yes, but also sftp using get and put commands

[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

[http://manpages.ubuntu.com/manpages/intrepid/man1/sftp.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/sftp.1.html)

you might want to rsync the file back to reflect the changes, and you best make a backup incase you do something wrong ;-)

---

### Post by sanderd17 on 2011-09-15
you can install the sshfs package and mount the directory with the following command:

```

sshfs USER@remote_server:/home/user/directory-to-be-mounted ~/remote_folder

```

Make sure that ~/remote_folder is an existing but empty directory on your machine.

---

### Post by pcvchriskmg on 2011-09-15
> **nothingspecial said:**
> You do it with scp

```
scp /path/to/file user@ip_of_laptop:
```

Or you could just edit it on the server.

It is a basic text file that I need to insert telephone numbers into. Where could I learn how to do this directly on the server??

---

### Post by haqking on 2011-09-15
> **pcvchriskmg said:**
> It is a basic text file that I need to insert telephone numbers into. Where could I learn how to do this directly on the server??

if you want to do it directly, you can do it using your direct ssh connection and changing to the directory where it is.

or use SSHFS which mounts the remote system locally.

---

### Post by nothingspecial on 2011-09-15
The easiest way would be to use the nano text editor.

nano file.txt

Insert numbers then

Ctrl-O to save
Enter to confirm
Ctrl-X to exit

---

### Post by weird0.kid on 2011-09-15
are you using windows on your desktop?

maybe winscp would be the way to go for you?

---

### Post by staticd on 2011-09-15
You could use an editor like vi. try vimtutor(a text file utorial) for an excellent introduction. Helped me when I was a command line noob.

Or else use

[code]
ssh -X user@server
$gedit path/to/myfile
[\code]
 
Allows you start graphical editors like gedit /nano etc on your server and have the window appear locally.

The best results for me were always through sshfs/sftp.

---

### Post by haqking on 2011-09-15
> **staticd said:**
> You could use an editor like vi. try vimtutor(a text file utorial) for an excellent introduction. Helped me when I was a command line noob.

Or else use

[code]
ssh -X user@server
$gedit path/to/myfile
[\code]
 
Allows you start graphical editors like gedit /nano etc on your server and have the window appear locally.

The best results for me were always through sshfs/sftp.


ssh -X assumes X forwarding is setup and/or allowed from the remote server however and across a WAN can be very laggy.

---

### Post by alarme on 2011-09-15
This is not for CLI, but if your laptop is running some version of Gnome:

Open nautilus
CTRL-L to show address bar
write  ssh://username@server
login
navigate
double click to edit, copy, paste...

voila

---

### Post by pcvchriskmg on 2011-09-15
> **sanderd17 said:**
> you can install the sshfs package and mount the directory with the following command:

```

sshfs USER@remote_server:/home/user/directory-to-be-mounted ~/remote_folder

```

Make sure that ~/remote_folder is an existing but empty directory on your machine.

After trying the scp route and ultimately failing, this is the option I was able to get to work. And it worked like a charm! Problem solved :)

---

### Post by pcvchriskmg on 2011-09-15
> **alarme said:**
> This is not for CLI, but if your laptop is running some version of Gnome:

Open nautilus
CTRL-L to show address bar
write  ssh://username@server
login
navigate
double click to edit, copy, paste...

voila
 
Voila is right; thanks, this is really easy. I'm certainly not going to forget this trick.

Chris

---

