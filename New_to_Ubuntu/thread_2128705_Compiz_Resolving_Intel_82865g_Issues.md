---
title: "Compiz: Resolving Intel 82865g Issues"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by hefficide on 2013-03-24
Hello and please forgive me if this is either common knowledge or repetitive. I have spent months trying to find a resolution to issues with Ubuntu ( 12.04, 12.10, and 13.04 ) and my GPU ( Intel 82865g ), scouring every search engine available - all to no avail. Yesterday I got lucky and figured it out. I am posting this in hopes that others with this issue might find this thread quicky and easily and not have to go through the extreme learning curve that I wound up enduring.

Thanks.

If you are having problems with Compiz and have an Intel GPU in the same family as the 865g all you need to do in order to get the 3D working is to add the following to your Startup applications:

Name: Compiz
Command: compiz --replace
Comment: Start Compiz

After countless tries - that included installing Xorg Swat, Xorg edgers, the new Intel Graphics Drivers installer, and many more failed attempts... the above, simple command resolved all of my issues instantly. Now my Compiz is working perfectly, rendering 3D effects, and letting me get all that Ubuntu has to offer! I hope this will help anyone else who is trying to find a resolution to their problems.

Thanks ( Moderators, if I have chosen the incorrect forum, please move this to a better home )
~Hefficide

---

