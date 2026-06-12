---
title: "Creating .deb to install in prefix other then /usr ?"
date: 2010-01-25
forum: Packaging and Compiling Programs
---

### Post by LinuxCindy on 2010-01-25
Hi guys. Hoping you can help me out.

I am sorry for asking this question, as it seems to me like it should be so simple. But, I can't find the answer on Google, the forums, anything. So frustrating!

I have been tasked with creating a number of .deb package for internal use in my company. The thing is, I need it to install all files under a location other then /usr. We have a /companyname we use as a custom path across all our servers that I need to use. (/companyname/bin /companyname/sbin /companyname/lib etc)

I have been reading on on to create .debs and have been able to do it, and it works just fine for the standard process. I have tried to edit the Makefiles of the source files to use --prefix and --DESTDIR, and the same thing with the debian/rules but its not working for me.

I guess I am not asking anyone to wipe after me here, but I would love some sort of direction on how to approach this.

Helps!
Thanks Much!
Cindy

---

### Post by SevenMachines on 2010-01-26
hi there. the way to do this probably depends on exactly how you've packaged the source. if your using dh_install in debian/rules then you could try creating a <packagename>.install file to tell debhelper where to install the various files. you should also not edit the source directly if you can avoid it, you can set configure/make options in the rules file.
obviously as its a company thing i can understand that you may not be able to upload the actual package as an example but if if you can attach or give a link to as much of your packaging as possible it'll be easier to see if anythings going wrong. good luck!

---

