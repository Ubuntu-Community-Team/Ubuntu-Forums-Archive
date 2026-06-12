---
title: "users permissions in SVN"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by thepiston on 2008-10-25
I created an SVN repository and also a user using [this tutorial]("http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/") and this user creation code:```
sudo htpasswd -cm /etc/apache2/dav_svn.passwd <username>
```.  My users can log into it, but cannot post into the repository.  The root SVN folder is set to 775... am I missing something?

---

### Post by bodhi.zazen on 2008-10-25
It depends on who owns the directory.

You will need permissions of 7 on the directory (I usually make the directory owned by svn.www-data with permissions of 770 ).

How are you checking in ?

One disadvantage of http is it does not preserver who made the changes, for that you need ssh.

I wrote a "brief" how to here :

[How to ssh + svn](http://blog.bodhizazen.net/?p=6)

Hope that helps. It is slightly more difficult to get your users used to ssh, but it is more secure.

---

### Post by thepiston on 2008-10-26
i don't know what you mean by most of that.  i used this tutorial and created a user just like it said:
[http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/)

---

### Post by bodhi.zazen on 2008-10-26
Well, yes that allows people to view your svn directory in a web browser, but how are you uploading ? How are you using svn (snv co ...  ???).

Are you saying you do not understand "basic" Linux ownership and permissions ?

---

### Post by thepiston on 2008-10-27
My developer says he is using Eclipse and can get in, but cannot create folders.  I guess I don't know the basics of Linux file/folder ownership... link me?

---

### Post by bodhi.zazen on 2008-10-27
OK, no problem.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/FilePermissions[/uhelp]


FYI SVN is not "easy", I also suggest the "red book"

[http://blog.taragana.com/index.php/archive/5-minutes-guide-to-subversion/](http://blog.taragana.com/index.php/archive/5-minutes-guide-to-subversion/)

[http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

SVN takes a little time to digest, and I suggest you do a little reading, 30-60 minutes should do fine.

The subversion directory needs to be owned by svn and use a group of www-data

svn allows rw over subversion

svn co ....
svn ci  ...

www-data allows you to access it over htttp protocols

svn co [http://server/project](http://server/project)

You need to co and ci over the same protocol.

Unless you have only a single developer, I highly suggest you look at ssh. The ssh protocol allows you to track changes by user. The protocols are in the references I gave you as in the blog (If you follow my blog security is fairly tight on the server).

---

