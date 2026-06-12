---
title: "HOWTO: Install Joomla over Xampp"
date: 2009-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by B4RR13N705 on 2009-05-29
After installing xampp:
>  [http://ubuntuforums.org/showthread.php?t=1109963](http://ubuntuforums.org/showthread.php?t=1109963) 
We will install joomla over xampp.
Download joomla latest version here:
>  [http://joomlacode.org/gf/download/frsrelease/9910/37908/Joomla_1.5.10-Stable-Full_Package.zip](http://joomlacode.org/gf/download/frsrelease/9910/37908/Joomla_1.5.10-Stable-Full_Package.zip) 
For the ones who dont know:
> 
Joomla is an award-winning content management system (CMS), which enables you to build Web sites and powerful online applications. Many aspects, including its ease-of-use and extensibility, have made Joomla the most popular Web site software available. Best of all, Joomla is an open source solution that is freely available to everyone.
A content management system is software that keeps track of every piece of content on your Web site, much like your local public library keeps track of books and stores them. Content can be simple text, photos, music, video, documents, or just about anything you can think of. A major advantage of using a CMS is that it requires almost no technical skill or knowledge to manage. Since the CMS manages all your content, you don't have to.

After downloading:
```

$ sudo cp Joomla_1.5.10-Stable-Full_Package.zip /opt/lampp/htdocs
$ cd /opt/lampp/htdocs
$ sudo tar -zxvf Joomla_1.5.10-Stable-Full_Package.zip

```
Rename the extracted folder as you like, for example, the name of your site. **I will name this folder like "*$joomla*"**
Now open you preferred Internet Navigator and go to:
>  http://<yourhost>/$joomla 
If you get a 404 Error, then:
```

$ sudo chmod a+x /opt/lampp/htdocs/$joomla

```
You will enter to the installation.
First, choose your preferred language.
Inside $joomla folder, create a file named *"configuration.php"* 
And:
```
 $ sudo chmod a+w configuration.php 
```
Click on NEXT.
Accept the license, and click NEXT.
Now it comes the most important part:
> 
Host name --> type here the name of your host, for example "localhost".
Username --> type here your MySQL username, for example "root".
Password --> type here your MySQL password.
Database --> type here your database name, for example "mysitedatabase".

Click on NEXT.
Configure here youre FTP config if you need to.
Click on NEXT.
> 
Sitename --> Your sites name, for example, "myjoomlawebpage"
Email --> type here admin's email.
Password -> type this the admin's password to manage the site.

You can install the sample data if you want, and load a migration script too.
Click on NEXT.
Now, **DELETE** your "$joomla/Installation" folder.
Click on ADMIN.
It will now ask you for the username and password, and youre ready to manage your own Joomla site! Good luck!!

---

### Post by niboraus on 2009-07-27
hi,

thanks for the details
i have LAMPP installed and working
when i try your example of 

$ sudo cp Joomla_1.5.10-Stable-Full_Package.zip /opt/lampp/htdocs
$ cd /opt/lampp/htdocs
$ sudo tar -zxvf Joomla_1.5.10-Stable-Full_Package.zip

its not working

i am running Ubuntu 9.04 under VirtualBox

however on the folder /opt/lampp/htdocs i have no permissions even though i am logged in at root as admin


is there something else i need to know?

regards

niboraus

---

### Post by B4RR13N705 on 2009-07-28
Maybe the name of the .zip package had change...
About the permissions try with chmod...

---

### Post by hotstepperk on 2009-09-15
hey. I'd like to know how to setup FTP with vsftpd. any way to do it? or is there no real need for FTP anyway. I'm having trouble setting it up with from this tutorial

[http://ubuntuforums.org/showthread.php?t=1255206](http://ubuntuforums.org/showthread.php?t=1255206)

---

