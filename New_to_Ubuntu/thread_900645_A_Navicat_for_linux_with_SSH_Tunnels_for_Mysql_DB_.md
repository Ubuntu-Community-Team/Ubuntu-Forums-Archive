---
title: "A Navicat for linux with SSH Tunnels for Mysql DB Management"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by graben3 on 2008-08-25
Hello everybody,

I was wondering if there is a software to manage my MySQL database that supports SSH tunnels like Navicat 8 does ?

Currently I have the Mysql Administrator & Query Browser installed but the SSH tunnels are handled with gSTM. Its really annoying to have to manually start the SSH tunnel in gSTM to connect to the remote DB each time. Navicat makes this really much more productive.

I know I can buy navicat in the end (there is a version for linux which is in fact a windows version embedded with Wine...) but I was wondering if there is some equivalent that is free ?

If you know any software for ubuntu that does SSH tunnels & Mysql Management, I would like try it !

---

### Post by gmoney on 2008-08-29
Hey Graben,

Are you familiar with phpmyadmin?  It's excellent for managing mysql databases.  I'm not sure if it handles SSH tunneling by default, but here's a couple of web pages that may give you some ideas on using phpmyadmin in conjunction with SSH.  

[http://jan.saell.org/blog/archives/42](http://jan.saell.org/blog/archives/42)

[http://macosx.com/forums/howto-faqs/48824-howto-use-phpmyadmin-through-ssh-tunnel.html](http://macosx.com/forums/howto-faqs/48824-howto-use-phpmyadmin-through-ssh-tunnel.html)

I'm not real familiar with gSTM, so forgive me if the above articles are just doing the same thing that gSTM does.  Two caveats on the latter page:  it was written with OSX in mind (hence the domain name), and it's from 2002, so it might be a bit outdated.  But I figured I'd share it anyway, because you might find it helpful.

In regards to Navicat, you may be able to snag a free (legal) copy, depending on your circumstances.  Personally, I was able to download the Linux version of Navicat for free when I signed up with my current web hosting company.  Also, it's interesting to learn that the Linux version is just the Windows version running in Wine.  I always wondered why Navicat looked so jankey on my box.  Now I know why.

Anyway, I hope those articles are helpful to you.

---

### Post by graben3 on 2008-09-08
Ya, I know PHPMyAdmin,

Unfortunately, PHPMyAdmin is a browser based tool and not exactly what I need. 

Its kind of annoying to work with PHP my Admin because when backuping data on/from a server that has some timeout for PHP scripts or too small upload / POST max size parameters, I have to chunk my SQL file to import it...

---

### Post by graben3 on 2008-09-09
Anyone ? advices ??? Help ?

I did not find anything yet... im sure there is something for ubuntu... there is always a solution under ubuntu...

By the way if anyone plans to go 64bits ubuntu, Navicat for linux wont work. Its kind of pre-embedded with a wine version that only runs on 32bits... damn... it gives me a 'segmentation fault' message everytime and on 32 bits ubuntu it was working fine.

There is currently no 64bits navicat for linux and they say on their website that there probably wont ever be one

---

### Post by hotrod205 on 2009-02-25
FWIW, I'm running Navicat just fine in 64-bit Ubuntu 8.10.  But I'm using Kubuntu, not sure if KDE runs it better than Gnome.  Also, I downloaded Navicat directly from the vendor, not sure if it is in the repositories or not.  

That said, I'm new to Navicat and can't get it to connect to my Ubuntu 8.10 LAMP server on my local LAN, but I've tried Navicat on an XP and Vista box also and cannot connect there either so my problem appears to be that my LAMP box is not setup for outside connections. If I can't figure it out I'll post that problem elsewhere.

---

### Post by llamabr on 2009-02-25
Also, it strikes me that this is not quite an absolute beginner question.  You may have better luck moving to the appropriate forum, which will be filled with experts in that area.

---

### Post by albandy on 2009-02-25
ssh user@remotemachine -L 3306:remotemachine:3306

Now you've imported the mysql port (3306) to your local machine.

Now you can use any linux mysql client to connect to your localhost:3306

---

