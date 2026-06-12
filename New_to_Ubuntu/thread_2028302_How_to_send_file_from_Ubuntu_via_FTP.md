---
title: "How to send file from Ubuntu via FTP"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by rollin77 on 2012-07-17
I have a file on an Ubuntu system that is an .ISO image, but the Ubunto system doesn't have a DVD burner so I need to send it to my Windows 7 system so I can burn it into a disc.

I have Solarwind's TFTP server installed on my Windows 7 PC, but I have no clue how to send the file from Ubuntu to my Windows PC.  

Any help?  Thanks in advance!

---

### Post by anewguy on 2012-07-17
Not an answer to the FTP question, but a way to solve your problem.  Most USB flash drives are large enough to store an ISO image, so why not just copy to a flash drive and take it to the other system?

---

### Post by critin on 2012-07-17
> **rollin77 said:**
> I have a file on an Ubuntu system that is an .ISO image, but the Ubunto system doesn't have a DVD burner so I need to send it to my Windows 7 system so I can burn it into a disc.

I have Solarwind's TFTP server installed on my Windows 7 PC, but I have no clue how to send the file from Ubuntu to my Windows PC.  

Any help?  Thanks in advance!

If you set up sharing, you can access the iso from Windows and point the burner to it.  I do it all the time with unetbootin.  

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

---

### Post by rollin77 on 2012-07-18
Thanks for the tips guys but I figured it out...I could have cleaned out my flash drive but kinda wanted to figure out how to FTP from Ubuntu command line anyway.

---

### Post by critin on 2012-07-18
> **rollin77 said:**
> Thanks for the tips guys but I figured it out...I could have cleaned out my flash drive but kinda wanted to figure out how to FTP from Ubuntu command line anyway.

Have you googled?

---

### Post by rollin77 on 2012-07-18
> **critin said:**
> Have you googled?
Of course I did, and if you had to you would see that you get more results on setting up an FTP server in Ubuntu as opposed to what I was asking for help with.

---

### Post by Wim Sturkenboom on 2012-07-18
> **rollin77 said:**
> Thanks for the tips guys but I figured it out...I could have cleaned out my flash drive but kinda wanted to figure out how to FTP from Ubuntu command line anyway.
And the solution was .... Can be useful for others as well. My attempt would be ftp from the command line :)

> **rollin77 said:**
> Of course I did, and if you had to you would see that you get more results on setting up an FTP server in Ubuntu as opposed to what I was asking for help with.
:lolflag:

---

### Post by audiomick on 2012-07-18
> **rollin77 said:**
> ... wanted to figure out how to FTP from Ubuntu command line anyway.

Did you find out how to do exactly that? If you are still interested, make sure the package "ftp" is installed and then do 
```
man ftp
```
in a terminal to see the manual page for it. I have to admit, I don't really understand all of that. When I have had to do ftp transfers, I have always used filezilla. This is a graphical program, I believe a front end for the ftp package, and would also do what you wanted to do, albeit not from the terminal.

---

### Post by critin on 2012-07-19
> **rollin77 said:**
> Of course I did, and if you had to you would see that you get more results on setting up an FTP server in Ubuntu **as opposed to what I was asking for help with.**

> I have a file on an Ubuntu system that is an .ISO image, but** the Ubunto  system doesn't have a DVD burner so I need to send it to my Windows 7  system so I can burn it into a disc.**

I have Solarwind's TFTP server installed on my Windows 7 PC, but **I have  no clue how to send the file from Ubuntu to my Windows PC.  **

Any help?  Thanks in advance!No, I didn't google FTP.   I was simply addressing the burning issue as you presented it.  [B]You needed to transfer a file from one pc to another in order to burn it.
[/B]
Sorry that I wasn't helpful and sorry it turned into a joke.  Perhaps the question should have put the stress on how to use FTP to transfer and left the 'why I need it' out.

Good luck!

---

### Post by rollin77 on 2012-07-19
> **audiomick said:**
> Did you find out how to do exactly that? If  you are still interested, make sure the package "ftp" is installed
That's what I did, I'm using an older version of Ubuntu, (10.04), that apparently doesn't come with ftp pre-installed, but it looks like newer versions do.   I don't remember the exact commands, but I  believe I did something like '**sudo apt-get install ftp**', then after that  just typed ftp to start the ftp program.  I thought I typed '**connect <ip address>**' to connect to my windows PC, but I can't repeat this process now.  I'm probably just missing something because you should just be able to type **'ftp <ip address>'** in terminal to connect to an ftp server, and all I had to do before on the windows side was just start up Solarwind's free tftp server program.

Once I was connected to the windows pc it was just a matter of navigating to the correct directory where the file was you want to send, and type '**put <filename**>' to start the transfer.  Unfortunately sending a 1.4Gb ISO file through an old router's 100mb ports equates to a 30 minute wait for a corrupted file.....but sometimes I like doing things the hard way just to see what happens :)

---

### Post by rollin77 on 2012-07-19
> **critin said:**
> Perhaps the question should have put the stress on how to use FTP to transfer and left the 'why I need it' out.
Sorry my question was so complex and confusing, I guess "How to send file from Ubunto via FTP" in the title was not as clear as it could have been.

---

### Post by donkyhotay on 2012-07-19
I use gftp which is a GUI FTP client for ubuntu. It's in the repos so it's easy to install. Just launch it up, put in the IP address for the computer you want to connect to, any username/passwords you have set up on the host machine and connect. You can xfer back and forth to any FTP server even if it's a windows box.

---

### Post by alphacrucis2 on 2012-07-19
A good gui ftp client I have found is Filezilla which is available for linux, windows and os/x. It does ftp & sftp. No tftp but Filezilla also has a server version which you could install on windows if you wanted to do it that way around. A linux version of filezilla is in the Ubuntu repos.

---

