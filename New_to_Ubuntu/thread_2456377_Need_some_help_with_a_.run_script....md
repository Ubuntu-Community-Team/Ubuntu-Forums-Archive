---
title: "Need some help with a .run script..."
date: 2021-01-10
forum: New to Ubuntu
---

### Post by redrock14 on 2021-01-10
Hello -

Running Ubuntu 18.04 on an Intel NUC server.  

The installer for PIA VPN that gets downloaded from their Downloads page is a .run file.  I downloaded the file, opened Terminal and went to Downloads.

I then ran the file and got a "permission denied" error:

./pia-linux-2.6.1-05824.run
Verifying archive integrity...  100%   MD5 checksums are OK. All good.
Uncompressing Private Internet Access  100%  
./pia-linux-2.6.1-05824.run: 1: eval: ./install.sh: Permission denied

I made sure the file was an executable by:

chmod u+x pia-linux-2.6.1-05824.run

Tried it again, and the error came up.  

After hours of RTFM, I found the .run command has arguments.  I tried 

./pia-linux-2.6.1-05824.run --target mytempdir

And this worked as it was supposed to work.  

I don't understand what is going on.  I've spent hours trying to figure this out - i am sure this is a Linux thing.  I would like to learn something.  Why did this work with the --target option?

Thanks!

---

### Post by CatKiller on 2021-01-10
> **redrock14 said:**
> I don't understand what is going on.  I've spent hours trying to figure this out - i am sure this is a Linux thing.
It's not "a Linux thing," since .run files are used to bundle a script and binary data together, which is very much a not-Linux way of doing things. The Linux thing would be distributing the source so that distro maintainers could create a native package to be installed with a package manager.

What it is, though, is a multiuser OS thing. Your usual account has no permissions to write anywhere but your home directory and per-user temporary files. If your user account has the correct privileges, you can temporarily elevate your privileges to those of root or a different user, which allows you to write elsewhere. By giving that script an explicit target that you are able to write to, rather than wherever it was trying to use before, it was able to complete its task, whatever that was.

---

### Post by redrock14 on 2021-01-10
Thank you.

In the middle of all my reading, I did see the .run type package is not a preferred way of doing things as you mentioned in your reply.  And the multiuser settings make sense now.  Essentially the "automated" way in which the script runs and creates the behind-the-scenes folder is where the problem is at.  The permission was not set properly, however when the destination folder is mentioned explicitly then it works.

Thank you.

---

### Post by TheFu on 2021-01-10
Generally,  VPN installation and startup requires elevated access.  More more secure OSes have this requirement.
I've never used the PIA installer, but have been a customer for a few years. Usually, I just use the openvpn package from the repos and grab the ovpn config files from PIA and use those.

The short answer, with a tiny bit of risk, is to use sudo with the command.
```
sudo /path/to/pia.x.x.x.run
```

More details:
Linux doesn't care about extensions. .run mean nothing special to the OS.  Neither does .sh or even .pdf.  On Unix-like OSes (basically every popular OS today except 1), the header of each file is checked to determine the type of file it really is.  Some GUI programs will filter file lists using extensions, but the OS does not care. We can use the 'file' tool to check the type of file.
```
file /path/to/pia.x.x.x.run
```
for example.

---

### Post by #&amp;thj^% on 2021-01-10
Never had a problem 5 years with PIA
```
bash pia-linux-2.x.-05676.run
```
After a CD to the installer.
Or even:
```
 sh pia-linux-2.6.1-05824.run
```
That version is current as of 1/10/2021

---

