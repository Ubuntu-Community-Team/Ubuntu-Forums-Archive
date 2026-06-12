---
title: "HOWTO: An easy way to configure your new Ubuntu 6.06 installation"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by mk1970 on 2006-06-02
**Ubuntu for desktops and laptops**

Do you want have an easy way to configure your new Ubuntu (6.06 or 6.10) installation? Do you need some multimedia codecs but you don't know what needs to be installed to get those videos working? This is what I have done with several Ubuntu PCs:

1. Install Ubuntu according to your preferences
2. Open a terminal (Applications > Accessories > Terminal)
3. Fetch my Ubuntu configuration script and execute it
4. Reboot

```

wget [http://www.iki.fi/kuparine/comp/ubuntu/en/install.sh]("http://www.iki.fi/kuparine/comp/ubuntu/en/install.sh")
sh install.sh

```

Details can be found at [http://www.iki.fi/kuparine/comp/ubuntu/en/install.html](http://www.iki.fi/kuparine/comp/ubuntu/en/install.html). This document also describes [how I configured RAID-1]("http://www.iki.fi/kuparine/comp/ubuntu/en/raid.html") for everything during installation to protect me against disk failures.

[COLOR="Red"]**Please note that you can now also upgrade an older version (e.g. upgrade from 6.06 to 6.10) by using the -u command line option.**[/COLOR]

**Ubuntu Server with VMware Server**

Do you want to run [VMware Server]("http://www.vmware.com/products/server/") on your new Ubuntu server? Are you too lazy to manually install VMware Server and all the required packages?
See [My Ubuntu Server Installation with VMware Server]("http://www.iki.fi/kuparine/comp/ubuntu/en/server.html") which describes how you can install Ubuntu Server with VMware Server.

1. Install Ubuntu Server from the Server Installation CD or use the Alternate Install CD and select "Install server" from the boot menu
2. Fetch the VMware Server and VMware Management Interface .tar.gz files and a license key from [VMware]("http://www.vmware.com/products/server/") and save them to your desktop computer
3. Fetch my [Ubuntu Server configuration script]("http://www.iki.fi/kuparine/comp/ubuntu/en/server.sh") (server.sh) to your desktop computer
4. Copy the above files to the newly installed server
5. Execute server.sh
6. Reboot

```

scp pc:Desktop/VMware-server-1.0.0-28343.tar.gz .
scp pc:Desktop/VMware-mui-1.0.0-28343.tar.gz .
scp pc:Desktop/server.sh .
sh server.sh

```

Details can be found at [http://www.iki.fi/kuparine/comp/ubuntu/en/server.html](http://www.iki.fi/kuparine/comp/ubuntu/en/server.html).

Comments and improvements are welcome!

---

### Post by SqRt7744 on 2006-06-02
looks nice, I'm glad you remembered ssh.

---

### Post by raublekick on 2006-06-02
awesome, i might try this out later. glad someone came up with something nice and easy like this for dapper really fast. i see some --force-yes's in there though...

---

### Post by mk1970 on 2006-06-02
[QUOTE=raublekick]i see some --force-yes's in there though...[/QUOTE]
The reason for these few instances is because the PLF signatures can't be verified (and this gives a warning).

PS. Does anyone know where to get the public keys so all packages retrieved from PLF can be authenticated? I'd like to get rid of those --force-yes switches...

---

### Post by Jose Catre-Vandis on 2006-06-02
Nice try, but your script tells me that I don't have dapper installed, even though I have just installed dapper 6.06 LTS having downloaded yesterday ! Its a good list of apps to install though  :-)

---

### Post by mk1970 on 2006-06-02
[QUOTE=Jose Catre-Vandis]Nice try, but your script tells me that I don't have dapper installed, even though I have just installed dapper 6.06 LTS having downloaded yesterday ! Its a good list of apps to install though  :-)[/QUOTE]

This means the version detection was not working correctly. I think I have fixed this now, please fetch the updated version and try again. If it still refuses to run, you can always use the -u switch...

---

### Post by Jose Catre-Vandis on 2006-06-03
I did a bit of copy and paste and created  my own "interactive" (lazy/simple/whatever) script, which worked pretty well. Thanks mk1970.

---

### Post by lukew on 2006-06-09
[QUOTE=mk1970]The reason for these few instances is because the PLF signatures can't be verified (and this gives a warning).

PS. Does anyone know where to get the public keys so all packages retrieved from PLF can be authenticated? I'd like to get rid of those --force-yes switches...[/QUOTE]
Hi,

I have been asking the same question and it seems that no one knows!

Any one??? - Someone must surely know!!!

Luke

---

### Post by SqRt7744 on 2006-06-12
[QUOTE=lukew]Hi,

I have been asking the same question and it seems that no one knows!

Any one??? - Someone must surely know!!!

Luke[/QUOTE]

yes, as a matter of fact I do  :)

to get the keys, use this page:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by johnfarrow on 2006-06-15
Installed the script after new drapper install and now have no audio.  Maybe one of the codecs?
Is there a way to uninstall the script?

---

### Post by johnfarrow on 2006-06-15
Previous post should have read no AUDIO.  Sorry bout that

---

### Post by SqRt7744 on 2006-06-15
[QUOTE=johnfarrow]Installed the script after new drapper install and now have no audio.  Maybe one of the codecs?
Is there a way to uninstall the script?[/QUOTE]

Are you sure the audio was running before using this script?

---

### Post by cleako on 2006-06-15
cool stuff, glad that installed wine so I dont have to do that :)

---

### Post by johnfarrow on 2006-06-15
Yes the audio was working before as I listened to Mandella.  I liked the easy way it installed java and all the others, but I really need the audio for Skype.

---

### Post by mk1970 on 2006-06-16
[QUOTE=johnfarrow]Yes the audio was working before as I listened to Mandella.  I liked the easy way it installed java and all the others, but I really need the audio for Skype.[/QUOTE]

So no audio in Skype? You can always uninstall the DSP hijacker and see if that helps:

```
sudo dpkg -P skype-dsp-hijacker
```

---

### Post by johnfarrow on 2006-06-16
Its not only Skype,  its no Audio whatsoever.  However I will try your suggestion and let you know it helps.  Thanks:)

---

### Post by johnfarrow on 2006-06-16
When I paste
sudo dpkg -P skype-dsp-hijacker,  into terminal, it asks for password.  When I try to enter password, nothing appears on the screen.  I type but nothing appears.

Any suggestions?

---

### Post by mk1970 on 2006-06-16
Are you sure you have skype and the DSP hijacker installed?

```
# dpkg -l | grep skype
ii  skype                      1.2.0.18-1  Free Internet Telephony - The whole world ca
ii  skype-dsp-hijacker         0.6-0ubuntu0seveas2  This tool lets you use skype with /dev/dsp1
```

Here's an example from my PC:

```
# sudo dpkg -P skype-dsp-hijacker
Password:
(Reading database ... 102439 files and directories currently installed.)
Removing skype-dsp-hijacker ...
Removing `local diversion of /usr/bin/skype to /usr/bin/skype.bin'
```

---

### Post by johnfarrow on 2006-06-16
As you can probably tell, I am a complete linux newbie.  Can I simply reinstall the original script?
Thanks for trying to help

---

### Post by mk1970 on 2006-06-17
[QUOTE=johnfarrow]Can I simply reinstall the original script?
[/QUOTE]

Yes, you can run it multiple times.

---

### Post by Guns90 on 2006-06-17
Disregard this.  I forgot I was in a sticky/how to.  I reposted in the General section.  Sorry.

---

### Post by Guns90 on 2006-06-17
I'm posting this in here so that you know that I had a problem with the flash plugin that locked up my terminal and no one could unlock it.  The same thing happened to a gentleman named DotBot.  You can see what took place here: [http://www.ubuntuforums.org/showthread.php?t=198446](http://www.ubuntuforums.org/showthread.php?t=198446)

---

### Post by johnfarrow on 2006-06-17
I now have the sound back after rerunning the script.  The Skype is still screwed up and I guess I will have to use the windows versions for that.
Thanks again for the help

---

### Post by mk1970 on 2006-06-18
[QUOTE=johnfarrow]The Skype is still screwed up[/QUOTE]
Have you tried with and without the DSP hijacker? First try with the hijacker installed and make a test call. If it fails, remove the hijacker with dpkg -P and make the test call again. Any difference?

---

### Post by mk1970 on 2006-07-26
I added instructions how to install VMware Server with a script. See the first post for details...

---

### Post by mk1970 on 2006-10-02
I added support for Ubuntu 6.10 and the possibility to upgrade an existing 6.06 to 6.10. The upgrade is activated with the -u command line option.

---

