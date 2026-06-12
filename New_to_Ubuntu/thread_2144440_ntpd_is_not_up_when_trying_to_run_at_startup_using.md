---
title: "ntpd is not up when trying to run at startup using /etc/rc.local"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by sandeep913 on 2013-05-12
Hi ,
I am trying to run openNTPD during bootup by giving ntpd -s in /etc/rc.local but it doesn't seem to come up when system is booted up. I suspect root privilege problem as ntpd requires root privilege to run. Please guide me through this.
Thanks in advance.

---

### Post by SeijiSensei on 2013-05-12
You shouldn't need to do any of that if you just install ("sudo apt-get install ntp") and run ntpd from the repositories.  It will install a startup script in /etc/init.d/ and start automatically upon boot. 

By the way, /etc/rc.local is run with root privileges.

---

### Post by Lars Noodén on 2013-05-12
If you installed OpenNTPd from the repository, then it should be already up and running automatically.  There should be no need to put anything in /etc/rc.local  There is no upstart script (yet) so there is a SystemV script in /etc/init.d/

```

/etc/init.d/openntpd status

```

You can also look manually to see if it is running.

```

pgrep -lf ntpd

```

---

### Post by dodo3773 on 2013-05-12
I've had similar problems in the past. Both with the ntp daemon and with startup. The solution for me was like this:
```

 sleep 30 && /usr/bin/ntpd -qg

```

I use ntp though and not openntpd so the -qg switches may not be the same for you I'm not sure. Try sleeping it for a little bit though and see if that helps.

---

### Post by sandeep913 on 2013-05-13
> **SeijiSensei said:**
> You shouldn't need to do any of that if you just install ("sudo apt-get install ntp") and run ntpd from the repositories.  It will install a startup script in /etc/init.d/ and start automatically upon boot. 

By the way, /etc/rc.local is run with root privileges.


I can't use repository for ntp installation, i need to install it manually.:(

---

### Post by sandeep913 on 2013-05-13
> **dodo3773 said:**
> I've had similar problems in the past. Both with the ntp daemon and with startup. The solution for me was like this:
```

 sleep 30 && /usr/bin/ntpd -qg

```

I use ntp though and not openntpd so the -qg switches may not be the same for you I'm not sure. Try sleeping it for a little bit though and see if that helps.


Thanks for your reply. I tried your solution but it didn't work for me. I tried giving large value for sleep also but no effect.

I gave this in rc.local

sleep 3000 && ntpd -s

Please tell me if i need to try something else.

---

### Post by dodo3773 on 2013-05-13
> **sandeep913 said:**
> Thanks for your reply. I tried your solution but it didn't work for me. I tried giving large value for sleep also but no effect.

I gave this in rc.local

sleep 3000 && ntpd -s

Please tell me if i need to try something else.

I doubt you would need more than 30 seconds in your sleep script. Does running "sudo ntpd -s" set the correct time as it is now if you run it in a shell?

Edit: Also, the comment above meant the repository already in Ubuntu. Not from any external additional repo. If you cannot access the repositories because you have no internet than you wouldn't be able to set the correct time to begin with. "sudo apt-get update && sudo apt-get install ntp" in a terminal as stated previously is probably want you want to do. It sounds to me like you may be a little lost here. You may also want to try the stuff on the wiki: [https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP](https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP)

---

### Post by sandeep913 on 2013-05-13
> **dodo3773 said:**
> I doubt you would need more than 30 seconds in your sleep script. Does running "sudo ntpd -s" set the correct time as it is now if you run it in a shell?

Thanks for your quick reply. sudo requires the password, which i can't give in startup script , and user id and password is also not fixed for all the systems(I need to run it on different systems.).

---

### Post by dodo3773 on 2013-05-13
> **sandeep913 said:**
> Thanks for your quick reply. sudo requires the password, which i can't give in startup script , and user id and password is also not fixed for all the systems(I need to run it on different systems.).

I was saying that to see if it worked as it is now. Also, I edited my previous post with more information.

---

### Post by sandeep913 on 2013-05-13
> **dodo3773 said:**
> I doubt you would need more than 30 seconds in your sleep script. Does running "sudo ntpd -s" set the correct time as it is now if you run it in a shell?

Edit: Also, the comment above meant the repository already in Ubuntu. Not from any external additional repo. If you cannot access the repositories because you have no internet than you wouldn't be able to set the correct time to begin with. "sudo apt-get update && sudo apt-get install ntp" in a terminal as stated previously is probably want you want to do. It sounds to me like you may be a little lost here. You may also want to try the stuff on the wiki: [https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP](https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP)

As far as i know sudo apt-get install ntp will install the latest version of ntp. I need to install a specific version of openNTPD. that's why i can't use repository. Correct me if i am wrong.

---

### Post by sandeep913 on 2013-05-13
> **dodo3773 said:**
> I was saying that to see if it worked as it is now. Also, I edited my previous post with more information.

Yes it worked with [COLOR=#000000]"sudo ntpd -s".[/COLOR]

---

### Post by dodo3773 on 2013-05-13
I don't have enough experience with openntpd to be of a whole lot of additional assistance besides pointing you to documentation to read. If the command "[COLOR=#8A8A8A]*sudo ntpd -s*[/COLOR]" works to set the correct time in the terminal than the rc.local command should work. If not try out the included init script and if that doesn't work I am not sure what to tell you.

---

### Post by Lars Noodén on 2013-05-13
> **sandeep913 said:**
> As far as i know sudo apt-get install ntp will install the latest version of ntp. I need to install a specific version of openNTPD. that's why i can't use repository. Correct me if i am wrong.

You can use [APT pinning](https://help.ubuntu.com/community/PinningHowto) to make the repository serve you a particular version of OpenNTPd but treat all the other packages normally.  It's not that hard to set up and it does give you all the advantages of maintaining the package through the repository even if it is a different version of the package.

Also keep in mind that **ntp** and [OpenNTPd](http://packages.ubuntu.com/raring/openntpd) are two different packages.  So when you use *apt-get* make sure you are choosing the right one.  The posts above have referred to both, which may lend to confusion.

**ntp** is installed by default, if I understand correctly, so for openntpd to work from a manual installation you will have to uninstall ntp manually.

---

### Post by sandeep913 on 2013-05-13
> **Lars Noodén said:**
> You can use [APT pinning]("https://help.ubuntu.com/community/PinningHowto") to make the repository serve you a particular version of OpenNTPd but treat all the other packages normally.  It's not that hard to set up and it does give you all the advantages of maintaining the package through the repository even if it is a different version of the package.

Also keep in mind that **ntp** and [OpenNTPd]("http://packages.ubuntu.com/raring/openntpd") are two different packages.  So when you use *apt-get* make sure you are choosing the right one.  The posts above have referred to both, which may lend to confusion.

**ntp** is installed by default, if I understand correctly, so for openntpd to work from a manual installation you will have to uninstall ntp manually.

Thanks. I will try out this and will let you know.

---

### Post by SeijiSensei on 2013-05-13
A quick search of the repositories shows there is an **openntpd** package with [these files](http://packages.ubuntu.com/raring/amd64/openntpd/filelist).  The four that matter to you most are probably:
```

/etc/default/openntpd
/etc/init.d/openntpd
/etc/network/if-up.d/openntpd
/etc/openntpd/ntpd.conf

```
The second of these should be the script to start the daemon.  

Try activating the service by running the command "sudo chkconfig openntpd on".  That should force it to start up at boot.  If that doesn't happen, take a look at the symlink for openntpd that should have been created by chkconfig in /etc/rc2.d.  It should begin with "S" and a two-digit number that determines the order in which scripts are executed.  For instance, the symlink pointing to the startup script for the apache2 web server is called "S91apache2".  The 91 means it runs near the end of startup sequence.  The final entries begin with "S99" including the one that starts rc.local.  If, by mistake, openntpd has a prefix smaller than the one assigned to networking, just move openntpd later in the sequence.  (Obviously I'm assuming this is a server where the network is started from /etc/network/interfaces not the graphical NetworkManager.) 

Just curious, but are you using [OpenNTPD]("http://www.openntpd.org/") because of its BSD license?

---

### Post by sandeep913 on 2013-05-14
> **SeijiSensei said:**
> A quick search of the repositories shows there is an **openntpd** package with [these files]("http://packages.ubuntu.com/raring/amd64/openntpd/filelist").  The four that matter to you most are probably:
```

/etc/default/openntpd
/etc/init.d/openntpd
/etc/network/if-up.d/openntpd
/etc/openntpd/ntpd.conf

```
The second of these should be the script to start the daemon.  

Try activating the service by running the command "sudo chkconfig openntpd on".  That should force it to start up at boot.  If that doesn't happen, take a look at the symlink for openntpd that should have been created by chkconfig in /etc/rc2.d.  It should begin with "S" and a two-digit number that determines the order in which scripts are executed.  For instance, the symlink pointing to the startup script for the apache2 web server is called "S91apache2".  The 91 means it runs near the end of startup sequence.  The final entries begin with "S99" including the one that starts rc.local.  If, by mistake, openntpd has a prefix smaller than the one assigned to networking, just move openntpd later in the sequence.  (Obviously I'm assuming this is a server where the network is started from /etc/network/interfaces not the graphical NetworkManager.) 

Just curious, but are you using [OpenNTPD]("http://www.openntpd.org/") because of its BSD license?

Thanks for the the explanation. I didn't know about "chkconfig". what i did is i executed this openntpd script in rc.local so it is coming on boot up. but i will try this also.
Yes i am using openntpd because of its BSD license.
Can you tell me where openntpd logs go. I checked /var/log/syslog and /var/log/messages also but it is not there.

Thanks

---

### Post by SeijiSensei on 2013-05-14
If I doesn't log to /var/log/syslog, I can't help.  I use the standard ntpd daemon myself.

---

