---
title: "[SOLVED] NIS Services fails to bind to YP Server"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-06-15
My brother just upgraded from 7.10 to 8.04 Ubuntu. When he boots the screen is blank for a very long time. Pressing Ctrl-Alt-F1 shows that it gets stuck at
> 
*Starting NIS Services
*Binding to YP Server
*....
*....
*....
*....
*....
*....
*....
*....
*....
*....     [fail]
This happened to me when I upgraded also but I just did a clean install after and it works fine.:)

After it finally boots everything works fine as far as I can tell. What is NIS and YP Server?

Also for some reason when on the screen from pressing Ctrl-Alt-F1 the text is WAY to big and a lot of the screen is not shown although sometimes it is fine.

Thanks for the help,
Justin

---

### Post by RealPSL on 2008-06-15
Unless your NIS server is responding this problem will continue to happen. However, judging from the text of your message I do not believe you have an NIS server to connect to. We need to disable that service from attempting to start and bind to the server so we can get rid of the delay. You can install sysv-rc-conf with ```
apt-get install sysv-rc-conf
``` and then use it to disable the yp service.

More information about NIS can be found here:

[http://https://help.ubuntu.com/community/SettingUpNISHowTo?highlight=(NIS)]("http://https://help.ubuntu.com/community/SettingUpNISHowTo?highlight=(NIS)")

---

### Post by cariboo on 2008-06-15
Ctrl-Alt-F1 into a console and type the following:

```
/etc/init.d/portmap stop
/etc/init.d/nis stop

```

Then once you are up and running you can permanently stop the service in System-->Administration-->Services click unlock, enter your password and then uncheck **nis**

JIm

---

### Post by Commander_Bob on 2008-06-15
I just did
sudo apt-get remove nis
My computer does not have it installed so I figured it would not matter if I uninstalled his. Now it boots fine.
Thanks,
Justin

---

### Post by Russel_Winder on 2009-04-01
The problem is of course for those of us who want to run NIS.  For this person removing NIS solves the problem, for those of us who want to run NIS we need a proper solution to the problem -- which still exists.

---

### Post by odanawt on 2009-04-01
> **RealPSL said:**
> Unless your NIS server is responding this problem will continue to happen. However, judging from the text of your message I do not believe you have an NIS server to connect to. We need to disable that service from attempting to start and bind to the server so we can get rid of the delay. You can install sysv-rc-conf with ```
apt-get install sysv-rc-conf
``` and then use it to disable the yp service.

More information about NIS can be found here:

[http://https://help.ubuntu.com/community/SettingUpNISHowTo?highlight=(NIS)]("http://https://help.ubuntu.com/community/SettingUpNISHowTo?highlight=(NIS)")

Looks like that link is dead.  Here is an active one that is very informative.

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nis.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nis.html)

Hope that it helps the inquisitive ones.

---

### Post by Russel_Winder on 2009-04-01
Thanks for posting that, but it is not going to be helpful in this situation.  The problem here isn't the NIS set up, that used to work, and is unchanged and so should still work.  The problem here is changes to the Ubuntu boot sequence (I think from Gutsy to Hardy, but . . . ).  Trawling the Web seems to indicate the issue is related to Network Manager and possibly HALD and the order of start in the init.  I guess I need to play with reordering things to see if waiting NIS binding to after Network Manager and HALD start fixes things.

---

### Post by Russel_Winder on 2009-04-03
It seems that setting the start priority to ensure NIS starts after Network Manager cures the problem.  By default NIS has priority 18 and Network Manager has priority 28.  By changing NIS to have priority 30 (i.e. anythiong greater than 28) there is no delay in binding to the YP server.

So if the Ubuntu (and Debian?) people would just change the default then it really would be problem solved.

---

### Post by Russel_Winder on 2009-04-03
I have created Bug 354588 on Launchpad for this.

[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/354588](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/354588)

---

### Post by Russel_Winder on 2009-04-04
See also thread 915161 ([http://ubuntuforums.org/showthread.php?t=915161](http://ubuntuforums.org/showthread.php?t=915161))

As noted on the error report, this change of number has the effect of speeding up booting massively, but doesn't actually fix the binding failure. NIS services start up takes a while but succeeds, binding to the server still goes through its 11 attempts then fails but now does it very quickly because of the different state of the network adapter as Network Manager has started.

For various reasons, 29 rather than 30 is being progressed as the start number for NIS.

---

### Post by ashu2188 on 2011-07-02
Your problem got solved by removing NIS.. Startup number just boots up NIS binding to ypserver faster. But the problem with the users who wants to use NIS still remains... any solutions please?

---

