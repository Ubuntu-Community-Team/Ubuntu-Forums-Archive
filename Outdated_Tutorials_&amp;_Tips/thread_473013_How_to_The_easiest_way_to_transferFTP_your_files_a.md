---
title: "How to: The easiest way to transfer/FTP your files among machines"
date: 2007-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by morningboat on 2007-06-13
Want to share the files between machines but don't know how? Want to setup an FTP server but being afraid of the complexity? Don't worry, here is an simple and easy GUI way for you to do this:

This is a guide for people to easily setup an FTP server, and use a FTP client to transfer files between machines. It will use the FTP tool called [CrossFTP Server]("http://www.gnomefiles.org/app.php/CrossFTP_Server") and [CrossFTP Client]("http://www.gnomefiles.org/app.php/CrossFTP_Client"). 

[LIST]
[*]System Requirement: [Install Sun Java 1.4+]("http://ubuntuforums.org/showthread.php?t=422692")
[/LIST]

[LIST]
[*]Install and Start FTP Server
[LIST]
[*]**Install**: Click [Web Start Now](http://www.crossftp.com/crossftpserver.jnlp)  and open it by Java Web Start (javaws). The server will be directly installed and run.
[*]**Configure**: Click "Configure" to setup the *port*, *max login*... Choose a port > 1024 since small number requires Administration right.
[*]**Add User and directory**:  Click "User", "Add" a user, setup its username and password, directory, and press "Save". See the attached picture.
[*]**Start**: Press "Start Server". That's it.
[/LIST]
[/LIST]

[LIST]
[*]Install and Start FTP Client, and test the server.
[LIST]
[*]**Install**: Click [Web Start Now](http://www.crossftp.com/crossftp.jnlp)  and open it by Java Web Start (javaws). The client will be directly installed and run.
[*]**Connect**: Fill in your FTP server's address (if on the same machine, you can use localhost, otherwise, put in the IP address, which can be checked by ipconfig), port, username and password, click connect, you won't miss it.
[/LIST]
[/LIST]

Everyone should be able to make it in 5 minutes. Here are two screenshots. Hope this will solve your problem easily. For more information, check this [online guide]("http://www.crossftp.com/server_guide.htm").

---

