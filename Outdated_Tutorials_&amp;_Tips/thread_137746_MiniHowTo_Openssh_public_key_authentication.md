---
title: "MiniHowTo: Openssh public key authentication"
date: 2006-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Rizado on 2006-02-28
First of all I assume you have some basic knowledge in how ssh works. If you don't, you should get some first. Not much, but you should know what it is and how to edit the config files (Although I'll cover most of those steps)

What is public key authencation? Well, as you know when you ssh into a computer you're asked for a password. Enter the correct one and you're in. This requires a good password to stop other people to also enter your computer. Sadly good passwords are often long and hard to remember, and is still not really that safe. A safer and often easier way is to use public key authencation. On the server you have a public key which everyone can see but to access the computer you'll need a private key that matches.
The private key looks something like this: 
```
-----BEGIN DSA PRIVATE KEY-----
MIIDPQIBAAKCAQEAz4ugnE2whL4hiZ7KVR1IykfX/Y/u9mBfz3MYQwe/oDf4WlzX
cJu5PGW50RU9cVYHebpTZASNY2x33yVMC2Bz1RRcKjglMRSe4yRZuY4eE07ejD7i
ZLHtA9VI+vzoNn26KCOKJVdj4BC9fWrLBR0XpfiKlRfvAmiwehRFBZ9UB+4dewCC
oCLwL/EzOD0YdT7JKzSlwHlMNach++RmMSqQYhywNDUAMI4Tqfk/aRU+SfLVjmka
/b0g+ihICZf14Tqmndwz+831+ddvKjRrGthMlhOd416apCspuWY+M8IdnU6/wMKx
19PH1SC28rur6ich1ZPxN4NWWQJPXuafkV/t5wIVAJrBzmPQQDFuazZyWshLGx2S
nBBVAoIBAF3jIeQ1Ls3pyi5+InZuecEHT4HdaG5pDa3DX/yQM5dDiUVPQeODySV/
JjeZst0IVdiuw/7dFrd3f6LV3x5xojCwTowWZOBi27ZwswILFxVii7aph5NPC+u+
Qrc2/ib5q4e3JXvol5w0/s2lEQABZ4XCHF7qdcULkGa675s3JWQiN2/XhVWj+cQT
7PpY0UVj5HVAQMuCUnnWpEIjsmUoxECxScUf0dEqQaAEu3XxZ62XpP0z6jm46cJO
CrAyBXh4f15CNLjGKBdgAK9a8ehc75zDHCJ9mhV+o7EMikjrceZ1zB0HNxXFJuBT
CegF6OIdG2sIoWQ+cUvdJdf8Sv0Pt6ICggEAWzmRek3rtw6AHyvup7PUv7LJYTR5
f4y6nUmGEIvBFba25aBXg3l+eyVjqsNCUykDGSn5eOKk9HucMDiaHEooJAs+/a9W
55XMtbQ7QeaAmVcIFnxB2u6/uFOBWR7Q7q7bTPJ9e6YZ43ZFXjj3GspcnSPr5yHI
iiyWtC/oUrslMKqVgUyNpmsHkvxC6neAxLKXXehSREkerxcyeWPEi7wv/HV6r1VG
YM4TS+hgKpx2x6pxnEBjP8Dm65+55bHw/fssxrOj2CeZSxUvOL3LPez9GJsSemD6
NP+1Qz0EiatxjoDM5mCMPzgqHa9sBjY1cflRI56HCEZVn9kxxTse94CZRwIUZxJG
GOZ8lrwYzjj7n3shcw5t6TA=
-----END DSA PRIVATE KEY-----

```This is a 2048 bit dsa private key. Not the easiest thing to bruteforce :cool:
To log into a server your private key must match the public key. I'm sorry if it's hard to follow, this is my first howto.

First of you need to create a public key and private key. It should be done on a client, but can be done on the server as well. This is done by:
```
ssh-keygen -t dsa -b 1024
```This will create a 1024 bit dsa key. You can change 1024 to whatever you want, higher is more secure, but will take longer time and 1024 is perfectly enough (should take years to crack). It's also the default. 512 is the minimum.  **It is no longer possible to create dsa keys other than 1024bit.** You'll be asked where to save it, the default is fine. And then a passphrase (Just like a password). Most people would say use atleast 10 characters and upper and lowercase and so on, I say it's not necessary at all. If you don't have any military secrets or something else that has to be protected it's fine with a much shorter one, or none at all. A potential bad guy would still need your privatekey. The passphrase is just a password for the privatekey.

Now you should have two new files in /home/username/.ssh/ called id_dsa and id_dsa.pub. id_dsa.pub is the public key which we now are going to move to the server (Or if it's already there.) This can be done in hundreds of ways. I just mounted a nfs partition but one really nice way I've also learned to use is scp. ```
scp id_dsa.pub rizado@192.168.0.1:/home/rizado
```You will be promted for password and if everything work id_dsa.pub should end up in /home/username on the server.
When you've transfered id_dsa.pub to the server it should be moved to "/home/username/.ssh and renamed authorized_keys. In my case: ```
mv id_dsa.pub /home/rizado/.ssh/authorized_keys
``` Once again this is on the server. Also make sure you DON'T have the private key (id_dsa) on the server at all. It should be safely placed in /home/username/.ssh on a client, on a memorystick, a floppy or any good place you can think of.

Now it's time to open the config file. It's located on the server: /etc/ssh/sshd_config
Do
```
sudo vi /etc/ssh/sshd_config
```Here we are going to check two lines. There should be "%h/.ssh/authorized_keys" and "PubkeyAuthentication yes". If they aren't there, create them. Also make sure they're not commented out (no ; or # infront of them)

Now it's time to try everything out. On the server do ```
sudo /etc/init.d/ssh restart
``` This should kick you out of ssh, if it doesn't just type exit, this is of course if we are using ssh to access the server.
Now it's time to do some client work. Ssh will ignore keys with too open permissions so we need to change those. Simply run "chmod 600 /path/to/id_dsa". 
 Make sure you have "id_dsa" in "/home/username/.ssh" and log into the server as usual. This time you should be greeted with "Enter passphrase for key..." if you choose to use a passphrase or simply be logged in if you didn't.
Note that if you don't want to keep id_dsa in /home/username/.ssh you will have to run ssh like this: ```
ssh -i /path/to/id_dsa iptoserver
```
If everything went fine it's time to disable the old password authentication. On the server open /etc/ssh/sshd_config again and make sure the line "PasswordAuthentication no" exist. Change the existing one or create it. It's probably a good idea to make sure that "PermitRootLogin" is set to no as well as it's a security risk. Save changes and restart ssh again.

The downsides of public key authentication is that you have to have the privatekey whenever you want to log into the server. I have solved this by keeping it on a memorystick along with putty and a puttyprivate key and I carry this with me wherever I go. Another cool solution (But maybe not so practical) would be to keep it on a mobile phone.

Note that if you want to use putty to log in you have to download puttygen and load id_dsa and choose save to create a putty compatible privatekey.

EDIT: I changed a few things. With edgy it does not longer seem to be possibible to choose anything other than 1024bit for DSA keys. Otherwise this guide should work just fine.

EDIT2: This is still working with feisty and I've also added a few things (like scp)

---

### Post by Rizado on 2006-03-02
I managed to press submit before it was finished so I finished it and pressed submit again, but the unfinished one was the one that showed up so I finished this one instead. Hope you'll find it helpfull and if there's any problems or anything you want to know don't hesitate to ask.

---

### Post by MighMoS on 2006-03-02
This is pretty helpful.  I've noticed that in /etc/ssh there are host_dsa keys.  What exactly are these -- are these just for the root user, or do they have a more generic function?

---

### Post by Rizado on 2006-03-02
Well i don't know for sure but they are needed (or atleast one of them. rsa or dsa) to load sshd. And they have something to do with host identification. When you first try to log in you are told that the authenticity of the remote host can't be established and gives you a fingerprint and askes you if you want to continue. You can create new ones with ssh-keygen just like creating public and private keys but they must only be accessible to root and can't have a passphrase. If you do that and try to log in with a client that has previously accessed the server you'll be told that the remote host identification has changed. Some configurations will simply lock you out untill you remove ~/.ssh/known_hosts while other will let you choose to enter anyway. This prevents a fake server to pretend to be the real server.

---

### Post by andiii on 2006-09-20
Excellent tutorial, got everything to work in 5 minutes! Thanks.

---

### Post by aaronLund on 2009-07-02
Going on 3 years and this tutorial still rules.

Nice work.

---

