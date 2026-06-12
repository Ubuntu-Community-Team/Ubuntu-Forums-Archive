---
title: "Patching Nautilus 3.6 in Ubuntu 12.10"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by HesusGC on 2012-12-25
Hello there. This is my first Ubuntu week and it has been great!. 
However I recently updated Nautilus 3.4 to 3.6 because I wanted to use gnome instead of Unity and a bug appeared. Searched for it and found the patch at this URL.

Nautilus Patch
[http://git.gnome.org/browse/nautilus/patch/?id=6cde4c5a6d639c85df09b8992a307f91d6b056a6](http://git.gnome.org/browse/nautilus/patch/?id=6cde4c5a6d639c85df09b8992a307f91d6b056a6)

So now I have this patch text that I don't know how to use. I don't know to handle it as a .deb or what to do with this. 
Could you please help. Thanks :)

---

### Post by mc4man on 2012-12-26
You would need to get the nautilus 3.6 source, patch, build & install.

If you are using the gnome3 ppa then the next quantal build will be patched for this, -  "git_launcher_no_frame.patch: "don't add a thumbnail 
    border around desktop file launchers" (lp: #1085320)"

If  you wish to patch & build yourself instead it's pretty simple, just post the results of this command so I can see what nautilus you have.

```
apt-cache policy nautilus
```

---

### Post by HesusGC on 2012-12-26
Hi there. Thanks a lot for your support. I did what you instructed me, and this is what I get:

apt-cache policy nautilus

```

nautilus:
  Installed: 1:3.6.3-0ubuntu2~ubuntu12.10.1
  Candidate: 1:3.6.3-0ubuntu2~ubuntu12.10.1
  Version table:
 *** 1:3.6.3-0ubuntu2~ubuntu12.10.1 0
        100 /var/lib/dpkg/status
     1:3.5.90.really.3.4.2-0ubuntu4 0
        500 http://mx.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
```

---

### Post by mc4man on 2012-12-27
So you're using the gnome3 ppa. 
If you wish I'll post up a copy & paste on building a patched nautilus using the ppa nautilus source. If so please open software-sources & make sure that the "Source Code" box is fully checked as in screen
Then run sudo apt-get update & let me know.

Otherwise it's really a minor bug & as mentioned the next time the ppa updates it's nautilus build it will include the fix, you could just wait it out.

---

### Post by HesusGC on 2012-12-27
yeah I think is a really minor bug and I only use 3 icons on my desktop so No problem. I think I'll wait for the patched ppa. 

However it would be great if you could just do a brief description of what's the process  to patch the source code. Maybe it will be useful later. 
Awesome, Thanks.

---

### Post by meteorrock on 2013-01-22
So how is this coming along? I got white squares all around my icons here on the desktop using a gnome 3 shell. Using ubuntu 12.10. 64 bit. 

How do you go about applying the .patch from the git_launcher_no_frame.patch.gz ?

Never applied patches before, noticed a google search is showing a cd into directory and a make and make install using patch -p1 or patch -p0 ? I just got confused.

I know how to cd into the file path, but does this patch go into the /usr/bin/ or can I apply it just in the ~home directory? 

Thanks. I want to help debug too. 

~~~~~~~~~~~~``

If anyone is lurking this thread, I think nautilus can be rolled back with this .deb at this site here. Make sure to select the correct file in there for your computers specs. This is only for the older ubuntu builds. [https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/)

---

