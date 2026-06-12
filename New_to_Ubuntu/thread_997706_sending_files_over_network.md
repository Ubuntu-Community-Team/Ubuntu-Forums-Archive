---
title: "sending files over network"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by ja660k on 2008-11-30
hey guys i have my other laptop with ubuntu on it which im about to retire and it will be taken over by the one im using, now i need a way to send files over my network...

something like ssh or sftp or scp

what programs do i need for this..?

---

### Post by Rhubarb on 2008-11-30
If both computers are on a local network, then install ssh on one (or both) computers:-

Open up a terminal (Applications --> Accessories --> Terminal), and enter this in:
```
sudo aptitude install ssh
```
This will install the open ssh server.
Now from the other computer you can browse (and hence share files) with it by:

Places --> Connect to Server ...
Service type: SSH
Server: the IP address of the computer with the SSH server on it
User Name: Your user name on the computer with the SSH server on it

Then press Connect.

It should prompt you for your SSH server's password, enter it in.
You'll find your home directory in /home/your_user_name/

Then you can copy across files and folders easily.

---

### Post by ja660k on 2008-11-30
```
ja660k@linUx:~$ sftp john@192.168.0.12
Connecting to 192.168.0.12...
ssh: connect to host 192.168.0.12 port 22: No route to host
Couldn't read packet: Connection reset by peer
```

thats what happens, the same when i use connect to server...


when i ifconfig on the laptop i wish to connect to. which am i looking for the bcast or the inet addr
cos neather of them work :-S

i also chmod 777 to my home dir... i know its bad but it didnt solve problem

---

### Post by shafi on 2008-11-30
> **ja660k said:**
> ```
ja660k@linUx:~$ sftp john@192.168.0.12
Connecting to 192.168.0.12...
ssh: connect to host 192.168.0.12 port 22: No route to host
Couldn't read packet: Connection reset by peer
```

thats what happens, the same when i use connect to server...


when i ifconfig on the laptop i wish to connect to. which am i looking for the bcast or the inet addr
cos neather of them work :-S

i also chmod 777 to my home dir... i know its bad but it didnt solve problem

for transferring files over network use Samba , you can find many tutorials how to do this on Google.

---

### Post by Rhubarb on 2008-11-30
> **ja660k said:**
> when i ifconfig on the laptop i wish to connect to. which am i looking for the bcast or the inet addr
cos neather of them work :-S

It's your inet addr that you need to use.
Another way to find your IP address, is to right click on the network manager (top right of the screen) --> Connection Information

You should be able to ping the other computer's IP address.
```
ping 192.168.0.12
```

The two computers must be networked for this to work.
Samba is another way that may work for you (Right click on the folder you wish to share, then select "Sharing Options".

---

