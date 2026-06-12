---
title: "HOWTO: Set up BackupPC Server for Win, Mac, Linux Clients"
date: 2007-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by tak1150 on 2007-09-17
I have written a comprehensive how-to article that is easy to understand and comes with step-by-step instructions and copy-n-pastable commands and so forth. This how-to should apply to any clients, Windows XP, Mac OS X, and Linux.

It took me a while to get the backup server going and wished that I had access to a how-to article like the one I've written. So I am hopeful that people will benefit from this.

I'll be happy answer questions here in this thread.

The link to the article is [[SIZE="4"]HERE[/SIZE]]("http://taksuyama.com/?p=13"). Enjoy.

---

### Post by peachy on 2007-10-24
Excellent howto, deserves a bump.

I too had to setup it on my own, wish i'd read your guide first, would have saved me a fair few hours.

---

### Post by jwillar on 2007-10-26
I am still unsure how to install/setup BackupPC for my home network. I have three systems running Kubuntu 7.10 with a 250GB NAS drive for common data storage on my network (no server, just a router).  At first I thought BackupPC would be perfect but now seeing all your references to installing it on a server, I am having doubts. Will I need to configure my laptop as a “server”? Will this cause harm to my otherwise normal use of my laptop?

Thanks,
jwillar

---

### Post by tak1150 on 2007-10-27
Hi jwillar,
I responded to you on [my website]("http://taksuyama.com/?p=13").

---

### Post by jcottier on 2008-02-08
I cant find how to find (or configure) the IP address for the web server.
If run sudo dpkg-reconfigure backuppc (on Gutsy 71.0) I just get this:-


  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring backuppc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474; BackupPC supports any web server with CGI enabled, but this automatic   &#9474;
  &#9474; configuration process only supports Apache.                             &#9474;
  &#9474;                                                                         &#9474;
  &#9474; Which web server would you like to reconfigure automatically:           &#9474;
  &#9474;                                                                         &#9474;
  &#9474;    [ ] apache                                                           &#9474;
  &#9474;    [ ] apache-ssl                                                       &#9474;
  &#9474;    [ ] apache-perl                                                      &#9474;
  &#9474;    [ ] apache2                                                          &#9474;
  &#9474;                                                                         &#9474;
  &#9474;                                                                         &#9474;
  &#9474;                                 <Ok>                                    &#9474;
  &#9474;                                                                         &#9474;
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

I do not know what the options are for, I have tried selecting apache and apache2. 

Then I am asked if I want to restart the webserver and I get this:-

 * Stopping backuppc...                                                  [ OK ]
Your MPM seems to be threaded. Selecting cgid instead of cgi.
This module is already enabled!
 * Starting backuppc...    

This does not seem to correspond with anything I have read so far :confused:

---

### Post by asmiller-ke6seh on 2008-02-08
TAK,

Thank you - I would have thanked you through the new system, but this thread originated before that feature was added.

This is just what I need for when I set up my household server in the next couple of months. My wife never backs up her PC, no matter how much I remind her ... so I am going to set up a household server for backup and as a media storage server as well as an extended external storage device for the whole house.

---

### Post by jamespetts on 2009-01-28
I'm afraid that this doesn't work for me, for reasons that are utterly opaque and incomprehensible. I followed the instructions exactly on both client and server, but when I execute the command:

*ssh -l root parlour whoami*

(parlour being the server - the result is no different when I use the IP address), I get the following error:

*ssh: connect to host parlour port 22: Connection refused*

I have spent a very long time trying to get this to work, and find this problem bizarre and incomprehensible. I should be extremely grateful for any suggestions as to what to do next.

---

