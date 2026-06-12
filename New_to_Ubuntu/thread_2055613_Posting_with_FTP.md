---
title: "Posting with FTP?"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Konchok11 on 2012-09-09
Post subject: Posting with FTP? 
Posting with FTP [File Transfer Protocol] 
USED TO be built right in to Firefox! 
In Firefox 11, this has disappeared! 
I have about 10 Gigs of .WAV files 
I want to upload to the web. 
I no longer have ANY CLUE 
how to do this! 
 
Can someone please tell me 
how I would go about this now? 
 
MY SYSTEM IS UBUNTU LINUX! 
HOW DO I POST FILES TO THE WEB? 
 
PLEASE HELP ME! 
 
KP

---

### Post by shreepads on 2012-09-10
Don't have to use Firefox, there are a number of other FTP clients available in the repos.

See this:
[http://www.ubuntugeek.com/list-of-ftp-clients-available-in-ubuntu-linux.html](http://www.ubuntugeek.com/list-of-ftp-clients-available-in-ubuntu-linux.html)

---

### Post by Wim Sturkenboom on 2012-09-10
Command line ftp client is installed by default, if I'm not mistaken. Or install a graphical FTP client (filezilla, ..., see earlier post).

> 
You can also email me at:
.....

Remove your email address; it's an invite to get spammed.

---

### Post by Lars Noodén on 2012-09-10
There is also a good text-based FTP client included in the package ncftp.  

For graphical FTP clients you can look at Nautilus or Dolphin.  In either Nautilus or Dolphin, press ctrl-L and then enter the URI for the FTP site.  

It might also be an opportune time to move beyond FTP:
[list]
[*][http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*][http://www.openlogic.com/wazi/bid/188103/](http://www.openlogic.com/wazi/bid/188103/)
[/list]

FTP is unsafe for uploads.

---

### Post by Paqman on 2012-09-10
I've always just used the file manager (Nautilus) to connect to servers. It can handle FTP and more secure things like SFTP and SSH. Open a file browser window and File > Connect to server. Easy peasy.

---

### Post by Zill on 2012-09-10
Konchok11:  If you wish to use Firefox then just install the extension [FireFTP]("http://fireftp.mozdev.org/").

---

