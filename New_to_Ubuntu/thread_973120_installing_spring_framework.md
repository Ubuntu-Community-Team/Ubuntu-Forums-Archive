---
title: "installing spring framework"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by ninjapawikan on 2008-11-06
Im new to ubuntu. and i have just installed ubuntu 8.10 in my netbook. right now im having a great time using it.
Anyways, here's my concern, recently i have a new project requiring me to develop with spring framework. And id like to use ubuntu as my development platform. how do i setup spring framework in ubuntu?

my current status:
i have already installed java6, thanks to this little instruction i googled.
[http://www.cyberciti.biz/faq/ubuntu-linux-install-eclipse-java-ide/]("http://www.cyberciti.biz/faq/ubuntu-linux-install-eclipse-java-ide/")

im planning to use eclipse for my ide, but still thinking if my netbook(eee pc 1000H) could hold up to the resources needed.

thanks,
ninjapawikan

---

### Post by jamesstansell on 2008-11-06
Hi,

You might be interested in the springide package, but there don't seem to be any springframework packages in the repositories.  So installing it won't really be ubuntu-specific.  The spring project should have instructions, or perhaps your project lead will?  If you try to follow instructions that assume windows the main thing is to translate the directory paths.  And if some part of the instruction happens to say to extract something directly into the eclipse directory you probably don't want to do that, since you've installed eclipse from the repository package.

Regards,

-james.

---

