---
title: "Update problem"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by mdjasim on 2012-09-30
Hi Ubuntu User
I am a new ubuntu user. When i first install ubuntu it seems good to work. But recently when i run the command to the terminal *sudo apt-get update *it shows some error which is

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

what can i do for this error?
How can i solve this error?

---

### Post by Wim Sturkenboom on 2012-09-30
Try again ;) It can be a temporary glitch somewhere.

The first two do work when I follow them. However the 3rd one goes wrong after 'dists'. [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/) is empty. I don't know the reason for this.

---

### Post by 2F4U on 2012-09-30
If you open the URL by hand, as I just did, you will notice that you get a 404, so the web site does not exist. The most likely reason is that the person who created the ppa simply has stopped supporting it, since if you look around on the site you will notice that they are pretty empty.

---

### Post by T.J. on 2012-09-30
It's possible the PPA archive mentioned is either offline temporarily or has been closed.  The error appears because it cannot fetch new index files from the PPA for a merge.  It's best to disable the PPA, at least for the time being. There are different methods to do this, depending on how the PPA was added to your index files. Do you know or remember how it was added?

If not, try searching in /etc/apt/sources.list and then commenting the line with the PPA out with a # before running another update.

---

