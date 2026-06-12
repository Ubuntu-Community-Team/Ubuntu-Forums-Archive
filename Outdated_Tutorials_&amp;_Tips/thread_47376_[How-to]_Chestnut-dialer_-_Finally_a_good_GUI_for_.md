---
title: "[How-to] Chestnut-dialer - Finally a good GUI for Gnome"
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by ralf57 on 2005-07-08
I've recently discovered this cool Pyton application at gnomefiles.org
I suddenly felt in love with it since it's really clean and easy to use.
This little tutorial refers to 0.2.2 version,the latest available.

1)Download the application from here:
[http://sourceforge.net/projects/chestnut-dialer/](http://sourceforge.net/projects/chestnut-dialer/) 

2)Install it following these steps:
- Uncompress the package
- cd into the created directory (chestnut-dialer-0.2.2)
- type:
```

./configure
make
sudo make install

```
Note: if you have 'checkinstall' installed in your system you can type
```
sudo make checkinstall
```
This will install the program and also build a .deb package for future usage.
Furthermore the application will be available via APT/Synaptic.
If you have troubles see README file for detailed instructions.

3)First run.
Type:
```
chestnut-dialer -i gtk2
```
The main panel will appear;now you can configure Options,the Default Account settings
and add your custom account(s).
At this point you should be ready to browse the net.

################
Troubleshooting
################

You might experience troubles
connecting to the net and receive errors like these:
```
EAP: unauthenticated peer name "foo-as5850-001" 
PAP authentication succeeded
EAP: too many Requests sent
Connection terminated.
```

Don't worry.
Type:
```
sudo gedit /etc/ppp/options
```
find
```
auth
```
and replace with
```
noauth
```

then in 
chestnut-dialer >> confaccount >> your_account >> PPP tab
make sure 'Add default route' is checked
and add 'noipdefault' (without quotes)
to PPP Options

Everything should be ok now.

###########################
Docking to systray
###########################
One of the few missing features at the
moment is the option to dock the program
to the notification area after a connection has
been established.
Btw,i've found a simple workaround to this.

1) Download the 'alltray' application from
[http://alltray.sourceforge.net/downloads.html](http://alltray.sourceforge.net/downloads.html)
Be sure to get the last version.

2) Install it to your system.

3) Go to
System >> Preferences >> Sessions >> Boot-up programs
Add a new command
```
alltray chestnut-dialer
```

The next time you load Gnome desktop a nice icon will
appear in the notification area ready to connect your box to the net.

Enjoy!

*** ralf57 ***

---

### Post by arnieboy on 2005-07-08
I didn't know about alltray! turns out its the application I was looking for!! thanks a lot dude!!
apps like thunderbird were begging for an app like this

---

### Post by snarkout on 2005-09-11
Thank you!  This is very useful.

---

### Post by ralf57 on 2005-09-11
[QUOTE=snarkout]Thank you!  This is very useful.[/QUOTE]
 Glad to know it is.

---

### Post by Izzin on 2006-11-15
Chestnut Dialer is actually my preferred dialer for when I use the new Sprint PCS cards. However I recently installed Edgy and for some reason I am unable to get Chestnut to function.

When I go to execute the program it just hangs, no debug out put, nothing. I am able to execute chestnut-dialer --help, and it pulls up help, and able to do chestnut-dialer --list-ui and get the ui listing. However I can not go further then that.

If anyone has any debug assistance it would be greatly appreciated.

-I

---

### Post by frank56economicsman on 2009-08-23
I used chestnut-dialer in vectorlinux and liked it. I used dh-make to build my package for a debian installation. I got it to dial from terminal but in my case did not know what step to take to get gtk2 front end to initiate or start. I also am getting this error on termimal:

franksdebiannetwork:/home/frank# chestnut-dialer 
/usr/share/chestnut-dialer/chestnut_dialer/connection.py:190: RuntimeWarning: tempnam is a potential security risk to your program 
  file_name = os.tempnam() 

I was guessing so I tried converting rpm gtk and got this error message:

Errors were encountered while processing: 
 chestnut-dialer-gtk2_0.3.3-2all.deb 
franksdebiannetwork:/home/frank/Desktop# dpkg -i chestnut-dialer-gtk2_0.3.3-2_all.deb 
Selecting previously deselected package chestnut-dialer-gtk2. 
(Reading database ... 94997 files and directories currently installed.) 
Unpacking chestnut-dialer-gtk2 (from chestnut-dialer-gtk2_0.3.3-2_all.deb) ... 
dpkg: error processing chestnut-dialer-gtk2_0.3.3-2_all.deb (--install): 
 trying to overwrite `/usr/share/chestnut-dialer/chestnut_dialer/gtk2_ui/box.pyo', which is also in package chestnut-dialer 
Errors were encountered while processing: 
 chestnut-dialer-gtk2_0.3.3-2_all.deb 
franksdebiannetwork:/home/frank/Desktop# 

I read the README files and did ./configure then make, then make install, everything seem to progress without errors but, it did not give me a chestnut dialer on Desktop

Frank

---

