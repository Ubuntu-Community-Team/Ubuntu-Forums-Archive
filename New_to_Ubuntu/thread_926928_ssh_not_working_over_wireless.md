---
title: "ssh not working over wireless"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by shivkrish22 on 2008-09-22
Hi 
I have ubuntu 8.04 installed on my vostro 1500 laptop. ssh does not work over the wireless connection. However if i connect through the wired connection it works for the same server. i found this bug report in launchpad: [https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816) 

Is there any workaround for this right now? or do i have to wait till the next update?

---

### Post by Peter09 on 2008-09-22
try ssh -v <command>. This is verbose mode and will provide more information on what is going on. I have it working over a wireless connection as standard.

---

### Post by shivkrish22 on 2008-09-22
<username>@<server's> password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8


thats the last few lines of the output when i use the -v option. it seems that authentication works, but does not proceed after that. any ideas?

---

### Post by Peter09 on 2008-09-22
Its funny, because there is someone else on the forum with basically the same problem

here:
[http://ubuntuforums.org/showthread.php?t=909599](http://ubuntuforums.org/showthread.php?t=909599)

not sure why this is happening, I have had no problems. What have the two of you in common?

---

### Post by shivkrish22 on 2008-09-22
i read the other thread and it does seem to be the same problem. I also found the bug report in the link i have put up in the first post. I was wondering if someone could look up the bug report at launchpad and confirm if there is a fix or not, simply because i am not sure how launchpad works and how to locate the proper fix if any. the bug report can be found here:  
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816)

the output pasted in the comment here: [https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816/comments/6](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816/comments/6)  is exactly what i get.

Maybe its a bug with Dell laptops? because the person in the other thread as well as the person reporting the bug in launchpad have it installed on a Dell, same as mine.

Thanks

---

### Post by Peter09 on 2008-09-22
This LaunchPad Bug suggests this as a fix. (Although some say it does not work)

> 

The workaround for this in Intrepid (don't know if it will work for hardy) is to first see if you have the ioctls:

root@moltar:/home/pgraner# iwpriv
lo no private ioctls.

eth0 no private ioctls.

eth1 Available private ioctls :
          set_leddc (8BE0) : set 1 int & get 0
          set_vlanmode (8BE1) : set 1 int & get 0
          set_pm (8BE2) : set 1 int & get 0

then actually set it:

pgraner@moltar:~$ sudo iwpriv eth1 set_vlanmode 0

Note this has to be done as root.


---

### Post by shivkrish22 on 2008-09-22
> shivkrish@shivkrish-laptop:~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

wlan0     no private ioctls.

thats the output of iwpriv. Im not sure how to proceed further.

---

### Post by willca on 2008-09-23
Hi 

Just wondering if you try this way and see how it goes or what it tells.

disable wired nic / ifdown eth0 or eth1?
then verify your wifi is running and you can connect to places (surf or ping or something).
then try to ssh locally / ssh -v localhost

If that goes well, then try it now remotely.

---

### Post by Eduardo Mercovich on 2008-09-24
> **shivkrish22 said:**
> i read the other thread and it does seem to be the same problem. [...] the bug report can be found here:  
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816)

Hello shivkrish22, hello Peter09. 

Yes, we have the same case ([http://ubuntuforums.org/showthread.php?t=909599](http://ubuntuforums.org/showthread.php?t=909599)). Just connect via cable and it works. 
The ioctl proposal in launchpad didn't worked for me neither. 

In the meantime (if a cable connection is cumbersome, like in my case), Putty works ok.

And again, my public thanks to Peter09 for his tireless help.  :-)

Best regards...

--
EM

---

### Post by shivkrish22 on 2008-09-24
i tried putty and it seems to work. so i guess i will have to manage with putty till this bug gets sorted out. i also use a program called NxClient to access the GUI and even that doesnt seem to work over wireless. So putty seems to be the solution for now. 
Thanks for all the help.

---

### Post by Peter09 on 2008-09-24
I believe Nx uses ssh as a basis for comms, so it does not surprise me that it does not work.

---

### Post by blackvd on 2008-10-27
I'm having the same problem on my Compaq Presario CQ50-115NR using wi-fi under Hardy. Able to connect via putty and filezilla sftp. 

Here's the bottom of my output with ssh -v

```
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
```

just hangs at Sending env LANG...

Is there a fix for this yet?

---

### Post by shivkrish22 on 2008-10-27
I think this problem is fixed in the latest kernel update "2.6.24-21-generic" as I am able to use ssh now.

---

### Post by blackvd on 2008-10-28
> **shivkrish22 said:**
> I think this problem is fixed in the latest kernel update "2.6.24-21-generic" as I am able to use ssh now.

According to my boot screen I'm using 2.6.24-19 how do I upgrade?

---

### Post by blackvd on 2008-10-29
Upgraded to Ibex and edited my menu.lst to add 2.6.27-7 and now it works great!

---

### Post by porkradish on 2009-03-24
I just want to add that my Dell mini 9 and me have been struggling with this for weeks until I found this.  T really appreciate the help and just wanted to say thanks.

---

