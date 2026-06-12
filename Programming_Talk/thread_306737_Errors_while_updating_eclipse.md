---
title: "Errors while updating eclipse"
date: 2006-11-25
forum: Programming Talk
---

### Post by domo876 on 2006-11-25
Hello,

I am new to ubuntu and linux. I have set up Ubuntu Edgy Eft and installed the lates eclipse 3.2.1 packages. I brought up eclipse and then tried to updates using the "Software Updates" feature of Eclipse. I keep getting errors about Eclipse being unable to create directories in /usr/lib/eclipse/features.....

What do I do? My user id belongs to the same group as root which is the owner and the group wx permissions are set for the eclipse and features directories.

Any help is appreciated.

---

### Post by shining on 2006-11-25
Why are you doing this?
Either install the eclipse providen by ubuntu, and let synaptic / apt-get manage the updates for you,
or install eclipse locally / manually (by downloading the tar.gz from eclipse site and untarring it somewhere), and then update it if you really need to.

---

### Post by JimTDI on 2006-11-25
I found it better to download Eclipse manually, and extract it to my home directory - and then run the Updates from within Eclipse itself.  But I'm on Dapper, and there is no Eclipse 3.2.1 package available from the Ubuntu repositories.

---

### Post by domo876 on 2006-11-26
> **shining said:**
> Why are you doing this?
Either install the eclipse providen by ubuntu, and let synaptic / apt-get manage the updates for you,
or install eclipse locally / manually (by downloading the tar.gz from eclipse site and untarring it somewhere), and then update it if you really need to.

I needed to install some plugins not available through apt-get. I guess I will have to do what you suggest. 

Thanks.

---

### Post by shining on 2006-11-27
> **domo876 said:**
> I needed to install some plugins not available through apt-get. I guess I will have to do what you suggest. 

Thanks.

I don't understand. Are you trying to install some plugins, or to update eclipse? That's two totally different things :)
The deb package are installed in /usr/lib/eclipse , and you've no write permission there.
However, nothing prevents you from installing additional plugins, which will be installed in ~/.eclipse/
I've both the deb eclipse package and eclipse manually installed, and both work as well with an additional plugin.
But the first has to be updated using apt-get, the second via eclipse.

---

### Post by lloyd mcclendon on 2006-11-29
HI

i am going to make your day, well anybody that uses eclipse actually.  forget debain packages, what a bunch of BS that is.


i found this the other day and had to fight an erection off.  

[http://yoxos.com/ondemand/](http://yoxos.com/ondemand/)


this is the best thing that has ever happened to me since i found eclipse.  take a look at some of the popular scenarios, i'm using the java web all in one + testNG (seems to be gone now actually :-| )

when you start up it updates automatically & the yoxos perspective is just wonderful when you need a plugin.  no more hunting for jar files, copying them in and hoping they work.  no more of the help > software updates > paste in a url and hope for the best crap either.  i am thrilled i think i'm actually gonna pay for it when my subscription runs out instead of just making a fake one every 3 months.

---

