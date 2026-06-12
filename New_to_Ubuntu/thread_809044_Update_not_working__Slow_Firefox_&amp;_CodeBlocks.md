---
title: "Update not working | Slow Firefox &amp; Code::Blocks"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by anothrguitarist on 2008-05-27
Since I installed hardy. I've been having problems updating. I receive the following error message when I check for updates: 

"Failed to fetch [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/Packages.gz](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Anyone know of a fix?


Additionally, programs such as Firefox and Code::Block run slowly, especially when scrolling. Anyone know of a solution?

---

### Post by Bubba64 on 2008-05-27
> **anothrguitarist said:**
> Since I installed hardy. I've been having problems updating. I receive the following error message when I check for updates: 

"Failed to fetch [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/Packages.gz](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Anyone know of a fix?


Additionally, programs such as Firefox and Code::Block run slowly, especially when scrolling. Anyone know of a solution?

Have you looked in software sources to see if this is in 3rd party stuff if it is tick it off make sure all the ones you want are on. If not there
it is in in      
sudo cat /etc/apt/sources.list   
paste this in terminal to open list and remove if you do not need it. the widgets url is not in my personal apt source this is an extra I believe. As far as Firefox running slow I am not sure what is going on.

---

