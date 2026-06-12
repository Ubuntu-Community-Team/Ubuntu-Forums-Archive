---
title: "SVN and NetBeans"
date: 2011-03-02
forum: Programming Talk
---

### Post by erotavlas on 2011-03-02
Hi,

I have some questions about the use of SVN and how I can use it from NetBeans. It's the first time that I use an SVN repository so I have followed the guide at this link [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion).

I can use with success the SVN via http with the same parameters reported in the previous link, but if I try to use custom folder the command ```
svn co http://hostname/svn/myproject myproject --username user_name
``` doesn't work anymore.

I have tried to use the following configuration
user group: subversion (it contains my user and www-data user)

```
sudo mkdir /home/myuser/svn
cd /home/myuser/svn
sudo mkdir myprojectsudo svnadmin create /home/myuser/svn/myprojectcd /home/svn
sudo chown -R www-data:subversion myproject
sudo chmod -R g+rws myproject
```After I have configured the apache server as following

in /etc/apache2/mods-available/dav_svn.conf

```
  <Location /myuser/svn>
     DAV svn
     SVNParentPath /home/myuser/svn
     SVNListParentPath On
     AuthType Basic
     AuthName "Subversion Repository"
     AuthUserFile /etc/subversion/passwd
     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
  </Location>
```After I have restarted the server and I have setted the password in  /etc/subversion/passwd file

```

sudo htpasswd -c /etc/subversion/passwd user_name
```Finally if I try to checkout the repository with 

```

svn co http://hostname/svn/myproject myproject --username user_name
```I get > Could not open the requested SVN filesystemHow can i solve it?

The second question is related to the connection between NetBeans and SVN. Team->subversion->checkout
After if I try to put the repository URL, I get

> org.tigris.subversion.javahl.ClientException: RA layer request failed
Server sent unexpected return value (504 Gateway Time-out) in response to OPTIONS request for 'http://ip/svn/myproject'Where could be the problem?

Thank you

---

