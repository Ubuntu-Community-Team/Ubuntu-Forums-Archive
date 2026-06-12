---
title: "Stalling during bootup"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Bakerbakura on 2012-03-20
Hi thar

So yesterday I was using Ubuntu as usual. The only changes I made to the system was updating four or five packages through the update manager, and changing my account from logging in automatically to requesting a password at startup. Today whenever I try to start up into Ubuntu after choosing it at the grub menu, after the Ubuntu logo with the flashing dots appear on the screen, the bootup just hangs with some lines like 
'Starting <insert service here> <skip to end of line>[OK]'.
If I press my power button my laptop then shuts down, but the same happens when I try to startup again. I'm using Oneiric Ocelot on a Lenovo G560.

---

### Post by Ms. Daisy on 2012-03-22
Can you get to recovery mode? 

Restart and hold the shift key down, that should bring up the grub boot menu where you can choose recovery mode.

[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordoneiricthumb01.jpg[/IMG]
edit- whoops! pic didn't work.

---

### Post by Bakerbakura on 2012-03-23
Hi

I can get to the GRUB menu and get into recovery mode, then log into root and all those lovely things, but I don't know how to fix my system while in recovery mode so that I can start up normally. Thanks for asking though.

---

### Post by Ms. Daisy on 2012-03-23
Give this a look, recovery mode has a "repair broken packages" option that sounds like just the thing you need:

[http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/](http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/)

---

### Post by Bakerbakura on 2012-03-24
Hey Miss Daisy

The problem is that my only Internet access is through a 3G modem, and I'm not sure how to connect with it via terminal. So I can't get an internet connection and download the needed packages. Maybe you know how to do this? Thanks for the help so far, though.

---

### Post by Ms. Daisy on 2012-03-24
Did the 3G modem work before Ubuntu broke?  If it did, then you can use 

```
nmcli con list
```

to find out the id of the configured connection.  Then use 

```
nmcli con up id <id> & 
```
or 
```
nmcli con up uuid <uuid> &
```

to turn the connection on & run it in the background.  Obviously <id> or <uuid> gets replaced by the id you found in the list.

I'm on windows and can't test this right now, so I can't swear it will work.  You can look at the man page for nmcli for more commands.  
[http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html)

---

### Post by Bakerbakura on 2012-03-26
Hi Miss Daisy

When I Enter 'nmcli con list', I get the following response: '(process 951): WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory.' When I navigate to /var/run and run 'ls', I see no dbus folder there.

---

### Post by Ms. Daisy on 2012-03-26
OK, sounds like you may not have the 3G modem configured.  See this for getting it to work via terminal:

[http://masdin.hubpages.com/hub/How-to-install-undetected-modem-Ubuntu](http://masdin.hubpages.com/hub/How-to-install-undetected-modem-Ubuntu)

But of course that only works if you've got wvdial already installed.  

Every tutorial/ repair I have found requires that you download packages to get the modem to work.  I don't know how to get you out of that Catch-22.  Hopefully someone else can offer some advice.

---

### Post by Bakerbakura on 2012-03-29
So the configuration of the modem did not work. So I opted to just reinstall Ubuntu without formatting the hard drive, so I still have my documents and things, though most of the programs I had installed now have to be redownloaded and installed. It's not too much of a hassle though. Thanks for trying to help, Miss Daisy.

---

