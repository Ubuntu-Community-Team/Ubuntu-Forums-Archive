---
title: "Keeping my Internet Connection alive"
date: 2005-01-04
forum: Programming Talk
---

### Post by Programmer on 2005-01-04
Hello :-)

As you know, I wrote a scripts that dials to my ISP and opened a PPTP tunnel to my cables company.
After running the script, i have 'ppp0' connection in my ifconfig, that contains my real ip address.

The problem is that sometimes this internet connection disappears  :confused:  only god knows why, and i need to run my script again to make it alive again.

How can i make this automatic ? I want that my linux will run the script for me every time my internet connection dies, without my interruption.
Note: My script need to be runned with root privileges.

Thanks, Alexander

---

### Post by jdong on 2005-01-04
You'd want it running as a daemon, sort of like an init script. Use an existing Init script as a reference: **/etc/init.d/cupsys** is a very clean one. 


Let's call it

/usr/local/bin/internetd

You'd also want a /etc/init.d/internetd, which is modeled off cupsys to start/stop internetd.

Your internet keepalive script should be an infinite loop with the following logic:

1. Check for internet access. Do so by pinging a well-known site, or by using regular expressions to parse ifconfig output. (Doesn't the first option sound SO much easier?)
    A: YES: Do nothing
    B: NO: Initiate an internet connection.
2. Sleep for x amount of time. Use the **sleep** or **usleep** command to do so. This is to prevent the script from going TOO quickly and slowing down the rest of your system! 1 second should be appropriate.

---

### Post by Programmer on 2005-01-07
Thanks :)

---

