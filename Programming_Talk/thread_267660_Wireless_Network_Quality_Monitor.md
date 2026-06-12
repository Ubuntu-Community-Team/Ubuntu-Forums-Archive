---
title: "Wireless Network Quality Monitor"
date: 2006-09-28
forum: Programming Talk
---

### Post by Ryan Marcus on 2006-09-28
After switching from Mac OS X to Ubuntu, I'm finding several things that are missing, for one, the level of signal of your wireless connection in the menu bar.

I looked at a few programs, such as gnome-network-manager, and decided it was better to write my own.

So I did. I took the few Java skills I had learned in class (yes, I'm in high school. Go ahead and attack me.) and attempted to make a well formed application.

This application is attached, and it compiled and ran correctly for me in Eclispe.

I'd like you to ask you guys a couple questions. First, I run the command "iwconfig eth0" to get the information I need... From my very basic understanding of UNIX, that "eth0" could change. Is there a way to get the name of all the active wireless interfaces that are connected to a network so I can make this work on computers other then mine?

Also, I'm fairly new to Java, so any constructive code comments you could give me would be great. I'm here to learn.

Lastly, I was wondering if there was a way that I could make my Java application show up in the notification area when you connect to a wireless network. Then, when you click on its icon, to display the JFrame (or JPanel.)

Thanks in advance for any help. Also, I apoligize for any dumb typos in this post. I'm typing without a spellchecker late at night. You know how it is.

---

### Post by moephan on 2006-09-29
To get a list of wireless network interfaces, try:
```

sudo iwlist sanning

```

HTH

Cheers, Rick

---

### Post by Ryan Marcus on 2006-09-29
You mean:
> 
sudo iwlist scanner


How would I use a sudo command from java? I added the term "sudo" to the command argument list, but it did not open the prompt I am used to seeing when a password is needed.

---

### Post by amo-ej1 on 2006-09-29
And what's wrong with simply opening /proc/net/wireless ?

```

edb@lapedb:~$ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 19  
eth1: 0000   84.  -46.  -87.       0      0      0      0      0        3

```

Open the file from your java application and simply get the signal level (-46 dBm in this case) and the noise level (-87 dBm in this case).

et voila ;-)

the value befor it (84) is the signal quality (on a 0-100 scale).

---

### Post by amo-ej1 on 2006-09-29
oh yeah and /proc/net/wireless give you a list of all attached wireless devices on your system so you can get the device name from there too.

---

### Post by Ryan Marcus on 2006-09-29
Hm, that is an interesting way of doing things as well, but it does not give me the list of all the wireless networks found, like sudo iwlist scanner does.

I'll rewrite the application to use the cat command, that should at least allow the application to work on more then just my computer.

How would I go about making a Java application use a sudo command, just so I can know in the feature?

Also, are there any Java classes I can use for implementing my application into the notification area, or other cool Java classes I can use to implemt it into the system?

EDIT:
I managed to get it working using the cat command. Thanks. I also feel a little dumb about asking the question about intergrating my application with GNOME, seeing how a google search for java gnome gave me quite a bit of information.

I would still like to know how to run sudo commands with Java.

---

### Post by moephan on 2006-09-29
Here are a few ideas....

1. You might also consider using iwconfig instead of iwlist. iwconfig may not require sudo to work. (BTW, if you run iwlist scanning without sudo it will appear to work, but it really only returns the results from the last time it was run as sudo).

2. If you want to run iwlist, you an use
```

sudo -p *password* iwlist scanning

```
but you will have to prompt the user for their password. I'm not sure how good that is.

3. GTK has a command called gksudo that will prompt the user for the password, perhaps there is something similar in the UI library you are using.

Cheers, Rick

---

### Post by Ryan Marcus on 2006-09-30
gksudo is exactly what I was looking for! Thanks!

---

