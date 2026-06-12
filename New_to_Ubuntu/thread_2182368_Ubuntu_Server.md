---
title: "Ubuntu Server"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by thatotherdude24 on 2013-10-21
I grew up using Microsoft products and all of my IT experience has been on Microsoft stuff so I have a general idea what all you can do with the server side of things. I'm curious what you can do with ubuntu on the server side of things in a home environment as well as a business. 

I do have a separate question as well. With active directory on MS stuff you can login with a username and password and user profiles are stored on the server and so on. Using ubuntu server and ubuntu desktop is there a way to setup an active directory type thing where somebody has a username and password and somebody could login to any computer running ubuntu and all their saved stuff is on the server?

---

### Post by newb85 on 2013-10-21
I don't really have experience with Ubuntu server edition, but what you've described in your second question can be achieved (I believe) by simply replacing the folders on the non-server machines in the User's /home directory with symlinks to corresponding folders on the server.

---

### Post by btindie on 2013-10-21
> **thatotherdude24 said:**
> I do have a separate question as well. With active directory on MS stuff you can login with a username and password and user profiles are stored on the server and so on. Using ubuntu server and ubuntu desktop is there a way to setup an active directory type thing where somebody has a username and password and somebody could login to any computer running ubuntu and all their saved stuff is on the server?

The simplest way to do that is by using NIS+NFS [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) you can replace NIS for authentication with LDAP which allows you to authenticate against an AD backend. But NIS is a lot more straightforward to configure.

---

