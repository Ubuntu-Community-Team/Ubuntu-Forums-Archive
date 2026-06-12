---
title: "Running Script on Startup"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Quick99 on 2012-02-03
Hello, I am a Linux newbie and I have spent the last several hours trying to get the no-ip client application installed and working on my fresh install of Ubuntu. It works, and I can run the application and see that it is working. However, I want the application to start when the computer starts. (Before login)

I have placed the following .sh file in /etc/init.d/
> /usr/local/bin/noip2However, when I login I can run this command:
sudo /usr/local/bin/noip2 -S

And it tells me that there are no instances of noip2 running. I think the problem is that I have to use sudo to start noip2, otherwise it tells me:
> Can't locate configuration file /usr/local/etc/no-ip2.conf. (Try -c). Ending!And I know for a fact that file does exist. When I use sudo it does not complain at all and noip2 starts.

Being a total newbie, I am not really sure what to even look for next, so any help is much appreciated.

Thanks,
Grant

---

### Post by Rodney9 on 2012-02-03
[http://www.ubuntuka.com/autostart-ubuntu-startup/](http://www.ubuntuka.com/autostart-ubuntu-startup/)

---

### Post by Quick99 on 2012-02-03
That was actually the first thing I tried. For the command I put in:
/usr/local/bin/noip2

I also tried:
sudo /usr/local/bin/noip2

After restarting the program was not running. The second command starts the program when typed directly into the Terminal.

---

### Post by kevdog on 2012-02-03
Where did you get the noip2 program?? I'll try it on my end!

---

### Post by kevdog on 2012-02-03
Ok -- figured it out -- rebooted and you can see the process is running:

sudo ps -aux | grep noip
[sudo] password for kevdog: 
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
nobody    1724  0.0  0.0   2380   784 ?        Ss   00:57   0:00 /usr/local/bin/noip2
kevdog    2076  0.0  0.0   4448   796 pts/0    S+   00:57   0:00 grep --color=auto noip

What you need to do is edit (as root!!!) your /etc/rc.local file and put /usr/local/bin/noip2 
before the exit 0 line.  

That's it!! Done!!

---

