---
title: "Internet filter"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by bayon on 2013-03-06
Hello, I am new to Ubuntu/Linux.
I need an internet content filter, that filters url by keyword in url, and that blocks a list of http[SIZE=2]**s**[/SIZE] sites. 

I will make the first configuration of the filter myself and I will use the filter myself. But the password of the filter, will enter my sister, so that i cant turn off the filter whenever i want. (So- i do not fit the filtering methods, which are based on configuration, which are not protected by password or by administrator privilages.)

I tried to install NxFilter and DansGuardian+Privoxy, but seeing how complicated is to install and configure them, i wondered - will I be able to get all the necessary results. 

So - is there a solution for my conditions for whichever of the Linux distributions?

---

### Post by Mr. Shannon on 2013-03-06
Will you have sudo (admin) rights on the computer, if so there is no solution for locking down the filter.  Otherwise this link [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/) has a fairly simple tutorial.  He uses iptables but gives all the commands so it shouldn't be to hard to follow.

---

### Post by bayon on 2013-03-06
I can ask my sister to set the admin password, which will be known only by her. Will that help to lock down the filter?

---

### Post by SeijiSensei on 2013-03-06
What you want to do is pretty complex.  

First, your best choice for a filter is [Squid]("http://www.squid-cache.org/").  You can write all sorts of rules that allow or deny connections to remote sites based on IP, domain name, or text in the URL.

HTTPS is a whole other ball game.  Putting a filter between clients and remote sites using SSL will generate repeated complaints by the client's browser that you are being subjected to a "man-in-the-middle" attack since the filter will disrupt the encrypted transaction between the browser and the server.  Squid 3.2 has some clever solutions for this problem, but they are not easy to implement.  If you're curious, do a search for "SSLBump".

At one client site where I manage filtering we use iptables firewalling rules to block remote HTTPS sites.  That's not an easy task, either.  Many sites with heavy traffic loads have multiple servers listening on multiple IP addresses.  You'd need to identify all the possible server addresses for each site, then write iptables rules like this:

```
/sbin/iptables -A OUTPUT -d 173.252.110.27 -p tcp --dport 443 -j REJECT
```

This blocks HTTPS connections to one of Facebook's servers.

I would not suggest any of this for newbie Linux users.  I cannot figure out from your request whom you're trying to filter, but a better method would be enforcing good behavior.

---

### Post by jinhee200 on 2013-03-06
Hi bayon,

This is Jinhee the developer of NxFilter.

I thought I made it very easy to install NxFilter.
But you said that you have some difficulties in using it.
Can you tell me on what part you have the problem?

If you are not familiar with Linux environment then you can try windows version of NxFilter.
There's a Windows installer for people not familiar with Linux.
And you can make it Windows service as well.

The setup process is pretty easy.
Just click the exe file and you get several icons.
One for starting NxFilter one for web-admin.
You need to have Java 1.6 or higher installed first.

After you start NxFilter then click the icon to web-admin.
Then you get the login prompt in your browser.
And the initial password for admin is 'admin'.

You can have authentication with IP or password.
And you also can integrate it into Active Directory.
Of course you can block https sites as well.
Maybe some other applications as long as they use DNS.

If you have difficulties in client setup then I recommend you
to read something about DHCP and DNS setup.
I think in your home-router you can set NxFilter as your DNS easily.

If you can't install it still then send me an email.
I can help you.

Jinhee

---

### Post by bayon on 2013-03-06
I cant start NxFilter.
i do not understand how to do this: "You can start NxFilter as a daemon use '-d' option for 'startup.sh'."

and are you trying to say that i can use 'nxfilter.exe' for installation on Ubuntu?

---

### Post by jinhee200 on 2013-03-06
No. I was telling you that if you are not familiar with Linux you can use Windows.
Because it's a lot easier.

If you were able to start NxFilter on your Linux that's OK.
And about the '-d' option.
It's there because some people want to run it on background mode.
Like this.

/nxfilter/bin/startup.sh -d

You can use that option in rc.local script to start it with system booting.
Coz that'd be better than starting it manually on your console.

---

### Post by jinhee200 on 2013-03-06
Sorry.
You couldn't start it.

Then try to run this command.

/nxfilter/bin/startup.sh

Did you install it into /nxfilter directory?
You need to give execute permission to the scripts in /nxfilter/bin directory as well.

Try this commad.

ls -la /nxfilter/bin

If there's no execute permission.

chmod +x /nxfilter/bin/*.sh

And go to /nxfilter/bin

cd /nxfilter/bin
sudo startup.sh

There should be some message.
At least some error message.

And trying it on Windows would be a good idea before you move into Linux.
When it comes to management Linux is better but it might be difficult for most of people if they don't have
enough knowledge of Linux.

---

### Post by bayon on 2013-03-07
I installed nxfilter to /home/rihards/nxfilter.
in folder 'bin' in all 4 'sh' files i changed 'NX_HOME=/nxfilter' to 'NX_HOME=/home/rihards/nxfilter'
then i did 'chmod +x /home/rihards/nxfilter/bin/*.sh'
then: '/home/rihards/nxfilter/bin/startup.sh: 11: /home/rihards/nxfilter/bin/startup.sh: java: not found'
and it didnt create any database into '/home/rihards/nxfilter/db'.
then i tried to go 'http://92.49.14.166/admin', but it does not work.

---

### Post by Cheesemill on 2013-03-07
> then: '/home/rihards/nxfilter/bin/startup.sh: 11: /home/rihards/nxfilter/bin/startup.sh: [COLOR=#ff0000]java: not found[/COLOR]'
Do you have Java installed on your system?

---

### Post by jinhee200 on 2013-03-07
Yeah. You need to install Java.
Try this.

  whereis java

In my case.

jinhee@ubuntu:~$ whereis java
java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
jinhee@ubuntu:~$

Or if you didn't install it.

  sudo apt-get install openjdk-7-jre

---

### Post by bayon on 2013-03-08
yes, i installed java and i got this step done, but to do the next step is hard either.

ahh.. its not worth it, i am trying to set up filter for 2 or 3 days and i am not done. i will stay to XP and to my Blue Coat K9 which does exacly everything i need.

Thanks for help, everyone!

---

### Post by jinhee200 on 2013-03-08
Sorry to hear that.
Next time if there's anyone not able to install NxFilter send me an email.

support at nxfilter.org

I can help you.

---

