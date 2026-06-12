---
title: "Xen / Ubuntu Install does not have internet access"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by JamesGist on 2008-08-28
I am brand new to Ubuntu and brand new to Xen so I might need a little guidance getting around the basic Linux tools.  

Here's my issue.

I installed Ubuntu on a Dell Dimension 9200.  The install seems to be fine.  I am definitely able to run firefox and browse the web. I used the instructions here:

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

to install Xen.  I got through page 1 fine but when I tried to install a domU I got an error.  I think it's because I don't have internet access.  Here is the error:
> 
E: Failed getting release file [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)...

I have been searching for a few hours but haven't come up with anything.  I think one solution said to execute 

```
xend restart
```

When I did, here is what I got.

> ifdown: interface peth0 not configured.  

When I restart and boot into my original Ubuntu install I can search the internet fine.  

Any thoughts?  or is there anymore info I can provide?

James

---

### Post by JamesGist on 2008-08-29
I think I've discovered the network problem.  I was connected to the onboard ethernet port.  I installed another NIC card and my Xen installation sees to be able to surf the web just fine.

---

