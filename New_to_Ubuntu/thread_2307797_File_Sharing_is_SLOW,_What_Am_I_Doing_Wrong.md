---
title: "File Sharing is SLOW, What Am I Doing Wrong?"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by snap-hiss on 2015-12-28
I have set up a shared folder on my Ubuntu machine. When I try to transfer files to an OSX machine the transfer rate is insanely slow (like 20 min to transfer 700 MB) is this normal? What can I do to fix this?

---

### Post by techvish81 on 2015-12-28
are you using wifi?

---

### Post by snap-hiss on 2015-12-28
yes

I take it that is not the best way to do things? How would I fix this?

---

### Post by Herdo on 2015-12-28
Well you could simply plug both devices into the router.

Are you using Samba to create the shared folder?

---

### Post by snap-hiss on 2015-12-28
Yes, I am using samba. I did try plugging both machines into the router, but this did not seem to make a difference in speed.

---

### Post by Vladlenin5000 on 2015-12-28
Then you're using an emulated Windows protocol between two non-Windows machines...

---

### Post by HermanAB on 2015-12-28
You need to run tcpdump and see what is going on:

ifconfig 
(to get the ethernet port name)

tcpdump -nXl -i ethernetportname

You should quickly get an idea of what request is hanging and retrying.

---

### Post by Morbius1 on 2015-12-29
> When I try to transfer files to an OSX machine the transfer rate is  insanely slow (like 20 min to transfer 700 MB) is this normal?
A file or many files at the same time?

If the objective is to copy a file from point A to point B and the size of the file is that big you could set up an http server on the Ubuntu box and "pull" the file from OSX:

*** Open a terminal.
*** cd to the folder that contains your files
*** Run the following command:
```
python -m SimpleHTTPServer
```

On OSX open Safari or whatever you are using as you internet browser and enter:
```
ubuntu-host-name.local:8000
```
Using the real host name instead of "ubuntu-host-name" or if avahi isn't working on your ubuntu machine the ip address:
```
192.168.0.100:8000
```

Now the only problem is directories. A directory is something your browser will open not something it will download. If you want to transfer an entire directory you will need to create an archive from it. Doesn't have to be compressed but it needs to be a single entity archive.

To end the server enter:
Ctrl+Z

[COLOR=#0000cd]*FYI: Samba ( well, it's Apple's own compatible version of SMB ) is the default file sharing mechanism in OSX. Has been for some time now. *[/COLOR]

---

