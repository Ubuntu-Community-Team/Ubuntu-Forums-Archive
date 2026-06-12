---
title: "Howto: Torchat - Anonymous P2P Chat"
date: 2008-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by mtron on 2008-03-16
This howto has been tested & written for ubuntu gutsy 7.10 (it is also reported to work on ubuntu hardy & debian unstable). It shows you how to configure the onion router [tor]("http://www.torproject.org/overview.html.en"), and install the P2P client [torchat]("http://code.google.com/p/torchat/").  this client is written in python and runs on windows & OSX  too! 

TorChat helps to protect you (and your chat partners) with the following features:   
[LIST]
[*]Nobody will be able to find out where you are.
[*]If sb. is already observing you and sniffing your internet connection they will not be able to find out:
[*] what you send or receive
[*] to whom you are sending or receiving from
[*] where your contacts are located
[/LIST]

**1. Install Tor & Privoxy**

```
sudo apt-get install tor privoxy
```**2. Configure Privoxy **

```
sudo gedit /etc/privoxy/config
```add this line at the end: (with the dot at the end)
```
forward-socks4a / localhost:9050 .
```Now go to Firefox addons and install this neat[ SwitchProxy Tool]("https://addons.mozilla.org/de/firefox/addon/125?application=firefox&id=125"). After a FireFox restart, go to Extra > Switch Proxy > manage proxies > add > standard > next.

enter the following information into both the HTTP Proxy and SSL Proxy fields. Hostname: 127.0.0.1 Port: 8118. 
use SocksV5 and port 9050 for socks
Set up any proxy exceptions you may need (localhost, 127.0.0.1 is a good idea) and then click on OK.(Do this also for the proxy label)

**3. Configure Tor:**

```
sudo gedit /etc/tor/torrc
```Find the following section and change it to:

> ############### This section is just for location-hidden services ###

## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

HiddenServiceDir [COLOR=Red]/var/lib/tor/hidden_service/[/COLOR]
HiddenServicePort [COLOR=Red]11009 127.0.0.1:11009[/COLOR]

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22now create the hidden tor dir & restart tor:
```
sudo mkdir /var/lib/tor/hidden_service/
sudo /etc/init.d/tor restart
```

**4. Install Torchat ** from Source
Now you can use firefox with tor. But we want chat, so get the [latest Torchat source]("http://code.google.com/p/torchat/") (at the time of writing this howto it was version 0.9.9.98 ) and unzip it under your home.

move source code:
(assuming the py files are unpacked in the folder /home/username/src)
```
sudo mkdir /usr/share/torchat
sudo mv ~/src/*  /usr/share/torchat/
```Create your "buddy-list.txt" file.
*Do this only for the initial install, later you want to move your existing buddy list to the /usr/share/torchat folder*

```
sudo echo "" > /usr/share/torchat/buddy-list.txt
sudo chown user:user /usr/share/torchat/buddy-list.txt
```replace  *user:user* from above with your username 

Install needed python-wx:
```
sudo apt-get install python-wxgtk2.8 python2.5
```create starter menu entry
```
sudo gedit /usr/share/applications/torchat.desktop
```paste into the editor window:
> [Desktop Entry]
Encoding=UTF-8
Name=torchat
Comment=anonymous chat client
Exec=python /usr/share/torchat/torchat.py
Icon=/usr/share/torchat/icons/torchat.ico
Terminal=0
Type=Application
Categories=Application;Internet;**5. get your user ID for torchat**:

```
sudo less /var/lib/tor/hidden_service/hostname
```this will display something like
> [COLOR=Green]defc7p5y3flzyjqy[/COLOR].onionthe green part is your id, tell this ID (without the .onion) your frinds to add you to their torchat.

**6. Tell Torchat your User ID:**

```
sudo gedit /usr/share/torchat/tc_client.py
```change OWN_HOSTNAME to yours, or it will NOT work!
> OWN_HOSTNAME = "[COLOR=Green]defc7p5y3flzyjqy[/COLOR]" #.onion ( <== change the 16 Quoted chars to your onion ID ... the green one from step 5)**7. Run Torchat:**

Now start torchat with the Start menu Icon or from a terminal:
```
python /usr/share/torchat/torchat.py
```You will see a window with your contact list. One of the contacts is labled "myself". This 16 numbers and letters are your unique address inside the Tor-Network. Wait a few minutes until the icon becomes green. Give this address to your friends so that they can add you to their list or add your friends address to your list. It all basically behaves like you would expect from an instant messenger.

The Author states that starting TorChat & logging in the tor network  can sometimes take up to 15 Minutes (it takes around 1 minute for me)

**The contents of the folder /var/lib/tor/hidden_service are your personal key. They must always be kept secret. If someone wants to impersonate your identity he must and will try to steal the contents of this folder from you.**

Keep this always in mind. It would be a good idea to use [TorChat]("http://code.google.com/p/torchat/") in conjunction with something like [TrueCrypt]("http://en.wikipedia.org/wiki/TrueCrypt"). To enable this, read on [here]("http://ubuntuforums.org/showpost.php?p=4559499&postcount=3")

**8.Removing TorChat**

```
sudo rm /usr/share/applications/torchat.desktop
sudo rm -R /usr/share/torchat/
```

If you also want to remove tor (uninstall the package with dpkg -r tor), don't forget to safely delete the tor hidden_service directory /var/lib/tor/hidden_service/  with e.g. the [shred tool]("http://linux.die.net/man/1/shred")

**9. Credits & License **

Permission is granted to copy, distribute and/or modify this document under the terms of the [GNU Free Documentation License]("http://www.gnu.org/licenses/fdl.txt"). So knock yourself out ;)

Bits & pieces for this howto were in true open source spirit shamelessly taken from:
- [HOWTO surf anonymous]("http://ubuntuforums.org/showthread.php?t=95527") by user dutch
- [Torchat]("http://code.google.com/p/torchat/"), written by prof7bit
- [Truecrypt FAQ]("http://www.truecrypt.org/faq.php")
- privoxy & tor manpages
- [Installing SwitchProxy for Tor]("https://www.torproject.org/docs/tor-switchproxy")

**10. changelog:**
- added buddy-list instructions (torchat doesn't start if file doesn't exist)
- updated torchat to 0.9.9.98 Now with anonymous filesharing support :)

---

### Post by bhavi on 2008-03-21
Thanks for the tutorial I was looking for configuring tor from days.....

---

### Post by mtron on 2008-03-21
I have decided to keep the truecrypt instructions seperate from the howto, because they got much more complex than i thought :(

I assume you followed the howto above and can use torchart already.

Get the latest truecrypt deb package from [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) and install it. 

Start truecrypt and choose the  "Create Volume" button. In the Wizard, set these values:

> Standard Volume
Volume Location: /home/username/.torchat/crypted.tc
Size 5 MB, AES encryption,
set your password.
filesystem:Fat

Now exit truecrypt and add the following line to /etc/fstab:
this will mount the directory where torchat expects it
```
/dev/mapper/truecrypt0 /var/lib/tor/hidden_service    fuse      users,noauto      0 0
```

apply changes to fstab:
```
sudo mount -a
```

create torchat starter script:
```
sudo gedit /usr/bin/torchat
```

paste into the editor window:

```
#! /bin/sh
# Torchat starter file

# enable the truecrypt hidden_service dir
# this will ask you for the truecrypt volume password and root password
truecrypt --mount /home/username/.torchat/crypted.tc /var/lib/tor/hidden_service

# start torchat
python /usr/share/torchat/torchat.py

# after torchat ends  disable truecrypt hidden_service dir
truecrypt --dismount /home/username/.torchat/crypted.tc
```

Don't forget to replace the "username" above with your username.

make executable:
```
sudo chmod +x /usr/bin/torchat
```

Change the torchat.desktop starter menu file:
```
sudo gedit /usr/share/applications/torchat.desktop
```

> [Desktop Entry]
Encoding=UTF-8
Name=torchat
Comment=anonymous chat client
Exec=/usr/bin/torchat
Icon=/usr/share/torchat/icons/torchat.ico
Terminal=0
Type=Application
Categories=Application;Internet; 

now temporarily mount the crypted new hidden_service file /home/username/.torchat/crypted.tc with the truecrypt gui to a location of your choice and copy the contents of the old hidden_serive dir to the new encrypted one:
(assuming you mounted the crypted.tc to ~/crypted)
```
sudo mv /var/lib/tor/hidden_service/* /home/username/crypted
```

Now we are done! Unmount all crypted Volumes in torchat aund close it. If you start torchat with just "torchat" from the terminal (or /usr/bin/torchat) the starter script will mount the Truecrypt volume (containing your secret key)  to  /var/lib/tor/hidden_service/.

After you close torchat, the script will unmount the hidden servic_dir again.

Hope you could follow everything. Good luck and have fun :)

---

### Post by mtron on 2008-03-21
> **bhavi said:**
> Thanks for the tutorial I was looking for configuring tor from days.....
 You're welcome! Did you experience any problems getting this to run? i did not receive much feedback yet ;)

---

### Post by mtron on 2008-04-01
i've taken out the warning, cause i'm done! :) 

Hopefully it will be useful to sb in future. Cheers, mtron

---

### Post by popeh on 2008-08-16
NM
I just installed from .deb package, and everything works fine now.

---

### Post by keb on 2009-12-22
**Please install Tor using the special Ubuntu packages from the Tor Project repository - they are guaranteed up to date and more likely to communicate properly with the Tor network.**  Or use the source packages.
If you come looking for help in irc.oftc.net #tor, the first thing people will tell you is to follow the instructions at 
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
to get Tor working and then read
[http://www.torproject.org/docs/tor-hidden-service.html.en](http://www.torproject.org/docs/tor-hidden-service.html.en)
about configuring hidden services.

---

### Post by t54 on 2009-12-26
Is Torchat still being developed? 

The author appears to have disappeared; his torchat address has been dead for about a year now and there is no sign of a new release of any kind for about a year now. 

Basically it is a great software but really needs to be updated to fix bugs and add improvements to realise its excellent potential. 

One of several problems is its failure in Linux to allow drag and drop of text into the chat window.  This is odd because, according to the author, Torchat was developed in Linux but the problem only exists in Linux and not in the Windows version.

---

### Post by clue1607 on 2010-09-14
> 6. Tell Torchat your User ID:
Code:
sudo gedit /usr/share/torchat/tc_client.py
change OWN_HOSTNAME to yours, or it will NOT work!I am using Squeeze and found your outstanding tutorial. But i am having difficulties with step 6:
I do find "OWN_HOSTNAME" in /usr/share/torchat/tc_client.py  **several** times. But nowhere an  "OWN_HOSTNAME =" like in ~/.torchat/torchat.ini. Therefore I wrote my hostname to ~/.torchat/torchat.ini.

When I start torchat I get turned green after few minutes. But no matter how long I let it run, nobody else seems to be online.

When I start torchat manually with /usr/bin/torchat I get some errors:

```
/usr/share/torchat/tc_client.py:30: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
./tor.sh: 5: tor: not found
(0) [tc_client,1562,startPortableTor] very strange: portable tor started but hostname could not be read
(0) [tc_client,1563,startPortableTor] will use section [tor] and not [tor_portable]
```Is there something wrong?

---

### Post by clue1607 on 2010-09-15
Solved:

I copied my own hostname to ~/.torchat/torchat.ini. No i get connected and it works.

---

