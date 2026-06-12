---
title: "Do you have to build the website on the actual computer running your Ubuntu Server"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by dan77 on 2014-04-02
hello;
I have several website domains that have been built on a different computer in my house and all the files are on that computer.  Do I have to rebuild them on the Ubuntu Server or can I link them to the server as I would a nameserver change from GoDaddy?
I am confused on a lot of aspects.  I have my Ubuntu Sever computer already running on a different terminal in my house but just not sure how to proceed.

---

### Post by SeijiSensei on 2014-04-02
Are you saying that you have folders with web pages in them like index.html?  You can just copy those folders to the appropriate locations on the server and [create virtual host definition]("https://help.ubuntu.com/12.04/serverguide/httpd.html")s for each site.  

If you mean you want to be able to put the websites on the server, but edit them from other machines, then you'd need to share the server's directories with something like [Samba]("https://help.ubuntu.com/community/Samba") for Windows clients or [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for Linux clients.  If you're comfortable editing the files with a text editor, you can just use SSH to log into the server and edit the files there with something like nano or emacs.  (That's what I do.)

---

### Post by dan77 on 2014-04-02
I use Joomla so I can upload the files to the server than log in online as an administrator and work from a different computer but I guess any new files, docs, jpgs, I may add would have to be copied and uploaded to the Ubuntu server itself correct???

---

### Post by sandyd on 2014-04-02
> **dan77 said:**
> I use Joomla so I can upload the files to the server than log in online as an administrator and work from a different computer but I guess any new files, docs, jpgs, I may add would have to be copied and uploaded to the Ubuntu server itself correct???

You will have to copy/export the joomla database as well and update the log paths in the configuration file.

---

