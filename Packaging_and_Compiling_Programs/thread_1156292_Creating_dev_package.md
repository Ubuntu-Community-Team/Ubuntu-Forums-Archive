---
title: "Creating dev package"
date: 2009-05-11
forum: Packaging and Compiling Programs
---

### Post by arich57 on 2009-05-11
Hey all,
  I'm new to all this so I'll apologize in advance. I am trying to create a package that will install some software and grab all the packages that I need to do development on  machine. Right now, it works in finding the dependencies and telling me that are not there but the the install ends. I have to run "apt-get install -f" to get it to install all the dependencies.

Is there a way to make it so it will automatic install the depends that are missing so I don't have to do "apt-get install -f" ? 

Thanks.

Update: solved it. use gdebi insteead of dpkg
-Aaron

---

