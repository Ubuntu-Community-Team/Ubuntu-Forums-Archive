---
title: "Getting started with svn on a remote server?"
date: 2008-06-15
forum: Programming Talk
---

### Post by moephan on 2008-06-15
Hello,

I am having trouble finding reliable information on this on the web. Perhaps someone could point me in the right direction?

I have an account with a hosting company to host my web sites. I can ssh into the server, and they have svn already installed. I was able to create a repository on the server using svnadmin.

Now I would like to use that repository from my laptops and such. However, I can find a reference that shows how to use svn on a remote server. I would like to be able to import/checkout/checkin, etc... without logging onto the server.

Hope that makes sense. Obviously, I'm a bit of a beginner with this. TIA.

Cheers, Rick

---

### Post by johnl on 2008-06-15
If you don't have a repository already set up, you'll need to ssh into your server and use svnadmin to create one. 
(There shouldn't be any additional setup to do on the server side, I think this type of connection is allowed by default)

From there you can access your repo like this (on the client side):

```

# checkout
svn co svn+ssh://user@your.server.net/path/to/repo

```


Once you check out, svn update, svn commit, etc will all work as expected over ssh connection.  It may ask for your password two/three times when intially checking out, and once when updating/commiting, etc.  If you don't want that, you can set up key authentication for ssh.


Hope this helps!

---

### Post by moephan on 2008-06-15
Thank you. With that information I was able to effectively search my hoster's help system and get it setup.

---

