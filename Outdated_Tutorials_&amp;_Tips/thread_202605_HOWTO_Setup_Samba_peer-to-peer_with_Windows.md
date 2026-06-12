---
title: "HOWTO: Setup Samba peer-to-peer with Windows"
date: 2006-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormbringer on 2006-06-23
**HOWTO: Setup Samba peer-to-peer with Windows**

As many fellow Ubuntu users seem to have trouble setting up samba peer-to-peer with Windows I decided to write a small howto on this matter.

NOTE: I am aware that there's a wiki-page as well as several other howto's around - but by looking at the constant "how do I setup samba" posts that are floating around in the forum I simply see the need for a more thourough guide on this matter.

Feel free to contribute and suggest - it'll only help to make this howto a better guide.

The goal of this howto is to have samba act like a Windows Workstation in the LAN. As a "value added bonus" we will use samba to do netbios name resolution so that you can use the names of the workstations for network drive mapping instead of their ip-addresses (i.e.: \MY_WINDOWS_BOX\SHARE) - but only for as long as your Linux box has an static ip-address and is up and running.

This guide is based on Ubuntu 6.06 LTS and intended for all architectures (i386, AMD64, ...) - if you are still using Breezy it's safe to follow this guide as there should be no differencies.

A second guide on how to setup samba as Primary Domain Controller along with several other services such as DHCP, DNS and NTP will follow later on as this topic will be a little more thourough.


**1. Prerequisites**

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

- You need to have samba installed.
If you haven't done so already open a terminal and type:

```

sudo apt-get install samba

```

Don't close the terminal upon installation - we still need the commandline to get several tasks done!


**2. Getting samba configured**

First, let us make sure samba isn't running:

```

sudo /etc/init.d/samba stop

```

As a starting point I included an smb.conf below, and there are only a few simple things you may need to tweak.

Since the installation of samba just installed a rather useless template file we're going to rename it - we keep the file just in case.

```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.template

```

Next we create a new empty file

```

sudo touch /etc/samba/smb.conf

```

And finally we need to open the file inside an editor

```

sudo gedit /etc/samba/smb.conf

```
*NOTE: If you're on KDE replace "gedit" with "kate"*

Copy / Paste the contents of the code-section below into your editor and read on ...

```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

```

Ok, I already mentioned that there are a few simple things you may need to tweak; so here they are:

-> netbios name = YOUR_HOSTNAME

Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best pratice would be to use the same name you configured upon installation.

Example:

netbios name = DAPPER

-> workgroup = YOUR_WORKGROUP

Replace "YOUR_WORKGROUP" with the name of your workgroup, but make sure you're using the same as configured in Windows.

To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

Example:

workgroup = MSHOME

-> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.

-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

```

sudo mkdir /home/samba

```

... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:

```

sudo chmod 0777 /media/samba

```
*NOTE: Don't forget to correct the path to the location you chose above!*

That's it - now we need to start samba ...


**1.1 Starting samba and setting up user accounts**

Let us fire up samba for the first time. Type:

```

sudo /etc/init.d/samba start

```

There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

Time to add yourself as an samba user.

*NOTE: You will be asked for a password - make sure you use the same as you use for login!*

```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

*NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!*

In the following example we will add an user called "mark" ...

Example:

```

sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark

```

The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


**2. Changing network settings in Windows**

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
*NOTE: Adjust this to the hostname and sharename you chose above!*
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
*NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.*
- Click "Finish"

That's it - samba is up and running now.


**3. Security consideration**

This is the right time to think about security right away.

In case your computer has more than one network connection (i.e. wired and wireless ethernet) you may want to restrict access to samba.

If not especially configured samba will bind its service to all available network interfaces.

So, let us assume you only want your wired network to have access and that the network card is called eth0.

Add the following lines to the [general] section of your smb.conf to achieve that goal:

```

interfaces = lo, eth0
bind interfaces only = true

```

If you did it correctly it should look similar to this:

```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

```

Now only the local loopback interface (dubbed "lo") and eth0 are able to access samba - there's no need to fear that someone might break into your system by wireless as the interface isn't bound to the service.


**4. Final words**

If you happen to have any questions feel free to ask - I'll try to help as soon as possible.

If you find any mistakes in this howto please let me know so that I can fix them.

Feel free to contribute and suggest - help to make this howto a better guide.


**5. Addendum: Useful links**

Here are some links you may find useful.

The onsite links refer to other samba-guides and to ubuntu_daemon's "Important Links" thread.

- Onsite
[Ubuntu Help: Windows Networkworking]("https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html")
[Ubuntu Documentation: Setting up Samba]("https://help.ubuntu.com/community/SettingUpSamba")

[READ THIS FIRST prior to posting - IMPORTANT links]("http://www.ubuntuforums.org/showthread.php?t=232059") (by ubuntu_daemon)


The offsite links refer to the offical Samba homepage and to a selected choice of their official documentation; these links are useful if you like to dig yourself into the mysteries of samba's configuration and usage as well as troubleshooting problems.

- Offsite
[Samba Homepage]("http://samba.org/")

[Practical Exercises in Successful Samba Deployment]("http://us3.samba.org/samba/docs/man/Samba-Guide/")
[The Official Samba-3 HOWTO and Reference Guide]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
[Using Samba, 2nd Edition]("http://us3.samba.org/samba/docs/using_samba/toc.html")

---

### Post by user1397 on 2006-06-24
stormbringer, wonderful guide you have created, I have a few questions though.  

you say that you will make this guide more thorough later to include DHCP with samba.  is that going to happen any time soon or have you not planned it yet?

also, please look at my attachment, it's a drawing of the way my network is physically setup.  i just want to know if my network is safe.  i use my windows desktop's shared folder as my backup folder, the folder where i backup all of my ubuntu stuff on it.  my smb.conf is as generic as it can be, and i don't have a shared folder on my ubuntu desktop because i can browse, save, write to, and delete files on my windows desktop's shared folder.  it never asks me for a password or anything on ubuntu.  i just go to places, network servers, and go into my windows desktop's shared folder.   

is it me, or does that just not sound safe at all?!

---

### Post by Stormbringer on 2006-06-24
[QUOTE="erik1397"]you say that you will make this guide more thorough later to include DHCP with samba. is that going to happen any time soon or have you not planned it yet?[/QUOTE]

Well - this HOWTO was a piece of cake as it aims at simple home usage. but ...

The "second part" of the guide (I guess I'll call it "HOWTO: Setup Samba as an PDC with additional services") is planned, in the early stage of becoming, but won't happen soon (read: within a couple of a few days) as it's even more complex to write.

The aim will be professional usage of Ubuntu/Samba in Office-, School- or Corporate environments (as a replacement for Windows Servers) - therefore I will need to include basic guides on how to configure DHCP, DNS and NTP to play nice altogether.

If you like to proof-read or contribute the one or another idea I'll PM you the "development draft" as it gets complete.

[QUOTE="erik1397"]also, please look at my attachment, it's a drawing of the way my network is physically setup. i just want to know if my network is safe.[/QUOTE]

By looking at the drawing it looks good ... but ...

In case you have neighbors within the reach of your wireless router I hope you at least enabled encryption (WEP, 128-Bit minimum) so that no one can abuse your internet connection or exploit your data.

[QUOTE="erik1397"]I can browse, save, write to, and delete files on my windows desktop's shared folder. it never asks me for a password or anything[/QUOTE]

Do you need to enter a password upon bootup of Windows?

If you need to enter a password to log into Windows then Ubuntu has saved your password in the keyring - you must not enter it anew upon connect to the shared folder.

If Windows (XP?) doesn't ask you for a password you better set one right away (START -> Control Panel -> User Accounts).

Running around without an password makes it easy to gain access to your system and data. Every scriptkiddy that's within the reach of your wireless router and able to use a wireless sniffer may gain access in a matter of minutes (that's no fiction but a fact unless you use WPA or WPAv2 encryption on your wireless link).

Storm.

---

### Post by user1397 on 2006-06-24
[quote=Stormbringer]Well - this HOWTO was a piece of cake as it aims at simple home usage. but ...

The "second part" of the guide (I guess I'll call it "HOWTO: Setup Samba as an PDC with additional services") is planned, in the early stage of becoming, but won't happen soon (read: within a couple of a few days) as it's even more complex to write.

The aim will be professional usage of Ubuntu/Samba in Office-, School- or Corporate environments (as a replacement for Windows Servers) - therefore I will need to include basic guides on how to configure DHCP, DNS and NTP to play nice altogether.

If you like to proof-read or contribute the one or another idea I'll PM you the "development draft" as it gets complete.[/quote]thanks for that info, and no i don't need the develpoment draft, but thank you for the offer (as i'm extremely horrible when it comes to samba!)



[quote=Stormbringer] By looking at the drawing it looks good ... but ...

In case you have neighbors within the reach of your wireless router I hope you at least enabled encryption (WEP, 128-Bit minimum) so that no one can abuse your internet connection or exploit your data.[/quote]yes i do have 128-bit encryption on my router



[quote=Stormbringer] Do you need to enter a password upon bootup of Windows?[/quote]no...

[quote=Stormbringer] If you need to enter a password to log into Windows then Ubuntu has saved your password in the keyring - you must not enter it anew upon connect to the shared folder.

If Windows (XP?) doesn't ask you for a password you better set one right away (START -> Control Panel -> User Accounts).[/quote]i just made one!

[quote=Stormbringer] Running around without an password makes it easy to gain access to your system and data. Every scriptkiddy that's within the reach of your wireless router and able to use a wireless sniffer may gain access in a matter of minutes (that's no fiction but a fact unless you use WPA or WPAv2 encryption on your wireless link).[/quote]even if you have wep encryption on your router?

---

### Post by Stormbringer on 2006-06-24
[QUOTE=erik1397]even if you have wep encryption on your router?[/QUOTE]

WEP has a known design flaw in the encryption algorithm - by capturing raw pakets with an wireless sniffer (AirSnort and other auditing tools like this) you are able to "sniff" the encryption key in use.

Using 128-Bit WEP encryption will only make it a little more harder to sniff the key, but not impossible (in the end it's the software that's doing all the rocket-science for you).

- If your wireless router has an option to allow only specific MAC addresses use this option to tighten your security (input the MAC addresses of all your wireless cards). It won't protect you if the MAC gets faked by an attacker, but it's an additional step to make your wireless radio a little more secure.

- DISABLE the broadcast of your ESSID (that's the ID of the wireless router) - it'll be harder to find by using sniffers if it's "stealth" (not announcing itself to the rest of the world next to you). If you need to connect a new device you should know the name (ID) of your wireless router - so you're able to input it.

Being a little paranoid when it comes to wireless ethernet is always a good idea.

Storm.

---

### Post by Arisna on 2006-06-24
Thanks for posting this, Stormbringer.  Thank you also for your suggestion in the other Samba topic, although for the time being my network is made up of all trusted users (immediate family) and has no wireless access, so I do not see a security risk in allowing everyone on the LAN to see my (fairly unimportant) shared files.  I should have been more specific before.

Finally, I was curious what the security advantage would be in having the "hosts allow" parameter within the share definitions versus within the global section.  I understand the utility of per-share usergroup permissions.  Again, thank you for helping out people like me who are inexperienced with Samba.

---

### Post by user1397 on 2006-06-24
[quote=Stormbringer]WEP has a known design flaw in the encryption algorithm - by capturing raw pakets with an wireless sniffer (AirSnort and other auditing tools like this) you are able to "sniff" the encryption key in use.

Using 128-Bit WEP encryption will only make it a little more harder to sniff the key, but not impossible (in the end it's the software that's doing all the rocket-science for you).

- If your wireless router has an option to allow only specific MAC addresses use this option to tighten your security (input the MAC addresses of all your wireless cards). It won't protect you if the MAC gets faked by an attacker, but it's an additional step to make your wireless radio a little more secure.

- DISABLE the broadcast of your ESSID (that's the ID of the wireless router) - it'll be harder to find by using sniffers if it's "stealth" (not announcing itself to the rest of the world next to you). If you need to connect a new device you should know the name (ID) of your wireless router - so you're able to input it.

Being a little paranoid when it comes to wireless ethernet is always a good idea.

Storm.[/quote]okay, i did disable the ESSID, but the mac address thing is a little iffy.  In my router settings, I found a "MAC Address Clone" tab, and in it, it says: [FONT=verdana][SIZE=2][COLOR=black]"In this page, you can change the WAN MAC address of this router.
User Defined WAN MAC Address: 00.00.00.00.00.00"
how am i supposed to input all of my MAC addresses when I can only input one?!
Also, how do I find my wireless devices' MAC addresses?
[/COLOR][/SIZE][/FONT]

---

### Post by Stormbringer on 2006-06-24
[QUOTE=Arisna]Finally, I was curious what the security advantage would be in having the "hosts allow" parameter within the share definitions versus within the global section.  I understand the utility of per-share usergroup permissions.  Again, thank you for helping out people like me who are inexperienced with Samba.[/QUOTE]

The advantage is that you can control which clients, or network, will be allowed to connect to the share in question. Hosts that don't fall into allowed-list are not able to log into the service - even if they provide valid user credentials.

It may not be that important in a typical home-setup, but it makes some sense if you run samba on a multi-homed (server with several network-cards) system.

Hope this clarifies your question.

---

### Post by Stormbringer on 2006-06-24
[QUOTE=erik1397]okay, i did disable the ESSID, but the mac address thing is a little iffy.  In my router settings, I found a "MAC Address Clone" tab, and in it, it says: [FONT=verdana][SIZE=2][COLOR=black]"In this page, you can change the WAN MAC address of this router.[/COLOR][/SIZE][/FONT][/QUOTE]

Don't touch this setting! It's related to the WAN interface (the interface that connects your router to the internet).

BTW: What make (manufacturer) and model is your router?

[QUOTE=erik1397]Also, how do I find my wireless devices' MAC addresses?[/QUOTE]

In Windows (2000/XP) open the command prompt and type

> ipconfig /all

Find the Network Interface that represents your Wireless radio and write down the "Hardware address" (consists of 8 pairs of Hex-values).

---

### Post by user1397 on 2006-06-24
[quote=Stormbringer]BTW: What make (manufacturer) and model is your router?[/quote]it is a linksys
 BEFW11S4 wireless-B broadband router (it's one of the older kinds)

---

### Post by closeyourwindows on 2006-06-26
This is by far the best guide I have seen.  It worked on the first try and without a reboot.  I have been struggling with samba for some time now and this guide is  great.  Thanks.

---

### Post by gary4gar on 2006-07-02
awesome tuttorial mate
keep it up, very good work done
keep more like this cumming

---

### Post by penguinfan on 2006-07-02
Thanx Stormbringer, we need more penguins like u. This is the simplest & best howto by far. I got samba working 1st time and without reboot.

---

### Post by Stormbringer on 2006-07-02
Thanks for all your cheers ... I'm glad the guide works out that smoothly as it has been a rather quick edit.

---

### Post by mwells on 2006-07-03
Hi,

Firstly many thanks for the how-to it looks awesome . .and have printed it off allready!!

I just wondered if I could ask a stupid question as there is something that I havnt quite understood (about samba, not from your tut), and that is about the passwords.

[QUOTE=Stormbringer][b]
-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer
[/QUOTE]

Am i putting in the passwords for the Linux account? :oops: 

I get a little confused as I know samba can take the password from the windows logon session (i think) . . and this can somehow be used to tie into a user of matching name on the linux system

For instance i want to make my home directory viewable and writable by me. . and have it password protected, but how would I do this?

hope they arn't too stupid a question to ask, and once again thanks for the how-to

/Matt

---

### Post by Stormbringer on 2006-07-03
[QUOTE=mwells]I just wondered if I could ask a stupid question as there is something that I havnt quite understood (about samba, not from your tut), and that is about the passwords.

Am i putting in the passwords for the Linux account? :oops: [/QUOTE]

In the section you quoted from my howto you have to put in your username - not your password!

```

force user = mwells
force group = mwells

```

This assumes your useraccount on windows AND linux is actually called "mwells". Please change it to your setting.

[QUOTE=mwells]I get a little confused as I know samba can take the password from the windows logon session (i think) . . and this can somehow be used to tie into a user of matching name on the linux system[/QUOTE]

Add your useraccount to samba (the smbpasswd thing) and Samba should grant your Windows box access automatically!

Just to stress it once again - this'll only work if both useraccounts on both computers and both OS's have the very same username/password combo. If this isn't the case then it won't work out automatically.

[QUOTE=mwells]For instance i want to make my home directory viewable and writable by me. . and have it password protected, but how would I do this?[/QUOTE]

REMOVE the semicolons from the lines in the [homes] section (in smb.conf, everything that is written after a semicolon is considered to be a remark) ... make it look like the following example ...

```

[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

```

[QUOTE=mwells]hope they arn't too stupid a question to ask[/QUOTE]

From my point of view "stupid questions" don't exist --- no one know about everything...

---

### Post by mwells on 2006-07-03
ah sorry, i meant the username, my bad.

And thanks very much for the quick reply, that helped me out a lot.

So just to clarify, if there is a user 'mwells' on linux with password 'x', and a user with exactly the same credentials on a windows box they would sail straight in . .but if the user on windows had the same name but no (or a different password), would they then get a password prompt when trying to connect to the home file?

Also the create_mode and directory mode, is it a correct assumption to make that these place the writes on the files/directories created by the accessing user? and what would the %S rule give for valid users?

Once again, many many thanks for your help .. I realise i am being increadably lazy not reseaching this myself!

/Matt

---

### Post by Stormbringer on 2006-07-03
[QUOTE=mwells]ah sorry, i meant the username, my bad.[/QUOTE]

No problem ...

[QUOTE=mwells]So just to clarify, if there is a user 'mwells' on linux with password 'x', and a user with exactly the same credentials on a windows box they would sail straight in.[/QUOTE]

Yap - Windows (XP) should be able to find the shared folders of your Linux box as well as your home directory automatically in the Network Neighborhood as long as both users have the same login-credentials and as long as both computers are inside the very same workgroup (sorry, forgot to mention this).

[QUOTE=mwells]but if the user on windows had the same name but no (or a different password), would they then get a password prompt when trying to connect to the home file?[/QUOTE]

If the user has the same name but no, or different, password, Windows _should_ prompt you for the password.

[QUOTE=mwells]Also the create_mode and directory mode, is it a correct assumption to make that these place the writes on the files/directories created by the accessing user? and what would the %S rule give for valid users?[/QUOTE]

The "create mode" and "directory mode" lines are meant to keep the modes of the files nicely ... without these, Windows would create files and directories as 775 / 775 (rwxrwxr-x).

The default directory mode - inside of /home/<username> - is 755, and having mere datafiles executable by default wouldn't make much sense.

%S hold the username of the connection - so you will automatically connected to the right user-home.

[QUOTE=mwells]I realise i am being increadably lazy not reseaching this myself![/QUOTE]

In case you like to do some research: man smb.conf ;-)

---

### Post by featherking on 2006-07-03
Great guide,

Dont know if anyone stumbled across this problem but i was trying to share a folder with a space in the name. "//RON/iTunes Music" is the path to the folder i was trying to access from my linux box. I couldnt get it to work with the space; however, i found after some searching that samba accepts "\040" without quotes, as a space!

So if you want to share a folder with a space try it like this //RON/iTunes\040Music and you should be good to go.

Hope that helps somebody

-The King

---

### Post by Stormbringer on 2006-07-03
Alternatively you may put the UNC-Path inside of Quotes to make it work...

i.e. "\\RON\iTunes Music"

Example from within the command-line of Windows

net use x: "\\RON\iTunes Music" /persistent:yes

---

### Post by Shampyon on 2006-07-12
I'm now fully networked, write access and all, with my brother's PC. All thanks to the help recieved here, giving me the courage and the knowledge to get my hands dirty and actually set this up, where normally I would rely entirely on automated installers.

I doubt I'd be able to articulate how to do all this to anyone else, over the phone or 'net, but if anyone ever asked me to go over to their house to set up an XP/Ubuntu network I know I'd be able to do so with confidence.

I just wanted to say thank you to all the people involved in this thread for sharing your knowledge and being patient with our problems :)

---

### Post by AsYouWish on 2006-07-17
So ah... didnt work. 

I followed the instructions. When I go to map network drive on my winXP box, it looks but doesnt find anything. Im (really really) sure I have the ip address right and the share name right.

Could it be that I'm trying to share /home/share ? I tried changing some things according to the Wiki to be able to read/write home directories, but still, the samba share isnt being seen by my xp computer.

My xp account is Matt, and the account on my ubuntu machine is matt, with different passwords. I added matt, Matt, and just to be safe MATT, as samba users, still no effect.

I feel like I'm missing something... any clues?

Thanks

---

### Post by Stormbringer on 2006-07-17
> **AsYouWish said:**
> My xp account is Matt, and the account on my ubuntu machine is matt, with different passwords. I added matt, Matt, and just to be safe MATT, as samba users, still no effect.

Having different passwords across two machines for the same useraccount is a most common pitfall.

You added the useraccount to Samba (btw: there's no need for Upper-/Lowercase as Windows ignores the cases in a standard setup - so simply delete the ones having different spelling to the one of your Linux box) --- but with WHICH password?

- If you gave the user the password of your Linux box it's the wrong one. Change it with smbpasswd to the correct one.
- If you gave the user the password of your Windows box it's the right one and everything _should_ work ok.

Samba not displaying anything usually means...

...the user isn't enabled on the Linux box (sudo smbpasswd -e <username>)
...the password of the user accounts don't match.
...that one of the systems is inside the wrong workgroup.

That's all I can think of by looking at your post.

-Storm

---

### Post by AsYouWish on 2006-07-17
Ok so... that didnt work. Here is my smb.conf. I've tried several differnt version but this is straight from your howto.

My smb.conf:

```

[global]
    ; General server settings
    netbios name = server
    server string =
    workgroup = mshome
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Files]
    path = /media/share/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = matt
    force group = matt


```

So my ubuntu acct is matt with password1 and my winxp accoutn is Matt with password2. I set and enabled user 'matt' with password2 in smbpasswd. Still nothing. When I enter \\192.168.1.102\Files I get a pause, and then a 'could not be located' error. 

Does it matter Im running this on a PPC?
Does it matter that \media\share is not actual media but just a dir I created?
Does it matter that i'm setting this up via VNC to desktop 1 (not 0)

Argh. Sorry to be a pain. Thanks.

---

### Post by Stormbringer on 2006-07-17
Your smb.conf looks fine - and it shouldn't matter that you're running Ubuntu PPC.

Try the following command inside a Terminal ...

# smbclient -L localhost -U%

When asked for a password you need to type "password2".

If the command returns an error you either entered the wrong password or there's something fishy with  your samba setup. You should see something like this ...

```

Domain=[STORMBRINGER] OS=[Unix] Server=[Samba 3.0.22-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk      Network Logon Service
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (nebuchanezzar)
        ADMIN$          IPC       IPC Service (nebuchanezzar)
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22-Ubuntu]

        Server               Comment
        ---------            -------
        NEBUCHADNEZZAR       

        Workgroup            Master
        ---------            -------
        STORMBRINGER         NEBUCHADNEZZAR

```

If you get a result similar to the one from right above then samba is running and doing fine.

If not, let's see if Windows is freaking out...

Try to ping your Windows box from Linux and vice versa just to make absolutely sure that you're network connection is fine.

If this works please take a look into the Firewall control panel in Windows and make sure that the firewall is either disabled or "File- and Printersharing" is allowed to pass through the firewall.

Try to disable "Require SignOrSeal" (encrypted smb-connections) in Windows XP ...

To make this an easy job simply paste to following lines into notepad and save it as DisableReqSignOrSeal.reg (or any filename you like)

```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters]
"requiresignorseal"=dword:00000000

```

Open the location where you saved the file, double-click, and confirm the dialog.

Reboot and try again...

It should be sufficient to paste this line into any open Explorer windows: \\192.168.1.102\Files

If it still doesn't work, try to connect to the share from the command-line:

net use x: \\192.168.1.102\Files password2 /user:matt /persistent:yes

Try these steps and tell me how it turned out.

---

### Post by AsYouWish on 2006-07-17
Yeah... I'm a retard. Forgot about ZoneAlarm... silently blocking me from the outside world. Couldnt ping the XP box from Ubuntu so I added 192.168.1.100-110 to the trusted zone and bingo. Fully functional.


Thanks so much.

---

### Post by PENGUIN-PC on 2006-07-18
[COLOR="Blue"][FONT="Comic Sans MS"][/FONT][/COLOR] Well first of all I would like to say thank you very much for this post!!:KS 
But Im haveing a few issues that I can't quite solve. I can ping my linux box from a windows box and vice versa, but I can't exchange any data or map a drive. I tried everything in your post, but I still get, from both boxes, that permission is required.:-k Here is my output when I type  

 smbclient -L localhost -U%

 Domain=[WINBLOWS] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          IPC       IPC Service ()
        IPC$            IPC       IPC Service ()
        MyFiles         Disk
        print$          Disk
Domain=[WINBLOWS] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        DARE-DEVIL

        Workgroup            Master
        ---------            -------
        WINBLOWS             DARE-DEVIL


and this is my smb.cfg file setup

[global]
    ; General server settings
    netbios name = dare-devil
    server string =
    workgroup = WINBLOWS
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    ;interfaces = lo, eth0
    ;bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = dare-devil
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

;Uncomment if you need to share your CD-/DVD-ROM Drive
[DVD-ROM Drive]
    path = /media/dvd-rw
    browseable = yes
    read only = yes
    guest ok = yes

[MyFiles]
    path = /home/dare-devil/
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dare-devil
    force group = WINBLOWS

Any help would be greatly appreciated Storm!! Again thanks so much for your time you have put into making this post.

---

### Post by Stormbringer on 2006-07-18
Ok, let's see if we can get your problem solved ...

- About the "permission is required" thing:
What's the exact error message and what do you do to get it?

- About your smb.conf
Wait a sec; what's that?

```

[MyFiles]
    path = /home/dare-devil/
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dare-devil
    force group = WINBLOWS

```

Are you trying to share your home directory? That won't work out that way.

**EDIT** What's the "force group" ??? "WINBLOWS"? All uppercase? That looks dead wrong unless you created such a group yourself.

```

    force user = dare-devil
    force group = dare-devil

```

Would be more right.
**/EDIT**

If you like to "share" your home, then you should do it that way instead ...

```

[global]
    ; General server settings
    netbios name = dare-devil
    server string =
    workgroup = WINBLOWS
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    ;interfaces = lo, eth0
    ;bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = dare-devil
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

;Uncomment if you need to share your CD-/DVD-ROM Drive
[DVD-ROM Drive]
    path = /media/dvd-rw
    browseable = yes
    read only = yes
    guest ok = yes

```

The difference is that I enabled the [homes] section and removed the share you declared at the bottom of the file.

If the directory in question (/home/dare-devil) ***IS NOT*** the home directory of a valid user account but a badly placed data directory you like to share on the network you may have an issue with the filesystem permissions.

# sudo chmod 0777 /home/dare-devil
# sudo chown dare-devil.dare-devil /home/dare-devil

Again - **DO NOT ALTER the permissions if it's the home directory of a valid user account! You may break your local login.**
You've been warned.

Restart samba (sudo /etc/init.d/samba restart) and map your home-directory (commandline example):

net use h: \\dare-devil\dare-devil your_password /user:dare-devil /persistent:yes

Awaiting your answer ...

-Storm

---

### Post by PENGUIN-PC on 2006-07-18
Ok...thanks for the quick reply, I expected it to be a day or two!! 

Anyhow, in response, yes WINBLOWS is the name of the WORKGROUP I created on my windows box, and I just thought it would keep things simple if I used that as my force group. Did I figure wrong in my understanding of how this all works? I am new to samba, so i really appreciate all your help. 

Yes, /home/dare-devil is the home directory of a valid user account. I would like to share the whole directory, and I only want to share it with my home network not anything outside of it. I would like to be able to uncomment out the following so I can use your suggestion.

;interfaces = lo, eth0
;bind interfaces only = true

Do these lines have anything to do with preventing me from being able to use the connection?

As for the exact error message I get here is the screen dump for you.

Ohh and it seems that I already kinda bokre my login on my linux box, because it was telling me that I shouldn't be sharing my home folder or something like that ahhhh](*,) 

Thanks again for any, and all your help, it reall is appreciated storm, your're a great penguin!

---

### Post by Stormbringer on 2006-07-18
> **PENGUIN-PC said:**
> Ok...thanks for the quick reply, I expected it to be a day or two!! 

Anyhow, in response, yes WINBLOWS is the name of the WORKGROUP I created on my windows box, and I just thought it would keep things simple if I used that as my force group. Did I figure wrong in my understanding of how this all works? I am new to samba, so i really appreciate all your help.

The "force group" parameter inside the definition of the share DOES NOT, i repeat: DOES NOT, refer to a Windows-Workgroup but to the group of the local useraccount(s) on your Linux box.

So, "force group" should contain the same definition as "force user". But as you only like to share your home you won't need to bother with this directive.

> **PENGUIN-PC said:**
> 
Yes, /home/dare-devil is the home directory of a valid user account. I would like to share the whole directory, and I only want to share it with my home network not anything outside of it. I would like to be able to uncomment out the following so I can use your suggestion.


Kill the share you added at the bottom of the file and remove the comments at the [homes] section (remove the ";" at the beginning of the lines).

> **PENGUIN-PC said:**
> 
;interfaces = lo, eth0
;bind interfaces only = true

Do these lines have anything to do with preventing me from being able to use the connection?


Nope - the lines just tell samba to which network interfaces the daemon should bind by default; if it isn't specified it will bind to *any* available interface that is up.

This is a very useful directive if your box has multiple interfaces (i.e. 2 network cards, wireless, firewire, bluetooth, and so on). By giving the names of the interfaces the daemon will only bind to the ones you configured; the ones not specified will be leaved out.

> **PENGUIN-PC said:**
> 
As for the exact error message I get here is the screen dump for you.

You actually can share your home directory ([homes] section of smb.conf), but trying it the way you did may lead to severe problems.

> **PENGUIN-PC said:**
> 
Ohh and it seems that I already kinda bokre my login on my linux box, because it was telling me that I shouldn't be sharing my home folder or something like that ahhhh](*,) 

That's what the screenshot of the nautilus error-message suggests.

Please type

# ls -lisa /home
# ls -lisa /home/dare-devil

inside a terminal and paste the output into a post.

---

### Post by PENGUIN-PC on 2006-07-18
WOW, ok I hope your ready for this. Here it is

dare-devil@DARE-DEVIL:~$ ls -lisa /home
total 12
3244033 4 drwxr-xr-x  3 root       root       4096 2006-05-16 04:41 .
      2 4 drwxr-xr-x 21 root       root       4096 2006-07-12 16:56 ..
3244035 4 drwxrwxrwx 67 dare-devil dare-devil 4096 2006-07-18 12:30 dare-devil
dare-devil@DARE-DEVIL:~$ ls -lisa /home/dare-devil
total 700
3244035   4 drwxrwxrwx  67 dare-devil dare-devil   4096 2006-07-18 12:30 .
3244033   4 drwxr-xr-x   3 root       root         4096 2006-05-16 04:41 ..
3739484   4 drwxr-xr-x  13 dare-devil dare-devil   4096 2006-07-15 10:18 Applications
3768336   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-04 18:07 ARCADE
3248758   4 -rw-r--r--   1 dare-devil dare-devil   1302 2006-07-13 03:28 .audacity
3310341   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-07-11 01:41 .avidemux
3244176  12 -rw-------   1 dare-devil dare-devil  10149 2006-07-18 13:19 .bash_history
3244037   4 -rw-r--r--   1 dare-devil dare-devil    220 2006-05-16 04:41 .bash_logout
3244038   4 -rw-r--r--   1 dare-devil dare-devil    414 2006-05-16 04:41 .bash_profile
3244039   4 -rw-r--r--   1 dare-devil dare-devil   2227 2006-05-16 04:41 .bashrc3244154   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-05-16 19:56 .bmp
3768363   4 drwxr-xr-x   6 dare-devil dare-devil   4096 2006-07-11 03:21 Business
3768413   4 drwxr-xr-x   5 dare-devil dare-devil   4096 2006-05-04 18:07 Cartoons
3244286   4 drwx------   5 dare-devil dare-devil   4096 2006-05-24 12:35 .config3244248  36 -rw-r--r--   1 dare-devil dare-devil  35240 2006-06-20 04:19 config.log
3244183   4 -rw-r--r--   1 dare-devil dare-devil     39 2006-06-28 14:20 .current-song
3244117   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-07-18 12:33 Desktop3244042   4 -rw-------   1 dare-devil dare-devil     26 2006-05-16 04:49 .dmrc
3653633   4 drwxr-xr-x  13 dare-devil dare-devil   4096 2006-05-17 14:58 DOC'S
3244668   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-07-10 23:10 .dvdcss3310330   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-07-10 23:10 .dvdrip3248756  24 -rw-r--r--   1 dare-devil dare-devil  21716 2006-07-10 23:13 .dvdriprc
3653638   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-05-17 14:26 DWG'S
3244056   4 -rw-------   1 dare-devil dare-devil     16 2006-05-16 04:49 .esd_auth
 868391   4 drwxr-xr-x   8 dare-devil dare-devil   4096 2006-07-17 12:16 .evolution
3277212   4 drwxr-xr-x  10 dare-devil dare-devil   4096 2006-06-02 13:49 exaile
3278005   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-06-02 14:04 .exaile3244036   0 lrwxrwxrwx   1 dare-devil dare-devil     26 2006-05-16 04:41 Examples -> /usr/share/example-content
3248847   4 -rw-r--r--   1 dare-devil dare-devil   1043 2006-05-25 03:36 .face
3768626   4 drwxr-xr-x   6 dare-devil dare-devil   4096 2006-05-22 07:24 Flicks
3248859  16 -rw-r--r--   1 dare-devil dare-devil  12569 2006-07-15 10:00 .fonts.cache-1
3277447   4 drwx------   4 dare-devil dare-devil   4096 2006-07-09 21:55 .gaim
3244043   4 drwx------   5 dare-devil dare-devil   4096 2006-07-18 12:30 .gconf
3244044   4 drwx------   2 dare-devil dare-devil   4096 2006-07-18 13:21 .gconfd3279927   4 drwxr-xr-x  21 dare-devil dare-devil   4096 2006-07-17 04:02 .gimp-2.2
3244162   0 -rw-r-----   1 dare-devil dare-devil      0 2006-07-18 10:56 .gksu.lock
3244161   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-16 17:35 .gnome
3244046   4 drwx------  16 dare-devil dare-devil   4096 2006-07-18 11:05 .gnome23244047   4 drwx------   2 dare-devil dare-devil   4096 2006-05-16 04:49 .gnome2_private
3278255   4 drwx------   4 dare-devil dare-devil   4096 2006-06-21 06:53 .gnomesword-2.0
3244057   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-23 18:47 .gstreamer-0.10
3739486   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-17 11:22 .gstreamer-0.8
3248905   4 -rw-------   1 dare-devil dare-devil     59 2006-06-11 18:35 .gtk-bookmarks
3244354   4 drwxr-x---   2 dare-devil dare-devil   4096 2006-07-18 00:08 .gtk-gnutella
3244359   4 drwxr-xr-x   5 dare-devil dare-devil   4096 2006-05-16 20:20 gtk-gnutella-downloads
3244058   4 -rw-r--r--   1 dare-devil dare-devil     92 2006-05-16 04:49 .gtkrc-1.2-gnome2
3424312   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-17 14:50 GUI's
3244462   4 -rw-r--r--   1 dare-devil dare-devil     32 2006-05-24 17:23 .hwdb
3249087   4 -rw-------   1 dare-devil dare-devil   2323 2006-07-18 12:30 .ICEauthority
3277169   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-06-01 12:09 .icons
3277598   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-24 13:32 .java
3278350   4 drwx------   3 dare-devil dare-devil   4096 2006-06-27 05:59 .kde
3248946 220 -rwxr-xr-x   1 dare-devil dare-devil 217311 2006-06-20 04:19 libtool3293951   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-06-28 14:21 .listen1900657   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-17 12:20 .local
3244463   4 drwx------   3 dare-devil dare-devil   4096 2006-05-16 20:56 .macromedia
3244257   4 -rw-r--r--   1 dare-devil dare-devil   2094 2006-05-24 17:14 .mailcap
3278385   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-06-27 06:10 .mcop
3248985   4 -rw-------   1 dare-devil dare-devil     31 2006-06-28 10:58 .mcoprc3244112   4 drwx------   3 dare-devil dare-devil   4096 2006-05-16 04:49 .metacity
3244045   4 drwx------   4 dare-devil dare-devil   4096 2006-05-17 12:56 .mozilla
3244204   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-16 17:48 .mplayer
3244200   4 drwxrwxrwx 181 dare-devil dare-devil   4096 2006-06-08 18:10 MUSIC
3244116   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-16 04:49 .nautilus
 868388   4 drwxr-xr-x  20 dare-devil dare-devil   4096 2006-05-17 14:41 Old Engineering stuff
3277304   4 drwx------   3 dare-devil dare-devil   4096 2006-07-15 10:48 .openoffice.org2
3244877   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-04 18:01 PDF'S
3294171   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-06-28 19:48 Photos
3244880   4 drwxr-xr-x  11 dare-devil dare-devil   4096 2006-06-20 02:27 PICS
3293955   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-06-28 14:14 Podcasts
3278348   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-06-27 06:11 .qt
3293357   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-07-17 05:51 .quodlibet
3245318   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-07-02 18:27 Random Stuff
3248889  36 -rw-------   1 dare-devil dare-devil  34653 2006-05-24 17:27 .realplayerrc
3244228  20 -rw-------   1 dare-devil dare-devil  17267 2006-07-18 05:00 .recently-used
3245325   4 drwxr-xr-x   5 dare-devil dare-devil   4096 2006-05-17 15:40 RioSSeries
3245330   4 drwxr-xr-x   5 dare-devil dare-devil   4096 2006-05-04 18:02 School
3739281   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-04 18:02 screen savers
3276888   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-05-23 18:27 .subversion
3244163   0 -rw-r--r--   1 dare-devil dare-devil      0 2006-05-16 04:51 .sudo_as_admin_successful
3278312   4 drwx------   4 dare-devil dare-devil   4096 2006-06-21 06:53 .sword
3277168   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-06-01 12:09 .themes3244134   4 drwx------   4 dare-devil dare-devil   4096 2006-05-17 12:12 .thumbnails
3244115   4 drwx------   4 dare-devil dare-devil   4096 2006-07-18 06:06 .Trash
3244111   4 drwx------   2 dare-devil dare-devil   4096 2006-05-16 04:49 .update-notifier
3293584   4 drwxr-xr-x   3 dare-devil dare-devil   4096 2006-07-17 08:34 .vlc
3244443   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-06-27 05:11 .wapi
3248751   4 -rw-r--r--   1 dare-devil dare-devil      4 2006-05-17 12:15 .windows-label
3739417   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-07-15 10:23 .wine
3244424   4 -rw-------   1 dare-devil dare-devil    121 2006-07-18 04:31 .Xauthority
3244203   4 drwxr-xr-x   2 dare-devil dare-devil   4096 2006-05-17 00:06 .xine
3739387   4 drwxr-xr-x   7 dare-devil dare-devil   4096 2006-05-04 18:03 XLS'S
3244120   4 drwxr-xr-x   4 dare-devil dare-devil   4096 2006-05-16 17:41 .xmms
3244040   4 -rw-r--r--   1 dare-devil dare-devil   1322 2006-07-18 13:17 .xsession-errors
dare-devil@DARE-DEVIL:~$

---

### Post by mmcclure79 on 2006-07-18
I set everything up step by step and I can;t get to my windows boxes from Xubuntu. I keep getting an error dialog box with: "smb:///" is not a valid location. This is when I'm trying to browse the network.

Here's my samaba config:
[global]
    ; General server settings
    netbios name = laptop
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/Share/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = michael
    force group = michael


then there's this:
michael@laptop:~$ smbclient -L localhost -U%
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        GATEWAY2000
        LAPTOP
        SARASUSAN            Punkie's Mommie

        Workgroup            Master
        ---------            -------
        WORKGROUP            LAPTOP


As far as I can tell Samba is seeing everything like it should, but I can'te tell what's going on...

---

### Post by PENGUIN-PC on 2006-07-18
hello

---

### Post by Stormbringer on 2006-07-18
Ok, so far the permissions look good ... just switch the permissions of your home directory back to default:

chmod 0770 /home/dare-devil

As for the smb.conf ... if you followed all the other steps (creating samba user accounts) the following conf should do the trick for you:

```

[global]
; General server settings
netbios name = dare-devil
server string =
workgroup = WINBLOWS
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
;interfaces = lo, eth0
;bind interfaces only = true

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

[homes]
valid users = %S
create mode = 0600
directory mode = 0755
browseable = no
read only = no
veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = dare-devil
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

;Uncomment if you need to share your CD-/DVD-ROM Drive
[DVD-ROM Drive]
path = /media/dvd-rw
browseable = yes
read only = yes
guest ok = yes

```

In Gnome press ALT+F2 (Run Application), type

gksudo /etc/samba/smb.conf

and paste the lines from above into the file or do the modifications by hand. Save the file, open a terminal and restart samba to make changes happen (sudo /etc/init.d/samba restart). Maybe it's a good idea to reboot your Windows box as well.

To get access to the home directory from Windows:

\\dare-devil\dare-devil

If that doesn't work try to subsitute the name of your Linux box with its ip-address (type ifconfig inside a terminal)

\\192.168.0.11\dare-devil
THIS IS AN EXAMPLE - REPLACE WITH >>>YOUR<<< IP-ADDRESS !!!

(somehow a thought of a long time ago creeps through the dark edges of my memories that windows may dislike the fact that the system and username is identical)

If my fear is right, then try to change the name you configured in samba to i.e.:

netbios name = devilbox

Restart samba and try to make the connection again.

Try this and report back.

Oh, and thanks for the cheers ... your sister is right; Austria is a nice country to spend your holidays.

---

### Post by Stormbringer on 2006-07-18
> **mmcclure79 said:**
> I set everything up step by step and I can;t get to my windows boxes from Xubuntu. I keep getting an error dialog box with: "smb:///" is not a valid location. This is when I'm trying to browse the network.

This rather sounds like some package is missing in your installation of Ubuntu.

As I have no experience with XUbuntu (running a fully fleged install of Ubuntu 6.06 AMD64) I'm only able to guess ...

Try to install "smbfs"...

sudo apt-get install smbfs

...and see if things work out. Chances are that the network browser may need that package to be installed.

---

### Post by PENGUIN-PC on 2006-07-18
STORM YOU ARE AMAZING!!!! Everything works just fine now! The user name and system name being the same was not a problem. I can't thank you enough! I was able to transfer files back and forth to both computers without any troubles at all. Now I guess I need to understand how all this worked. Cheers!!

---

### Post by Stormbringer on 2006-07-18
> **PENGUIN-PC said:**
> STORM YOU ARE AMAZING!!!! Everything works just fine now! The user name and system name being the same was not a problem. I can't thank you enough! I was able to transfer files back and forth to both computers without any troubles at all. 

As usual I'm honored I could be of help.

> **PENGUIN-PC said:**
> 
Now I guess I need to understand how all this worked. Cheers!!

If you really like to dig yourself into the mysteries of samba start by reading the man-page (type "man smb.conf" inside a terminal) or take a look into [Samba's website]("http://samba.org/"); lots of resources can be found there.

---

### Post by Turtle.net on 2006-07-19
Hi,
I know you already answered this kind of question ... but it's still not clear for me.
Let say I have a desktop running Ubuntu and a laptop running XP.
If I understand well I need to have the same login/passwd for my desktop and laptop to access the share folders through samba ???
That could be easy if the desktop and the laptop have the same real user ... but what if the user are different (and then want to create different user accounts, logins, passwd...) or if you have several laptops connected to the desktop...

Sorry if you think that my questions are irrelevant...I definitely need some sleep.

---

### Post by cpk1 on 2006-07-19
I followed all the steps but samba still doesnt seem to be cooperating.  In windows when I try to map the drive using \\roxxor\home\kateandalex\sharedsamba it just keeps on prompting me for user name and password, it doesnt say if its wrong or right, just keeps bringing up the same thing, both machines are able to ping each other as well. Any help would be greatly appreciated. Also as a side note in the force user and force group could you just add more people by seperating them with ; so they would all be able to access the same share? smbclient -L localhost -U% only gives me:
cpk1@roxxor:/etc/samba$ smbclient -L roxxor -U%
Domain=[TEAMAWESOME] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_LOGON_FAILURE
Also testparm gives me this 

cpk1@roxxor:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[roxxorshared]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = TEAMAWESOME
        server string =
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes
        valid users = %S
        read only = No
        create mask = 0600
        printing = cups
        print command =
        lpq command = %p
        lprm command =
        veto files = /*.{*}/.*/mail/bin/
        browseable = No

[print$]
        path = /var/lib/samba/printers
        write list = root
        read only = Yes
        create mask = 0664
        directory mask = 0775
        guest ok = Yes
        browseable = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes

[roxxorshared]
        path = /home/alexandkate/sambashared
        force user = alexandkate
        force group = alexandkate
        create mask = 0644
        browseable = Yes

---

### Post by Stormbringer on 2006-07-19
> **Turtle.net said:**
> Hi,
I know you already answered this kind of question ... but it's still not clear for me.

Let say I have a desktop running Ubuntu and a laptop running XP.
If I understand well I need to have the same login/passwd for my desktop and laptop to access the share folders through samba ???

No, you mustn't have the same login/password - it's just a recommendation to keep things simple.

Only IF you have the same useraccounts on, to follow your example, your desktop and laptop life would be a lot easier if both accounts would have the same passwords.

> **Turtle.net said:**
> That could be easy if the desktop and the laptop have the same real user ... but what if the user are different (and then want to create different user accounts, logins, passwd...) or if you have several laptops connected to the desktop...

Samba is a _server_ daemon --- where's the problem?

Just add the required useraccounts with their respective passwords by using smbpasswd and you're all set (we're using TDBSAM as our backend for user accounting; not Linux's shadow). Additionally you may need to make sure that the access right(s) to the share(s) (located in smb.conf) will fit.

Any specific scenario you are thinking about?

---

### Post by Stormbringer on 2006-07-19
> **cpk1 said:**
> I followed all the steps but samba still doesnt seem to be cooperating.  In windows when I try to map the drive using \\roxxor\home\kateandalex\sharedsamba<snip>

The mapping is wrong ...
Could I bug you to try again with: \\roxxor\roxxorshared

You need to use the name of the share as you specified inside the brackets...

[roxxorshared] **<--- THIS ONE HERE!!!**
        path = /home/alexandkate/sambashared **<--- *NOT* THIS!!!**
        force user = alexandkate
        force group = alexandkate
        create mask = 0644

---

### Post by cpk1 on 2006-07-19
thank you for the quick reply, unfortunatly \\roxxor\roxxorshared gets the same result =\

edit: sorry i forgot to mention i have swat installed but am not using it, but i am under the impression it wont change my .conf file unless i access the webpage?

---

### Post by Stormbringer on 2006-07-19
Wait a moment ... I overlooked this one here ...

```

cpk1@roxxor:/etc/samba$ smbclient -L roxxor -U%
Domain=[TEAMAWESOME] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_LOGON_FAILURE

```

AND

```

cpk1@roxxor:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[roxxorshared]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated

```

The first error message usually only shows up when a firewall (do you have Firestarter running?) is blocking the traffic or if eth0 and/or lo isn't up.

EDIT: Did you add AND enable your useraccount in samba (NT_STATUS_LOGON_FAILURE)?

The second error message is new to me ... did you specify that parameter inside your smb.conf (testparm doesn't show everything)? Hmm ... need to look into this.

Please post the whole contents of your smb.conf!


And about the access rights ...

force group and force user has NOTHING to do with access rights to the share; it has to do with local filesystem permissions! The parameter you were thinking about is "valid users" (valid users = user1, user2, user3 ...)

Without specifying "valid users =" ALL authenticated users will be able to access the share.

-Storm

---

### Post by cpk1 on 2006-07-19
here is my full conf

cpk1@roxxor:/etc/samba$ cat smb.conf
[global]
    ; General server settings
    netbios name = ROXXOR
    server string =
    workgroup = TEAMAWESOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[roxxorshared]
    path = /home/alexandkate/sambashared
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = alexandkate
    force group = alexandkatecpk1@roxxor:/etc/samba$    

not sure which account you mean when you say useraccount, i had alexandkate added and enabled when i first went through and just now added cpk1, still same output from smbclient -L roxxor -U% no firewall that I can see on ps aux, plus i think it would be blocking apache and mysql if there was one running.  once again thank you for your direct help!

---

### Post by cpk1 on 2006-07-19
good news! got rid of everything and tried going through it all again and it worked!  I think trying to use swat might have messed things up? That or I just made a typo/mistake and didnt notice it. I wasnt able to map the drive in windows by start > right click my computer > map network drive.  I just found my linux box in network places and mapped it from there, login worked and everything! thank you for the help and the well written guide!

---

### Post by Turtle.net on 2006-07-20
> **Stormbringer said:**
> No, you mustn't have the same login/password - it's just a recommendation to keep things simple.

Only IF you have the same useraccounts on, to follow your example, your desktop and laptop life would be a lot easier if both accounts would have the same passwords.

Ok, now I think I understand the trick with the accounts.
On my home network I have a desktop (running ubuntu only) and a laptop (running XP and ubuntu in dual boot).
On my laptop, I have the same login/pswd for ubuntu and for XP (let say it's lap/xxx) and on my desktop i have the following login/pswd : desk/yyy.
My problem is : I can access the share folder I created on my desktop from my laptop under ubuntu ... but not under XP (same IP for XP and ubuntu on the laptop btw).
I really don't understand. Just to be sure I removed the firewall on my XP box ... and nothing changed.
Do you think the problem can be caused by the fact that XP is a smb server by itself ?

---

### Post by Turtle.net on 2006-07-20
I have done a little bit of XP network configuration using the XP's network wizard, and I disabled all the shared folders ... then suddenly the shared folder from my desktop appeared.
So the problem was really to have XP as a smb server on the same network.
Looks like my problem is solved ;)

---

### Post by mac73 on 2006-07-21
hi Stormbringer

tnx 4 givin such a good help.
u make samba so easy dat any novice user can configure it .

bt i hv 1 doubt dat i want to add group.

i hv tried dat with followin commands

   groupadd -r groupname
   adduser -r -g trust -d/dev/null/-s/dev/null compname$

  which we always use in redhat linux
   bt. not workin in ubuntu

  and 1 more thing i wanna make MSHOME as domain rather than workgroup.
  what changes i hv to make in smb.conf?

  i tried dat with   



           domain master = yes

bt. not getin.

pls........... help me out.
tnx

---

### Post by justicerulesok on 2006-07-26
I've just found this thread & wanted to say thank you :-)

You've just solved 25% of my ubuntu issues & made me look really clever in front of my boss. :-D :-D 

Cheers!

Justice

---

### Post by BatteryCell on 2006-07-26
Worked great for me :-) only question is how does one tie in a mac into this server (seeing as mac sort of runs on unix)?

---

### Post by core on 2006-07-28
Hi stormbringer, and thanks already for the howto. It worked great a few days ago when i followed it. I'm using vmware to emulate a virtual machine with windows xp on it, and I was mapping driver E:\ as my linux home directory. It was ok, no problems.

Still, after a few days it stopped working and I still don't know why. I'm using my pc about 3 times a week, all I've been doing is mostly those kubuntu critical updates, and I'm not sure if I changed my password.

I thought this password problem was the issue, but still to make sure it worked again i decided to run the howto all over again.

checked samba install, stopped daemon, overwritten smb.conf with yours and reconfigured it again, pointing the samba path to /home/my_user. reconfigured windows on it too, removed that netbios-wins support thingy and added my ip again, but no luck. The DAPPER network computer is detected, MyFiles folder is detected, they always are, but when I try to map a drive to it, it says (after a few seconds attemping to connect)

"The mapped network drive could not be created because the following error has occured: An extended error has occurred."

The error is different when the daemon is stopped, so I assume it has something to do with the configuration.

What am I doing wrong? Sorry for the extended crying for help :p Thanks in advance.

PS: I have static ip address but sometimes it changes on ISP maitenance. I noticed the IP changed these past few days, but I've configured it again with the new IP.

---

### Post by Stormbringer on 2006-07-28
> **mac73 said:**
> hi Stormbringer

tnx 4 givin such a good help.
u make samba so easy dat any novice user can configure it .

bt i hv 1 doubt dat i want to add group.

i hv tried dat with followin commands

   groupadd -r groupname
   adduser -r -g trust -d/dev/null/-s/dev/null compname$

  which we always use in redhat linux
   bt. not workin in ubuntu

  and 1 more thing i wanna make MSHOME as domain rather than workgroup.
  what changes i hv to make in smb.conf?

  i tried dat with   



           domain master = yes

bt. not getin.

pls........... help me out.
tnx

Sorry for the late reply ... been a little busy lately.

The configuration variable "WORKGROUP =" >>> IS <<< the name of the Domain - t4|<3 4 l00|< 47 7|-|3 d0|<u 4|\|d l34|2|\| 70 3><p|2355 `/0u|2531f!

Oh --- and before you can add a user to some group you better create the group on the local system (groupadd).

---

### Post by Stormbringer on 2006-07-28
> **core said:**
> The DAPPER network computer is detected, MyFiles folder is detected, they always are, but when I try to map a drive to it, it says (after a few seconds attemping to connect)

"The mapped network drive could not be created because the following error has occured: An extended error has occurred."


I love Microsoft's error messages; they are soooo informative.

As you are using VMware (no matter if it's Workstation or Server): did you install a kernel upgrade lately?

If the answer is yes, did you run "sudo vmware-config.pl" to compile the necessary modules for the new kernel? If the answer is no do it _right now_!

Otherwise ...

Please start up VMware, open a command prompt, and type:

ipconfig /all

Please post the output into a reply (or PM me if it's a public IP address).

> **core said:**
> The error is different when the daemon is stopped, so I assume it has something to do with the configuration.

When samba is stopped you should get an error saying that the network path could not be found ... no wonder though.

-Storm

---

### Post by franciscopaco on 2006-07-28
Stormbringer. I just whant to say, Thanks for the howto

---

### Post by core on 2006-07-28
> As you are using VMware (no matter if it's Workstation or Server): did you install a kernel upgrade lately? If the answer is yes, did you run "sudo vmware-config.pl" to compile the necessary modules for the new kernel? If the answer is no do it _right now_!

Yes, but i think samba stopped working before. After I updated the kernel, VMWare stopped working, so I ran vmware-config.pl again to compile it according to my current kernel.
But still, I did it again right now, restarted windows and still the same error appears.


> Otherwise ...

Please start up VMware, open a command prompt, and type:

ipconfig /all

Please post the output into a reply (or PM me if it's a public IP address).

I did so, check your PM inbox. Thanks!

Still, help from others are more than welcome.

---

### Post by verbatim210 on 2006-07-29
any idea why i cannot WRITE to my samba share?

---

### Post by Stormbringer on 2006-07-29
> **verbatim210 said:**
> any idea why i cannot WRITE to my samba share?

I bet the permissions of the folder/mountpoint in your local filesystem are wrong ...

sudo chmod 0777 /path/to/the/shared-folder
sudo /etc/init.d/samba restart

NOTE: DON'T CHANGE THE MOD OF YOUR HOME-DIRECTORY!

---

### Post by Stormbringer on 2006-07-29
> **core said:**
> I did so, check your PM inbox. Thanks!

I wrote an reply to your message by PM as well ... please have a look at your inbox.

-Storm

---

### Post by verbatim210 on 2006-07-29
> **Stormbringer said:**
> I bet the permissions of the folder/mountpoint in your local filesystem are wrong ...

sudo chmod 0777 /path/to/the/shared-folder
sudo /etc/init.d/samba restart

NOTE: DON'T CHANGE THE MOD OF YOUR HOME-DIRECTORY!

thanks storm
your bullet hit the dot!

---

### Post by Flyn on 2006-07-29
Only Samba HOWTO that worked for me.
Great job!

---

### Post by dmizer on 2006-07-30
you sir/madam are my personal hero.

you LITERALLY saved my job.  thank you.

---

### Post by dmizer on 2006-07-31
and just ran into my first snag.  can't figure out how to add multiple users.

it works for the primary user on the system, but if i add users via the following example:
```
sudo useradd -s /bin/true NEW_USERNAME
sudo smbpasswd -L -a NEW_USERNAME
sudo smbpasswd -L -e NEW_USERNAME
```
i can't get the additional user to work.

for this section of my samba.conf file:
```
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```
where do i add the additional user?

if i say "force user = YOUR_USERNAME NEW_USERNAME"
then no one can logon.
but if i configure it as follows:
```
force user = YOUR_USERNAME
force group = YOUR_USERGROUP
force user = NEW_USERNAME
force group = NEW_USERGROUP
```
where NEW_USERGROUP is the same as NEW_USERNAME.

then i can log on with the YOUR_USERNAME, but no one else works.

EDIT:
[COLOR="Red"]yeah so, i reread it and figured out that new users don't have to be added to the samba.conf file.  i have two users working now :)[/COLOR]

---

### Post by Stormbringer on 2006-07-31
> **dmizer said:**
> EDIT:
[COLOR="Red"]yeah so, i reread it and figured out that new users don't have to be added to the samba.conf file.  i have two users working now :)[/COLOR]

Hi!

Just came across your post; sorry for the delay *gomen*

Glad you figured it out ... as it's just a matter of adding and enabling the user(s) with smbpasswd.

- Storm

P.S.: As the "force user" and "force group" parameter seems to cause confusion here's a general hint for everyone ...

The parameter refers to the user/group to whom the files inside the shared directories will belong; it has nothing to do with access rights/priviledges!

---

### Post by royskie on 2006-07-31
storm....you're the man!.....I 've just started using Ubuntu....you're howto is so easy to follow that I got file sharing working in the first pass!...cheers to you dude!

---

### Post by dmizer on 2006-07-31
> **Stormbringer said:**
> Hi!

Just came across your post; sorry for the delay *gomen*

Glad you figured it out ... as it's just a matter of adding and enabling the user(s) with smbpasswd.

- Storm

P.S.: As the "force user" and "force group" parameter seems to cause confusion here's a general hint for everyone ...

The parameter refers to the user/group to whom the files inside the shared directories will belong; it has nothing to do with access rights/priviledges!

tondemonai.

it only took me about 20 minutes and a reread of your first post to figure it out on my own.  and i actuall made good use of that "force user, force group" to resolve a problem with some sensitive "boss only" access files.

you really are the man.  vielen dank!

edit:
actually, i went back through and figured out why i tripped up on adding new users.  it's in this line:

> In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!
so no problem adding them to my system, but when you say "AND samba" i assumed you meant samba.conf.

---

### Post by Flavian on 2006-08-01
Hi :)
Thanks for this great howto!
It worked out just fine.
However I got a problem with the user permissions.
I want my brother to access his folder and I want myself to access my own, but neither one of us should see the content of the others folders.

The problem is that "force user" doesn't seem to work.
Everyone can view all the folders. I tried messing around with chmod and chown, but it doesn't work out.
I also set up the users on the linux machine and did everything according to the howto!

I don't know what to do anymore. I really need user permissions, since there are files that some people should not see.

Can someone help please?
Flo

---

### Post by Flavian on 2006-08-01
[QUOTE=Stormbringer;1319971
The parameter refers to the user/group to whom the files inside the shared directories will belong; **it has nothing to do with access rights/priviledges!**[/QUOTE]

Sorry, I just read your post after posting my last one!
I think I made that mistake as well.
Can you tell me than how I set up access permissions, like in windows, that would be very important!
Thanks in advance.
Flo

---

### Post by Stormbringer on 2006-08-01
> **Flavian said:**
> 
Hi
Thanks for this great howto!
It worked out just fine.
However I got a problem with the user permissions.
I want my brother to access his folder and I want myself to access my own, but neither one of us should see the content of the others folders.

The problem is that "force user" doesn't seem to work.
Everyone can view all the folders. I tried messing around with chmod and chown, but it doesn't work out.
I also set up the users on the linux machine and did everything according to the howto!

I don't know what to do anymore. I really need user permissions, since there are files that some people should not see.

Can someone help please?
Flo

----------------------------------------

Sorry, I just read your post after posting my last one!
I think I made that mistake as well.
Can you tell me than how I set up access permissions, like in windows, that would be very important!
Thanks in advance.
Flo

OK - let us start this way: could you please tell me what shares you configured (i.e. include the part in question into a reply)? Would make life easier as I won't have to guess.

However, let's assume the following - maybe we get a direct hit:

You and your brother have a user account on your Linux box and you want to access the HOME directories (/home/<username>)

- Open smb.conf for editing
Either type "sudo gedit /etc/samba/smb.conf" in a terminal or press ALT+F2 and input "gksudo gedit /etc/samba/smb.conf".

- Find the following section:

```

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

```

and change it to ...

```

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

```

- Save the changes

- Restart samba

Type "sudo /etc/init.d/samba restart" in a terminal


On Windows the shared home-directory (it's called by the username you have on your Linux box) should be automatically detected. If not, simply type \\<COMPUTERNAME>\<username> into the address bar of Windows Explorer - and if it doesn't work out by the name subsitute it with the ip address. Don't forget to input the correct credentials (username/password) when asked.


If you are running a different configuration I rely on your feedback ...

-Storm

---

### Post by Flavian on 2006-08-01
Hi Storm thanks for your quick reply!

Here's the deal ;)
My Network at home includes 3 Pcs and a server.

My brother: windows
My Dad: Windows
Me: Windows / Linux Hybrid

Since I use linux most of the time I was planning on just setting up normal shares for everyone (like I had it before when I had my windows server running) so everyone has his own area where he can store stuff and no one else but him can access it.
And than there is a global share called "Data" where I have stored all the programs, and installs (especially for windows) which me and my brother should have write permissions to, but my dead only read because he is very computer illiterate and I don't want him to mess up or delete files by accident.

So it was when I had set up the windows server and so I was thinking to do it with linux.

I have to say that I do not really understand the benefit of the /home directory thing.
AND the home directory is also on the system partition of the linux server, which means that I would have to move it one of the bigger HDDs in the server. (I could not find how to do that, so I stuck to the idea mentioned above, by just creating single shares)

I hope you could follow my description...

Here's my smb.conf:

> 
[global]
    ; General server settings
    netbios name = SERVER
    server string =
    workgroup = WURM
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = trues
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes


############ Fileshares begin here #############

[Data]
    path = /media/hdb1
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0750

[Florian]
    path = /media/hdc1/Florian
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0750
    force user = florian
    force group = florian

[Lukas]
    path = /media/hdc1/Lukas
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0750
    force user = lukas
    force group = lukas
    
[Hans-Jörg]
    path = /media/hdc1/Hans-Jörg
    browseable = yes		
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0750
    force user = hans-jörg
    force group = hans-joerg



Thanks for your nice help :)
Flo

---

### Post by Stormbringer on 2006-08-01
> **Flavian said:**
> Here's my smb.conf:

null passwords = [COLOR="Red"]trues[/COLOR]


TYPING MISTAKE ENCOUNTERED!!!!
Please correct it to read "true"

> **Flavian said:**
> 
[Data]
path = /media/hdb1
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0750


Although you want ALL of your family to have access here you should set "force user" and "force group" to the user account with whom you usually work on your Ubuntu box - I assume it's yours ...

Please add...

force user = florian
force group = florian

As I already stated in the thread: the "force user" and "force group" parameter **has nothing to do with access priviledges but with the permissions of the local linux filesystem.** All authenticated users will have access here.

EDIT
Short explaination:
Setting a forced user/group will make sure that all files and folders will belong to the user that is working on the box - so you won't have any troubles accessing the files/folders from within Ubuntu.

To figure out the difference...

Do a

ls -lisa /media/hdb1/

and

ls -lisa /media/hdc1/Lukas
or
ls -lisa /media/hdc1/hans-joerg

The difference in the file permissions should be easily spotted.
/EDIT
> **Flavian said:**
> 
[Florian]
path = /media/hdc1/Florian
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0750
force user = florian
force group = florian


To lock this share so that ONLY YOU will have access add the following line...

valid users = florian


> **Flavian said:**
> 
[Lukas]
path = /media/hdc1/Lukas
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0750
force user = lukas
force group = lukas


Same here ... if ONLY lukas should have access add ...

valid users = lukas


> **Flavian said:**
> 
[Hans-Jörg]
path = /media/hdc1/Hans-Jörg
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0750
force user = hans-jörg
force group = hans-joerg


Please refrain from using german umlauts - stick to plain ASCII (although Dapper supports UTF-8 without any hitches, at least for me, you better not try to trigger problems lurking in the dark corners). German Umlauts in the share declaration and/or path in the local filesystem may cause major issues. This, however, does not apply to the files you store on the share ... as long as >Windows< happily recognizes the correct characters you are fine.

Therefore, better delete the user account (from your system and with smbpasswd from samba) and make it up anew by writing is as "hans-joerg".

As soon as it's done add ...

valid users = hans-joerg

...to lock down the share for this user ONLY.


After you made the changes you need to restart samba (reloading doesn't always work out) --- sudo /etc/init.d/samba restart.

-Storm

---

### Post by Flavian on 2006-08-01
Thank you very much, Storm for your nice and easy to follow answer!
You said that I should not use German Umlauts, yepp I would love not to do so :D Since it's an annoying pain, BUT I read in your first post that one should use the exact same user name and password as used for the Windows Box.
Since I was so smart to put Hans-Jörg there, I thought it might not work out with the user / password checking.

If all else fails I would have to change the windows install on my Dad's laptop I suppose :)

Thank you very much for your help again.
Flo

---

### Post by Stormbringer on 2006-08-01
> **Flavian said:**
> You said that I should not use German Umlauts, yepp I would love not to do so :D Since it's an annoying pain, BUT I read in your first post that one should use the exact same user name and password as used for the Windows Box.
Since I was so smart to put Hans-Jörg there, I thought it might not work out with the user / password checking.

Alright, if you already have the user account on your dad's Windows laptop then simply leave it as it is to spare you the hassle of reconfiguring the whole stuff.

Glad I could be of help once more.

Cheers,
Storm

---

### Post by Flavian on 2006-08-01
One more little question left (sorry to bug you with that, but I am a real newbie to Linux :/ )

What do I do when I want to have

Lukas: read/write
Florian: read/write
Hans-Jörg: ONLY READ permissions

on [Data] ?

Thanks in advance.

Flo

---

### Post by Stormbringer on 2006-08-01
> **Flavian said:**
> What do I do when I want to have

Lukas: read/write
Florian: read/write
Hans-Jörg: ONLY READ permissions

on [Data] ?

Uh, it starts to get tricky ... that's an option I never had to implement (not even in a corpoprate server setup) ... hmm ...

Try it that way (but write down the current mode and ownership in case it breaks something really badly):

sudo chmod 0774 /media/hdb1
sudo chown florian.lukas /media/hdb1

To my knowledge it should give "others" read-only rights ... not really sure if samba will honor that.

---

### Post by andho on 2006-08-04
gud day and amazing how-to stormbringer.
i read through this thread and cudnt figure out how to access my windows shares from the ubuntu box. 
ps. i can access the ubuntu shares from the windows box.

---

### Post by stig on 2006-08-04
Stormbringer, this is a brilliant howto guide and you have solved a lot of individual problems in the thread. I have had problems trying to set up a network for ages, so I decided to follow your howto instructions. But I have one last problem as shown below.

I have two Ubuntu 6.06 PCs and one Windows 98 behind a broadband NAT router, connected by cable and using DHCP. The Windows PC does not use any passwords. One Ubuntu box is used by me and the other by my wife. We use them for our home business and our leisure. My objective is to be able to copy files from one box to another so that we can back-up and transfer files to each other’s box.

I followed your instructions carefully on both Ubuntu PCs making identical smb.conf files, except for the netbios name = where I have used the individual computer name (ubuntu1 and ubuntu2), and the force user and force group which have the respective user (me on ubuntu1 and wife on ubuntu2). They have the same workgroup name, mshome. Wins support is set to “no” because I am on DHCP.  I set up a home/samba folder on each box and did the permissions as you instructed.

Then I made the PC user a samba user and set the passwords as the ubuntu logon password - so my ubuntu box has me as a samba user with my password, and my wife’s box has her. I found that this allowed me to access the shared “samba” folder on my wife’s box but only using her login name and password (and vice versa for the other box). So I set each of us as a system user and samba user on the other box (as in your “mark” example) -  I made my wife a user on my box and me a user on hers. This then allowed me to access the shared samba folder on her box using my name and password. I checked that I could copy files into the folders - i.e. between ubuntu boxes. And this works. So far so good!

But I cannot access the ubuntu folders from Windows. In Network Neighbourhood I get icons for the ubuntu boxes but when I try to click them open it always asks me for a password. I get:
“Enter Network Password” “You must supply a password...” “Resource: \\UBUNTU2\IPC$”
Clicking OK without a password does not work and neither of the samba/ubuntu passwords works.

It would be great if you could help me solve this final problem!

---

### Post by Stormbringer on 2006-08-04
> **andho said:**
> i read through this thread and cudnt figure out how to access my windows shares from the ubuntu box.

That's quite easy actually....

Method 1 - Gnome:

While in Gnome you may use "Connect to Server" (to be found in the places menu).

Change the Drop-Down to "Windows Share (smb)", enter the name or IP# of your Windows PC, enter your name and your password. You musn't fill out all of the fields.

If you done right the icon of the network drive will appear on your desktop.

Be advised that this method has the one or another drawback:

The Windows Share gets connected as a virtual filesystem (no mountpoint). Applications not using Nautilus's file-requester dialogs (OpenOffice and Skype on Ubuntu AMD64 as an example) aren't able to access the share.

The idea behind this concept is great, the realization is ... useless.


Method 2 - Mount it

You can also mount the Share(s); either on boot or manually.

First, make sure you have smbfs installed - open a terminal and type:

sudo apt-get install smbfs

As soon as it's installed you can go ahead and happily mount your shares.

Example:

- Create a mountpoint
sudo mkdir /media/WindowsShare

- Mount the share into place
sudo mount -t smbfs \\WINDOWSBOX\Share /media/WindowsShare -o username=your_username,password=your_passwd,fmask=0644,dmask=0755

NOTE: If your username or share has SPACES type it this way

... "\\WINDOWSBOX\My Share" "/media/Windows Share" ... -o username="user name", ...

To mount the shares of your Windows box on system startup you need to create the necessary lines in /etc/fstab - example:

sudo gedit /etc/fstab

At the end of the file attach ...

\\WINDOWSBOX\Share   /media/WindowsShare   smbfs  username=your_username,password=your_passwd,fmask=0644,dmask=0755   0 0

Save the file.

Make sure the mountpoint(s) EXIST - then do a...

sudo mount -a

...to mount the shares you just added to fstab without rebooting.

-Storm

---

### Post by Stormbringer on 2006-08-04
> **stig said:**
> But I cannot access the ubuntu folders from Windows. In Network Neighbourhood I get icons for the ubuntu boxes but when I try to click them open it always asks me for a password. I get:
“Enter Network Password” “You must supply a password...” “Resource: \\UBUNTU2\IPC$”

There seems to be a problem with the **I**nter**P**rocess **C**ommunication...


My home network is similar to yours ... 2 PCs (1x Ubuntu, 1x Windoze) behind a NAT hardware firewalling router (Symantec VPN 100) connected to cable.

If possible try to reconfigure your router so that all of your internal PCs get the same IP address by DHCP every time ... look out for a config option called "DHCP reservation" or such. If you tell me the make and model of your router I may be able to see if there's a manual online to assist you.

But ... back to your problem ...

The error message says IPC$ (that's the administrative "share" for the interprocess communication) on UBUNTU2 cannot be reached.

As you have set WINS to no it's no real wonder as the host cannot be reached by name (there no instance that's running a name-to-address resolver).

On Windows, open the Command-Prompt (START -> "Accessories") and try to mount the share by hand:

net use z: \\192.168.0.10\Share password /user:username /persistent:no

You need to replace the ip-address with the one of Ubuntu2 (ifconfig inside a terminal); and you may also need to tweak the driver-letter, password and username.

If it works out that way: well ... think about the suggestion I made at the beginning of this post; you won't be able to "call" the Linux-boxes by name for as long as WINS is disabled.

If it doesn't work out:

- Check if your Windows box is running a firewall (or some other protective software) that is blocking the network traffic.
- Check if your router might block the traffic.

No matter what, please report back.

-Storm

---

### Post by stig on 2006-08-04
> **Stormbringer said:**
> If possible try to reconfigure your router so that all of your internal PCs get the same IP address by DHCP every time ... look out for a config option called "DHCP reservation" or such. If you tell me the make and model of your router I may be able to see if there's a manual online to assist you.

Thanks for the quick reply! I am using a Speedtouch 510 router but it is supplied as part of my broadband package by my ISP. The configuration is protected by a password and I would have to go through the ISP (who have the password) to get any changes made or to find out any config details.

> 
On Windows, open the Command-Prompt (START -> "Accessories") and try to mount the share by hand:

net use z: \\192.168.0.10\Share password /user:username /persistent:no

You need to replace the ip-address with the one of Ubuntu2 (ifconfig inside a terminal); and you may also need to tweak the driver-letter, password and username.


I tried this but it said it did not recognise the username (which was the relevant one for the ubuntu box whose IP I entered, and using my ubuntu/samba password). I have Zonealarm butswitching it off does not help.

In the past, with a quite different set-up, I have managed to access shared folders on my ubuntu PC from the Windows PC. (But I had problems with copying files across which is why I had to give up that method and look for another). So it is possible for my Windows to access the Ubuntu PC - but not at present!

EDIT: I should have added that my primary objective was to get the Ubuntu PCs networked because I want to convert completely to Ubuntu very soon - and your howto has achieved that very smoothly and rapidly for me. Perhaps I am unusual in that I originally had less trouble getting Wndows networked to Ubuntu, than I did linking Ubuntu to Ububtu! So my motivation to change the DHCP settings is less because the Ubuntu networking is now going well.

---

### Post by Stormbringer on 2006-08-04
> **stig said:**
> Thanks for the quick reply! I am using a Speedtouch 510 router but it is supplied as part of my broadband package by my ISP. The configuration is protected by a password and I would have to go through the ISP (who have the password) to get any changes made or to find out any config details.

Isn't the SpeedTouch 510 a DSL router ?!? O_o

However, you are right - with this device you cannot change it's configuration as it has been made up by your ISP.

> **stig said:**
> I tried this but it said it did not recognise the username (which was the relevant one for the ubuntu box whose IP I entered, and using my ubuntu/samba password). I have Zonealarm butswitching it off does not help.

OK, so let us "debug" the problem ...

- You are able to connect from UBUNTU1 to UBUNTU2 and vice versa. 
- You are NOT able to connect from Windows to UBUNTU1 by using the very same username/password credentials you used before?
- You are NOT able to connect from Windows to UBUNTU2 by using the very same username/password credentials you used before?

What about the other way? Are you able to gain access TO Windows from UBUNTU1 and/or UBUNTU2? (sorry if you already answered or mentioned that before; I'm somewhat lost in the posts).

If you can't connect from UBUNTU1 or 2 TO Windows, then it's definitely Windows causing the issue. In this case I'm rather out of ideas ... as troubleshooting Windows is way too dependend on what software is installed.

However, I would advise you to switch your Firewall as ZoneAlarm isn't exactly known to work and operate flawlessly (same goes for Symantec's Internet Security / Firewall). Simply Google the web for "Personal Firewall Review" and read through some reviews to get the picture.

---

### Post by andho on 2006-08-04
hey thanx man
so i dont even need samba to access the windows shares eh?
was it done by lisa?

ur explanations are great, real easy to follow. u rock

---

### Post by Stormbringer on 2006-08-04
> **andho said:**
> hey thanx man
so i dont even need samba to access the windows shares eh?

If you ONLY want to access a Windows-Share FROM your Ubuntu box you don't need samba at all, you only need "smbfs" installed in order to mount the share.

You ONLY need samba if you like to access a share on your Ubuntu box FROM Windows.


> **andho said:**
> was it done by lisa?

Huh?

> **andho said:**
> ur explanations are great, real easy to follow. u rock

Thanks for the cheers.

-Storm

---

### Post by RadioHam on 2006-08-04
Hi Storm,

Just wanted to say thanks. I have played with Linux (mostly RH) at home for years trying to use as a server for my home network with Samba for file sharing and it never worked fully. Getting it to work reliably was always a problem.

Some one recently gave me a ubuntu cdrom for 5.1 and I am amazed how easy it was to install on a Dell laptop with a PCMCIA network connection.

But that was nothing compared to when I found your HOWTO and after printing the first pages, followed the steps inserting my specifics (username etc ) enabling WINS and blow me down. It worked first time. I have Samba up and running providing shares for my XP desktop with no problems. I am really impressed. I have moved the shares from my server running WinNT Desktop to the laptop so sure I am that it is stable.

Well done Storm, I can't tell you how impressed I have been reading this HOWTO and the hard work that you have done to help newbies like me. You are to be congratulated.

So now  to the questions.

1: Is it necessary to add the 'sudo useadd and smbpasswd lines into the smb.conf file for each time so that they are there if the server is rebooted?

2: Can you please explain the printing = CUPS and printcap name = CUPS for me? Is this the name of your printserver? 

Thanks in Advance.
RadioHam:D :

---

### Post by stig on 2006-08-05
I've edited this post a couple of times to clarify it (see sections in EDIT tags).

> **Stormbringer said:**
> Isn't the SpeedTouch 510 a DSL router ?!? O_o

However, you are right - with this device you cannot change it's configuration as it has been made up by your ISP.

Yes, it is a DSL - sorry if I didn't mention that (does it make an important difference to what we have discussed?). I have emailed the ISP to ask them if they can tell me how to set the router to either DHCP with fixed lease or static IP addresses instead.

> 
OK, so let us "debug" the problem ...
- You are able to connect from UBUNTU1 to UBUNTU2 and vice versa.

Yes 

> - You are NOT able to connect from Windows to UBUNTU1 by using the very same username/password credentials you used before?
- You are NOT able to connect from Windows to UBUNTU2 by using the very same username/password credentials you used before?

EDIT: Correct. I can see the icons for the Ubuntu PCs in Network Neighbourhood but I cannot access them because it does not accept any combination of my samba/ubuntu username and password or username and no password.

Also I could not connect using the command you gave:
net use z: \\192.168.0.10\Share password /user:username /persistent:no
using the username and password together with the IP address found for the ubuntu PC at the time. But I was a bit unsure about the command you gave:
net use z: \\192.168.0.10\Share password /user:username /persistent:no

because you said I might have to "tweak the driver-letter, password and username". I put in "z" as you have in the line - is that the drive letter? Also, I left "persistent:no" as you have it, assuming I didn't need to change anything in that./EDIT

> What about the other way? Are you able to gain access TO Windows from UBUNTU1 and/or UBUNTU2? (sorry if you already answered or mentioned that before; I'm somewhat lost in the posts).

Yes - this works OK.
EDIT: I noticed your reply to Ando saying:
> If you ONLY want to access a Windows-Share FROM your Ubuntu box you don't need samba at all, you only need "smbfs" installed in order to mount the share. You ONLY need samba if you like to access a share on your Ubuntu box FROM Windows.
So I suppose I am accessing my Windows because of smbfs and the fault is with Samba in the other direction./EDIT

> However, I would advise you to switch your Firewall as ZoneAlarm isn't exactly known to work and operate flawlessly (same goes for Symantec's Internet Security / Firewall). Simply Google the web for "Personal Firewall Review" and read through some reviews to get the picture.

I can switch the firewall off and it doesn't make any difference.

Thanks for all the help - even if I don't get the last step (access to Ubuntu from Windows)  you will have given me 95% of what I need now (and 100% of what I'll need soon when I get completely migrated to Ubuntu!)

---

### Post by Stormbringer on 2006-08-06
> **RadioHam said:**
> So now  to the questions.

1: Is it necessary to add the 'sudo useadd and smbpasswd lines into the smb.conf file for each time so that they are there if the server is rebooted?

Huh? The "sudo useradd <username>" and "smbpasswd <options> <username>" command are to be typed into the terminal (command line) ... they are NOT supposed to written into smb.conf

Please re-read the HOWTO ... you surely misunderstood a part of it.

> **RadioHam said:**
> 2: Can you please explain the printing = CUPS and printcap name = CUPS for me? Is this the name of your printserver?

Nope - it's NOT the name of a printserver.

The parameter tells samba which PRINT SPOOLING software is to be used ... and CUPS (Common UN*X Printing System) is the default print spooler used in Ubuntu.

So, the lines tell samba the your print-spooler is in fact CUPS.

-Storm

---

### Post by Stormbringer on 2006-08-06
> **stig said:**
> Yes, it is a DSL - sorry if I didn't mention that (does it make an important difference to what we have discussed?). I have emailed the ISP to ask them if they can tell me how to set the router to either DHCP with fixed lease or static IP addresses instead.

The only difference is as follows...

On cable you would have to buy your own broadband (firewalling) router --- something like a Netgear RP613 series or similar.

In this case you would have access to the administrative interface of the router to configure things.

> **stig said:**
> EDIT: Correct. I can see the icons for the Ubuntu PCs in Network Neighbourhood but I cannot access them because it does not accept any combination of my samba/ubuntu username and password or username and no password.

So far at least the master browser is recognized by Windows.

This is nice, but it does not solve the fact that the $IPC connection gets refused for some reason.

> **stig said:**
> Also I could not connect using the command you gave:
net use z: \\192.168.0.10\Share password /user:username /persistent:no
using the username and password together with the IP address found for the ubuntu PC at the time. But I was a bit unsure about the command you gave:
net use z: \\192.168.0.10\Share password /user:username 

because you said I might have to "tweak the driver-letter, password and username". I put in "z" as you have in the line - is that the drive letter? Also, I left "persistent:no" as you have it, assuming I didn't need to change anything in that./EDIT/persistent:no

If you wrote "z" instead of "z:" it will not work out for sure - but I assume you did it the right way.

Tweaking the driveletter means that you should use a letter that's not occupied by any other drive - so if "Z:" isn't assigned to any device on your system it's fine.

> **stig said:**
> EDIT: I noticed your reply to Ando saying: <snip>

So I suppose I am accessing my Windows because of smbfs and the fault is with Samba in the other direction./EDIT

If you connect FROM Ubuntu TO Windows you're using smbfs.
If you connect FROM Windows to Ubuntu you're dealing with samba.
If you connect FROM Ubuntu to Ubuntu you're dealing with samba on both sides (1x smbfs on the client, 1x samba on the target workstation which will either be Ubuntu1 or Ubuntu2 depending on the direction).

> **stig said:**
> I can switch the firewall off and it doesn't make any difference.

As you're able to connect and transfer files between your Linux boxes I'm next to absolutely sure that the issue is caused by Windows; otherwise you would have similar issues by connecting from Linux to Linux as well.

> **stig said:**
> Thanks for all the help - even if I don't get the last step (access to Ubuntu from Windows)  you will have given me 95% of what I need now (and 100% of what I'll need soon when I get completely migrated to Ubuntu!)

In case you're able to create an image of your Windows box by using a program like partimage or Symantec Ghost (creates a snapshot of the currently installed system that can be restored upon need - you have to create the image on i.e. an external hard drive with sufficient space!):

Create a snapshot image of your current installation and as soon as you're done try to install a fresh plain copy of Windows (+Service Pack 2) just to see if it works out ... if it does you would know that the actual installation is causing the issue.

Then you could proceed onwards until it breaks again to find out what interferes with the network setup.

Anyway, glad I could be helpful.

-Storm

---

### Post by RadioHam on 2006-08-06
Cheers Storm,

Newbie on steep learning curve! Have Samba working so now on to Printing and email serving next!!!

Thanks for the great HOWTO on Samba.

---

### Post by trevorv on 2006-08-06
Hey, thanks for the great guide.

I have Ubuntu on my Thinkpad, which I can now access from my Windows box, but only connecting directly, by typing the IP. If I just double-click on the icon in Windows I get the error; 

\\Trevorv-thinkpad is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

If I try and connect to the Thinkpad from the Thinkpad (over the network), it gives

The folder contents could not be displayed.

Sorry, couldn't display all the contents of "Windows Network: mshome".

When trying to display the workgroup, but again I can connect if I go via "Connect to server" then I'm in.

So, it works, but not properly. Any ideas?

Cheers!

---

### Post by Kodiak3000 on 2006-08-06
Stormbringer - thanks for this great guide.  Everything went smoothly until I got to mapping the network drive.  I chose "U" ;)  then typed in the \\Ubuntu\MyFiles (Ubuntu is the name of the machine) and got a request for user name and password!  Hurray!

But then when I typed in my user name and password, it just kept returning the same dialog, requesting user name and password.

Any idea what I'm doing wrong? :-k 

Thanks.

---

### Post by patman on 2006-08-08
Is there any chance of getting a look at your (in development) HOWTO for join a PDC? I'm getting pretty frustrated just trying to join the domain from my windows box.  

The shares work ok, but when I try to join the domain I get a 
dialog box (on the windows system) that says "access is denied".  

And... thanks for the great HOWTO  and your willingness to be so helpful.  

Pat

---

### Post by stevewabc on 2006-08-08
:confused: OK I have lost it! [-o< 

Help please this is what im after here then I hope you all will be able to get me up and running.
file severver with samba
and 4 other computers running XP
Now I want to have all the computers to use /home/office as the main hardrive and each user can only access the files in witch I alow.

But for now I can even get my laptop to conect to the server I can ping it and the sever can ping the laptop, I even see homefront under maping lol but can connect to it. here is my samba config. and smbaclient

 [global]
    ; General server settings
    netbios name = homefront
    server string =
    workgroup = homefront
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = steve
    force group = steve
__________________________________________________________________

root@homefront:~# smbclient -L localhost -U%
Domain=[HOMEFRONT] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      
        MyFiles         Disk      
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[HOMEFRONT] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        HOMEFRONT            
        LAPTOP               homefront

        Workgroup            Master
        ---------            -------
        HOMEFRONT            HOMEFRONT

__________________________________________________________________

What im I doing rong?

when I try maping im doing it like this:
Drive: H
Folder: \\home\samba
I get network name is not available
ok so next:
Folder: \\111.111.11.111\home\samba
now I get a login screen 
user name: steve
Password 

and that doesnt work eather 

grrrrr

---

### Post by Fraoch on 2006-08-08
Stormbringer, or anyone who knows - stupid question alert!

Isn't Samba pre-configured in a default Ubuntu 6.06 install?

The reason I ask is because this is the first I've seen of this guide and Samba seems to be kinda-sorta working.

I say kinda-sorta because I can see my Windows shares and my Windows shares can see my Ubuntu share, but it's S-L-O-W (often erroring out before I can see anything) and I can't transfer files of more than a few kB, that's if I can see them at all.

There seem to be 30 second pauses each step of the way and file transfers on the Windows side terminate with a "The network name cannot be found" and on the Ubuntu side with a timeout error, that strangely times out instantaneously if I hit retry.

So should I try these directions first or is Samba already running?

Thanks!

Edit: there could be something more than this going on, several network devices don't really respond to my Ubuntu machine:

- [SlimServer]("http://www.slimdevices.com/su_downloads.html") on my Windows machine
- my Linksys WRT54G router running DD-WRT
- my new [SmoothWall]("http://www.smoothwall.org") box

All these load the title of the page and the custom web page icon, but not much else.  SlimServer loads a few lines of text after several minutes, the others don't load anything.

Interestingly my DSL modem works fine.  This seems to point to the router being the cause, but everything looks good there as far as I can tell, and Windows LAN performance is much, much better especially for the networked devices.  It's not perfect though, it often takes a long time to call up the share, and every once in a while it can't find the share, but once it's up, speed is fine.

---

### Post by Stormbringer on 2006-08-08
> **Kodiak3000 said:**
> But then when I typed in my user name and password, it just kept returning the same dialog, requesting user name and password.

Any idea what I'm doing wrong? :-k 

Thanks.

Did you enable the accounts right after adding them (smbpasswd -e <username>)?

The returning dialog at least looks like it's the problem.

[@all]
Sorry for the late replies ... was kinda busy and somehow I didn't get notifications --- really sorry.
[/@all]

---

### Post by Stormbringer on 2006-08-08
> **trevorv said:**
> I have Ubuntu on my Thinkpad, which I can now access from my Windows box, but only connecting directly, by typing the IP. If I just double-click on the icon in Windows I get the error; <snip>

Did you enable WINS in samba and add the IP of your Linux box in the WINS server field inside the TCP/IP properties of Windows?

If yes, make sure your Linux system is booted before you boot your Windows box, otherwise Windows will fail to access the master browser list.

Seems to be related somewhere around these settings as you're able to connect by using the IP.

-Storm

---

### Post by Stormbringer on 2006-08-08
> **patman said:**
> Is there any chance of getting a look at your (in development) HOWTO for join a PDC?

Well ... if you don't mind digging yourself through 12 losely connected DIN A4 pages; sure. But there are still several holes that need to be filled and a lot of work required to get it fully written.

[QUOTE=patman;1352513]I'm getting pretty frustrated just trying to join the domain from my windows box.

The shares work ok, but when I try to join the domain I get a 
dialog box (on the windows system) that says "access is denied".  

And... thanks for the great HOWTO  and your willingness to be so helpful.

This sounds as you haven't added and enabled root to samba or forgot to put a "Administrator = root" into username map.

In order to join the Domain you need to authenticate yourself as Administrator --- you cannot join by using the user credentials.

Mind to tell me a little more on the setup ... ? ... maybe we get it solved.

-Storm

---

### Post by Stormbringer on 2006-08-08
> **stevewabc said:**
> What im I doing rong?

Let's try to find out ... at first sight the configuration as well as the output you attached to your post looks fine from my point of view.

> **stevewabc said:**
> when I try maping im doing it like this:
Drive: H
Folder: \\home\samba

Your computer is called "homefront", so ...

\\homefront\samba

... would be more accurate and might cut it.

But, as you said it even doesn't work by using the ip ...

Is there any error message or does the authentication just fail?

-Storm

---

### Post by Stormbringer on 2006-08-08
> **Fraoch said:**
> Stormbringer, or anyone who knows - stupid question alert!

Isn't Samba pre-configured in a default Ubuntu 6.06 install?

So should I try these directions first or is Samba already running?

Nope --- samba isn't installed by default, and the smb.conf that will be installed together with samba is a mere template; not really fit for any use.

Be invited to follow the HOWTO and give it a try ...

> **Fraoch said:**
> The reason I ask is because this is the first I've seen of this guide and Samba seems to be kinda-sorta working.

I say kinda-sorta because I can see my Windows shares and my Windows shares can see my Ubuntu share, but it's S-L-O-W (often erroring out before I can see anything) and I can't transfer files of more than a few kB, that's if I can see them at all.

Well, I have some strange network issues with samba myself I cannot exactly work out ...

If I copy a large file, let's say 100MB+, from Windows to Linux it thunders through the network cabling with 20MB/sec+ (Gigabit). It even works that way if I copy back the file from Windows.

If I copy the same file back from Linux to Windows by smbfs it snails away with a few hundred KB up to ~5MB/sec at best.

However, so far I only get connection aborts if I try to transfer a file that is larger than 2048MB (i.e. DVD image) from Linux to Windows by using smbfs ... it freaks out as soon as the copy progresses through the aforementioned threshold.

> **Fraoch said:**
> There seem to be 30 second pauses each step of the way and file transfers on the Windows side terminate with a "The network name cannot be found" and on the Ubuntu side with a timeout error, that strangely times out instantaneously if I hit retry.

Hmm ... this rather sounds like a issue on the physical network ...

> **Fraoch said:**
> Edit: there could be something more than this going on, several network devices don't really respond to my Ubuntu machine:

- [SlimServer]("http://www.slimdevices.com/su_downloads.html") on my Windows machine
- my Linksys WRT54G router running DD-WRT
- my new [SmoothWall]("http://www.smoothwall.org") box

All these load the title of the page and the custom web page icon, but not much else.  SlimServer loads a few lines of text after several minutes, the others don't load anything.

Interestingly my DSL modem works fine.  This seems to point to the router being the cause, but everything looks good there as far as I can tell, and Windows LAN performance is much, much better especially for the networked devices.  It's not perfect though, it often takes a long time to call up the share, and every once in a while it can't find the share, but once it's up, speed is fine.

As you seem to have done a little troubleshooting on your network it looks as the router is causing you the trouble ... and in this case I assume your router is the ShoreWall box.

On this point I'm unable to help you as I don't know ShoreWall at all ... but there are a lot of resources about it around on the net.

-Storm

---

### Post by hotch on 2006-08-08
I greatly appreciate the How To on setting up Samba with Windows. I followed it and it worked. I have two Windows computers networked peer to peer through a router, and have added a Ubuntu laptop. I can now access the Ubuntu computer from my Windows one via the Network Neighborhood. Mapping the laptop as a drive does not work because Windows XP does not appreciate a mapped drive when the computer it represents is not turned on. 

The problem now runs the other way. I cannot access the Windows computers and their shared folders or files from the Ubuntu one. Under Places, Network Servers, the network is there and the various computers are there. When I try to access any of the computers in the workgroup, I get a notice such as this one:

"The filename "BOB" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

"Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

Since this happens even when trying to access the Ubuntu computer shared file from the network file browser (after all, it is there), I get the feeling that the problem is in Ubuntu and not in Windows. What went wrong and what do I do about it?

---

### Post by hydroboy on 2006-08-08
Great thread.  Thanks all.

---

### Post by Fraoch on 2006-08-08
Dangit, well although the procedure in this thread worked perfectly (no errors), my networking problems persist.

Both Windows PCs behave the same.  The Samba share appears right away, with "Shared Printers" and "My Files" folders.  The "My Files" folder contains the folder you had me define in the conf file.

I can copy files off my Ubuntu machine no problem at all.  Maximum speed.  I can even delete files off my Ubuntu machine from both Windows PCs as if it was a local drive.  However I just cannot copy a file onto the Ubuntu machine.  I get a long pause and "The network resource is unavailable" error.

The Ubuntu machine can barely see the Windows shares much less do anything to them - read or write usually result in timeouts.

It's like the Windows machines have write-not-read permissions and the Ubuntu machine has view-only permission.  That's not the case though, and some of the other permissions act like they're trying to work.

It seems to be one of those nebulous general networking issues that's OS independent.  I had high hopes that defining a WINS server would solve the issue as it appears to me like some sort of network locator isn't running properly, but that isn't it.  My attention is now focused on NetBIOS but that seems to be running too.

Thanks for the great how-to though.  Your instructions worked perfectly.  It's something else that's causing me grief!

---

### Post by isharra on 2006-08-09
> **stig said:**
> I have two Ubuntu 6.06 PCs and one Windows 98 behind a broadband NAT router, connected by cable and using DHCP.

I haven't seen a resolution so forgive me if you've already fixed it.

Does the problem go away if you change from "security = user" to "security=share"?

It's been several years since I dealt with Win9x but if I recall correctly 9x only supported share security in a workgroup. You had to be logged in to a domain (nt authentication) to use user security. To do that would mean setting up one of the ubuntu machines as a PDC and that's beyond the scope of this thread.

IPC$ (inter process communication) errors are usually authentication or capability errors (wrong password, wrong encryption or wrong security type.)

I seem to remember having to set "encrypt passwords = true" in the [global] section of smb.conf but thay may have changed.

If neither of the above works, then make try again using an account with a  password on the win98 machine. Null passwords required a working guest account. (I'm unsure if one is set up by the ubuntu installation, nobody used to be the default)

---

### Post by raja on 2006-08-09
Looks like a great and detailed post, Stormbringer. I have one more of those 'stupid' questions for you. Does this work the same way for setting up file sharing between Ubuntu on my laptop and windows XP running on vmware? And would it work with a NAT network when both the ubuntu (host) and xp (guest)will have the same IP or will I need different IP addresses?
Thanks

---

### Post by Stormbringer on 2006-08-09
> **hotch said:**
> I greatly appreciate the How To on setting up Samba with Windows. I followed it and it worked. I have two Windows computers networked peer to peer through a router, and have added a Ubuntu laptop. I can now access the Ubuntu computer from my Windows one via the Network Neighborhood. Mapping the laptop as a drive does not work because Windows XP does not appreciate a mapped drive when the computer it represents is not turned on.

That's right --- if the computer to which the network drive is mapped isn't powered up the drive is marked with a red "X" in "My Computer".

However, as soon as you boot up your lappy you simply need to click the mapped drive and the connection will be restored.

That's how it usually works by design ... just in case you wonder.

> **hotch said:**
> The problem now runs the other way. I cannot access the Windows computers and their shared folders or files from the Ubuntu one. Under Places, Network Servers, the network is there and the various computers are there. When I try to access any of the computers in the workgroup, I get a notice such as this one:

"The filename "BOB" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

"Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

Since this happens even when trying to access the Ubuntu computer shared file from the network file browser (after all, it is there), I get the feeling that the problem is in Ubuntu and not in Windows. What went wrong and what do I do about it?

Well, if you try to access a Windows-Share FROM Ubuntu (no matter is you use Nautilus's "Connect to server" or manual mount by smbfs) it has NOTHING to do with samba as samba IS ONLY REQUIRED TO GAIN ACCESS **FROM** WINDOWS (<-- no shouting, just to trigger attention).

So, at the best there's something square with Gnome's VFS that gets used when connecting to Windows from Nautilus.

Why not trying to install smbfs and give it a shot on the commandline?

Open a terminal and type ...

sudo apt-get install smbfs

...and try to mount the share ...

sudo mount -t smbfs //SERVER/Share /media/mountpoint -o username=windows_username,password=windows_password,fmask=0666,dmask=0777,iocharset=utf8

Note: You eventually need to create the directory under /media to which you mount the share ... sudo mkdir /media/mountpoint

If it works out you have confirmation that's something wrong with Gnome and/or it's VFS.

As the connection from Linux to Windows isn't related to samba I'm not really able to assist you in troubleshooting Gnome (order KDE or whatever flavor of Ubuntu you may using).

-Storm

---

### Post by Stormbringer on 2006-08-09
> **Fraoch said:**
> Dangit, well although the procedure in this thread worked perfectly (no errors), my networking problems persist.

Both Windows PCs behave the same.  The Samba share appears right away, with "Shared Printers" and "My Files" folders.  The "My Files" folder contains the folder you had me define in the conf file.

I can copy files off my Ubuntu machine no problem at all.  Maximum speed.  I can even delete files off my Ubuntu machine from both Windows PCs as if it was a local drive.  However I just cannot copy a file onto the Ubuntu machine.  I get a long pause and "The network resource is unavailable" error.

The Ubuntu machine can barely see the Windows shares much less do anything to them - read or write usually result in timeouts.

It's like the Windows machines have write-not-read permissions and the Ubuntu machine has view-only permission.  That's not the case though, and some of the other permissions act like they're trying to work.

It seems to be one of those nebulous general networking issues that's OS independent.  I had high hopes that defining a WINS server would solve the issue as it appears to me like some sort of network locator isn't running properly, but that isn't it.  My attention is now focused on NetBIOS but that seems to be running too.

Thanks for the great how-to though.  Your instructions worked perfectly.  It's something else that's causing me grief!

Check if the "My Files" folder on Ubuntu has the appropriate rights. Issue a ...

ls -lisa /media/MyFiles

... and look out for the columns showing your the access modes, the owner and the group.

If the permissions don't look like drwxrwxrwx you forgot to issue "sudo chmod 0777 /media/MyFiles".

If the owner and group IS NOT your username you forgot to issue "sudo chown your_username:your_username /media/MyFiles"

If there's something wrong with the permissions you won't be able to copy onto the share from Windows; but it should give a message like "You don't have the appropiate permissions blah blah" instead of a networking error.

Just give it a try and remember to correct paths to match your setup.

-Storm

---

### Post by Stormbringer on 2006-08-09
> **isharra said:**
> I haven't seen a resolution so forgive me if you've already fixed it.

Does the problem go away if you change from "security = user" to "security=share"?

It's been several years since I dealt with Win9x but if I recall correctly 9x only supported share security in a workgroup. You had to be logged in to a domain (nt authentication) to use user security. To do that would mean setting up one of the ubuntu machines as a PDC and that's beyond the scope of this thread.

IPC$ (inter process communication) errors are usually authentication or capability errors (wrong password, wrong encryption or wrong security type.)

I seem to remember having to set "encrypt passwords = true" in the [global] section of smb.conf but thay may have changed.

If neither of the above works, then make try again using an account with a  password on the win98 machine. Null passwords required a working guest account. (I'm unsure if one is set up by the ubuntu installation, nobody used to be the default)

If you run Win95/98/Me the example configuration of samba in the HOWTO isn't suitable.

However, as the aforementioned operating systems aren't any longer supported by Microsoft you're better off switching to a more recent OS (i.e. Windows XP) if your Computer is capable of running it.

-Storm

---

### Post by Stormbringer on 2006-08-09
> **raja said:**
> Looks like a great and detailed post, Stormbringer. I have one more of those 'stupid' questions for you. Does this work the same way for setting up file sharing between Ubuntu on my laptop and windows XP running on vmware? And would it work with a NAT network when both the ubuntu (host) and xp (guest)will have the same IP or will I need different IP addresses?
Thanks

Should work fine with the VMware setup ... no idea about the NAT though.

I run VMware Server on my box, and inside of the "emulated" Windows XP I'm able to access the shares of samba running on the same box; difference is that I'm using bridged networking (the NAT to the outside world is done by my hardware router).

-Storm

---

### Post by stig on 2006-08-09
> **Stormbringer said:**
> If you run Win95/98/Me the example configuration of samba in the HOWTO isn't suitable.

However, as the aforementioned operating systems aren't any longer supported by Microsoft you're better off switching to a more recent OS (i.e. Windows XP) if your Computer is capable of running it.

-Storm

First, in answer to Isharra, I seem to have everything working except accessing my Ubuntu shares from the Windows 98 box - but there is a possible complication becasue I'm using DHCP. I'm going to try setting static IP addresses and see if that gets me anywhere. But as I mentioned in previous posts, I will soon switch completely to Ubuntu, so the motivation is low! (And as Stormbringer points out, Win98 is no longer supported by MS - or people like ZoneAlarm.)

Second, Stormbringer, in what way is your example config in the Howto not suitable for Win98?

---

### Post by Stormbringer on 2006-08-09
> **stig said:**
> (And as Stormbringer points out, Win98 is no longer supported by MS - or people like ZoneAlarm.)

I have no idea on how to interprete the line, but: Face the facts ... 9x/Me is discontinued ... and not only since yesterday's patchday.

> **stig said:**
> Second, Stormbringer, in what way is your example config in the Howto not suitable for Win98?

As Isshara already pointed out:

- Win9x/Me seems to have issues with security=user (security=share should work out, but it isn't tested by me as I don't have any ancient Windows's to my avail anymore)
- Win9x/Me isn't really able to handle encrypted smb connections (this option isn't used here and defaults to unencrypted).
- In order to join into a domain (samba in PDC mode instead of stand-alone) you need to tweak some parameters to make it happen; not really sure if the parameters would also be needed in the stand-alone peer-to-peer setup).

Just take a look through the man-page or html documentation of samba and look out for remarks regarding Windows 9x ... there are some.

So, although I would really like to help in resolving Win9x/Me related issues I simply can't as I never used them (my way through Windows hell consisted of: Win3.xx -> NT 3.5x -> NT4 -> W2K -> WXP) and don't have them to my avail in order to setup a test-environment in VMware.

-Storm

---

### Post by jdriessen on 2006-08-09
thankyou thankyou thankyou for this guide!!

this is the first guide that cleanly with no fuss sets up my windows installation to share files with ubuntu

this is great!

---

### Post by stevewabc on 2006-08-09
ok thanks to this form my file sharing is up but my Print server is XXXX. ok This server has no gui, so to configure the printers im typing under root lynx 127.0.0.1:631/Administration/ and it shows new printer HP895C and my laserJet5 so I tab down to Add this Print
hit enter, it list the printer drivers its going to load all looks good so I tab to Add Printer,   then I get not Authorized grrr then it asks for user name for cups so I tried everything and always get  Authorization Failed.. 

this is cups 1.2.2
Please help do I need to down grade cups is it a bug? my hole damn office has no printers now ](*,)

---

### Post by Fraoch on 2006-08-09
> **Stormbringer said:**
> Check if the "My Files" folder on Ubuntu has the appropriate rights. Issue a ...

ls -lisa /media/MyFiles

... and look out for the columns showing your the access modes, the owner and the group.

If the permissions don't look like drwxrwxrwx you forgot to issue "sudo chmod 0777 /media/MyFiles".

If the owner and group IS NOT your username you forgot to issue "sudo chown your_username:your_username /media/MyFiles"

If there's something wrong with the permissions you won't be able to copy onto the share from Windows; but it should give a message like "You don't have the appropiate permissions blah blah" instead of a networking error.

Just give it a try and remember to correct paths to match your setup.

-Storm

Actually Stormbringer, there's no need.  I've pinpointed the problem.

I was using a [Slim Devices Squeezebox]("http://www.slimdevices.com") as a wireless bridge.

When I wire the Ubuntu PC into my router directly, file sharing works as expected: from/to the Ubuntu machine, internal LAN webpages, everything.

This points the finger at the Squeezebox - even though Internet access was fine (I downloaded the Ubuntu updates at 315 kB/s, close to my Internet saturation speed of ~330 kB/s) it's somehow mangling filesharing bits.

The good news is this is all in firmware and the company is very responsive.

Even more good news is, of course, that Samba's working perfectly thanks to your guide.  Thanks again!

---

### Post by whatrucrazy on 2006-08-09
firstly thanks heaps stormbringer for the how-to but esp for the effort at anwering peoples questions, really appreciated by all!

ok, 3 questions.

1- does using samba effect the overall security of my ubuntu box? i'm not worried about accessing my windoze box from ubuntu (i know its not using samba), but it does concern me that an unsecure system like windoze can access my (hopefully) locked down ubuntu box. somehow is _worrying_. should i be concerned? if someone hacks the windoze box is my ubuntu system then an easy target, even if i have locked down permissions as best as i can??

2- does the 'Share folder' option in nautilus have anything to do with using samba, or is this a linux-linux, or user-user option? I had thought the permissions on the folder to be shared via samba just had to be set to allow access to any user, but then i noticed the nautilus option?

3- i installed firestarter, but don't initialise it at startup. this doesn't mean i don't have a firewall running though, yeah? by my understanding firestarter sets the rules and the rest just runs whenever the os is on. if this is the case, could this be why i can't get samba to run? ubuntu can read and write on the wondoze box, but the windoze cant even get any access to the ubuntu box. if that's why do i just configure firestarter to alow the windoze box's IP access?

sorry for the long post but i've been working on this for 2 days.:-k 

thanks everyone who has helped in this thread, you all rock!

---

### Post by hotch on 2006-08-10
Thanks again for the information. I had mentioned that I could access from Windows to Ubuntu, but not the other way around. Your suggestions sounded good, but then I discovered that the problem was not Ubuntu, it was me. The answer was right in front of me.

Instead of going through from the upper taskbar through Places/Network Servers, All I need to do is go from Places to Connect to Server, plug in the name of the Windows computer, and voila, there are all the shared folders in that computer. This apparently mounts that computer (or whatever) and puts an icon on the desktop.

---

### Post by ubuntu_demon on 2006-08-11
Stormbringer I linked to this HOWTO on :

READ THIS FIRST prior to posting - IMPORTANT links
[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

A suggestion : link to further documentation in your first post for example :
-official samba documentation
-wiki.ubuntu.com samba documentation

---

### Post by tonydm on 2006-08-11
It worked great!... @ first:( 

I added an additional user and something broke.  Now the drive\share I had mapped wouldn't connect.  So I deleted it (windows) and tried to remap it.  Now I cannot login/authenticate remap.

As part of the initial setup that I followed I set up this.  Mapped and logged in from my XP Mach.

[MyFiles]
    path = /home/tonydm/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tonydm
    force group = tonydm
    available = no
    public = no
    writable = no

Then added the following to the smb.conf and issued sudo smbpasswd -L -a megan and sudo smbpasswd -L -e megan.  Restarted samba.  And it broke.  Help Please.

[MegansFiles]
    path = /home/megan/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = megan
    force group = megan
    available = no
    public = no
    writable = no

[Common]
    path = /home/common
    available = yes
    browseable = yes
    public = yes
    writable = yes

---

### Post by dave2010 on 2006-08-11
I have gone through the HOWTO step by step.
Here is my problem:
I can see my ubuntu pc in winxp but when i try and access it it says that i might not have the right permissions.
Any ideas appreciated as this and network printing are the last hurdles before i totally switch over.
Cheers,
Dave.

---

### Post by jpordonez on 2006-08-12
I read all your document and it is really very usefull. I have one additional question. My principal interest is to be able, on my Linux machine to use windows workstation names instead of their IP , when trying to connect to any windows share folder. 

1) Is this samba setup enabling this ?

2) If I have more thna one Linux machine on the network what WINS ip should I enter on the Windows machine ?


Thanks for your help.

---

### Post by Punkie on 2006-08-12
All well and great. With the exception that on a standard 6.06 install there is NO SAMBA. And installing it (apt-get install samba) does not work as he complains that it is not available. ubuntu however reports that smbclient and samba-common can replace the package.

Do they replace samba? If so then how can i apply the same steps to them?
If no, then can one get to install samba from the CD? or does one need internet access? (which i dont have on the ubuntubox...)

---

### Post by Stormbringer on 2006-08-12
> **stevewabc said:**
> ok thanks to this form my file sharing is up but my Print server is XXXX. ok This server has no gui, so to configure the printers im typing under root lynx 127.0.0.1:631/Administration/ and it shows new printer HP895C and my laserJet5 so I tab down to Add this Print
hit enter, it list the printer drivers its going to load all looks good so I tab to Add Printer,   then I get not Authorized grrr then it asks for user name for cups so I tried everything and always get  Authorization Failed.. 

this is cups 1.2.2
Please help do I need to down grade cups is it a bug? my hole damn office has no printers now ](*,)

[OFFTOPIC]
So I drop by in "my" thread and there are a bunch of posts ... I really wonder why the board fails to send me the "topic reply" notifications ...
[/OFFTOPIC]

You get the error on Windows, right?

In the add printer wizard select "network" as the connection type and give the UNC path to your print server - i.e. \\SERVER\HPLJ5 (you may also browse the network).

After that Windows should ask you to provide the printer driver ...

Simply select the appropriate printer driver from the list (LaserJet 5 and/or DeskJet 895C) and let it install.

Should work out fine ... I'm running an HP LJ4M on my Ubuntu 6.06.1 LTS; the distribution is up-to-date and the print-spooling works fine when I print from Windows.

---

### Post by Stormbringer on 2006-08-12
> **whatrucrazy said:**
> ok, 3 questions.

1- does using samba effect the overall security of my ubuntu box? i'm not worried about accessing my windoze box from ubuntu (i know its not using samba), but it does concern me that an unsecure system like windoze can access my (hopefully) locked down ubuntu box. somehow is _worrying_. should i be concerned? if someone hacks the windoze box is my ubuntu system then an easy target, even if i have locked down permissions as best as i can??

As for samba: You're fine as long as you're blocking port 137, 138, 139, 445 (TCP and UDP) against access from the outside world (Internet).

If your Windows box gets pwned by a trojan or backdoor your Ubuntu box may be at risk if there's some security hole that hasn't been patched.

If you don't run things like SSH (i.e. you connect to your Ubuntu box by SSH using PuTTY with passwordless RSA-key authentication) or telnet chances are rather minimal (although I read an thread here on the forums that a box got hacked through a windows client).

> **whatrucrazy said:**
> 2- does the 'Share folder' option in nautilus have anything to do with using samba, or is this a linux-linux, or user-user option? I had thought the permissions on the folder to be shared via samba just had to be set to allow access to any user, but then i noticed the nautilus option?

As it doesn't need to samba for operation it doesn't seem to be related to samba ... although I might be at error as I haven't used that option and haven't dug myself through the tons of documentation on Gnome.

> **whatrucrazy said:**
> 3- i installed firestarter, but don't initialise it at startup. this doesn't mean i don't have a firewall running though, yeah? by my understanding firestarter sets the rules and the rest just runs whenever the os is on. if this is the case, could this be why i can't get samba to run? ubuntu can read and write on the wondoze box, but the windoze cant even get any access to the ubuntu box. if that's why do i just configure firestarter to alow the windoze box's IP access?

What's the layout of your network? Do you have 2 network cards in your linux box or do you connect through a hardware router?

A little more background would be nice to give it a thought ...

-Storm

---

### Post by Stormbringer on 2006-08-12
> **ubuntu_demon said:**
> Stormbringer I linked to this HOWTO on :

READ THIS FIRST prior to posting - IMPORTANT links
[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

A suggestion : link to further documentation in your first post for example :
-official samba documentation
-wiki.ubuntu.com samba documentation

Thanks for linking the guide into the "Important links" sticky.

Will update the first post as suggested; guess it a real good idea to link to the official samba documentation so that people are able take a look into it.

Thanks,
-Storm

---

### Post by Stormbringer on 2006-08-12
> **tonydm said:**
> It worked great!... @ first:( 

I added an additional user and something broke.  Now the drive\share I had mapped wouldn't connect.  So I deleted it (windows) and tried to remap it.  Now I cannot login/authenticate remap.

As part of the initial setup that I followed I set up this.  Mapped and logged in from my XP Mach.

[MyFiles]
    path = /home/tonydm/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tonydm
    force group = tonydm
    available = no
    public = no
    writable = no

Then added the following to the smb.conf and issued sudo smbpasswd -L -a megan and sudo smbpasswd -L -e megan.  Restarted samba.  And it broke.  Help Please.

[MegansFiles]
    path = /home/megan/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = megan
    force group = megan
    available = no
    public = no
    writable = no

[Common]
    path = /home/common
    available = yes
    browseable = yes
    public = yes
    writable = yes

Adding an user shouldn't affect samba ... two possibilities ...

1. Samba dislikes you for the typo: "writable" is spelled WRONG ... "writeable" is much more accurate. Please take a look into it and correct the parameter if you really happend to commit that typo in your smb.conf. Afterwards restart samba (sudo /etc/init.d/samba restart).

2. Shouldn't be required as we're using TDBSAM as user/password backend, but try to add the user to the system (in Gnome: "System" -> "Administration" -> "Users and Groups").

I would dare to bet the first one should fix your problem in case it is a typo.

-Storm

---

### Post by Stormbringer on 2006-08-12
> **dave2010 said:**
> I have gone through the HOWTO step by step.
Here is my problem:
I can see my ubuntu pc in winxp but when i try and access it it says that i might not have the right permissions.
Any ideas appreciated as this and network printing are the last hurdles before i totally switch over.
Cheers,
Dave.

A little more information would be great ...

I assume you followed the guide, so the authentication error could only be related to the useraccount or samba's setup.

- Did you add your useraccount to samba and enable it (the part that deals with smbpasswd -L -a <username> and smbpasswd -L -e <username>)?

If you only added the account you still need to enable it for access.


Also, check your smb.conf for possible typos in case you didn't copy/paste ... or in case you did some modifications yourself.

-Storm

---

### Post by Stormbringer on 2006-08-12
> **jpordonez said:**
> I read all your document and it is really very usefull. I have one additional question. My principal interest is to be able, on my Linux machine to use windows workstation names instead of their IP , when trying to connect to any windows share folder. 

1) Is this samba setup enabling this ?

If you enabled WINS ("wins support = yes" in smb.conf) it's samba doing the job (Name to address, and vice versa, translation).

> **jpordonez said:**
> 2) If I have more thna one Linux machine on the network what WINS ip should I enter on the Windows machine ?

Tricky question ... this depends on the setup of your network ...

If you run Ubuntu- and Windows as Workstations you can safely enable WINS on all boxes and provide all IPs to Windows - the WINS browsers will sync each other when all are up.

If you run Ubuntu as a server you're better off enabling WINS on the server only.

However, in Linux you may want to edit /etc/nsswitch.conf to enable WINS resolution between Linux boxes.

Find the line reading:

hosts: files dns mdns

and add "wins" at the end of the line to make it read:

hosts: files dns mdns wins

Now, if you connect from a Linux box to another Linux box by smb you may use the name instead of the IP as WINS will try to resolve the name-to-address (will only work if there's a WINS server up and available).

-Storm

---

### Post by Stormbringer on 2006-08-12
> **Punkie said:**
> All well and great. With the exception that on a standard 6.06 install there is NO SAMBA. And installing it (apt-get install samba) does not work as he complains that it is not available.

Samba is available for installation online...

```

stormbringer@nebuchadnezzar:~$ sudo apt-cache policy samba
samba:
  Installed: 3.0.22-1ubuntu3.1
  Candidate: 3.0.22-1ubuntu3.1
  Version table:
 *** 3.0.22-1ubuntu3.1 0
        500 http://security.ubuntu.com dapper-security/main Packages
        100 /var/lib/dpkg/status
     3.0.22-1ubuntu3 0
        500 http://archive.ubuntu.com dapper/main Packages

```

As you can see ... the package is called "samba", and it's located in the networking section of the main repository (you need internet access!).

"sudo apt-get install samba" will therefore only work if you're connected to the internet.

> **Punkie said:**
> ubuntu however reports that smbclient and samba-common can replace the package.

Do they replace samba? If so then how can i apply the same steps to them?
If no, then can one get to install samba from the CD? or does one need internet access? (which i dont have on the ubuntubox...)

"samba-client" and "samba-common" are just the CLIENT packages of samba (Gnome and some other programs need these packages in order to gain access **TO** Windows) ... samba is the SERVER part that makes it possible to gain access **TO** Linux **FROM** i.e. Windows. So - no - these packages DO NOT replace samba or stuff as they are not related to the server part ... although it would be funny if Ubuntu really wrote stuff like that somewhere hidden in the depths of the site and/or Wiki.

Oh, and as I don't have the CD at hand I'm unable to tell you if samba is available for installation from CD ... will take a look into it on Monday and edit this post.

-Storm

---

### Post by ubuntu_demon on 2006-08-13
> **Stormbringer said:**
> Thanks for linking the guide into the "Important links" sticky.

Will update the first post as suggested; guess it a real good idea to link to the official samba documentation so that people are able take a look into it.

Thanks,
-Storm
Great! Thanks for adding the stuff. I already put some other Samba links in the sticky. Please PM me if you have added some links so I might add them there too.

---

### Post by jpordonez on 2006-08-17
I have setup according to your directions and it all works fine. One additional question:

I have a website running on the Windows machine. I can access it from the linux machine using the IP, but I would like to browse it using the windows machine name instead of the IP. Is this possible ? How do I set this up ?

---

### Post by Stormbringer on 2006-08-17
> **jpordonez said:**
> I have a website running on the Windows machine. I can access it from the linux machine using the IP, but I would like to browse it using the windows machine name instead of the IP. Is this possible ? How do I set this up ?

A WEBSITE? This has nothing to do with samba ... X_X ... I hope you're aware of that fact.

Accessing the website you're running on your Windows box by name requires the installation of a DNS-server for your intranet on a server that's inside your internal network as well.

Please take a look at this HOWTO: [Howto: Setup a DNS server with bind]("http://ubuntuforums.org/showthread.php?t=236093")
It's more related to your question.

---

### Post by rc-edens on 2006-08-17
Nice HOWTO - very comprehensive. 

I neglected to check the Ubuntu forums when I was looking for Samba setup info two days ago :( but instead used a small Samba HOWTO contained within an article I ran across at TomsHardware.com. The Samba info there starts on page 8 of the article: [http://www.tomsnetworking.com/2006/08/08/diy_nas_smackdown/]("http://www.tomsnetworking.com/2006/08/08/diy_nas_smackdown/").

Although it's a small set of instructions, it was just what I needed for setting up an Ubuntu photo file server for my Windows XP Photoshop machines.

--- "RC" Edens

---

### Post by WzrdOfOost on 2006-08-18
Too bad I did not see these forum when I wsa struggeling with samba. I just cleaned the whole smb.conf and started from scratch. I blogd my struggle here [http://my-linux-server.blogspot.com](http://my-linux-server.blogspot.com)

---

### Post by ledj0 on 2006-08-21
Hello and thanks for your efforts in helping everybody.

My problem is the following: I have a server (GATEWAY) that runs Ubuntu 6.06 and that, as it's name implies, is used as a gateway to a public network. Samba runs on this server and the firewall is configured to let Netbios and Samba ports traffic allowed from private interface. Also, I have setup all Windows workstation to use WINS over TCP using to the Gateway server IP address.

My smbpasswd user list is synchonized with my Windows user names and password for all workstations and the smbpasswd users are enabled.

I have 1 laptop that runs Win2K pro, 1 workstation that runs WinXp pro and 1 workstation that runs WinXP-home. Everything works fine from my win2K workstation. Using Windows explorer, I can navigate through the workgroup to the public share on the Gateway server. When using the WinXp ones, I simply cannot get to the shares. Here is what happens:

I open Windows Explorer and navigate to my server. When I click on Gateway, I am asked by Wndows to enter a name and a password. I enter a valid name and password (ex: jacques and mysecret where they are both entered and enabled in the smbpasswd). The password screen is then redrawn asking for a name and password this time, the user field is populated with "GATEWAY\jacques". I enter again the password but no can do. The system remains in this loop forever.

I tried the net test from the XP workstations and it worked OK (net use z: \\192.168.1.1\public mysecret /user:jacques /persistent:no and the drive is mapped correctly with the correct access rights) so it seems that it is at the password exchange level that ther is a problem.

I also get that nasty password screen when I try to install a public printer on the XP workstation while I have no problen installing on the Win2K equipment.

Here is my configuration:

```
 
[global]

    workgroup = HOMELEDX
    netbios name = GATEWAY
    server string = 
    interfaces = eth1 lo
    bind interfaces only = yes

    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/usermap
    name resolve order = hosts wins bcast
    wins support = yes

    encrypt passwords = yes
   
    printing = cups
    printcap name = cups

[public]
    path = /exports/samba/public
    read only = yes
    browseable = yes
    guest ok = no
    force user = ledxadmin
    force group = users

[printers]
    comment = All printers
    path = /var/spool/samba
    guest ok = no
    printable = yes
    use client driver = yes
    browsable = no


``` Thanks in advance for your help.

ledj0

---

### Post by Stormbringer on 2006-08-22
> **ledj0 said:**
> I open Windows Explorer and navigate to my server. When I click on Gateway, I am asked by Wndows to enter a name and a password. I enter a valid name and password (ex: jacques and mysecret where they are both entered and enabled in the smbpasswd). The password screen is then redrawn asking for a name and password this time, the user field is populated with "GATEWAY\jacques". I enter again the password but no can do. The system remains in this loop forever.

You're not the only one who reported this odd behaviour in this thread - and I tried hard to reproduce the problem inside a VMware environment (Ubuntu 6.06 Server with all patches applied, Windows XP Home Edition / Professional with SP2 and all hotfixes applied) but failed so far.

To be honest ... I have no idea what the problem might be as I cannot reproduce the behaviour at all. It always works out for me (not only in the peer-to-peer setup but in a full PDC setup as well).

> **ledj0 said:**
> I tried the net test from the XP workstations and it worked OK (net use z: \\192.168.1.1\public mysecret /user:jacques /persistent:no and the drive is mapped correctly with the correct access rights) so it seems that it is at the password exchange level that ther is a problem.

That's what I think too ... something's different in the authentication; seems as Windows Explorer handles things slight different than "net" does.

> **ledj0 said:**
> I also get that nasty password screen when I try to install a public printer on the XP workstation while I have no problen installing on the Win2K equipment.

Ah ha ... so it's related to XP only ... well ... if that's the case then Server 2003 and/or XP x64 should have a similar problem as they share the same code-base (at least that's what M$ tells).

> **ledj0 said:**
> Here is my configuration:
<snip>

Looks fine to me ... no typos and no misconfiguration.

However, as you seem to run this setup on a multi-homed firewalling server ...

Mind to post the firewall-rules of iptables you configured (just clean out any public IP with xxx.xxx.xxx.xxx)?

Does the output of "smbclient -L localhost -U%" look fine or does it show any errors?

-Storm

---

### Post by ledj0 on 2006-08-22
There might have been different problems: after I posted that message, I reviewed all parameters that might influence this setup in and out Samba. I realized that I did not have Wins registration (tcp-139) and SMB/CIFS udp-445 opened. Also, I have made a change in my [public] share's force user and force group. Finally, I removed the "username map" entry as the map file did not contain anything.

I never used a Wins server in my network so this is why I overlooked the first one and the second is probably due to misreading or plain fatigue:-?   . 

I cannot tell exactly which of these change solved the problem. I will certainly try to isolate this some time but here's what I think:

- I don't think the firewall ports have caused that specific problem since things were working fine in 2k. I tend to think that it might have influenced the browsing speed. Also, I doubt very very much that the password exchange routine varry that much at the interfacing level from 2k to XP but hey...we never know with Bill's baby;).

- As you made it clear in this thread, the "force user" and "force group" parameters have nothing to do with login but deals with file ownership. This means that this parameter should not have made difference in this situation.

- This leaves the "username map" parameter. In my first post, I did not go into all details as did not want to write a novell. I said that my user configuration was checked, etc. Here are the details:

- the login name from the 2k workstation was exactly reproduced in the linux box with the exact same case (ex: abc - abc). There was a direct match from win to samba password.

-the login name from XP was the same name exept for the first character which was uppercase in win (ex Def - def). It is mentionned in some Samba books as well as in this thread that username case is converted to lowercase so I did not bother since this was exactly the case. 

However the match was not perfect and there is a "username map" parameter so (from this point, this is only speculation from my part as I did not go through Samba's sources ) Samba goes in resolution mode.  It looks at "username map" parameter and if it does not find a map there, it simply returns as if you sent an invalid name. In my opinion, removing this parameter is the key as from there, Samba will follow it's standard internal resolution algorithm.

In any case, things are (finally) working fine now. I will try to isolate exactly what fixed this and post back to this thread (after a short vacation8) ).

Big thanks again for your time and efforts, you are a champ.

ledj0

---

### Post by dkaplowitz on 2006-08-27
Great guide, Stormbringer, thanks! For some reason it was looking for a non-existent file /etc/smb/smbusers. I touched that file and it solved that error. And aside from not realizing that the workgroup name was case sensitive (I assumed it wasn't), it was a breeze to set up.

Cheers!

Dave

---

### Post by HAL98 SE on 2006-08-27
Thanks so much for this HOWTO. It worked first time. Now i can start to see how Samba works!

---

### Post by spot101 on 2006-08-28
Questions about printers in Samba.

First off thanks for the great How to. By the look of this thread it's being apprecated by lots of people.

I'd like to print using windows native drivers. (Better feature support and sometimes better quality printing)

I've done a bit of reading but I am still not clear what is required.

What changes do I need to make to smb.conf and CUPS to make this work?

I don't need to auto install drivers across the network as I have read else were. Just the bacics are needed. 


Much thanks,
Spot.

---

### Post by Stormbringer on 2006-08-28
> **spot101 said:**
> Questions about printers in Samba.

First off thanks for the great How to. By the look of this thread it's being apprecated by lots of people.

I'd like to print using windows native drivers. (Better feature support and sometimes better quality printing)

I've done a bit of reading but I am still not clear what is required.

What changes do I need to make to smb.conf and CUPS to make this work?

I don't need to auto install drivers across the network as I have read else were. Just the bacics are needed. 


Much thanks,
Spot.

If you want to hook your printer to your Ubuntu-Box and share it for the client on the LAN you need to install the Printer in CUPS first (in Gnome: "System" -> "Administration" -> "Printing") - there's no way around.

As soon as you installed your printer restart samba so that the newly added printer gets recognized for sure.

To add the printer to your Windows client you may either use the Network Neighborhood (browse to your Ubuntu Box, open the "Printers" Folder, right-click your printer and select "Connect") or the Add Printer Wizard in the Control Panel.

In both cases Windows will ask you to provide a driver for your printer in case it isn't directly supported by Windows. Install the driver and your're done.

The spool-file of Windows will be sent to Samba and forwarded to the appropriate CUPS-spool. If the job is already in the fitting native printer-language (PCL, PostScript, whatever) it will be put into the queue without further pre-processing and finally be printed.

In case the spool-file mismatches with the capabilities of the CUPS driver the job WILL be pre-processed to make it fit.

In the end it's CUPS that's handling your printer - not Windows or one of it's drivers.

If you have doubts you may also hook the printer to one of your Windows clients and setup a shared printer there ... in case the Windows-driver will output better quality.

-Storm

---

### Post by spot101 on 2006-08-29
Thanks for the ultra quick reply. I'm glad it's so straight foreward to do. I had read about having to set-up raw print queues in CUPS and wasn't sure if it needed to be that invloved. This way is automatic. Cool!!

Earlier in this thread I read about someone who needed to set-up samba for himself, his brother and father. The problem was to give read/write access to a share to himself and his brother and read only access to the father.
In my reading I came accross this and wondered if this approach would work.


> Here's another example of using variables: let's say there are five clients on your network, but one client, maya, requires a slightly different [homes] configuration. With Samba, it's simple to handle this:
[homes] 
    ...
    include = /usr/local/samba/lib/smb.conf.%m
    ...

The include option here causes a separate configuration file for each particular NetBIOS machine (%m) to be read in addition to the current file. If the hostname of the client system is maya, and if a smb.conf.maya file exists in the /usr/local/samba/lib directory, Samba will insert that configuration file into the default one. If any configuration options are restated in smb.conf.maya, those values will override any options previously encountered in that share. Note that we say "previously." If any options are restated in the main configuration file after the include option, Samba will honor those restated values for the share in which they are defined.
From Using Samba Chapter 6 [http://us2.samba.org/samba/docs/using_samba/ch06.html]("http://us2.samba.org/samba/docs/using_samba/ch06.html")

You might then be able to set the share read only for one user. i.e. the father.

Any thoughts?

Thanks again for your help.

Spot.

---

### Post by addisor on 2006-08-31
All went well to a point. The XP computer is a wireless laptop. When i got to the network mapping bit, i chose Z drive and //rob/myfiles, fails everytime with "an extended error has occured" any suggestions

---

### Post by dmizer on 2006-08-31
what is suppose to be in the /etc/samba/smbusers file?

for some reason or another, this file has been either deleted or removed without my knowledge (an update maybe?)

my logs contain the following:
```
Sep  2 01:11:53 storage smbd[21960]: [2006/09/02 01:11:53, 0] lib/username.c:map_username(139) 
Sep  2 01:11:53 storage smbd[21960]:   can't open username map /etc/samba/smbusers. Error No such file or directory 
```
i am VERY concerned about this.  both that the file can't be found, and the fact that i'm getting write_data errors.

i am still able to log in, and everything seems to be running okay ...

---

### Post by jng on 2006-09-01
New to Linux I was searching for a guide to set up Linux to work in network with Windows, and I searched through several guides to setup Samba, but I could not make it work - until I found this guide. Following your instruction it just works flawlessly.

Thank you very much for this fine guide. :D

---

### Post by INS_tha_rebel on 2006-09-01
Edit

---

### Post by dmizer on 2006-09-01
> **INS_tha_rebel said:**
> Not sure what to do next......any ideas??
yes.

instead of accessing the linux drive through network places do the following:

right click on my computer and select "mount network drive"
don't browse for the share. enter in the following for location: //linuxboxname/foldername

where linuxboxname is what you entered in smb.conf for the field: "netbios name ="
and foldername is what you entered between the brackets in smb.conf for: [MyFiles]

if that doesn't work, try the same again but click on the link that says "connect with a different username and password", and enter in your login information there.

then you should be able to see your network folder in "my computer" as well as in network places.

---

### Post by gary4gar on 2006-09-02
well real good guide!
pls keep writing this n00b stuff it hepls me a lot

---

### Post by paul.rayner on 2006-09-03
Great Howto Really helpful.

---

### Post by Bill_MI on 2006-09-03
First, thanks for the excellent HowTo!  Working first time without a reboot, as many have reported.

Configuration questions from a techy-type climbing the Linux learning curve...

1) A good friend says they use WEBMIN to configure SAMBA shares.  I've seen and tried WEBMIN, but not on this machine and not for shares.  It doesn't appear in any official or community repositories.  What drawbacks happen with WEBMIN?  Is it not easy to get for a good reason?

2) I read how SUDO and SWAT don't work very well but ROOT can be given a password to get around it ([http://ubuntuforums.org/showthread.php?t=58434&highlight=swat)](http://ubuntuforums.org/showthread.php?t=58434&highlight=swat)).  The ramifications of this are still unclear.  I'm glad I found THIS HowTo before going that direction.

Shouldn't SWAT either be packaged to work or removed as "supported"?  Am I missing a basic definition of what "supported" means?

Insight and opinions welcomed.  TIA

---

### Post by de4th on 2006-09-04
Excellent how to! Thank you very much!
It worked good :cool:

---

### Post by dmizer on 2006-09-04
> **Bill_MI said:**
> First, thanks for the excellent HowTo!  Working first time without a reboot, as many have reported.

Configuration questions from a techy-type climbing the Linux learning curve...

1) A good friend says they use WEBMIN to configure SAMBA shares.  I've seen and tried WEBMIN, but not on this machine and not for shares.  It doesn't appear in any official or community repositories.  What drawbacks happen with WEBMIN?  Is it not easy to get for a good reason?

2) I read how SUDO and SWAT don't work very well but ROOT can be given a password to get around it ([http://ubuntuforums.org/showthread.php?t=58434&highlight=swat)](http://ubuntuforums.org/showthread.php?t=58434&highlight=swat)).  The ramifications of this are still unclear.  I'm glad I found THIS HowTo before going that direction.

Shouldn't SWAT either be packaged to work or removed as "supported"?  Am I missing a basic definition of what "supported" means?

Insight and opinions welcomed.  TIA

i suggest sticking to this howto for configuring samba.  it's easier than trying to beat your head in over webmin.  webmin is a good tool for some things but not all.  if you're running a headless server, ssh is still your best friend.

don't know much about swat.

sudo is a safety net.  if you run as root regularly, you can cause a system wide problem with a single stroke of a key.  believe me, i've done it.  especially on a server, running as root should be avoided at ALL costs ... if for no other reason than simply security sake.

maybe you meant ssh rather than sudo?  there's some good ssh howto here: [http://easylinux.info/wiki/Ubuntu_dapper#SSH_Server](http://easylinux.info/wiki/Ubuntu_dapper#SSH_Server). sudo in combination with fuse can be used on a linux machine to mount remote linux file systems such that you can browse them with your filemanager.

i wouldn't suggest installing wembin via repos.  there's a fantastic howto here: [http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin+dapper](http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin+dapper)

really, in my opinion ... ssh and samba are necessities.  webmin is a handy tool to have around on occasion.

---

### Post by Bill_MI on 2006-09-05
Thanks, dmizer, I'll definitely browse your suggestions.

I didn't mean SSH - more like "the SUDO process" of default Ubuntu.  I guess in further reading that setting a strong root password doesn't compromize much and essential for SWAT.

Why I was looking into SWAT: I really wanted to get more insight into SAMBA by examining a good configuration front end but it probably doesn't exist.  Thus, the need for HowTos is big.

Stormbringer did a good job on this one - it has the right mix of  blind steps and insightful info for something as configurable as SAMBA. :D

---

### Post by nef on 2006-09-09
This is a great HOWTo storm.  This is exactly what I was looking for.  I just have a 2 questions.  On my windows box, the usernames are have the first letter capitalized.  Doing the 

sudo useradd -s /bin/true User_name

it allowed me to capitalize the first letter in ubuntu.  But, when I try to log into ubuntu with the fist letter capitalized it doesnt allow me.  Ubuntus username syntax requires the first letter in the username to be lowercase.  What I want to know, is there a way I can log into the accts in ubuntu with the first letter capitalized or will I need to change the username on the windows box to have the first letter in lowercase.

Second question.  How do I connect the printer I have shared in samba to another box running ubuntu?  Thanks.  You rock.


Nef

---

### Post by Giggity on 2006-09-10
Edit:  problem now fixed...

Thanks, Storm.  I followed your instructions, and everything worked perfectly.  I was able to map a network drive in my virtual WinXP right off the bat.

Then I rebooted the virtual machine after installing a program.  Apparently that was the stupidest thing I've done in at least a week.  Upon rebooting, I tried to access the network drives, and the virtual WinXP  asked me for my username and password.  I entered the same things as last time ("ROB-DESKTOP\rob" for the User Name and the password set in "sudo smbpasswd -L -a rob" for the password).  But this time, pressing enter just redraws the password window, ad infinitum.

I know my smb.conf is proper since all three of my desired drives mounted the first time.  Does anyone have any idea how I managed to foul up a perfectly functional setup?

Solution:  I replaced "ROB-DESKTOP" with "ROB_DESKTOP" (hyphens became underscores) when mapping the network drive.  I'm pretty darn sure the first time it worked, it was spelled with a hyphen, just like the hostname is shown in the Konsole.  Can anyone explain that?

---

### Post by rlgoddard on 2006-09-14
Hi,
 
Got a question regarding these two lines in smb.conf:
 
```
 
force user = YOUR_USERNAME
force group = YOUR_USERGROUP

```
 
Does this refer to my Ubuntu user name (joey) or to my Windows MCE user name (lolita)?
 
Thanks for your simple to follow how-to guide!
 
Take care,
Russ

---

### Post by mango.muncher on 2006-09-14
[COLOR="Cyan"]force user = YOUR_USERNAME
force group = YOUR_USERGROUP[/COLOR]

I used this 'How to' and entered Ubuntu username for both, later on you will set up windows username rights.

Storm you are a Ubuntu demi god! Thanks for this guide, now i can print from my Virtual XP machine.:biggrin:

---

### Post by superdave7380 on 2006-09-15
Help!

Brand new Linux user here... (sorry... geez...)

Tryin' to share the following with an XP computer.

[MOVIES]
I tho
path = /home/MOVIES
browsable = yes
writable = yes
public = yes
create mask = 0775
directory mask = 0775

3 users on the XP machine
All set as administrators (I know, very secure...)

I added all 3 to linux (adduser...)
I added all 3 to samba (smbpasswd...)
Same passwords all around...

On the PC, 2 out of 3 users can see the share no prob! (amazingly enough)
No password needed. Spiffy.

Problem is: The final user has to enter his name/password for some reason.

He is the original admin on the XP machine. (coincidence?) Again, all 3 users are now adminstrators...

I thought maybe he was seen as "adminstrator" instead of his username.. so i created an "administrator" user + smb user... that didn't work... deleted that...

So again, works for 2 of 3 admins on XP. For the 3rd (original admin), he has to enter his username/password. Then, it works no prob.

Why is he different? I dunno.

Help!

And thank you.[MOVIES]
path = /home/MOVIES
browsable = yes
writable = yes
public = yes
create mask = 0775
directory mask = 0775

---

### Post by myname on 2006-09-15
GREAT GUIDE!

I was able to get my samba server up and running (Kubuntu), and have my windows machine connect to it.  However, I have Ubuntu on my other box, and I can't connect to either my windows server OR my Kubuntu server through Samba.

The samba client SMBCLIENT is installed, do I need anything else installed?  With the base install of Ubuntu I have never been able to connect it to my windows server, BUT with the base install of Kubuntu I am able to.  

If both of these are based off the same code base, shouldn't they both connect?

Any help on getting my Ubuntu box to connect via Samba would be greatly appreciated.

---

### Post by jfighter on 2006-09-17
I got samba to work on my network so my Windows XP clients can now access the shared volume on my Ubuntu server.

However, I've browsed through this thread and still haven't found the answer to this one question: Can samba installed on Ubuntu server be used to enable Windows XP clients on the LAN to access shared folders residing on the hard drives of OTHER XP clients within the workgroup?

The reason I ask is that I have 10+ Windows XP client machines on my LAN and once I put the 11th computer on the LAN, Windows displays a message to the effect of "you have exceeded the 10 workstation connection limit...go buy Windows Server 2003 you poor bastard".

I know that Samba can connect up to 250 workstations on a LAN, but is it able to offer peer-to-peer file sharing between CLIENTS within the workgroup?

Thanks to Storm for his excellent contributions and all posters for any help!

---

### Post by myname on 2006-09-17
I have not tried this, but, in theory it *could* work.  Then again, I am a novice Linux user/recent converted to Linux from windows guy myself.

But if you mount the shares on your Linux box, can you not also share those mounts?

meaning, from your linux box, you mount your windows shares:

/mnt/windowsXP_box1
/mnt/windowsXP_box2
/mnt/windowsXP_box3
etc.

Then can you share those mounts?  so from the XP machiens, you connect to the Linux box and see the shares?

Like I said, I haven't tried this, but it kinda makes sense in theory.  

Any linux guru's out there know if this will work?

--kp

---

### Post by spot101 on 2006-09-18
> **jfighter said:**
> I got samba to work on my network so my Windows XP clients can now access the shared volume on my Ubuntu server.

However, I've browsed through this thread and still haven't found the answer to this one question: Can samba installed on Ubuntu server be used to enable Windows XP clients on the LAN to access shared folders residing on the hard drives of OTHER XP clients within the workgroup?

The reason I ask is that I have 10+ Windows XP client machines on my LAN and once I put the 11th computer on the LAN, Windows displays a message to the effect of "you have exceeded the 10 workstation connection limit...go buy Windows Server 2003 you poor bastard".

I know that Samba can connect up to 250 workstations on a LAN, but is it able to offer peer-to-peer file sharing between CLIENTS within the workgroup?

Thanks to Storm for his excellent contributions and all posters for any help!

From my research the probelm you face is a limit on the number of inbound connections WinXP Pro can accept.This [Microsoft Support Article]("http://support.microsoft.com/?scid=kb;en-us;314882") suggests you reduce the auto-disconnect time to make a connection available more quickly using this command:

net config server /autodisconnect:*time_before_autodisconnect_in_minutes*

Maybe you should reconsider your network architecture? Making the Ubuntu/Samba system the central repository on the network with multiple shares might be an easier approach.

Hope this helps.

Spot.

---

### Post by mattice06082 on 2006-09-18
I'm totally new to Ubuntu and I was able to follow these instructions so that goes to show how well written it was.  Thanks for sharing it with the community.

After following this HOWTO I'm able to see my windows machines using the Places -> Network Server browser.  However is there a way to refer to the network machines from within the Terminal?  I've tried ls //MachineName/SharedDir and ls \\MachineName\SharedDir, but haven't had any success.  As I said I'm new so please don't lol.

Also tried //priviteipaddress/ShareDir, but this didn't work either.

smbmount is what I was looking for.  Found it at [http://www.ubuntuforums.org/showthread.php?t=255872]("http://www.ubuntuforums.org/showthread.php?t=255872").

---

### Post by jfighter on 2006-09-19
> **spot101 said:**
> From my research the probelm you face is a limit on the number of inbound connections WinXP Pro can accept.This [Microsoft Support Article]("http://support.microsoft.com/?scid=kb;en-us;314882") suggests you reduce the auto-disconnect time to make a connection available more quickly using this command:

net config server /autodisconnect:*time_before_autodisconnect_in_minutes*

Maybe you should reconsider your network architecture? Making the Ubuntu/Samba system the central repository on the network with multiple shares might be an easier approach.

Hope this helps.

Spot.

Very good points.  I will try out myname's recommendation of mounting from the server and sharing back to clients (kinda roundabout way of doing it I must say but I guess there isn't a more elegant solution).  If that way doesn't work, doing multiple shares from server as spot suggests wouldn't be a bad alternative.

I'll report on what happens as soon as I have results.  If anyone has a more elegant solution, do tell.  Thanks again for the suggestions!  :)

---

### Post by dmizer on 2006-09-20
> **superdave7380 said:**
> Why is he different? I dunno.

Help!

And thank you.
i'll give it a shot.

from page one in the guide for adding users to your ubuntu samba:
> In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!
so your final user is loging into his windows box as "administrator" which means that you would have to add "administrator" to your ubuntu box.

there's another way though.

just go to the box that's not loging on correctly.  right click on "my computer" and select "mount network drive".  there's a little link below that says "log on as different user" ... select that and you can enter a different user name and password than administrator (and it will still be able to connect at boot).  enter in the user name  you added to samba for this individual, and you should be good to go.

---

### Post by superdave7380 on 2006-09-20
thanks, dmizer. i appreciate it.

---

### Post by MacPC on 2006-09-22
Hi there,

I am trying to network my Ubuntu PC to my two Windows PCs. One is a laptop and the other one is a desktop. Both Windows PCs are runnung Windows 2000 Pro. From the Ubuntu, I can access any folders on the laptop without any problem, but when I try to access the desktop, I can only access first one or level of the folder then I get this message "The folder contents could not be displayed. you do not have the permissions necessary to view the contents of 'XXXX'" For example, I choose this path: [my machine]-->WINTNT-->Web folder, every files on my laptop shows up, but when I use the same path on the desktop, once I try to open the Web folder, this message pops up. I am quite sure that on both PC, the file shareings are identical, what am I missing here? :confused: :( :sad: :-x :?: :?: :?: 

Also, how can I make the Ubuntu a server? On both Windows PCs, the Ubuntu PC shows up in My Network -->Computer Near Me, but when I try to access it after typing in username and passwork, I am denied asscess, how can I fix this?

One more question, how can Ubuntu share fils with the Mac OSX Tiger?

Thanks in advance. Too many questions too little time. :eek: 

MacPC

---

### Post by rabbit69ca on 2006-09-28
Great how:to very helpful, but I am having some problems. 

I believe it is setup correctly but when I try and map the network drive it is asking me for a username and password, I have all the UN/PWs setup the same 

the SMB user the actual Ubuntu account user as well as the windows username and password. (just to prevent confusion) but for som reason when I put that into the field it doesn't accept it. 

not 100% why.

anyideas?

Thanks 

EDIT:  Forgot to mention that my ubuntu machine is able to see and access the share folders on my 2 windows machines

And again, thanks in advance

---

### Post by DDM on 2006-09-28
This HOWTO worked great, I finally have my network up and running again. Plus, network printing to my printer connected to my ubuntu box worked without any effort on the linux side. I keep forgetting about how annoying it is to hand-install drivers in Windows.

---

### Post by beast2k on 2006-09-28
Nice how-to, I just followed it and it works great thanks for posting. It's alot easier to understand than alot of other samba how-to's.

---

### Post by dmizer on 2006-09-29
> **myname said:**
> But if you mount the shares on your Linux box, can you not also share those mounts?

meaning, from your linux box, you mount your windows shares:

/mnt/windowsXP_box1
/mnt/windowsXP_box2
/mnt/windowsXP_box3
etc.

Then can you share those mounts?  so from the XP machiens, you connect to the Linux box and see the shares?

Like I said, I haven't tried this, but it kinda makes sense in theory.  

Any linux guru's out there know if this will work?

--kp

just to clarify, what i think you mean is this.
linux sambashare is mounted by one single xp box.
that xp box shares the samba share and the next xp box doesn't mount the linux share directly but indirectly through the first xp box.

ie ... where windows shares a mounted linux share.

this can not be done.  windows can't share a share.  with the given configuration, each box will be able to see the others shares, but none will be able to see the other's mounted shares.

it's just not possible in windows.  don't think it's possible in linux either.

---

### Post by rabbit69ca on 2006-09-29
Never mind guys,a friend of mine helped me out, thanks anyway tho. 

I got it working

 It was a problem in my smb.conf file 

so I used his and presto.

---

### Post by parradux on 2006-10-01
Alright this guide was great, but i'am having a few problems. 

I have gotten to the point where I have to map my network drive. However, when I put \\xxx\\xxx into the folder space windows tells me it cannot connect. 

How do I fix this problem?

Also I have another question, through using this, how can I access my other shared folders on Windows so I can go back and forth.

---

### Post by dmizer on 2006-10-02
> **parradux said:**
> However, when I put \\xxx\\xxx into the folder space windows tells me it cannot connect. 

it should be \\servername\foldername ... before the server name is two backslashes, and after the server name is only one.

---

### Post by parradux on 2006-10-02
Ok i'am going to be a little more specific: 
And a little more background info: My account name/password is on windows is different then on my laptop. I think this may be a problem from reading some of the forum posts. So how do I fix this?


smbclient -L localhost -U% gives me: 

Domain=[HOME SERVER] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[HOME SERVER] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        BORIS-LAPTOP
        NESIC-SERVER

        Workgroup            Master
        ---------            -------
        HOME SERVER          BORIS-LAPTOP


My smb.conf is: 

[global]
    ; General server settings
    netbios name = boris-laptop
    server string =
    workgroup = HOME SERVER
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = boris
    force group = boris

---

### Post by lbarosi on 2006-10-02
Hi,


 Everithing worked fine. Getting Windows XP to see the network is a little bit har but samba documentation linked helped a lot.

 However, I still have some problems:

 Connecting from XP works fine. There are two users and They are correctly set up.

 Connection from Ubuntu, only one user password works! I probably did sometthing wrong, but I can't figure what could be.

 I have two computer XP/Ubuntu and I'm trying to set a network all transparent whatever OS they are running. Which means I'd like to have a sambafs in fstab, but I wouldn't like to type in my password in fstab. Windows files are really public, I only need to enforce privacy on the linux side.

 Thanks for any help.

---

### Post by DDM on 2006-10-03
I've had this setup, and it works beautifully. However, I have two problems with my setup, which has a laptop running XP and connected with a wireless card to a router, which connects to my Ubuntu desktop which has the printer attached.

1) Printing is flaky. Once the print command is issued on the laptop, the print menu takes about a minute to show up. Sometimes, it just doesn't work whatsoever.

2) File transfers are very slow; maybe 50K/sec. If I transfer a file over the same connection with apache or a ftp server, I get full 802.11g speeds.

---

### Post by dannyboy79 on 2006-10-03
lbarosi=if you are worried about adding a windows share to your fstab and not wanting to put in your username and password just use a credentials file and make it only openable by root. check this site out, it has helped everyone I have ever told about it.
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
DDM, are you atalking about when you transfer files and you sitting at your winxp box? or when you are sitting at your linux box. then if you're at windows, are you going thru network neighborhood or are you mapping a network drive. i noticed things go faster when you map and a network drive. also, ftp is always gonna be faster, it's a totally different protocol! maybe there is an answer here:
[http://www.gatago.com/linux/samba/19227375.html](http://www.gatago.com/linux/samba/19227375.html)

i personally use ftp when i need to transfer movies or xbox games, if it's just a small file or whatever than i use smb. i sometimes even use ssh.

---

### Post by Skaurecircle on 2006-10-04
Followed the instructions at the start of this thread and Samba is working fine, I am able to browse the XP box and pull files into Ubuntu. My question is this, while I was following the instructions I got to a piont when I kept getting an error message ( Please look below). Its at the piont when you have tp put in your username with a password, Strormbringer recommends the one i used at installation which I did, howver I get the error message, thing is Samba works fine regardless, should I be worried or just write it off to good luck?

Error Message: 

garth@garth-desktop:~$ sudo smbpasswd -L -a your_username
Password:
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user your_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user your_username

---

### Post by dannyboy79 on 2006-10-04
it's telling you that whatever username you're trying to add to your smb database is NOT a linux user on the machine. since smb refers to the same database that linux uses for it's users, then in order to add a smb user you need to have already added that same user to your linux box. you can either use the gui within system, admin, users and groups or i think from the terminal it's adduser 'username'. what i find weird is that you state that samba is already working for you. why are you trying to add more users than. after I re-read your post, something is totally wrong here. there would be no way that samba would be working fine if you were unsuccessfull in adding your username to smb if your smb.conf has passwd backend=tbdsam ( i think that's what it is) also, are you using security=user or share. if you are using share than it might be working because then you're not using authentification for your file sharing and ANYONE on your lan can access see files. i am curious, are you saying that you are able to VIEW your winxp box thru nautilus and also view the shares on it. if so, please post your smb.conf. thanx. this is one thing that just will not work for me. do you have the windows xp guest account activated? thank you for posting if you do, you could help me and I can maybe help you, if you need that is.

---

### Post by sKuarecircle on 2006-10-04
cooll I have no probs with that, but you got to let me know where to get, and how to get the smb.conf file.

---

### Post by sKuarecircle on 2006-10-04
Nevermind dumb question, as far as the seeing other Xp Boxes on my lan, I there is only one other one, and if i go to plase, network servers i am able to browse it with no password requests.

Here is my smb.conf file:

[global]
    ; General server settings
    netbios name = garth
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = garth
    force group = garth

Please offer your opinoion because I would rather have it done the right way

---

### Post by pcpat67 on 2006-10-05
When I enter:
```
sudo gedit /etc/samba/smb.conf
```
I get:
```
sudo: gedit: command not found
```
I also navigated to the file in the file manager and tried to edit it by opening the file from there and saving it, but it wouldn't let me save the changes. It popped up an error box that said "Can't open file to write"
What can I do?

---

### Post by ImpelGD on 2006-10-10
Thanks Stormbringer - just what I needed! :KS

> **core said:**
> when I try to map a drive to it, it says (after a few seconds attemping to connect)

"The mapped network drive could not be created because the following error has occured: An extended error has occurred."

The resolution to that problem may have already been posted (I haven't read all 18 pages), but I also got that unhelpful message when I'd used my Windows username instead of my Ubuntu username in the Samba config file.

> **pcpat67 said:**
> When I enter:
```
sudo gedit /etc/samba/smb.conf
```
I get:
```
sudo: gedit: command not found
```
I also navigated to the file in the file manager and tried to edit it by opening the file from there and saving it, but it wouldn't let me save the changes. It popped up an error box that said "Can't open file to write"
What can I do?

I'm no expert, but perhaps you haven't created the smb.conf file successfully? Try repeating the 'touch' command to create the file first.

---

### Post by jamesr on 2006-10-10
Hi,

> 
Code:

sudo: gedit: command not found



That is the command is not running are you running Ubuntu or Kubuntu or you could do the following 

Open a terminal window and then
```
sudo nano /etc/samba/smb.conf
```

---

### Post by dannyboy79 on 2006-10-11
> **ImpelGD said:**
> Thanks Stormbringer - just what I needed! :KS



The resolution to that problem may have already been posted (I haven't read all 18 pages), but I also got that unhelpful message when I'd used my Windows username instead of my Ubuntu username in the Samba config file.



I'm no expert, but perhaps you haven't created the smb.conf file successfully? Try repeating the 'touch' command to create the file first.

If it says COMMAND not found, that has nothing to do with the FILE, it is saying that it can't find the command. This would only occur if he is using Xubuntu or Kubuntu because those both come with different text editors. Gedit is Gnome's editor. So you can either use nano with is in most linux distributions or you mousepad if you have Xubuntu I think kate is for Kubuntu.

---

### Post by dannyboy79 on 2006-10-11
> **sKuarecircle said:**
> Nevermind dumb question, as far as the seeing other Xp Boxes on my lan, I there is only one other one, and if i go to plase, network servers i am able to browse it with no password requests.

Here is my smb.conf file:

[global]
    ; General server settings
    netbios name = garth
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = garth
    force group = garth

Please offer your opinoion because I would rather have it done the right way

You're not being asked for a password because you have null passwords = true.

---

### Post by EssGee on 2006-10-11
Thank you for this very well written and easy to follow How-To.  I now have Samba up and running perfectly well for my needs.

From my experience, I offer a couple of points that may help others.

1) Specifying your workgroup.  The method suggested is:
> ....To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

Example:

workgroup = MSHOME

Case matters when it comes to specifying your workgroup name in your smb.conf file.  I would suggest that you check it against "My Network Places-Microsoft Windows Network" in Windows explorer and enter it exactly as shown there. In my case, Windows XP would not pick up my Linux box until I changed the entry "MYNETWORK" (shown in Contol Panel-System-Computername) to "Mynetwork" (shown in Windows Explorer).

2) Share Name
> ...-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/
To reiterate, the share name in this case is "MyFiles" not " /media/samba/".  So when you map your share on DAPPER (your NETBIOS name, for example) on your Windows machine/s, you would specify:
//DAPPER/MyFiles
**_not_**
//DAPPER/media/samba

Thanks again, Stormbringer for an extremely useful document.

---

### Post by FoggyMtn on 2006-10-13
[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
:D


WHOOO HOOO!!!!!!  Thank you!!!!!!!!!!!!!!   I have been trying to get samba going for ages.  I tried all of those other tutorials and couldn't get squat!  With yours, I was up and running in 30 minutes!!   Unbelievable!!!!!!!!!!!!!!!!!!!!


foggy

---

### Post by dannyboy79 on 2006-10-15
Thank yiou very much for this guide. it helped me setup my network of xbox's, winxp, ubuntu, and xubuntu laptop. I am curious though, you tell people to use these 2 things
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
but you don't tell them how to set these up. DOn't people have to create a hosts file and put in there hosts? like 192.168.0.2 UBUNTU & 192.168.0.3 WINXP where the ip is the ip of the machine and the name is the hostname? I thought ubuntu only comes with a host file not hosts? Also, the smbusers file I thought was to map WINXP user names to your ubuntu usernames? like my username.map file is actually named that not smbusers also, within it would be for example: daniel = Judy Klimp which means that user on WINXP Judy Klimp is mapped to user daniel on my Ubuntu box. Am I correct on both of these things? if so, you should really add this to you howto. If I am wrong, could you maybe explain why? Thanks again as this guide along with what else I have setup has made my network great. also, a question. what does the null passwords = true mean? cause I don't want people without a password to be able to get at my shares! should i turn this off? one more thing, if someone is setting up an additional samba computer like i am using xubuntu i can't have both computers say wins support = yes because they both can't be the wins server so I had to change my xubuntu box to say, wins server = 192.168.0.3 which is the ip of the ubuntu box. am i correct with this. i hope so because it is working. oh, one other thing ha, wouldn't i want to use the valid users = $S for the share that I created if I don't want any other users to be able to use it? thanks again for the last time. ha ha

---

### Post by Moeru on 2006-10-16
I'm considering redoing my file server to Linux. My only concern is my fellow users in my apartment (2x WinXP boxes) writing to the File Server and causing an error. I know NTFS was a tad shaky in the past but I'm not sure to go about this in Samba if they need to drop stuff on the file server

---

### Post by Beamvr6 on 2006-10-16
Many thanks for this guide stormbringer!

Some irony is that my employer installed XP still refuses to map the networkdrive although it does see the Shared folder and the printer connected to the Ubuntu box while the Gnome file browser can work with all shared files on the XP notebook. Although this works pretty OK for me I was wondering if having shared folders on the XP thingie might interfere with mapping the network drive?

TIA from a very happy Ubuntu user.

---

### Post by ebutton on 2006-10-17
Thank you very much!

Your info worked perfectly.  I am now able to run XP and Win2k backups to a mapped drive on my ubuntu box.  Very sweet.

Good Fortune To You.

EdB

---

### Post by pooslinger on 2006-10-21
I have WinXP and Win98se working through VMware accessing the same folder using SAMBA.  If this works please update the main post.


I followed the original guide except I used "wins support = no"
________________________________________________________________

**[SIZE="4"]*_How to:_* Fix Win98 "Incorrect Password" prompt when mapping drive.[/SIZE]**

1. In Win98:

Primary Network Login -> Client for MS Networks.

You will have to input a user/password on start up when you do this. 

*Remember this password/username!!!


2. ^ Use the user/pass from above and make/activate an account. Case sensitive.

```
sudo useradd -s /bin/true "Win98 usernames"
sudo smbpasswd -L -a "Win98 username"
sudo smbpasswd -L -e "Win98 username"
```

3. Map network drive in Win98.

You can now access SAMBA shares through Win98.



[COLOR="Red"]_**Extra things that might have to be done before hand:**_[/COLOR] I did them but I don't know if they are needed.

1. ```
sudo /etc/init.d/samba stop
```

```
sudo gedit /etc/samba/smb.conf
```

Add the following to your [global] section

encrypt passwords = yes 

```
sudo /etc/init.d/samba start
```

2. In Win98:
    HKEY_LOCAL_MACHINE\System\Current\ControlSet\Services\VxD\VNETSUP\

    Select Edit->New->DWORD value from the mnu bar.  Rename the entry
"new  value #1" to "EnablePlainTextPassword".  Set its value to 1.

3. Install Win98 unofficial service pack:

[http://exuberant.ms11.net/98sesp.html](http://exuberant.ms11.net/98sesp.html)

---

### Post by brash on 2006-10-21
My grateful thanks to the original poster -- while I skipped over everything except the very first post, and admittedly didn't understand much of that, I now finally am able to access a shared fat32 partition and to trasnsfer files back and forth with the windows xp computers on our home network :)

(you can't imagine my relief when the IP/DHCP/WINS details turned out to be something I could safely ignore ... as a first-day Ubuntu user, I was just grateful I could handle copy-pasting the proper lines into the terminal.)

Thanks, you are a real sweetheart for doing this.

---

### Post by Schlupp on 2006-10-25
Hello! First thanks a lot for this very good documentation....
I did all the stuff u proposed and it worked quite well (even one other pc (winxp) didnt enable "wins".
The problem ist now, that the connection is VERY "instable". Some times I found the other pcs in the network (including my one) sometimes not, sometimes I can only see the workgroup but not the pcs in it. Some times it works after some minutes/an hour without restarting samba or anything like this.
And some minutes ago I could find the other pcs in one network-window, but not in another, after closing both, I couldnt see the other pcs anymore....
I dont know what to do....some times it works perfectly, sometimes not....
Anyone now this problem, could help me out, what could be wrong??
thanks a lot for help!!

Schlupp

---

### Post by christhemonkey on 2006-10-25
Good guide,

One suggestion, after people have made their changes to their smb.conf,
maybe you should make sure they run `sudo testparm` to check they didnt make an error?

Just my £0.02

---

### Post by stig on 2006-10-27
Wow...I happened to look in Ubuntu Cafe and saw that Stormbringer's thread is now 20 (twenty!) pages long and nearly 50,000 people have viewed it.

Stormbringer's thread helped me when it was only a few long and I just want to say that he's doing a greaaaat job!

Thanks Stormbringer!:p

---

### Post by ric_spam on 2006-10-27
I did a search of the forums and found some posts asking questions, so I might suggest a follow up HOWTO -- SWAT
 - install, configure and then how to manage Samba via SWAT.

TIA

---

### Post by the_original_bluefish on 2006-10-27
> **Stormbringer said:**
> If you want to hook your printer to your Ubuntu-Box and share it for the client on the LAN you need to install the Printer in CUPS first (in Gnome: "System" -> "Administration" -> "Printing") - there's no way around.

As soon as you installed your printer restart samba so that the newly added printer gets recognized for sure.

To add the printer to your Windows client you may either use the Network Neighborhood (browse to your Ubuntu Box, open the "Printers" Folder, right-click your printer and select "Connect") or the Add Printer Wizard in the Control Panel.

In both cases Windows will ask you to provide a driver for your printer in case it isn't directly supported by Windows. Install the driver and your're done.

The spool-file of Windows will be sent to Samba and forwarded to the appropriate CUPS-spool. If the job is already in the fitting native printer-language (PCL, PostScript, whatever) it will be put into the queue without further pre-processing and finally be printed.

In case the spool-file mismatches with the capabilities of the CUPS driver the job WILL be pre-processed to make it fit.

In the end it's CUPS that's handling your printer - not Windows or one of it's drivers.

If you have doubts you may also hook the printer to one of your Windows clients and setup a shared printer there ... in case the Windows-driver will output better quality.

-Storm

Storm, thanks a million for your post. Ubuntu ought to include your simple setup as part of it's distro for samba as an example. Example files would probably provide a ton of help for us budding ubuntu users.

Just an FYI for anybody reading... I encountered a problem with windows connecting to the printer. I would get an 'Access Denied, unable to connect' status on the printer.

To fix this problem, I did the following:
1. chmod -R 777 /var/lib/samba/printers
2. Edit /etc/samba/smb.conf and added the line 'use client driver = Yes' to the [Printers] section
3. Edit /etc/cups/mime.convs and ensured that the application/octet-stream line is uncommented
4. Edit /etc/cups/mime.types and ensured that the application/octet-stream line is uncommented
5. Restarted CUPS and samba

It would appear that others were having this problem... and I found the fixes at
- [http://www.linuxquestions.org/questions/showthread.php?t=322874](http://www.linuxquestions.org/questions/showthread.php?t=322874)
- [http://lists.freebsd.org/pipermail/freebsd-questions/2004-January/030676.html](http://lists.freebsd.org/pipermail/freebsd-questions/2004-January/030676.html) 
- [http://jmatrix.net/dao/case/case.jsp?case=7F000001-17918F0-10C13CE7D87-C4](http://jmatrix.net/dao/case/case.jsp?case=7F000001-17918F0-10C13CE7D87-C4)

This might save some people some time. It looks like the 'use client driver = Yes' is required for windows clients (not mac) and that uncommenting the mime types is required since the windows driver sends the raw content to be dumped on the printer... so uncommenting those lines enables CUPS to hand that kind of content appropriately.

Cheers

---

### Post by wilberfan on 2006-10-28
[ I just realized that [this thread]("http://ubuntuforums.org/showthread.php?t=286528") is the same issue I'm having ] 

GREAT post, I must say...

This has allowed to get samba running on Dapper (over and over!)--but I've just installed Edgy, and I can't see my Windows XP box...   

The XP box sees the Ubuntu box almost immediately (very peppy), but when I open the Network Server window in my Edgy box, it takes rather a long time (20 or 30 seconds) before it shows the "Windows Network" icon.   When I open that, all I get is a 'desktop configuration file' called "Home"...

I've checked that my Windows XP firewall is off (that was the problem the LAST time I couldn't see the XP box!).   Is my smb.conf file OK?

> [global]
    ; General server settings
    netbios name = DELL-Ubuntu
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/me/share/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = me
    force group = me


Anyone have any thoughts?

---

### Post by cor2y on 2006-10-28
Can someone tell me how to get Samba working with Vmware.
I've tried setting up as the guide pointed out. On wireless networks and wired lan it works but when it comes to setting a virtual machine , the virtual machine doesn't pickup the samba partiton.
Although the user ahs been added as well as the group.
Tried both NAT and bridged connection in VMware
Can someone help?

---

### Post by fatsheep on 2006-10-28
Thanks for the great guide.  However I don't really like how the Windows user (in this case my family) has to enter *MY* username and password so I created a dummy account that matches the windows username and password and set that up instead.

---

### Post by Juzz on 2006-10-29
I've followed the howto I even created the file that was supposed to contain the user mapping for samba, but all to no avail.
Neither me or my wife can access the shares.

When I try to connect to my samba server on ubuntu linux using smbclient:

```
veggerby@Juzzlaptop:~$ smbclient //192.168.1.10/musik
Password:
Domain=[MEDIECENTER] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_NO_SUCH_USER
```

My share looks like this:

```
[musik]
    path = /mcenter/Music/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ;mythtv,veggerby,benthe
    force group = ;mythtv
```
I've only just added the ";" trying to comment out the users and group to see if that would help anything.

My Globals section looks like this:

```
[global]
    ; General server settings
    netbios name = MEDIECENTER
    server string =
    workgroup = DV-CREW
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes
```

I've tried to create the file in the "username map" line "sudo touch /etc/samba/smbusers", and recreate the users, but that has had no effect - the file is still 0 bytes and with nothing in it.

I've ensured that I am in the same workgroup as my samba server (in case you noticed - my media center).

Can anybody see what is going wrong here?

We really want to get those shares up and running.

---

### Post by JawsThemeSwimming428 on 2006-10-30
I just went through the walkthrough and I still can not get my Ubuntu machine to share with my Windows machine. I think I followed all of the instructions pretty closely and I'm not quite sure what the problem is. When I go to map the network drive in Windows I type in \\the correct name\Ubuntu and then it comes up with the path could not be found. What should I do now?

---

### Post by navlelo on 2006-11-01
Great Howto! I had some problems on Edgy, but when I went back to Dapper, the Samba configuration was quick and easy, and *almost* problem free. I have two remaining problems and a question that I haven't managed to solve by myself:

Problem 1:
This is probably a Windows Xp issue. On my main XP account (with admin rights) I can not log in to my Ubuntu box automaticly. The mounted network drives give an error message every time I log on to the account. Another account on the same XP box logs in automaticly without any problems. I have checked many times that the user name and password are exactly the same in XP and Ubuntu/Samba.

Problem 2:
Guests can not browse my shared folder although I have set "guest ok = yes". I can not see what folders the server has without logging in with a user account that is registered in Ubuntu/Samba.

Question:
My computer is almost always on, and my guests frequently use it for browsing the Internet or my media files. They have full access to all my personal files because I don't feel it is natural or polite to make them log on as a different user. Is there a way to make an area on my network drive that is protected by an extra password prompt when I'm already logged in? 

I could of course make an additional, extra private, user account on both the XP and the server, but I won't bother to log on to a different account just to add a number in a spreadsheet or something like that.

I hope someone has one or more answers for me!

---

### Post by ImpelGD on 2006-11-01
> **navlelo said:**
> Is there a way to make an area on my network drive that is protected by an extra password prompt when I'm already logged in?
I believe you could add another share with any username and password of your choosing. When you wish to access it with XP, use the 'connect as different user' option (or similar) and use your chosen details. Uncheck remember/automatically log on.

---

### Post by navlelo on 2006-11-02
> **ImpelGD said:**
> I believe you could add another share with any username and password of your choosing. When you wish to access it with XP, use the 'connect as different user' option (or similar) and use your chosen details. Uncheck remember/automatically log on.
Thank you for the suggestion, but it doesn't work. If I try to log on a different folder on the same server with a different username, I get the error (translated by me from Norwegian): *"More than one connection from the same user to a server or shared resource, by the help of more than one username, is not allowed. Disconnect all previous connections to the server or shared resource, and try again."* I don't know if there is a way to change this limitation on the Windows side, at least I haven't found it.

As long as I am logged in to a folder on the server, I can access all other folders available to that user without being prompted for a password. The closest thing I've got now is a folder that isn't browsable, and therefore can only be accessed by typing the correct folder name. While it is better than nothing, it's neither practical nor completely safe.

I am still hoping there is a setting in Samba that forces a new login for a resource, and I still have no solution to the two other problems in the post above.

---

### Post by linuxguiri on 2006-11-03
Great howto! It would be great if you posted this on the wiki. The one that's already posted there as well as the official help guide are way over my head (and probably a lot of other users).

For the benefit of others who might have the same problem:
I ran into this error when I attempted to access the share from WinXP:
"\\linuxhostname is not accessible. You might not have permission to use..."

Apparently the solution is to open some specific ports on the ubuntu firewall. As I didn't know how to do this, I just temporarily disabled the ubuntu firewall via Firestarter. If anyone knows which ports and how to open them up, please let me know.

---

### Post by dannyboy79 on 2006-11-10
> **linuxguiri said:**
>  For the benefit of others who might have the same problem:
I ran into this error when I attempted to access the share from WinXP:
"\\linuxhostname is not accessible. You might not have permission to use..." 
You are missing the share name, so if you were sharing a folder on your linuxhostname computer called dave, then in winbloz, you type in \\linuxhostname\dave. keep in mind that the user you logged in with in winbloz should be the same user and password that you did the smbpasswd -a username command.

> **linuxguiri said:**
> Apparently the solution is to open some specific ports on the ubuntu firewall. As I didn't know how to do this, I just temporarily disabled the ubuntu firewall via Firestarter. If anyone knows which ports and how to open them up, please let me know. 
You may be decieving others on accident, Ubuntu has a firewall installed by default (iptables) but does NOT have any rules enabled by default. So that means that there are NO PORTS being blocked going in or going out after a fresh install of ubuntu desktop version. (not sure about the lamp version or server versions) Your problem sounds weird as you say it works when you turn the firewall off, this must be because you enabled rules by default. The ports that you want to add if you'd like are netbios-ns 137/tcp # NetBIOS Name Service
netbios-ns 137/udp
netbios-dgm 138/tcp # NetBIOS Datagram Service
netbios-dgm 138/udp
netbios-ssn 139/tcp # NetBIOS Session Service
netbios-ssn 139/udp
microsoft-ds 445/tcp # Microsoft Directory Service
microsoft-ds 445/udp
which is documented here: [http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/) but I don't believe that's your issue unless you did previously set up your firewall.

---

### Post by zaziork on 2006-11-18
> **Stormbringer said:**
> 

Please start up VMware, open a command prompt, and type:

ipconfig /all

Please post the output into a reply (or PM me if it's a public IP address).



Firstly, thank you, Stormbringer, for the HowTo. Very much appreciate it.

May I ask either "Core" or yourself: In general terms, what was the resolution to the "an extended error has occured" error, about which you corresponded in private? I'm having exactly the same problem...

TIA.

---

### Post by lime4x4 on 2006-11-20
ok i followed the guide i can browse my other hard drives that are on another ubuntu box but it will not let me write to the drives here is a copy of my file that pertains to my shares
[MyFiles]
    path = /media
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = mythtv
    force group = mythtv

i'm i correct in assuming i also need to add

   write=yes

---

### Post by themikeflynn on 2006-11-21
"The drive could not be mapped because no network was found."

I get this error after following the guide. Windows won't recognize the network. When i go to "My Network Places >> Entire Network >> Microsoft Windows Network" everything starts getting slow, as if it realizes something is there, but it won't go through. The connection is fine; I've had no trouble accessing my LAMP server that I have set up. But I just can't get this filesharing via Samba to work out.

Any advice?

---

### Post by adamkane on 2006-11-21
The HOWTO is a wee-bit over-long. Here's how you do it:

Install samba-common.

```

sudo apt-get install samba-common

```

Right-click folder you want to share.

Enable the folder for sharing.

Add a Samba user:

```

sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers

```Insert the following line into the new file 

```

system_username = "network username"

```Save the edited file 

To delete network user:

```

sudo smbpasswd -x system_username

```Done.

---

### Post by Kulgan on 2006-11-25
Unless you want to be able to browse stuff on your Windows computer. That takes a little more. 

I had it working fine with the original tut, but now for some reason I can't get to the shared folders in Windows. I find that really strange, as I can print to the printer on the same machine. I went to Places -> Network Servers -> Windows Network -> mshome -> DESKTOP, and got all the files from Windows. Now all I have is 

> Sorry, couldn't display all the contents of "Windows Network: mshome".

When I open "mshome". Odd, and I have no idea what is wrong. I can still get to the Ubuntu shared files from the Windows computer. 

Any ideas?

-K

---

### Post by dmizer on 2006-11-28
@kulgan ...

see the second link in my sig for mounting windows shares from ubuntu.

---

### Post by Kulgan on 2006-11-28
great article, I'll try that as soon as I have finished my homework... :D 

In the bit where you add "wins" to the hosts: line, I have "hosts: files dns mdns". does that matter?

---

### Post by featherking on 2006-11-28
that shouldnt matter, you are just adding wins resolution to your hosts file in addition to those others

---

### Post by keithnorris on 2006-11-29
:) 
Thanks for a great resource. No questions. No problems. Just: Thanks.

---

### Post by gvsrinivasan on 2006-12-03
the samba guide was good , 
i want to  know how can i share an internet connection available on windows xp on one system  with another one having kubuntu dapper drake in it through samba or by any other possible way 

i urgently need internet connection in kubuntu to carry out my day today works on it

---

### Post by Kulgan on 2006-12-03
are you talking of using the windows machine as a "router"? Like, the connection itself goes through the windows machine before into the wall or whatever?

---

### Post by guetrochide on 2006-12-03
thank you for the topic[.]("http://launch.groups.yahoo.com/group/DeMoNTeAM/messages/1001?viscount=100")[.]("http://launch.groups.yahoo.com/group/DeMoNTeAM/messages/1001?viscount=100")

---

### Post by gvsrinivasan on 2006-12-03
i am having an adsl  broadband connection in my amd  semperon machine running windows xp and want to share it with another Intel celeron machine which has kubuntu dapper drake in it ,i want the internet connection on windows xp machine  to be shared with kubuntu through any other means of achieving it  so if u don't  mind  a router  means  the  connection pass through   windows xp before coming on to Ubuntu , if i am wrong ,then forgive me ,i am completely new to networking

---

### Post by Kulgan on 2006-12-03
The best solution for this is to just get a router. They are not that expensive, and quite easy to set up - a lot will get you free help setting up and such. See the [image]("http://ubuntuforums.org/attachment.php?attachmentid=20430&d=1165156794") for the difference... The router just spits the internet connection, rather than having to set up the windows machine to do it. It also means that you can expand the network...l

---

### Post by gvsrinivasan on 2006-12-03
thanks for the reply and clarification about the router, i am living in India and  a router costs  up to 85$  here ,so it will be good if it is possible in my current setup to achieve the internet connection sharing through crossover cables and samba is working through it only  and through any software to do the internet connection sharing on Linux  ,
 again thanks for the reply

---

### Post by Kulgan on 2006-12-03
so you want the connection to go through the windows machine - so then you would need software for windows rather than linux. As far as I know, you would just connect to the windows machine as if it was a gateway, but you will most likely have set the windows machine up with all sorts of security settings first - windows is a little odd about that :/

I reccomend you start a new thread in the Networking section of the Forums - the mods probably like keeping things nice and tidy...

---

### Post by gvsrinivasan on 2006-12-03
ok .so  i can use the windows machine as a gateway for connecting internet on Linux, it will be good if u cover some good software packages available for samba as a second part in the samba how-to guide ,u can also distribute it as a pdf file  ,i will be happy if next version of Ubuntu 
comes preloaded with samba installed instead of samba-common in it, thanks for patiently clarifying my various doubts on internet connection sharing

---

### Post by Kulgan on 2006-12-04
All I know is that it should be POSSIBLE - and that's pretty much it. I'm sure you will get help in your new post :D

---

### Post by madscientist on 2006-12-04
Hi all.  I've been reading Samba howtos etc. until my eyes bleed :).  None of them seem to address what I want to do, or if they do I can't see it.

I have a (small office) network which is run by Windows people using Active Directory and all that stuff.  I have my little Ubuntu system sitting on my desktop.  So far I am able to mount shares and all that stuff, so I have no problems there.

What I can't seem to do is publish my system's hostname so that any other systems can resolve it!

Our Windows systems use static IP, not DHCP, and apparently there's some checkbox in the Windows network config that tells it to publish its hostname.  I have a static IP for my Linux box too, but I don't know how to get my Linux box's hostname to be published.  The Windows admin guys do NOT set up the hostname statically (apparently): the client pushes it somehow.

I don't want to be any sort of server: my system must be 100% client.  I can't be a WINS server, or NMBD server, or Samba server, etc. (I only have a vague understanding of what those are anyway).

Is there some way I can configure Samba, or something else, to publish my hostname to a Windows environment (I assume using AD)?  If someone could even point to which part of Samba might be used to do such a thing I would appreciate it.

Thanks for any tips or pointers!

---

### Post by trietgiang on 2006-12-05
Thank you so much for this guide. I had all working fine in the first attempt. 

Just two questions please:

1) In the smb.conf file, there is a line:
username map = /etc/samba/smbusers
I checked in /etc/samba, there is not a "smbusers" directory. Is this normal?

2) I had this line in the last part of the conf file:
path = /home/samba/
Does it mean that all users connecting to this Linux will share this directory? Should individual directory is created per username? If no, how do I do that? Say I have 10 Windows users, I can create their accounts in Linux, how should I modify the smb.conf file to make individual's directories?

Thank you for your time, and keep up the great work.
Best regards,
Triet

---

### Post by Kulgan on 2006-12-05
madscientist:
I'm afraid I know nothing about Active Directory (though I may use it unknowingly :-k ), and don't know much about static setups, either. Is is a workgroup or domain? What exactly are you trying to accomplish - if you don't want to have a samba server, then you don't want to host data, in which case there is no problem, is there?

---

### Post by madscientist on 2006-12-05
> **Kulgan said:**
> madscientist:
I'm afraid I know nothing about Active Directory (though I may use it unknowingly :-k ), and don't know much about static setups, either. Is is a workgroup or domain? What exactly are you trying to accomplish - if you don't want to have a samba server, then you don't want to host data, in which case there is no problem, is there?I'm not sure I know the difference between a workgroup and a domain: there is a workgroup name on the windows systems that I need to use.  I can mount shares using smbfs without a workgroup name though.

I need for people to be able to resolve my hostname.  For example, if they have putty on their system I want them to be able to "ssh myhost" where "myhost" is my linux box, and have it work.  I also plan on hosting some services such as a web browser, etc. on my box.

In the Linux/UNIX world, which is where I'm from, that would involve either (a) pushing the hostname in the DHCP response, for dynamic IP, or (b) hard-coding the hostname/IP into the local DNS system.  For Windows there appears to be some way of doing a combination: the IP address is statically configured, but the hostname is not specified on the server.  Somehow the client pushes its hostname, then the hostname is available through normal DNS requests (like, I can use "host windowsbox" on my Linux system and have it resolve "windowsbox" to an IP address, where "windowsbox" is a Windows system using this method of "pushing" hostnames.

Does this make any sense?  Anyone have any idea what I'm referring to?  I'm afraid that while I have an embarrassing number of years experience with all things UNIX, I know virtually nothing about Windows, especially Windows servers and services.

---

### Post by Kulgan on 2006-12-05
I'm afraid that *I* can't - wish you luck finding help, though! Don't give up ;)

---

### Post by BabyUbuntu on 2006-12-06
hi all....

i want to ask someting.. maybe its stupid question but its important for me

i have server mp3 ( ubuntu ) and 5 window clients + 1 laptop ubuntu
my problems are..
1. when i try to connect ubuntu from xp..have to login first. the question is.. how to connect ubuntu ( samba ) without login prompt?
2. if i playing my laptop(ubuntu) and i wanna playing mp3 from XP.. i've to copy to my local disk first.. my question is.. how to playing mp3 from xp without copy file first?

em sorry...my knowlagde bout linux very low.. i really need ur help

---

### Post by Kulgan on 2006-12-06
what stops you from playing mp3s right from the XP computer?

---

### Post by BabyUbuntu on 2006-12-06
lemme explain my condition
when i'm using ubuntu and i want to playing mp3s on my XP,, i have to copy mp3 files from XP to ubuntu first.. i cant playing mp3s on my XP via local area network.. how to playing mp3 from via LAN without copy file first on my ubuntu? (ubuntu as client and XP as mp3 server)

---

### Post by Kulgan on 2006-12-06
If you go to Places -> Network Servers -> Windows Network -> <WORKGROUP> -> <HOSTNAME> -> Wherever you keep the files, you should be able to play them. Even if you can't write, playing them should take no more permission than copying them...

---

### Post by mirzmaster on 2006-12-18
I just wanted to toss in my 2 cents of appreciation and thank the author of this guide for their hard work into writing it up.  This was the perfect guide to help me setup my Samba configuration!

Thanks, again!

---

### Post by broughcut on 2006-12-29
ditto.

finally working. after 6 hrs trawling this thread and google for a solution to a "can not connect" error on the map drives step I had the sense to install file and printer sharing. Surprised Windows didn't prompt me for this during the home network wizard. Anyway, seems to be working great (Windows as a guest OS under VMware server).

> 2. Changing network settings in Windows

Now we should let Windows know that there's a WINS server active in the network.

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
 

**- make sure Client for Microsoft networks, and File and Printer Sharing for Microsoft Networks are both checked** :rolleyes: :redface: 

> - Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows


---

### Post by jtwadsworth on 2006-12-30
Great writeup!  I have been struggling with this for a time and it is helping...still some problems though.  With this writeup my WinXP machines on the LAN can see the Ubuntu shared folder just fine and visa versa.  The problem is that once I click on the share through a WinXP box, I am asked for a login and pw and nothing works.

To be clear, I am sharing out an NTFS drive from Ubuntu to the rest of the LAN (either through IDE or USB connection, I've tried two different drives).

When trying to log in with smbclient to the shared drive I get the following:

tree connect failed: NT_STATUS_BAD_NETWORK_NAME

My smb.conf share info is here:

```
[MyMusic]
    path = /media/'WDC 300GB'/'My Music'
    browseable = yes
    read only = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = UNIX_ACCOUNT
    force group = UNIX_GROUP
```

I tested the SAMBA sharing out my home folder and it worked just fine...is there some problem with sharing out an NTFS disk through Ubnutu?

jtw

---

### Post by mistypotato on 2007-01-02
Thanks Stormbringer!!!

You finally put me out of my Samba misery :KS  :KS  :KS 

You post finally got Samba working for me so I'm posting the link to it again here

[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")

---

### Post by AEngineer on 2007-01-02
I agree with all the other folks who've praised what you did.  Many thanks.  

Of course I'm here with a problem, one I couldn't find addressed in the many posts, although it may be.

I followed the tutorial and have my windows machine seeing what I called "server1".  I can start the mount process with XP, but when I get to the connect dialog box it doesn't accept my 
username and password.  After it refuses plain "george" (username) It offers to try using the following "P390\george" as user name, where P390 is the machine name, but that doesn't work either.


- I've checked that the user name (and password) are identical on both machines - including case.
- I've restarted the windows machine

I'm baffled what to do next to track down why it won't accept the login that is the same on both my XP and ubuntu (6.10) machine.

Thanks for any help you can give

---

### Post by AEngineer on 2007-01-02
Oops.

I restarted Ubuntu, closing a dialog box in the process and now it works as it should.  I shot too soon.

Thanks again anyway.

---

### Post by tagra123 on 2007-01-03
Nautilus in dapper kept giving error messages unles you manually set up the network share via connect to seerver using an ipaddress.

I found a solution that actually works.

[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

### Post by Cogito² on 2007-01-04
> **Stormbringer said:**
> **HOWTO: Setup Samba peer-to-peer with Windows**

....


Warning: I know/understand very little of linux/ubuntu.

I followed the tutorial and decided to simplify it by changing very little. I used DAPPER for the host name, MSHOME for the workgroup and /home/samba/ for the path. Everything seems to go fine except I just can't map the network drive. I tried using both wins and not using wins. When not using wins, I used "\\<ip-address>\home\samba\" or "\\<ip-address>\samba\" or "\\<ip-address>\home" etc., but it always give me "The network path ... could not be found." When using wins (I went back through the tutorial setting it up with wins from the beginning), I would try using "\\DAPPER\home\samba\" or other variations as before and it would still not be able to find the network path.

So I guess this is more of a windows question than anything, but can anyone see anything that I may obviously be doing wrong? Thanks in advance for any help.

(Note: I actually only want to network the computers once...after that I don't care. I have about 30 gigs i want to transfer off my linux box across the network to a windows box before reformatting it. I haven't yet been able to link them and so far the only other solutions (eg. ftp) leave me with a ~50 KBPS speed which would take about a week to transfer...meaning that I need to use the network so I can get the network speeds cutting the time down by a factor of a hundred or so. So if my above problem isn't easily solved, I'd definitely be willing to try another completely different networking solution so that I could get these files transfered.)

---

### Post by tagra123 on 2007-01-04
For a quick and dirty one time method of copy look at 
scp 

 -- google for  scp examples.



_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_

[COLOR="Navy"]NFS is easier to get working than samba and o[/COLOR]n my network is 3 times faster.
On the Server (computer with the files)

```
sudo apt-get install nfs-kernel server
mkdir /home/sharedfolder
```


Share the folder -- right clicking on it will give you this option.

or you **can edit the /etc/exports file** and add a line like this

```
/home/username/sharedfolder            192.168.1.0/255.255.255.0(rw)
```


>>>>>>>>>>>>>>>>>><<<<<<<<<<<<<<<<<<<<<<<<
to access it from the remote computer

on the remote computer

```
sudo apt-get install nfs-kernel-server
sudo mkdir /mnt/nfsshare
sudo chmod 777 /mnt/nfsshare

mount -t nfs 192.168.1.XXX:/home/username/sharedfolder /mnt/nfsshare

```

Now you can use nautilus to drag and drop to your hearts content.

_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_

For samba you can look at my earlier post #240

[http://www.ubuntuforums.org/showpost.php?p=1963941&postcount=240](http://www.ubuntuforums.org/showpost.php?p=1963941&postcount=240)

Samba just seem broken since breezy. There is no way anyone can justify the time it takes to set it up correctly.  I like ubuntu but it took some work to get the breezy samba to work with the dapper samba.

---

### Post by Cogito² on 2007-01-04
Okay thanks for the info. I'm going to try the scp method first. I'm looking into winscp for my windows box and then I'm now trying to figure out what I'd need for the linux box. I need to transfer the files from my linux box to my windows box so I'd guess I'd need to make the linux box act like a server in a sense (correct me if I'm wrong). Anyway I'm going to fiddle around with that and see if I can get it working, but if you have any words of wisdom you'd like to add, then I'm all ears. Thanks a lot.

---

### Post by tagra123 on 2007-01-04
> **Cogito² said:**
> Okay thanks for the info. I'm going to try the scp method first. I'm looking into winscp for my windows box and then I'm now trying to figure out what I'd need for the linux box. I need to transfer the files from my linux box to my windows box so I'd guess I'd need to make the linux box act like a server in a sense (correct me if I'm wrong). Anyway I'm going to fiddle around with that and see if I can get it working, but if you have any words of wisdom you'd like to add, then I'm all ears. Thanks a lot.


If you alread have ubuntu installed on one pc than just put the live cd in the other and mount the windows partition -- you might have to read a couple of items from google on mounting ntfs partitions -- actually I think the live cd mounts it in the tmp folder with an odd looking name.

You can still use apt-get install  blah blah blah   on the live cd -- it just wont remember that you installed it because its using RAM.


Might ever be easier to remove the drive dfrom the windows computer -- hook it up to the ubuntu computer boot ubuntu, mount the windows partition on the drive you've just connected  and copy away

---

### Post by Cogito² on 2007-01-04
Yeah I just realized that just mounting the drive in linux may be the best bet (I tried mounting the linux drive in windows earlier, but that didn't work and I forgot to try the other way). I'm going to try that first and I think that even I can do this (or at least figure it out with the documentation and everything). Thanks for your help so far. Hopefully this does it.

edit: My latest questions have moved to this thread: [http://www.ubuntuforums.org/showthread.php?t=331549&page=2&highlight=mount+ntfs](http://www.ubuntuforums.org/showthread.php?t=331549&page=2&highlight=mount+ntfs) in case you also happen to be knowledgeable in that respect. ;)

---

### Post by TheOtherLinuxFreak on 2007-01-05
great how to. very helpful!!  does any one know how to do internet connection sharing with ubuntu?

---

### Post by prepstyles on 2007-01-08
Not sure if Stormbringer still monitors this thread but Cheers on the guide anyway!

I <ctrl>-f 'd through the previous pages and couldn't find anything related to my problem, so forgive me if this has been covered before...

So I followed the initial post and got samba shares setup on a XUbuntu box on my lan.
I have WIRED Linux and windows boxes that can access the shares on the samba box.
However I have WIRELESS windows boxes that cannot find the shares when I attempt to map them.
I have my router set for static ip 's.

Any thoughts on why it would work for wired clients but not wireless?

Cheers!

---

### Post by Kulgan on 2007-01-08
at the bottom of the original post, there is some mention of that. You may have don something similar to that by accident. Sh1t happens :p

---

### Post by SQNik on 2007-01-09
I install Samba like in HOW to : [http://www.ubuntuforums.o...highlight=samba](http://www.ubuntuforums.o...highlight=samba)

MY SMB.conf :


[global]
; General server settings
netbios name = serwer
server string =
workgroup = GELMONT
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[MyFiles]
path = /media/samba/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = sqnik
force group = sqnik

next 

sudo smbclient -L localhost
Password:
Anonymous login successful
Domain=[GELMONT] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

Sharename Type Comment
--------- ---- -------
print$ Disk
MyFiles Disk
IPC$ IPC IPC Service ()
ADMIN$ IPC IPC Service ()
Anonymous login successful
Domain=[GELMONT] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

Server Comment
--------- -------

Workgroup Master
--------- -------


Why don't detect my Workgroup and Server ? Please help !!

Sorry for my english :P

---

### Post by TheOtherLinuxFreak on 2007-01-09
> **SQNik said:**
> I install Samba like in HOW to : [http://www.ubuntuforums.o...highlight=samba](http://www.ubuntuforums.o...highlight=samba)

MY SMB.conf :


[global]
; General server settings
**_netbios name = serwer_**
server string =
workgroup = GELMONT
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[MyFiles]
path = /media/samba/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = sqnik
force group = sqnik

next 

sudo smbclient -L localhost
Password:
Anonymous login successful
Domain=[GELMONT] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

Sharename Type Comment
--------- ---- -------
print$ Disk
MyFiles Disk
IPC$ IPC IPC Service ()
ADMIN$ IPC IPC Service ()
Anonymous login successful
Domain=[GELMONT] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

Server Comment
--------- -------

Workgroup Master
--------- -------


Why don't detect my Workgroup and Server ? Please help !!

Sorry for my english :P


mabe  because u spelled server  "serwer"

---

### Post by Lowfront on 2007-01-10
Alright i'm able to connect to ubuntu from windows.  But all the folders in my media folder are locked.

When I go to add a file from windows it says,  access is denied.  Make sure the disk is not full protected and that the file is not currently in use.


So how to I unlock these folders and files?

---

### Post by TheOtherLinuxFreak on 2007-01-10
> -> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

Code:

[QUOTE]sudo mkdir /home/samba

... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:

Code:

> sudo chmod 0777 /media/samba

NOTE: Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...[/QUOTE]

this is how u create a file in ur home directory. if u cant get it unlocked. it did this and it worked for me.

---

### Post by baldmosher on 2007-01-12
> **Stormbringer said:**
> The "force group" parameter inside the definition of the share DOES NOT, i repeat: DOES NOT, refer to a Windows-Workgroup but to the group of the local useraccount(s) on your Linux box.

Thankfully I only needed to get to page 3 to get this working - thanks for the help!

---

### Post by rahelvey on 2007-01-14
thankyou sir stormbringer
I have had the unpleasant task of reinstalling my wifes windoze xp a number of differant times with the same 2 day trial of it up to speed.
Networking has always had me on the line for it works the same twice.
Your howto is now bookmarked for it worked perfect and quick.
Again thank you

---

### Post by mikemaggio on 2007-01-15
I have installed Samba following the instructions but no matter how I try I cannot connect my windows 2000 server or my ubuntu workstation to the domain. Here is the error Windows 2000 gives me.

---------------------------
Network Identification
---------------------------
The following error occurred validating the name "educateint.com".
This condition may be caused by a DNS lookup problem. For information about troubleshooting common DNS lookup problems, please see the following Microsoft Web site:
[http://go.microsoft.com/fwlink/?LinkId=5171](http://go.microsoft.com/fwlink/?LinkId=5171)

The specified domain either does not exist or could not be contacted. 
---------------------------
OK   
---------------------------
 Don't know how to proceed.

---

### Post by happyhacker on 2007-01-19
I have another PC connected to XP which does not use WINS.

Could I use WINS in this situation? I assume no because it is not configured on XP.

My login in windows is admin pws=xxxxx; If I try to use a SAMBA login on UBUNTU with 'admin' I get a response 'useradd: group admin exists - if you want to add this user to that group, use -g' Is this a clash?

---

### Post by pharmd24 on 2007-02-03
Very good how to! thanks it filled in the couple of holes I still had in my network!

---

### Post by techno-mole on 2007-02-05
how do i find out what the ip adress of my linux system is ?
or do i sue the routers ip address ?
cheers

---

### Post by Lista on 2007-02-06
Techno-mole, 'ifconfig' typed into the terminal will do the trick.

As for me, I'm having a different kind of issue. I've managed (party) to set Sabma up, and I'm able to access my Ubuntu desktop from XP, but not the other way around. Useful clue could be that I can't even see a workgroup name when viewing Network servers.

Experts, any ideas?

---

### Post by sabredog on 2007-02-06
I asked this question earlier but no one seemed to be able to help, so I will ask again here.

Can I connect to both a domain and a workgroup using Samba.

Currently connected to a workgroup with no issues but would like to connect to a domain within the same LAN concurrently.

cheers and thanks

---

### Post by troyDoogle7 on 2007-02-09
I find it ironic, that this entire page can be summarized in windows at least as.. .right click, share, press ok......

Sad to see how far linux has to go to be mainstream.  and simple... 

Some one will no doubt flame me and argue how simple it is... but nearly 10 pages of printouts !== simple

---

### Post by monomaniacpat on 2007-02-09
I have followed the how-to to-the-letter, but I cannot get access from the PC. In fact, it doesn't even show up in the workgroup (MSHOME) initially, but when I've tried to mount the drive (as per the tutorial) it magically appears. When I double click on the Samba Server, it says "you may not have permission to use this network resource".

I have setup the username and password, and added it into the dialogue box in windows, but no give.

Here's the contents of my smb.conf:

```
[global]
    ; General server settings
    netbios name = inspiron-8200
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/patrick/downloads
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = patrick
    force group = patrick
```

Thanks for any help you can give!

---

### Post by alabamaXslim on 2007-02-10
NOOB ALERT. (Sound of claxon ringing)

Great Tutorial. I went from nothing to a Ubuntu 6.10 Server with Samba enabled shares in just 2 days. I followed the HOWTO to the letter and it all worked as advertised.

Now the next step for me is to share a tape drive. The ultimate goal being to use my Windows Backup software to backup the Windows Boxes to the shared tape device.

Here are my particulars:


**cat /proc/scsi/scsi shows**
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: DELL     Model: Alpha Server     Rev: V1.0
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 06 Lun: 00
  Vendor: HP       Model: Ultrium 1-SCSI   Rev: E21V
  Type:   Sequential-Access                ANSI SCSI revision: 03


**ls -l /dev shows**
crw-rw---- 1 root tape      9,   0 2007-02-09 22:47 st0
crw-rw---- 1 root tape      9,  96 2007-02-09 22:47 st0a
crw-rw---- 1 root tape      9,  32 2007-02-09 22:47 st0l
crw-rw---- 1 root tape      9,  64 2007-02-09 22:47 st0m


**ls -l /media shows**
total 8
lrwxrwxrwx 1 root root    6 2007-02-09 14:56 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-02-09 14:56 cdrom0
lrwxrwxrwx 1 root root    7 2007-02-09 14:56 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-02-09 14:56 floppy0


**cat /etc/samba/smb.conf shows**
[global]
    ; General server settings
    netbios name = ALPHA
    server string =
    workgroup = CJKNET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    domain master = yes
    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = no
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = no
    browseable = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
[CD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = no

[MyFiles]
    path = /usr/local
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = derekw
    force group = derekw


**cat /etc/fstab shows**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3a4df524-78da-44c1-ae92-a32e2618d990 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=52ae24f4-e463-47ea-af34-b18abb039439 /home           ext3    defaults        0       2
# /dev/sda10
UUID=a670103e-a5e6-47a5-8193-c038465ccc65 /opt            ext3    defaults        0       2
# /dev/sda8
UUID=25ec553b-b6cd-493b-8cdd-638af2e4ffca /tmp            ext3    defaults        0       2
# /dev/sda6
UUID=a3a3f604-fd3e-4c67-9228-c36916fcfc97 /usr            ext3    defaults        0       2
# /dev/sda11
UUID=bea65b31-699d-4e86-9714-a2947434656d /usr/local      ext3    defaults        0       2
# /dev/sda7
UUID=ba658367-1c67-4305-b17e-00483d585a77 /var            ext3    defaults        0       2
# /dev/sda9
UUID=66710c69-7006-478e-8995-cc7366ed9f7a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


**sudo mt-st -f /dev/st0 status shows**
SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x0 (default).
Soft error count since last status=0
General status bits on (50000):
 DR_OPEN IM_REP_EN


**cat /etc/stinit.def shows**
# This file contains example definitions for different kinds of tape
# devices.
#
# You can find some examples in /usr/share/doc/mt-st/examples.
#
# Common definitions to be applied to all tape devices
# (This is the driver's default)
{buffer-writes read-ahead async-writes}

I can't think of any info you might need. I really appreciate any help someone can give.

No hurry but I would like to get it done in the next 5 minutes. (lol)

Again, great HOWTO. Couldn't have done it with out you and learned a few things in the process.

***_alabamaXslim_***

---

### Post by adam0509 on 2007-02-10
I personally use **LinNeighborhood** who works perfectly (universe or multiverse). It's like a Grafical Gui for samba....



<code>$ sudo apt-get install linneighborhood smbfs samba</code>

you need to do this to make it works :

<code>$ sudo chmod u+x /usr/bin/smbmnt</code>
<code>$ sudo chmod u+s /usr/bin/smbmnt</code>
<code>$ sudo chmod u+x /usr/bin/smbumount</code>
<code>$ sudo chmod u+s /usr/bin/smbumount</code>

---

### Post by lukem on 2007-02-10
Thank you very much Stormbringer.  I only read the first 2 pages of the thread but I'm up and sharing and sharing the printer as well.  Excellent Job. 

Thanks
Luke

---

### Post by fcerullo on 2007-02-11
Hey Man!

Your guide worked like a charm! Thanks a mil.. I was struggling with SMB for a couple of days...

Fabio

---

### Post by spartan777 on 2007-02-11
excellent how-to. the only thing is that I'd like for everyone to read my files, it seems that I have to allow people on a person-by-person basis by adding each username and password. can I just allow everyone to bypass this and read my files?

---

### Post by xpan on 2007-02-11
Hi, 

My simple home network was working fine before the latest update of samba. Even network printing was working.

Please help. Here is my samba configuration. Neither can I see my windows shares, nor the windows user can see mine (it was working before). It is as if my two computers (ubuntu and MSXP) see different "home" workgroups...

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   netbios name = xpan-laptop
   workgroup = Home
   hosts allow = 127.192.168.1.65
   browsable = yes

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
;   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = yes
   guest ok = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[public]
path = /home/xpan/public
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
invalid users = 
read only = no



[downloads]
path = /home/xpan/downloads
available = yes
browsable = yes
public = yes
writable = no

```

---

### Post by serlex on 2007-02-11
samba really needs work, sometimes works sometimes does not!

---

### Post by xpan on 2007-02-11
ok, I installed gsambad and tried to work with the GUI.

It seems that now I can browse through the shared printers and folders but I cannot see their contents. Even in the public folder. I also cannot print (windows says that it is not allowed)

This is my new samba configuration:

```

[global]
netbios name = xpan-laptop
server string = 
workgroup = home
hosts allow = 127. 192.168.1.
printcap name = /etc/printcap
load printers = yes
printing = cups
cups options = raw
log file = /var/log/samba/samba.log
max log size = 1000
security = share
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M %u
smb passwd file = /etc/samba/smbpasswd
encrypt passwords = yes
unix password sync = no
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
interfaces = 127.0.0.1/8 192.168.1.0/24 
remote browse sync = 192.168.1.1
remote announce = 192.168.1.1
local master = no
os level = 33
domain master = no
preferred master = no
time server = no
domain logons = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = no
winbind use default domain = yes
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

[public]
path = /home/public
comment = Public Folder
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes

```

I know I am really getting close. Any tips would be appreciated.

---

### Post by lamalex on 2007-02-12
I can get to windows from ubuntu no problem, but not the other way around, my username and password don't work and I can't figure out why. I've tried a couple different users none of them work. Any ideas?

---

### Post by xpan on 2007-02-13
please attach your /etc/samba/smb.conf file

---

### Post by Word on 2007-02-13
I followed the howto but I still can not access the file from a windows machine it ask for a password. I made a smb user account. Here is my smb file

[global]
    ; General server settings
    netbios name = Magrathea
    server string =
    workgroup = pattonhome
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Magrathea]
    path = /storage
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = kweli
    force group = pattonhome
**************************************
Domain=[PATTONHOME] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          IPC       IPC Service ()
        IPC$            IPC       IPC Service ()
        Magrathea       Disk      
        print$          Disk      
Domain=[PATTONHOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        KWELIVIAO            
        MAGRATHEA            
        USER                 

        Workgroup            Master
        ---------            -------
        PATTONHOME           MAGRATHEA

**********************************************
Whats wrong?

---

### Post by xpan on 2007-02-14
why don't you try security = share. 

It is not so safe, but it is fine for a small home network.

---

### Post by Word on 2007-02-15
that does not work either

---

### Post by TomFumb on 2007-02-15
wow thanks, really good howto - I was dreading having to do this one day as I'm pretty new to Linux. You've really helped me out - great work

---

### Post by Obor on 2007-02-16
Thanks for the guide. I went through the ubuntu part but I'm stuck on the windows part. I'm running Windows 2000 through Vmware and I can't find anything that will be equal to "map network drive" in XP. :confused: 

Anyone with Windows 2000 that wants to point me in the right direction?

---

### Post by marcud on 2007-02-18
hi and thankyou
i am no good with computers but i have now managed to set up half my network, my windows computer can see my ubuntu but ubuntu cannot see windows.

Now i am not an expert so i may have for gotten to look somewhere or do something could you help?

thanks

---

### Post by marcud on 2007-02-18
hi and thanks
i am a non computer expert and i have set up my network but my ubuntu will not see my windows can you help or have i missed something?

Thanks
you may of got a similar quote recently i think i posted two opps!

---

### Post by xpan on 2007-02-18
> **marcud said:**
> hi and thanks
i am a non computer expert and i have set up my network but my ubuntu will not see my windows can you help or have i missed something?

Thanks
you may of got a similar quote recently i think i posted two opps!

have you "shared" a folder in windows? 

Are you sure that windows and linux "see" the same workgroup?

---

### Post by Robin T Cox on 2007-02-18
> **Obor said:**
> Thanks for the guide. I went through the ubuntu part but I'm stuck on the windows part. I'm running Windows 2000 through Vmware and I can't find anything that will be equal to "map network drive" in XP. :confused: 

Anyone with Windows 2000 that wants to point me in the right direction?

Just right-click the Windows 2000 desktop icon labelled 'My Network Places', and 'Map Network Drive' is the fifth item in the menu that appears.

---

### Post by lolwhites on 2007-02-24
I went throught the guide and got stuck on the Windows part. Which IP should I set on the Windows network connection? Went to System=>Administration=>Networking and checked the properties of eth1 and eth0 but it says configuartion is automatic. The "Hosts" tab in the same window give a variety of IP addresses but the only ones that look right (127.0.0.1 and 127.0.1.1) don't seem to work when I type then into the right spot on the Windows PC.

Edit - I tried typing *ifconfig* into terminal and got another inet address for eth1 but using that doesn't work either.

---

### Post by rggavubt on 2007-02-26
When I do your last step before you start Samba, I get this :

chmod: cannot access `/media/samba': No such file or directory

What did I do wrong??

---

### Post by rggavubt on 2007-02-26
> **rggavubt said:**
> When I do your last step before you start Samba, I get this :

chmod: cannot access `/media/samba': No such file or directory

What did I do wrong??

Cancel this question.  I had changed directory to /home/samba and didn't put in the request with that new path....I got it work when I updated the path in the command.

---

### Post by els on 2007-02-28
Thanks!

---

### Post by jingo811 on 2007-03-02
```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```
When you do this ADD USER part, how can I manage the users that has been added?
What file controls this?
For instance a Win XP user that I have added how do I know what permission they belong to:
OWNER, GROUP or OTHERS?
How can I make the Win XP switch from one permission category to another?

---

### Post by blenderfish on 2007-03-12
Thank you for the how-to.  So my questions is  what if I have multiple drives mounted that I want to share?  I have one drive, .media.hda3 that I have shared successfully, but I also want to share /media/hdb1.  How do I go about adding this into the .config that is in the how-to?

---

### Post by zapcojake on 2007-03-13
Hello, I followed this howto and it worked great.  The only problem I am having is that the harddrive on the Ubuntu server box runs constantly.  What is causing this and how do I fix this?

---

### Post by kptracey on 2007-03-20
Stormbringer,

Please add 'turn off your firewall' to your tutorial. I've spent days trying to get Samba up all the while forgetting about setting up firestarter during first install.

As soon as I turned off my firewall everything worked without a hitch. 

EDIT: I should add that I restarted my firewall and gave my laptop access.

Cheers,

Kieran

---

### Post by bpsg119 on 2007-03-24
Strombringer thank you for the howto-- its helped immensely.

I did run into an issue which I am circumnavigating currently with what I believe is a less than ideal solution.

I installed ubuntu on an old computer to use as a dedicated filesever. I have several windows XP boxes that will need to be able to access(read and write) storage drives in the computer(only have one at the moment).

Stupidly, all my windows machines use a main account, and this just happens to be my full name, so the userid looks like: "Firstname Lastname". Passwords are the same.

Using your guide I was able to get the share created on the linux end, but Ubuntu doesn't like having user accounts with spaces in the middle. I was able to do it, but the graphical user management program complains every time I look at this account I created. This works, but I'm under the impression that the /etc/samba/smbusers file offers a better solution to deal with accounts with spaces than having user accounts with spaces in ubuntu.

I followed the instructions in the first post but can't get it working unless I have a user account in ubuntu with userid- "Firstname Lastname".
Here is what I have tried:
created a user on the ubuntu system that's a single word, for example 'foo'
sudo useradd -s /bin/true foo
sudo smbpasswd -L -a foo
sudo smbpasswd -L -e foo

In the /etc/samba/smbusers file I entered
foo = "Firstname Lastname"

the password for foo is the same as the password for accounts "Firstname Lastname" on my XP machines.
---restart the samba server

In XP, when I go to connect/map the share, I am promted for a password. I've entered everything I can think of; entering-- Firstname Lastname  and associated password and foo with password both fail. What does work is entering the userid/password for the administrator account I use in ubuntu. 

My smb.conf file looks like that in the first post of the thread with changes made to reflect the name of the share, server, workgroup, etc. 

Any idea why this doesn't work? For the time being it appears to be working with a user "Firstname Lastname" created on the ubuntu system with password, but it just doesn't seem right to have the space in there for this.

I appreciate any feedback

---

### Post by Charlie Evatt on 2007-03-26
Hi there, thanks for the great HowTo, I have managed to get the file-sharing working from Ubuntu desktop accessible from my Windows and Mac computers. 

However there is one slight issue - 

* I have 3 shared folders - one for each member of my household
* Whichever user I log into the server with (server name:renaissance), I can access ANY of the shares, which should not be the case.

My system log tells me that it cannot find smbpasswd.... Where are these files stored, and what is happening? Can you help me? Thanks

---

### Post by tallguyII on 2007-03-29
Thanks for this great tutorial. I got most everything working and can see the windows shared folders but:

I can't play an mp3 file from the shared folder but I can copy it to my desktop and then play it? What do I need to be able to use files from shares without coping them?

Also how do I start Samba at each reboot?

Thanks again for a great tutorial, Rich

---

### Post by dvdragon on 2007-03-31
Your guide was very helpful. Thank you!

---

### Post by kostkon on 2007-04-07
Great guide!! Many thanks!! I'm going to make a file server soon and surely I'll use this lovely guide.

---

### Post by Veer on 2007-04-11
Just wanted to drop a quick thanks to Stormbringer for the awesome howto.


Works great!

---

### Post by kapampa on 2007-04-19
Thanks!! An excelent work!!

---

### Post by nickpaton on 2007-04-21
Works great in Feisty 

Many thanks!

---

### Post by nickpaton on 2007-04-21
> **kptracey said:**
> Stormbringer,

Please add 'turn off your firewall' to your tutorial. I've spent days trying to get Samba up all the while forgetting about setting up firestarter during first install.

As soon as I turned off my firewall everything worked without a hitch. 

EDIT: I should add that I restarted my firewall and gave my laptop access.

Cheers,

Kieran

Realise you posted some time ago, but it will assist others as well.

First thing to be aware of is that you need to have a static or reserved IP address for your XP PC to which you want to connect, or else you will need to reconfigure Firestarter for each session.

To do this, see my general notes below setting up Firestarter. 

To use via an activated firewall.

Assume using Firestarter as GUI.

If it's not already installed, load via Synaptic.

Firestarter Wizard settings:

Detected Device(s) - select the one you are currently using - mine is wireless and is called Eth1

Skip Enable Internet sharing page

Select Start Firewall now button.

Save

System>Administration>Firestarter

Policy Tab > Editing "Inbound traffic policy"

Click inside "Allow connections from host" box.  Green Add Rule symbol will appear.

Click on Add Rule > Allow connections from: and in IP, host or network host box, add the IP address of your XP PC.

Don't bother with any comments.

Click on Add, and your XP PC will now be allowed access to through the firewall.

[COLOR="Black"]_General note on IP addresses for PC's._[/COLOR]

It is a good idea to make sure that the same IP is assigned to each PC whether Linux or Windows when they are switched on each time.

To do this go into your modem router settings and find a page which will have a heading similar to "LAN IP Setup" (this is title for Netgear router).

Tick the box for "Use Router as DHCP Server" and assign a sufficient range of IP addresses to cover the number of PC's you have on your network.
Example:

My router IP address is 192.168.0.1

I have 4 PC's / laptops running a mixture of Linux and Windows.

The range of assigned IP addresses therefore will be:

Lowest: 192.168.0.2
Highest: 192.168.0.5

Click on Apply button

Close down the router config window (it may crash since the PC you have been using to configure it may now have a different IP address.

Reboot all PC's.

Reopen the Router settings pages and go to LAN IP setup page again.

On Netgear routers on this page, there is a section "Address Reservation" - click on Add and the new page will have each of your started PC's listed with an IP and MAC address assigned.

For each PC select the PC with a bullet and click on Add.  leave the PC you are accessing the Netgear router settings until last.
When all have been added and shown in the Address Reservation list, click Apply.

The settings page will crash now for sure but when it does, simply restart all PC's, enter the Router Settings pages and confirm that each PC address is listed as being assigned.

By doing this you will always guarantee that each PC is seen as having a static IP address within the network.

Whilst you are in the router settings, you may want to add some extra security by changing the default IP address of your router.  This is to prevent hackers getting into your system by trying the manufacturers default IP addresses to access your network.
This is done (for Netgear routers) once again on the LAN IP Setup page, under LAN TC/IP Setup box.
Simply change the existing address to something like 10.0.0.200 (not mine BTW!), but remember that you will have to then adjust the address reservations of each PC to start from 10.0.0.201.

Also it's a very good idea to change the default password to access the router settings and this on Netgear routers is under the Set Password page.

To assist in remembering your new default IP address and password, write them on the router base.

HTH and apologies for the length of this!

---

### Post by Stepes on 2007-04-26
Sorry if it has been asked before but I searched a bit and couldn't find a solution.

I get the typical cant find destination when trying to map it in windows. I have same usernames on both pcs. I set in samba the pass of my win pc which is empty. Also I can ping the windows machine from linux :/ what is wrong? 

named the laptop STEFKUBUNTU and tried to map: \\STEFKUBUNTU\MyFiles\ , \\STEFKUBUNTU\MyFiles\home\samba , \\STEFKUBUNTU\MyFiles\samba , \\STEFKUBUNTU\home\samba , \\STEFKUBUNTU\~\home\samba :P nothing  worked

Thanks alot

---

### Post by jwjazz on 2007-05-02
Hi,
thanks for the tutorial.  i am having some problems though.  I went thru the first time and everything worked.  Then something changed on my linux machine and now i can't get windows to map a network drive.  i tried using wins and without.  Sometimes windows can see the linux machine in the workgroup, but it says i cannot access the server.  even though i have added the username and password from windows.  In my modems setup page, it shows both computers and lists their ip addresses, and also the names of both machines.  But neither machine can see the other one. 
The only error message I get is when I login to ubuntu, it says the $Home folder's .dmrc file is being ignored, and something about it not saving the session and language information.  And that the user must own the folder and so on.  I made sure that the user owns the folder by looging in as root and changing the permission to the regular user.  i don't know how it got changed in the first place.  Anyway, this seems unrelated, but it's the only difference i can think of.  Can anybody help a frustrated user?

Thanks

---

### Post by navlelo on 2007-05-02
> **jwjazz said:**
>  Can anybody help a frustrated user?
I'm not an experienced Linux user and may be very wrong, but it sounds to me as if you have given wrong permissions to one or more files. You should check permissions for both samba files and /home files.

---

### Post by jwjazz on 2007-05-03
I checked the file permissions and they are correct.  Not sure why i am getting that error message that the owner is not the user.  I have managed to setup a network with one limitation.  Ubuntu cannot see the windows xp machine, but from the xp side everything is good.  Any ideas on what's wrong?

---

### Post by flade on 2007-05-05
I there a way to use quota with samba. Or is this used only on system accounts ?

I want to limit folder size to users.


reg,

---

### Post by kenrowe410 on 2007-05-05
> **jwjazz said:**
> I checked the file permissions and they are correct.  Not sure why i am getting that error message that the owner is not the user.  I have managed to setup a network with one limitation.  Ubuntu cannot see the windows xp machine, but from the xp side everything is good.  Any ideas on what's wrong?

   Same problem for me.  Everything seems to be set up according to this HOWTO, but no luck seeing the XP shares on my Ubuntu machine.  Anyone have any insight?

Thanks in advance,

Ken

---

### Post by Erlander on 2007-05-06
> **jwjazz said:**
> I checked the file permissions and they are correct.  Not sure why i am getting that error message that the owner is not the user.  I have managed to setup a network with one limitation.  Ubuntu cannot see the windows xp machine, but from the xp side everything is good.  Any ideas on what's wrong?

Every time I've tried to setup a Samba network I've had the above situation between my Ubuntu pc and my Windows XP Home pc but not with my wife's XP Pro notebook.

I beleive it is a function of the cutdown network support in XP Home.  My solution has been to dual boot the XP Home pc using Feisty.  With SSH Client and Server installed on both I can browse to my hearts content provided the dual boot was booted with Ubuntu which is how it now is 95% of the time.

Rob

---

### Post by nrune on 2007-05-06
Thanks for the how to, has made my life much easier!

---

### Post by bsm1th on 2007-05-06
If I remember from my Microsh*t days, for a workgroup name, there is a difference between Home and home. Try making sure all computers use the same spelling, even caps. Samba may have realized this in the last update

                           Worth a try..

                            Bob <bsm1th@charter.net>

---

### Post by XTREEM|RAGE on 2007-05-09
a great tutorial, that works even for noobs like me :D :lolflag:

---

### Post by Fraoch on 2007-05-10
Does this setup work in Feisty?

I set it up, everything works fine, on reboot smb.conf gets rewritten with settings that break everything.

How can I tell Feisty not to screw with smb.conf?

---

### Post by LegoAddict on 2007-05-10
It works in Feisty. (note:  I did it up to the part where you have to fool in Windows.  Then I stopped, still works)

I just came from doing it.  My Ubuntu laptop was trying to join the home network that all the Windows boxes were hooked into and working fine (although there were some little quirky bits we've never been able to get rid of).  I couldn't share files with either the three XP computers or the XP running under a VM in Ubuntu.  Now the VM can share files with my laptop and Ubuntu can share files with all but one computer (which is the quirky one and is going to be reformatted soon anyways).


Great guide, very well explained, easy to follow even for a newbie like myself


Thanks a tonne

---

### Post by Fraoch on 2007-05-10
Oh, it works fine when you set it up according to this guide, but Feisty thinks it's smarter than you are and will helpfully rewrite smb.conf on reboot, screwing up all the settings.

I'm thinking of making smb.conf read-only, but it probably makes its changes as root so that may not help.

---

### Post by LegoAddict on 2007-05-11
Hmmm...


I rebooted and Samba is working better than ever (literally... my quirky computer can find it now)

---

### Post by Fraoch on 2007-05-11
Has your smb.conf changed?  Mine gets about 5 lines added to it which, among other things, makes the samba share read-only.

---

### Post by twinax on 2007-05-11
Hi Stormbringer
I used your guide , and it is very good, thanks. I do need a little more security though, or maybe I am missing something.  For our company this is going to be where we share files. But there is going to be folders that only certain people can get into.  

I have created the folders and the users as per guide , but all users have access to all folders. I tried using web admin, but even if I chose ggroen as a valid user for "accounting" folder , , when I try to access it shows incorecct password or username.  

Any ideas would be much appreciated.
Thanks

---

### Post by LegoAddict on 2007-05-11
There was a small quirk where my shared folder (I later added my Home) "Feisty" was only browsable.  Of course, I don't remember changing anything, so this is probably me just overlooking something, as everything is working fine for me.

---

### Post by Fraoch on 2007-05-11
Guess I'm alone on this one. :( Thanks.

---

### Post by scott_rodgers100 on 2007-05-15
I think I'm trying to do something simple, but it's not working and I'm a newbie with linux so messing with all the config files listed here makes me nervous.  All I'm trying to do at this point it to create several linux file servers to replace some windows 2000 servers.  All they do is share a directory.  What I did:

From Linux

Installed Ubutu from CD on a test machine (static IP)
Created a folder called "share" on the desktop
Shared the folder through the sharing option

From Windows XP:

Map Network Drive
\\11.11.11.11\share

XP Finds it fine but asks for an ID and password ... I put my linux user name and password in with no luck.  Then started messing with user accounts / the stuff listed here etc .... then the share wouldn't work at all.

Is there a simple way to make this work?  What user and password is WP looking for here and where do I set it up?

---

### Post by Fraoch on 2007-05-16
> **scott_rodgers100 said:**
> I think I'm trying to do something simple, but it's not working and I'm a newbie with linux so messing with all the config files listed here makes me nervous.  All I'm trying to do at this point it to create several linux file servers to replace some windows 2000 servers.  All they do is share a directory.  What I did:

From Linux

Installed Ubutu from CD on a test machine (static IP)
Created a folder called "share" on the desktop
Shared the folder through the sharing option

From Windows XP:

Map Network Drive
\\11.11.11.11\share

XP Finds it fine but asks for an ID and password ... I put my linux user name and password in with no luck.  Then started messing with user accounts / the stuff listed here etc .... then the share wouldn't work at all.

Is there a simple way to make this work?  What user and password is WP looking for here and where do I set it up?

I would start over from scratch, following the exact steps in this howto.

---

### Post by Fraoch on 2007-05-16
> **Fraoch said:**
> Guess I'm alone on this one. :( Thanks.

Thankfully, once I changed it back, Ubuntu didn't change it again.  Working fine now.

I even got creative, changing the share name to "SambaShare" (yes, I know, I'm so adventurous!) and adding a separate share from an already-existing folder - just copy the "MyFiles" section and change the name and path.  Other PCs will now see two shares.  You can map them to drives in Windows if you want.

I have two Ubuntu PCs and one Windows laptop.  I had NFS working between the two Ubuntu PCs and that was FAST - files transferred at 93 Mbps, more or less saturating the 100 Mb connection.  Unfortunately samba is much slower at around 45 Mbps.  It's too bad, but my slower Ubuntu machine can't handle samba and NFS simultaneously (too much CPU and memory load) and since it needed samba to network with the Windows laptop I've settled on samba for networking.

---

### Post by scott_rodgers100 on 2007-05-16
I got this to work quite easily

Get a command box:

sudo /etc/init.d/samba stop
sudo gedit /etc/samba/smb.conf

find lines that look like these:

"security=share"  "encrypt passwords=no" 

Just before the line type: "; I'm changing this"
Then put a ; in front of the "security=****" line
Then type in the "security=share" line
Do the same thing for the "encrypt passwords" line

save the file

sudo /etc/init.d/samba start

---

### Post by Alex99 on 2007-05-20
Hi, servus,

again thanks for a very helpful howto. I can now access my ubuntu files from my vista machine. However, the other way around it doesn't work. Could you point me in the right direction please?

Ubuntu Edgy
Windows Vista
Private WLAN network
under Places > Network Servers I see the windows machine, but I can't log in.  When I insert my IP-address in windows (under TCP/IP > Properties > advanced >WINS), I no longer see it.

Thankful for every hint! Alex

---

### Post by vladimiroane on 2007-05-21
Everything was fine until one day it stooped working. I can not longer see my Windows shares although I don't have any problem accessing my Ubuntu box from Windows. Any idea what might have happened. 

Since then I did all the steps in the tutorial once again but no luck. In nautilus under network, windows network there is nothing.

---

### Post by kanna1620 on 2007-05-22
> **Stormbringer said:**
> **HOWTO: Setup Samba peer-to-peer with Windows**


Really a nice and good How to. Thank you.

---

### Post by xwisdom on 2007-05-25
Hi,

This is a very nice tutorial. Many thanks. 

I just have one question:

Can Samba be configured to athenticate it's user via the ubuntu user database? In other words, I would just like to be able to user Ubuntu to create the user and then had samba validate the network user without me having to create a new samba user (using smbpasswd) that matches the new ubuntu user.

Is this possible? Any pointers, suggestions?

---

### Post by plech.d on 2007-05-26
Hi, thanks a lot for pasting this tutorial, but I seem to be having a problem right at the very beginning.

I installed Ubuntu Feisty Fawn on my laptop. The first thing I did after installation was that I started the terminal and wrote "sudo apt-get install samba". This told me that samba was not available, but that another package - samba-common - replaced it. So I tried to write "sudo apt-get install samba-common", which told me that I've already got the newest version installed.

So then I went on with your tutorial and tried to stop samba by typing "sudo /etc/init.d/samba stop" but found that there was no file called "samba" in the init.d directory. Nothing called anything similar to Samba was there.

Can you help me with this? Is it possible that the Ubuntu CD I downloaded misses Samba??

Thanks very much for your reply

---

### Post by fredde_firebug on 2007-06-03
I'm getting message gedit: command not found when i type    sudo gedit /etc/samba/smb.conf
I have also tried kate

---

### Post by Shampyon on 2007-06-04
> **fredde_firebug said:**
> I'm getting message gedit: command not found when i type    sudo gedit /etc/samba/smb.conf
I have also tried kate

Are you on xUbuntu? If so, try *sudo mousepad /etc/samba/smb.conf*

---

### Post by dene on 2007-06-05
Hi all,
A very new newbie, I've had 30 years experience with computers from CP/M to Win 98, and have  recently converted to linux, choosing kubunto 6.0.6 LTS.

As I still have legacy PC's running WIN 9x, I want to share files. I can see and get files from the windows machines using konqueror but can't make the linux machine visible on the windows network.

when I try the "stop" or "start"  commands on samba i get;

"dene@dene-laptop:~$ sudo /etc/init.d/samba start
Password:
sudo: /etc/init.d/samba: command not found
dene@dene-laptop:~$"

... what's the next step please? I don't even know how to search for the executable using "ls" or even what I should be looking for. I've checked using the adapt manager to make sure samba is installed. ... help please

Dene

---

### Post by Speedoo on 2007-06-06
Hi Stormbringer,
I'm a complete linux noob trying to add my Ubuntu box to my network.  I followed your instructions, and sure enough, I now have an entry in my Windows Explorer called "MyFiles on <ipaddress> (Z:).  However, this drive shows up as blank.  I went back to the linux machine, thinking I'd find an empty directory at /home/myfiles, but no luck.  Am I supposed to be seeing my linux files on my Windows machine?  Or do I need to move files I want to share to a specific place in Ubuntu?  And if so, where?  Also, I'm still not able to access the printer on my linux machine from my Windows laptop.
Thanks for bearing with an amateur!

Speedoo

---

### Post by Speedoo on 2007-06-06
Oops, I think I answered my own question.  Apparently all I had to do was SHARE to SMB the linux directory I want to share.  Oddly enough, sharing a directory actually enabled network printing as well!  Don't understand it, but it seems to be working.  Thanks for all the time you put into helping us noobs!

---

### Post by Draugauth on 2007-06-08
> **dene said:**
> Hi all,
A very new newbie, I've had 30 years experience with computers from CP/M to Win 98, and have  recently converted to linux, choosing kubunto 6.0.6 LTS.

As I still have legacy PC's running WIN 9x, I want to share files. I can see and get files from the windows machines using konqueror but can't make the linux machine visible on the windows network.

when I try the "stop" or "start"  commands on samba i get;

"dene@dene-laptop:~$ sudo /etc/init.d/samba start
Password:
sudo: /etc/init.d/samba: command not found
dene@dene-laptop:~$"

... what's the next step please? I don't even know how to search for the executable using "ls" or even what I should be looking for. I've checked using the adapt manager to make sure samba is installed. ... help please

Dene

it is sudo /etc/init.d/samba restart
or at least that is how I restart samba after making changes.
Make sure you have Samba  installed though.  Other than that I am new myself and running into some problems so not sure how much help I will be.

---

### Post by Draugauth on 2007-06-08
First off let me say that that was an awesome guide and wish I had found it a couple weeks back.

But now I have a new problem.

I can read the whole share but I can only write to the root directory of the share.  Example

[Multimedia]
  path = /media/multimedia
  browseable = yes
  read only = no
  guest ok = no
  create mask = 0644
  directory mask = 0755
  writable = yes
  write list = user_name
  valid users = user_name


Now I can write and delete files that are the "root directory" for the share but any sub-directories I am denied although I can read the files just fine.

How can I fix that?

Also due to the fact that I have friends that come over etc and need access to the shares is there a way to setup groups and make it so that only certain groups can read/write or just read?

Oh and one last thing.
My roommate and I fix windows computers all the time.  As such I have 1 share that is as follows

[Backup]
  path = /media/backup
  browseable = yes
  read only = no
  guest ok = yes
  create mask = 0777
  directory mask = 0777
  writable = yes
  public = yes

However no one can seem to access it period.  Any suggestions?

Again thank you for all the hardwork you have done with this stuff.  It has really helped me out a lot.

I have tried reading the mans but I am one of those that can't make heads or tails out of instructional manuals but once I see a good example or am shown how to remember it like an elephant ;)

---

### Post by ukripper on 2007-06-09
Nice guide mate. Keep it up with good work.

---

### Post by Neurasthenic on 2007-06-09
Hi, thanks for the guide! I'm pretty new and have been wondering how to set up file sharing between my computers. 

I followed the guide and can see the other computer from both of my boxes (one Ubuntu, one Vista). The main thing I'm trying to do is access my music from the Vista system on my Ubuntu computer. So I navigate to the folder (Places > Network > PCNAME > My Music). Once I'm in there, I can see a list of all my folders, but I can't actually see what's inside them - even if I go in on the Windows machine and specifically share the individual folders. I get this error in Nautilus when I try to view a folder that I've specifically shared: "The folder contents could not be displayed."
If I try to view a folder that is not specifically shared, but is inside the shared My Music folder, I get this error: "Nautilus cannot display "smb://nick-pc/My%20Music/Ayreon. Please select another viewer and try again."

Can anyone help figure out how I can get to my actual MP3's?

Edit: I download a Samba browser, and can now see my MP3's - but my new question is, why could I not see them before? What is the Nautilus browser doing differently than this new program?

---

### Post by arobase on 2007-06-09
Nice guide , many thanks, worked perfectly for me on the last Ubuntu distribution

---

### Post by volksman on 2007-06-11
This might sound weird but what happens if you remove any windows boxes from the network and only have samba running on linux boxes?

Does there need to be a windows box to have the master browser or whatever its called?

---

### Post by volksman on 2007-06-11
I'm good...the answer to the above is yes (sorta).  There has to be a master browser.  So you can configure Samba to do so if you have no windows boxes left in your network.

---

### Post by Erlander on 2007-06-11
> **volksman said:**
> This might sound weird but what happens if you remove any windows boxes from the network and only have samba running on linux boxes?

Does there need to be a windows box to have the master browser or whatever its called?

I have a dual boot (Windows & Ubuntu) pc, another Ubuntu pc and a Windows laptop on a network.  When only running the 2 pc's under Ubuntu I find SSH better.  I just installed SSH client and server on each.  Works well.

Rob

---

### Post by ukripper on 2007-06-12
SMB protocol works great even without windows boxes. I mostly use print server and two other ubuntu boxes configured with samba, works without any glitch (perfect is the word).

---

### Post by lamadredelsapo on 2007-06-15
Great how to! I have been looking for this quite a long time

---

### Post by joeygreen on 2007-06-15
Thank you so much for putting this together, it was beyond helpful.

---

### Post by shane2peru on 2007-06-21
First of all thanks for this tutorial!!!  Now I have one small problem that has probably been addressed (I'm sorry I didn't read all 18 pages of this thread).  Perhaps you may want to include a little note about this issue if it has been dealt with in the past.  I have Kubuntu 7.04 (Fiesty) and Windows XP box.  I believe my problem is that the user name and the password is different for both computers.  Is there any way to deal with this, or do I need to change settings on one or the other?  
Ex.
username for XP = george 
password for XP = dumbquestion
username for Ubuntu= frank 
password for Ubuntu=hereitis.


Thanks.

Shane

---

### Post by bren on 2007-06-21
hi shane

you are nearly there....
there is an easy way to sort this and it is described elsewhere but to repeat..... (:-))

you need to set up a samba user now you have

username for XP = george
password for XP = dumbquestion
username for Ubuntu= frank
password for Ubuntu=hereitis
username for samba = george
password for george = dumbquestion

now when you ask samba to speak to the windows box it logs in with your usual name / pass

go back to the tutorials and look for the bit where its got code like

samba add user ..........

and give the xp details to the samba user

hope that helps

bren

---

### Post by shane2peru on 2007-06-21
> **bren said:**
> hi shane

you are nearly there....
there is an easy way to sort this and it is described elsewhere but to repeat..... (:-))

you need to set up a samba user now you have

username for XP = george
password for XP = dumbquestion
username for Ubuntu= frank
password for Ubuntu=hereitis
username for samba = george
password for george = dumbquestion

now when you ask samba to speak to the windows box it logs in with your usual name / pass

go back to the tutorials and look for the bit where its got code like

samba add user ..........

and give the xp details to the samba user

hope that helps

bren
Bren,

Thanks for the quick response.  What I did was ran that add user line twice, once for my Ubuntu username & password and once for my Windows username & password, then when I ran that other command listed somewhere in this thread and get this response: ```
smbclient -L localhost -U%
Domain=[RICES] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service ()
Domain=[RICES] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------
        COMPAQ               Kat's Compaq
        KUBUNTU

        Workgroup            Master
        ---------            -------
        RICES                KUBUNTU

```
which lists both computers.  When I open konqueror and go to the remote places I can see the other computer Compaq (XP) when I click on it, I can't see anything.  When I open My Network Places on the XP computer I can't even see the Ubuntu computer.  I really don't understand all this.  I disabled the firewall on the XP computer to see if it works and still can't see anything.  Here is my config file too:  ```

[global]
    ; General server settings
    netbios name = Kubuntu
    server string =
    workgroup = RICES
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/shane/share/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = shane
    force group = shane

```
Any help would be greatly appreciated.  :)  Thanks. 

Shane

---

### Post by bren on 2007-06-21
> What I did was ran that add user line twice, once for my Ubuntu username & password and once for my Windows username & password

why did you do that?
you need to remove the ubuntu username one I think????

if that doesn't work then start from the beginning .....
follow strormbringers very easy to follow step-by-step tutorial
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)
don't do anything extra this time!

your config looks ok ....

bren

---

### Post by shane2peru on 2007-06-21
> **bren said:**
> why did you do that?
you need to remove the ubuntu username one I think????

if that doesn't work then start from the beginning .....
follow strormbringers very easy to follow step-by-step tutorial
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)
don't do anything extra this time!

your config looks ok ....

bren

Well, Um, not sure why I did that :redface: .  I think I did it after things didn't work right, I figured I needed to add a few users, one for the Windows and one for the Ubuntu seeing how it wasn't covered in the how to, (with different user names and passwords).  I would not have a problem removing them, but how??? :confused:  The add command and enable command is there, but nothing about removing people. :)  I can purge my Samba installation and then start over,  would that purge the users too?  I get confused when it gets to the password and users because I don't know what password and usernames to use?  Ok, from now on we can refer to the Windows UAP (Username and Password) and the Ubuntu UAP, and then there is a Samba UAP?  ???  Any ideas?  
Thanks for the quick responses.  I'm awaiting the remove command.  :D

Shane

---

### Post by fast eddie on 2007-06-24
OK, I have set up as per instructions and I can see the Win XP machine from my Ubuntu pc but I cannot seem to map a drive, run Putty or WINSCP from my XP machine.

Can some one please give me some suggestions as to what I am doing wrong :confused:

---

### Post by mahasmb on 2007-06-26
I've got a little problem...

> maha@maha-laptop://$ sudo smbpasswd -L -a your_username
New SMB password:
Retype new SMB password:
[COLOR="Red"]Failed to modify password entry for user your_username[/COLOR]
maha@maha-laptop://$ 


*Edit: Silly, silly me. Replace 'your_username' with you know, your user name -_-;

---

### Post by howardf42 on 2007-06-26
Thank you StormBringer for an excellent How-to.  I hope that a year later you're still tracking this thread.  I went through your setup routine and after all is said and done,  I'm still not connected.  When I attempt to map the drive in Windows, after entering my username and password, I get a  message:  "The mapped network drive could not be created because the following error has occured:  An unexpected network error occured."

I've tried with and without WINS enabled and get the same results.  Any clues an what to look for now?

Thanks,
Howard

---

### Post by fast eddie on 2007-06-27
I am getting the same message as howardf42

---

### Post by Aksumka on 2007-06-28
Can someone help me out with this? 

I followed this How to, or a similar one months ago and it was working great. But the computer I was running it crashed so I had to reinstall ubuntu (6.06, 7.04 caused the crash). I now can not figure out how I had it set up. I have it working, i can connect to it, but I need a user name and password that I never set. I tried every username and password combo i have ever associated with the computer. 

Please help! It took me like 2 days just to get this computer up agian!

---

### Post by Tommy James on 2007-06-28
Cancel the request.   It was the old ID10T error.  Forgot to enter the gateway address when I made the IP address static.  Sorry for the post!

Thanks again for the How To ---- very helpful!


Good news/Bad News

Good news:  Followed the How To and sharing between my Work XP box and Ubuntu Personal Desktop  work great.  No issues.  The 3rd box, running xubuntu, is being used as a CUPS print server.  Everything is good there, too.  I can print from Ubuntu box to the xubuntu shared printer.  All boxes are on the same router.

Bad news: Internet would work now!?!  Any thoughts?  My xubuntu and XP systems can get to the net.  Its like something got turned off while I was doing my config.

Thanks everyone for the help.

Also, thanks for the How To very, very, easy to follow!

---

### Post by victorgreen on 2007-06-30
Stormbringer, you're a life saver. Samba works now!!

---

### Post by devillion on 2007-07-01
After following this guide using **live** 7.04, my samba network is up and visible, but i can't connect to it. When i attempt to "map network drive" in windows, i cannot login, and only get "an unknown network error has occured".

How can i diagnose what is going wrong, if windows isn't telling me?

---

### Post by chrisbain88 on 2007-07-02
Hi,
I have set up my samba share how this tutorial has said, and it works so i can see the share and contents that i could not before, however my problem arises as i can not copy to or from the share.  using my xp computer.  The copy finally comes up after sitting there for a while, and everytime the network connection disconnects and reconnects.
Does anyone have a solution.
Cheers
Chris

---

### Post by WebHorn on 2007-07-03
This guide was helpful, but I had a unique problem that took me a little while to figure out that I didn't see the answer for here.  Basically I wanted share-level behavior with user-level security.  I wanted any machine to be able to list the shares, and then have to authenticate if they needed more permissions to get into a more protected share (or not, if they were trying to get into a public share).

I wrote up a [more in-depth thread](http://ubuntuforums.org/showthread.php?t=490168) on the settings you will need to use to achieve this behavior.  Of course you could always use share-level security, but where's the fun in that?

---

### Post by warbread on 2007-07-05
Ok, so I've followed the How-to very closely, but am having problems mapping the network drive in Windows.  

I have the same user name and password for Windows as I have for samba, but it differs from my Linux password (user name is the same throughout)  I can see the samba share in the Windows network browser, but I can't access it.  The login prompt comes up, and I put my information in, but it acts as though the information is incorrect.  The box blinks, and then it comes back to asking me for my info.

Anyone know what the deal could be?

---

### Post by kenmonk on 2007-07-06
I've managed to get Samba working in the past, but am having problems with the current version - kubuntu. Checks (from information in the earlier massages) seem to suggest that it is a password problem as I can't change my smb password as a user.

The obvious thing to try, therefore, (or so it seemed) was to sudo to root and set it there (which I thought I had already done anyway.  The same problem still exists!!

I have put below a copy of the error message I get when I try to run:
                   smbclient -L localhost -U%
followed by my attempts to reset the password to something definite.  As   you can see, it still blows up in exactly the same way!

Anyone any suggestions as to what I'm doing wrong?

______________________________________________________________________
Terminal Copy
______________________________________________________________________
ken@Ken-MeshLaptop:~$ smbclient -L localhost -U%
Domain=[NORTONPHOTO] OS=[Unix] Server=[Samba 3.0.24]
tree connect failed: NT_STATUS_WRONG_PASSWORD
ken@Ken-MeshLaptop:~$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
machine 127.0.0.1 rejected the tconX on the IPC$ share. Error was : NT_STATUS_WRONG_PASSWORD.
Failed to change password for ken
ken@Ken-MeshLaptop:~$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
machine 127.0.0.1 rejected the tconX on the IPC$ share. Error was : NT_STATUS_WRONG_PASSWORD.
Failed to change password for ken
ken@Ken-MeshLaptop:~$ man smbpasswd
Reformatting smbpasswd(8), please wait...
ken@Ken-MeshLaptop:~$ sudo smbpasswd -a ken
New SMB password:
Retype new SMB password:
ken@Ken-MeshLaptop:~$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
machine 127.0.0.1 rejected the tconX on the IPC$ share. Error was : NT_STATUS_WRONG_PASSWORD.
Failed to change password for ken
ken@Ken-MeshLaptop:~$ smbclient -L localhost -U%
Domain=[NORTONPHOTO] OS=[Unix] Server=[Samba 3.0.24]
tree connect failed: NT_STATUS_WRONG_PASSWORD

---

### Post by warbread on 2007-07-07
> **warbread said:**
> Ok, so I've followed the How-to very closely, but am having problems mapping the network drive in Windows.  

I have the same user name and password for Windows as I have for samba, but it differs from my Linux password (user name is the same throughout)  I can see the samba share in the Windows network browser, but I can't access it.  The login prompt comes up, and I put my information in, but it acts as though the information is incorrect.  The box blinks, and then it comes back to asking me for my info.

Anyone know what the deal could be?

Well, I've solved my own problem, having just come back to it.  I had an entry in /etc/samba/smbusers from a previous set of instructions that was conflicting with this How-To.  I deleted the entry and everything works great.

---

### Post by spartan778 on 2007-07-10
First off I like to say this is an excellent tutorial. Next I got everything working perfect in windows however when I try to access my windows folders in kubuntu I get an error message that says "Could not connect to server WINDOWS Connection failed: NT_STATUS_CONNECTION_REFUSED". Is there something in kubuntu I failed to do, or it a windows problem. I am using XP home.

---

### Post by Depressed Man on 2007-07-11
This guide got it working for me... but one day it randomly stopped working (well the hostname part). So now I have to connect by IP address and not my hostname/MyFiles

Followed random posts thru searches, installed Winbind and still can't get my hostname working again.

---

### Post by delphiguy on 2007-07-12
I followed this guide before when I first tried using Dapper + VMWare and it worked, but now I tried it on my Feisty + VMWare can't seem to make it work.  All windows does is ask for a username and password, but when I provided the username and password that I have setup with samba it seems to fail and asks again.

Any ideas? maybe I may have missed something here.

thanks

---

### Post by dvenardos on 2007-07-15
Wow thanks, I was missing that enable user step. Between this and the samba configuration on OS X I was able to get it working the way I wanted.

It would be nice if Ubuntu had an option for windows file sharing like Mac OS X that automatically shared the home directories and would add any new users to the samba password file. This would cover the needs of almost all the average joes out there.

With Mac OS X all the wins stuff is totally uneeded. I can connect to by smb://machinename and everything works fine.

---

### Post by dvenardos on 2007-07-15
> **delphiguy said:**
> I followed this guide before when I first tried using Dapper + VMWare and it worked, but now I tried it on my Feisty + VMWare can't seem to make it work.  All windows does is ask for a username and password, but when I provided the username and password that I have setup with samba it seems to fail and asks again.

Any ideas? maybe I may have missed something here.


I had problems with VmWare and samba also it appears that there is a bug in the current vmWare player when using bridged networking, more info on the vmware forums. I switched to NAT and everything worked fine.

---

### Post by rboothe on 2007-07-16
I'm very new to ubuntu and have been trying for some time to have the other windows based machines "see" & browse the ubuntu machine and vice versa.

I've read the thread but got stuck where you adives to "open a terminal".  How do i open a terninal ??? I started "Terminal server client" but didn't have a clue regarding what to enter in the dialog boxes (i.e what goes in "computer", "domain", "client hostname"....etc ???

---

### Post by Depressed Man on 2007-07-17
If you are using gnome press alt+f2 and type this in gnome-terminal

Or click accessories > terminal from the menu bar.

---

### Post by musicarvind on 2007-07-25
Hi thank u sooooooooo much for this tutorial. The main reason for running samba was to share my printer and it worked.  

However my Linux box shows on my XP computer. It shows the printer. of which was ideal and works YAY!. but .. it also has a folder MyFiles.  I click on it and it says that you do not have permission. Contact your administrator etc etc etc.  My question is how come it does not show the folder \\ARVIND\home\samba\ of which i wrote in the config file of samba? 

thanks for any help.

---

### Post by CowzRule on 2007-07-26
> **musicarvind said:**
> Hi thank u sooooooooo much for this tutorial. The main reason for running samba was to share my printer and it worked.  

However my Linux box shows on my XP computer. It shows the printer. of which was ideal and works YAY!. but .. it also has a folder MyFiles.  I click on it and it says that you do not have permission. Contact your administrator etc etc etc.  My question is how come it does not show the folder \\ARVIND\home\samba\ of which i wrote in the config file of samba? 

thanks for any help.

I could be wrong, but shouldn't it be ```
/home/ARVIND/samba
```

---

### Post by girard on 2007-07-31
Hi. I've been reading the whole day, so pardon if I didn't have enough drive to read through the 30+ pages in this thread. 

I am able to access/copy/add files from the linux end of the network. But I am having trouble accessing linux from the XP end. I can see my FIESTY machine in the workgroups, but the folder MYFILES, I cannot access it. actually, it was there the first time, I couldn't access it, and then it disappeared. 

can anyone help me out? in what part of the tutorial did I set the "shared linux folder"? 

here's my smb.conf

> 
[global]
    ; General server settings
    netbios name = FIESTY
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = KUBLI
    force group = KUBLI
available = no
browsable = yes
public = no
writable = no


i'll try to find a solution, but any help would be appreciated... my eyes hurt already... thanks a lot....

---

### Post by girard on 2007-07-31
got it to work already!!! although i got lost in the process and i can't exactly share how i fixed it... i think it was the changes i made with my Netbios name and force user and force group. I changed everything into my login name... oh yeah... that's what it said in the tutorial right? lol. my bad. sorry.

this is so cool. thanks for this great tutorial! now i don't have to transfer files using my usb drive! haha!

---

### Post by microbyte on 2007-07-31
Wow! You're instructions are great! I can't say that it has worked *yet*, but that isn't your fault.

I'm going to try it again, and see what happens.

I did have one quick clarification question, though. You mention actually mounting folders as HDs (or something) on the PCs. I was wondering if that is necessary, or if I can just browse it like through* My Network Places* in XP. Would that work?

Thanks!

Added: Okay, I went and tried it again. It still doesn't work. I can see that my linux computer exists from my other PCs, but none of them can access it. I can't see anything under the Windows Network folder on my linux PC. I don't know if this will mean anything, but I was trying to do a simple VNC connection through my network, and that doesn't want to work either.

The only things I tried different this time was to do the actual user acount name of my XP computer, and not the netoworking PC name. Other than that, there wasn't anything to change. Oh, I forgot. I did it without WINS this time, as I think it messed up the internet connection on my linux PC when I gave it a static IP address.

Any Ideas?

---

### Post by girard on 2007-08-01
> **microbyte said:**
> Wow! You're instructions are great! I can't say that it has worked *yet*, but that isn't your fault.

I'm going to try it again, and see what happens.

I did have one quick clarification question, though. You mention actually mounting folders as HDs (or something) on the PCs. I was wondering if that is necessary, or if I can just browse it like through* My Network Places* in XP. Would that work?

Thanks!

Added: Okay, I went and tried it again. It still doesn't work. I can see that my linux computer exists from my other PCs, but none of them can access it. I can't see anything under the Windows Network folder on my linux PC. I don't know if this will mean anything, but I was trying to do a simple VNC connection through my network, and that doesn't want to work either.

The only things I tried different this time was to do the actual user acount name of my XP computer, and not the netoworking PC name. Other than that, there wasn't anything to change. Oh, I forgot. I did it without WINS this time, as I think it messed up the internet connection on my linux PC when I gave it a static IP address.

Any Ideas?

perhaps you could be experiencing the same slow loading of folders like i do... i thought at first that the network wasn't setup correctly because nothing was showing up. then i was forced to leave my desk after clicking on the share folders, when i came back it was there. that;s when i realized that i takes a really long time for the folders to load - which is different i think from a "slow network connection". that's because when they do get loaded, copying files are pretty normal. 

i haven't found a solution to this problem yet, nor has anyone replied to my thread. here:

[http://ubuntuforums.org/showthread.php?t=514916]("http://ubuntuforums.org/showthread.php?t=514916")

does your windows show limitied or no connectivity? i'm tracing the problem to this, since it makes sense for things to slow down when you have limited connectivity. 

has anyone experienced this?

---

### Post by befana on 2007-08-03
Thank you, Stormbringer!!!!
Your howto helped me.
I think it's great!

---

### Post by kgr132 on 2007-08-04
Awesome!
This HowTo worked like a charm. Many thanks.
-K-

---

### Post by gordon3913 on 2007-08-05
I followed your instructions and everything went great.
Thank you for a great tutorial.

---

### Post by TrashmanL on 2007-08-05
This HOWTO post is still working. I already had Samba installed, and used the Shared Folders GUI included in Feisty Fawn. I was reading my windows shares fine, but when I tried to see my Linux files on my Windows box, it kept asking me for a password (that didn't exist). I used the settings in smb.conf in this HOWTO and now everything works fine! Thanks!

---

### Post by zilch0 on 2007-08-05
Excellent guide, and thank you to everyone that contributed.  Saved me from a huge headache!  :-({|=

---

### Post by somafm on 2007-08-05
Great tutorial, worked just fine :)

---

### Post by harakiri1976 on 2007-08-07
Hi!

I followed this Tutorial... 

[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

..and when I go to 

 Places -> Network

 I can't see my Windows Computer or Folder to Share.

And it's the same thing in Windows. Can somebody give me some clues what is missing? I followed every steps very careful and I can't find why I can't share anything:(

---

### Post by rabideau on 2007-08-09
Excellent Help Video!:popcorn:

---

### Post by cooldudeny on 2007-08-10
ok so i saw this youtube video to set up the samba and how to edit the settings and how to share the folder but now when i go back to my wireless laptop and click on shared computer it ask me for the username and password and once i m done putting in the password 
it is showing me the shared folder but i m tryint to open the share folder it is giving me error 

[[IMG]http://img518.imageshack.us/img518/3726/errorjo6.th.jpg[/IMG]](http://img518.imageshack.us/my.php?image=errorjo6.jpg)

please tell me if i missed any steps while setting things up 

to give a overview of my network i have a pc and a laptop both running wireless router with dsl internet 

please help thanks

---

### Post by girard on 2007-08-10
is anyone experiencing slow access times in the linux end of the network? this seems to be my problem. access on the windows side is good, but when it comes to linux accessing windows, it takes quite some time. that is, it's only slow when you first access the windows share, but once they get accessed at least once, everything is pretty good. any ideas on this?

---

### Post by cooldudeny on 2007-08-10
hey i am using a wireless router for my internet at home how can i get a static ip address ?
and if i dont have a static ip address i can not share folders on a network ?

please let me know and also i am really new at all this so might be asking question that will sound silly so please forgive my ignorance in this field

---

### Post by bren on 2007-08-10
if you ISP will not give you static IP (someimes costs more) then you can use a free service from dynamicdns to do this

---

### Post by stalker145 on 2007-08-11
> **cooldudeny said:**
> hey i am using a wireless router for my internet at home how can i get a static ip address ?
and if i dont have a static ip address i can not share folders on a network ?

please let me know and also i am really new at all this so might be asking question that will sound silly so please forgive my ignorance in this field

If you are speaking of a static IP within your network, it is as simple as either opening 'Network' under the 'Administration' menu and plugging in a static IP vice DHCP or going into your router and assigning a specific IP to the MAC that your computer has. 

Attached are a pair of images showing how to get to the Network settings. Assigning IP's via your router is a little different since all routers are different - I've attached an example of my Linksys if you have one of those.

Now, if you're speaking of getting a static IP for your MODEM so that you can access your files from the outside then, as mentioned, you either need to pay your ISP more money for a static IP or go for a dynamic DNS service.

Check back if this fails to answer or you need more help.

---

### Post by cooldudeny on 2007-08-12
> **stalker145 said:**
> If you are speaking of a static IP within your network, it is as simple as either opening 'Network' under the 'Administration' menu and plugging in a static IP vice DHCP or going into your router and assigning a specific IP to the MAC that your computer has. 

Attached are a pair of images showing how to get to the Network settings. Assigning IP's via your router is a little different since all routers are different - I've attached an example of my Linksys if you have one of those.

Now, if you're speaking of getting a static IP for your MODEM so that you can access your files from the outside then, as mentioned, you either need to pay your ISP more money for a static IP or go for a dynamic DNS service.

Check back if this fails to answer or you need more help.

hi but the thing is that my ubuntu is on my pc which is connected wirelessly to the network and not with the wire so i dont even have a option for the static ip under the network settings

---

### Post by stalker145 on 2007-08-13
> **cooldudeny said:**
> hi but the thing is that my ubuntu is on my pc which is connected wirelessly to the network and not with the wire so i dont even have a option for the static ip under the network settings

Static IP's are available for wireless the same as they are for wired. You would set it up in the same way and the same location.

---

### Post by switch13 on 2007-08-13
Stormbringer

Your tut is great!
But the problem that I have is...

I have installed Ubuntu Dapper Drake 6.06 on my pc at home, which has no internet connection.
Now my question is the following.  How do I successfully install SAMBA with all the needed tools for a server with user authentication ect.

I have freshly installed Ubuntu, then downloaded samba 3.0.25b deb package,
installed it with no problems, but when I want to start SAMBA there is no way of starting it.
/etc/init.d/samba start
does not do anything, because there is no samba executable in init.d folder.

Can you please tell me what am I missing?

Can you please try to give me a detailed tut on how to install samba with no internet connection.

Your help would be greatly appreciated!!

---

### Post by wieman01 on 2007-08-14
Brilliant HOWTO. Big thank you to the author although she/he has not been on line for a while. Appreciate it.

---

### Post by wieman01 on 2007-08-14
> **switch13 said:**
> Stormbringer

Your tut is great!
But the problem that I have is...

I have installed Ubuntu Dapper Drake 6.06 on my pc at home, which has no internet connection.
Now my question is the following.  How do I successfully install SAMBA with all the needed tools for a server with user authentication ect.

I have freshly installed Ubuntu, then downloaded samba 3.0.25b deb package,
installed it with no problems, but when I want to start SAMBA there is no way of starting it.
/etc/init.d/samba start
does not do anything, because there is no samba executable in init.d folder.

Can you please tell me what am I missing?

Can you please try to give me a detailed tut on how to install samba with no internet connection.

Your help would be greatly appreciated!!
Stormbringer has not visited the forums since February as his/her profile tells me.

Are there no SAMBA packages on the Dapper Live CD? There should!

---

### Post by rdagijones on 2007-08-16
I have followed the steps in the original post to establish a Samba peer-to-peer.  Everything has processed without errors.  I am still having some trouble getting Windows to accept the passwords, but I am working on that.  I have read some of the follow-up thread but still have a few questions:  I am adding the Linux box to an existing Windows network.  I have the Linux box connected from an ethernet card to a D-Link wireless router by a wired LAN connection. Two Windows laptops are connected to the router via wireless.  In addition, I have a Lexmark Z65n printer connected to the router via integrated ethernet of the printer.  All of the Windows machines print through the router.  The printer has an assigned IP address (192.168.0.128 ) and I have dedicated that address to the printer in the D-Link static  DHCP client list.  **How do I configure Samba so that it will find the printer? ** The printer does not appear in the network.  Lexmark has a handy little program for Windows that allows you to search for the Z65n on a network and even reassign the IP address.  No such program for linux.:confused:

---

### Post by ahkond on 2007-08-16
Hello samba people.  I've got one desktop running Feisty, and another running Windows XP, connected by a router.  I keep the Windows box running 24/7, and generally boot up the Ubuntu box every day or so.  

I have samba installed on the Ubuntu box, and when I start it up, if I do a "ps -ef", I see two instances of /usr/sbin/nmbd -D running, and two instances of /usr/sbin/smbd -D.  

I've set up a samba share called "MyFiles".  My samba configuration and the setup of the share & accounts were all done using Stormbringer's guide.  

If boot the Ubuntu box, go back to the Windows box and attempt to connect to \\ubuntu-box\MyFiles, I get errors (Windows doesn't see the Ubuntu box on the local network).  

BUT: 

If I then go back to the Ubuntu box, stop samba and then restart samba (by calling /etc/init.d/samba stop, followed by /etc/init.d/samba start), and then go back to the Windows box and try again, it then works, every time.  

I have to stop and restart samba manually to get it to work.  This is annoying.  

Is there something simple going on here?  Is there some link in the chain of startup and config scripts calling each other that is failing during boot-up?  Is something allowed for me at the terminal but not the startup process?  When I open the terminal and stop samba, I'm prompted for my password, so I'm assuming that something running during startup doesn't have permission to do something important.  

It's not even clear to me exactly why samba is running on startup in the first place, though, so I'm not sure where to start looking.  

Thanks

-a

---

### Post by ahkond on 2007-08-21
Here's an update: 

samba has completely stopped working.  I didn't change anything and now my Windows box cannot see my Ubuntu box at all, even when I stop & restart the samba daemons.  

-ahkond

---

### Post by cooldudeny on 2007-08-23
> **stalker145 said:**
> Static IP's are available for wireless the same as they are for wired. You would set it up in the same way and the same location.

so if i will change it to the static ip address then where do i need to get the ip address to put in the fields ?

where will i get all the info from and once doing the static ip on my ubuntu pc do i have to do anything to my other computers on the network to acess the shared folder on ubuntu ?

---

### Post by wieman01 on 2007-08-23
> **cooldudeny said:**
> so if i will change it to the static ip address then where do i need to get the ip address to put in the fields ?

where will i get all the info from and once doing the static ip on my ubuntu pc do i have to do anything to my other computers on the network to acess the shared folder on ubuntu ?
These are basic networking questions, so I suggest that you do some reading on the web or so. You have option in Ubuntu's networking apple and there you can configure static leases and address. These are fundamentals that you should know before you start playing around with your network.

---

### Post by Washi on 2007-08-23
I just wanted to add another post of thanks for this tutorial =D>

---

### Post by federsel on 2007-08-24
I can not install samab - the system says I have samba-common and smbconig instead. What should I do?

---

### Post by wieman01 on 2007-08-24
> **federsel said:**
> I can not install samab - the system says I have samba-common and smbconig instead. What should I do?
"samba-common", mate, "samba-common".

---

### Post by federsel on 2007-08-24
I just connected to my pc using "connect to server" and there typing in my ip. I can now reach all the shared files on my pc so I dont need to do anything with samba, or?

---

### Post by wieman01 on 2007-08-24
> **federsel said:**
> I just connected to my pc using "connect to server" and there typing in my ip. I can now reach all the shared files on my pc so I dont need to do anything with samba, or?
No. :-) Ideally that's the way it works. An Ubuntu machine can browse Windows shares, it's tricky the other way around. Hence this thread.

---

### Post by ahkond on 2007-08-24
wieman01 wrote: 

> An Ubuntu machine can browse Windows shares, it's tricky the other way around. Hence this thread.

For me, I have to use samba precisely because this isn't true.  I can get my Windows PC to see samba shares on my Ubuntu box occasionally (about 1/3 of the time), but I have *never* been able to get my Ubuntu computer to see Windows shares on my Windows PC.  When I try to connect or browse the network, I get prompted to log in to the Windows workgroup, and no matter what account name and password I use, I am prompted again, and again, and again, and again, until I give up.  I've tried creating new accounts, changing the passwords, etc. etc. and it never works; Ubuntu just keeps prompting me to log in.  

Hence, I use samba shares on my Ubuntu computer, and tell my Windows computer to connect to them, and I use the samba account & password, and that works about 1/3rd of the time because the Windows PC usually can't detect the Ubuntu computer at all and claims that it doesn't exist.  When this happens, I copy files back and forth using a USB jump drive.  

-a

---

### Post by wieman01 on 2007-08-25
> **ahkond said:**
> wieman01 wrote: 



For me, I have to use samba precisely because this isn't true.  I can get my Windows PC to see samba shares on my Ubuntu box occasionally (about 1/3 of the time), but I have *never* been able to get my Ubuntu computer to see Windows shares on my Windows PC.  When I try to connect or browse the network, I get prompted to log in to the Windows workgroup, and no matter what account name and password I use, I am prompted again, and again, and again, and again, until I give up.  I've tried creating new accounts, changing the passwords, etc. etc. and it never works; Ubuntu just keeps prompting me to log in.  

Hence, I use samba shares on my Ubuntu computer, and tell my Windows computer to connect to them, and I use the samba account & password, and that works about 1/3rd of the time because the Windows PC usually can't detect the Ubuntu computer at all and claims that it doesn't exist.  When this happens, I copy files back and forth using a USB jump drive.  

-a
You are right. That's what I actually meant. Once Samba is installed Ubuntu does see other shared (Windows) drives, but not the other way around.

---

### Post by ahkond on 2007-08-25
> **wieman01 said:**
> You are right. That's what I actually meant. Once Samba is installed Ubuntu does see other shared (Windows) drives, but not the other way around.

In my case, no.  I have samba installed on my Ubuntu computer, but it still can't see other shared (Windows) drives.  The other way around DOES work (Windows PC can see samba shares that are on the Ubuntu computer). 

-a

---

### Post by wieman01 on 2007-08-25
> **ahkond said:**
> In my case, no.  I have samba installed on my Ubuntu computer, but it still can't see other shared (Windows) drives.  The other way around DOES work (Windows PC can see samba shares that are on the Ubuntu computer). 

-a
Weird. It is the opposite way in my case. Anyway...

---

### Post by stalker145 on 2007-08-25
> **cooldudeny said:**
> so if i will change it to the static ip address then where do i need to get the ip address to put in the fields ?

where will i get all the info from and once doing the static ip on my ubuntu pc do i have to do anything to my other computers on the network to acess the shared folder on ubuntu ?

Check your router, first of all. Depending on your equipment and your present network setup you have a couple of different options.

1) Check your IP range. More than likely it will be on the main page of your router's management page. From there you can determine what IP address to give your static computer. Personally, I have my static IP's assigned by MAC - it keeps the DHCP'd computers from stealing the IP somehow. Also it keeps you from having to go to each individual computer and configuring networking.

2) Just go into your network setup in Ubuntu and plug in an available IP (that you got from your router's management page) and away you go.

> **wieman01 said:**
> These are basic networking questions, so I suggest that you do some reading on the web or so. You have option in Ubuntu's networking apple and there you can configure static leases and address. These are fundamentals that you should know before you start playing around with your network.

RTFM? Nice response. Why waste a post with such statements?

---

### Post by alvinz on 2007-08-26
i LOVE this thread ... THANKS alot !!!

been searching for an available sharing method whole day.
i am using vmware player with Ubuntu Fiesty and this file sharing method is good.

THANKS ! :):KS

---

### Post by wieman01 on 2007-08-26
> **stalker145 said:**
> RTFM? Nice response. Why waste a post with such statements?
Goo question. But setting up a SAMBA share, etc. without basic networking knowledge means trouble. That's what I wanted to say. And this thread is a thread relating to network shares and not networking in general. 

Nevertheless you have replied appropriately and thanks for it.

---

### Post by MarshallClan on 2007-08-29
Hey All! 
 Many thanks to Stormbringer for this lovely How-To! You made it nice and smooth for us noobs out here!
 _-K-_

---

### Post by miershpedankl on 2007-08-29
I am brand new to Linux and this tutorial was VERY nice to follow.  I was able to install and configure Samba successfully, but I am not able to connect from my Windows laptop.  I connect with the laptop via a wireless network.  When I tried to map a drive I entered \\ip\MyFiles and was prompted to enter my username and password.  After entering those I was re-prompted to enter them again, but with the NETBIOSNAME/username.  This did not work either,  I followed the instructions, so I am aware of what I set as my username and password as well.  Any suggestions??

Also - I when I got to the schmod change command I wasn't sure which Terminal to use, or even if it matters.  It might be good to clarify at that point in the process.

Additionally - I am not sure I understand what happens after I save and close the "gedit" editor.  Where does it go and what does it do?  

Lastly - this is what I am trying to do:  I have an external HDD as storage and a Bluetooth USB for printing connected to my Ubuntu box (simply b/c it the best location in the house).  I want to be able to access and use both of these devices and I understand that Samba is the way to get that done.  Am I correct?  Will I see the external HDD and Bluetooth USB when I am able to successfully connect to Samba from my Windows laptop?

Thanks so much and, again, GREAT tutorial.

Miershpedankl

---

### Post by wieman01 on 2007-08-30
> **miershpedankl said:**
> I was able to install and configure Samba successfully, but I am not able to connect from my Windows laptop.
Have you created a SAMBA user account for your Windows user?
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```
> **miershpedankl said:**
> Also - I when I got to the schmod change command I wasn't sure which Terminal to use, or even if it matters.  It might be good to clarify at that point in the process.
Any command line tool. There is a terminal tool available in the Gnome menu somewhere (I don't use know, so I cannot tell you exactly where). As long as you open it and see your username and PC name with a prompt, you are ok. :-)
> **miershpedankl said:**
> Additionally - I am not sure I understand what happens after I save and close the "gedit" editor.  Where does it go and what does it do?
Gedit lets you configure text files which are part of the system. Very much like Notepad in Windows. You edit files, save them, and close Gedit. 
> **miershpedankl said:**
> Will I see the external HDD and Bluetooth USB when I am able to successfully connect to Samba from my Windows laptop?
The external HD won't be an issue as long as you enable sharing on it. I cannot comment on Bluetooth as I know too little about it.

---

### Post by takeiteezzy on 2007-08-31
Hi,
I have two computers connected to my WRT54G router, one windows xp mce and ones Ubuntu 7.04. I've spent 4 days trying to set up this but still with little success, please somebody help me. I followed this tutorial and basically got pretty close. When I try to map the network drive, it simply says "The specified group does not exist." Yet when I go to My Network Places > View workgroup computers, I see my Ubuntu computer there along with my current xp computer. I double click it and see "MyFiles" and "Printers and Faxes", but if I click MyFiles, it says " \\Secondary\Myfiles is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The specified group does not exist." Moreover, I can see my windows computer in Network, in Ubuntu. I can access, read, write, and do whatever I want to my whole shared D drive. In both Ubuntu and XP's network places, both computers appear to be in TERRY, my workgroup (not sure if related to the group in error messages). I can ping my Ubuntu, using either "secondary" or 192.168.1.150 from my XP and I can also ping windows from Ubuntu. I'm building this whole thing to be my mom's birthday present and this is part of a bigger project. Please tell me what I did wrong, as I'm starting to think I'm stupid, having even reinstalled Ubuntu 3 times.

---

### Post by miershpedankl on 2007-08-31
> Have you created a SAMBA user account for your Windows user?

Yes, I created a user account as described.  I actually completed every step in the tutorial with apparent success.  

Thanks for the clarification on the other questions.  

miershpedankl

---

### Post by takeiteezzy on 2007-09-01
Hi,
I did some more tweaking ( my post up there), and somehow if I delete my "sudo smbpasswd -L -a Terence" account by adding the argument -x, my windows connects to samba, but asks for password. But if I add back the account in the terminal, the previous error comes out again. Can somebody please help.
Terence

---

### Post by theseeker on 2007-09-01
Hello,

I've followed the instructions of the howto to setup a Vista/Feisty network. Mty smb.conf looks as below:

```
[global]
    ; General server settings
    netbios name = steppenwolf
    
    workgroup = GERTRUDE
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
    
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/shares/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = giorgos	
    force group = giorgos
available = no
browsable = yes
public = no
writable = no
```

I do all required steps as mentioned in the howto, and when the time comes to connect from my laptop (Vista) to my Feisty box, Vista don't see any \\steppenwolf\MyFiles location. When I try to connect from my Ubuntu box to Vista through Places --> Connect to server... I can see both drives of my laptop (shown as $C, $G) but, no access there as well.

I am frustrated! I think networking should be smoother, not having to get your hands all dirty to not manage to set up the network in the end. 

Please, any support is much appreciated! 

Thanks!

---

### Post by metal_hed on 2007-09-08
i followed this tut and at first all was well i was able to map the drive to my vista machine. now however, every time i try to connect to samba is says that "an extended error has occurred". i didn't change any settings what so ever and i can't seem to figure out why this happens. when i connect it asks for username and p/w so i know it connects to the path, it accepts the username and p/w because if i put wrong info it asks to enter again, yet i always get that error showing up after.

if anyone has a solution could they please help out!

much appreciated

---

### Post by wobwill on 2007-09-11
Hi,

I have a question about wireless security.

XP is hardwired to my router while Ubuntu is connected wirelessly.

If I follow the advice in the guide won't I be disabling Samba as it will not be associated with my wireless card? If so how do I ensure everything is secure? Or have a misunderstood the bit on security.

Just so you know. I followed the guide exactly up to that point and it works an absolute treat - Thank You.

Will.

---

### Post by wieman01 on 2007-09-11
> **wobwill said:**
> Hi,

I have a question about wireless security.

XP is hardwired to my router while Ubuntu is connected wirelessly.

If I follow the advice in the guide won't I be disabling Samba as it will not be associated with my wireless card? If so how do I ensure everything is secure? Or have a misunderstood the bit on security.

Just so you know. I followed the guide exactly up to that point and it works an absolute treat - Thank You.

Will.
Wether it is wireless or Ethernet makes no difference at all as long as your wireless network is secured i.e. encrypted (ideally WPA2 or WPA). That's all you need to worry about in that respect.

---

### Post by wobwill on 2007-09-11
Thanks for getting back to me.

My network is secured like this

1) disabled ssid broadcast
2) MAC Filtering enabled
3) 128 hex WEP key

I know I should use WPA instead but it was such a pain getting the whole thing set up in the first place i've been a bit shy since. Especially as the problem was with a house mates wireless link (which I know makes it even worse)!

Will

---

### Post by wobwill on 2007-09-11
I have a problem with seeing shared documents.

I have set up Samba as this guide says and have a shared drive between ubuntu and windows - wehay!!

I have since shared my XP data drive and my documents with the shared drive. However when I go into samba (/home/samba) or into network I can't see any of the files or folders on my XP machine. Have I done something wrong? What should I do to fix it?

Will

---

### Post by wieman01 on 2007-09-11
> **wobwill said:**
> Thanks for getting back to me.

My network is secured like this

1) disabled ssid broadcast
2) MAC Filtering enabled
3) 128 hex WEP key

I know I should use WPA instead but it was such a pain getting the whole thing set up in the first place i've been a bit shy since. Especially as the problem was with a house mates wireless link (which I know makes it even worse)!

Will
Alright... I only mentioned it to let you know that WEP is highly insecure. Even disabling ESSID broadcast and enabling MAC filtering won't protect you as Aircrack is able to determine the ESSID immediately and cloning of MAC addresses is a piece of cake. Nevertheless it is better than nothing... :-)

---

### Post by wobwill on 2007-09-11
I've been reading your post on WPA secuity. It has become the next job on my to do list!

---

### Post by wieman01 on 2007-09-11
> **wobwill said:**
> I've been reading your post on WPA secuity. It has become the next job on my to do list!
No prob. Just post there if you have problems. You might have to replace the current wireless driver with "ndiswrapper". But we get to that later. See you then!

---

### Post by wobwill on 2007-09-11
going back to my other question,

Can anyone tell me why i'm not seeing the files and folders from my xp machine that i've shared with ubuntu?

In XP i've shared some files and folders with the shared drive but they don't appear in samba or on the network drive in ubuntu.

Will

---

### Post by haydnc on 2007-09-11
There seems to be a trend that every time a new version of Ubuntu comes out the whole samba-networking thing stops working for a while.

In particular the ability to use security = share so that any one connecting to the new Ubuntu box can access data without messing around with user accounts on the Ubuntu box.

I have a test machine running Gutsy with this exact problem, while everything is working perfectly under Feisty and the Gutsy machine can connect to Feisty and Windows shares but nothing can connect back to the Gutsy machine.

Does anyone know of a foolproof way to avoid this ongoing problem, or do I just need to wait until the final release of Gutsy, then endure the month or so of people complaining they can't connect to Samba shares before someone works out what's wrong and how to fix it?

A HOWTO that doesn't use the intermittent security=share but also does not require that every windows user have an account set up on the Ubuntu machine would be good if that's even possible. 

If it's not possible could someone please tell me how to get this working on a Gutsy machine?

---

### Post by haydnc on 2007-09-11
Answered my own question!

Apparently the structure of the smb.conf has changed slightly (again) and there's now an annoying little line in there that says:

valid users = %S

If you comment that out and enable the one below it which says something like:
;   guest ok = yes

in combination with using security = share

file sharing still works between Gutsy and whatever. 

I hope this makes some sense and is useful to someone. :)

---

### Post by sbrown1038v on 2007-09-18
Just wanted to thank you for this great 'HOW-TO'.  I think I could not get samba working because I didn't run smbpasswd with the -e switch to enable the account after setting the password.  It's working great now!

---

### Post by antonr on 2007-09-18
Following this guide, I got samba working (Kubuntu 7.04 <-> WinXP), but without needing to reboot WinXP. Instead of rebooting WinXP, I did the following in a DOS Console, to restart the network:

    net stop netman
    net start netman

This option should be useful when you don't want to reboot.

---

### Post by antonr on 2007-09-18
Stormbringer, just a few typos in the guide:

1:

	> Add the following lines to the [general] section of your smb.conf to achieve that goal:

But there is no "[general]" section in the provided smb.conf file.
It looks like you meant "[global]".


2:

In the supplied smb.conf, it has:

	> force group = YOUR_USERGROUP

but you later refer to it as:

	> -> force group = YOUR_USERNAME

It looks like the second one is correct. (Well, it worked for me :)

Hope that helps.
Regards.

---

### Post by MisanthropicOne on 2007-09-19
Thank you, Stormbringer for this great little walk-thru. Moving files around between my windows installs and my roommate's machine to my mythtv box should no longer be a problem for either of us.

---

### Post by JawsThemeSwimming428 on 2007-09-20
This is indeed a great guide. I had previously tried to access my Windows files, via Samba, and was unsuccessful (in Dapper). I followed the guide word for word and was able to see my shared folder on my Feisty machine from Windows Vista Home Premium. However, when I rebooted Feisty I did not have access to the mapped drive from Vista. It said The network path could not be found. I wasn't sure what happened, as both of these machines have static IP's and I thought it was supposed to reconnect at logon. I disconnected the drive and tried to re-establish it and when I was trying to map the drive in Vista it couldn't even see Feisty on my network. I am not sure what happened. I am trying to figure it out right now but if someone could help me out I would be very appreciative. Thanks!

---

### Post by JawsThemeSwimming428 on 2007-09-20
One thing I did notice... I tried to share my home folder, but when I rebooted I was presented with the following message onces I typed my password and hit Enter to log in:

" User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I am not quite sure what that means or what I should do to fix it (or if it has anything to do with my network folder access problem above... In smb.conf I elected to share /home/willy which is my home directory).

---

### Post by JawsThemeSwimming428 on 2007-09-21
I'm still trying to figure out what is happening. Anyone have any idea?

---

### Post by wieman01 on 2007-09-22
> **JawsThemeSwimming428 said:**
> I'm still trying to figure out what is happening. Anyone have any idea?

I have only limited experience as far as Samba is concerned and none in conjunction with Vista. But... are your Vista and Ubuntu user name with which you to attempt to log on identical? This could explain the error message concerning permissions.

I also found this, perhaps it is worthwhile taking a look at it:

[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746]("http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746")

---

### Post by vassalle on 2007-09-22
I tried a search but couldn't find what I'm looking for. I don't know if this have been asked before (going through 44 pages is quite time consuming).. So, bare with me :D

Is there a way for me to share my folder without the person accessing the folder having to put in his user account & password? Something like sharing from an XP box to another, just right click and share folder - no passwords, or user accounts needed.

I've read somewhere that changing the option security = share might allow this but somehow it didn't work for me.. Hopefully someone here can come up with a solution and end this misery. Thanks in advance!

---

### Post by JawsThemeSwimming428 on 2007-09-22
Thanks, I am trying that link right now. I wasn't aware that the usernames had to be identical? My Vista username is willy-velocitymicro and my Feisty username is willy. Do I have to change one?

---

### Post by JawsThemeSwimming428 on 2007-09-22
Vista Home Premium does not have secpol.msc or gpedit.msc, or I can not find it. It says it can't be found. Is there another way to do it?

---

### Post by JawsThemeSwimming428 on 2007-09-23
Thanks wiema01... I think I got it working. Firestarter was getting in the way and after I re-did my smb.conf everything seems to be in order.

One question though...on my Feisty machine when I go to Network and open up my Windows Network, all it does is open up an empty folder. Do I need to do something else so that I can browse my Vista machine from Feisty?( I am able to browse my Feisty shares from Vista)

---

### Post by wieman01 on 2007-09-23
> **JawsThemeSwimming428 said:**
> Thanks wiema01... I think I got it working. Firestarter was getting in the way and after I re-did my smb.conf everything seems to be in order.

One question though...on my Feisty machine when I go to Network and open up my Windows Network, all it does is open up an empty folder. Do I need to do something else so that I can browse my Vista machine from Feisty?( I am able to browse my Feisty shares from Vista)
Ah, Firestarter... ;-) I remember having trouble with that as well.

You need to enable the "share a folder" function in Vista. At least that is so in WinXP. You would then be able to see that folder from Feisty.

---

### Post by serban on 2007-09-24
Hello,
after reading the posts here, I still didn't resolve my problem (I bet it's something easy, I just don't see it).
So .. I can ping Xubuntu & XP (eachother) but that's about it. Here is what I have:
root@tata1:/home/tata# smbclient -L localhost -U%
Domain=[TATA] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      
        MyFiles         Disk      
        IPC$            IPC       IPC Service (Samba 3.0.24)
Domain=[TATA] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------
        XUBUNTU              Samba 3.0.24

        Workgroup            Master
        ---------            -------
        TATA                 XUBUNTU



 and this is my smb.conf :

[global]
    ; General server settings
    netbios name = xubuntu
    
    workgroup = tata
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tata
    force group = tata
available = yes
browsable = yes
public = yes
writable = yes

The username in XP is "tata"  (as in Xubuntu) with the same password as in Xubuntu; the workgroup in xp is "tata" (as in Xubuntu)

When I request "\\192.168.2.3\MyFiles" I get no answer (by the way, the IP is correct)
Can somebody give me some hints? - I'm going nuts.
Thank you

It's me again :)
Actually it works ... on any other computer but the one I was trying. It must be something wrong with that XP. It works on another XP and two Vistas so I'm happy.
Thank you for all the information you put here - that makes us, the beginners, not to give up. 
Serban

---

### Post by dinbotclone on 2007-09-25
aswome job...now i can get rid of my windos box and use ubuntu as my file/print server....again very easy how-to much bettee than 90% of the other ones i have used in the past

---

### Post by JawsThemeSwimming428 on 2007-09-26
serban,

 If you have Firestarter or a similar Windows firewall installed you have to create rules allowing them to connect to the machines on your network. That was my issue and once I created the rules I was able to browse the machines. Something to check out.

---

### Post by wieman01 on 2007-09-26
> **JawsThemeSwimming428 said:**
> serban,

 If you have Firestarter or a similar Windows firewall installed you have to create rules allowing them to connect to the machines on your network. That was my issue and once I created the rules I was able to browse the machines. Something to check out.
Open port 137-139 and 445 for inbound and outbound traffic I suppose.

---

### Post by Duwady on 2007-09-30
Just wanted to thank you for making my day.  I was frustrated since last 2 weeks. and made such a mess that I had to reinstall many times.  

But following your how-to, I am up and running....  tra la la la la

Once again, THANK YOU!!!!!!!

Now, I can face my wife. :)

---

### Post by superpenguin79 on 2007-09-30
Thanks for the tip on the firewall.. I am familiar with the networking, but sometimes you forget the simple stuff.. ;)

---

### Post by acorn22 on 2007-10-06
Thanks for the guide. I got prety far I think, but I have one hiccup.

I have a linux computer next to an XP computer and I have followed all the directions on the linux side. So far so good. (Enabled WINS) However when I go the the windows computer and try to map a network drive It prompts me for a username and password. No usernames/passwords work. What is wrong?

Thanks

---

### Post by Duwady on 2007-10-06
I was also in the same boat, but I followed the step given in the first post.

The problem seems to be on the Windows side, please look at the steps given again, and retrace your steps. I am sure you will catch it the second time around.

---

### Post by jtreg on 2007-10-08
thanks for info... as I have my network connection wired up as Automatic DHCP (I cannot connect to my router to internet otherwise... If I do this I cannot share files with Windows XP machines via Samba... what should I do?

---

### Post by Duwady on 2007-10-08
The only problem with DHCP configuration is that it keeps on changing.  Otherwise, the above will work with DHCP also.

If you can see it, but cannot connect to it, then the issue is again the windows. I anabled WINS in Samba, and followed this step on the XP machine.

QUOTE
If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows 

UNQUOTE

After restarting the computer, I could see it, and access it.  This step has to be done before you map a network. 

If it does ask for the password, give "root" as id, and your root password, though I do not think it will ask.

Let me know if this helps, otherwise I will let you know what else I did.

---

### Post by Duwady on 2007-10-08
Also, it is not that difficult to change the IP address on the linux machine from Dynamic (from DHCP) to Static (given manually), without being out of the internet loop.  You may not even need to change the things on the router.

Let me know if you want to try this out.

---

### Post by lionround on 2007-10-08
I have an external USB Lacie HD (with Seagate drive) 250 gig, fat32. It is mounted at /media/LACIE with a folder on it at /media/LACIE/music. I have about a gig of music in the folder.

I want to be able to share/read/write files to and from the drive from my XP and 98 machines.

I am using Ubuntu Feisty Fawn 2.6.20-16-generic.

I have Samba installed and properly configured (I hope.)

The problem is that when I try to access it from either my XP or 98 or Ubuntu machines through the network, it shows up in Network Neighborhood under \\Ubuntu\Lacie (note the lack of the media in the path) and when I click on it is "inaccessible." I can access it if I just go to Places -> Lacie.

The owner permissions are set to david (that's me) with read and write and the root group. It won't allow me to change ANY of these options.

I am not using my Ubuntu box as a WINS server.  Should I be?

I tried gksudo nautilus and could not change anything.

Suggestions please.

---

### Post by Duwady on 2007-10-09
I believe "\\Ubuntu\Lacie" is showing the share name, and not the path, but I may be wrong as I am still learning. :)

When you add users in Samba, I think you should have the same userid and same password that is used in your XP (Don't know about 98, but it could be same).  That is how I set it up, and now it is working.

The "how-to" does give an option of what to do if Ubuntu is WINS and what to do if it is not, so I guess that is not mandatory.

Hope this helps.  Remember, I am as new as you, but just got lucky and got it working by following the how-to.

---

### Post by adamjs on 2007-10-10
how would you edit the config file to only allow particular users access to a particular share?
AJS

---

### Post by Donkor on 2007-10-13
Trying to get it enabled on my network.  I have a static IP, but don't want to enable WINS since I've quite a few computers that would have to be modified in order to connect.

This is my config 
> 
[global]
    netbios name = dave
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts bcast
    syslog = 1
    syslog only = yes
[data]
    path = /home/dave/data
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = XP
    force group = HOME


Workgroup name is HOME
The account name I'm trying to access it with is named XP and the password I used with "useradd" is my windows password.  I CHMOD'ed the directory to 777 but it still can't access it because I get the "The specified group does not exist" error message, though I can see a list of folders the computer is sharing. 

What did I do wrong?

---

### Post by Alpinist on 2007-10-14
Stormbringer, Thanks for the tutorial.  I have been struggling with Samba for a while now and your easy to follow guide finally got me fully configured and working correctly.

---

### Post by inkster21 on 2007-10-18
Thank you so much for this one... really great guide! especially for me a newbie.. how wud i know that i nid to type those commands on a terminal window rather than on the alt F2 thing...thank God i ran on to this. really im a total newbie in ubuntu its not like the user friendly interface in windows. no offense^^ but i really want to learn about Ubuntu!

---

### Post by Maddmaxx on 2007-10-19
Just wondering what was changed in Samba after the 7.10 upgrade... I have my shared folders mapped in windows and my password was saved in windows so when I clicked a network drive it wouldn't ask for password. Now after the upgrade it has been asking for the password, and when I enter the same password again it's a no-go. I hope I'm not hijacking this thread, it just seems related. Just hoping that some of us less experienced users can be enlightened. 

Thank you in advance!

---

### Post by g2g591 on 2007-10-19
I've been following the guide [URL="https://help.ubuntu.com/community/MountWindowsSharesPermanently"]https://help.ubuntu.com/community/MountWindowsSharesPermanently , and when I mount -a I get 8177: tree connect failed: ERRSRV - ERRinvnetname (Invalid network name in tree connect.)
SMB connection failed
The computers name is OLD and the share name is also OLD (named so because its a old '98 with a new network card slapped in) 
[/URL]

---

### Post by Maddmaxx on 2007-10-20
smbusers and smb.conf were wiped, had to reconfigure, all is well for now...

---

### Post by jim8433 on 2007-10-20
I need help to resolve Samba setup with Gutsy.  I had no problems under Feisty, but Gutsy has me perplexed.  I have an XP client that can at times see my Gutsy desktop computer, but I get message indicating that XP may not have permission to connect to my Gutsy server.  I have tried various adjustments to my smb.conf, even used SWAT to try to put together a workable smb.conf.  When I can see my XP on Samba from desktop, I can see shared files, but cannot even see my local shares on my Samba server box.  Can anyone help me clear this up for me?  I love Ubuntu.

---

### Post by kosekiseiji on 2007-10-20
can someone help me? I've set up a samba share from this tutorial and it works from other computers (namely a mac) if I use it's terminal and use smbclient //servername/share

but can't get it working using smb://servername/share

what am I doing wrong?

I've used debian before and haven't had a problem... usually it's just a case of adding a password using smbpasswd

I'm using gutsy
here is my smb.conf
[global]
    ; General server settings
    netbios name = timbu
    server string =
    workgroup = bruces
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/tim/Music/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tim
    force group = tim

---

### Post by rcane84 on 2007-10-20
Hello everyone,

A really helpful walk-through, but I'm not out of the woods yet.  I have Ubuntu installed on an older P3 desktop and Windows XP Pro on a P4 Laptop. I have been trying to set up a network and have had some success but it is not all the way there. From the Ubuntu desktop I am able to see the shared files on my Windows computer and am able to transfer them over no problem. The thing is I can't do it the other way. When I try to access what should be my Ubuntu shared folder (all of \home) I am unable to do so from XP machine. 

I set samba and decided to go with a fixed dhcp lease. Here is the code (sudo gedit /etc/samba/smb.conf) I hopefully configured right.

[global]
; General server settings
netbios name = RICHARD


workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE
SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true

username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = no

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes


; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
valid users = %S
create mode = 0600
directory mode = 0755

browseable = yes
read only = no
veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.

;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.

;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for

; Windows - I'll cover this topic in another HOWTO.
server string = richard
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664

directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]

;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[MyFiles]
path = /home
browseable = yes
read only = no
guest ok = no
create mask = 0644

directory mask = 0755
force user = RICHARD
force group = RICHARD
available = yes
public = yes
writable = no

[samba]
path = /home/samba
available = yes
browseable = no
public = yes
writable = yes


I have tried disconnecting both the windows firewall and the Telus Internet Security firewall (internet access provider security) and it hasn’t made any difference. I seem to be doing fine until I get to this part:

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

I followed this I get a pop up window saying “Attempting to contact \\192.168.0.101\MyFiles...” then I have to enter my username and password and the same window asking me to enter my username and passoword pops up over and over. I’ve tried typing “Richard” – the computer’s name instead of the ip address with no luck. I’ve also tried varying the “MyFiles part” with \home with no luck. I’m also running AVG free edition for linux does that make a difference?

I’ve made sure that \home is a shared folder in Ubuntu under system>administration>shared folders. Please let me know if any of you have some suggestions I might try. I think I may have also done something like “ chmod 0770 \home” in the terminal. I probably shouldn’t have though I don’t know if it wrecked it. I can’t remember why I did it. It was super early.

Thanks for the help!

Richard

---

### Post by BLTicklemonster on 2007-10-20
I give up. I had finally gotten my ubuntu machine to share to xp, and vice versa, then the last gutsy upgrade happened, and I am back to square one. Thing is, I don't remember exactly what got the network going the first time, and nothing here has gotten it going again.

This is totally frustrating. We took a hundred or so pictures of my grandson today, and I wanted to share them to upstairs. First time to use the network since the upgrade. Dang.

---

### Post by olavjunior on 2007-10-21
I don't quite get this.. Windows can access my ubuntu, but when I try to access windows from ubuntu, it asks me for a username and password. WHY?

EDIT: ok, good idea to share something on the xp machine. Haha, stupid! My mates fault :)

---

### Post by dolphoneman on 2007-10-21
Stormbringer, even though this HOWTO is over a year old, it still holds water and works great.

Thank you for taking the time to write and post it.

---

### Post by DasCrushinator on 2007-10-21
I followed this guide on Gutsy, but I am having trouble connecting.  I get this error when I try:

[http://img90.imageshack.us/img90/1442/screenshotnautilusmh0.png](http://img90.imageshack.us/img90/1442/screenshotnautilusmh0.png)

---

### Post by Troberg on 2007-10-23
Wonderful guide, worked like a charm on six different machines running Kubuntu Gutsy.

On three of the machines, though, there is a slight hitch. Whenever I reboot the machine, the samba service does not start correctly. It's set to start on boot, and if I look at it in system settings, it believes it's running until I try to restart it, so it has probably tried to start it at some time during boot. If I restart it, it runs perfectly.

Any ideas?

---

### Post by wieman01 on 2007-10-23
> **Troberg said:**
> Wonderful guide, worked like a charm on six different machines running Kubuntu Gutsy.

On three of the machines, though, there is a slight hitch. Whenever I reboot the machine, the samba service does not start correctly. It's set to start on boot, and if I look at it in system settings, it believes it's running until I try to restart it, so it has probably tried to start it at some time during boot. If I restart it, it runs perfectly.

Any ideas?
Perhaps a conflict with "Firestarter"?

---

### Post by petersfreeman on 2007-10-23
Thank you very much, Stormbringer!  Not only did I get everything working perfectly by following your advice, I also solved a nagging windows problem that I was having on the network.

I really appreciated that you took the time to document it so unambiguously.

Cheers,

Peter

---

### Post by NZ-Wanderer on 2007-10-23
Just want to say thank you to the thread author for his how-to, My Kubuntu Gutsy now talks very happily with my Vista Ultimate and XP machines and visa versa:) :)

---

### Post by Troberg on 2007-10-25
> Perhaps a conflict with "Firestarter"?

Nope, it's note even installed.

---

### Post by Duwady on 2007-10-25
I was playing with Server 6.06, and followed this steps, and was very happy.

Now I wiped it all, and installed Gutsy Desktop.  Is the steps mentioned here still valid for Gutsy?

Thanks.

---

### Post by Troberg on 2007-10-25
> Is the steps mentioned here still valid for Gutsy?

Worked nicely for me, except for the startup issue I mentioned, but that was only on a few machines, the rest worked perfectly.

---

### Post by wieman01 on 2007-10-25
> **Duwady said:**
> I was playing with Server 6.06, and followed this steps, and was very happy.

Now I wiped it all, and installed Gutsy Desktop.  Is the steps mentioned here still valid for Gutsy?

Thanks.
Affirmative. Clearance to go ahead. :-)

---

### Post by Duwady on 2007-10-25
Just followed it on Gutsy...  and it rocks!!!!!  :)

---

### Post by haglv on 2007-10-25
[I have installed and configured samba  on my laptop with Ubuntu which is networked wirelessly to 2 window computers. The Window computers can access the laptop but the laptop gets the message "Folder contentscan't  be displayed, cannot display the contents of Windows Network:harry"
Help
Harry

---

### Post by Krextyl on 2007-10-27
Hey nice How to, so I got everything up and running just a the instructions say. I got a logical Z drive on my windows machine in which I am able to drag and drop files to and from my linux machine. But when I try to do the same on the Linux machine, I get an error from that end - see the image I've attached. I was trying to access it from pulldown Places>Network>Windows Network>Nuthouse (workgroup name)>Desktop (name of one of the machines on my LAN which has shared folders on it), thats when I got the message I attached. Please let me know if I going about this correctly, I am still new, :biggrin:

---

### Post by Krextyl on 2007-10-27
Another side note and probably much more advanced, possibly warranting a different thread - I have a PS3 on my LAN, is there a way to setup a interface with it (even if only on the linux end) to move files back and forth like multimedia movies, audio etc.. Just Pondering the thought of it makes me say Cool! I've been told that the PS3 system is operated by a linux based system, not sure on the validity of that and if that even helps or not - but it would still be awesome to directly communicate with it,especially to use it as a media server over my network.

---

### Post by Gaztech on 2007-10-28
Apologies if this has already been asked and answered (this is a long thread :))

I've got Samba share setup and it's happy with my XP PC. However I want to do the reverse and add some windows shares to my Linux box basically, my music and movies folder on my xp machine. 

If I create a mount point in say /media/my_win_share and mount it permanently (so it is mounted whenever I turn on my ubuntu machine) will it create problems if I boot up the ubuntu machine without the XP machine being switched on i.e. does the share not being present muck up the ubuntu file system in any way?

I was planning on using instructions along the lines of this and using the smbfs package:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

There is a section at the end that makes mention of bad things happening if the server isn’t present, can someone confirm this is (or isn't) the case and if so is there a way round it?

Thanks in advance for any help :)

Gaz

PS this is on Kubuntu 7.10!

---

### Post by suzyweb on 2007-10-29
Thanks so much for this wonderful guide!

I encountered no problems until I got on my Windows machine and tried to log into my Linux machine. It asks me for a name and password then when I enter the name and password for my Linux box it gives me and error that says:

The network path 192.168.0.4\home\Samba could not be found.

Any clue what this means?

Thanks for all your help!

---

### Post by jaydeflix on 2007-10-29
Ok, so, I got it set up so that I can see the share from Windows, I can map it, no password asked for, but, I can't actually *see* the subfolders.  It's 0777 across the board, all the way down to the files.  smb://127.0.0.1/media works fine from the ubuntu box.  What might I be missing (besides a boatload of info in this to help you answer me...)

---

### Post by werdna5225 on 2007-10-29
I'm sorry if this has already been asked, but when I try to map the network drive, I get an error that says the path could not be found.  Does anyone know what the problem could be?   Also, the ubuntu computer is found in the workgroup but when i try to access the ubuntu computer i get the login dialogue but can't seem to get it to ok access.

---

### Post by Troberg on 2007-10-30
Another small problem I've noticed:

I'm sharing files with international characters, in my case the Swedish Å, Ä and Ö. Windows and Linux apparently has different ideas about how to represent these characters, and they come out as pairs of other characters.

Yeah, I know using international characters is begging for trouble, but it's too many files with to many interdependencies to rename with a reasonable effort.

Any ideas?

> I'm sorry if this has already been asked, but when I try to map the network drive, I get an error that says the path could not be found.

When I get it, it's because the Samba service has failed to start. Try to restart it (don't trust the system when it's telling you it's running, just restart it). If you get a message that the service can't be stopped because it's not running, you've got the same problem as I got. In that case, just start it manually. I have no idea why this is happening or how to get it to start properly without manual intervention.

---

### Post by yashoda on 2007-10-31
I've been reading this HOWTO for 2 days now!

I was just about to give up, when I noticed that the XP machine was recognising my Ubuntu laptop!

but when I typed my username and password in, they weren't accepted!

I've used the password setting commands again, to ensure I am typing in the correct password.

Any advice?


ps. I do agree though, that this is the most straightforward HOWTO on Samba yet!

---

### Post by Troberg on 2007-10-31
> but when I typed my username and password in, they weren't accepted!

Are you sure you got the workgroup right? That caused me some problems much like yours when I hurried a bit too much on one machine.

Otherwise, check caps lock. :)

---

### Post by yashoda on 2007-10-31
Hi Troberg,

Thanks for replying.

Yeah, i got the Workgroup in Caps, cos that's how it showed in Windows, when I checked the Computer Name.

will try as, "Mshome" instead.

---

### Post by yashoda on 2007-10-31
nope... still asks for username, and password which don't seem to be correct.

---

### Post by Scimu on 2007-10-31
Thanks a lot for this, I have networking all setup now! :D

---

### Post by Krextyl on 2007-10-31
Anybody? posts #476 and #477

Thanks

---

### Post by Wharf Rat on 2007-11-03
Stormbringer,

I finally  carefully followed your instructions.  It works!  My wife's XP laptop can share files and print to my Ubuntu desktop.  

Thank you very much!!

For those of you still having problems, look at the Windows machine settings.  My two Ubuntu machines talked just fine -- Windows could never make the connection.

---

### Post by de_valentin on 2007-11-06
Hi there,

I received an error here

1.1 Starting samba and setting up user accounts

Let us fire up samba for the first time. Type:

Code:

sudo /etc/init.d/samba start

There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

it reads

command not found:confused:

---

### Post by superdif on 2007-11-06
> **yashoda said:**
> nope... still asks for username, and password which don't seem to be correct.

Did you find any solution anywhere for this problem. I ask because I have the same problem.

From my Kubuntu machine I can access the shares on the Windows machines, but not vice versa. :(

---

### Post by saphyrre on 2007-11-06
> **de_valentin said:**
> Hi there,

I received an error here

1.1 Starting samba and setting up user accounts

Let us fire up samba for the first time. Type:

Code:

sudo /etc/init.d/samba start

There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

it reads

command not found:confused:




Try this:

sudo /etc/init.d/smb start


Off-note, Stormbringer, you are a peacebringer to me:)... i have read over 20 how-to's about samba, this is by far the best one; i was able to access samba shares from both Vista and Xp clients. 

Thanks a lot!!

---

### Post by LittleDonnieJ on 2007-11-08
Dude... Stormbringer...  YOU ROCK!!! :guitar:   you are my Sandle-Hat guy.  love the urahara tux!

---

### Post by CameronCalver on 2007-11-09
Thanks storm bringer worked a treat but one thing

Iv set up users on the server Cam,Robyn,Laura,Daniel etc i would like it so that i could make a folder on the share called Cam for example and then everyone would be able  to see that folder but they would not be able to access it, only cam could access it. How would  go about doing this?

---

### Post by arcole on 2007-11-10
> **superdif said:**
> Did you find any solution anywhere for this problem. I ask because I have the same problem.

From my Kubuntu machine I can access the shares on the Windows machines, but not vice versa. :(

have been having this same issue with 7.10. this guide worked great with 7.04 but with an install of 7.10 something gets screwed up. but after about 3 reinstalls i think i may have a fix for some people. it worked for me.

when you use the "server install" dont let the cd install samba when asked install it after the os install is done. have no clue what if anything this helps with but it worked for me.

---

### Post by Smerky on 2007-11-12
Hello,

So I'm really new to linux and especially linux servers and I'm also lost. I've been trying to set up a samba server( Ubuntu 7.10) on a desktop that I have here on my home network, which is composed of one XP desktop, a Ubuntu Virtual machine, and my linksys router.)

So far I've just flunked and I've been trying to search for a detailed guide that can help me. This guide has been pretty excellent but I've ran into a few problems at the very beginning.

I got to the point where I installed samba and then I stopped it. After that the nest couples of steps goes as follows:

```

root@hoab:~# mv /etc/samba/smb.conf /etc/samba/smb.conf.template
root@hoab:~# touch /etc/samba/smb.conf
root@hoab:~# gedit /etc/samba/smb.conf
cannot open display:
Run 'gedit --help' to see a full list of available command line options.
```

At that point I had no idea what to do. So I tried looking at some other help files and such and haven't got any where. I also tried installing the gedit (The first time it said it wasn't installed), smbclient, samba-common, and smbfs.

Would someone mind helping me? I'd really appreciate it.

---

### Post by arcole on 2007-11-14
> **Smerky said:**
> Hello,

So I'm really new to linux and especially linux servers and I'm also lost. I've been trying to set up a samba server( Ubuntu 7.10) on a desktop that I have here on my home network, which is composed of one XP desktop, a Ubuntu Virtual machine, and my linksys router.)

So far I've just flunked and I've been trying to search for a detailed guide that can help me. This guide has been pretty excellent but I've ran into a few problems at the very beginning.

I got to the point where I installed samba and then I stopped it. After that the nest couples of steps goes as follows:

```

root@hoab:~# mv /etc/samba/smb.conf /etc/samba/smb.conf.template
root@hoab:~# touch /etc/samba/smb.conf
root@hoab:~# gedit /etc/samba/smb.conf
cannot open display:
Run 'gedit --help' to see a full list of available command line options.
```

At that point I had no idea what to do. So I tried looking at some other help files and such and haven't got any where. I also tried installing the gedit (The first time it said it wasn't installed), smbclient, samba-common, and smbfs.

Would someone mind helping me? I'd really appreciate it.

easy change "gedit" to "nano"

---

### Post by artemen on 2007-11-15
I AM COMPLETELY  new with samba and linux itself, know some staff about networking and that's about it. Did you  mean jast "copy paste whatever in the <code> boxes"? Please, forgive my ignorance, but can we change YOUR_USERNAME in the code before typing it in?  thanks a lot for this post.

---

### Post by Troberg on 2007-11-15
> Did you mean jast "copy paste whatever in the <code> boxes"? Please, forgive my ignorance, but can we change YOUR_USERNAME in the code before typing it in?

Yes and yes.

---

### Post by cor2y on 2007-11-30
Can someone help me I can't access the share folder.
Its listed in My Network places on the windows side but it says that there is no permission to view.

---

### Post by tbrothers on 2007-12-02
Ubuntu server 7.10

Thanks StormBringer!  Your config file and instructions worked Perfect!

However - for the life of me I cannot find the file smbusers.  Following your instructions and using the commands

"sudo smbpasswd -L -a <username>"
"sudo smbpasswd -L -e <username>"

I've granted the appropriate users the ability to map drives via samba ... and they all work great.  I just don't know where the user information is being stored.  I've searched the entire drive and cannot find file smbusers.

What am I missing?

Thanks,
Terry

---

### Post by pljones on 2007-12-02
Sorry, but there are 51 pages here and I've not read all of them...

I'm running Hardy.  I believe things were working under Gutsy but I couldn't swear to it.

I have an fstab entry:
```
//dell/SharedDocs           /mnt/dell_SharedDocs  cifs  auto,credentials=/etc/security/dell_SharedDocs.cifs,rw,file_mode=0666,dir_mode=0777  0  0
```
where the contents of the credentials file is:
```
username=guest
password=
```
Running```
sudo mount -t cifs -a
```at the terminal works fine.  However, the share isn't mounted at boot.

(I've tried with smbfs and the guest option, too, and it's exactly the same.)

Now...  I've scanned through /etc/init.d and I can't see anything that would actually mount this share!  I'm guessing this could be part of the problem...

Is anyone else testing Hardy and having this problem?  Or know the solution?

---

### Post by ukripper on 2007-12-05
> **pljones said:**
> Sorry, but there are 51 pages here and I've not read all of them...

I'm running Hardy.  I believe things were working under Gutsy but I couldn't swear to it.

I have an fstab entry:
```
//dell/SharedDocs           /mnt/dell_SharedDocs  cifs  auto,credentials=/etc/security/dell_SharedDocs.cifs,rw,file_mode=0666,dir_mode=0777  0  0
```
where the contents of the credentials file is:
```
username=guest
password=
```
Running```
sudo mount -t cifs -a
```at the terminal works fine.  However, the share isn't mounted at boot.

(I've tried with smbfs and the guest option, too, and it's exactly the same.)

Now...  I've scanned through /etc/init.d and I can't see anything that would actually mount this share!  I'm guessing this could be part of the problem...

Is anyone else testing Hardy and having this problem?  Or know the solution?

Mount share in ```
/etc/fstab
``` not in init.d(which is to run your daemons/services)

Try this ```
mount -t smbfs -o username=<name>,password=<passwd> //sambashare /mountpoint
```

if it mounts using above then try adding to fstab:
//Machine name/ukripper    /Machine name/ukripper     smbfs credentials=/home/ukripper/.smbmount-ukripper,rw

---

### Post by pljones on 2007-12-05
Sorry, but if you'd understood my message, you'd have realised I'd already tried what you suggest.

For who knows what reason, today it's working... :?

---

### Post by andho on 2007-12-06
when i try to access my ubuntu shares from my windows machine (i didnt use the wins setup) windows prompts for the username and password and i have to enter username and password to access it.
i also tried to access the same shares from the same ubuntu machine and it asks for username and password in it too. how come?

---

### Post by vsiege on 2007-12-06
Do you have any OS X tutorials? I cant see my os x machine under xubuntu but, i can see xubuntu on my mac. I was referred to this thread by other users from the Networking & Wireless category.

Computers Systems on my network:
1x - Ubuntu Server 7.10
with Xfce desktop, LAMP Server, OpenSSH Server, PostgreSQL Database, Print Server and SAMBA
2x - OS X 10.4
2x - MS XP Home Edition

Router:
Netgear

---

### Post by StephUb on 2007-12-06
I got the same here..
Using samba and smb:cif from the OS X i am able to open my share folder in ubuntu (here i have a problem of permission that i have to solve)

BUT, i try different ways to connect to OS X share folder from ubuntu and i couldn't get it to work, i try many thing like ip adress, i have the mac appearing is my windows workgroup but cannot acces it

Any help?

PS side question, is samba going through the wireless router or can someone intrude in the system via ad-hoc ?

thanks

---

### Post by Lord DarkPat on 2007-12-19
OK. I can Access linux files from windows, but not vice versa. 
Wat Do I do. And BTW, nice guide. It's scary for a semi-boob like me though, I managed nevertheless

---

### Post by Lord DarkPat on 2007-12-19
I can access My Linux Files through windows, but I can't see windows in my Samba Shares

Computers Systems on my network:
1x - Kubuntu Gutsy
2x - MS XP Professional

---

### Post by buccaneere on 2007-12-19
sudo /etc/init.d/samba stop
sudo /etc/init.d/samba stop
 * Stopping Samba daemons...                                                    start-stop-daemon: warning: failed to kill 4910: No such process

What's this critter???

---

### Post by gilf on 2007-12-23
> **buccaneere said:**
> sudo /etc/init.d/samba stop
sudo /etc/init.d/samba stop
 * Stopping Samba daemons...                                                    start-stop-daemon: warning: failed to kill 4910: No such process

What's this critter???

Looks like you tried to stop the same process twice.

Second time through, it was gone already.

---

### Post by gilf on 2007-12-23
> **tbrothers said:**
> Ubuntu server 7.10

Thanks StormBringer!  Your config file and instructions worked Perfect!

However - for the life of me I cannot find the file smbusers.  Following your instructions and using the commands

"sudo smbpasswd -L -a <username>"
"sudo smbpasswd -L -e <username>"

I've granted the appropriate users the ability to map drives via samba ... and they all work great.  I just don't know where the user information is being stored.  I've searched the entire drive and cannot find file smbusers.

What am I missing?

Thanks,
Terry

Don't know where they are actually located, but I can suggest that they are much easier to see and manage with the graphic management program:

system-config-samba

download it with synaptics

Once installed, use it by clicking to System>Administration>Samba

---

### Post by firehelix on 2007-12-23
Another TY to stormbringer!

You gave new life to a unique (read: really old) box of mine

Just for a quick reference, the box is an old IBM PC 704 server
2 pentium pro's ( 4 capable)  at 200mhz each (lol)
1 gig of simm ram ( you know, that stuff from before SD RAM )
12 scsi hot swap hard drives in a raid
8 gig pata hard drive for /

bloody thing weighs over 75 lbs.

tried Damn Small Linux, ran and installed fine, but just installing samba was a nightmare

tried knoppix, samba ran fine, but install made everything break

various other distros just plain old didnt work, including debian, ubuntu 7.10, and ubuntu 7.04

I was about to give up on the whole project, but I came across your tut after getting ubuntu 6.06 up and running.  Thank you so much for the helping hand and making my project  something other than a complete flop :)

---

### Post by buccaneere on 2007-12-26
This sequence/process needs to be executed on all 5 machines... Correct?

---

### Post by buccaneere on 2007-12-26
[HTML]sudo chmod 0777 /media/samba[/HTML]

I got here, and the return was, 'no such file or directory'.

Somethin' about the assumptions just prior to this command I didn't follow...

Help?

---

### Post by buccaneere on 2007-12-26
What is 'fixed dhcp lease?

From my router settings (red is current values):

 DHCP Server Settings :
Use this section to configure the built-in DHCP Server to assign IP addresses to the computers on your network.

Enable DHCP Server : [COLOR="Red"]Y[/COLOR]
	 
DHCP IP Address Range : [COLOR="Red"]100[/COLOR]
	   to [COLOR="Red"]199[/COLOR] (addresses within the LAN subnet)
DHCP Lease Time : [COLOR="Red"]180[/COLOR]
	  (minutes)

---

### Post by gilf on 2007-12-27
> **buccaneere said:**
> [HTML]sudo chmod 0777 /media/samba[/HTML]

I got here, and the return was, 'no such file or directory'.

Somethin' about the assumptions just prior to this command I didn't follow...

Help?


This will work only if you have a folder called /media/samba.  You would need to create that folder.

You could name it anything -- /media/samba is just an example name.

It does have to be the same name as the one you refer to in your samba config file (look at the example toward the end of that config file)

the chmod command changes the permissions to that /media/samba file -- but since you didn't create that folder in the first place, your system reported an error -- 'no such file or directory/

---

### Post by gilf on 2007-12-27
> **buccaneere said:**
> What is 'fixed dhcp lease?

From my router settings (red is current values):

 DHCP Server Settings :
Use this section to configure the built-in DHCP Server to assign IP addresses to the computers on your network.

Enable DHCP Server : [COLOR="Red"]Y[/COLOR]
	 
DHCP IP Address Range : [COLOR="Red"]100[/COLOR]
	   to [COLOR="Red"]199[/COLOR] (addresses within the LAN subnet)
DHCP Lease Time : [COLOR="Red"]180[/COLOR]
	  (minutes)

This means that your DHCP leases are not permanent. They last for 180 minutes.

Since you are using DHCP, and since the adrress assigned to your computer only lasts 180 minutes before it is renewed (and possibly changed) you should carefully follow Stormbringer's instructions.

Mainly that means NOT enabling WINS.

That's okay, however. I'm writing you from a home network that does not use WINS in the Samba config  (like you) and it works fine.

---

### Post by 2017-Z on 2008-01-05
A very excellent guide which I enabled me to get my netowork working perfectly. However, after I did the last Windows step (to map the network drive) I can't access my laptop from Ubuntu.

"Sorry, couldn't display all of contents of Windows Network: nyx"

It was working both ways before that point (although it may because I logged out? Although I'm pretty certain it was working on re-log too) now I can only access the Ubuntu shares.

Thanks for any help - and thanks again for the howto!

BTW: nyx is the name of my Windows laptop I realized that it may sound a bit confusing.

---

### Post by jediknight1226 on 2008-01-05
I did everything you said but am unable to log in. I am trying to log in from my laptop using windows vista. I can see the computer that is running ubuntu but when i try to log in it says logon failed. It says it needs to be in the format of DOMAIN\username. I have tried everycombination I know of but it still says login failed. Am I not putting it in the right format? It is wanting the password for the linux pc right? I set up samba with the same user names and passwords as ubuntu so its not like there is that many choices. I am so frustrated please help!

---

### Post by 2017-Z on 2008-01-06
> **jediknight1226 said:**
> I did everything you said but am unable to log in. I am trying to log in from my laptop using windows vista. I can see the computer that is running ubuntu but when i try to log in it says logon failed. It says it needs to be in the format of DOMAIN\username. I have tried everycombination I know of but it still says login failed. Am I not putting it in the right format? It is wanting the password for the linux pc right? I set up samba with the same user names and passwords as ubuntu so its not like there is that many choices. I am so frustrated please help!

From my observations in the log-in box where the username goes it needs to read like this

HOSTNAME\username

or maybe

\\HOSTNAME\username

(I'm not able to check right now.)

So you need to use the name of the computer you're connecting to and not the domain name.

That is if I'm understanding what you're asking right.

---

### Post by lordViN on 2008-01-07
nice guide!!,

I have a question how can I make windows automatically connect at logon to the ubuntu share?

---

### Post by jediknight1226 on 2008-01-07
> **2017-Z said:**
> From my observations in the log-in box where the username goes it needs to read like this

HOSTNAME\username

or maybe

\\HOSTNAME\username

(I'm not able to check right now.)

So you need to use the name of the computer you're connecting to and not the domain name.

That is if I'm understanding what you're asking right.


I tried that too. \\HOSTNAME\username says invalid format and HOSTNAME\username saiys invalid login. I can get to the pc using putty to get at the command line. Its just when I try to access through network neighborhood it doesn't work. I can edit the /etc/samba/smb.conf file and change the security from user to share and it will work. I really wanted you to have to login to it though.

---

### Post by cybrough on 2008-01-11
Thanks for all of your work.  I've tried most of your suggestions and read most of post in this thread, however  I can't share my files with my windows boxes nor can I see my workgroup. i.e. when I enter this command smbclient //192.168.0.152/"My Documents" -U carl I get this response:  Domain=[CARL-DELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
I've booted KNOPPIX and it shares my files automatically.  I wonder if my Ubuntu is boken some how.  Any suggestions much appreciated. 

CY

---

### Post by gusman21 on 2008-01-11
> **cybrough said:**
>  smbclient //192.168.0.152/"My Documents" -U carl 

CY

 smbclient "//192.168.0.152/My Documents" -U carl

check your quotation marks.

-=GuS=-

---

### Post by bradmayne on 2008-01-12
hey i had samba working with gutsy for about a week.  i didn't follow your guide however.  after samba broke today i tried your guide. its didn't help. My thinking is this now: that maybe nautilus is somehow broken.  would the dmesg command help me?  what would i look for? i dunno but samba is the one package that is really making mad.

---

### Post by cybrough on 2008-01-13
I've been working to get samba working.  I can reach my windows shares with:  smbclient //192.168.0.152/SharedDoc -U carl.  But using: smbclient //carl-dell/SharedDoc -U carl returns this error:  ERROR: Badly formed boolean in configuration file: "y".
lp_bool(y): value is not boolean!
Connection to carl-dell failed

I don't know what config file is being referenced.  Also I can see that there is a windows network but none of my boxes appear in Places>Network.  Any ideas welcome

Cy

---

### Post by eolatunde4 on 2008-01-23
I have followed this HOWTO: I thought precisely, however when I go to map the drive in windows I get "An Extended Error has Occurred".  I am very new to Unbuntu.  I'm using 7.1 server addition.  I can now see Samba in my neighborhood networks.  I just can't connect to it.  Any suggestions?

Emmanuel

---

### Post by WildeBeest on 2008-01-27
I also followed stormbringers guide. Very easy to follow.

The problem I have is when I go to map a network drive on my XP box.
It prompts for the user name and password. 

This is where things hang up. The user names and passwords are the same on both Ubuntu and XP.
I type in the password and it just keeps prompting me for it.

I have a linksys router, Wins is disabled(DHCP). Both machines are wired connections.

Any idea what could be wrong?

---

### Post by ronb94 on 2008-01-27
Great howto but i have some questions:
I have two computers:
A-Ubuntu and Xp dual boot
B-XP(laptop)
When i am in ubuntu in Computer A Computer B can acess to the share folder in ubuntu.But when i am on Xp on computer A computer B  And A cant acess the share folder in Ubuntu because the Ubuntu is turning off and the xp has the same IP like in the ubuntu.
How can i acces the Ubuntu share folder when its turning off?
Thanks

---

### Post by spockrock on 2008-01-27
Has anyone experienced this, when they install winbind on the linux box you get that error message from the windows box saying that you do not have permission to access, and like wise on another linux box it it gives me the contents cannot be displayed??

Did I not setup winbind correctly, the funny thing on another setup, Winbind does not cause an issue.  Suggestions??

---

### Post by edfromballarat on 2008-01-28
just a quick note from a noob who spent all day trying to make this work with no love apart from pinging between computers

if you have a firewall running, make sure you open a port!

Samba now works a treat between Ubuntu wired desktop and wireless Vista HTPC.  The connection is a lot faster than when I had an XP desktop.  Can watch movies direct from desktop, and almost **sigh** HD movies, will have to copy them across.  Thanks for all the posters who helped me troubleshoot this problem!

---

### Post by tmcmulli on 2008-01-28
Yep, I have the same thing here.  Just removed Winbind on my Samba box.

---

### Post by spockrock on 2008-01-28
> **tmcmulli said:**
> Yep, I have the same thing here.  Just removed Winbind on my Samba box.

I am wondering what in winbind is causing the issue, its frustrating because I would like winbind and samba to work together.

---

### Post by sapperjanko on 2008-01-29
Nice little guild BUT, i am still having big probs....

Im only a n00b here so im using Windows for the forums, I couldnt copy the codes to smb.conf so i got on my ubuntu 7.10 server box, n typed that whole code out.

10-15 mins later

I then put WINS on my lovely Win 98SE and XP boxes, but with saying that, after i restarted the computer i lost all net connections.. Took me about another 5 mins before Windows would let them connect to my Router with DHCP.

But once i got that workin again, and NetBIOS disabled, i still cant connect to samba within windows, i put me password in n all, then comes back sayin i dont have access....

WHAT THE HELL AM I DOING WRONG, i followed everything. Even added the user mark

---

### Post by kalanc on 2008-01-29
Hi, I'm fairly to linux as i've just installed Xubuntu on a P3. I'm trying to set up folder sharing with XP. I can see the folders from XP, but as soon as I try to open them I get a messaage that I do not have permission to use this network resource. Can somebody please help me out on this?
I've installed samba and set up the smb.conf file as instructed.

---

### Post by spockrock on 2008-01-29
> **sapperjanko said:**
> Nice little guild BUT, i am still having big probs....

Im only a n00b here so im using Windows for the forums, I couldnt copy the codes to smb.conf so i got on my ubuntu 7.10 server box, n typed that whole code out.

10-15 mins later

I then put WINS on my lovely Win 98SE and XP boxes, but with saying that, after i restarted the computer i lost all net connections.. Took me about another 5 mins before Windows would let them connect to my Router with DHCP.

But once i got that workin again, and NetBIOS disabled, i still cant connect to samba within windows, i put me password in n all, then comes back sayin i dont have access....

WHAT THE HELL AM I DOING WRONG, i followed everything. Even added the user mark

> **kalanc said:**
> Hi, I'm fairly to linux as i've just installed Xubuntu on a P3. I'm trying to set up folder sharing with XP. I can see the folders from XP, but as soon as I try to open them I get a messaage that I do not have permission to use this network resource. Can somebody please help me out on this?
I've installed samba and set up the smb.conf file as instructed.

Hi on both your machines linux machines that you are making this change on, try this in terminal;

```
sudo apt-cache policy winbind.
```

if you get this back;
```

winbind:
  Installed: 3.0.26a-1ubuntu2.3
  Candidate: 3.0.26a-1ubuntu2.3
  Version table:
 *** 3.0.26a-1ubuntu2.3 0
        500 http://ca.archive.ubuntu.com gutsy-updates/main Packages
        500 http://security.ubuntu.com gutsy-security/main Packages
        100 /var/lib/dpkg/status
     3.0.26a-1ubuntu2 0
        500 http://ca.archive.ubuntu.com gutsy/main Packages

```

in terminal try this 
```
sudo apt-get remove winbind
sudo /etc/init.d/samba restart
```

and give it about 5 mins and try to connect to the linux machine again.  I was having a similar issue but winbind was causing the problem.

---

### Post by sapperjanko on 2008-01-30
> **spockrock said:**
> Hi on both your machines linux machines that you are making this change on, try this in terminal;

```
sudo apt-cache policy winbind.
```

if you get this back;
```

winbind:
  Installed: 3.0.26a-1ubuntu2.3
  Candidate: 3.0.26a-1ubuntu2.3
  Version table:
 *** 3.0.26a-1ubuntu2.3 0
        500 http://ca.archive.ubuntu.com gutsy-updates/main Packages
        500 http://security.ubuntu.com gutsy-security/main Packages
        100 /var/lib/dpkg/status
     3.0.26a-1ubuntu2 0
        500 http://ca.archive.ubuntu.com gutsy/main Packages

```

in terminal try this 
```
sudo apt-get remove winbind
sudo /etc/init.d/samba restart
```

and give it about 5 mins and try to connect to the linux machine again.  I was having a similar issue but winbind was causing the problem.

Thanks for the quick reply..

Now first of all doin that winbind check i also got these lines
```
500 cdrom://Ubuntu-Server 7.10 _gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages
```

I did remove winbind, now on my windows machince do i do what it said at the start of the totorial about setting up the computs with winBIOS.


EDIT:: I just was able to connect to the test user (mark) without winBIOS, atm all is working fine, but i have got write protection... How is this removed, so i can upload files..

---

### Post by Plagiarise on 2008-01-30
Brilliant tutorial!!!!!! I have been trying to get samba to work with my xbox xbmc for a week. Tried a stack of different tutes to no avail. Was almost ready to go back to XP. Working perfect now,  faster than XP. :)

---

### Post by GamingMazter on 2008-01-31
great guide :D

---

### Post by Xtrmi on 2008-02-01
I did this with my eeepc running xubuntu and my vista desktop and I haven't had any success. What I really need to achieve is to be able to access my files stored on my vista computer. I see the work group and can see the folders on my vist pc but I keep getting an error message saying that the folder can't be mounted. Anybod have suggestins?

---

### Post by matthewboh on 2008-02-02
Wow - I've been having such trouble getting SAMBA to run correctly.  But here's a few things that I was able to finally figure out.

I installed a brand new Gutsy LAMP Server and added on Samba - but kept on trying to run smbclient on the server.  I would try to run

```
 smbclient -L *Servername* -U *Username*

```

and would get back 

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_LOGON_FAILURE

```

After hours of Google searches, came across Grokking Code at [http://grokkingcode.wordpress.com/2008/01/15/note-to-self-upgrading-samba/](http://grokkingcode.wordpress.com/2008/01/15/note-to-self-upgrading-samba/) and found if I deleted out the cache - things suddenly worked.  I can now run smbclient from any Linux machine in my network and look at my Samba shares. 

Next is to figure out how to get the Places to find the server - I'll update this post.

---

### Post by moonlightcheese on 2008-02-05
i tried to install Samba and couldn't get it working out of the box.  i then tried the configuration file from this HOWTO and that didn't work either.  i still haven't gotten it working, but after researching a bit on SAMBA, there are some configuration considerations in the provided config that i feel need questioning.

first, the **netbios name**,**server string**,and **workgroup** options MUST be set in order for any Windows OS to see the share.  i don't think that's stated in the original post.

second, why did you change the default **passdb backend** to **tdbsam**?  you use smbpasswd to add and enable those user accounts but does that actually change the tdbsam users or just the smbpasswd users?

the manpage for SAMBA3 explicitly states not to use **wins support = yes** unless you are working with multiple subnets.  does this actually do anything useful when turned on?

---

### Post by nooozeguy on 2008-02-05
Update: 
I can access files from my Windows computer on my Linux system, but I cannot access Linux files from my Windows PC.

It asks me for my user name and password and I enter the info that I have confirmed is both on my Ubuntu desktop and my Vista laptop.

The information is never accepted, even though I am using the same login info on my Linux system to access Windows files.

I would appreciate any help!

Thanks,
Josh

=============

I am running a desktop on Ubuntu and a laptop on Vista Home Premium.

I have followed this guide and I can see both computers in the network on each computer.

But I cannot access files on the other computer.

I have added users to both the Linux and Vista systems with identical information.

I am (going to try) to attach a screen shot of my network folder from Linux... Can someone please explain what the icons mean (something looks wrong) and what I can do to fix this?

Thanks,
Josh

---

### Post by moonlightcheese on 2008-02-05
i got my issues fixed.  if this config file doesn't work for you, try checking your router settings to make sure your DNS settings are correct.  i changed my router IP and neglected to change the DNS entry to point to the gateway for DNS :(

in addition, wins support DOES NOT need to be on.

---

### Post by sandman652001 on 2008-02-15
Maybe you can help me I have 3 Ubuntu pc setup as per your guide an 1 windows pc that work perfectly. I recently added a server with Ubuntu gutsy 64bit on it and set it up following  this guide to the letter.
I can browse the network and I can see the shares on it but if I use the force user parameters on them I get a user id and password prompt and then I get the following error

The folder contents could not be displayed.
   Sorry, couldn't display all the contents of "common".
error message
 
it seems like a user permission problem but the user and password are correct the folders are chmodded to 777. On top of that if I share a file without the force user I can access it
any ideas? following is my smb.conf


[global]
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        announce version = 5.0
        username map = /etc/samba/smbusers
        null passwords = true
        public = yes
        passdb backend = tdbsam
        wins support = true
        netbios name = Lserver
        writeable = yes
        server string = Fileserver
        printing = CUPS
        path = /home/sandman
        workgroup = home
        syslog only = yes
        os level = 65
        printcap name = CUPS
        syslog = 1
        security = user
    ; General server settings





; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;       writable = yes
;       valid users = %S
;       veto files = /*.{*}/.*/mail/bin/
;       create mode = 0600
;       directory mode = 0755

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[common]
        path = /home/sandman/common
        browseable = yes
        read only = no
        guest ok = no
        create mask = 0644
        directory mask = 0755
        force user = sandman
        force group = sandman

[share]
        path = /home/sandman/share
        read only=no

share is accessible common is not

---

### Post by moonlightcheese on 2008-02-15
> it seems like a user permission problem but the user and password are correct the folders are chmodded to 777. On top of that if I share a file without the force user I can access it

```
[common]
path = /home/sandman/common
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = sandman
force group = sandman
```

force user is an option that actually **forces all permissions to be bitwise AND'd with the actual permissions**.  this basically means that regardless of what your internal settings are, all directories and files created through samba (remotely) will be created as the user sandman in the group sandman, as you have masked the directory and file bits with those two settings (create mask and directory mask).  set those two settings to whatever you want every file made on your share to be (as far as permissions).  the catch is that 'sandman' must have at least as many permissions as you specify for these two settings.  in other words, if directory mask = 0755 but sandman only has 0644 permissions on that share, you will not be able to execute files on the share regardless of the mask.

the fact that omitting 'force user' settings fixes your problem means that it IS a permissions problem most likely.  also you do not need to turn on wins server.  they actually tell you to leave it off unless you absolutely need it in the smb.conf man page.  i suggest reading the smb.conf man page in it's entirety.

---

### Post by the7yearplan on 2008-02-15
I set up samba on my linux desktop so that I could access some files on my windows laptop.  I ran through the howto and at first I could not see the linux box at all but after some time popped in the workgroup.  If I try to access it however I get the following error message:

"\\Linuxbox is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

The network path was not found."

The windows username and password matches the linux username.

Both computers are connected to the router by wireless only, if that makes any difference.

Also here is my smb.conf
```
[global]
    ; General server settings
	netbios name = linuxbox
	
	workgroup = jbk
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	interfaces = lo, ath0
	bind interfaces only = true

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Media]
	path = /media/
;	browseable = yes
	
	create mask = 0644
;	directory mask = 0755
	force user = krothenbaum
	force group = krothenbaum
	valid users = administrator, avahi-autoipd, avahi, backup, bin, daemon, dhcp, games, gdm, gnats, haldaemon, hplip, irc, itunes, klog, krothenbaum, list, lp, mail, man, messagebus, news, nobody, proxy, root, smbguest, statd, sync, sys, syslog, uucp, www-data
available = no
browsable = no
public = no
writable = yes
```

---

### Post by sandman652001 on 2008-02-15
you are probably right but I'm stumped, i have 4 Ubuntu pcs with the same smb.conf the only difference being the computer name.on all 4 pcs I have the same user sandman with the same password even the folders I share are the same! the only difference is that the server is the 64bit version and has no gui. I log in with putty to the server with no problem. 3 of the pcs work perfectly! the server does not!:confused:















i

---

### Post by moonlightcheese on 2008-02-15
> **the7yearplan said:**
> I set up samba on my linux desktop so that I could access some files on my windows laptop.  I ran through the howto and at first I could not see the linux box at all but after some time popped in the workgroup.  If I try to access it however I get the following error message:

"\\Linuxbox is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

The network path was not found."

The windows username and password matches the linux username.

Both computers are connected to the router by wireless only, if that makes any difference.

Also here is my smb.conf
```
[global]
    ; General server settings
	netbios name = linuxbox
	
	workgroup = jbk
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	interfaces = lo, ath0
	bind interfaces only = true

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Media]
	path = /media/
;	browseable = yes
	
	create mask = 0644
;	directory mask = 0755
	force user = krothenbaum
	force group = krothenbaum
	valid users = administrator, avahi-autoipd, avahi, backup, bin, daemon, dhcp, games, gdm, gnats, haldaemon, hplip, irc, itunes, klog, krothenbaum, list, lp, mail, man, messagebus, news, nobody, proxy, root, smbguest, statd, sync, sys, syslog, uucp, www-data
available = no
browsable = no
public = no
writable = yes
```

first of all... you have to have a server string
```
server string = linuxbox
```
second, turn off wins unless you're setting up a static IP and you know what you're doing.
third, what the :!:  is this?
```
[Media]
       path = /media/
;       browseable = yes

       create mask = 0644
;       directory mask = 0755
       force user = krothenbaum
       force group = krothenbaum
       valid users = administrator, avahi-autoipd, avahi, backup, bin, daemon, dhcp, games, gdm, gnats, haldaemon, hplip, irc, itunes, klog, krothenbaum, list, lp, mail, man, messagebus, news, nobody, proxy, root, smbguest, statd, sync, sys, syslog, uucp, www-data
available = no
browsable = no
public = no
writable = yes
```

this is a little more tidy and... sensible.
```
[Media]
       path = /media/
       browseable = yes
       create mask = 0644
       directory mask = 0755
       force user = krothenbaum
       force group = krothenbaum
       public = yes
       writable = yes
```

fourth... take out this line:
```
passdb backend = tdbsam
```
because the default value (smbpasswd) does a much better job.  then use smbpasswd to add and enable the user krothenbaum in the smbusers database and be sure to use the same password as the login password.  you can 'man smbpasswd' if you want more info on smb users.

---

### Post by the7yearplan on 2008-02-15
Made all those changes still no go same error, here is the updated smb.conf:

```

[global]
    ; General server settings
	netbios name = linuxbox
	server string = linuxbox
	workgroup = jbk
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	interfaces = lo, ath0
	bind interfaces only = true
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = no

	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Media]
       path = /media/
       browseable = yes
       create mask = 0644
       directory mask = 0755
       force user = krothenbaum
       force group = krothenbaum
       public = yes
       writable = yes

```

---

### Post by moonlightcheese on 2008-02-15
ath0?

> If bind interfaces only is set then unless the  network  address
              127.0.0.1 is added to the interfaces parameter list smbpasswd(8)
              and swat(8) may not work as expected due to the reasons  covered
              below.

the man page explicitly says not to use this option as it can mess up your configuration.  why even set it?  it looks like you're just setting random stuff.  all i'm doing is comparing your config options to the descriptions in 'man smb.conf'.  you can do this too.  it's not hard.

---

### Post by BLTicklemonster on 2008-02-16
Easiest way to network Windows to Ubuntu that I've found (only one that works for me) is in my sig.

---

### Post by moonlightcheese on 2008-02-16
here's my config and it works great.  also check your router settings, especially when using a static IP.  if your DNS settings are incorrect or something you will have issues.  i ran into this.
config:
```
[global]
    ; General server settings
    netbios name = big
    server string = big
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = smbpasswd
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = wins bcast hosts

    wins support = yes

;    printing = CUPS
;    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;   path = /var/lib/samba/printers
;   browseable = yes
;   guest ok = yes
;   read only = yes
;   write list = root
;   create mask = 0664
;   directory mask = 0775

;[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[disk]
    path = /media/disk/
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0664
    directory mask = 0775
    force group = mythtv
```

---

### Post by the7yearplan on 2008-02-16
BLTicklemonster:

I went through your write up and when I tried to access shares from my windows pc on my linux box I was able to see the workgroup but when I tried to view the contents I got the following error:

The folder contents could not be displayed.

Sorry couldn't display all the contents of "Windows Network:jbk"

moonlightcheese

Yes I was trying random things but I had gone through the original howto twice and had no luck.  No matter how I set things up I was getting the same error.

I have my router setup to give each computer on the network a static ip based on their MAC address.

---

### Post by BLTicklemonster on 2008-02-16
Try backing up smb.cnf (whatever) then remove everything in it, reboot, and start over with a clean state. I had to do that, and it worked.

---

### Post by krambo on 2008-02-19
Congratulations and thank you so much - this is by far and away the best guide yet!  I should know, I have seen them all I think!! ;)

---

### Post by theToolman on 2008-02-20
For those in Kubuntu, the config interface worked fine for me in Kubuntu when I followed the kubunutguide - very simple.

[http://kubuntuguide.org/Gutsy#Filesharing](http://kubuntuguide.org/Gutsy#Filesharing)

Important to note that the GUI has a bug that puts problematic lines in:

```
Note: If you use Sharing in KDE's System Settings panel, be aware there's a small bug, reported here: 

https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/95452 To 

summarize, you need to comment out/delete any instances of these two lines in /etc/smb.conf :

case sensitive
msdfs proxy
```

---

### Post by Warprunner on 2008-02-24
Stormbringer I can't say thank you enough!!!
This worked like a charm! :-({|=
Now I have to get the Ubuntu to Ubuntu working!!!

---

### Post by pneaveill on 2008-02-24
> **the7yearplan said:**
> 

I have my router setup to give each computer on the network a static ip based on their MAC address.

Just for clarification, is router set to give dynamic there or static IP? If truly static, then your computers need to be set for static as well.  If dynamic, then computers need to be set dynamic. Think static is easier for some with file-sharing.

Hope that helps

---

### Post by thek1 on 2008-02-26
Hi all,
congratulation for the very clear and simplified guide! I'm reaching the goal to share my disk on ubuntu box by cross cable with windows xp home edition. There are only 2 problems still alive....
1. My connection is very very slow (I tried to change the cable with no results)
2. I can share only 1 folder on fat32 partition. I can't mount a shared folder under windows xp home on the other partition. When I try to access other partition and a windows login appears I tried to insert either user and pwd created for samba shares without the form DOMAIN\USER and USER / PWD without domain.

I suppose I miss something in user permission.

Thank's in advance.
Vincent

---

### Post by pneaveill on 2008-02-27
> **thek1 said:**
> Hi all,
congratulation for the very clear and simplified guide! I'm reaching the goal to share my disk on ubuntu box by cross cable with windows xp home edition. There are only 2 problems still alive....
1. My connection is very very slow (I tried to change the cable with no results)
2. I can share only 1 folder on fat32 partition. I can't mount a shared folder under windows xp home on the other partition. When I try to access other partition and a windows login appears I tried to insert either user and pwd created for samba shares without the form DOMAIN\USER and USER / PWD without domain.

I suppose I miss something in user permission.

Thank's in advance.
Vincent

In the last few days or so, I came into a similar problem. From much googling, I have discovered that XP home does not like networking, especially at the domain level.  One must verify that XP home, does, in fact see the network at the workgroup level and not domain. Just in case you did not previously know to check on the XP machine(s) (please be careful here):

-- right click MY computer
click properties
computer name tab
edit

Hope this helps
----------- edit -------
My current problem is that I have 12 machines on a network at work about a third of them XP home and the rest XP pro. XP home registers the network as a workgroup and the XP pro sees it as a domain

---

### Post by Fiddlestx on 2008-02-28
EDIT**

I fixed it. After hours of searching I finally stumbled upon this thread.
[http://ubuntuforums.org/archive/index.php/t-589364.html](http://ubuntuforums.org/archive/index.php/t-589364.html)

I tried removing samba then re-installing it and just editing the original conf file to the paramiters in the original post, it worked :D I hope this can help someone because I know it frustrated me for the better part of a day.
-------------------------------------------------------

First one great install guide it was very clear and easy to understand.
I am having a bit of a problem getting my windows box to connect however.

My windows box is running Win XP Home and my linux box is running Ubuntu 7.10 server edition.

 I have it set up for WINS with and my linux box set with a static ip on the network. Everything works fine until I try to map the network drive. If i hit browse it lists the network and will open the computer and navigate to the share folder. However when I hit finish to map it it waits about 20sec and spits out this error: "The mapped network drive could not be created because the following error has occured. An extended error has occured."

I went throught the entire setup and have everything running properly on my linux box as far as I can tell anyways. I double checked the user login info on both computers to make sure they match.  Here is the config.

```
[global]
    ; General server settings
    netbios name = servername
    
    workgroup = workgroup
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    
    read only = no
    guest ok = nod
    create mask = 0644
    directory mask = 0755
    force user = administrator
    force group = administrator
available = yes
browsable = yes
public = yes
writable = yes
```

This is the error output: 

```
[2008/02/28 10:10:56, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/28 10:10:56, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/28 10:42:56, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/28 10:42:56, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/28 11:14:56, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/28 11:14:56, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

Any help would be great appreciated as I'm completely lost with all this.

---

### Post by DingsBumps on 2008-02-29
Great guide, but I'm encountering a problem. The XP user I wish to add has a space in their name (eg: John Smith).
Following the configuring SAMBA guide linked to in the article, I found there is a -m switch used with the smbpasswd command to indicate that the user is actually a machine, so you can auth a whole machine instead of 1 user.

> In the following example we will add an user called "mark" ...

Example:

```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```


So to add the XP PC, I do 

```
sudo useradd -s /bin/true FAMILY-PC
sudo smbpasswd -L -a -m FAMILY-PC

```
And I get this:
```
marc@marc-desktop:~$ sudo smbpasswd -L -a -m FAMILY-PC
Failed to modify password entry for user FAMILY-PC$

```

Any suggestions?

---

### Post by swordphsh on 2008-03-05
Does anyone know exactly how safe this samba sharing is?

I live in a college dorm room and would like to share files with my room mate, but am afraid my computer could be vulnerable to the rest of the network.

 I want to know if it's safe to leave my samba service on all the time or not.

Thanks.

---

### Post by siroche on 2008-03-14
Thanks for the step by step but...
followed the steps
on my XP machine I can network to my laptop (ubuntu) via the workgroup but when I put in the \\simon-laptop\home\samba and hit enter it requests a user and password which I enter, then it comes back as 'The folder you entered does not appear to be valid. Please choose another'
I'm bambozzled !
This is the smb.conf
[MyFiles]
    path = /home/samba/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = simon
    force group = simon

/home/samba also shows up under admin > shared folders too
What do I do now ?

---

### Post by siroche on 2008-03-15
Further info if it helps
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      
        MyFiles         Disk      
        IPC$            IPC       IPC Service (Samba 3.0.26a)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

        Server               Comment
        ---------            -------
        OLIVERROCHE01        Home_PC
        SIMON-LAPTOP         Samba 3.0.26a

        Workgroup            Master
        ---------            -------
        WORKGROUP            OLIVERROCHE01

---

### Post by siroche on 2008-03-17
OK, I think its time to install XP again - I give after this last post. Still cannot get a shared file between XP and ubunto.
Only error I got 
mount: can't find //simon-laptop/home/samba in /etc/fstab or /etc/mtab
simon@simon-laptop:~$ sudo mount -l
 
Here is the contents of FSTAB
simon@simon-laptop:~$ sudo mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
simon@simon-laptop:~$ sudo gedit /etc/fstab

after this I give up and Bill wins !!!

---

### Post by mdarif79 on 2008-03-20
hi cant u help me... i have follow your instructure but having problem

teknikal@teknikal:~$ sudo apt-get install samba
[sudo] password for teknikal:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate
teknikal@teknikal:~$ 

what cant i do to his problem

---

### Post by notepad on 2008-03-23
the [homes] section completely fails to work on ubuntu 7.10 running samba 3.0.26a. ive tried changing settings and restarting samba dozens of times and nothing makes it work.
does anybody have a working [homes] that shares between two ubuntu machines?

---

### Post by bornfree on 2008-03-27
i got a question.. i need to share 2 directories.. /home/shares/test and /home/shares/allusers for 2 users, tom and officer

tom can only access to the test directory, but officer can access both folders but i cant seems to make my samba do the share in this way.. below is my smb.conf file. please point out my mistakes. thank you.

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = user
    username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
wins support = no
[homes]
   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

available = yes
browsable = yes

[www]
path = /var/www
available = yes
browsable = yes
public = yes
writable = yes

[test]
 comment = tom user
 path = /home/shares/test
; valid users = tom
 force users = tom
 force group = tom
 create mask = 0660
 directory mask = 0771
 writable = yes

[allusers]
 comment = All Users
 path = /home/shares/allusers
; valid users = officer 
 force users = officer 
 force group = officer 
 create mask = 0660
 directory mask = 0771
 writable = yes


```

---

### Post by mabbasj on 2008-03-28
hi All,

I am using Ubuntu 7.10.
I am facing problem regarding Maping of share from Win XP.It giving me error of " Network Path could not found" . 
I checked every thing there is no firewall or like that install at both end.
Please suggest me.

---

### Post by tobydeemer on 2008-03-28
Hi Stormbringer-

I was hoping you might be able to help me out. I started a thread here:
[http://ubuntuforums.org/showthread.php?t=738567](http://ubuntuforums.org/showthread.php?t=738567)
Mostly because I felt shifty about posting something that long onto your thread. Anyway, I was hoping you'd be willing to look at my setup and throw out some ideas. Please feel free to leave your answeres on this thread if you prefer so that others can see them more easily; I just didn't want to bog everything down. I'm using the smb.conf from your guide, tailored to my network, and it's *almost* there...


Thanks a lot for any ideas.

---

### Post by GodsDead on 2008-04-02
This is an ausom setup, i managed to get both my Disk drives setup etc, which is cool, apart that you cant view "CD's" or audio disks as ubuntu calls them Via the network!!! how can i set this up?

and also, how can i setup the network so no username or password is needed, since its all via LAN i dont need to worry about security! 

Cheers

---

### Post by Eiríkr on 2008-04-10
Hello Stormbringer --

Many thanks for your HOWTO.  I haven't used it myself to be honest, but I've seen how helpful it's been to many other posters on the forum.  

Over time, it appears that some things have changed, such that some of your guide unfortunately no longer applies quite correctly.  I have noted a few points and conf file options that might need changing from what's listed in your template, which I describe here.

----------

> **Stormbringer said:**
> **1. Prerequisites**

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

This no longer seems to be the case.  I had a DHCP setup with all dynamic addresses, but, provided I had "wins support = yes" and "preferred / domain / local master = yes" in my smb.conf file, I never needed to specify any WINS server address on the Windows side.  (NB: Nor do I have **winbind** installed.)

Here's the [global] section from the initial template in your original post.  The bold options seem slightly problematic. 
```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    **server string =**
    workgroup = YOUR_WORKGROUP
    **announce version = 5.0**
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    **null passwords = true**
    **username map = /etc/samba/smbusers**
    name resolve order = hosts wins bcast

    wins support = yes

    [b]printing = CUPS
    printcap name = CUPS[/b]

    syslog = 1
    **syslog only = yes**
```

Let's look at these bold options one by one.  I link to the relevant man page section in the name of each.

**[server string](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SERVERSTRING) =**
Since this is blank, may as well leave it out for simplicity's sake (simple is good! :)), and allow the server to use the default value of "Samba %v", where %v is the package version.

**[announce version](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ANNOUNCEVERSION) = 5.0**
This setting is very likely completely unnecessary.  Beyond that, this value of "5.0" appears to be bogus.  From the man page:
> This specifies the major and minor version numbers that nmbd will use when announcing itself as a server. The default is 4.9. **Do not change this parameter unless you have a specific need to set a Samba server to be a downlevel server.**

Default: *[font=courier]announce version = 4.9[/font]*

**[null passwords](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NULLPASSWORDS) = true**
This strikes me as a bad idea, security-wise.  This option is only relevant if you have Samba accounts for which no password has been defined, and has nothing to do with guest access.  I would *strongly* recommend removing this option unless there is a real compelling reason to configure and then use Samba accounts with no passwords.  

**[username map](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP) = /etc/samba/smbusers**
This option is not a problem at all, but I was confused that you include the option but don't describe how to use it.  This allows you to log in from Windows (or any other Samba client) with a username that does not actually exist on the Ubuntu machine.  This can be very useful in terms of security, or simply in making things easier for the user.  It's also possible to map multiple client usernames to a single server-side username.  More on this below.

[b][printing](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING) = CUPS
[printcap name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME) = CUPS[/b]
Neither of these options belongs in the [global] section.  They are *only* relevant within a share definition for a printer.  

**[syslog only](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOGONLY) = yes**
This means that most Samba server process messages are shunted to the /var/log/syslog file.  While not a problem in and of itself, the syslog is already a very busy file, making it harder to sift through and find Samba-related messages.  Over time I've learned that it's much easier to have Samba's logging info sent to the default /var/log/samba/log.smbd and log.nmbd files.  As with anything, YMMV (your mileage may vary).  :)


It's worth pointing out that the following two share definitions are *only* relevant for users actually sharing a printer via Samba.  If you're not doing that, remove these shares to simplify your conf file.  
```
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no
```


> **Stormbringer said:**
> Ok, I already mentioned that there are a few simple things you may need to tweak; so here they are:

-> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.
See above description.  This no longer appears to be the case; a fully-dynamic DHCP setup seems to work just fine with "wins support = yes" and no WINS server specified on the Windows side.  

> **Stormbringer said:**
> -> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!
Spaces are allowable, but they complicate things.  In the /etc/fstab file, spaces must be replaced with **\040**.  In mount commands, you can simply double-quote the part of the path that has spaces: **//server/"share name with spaces"/subdirectory**


> **Stormbringer said:**
> -> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

These options are irrelevant for single-user setups.  Such forcing is really only needed for shares accessed by multiple different people, where you want any files or directories created to have the owner and / or group set to YOUR_USERNAME.  The Samba server uses real login usernames for any file operations, which is why you can only run **smbpasswd** for usernames that actually exist on the server.  This also means that users accessing a share via Samba will be subject to the regular filesystem rules for Unixy systems -- any files or directories created will, by default, have that user as the owner and group, unless otherwise specified by the setuid or setgid permissions on the shared directory, or by these **force user** or **force group** options.  


> **Stormbringer said:**
> **1.1 Starting samba and setting up user accounts**

...

Time to add yourself as an samba user.

*NOTE: You will be asked for a password - make sure you use the same as you use for login!*

```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

It is not necessary that the usernames and passwords on the server and client match -- they can be different, and for the security conscious, they even *should* be different.  Note that the username you supply to the **smbpasswd** command ***must*** exist as a real Ubuntu username on the server.  However, the username you use on the client side (or that you give your friends so they can access your Samba shares) does *not* need to match this same username, *provided* you use the **username map** option in the [global] section.  Have a look at [post=4496702]this post[/post], particularly the "In the [global] section" portion, for a description of how username mapping works.  


> **Stormbringer said:**
> [i]NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box 
just press enter when prompted to enter a password for the user account you're about to create![/i]

This is where the **null passwords** option marked above comes into play.  Note that null passwords are an extraordinarily bad idea in this day and age.  It's awfully close to simply leaving your doors wide open for anyone to walk right in.  Leave it to Windows to have null passwords as the default.  :(  Seriously, **unless you have a real, compelling reason to have null passwords, do *not* do this.**  Set a password.  There, you've been warned.  :)


> **Stormbringer said:**
> **2. Changing network settings in Windows**

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

As described above, **wins support = yes** seems to work just fine on dynamic DHCP-configured networks, so there's no reason to set this option to "no", and there's no reason to go to the trouble of specifying a WINS server on the Windows side.

----------

Hope this helps,

Eiríkr

---

### Post by Eiríkr on 2008-04-10
> **GodsDead said:**
> This is an ausom setup, i managed to get both my Disk drives setup etc, which is cool, apart that you cant view "CD's" or audio disks as ubuntu calls them Via the network!!! how can i set this up?

and also, how can i setup the network so no username or password is needed, since its all via LAN i dont need to worry about security! 

Cheers

While there is such a thing as "guest access" in Samba whereby no username or password is required, it's actually quite complicated to set up properly.  If you're accessing your Samba shares via Windows, just map a network drive to the share, click the "Reconnect at logon" box in the dialog, and enter your username and password just this once when prompted.  Once you've done this, the drive (i.e. share) will automagically mount every time you log in with no need to ever again enter your username or password.  If you're accessing your Samba shares via Ubuntu, Nautilus (your file browser) should have a radio button option on the username and password dialog that says "Remember forever".  Clicking this means you'll never again need to enter your username or password to access this share.  

HTH,

Eiríkr

---

### Post by rado_london on 2008-04-14
Thank you very much for the good howto guide. I was afraid of using Samba due to its complicated (at least I thought it was) configuration, but now I can use Ubuntu on my server and never even consider Windows an option. It makes my HDD parts dirty:lolflag:

---

### Post by jdix123 on 2008-04-17
I want to set up a single share that all users on my network have access to, but I don't want to have separate users added to my server for each and every one of their windows logins.  Is it possible to have a single user and password linked to the share and have multiple machines logging on to it?

---

### Post by Newbie1978 on 2008-04-23
Hello! first let me thank you for this guide is very detailed but even so I don't know where I mess up, I follow every step until the 2. Changing network settings in Windows, I do that part and reboot but when I try to map the network drive within Windows I get an error saying that the IP addres or the hostname and sharename can not be found, I'm trying to run an Ubuntu Pc on a Windows XP. Please help anyone I'm down to the last steep

---

### Post by LeeU on 2008-04-28
I have a guess. I was having the same problem and finally figured out it was the path. Let's say that in the smb.conf file you have the following (in the right places, of course):

   netbios name = bob-desktop
   path = /home/bob/Somewhere/
   force user = bob

When the little window pops up in Windows when you go to map the drive, place this in it, on separate lines:

bob-desktop\bob
\\bob\Somewhere

That seemed to work for me (with different settings, of course).

I'm trying to figure out how to access a second drive on Ubuntu from Windows.

---

### Post by LeeU on 2008-04-28
I have a guess. I was having the same problem and finally figured out it was the path. Let's say that in the smb.conf file you have the following (in the right places, of course):

   netbios name = bob-desktop
   path = /home/bob/Somewhere/
   force user = bob

When the little window pops up in Windows when you go to map the drive, place this in it, on separate lines:

bob-desktop\bob
\\bob\Somewhere

That seemed to work for me (with different settings, of course).

I'm trying to figure out how to access a second drive on Ubuntu from Windows.

---

### Post by Iamiko on 2008-04-29
Thanks Stormbringer... this guide just saved my sanity twice in one month! I managed to get my samba server set up and working a couple of weeks back and after my Ubuntu went pear-and-melon shaped on update from 7.10 to 8.04 it saved my sanity again as a very frustrated and panicy college student trying to get their laptop fixed for college!

:guitar:You rock :p

---

### Post by the_new_z on 2008-04-30
Guys,

I used the configuration described here and everything worked fine for over 2 years.  Now, all of a sudden it stopped working without any intervention on my part.  When I try to (re)start the SAMBA daemon, it fails.

I have an Ubuntu 6.04 server and only one XP box on the network.  I am using the server for torrents, so I used SAMBA to connect from the XP machine.

Here is my smb.conf

```

[global]
    ; General server settings
    netbios name = server
    server string = Samba Server
    workgroup = GITS
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth1
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    load printers = yes
    printing = cups
    printcap name = cups

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    comment = All Printers
    browseable = no
    path = /tmp
    printable = yes
    public = yes
    writable = no
    create mode = 0700
    printcap name = /etc/printcap
    print command = /usr/bin/lpr -P%p -r %s
    printing = cups

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[public]
    path = /fat
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = flower
    force group = flower

```

Here is syslog

```
Apr 30 15:40:05 server smbd[9117]: [2008/04/30 15:40:05, 0] param/loadparm.c:lp_do_parameter(3412)
Apr 30 15:40:05 server smbd[9117]:   Global parameter printcap name found in service section!
Apr 30 15:40:05 server smbd[9117]: [2008/04/30 15:40:05, 0] smbd/server.c:main(829)
Apr 30 15:40:05 server smbd[9117]:   ERROR: failed to setup guest info.

```

What is this failure to set up guest info!?

---

### Post by LeeU on 2008-05-02
If you want access to the home directories, check this short tutorial: [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/#comment-48625]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/#comment-48625"). It makes a great addition to this one.

---

### Post by Fraoch on 2008-05-07
Does this still work for Hardy?  I'm having a fair amount of problems - the networking app times out and it can't find shares without entering them manually, see [http://ubuntuforums.org/showpost.php?p=4897393&postcount=4](http://ubuntuforums.org/showpost.php?p=4897393&postcount=4)

---

### Post by guyfromfl on 2008-05-09
Storm, 
Thanks for your help.

You may have already gone over this topic, but at 51 pages...I got bored at 18 and decided to write a new reply :)

Problem: 

I am running 5 machines on my network, 3 win and 2 linux boxes.

My computers are
M4.SAMBA - linux & domain master static 192.168.1.111
MARK-XPS - Windows Vista

other computers:
Dellie - Linux static 192.168.1.112
Inspirion - Win Vista

packie - win xp

the reason i pair the computers is because I am using mine as a mini lan within the lan in my room, and same with the other win/lin pair but another room.  but all run on the workgroup TDC.

ok here's the problem:

both win's can write to the linux boxes, but neither linux boxes can 'see' the network.  in the file browser when you goto network and try to get on the windows network it just hangs. 

smbclient -L localhose -U% returned the same data you listed so it knows its surroundings.

any ideas?

thanks
mark

---

### Post by that_IT_guy on 2008-05-13
Ok, first off I did not read every page of the thread.  But what worked for me on a clean install of 8.04 (Hardy I think) was simply by doing pretty much the oppisite of what the first page of this thread tells you to.  I set my primary nic's IP to static, and for some reason beyond me I could not ping my gateway(and Im in the IT field as the name implies so ipconfigs are nothing new).  Any way, I decided to go the DHCP route, obtained an IP address and ran "smbtree" in the terminal and all my shares were there.
Really simple really stupid, but may be the fix for you.
Good luck. 
Hope my lil spiel helps you out.

---

### Post by BeastlyKings on 2008-05-14
I haven't read but 4 pages of this thread, but I have a prob.
I can't see my linux shares from either of my windows machines (1x XP 1x Vista).
I can connect to my linux box and I can see the printers on said box, but none of the shares.

[My Config file]("http://pastebin.com/f44c9d2d2")
[Vista Network Image]("http://i28.tinypic.com/1fe98h.jpg")
[XP Network Image]("http://i27.tinypic.com/34pz0hw.jpg")


Please help? This is very frustrating..




EDIT: FIRGURED IT OUT!! I was mapping to the physical directory on my linux box and not "MyFiles". So stupid..
Although I think there was more to it than that, it works now!

---

### Post by Plasma_NZ on 2008-05-19
Ok - awesome guide - absolutely flawless... congrats

But im trying to use the printer on this linux box with a windows box, windows box says denied..? what do need to change..?

---

### Post by Erlander on 2008-05-19
Try System/Administration/Printing and under the Policies tab make sure that "Shared" is checked.

Good luck.

Rob

---

### Post by nilsw on 2008-05-19
Thanks for a well written howto! It works fine for shared files. But I have a problem using my HP 2110 printer from Windows XP. After loging on to the printer from Windows i get the message "The server for the printer does not have the correct printer driver installed. ..." The search proposed does not display info for my HP 2110 (which also is installed on the windows machine) and the Have Disk option does not find a driver on the printer installation disk. The printer work fine from Ubuntu and is set up for sharing.
Is it a driver for windows or Ubuntu that is missing?

Found the solution in: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
"For a driver, you should select the "MS Publisher Color Printer" driver from the "Generic" manufacturer. This driver should be found on all Windows 2000 and XP installations by default and it gives all the printing functionality one can need. "

---

### Post by calif99x on 2008-05-21
Hi:

I need some help with getting my Samba going. This guide was the most useful after moving from Ubuntu 7.10 to 8.04 broke my Samba setup.  

Using the process, I was able to get most of my Samba shares visible and working again... for a short time period.

I noticed a couple of my shares were not showing up and the difference was the working shares were owned by "fred" and group "fred"; the non-visible (non-working) ones were owned by "root" as they were NFS drives brought over from a Windows box.

No problem I thought, I will simply add usershare only = no to allow the other shares to be used.  Poof --- Samba is again not working; and now the Windows XP box will not even see my Samba/ Ubuntu system anymore.  OK, I will just delete out the change; no, that does not fix the problem; the system running Samba is no longer visible on the network.

I can ping the Samba system, but MS Network places does not list the box, and none of the commands on Windows XP such as "net view sambabox" work ( I get system error 64).

It almost seems that there is a compiled file somewhere that I need to delete/flush/update.

Any help in getting things back on track would be appreciated.

---

### Post by Troberg on 2008-05-23
Another guy here that got his Smaba killed by the Hardy upgrade. Killed it on all machines that had samba shared (10 machines, give or take), so it's not an isolated problem. All machines were set up using this guide.

I can see the shares, both from Windows, Linux and Xbox with XBMC, but I can't log on to them.

I've tried to recreate the users, but it made no difference. I've been wrestling with this problem since Hardy was released, and now I'm stumped. Big puppy eyes help, please!

---

### Post by Neobuntu on 2008-05-25
Firewall?

---

### Post by Troberg on 2008-05-25
I don't think so, I don't use firewalls on the machines which are safely inside my own network.

How do I check if Hardy added one without telling me?

---

### Post by raymondvillain on 2008-05-26
Thanks for a great how to!  Just want to add that I didn't bother to mess with the fixed ip address stuff AND I left "wins support=yes" and my laptop with windows Vista found the Ubuntu box! Fantastic!

It also (windows machine) found the printer on the Ubuntu box!  Milagro!

Now if I could just get my bluetooth mouse wheel to work!

Thanks again!

---

### Post by other guy on 2008-05-26
Great help having this tutorial. Simple, easy and now no more sneaker net.

Thank you for the simple yet effective guide.

---

### Post by gary4gar on 2008-05-27
How to share multiple Directories?
like i want to share my /home,/media & /mnt dir
Please tell how to do it?

---

### Post by Troberg on 2008-05-27
Just add additonal sections for each directory, just like the first, and it should work just fine.

---

### Post by berrydfu on 2008-05-31
This is my first Ubuntu computer just got it built and I am a total noob.  I want to be able to access all my media files on my Windows computer. 

Great How-To, but haven't been able to finish step 2. Changing network settings in Windows.  When I attempt to map the network drive within Windows I receive an error stating, "network path could not be found".  

System
Hardy Heron 64 bit box and XP Media Center 2005 on my Windows box.

Both user names and passwords are the same on both boxes.  I tried once with WINS enabled and again without WINS enabled.  I currently have my IP addresses locked in my router under DHCP.  I also disabled my firewall. No luck either way.

Any help would be greatly appreciated.

---

### Post by Troberg on 2008-05-31
Berrydfu: That's the same problem I have, got it in the upgrade to Hardy. Anyone, please help!

---

### Post by kiev on 2008-06-02
** **
** **
[B]How do I can it to setup through the visual interface of kde?!!!
** **
For 10 years in linux the same problems!!! !!! !!![/B]
** **
** **
** **
[img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] [img]http://ubuntuforums.org/images/icons/icon8.gif[/img]
** **
** **

---

### Post by calif99x on 2008-06-02
Suggest you use the Synaptic package manager under administration to install Samba, Sambafs and Nautilus (if not already installed).  You will be given some suggestion for other items to install; use judgment to decide if the make sense.

I strongly suggest you also install Webmin as I used this to configure the shares (under the servers link) I wanted to show to Windows.  You may need to use a terminal window to set the Samba password if you are using a different user or want a different password for network access.

No manual editing of the smb.conf file is necessary with this tool.

Just access network neighborhood from windows and enter login/password for samba when prompted.

Cheers

---

### Post by darthrevan13 on 2008-06-06
Awesome tutorial, but I'm having one little issue
I can't see any files shared on my windows computer from Ubuntu but i can see the files i shared from Ubuntu on my windows computer. I deactivated any kind of firewall, I tried deactivating sharing to a partition then sharing it again but I still can't see anything on Ubuntu. Any idea why?

---

### Post by Fraoch on 2008-06-06
> **darthrevan13 said:**
> Awesome tutorial, but I'm having one little issue
I can't see any files shared on my windows computer from Ubuntu but i can see the files i shared from Ubuntu on my windows computer. I deactivated any kind of firewall, I tried deactivating sharing to a partition then sharing it again but I still can't see anything on Ubuntu. Any idea why?

[http://ubuntuforums.org/showthread.php?t=784259](http://ubuntuforums.org/showthread.php?t=784259)

A known problem for lots of users in Hardy.

---

### Post by edcpartners on 2008-06-10
What is Samba?

Is it new?

---

### Post by dmizer on 2008-06-10
oops.

---

### Post by Johnsie on 2008-06-12
I read this and it seems like alot of work. Put simply, it's alot easier to do in Windows.

---

### Post by Troberg on 2008-06-12
OK, at last I found my problem!

I had specified both group and user in smb.conf, which worked nicely in Gutsy and earlier. When I removed group, it worked perfectly again. Yay!

Now, I only have to make this change on 12 other machines as well. Yay...

---

### Post by dmizer on 2008-06-12
> **Johnsie said:**
> I read this and it seems like alot of work. Put simply, it's alot easier to do in Windows.

i still clearly remember the first time i tried to set up a share between two windows computers.  it took me more than a week to figure everything out, and still regularly had problems when windows update came around.

took me about the same amount of time to figure out how to set up shares in ubuntu.  and once i set everything up, i never had to touch it again.

now that i know how to set things up, i can do both equally quickly.  sometimes ubuntu is much faster because it doesn't need to reboot in order to change the workgroup or netbios name.

different?  yes.  easier?  not necessarily.  please remember to keep in mind how much time you've spent learning how to make windows work, compared to how much time you've spent learning how to make linux work.

---

### Post by Roasted on 2008-06-15
Yeah. Windows is definitely a little more finicky with ironing out the issues and seems to require constant configurations in days/weeks/months to come. The only time I adjust samba is when I do a fresh install of a new distro. 

Back on topic, I have a few questions. I was reading through this how-to and some curiosity was sparked.

I noticed that the one part of this how-to spoke about mapping the network drive. There are 6 computers on my LAN, and my main desktop I dual boot. My main desktop is also the samba server. Since there will be times that samba will be down due to me being in XP for gaming, perhaps it'd be wiser to avoid putting that change in? I remember trying to map network drives before, and I got a ton of errors on the other machines saying unable to map network drive.

My setup is very simple, in my opinion. I set up the config file. I set the netbios name and all that garbage. I also added 4 users and set the permissions and whatnot. Then, I created the users, created the passwords for the users, and started the samba daemon. Bam. Done.

Now, the way users log in to the samba server, is they go to start - run - 192.168.x.x, a username/pw box comes up. They log in, and see 4 folders. They click on their folder (each user ONLY has access to their designated folder) and they can drag/drop accordingly to organize their files in their share.

Considering the nature of my setup, along with the fact that my samba setup doesn't run 247 due to me dual booting once in a while, do you folks think it's worthwhile to map the network drives for the sake of simplicity? Or should I keep everybody just start-run-192.168.x.x'ing to back up their files?

---

### Post by dmizer on 2008-06-16
> **Roasted said:**
> I noticed that the one part of this how-to spoke about mapping the network drive. There are 6 computers on my LAN, and my main desktop I dual boot. My main desktop is also the samba server. Since there will be times that samba will be down due to me being in XP for gaming, perhaps it'd be wiser to avoid putting that change in? I remember trying to map network drives before, and I got a ton of errors on the other machines saying unable to map network drive.

[snip]

Considering the nature of my setup, along with the fact that my samba setup doesn't run 247 due to me dual booting once in a while, do you folks think it's worthwhile to map the network drives for the sake of simplicity? Or should I keep everybody just start-run-192.168.x.x'ing to back up their files?

mapping the network drive in windows is not much more than a convenience.  it primarily addresses the aversion that most windows users seem to have with passwords.  if you map the drive, then the windows user never sees the password prompt because it's handled through the mapping.

if your windows users don't mind typing a password to access their share, then it probably isn't necessary to map the drive.

---

### Post by rplantz on 2008-06-19
I'm still going through these (so far) 62 pages. Very good remarks, but lots to read.

The original HOWTO suggests using fixed IP addresses so I can get the benefits of WINS.

1. What are the tradeoffs of using fixed IP addresses in my LAN? I would still get a dynamic IP address from my ISP, but I can configure my router so that each machine in my home has a fixed IP address --- 192.168.1.nnn

2. What are the benfits of WINS?

I can sorta get things to work, but my setup feels "messy" to me. For example, the only way I could transfer some files the other day was to connect my Mac to both Ubuntu machines and use the Mac to copy the files. It worked but didn't feel right. I'm trying to understand things rather than just getting them to "work."

---

### Post by dmizer on 2008-06-19
> **rplantz said:**
> I'm still going through these (so far) 62 pages. Very good remarks, but lots to read.

The original HOWTO suggests using fixed IP addresses so I can get the benefits of WINS.

1. What are the tradeoffs of using fixed IP addresses in my LAN? I would still get a dynamic IP address from my ISP, but I can configure my router so that each machine in my home has a fixed IP address --- 192.168.1.nnn

2. What are the benfits of WINS?

I can sorta get things to work, but my setup feels "messy" to me. For example, the only way I could transfer some files the other day was to connect my Mac to both Ubuntu machines and use the Mac to copy the files. It worked but didn't feel right. I'm trying to understand things rather than just getting them to "work."

no, the original post indicates that you'll need fixed ip if you want the ubuntu computer to function as a wins server.  if you have a windows computer on your network, this is not necessary.  just set the "wins support = yes" to "wins support = no" and carry on.

the benefit of moving to a static network and using wins is that you have a centralized name server, which makes local names resolve more quickly.

---

### Post by rplantz on 2008-06-19
> **dmizer said:**
> 
the benefit of moving to a static network and using wins is that you have a centralized name server, which makes local names resolve more quickly.

But doesn't my router resolve the local names? I have "DHCP Server" enabled on it. It shows:
```

Host Name     IP Address
bob-PC        192.168.1.103
ubuntu        192.168.1.101

```
which seems reasonable to me. And if I boot up my Mac (OS X) it also appears on the list with another IP Address without going out to the internet.

I'm assuming that if one of my computers wants to talk to another, it can use the other one's name and my router will resolve the IP address.

Wouldn't this be faster than using wins on another computer? And if I did choose to use wins, wouldn't I have to always have the wins server on?

---

### Post by dmizer on 2008-06-19
> **rplantz said:**
> But doesn't my router resolve the local names? I have "DHCP Server" enabled on it. It shows:
```

Host Name     IP Address
bob-PC        192.168.1.103
ubuntu        192.168.1.101

```
which seems reasonable to me. And if I boot up my Mac (OS X) it also appears on the list with another IP Address without going out to the internet.

I'm assuming that if one of my computers wants to talk to another, it can use the other one's name and my router will resolve the IP address.
for most practical purposes, this is correct.  the only exception i can think of is cifs, which i will discuss below.

> **rplantz said:**
> Wouldn't this be faster than using wins on another computer? And if I did choose to use wins, wouldn't I have to always have the wins server on?
yes it would be faster than having wins on, and yes, you would always need a windows computer or wins server turned on.

i have not yet (personally) run into a situation where i needed "wins support = yes".

the only problem you may run into with your setup is connecting to windows shares by name from ubuntu.  but that wouldn't be fixed by having "wins support = yes" anyway.

---

### Post by kismeras on 2008-06-23
Hey Guys, 

Great post. However, after following the instructions i still have this problem.
My problem is that Windows can see the Ubuntu shares. However, Ubuntu can see the windows computers on the network, but it can NOT see the files that are being shared. If i enable simple file sharing in windows, then it works. However, i don't want to use simple file sharing. Anyone seen this before? Thanks.

---

### Post by dmizer on 2008-06-24
> **kismeras said:**
> Hey Guys, 

Great post. However, after following the instructions i still have this problem.
My problem is that Windows can see the Ubuntu shares. However, Ubuntu can see the windows computers on the network, but it can NOT see the files that are being shared. If i enable simple file sharing in windows, then it works. However, i don't want to use simple file sharing. Anyone seen this before? Thanks.

this howto is for allowing windows computers to see shares on your ubuntu computer.

if you want to view windows shares from your ubuntu computer, please see the second link about cifs shares in my sig.

---

### Post by linuxnovice on 2008-06-24
Hi,

I have been using this tutorial since Fiesty and have had no problems. A couple of weeks back I installed Kubuntu Hardy and setup samba according to this tutorial and I had no problems and everything went smoothly. A week back, my wireless router was behaving funny so I had to reset it which kind of messed up the IP's. Though I was using dhcp my windows box and linux box would always get the same IP assigned to them during boot-up. But after reset the router, I had to setup samba once again. 

After setting up samba (following this tutorial), now I am able to see all the folders that I shared on my windows in Kubuntu. I am even able to mount the remote smb shares. However, whenever I try to map the network drive in windows, I get the following error:

"The mapped network drive could not be created because the following error has occurred:

An extended error has occurred"

This is really weird, it does not even tell what kind of error it is. I made sure all the IP's are correct. As far as I know I dont think I have any firewall installed on Kubuntu unless the distro came with one. So I really dont know what is wrong here.

Currently my kubuntu box has the IP 192.168.2.4 and windows box has the IP 192.168.2.2. I have a belkin wireless router.

Here are the contents of my smb.conf file:

[global]
    ; General server settings
    netbios name = HARDY
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/myvault/sambashare
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ss
    force group = ss

Any help is greatly appreciated.

Thanks.

---

### Post by skrimpy on 2008-06-24
I am using a Feisty install and have a Windows XP computer.

I used this guide to get my Samba configured and working well.  I had it set up so that my Windows computer had access to my /var/www file.  I use a CSS editor that doesn't have a Linux build.  I develop the rest of my stuff on my LAMP here on my Linux box.

Previously I had my /var/www mapped and accessible from Windows so I could use my CSS editor to open and write to .css files that are housed on my Linux computer.  

It worked flawlessly.

I haven't changed anything in Samba.  But suddenly its not working.  I am getting an error when I try to reconnect to the network drive (after rebooting the windows computer for something)

"An error occurred while reconnecting Z: to \\my-ip\www
Microsoft Windows Network: An unexpected network error occured.
This connection has not been restored"

I am pulling my hair out trying to figure out what is going wrong.  

It prompts me for my user name and my password (for my Linux user), then I get that error.

Any suggestions?

---

### Post by Troberg on 2008-06-24
Skrimpy and Linuxnovice, try removing or commenting out the line "force group = something". It helped for me.

---

### Post by skrimpy on 2008-06-24
Thank you Troberg, that worked immediately for me!  I wonder why the group started messing things up when its been working flawlessly for months?

---

### Post by linuxnovice on 2008-06-25
> **Troberg said:**
> Skrimpy and Linuxnovice, try removing or commenting out the line "force group = something". It helped for me.

Do you mean the one in the bold? You mean that I just comment it out?

[MyFiles]
path = /home/myvault/sambashare
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = ss
**force group = ss**

---

### Post by Troberg on 2008-06-25
Yep, that's the one. Remove or comment out, according to taste.

This thread is getting long and contains a lot of historical stuff. Perhaps it's time to gather the current bits and start a new one?

---

### Post by jacobleonardking on 2008-06-26
I have the following setup:

Ubuntu hardy 8.04 server w/ samba, bind9, etc acting as MDC with shares, validating login, etc.
Several WinXP clients.

The clients can log in with samba accounts on the domain, access shares, etc. They can access local drives. However, they cannot install programs or do anything else that requires local administrative access. This would be reasonable, but they don't get a prompt on the client machines for the local administrator password; they just get an error that they don't have administrative priviliges on the machine.

It is horribly inconvenient to log out of the client machines, and log back in as administrator every time we want to install a program.

Presumably there is some setting in smb.conf or somesuch to fix this? I've been looking, but can't find it.

Thank you muchly in advance.

---

### Post by ybd on 2008-07-01
Thank you Stormbringer, this guide worked for me, after some fiddling around. Great job for all that dedication to the community!

---

### Post by rplantz on 2008-07-01
Please add my thanks; this thread has been very helpful.

Most of my problems seem to have been due to my lack of understanding some terminology, especially on the Windows side. My career in computer science began in 1961, but I'm a newbie to Windows. :D

For those who might be interested, I've explained my solutions at [http://ubuntuforums.org/showthread.php?p=5270569#post5270569](http://ubuntuforums.org/showthread.php?p=5270569#post5270569).

Bob

---

### Post by Kaniknas on 2008-07-01
I have successfully configured samba so that I can connect to a windows network with about a dozen different members.  I would like to be able to run Labview VIs which are housed on a server on the network, but they aren't given executable privileges which forces me to copy each VI and all its dependencies to my local comp, and then load them again if I change them.  Does anyone know if I can give default privileges to certain members/locations on the network or if a better solution exists?  

-Matt

---

### Post by oygle on 2008-07-09
I can browse with Hardy/Nautilus , but cannot write to the XP computer (see [http://ubuntuforums.org/showpost.php?p=5348784&postcount=50](http://ubuntuforums.org/showpost.php?p=5348784&postcount=50) ) . I used to be able to do this with Gutsy, and there have been no changes to the XP computer. It was only 4 days ago that I installed Hardy.

Does anyone know what could affect the write permissions on the XP computer ? I don't have any Samba shares, as there is no need for the XP computer to access any files on Ubuntu computer.

The event viewer on the XP is showing a successful logon, when nautilus does the browsing.

---

### Post by bomanizer on 2008-07-13
Hello, could someone tell me what I'm doing wrong? I've been banging my head to the wall with this for days and can't find anything wrong with my settings. Here they are:

```
[global]
    ; General server settings
    netbios name = lauta
    server string =
    workgroup = winkkari
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/janne/vmshare
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = janne
   
```

---

### Post by teslarage on 2008-07-14
> **Troberg said:**
> Skrimpy and Linuxnovice, try removing or commenting out the line "force group = something". It helped for me.

Thank you! That worked for me too! It was working fine the last few months, but I wonder why today it simply refused to work.

---

### Post by Finn61 on 2008-07-16
> **teslarage said:**
> Thank you! That worked for me too! It was working fine the last few months, but I wonder why today it simply refused to work.

Yes, I too had to remove the Force Group option (which had been working fine for me for a long time). Glad I found this thread.

I have a feeling there was a Samba update pushed out recently.

---

### Post by blastfm on 2008-07-22
I also am having the "An extended error has occurred" problem.
My setup is the following:
Hardy wired to my router.
XP via WiFi to to the same router.

I originally can access my files from Hardy on my XP laptop without issues after following the instructions from the 1st page. Back then I had my laptop set to join a workgroup.

Then my XP laptop had to be changed. I use this laptop for work and it had to be changed to login to the office domain for a certain project. Since then I cant map to the shared folders on Hardy even after I changed the Workgroup in smb.conf to use the domain name I had on my laptop.

I can see the shared folders if i type Hardy's IP address on the XP Explorer. But when I attempt to map to it, I get the error message. 

Here is my smb.conf:


> 
[global]
    ; General server settings
;	netbios name = my_pc
	server string = 
	workgroup = ap.company.net
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

;	printing = cups
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
	path = /mnt/share1/
;	browseable = yes
	read only = no
;	guest ok = no
	create mask = 0644
;	directory mask = 0755
	force user = user1
	force group = user1

[user1_home]
	path = /home/user1/
;	browseable = yes
;	writeable = No
	create mask = 0644
;	directory mask = 0755
	force user = user1
	force group = user1
	valid users = user1


On my XP laptop
From: Control Panel > System > Computer Name tab
Full computer name: user_name.ap.office1.net
Domain: ap.company.net



PS:
If this has been asked before, I apologize... I hope you can point me to the right direction. If not, thanks anyway

---

### Post by Troberg on 2008-07-22
Try what I suggested a few posts ago:

Remove the line

force group = user1

I don't know why it's not working with that line, but removing it helps for me.

---

### Post by ThunderRd on 2008-07-25
I found this thread after I had already posted in Networking, but I think the question is better off here...

I have a dual boot machine with 8.04.1 and XP.  Each OS is on its own IDE drive, XP on the primary.  This machine runs Linux most of the time, and is a file server.  There are also two SATA drives for storage on the machine.  I installed XP first, followed by Ubuntu, and fdisk reported this:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bd87bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6639b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130f286b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a3e006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    b  W95 FAT32
```

As you can see XP is on sda1, Linux on sdb1, and sdc1/sdd1 are the SATA drives.

So far, no problem, although I did wonder at the time why the OS's werent on hda/hdb.  I thought that would be correct for IDE drives.  Anyway, I wanted to set up SAMBA to share some of the directories on the SATA drives with another[XP]machine.  I had all kinds of problems - the drives would show up, then not show up after a reboot/startup; EXTREMELY SLOW copy speeds both to and from the Linux box, (for example the machine wanted 70 minutes to copy a 23MB file to the XP machine); and various other problems with the setup.  I do have some practice with SAMBA in 7.10 but 8.04 has changed all that.

I researched and read inumerable posts over a three day period and decided to start over and set up SAMBA again.  Basically, I installed SAMBA and SMBFS, set the mount points for the two drives in fstab, and slowly worked through smb.conf.

Every time I marked a share, the drive would not automount.  I couldn't understand this but kept looking for the problem.  After some time I realized that the mount points were shifting[?]/changing[?] on their own-like this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130f286b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a3e006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bd87bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sdc2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6639b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4660    37431418+  83  Linux
/dev/sdd2            4661        4865     1646662+   5  Extended
/dev/sdd5            4661        4865     1646631   82  Linux swap / Solaris
```

As you can see the output of fdisk is completely different here.  This was giving me fits.  I would get the shares set, the XP box would see them, and could copy them (VERY SLOWLY), but the next time I booted the machine the mount points would disappear and so would the shares - along with the drives not mounting.

I'm not sure what I'm doing wrong.  All I want to do is be able to automount the 2 SATA drives and share some of the directories with the XP machine.  I reckon that something I did wrong was also the cause of the slow file operations.  If I can get SAMBA set up properly, I can check that next.


fstab and smb.conf are here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

UUID=e4e7a3e8-1a47-434d-89b9-27791d79be88 /               ext3    relatime,errors=remount-ro 0       1

UUID=6b80dd2e-1943-4a6b-a432-452160ac8c12 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 	0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 	0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 	0       0

/dev/sdc1	/media/FAT32_REPO	vfat	rw,user,auto,exec	0	0

/dev/sdd1	/media/FAT32_ARCH	vfat	rw,user,auto,exec	0	0
```

```
[global]
    ; General server settings
    netbios name = OPTERON-185
    server string = %h server       (Samba, Ubuntu 8.04.1)
    workgroup = RBZGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = lmhosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
;    path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775

#[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

;[MyFiles]
;    path = /media/samba/
;    browseable = yes
;    read only = no
;    guest ok = no
;    create mask = 0644
;    directory mask = 0755
;    force user = YOUR_USERNAME
;    force group = YOUR_USERGROUP


;My stuff would go here, it isn't there now but will be after I sort this out:
;    path = /media/path/to/share
;    browseable = yes
;    read only = no
;    guest ok = yes

```

---

### Post by emagi13 on 2008-07-26
Hi Stormbringer,

     First, let me say thank you for tutorial.  It heled greatly for a complete noob like me.  I've been dealing with MS since DOS 2.x; but I never got into Linux until the latest version of Ubuntu.
     With that having been said, I think I did something wrong.  I followed your directions, except that samba was already installed, and I can now see my Linux shares from the Windows PC's on my home Windows workgroup.  The problem arises in trying to see the shares on the Windows PC's.  Some times I see the Windows computers in the Network tab under Places (GUI browsing as I'm not proficient enough with the commands to do it in Terminal).  At other times, they don't show up at all.  Even when they do show, I can't see the shares in them.  I've even tried CTRL-L and typing in the full path of the share (e.g. smb://Desktop/External)
     I also tried something I saw on another forum and tried changing 'security=user' to 'security=share'.
     Any ideas what to try next?  If I can, I'll attach my .conf file so you can see if the problem is there.

Thanks,

Jamie

---

### Post by Troberg on 2008-07-26
Try removing the line

force group = jamie

Someone who has the power to edit the origanl post to add this? A lot of people are having this problem.

---

### Post by dmizer on 2008-07-29
> **Troberg said:**
> Try removing the line

force group = jamie

Someone who has the power to edit the origanl post to add this? A lot of people are having this problem.

This is still a valid option for most situations.

---

### Post by Troberg on 2008-07-30
Sure, but it's also causing problems in lots of situations, so it should at least be mentioned as a possible fix.

---

### Post by CoFRBrutus on 2008-08-01
> **Troberg said:**
> Sure, but it's also causing problems in lots of situations, so it should at least be mentioned as a possible fix.

I would agree. I've been reading a couple of howtos on samba shares, and both had the force name force group option, and I couldn't get a share to show up on my win box. Decided to check the last posts in this forum and found the answer. Commented force user out and it worked fine.

Great guide though.

---

### Post by hezuo on 2008-08-01
hi, i'm a newbie and i wanted to find out if  there is any simpler way to do this

---

### Post by dmizer on 2008-08-02
> **Troberg said:**
> Try removing the line

force group = jamie

Someone who has the power to edit the origanl post to add this? A lot of people are having this problem.

Those of you experiencing this problem:
- Are you sharing your home directory?
- If you are not sharing your home directory, please post what directory you ARE sharing, and post the permissions assigned to that directory.

---

### Post by Troberg on 2008-08-02
I'm sharing a subdirectory to my home directory, and should have full permissions for both group, root and user there.

---

### Post by dmizer on 2008-08-02
> **Troberg said:**
> I'm sharing a subdirectory to my home directory, and should have full permissions for both group, root and user there.

Do you have the same problem if your share is located in /media/share instead of /home/$user/share?

---

### Post by Troberg on 2008-08-02
I had problems with that earlier, but that was back on Dapper. I'll try later, but I don't have time today.

---

### Post by anachronon on 2008-08-02
Help!  I just can't seem to get this to work.  I am only trying to set up very basic file and printer sharing.

I have tried it with both WINS enabled and disabled.  Always, the result is the same.  I only get as far as Step 2 of the tutorial, "Map Network Drive".  After entering all the info (both the WINS enabled and disabled versions), I keep getting the same error when I hit "Finish":

> The mapped network drive could not be created because the following error has occured: An extended error has occurred.


I am using Ubuntu Hardy on a PC, and I am attempting to set up a network with a Dell laptop using Windows XP.  I am working through a Belkin 54g wired/wireless router.

One off-topic note:  In all the times I've tried to set up a simple, home network, not once has one ever gone smoothly.  It's always been a battle.  I guess networks just hate me.

---

### Post by anachronon on 2008-08-02
One note I forgot to add:  When I click "Finish" in "Map Network Drive", it prompts me for my username and password.  I give it my Linux username and password, the same ones I used in the "gedit" step.  Do I need to be using something else?

---

### Post by anachronon on 2008-08-02
Hold everything, forget my last two posts.  I found I typo in my "smb.conf" file.  My eyesight is getting bad, as I stared at that mistake several times, without seeing it.

Thanks anyway.  Sorry for the false alarm.  Great tutorial!

---

### Post by KIAaze on 2008-08-07
Thanks Stormbringer.
It's the first time I got filesharing working between Ubuntu and Windows. :)

You might want to add in your howto, that it's possible to set a different password for the windows user than the one he uses on windows.
I did so because I'm sharing over wireless and the windows account had no password (now it has but with autologon).

Also, how could I set up a shared folder on Windows accessible from Ubuntu?
That would be more practical in my case.

---

### Post by mahela007 on 2008-08-10
hi... First off, I'm not very comfortable with setting up networks so i need some help.
i folllowed the tutorial on the first page of this thread upto the  point where it read "[B]2. Changing network settings in Windows". however i didnt have to do anything more at this point and the folder can be shared with the windows PC. However the linux box wont show me the windows shares at this point. do i have to complete it to show the windows shares?  

another question. 
I know the folder i created has sharing permission. however in nautilus when i R click the folder and click properties and then go the to the tab labelled "share" the box labelled "share this folder " is not selected. is thie normal?
[/B]

---

### Post by mahela007 on 2008-08-10
oh! can someone tell me how to find the ip address of my Linux box?

---

### Post by Troberg on 2008-08-11
Find IP adress by using the command ifconfig.

As for mounting windows shares on Kubuntu/Ubuntu, that's another problem than the one covered in this thread. However, I've used these guides successfully:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares](http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares)

I suggest at least adding comment about this being another matter a link to a guide for this in the original post, as it's a very common question and a common source of frustration for newbies.

---

### Post by mahela007 on 2008-08-12
hey guys... I have another seemingly stupid question. Why is it important to add users to SAMBA? I havent added any users other than myself but already samba shares which appear on the windows network can be accessed by using the password of the other users of my linux PC. Why should I add separate users to samba?

---

### Post by linuxnovice on 2008-08-16
Hi,

I am not sure if this has been asked before. Recently, I had to give my windows box a password. I also moved to another place so I had to set up the network again. I followed the tutorial (i have done it many times) and got my windows box to see the shared folder on my linux box. However, when I try to go into the windows box in the samba share from kubuntu i get asked for a user name and password. I tried typing my windows user name and passwd but no use. So basically i cant access my windows box from kubuntu. I would like to know how I set up windows (with an account with passwd) for file sharing.

Thanks.

---

### Post by dmizer on 2008-08-17
> **linuxnovice said:**
> Hi,

I am not sure if this has been asked before. Recently, I had to give my windows box a password. I also moved to another place so I had to set up the network again. I followed the tutorial (i have done it many times) and got my windows box to see the shared folder on my linux box. However, when I try to go into the windows box in the samba share from kubuntu i get asked for a user name and password. I tried typing my windows user name and passwd but no use. So basically i cant access my windows box from kubuntu. I would like to know how I set up windows (with an account with passwd) for file sharing.

Thanks.

Please see the second link in my sig regarding cifs shares.

---

### Post by RealG187 on 2008-08-18
> mpg@MIKED5:~$ sudo smbpasswd
[sudo] password for mpg: 
New SMB password:
Retype new SMB password:
Failed to find entry for user root.
Failed to modify password entry for user root


I can connect to it from windows but I do not know the password and it won't let me change it!

---

### Post by blastfm on 2008-08-21
> **Troberg said:**
> Try what I suggested a few posts ago:

Remove the line

force group = user1

I don't know why it's not working with that line, but removing it helps for me.

Sorry for the very late reply. Was away from my Hardy for a long time. Anyway I tried the above suggestion and it solved my problem on the XP on VMWare Server. I have yet to check this on my XP laptop that has Domain settings. 

Anyway, this helped a lot :guitar:

---

### Post by RealG187 on 2008-08-27
Okay I followed the directions [here]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/") (for VM Ware) and I think I F'ed up my samba. I deleted sandbox as I cannot access it and made a new share the normal way (right click -- sharing) but when I access my machine it shows sansbox and not my new share, it shows what it shouldn't amd won't show what it should!

I typed

```
sudo /etc/init.d/samba restart
```
and it still wont do it

---

### Post by hmarkg on 2008-09-10
Sorry but i do not know has someone already asked this question in the previous reply. I am having problem linking my ubuntu box to the other two MS Windows XP computer. I have already setup the samba on my ubuntu box the same way as the first post and did not encounter any problem. I also have a static IP address on my ubuntu box. The problem is when i am trying to link from the Windows XP to the ubuntu box by mapping the Network drive, i cant seem to be able to connect to the ubuntu box. It says that there is a extended error on Windows XP... How come like this...??

---

### Post by atok on 2008-09-11
why is this happening? i've followed the howto to the letter.

```
atok@atok-ibook:~$ smbclient -L kazekage -U%
Connection to kazekage failed (Error NT_STATUS_BAD_NETWORK_NAME)
```

---

### Post by Connekt on 2008-09-16
I seem to have run into some problems during the setup.  I just installed Linux Ubuntu Hardy sunday and have been setting it up ever since (its been a fun ride).

When I go to finish mapping the net work drive, it pops up with connect to CONNEKTO (my xp box) with a login setup.  I didn't put a password for this box and when i try to hit OK or type in my linux box password it just resets the field.

This is my setup so far:

Linux Host: connekt
Password: ******
Windows Xp (Virtual Box'd): CONNEKTO
No Password
MyFiles: /dev/sdb1 (physical ntfs drive)
Wins: no
Workgroup: HOME1

Question: Should my linux box ip be the local ip (in this case, 127.0.1.1)?

\\127.0.1.1\MyFiles  (in Mapping)

As a side note the drive i'm attempting to share is NTFS and is "Unclean". Seeing as I do not have XP dual-booted (I just have it running as a guest through Virtualbox) I am attempting to share this in order to not only access the drive but hopefully defrag it in XP to be able to mount it in Linux. (If that makes sense)

I've also tried with Wins = Yes (I'm not really sure if I have Dynamic or Static), and with that setup it wouldn't connect to \\connekt\MyFiles, although with both setups I am able to see connekt on the workgroup.

I'll continue to toy around with it, but I hope someone can give me some insight as to the problem.

---

### Post by Batman123 on 2008-09-17
Hello,

First of all, great howto by Stormbringer. But I'm still experiencing some problems with samba. Hope you guys can help me with this.

I'm running with Ubuntu 8.04 and my brother is running with Win Xp Pro sp2.
The goal is to have both computers share files with each other automatically after bootup

Problems...

1. In Places/network I'm unable to see my bros pc (only my own in there). I am able to connect to it via location bar (smb://ip-address) and then see its shares, but can't see it in windows network/home. So what's up with that? How can I get it see my bros pc and share its resources?

2. When I boot up my Ubuntu, the connection between the computers seems to be gone. I have to restart samba to get it back online again. I think it's because of DHCP. My ip has been same for ages, but I think DHCP reloads it during bootup, so it messes up the connection. And yes I'm using WINS.

3. With every boot up, my hosts(/etc) seems to add .home right after my hostname. I'm not sure but I think it messes up something.

I think those are the main problems. The connection is working, not exactly the way I want it to work.

I hope somebody understands what I'm saying.
And of course...thank you in advance for even bothering trying.
I appreciate it !

-Dark Knight

---

### Post by gregphil on 2008-09-28
(To: Stormbringer)

Good attempt to explain a standard peer-to-peer setup but there are a few things you didn't mention:

1.  Enabling a WINS server is not actually "peer-to-peer" as only one (1) machine on the sub-net can be a WINS server.  If you have two or more linux machines on the sub-net and you enable WINS server on more than one, then the browsing will misbehave in strange ways.  Futher the machine configured as a WINS server must be powered up for the other machines to browse.  Also the need to a fixed IP for the WINS server is not compatable with today's typical DHCP configured machines.

A linux Wins server is NOT actually needed if you have some other form of name resolution (such as a DHCP server that does name resolution (i.e. almost any modern router)) present on the sub-net.

2. Ubuntu 8.04.1 is currently broken as far a browsing **authenticated** Windows shares is concerned.  The GUI apps like "Nautilus network file browser" depend on a gnome library (gvfs) for authentication and it is broken:  (these bugs apply to more than ADS networks, any authenticated Windows share seems to be effected)
[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072") 
[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26") 
This means Nautilus will show the Windows machines on the sub-net, but when you click on them no shares are listed.  All is not lost, if you are willing to host anonymous (guest allowed) shares from the Windows boxes, then Nautilus browsing can work.  But this is a terrible security leak.  Also, although Nautilus can't browse, it can connect to a share if you enter the entire path name of the share you want to connect to (type it into the text target box).  Of course this means you need to know the Windows share names ahead of time.

kubuntu 8.04.1 does not use the gnome library and can GUI browse Windows shares.

3. Some useful linux command line tools exist to check aspects of the Samba sharing configuration:  "smbtree" and "smbclient -L COMPUTERNAME".  These don't use the gvfs library and work correctly.  They can show all the shares samba "sees" and any error messages can give you a hint what might be wrong (invalid password etc)

4. Some programmmer working on ubuntu decided to use more than one address for localhost, so if you use a global "hosts deny" and then specify "hosts allow" in smb.conf you will need to make sure that 127.0.1.1 is allowed as well as the normal 127.0.0.1 loopback.

*****************
Thank You for trying to explain samba.  It really needs to get "fixed" so new users can easily network with their "old" windows machines and move their data to the linux machines.  It currently is almost impossible to get GUI browsing working in a normal home authenticated peer-to-peer configuration.  (I just use KDE to copy shared files)

---

### Post by theDaveTheRave on 2008-09-29
Thanks for a brilliant howto.

Everything seems to be set up and working with one very annoying problem, well in fact 2 annoying problems!

first:

I can see the share on the XP machine, but when I "browse" through it I get a permanent "loading" icon (the little spinning circe). Initially I can see the names of all the files, but after a while, when I've hoped to another virtual desktop and later returned, all the files are gone and the icon is still happily spinning around re-loading? I'm sure I have done something wrong but I'm not sure what it is.

Second:

I simply can't see my ubuntu samba share, I saved this as /home/samba, but however I try to navigate to the system I can't see any folders or shares?

Again I'm sure I'm doing something wrong but I'm not sure what it is?

Help would be greately appreciated.

The reason I am doing this is the following, I'm writing a new database for my new job, and I want to have the database update between my laptop and the SQL server on my XP machine, in essence have my laptop acting as a slave server to the XP.

Ultimately the SQL server will move to a raid device (currently running windows, but hopefully moving over to either ubuntu or deb), with 2 slave server, one being a networked local XP terminal (as it is going spare) and the other being an external USB HDD (again this will end up being slaved to my laptop and hence enable me to "play" with the rest of the system I am developing, without endangering the core data in the MySQL data source.

I want to get this working really soon, primarily as proof that the whole thing will work, then the boss will be happy to put Ubuntu or Deb onto the Raid server he recently acquired!

thanks for the help in advance.

Dave

----- EDIT-----
Oh dear, the wait is so bad the only way I can do anything afterwards is to kill the nautilus that is viewing the share!
Please help!

---

### Post by umang26 on 2008-09-30
Thanks a TON!! much appreciated!

---

### Post by NeillHog on 2008-10-04
Firstly - a huge thank you.
I changed to Linux a year ago and have never regretted it.
But the problem of sharing files with other XP PCs in the house had driven me to distraction.
With this tutorial I was up and running in an hour.

I have set up /home/neill/SharedFolder/ as my shared folder.
I first logged in to it from my son's XP PC with my user name and password.
That worked.
Then I set up my son as a Samba user with the same user name and password as he uses to log in to XP. It works great!

But....
He can delete the files even though the directory /home/neill/SharedFolder/ has the rights 744 (owner can view and modify, group can view and others can view).

Is this normal? Where can I change something so that he can see but not change any files.

Thank you!
Neill

---

### Post by snipe6006 on 2008-10-05
Hello, I followed your tutorial all the way until when I tried to access from my Windows XP computer. It gives an error that my share is not accessible because "The user name could not be found."
What is wrong? 
Help is appreciated

---

### Post by jlabomb on 2008-10-25
I was able to get it to work with this. It was a matter of setting the user name and password inside samba afterwards. Thanks.

---

### Post by kiatng on 2008-11-02
Thanks for the great tutorial. I was trying to share files between Ubuntu (now ver 8.10) with Win XP SP2. After following the tutorial, I could see the shared folders from Ubuntu but on the Win XP side, I encountered one or two errors. One error was  "The group name could not be found.", the other was endless prompt of user name and password. 

I had this resolved by chance after a couple of weeks. If you face similar problem, try and check this on the Ubuntu that the checkbox is enabled for the option "Share files with the local network" in System>Administration>Users and Groups>choose user>Unlock>Properties>User Privileges.

---

### Post by doccpu on 2008-11-10
1. In your example smb.conf you give no line like 
/home/samba
so where and why would you use this path?
2. I had a lot of trouble and 3 days of netting and pulling out hair to get a ntfs disk mounted as rw and then seen as a share.
Are there ANY good definitive texts or books on ubuntu linux and Samba?
I have had a problem for years trying to get linux to do what i want locally and as shared drives. too many exceptions to the rules on permissions and what it SHOULD do. 
one good example samba says rw any user but linux says ro but only on an authenticated user. How can you really know who can do what?
Too many of the texts assume you have a folder doing what you want then you find out it won't either locally or other wise and the non admin style of logins in ubuntu make it a night mare. It keeps saying only root can do that.:confused: Well root isnt allowed.:mad:

---

### Post by befana on 2008-11-15
Stormbringer,
can I translate this howto in my language and give it to my friends?

---

### Post by happyhacker on 2008-11-16
This thread seems to have run it's course. People are having problems here and getting no answers!. I'm investigating using Ubuntu in my network but this frightens me somewhat as one post seems to imply Ubuntu still has bugs.

---

### Post by Erlander on 2008-11-16
The reason for the lack of replies is that the OP has not visited the forums since February 12th 2007.

I find that Ubuntu is very stable.  Having once got my samba shares working I saved my config files elsewhere and every time I upgrade or change my system I just copy them to the /etc/samba directory.

Rob

---

### Post by mostlyalive on 2008-11-19
> **cantthinkofanickname said:**
> This thread seems to have run it's course. People are having problems here and getting no answers!. I'm investigating using Ubuntu in my network but this frightens me somewhat as one post seems to imply Ubuntu still has bugs.

Of course Ubunutu has bugs. All operating systems have bugs in them from Windows to Ubuntu to AIX. That said, Ubuntu is pretty stable and with a bit of tweaking, samba works pretty well.

---

### Post by dmizer on 2008-11-19
> **cantthinkofanickname said:**
> This thread seems to have run it's course.

This thread is still very active and helpful. The configuration given in the howto is still valid for most situations.

---

### Post by myharshdesigner on 2008-11-24
Nice Post. it's very usefull

---

### Post by two4two on 2008-11-26
Actually, when I used the GUI it was very easy except I still couldn't see my Linux box from my WinXP box.  So I entered the **[COLOR="Blue"]sudo /etc/init.d/samba start [/COLOR]** command and voila: visible from WinXP (although I didn't try to browse or update any files yet).  Also I didn't see what happens if I reboot if the SAMBA START is automatically performed during boot.  Also in the Ubuntu community documentation Setting Up SAMBA they have a reference to:

[B][COLOR="Blue"]Configuring your computer
Start the network configurator using the following menu: 


(see attached image)


System -> Administration -> Network 

 

You will need the General tab, in the middle. [/COLOR][/B]




I am running 8.10 with current updates and I don't have such a panel.  Where do I get one?  That would be a really nice addition to my Ubuntu.

---

### Post by happyhacker on 2008-11-27
I have now installed samba and webmin and after a days fiddling and learning have got a couple of shares working from windows. Looking forward to getting inot this a bit deeper. My only problem is that when I get the server shares running for everyone in the office someone has to turn the machine on in the mornings as the bios does not have any boot options from power on.

---

### Post by chiques on 2008-11-27
I went through the whole configuration. How do I actually access the Windows XP machine on my network. I see it in my Network window but when I double click into it it's a blank screen. I know its accessible because I was able to access from my Mandriva machine.

---

### Post by merlin351 on 2008-11-28
Stormbringer - It has probably been some time since the last post.  I have migrated from SuSE SLES10 to UserOS 8.o4 (PC User Version in Australia).  It's a very lite version of Heron I think.  Thanks for the post.  I had an awful time getting my Home/Local/Share up and running and I'm not quite sure how I did it.  After I followed your Tute I could not get my windoze boxes to R/W to the share.  All the users on my system could see and R/W to their own private folder.  I changed the ownership using chown as you indicated and this did not work.  Somehow under the GUI I managed to change the permissions and it works just great. I think it was the the change to the same name of the group from user to the name I put into smb.conf.  This may seem like its going nowhere but I really wanted to thank you for the great howto.  I will look forward to testing out the PDC version.:popcorn:

---

### Post by ipburbank on 2008-12-01
I don't even have a network panel under the admin panel

---

### Post by Roasted on 2008-12-02
At home, I have my 8.10 64 bit Desktop along with 4 XP machines and my laptop, which dual boots Vista and Ubuntu 8.10.

Question is, in Ubuntu 8.10 on my laptop, how would I go about connecting to my Samba share? Is it possible? I know that Samba is often referred to as the Windows share client of Linux, but nonetheless I was under the impression Samba supported the big "3" platforms (OS X, Windows, Linux).

In short - I want to know how to connect Linux-to-Linux in Samba with an existing share set up. Where do I go? What do I do?

---

### Post by bachurch on 2008-12-05
Hi,
I almost have this working.
From my windows xp machine I can see \server\myfiles. Does myfiles point to my share? I have a drive mounted at /media/usershare and my files point to /media/usershare. It seems I am almost there. Any thoughts?

Thanks.

---

### Post by gregphil on 2008-12-06
That is a known bug in Ubuntu above version 7 (Heron and later...), actually in a gnome library used by the Heron gnome GUI apps.  Kubuntu does not use gnome so it does not have this problem.

see: [Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072")

The bug actually applies to ALL **authenticated** Windows shares, not just ADS networks.  Unauthenticed shares (guest or anomymous access allowed) are not effected (they work).

Hopefully the bug will get fixed someday.

---

### Post by Roasted on 2008-12-08
What kind of transfer speeds are you guys seeing with Samba?

---

### Post by other guy on 2008-12-08
Depending on the machine I am connected to. I see no difference between my Linux boxes and Windows boxes. Usually around 90% utilization.

Which on a 10/100 card. 90Mbs / 8 = 11.2MB/s. Sometimes it goes lower. Sometimes it jumps up a little. 

I expect to see the network at around 90% on average. I have one tired old box that only gives me 60%. Which the math of divide, bit by 8 to get Bytes.. Is about 7.5MBs or 60Mbs. Notice the small b and larger B.

---

### Post by Roasted on 2008-12-08
I was pulling only 2 MB/second earlier, wirelessly from my XP laptop.

Later, it jumped to 4 MB/second.

Using a spare computer behind me, 10/100 PCI LAN card installed, I pull an average of 6.9/7.5 MB/second.

Earlier, I pulled high 10's MB/second transfer rate.

I just had no idea if this was considered "good" or bad or what... But if you're getting 11 and fluxuating a bit, and I'm getting an average of 7ish on my wired network and fluxuating a bit, I guess I'm pretty normal? Whatcha think?

Could I expect these numbers to "drastically" increase if I had a router with 10/100/1000 ports? 

Also - Any NFS users here? I keep hearing people say NFS is faster, but what little documentation I can find on NFS shows that the speed difference from Samba is really... well... the same... but that's just based on what little info I've found. I can't find any decently concreted numbers.

---

### Post by other guy on 2008-12-08
Average wireless is only 54mbs. Which is in OS terms. 6.7MBs. That is at 100% utilize. Which is not going to happen all the time. You have to factor overhead in.

Just multiply your MB speed by 8 to get the megabit speed. Reverse to find out the other way. Which is divide.

Signal strength on wireless can effect speeds greatly at times. If it is consistent on being really low. then you can assume you need to find a correction. If it jumps.. There could be interference. Depending on how sustained it is. Is how you deal with it.

Overhead on a wired connection can also effect speeds.

A full gigabit network. Full speed is 125MBs. The most your going to get on a tbase 100 is 12.5MBs

Unless you are using a quality duplexed eth card. Expect around 65-80% of the network speed potential. Also cable quality is also factored in. Not in like brand quality. Wear and tear on the cables.

---

### Post by Roasted on 2008-12-08
So with the speeds I'm getting on a WRT54G network with all 10/100 connections, that's considered "good".. isn't it?

---

### Post by anachronon on 2008-12-08
I have a question.  I have had print sharing set up from a WinXP laptop, to Ubuntu, through Samba, for some time (I used the "How-to" at the start of this thread).  However, the other day, I went to print something from the laptop, and it could not talk to my Linux box, where the printer is connected.

I am working through a Belkin router.  Both computers are able to connect to the internet through the router.  So, that does not seem to be the issue.  It appears to be purely a software problem.  Perhaps, some setting got changed.

So, is there an easy way to troubleshoot this?  I would hate to have to uninstall everything, and start from scratch.  I know a little about networking, but not much.  This is one of the rare times that I have owned more than one computer.

---

### Post by doogiekd on 2008-12-10
hi.

i'm trying to connect my intrepid box to a windows xp box. (the windows xp box is connected to a 1tb external hard drive hosting music files.)

the problem: the ubuntu box is in my office and connects to the internet via a sling box to the lynksys wireless router. the wireless router is directly connected to the xp box. 

the xp box cannot find the ubuntu box via the router via the slingbox. "network path not found" is the error message. 

any suggestions?

thanks, 
kenneth

---

### Post by Roasted on 2008-12-10
doogie - post your smb.conf

In Terminal...

```
sudo gedit /etc/samba/smb.conf
```

Select All.
Copy.
Paste here.

---

### Post by doogiekd on 2008-12-11
Hello Friends, 

The original post:

i'm trying to connect my intrepid box to a windows xp box. (the windows xp box is connected to a 1tb external hard drive hosting music files.)

the problem: the ubuntu box is in my office and connects to the internet via a sling box to the lynksys wireless router. the wireless router is directly connected to the xp box.

the xp box cannot find the ubuntu box via the router via the slingbox. "network path not found" is the error message.

any suggestions?

thanks,
kenneth


The request for my samba config file:


[global]
    ; General server settings
    netbios name = sun
    server string = Samba Server %v
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/administrator/sambadata
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force user = potatoes
    force group = potatoes


The error message in XP when attempting to map network drive:

\\192.168.1.101\home\administrator\sambadata could not be found

---

### Post by Roasted on 2008-12-11
Take a closer look at this.

```
[MyFiles]
path = /home/administrator/sambadata
```

and this

```
The error message in XP when attempting to map network drive:

\\192.168.1.101\home administrator\sambadata could not be found 
```

See the problem? You have "home administrator" in your UNC path when it SHOULD be \home\administrator\sambadata.

Try that and get back to us. :)

---

### Post by doogiekd on 2008-12-11
The error message from XP (entry error in the original post-corrected) is:

\\192.168.1.101\home\administrator\sambadata could not be found


Hello Friends,

The original post:

i'm trying to connect my intrepid box to a windows xp box. (the windows xp box is connected to a 1tb external hard drive hosting music files.)

the problem: the ubuntu box is in my office and connects to the internet via a sling box to the lynksys wireless router. the wireless router is directly connected to the xp box.

the xp box cannot find the ubuntu box via the router via the slingbox. "network path not found" is the error message.

any suggestions?

thanks,
kenneth


The request for my samba config file:


[global]
; General server settings
netbios name = sun
server string = Samba Server %v
workgroup = MSHOME
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = no

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[MyFiles]
path = /home/administrator/sambadata
browseable = yes
read only = no
guest ok = no
create mask = 0777
directory mask = 0777
force user = potatoes
force group = potatoes


The error message in XP when attempting to map network drive:

\\192.168.1.101\home\administrator\sambadata could not be found

---

### Post by sharanyan on 2008-12-11
thanks a lots, very usefull all of us..

---

### Post by Roasted on 2008-12-11
Don't you have to run the network setup wizard in XP before you can transfer stuff via UNC path at start - run like \\192.168.1.101\sambaserver... etc????

Pretty sure I had to... Did you run that wizard?

---

### Post by doogiekd on 2008-12-11
The directions for this tutorial just says to map the a network drive. I already have a network set up with other boxes. Are there additional instructions for setting up Samba on XP Home Edition?

---

### Post by dystorteddream on 2008-12-11
Okay, so I've skimmed over this, plus spent allll day long looking on the interwebz about this issue. I'm finding so much conflicting information, or even moreso... a lack of solid information. So here's my scenario. 

I've got two machines. One running 32 bit Windows Vista SP1 and another running Ubuntu 8.04 (which i've also installed KDE-Desktop on).

Both computers are a part of "WORKGROUP" workgroup, so i know that differing workgroups isn't the problem. My Vista machine is connected to my netgear router by ethernet, while the ubuntu is connected via wifi to it. Internet is working fine on both machines.

I am unable to see my linux box on vista no matter what. On my linux box, I can see "GATEWAYPC" when browsing through my smb/workgroup... however, like i see in many people's cases... unable to browse the files. I have changed the settings on my vista machine so that the shared files are open to anybody on my network (anonymous, etc) and yet still unable to do anything. Since my vista machine has a 500 GB HDD on it, my music and videos are on here and would like my vista machine to work as a server, and allow my ubuntu machine to be able to browse the files in the other room and utilize them. 

I've got SWAT working with samba to the point where i can edit things here and there, but it's still becoming a pain because I'm not seeing any solid information for me to change. I've changed a few registries in my vista box from sources online as a work around, but still no changes. 

If anybody needs any more info, please let me know... but i'm getting pretty frustrated. As much as i'd love to just dual boot my vista machine, it'd be way too time consuming and my lady is computer illiterate anyways... and trying to get her to use something other than windows would be like pulling teeth from a croc. Thanks in advanced everyone!


D~D

edit: I am now able to access my linux box by going to >> Start >> 192.168.1.3/dystorteddream/  and that does pull up my linux box... even though it is showing as read only, and does not allow me to view all of the folders. smb.conf is showing that read only is off. So I really don't know what's going on. Ubuntu is still having problems browsing the files shared on the vista system.

---

### Post by vocalfons on 2008-12-13
mmmm, I've tried the guide, and did it step by step. What goes wrong here?


alfons@LINALF:~$ sudo smbpasswd -L -a vocalfons
New SMB password:
Retype new SMB password:
Failed to modify password entry for user vocalfons

---

### Post by Roasted on 2008-12-13
Do you have a local user account on your Ubuntu machine named that?

Any Samba user you create within Samba must already exist within Ubuntu.

---

### Post by milkyspit on 2008-12-19
I could use some assistance! Have a network of a half-dozen machines with half being Windows XP and the other half being Ubuntu 8.04 LTS. All the machines are seeing one another's names via WINS... EXCEPT for the latest. Let's consider two machines, GOODBOX and BADBOX, to keep things relatively simple. Here is what I know...

1. BADBOX can ping GOODBOX and get the correct IP address. (Both boxes assigned IP addresses via DHCP.)

2. BADBOX can see GOODBOX vis nmblookup

3. BADBOX can open vnc and ssh sessions to GOODBOX

4. BADBOX can ping itself

5. GOODBOX can ping BADBOX when using IP address, but cannot ping BADBOX by name... GOODBOX tries to resolve the BADBOX name via OpenDNS! GOODBOX can ping other boxes on the network properly by name, so seems as if this is not just a simple name resolution issue on GOODBOX.

6. GOODBOX cannot see BADBOX via nmblookup, nor can it vnc or ssh into BADBOX

7. Samba is running on both boxes. I can see the nmbd process running on both boxes, too.

8. Neither box is running an active firewall, so it would seem that's not the problem.

I've spent a full day trying to fix this and made no headway. Have compared configuration files on the two boxes, including nsswitch.conf, smb.conf, resolv.conf, interfaces, and possibly some I've forgotten; but no differences noted and no clues as to why things aren't working.

I need some help... please! :(

---

### Post by mahasmb on 2008-12-22
I'm on Intrepid Ibex and I'm trying to print to a Windows XP computer wirelessly. The XP computer is connected a Brother DCP 7020.

I've got SAMBA set up, I can see the printer on my Intrepid machine, and I can install the drivers. Unfortunately, after setting everything up I get this error whenever I try to print:

```
Processing - Connection failed : NT_STATUS_ACCESS_DENIED
Processing - Unable to connect to CIFS host, will retry in 60 seconds...
```

Is this a samba problem? I can't find a fix for it.

---

### Post by Volund on 2008-12-22
Dude, stormbringer, you rock, The setup on Samba was really easy following this guide, and mow all my pr0n is on my windows box instead of my lappy :D thanks much.

---

### Post by Erlander on 2008-12-22
> **mahasmb said:**
> I'm on Intrepid Ibex and I'm trying to print to a Windows XP computer wirelessly. The XP computer is connected a Brother DCP 7020.

I've got SAMBA set up, I can see the printer on my Intrepid machine, and I can install the drivers. Unfortunately, after setting everything up I get this error whenever I try to print:

```
Processing - Connection failed : NT_STATUS_ACCESS_DENIED
Processing - Unable to connect to CIFS host, will retry in 60 seconds...
```

Is this a samba problem? I can't find a fix for it.

Have you set up windows printer sharing?

Rob

---

### Post by mahasmb on 2008-12-23
Absolutely. I can connect to the printer and set it up. It just won't print.

---

### Post by dreamfoundry on 2008-12-24
I'mnot sure if this has been discussed previously in this very long forum.

I have followed all these steps (pretty much to the word) and now I am able to see my Ubuntu box (ubuntu server 8.04) from my Windows XP box.

As soon as I access the shared machine through windows I am asked for my username and password. I then enter my username and samba password, after which I am shown a list of all the shared folders. 

Now comes the problem. As soon as I attempt to access one of these shared folders I am again asked for a username and password. No matter which username and password I enter, I cannot get past this step. 

What could I be doing wrong?

---

### Post by masterkiller on 2008-12-26
wow nice "how to" as it was so easy to follow  nice work
thank you

---

### Post by amp88 on 2009-01-01
> **Stormbringer said:**
> **HOWTO: Setup Samba peer-to-peer with Windows**

Thanks for the excellent guide!

---

### Post by anachronon on 2009-01-01
PLEASE HELP!

I have been using Samba for nearly a year.  It enables me to connect my Windows laptop to my old parallel printer, through my Linux desktop.  Never had any problems.

But then, about a month ago, the connection just stopped working.  I have gone back over all of the set-up steps, numerous times, and nothing has been changed.  Yet, I cannot get the connection to work again.  I am using a router, and I have double-checked the IP addresses.

About the only thing I find odd are the permissions of the Samba folder that I created.  I have used "sudo chmod 777" to open the permissions.  But, when I check that folder with the file browser, the browser claims that the Samba folder is root restricted (I'm guessing, mod "000").

Please help me with this.  This is the second time I have asked!  I am unable to use my printer with my laptop (very important).

---

### Post by Erlander on 2009-01-01
> I am unable to use my printer with my laptop (very important). 
Have you enabled printer sharing in your printer setup?

---

### Post by anachronon on 2009-01-01
Quick update.  There was one thing that I never thought to check.  When I first lost the connection, I pinged the Linux desktop from the Windows laptop.  It was successful, so I thought that the connection was fine.

However, I just tried going the other way, and found that I could NOT ping the Windows laptop from the Linux desktop!  I have double-checked everything.  It works one way, but not the other.  How is that possible?  What do I need to do?

---

### Post by anachronon on 2009-01-01
> **Erlander said:**
> Have you enabled printer sharing in your printer setup?
Yes, all print sharing is enabled.  No settings have changed.  The connection just stopped working, after being functional for nearly a year.

---

### Post by anachronon on 2009-01-02
To add some light to my previous two posts, here is another thread that I found.  Though my research STILL cannot find any answer to my problem, I have found that it is suddenly very common.  It all seems to have started back in September:

[http://ubuntuforums.org/showthread.php?t=923922](http://ubuntuforums.org/showthread.php?t=923922)

I urge everyone with knowledge of networking to read this thread.  Something has changed, and no one with the necessary expertise seems to be helping.  Was there a bad update, somewhere?  Why the lack of response?

---

### Post by theDaveTheRave on 2009-01-09
Stormbringer,

Just a note to see if you have any idea about a problem I am getting, I'm going to post a new thread also on the same thing, but I think you may have an idea as I get the feeling that it is samba related.

so....

The situation.

I'm happily sitting in front of my pc and working on some programming stuff, when suddenly I get a major slow down of the pc (it won't even respond to keystroke inputs for about 15 mins).

Eventually I pull the power - it seems to be the only solution! (bear with me here people I'm about to get to the point.... ;) ).

So after I've rebooted I look into my various system logs and I find these messages

> Jan  9 11:57:58 Anticlimax smbd[7533]:   create_builtin_users: Failed to create Users

Then a little later I see these in the log files

> Jan  9 12:44:29 Anticlimax nmbd[5571]:   ***** 
Jan  9 12:44:29 Anticlimax nmbd[5571]:    
Jan  9 12:44:29 Anticlimax nmbd[5571]:   Samba name server ANTICLIMAX is now a local master browser for workgroup IRREDUTIBLES on subnet 134.157.195.129 
Jan  9 12:44:29 Anticlimax nmbd[5571]:    
Jan  9 12:44:29 Anticlimax nmbd[5571]:   ***** 
Jan  9 12:44:29 Anticlimax nmbd[5571]: [2009/01/09 12:44:29, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan  9 12:44:29 Anticlimax nmbd[5571]:   find_domain_master_name_query_fail: 
Jan  9 12:44:29 Anticlimax nmbd[5571]:   Unable to find the Domain Master Browser name IRREDUTIBLES<1b> for the workgroup IRREDUTIBLES. 
Jan  9 12:44:29 Anticlimax nmbd[5571]:   Unable to sync browse lists in this workgroup

so now I'm curious and try to see when all this started, I've noticed that the inability to find the workgroup is persistent, and don't know how to solve this, our local domain name is irredutibles (or at least that is what the boss has called it) is there anything I can do to confirm it's presence and that he isn't just "giving it a name" that doesn't really exist except for in the teams computers?

Also on further investigation I find this

> Jan  9 10:22:12 Anticlimax nmbd[5609]: [2009/01/09 10:22:12, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Jan  9 10:22:12 Anticlimax nmbd[5609]:   process_local_master_announce: [COLOR="Red"]Server ASTERIX[/COLOR] at IP 134.157.195.68 is announcing itself as a local master browser for workgroup IRREDUTIBLES and we think we are master. Forcing election. 
Jan  9 10:22:12 Anticlimax nmbd[5609]: [2009/01/09 10:22:12, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Jan  9 10:22:12 Anticlimax nmbd[5609]:   ***** 
Jan  9 10:22:12 Anticlimax nmbd[5609]:    
Jan  9 10:22:12 Anticlimax nmbd[5609]:   Samba name server ANTICLIMAX has stopped being a local master browser for workgroup IRREDUTIBLES on subnet 134.157.195.1 
Jan  9 10:22:12 Anticlimax nmbd[5609]:    
Jan  9 10:22:12 Anticlimax nmbd[5609]:   ***** 
Jan  9 10:22:25 Anticlimax nmbd[5609]: [2009/01/09 10:22:25, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Jan  9 10:22:25 Anticlimax nmbd[5609]:   ***** 
Jan  9 10:22:25 Anticlimax nmbd[5609]:    
Jan  9 10:22:25 Anticlimax nmbd[5609]:   Samba name server ANTICLIMAX is now a local master browser for workgroup IRREDUTIBLES on subnet 134.157.195.1 
Jan  9 10:22:25 Anticlimax nmbd[5609]:    
Jan  9 10:22:25 Anticlimax nmbd[5609]:   ***** 
Jan  9 10:22:25 Anticlimax nmbd[5609]: [2009/01/09 10:22:25, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan  9 10:22:25 Anticlimax nmbd[5609]:   find_domain_master_name_query_fail: 
Jan  9 10:22:25 Anticlimax nmbd[5609]:   Unable to find the Domain Master Browser name IRREDUTIBLES<1b> for the workgroup IRREDUTIBLES. .

which ties in perfectly with the time my system slow down started, for information ASTERIX is another pc with shared drives (it happens to be an XP machine

I found some information on this [here]("http://lists.samba.org/archive/samba-technical/2000-June/008259.html") but I don't know what I need to change to set my pc as a "client" to stop it talking to the other system.

Your help is much appreciated.

David

---

### Post by topaz1968 on 2009-01-26
Fixed the problem after reading the entire thread that I didn't see at first due to having gotten a cached copy from my search.

---

### Post by topaz1968 on 2009-01-26
Fixed the problem after reading the entire thread that I didn't see at first due to having gotten a cached copy from my search.

---

### Post by topaz1968 on 2009-01-26
Fixed the problem after reading the entire thread that I didn't see at first due to having gotten a cached copy from my search.

---

### Post by dmizer on 2009-01-27
> **theDaveTheRave said:**
> I found some information on this [here]("http://lists.samba.org/archive/samba-technical/2000-June/008259.html") but I don't know what I need to change to set my pc as a "client" to stop it talking to the other system.

Your help is much appreciated.

David

I wasn't too sure how to interpret that post either, but after reading the "domain master" section of man smb.conf (several times) it became clear.

> Note that Windows NT Primary Domain Controllers expect to be able to claim this workgroup specific special NetBIOS name that identifies them as domain master browsers for that workgroup by default (i.e. there is no way to prevent a Windows NT PDC from attempting to do this). This means that if this parameter is set and nmbd claims the special name for a workgroup before a Windows NT PDC is able to do so then cross subnet browsing will behave strangely and may fail.

Add:
```
domain master = no
```
to the [global] section of your smb.conf

---

### Post by theDaveTheRave on 2009-02-03
dmizer

Thanks for the help, I will test the change next time I get an issue. Currently there are no slow downs or other problems, and I guess that it would work best to test when I have the problem, turn off the <domain master> as you suggest and then see if it has changed anything?

Oddly enough there were other "issues" where I worked at the same time. All the pc's are on static IP. And there was a conflict on one of the addresses... co-incided quite nicely with when there was a problem.

David.

ps. If you are wondering why I keep going quiet, it is because I am doing bioinformatic research for a group. Every 2 weeks I head off to the university of Rouen for the "accademic" part of a Masters course.

David

---

### Post by stevoo on 2009-02-04
You are my new best friend ... i spend two days trying to configure it ... but i was always missing something :D 

You gave me everything ...


Great guide

---

### Post by januszky on 2009-02-08
Greetings!

Another newbie here.  This on-going discussion is certainly a testimonial to Stormbringer's tutorial and willingness to help the newcomers.  I have used the example as the basis for my samba configuration.  I have a problem but more on that later after some background . . .

**BACKGROUND INFO**
MY Home Office LAN: 2-Windows XP Pro, 1- Windows 2k Pro, 1- Windows 98SE (rarely used by granddaugher for games).  My oldest daughter access the internet via router (wireless_ on her Visa laptop.  

**LAN CONFIGURATION**
Router for DHCP, DNS and Gateway via DSL. No connection sharing via one machine. Basically, each machine accesses the internet independently.  LAN configuration for each machine: Client for Microsoft Networks, File and Printer Sharing for Microsoft Networks, and Internet Protocal (TCP/TP).  Advanced TCP/TP Settings: DHCP Enabled; No DNS addresses; no WINS; Disable NetBIOS over TCP/IP.  All services (Client for Microsoft Networks, File and Printer Sharing for Microsoft Networks) are bound to NetBEUI Protocal instead ot TCP/IP for security -- per Steve Gibson's Shields Up site. 

**CURRENT SITUATION**
I recently installed Linux (non-Ubuntu distribution) on a spare machine and thought it would be something I could use for video teleconferences and music.  I have little experience with Linux (total newbie) but have managed to find my way -- up until this point.  For the last several weeks I have gone nuts trying to get Samba working with my network.  I simply want it to be a workstation like the others MS boxes and be able to access music and other files on the MS boxes, etc.  

I have searched and read a lot but have hit a dead end.  I have tried various configurations and have reached my wit's end with this.  I have posted my problem on the distribution's forum but there has not been a response.  Ubuntu forums seem to be more responsive, IMHO.  What I have learned is that Ubuntu has the best information and "how to" tutorials.  Yes, I plan to d/l and install Ubunto.  However, I would like to get this problem behind me -- so I come here with a plea for help in getting Samba to work.

**PROBLEM DESCRIPTION**
Although the Linux network ethernet settings use auto IP (BOOTP/DHCP), the IP address is a static assignment by the router (for all LAN).

I am able to ping to/from all machines with IP addresses and machine names.  In the Linux box I am able to see shares I have set up but I am unable to access the shared docs on the Win XP machines.  From Win XP machines, I do not see the Linux shares.  Nada.  Just message that path not found. 

It seems like a firewall issue but the Linux box does not have a firewall running.  The Windows XP machines have Zone Alarm configured to permit access of all machines on the LAN.  There is nothing to indicate the router might be a problem but I did configure it to permit ports 131-139, 445. 

**SAMBA CONFIGURATION**
I "think" my configuration is setup for no password accessing of files on other machines.  There is no security issue with this little home LAN that would require username and passwords.  What I am trying to achieve is no username/password accessing of files -- just like on my Win machines.  

Here is my current SAMBA configuration:

[global]
netbios name = Triboot
server string = Mandriva_2009
workgroup = MYNET
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 O_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true

log file = /var/log/log.%m
max log size = 50

username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
name resolve order = hosts wins bcast

local master = yes
preferred master = yes
os level = 65

wins support = yes


[private]
comment = Private
path = /usr/smbroot/private
public = no
writeable = yes
valid users = @private
write list = @private
directory mask = 0770
create mask = 0770

[public]
path = /usr/smbroot/public
comment = Public
public = no
create mask = 0770
directory mask = 0770
write list = @public

[temp]
path = /usr/smbroot/tmp
public = yes


Thank you for taking the time to read this.  I appreciate any help or suggestions.  i am totally lost and do not know the next step.

januszky

---

### Post by Eiríkr on 2009-02-09
Hello Januszky --

Welcome to the fora!  I hope your time in Linux Land, no matter which distribution, is ultimately a successful and positive experience.  There's definitely a learning curve, but it sounds like you're already well aware of that.  :)

Reading over your post, I noted that you're working on a no-password setup.  This can be tricky with Samba, due to Samba's default [font=courier]user[/font] access mode being backed by the Unix-y user-based permissions model.  That said, let's go over your [font=courier]smb.conf[/font] options and see what we can find.  Here, I skip all options that look fine.  I also link each listed option to the relevant section of [the official Samba conf file online man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html) for reference -- if you have any questions at all about an option, this is what you want to read.  

------------------------------------------------------------
**[global]**

**[security](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY) = user**
This is already the default value.  This line can thus be safely omitted from your conf file -- simple is good.  :)

**[null passwords](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NULLPASSWORDS) = true**
This is *only* needed if you have Samba usernames explicitly defined with no passwords (using the [font=courier]sudo smbpasswd -a USERNAME[/font] command).  

**[max log size](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAXLOGSIZE) = 50**
The value here is the size of the log file in KB:
> Samba periodically checks the size and if it is exceeded it will rename the file, adding a [font=courier].old[/font] extension. 
...
Default: [font=courier]max log size = 5000 [/font]
50KB seems quite small to me, but it's no biggie.  

**[username map](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP) = /etc/samba/smbusers**
This is **key** to your setup.  From the man page:
> This option allows you to specify a file containing a mapping of usernames from the clients to the server. This can be used for several purposes. The most common is to map usernames that users use on DOS or Windows machines to those that the UNIX box uses. The other is to map multiple users to a single username so that they can more easily share files. 

The 'other' purpose mentioned here sounds exactly like what you're trying to do.  Would you be so kind as to post the output of [font=courier]less /etc/samba/smbusers[/font]?  Feel free to change the names to protect the innocent.  :)  The key point here is the local usernames you are mapping to, and whether the permissions on your shared folders are configured to allow access to those usernames.

**[smb passwd file](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SMBPASSWDFILE) = /etc/samba/smbpasswd**
Default value.  Omitable.

**[name resolve order](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NAMERESOLVEORDER) = hosts wins bcast**
This is *almost* the default -- the default starts with [font=courier]lmhosts[/font] with the rest all the same.  This is most likely omitable.


**[private]**

**[path](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PATH) = /usr/smbroot/private**
A couple thoughts strike me here.  First off, the [font=courier]/usr[/font] directory on Unix-y systems has traditionally been set aside for user applications and utilities, whereas the [font=courier]/home[/font] directory is more often used for user data.  (More info [here](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) if you're interested.)  This is neither here nor there with regard to Samba specifically, but it's something to think about in terms of how you want to organize your hard drive(s) and partitions.  By way of an alternate example, I set up a separate [font=courier]/data[/font] directory into which I put all user data aside from settings files -- things like documents, music files, and the like.  I also put this directory in its own partition -- this way I can wipe the root partition and install a completely different distro, and I don't have to worry about losing my data files (provided I'm careful with the partitions).  

My second thought has more to do with your specific problems, and that is permissions -- it'd be very helpful if you could post the output of [font=courier]ls -l /usr/smbroot/private[/font].  This will allow us to see the owner, group, and access permissions for this directory, which could be part of what's causing your problems.  

**[public](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PUBLIC) = no**
Synonym for [font=courier][guest ok](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK)[/font].  Default value.  Omitable.

**[valid users](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS) = @private**
**[write list](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITELIST) = @private**
These two together seem redundant -- the [font=courier]write list[/font] option is only relevant if you want to allow *some* users to access as read-only, and others as writeable.  The [font=courier]valid users[/font] option defines only those users allowed to access this share.  Your option values here make it look like you want to allow write access to everyone allowed to access at all -- so you can probably omit the [font=courier]write list[/font] line.  


**[public]**

**[path](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PATH) = /usr/smbroot/public**
Much like for your private directory, please post the output of [font=courier]ls -l /usr/smbroot/public[/font].  

**[write list](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITELIST) = @public**
With no [font=courier]valid users[/font] specification, *any* non-guest user that can log onto your Samba setup (i.e. any user properly mapped to a local Linux username in your [font=courier]smbusers[/font] file, since you specify one) will be able to read this directory, but only members of the [font=courier]public[/font] Linux group will be able to write to it.  


**[temp]**
**[path](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PATH) = /usr/smbroot/tmp**
Much like for your private directory, please post the output of [font=courier]ls -l /usr/smbroot/tmp[/font].  

**[public](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PUBLIC) = yes**
Synonym for [font=courier][guest ok](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK)[/font].  From the man page:
> If this parameter is [font=courier]yes[/font] for a service, then no password is required to connect to the service. Privileges will be those of the guest account.

It's important to look into what your guest account is, if you have any intention of allowing guest users.  The guest account can be specified in the [font=courier]smb.conf[/font] file by using the [guest account](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT) [global] option.  Note that the guest Samba account defaults to the [font=courier]nobody[/font] Linux user account, and this account usually has permission to access almost nothing in the filesystem, by default.  

------------------------------------------------------------

I suspect your problem comes down to filesystem permissions and username mapping.  The command output requested above should provide some very useful clues to getting your config fully sorted out.  

HTH,

-- Eiríkr

---

### Post by dmizer on 2009-02-09
> **januszky said:**
> **PROBLEM DESCRIPTION**
Although the Linux network ethernet settings use auto IP (BOOTP/DHCP), the IP address is a static assignment by the router (for all LAN).

I am able to ping to/from all machines with IP addresses and machine names.  In the Linux box I am able to see shares I have set up but I am unable to access the shared docs on the Win XP machines.  From Win XP machines, I do not see the Linux shares.  Nada.  Just message that path not found. 

It seems like a firewall issue but the Linux box does not have a firewall running.  The Windows XP machines have Zone Alarm configured to permit access of all machines on the LAN.  There is nothing to indicate the router might be a problem but I did configure it to permit ports 131-139, 445. 

There are two parts to a Samba configuration, a server and a client. This howto describes how to configure a Samba server. In other words, you've only configured your Ubuntu computer so that Windows computers can connect to it. If you want to use Ubuntu to connect to Windows computers, you'll need to configure Ubuntu as a client. To configure Ubuntu as a Samba client, please see the second link in my sig.

---

### Post by januszky on 2009-02-09
Eiríkr, dmizer -- 

Thanks for the ultra-fast response!  Frankly, I am a bit shocked!  I just posted my message just a few hours ago.

Okay, you have given me some things to do.  I am eager to do these tasks ASAP -- after jury duty today (if I don't get into a long trial).  

I will post back.

j

---

### Post by januszky on 2009-02-09
**Eiríkr**, here is the info you requested:

**OUTPUT: SMBUSERS**
[B][COLOR="SeaGreen"][root@Triboot ~]# less /etc/samba/smbusers
[/COLOR][/B]
# Unix_name = SMB_name1 SMB_name2 ...
root = administrator admin
nobody = guest pcguest smbguest
/etc/samba/smbusers lines 1-3/3 (END)

**PERMISSIONS INFO** 
Note: each folder has copy of test file (dhcp config) 

**[COLOR="SeaGreen"][root@Triboot ~]# ls -l /usr/smbroot/private[/COLOR]**
total 16
-rw-rw-r-- 1 bigjohn bigjohn 13739 2009-02-02 16:51 dhcp config

**[COLOR="#2e8b57"][root@Triboot ~]# ls -l /usr/smbroot/public[/COLOR]**
total 16
-rw-rw-r-- 1 bigjohn bigjohn 13739 2009-02-02 16:51 dhcp config

**[COLOR="#2e8b57"][root@Triboot ~]# ls -l /usr/smbroot/tmp[/COLOR]**
total 0


**dmizer**, I checked out the seond link and I am sorry but I'm not at that level.  I only looked at the first 2-3 pages but not all 85.  I gathered that it may be about a different approach with smbfs (which I know zero about).  I know it is basic but not me . . . yet.  :)  So, please excuse my ignorance (not knowing).  I'm an old guy who messed with a little DOS & BASIC decades ago and 'nix is new to me but I'm not uncomfortable with command line stuff given direction.  I'm at a genuine beginning stage now.

Thanks for reading and helping!

j

---

### Post by TechMansoor on 2009-02-09
This is the error I'm getting when trying to edit the smb.conf. I'm trying to follow the original poster instructions but through ubuntu server as opposed to desktop.


"mansoor@LocalFileServer:/etc/samba$ sudo edit smb.conf
Warning: unknown mime-type for "smb.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"


I get an error everytime I try to: sudo gedit/edit/vi/vim


Any suggestions as to why I wouldn't be able to get into the smb.conf file?

Everything worked up until this point:

"And finally we need to open the file inside an editor

Code:

sudo gedit /etc/samba/smb.conf"

---

### Post by Eiríkr on 2009-02-09
> **TechMansoor said:**
> This is the error I'm getting when trying to edit the smb.conf. I'm trying to follow the original poster instructions but through ubuntu server as opposed to desktop.


"mansoor@LocalFileServer:/etc/samba$ sudo edit smb.conf
Warning: unknown mime-type for "smb.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"


I get an error everytime I try to: sudo gedit/edit/vi/vim


Any suggestions as to why I wouldn't be able to get into the smb.conf file?

Everything worked up until this point:

"And finally we need to open the file inside an editor

Code:

sudo gedit /etc/samba/smb.conf"

Well, this is certainly bizarre, but I think I've found one possible problem -- the [font=courier]edit[/font] program is *not* a text editor, it is instead an alias for certain [font=courier]run-mailcap[/font] functionality.  I confess I really don't understand what [font=courier]run-mailcap[/font] is supposed to be used for, even after reading through the somewhat cryptic man page...

Anyway, try [font=courier]sudo gedit /etc/samba/smb.conf[/font] instead, and let us know what happens.  

HTH,

-- Eiríkr

---

### Post by TechMansoor on 2009-02-09
> **Eiríkr said:**
> Well, this is certainly bizarre, but I think I've found one possible problem -- the [font=courier]edit[/font] program is *not* a text editor, it is instead an alias for certain [font=courier]run-mailcap[/font] functionality.  I confess I really don't understand what [font=courier]run-mailcap[/font] is supposed to be used for, even after reading through the somewhat cryptic man page...

Anyway, try [font=courier]sudo gedit /etc/samba/smb.conf[/font] instead, and let us know what happens.  

HTH,

-- Eiríkr

Well yeah, I actually stated I get a similar error when trying gedit as well.

But here is the official error when trying gedit:

(gedit:28371): Gtk-WARNING **: cannot open display:

Error when trying vi or vim is not exsistent, but it goes into a blank smb.conf file which means its a new file of sorts I believe.

Anywho..again any suggestions would be thoroughly appreciated.. :):):):):)

---

### Post by Eiríkr on 2009-02-09
> **januszky said:**
> **Eiríkr**, here is the info you requested:

Hello Januszky --

Doh!  I forgot to add the [font=courier]-d[/font] switch to the [font=courier]ls[/font] command -- this  tells [font=courier]ls[/font] to output the info for the directory itself (which is what we need), instead of just the directory contents (which we don't need just now, maybe not at all).  So, if you could also post the results of the following, it would be much appreciated!  :)

```
ls -ld /etc/samba/private
ls -ld /etc/samba/public
ls -ld /etc/samba/tmp
```

The contents of your [font=courier]smbusers[/font] file raises numerous issues, which I don't have time to get into right at the moment -- I should have time later this evening, however.  Hopefully by then you'll also have posted the [font=courier]ls -ld[/font] output, and we can really go to town!  :D

Cheers,

-- Eiríkr

---

### Post by Eiríkr on 2009-02-09
> **TechMansoor said:**
> Well yeah, I actually stated I get a similar error when trying gedit as well.

But here is the official error when trying gedit:

(gedit:28371): Gtk-WARNING **: cannot open display:

Error when trying vi or vim is not exsistent, but it goes into a blank smb.conf file which means its a new file of sorts I believe.

Anywho..again any suggestions would be thoroughly appreciated.. :):):):):)

When you try to open [font=courier]gedit[/font], are you ssh-ing into a different box, or are you opening a terminal locally, right on the same machine that has the [font=courier]smb.conf[/font] file?

Either way, it sounds like your environment variables are slightly borked.  Try the following:

```
sudo export DISPLAY=:0
sudo gedit /etc/samba/smb.conf
```

If [font=courier]gedit[/font] comes up blank as [font=courier]vim[/font] does, then yes, your [font=courier]smb.conf[/font] file seems to be either missing or empty.  If so, check [font=courier]ls /etc/samba/[/font] and see if there might be a backup left over -- [font=courier]smb.conf~[/font] would be the file you want.  If that file exists but [font=courier]smb.conf[/font] does not, copy it over, and then edit:

```
sudo cp /etc/samba/smb.conf~ /etc/samba/smb.conf
sudo gedit /etc/samba/smb.conf
```

If there is no backup file, and [font=courier]gedit[/font] comes up blank, then I'm afraid you'll just have to copy in whatever template or options you want, and go from there.  Thankfully, there are many sample [font=courier]smb.conf[/font] files here on the Ubuntu fora that you can choose from.  :)

Cheers,

-- Eiríkr

---

### Post by TechMansoor on 2009-02-09
> **Eiríkr said:**
> When you try to open [font=courier]gedit[/font], are you ssh-ing into a different box, or are you opening a terminal locally, right on the same machine that has the [font=courier]smb.conf[/font] file?

Either way, it sounds like your environment variables are slightly borked.  Try the following:

```
sudo export DISPLAY=:0
sudo gedit /etc/samba/smb.conf
```

If [font=courier]gedit[/font] comes up blank as [font=courier]vim[/font] does, then yes, your [font=courier]smb.conf[/font] file seems to be either missing or empty.  If so, check [font=courier]ls /etc/samba/[/font] and see if there might be a backup left over -- [font=courier]smb.conf~[/font] would be the file you want.  If that file exists but [font=courier]smb.conf[/font] does not, copy it over, and then edit:

```
sudo cp /etc/samba/smb.conf~ /etc/samba/smb.conf
sudo gedit /etc/samba/smb.conf
```

If there is no backup file, and [font=courier]gedit[/font] comes up blank, then I'm afraid you'll just have to copy in whatever template or options you want, and go from there.  Thankfully, there are many sample [font=courier]smb.conf[/font] files here on the Ubuntu fora that you can choose from.  :)

Cheers,

-- Eiríkr

Ok so I am definitely ssh'ng into a local box to do all these commands. I didn't have an smb.conf~ but I had an smb.conf.template that I created per the instructions in the original post. Indeed, after copying back over the template to the smb.conf file, I still get the same gedit error:

(gedit:28529): Gtk-WARNING **: cannot open display:


what next?? I'll try the directions prior to this one now

---

### Post by TechMansoor on 2009-02-09
> **Eiríkr said:**
> Hello Januszky --

Doh!  I forgot to add the [font=courier]-d[/font] switch to the [font=courier]ls[/font] command -- this  tells [font=courier]ls[/font] to output the info for the directory itself (which is what we need), instead of just the directory contents (which we don't need just now, maybe not at all).  So, if you could also post the results of the following, it would be much appreciated!  :)

```
ls -ld /etc/samba/private
ls -ld /etc/samba/public
ls -ld /etc/samba/tmp
```

The contents of your [font=courier]smbusers[/font] file raises numerous issues, which I don't have time to get into right at the moment -- I should have time later this evening, however.  Hopefully by then you'll also have posted the [font=courier]ls -ld[/font] output, and we can really go to town!  :D

Cheers,

-- Eiríkr

OK. so after trying all three of these commands, I get a " no such file or directory" error on all three commands. I'm guessing samba now isn't configured correctly or actually installed correctly perhaps?

Originally I did a sudo apt-get install samba and hoped for the best...

It appeared to install correctly indeed.

Thanks so much for your help guys thus far.. you guys are awesome!!!

---

### Post by januszky on 2009-02-09
**Eirikr**, here's the new output:

**[COLOR="SeaGreen"][root@Triboot ~]# ls -ld /usr/smbroot/private[/COLOR]**
drwxrwx--- 2 root private 4096 2009-02-04 23:32 /usr/smbroot/private/

**[COLOR="#2e8b57"][root@Triboot ~]# ls -ld /usr/smbroot/public[/COLOR]**
drwxrwx--- 2 root public 4096 2009-02-04 23:32 /usr/smbroot/public/

**[COLOR="#2e8b57"][root@Triboot ~]# ls -ld /usr/smbroot/tmp[/COLOR]**
drwxrwx--- 2 root root 4096 2009-02-05 14:31 /usr/smbroot/tmp/
[root@Triboot ~]#

Not to worry about not being able to get to this right way.  My time is your time -- whenever.  :)

j

---

### Post by TechMansoor on 2009-02-09
> **januszky said:**
> **Eirikr**, here's the new output:

**[COLOR="SeaGreen"][root@Triboot ~]# ls -ld /usr/smbroot/private[/COLOR]**
drwxrwx--- 2 root private 4096 2009-02-04 23:32 /usr/smbroot/private/

**[COLOR="#2e8b57"][root@Triboot ~]# ls -ld /usr/smbroot/public[/COLOR]**
drwxrwx--- 2 root public 4096 2009-02-04 23:32 /usr/smbroot/public/

**[COLOR="#2e8b57"][root@Triboot ~]# ls -ld /usr/smbroot/tmp[/COLOR]**
drwxrwx--- 2 root root 4096 2009-02-05 14:31 /usr/smbroot/tmp/
[root@Triboot ~]#

Not to worry about not being able to get to this right way.  My time is your time -- whenever.  :)

j

mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/private
ls: cannot access /usr/smbroot/private: No such file or directory
mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/public
ls: cannot access /usr/smbroot/public: No such file or directory
mansoor@LocalFileServer:/$ sudo ls -ld/usr/smbroot/tmp
ls: invalid option -- '/'
Try `ls --help' for more information.
mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/tmp
ls: cannot access /usr/smbroot/tmp: No such file or directory
mansoor@LocalFileServer:/$


Indeed, these directories doesn't appear to be installed..what is up with that? :(

---

### Post by Eiríkr on 2009-02-09
> **TechMansoor said:**
> mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/private
ls: cannot access /usr/smbroot/private: No such file or directory
mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/public
ls: cannot access /usr/smbroot/public: No such file or directory
mansoor@LocalFileServer:/$ sudo ls -ld/usr/smbroot/tmp
ls: invalid option -- '/'
Try `ls --help' for more information.
mansoor@LocalFileServer:/$ sudo ls -ld /usr/smbroot/tmp
ls: cannot access /usr/smbroot/tmp: No such file or directory
mansoor@LocalFileServer:/$


Indeed, these directories doesn't appear to be installed..what is up with that? :(

Just time for a quick note before running out the door -- these [font=courier]ls -ld[/font] commands are specific to Januszky's setup -- you can ignore them.  

And your "display not found" problems are because you're ssh-ing in.  You need to add the [font=courier]-X[/font] flag (that's a capital "X") to your ssh command line to enable proper X GUI program functionality -- otherwise the GUI program tries to run on the machine you've ssh-ed to, only without the proper display envars set, which doesn't work too well, as you've noticed.  Read up on [font=courier]man ssh[/font] if you're interested in more, or google for "ssh x tunnel" for what might be easier-to-understand material.  :)

Cheers,

-- Eiríkr

---

### Post by TechMansoor on 2009-02-09
> **Eiríkr said:**
> Just time for a quick note before running out the door -- these [font=courier]ls -ld[/font] commands are specific to Januszky's setup -- you can ignore them.  

And your "display not found" problems are because you're ssh-ing in.  You need to add the [font=courier]-X[/font] flag (that's a capital "X") to your ssh command line to enable proper X GUI program functionality -- otherwise the GUI program tries to run on the machine you've ssh-ed to, only without the proper display envars set, which doesn't work too well, as you've noticed.  Read up on [font=courier]man ssh[/font] if you're interested in more, or google for "ssh x tunnel" for what might be easier-to-understand material.  :)

Cheers,

-- Eiríkr

I'm using putty if that makes a difference.

---

### Post by dmizer on 2009-02-09
> **januszky said:**
> **dmizer**, I checked out the seond link and I am sorry but I'm not at that level.  I only looked at the first 2-3 pages but not all 85.  I gathered that it may be about a different approach with smbfs (which I know zero about).  I know it is basic but not me . . . yet.  :)  So, please excuse my ignorance (not knowing).  I'm an old guy who messed with a little DOS & BASIC decades ago and 'nix is new to me but I'm not uncomfortable with command line stuff given direction.  I'm at a genuine beginning stage now.

If you can follow this howto, you can follow that one. All you need to do is follow the first post. It looks like a lot, but it's really only a few edits. If you follow it closely, you will have working access to your Windows computers.

If it's still too much for you, you might try a different approach. Use FTP instead of Samba for file sharing. Try the 5th link in my sig.

---

### Post by dmizer on 2009-02-09
> **Eiríkr said:**
> Anyway, try [font=courier]sudo gedit /etc/samba/smb.conf[/font] instead, and let us know what happens.  

Any time you use a graphical interface, you should invoke SU priveleges with gksudo or you will likely get GTK errors.
```
gksudo gedit /etc/samba/smb.conf
```

This is important to note because Ubuntu does not have a root account by default.

More information here: [http://linux.die.net/man/1/gksudo](http://linux.die.net/man/1/gksudo)

It's also important to note that sometimes GUI text editors add invisible characters to files, so it's really not a good idea to use them for editing conf files.

---

### Post by Eiríkr on 2009-02-09
> **TechMansoor said:**
> I'm using putty if that makes a difference.

It makes a huge difference -- this means you're sitting in front of a Windows computer, so no X-based (i.e. Linux GUI) programs will run.  You'll have to use vim, emacs, nano, or pico instead, since these are terminal-based.  My personal preference is vim, but pick your poison.  ;)  There should be cheat-sheets easily findable online for the commands used in any of these.  

Cheers,

-- Eiríkr

---

### Post by erictherev on 2009-02-16
In other distros I have used in the past, I was able to configure samba for sharing, then have my file share box just show up on the Win network without making any modifications to the Win machines on the network. I have transferred the same smb.conf from distro to distro and have always had good luck with this.

I recently upgraded my system from a 160Gb hdd to a 320Gb hdd, and when doing so, I managed to lose my smb.conf. Now, I'm having a hard time reconfiguring my system to share files over the Win network. In most other distro, I did this via the kcontrol panel, but in Kubuntu 8.1.0, this feature is gone.

I need help setting up my system so that it will just share to everyone, without passwords and without having to modify settings on the Win boxes.

Here's my smb.conf, if it helps at all.

```
[global]
    ; General server settings
    netbios name = HONOGHR
    server string =
    workgroup = GALACTIC_EMPIRE
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Comics]
path = /home/shared/Comics/
browseable = yes
read only = no
guest ok = yes

[Gaming]
path = /home/shared/Gaming/
browseable = yes
read only = no
guest ok = yes

[ISOs]
path = /home/shared/ISOs/
browseable = yes
read only = no
guest ok = yes

[LEGO]
path = /home/shared/LEGO/
browseable = yes
read only = no
guest ok = yes

[Music]
path = /home/shared/music/
browseable = yes
read only = no
guest ok = yes

[Setup]
path = /home/shared/Setup/
browseable = yes
read only = no
guest ok = yes

[Torrents]
path = /home/shared/torrents/
browseable = yes
read only = no
guest ok = yes
```

---

### Post by dmizer on 2009-02-16
> **erictherev said:**
> In other distros I have used in the past, I was able to configure samba for sharing, then have my file share box just show up on the Win network without making any modifications to the Win machines on the network. I have transferred the same smb.conf from distro to distro and have always had good luck with this.

I recently upgraded my system from a 160Gb hdd to a 320Gb hdd, and when doing so, I managed to lose my smb.conf. Now, I'm having a hard time reconfiguring my system to share files over the Win network. In most other distro, I did this via the kcontrol panel, but in Kubuntu 8.1.0, this feature is gone.

I need help setting up my system so that it will just share to everyone, without passwords and without having to modify settings on the Win boxes.
This should work for you (note, the "wins support = no" is an extremely important change):
```
[global]
    ; General server settings
    netbios name = HONOGHR
    workgroup = GALACTIC_EMPIRE
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    security = share
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[Comics]
path = /home/shared/Comics/
browseable = yes
read only = no
guest ok = yes

[Gaming]
path = /home/shared/Gaming/
browseable = yes
read only = no
guest ok = yes

[ISOs]
path = /home/shared/ISOs/
browseable = yes
read only = no
guest ok = yes

[LEGO]
path = /home/shared/LEGO/
browseable = yes
read only = no
guest ok = yes

[Music]
path = /home/shared/music/
browseable = yes
read only = no
guest ok = yes

[Setup]
path = /home/shared/Setup/
browseable = yes
read only = no
guest ok = yes

[Torrents]
path = /home/shared/torrents/
browseable = yes
read only = no
guest ok = yes
```

---

### Post by erictherev on 2009-02-16
That works perfectly!

Now, I want to add another share that I want to have password-protected, so that when any other network computer (Win or Linux) attempts to connect to it, the user is prompted for a password.

Any ideas there?

---

### Post by dmizer on 2009-02-16
> **erictherev said:**
> That works perfectly!

Now, I want to add another share that I want to have password-protected, so that when any other network computer (Win or Linux) attempts to connect to it, the user is prompted for a password.

Any ideas there?

This depends on what you mean by "user is prompted for a password".

If the username and password are the same as they have for logging into Windows, this is not a problem because Samba authenticates at the user account level. If a login username and password do not match the Windows user's account, this usually causes errors. So, if all your Windows computers are logged in as "administrator", you won't be able to do much in the way of authenticated shares.

---

### Post by erictherev on 2009-02-16
> **dmizer said:**
> This depends on what you mean by "user is prompted for a password".
I want any user attempting to access the data contained in this one shared directory to have to manually enter a password every time they attempt to access it.

> **dmizer said:**
> If the username and password are the same as they have for logging into Windows, this is not a problem because Samba authenticates at the user account level. If a login username and password do not match the Windows user's account, this usually causes errors. So, if all your Windows computers are logged in as "administrator", you won't be able to do much in the way of authenticated shares.
I don't want there to be usernames and passwords associated with all of the shared directories, just the one.

---

### Post by dmizer on 2009-02-16
> **erictherev said:**
> I want any user attempting to access the data contained in this one shared directory to have to manually enter a password every time they attempt to access it.
Again, if the Samba username and password is different from the Windows login username and password, this configuration is difficult.

> **erictherev said:**
> I don't want there to be usernames and passwords associated with all of the shared directories, just the one.
This is quite possible, but again ... it's important to realize that [Windows login id and password] = [Samba userid and password].

So if user John logs into his Windows computer with a password of 1234, it's not possible (from my experience) to allow John to log into Samba with anything other than:
user - John
pass - 1234.

However, John will still be perfectly free to use any share you have configured for guest access whether John has logged into Samba or not.

---

### Post by erictherev on 2009-02-16
OK, I think I get this, but if I continue trying to follow your tutorial with this, wouldn't I have to enable WINS in my smb.conf?

Also, is this completely case sensitive? i.e. Would john on the Linux system have to be john in Windoze, or could he be John?

---

### Post by erictherev on 2009-02-16
OK, I answered my own questions...

Case sensitive = yes

Enable WINS support in smb.conf = yes

I did leave out the "ForceUser" and "ForceGroup" options in my smb.conf, but even so, on the Windoze systems that are supposed to have access to that directory, there is free access. On the PCLinuxOS system that is not supposed to have access, it prompts for username and password. I'm sure that other systems on the local network would either be denied access or would have to enter username and password.

As far as all of the other shared directories go, there is free access, just like there should be.

Thanks a lot for all of your help, dmizer!

---

### Post by dmizer on 2009-02-17
> **erictherev said:**
> OK, I think I get this, but if I continue trying to follow your tutorial with this, wouldn't I have to enable WINS in my smb.conf?
No, wins in smb.conf is not what it sounds like. 

> **erictherev said:**
> Also, is this completely case sensitive? i.e. Would john on the Linux system have to be john in Windoze, or could he be John?
Yes, this is case sensitive. John != john

I'll post an example when I get home from work, my SSH connection isn't cooperating at the moment.

---

### Post by fourthofjuly on 2009-02-17
hello!

i am relatively a newbie at ubuntu server level...

if we setup ubuntu samba server for xp clients, is there any way we can force xp users to save files to their samba share instead of saving files locally on the client machines?

the main purpose is to have a central organised data storage so that any user can have access to his / her files sitting at any of the 100 client  machines.

also, is there any antivirus system that can be setup on the server that can defend our xp clients?

plus, taking backup is obviously easier for the admin since the machines are scattered in several locations.

please guide us...

regards,

fourthofjuly

---

### Post by jivabill on 2009-02-17
Hi fourthofjuly, nice to meet you.
I am sorry to say that my skill level with Linux and with networking especially is not sufficient to answer you questions.  I know there are others in the networking forums who know the answers, I hope one or more of them will jump in and help you.

As to setting up the network to force clients to save to a specific location, I think that can be done, I right now do not know how.  Same with an antivirus at the server level to protect the XP clients.  That I think is a standard practice in networking.  Again, it is beyond my knowledge at the moment.  I too am still learning, with help here, about the subject.
Bill

---

### Post by RealG187 on 2009-02-20
This works great, but is there a way I can remove the password that XP asks for? Can I make different shares have different password and some have no password (if I dont want unauthorized access to my files I won't share them to begin with. I don't want my samba password to be the same as my ubuntu login because if I tell the pass to network users they will know the login to my laptop.

---

### Post by Faolan on 2009-02-21
> **RealG187 said:**
>  I don't want my samba password to be the same as my ubuntu login because if I tell the pass to network users they will know the login to my laptop.

Create a new SAMBA user, that should do the trick:

smbpasswd -a username
smbpasswd -e username

The first line creates the user and the second enables it, if you're using a database user list you may need to create a new Linux user then use this command:

pdbedit -a username

To confirm a user account use this:

pdbedit -w -L | awk -F: '/username/ {print $1}'

---

### Post by Faolan on 2009-02-21
> **fourthofjuly said:**
> hello!

if we setup ubuntu samba server for xp clients, is there any way we can force xp users to save files to their samba share instead of saving files locally on the client machines?

the main purpose is to have a central organised data storage so that any user can have access to his / her files sitting at any of the 100 client  machines.

Probably the best option here would be have a setup similar to a Windows Server farm. Essentially you would map the drives using:

net use z: \\Netbios name\share name

In the users start up script in Windows, then point the users My Docs folder to that share.

Presumably you will want on the server individual space for each user so you're probably going to have share a folder like this

[usershare]
  comment = User My Docs folder
  path = /home/users/%U/MyDocs
  browsable = no
  public = no
  read only = no
  valid users = %S

To be honest you're probably going to have down the LDAP/Active Directory Route which would make managing a 100 users easier.

This is not something I've done, but I've been looking into.

---

### Post by fourthofjuly on 2009-02-22
thanks Faolan, your help is appreciated...

as i understand, this will create a z: drive under all xp machines where the users should be asked to save their files; this will store the files to the user's home folder on the server and not on the client...

for antivirus, i liked clamav, but it is a manual scanner... 

if installed to the server, can it be automated to scan files immediately when they are saved? also if a virus is detected, what action will clamav take?

---

### Post by dmizer on 2009-02-22
> **fourthofjuly said:**
> for antivirus, i liked clamav, but it is a manual scanner... 

if installed to the server, can it be automated to scan files immediately when they are saved? also if a virus is detected, what action will clamav take?
You can automate clamscan with crontab. It will not automatically scan every file when it's created, but you can configure cron start periodic scans.

---

### Post by Faolan on 2009-02-23
> **fourthofjuly said:**
> thanks Faolan, your help is appreciated...

as i understand, this will create a z: drive under all xp machines where the users should be asked to save their files; this will store the files to the user's home folder on the server and not on the client...

You will also need to set the users home profile to point to that directory. This can be done doing the following in XP:

Start - Run - control userpasswords2
Go to the advanced tab, choose advanced then users/username
In Username got to profile
Put in the Profile Path the Path to their folders on the Linux box.

This will give them a roaming profile. However if you want to make all their my documents roaming you need to do:

Right click on My Documents and choose properties
Choose Move and point it to the shared drive.

The is more efficient in an AD domain where you can set a group policy for all members. This means you don't have to do it for every member and when you create new members it cuts down on mistakes.

Finally you will have to map the drive using in start up scripts:

net share driverletter://server/directory 

So that My Docs is available, so you'll need to set up a valid user list and/or AD in SAMBA to prevent your passwords being seen in the script.

---

### Post by Iceman_B on 2009-02-23
Nice Tutorial! It got me(a linux n00b) as far as having a working share on my Ubuntu box!
I would like some asssitance in making a clear picture out of the following:

I have an 8.10 box running, no screen hooked up, so I'm admining it remotely via putty(winxp pro).

The ubuntu box is called "rin-chan", the only user on it is "ravi".
My Windows laptop has a few users, the main being "Ravi" with a password.

I want to make share available for all my house mates in the network, whom are all using either WinXP home or pro.

[http://paste.ubuntu.com/121868/](http://paste.ubuntu.com/121868/) for my config.

How exactly do you configure the usernames and groups within samba? I want the share to be persistent after an initial mount and not have to deal with different user accounts on the windows machines. I also want nobody from within windows being able to modify any rights, everyone should get complete rights on all the files and subdirs within that share.
All users on windows have different usernames.

What's a smart way to accomodate all of this? What usernames in samba and/or linux correspond with those in windows?

Once that is running, I'd like to know how I make the entire share 10.0 GB in size, how would I go about to fix that?

Thanks!

---

### Post by fourthofjuly on 2009-02-23
thank you dmizer...

i guess for hourly scan, i will add following after crontab -e

0 * * * * /usr/bin/clamav

will this scan each & every file right from root? or should i append / above? again that should require root privileges...

pl help...

---

### Post by fourthofjuly on 2009-02-23
thank you again Faolan...

i will test the second (more effecient) method, which should help...

---

### Post by erictherev on 2009-02-28
What I have is a samba share setup with a Kubuntu 8.10 file server and Windoze machines that can connect to it. Most of the files are shared with all users, with the exceptions of the home directories for 2 of the users (nomad and lupa), which only the owners of those directories can access. Additionally, there is one other directory (not listed in the code below) that both of those users, and only those users, can access. As far as filesharing goes, this setup works great.

What I want is for the HP LaserJet 6P connected to the Kubuntu system to be openly shared on the network. Currently it shows up on the Windoze systems, but under the icon it says, "Access denied, unable to connect".

Any ideas on how to fix this?

```
[global]
; General server settings
netbios name = HONOGHR
workgroup = GALACTIC_EMPIRE
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 

security = share
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes
map to guest = Bad User

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[Comics]
path = /home/shared/Comics/
browseable = yes
read only = no
guest ok = yes

[Gaming]
path = /home/shared/Gaming/
browseable = yes
read only = no
guest ok = yes

[ISOs]
path = /home/shared/ISOs/
browseable = yes
read only = no
guest ok = yes

[LEGO]
path = /home/shared/LEGO/
browseable = yes
read only = no
guest ok = yes

[Music]
path = /home/shared/music/
browseable = yes
read only = no
guest ok = yes

[Setup]
path = /home/shared/Setup/
browseable = yes
read only = no
guest ok = yes

[Torrents]
path = /home/shared/torrents/
browseable = yes
read only = no
guest ok = yes

[lupa's_documents]
path = /home/lupa/Documents
browseable = yes
read only = no
guest ok = no

[nomad's_documents]
path = /home/nomad/Documents
browseable = yes
read only = no
guest ok = no
```

As always, any and all help is greatly appreciated.

---

### Post by dmizer on 2009-02-28
> **erictherev said:**
> What I want is for the HP LaserJet 6P connected to the Kubuntu system to be openly shared on the network. Currently it shows up on the Windoze systems, but under the icon it says, "Access denied, unable to connect".

Don't use samba to share your printers. I've never been successful with this. Use the cups interface to configure and share your printers to your windows machines:

[http://localhost:631](http://localhost:631)

---

### Post by januszky on 2009-03-01
Greetings!

I have read almost everything about getting Samba to work for me.  Posts on forums only lead to unrelated "solutions" (that were no solutions at all).  I never found anyone with the exact same problem I had.  

See: [http://ubuntuforums.org/showthread.php?t=202605&page=72](http://ubuntuforums.org/showthread.php?t=202605&page=72)

Yeah, *HAD*.  When I was about to totally give up on actually being able to access files from my LAN,  I decided to take a different approach and discovered the solution, one I'd not seen on any forum -- at least as a coherent solution.  

Of course, learning is a journey and every reply and comment contributed to my finally arriving at a solution.  

So, I am grateful to those who offered suggestions. Thanks!!

j

---

### Post by dmizer on 2009-03-01
> **erictherev said:**
> I did leave out the "ForceUser" and "ForceGroup" options in my smb.conf, but even so, on the Windoze systems that are supposed to have access to that directory, there is free access. On the PCLinuxOS system that is not supposed to have access, it prompts for username and password. I'm sure that other systems on the local network would either be denied access or would have to enter username and password.

I just realized I never posted my example like I intended to. My apologies.

Here's a share with user only access:
```
[accounting$]
        path = /home/shared/accounting
        browseable = no
        read only = no
        guest ok = no
        valid users = jack,jill
```
For this share, only users jack and jill have access to the share. I also put a "$" after the share name to make it invisible on the network, and the only way to get to the share is to manually map the network drive as outlined here: [http://support.microsoft.com/kb/308582](http://support.microsoft.com/kb/308582)

Both jack and jill were added to the Ubuntu server as users with the the following command:
```
sudo useradd -s /bin/true jack
sudo smbpasswd -L -a jack
sudo smbpasswd -L -e jack
```

No one other than jack or jill can gain access to the share even if they knew the share existed.

---

### Post by erictherev on 2009-03-01
Thanks again, dmizer...

I told CUPS to "Allow printing from the Internet" and now it works.

> **dmizer said:**
> Don't use samba to share your printers. I've never been successful with this. Use the cups interface to configure and share your printers to your windows machines:

[http://localhost:631](http://localhost:631)

---

### Post by racknemx on 2009-03-03
Thanks a lot Storm, great HOWTO, worked perfectly from the first time i tried it (after days of struggling with samba), and its very nice of you to answer so fast, THANKS again. :D

---

### Post by RealG187 on 2009-03-04
Is it possible to make it so most my folders don't have a password/username, but some do, but the user name and password are different than the ones I login with?

---

### Post by Dazey on 2009-03-07
Hi Stormbringer,

I'm a new Ubuntu user - which will become evident.  Anyway this file sharing is one of the most important things for me.  I got stuck in a couple of places though.  One is.. how to configure the windows network.  You said to do an ipconfig in windows, right?  That shows me my internet IP address.  Is that what I want, or....?  Thanks in advance!

Linda

---

### Post by Iceman_B on 2009-03-08
> **Dazey said:**
> Hi Stormbringer,

I'm a new Ubuntu user - which will become evident.  Anyway this file sharing is one of the most important things for me.  I got stuck in a couple of places though.  One is.. how to configure the windows network.  You said to do an ipconfig in windows, right?  That shows me my internet IP address.  Is that what I want, or....?  Thanks in advance!

Linda
Make sure all the windows machines within the network are on the same network(eg. 192.168.x.y) AND the same workgroup.
On XP: right-click "My Computer" > Properties > Computer name > change...
Whatever you enter as workgroup, make sure you do the same for each computer in the network.
Then enter that workgroup name in your samba configuration file.

What this technically does in Windows, I have no idea, if someone could explain it to me, please do so.

---

### Post by m0lo on 2009-03-10
After completing this awesome guide everything is working but one thing. When I log on, from the Windows client, I get a folder called "MyFiles" thou I specified to get to the home directory on the smb.conf /home/m0lo/. When I click on the MyFiles folder nothing happends, it just loops. What could be the problem? Where is this "MyFiles" folder located? Can't find it when I search.

```
[global]
    ; General server settings
    netbios name = LAPTOP
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/falkinski/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = FALKINSKI
    force group = FALKINSKI
```

Greatful for all answers!

---

### Post by Iceman_B on 2009-03-10
Try changing the last part to 

```

[MyShare]
    path = /home/falkinski/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = FALKINSKI
    force group = FALKINSKI
```

The [MyShare] label is the name that gets seen as a folder name by Windows, from my experience.

---

### Post by WildeBeest on 2009-03-11
Anyone know how to share a printer connected to a Ubuntu machine with Windows XP?

I'm running 8.04 64 bit.

I have the following in smb.conf

```
[print$]
comment = Printer Drivers
path = /etc/samba/drivers
browseable = yes
guest ok = yes
read only = yes
write list = root

[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
public = yes
guest ok = yes
writable = no
printable = yes


```

The windows machine sees the printer (add network printer).
After I select the printer:
It gives me an error message "The server for the printer does not have the correct printer driver installed. If you want to search for the printer driver, click OK..."
I click OK and it brings up a list of printers and the printer is not in the list.

---

### Post by dmizer on 2009-03-11
> **WildeBeest said:**
> Anyone know how to share a printer connected to a Ubuntu machine with Windows XP?

Click: System > Administration > Printing
Under Server Settings check the "Share published printers connected to this system".
Click: Apply.

Done.

---

### Post by dmizer on 2009-03-11
> **WildeBeest said:**
> Anyone know how to share a printer connected to a Ubuntu machine with Windows XP?

Click: System > Administration > Printing
Under Server Settings check the "Share published printers connected to this system".
Click: Apply.

Done.

For more information on how to configure your Windows computer to see the printer, check here: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine)

---

### Post by Erlander on 2009-03-12
> Anyone know how to share a printer connected to a Ubuntu machine with Windows XP?You may also have to install the Windows print driver for the printer on the XP machine.

---

### Post by WildeBeest on 2009-03-12
@dmizer

I had already done that.

@Erlander

Did that too.



Since my last post I did get it to work when the login/password on my Windows machine is the same as the Ubuntu box.

How do I print from a Windows machine that does not have logins setup?
(Like my wife's laptop)

---

### Post by dmizer on 2009-03-12
> **WildeBeest said:**
> @dmizer

I had already done that.

@Erlander

Did that too.



Since my last post I did get it to work when the login/password on my Windows machine is the same as the Ubuntu box.

How do I print from a Windows machine that does not have logins setup?
(Like my wife's laptop)

CUPS won't care if your Windows box has a login or not. If you have cups properly configured for printer sharing, and you've entered the correct path when adding the printer on Windows, you WILL have a working network printer.

Try configuring your printer by browsing to [http://localhost:631](http://localhost:631)

Are there any firewalls in the way? Do you have firestarter installed on Ubuntu?

Alternatively, you can try changing the "security = user" option to "security = share" in smb.conf.

---

### Post by WildeBeest on 2009-03-13
Thanks dmizer "http://localhost:631" worked.

I just thought it was a logon issue because when both were the same I could browse from add printer and see the printers.

---

### Post by ikalce on 2009-03-14
> **Stormbringer said:**
> **HOWTO: Setup Samba peer-to-peer with Windows**

As many fellow Ubuntu users seem to have trouble setting up samba peer-to-peer with Windows I decided to write a small howto on this matter.

NOTE: I am aware that there's a wiki-page as well as several other howto's around - but by looking at the constant "how do I setup samba" posts that are floating around in the forum I simply see the need for a more thourough guide on this matter.

Feel free to contribute and suggest - it'll only help to make this howto a better guide.

The goal of this howto is to have samba act like a Windows Workstation in the LAN. As a "value added bonus" we will use samba to do netbios name resolution so that you can use the names of the workstations for network drive mapping instead of their ip-addresses (i.e.: \MY_WINDOWS_BOX\SHARE) - but only for as long as your Linux box has an static ip-address and is up and running.

This guide is based on Ubuntu 6.06 LTS and intended for all architectures (i386, AMD64, ...) - if you are still using Breezy it's safe to follow this guide as there should be no differencies.

A second guide on how to setup samba as Primary Domain Controller along with several other services such as DHCP, DNS and NTP will follow later on as this topic will be a little more thourough.


**1. Prerequisites**

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

- You need to have samba installed.
If you haven't done so already open a terminal and type:

```

sudo apt-get install samba

```

Don't close the terminal upon installation - we still need the commandline to get several tasks done!


**2. Getting samba configured**

First, let us make sure samba isn't running:

```

sudo /etc/init.d/samba stop

```

As a starting point I included an smb.conf below, and there are only a few simple things you may need to tweak.

Since the installation of samba just installed a rather useless template file we're going to rename it - we keep the file just in case.

```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.template

```

Next we create a new empty file

```

sudo touch /etc/samba/smb.conf

```

And finally we need to open the file inside an editor

```

sudo gedit /etc/samba/smb.conf

```
*NOTE: If you're on KDE replace "gedit" with "kate"*

Copy / Paste the contents of the code-section below into your editor and read on ...

```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

```

Ok, I already mentioned that there are a few simple things you may need to tweak; so here they are:

-> netbios name = YOUR_HOSTNAME

Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best pratice would be to use the same name you configured upon installation.

Example:

netbios name = DAPPER

-> workgroup = YOUR_WORKGROUP

Replace "YOUR_WORKGROUP" with the name of your workgroup, but make sure you're using the same as configured in Windows.

To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

Example:

workgroup = MSHOME

-> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.

-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

```

sudo mkdir /home/samba

```

... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:

```

sudo chmod 0777 /media/samba

```
*NOTE: Don't forget to correct the path to the location you chose above!*

That's it - now we need to start samba ...


**1.1 Starting samba and setting up user accounts**

Let us fire up samba for the first time. Type:

```

sudo /etc/init.d/samba start

```

There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

Time to add yourself as an samba user.

*NOTE: You will be asked for a password - make sure you use the same as you use for login!*

```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

*NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!*

In the following example we will add an user called "mark" ...

Example:

```

sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark

```

The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


**2. Changing network settings in Windows**

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
*NOTE: Adjust this to the hostname and sharename you chose above!*
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
*NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.*
- Click "Finish"

That's it - samba is up and running now.


**3. Security consideration**

This is the right time to think about security right away.

In case your computer has more than one network connection (i.e. wired and wireless ethernet) you may want to restrict access to samba.

If not especially configured samba will bind its service to all available network interfaces.

So, let us assume you only want your wired network to have access and that the network card is called eth0.

Add the following lines to the [general] section of your smb.conf to achieve that goal:

```

interfaces = lo, eth0
bind interfaces only = true

```

If you did it correctly it should look similar to this:

```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

```

Now only the local loopback interface (dubbed "lo") and eth0 are able to access samba - there's no need to fear that someone might break into your system by wireless as the interface isn't bound to the service.


**4. Final words**

If you happen to have any questions feel free to ask - I'll try to help as soon as possible.

If you find any mistakes in this howto please let me know so that I can fix them.

Feel free to contribute and suggest - help to make this howto a better guide.


**5. Addendum: Useful links**

Here are some links you may find useful.

The onsite links refer to other samba-guides and to ubuntu_daemon's "Important Links" thread.

- Onsite
[Ubuntu Help: Windows Networkworking]("https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html")
[Ubuntu Documentation: Setting up Samba]("https://help.ubuntu.com/community/SettingUpSamba")

[READ THIS FIRST prior to posting - IMPORTANT links]("http://www.ubuntuforums.org/showthread.php?t=232059") (by ubuntu_daemon)


The offsite links refer to the offical Samba homepage and to a selected choice of their official documentation; these links are useful if you like to dig yourself into the mysteries of samba's configuration and usage as well as troubleshooting problems.

- Offsite
[Samba Homepage]("http://samba.org/")

[Practical Exercises in Successful Samba Deployment]("http://us3.samba.org/samba/docs/man/Samba-Guide/")
[The Official Samba-3 HOWTO and Reference Guide]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
[Using Samba, 2nd Edition]("http://us3.samba.org/samba/docs/using_samba/toc.html")

I make all of this conf but when i go to Network and double click on it it say:
UNABLE TO MOUNT LOCATION
failed to retrieve share list from server

here is my smb.conf

[global]
    ; General server settings
    netbios name = wtf
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/wtf/Shared Files/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = wtf
    force group = wtf



pls tell me what i should do ?

---

### Post by ikalce on 2009-03-14
and ..
from windows XP i can acces to my shared files on lunux box with the user name and pass who i wrote it and i can see modify and etc ... but from linux i cant seee anything :D
wtf is the problem pls some one tell me .......

---

### Post by dmizer on 2009-03-15
> **ikalce said:**
> wtf is the problem pls some one tell me .......

Your problem is this:
```
path = /home/wtf/[COLOR="Red"]Shared Files[/COLOR]/
```
You have a space in your path name. Either elminate the space (easy), or figure out how to correctly escape the space (I don't recall how at the moment and can't find it quickly).

---

### Post by ikalce on 2009-03-16
> **dmizer said:**
> Your problem is this:
```
path = /home/wtf/[COLOR="Red"]Shared Files[/COLOR]/
```
You have a space in your path name. Either elminate the space (easy), or figure out how to correctly escape the space (I don't recall how at the moment and can't find it quickly).

id did that with "_" =>  Shared_Files is now shared folder bit still can`t acces it pls for more help .....
The problem is from linux not from Windows :D

---

### Post by dmizer on 2009-03-16
What do you mean by this statement:
[code=ikalce]but from linux i cant seee anything[/quote]

Do you mean that you have more than one Linux computer and it's trying to access this share? Or do you mean that you have two computers (one XP, and one Linux), and you can't see XP shared files?

---

### Post by steve70 on 2009-03-20
I'm having some issues here...

I want my 8.10 machine to share files with my XP Home PC. I followed the tutorial, and was able to get samba going on my Ubuntu box, but when I tried to connect from my XP home box, windows wasn't able to connect, even though both PCs can ping each other, and the firewall disabled. 

Here comes the stupidity.....

In an attempt to reinstall samba, I removed the "samba" folder (and the samba.conf file within) and progam. When I reinstalled, I'm getting this error. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  libuser1 python-libuser
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 4226 package `libgvfscommon0':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

I can say now that I'm TOTALLY LOST in linux....

Two questions:

1. How bad was the screw up?
2. What do I need to do to get back to square one (ability to install samba)

---

### Post by milkyspit on 2009-03-20
> **steve70 said:**
> I'm having some issues here...

I want my 8.10 machine to share files with my XP Home PC. I followed the tutorial, and was able to get samba going on my Ubuntu box, but when I tried to connect from my XP home box, windows wasn't able to connect, even though both PCs can ping each other, and the firewall disabled. 

Here comes the stupidity.....

In an attempt to reinstall samba, I removed the "samba" folder (and the samba.conf file within) and progam. When I reinstalled, I'm getting this error. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  libuser1 python-libuser
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 4226 package `libgvfscommon0':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

I can say now that I'm TOTALLY LOST in linux....

Two questions:

1. How bad was the screw up?
2. What do I need to do to get back to square one (ability to install samba)

Steve, I believe the dpkg and/or apt-get command(s) offer a "reinstall" option. I don't recall the exact syntax offhand, but you'd basically want to issue that. If it doesn't work, next thing I would try is removing the package... force the removal (another option) if needed... then install fresh. That ought to do it. Sorry I don't have the exact commands memorized, though you shouldn't have much difficulty looking it up.

Hope this helps.

---

### Post by jja7001 on 2009-03-21
First, thanks for writing this HowTo.  I think it is exactly what I have been looking for! The step-by-step instructions are very well done, and were pretty easy to follow. The only thing that confuses me is what to do in the places where user names and passwords are called for.  In each instance, I'm not sure if the usernames and passwords required are those for the linux computer which is running samba, or for the windows computer I am trying to connect to. 

Specifically:


Regarding "netbios name = YOUR_HOSTNAME"
    Is "YOUR_HOSTNAME" the name of the linux box or the windows box?

Regarding "force user = YOUR_USERNAME" and "force group = YOUR_USERNAME"
    Is "YOUR_USERNAME" the name used to login to the linux box, or the one used to login to the windows xp box?

Regarding smbpasswd:
>     sudo smbpasswd -L -a your_username
    sudo smbpasswd -L -e your_username
Is "your_username" the user name used to login to the windows box or the linux box?

Likewise, in the example quoted below, is "mark" a user name for the linux box or the windows box?

> sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark


---

### Post by Iceman_B on 2009-03-21
Ive been trying to wrap my head around this user/password thing for a while now, and I'm still not sure about it.

This is what I gathered thus far:

Linux: has users with passwords. Your average user accounts.

Samba: has a seperate list of users, BUT they MUST be the same linux users on the same system.

Samba shares: Are accessible from Windows by any Samba(linux) users defined BUT, this will require a manual login.
And I believe it requires a manual login each time windows starts.
A prompt will pop up I believe.

If you want the share to be automatically mounted, you'll need to create a linux user with the same username as in Windows.
Then add that user to Samba and make sure the password in SAMBA is the same as the password for that user in WINDOWS.
This is because Windows tries to log onto a network share using the same login credentials as the user that just logged in.

For example:

Windows: User "Zero" pass "black"
In Linux: Create a user "zero", pass can be anything.
In Samba: add the user "zero" with password "black".

If anyone else knows wether this is all theoretically correct, please yell out.

---

### Post by dmizer on 2009-03-23
> **jja7001 said:**
> <snip>In each instance, I'm not sure if the usernames and passwords required are those for the linux computer which is running samba, or for the windows computer I am trying to connect to. 

Specifically:


Regarding "netbios name = YOUR_HOSTNAME"
    Is "YOUR_HOSTNAME" the name of the linux box or the windows box?
First of all, it helps to think about what this tutorial is doing. You are creating a file server. This means you are configuring your Ubuntu computer to share files to Windows computers. This howto does NOT tell you how to configure Ubuntu to see files on Windows computers.

Second of all, it helps to know that (by default) Ubuntu comes with no way of identifying itself to Windows computers. So without this option in your smb.conf, the only way a Windows computer could access Ubuntu is by IP address.

So to be more specific, the "YOUR_HOSTNAME" option should be the name you want your Ubuntu/Linux computer to be known as.

> **jja7001 said:**
> Regarding "force user = YOUR_USERNAME" and "force group = YOUR_USERNAME"
    Is "YOUR_USERNAME" the name used to login to the linux box, or the one used to login to the windows xp box?
For future reference, it may be useful for you to know about the "[man](http://www.linfo.org/man.html)" command. This command will show you the manual for just about whatever topic you're working with in Linux. For example if you enter this command:
```
man smb.conf
```
You can scroll through the text until you see the entry for "force user" which states:
```
This specifies a **[COLOR="Red"]UNIX[/COLOR]** user name that will be assigned as the default user for all users connecting to this service. This is useful for sharing files. You should also use it carefully as using it incorrectly can cause security problems.
```

Or in other words, this option should be your Ubuntu username (the one with local read/write privileges to the shared files).

> **jja7001 said:**
> Regarding smbpasswd:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```
Is "your_username" the user name used to login to the windows box or the linux box?
This was probably the most confusing point for me when I first used this tutorial. If I were to rewrite it, I would have used this example instead:
```
sudo smbpasswd -L -a your_ubuntu_username
sudo smbpasswd -L -e your_ubuntu_username
```

Basically, you're including your Ubuntu user (the one with sudo privileges) in the samba user group so that when you modify shared files locally, permissions don't get screwed up on the share.

> **jja7001 said:**
> Likewise, in the example quoted below, is "mark" a user name for the linux box or the windows box?
```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark 
```
Again, the "man" command would probably have been helpful to you here.

Entering
```
man useradd
```
Gives you this information:
```
useradd - create a new user or update default new user information 
```

Here, you are giving your Windows user an account in Ubuntu. This is so your Windows user has correct permissions to view and modify files on Ubuntu. As noted in the howto, it's important to use the exact same username and password you use to log into your Windows computer. If you've ever configured a dedicated Windows file server, you would have to perform this task on the Windows file server as well.

---

### Post by RealG187 on 2009-03-23
> **Iceman_B said:**
> Ive been trying to wrap my head around this user/password thing for a while now, and I'm still not sure about it.

This is what I gathered thus far:

Linux: has users with passwords. Your average user accounts.

Samba: has a seperate list of users, BUT they MUST be the same linux users on the same system.

Samba shares: Are accessible from Windows by any Samba(linux) users defined BUT, this will require a manual login.
And I believe it requires a manual login each time windows starts.
A prompt will pop up I believe.

If you want the share to be automatically mounted, you'll need to create a linux user with the same username as in Windows.
Then add that user to Samba and make sure the password in SAMBA is the same as the password for that user in WINDOWS.
This is because Windows tries to log onto a network share using the same login credentials as the user that just logged in.

For example:

Windows: User "Zero" pass "black"
In Linux: Create a user "zero", pass can be anything.
In Samba: add the user "zero" with password "black".

If anyone else knows wether this is all theoretically correct, please yell out.

I tried that but Windows 98 says there's an incorrect password. In XP I can log on using a different name, in 98 I can't. How can I remove the password alltogether?


Can someone please help me here:
[http://ubuntuforums.org/showthread.php?t=815382](http://ubuntuforums.org/showthread.php?t=815382)

---

### Post by mstrap123 on 2009-04-12
i have successfully setup samba on ubuntu 7.10 server using the guide...but the connection to samba keep disconnecting..is there any other settings that need to be done

---

### Post by ishboo on 2009-04-18
I did this tut and everything looks good. I can easily access my share on my linux PC from my windows Vista Machine. 

But my problem is accessing my windows shares from my linux PC. I have not been able to access shares since I have installed ubuntu. It keeps like crashing my filebrowser mking it freeze up my ubuntu, and finally saying unable to mount. I removed the password from the shares and gave full control to everyone group, still no luck.

and this is also a problem with my other PCS, I cannot access their windows XP shares either.

Anyone know why I cannot access my windows shares?

---

### Post by jivabill on 2009-04-18
Well, I had EXACTLY the same experience trying to network my XP Pro machine with my Ubuntu machines.  Exactly.  I can look at all the files and folders that I mark as shared on the Ubuntu machines from the XP Pro box, no problem. But I have the same problems, unable to mount etc, when I try to view the XP Pro box shares from the Ubuntu side.

So I spent many hours researching this, trying different long involved pieces of command line magic to no avail.  I tried removing all limits on permissions etc.  Nada.  

So where I am at is this is not worth the effort.  What I do is if I want to diddle with a file on one of the Ubuntu boxes I simply move it into a shared folder.  Then I go to the XP Pro box and manipulate it across the network.  Or move it to the XP Pro box, whatever.

I don't even bother with trying to manipulate files/folders across the network from the Ubuntu machines.

Certainly that is a "limited network" but that is all that will work so be it.  Just one of those places where the Ubuntu forces have not yet got their act together.
My two cents.

---

### Post by ishboo on 2009-04-18
> **jivabill said:**
> Well, I had EXACTLY the same experience trying to network my XP Pro machine with my Ubuntu machines.  Exactly.  I can look at all the files and folders that I mark as shared on the Ubuntu machines from the XP Pro box, no problem. But I have the same problems, unable to mount etc, when I try to view the XP Pro box shares from the Ubuntu side.

So I spent many hours researching this, trying different long involved pieces of command line magic to no avail.  I tried removing all limits on permissions etc.  Nada.  

So where I am at is this is not worth the effort.  What I do is if I want to diddle with a file on one of the Ubuntu boxes I simply move it into a shared folder.  Then I go to the XP Pro box and manipulate it across the network.  Or move it to the XP Pro box, whatever.

I don't even bother with trying to manipulate files/folders across the network from the Ubuntu machines.

Certainly that is a "limited network" but that is all that will work so be it.  Just one of those places where the Ubuntu forces have not yet got their act together.
My two cents.


Well there has to be some way of fixing this... Or I dont think people would use ubuntu within networks. I mean what you do simply defeats the purpose of networking a computer. 

I must say I was able to view the share files on my Windows machines when I had done a fresh install of Ubuntu, I was able to mount on desktop. But then it was still very buggy, would only work 1 of 10 times trying to access it. Then it would disappear. 

Now I am stuck at the point of viewing the workgroup, And I see each PC, but cannot view any shares on them.

---

### Post by jivabill on 2009-04-18
> **ishboo said:**
> Well there has to be some way of fixing this... Or I dont think people would use ubuntu within networks. I mean what you do simply defeats the purpose of networking a computer. 

I must say I was able to view the share files on my Windows machines when I had done a fresh install of Ubuntu, I was able to mount on desktop. But then it was still very buggy, would only work 1 of 10 times trying to access it. Then it would disappear. 

Now I am stuck at the point of viewing the workgroup, And I see each PC, but cannot view any shares on them.

Indeed.  And that to is my experience here, I can see all the machines from Ubuntu, any and all of them.  FYI I have also a win98se machine.  I see that too.  Can't access anything from Ubuntu machines.  BUT I can freely access the win98se from the XP machine and can access all the shares thru the group of Ubuntu machines from XP.  And of course the win98se machine can access the shares on the XP machine.

And you are right, I am sure there is probably a way to fix this.  It is just a matter of time and effort.  For me it just is not worth it to put more time into the problem.  When (and if) they come out with an official fix that works then I will try it.  Perhaps the problem will be taken care of in the later releases of Ubuntu.

---

### Post by ishboo on 2009-04-18
> **jivabill said:**
> Indeed.  And that to is my experience here, I can see all the machines from Ubuntu, any and all of them.  FYI I have also a win98se machine.  I see that too.  Can't access anything from Ubuntu machines.  BUT I can freely access the win98se from the XP machine and can access all the shares thru the group of Ubuntu machines from XP.  And of course the win98se machine can access the shares on the XP machine.

And you are right, I am sure there is probably a way to fix this.  It is just a matter of time and effort.  For me it just is not worth it to put more time into the problem.  When (and if) they come out with an official fix that works then I will try it.  Perhaps the problem will be taken care of in the later releases of Ubuntu.


I'm also having troubles accessing shares from ubuntu to ubuntu PCs as well. 

This is a real bummer. :/ guess I'll wait for some help, or maybe it gets fixed in a newer release.

I wonder if setting up a local FTP would work for the time being :)

---

### Post by dmizer on 2009-04-19
> **ishboo said:**
> I'm also having troubles accessing shares from ubuntu to ubuntu PCs as well. 

This is a real bummer. :/ guess I'll wait for some help, or maybe it gets fixed in a newer release.

I wonder if setting up a local FTP would work for the time being :)

For sharing files between Linux computers (Ubuntu to Ubuntu), don't use samba, use NFS. See the fourth link in my sig for how to configure NFS shares.

---

### Post by ishboo on 2009-04-22
> **dmizer said:**
> For sharing files between Linux computers (Ubuntu to Ubuntu), don't use samba, use NFS. See the fourth link in my sig for how to configure NFS shares.

Thanks I appreciate this! I am actually getting my family on ubuntu, so I would def love to learn.

---

### Post by rwslippey on 2009-04-22
I like your howto here and its appsolutly the best i have seen.. and I have been trying to get samba to work for days...

My problem now is... I want to be able to access my server from a ubuntu box also..

Basicly I have 3 systems (adding a 5 systems in my home)
One is a dedicated server for samba and some other stuff..(ubuntu Server LTS)

The others are all currently ubuntu desktops.. 

I want to give all of the users on my network access to file storage on the network and have it accessible from windows networks..

the future plans for this are to give me and my father , who works over the road... the ability to store files on the server and access them from outside our network via VPN ... 

how do i configure ubuntu desktop to access the server...

oh and I understand their are other ways to creating a file server for ubuntu desktops however the new computer will be windows to run some "required windows programs, ill need access their too"

Thanks again  great howto...

---

### Post by dmizer on 2009-04-22
> **rwslippey said:**
> how do i configure ubuntu desktop to access the server...

If you want to configure it, and never think about it again, see the second link in my sig. Otherwise, you can simply use the "places" > "connect to server" option in your menu.

---

### Post by rwslippey on 2009-04-22
Well   managed to make a connection... currently have it configured for the homes..... user's home directory ( and it was in due in great part to your post here) however I can't seem to write to it? not sure why   permisions look right...  Think I'm missing something


Thanks

Rob

---

### Post by dmizer on 2009-04-22
> **rwslippey said:**
> Well   managed to make a connection... currently have it configured for the homes..... user's home directory ( and it was in due in great part to your post here) however I can't seem to write to it? not sure why   permisions look right...  Think I'm missing something


Thanks

Rob

For several reasons, it will work much better if you only share a single folder dedicated to shared files.
[LIST]
[*]Most importantly, you won't be exposing your desktop configurations and settings to your lan.
[*]You can control permissions correctly.
[*]Far less of a security risk.
[/LIST]

In order to give _anyone_ full read/write permissions to your home folder, you have to set permissions to at least 766 at the directory level. But changing the permissions in your entire home folder will break things.

---

### Post by rwslippey on 2009-04-23
I managed to find my problem.. 

I have it configured for the home directorys... each user will have a home directory and be able to mount and write to it. The problem was listed on another post by you. (files were owned by root)

However your secuirty response raised a question. Is my configuration an unsafe secuirty practice. 

Thanks again

rob

---

### Post by dmizer on 2009-04-23
> **rwslippey said:**
> I managed to find my problem.. 

I have it configured for the home directorys... each user will have a home directory and be able to mount and write to it. The problem was listed on another post by you. (files were owned by root)

However your secuirty response raised a question. Is my configuration an unsafe secuirty practice. 

Thanks again

rob

As long as each user will have their own directory ... no problem. :)

Glad you got it working!

---

### Post by rwslippey on 2009-04-23
oh yes of course ... every user has their own home directory... their will be one directory accessable to a select number of users... Mainly me and my dad for transfering files back and forth.... but limited to just him and I...

thanks for your help   again great how to...

Rob

---

### Post by scorpion210 on 2009-04-26
Hi StormBringer,
I went through your HOWTO exactly as you had it, and I"m still not able to gain access to my linux box from Windows.  Upon the last step where you had 
"With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
*NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.*
- Click "Finish""
I receive an error message stating "The mapped network drive could not be created because the following error has occured: The specified network name is no longer available"

Now in my set up here is my samba file:
[global]
    ; General server settings
    netbios name = ken-linux-desktop
    server string =
    workgroup = CTECH
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ken
    force group = ken
=========================================================
Any thoughts or ideas on how I may have my samba file setup? Or what I may be doing worng. Thanks

---

### Post by clmcm400 on 2009-04-26
Thank you for this.  I created a thread about a month ago (then some crap came up), but I never got it working.  Did it again from scratch, and this worked great.
:)

---

### Post by dmizer on 2009-04-26
> **scorpion210 said:**
> 
Any thoughts or ideas on how I may have my samba file setup? Or what I may be doing worng. Thanks

Try this smb.conf:
```
[global]
    ; General server settings
    netbios name = ken-linux-desktop
    workgroup = CTECH
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ken
```

---

### Post by Iceman_B on 2009-04-26
Hey all,

I've managed to get Samba up and running.
What I want to do is this.
I have a harddrive with Ubuntu 8.10 server on it.
"parted" says:
```
Model: ATA Maxtor 6Y160P0 (scsi)
Disk /dev/sda: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      32.3kB  163GB  163GB  primary   ext3         boot
 2      163GB   164GB  757MB  extended
 5      163GB   164GB  757MB  logical   linux-swap
```

Windows says my share is 149 GB big.
What I want to do it make one piece of my harddrive, the lastmost part, a chuck of 140 GB which I can mount under my encrypted folder. The rest I want to leave for the OS, logs and whatnot.

The 140 GB piece is something I want to use as a samba share, a place where I can download media to (from linux itself) and share that via Samba. Also, I want to use more than one useraccount since I want to share the drive with my housemates.

Finally, I want every user to have his/her own little folder which is read/write only for that user, and have all other folders and the main root folder of the share be read-only for everyone but myself. The only real unix user is the one I created upon installl, I want all rights across the entire Samba Share.

How do I set this up and more importantly, can I still set this up?

---

### Post by scorpion210 on 2009-04-26
I figured out what the issue was.  For WINS I had it set to NO.  I changed that to yes, then used the \\ipaddress\MyFiles\ when I mapped it on my WINXP box.  Then had to allow Firestarter Firewall to accept incoming connections from the WINXP box.  Thank you StormBringer for your HOWTO.  Thank you.

---

### Post by laluz on 2009-04-27
Hi, I had a problem connecting to the file share. Printing and listing of the resources worked fine.

I kept getting the windows error 2221 "user name not found". And in the  /var/log/samba/log.wb-KUBUNTU there was this error 
[2009/04/27 08:11:41,  0] winbindd/winbindd_passdb.c:sid_to_name(159)
  Possible deadlock: Trying to lookup SID S-XXXXXXX with passdb backend

 I had to remove the winbind as discussed here
[http://ubuntuforums.org/archive/index.php/t-654699.html](http://ubuntuforums.org/archive/index.php/t-654699.html)

It can not be the real solution though. Just dumping the winbind?

---

### Post by Propaganda Panda on 2009-05-03
Ok, I followed the guide and got it working sort of. Im running 9.04. I was under the impression i could just right click and share, but I cant do that with a whole drive it seems.

If i use any of the windows PCs and login with my Ubuntu U/N and P/W access is granted.

Problem is i have 2 drives, and I want anyone on the network to have access to them without having to type in anything. Is this even possible?
They are separate drives and I dont care what anyone does to them.

I stopped doing anything after editing the smb.conf
The terminal stuff didnt seem to apply to what i was doing.. Should I keep going?

```

[global]
    ; General server settings
    netbios name = Share-PC
    server string =
    workgroup = JAPAN
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Sagittaron]
    path = /media/sdc1
    read only = no
    browsable = yes
    public = yes
    guest ok = yes

[Music]
        path = /media/sdd1
        read only = no
        browsable = yes
        public = yes
    guest ok = yes
```

---

### Post by eatdirt001 on 2009-05-05
I need help. After entering the information for the Map network drive in the windows xp computer that's connected to the printer, I am prompted for a username and password. I enter the hostname of my laptop, then it gets changed to "ip-address/hostname". I enter the password of my laptop, but it doesn't work. Does anyone else get this?

---

### Post by stanley82 on 2009-05-06
Hi, I've been trying on and off for some time to get win98 networkneighborhood up on samba.  I've got my three ubuntu machines to access my main 500 gig drive on my main system but not from my main system to the others.  Win98 is a loss.  Why do I have to manually assign IPs in place of having the router do it automatically?  When all my systems were win98 that was okay!  Some times I can see my win98 machine but not open the files from any ubuntu machine.  I'm quite lost for something that was really simple on win98.  The more I read the more I try and I think I need to do a clean all and start over from zero.  Any ideas?  Ian.

---

### Post by dmizer on 2009-05-10
> **stanley82 said:**
> Hi, I've been trying on and off for some time to get win98 networkneighborhood up on samba.  I've got my three ubuntu machines to access my main 500 gig drive on my main system but not from my main system to the others.  Win98 is a loss.  Why do I have to manually assign IPs in place of having the router do it automatically?  When all my systems were win98 that was okay!  Some times I can see my win98 machine but not open the files from any ubuntu machine.  I'm quite lost for something that was really simple on win98.  The more I read the more I try and I think I need to do a clean all and start over from zero.  Any ideas?  Ian.

Under the [global] section, add this option
```
lanman auth = yes
```

---

### Post by Fyrzen_ on 2009-05-25
Hello, great guide, easy to follow. :)

I've been trying to connect my vista laptop to my Ubuntu PC for ages. And the result has always been... failure. Sadly it's no different this time. I have no idea where to proceed from here. If anyone has any idea, please let me know.

It appears to be stuck on the Windows end if i'm interpreting this right.

INFO:
-It is possible to ping both PC's from oneanother. 
-The users and passwords on both boxes are **different.**.
-Naturally, i added and enabled both users using smbpasswd.
-Since I get my IP through DHCP, wins = no.
-The error Windows provides, when mapping the device is: "The Network Path was not found!"
-The path i'm trying to map is \\<ubuntu-IP>\MyFiles

-My smb.conf: (excluding the comments)

```
[global]
    ; General server settings
    netbios name = spyder
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes



; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = fyrzen
    force group = fyrzen
```

Any help is greatly appreciated! :mrgreen:

---

### Post by harpss1ngh on 2009-05-29
Hi, Stormbringer.

In your 1st post you mentioned that you planned to create a guide on HOWTO: Setup Samba as an PDC with additional services.


Is this guide available to view yet?

---

### Post by randyklein99 on 2009-05-29
Fyrzen,

Is your vista machine in WORKGROUP?  IME, the default windows workgroup is MSHOME.

---

### Post by ubila on 2009-05-30
Hello :D
Great guide thanks :D

Got everything working very quickly with no immediate problems :D

Do have a few issues though,

When i was mapping the network drive, i cant seem to map it to my hostname\file 
it only seems to work with ip-address\file 

And i seem to get alot of large lag/delay spikes when i open "My Computer" folder or when i try save a file using a program like Eclipse (php/java editing program) onto the samba share... Even browsing the mapped network drive causes large delays sometimes :(

My linux box hostname is the same as the hostname i entered into the smb.conf

Any help would be appreciated.

Cheers :D

---

### Post by Fyrzen_ on 2009-06-03
> **randyklein99 said:**
> Fyrzen,

Is your vista machine in WORKGROUP?  IME, the default windows workgroup is MSHOME.

The default workgroup name for Windows Vista is WORKGROUP, unless you upgraded to Vista from XP, in which case the default workgroup name is the same MSHOME as with any NT based Windows.:popcorn:

---

### Post by randyklein99 on 2009-06-03
> **Fyrzen_ said:**
> The default workgroup name for Windows Vista is WORKGROUP, unless you upgraded to Vista from XP, in which case the default workgroup name is the same MSHOME as with any NT based Windows.:popcorn:

Thanks for that clarification.

---

### Post by dmizer on 2009-06-03
Fyrzen_, try this:
```
sudo chmod -R 777 /home/samba
```

Backup your current smb.conf:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-old2
```

Replace it with this:
```
[global]
    ; General server settings
    netbios name = spyder
    workgroup = WORKGROUP
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    name resolve order = hosts wins bcast
    security = user

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    force user = fyrzen
```

---

### Post by Fyrzen_ on 2009-06-09
dmizer, thanks for the help.

I'm still getting an error on Vista:
> The specified network name is no longer available.

On the Windows side I have disabled File and Printer Sharing, which is said to conflict with accessing another Samba fileserver(wether it is on or not does not seem to effect the error message). I have also disabled NTLMv2 authentication, which Vista uses by default, but 2.x versions of Samba do not support and use old NTLM.

---

### Post by ramana1432 on 2009-06-14
thanx for your thread:D. i sucessfully done the samba configuration:o

---

### Post by harpss1ngh on 2009-06-15
Hey does anyone know whether stormbringer released his guide for HOWTO: Setup Samba as an PDC with additional services as he said he would according to his tutorial in his 1st post?

Does anyone know of any guide for setting up samba as a PDC with additional services?

I've managed to create a samba file server using this guide and slightly customizing it but I would like to use it as a PDC for a network with workstations running on windows XP Pro.


I appreciate any help

---

### Post by Icky_Ev on 2009-06-17
This guide saved my sanity. Thank you for writing a step by step for "the rest of us" :KS

---

### Post by paul94 on 2009-06-27
Thank you very much. Worked like a dream into Windows 2000 laptop from/to my laptop (Jaunty):D

---

### Post by Iceman_B on 2009-06-28
Does anyone know how to make Windows XP think that the samba share is part of the Local Network instead of the Internet Zone?

---

### Post by dmizer on 2009-06-28
> **Iceman_B said:**
> Does anyone know how to make Windows XP think that the samba share is part of the Local Network instead of the Internet Zone?

Make sure your workgroups match.

---

### Post by Iceman_B on 2009-07-05
> **dmizer said:**
> Make sure your workgroups match.
But they do!
The string right after workgroup is exactly the same as in Windows.
My server shows up when the browse the workgroup from within windows, and yet I get unusual prompts and the icon in the lower right corner also says "Internet zone".

```
[global]
        workgroup = ZION
        server string = %h (Running Samba on Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 4096
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d


```

So yeah, I'm baffled. How do I fix this ._.?

---

### Post by dmizer on 2009-07-05
> **Iceman_B said:**
> So yeah, I'm baffled. How do I fix this ._.?

You need to add the netbios name option, as described in the first page of this tutorial.

```
[global]
        workgroup = ZION
        [COLOR="Red"]netbios name = name-of-your-computer[/COLOR]
        server string = %h (Running Samba on Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 4096
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
```

---

### Post by Ian Ferguson on 2009-07-18
Thanks, Stormbringer. I'd been going spare trying to get two Ubuntu machines and a Vista machine to talk to each other and share files, but your replacement smb.conf did the trick!

---

### Post by ztmike on 2009-07-24
Can someone help me?

I'm going by this guide: [http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

But at 5:02 when that page pops up I get a blank page? I've installed Samba and tried reinstalling also, but I still can't get the text to come up?

---

### Post by Michalxo on 2009-07-25
> **ztmike said:**
> Can someone help me?

I'm going by this guide: [http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

But at 5:02 when that page pops up I get a blank page? I've installed Samba and tried reinstalling also, but I still can't get the text to come up?

There should be default file, so try
```
cat /etc/samba/smb.conf
```
Edit it with gksudo gedit ;)

---

### Post by ztmike on 2009-07-25
> **Michalxo said:**
> There should be default file, so try
```
cat /etc/samba/smb.conf
```Edit it with gksudo gedit ;)

Excuse me noobiness..but how do I edit with gksudo gedit or what I'm I even editing in that?

I am COMPLETELY LOST here. :confused:

---

### Post by Gourgi on 2009-07-28
> **ztmike said:**
> Excuse me noobiness..but how do I edit with gksudo gedit or what I'm I even editing in that?

I am COMPLETELY LOST here. :confused:

```
gksu gedit /etc/samba/smb.conf
```

---

### Post by davethewave83 on 2009-08-01
I followed all of this thinking it would let me access the files on my windows box from my linux box. This did not help at all. I have Samba and it can see my windows pc's name, but it cannot browse files. :(

---

### Post by dmizer on 2009-08-01
> **davethewave83 said:**
> I followed all of this thinking it would let me access the files on my windows box from my linux box. This did not help at all. I have Samba and it can see my windows pc's name, but it cannot browse files. :(

This howto is for setting up a Samba server. This means that following this tutorial will only allow Ubuntu to share files to Windows. If you want to access files that are shared from Windows, you can try the 6th link in my sig, after which, you should be able to access your Windows shares via Places > Network

---

### Post by lisati on 2009-08-01
> **bashirchacha said:**
> I am unable do that. Can you please explain more.

I'm not sure what you mean. Dmzier suggested reading this site: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) and then using Places->Network (within Ubuntu) to access the files on your Windows system.
Did you have trouble going to the link, or do you have a problem with one of the instructions there?

---

### Post by Iceman_B on 2009-08-02
> **dmizer said:**
> You need to add the netbios name option, as described in the first page of this tutorial.

```
[global]
        workgroup = ZION
        [COLOR="Red"]netbios name = name-of-your-computer[/COLOR]
(...)

```

Excuse the huge quote.
I did exactly this, but it doesn't work.
In Windows I only mapped a network drive, I did not set a WINS server. Should I?
Or is there some additional setting to accomplish what I want?

---

### Post by dmizer on 2009-08-03
> **Iceman_B said:**
> Excuse the huge quote.
I did exactly this, but it doesn't work.
In Windows I only mapped a network drive, I did not set a WINS server. Should I?
Or is there some additional setting to accomplish what I want?
No need to play with the WINS server settings.

Please post the output of:
```
smbtree
```

---

### Post by Iceman_B on 2009-08-09
@dmizer:
```
ZION
        \\SEBATIAAN_DESKT
        \\SEBASTIAAN-LAPT
        \\RIN-CHAN                      Rin-chan (Running Samba on Ubuntu)
                \\RIN-CHAN\print$               Printer Drivers
                \\RIN-CHAN\SecretzBeHere        Ravi's Digital Media Vault!
                \\RIN-CHAN\INCOMPLETE           Incomplete files! Use at own risk!
                \\RIN-CHAN\IRC_Downloads        Files downloaded over IRC. May contain incompletes.
                \\RIN-CHAN\IPC$                 IPC Service (Rin-chan (Running Samba on Ubuntu))
        \\FATE-CHAN
                \\FATE-CHAN\C$                  Default share
                \\FATE-CHAN\ADMIN$              Remote Admin
                \\FATE-CHAN\Downloadz           Ravi's D Downloads
                \\FATE-CHAN\Laptop Shared Docs  Shared documents from Ravi's laptop
                \\FATE-CHAN\D$                  Default share
                \\FATE-CHAN\IPC$                Remote IPC
                \\FATE-CHAN\E$                  Default share
```

Rin-chan is my server, Fate-chan is my laptop. The others are from housemates.
This is via Putty.

---

### Post by dmizer on 2009-08-09
Okay, also post your current /etc/samba/smb.conf file.

---

### Post by philetus on 2009-08-12
About 6 months ago I set up file sharing between Ubuntu and windows and set up Synergy to control both computers.

I never once had to add a smb password.
I wish I could remember how, but I'm getting older and only have about 3 brain cells left.

I do remember I used a couple very good tutorials and I can't find them any more either.

Was it simpler to do this in Jaunty?

---

### Post by kokeroulis on 2009-08-13
Thanks you for your tutorial.It works great unless one thing.I have to change the 2 last lines from

```
force user = kokeroulis
force group = YOUR_USERGROUP
```

to 

```
;force user = kokeroulis
;force group = YOUR_USERGROUP
```

---

### Post by Steve H on 2009-08-15
Thanks for that Stormbringer. With that little guide I've managed to create quite a nice little SAMBA share for my Wii to get to my media files. Works a treat. Saved me a lot of hassle, thanks again fella.

:P

---

### Post by timeapr on 2009-08-16
Thanks, I've confirmed I've configured it ok however Samba doesn't start when I boot my machine, issue the start cmd and all is fine. Bit of a pain but better than going to the loft with a USB Stick!

---

### Post by Iceman_B on 2009-08-16
> **dmizer said:**
> Okay, also post your current /etc/samba/smb.conf file.

[http://paste.ubuntu.com/254323/](http://paste.ubuntu.com/254323/)

---

### Post by k4kelly on 2009-08-22
Stormbringer you did a nice job on this tutorial, but so far I've not been able to get my network working right. I made several mistake in setting things up and there a couple of items I not clear on.  It would be nice if you would move the WARNING message about not using your primary home directory ahead of where you show it being used. i have ubuntu loaded on 240GB hard drive partition with 10GB swap, 120GB ext 3, and 110GB xfs for video storage. When I looked in xfs (103.8 GB Media) there were 58 files in the root directory evidently MythTV backend installed there. Since I had a lot of free disk space it seeded like a good idea to put it in the home directory. I did a change mode on home to do this. Now I get a little message block when I boot that I should change the user to user and the mode to 644 on home directory. When I do this I can not access home on any thing in the home folder so I changed it back to 755.  I did a ls -l befor I made the change but it didn't show the setting for home. 

1/  What are the correct setting for home and do I need to do anything else to fix this other than reload which i had to do about a dozen time trying to get the nvida drivers
working.  I finally got them working a week ago and started working on getting my network going.

2/ I see nothing in the tutorial about setting file sharing by right clicking on the file and selecting share and or propeties in the computer window. I having problems with this I change the "Allow other people to write in this folder" option to on and when I go back and look they are changed back. Do these option need to be on to write to a file. If so what do I need to do keep them on. If I use the terminal program to list the bits drwxrwxrwx. ( I created a new folder on the XFS partition name share for storage that is what I'm looking at.)

3/ I had a hard time figuring out how to access the partition from the terminal. I located it in /home/disk. When I looked in the Computer file browser the name is "103.8 GB Media" which is what i looked for. In the terminal the name is disk and the name doesn't show up until I open it first in the file browser. Is this partition not mounted until I click on it and would this cause the network not to see it. 

4/ When you right click a directory icon and select properties there is a group selection. User name is what is selected. What is the sambashare and how is it used?


I kind of hate to  reload agin. I had so much trouble getting the Nividia drivers working. i know what to do now and don't think it would be a problem but then I didn't think it would be a problem getting to ubuntu computer networking either. I'm trying to get back to where I starded and only use what you have in your totorial. I see a new icon today when i open the network window. "glenda's public files on glenda-desktop" When I click on it I get a error message "DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)" but in the places menue on the left side of the file browse a new folder with the same name has appeared. I click on it and all the files in Glenda's public directory pop right up. In her smb.conf there is section [Documents] and a path to the Documents directory which has the public folder in it and a couple of other folders which are selected to share but don't show up. After I get all this back to a good starting point if I still have a problem I will post all the files etcs.

---

### Post by doogiekd on 2009-08-27
First, 

Thanks for this how-to. It worked perfectly and now I can watch movies in the bedroom.

Just to clarify for anyone who like me, has an external hard drive and wants to share all of the hard drive:

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.


just type:

path = /media/<name of your hard external hard drive>

Thanks again, 

doogiekd

---

### Post by mookiemu on 2009-08-30
awesome howto! thanks a million!

---

### Post by hellblayzer on 2009-08-30
Im having problems accessing the shared folder from linux in windows. I can see the system fine in the network "browser" in windows, but when i try to access it is says "\\"folder" is not accessible. You might not have permission to use this network resource. etc". Can any help me figure out how to fix this? ive been searching forums and googling the problem for around 2 hours and cant find anything that has worked :( below is my smb.conf file

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = yes


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

Many thanks for any help that anyone gives :)

---

### Post by fish-hawk on 2009-09-17
Thanks a million for this!! Worked like a charm. Tried 2 time prior to configure smb shares, no luck and a lot of hours lost. Great walk through!

---

### Post by metalcoat on 2009-09-18
Also a new add for karmic users, samba4 will directly affect your shares.  Do not install unless it is really needed.  I had it installed and samba wouldn't work at all. Uninstalled and restarted bam! instant gratification:P

---

### Post by lyeberry on 2009-09-19
thanks for the guide, now I can sync my music to my zune on my windows guest.

---

### Post by Roasted on 2009-09-20
> **metalcoat said:**
> Also a new add for karmic users, samba4 will directly affect your shares.  Do not install unless it is really needed.  I had it installed and samba wouldn't work at all. Uninstalled and restarted bam! instant gratification:P

There's not a patch for this?

---

### Post by sparker1 on 2009-09-22
A big thankyou to Stormbringer and others here. You have no idea the trouble I was having trying to set up browsing between XP and Ubuntu. I was at the point of going back to Microsoft entirely. That hurdle is over now thanks to the information in here.

---

### Post by mahela007 on 2009-10-04
I've already configured samba to run with one windows laptop. However, I just bought a new (windows)  computer and I can't see the samba shares in the new computer. What should I do?

---

### Post by KIAaze on 2009-10-05
I don't have a lot of experience with this, but maybe you just need to change its workgroup to the one you defined in /etc/samba/smb.conf?
Also, check the firewalls.

---

### Post by kevinguillorytraining on 2009-10-09
I came from google search. My problem resolved after reading your how-to.

---

### Post by Dafong on 2009-10-10
Yep got me thru the whole viewing files on Windows issue to.

Also worked with Win Vista x64 Ultimate even though there was some common sense involved.

Thanks very much for the guide.

---

### Post by Bigtall1 on 2009-10-21
Thank you for this stormbringer, using your guide I managed to set up samba no probs, and having never used it before I am very impressed!
Thanks again

---

### Post by rymonroe on 2009-10-30
Great HOWTO. Very helpful! I have followed this howto and I am now able to access the files in my ubuntu computer from my vista computer. I can not however access files in my vista computer from my unbuntu computer. When I try to access my vista computer from my unbuntu (Places/Network), I see nothing as if nothing was being shared on my vista computer. I have disabled all firewalls on my vista computer. Any help would be greatly appreciated.

---

### Post by vigdavies on 2009-11-01
I did everything to my smb file that I read. I have it working except I cannot see it from my Windows computer. My samba server cannot even see the files on my Windows computer either. I both machines can ping each other, and the workgroup name is the same as each other. I see on my Windows machine that the netBIOS over Tcpip is disabled. 

What do I need to do to have active networking for my two home machines now ?

Help please.

---

### Post by WannabeFantasma on 2009-11-04
Damn for this, vista is a pain in the *ss :( 

xp worked in 2 mins (just to test) and vista after 1 week... still nothing :(

I'll mess with it till it works though.... Hope it'll be soon because i'm about to lose my mind :(

---

### Post by TheTank on 2009-11-04
Dunno if it was mentioned but you can also have the hostname auto-inserted like this
```

server string = %h server

```
At least it works for that entry.

---

### Post by raydowe on 2009-11-07
Just wanted to say to the author, THANK YOU!

Have had troubles with Samba since my first experience with Linux. After reading this, it works perfectly! Short, sweet, and easy to follow.

Thanks again.

---

### Post by Fcampo on 2009-11-18
Thank you very much, i tougth that went easier, but you did an excellent step by step. i'm happy enougth, i had configured it, with your guide.

:D

---

### Post by churfsan on 2009-11-20
Hi,

The tutorial is excellent and I was able to get it right (one of the few times !!) straightaway. Thank you very much Stormbringer!!

In one issue, I am facing a problem. I wanted to share the DVD drive, hence I enabled the section in sharing the drive:

**********
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes
***********

I am using Ubuntu 9.10

When I access the machine from a remote machine, I am able to see the DVD drive, however, unable to see any contents in it.

Whenever I insert a CD or DVD, Ubuntu is creating a new mount in /media/XXX, where XXX is the label of the CD or DVD inserted. Hence, even locally there is nothing in /media/cdrom.

In my fstab, the entry is as follows:

/dev/scd1  /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0  0

I want to be able to access my inserted CD / DVD from remote machine. Please help me.

Thank you very much

Churfsan

---

### Post by killr0y on 2009-11-20
how do i get samba to auto mount the 4 hard drives i have on the box for storage, when it reboots. samba starts, but the drives don't remount.

---

### Post by anewman on 2009-11-21
I have the same issue as churfsan. For now the only way is to insert the DVD, then set the share options for that DVD label's directory.

Ok what I did was..... (not knowing what to do and being aware the chance of a post detailing how to do it properly was unlikely)

sudo nautilus
Right clicked media folder then sharing options, ticked share folder and allow others to create and delete files in this folder. Nautilus gave a prompt about permissions and I clicked to modify them.

Gives access to all the media on my desktop which I'm not sure is a good idea security wise, but the wireless has WPA2, a password is required for the user group, and data sent via samba is encrypted I think - so I figure security should be reasonably good?!

---

### Post by jcanz on 2009-11-23
[B]Re: HOWTO: Setup Samba peer-to-peer with Windows

Thanks for the clear and detailed guide. I am pretty new at this and this should prove very usefull. Thanks again
[/B]

---

### Post by wavery on 2009-11-23
Is the initial post to this thread still applicable for 9.10 and Windows 7?  Just wondering if I should start there or if there is an updated post buried somewhere in here.

---

### Post by wavery on 2009-11-23
Newb working through this tutorial so bear with me please.  I'm stuck at the beginning because I'm being told I don't have permission to modify/move/delete the smb.conf file.  I'm using the 'sudo' command to access through the terminal and I'm logged in as the administrator.  Is this something different in 9.10, or am I missing something obvious?  Thank you.

Nevermind...got it.

---

### Post by jamesisin on 2009-11-28
Care to take a crack at my Samba problem in 9.10?

[http://ubuntuforums.org/showthread.php?t=1335774](http://ubuntuforums.org/showthread.php?t=1335774)

---

### Post by WordConjurer on 2009-12-05
Thank you for this how-to because my XP can now access my Ubuntu files. However, I still cannot access the XP from the Ubuntu, and I'm starting to believe I only needed smbfs instead.

I'm so lost and I'm not sure how much more time I can spend trying to connect my laptop to my computer. 

Please let me know if you can help!

---

### Post by luvr on 2009-12-15
> **churfsan said:**
> I wanted to share the DVD drive, hence I enabled the section in sharing the drive:

**********
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes
***********
and:
> In my fstab, the entry is as follows:

/dev/scd1  /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0  0
I'm not sure this would work, but could you try with
```
    path = /media/cdrom**0**
```
in the *"DVD-ROM Drive"* section? (Note the **0** that I appended to the path--to bring it in line with the mount point as specified in fstab.)

---

### Post by crx686 on 2010-01-01
HI

 Thanks for your how to. It was very easy to understand.  I have a couple different problems I'm trying to get working. I Have a network hard-drive that is in a enclosure its not in a computer.It has its own network card. Its a NexStar LX. It has a SMB server running on it. All my windows machine can access it and run files and music from it. But when you use a Ubuntu machine it only can browse the folders it can't execute it from the drive you have to copy it to the Ubuntu machine and run it from there same as music to. I'm wondering how can I run files and play music from that network drive without copying it to my desktop? I know its a permission thing i think. I followed your how to guide and I still can't get it to work. I've tried so many things and nothing is working. the other problems I have is when i go to place then network then click on windows network i get a error "Failed to retrieve share list from server". Thanks for all your help. Have a great new year

---

### Post by majikhotline on 2010-01-01
This is the only guide that I have been successful with....and it took me months to finally get it right! I have networked linux ubuntu and windows 7 together. Thanks Stormbringer!

---

### Post by dmizer on 2010-01-02
> **crx686 said:**
> HI

 Thanks for your how to. It was very easy to understand.  I have a couple different problems I'm trying to get working. I Have a network hard-drive that is in a enclosure its not in a computer.It has its own network card. Its a NexStar LX. It has a SMB server running on it. All my windows machine can access it and run files and music from it. But when you use a Ubuntu machine it only can browse the folders it can't execute it from the drive you have to copy it to the Ubuntu machine and run it from there same as music to. I'm wondering how can I run files and play music from that network drive without copying it to my desktop? I know its a permission thing i think. I followed your how to guide and I still can't get it to work. I've tried so many things and nothing is working. the other problems I have is when i go to place then network then click on windows network i get a error "Failed to retrieve share list from server". Thanks for all your help. Have a great new year

Please see the 6th link in my sig.

---

### Post by Mongao on 2010-01-04
Hi all,

When installing Ubuntu, I created the /home drive in a separate partition, but actually I don`t use it, as the folders that I want to share are all on the media drives, called /media/data_a; media/data_b; etc (actually these are NTFS partitions so Windows can see them as well).

I have a doubt about this part here:

[MyFiles]
    path = /media/samba/


So, as far as I understand, my line should be only:

[MyFiles]
    path = /media/

But if I do this, things DON`T work.

If I do this:

[MyFiles]
    path = /home/samba/

Things work ! It shouldn`t work, but it works. I haven`t saved nor shared anything in the "home" partition, so how is it possible that it works ?

I am not satisfied, I`d like to understand.

Thanks so much,
Mongao

---

### Post by rimshot4 on 2010-01-04
This excellent guide fixed my problem! I only wish I had found it on my first day of fiddling with my network instead of the fourth. Thanks!

---

### Post by finlost on 2010-01-30
> Problem solved.  [Dmizer expanded on the usernames]("http://ubuntuforums.org/showpost.php?p=6941704&postcount=785") and I realized I had botched mine.  After a reboot of each machine to clear things, I was able to access my USB HDD from my Vista machine.

I am stumped. Networking has always been a struggle for me.  I have followed the instructions as posted on the initial page of this topic and did quite a bit of searching.

My desktop is running 9.10 and my laptop is running Vista Home Premo.  I have a USB HDD connected to my 9.10 desktop that I want to access from my Vista laptop.  I am able to map to the USB HDD from my Vista laptop.  I am able to pull up the properties of the USB HDD from my Vista laptop.  I am unable to do anything else as in access the files on the USB HDD from my Vista laptop. I am guessing I forgot to dot an "i" or cross a "t" somewhere.  I setup a static IP address for my 9.10 desktop.

This is my smb.conf file. 
```
[global]
    ; General server settings
    netbios name = KARMICKOALA
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/FreeAgent Drive
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = dave
    force group = dave
```

 What other information, if any, is pertinent to get this resolved?

---

### Post by mactabiliz on 2010-02-22
For those of you having problems with network paths not being found on windows make sure that if you select a home folder you don't use a tilde (~) to represent the absolute path of your home folder rather use /home/username/

---

### Post by Jose Catre-Vandis on 2010-02-23
I have a problem. Followed the howto quite a while ago and have been recommending it to everyone! Works well for my XP machines and Ubuntu boxes. 

However, just got a new PC with Windows 7 Home Premium installed. Am able to map a network drive just fine, and access - read write files on the server. But for large file transfers, or when trying to watch a video over the share, at some point Windows 7 will crash (BSOD!) 

Having googled I checked that "security = user" (it does) and added a registry entry for LmCompatibilityLevel=2. But still crashing.

What I haven't done yet is set up the 7 PC for wins (the last part of the howto) - I'll try this later today when I get home.

Anyone else experienced this problem / found a solution?

---

### Post by dmizer on 2010-02-23
> **Jose Catre-Vandis said:**
> I have a problem. Followed the howto quite a while ago and have been recommending it to everyone! Works well for my XP machines and Ubuntu boxes. 

However, just got a new PC with Windows 7 Home Premium installed. Am able to map a network drive just fine, and access - read write files on the server. But for large file transfers, or when trying to watch a video over the share, at some point Windows 7 will crash (BSOD!) 

Having googled I checked that "security = user" (it does) and added a registry entry for LmCompatibilityLevel=2. But still crashing.

What I haven't done yet is set up the 7 PC for wins (the last part of the howto) - I'll try this later today when I get home.

Anyone else experienced this problem / found a solution?
That's a new, and scary one.

Might consider taking a look at the Win7 specific information located in the 6th link in my sig.

Also, please post your current smb.conf file as well as important text in the BSOD error.

Edit:
Are you using Norton 360, or the Beta release of Win7? Does disabling or uninstalling your antivirus alleviate the issue?

Edit II:
More information here -> [http://blog.tombushby.com/2009/02/02/windows-7-the-good-the-bad-and-the-tdxsys-bsod-resolved/](http://blog.tombushby.com/2009/02/02/windows-7-the-good-the-bad-and-the-tdxsys-bsod-resolved/)

---

### Post by Jose Catre-Vandis on 2010-02-23
Thanks dmizer, that blog entry is a good find, and may explain why when running W7 RC I had no problems with the samba share as I had not installed any anti virus. I had a good read through your 6th sig entry, but couldn't see anything that related specifically (you may say otherwise!) but will run through it again.

This is an OEM W7 Home Premium release (not a beta). I have AVG free on my system, so it looks like that has to go as only paid versions are W7 certified (grrr). Lets see how we get on tonight :)

---

### Post by dmizer on 2010-02-23
> **Jose Catre-Vandis said:**
> Lets see how we get on tonight :)

I'll keep an eye out for your results, as I'm also using AVG free. Good luck.

---

### Post by Jose Catre-Vandis on 2010-02-23
Well, I am not going to commit to success just yet, but after a few changes (that I should have made in the first place!) I have been unable to crash W7 :)

I finished off the last part of the howto by adding the IP info to WINS.

I changed the workgroup in W7 to match the workgroup being issued by samba on the server

I had already got rid of Windows Live ID Sign In (well ,couldn't find it to uninstall)

Applied all settings as in your 6th entry in your sig, dmizer (even though these were, as I understood for sharing from W7 not to.

Some Windows updates came down too

Rebooted.

Now previously I was having to mount the network drive, nothing was showing under network, but now my server was showing up, and listing the shares available. :)

Tried everything to crash it, watching videos, transferring big files, etc. No problems, and this was with AVG Free remaining as is, untouched.

I did find elsewhere that you can disable "Link Scanner" in AVG, which appears to be the cuplrit, or there is a registry entry to completely disable AVG - see [here]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1133218.html").

So for the moment all is well. I don't spend a lot of time in W7, but will do more testing and report back. Thanks for help and pointers. :)

Edit: That's three hours of solid testing now :)

---

### Post by dmizer on 2010-02-23
> **Jose Catre-Vandis said:**
> [snip]
So for the moment all is well. I don't spend a lot of time in W7, but will do more testing and report back. Thanks for help and pointers. :)

Edit: That's three hours of solid testing now :)

That's fantastic. Glad it seems to be working fine now. That sounds like a serious one. I might suggest you post a formal howto for repairing it, as it seems there are a lot of people on the net who are experiencing the problem but are either running sans virus protection or don't know how to fix it at all.

Thanks for the update!

---

### Post by jpolcari on 2010-02-24
Where is part 2 about setting up a PDC?

---

### Post by Amablue on 2010-02-26
I followed the guide and have everything just about set up, but I 'm running into trouble right at the very end. When I try to log on from windows it doesn't work. The username and password prompt just pop up again as soon as I hit enter. 

My Ubuntu computer's username is alex while on Windows it's Alex, I don't know if that matters or not, but I know that linux is typically case sensitive. I added a user for both just in case (I figured it couldn't hurt) and gave them both the same password (which is the same one used on Ubuntu and Windows). 

When I use smbclient from the linux computer I get this output

```
sudo smbclient -L LINUXBOX -U Alex -W WORKGROUP
Enter Alex's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service ()
	MyFiles         Disk      
	print$          Disk      
	Deskjet-F4200-series Printer   HP Deskjet F4200 series
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	LINUXBOX             
	SHIGERU              

	Workgroup            Master
	---------            -------
	WORKGROUP            LINUXBOX

```

However, like I said, it doesn't seem to want to cooperate with my other computer. I tried googling for help but there's just too much to sift though. I apologize if this has already been asked, but the thread is about 80 pages more than I'm able to parse in any kind of timely manner. 

Thanks in advance for the help

---

### Post by Jose Catre-Vandis on 2010-03-09
> **dmizer said:**
> That's fantastic. Glad it seems to be working fine now. That sounds like a serious one. I might suggest you post a formal howto for repairing it, as it seems there are a lot of people on the net who are experiencing the problem but are either running sans virus protection or don't know how to fix it at all.

Thanks for the update!

Found another tip that may help to solve Windows 7 crashes when accessing samba shares, but its a bit of a workaround and only good if you have one samba server running.

Edit your **smb.conf** and change the **netbios name** to the name of your **workgroup**. So if

```
workgroup = MYHOME

then:

netbios name = MYHOME
```

This certainly worked for some people, and is so far working for me, along with the other adjustments above

---

### Post by ojobson on 2010-03-14
Nice thread on setting up SAMBA - very useful, however I have issues with the read speeds from my samba shares - they are very slow!

I have Ubuntu 9.10 installed with gigabit ethernet - the clients used are a MacBook Pro (2009 5,5) and a Win 7 Pentium D machine.

Writing to the samba share on the server is around 35 to 50 MBps depending on the client. Reading from the server using samba is about 7 MBps on both the Win and OS X clients.

This read speed is a marked contrast to the appletalk (netatalk) share on the ubuntu server - this achieves around 40MBps when read from the MBP - so the hardware can handle it. The Win/MBP can both talk over samba at about 45 MBps in either direction.

I have used all the various SO_RCVBUF=XXXXX, SO_SNDBUF=XXXXX, TCP_NODELAY etc and tweaked the mtu to 7200. I have tried a smb.conf almost identicle to the one at the start of this thread but no matter what I can't seem to shift the speed higher.

Any thoughts?

---

### Post by nickthegreekk on 2010-03-16
Hello every one 

I have only one question and i can't find a solution.

I have managed to configure a box with ubuntu server that serves my home page , vsftpd for ftp and transmission-daemon to get some files from here and there...
I use samba to share the files among the local network which has attached a few m$ boxes and some Macs.Till this point everything works great , samba is set to allow guests and everybody is happy.The dark side is that the router is attached to the modem as well and i can access the shares from the Internet as well, which in my case is a pretty bad senario...

To the point now if I cut the ports with iptables the server ( naturally ) hides from the local network as well...so no internet access and no access at all.
I am open to suggestions... :D

Thanks.

---

### Post by dmizer on 2010-03-17
> **nickthegreekk said:**
> Hello every one 

I have only one question and i can't find a solution.

I have managed to configure a box with ubuntu server that serves my home page , vsftpd for ftp and transmission-daemon to get some files from here and there...
I use samba to share the files among the local network which has attached a few m$ boxes and some Macs.Till this point everything works great , samba is set to allow guests and everybody is happy.The dark side is that the router is attached to the modem as well and i can access the shares from the Internet as well, which in my case is a pretty bad senario...

To the point now if I cut the ports with iptables the server ( naturally ) hides from the local network as well...so no internet access and no access at all.
I am open to suggestions... :D

Thanks.

You need to look at the configuration of your router, not the samba server. You should also disable samba until you get the problem solved.

---

### Post by nickthegreekk on 2010-03-17
> **dmizer said:**
> You need to look at the configuration of your router, not the samba server. You should also disable samba until you get the problem solved.

I got it working as it should now.
Blocking the samba port from the modem side did the job.
Thanks for the tip you are the man!

;)

---

### Post by tdietsche on 2010-03-18
THANK YOU! This post is great. I have been fighting samba for days trying to get my XP box to see the samba share. Ten minutes doing these steps and kazam! it works. 

Now let's mount a campaign to improve the official samba docs to have something this simple and helpful, instead of the hundreds of pages of accurate but mind-numbingly useless reference info they currently have. Typical of a lot of open source projects I am afraid, they all seem to have a bias against useful docs for beginners.

---

### Post by Caldur06 on 2010-03-18
I'm still having problems with this. My setup is Windows 7 with ubuntu 9.10 running in VMWare. Both are brand new installs. In addition, I'm on a university campus, and when I want to map a drive on Windows it's making me go through the university's domain, which uses ntlmv2 encryption. The error I'm getting is:

The mapped network drive could not be created because the following error has occurred:

The specified network name is no longer available.

I setup a user on ubuntu that matches my university (and therefore what I login to Windows as) login and password.

My smb.conf:

```
[global]
    ; General server settings
    netbios name = sweet-ubuntu
    server string =
    workgroup = SGF
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    ;wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[SharedFiles]
    path = /home/kevin/SharedFiles
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    valid users = kds45
    ;force user = kds45
    ;force group = kds45
```

I'm trying to get SharedFiles to work. Some settings in the file probably aren't exactly how they are on the tutorial. The reason is that I followed the tutorial, it didn't work, and I've been playing around with it for hours trying to get it to work.

I've restarted samba plenty of times, so that isn't it.

Also, I do know that it's finding my ubuntu server, because when I try to map the drive in windows, it gives the error above if I put "\\sweet-ubuntu\SharedFiles" or "\\192.168.11.130\SharedFiles". However, if I put something incorrect: "\\blah\SharedFiles" it does something different, namely, takes forever and gives a different error.

Any ideas or things to try? Any help is much appreciated! Thank you!

---

### Post by alawson on 2010-03-21
Hi,

I'm having a lot of trouble connecting from a Windows 7 Ultimate workstation to a SMB share advertised from a Ubuntu 9.10 box with Samba 3.4.0. I have other Windows clients (XP) able to connect but the Win7 box won't authenticate. I can see the server name in the Network section of Windows Explorer, so Win7 is able to find the Samba server, but when I click on it, I get a dialog prompting for username and password and indicating that a previous attempt has failed.

I see the following in /etc/log/samba/log.*[HOSTNAME]* every time the Win7 box attempts to auth;

```
[*[TIMESTAMP]*,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

Because XP clients are ok, I reckon the problem must be with the Win7 box. I've tried making the regedits and changing the Win7 security settings in Control Panel/Admin tools/Local Security Policy as mentioned in this article. Anything else I should be trying?

Apologies if this is already covered - I've just spent a fruitless hour searching the forums..... Thanks for any assistance.

Cheers,
Andy.

---

### Post by Adrian_b on 2010-03-25
Hot dang. I've been trying to set up a samba share in xubuntu 10.04 the past two days but failed. This guide brought me to it in ten minutes!

---

### Post by paulcaughell on 2010-03-28
I followed the instructions in the first post and for the most part, samba seems to be working.  The problem I'm having is connecting to a share on my windows XP home machine from my ubuntu 10.04 machine.  I keep getting prompted for a password, when no passwords are set on the windows machine.  Occasionally, it works without putting in a password, I can't figure out why.

---

### Post by thedp on 2010-03-29
Thanks for posting. Simple and to the point.

---

### Post by AgungX on 2010-04-02
:P thx for share...

---

### Post by Silvertones on 2010-04-09
I have a wireless peer to peer network setup per this HOW TO . On the Windows XP machine I have mapped the Shared folder  on the Ubuntu machine as a drive. So far so good. The weird part is if  when I first start up my computers once the cards have connected if I  try to access the Ubuntu machine first from Windows I get an error. If I  try to access the Windows machine from  Ubuntu it connects fine. I can  then go to the Windows machine click on the mapped drive, enter the  password and all is fine.
Why do I have to access the Windows machine  first?

---

### Post by IndyGunFreak on 2010-04-10
Has anyone used the instructions in Post #1, on 10.04?  It worked perfectly on 9.10, and frankly, I can't see why it doesn't work on 10.04.

```
ken@ubuntu:~$ sudo /etc/init.d/samba stop
sudo: /etc/init/samba: command not found
ken@ubuntu:~$ 

```

I get the same error when running start or stop, so I'm assuming it's been moved somewhere...?

---

### Post by lisati on 2010-04-10
> **IndyGUnFreak said:**
> Has anyone used the instructions in Post #1, on 10.04?  It worked perfectly on 9.10, and frankly, I can't see why it doesn't work on 10.04.

```
ken@ubuntu:~$ sudo /etc/[COLOR="Red"]init.d[/COLOR]/samba stop
sudo: /etc/[COLOR="Red"]init[/COLOR]/samba: command not found
ken@ubuntu:~$ 

```

I get the same error when running start or stop, so I'm assuming it's been moved somewhere...?

Hmmmm..... init.d being interpreted as init? Maybe a clue. I'm running 9.04 at the moment, so I'm unable to check.

---

### Post by IndyGunFreak on 2010-04-10
> **lisati said:**
> Hmmmm..... init.d being interpreted as init? Maybe a clue. I'm running 9.04 at the moment, so I'm unable to check.

Hmm, somehow that ".d" fell off in the copy paste.  I just ran the command, and its definitely "init.d" that isn't found...

IGF

---

### Post by luvr on 2010-04-11
> **IndyGUnFreak said:**
> I get the same error when running start or stop, so I'm assuming it's been moved somewhere...?

In that case, I would take a look at the properties of the **samba** package: Start Synaptic (*"System"* -> *"Administration"* -> *"Synaptic Package Manager"*), find the **samba** package in the list of packages, right-click, and select *"Properties."* Display the *"Installed Files"* tab, and see if you can find the *"samba"* file that you're looking for.

---

### Post by DBrocks on 2010-04-11
Try running

```
sudo /etc/init.d/smbd restart
```

Looks like samba moved to smbd... (On my 10.04 server at least)... weird.

---

### Post by Silvertones on 2010-04-12
I figured it out. Sort of a dumb thing on my part. I uninstalled my WUBI install a few weeks back and did a side by  side install. I of course had to set my network back up. In haste I type the rules to allow the Windows machine to access the Ubuntu machine backwards in UFW so effectively was still blocking until I would initiat contact from the Ubuntu machine. It's working fine now.

---

### Post by peterv6 on 2010-04-14
Dear Stormbringer, I'm hoping you can help me out.  I followed your guide to set up Samba, but it was only partially successful.  I can access files on my Ubuntu 9.10 machine from my Windows XP Pro machines, but I can't access any Windows XP machines from the Ubuntu machine.  I'm a rookie with Samba, so I probably missed something.  Do I have to set anything up on the Windows machines so that the Ubuntu machine can access them?  I've been working on this for days, and it's starting to get a little blurry, if you know what I mean.
Thanks,
Peter V.

---

### Post by luvr on 2010-04-14
> **peterv6 said:**
> I can't access any Windows XP machines from the Ubuntu machine.
How exactly do you try to access the XP machines from Ubuntu?
And what exactly happens--e.g., what error messages do you get?

---

### Post by peterv6 on 2010-04-14
I go click on places -> network -> Windows network.

Once there, I see 2 "workgroups".  One is my network workgroup named "HADEN". The other one is named "WORKGROUP", and I have no idea why that's there.  (I've changed it in my smb.conf file to HADEN.)

I click on the HADEN workgroup and I get this message:

Unable to mount location Failed to retrieve share list from server.

I've also tried the "connect to server" option in the places menu, but it doesn't list SMB as a server option.

Any help will be greatly appreciated.
Thanks for replying,
Peter V.

---

### Post by Morbius1 on 2010-04-14
Run the following commands from you Linux machine. It won't fix anything, it will simply output how your system sees the network. With any luck it will also output error messages that will help in the diagnosis:

**smbtree**
**findsmb**

---

### Post by peterv6 on 2010-04-14
I ran the commands, and here is the output:
```
peterv@MBP17.local<528>$: smbtree
Password: 
HADEN
	\\SERVER2        		
		\\SERVER2\J$             	Default share
		\\SERVER2\SERVER1 - J    	
		\\SERVER2\SERVER1 - I    	
		\\SERVER2\Printer        	Microsoft Office Document Image Writer
		\\SERVER2\SERVER2 - F    	
		\\SERVER2\SERVER2 - G    	
		\\SERVER2\C$             	Default share
		\\SERVER2\SERVER2 - E    	
		\\SERVER2\H$             	Default share
		\\SERVER2\ADMIN$         	Remote Admin
		\\SERVER2\Printer2       	Creates Adobe PDF
		\\SERVER2\SERVER1 - M    	
		\\SERVER2\F$             	Default share
		\\SERVER2\SERVER2 - C    	
		\\SERVER2\SERVER2 - D    	
		\\SERVER2\M$             	Default share
		\\SERVER2\G$             	Default share
		\\SERVER2\I$             	Default share
		\\SERVER2\SharedDocs     	
		\\SERVER2\print$         	Printer Drivers
		\\SERVER2\D$             	Default share
		\\SERVER2\IPC$           	Remote IPC
		\\SERVER2\Server1_Printer	HP OfficeJet K80
		\\SERVER2\SERVER1 - H    	
		\\SERVER2\E$             	Default share
	\\MBP17WIN       		MBP17win
		\\MBP17WIN\C$             	Default share
		\\MBP17WIN\ADMIN$         	Remote Admin
		\\MBP17WIN\MBPwinC        	
		\\MBP17WIN\IPC$           	Remote IPC
	\\MBP17          		
anonymous failed session setup with NT_STATUS_LOGON_FAILURE
	\\DELLP2         		
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to DELLP2<20> (63.251.179.13). Error NT_STATUS_CONNECTION_REFUSED

```

The last error on DELLP2 isn't a problem.  The problem is the MBP17, that's my MacBook Pro which is running the Samba server.  Any ideas?  SERVER2 is a Windows XP Pro machine, and MBP17WIN is Windows XP Pro running on the MacBook Pro in Parallels 5.0.

Findsmb output:
```
peterv@MBP17.local<530>$: findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.100   MBP17         +[	HADEN         ]

Wed Apr 14 17:05:05 EDT 2010 

```

Output from testparm:
```
Load smb config files from /private/etc/smb.conf
Processing section "[homes]"
Processing section "[Peter Vanderhaden's Public Folder]"
Processing section "[printers]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	dos charset = CP437
	display charset = UTF-8
	realm = LKDC:SHA1.152B9CC2A07F9F4031A937C6B17B1F45E1A2C93F
	server string = MBP17
	auth methods = odsam
	obey pam restrictions = Yes
	passdb backend = odsam
	lanman auth = No
	use kerberos keytab = Yes
	log level = 1
	debug pid = Yes
	max xmit = 131072
	name resolve order = lmhosts wins bcast host
	max smbd processes = 10
	printcap name = cups
	stat cache = No
	os level = 2
	preferred master = No
	domain master = No
	idmap domains = default
	idmap alloc backend = odsam
	idmap negative cache time = 5
	com.apple:show admin all volumes = yes
	com.apple:lkdc realm = LKDC:SHA1.152B9CC2A07F9F4031A937C6B17B1F45E1A2C93F
	com.apple:filter shares by access = yes
	darwin_streams:brlm = yes
	idmap config default:backend = odsam
	idmap config default:default = yes
	ea support = Yes
	stream support = Yes
	use sendfile = Yes
	mangled names = No
	include = /var/db/samba/smb.shares
	vfs objects = notify_kqueue, darwinacl, darwin_streams

[homes]
	comment = User Home Directories
	valid users = %S
	read only = No
	create mask = 0750
	browseable = No
	include = /var/db/smb.conf

[Peter Vanderhaden's Public Folder]
	comment = Peter Vanderhaden's Public Folder
	path = /Users/peterv/Public
	read only = No
	create mask = 0644
	guest ok = Yes

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

Wed Apr 14 17:05:05 EDT 2010 

```

The last strange part of this is when I go into network neighborhood, MBP17 (which is running the server) does show up.  When I click on it, I get a prompt to enter a userid and password.  I enter my userid and password from the MacBook Pro, and it doesn't accept the password.  Any ideas?

---

### Post by Morbius1 on 2010-04-14
I don't mean to speak for the author of this HowTo but I think this is beyond a "peer-to-peer with Windows" kind of discussion.

I kept looking at your smb.conf thinking to myself - this will never work. I'm embarrassed to admit how long it took me before I realized that was the smb.conf from your Mac server.

---

### Post by peterv6 on 2010-04-14
If that's the case, hopefully the thread author will let me know, because if that's so, I'll open this as a new post on it's own.  Thanks for your replies though.  The commands you showed me did help clarify where some of the issues are.

---

### Post by peterv6 on 2010-04-16
Finally figured this out.  The problem was that the workgroup name wasn't specified in the WINS tab in Network preferences in OS X.  Once that was added, the rest worked.

---

### Post by chipseller on 2010-04-16
This is an excellent guide, BUT I have two wireless laptops, one of which is my wifes (Vista home basic) and the other my work PC (Vista Business + CentOS5). I could print from my wifes pc but could not change the print settings - my work pc could not even find my main pc. After following this guide I could print from both machines, change print settings etc, but ubuntu seems to have disabled something so that neither pc now prints and when i try to connect i am asked for a username and password which, of course, does not work. have you any idea what has been disabled and how i can get back to a working system and sop ubuntu doing this again?

---

### Post by IndyGunFreak on 2010-04-18
> **DBrocks said:**
> Try running

```
sudo /etc/init.d/smbd restart
```

Looks like samba moved to smbd... (On my 10.04 server at least)... weird.

hmm, I tried this... and I get this and don't really understand what it means...

```
ken@ken-desktop:~$ sudo /etc/init.d/smbd restart
[sudo] password for ken: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart smbd
smbd start/running, process 1739
ken@ken-desktop:~$

```

Same message if I start, stop, or restart.. It looks like its telling me to use a "service utility" to start and stop samba, but I really don't understand what its saying...

Also, this is how I've been starting samba, and I get errors, but it seems to work after running start again...

```
ken@ken-desktop:~$ sudo /etc/init.d/samba4 start
 * Starting Samba 4 daemon samba                                                Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "printcap name"
Ignoring unknown parameter "printcap name"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "syslog only"
Ignoring unknown parameter "syslog only"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "write list"
Ignoring unknown parameter "write list"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
                                                                         [ OK ]
ken@ken-desktop:~$ sudo /etc/init.d/samba4 start
 * Starting Samba 4 daemon samba                                         [ OK ] 
ken@ken-desktop:~$ sudo /etc/init.d/samba4 stop
 * Stopping Samba 4 daemon samba                                         [ OK ] 
ken@ken-desktop:~$ 

```

Any help or suggestions anyone has, I'd be grateful.

---

### Post by peterv6 on 2010-04-18
It looks to me like you've got some syntax errors in your smb.conf file.  If you want to post a copy of it here, I'll take a look at it for you.
Peter V.

---

### Post by IndyGunFreak on 2010-04-18
> **peterv6 said:**
> It looks to me like you've got some syntax errors in your smb.conf file.  If you want to post a copy of it here, I'll take a look at it for you.
Peter V.

Thanks!  This is pretty much the same setup I used on 9.10, and it worked flawlessly... The "Zune" folder, is an NTFS partition that is separate from my /... I store all my files on that partition, and the Zune folder is obviously, to sync my zune.. :)

```
[global]
    ; General server settings
    netbios name = ken
    server string =
    workgroup = MSHome
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/0A334CDB50EF900C/Zune
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = ken
    force group = ken
```

---

### Post by IndyGunFreak on 2010-04-18
OK, had a few minutes to look at it again, and I think I have it solved.

I started my virtual OS, then on the Host, ran:

```
ken@ken-desktop:~$ sudo service smbd start
smbd start/running, process 2483
ken@ken-desktop:~$ 

```

and it allowed me access to my share on the Guest... then just to verify..
```
ken@ken-desktop:~$ sudo service smbd stop
smbd stop/waiting
ken@ken-desktop:~$ 

```

made the share inaccessible from my Guest OS... so while my smb.conf file may indeed have some errors as suggested above, but DBrocks in post #906 also helped a lot.

Thanks.

---

### Post by mfraser on 2010-04-23
> **DBrocks said:**
> Try running

```
sudo /etc/init.d/smbd restart
```

Looks like samba moved to smbd... (On my 10.04 server at least)... weird.

Also looks like they're now recommending you use

```
sudo service smbd restart
```

instead of

```
sudo /etc/init.d/smbd restart
```

---

### Post by peterv6 on 2010-04-23
Indy,
Sorry it took so long to get back.  I did look at the smb.conf, and I couldn't find anything blatently wrong either.
Peter V.

---

### Post by Stolea on 2010-04-30
I have been following Stormbringer's How-to set up networking since version 8.04. It has always worked a treat.
I have just installed 10.04 and followed the steps, but ```
sudo /etc/init.d/samba stop
```gets the reply ```
sudo: /etc/init.d/samba: command not found

```
Same for ```
sudo /etc/init.d/samba start
```

Has anything changed with samba under 10.04 or am I doing something wrong?

---

### Post by luvr on 2010-04-30
> **Stolea said:**
> Has anything changed with samba under 10.04 or am I doing something wrong?

Just [look back a few posts,]("http://ubuntuforums.org/showthread.php?p=9163211#post9163211") where **mfraser** states that the recommended way to restart the Samba server is now:
```
sudo service smbd restart
```

---

### Post by Stolea on 2010-04-30
Thanks for that I had started reading from the start and gave up somewhere aound page 50. Should have persisted :)
Does anyone have any idea why they would change a nice obvious command like "samba xxx" to something obscure like "smbd"?
Doesn't look like much of an improvement. :(

---

### Post by luvr on 2010-04-30
> **Stolea said:**
> Does anyone have any idea why they would change a nice obvious command like "samba xxx" to something obscure like "smbd"?
That's because **"smbd"** is the official name for the *"SaMBa Deamon."* Once you understand what the acronym stands for, it will certainly become far less obscure.

(Note also that *"deamon"* is the term used in Unix and similar systems for what Windows calls *"service."*)

---

### Post by Morbius1 on 2010-04-30
It's literally been years since I had to start samba with a smbd  daemon but isn't the "correct" way to restart samba this way:

sudo service smbd restart
sudo service nmbd restart

The previous "samba" daemon would start the two daemons in sequence. Now that they are separate again I think you need to restart both individually.

---

### Post by Stolea on 2010-04-30
???? What is "nmbd" ???

---

### Post by Morbius1 on 2010-05-01
> **Stolea said:**
> ???? What is "nmbd" ???

> nmbd - NetBIOS name server to provide NetBIOS over IP naming services to clientsAs I remember it, when Red Hat created the "samba" or "smb" "service" it combined the launching of the smbd and nmbd daemons in sequence. 

Just found this reference in the RHEL reference:
> **The nmbd daemon**

        The nmbd server daemon understands and replies to         NetBIOS name service requests such as those produced by SMB/CIFS in         Windows-based systems. These systems include Windows 95/98/ME,         Windows NT, Windows 2000, Windows XP, and LanManager clients.  It         also participates in the browsing protocols that make up the Windows         **Network Neighborhood** view. The default port         that the server listens to for NMB traffic is UDP port 137.       
[COLOR=Blue]         The nmbd daemon is controlled by the         smb service.       [/COLOR]
The "smb service" combined the smbd and nmbd daemons. Now that we're going back to the olden days I think we need to run both separately in sequence.

If you go back to jaunty and issue the following command you would get this result:

> sudo service samba status
 * nmbd is running
 * smbd is running

---

### Post by luvr on 2010-05-01
> **Stolea said:**
> ???? What is "nmbd" ???
If I understand correctly, the **"nmbd"** deamon is the NetBIOS name resolution service; whenever you want to connect to a Windows Networking server *(be it a Microsoft Windows machine, or a Samba server),* it will translate the NetBIOS server name into its IP address.

At least, that's my understanding, currently. I'm still trying to make sense of Windows Networking, and it is my goal to learn how to configure Samba in such a way that NetBIOS name resolution works flawlessly in a small home network (*without* a dedicated server machine)--just as it does between Windows machines.

---

### Post by Mongao on 2010-05-15
Hi all,

I have upgraded and my network stopped working; actually it was working only partially, the Ubuntu computer was seeing the Windows one, but the opposite was not true. Now none see either.

Please, regarding this part of the original code

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    

and considering the author`s comment:

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

Please, HOW MAY I FILL IN THE PATH considering that my shared folders are in media/HD_1 and NOT on the samba folder ?

Thanks,

Mongao

---

### Post by Eiríkr on 2010-05-15
Hello Mongao --

I'm afraid it's a bit unclear what your question is.  For the code here:

```
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
```
the [FONT="courier"]path[/FONT] entry is the path to whatever directory you're trying to share.  Simply replace [FONT="courier"]/media/samba/[/FONT] with whatever directory you're using.  

If you mean you don't know where to put any of this, please re-read Stormbringer's tutorial.  The code section I include above is part of the [FONT="Fixedsys"]smb.conf[/FONT] file used to configure your Samba server.  

If all of this is Greek to you, that's okay -- we all start somewhere! :D -- but it does mean that we're going to have to start this conversation from a different point altogether.  If you're confused, please let us know, as specifically as you can.  

Cheers,

-- Eiríkr

---

### Post by Mongao on 2010-05-15
> **Eiríkr said:**
> Hello Mongao --

I'm afraid it's a bit unclear what your question is.  For the code here:

```
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
```
the [FONT="courier"]path[/FONT] entry is the path to whatever directory you're trying to share.  Simply replace [FONT="courier"]/media/samba/[/FONT] with whatever directory you're using.  

If you mean you don't know where to put any of this, please re-read Stormbringer's tutorial.  The code section I include above is part of the [FONT="Fixedsys"]smb.conf[/FONT] file used to configure your Samba server.  

If all of this is Greek to you, that's okay -- we all start somewhere! :D -- but it does mean that we're going to have to start this conversation from a different point altogether.  If you're confused, please let us know, as specifically as you can.  

Cheers,

-- Eiríkr

Thanks Eirikr,

Yes, I`ve imagined that I have to replace the path according to the folder that I wanna share, in my case it would be:

path = /media/dados_1/

and it didn`t work, initially......weirdly, I simply DELETED everything that is under this "My Files" section and it started working again, even without doing any set up in Windows as advised.

Go figure....well, it`s working.

Thanks,
Mongao

---

### Post by Ladybird78 on 2010-05-28
Hi,
 I used Stormbringer's tutorial to set up a Samba share between a Linux machine ( Lucid Lynx) and a Windows XP machine.

At the beginning, I changed the path In [My Files] ( See Stormbringer's tutorial) as,
path = home/samba/
And I could see everything on /home/samba/ from the Windows machine.

Now I want to share an external hard disk mounted on the Linux machine (/media/MyBook) with the Windows machine.  
How can I achieve this without disrupting the connection I have already established via Samba  ( i.e. /home/samba) 

Will something like
[MyFiles2]
path =/media/MyBook/
.......
work?

Thanks
Ladybird78

---

### Post by Silvertones on 2010-05-28
You do this from the windows machine. My network places/add network place. browse to the external drive.You first need to set the sharing for this drive in ewindows as well. I suggest you only share certain folders.This will keep the rest safe.

---

### Post by Morbius1 on 2010-05-29
> **Ladybird78 said:**
> Now I want to share an external hard disk mounted on the Linux machine (/media/MyBook) with the Windows machine.  
How can I achieve this without disrupting the connection I have already established via Samba  ( i.e. /home/samba) 

Will something like
[MyFiles2]
path =/media/MyBook/
.......
work?

I take it you didn't like my answer to your other post on this subject. :)
( BTW you should have mentioned that you were already using Classic-shares because the answer I gave you was for Nautilus-shares )
You forced me to read this HowTo but if your original Classic-share is set up this way:
> [MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUPThen changing the path to /media/MyBook/ to create another share should work:
```
[MyFiles2]
[COLOR=Blue]     path = /media/MyBook/[/COLOR]
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```Just remember to restart samba.

Assuming the MyBook is formatted in NTFS, the key here is the "     force user = YOUR_USERNAME". The MyBook will automount with access only to "YOUR_USERNAME" so the "force user" will convert any remote user to you for that share. Also the "create mask" and  "directory mask" options in the share definition won't actually do anything because linux can't set permissions on a windows filesystem ( outside of a mount ) but it won't do any harm - it will just be ignored.

---

### Post by Silvertones on 2010-05-29
OOPS mis read the question. Like Morbius! said however you still have to set up the Win machine to see it.
Why not change that [my files] & [my files2] to something more meaningful to you?

---

### Post by manji_kun on 2010-05-31
you probably had this question before, but this doesn't seem to be the direct path for windows 7 (xp i think) how do you set all this up with 7?

---

### Post by Ladybird78 on 2010-05-31
Morbius1

Thank you for your reply, yes I forgot some info in my first post but, I tried the instructions provided on your second post but it didn't work. For the mount /media/MyBook I gave the same force user that I gave for /home/samba but it didn't work. Now I cannot even see stuff on /home/samba from my Windows machine :(

---

### Post by Morbius1 on 2010-06-01
From your Ubuntu machine post the output of the following commands please:
```
net usershare info
sudo net usershare info
testparm -s
```Creating a new share - even if it wasn't done correctly - shouldn't have disabled your old share.

---

### Post by Ladybird78 on 2010-06-01
Hello Morbius!,
Yes, the initial share is okay, I think for some time I couldnt see it on the network so I was worried. But now I can see my old share ( /home/samba) 
So when you say, create a new share that is a new username and a password is that correct?And I will have to put this new username as the "force user". Also is there anything that I need to do on my Windows machine?
 
Thanks again!

---

### Post by Morbius1 on 2010-06-01
> **Ladybird78 said:**
> Hello Morbius!,
Yes, the initial share is okay, I think for some time I couldnt see it on the network so I was worried. But now I can see my old share ( /home/samba) 
So when you say, create a new share that is a new username and a password is that correct?And I will have to put this new username as the "force user". Also is there anything that I need to do on my Windows machine?
 
Thanks again!
You don't want a new username and password. It has to be your local login username. The username you use to login to the box that has the external drive attached to it.

Again following the original tutorial, you should have two shares in smb.conf. The original one:
```
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP                      
```And the new one:
```
[MyFiles2]
    path = /media/MyBook/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```

---

### Post by iamsickofschool on 2010-06-02
Hey, this guide was awesome man. It helped me out so much more than anything I have read. A few things though. I don't know if this has been covered since I didn't read through the 95 pages of replies but the new version of samba got rid of the /etc/init.d/samba file. The thread I provided contains what they have changed it too. Besides needing the new file to turn samba on and off, it didn't mess anything else up in your guide.

[http://ubuntuforums.org/showthread.php?t=1439418](http://ubuntuforums.org/showthread.php?t=1439418)

I do have a question though, and again I don't know if this was covered previously but my Win7 computer sees my Linux computer with no problem after using your guide but Linux can't seem to find my Win7 computer. Do you have any advice?

---

### Post by r.fortunato6995 on 2010-06-07
thanks your tutorial, so far it is the best I have read. I finally was able to join my home network and I can access my files from a windows OS computer  however, I when I try to acess any windows computer from Linux, i get a message: "you can stop this by clicking stop" then in about 3 minutes, i get another message: "unable to mount location, failed to retreive share list from server" I may have an error on my parametters, but I am not an expert at this. here is what I have done so far:

[global]
    ; General server settings
    netbios name = RAMON
    
    workgroup = RAMONET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ramon
    force group = ramon
available = no
browsable = yes
public = no
writable = no


please let me know if what I have done wrong. thank you.

---

### Post by stig on 2010-06-09
This message "Unable to mount location, failed to retrieve share list from server" seems to crop up often in the forums and cause a lot of people trouble. Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1493834&page=2]("http://ubuntuforums.org/showthread.php?t=1493834&page=2")

The guy who posted the thread managed to solve his problem but it didn't cure mine. I added my information in the thread from page 2 but it probably got ignored because the thread was then labelled `Solved' on behalf of the original poster. I finally re-installed samba and that seemed to cure the main problem. It seems odd though that samba should corrupt on all my PCs at exactly the same time.

My network was set up using Stormbringer's guide and had been working flawlessly until this recent problem. Now I still get problems where one day all is well and every PC sees every other one and then days when one is OK but not another etc. There seems no rational basis to it. Does it matter the order in which the PCs are booted up? Does any one PC have priority over another? I'm using DHCP and I set up the network using samba originally because I had both windows and Ubuntu but for some years now I have had only Ubuntu. All PCs are still on 8.04 LTS.

---

### Post by ivan7777 on 2010-06-16
Hi guys,

Another noob here. I've followed the tutorial to the letter even copying the smb.conf and changing only the appropriate fields such as workgroup and the share names. 

however, on my windows 7 network the ubuntu server didn't show up but I can still access it by typing its ip address. 

Now, there is no problem doing normal stuff like copying, deleting files, etc but recently I tried to backup my windows 7 on to it but it failed all the time after a while. 

Just wondering what do I need to do to make it the server visible on the network window without typing the ip address. 

I'm using the latest ubuntu server. 

Regards, 

Ivan

---

### Post by Eina1 on 2010-06-26
I'm new to ubuntu and networks so all of this seems greeg, my first problem is that I get a bad flag error when I try to safe the getit file.  I've got 3 pc' 1 ubuntu 10.04, one with hardy heron (for the emc) and 1 laptop (win xp), I would like to enentually have them all on a network

---

### Post by Morbius1 on 2010-06-26
> **Eina1 said:**
> I'm new to ubuntu and networks so all of this seems greeg, my first problem is that I get a bad flag error when I try to safe the getit file.  I've got 3 pc' 1 ubuntu 10.04, one with hardy heron (for the emc) and 1 laptop (win xp), I would like to enentually have them all on a network
To answer your specific question, you need to open gedit this way:
```
gksu gedit /etc/samba/smb.conf
```You know, this HowTo is predicated on this observation:
>  Since the installation of samba just installed a rather useless template  file we're going to rename it - we keep the file just in case.That may very well have been true in 2006 and Ubuntu 6.06 when this was written but I would argue that it may not be true today.

---

### Post by Eina1 on 2010-06-26
error: line 53474: bad flag vector alias
error: line 53475: bad flag alias index: 0
error: line 53475: bad flag vector alias
error: line 53476: bad flag alias index: 0

desktop:~$ sudo /etc/init.d/samba start
sudo: /etc/init.d/samba: command not found


Just some of the lines I've copied.
I did get the file made and safed - i've found it trough the (windows)
but there's no samba in /etc/init.d.

---

### Post by Morbius1 on 2010-06-26
> desktop:~$ sudo /etc/init.d/samba start
sudo: /etc/init.d/samba: command not foundLike I said this HowTo is very old.

  There have been changes to how services are started and even the mechanism that's used to start them.

In Ubuntu 10.04 the way to start samba is:
```
sudo service smbd start.
```If it's already running and you want to restart it:
```
sudo service smbd restart
```

---

### Post by kmceng on 2010-06-26
I've done your sig6 samba config and STILL I can't get Dolphin to get past smb:/WORKGROUP/ without asking for authorization (user/password).

In Linux Mint Helena KDE4.2 it all works great.
'findsmb' works fine and sees our entire network. (small LAN about a dozen machines)

But in Sidux 2009-04(dual-boot on same machine) samba just won't cooperate. findsmb finds nothing! (nmblookup seems to NOT be installed, but I can't figure out why not) samba, smbclient, smbfs, winbind are all installed.

If I use the IP to one of our servers e.g. smb:/192.168.1.10/ I get all the directories and have complete access, no questions asked. But smb:/workgroup/ asks for authorization and won't let me in even with root/password of the server!

Any hints?

Keith C.

---

### Post by gabe17 on 2010-07-11
Hi! I wanted to install and configure samba as it is written in this how-to, but my first problem - when I wanted to stop the samba, it wrote me: "command not found". 
```

sudo /etc/init.d/samba stop
sudo: /etc/init.d/samba command not found

```

Can anybody write me what's wrong?

---

### Post by Morbius1 on 2010-07-11
2 things wrong ( a relative term. remember this is a very old HowTo ).

(1) If your using Ubuntu 10.04 the "samba" service no longer exists. Ubuntu has turned back the clock and once again separates the old samba service into it's component parts: nmbd and smbd.

(2) smbd is no longer in /etc/init.d

So for you, to stop samba you need to do this:
```
sudo service smbd stop
```

---

### Post by gabe17 on 2010-07-13
Thanks for help, I think it would be good to edit it in the tutorial in order to avoid problems for other people. 

I would like to ask another (noob) question: what should I do to be able to transfer files with samba between 2 PC's both with ubuntu?

---

### Post by tibguyak on 2010-07-16
Wonderful effort.

Would like you to add these few lines as well if you think it makes sense.
[I]
If there is a permission issue while trying to access from Windows, do the below - 

: Add "usershare owner only = False" to global section in smb.conf
: Then rightclick the folder '/home/samba' (or whichever share that was mounted) -> Properties -> 'Share' tab to enable the share

[/I]

---

### Post by tibguyak on 2010-07-16
[COLOR="Silver"] Re: HOWTO: Setup Samba peer-to-peer with Windows
Thanks for help, I think it would be good to edit it in the tutorial in order to avoid problems for other people.

I would like to ask another (noob) question: what should I do to be able to transfer files with samba between 2 PC's both with ubuntu?
[/COLOR]

Hi gabe,
I think the answer to transfering files lies in enabling the read/write access on both the PC's.
This can be easily done by doing 'chmod 0777 /home/samba (viz your share folder)

---

### Post by Morbius1 on 2010-07-16
> **tibguyak said:**
> Wonderful effort.

Would like you to add these few lines as well if you think it makes sense.
[I]
If there is a permission issue while trying to access from Windows, do the below - 

: Add "usershare owner only = False" to global section in smb.conf
: Then rightclick the folder '/home/samba' (or whichever share that was mounted) -> Properties -> 'Share' tab to enable the share

[/I]
You're mixing different samba methods. This HowTo is on Classic-shares. "usershare owner only = False" is usershare or Nautilus-share and is invoked using nautilus itself.

This HowTo will create a share definition at [COLOR=Blue]/etc/samba/smb.conf[/COLOR]

Nautilus-share ( or usershares ) will create a share definition at [COLOR=Blue]/var/lib/samba/usershares[/COLOR]

It's best not to use both methods on the same target folder.

---

### Post by duceduc on 2010-07-30
I managed to get a file server up and it is *working fine but it is not doing what I want it to do. I will explain.

From my Windows pc, I can view my mounted file via windows explorer by typing in **\\serverip\filename**
However, I would like to browse my files via the IE browser. When I type in **\\serverip\filename**, it sends me to my website page instead.

I am not sure what to do at this point to fix this.

---

### Post by delurfangs on 2010-07-31
Ok i am sorry if this was answered or solved already but i must leave for work soon and dont have time to read all the comments. 

i have ubuntu running on my desktop and windows vista running on a laptop when i try to connect to my linux desktop from my vista laptop it asks for a username and password when i type in the user name and password i configured in samba (which the same username and password combo that is used for my ubuntu account my vista account and my samba account) it tells me it is wrong but when i go to type it again incase i misspled it it put the name of the windows computer infront of my user name so instead of  " kodie " as the user name it fills in "  Ed\kodie  " for me (Ed is the name of the computer) is that the problem and if so how do i fix it 
and here is some stuff to look over 


[global]
    ; General server settings
    netbios name = campbell
    server string =
    workgroup = WORKGROUP1
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[samba]
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = kodie
    force group = kodie









kodie@kodie-desktop:~$  smbclient -L localhost -U%
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

    Sharename       Type      Comment
    ---------       ----      -------
    MyFiles         Disk      
    print$          Disk      
    psc-1310-series- Printer   hp psc 1310 series
    IPC$            IPC       IPC Service ()
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

    Server               Comment
    ---------            -------
    ED-PC                
    KODIE-DESKTOP        kodie-desktop server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    MSHOME               ACER-6E40E97492
    WORKGROUP            KODIE-DESKTOP


let me know if you need anything else

---

### Post by Beholder87 on 2010-08-01
Hi is there a link to a tutorial for Ubuntu 10.04 (lucid)??

I attempted to follow this one: [http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

But I was unsuccessful. I have been trying to share a Music folder that is in a NTFS partition over the network. 
When I run the testparm command this is what I get:

```
*****@Engel:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Music]
	comment = My Music
	path = /media/DATA/Music
	guest ok = Yes
*****@Engel:~$ 
```

The tutorial mentioned that I had to change the folder permissions according to Samba. In my case I want to have other computers to access/read only. I could not change the ownership from root to mine own, but it is set to have all people create and delete files.

When I go to a Windows 7 machine and click to see the network, my computer doesn't even appear on the list...

Could someone help me share this folder over the network? 
Attached is my /etc/samba/smb.conf file
Thanks

Update: I found out what was wrong... the firewall was rejecting any computer to access my shared folder...

---

### Post by Slates on 2010-08-08
I have a really basic samba question - maybe one of the folks that helped out earlier can shed some light on it for me.

Ive proeviously got Samba working just fine on Ubuntu 9.10. Ive upgradedto 10.4 and it all stopped working.

So Ive gone back to a baisc setup. But it still doesnt work ... by which I mean my windows machines which I can ping to and from Ubuntu/vnc to and from, ssh to and from, cant see my Ubunutu machine at all. Also when I go into the SAMBA accessories in the desktop, nothing happens at all (ie no menus/screens appear). No files at all get modified in /var/log/samba. There are no clues !

So here's what Ive tried :


[LIST]
[*]sudo apt-get samba install,tells me its already installed, latest version
[*]sudo apt-get remove samba, removes the package
[*]Sudo apt-get reinstalls it, but reports smbd stop/pre-start job failed to start
[*]sudo smbpasswd reports command not found
[*]smbd.conf file losted below.
[/LIST]
So Im doing something very basic and wrong here ! Cananyoine tell me what it is please ?

> # NetBIOS name resolution options
   netbios name = DellD600
   server string = Ubuntu
   workgroup = mylan
#  wins support = yes
   log file = /var/log/samba.log %u
# Master browser options (related to name resolution)
   local master = yes
   domain master = yes
   preferred master = yes
# Network security options
   hosts allow = 192.168.1.0/24
   interfaces = 127.0.0.1/8 192.168.1.0/24
# User security options
   security = user
   encrypt passwords = yes
   obey pam restrictions = yes
   username map = /etc/samba/smbusers  # Only useful if mapping usernames
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n


---

### Post by 5349U11 on 2010-08-10
> 
With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
*NOTE: Adjust this to the hostname and sharename you chose above!*
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles

*NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.*
- Click "Finish"

This may seem like a stupid question, but i have played around a bit and still no results, but am i literally supposed to put **MyFiles **or the directory that i put for **MyFiles** in that config file?

---

### Post by dmizer on 2010-08-10
> **5349U11 said:**
> This may seem like a stupid question, but i have played around a bit and still no results, but am i literally supposed to put **MyFiles **or the directory that i put for **MyFiles** in that config file?

Nope, not a stupid question.

From this section (highlighted in red):
```
[[COLOR="Red"]MyFiles[/COLOR]]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```
In this case, you can change "MyFiles" to anything you like. This is the name of your share and what you will see it named as when you browse to it from your Windows machine.

---

### Post by hertfordkc on 2010-08-17
[SIZE=4]Excellent howto.  
Filesharing was OK with 9.04.  I upgraded to 9.10 and then to 10.04 and have lost filesharing.  Pinging works.
I tried to run through the setup from the beginning and get this:

rkc@ubuntu:~$ sudo /etc/init.d/samba stop
sudo: /etc/init.d/samba: command not found
rkc@ubuntu:~$ sudo /etc/init.d/samba start
sudo: /etc/init.d/samba: command not found

after reinstalling samba.  
I don't see any reference to samba in /init.d/, but still have smb.conf in /etc/samba/.
Maybe a default path changed?
Thanks in advance.
[/SIZE]

---

### Post by hertfordkc on 2010-08-17
Which looks like Slates problem.

---

### Post by hertfordkc on 2010-08-18
> **Morbius1 said:**
> 2 things wrong ( a relative term. remember this is a very old HowTo ).

(1) If your using Ubuntu 10.04 the "samba" service no longer exists. Ubuntu has turned back the clock and once again separates the old samba service into it's component parts: nmbd and smbd.

(2) smbd is no longer in /etc/init.d

So for you, to stop samba you need to do this:
```
sudo service smbd stop
```

Slate and I also ran into this problem.  While I learned enough from the above reply to stop and start SMBD, I haven't a clue as to what I need to do to the smb.conf file or where it needs to be saved.    What about nmbd?
Is there a simple explanation?

Also, where should I have looked to find out about this reversion?  Did the lynx install put a big readme somewhere?:confused:

---

### Post by dld521 on 2010-08-27
Stormbringer:
It's a great how-to, but I'm having one slight problem.  Samba does not appear in my /etc/init.d file.  Just to be sure (because I'm pretty new to Linux), I removed and reinstalled Samba.  Throughout the operation I copied and pasted your code and command lines where appropriate.  So I'm not sure what to look for.   

[EDIT]  I just saw a post (right above this post) that says in Lucid, file names are changed.  Should I be substituting the "new" (old?) smbd for samba in each place in the code?

There is one other thing in your instructions that I found ambiguous.  You say to replace YOUR_HOSTNAME on the netbios line with "your desired hostname."  I'm trying to set up my Linux box to print on printers that are on a Windows machine.  Is the proper hostname the name of my Linux box or the Windows machine that has the printer I want to use?

Thanks for your patience and help.

---

### Post by Morbius1 on 2010-08-27
> Should I be substituting the "new" (old?) smbd for samba in each place in the code?You can and it will work. But you will get something that looks an awful lot like an error message because they really want you to use this format:
```
sudo service smbd restart
```> You say to replace YOUR_HOSTNAME on the netbios line with "your desired hostname." I'm trying to set up my Linux box to print on printers that are on a  Windows machine.  Is the proper hostname the name of my Linux box or the  Windows machine that has the printer I want to use?"YOUR_HOSTNAME" is the hostname you want to use on your Linux box not the Windows box.

---

### Post by theOgFlomaster on 2010-08-29
I have samba installed and and I have a /etc/samba  folder, but I can't start or stop it 

```
xbmc@XBMCLive:/$ sudo /etc/init.d/samba start
sudo: /etc/init.d/samba: command not found
xbmc@XBMCLive:/$

```

please help. I don not have a samba file in my /etc/init.d/ folder 

-=Jason=-

---

### Post by gcmartin on 2010-09-23
SAMBA in Ubuntu has changed! IT IS NOW **[SIZE="2"]UBUNTU VERSION SPECIFIC[/SIZE]**.
This thread needs 2 things:[LIST=1]
[*]reference to separate documents on "Howto use SAMBA services"** BY VERSION NUMBER!**[*]_separate FORUM THREADS_ for SAMBA in Ubuntu **BY VERSION NUMBER!**
[/LIST]
***_[SIZE="2"][SIZE="3"][SIZE="4"]Can the owner/moderator address this for the community?[/SIZE][/SIZE][/SIZE]_***It also would be nice if someone could provide a link in the SAMBA document(s) explaining why it was necessary to change Ubuntu's usage. Was some "new" person added who wanted it changed for some good reason or did the new developer(s) want a new "signature" to differenciate their work from previous Ubuntu? Why?

Thanks in advance...

---

### Post by Silvertones on 2010-09-23
Sorry to disappoint but I used this tutorial in 9.1 and 10.04 and it worked flawlessly. I share files between my Win XP & Ubuntu and vice versa. I also share a printer that is hooked up to the Ubuntu Machine.
Do read the instructions and commands VERY carefully.

---

### Post by dmizer on 2010-09-23
> **gcmartin said:**
> SAMBA in Ubuntu has changed! IT IS NOW **[SIZE="2"]UBUNTU VERSION SPECIFIC[/SIZE]**.
This thread needs 2 things:[LIST=1]
[*]reference to separate documents on "Howto use SAMBA services"** BY VERSION NUMBER!**[*]_separate FORUM THREADS_ for SAMBA in Ubuntu **BY VERSION NUMBER!**
[/LIST]
***_[SIZE="2"][SIZE="3"][SIZE="4"]Can the owner/moderator address this for the community?[/SIZE][/SIZE][/SIZE]_***It also would be nice if someone could provide a link in the SAMBA document(s) explaining why it was necessary to change Ubuntu's usage. Was some "new" person added who wanted it changed for some good reason or did the new developer(s) want a new "signature" to differenciate their work from previous Ubuntu? Why?

Thanks in advance...
You're talking about a howto that was last edited in 2006. This thread really isn't the best place to be getting current information about Samba.

Samba is currently under development to include support which will allow Linux servers to be a Windows domain controller which will open the door for Linux AD servers. This is one reason for separating the smbd and nmbd parts of the samba init script.

Also, since Linux is a community effort, if you feel that something is lacking with regards to documentation, feel free to close the gap. You might also be interested in this: [http://doc.ubuntu.com/ubuntu/serverguide/C/samba-fileserver.html](http://doc.ubuntu.com/ubuntu/serverguide/C/samba-fileserver.html)

---

### Post by Stormbringer on 2010-09-24
Since dmizer already said it ...

This Howto I've once written was aimed at Breezy/Dapper and is clearly expressed at the very beginning of the OP post. It may have worked with other, newer, Ubuntu versions but is at least no longer suitable for Lucid anymore.

I actually stopped using Ubuntu quite a long time ago out of a lot of reason I'm not going to debate here.

At any rate, the problems you all are expericing at the moment ...

service smbd start|stop|reload|restart (on Lucid)
Vs.
/etc/init.d/smbd start|stop|reload|restart (on earlier versions)

... is Canonical's very own fault.

The "service" control has already been around in RHEL/Fedora (and forks like Cent OS) at the time of Dapper though Debian, and subsequently Ubuntu, has been ignorant enough not to use it for years to come ... till now.

NOW that they finally adopted "service" they fail to advertise this change, at least I don't see it mentioned anywhere.

Anyway, since I already sent this to a forum mod (don't ask me whom) some time ago without effect...

Could someone please either delete the thread or hand it over to someone who wants to maintain it?

And while we're at it ... please delete, or deactivate if sooooooo desire to collect dead accounts, the user account as well. I'm not using Ubuntu (or is now called Ma[r]k OS X?) and have no plans picking it up again.

---

### Post by dolorian on 2010-09-29
Stormbringer, I followed precisely your guide on 10.04 and everything works fine, except just one thing. 
I cannot create new dirs/files and rename old ones from windows. I can although edit the files with notepad (open+save).  This happens when the parent directory is 0755. If I change its rights to 0775 from linux, I can create/rename files/dirs from windows. 

The problem is I do not want my dirs to have 0775 permission. I crawled the whole web but wasn't able to find good soluiton. I've tried thousands of combinations with the samba config directives - no success. The only solution is $chmod -R 775 /my/share

Any idea ?

---

### Post by Morbius1 on 2010-09-29
dolorian,
If you read the post immediatly before yours you might have noticed that Stormbringer has left the building and is not likely to respond to your question.

> I cannot create new dirs/files and rename old ones from windows. I can  although edit the files with notepad (open+save).  This happens when the  parent directory is 0755. If I change its rights to 0775 from linux, I  can create/rename files/dirs from windows.Then you didn't do this:
> [MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
"force user" would have converted whoever samba authenticated to "YOUR_USERNAME" and assumming "YOUR_USERNAME" is the owner of /media/samba you could have set permissions to 0700.

---

### Post by dolorian on 2010-09-30
I think I did it. Here is my smb.conf:

```

[global]
    ;General server settings
    netbios name = Ubuntu64
    server string =
    workgroup = SVEST
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    syslog = 1
    syslog only = yes

[WWW]
    path = /var/www/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = myuser
    force group = myuser

```

Under  /var/www/, which is owned by myuser.myuser and has 755 I can't create/rename/delete files, but I can edit them from windows. 
If I change  /var/www/ rights to 775, I can do everything there from windows.

---

### Post by Morbius1 on 2010-09-30
[http://ubuntuforums.org/showthread.php?t=919951](http://ubuntuforums.org/showthread.php?t=919951)

---

### Post by dccrens on 2010-10-02
This is the best setup guide for samba and 10.04 with Vista and Xp. I struggled for days before finding this and within 2 minutes had this working with the Wins Server setup. 

Check this out: [http://ubuntu.swerdna.org/ubusambabrowse.html]("http://ubuntu.swerdna.org/ubusambabrowse.html")

---

### Post by patek on 2010-10-13
I just saw the post above, and found [http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html), but I'm too fed up to read it at the moment. I've written the post already so I might as well put it up, right?

I went through this manual twice, read the read-before-you-post and the first couple of post, and spent a good amount of time googling.

Basically, I have a 10GB+ of data on the linux machine (pat) to transfer onto the windows machine (npcc-pc). Please note my mobile broadband wouldn't work on the linux one. The linux machine is about to die, and hopefully I will never have to use it again, so I'm not bothered about making / accessible. I have them linked up using a crossover cable and the sockets are blinking on both.

I'd like to think I've set everything right on the ubuntu machine, and I mut be doing something wrong on the win one.  Basically, it all looks different on vista. When I go to 'Manage networks', there is two lan connections, Local Area Connection and Local Area Connection 2, even though the machine only has one socket. Local Area Connection is an 'unidentified network, shared'. I've set everything up in the properties as guided (for TCP/IPv4 only, as there is no WINS tab for TCP/IPv6). LAC2 appears as unplugged.

On the linux machine, I'm using xfce4. I went to the network settings tab, and went to edit the 'auto eth0'. I entered 192.168.0.10 as the address in the IPv4 tab. I was expecting to see pat in my windows explorer's network tab, but there is only two different icons for npcc-pc, and an 'Internet gateway device'.

I will enter my ifconfig and ipcongfig outputs as attachments. I can't upload smb.conf, so I'll qoute it below. Can anyone tell me where I'm going wrong? I feel like an idiot.

```
[global]
    ; General server settings
    netbios name = pat
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = pat
    force group = pat
available = yes
browsable = yes
public = yes
writable = no

```

---

### Post by Ragnar! on 2010-11-11
:KSThanks dccrens that link got me up and running in about 10 minutes after trying half the night!:KS

---

### Post by jcwx86 on 2010-11-24
Brilliant walkthrough - thanks!

---

### Post by degarb on 2010-12-20
My husband's head exploded after reading half way down through these instructions, despite trying the author's careful and thoughtful construction.  I am a widow now, but still would like to get the Standard windows network share to work.   Has Ubuntu improved since 2006, or are they still in dark ages and early years of computing, editing conf files to get a network to work.   In other words more kind,  how outdated is this thread?

---

### Post by Morbius1 on 2010-12-21
> **degarb said:**
> Has Ubuntu improved since 2006, or are they still in dark ages and early years of computing, editing conf files to get a network to work. 
Most likely you will at some point need to modify a config file as is true in all of Linuxdom.
>   In other words more kind,  how outdated is this thread?The section of the forum you posted in is:
Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Tutorials & Tips > [COLOR=Blue]Outdated Tutorials & Tips
[/COLOR] 
The author is no longer a member of the forum:
> I actually stopped using Ubuntu quite a long time ago out of a lot of reason I'm not going to debate here... Could someone please either delete the thread or hand it over to someone who wants to maintain it?

And while we're at it ... please delete, or deactivate if sooooooo desire to collect dead accounts, the user account as well. I'm not using Ubuntu (or is now called Ma[r]k OS X?) and have no plans picking it up again. Having said all that and despite it's title " Samba peer-to-peer" it still stands as a very well written HowTo on how to set up a Linux box as a WINS Server. Adjustments will have to made if you're using Ubuntu because services have changed since 2006.

---

### Post by bludshot on 2011-01-01
The original post guide has one problem: Where it says sudo /etc/init.d/samba stop and also how to start it, it should instead say:

sudo service smbd stop

and then start


Also the first pre-requisite is that you have a static IP but the guide doesn't mention how to do that. Here is a guide for that: [http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by dmizer on 2011-01-01
> **bludshot said:**
> Also the first pre-requisite is that you have a static IP but the guide doesn't mention how to do that. Here is a guide for that: [http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/)

Neither Samba nor this guide require you to have static IP.

---

### Post by Morbius1 on 2011-01-01
> **dmizer said:**
> Neither Samba nor this guide require you to have static IP.
Although this guide does gives you a way out, most of it is really a HowTo on setting up a WINS server. Having and using a WINS server in a LAN does in fact require you to have at least one static IP address - for the WINS server itself.

---

### Post by bludshot on 2011-01-01
> **dmizer said:**
> Neither Samba nor this guide require you to have static IP.

> **Stormbringer said:**
> **HOWTO: Setup Samba peer-to-peer with Windows**

**1. Prerequisites**

- Your Linux box should have an static ip-address.


.

---

### Post by dmizer on 2011-01-02
> 1. Prerequisites

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. **If that's no valid option you cannot use WINS** ... more on this way down.
WINS is not essential for a Samba server. It's helpful, but not essential.

What is WINS (from man smb.conf)?
```
       wins support (G)

           This boolean controls if the nmbd(8) process in Samba will act as a
           WINS server. [B]You should not set this to yes unless you have a
           multi-subnetted network and you wish a particular nmbd to be your
           WINS server[/B]. Note that you should NEVER set this to yes on more
           than one machine in your network.

           Default: wins support = no
```
In most cases a WINS server is not necessary, especially if you have a local DNS server as is the case with most modern retail router equipment.

---

### Post by bludshot on 2011-01-02
I was not declaring that the first pre-req in using samba was to have a static IP, nor was I stating that the guide absolutely requires you to have a static IP. I was merely referencing the first prereq listed in the guide (which is there) and suggesting that instead of the guide just telling people they should have a static IP without explaining how, that a link to a guide telling you how to set your IP to static would be helpful, so I provided that link.

---

### Post by dmizer on 2011-01-02
> **bludshot said:**
> I was not declaring that the first pre-req in using samba was to have a static IP, nor was I stating that the guide absolutely requires you to have a static IP. I was merely referencing the first prereq listed in the guide (which is there) and suggesting that instead of the guide just telling people they should have a static IP without explaining how, that a link to a guide telling you how to set your IP to static would be helpful, so I provided that link.

I clearly misunderstood. My apologies.

---

### Post by bertolo on 2011-01-08
omg this thread has 99 pages :S
can someoene give me a fast update of this for 10.04?
this is important thing, someoen should post a sticky about this.

---

### Post by degarb on 2011-01-08
99 pages should be nothing for a Linux user.

---

### Post by dmizer on 2011-01-09
> **bertolo said:**
> omg this thread has 99 pages :S
can someoene give me a fast update of this for 10.04?
this is important thing, someoen should post a sticky about this.

The wiki documents regarding samba should be sufficient: [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

---

### Post by degarb on 2011-01-09
> **dmizer said:**
> The wiki documents regarding samba should be sufficient: [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

I spent 14 hours getting mine running.  Nothing worked, then I peeked into the host file, and found some bad entries there that the installer automatically stuck in there.   Fixed those and it started working.  Still doesn't browse other computers nearly as quickly as the xp machines, but works if you persist on clicking 1 or more times and waiting. This incompetence possibly also led me to believe it wasn't working when it was. 

I think it would be more useful to have a simple double-check check list that didn't include detailed instruction about crap we are needing.  We certainly aren't interested in the packet architecture.  Someone, better experienced than I, could boil this down better.  The useful stuff that I remember doing that may have helped:  1. check host file 2. check samba.conf make sure name is same as xp machines and all allow entries are there 3. check the inclusion of packages needed to get ntfs browsing over network,etc. Since many distros don't think getting a real mixed computer home network is necessary (Real homes have many occupants that use and share on macs, xp, win7, 98, other linux distros, and the resident linux distro.) 4. Know how to add a user using latest JK Rowling inspired comandline commands.

---

### Post by Morbius1 on 2011-01-09
> **degarb said:**
> Nothing worked, then I peeked into the host file, and found some bad entries there that the installer automatically stuck in there.    I have never seen that happen. I'm not saying it didn't in your case but I have never seen that happen.
> 2. check samba.conf make sure name is same as xp machines and all allow entries are thereIf you're talking about the Workgroup name I have 4 in my network and everyone ( WinXP, Mac, occasionally a WinVista, other Linux, ... ) seems fine with it.
> 3. check the inclusion of packages needed to get ntfs browsing over network,etc.  I honestly and truly have no idea what that means. NTFS and FAT32 can present a problem if they are not mounted with the right permissions ( i.e., USB stick ) to facilitate samba access but Samba offers a way around that problem. That's not a Samba problem it's a Linux permissions problem.
> 4. Know how to add a user using latest JK Rowling inspired comandline commands.There are GUI's that do all that but most HowTo's - in fact most of the help you find in forums - tend to be desktop environment agnostic. Especially with something like Samba that can be configured on just about anything. If someone gave a description on how to do something using a gnome utility it's not going to do the KDE user any good.

---

### Post by degarb on 2011-01-09
> **Morbius1 said:**
> I have never seen that happen. I'm not saying it didn't in your case but I have never seen that happen.
If you're talking about the Workgroup name I have 4 in my network and everyone ( WinXP, Mac, occasionally a WinVista, other Linux, ... ) seems fine with it.
 I honestly and truly have no idea what that means. NTFS and FAT32 can present a problem if they are not mounted with the right permissions ( i.e., USB stick ) to facilitate samba access but Samba offers a way around that problem. That's not a Samba problem it's a Linux permissions problem.
There are GUI's that do all that but most HowTo's - in fact most of the help you find in forums - tend to be desktop environment agnostic. Especially with something like Samba that can be configured on just about anything. If someone gave a description on how to do something using a gnome utility it's not going to do the KDE user any good.

So, what is your checklist?  Something is missing, else things should all work on install.  It didn't with any of my three machines (vector, ubuntu  9, lmde 10 after ubu10 installer kept crashing), or all these other people.

Probably, as pointed out by Morbius,  my end user perceptions are warped to think this or that worked, but are serendipitous to some real solution I tried anon the psydo patch.  So, I don't firmely know (only three full installs + 2 vbox). I did have to install packages to get ubuntu 9 working (this I am certain), and packages on mint 10 lmde to get networking running (this others were certain, though I spent time doing this).  It seems also to my perception (since frantically trying 40 pages and websites with recommended fixes.) that nothing worked until I set workgroup name the same as xp (probably a placebo fix).   

Interesting point about kde, gnome, xfce.  In last year, I have slitaz, ubuntu xfe 9, mint 10 kde and crunchbang (pretty much same as ubuntu).  I just assumed that since Ubuntu 9 xfce and Mint 10 kde were pretty much arranged in same logical manner (graphics differ, one at top and one at bottom), that, finding switches in gui is pretty much the same. You don't need graphic to describe a folder structure or gui heirachy:  Administration> Control panel>drives>mount iso , nor are they totally arbitrary. Musing too, often Windows tutorial descriptions of fixes  may cover the two most common layouts.

---

### Post by Morbius1 on 2011-01-09
> So, what is your checklist?  Something is missing, else things should  all work on install.  It didn't with any of my three machines (vector,  ubuntu  9, lmde 10 after ubu10 installer kept crashing), or all these  other people.Don't have a checklist. Haven't had a problem since I bought my current router ( an aging DLink DI-604 into which I have a wireless access point attached ). And that was years and many distros ago. There doesn't appear to be anything wrong with my network. Most of these Samba HowTo's are in response to something being wrong with the network and how Samba can be used to correct for it.

Take a look at this HowTo and you'll note that there is really very little pure Samba content. It has a recommended smb.conf file, something on setting up users with passwords, and something about security. The bulk of this HowTo is how to set up a WINS server and how to configure a Windows client to access the WINS server.

One doesn't set up a WINS server unless there is something wrong with the network and name services are either not present or not working or the network is very complex with multiple subnets. By default Ubuntu uses "broadcast" to inform the rest of the network that it is alive and well and has shares available. As it turns out Windows also uses "broadcast" so everything for me works out of the box. Only once did I have to make a change in smb.conf to correct for a network problem and that was on a laptop. It was easily fixed by forcing it to use broadcast first in the name resolve order. And I never did change it's workgroup name.

There are things that can get in the way of samba such as firewalls, linux file permissions, even the length of the machine name but that's why forums were created :)

---

### Post by miekrand on 2011-01-13
In Ubuntu 10.10 a few things changed.  

To stop or restart samba

sudo service smbd stop
sudo service smbd start
sudo service smbd restart

The link to windows networking at the bottom has changed to
[https://help.ubuntu.com/10.10/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.10/serverguide/C/windows-networking.html)

I am in the process of connecting my Ubuntu 10.10 to my mothers XP Thingy so that I can use our printer again since I dont have a network card in my simple HP PSC 1500xi I am forced to use file/printer sharing.

Can I ask for permission  to post a new HOWTO for the latest Ubuntu?  When I get mine working of course.  And if anyone wants an Italian translation, if time permits I could do that also.

---

### Post by krustybaguette on 2011-02-19
@stormbringer

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

Code:

sudo mkdir /home/samba

... and adjust "path =" to read ...

path = /home/samba/

I'd like to put my /home on an external hard disk connected by a hard drive adapter (Sharkoon) Since the adapter can be turned off and on I would need to remember to turn it on when using my computer but how would I mkdir on this other drive? Here's what I've tried:

kenny@PORTEGE-7140CT:/media/Sharkoon Drive Adapter$ mkdir /home
mkdir: cannot create directory `/home': File exists
kenny@PORTEGE-7140CT:/media/Sharkoon Drive Adapter$ sudo mkdir /home
[sudo] password for kenny: 
mkdir: cannot create directory `/home': File exists
kenny@PORTEGE-7140CT:/media/Sharkoon Drive Adapter$ 

Does this mean I would have to wipe out the existing /home on my main drive (sda)?

---

### Post by degarb on 2011-02-20
> **miekrand said:**
> In Ubuntu 10.10 a few things changed.  

To stop or restart samba

sudo service smbd stop
sudo service smbd start
sudo service smbd restart

The link to windows networking at the bottom has changed to
[https://help.ubuntu.com/10.10/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.10/serverguide/C/windows-networking.html)


Ah, ha. Been forgetting to post for why old ways didn't work.


I like that you don't need to remember path.  I guess   sudo service samba stop  would have been too obvious.  So, they chose something less intuitive.  Wouldn't want to make things too logical or easy.

---

### Post by Morbius1 on 2011-02-20
> I guess   sudo service samba stop  would have been too obvious.  So,  they chose something less intuitive.  Wouldn't want to make things too  logical or easy.In the beginning of time there was the smbd daemon and the nmbd daemon. Some smart folks over at RedHat decided to combine the two into one "service" called "samba" since System Administrators tend to run both in sequence. In Debian it's still that way.

In Ubuntu ( I think because of upstart - not sure ) they went back to the olden days where your run smbd and nmbd separately.

---

### Post by degarb on 2011-02-20
> **Morbius1 said:**
> In the beginning of time there was the smbd daemon and the nmbd daemon. Some smart folks over at RedHat decided to combine the two into one "service" called "samba" since System Administrators tend to run both in sequence. In Debian it's still that way.

In Ubuntu ( I think because of upstart - not sure ) they went back to the olden days where your run smbd and nmbd separately.

That explanation should help the memory.  I will still need to remember to desiccate the word samba of her vowels to the word smb.  Linux bash seems  to hate vowels.  Must have to do with some voweless clicking language in StarTrec.

---

### Post by Korsakoff on 2011-05-05
--- crap --- please delete

---

### Post by Korsakoff on 2011-05-05
How can I made a folder accessible only for a group of users?

---

### Post by Morbius1 on 2011-05-05
How about this:

[1] Create a unique group:
```
 sudo groupadd newgroup
```[2] Add your users to that group
```
 sudo gpasswd -a user1 newgroup
```[3] Make the share look something like this:

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
[COLOR=Blue]valid users = @newgroup[/COLOR]
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP


Logout and login again for the group changes to take affect and then restart samba:
```
sudo service smbd restart
```

---

### Post by Korsakoff on 2011-05-05
Many thanks m8

---

### Post by Morbius1 on 2011-05-05
I read through the original HowTo again and realized he never altered the Linux permissions on the shared directory itself so my step [3]  won't work.

To keep with the authors original intent I have modified my step [3] to this:

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
[COLOR=Blue]valid users = @newgroup[/COLOR]
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

"valid users" will restrict who can get in to the "newgroup" users.
"force user" will force the user to you so everyone in the newgroup group will be able to read and write.

Sorry about the confusion.

---

### Post by Korsakoff on 2011-05-05
I created two usergroups in my local sys, and rightnow I want that one group can access one dir, and other one another.

named: alfa and beta

my conf looks like (they are the same)

[Alfa]
    path = /home/samba/alfa/
    browseable = yes
    read only = no
    guest ok = no
    valid users = @alfa
    force group = alfa
    create mask = 0664
    directory mask = 0775

and I don't even know what is the @newgroup

---

### Post by Morbius1 on 2011-05-05
The newgroup is just an example. 

[Alfa]
    path = /home/samba/alfa/
    browseable = yes
    read only = no
    guest ok = no
    valid users = @alfa
    force group = alfa
    create mask = 0664
    directory mask = 0775

You did it right as long as you added the users to that group ( step [2] ). The only problem and the reason for my correction to step [3] is that your definition is fine if it were a pure Server. All remote users can add a file to the share and it will save as:
user = remote-user-name
group = alfa
permissions = 664 / 775

So all other remote users can read / write to each file.

But if this is a a desktop computer with a user named say ... morbius his add to the share locally will save as:
user = morbius
group = morbius
permissions = 644 / 755

The remote user can read but not write to morbius' files. So to follow the original HowTo use the "force user" to make all remote users appear to be you after they are authenticated.

---

### Post by Korsakoff on 2011-05-05
Mine one is a local server (Natty x64). I think I am getting into your explaination.

My final goal is to get department folders on the local server accessible only to the department group.

If you have any other suggestion to get it working, I would very appreciate it!

---

### Post by Morbius1 on 2011-05-05
> **Korsakoff said:**
> Mine one is a local server (Natty x64). I think I am getting into your explaination.

My final goal is to get department folders on the local server accessible only to the department group.

If you have any other suggestion to get it working, I would very appreciate it!
Create multiple shares by department and create multiple groups by department and use your [alpha] share definition as a template.

---

### Post by Korsakoff on 2011-05-05
That's what I was going to do! Thanks Morbius!

---

### Post by Phaze08 on 2011-05-29
Ok, so I'm not sure if this is what I need, but what I need to do is be able to browse files on remote computers on a vpn. The one at my job. Now, I have nautilus elementary with breadcrumbs and when I click on network, it has my home network and the vpn. Now, when I click the home network, it lets me browse local computer files, but when I click the vpn, it just says cannot retrieve list of host computers. Anyone know what I'm doing wrong? I installed samba and set it up but as far as I can tell, its not doing anything different. Im new to Ubuntu and if I can get this done, I can run it full time without having to fall back on windows.

---

### Post by Kionas on 2011-06-19
Great set of instructions.... worked well.  One thing to look out for though that got me thinking for a while.
Command for startup is :

sudo /etc/init.d/samba start

but for some reason this did not work for me until I realised that the actual command/script is called samba4 and not just samba.  So the command line that worked for me was:

sudo /etc/init.d/samba4 start

hope this helps someone.

---

### Post by Morbius1 on 2011-06-19
From synaptic on [COLOR=Black]Samba4[/COLOR]:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. **[COLOR=Blue]These should be considered _experimental_, and should not be used in production.[/COLOR]**I would not recommend installing Samba4.

---

### Post by Kionas on 2011-06-19
Thanks for the heads up..... the good news it works well.

That would leave me with the question though;  I know I have installed samba, but where is the samba command file if not in /etc/init.d/ ???

Any suggestions would be appreciated.

thanks

---

### Post by Morbius1 on 2011-06-20
Samba ( the daemon ) is controlled by the service name smbd:

```
sudo service smbd start 
```

---

### Post by OrvillP on 2011-06-21
[FONT=Arial, sans-serif][SIZE=2]I have a small private workgroup named RSLHOME consisting of 2 Win 7 PCs, 1 Win Vista PC, this Ubuntu 11.04 PC (MediaViewer), 2 Linux NASs, a USB device server for remoting my printers and scanner and a router for Internet access. All these components are connected together by 1Gbps Ethernet. The user names on all 3 of the Win PCs and the 2 NASs is RSL with the same password on all. All of the Win PCs and NASs have shares. I want to use Samba on MediaViewer to join the workgroup and access shares on the other PCs and NASs.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]I did a sudo apt-get install samba smbclient and a sudo apt-get install smbfs. Then I looked at smb.conf and got my mind blown. Am I in the right place to ask for help in sharing files with Windows computers using Samba?[/SIZE][/FONT]

---

### Post by kevcoder on 2011-06-21
take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1781455") that I started with the same issue.  I just got this working between 2 win7 and an  ubuntu 11.04 machine.


Hope it helps

---

### Post by vikrang on 2011-08-19
Dear Stormbringer , your smb.conf file was the only one that works for me partially. I am able to view my windows (XP) shared folders in the KDE dolphin manager in Networks ..However I am not able to mount the share ..I get the error "Could not resove address for host VIKRAM : Unknown error" where VIKRAM is the XP computer's name. 
 
From the other perspective , If I share a Linux folder and try to search in Windows network neighbourhood , I am not able to view any folder in the linux box..If I give the IP address to map the drive , it gives the error "could not find //192.168.1.2"
 
I have tried changing DHCP to static in host , but still it doesnt resolve the issue.. I have also tried utils like SMB4K , XSMBROWSER and SWAT ..I cannot figure how to get the 2 computers to talk to each other..
 
I also tried changing distro from ubuntu to arch and followed the ArchWiki to the letter, but stilll the same problem.(in fact I have a dual boot of Arch and Ubuntu because these are the most popular in terms of package availability as If anything is not available in either , it is not available anywhere in Linux world)
 
I am posting this in both Ubuntu and Arch forums so that I get a quick solution from somewhere.

---

### Post by YourSurrogateGod on 2011-09-27
> In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

What's WINS?  Wouldn't the issue of knowing where to send data be taken care of by using DNS?

---

### Post by Jeinhor on 2011-10-30
At first, I dismissed this guide as it was pretty old (first post from 2006). Turns out I shouldn't have. Worked great! The only change:

```
sudo service smbd stop/start/restart
``` instead of ```
/etc/init.d/samba stop/start/restart
``` :)

Thanks!

---

### Post by Forux on 2011-11-01
Hello,

i have problem with samba:

my OS ubuntu 11.10
server OS ubuntu server 11.10

i do next: smbmount //domain/folder /media/folder -o user=guest,password=,create mask=0666

and when i try create file in /media/folder with my account it create file with permissions: 644

when i do the same from root - all ok - 666

Please help me solve this problem.

P.S. my accounts groups is:
forux adm dialout cdrom plugdev lpadmin admin sambashare

UPDATE: server also has create mask 666

---

### Post by loren41 on 2011-11-01
I see that your howto is a bit dated, but I guess the basics are still valid and that is where I am having trouble.  I am running a home network on a Windows 7 PC.  This PC is currently connected to an unRAID server where I backup my files from both the PC and the laptop.

I recently upgraded the laptop from Ubuntu 11.04 to 11.10 and lost my connection to the unRAID server.  Your procedures were followed and I tried to set my permissions using 'sudo chmod 0777 /media/samba'  The command failed with the following message: chmod: cannot access '/media/samba': No such file or directory.

Can you help me?

---

### Post by Kostarsus on 2011-11-20
Hello,
 
a realy good article. Even if it is old, th configuration functions good.
But I've a problem with my samba system.
I use samba on ubuntu 11.10. I connect with a Windows 7 SP1 client to the samba server.I'd installed the registry additions on the Windows client. I can browse the enabled directories. I can create, read, write and copy files to the directories of the samba server.
So far so good.
If I try to download a file wih the internet exploerer, and want to save the file directly in an enabled samba directory, the download breaks directly. A zero byte paritional download file was created but the download stopped.
Can anyone help me, please?
 
cu Kostarsus

---

### Post by bryan.sailer on 2011-11-26
I have samba share setup on my home network. Just recently my share folders started showing up as printers on my windows machine. I am also unable to see the share folders from my laptop. The share folders on located on my desktop which is running Ubuntu 10.10. and my laptop is also running Ubuntu 10.10. The only change that I have made within the past few weeks was to add my printer to my network. The printer is a network printer plugged into my switch. What could be causing this to happen?

Bryan Sailer
Ubuntu 10.10

---

### Post by Steve R. on 2011-12-13
I just installed the Asus RT-N56U wireless router for my home network and now get (on my Ubuntu computer) the error message:"Unable to mount location" and "Failed to retrieve share list from server". [This issue has already been posted here by heathd666]("http://ubuntuforums.org/showthread.php?t=1735655") and remains unanswered. 

Previously, I had a Linkyss router with no issues. In taking a look at the IP addresses displayed by the Asus RT-N56U, it appears that they may be out-of-range for the computer running Ubuntu 10.10. I will be looking into how Samba (on the Ubuntu computer) defines the range of allowable IP address.

Any thoughts? 
Is the range of available IP addresses a plausible reason for this issue?


RESOLVED: Please see: [Howto: Fix Windows share browsing issues, Problem #3]("http://ubuntuforums.org/showthread.php?t=1169149")

---

### Post by Jesper Tage on 2011-12-13
> **Jeinhor said:**
> At first, I dismissed this guide as it was pretty old (first post from 2006). Turns out I shouldn't have. Worked great! The only change:

```
sudo service smbd stop/start/restart
``` instead of ```
/etc/init.d/samba stop/start/restart
``` :)

Thanks!

OR

```

sudo restart smbd
sudo restart nmbd



```Change Restart with stop or start

---

### Post by duceduc on 2012-02-08
I don't know what have happened. Before rebooting my windows 7, I was able to see my server under network. After I rebooted windows, I cannot see my server. I've tried manually searching for it via \\webserver but it doesn't find it. The error I get from windows is:

---

### Post by duceduc on 2012-02-10
Here is a little more info from the above post. My syslog says
> Cannot find my workgroup NIPPLE_NECK on subnet UNICAST_SUBNET.

I am not sure where to look for this.

---

### Post by doskyis on 2012-02-24
Hi Everyone,

I followed the instructions on this How-To and I can now see my Linux Laptop on my Windows laptop when I try to map the new drive. However, once I click on the Linux drive it asks for a username and password. I've tried just about every combination of username and password I think it is asking for but haven't has any luck.
Any suggestions?

PS. I have a windows 7 laptop and the linux is running Ubuntu 11.04

---

### Post by killernat on 2012-02-27
is it possibale to make a 2nd network folder  lets say copy all the settings from [MyFiles] and make another one below it like [Myfiles2]  and have a diffrent home directory on a side note am i allowed to change the [MyFiles] to a diffrent name like [media]

---

### Post by killernat on 2012-02-27
so yes i can do what i said after reading part of the samba manual it is a lot simpler than i had thought

---

### Post by duceduc on 2012-03-13
I cannot find the cause of why my shorewall is blocking samba. I had this installed in another ubuntu server and I didn't have to touch shorewall and I am able to see the server on my windows. Now after installing samba on a 11.10 server, shorewall is blocking in samba for some reason. If I shut down shorewall, samba works.

Here is my shorewall rules.
> # mail lines
SMTP/ACCEPT     net             $FW
SMTPS/ACCEPT    net             $FW
Submission/ACCEPT       net             $FW
IMAP/ACCEPT     net             $FW
IMAPS/ACCEPT    net             $FW

# Web
ACCEPT		net		fw		icmp 8
ACCEPT		net		fw		icmp
ACCEPT		net		fw		tcp	pop3,pop3s,imap2,imap,imaps,submission,8118,3128,943,8443,1194,45631,1723,49152
ACCEPT		net:216.162.217.194	fw	tcp	munin
ACCEPT:ULOG	net		fw		tcp	21,55535:65535

SSH/ACCEPT	net		$FW
HTTP/ACCEPT	net		$FW
HTTPS/ACCEPT	net		$FW

SMB(ACCEPT)	fw		loc
SMB(ACCEPT)	loc     	fw

FTP(ACCEPT)	loc		net

#LAST LINE -- DO NOT REMOV


---

### Post by duceduc on 2012-03-14
> **duceduc said:**
> I cannot find the cause of why my shorewall is blocking samba. I had this installed in another ubuntu server and I didn't have to touch shorewall and I am able to see the server on my windows. Now after installing samba on a 11.10 server, shorewall is blocking in samba for some reason. If I shut down shorewall, samba works.

Here is my shorewall rules.

I fixed my issue of shorewall blocking samba. I changed the setting in /usr/share/shorewall/macro.SMB

I replaced 'PARAM' to 'ACCEPT' on all cases.

---

### Post by Crackouch on 2012-03-18
Samba is almost working, but I can't seem to get my credentials justified in order to map the network drive.
I have an Ubuntu 11.10 machine and a windows 7 for my SOHO. I preceded with the following steps
1. I created an Ubuntu group called "sohonetwork"
 
 sudo groupadd sohonetwork
 
2. On my Ubuntu box, I created a folder under / .
 
 sudo mkdir NetworkFileSystem
 
3. I then changed the group association of that folder
 
 sudo chgrp sohonetwork NetworkFileSystem
 
4. Set additional permission parameters:
 
 sudo chmod g+rws /NetworkFileSystem
 
5. Then I installed Samba and altered the /etc/samba/smb.conf (I made a copy) to recognize the workgroup and create the samba share:
 
 workgroup = HOMENET
 
 [NetworkFileSystem]
    path = /NetworkFileSystem
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory = 0755
    force user = homeuser
 
6. Finally, I created an Ubuntu user and added it to the group
 
 sudo useradd -G sohonetwork -p "Password1" homeuser
 
Now, my Windows 7 box (which has GUI capability to map drives) recognizes my file server, but cannot map to the folder because my credentials are rejected. I tried homeuser "Password1" as well as my root administrator credentials. It's not letting me in. I even tried totally freeing up the folder with the following command:
 
 sudo chmod 0777 /NetworkFileSystem
 
I have broken down and recreated the setup many times and I get the same results. Am I missing anything? The bummer of all this is that I had Samba working before perferctly but unfortunately I has prompted to reinstall Ubuntu due to disk space issue and redo all this.
 
What am I missing? Please help? Thanks, Dave

---

### Post by Morbius1 on 2012-03-18
Unlike Windows where there is only "the" user, Linux and Samba maintain two separate structures for users. You created a Linux user named "homeuser" and it sounds like you want to use that user name to access the Samba share but it doesn't sound like you added him to the Samba password database:
```
sudo smbpasswd -a homeuser
```You will be asked for sudo's password and then it will ask you for homeuser's samba password. It can be the same as the login password or it can be something different.

[COLOR=Blue]**EDIT**[/COLOR]: You also have a mistake in your share definition:
> directory = 0755Did you mean directory mask?

You know, when you use "force user" there's really no need for create or directory masks or steps 1, 3, and 4. All remote users after authentication will be converted to the user homeuser. So if you set up a new user called morbius I will have to authenticate as morbius but should I save something to that share it will save with owner = homeuser.

---

### Post by Crackouch on 2012-03-23
I did create a samba user as well and it still locked me out.
 
and I did mean directory mask (I mistyped in the forum).
 
I'd to give it another shot. How do I undo everything and start from scratch?
 
Thanks Morbius1, Crackouch

---

### Post by Crackouch on 2012-04-15
Morbius1...Thanks for helping. But I am not quite there yet
 
I whittled down my commands as follows:

1. On my Ubuntu box, I created a folder under / .

sudo mkdir NetworkFileSystem

2. Then I installed Samba and altered the /etc/samba/smb.conf (I made a copy) to recognize the workgroup and create the samba share:

workgroup = HOMENET

[NetworkFileSystem]
path = /NetworkFileSystem
browseable = yes
read only = no
guest ok = no
force user = homeuser

3. I created an Ubuntu user and added it to the group

sudo useradd -p "Password1" homeuser

4. I created a Samba user
 
sudo smbpasswd -a homeuser
 
Now, with my Windows 7 box, I was able to map the drive. But I cannot copy folders and files from an external USB drive to it. It says I don't have the permissions to do so.

Please help when you can. Thanks, Dave

---

### Post by Morbius1 on 2012-04-16
"sudo mkdir /NetworkFileSystem" created a folder that is owned by root with full access to root but only read access to everyone else. You need to make it write accessible for someone other that root. One way:
```
sudo chmod 0777 /NetworkFileSystem 
```

---

### Post by Crackouch on 2012-04-16
Thanks so much again. I have fully documented the procedure this time around!!
 
Crackouch

---

### Post by acanning on 2012-04-25
Hello All

I wonder if you might be able to help. I have a common setup in that I want to use an Ubuntu machine for basic file sharing within a small Windows 7 network. I can create shares using Samba with guest access but I really want proper secure user access although all users will access the same folder on the server. The problem is that it doesn’t work. Windows can see the shared folder but always asks for a password when I try to access the folder. The username/password I enter never works.

This is what I have done so far... 

Installed Ubuntu Desktop ver 10.04 (as my server)

Installed Samba

Created User ‘Ash’ on Server using the same password as my Windows 7 machine.

Also created a samba user using command ‘sudo smbpasswd –a Ash’

My Samba config file is default other than this section at the end;

[MyFiles]
path = /Home/server/Public/Dropbox/
available = yes    
browseable = yes
read only = no
guest ok = no
writable = yes

What am I doing wrong? Why does my Windows machine always ask for a password and then not let me access the folder saying that my login or password isn’t correct. When I boot-up the Windows machine I have to enter my username and password so I thought that should cover the login to the shared folder. If I enable guest access then it works without asking for a password.

I haven’t enabled sharing using the Nautilis file browser...that’s right isn’t it? I configure using the smb.conf file.

I don’t operate a domain only a workgroup called ‘workgroup’.

I know lots of people have problems like this but I feel like I’ve tried everything with no success. Anyone have any suggestions.

Many thanks

---

### Post by acanning on 2012-04-26
I think I may have posted my question in the wrong place. I'll re-post in a more up to date area.
 
Thanks

---

### Post by Fraoch on 2012-05-14
You know, as old as this HOWTO is...it deserves a bump.

Sometimes when I upgrade Ubuntu I lose access to all my network shares and have to start all over again.  This was the case with the upgrade to 12.04.

Each upgrade there are better and better GUI tools to configure samba but none of them seem to work for me.  This HOWTO just always works.

Thanks to the OP!

---

### Post by hanhanafi on 2012-05-21
Hello, I have some problem with my Samba server. 
I can't configure Samba with IPV6.
Can you tell me how to solve it? 
My computer server use Ubuntu 10.4 and client use windows 7
Sorry my english is bad :grin:

---

### Post by Crackouch on 2012-05-30
Thanks for previous help.
 
My Samba shares suddenly became offline on my Windows 7 machine and I cannot access the contents saying "Access is denied," "you don't have the permissions," etc.
 
For some time, my original /etc/samba/smb.conf-iguration worked like a charm, as follows:
 
workgroup = HOMENET
 
[NetworkFileSystem]
path = /NetworkFileSystem
browseable = yes
read only = no
guest ok = no
force user = homeuser
...Along with the proper permissions statement:  sudo chmod 0777 /NetworkFileSystem
 
I decided to add a 1TB drive to my Ubuntu machine to store my music. I mounted the drive (set up automatically at boot), set the same permissions as /NetworkFileSystem, and then added another share to the Samba file:
 
[MusicFiles]
path = /media/MusicFiles
browseable = yes
read only = no
guest ok = no
force user = homeuser
 
It originally worked OK. Both shares were accessible and I was able to play the Ubuntu music files on my W7 box. Then I shut down I machines for the day. When I turned them on again, the W7 machine indicated that I could not connect to the network drives, even the NetworkFileSystem. I tried commenting out the MusicFiles share in my Samba file, unmapping and remapping the NetworkFileSystem share. The folders of that share appear with an "X" and I cannot get in them.
 
Please help if and when you can...
Thanks, Crackouch

---

### Post by Crackouch on 2012-07-05
> **Crackouch said:**
> Thanks for previous help.
 
My Samba shares suddenly became offline on my Windows 7 machine and I cannot access the contents saying "Access is denied," "you don't have the permissions," etc.
 
For some time, my original /etc/samba/smb.conf-iguration worked like a charm, as follows:
 
workgroup = HOMENET
 
[NetworkFileSystem]
path = /NetworkFileSystem
browseable = yes
read only = no
guest ok = no
force user = homeuser
...Along with the proper permissions statement: sudo chmod 0777 /NetworkFileSystem
 
I decided to add a 1TB drive to my Ubuntu machine to store my music. I mounted the drive (set up automatically at boot), set the same permissions as /NetworkFileSystem, and then added another share to the Samba file:
 
[MusicFiles]
path = /media/MusicFiles
browseable = yes
read only = no
guest ok = no
force user = homeuser
 
It originally worked OK. Both shares were accessible and I was able to play the Ubuntu music files on my W7 box. Then I shut down I machines for the day. When I turned them on again, the W7 machine indicated that I could not connect to the network drives, even the NetworkFileSystem. I tried commenting out the MusicFiles share in my Samba file, unmapping and remapping the NetworkFileSystem share. The folders of that share appear with an "X" and I cannot get in them.
 
Please help if and when you can...
Thanks, Crackouch
 
I found out on my own. More of a Windows 7 issues. I had to remount the drives.

---

### Post by c2tarun on 2012-07-09
> **Fraoch said:**
> You know, as old as this HOWTO is...it deserves a bump.
 
Sometimes when I upgrade Ubuntu I lose access to all my network shares and have to start all over again. This was the case with the upgrade to 12.04.
 
Each upgrade there are better and better GUI tools to configure samba but none of them seem to work for me. This HOWTO just always works.
 
Thanks to the OP!
 
 
I agree, anyone who setup Samba on *buntu 12.04 can please share the tutorial. It will be helpful to all of us.

---

### Post by GaryRixon on 2012-07-09
Thank you so much. I'm not lying when I say I have been attempting to setup a password protected samba share for about a month now. 

I don't have masses of free time, but I really enjoy administrating the servers I have setup and you have no doubt saved me many hours of tinkering.

I simply had no idea you had to add a samba user.

Here is my home network/server setup if you're interested...[IMG]http://s12.postimage.org/89630yyjh/323173_468927506451291_917989042_o.jpg[/IMG]

---

### Post by megamister on 2012-08-07
Samba Server and Windows machine isn't very difficult with a simple little tool called **[SIZE="3"]System-Config-Samba[/SIZE]** a simple Graphical Samba tool. 

Once you install it with your favorite package manager it will be listed in your menu as &#8220;**Samba**&#8221;. Some versions you will get an error saying **[SIZE="3"]KDEInit could not launch 'gksu' Could not find 'gksu'  executable[/SIZE]**. Don't worry like I did it's only a little glitch. Just means you have to go to a Terminal and type &#8220;**Sudo system-config-samba**&#8221; then enter the root password. I'm sure there is a more complicated way to fix it...but I don't know it. 

Once you get it up and running, [COLOR="Red"][SIZE="3"]set up a new Samba User and password[/SIZE][/COLOR](REQUIRED for Samba operation and must be a local user) from the drop down menu. Then click the green + icon and browse the folders to your desired Targeted share folder.

Once folder is selected you can set a name for your share that will show up on all other computers.
You will also have to setup the permissions for access, being write or read only. 

Then click the tab labeled Access this is where you select who can access the share, a user from the list(your new user should be listed) or select Everyone. If you select a user, that will require a username and password to be entered to access the shared folder.

Once you click OK your share should be listed and shared. You also have to make sure your permissions are set correctly for the actual shared folder and the files. For example if your Samba share says everyone can access, but the actual file permissions say read only then your gonna have a problem. If you make changes to your Samba share, they likely won't be immediately initiated. Sometimes you have to restart the Samba server or logoff the client machine then login again to get the changes. 
 
I have used **System-Config-Samba** currently on Kubuntu 12.10 Alpha, Linux Mint 13(12.04)  and earlier versions of Kubuntu.

---

### Post by Morbius1 on 2012-08-08
The value of this HowTo - [COLOR=Blue]which is no longer being maintained BTW since the author has left Ubuntu[/COLOR] - is that it's a step by step to changing your Ubuntu machine into a WINS server. The post above is something else.

And if you want ease of use you can create a share without installing system-config-samba simply by using Nautilus. Make believe you are sitting in from of a WinXP machine and you want to create a Windows Simple Share ( guest accessible ):
Right click a file you own.
Select sharing options.
Select all the options.
Done.

You can also use it to create a Private share requiring authentication. It automatically creates the Samba share and modifies permissions so you don't have to.

KDE can do this as well but you need to install "kdenetwork-filesharing". Curiously in KDE's case it doesn't automatically modify permissions. XFCE can't do this but in a few minutes you can enable it by creating your own Thunar Custom Actions.

The one thing nautilus-share or  kdenetwork-filesharing can't do is provide a GUI to add a user to the Samba password database but in most cases people are only creating guest shares so it's not necessary to create users and add them to the samba password database.

---

### Post by megamister on 2012-08-08
> **Morbius1 said:**
>  The post above is something else.


Maybe I'm mistaken but the title is "Setup Samba peer-to-peer with Windows" then the OP goes into modifying the Samba config files. Which isn't really necessary anymore and will likely confuse and cause more problems unless you really know what your doing. 

Recently people are asking how to set it up with newer versions. So I gave a simple little pkg that can be used to make it pretty easy and painless. 

Most of the newer versions can share from the file properties etc. But that can also get complicated. I started out sharing like that but then for managing those files it gets confusing. You have to know and remember all of your shares and their paths for management. If you just have 1 or 2. Not too big of a problem but if you have multiple and maybe longer paths. Then it gets hard to keep track of all your shares. So especially for beginners using **System-Config-Samba** is just simple to use and all your shares are listed in one place.

---

### Post by Morbius1 on 2012-08-09
Fair enough but this is a HowTo not a request for help. If you were to create a HowTo on using system-config-samba and I came in and said "No, a better way is to create Samba Usershares using Nautilus" I suspect you would consider that rude.

Perhaps you should create your own Howto. If you do you might want to clean it up a bit:
> Once you get it up and running, [COLOR=Red][SIZE=3]set up a new Samba User and password[/SIZE][/COLOR] from the drop down menu.There's 2 things wrong with that:

[1] You can't do that from the drop down menu. You can add an existing local user to the samba password database from the drop down menu but you can't create a new user from there. You would need to create a local user on the server first and then use the drop down menu to add him to the samba password database.

[2] You don't need to do any of that if all you are doing is creating guest accessible ( Public ) shares.
> Maybe I'm mistaken but the title is "Setup Samba peer-to-peer with  Windows" then the OP goes into modifying the Samba config files. Which  isn't really necessary anymore and will likely confuse and cause more  problems unless you really know what your doing.This HowTo is about peer-to-peer but he is tackling a specific problem of netbios name resolution by creating a WINS server on the Linux box:
> wins support = yesWould I have done it that way - No. If this is a simple home lan with everyone on the same subnet is that even necessary - I would argue that it is not. But the beauty of this HowTo is that even though it is no longer maintained and even though it is now 6 years old it is still relevant and still works.

And your description would require a user to alter smb.conf anyway because if it's a peer-to-peer setup it won't work. The remote user will save a file with owner as either "nobody" or a username with read only access to the user on the server. If you want the server user to have write access to newly added files something will have to be done. One way to do that is something suggested in the original HowTo:
> force user = YOUR_USERNAMEStormbringer was(is) a pretty smart fella.

[COLOR=Blue][I]Totally unrelated side note:
> You have to know and remember all of your shares and their paths for  management. If you just have 1 or 2. Not too big of a problem but if you  have multiple and maybe longer paths. Then it gets hard to keep track  of all your shares. So especially for beginners using **System-Config-Samba** is just simple to use and all your shares are listed in one place.     Nautilus-share is patterned after a WinXP simple share. It's icon in Nautilus changes to indicate that it is shared just like in Windows. It even automatically modifies Linux permissions so that it's consistent with how you shared the folder. You can always get a complete listing of these shares by issuing:
```
net usershare info --long
```It tells you the path to the shared folder and how you are sharing it.[/I][/COLOR]

---

### Post by megamister on 2012-08-09
See this is why we have forums, to learn and discuss topics. I posted  related  info based on the comments of the 2 previous users before me that were presumably looking for simplified info like I posted. Otherwise they would have used the original info and applied it to their problem and  likely solved it. But they didn't/couldn't so asked for help, so I tried to assist based on what asked. Maybe some would consider it thread jacking, but I think it's very closely related. We have to remember some will read these comments for many years to come. We just may answer someone's question 6 yrs later. :KS



 > **Morbius1 said:**
> Fair enough but this is a HowTo not a request for help. If you were to create a HowTo on using system-config-samba and I came in and said "No, a better way is to create Samba Usershares using Nautilus" I suspect you would consider that rude.

Well apparently the OP is not around anymore, so his opinions are kinda irrelevant. But honestly if I read the 2 previous posts and then mine, it seems to fit. So no I wouldn't consider it rude. And I never once said a “better way”.  If someone interprets my wording as that, then thats their opinion\interpretation. And honestly if you jumped and said that, I would likely respond, yes that is a another way. Then maybe discuss the pros and cons of either. But that's just me. I will generally just take the situation at face value. Questions were asked and someone answered with what they thought would help. Why should I think that's rude? Answer: I wouldn't.


If this was strictly a How To and no related discussion, I don't think we would have 106 pages.




> **Morbius1 said:**
> Perhaps you should create your own Howto. 

Sorry I don't think I'm anywhere near that point yet. 




> **Morbius1 said:**
> 
[1] You can't do that from the drop down menu. You can add an existing local user to the samba password database from the drop down menu but you can't create a new user from there. You would need to create a local user on the server first and then use the drop down menu to add him to the samba password database.

I thought I made it pretty clear in my wording, from the drop down menu you make a new [COLOR="Red"][SIZE="3"]Samba User[/SIZE][/COLOR], **not** a Local User. From the Preferences menu you click on “Samba Users” and you get a popup that says “Create New Samba User”. Then you get a popup that gives options for selecting a Unix Username with a list of Local Users etc. A Windows Username box, Samba Password and Confirm Samba Password. So apparently **I CAN**, create a new Samba User just like I stated. That differentiation threw me off for a bit when I was first setting things up too. Most of the tutorials I read would just reference a "user" or say something like set up a new user if you don't have one. Well if your new to it, your gonna think oh I already have one set up when I installed(meaning a local user). Which is obviously wrong, and also why I tried to make it very clear the first thing you have to do is set up a [COLOR="Red"][SIZE="3"]New Samba User. [/SIZE][/COLOR]But just to clarify the issue. I'm gonna slightly modify my post to say a Samba User is required.




I did not post a comprehensive How To, with all the options, scenarios and settings listed. I listed the simple basics that would apply to people asking how do I set up Samba. 


> **GaryRixon said:**
> Thank you so much. I'm not lying when I say I have been attempting to setup a password protected samba share for about a month now. 

I don't have masses of free time, but I really enjoy administrating the servers I have setup and you have no doubt saved me many hours of tinkering.

I simply had no idea you had to add a samba user.



> **c2tarun said:**
> I agree, anyone who setup Samba on *buntu 12.04 can please share the tutorial. It will be helpful to all of us.





> **Morbius1 said:**
> 
And your description would require a user to alter smb.conf anyway because if it's a peer-to-peer setup it won't work. The remote user will save a file with owner as either "nobody" or a username with read only access to the user on the server. If you want the server user to have write access to newly added files something will have to be done. One way to do that is something suggested in the original HowTo:
Stormbringer was(is) a pretty smart fella.


That is a good note to add, that will likely help somebody. I may have a use for that option. I'm sure he was\is a smart fella. But I don't know him so I will take your word on that. 





> **Morbius1 said:**
> 
[COLOR=Blue][I]Totally unrelated side note:
Nautilus-share is patterned after a WinXP simple share. It's icon in Nautilus changes to indicate that it is shared just like in Windows. It even automatically modifies Linux permissions so that it's consistent with how you shared the folder. You can always get a complete listing of these shares by issuing:
```
net usershare info --long
```It tells you the path to the shared folder and how you are sharing it.[/I][/COLOR]

I'm personally aware it's very similar to XP simple share, as that's what I started sharing with. Then when I switched to Linux. I also did it that way too until I started needing more customization and found a better\efficient way of managing what I needed. 

That syntax is helpful thanks, I added it to my references. The problem is though that I think a majority of Linux users are not command line comfortable, at least the newer ones. Sure everything CAN be done from the command line as the GUI(Graphical User Interface) is only a visual way of translating to commands in a Terminal. A lot of newer users are transferring from a Windows system and are general users. But the more you begin using Linux the more you're forced to learn and get comfortable with the Terminal. 

So we need simpler visual tools to be able to do things until we gain a better understanding of how and why. Then it's much easier to go in and start editing config files. Many of the admins and veteran Linux users forget what it's like to be a newer user and trying to do simple things when you don't know all the commands, syntax, paths, and understanding of the file system.  Then when your trying to research a solution you find 4 pages of command line instructions telling you how to do it. With no indication of which versions it will work with, or sometimes no indication of if or which pkgs or repositories needing to be updated first... Or... I could go on and on.

I know I personally have read hundreds if not thousands of posts sometimes related and sometimes only slightly. But one line in a comment clicked on the light bulb and pointed me in the right direction. Such as nice big letters saying a new samba user must be created...Doh!!!

---

### Post by Morbius1 on 2012-08-09
> Once you get it up and running, [COLOR=Red][SIZE=3]set up a new Samba User and password[/SIZE][/COLOR](REQUIRED for Samba) from the drop down menuYou do not create a samba user from the drop down menu. The menu is a list of all the current local users on your system. You create a local user using "User Accounts" and then add that user to the samba password database giving him a samba password.

So there's only 2 ways you can use this utility:

[1] Create a local user named say .. bob... that matches the client users name using User Accounts. Then use the samba utility to add his name to the database:
Unix username = bob
Windows username = bob

[2] You can if you really want to mess yourself up just use the samba utility:
UNIX Username = avahi
[COLOR=Blue]*in this scenario we didn't create the user bob in User Accounts so we can't select him from the drop down list.*[/COLOR]
Windows Username = bob

In this case 2 things will happen:
** A line will be added to smb.conf if it isn't there already:
> username map = /etc/samba/smbusers** If you actually go to that file you will see that the user "bob" has been mapped to the user avahi:
> avahi = bobThat's a mess. 

And there is one last thing on the whole issue of samba users and passwords. If you only create guest accessible shares you don't have to do any of this.

---

### Post by megamister on 2012-08-09
What the pkg is doing behind the scenes gets complicated and like you said messy. That's why I said...Create new Samba User. That's the way the it's labeled, that's what people are going to think while setting it up. Many  tutorials I have read says create a samba user. You enter the username and password in the smb.conf file. Without the info there it doesn't work, and you are essentially creating an entry that wasn't there. So it can be argued that it's not created. But by adding the entry it is created. It is a requirement that the user is already a local account. But that is getting slightly off track again. Again this gets very complicated and annoyingly so especially for someone just trying to set up some simple shares. Once you start to understand what's going then you can start getting into technicalities and modifying files. 

But again to clarify for those who don't know or understand, I will add a note the Samba User is a local user acct.

You clearly have a great understanding of how it all works, excellent you can probably answer some of my other more technical questions. But what comes easy and natural for you is very foreign and difficult for someone just trying to set something simple up. There is a good term for doing things it's KISS, **K**eep **I**t **S**imple **S**tupid. I don't need to understand how my car engine actually atomizes the fuel and air to burn in combustion to drive my car to the store. Until I'm ready to dig in and learn about it.

Which brings up another question, if I recall there is a user group "smb". So an admin could add a local user to the smb group, would that create an entry in the smb.conf? But a password would still need to be added correct?

---

### Post by Morbius1 on 2012-08-10
> Once you get it up and running, [COLOR=Red][SIZE=3]set up a new Samba User and password[/SIZE][/COLOR](REQUIRED for Samba operation and must be a local user) from the drop down menu. ** That's closer but you never explained that he needs to create the local user first using something like "User Accounts" before using system-config-samba.

** Adding a Samba user is not required for Samba operation. It is only required if you create a Private share that requires authentication. If you create a Public share that allows anonymous "guest" access then one is not required.
> You enter the username and password in the smb.conf file. Without the  info there it doesn't work, and you are essentially creating an entry  that wasn't there.Smb.conf has no entries nor does it have any provisions for a user's username and password.
> But what comes easy and natural for you is very foreign and difficult  for someone just trying to set something simple up. There is a good term  for doing things it's KISS, **K**eep **I**t **S**imple **S**tupid.
Which is why in a more appropriate setting - like not in someone's HowTo - I always recommend the following:

Step1: Make believe you are sitting in front of a WinXP machine
Step2: Open the File Manager - Nautilus
Step3: Right click on a folder you own and select "Sharing Options"

*Note: If you are not the owner of the folder then run nautilus as root: "gksu nautilus"*

It will create the samba share, adjust the Linux permissions automatically, and change the icon of the folder being shared to indicate that it is shared. It can't do everything a Classic Samba Share can do but neither can system-config-samba.

---

### Post by Intacto on 2012-09-13
Hello. I recently installed linux mint on my acer aspire one d250 and I am in urgent need to share files between the linux and a windows7 OS. I used your how-to guide to configure my samba (with slide differences for the mint part) and it seems it worked. Users and passwords created normally and no errors occured BUT, when I write down \\ip-address of the linux PC\MyFiles and write down any of the created users and passwords i get this error in the windows PC: \\ip-address\Myfiles is not accessable. You may not have the rights to use this network resource. Try contacting the server administrator to gain access. 
The group name could not be found.

I am pretty sure I gave identical name to both the linux/win7 network groups and I never got any error while configuring the samba. 
Any ideas what might have gone wrong ?
Thanks in advance.
Intacto.

---

### Post by megamister on 2012-09-14
> **Intacto said:**
> Hello. I recently installed linux mint on my acer aspire one d250 and I am in urgent need to share files between the linux and a windows7 OS. I used your how-to guide to configure my samba (with slide differences for the mint part) and it seems it worked. Users and passwords created normally and no errors occured BUT, when I write down \\ip-address of the linux PC\MyFiles and write down any of the created users and passwords i get this error in the windows PC: \\ip-address\Myfiles is not accessable. You may not have the rights to use this network resource. Try contacting the server administrator to gain access. 
The group name could not be found.

I am pretty sure I gave identical name to both the linux/win7 network groups and I never got any error while configuring the samba. 
Any ideas what might have gone wrong ?
Thanks in advance.
Intacto.


I'm not sure who your directing your question at since you don't say, but I will try to help. My guess is you have permission issues. You might try navigating with a Root level file manager to your folders\files and check your permissions. Make sure your owner, group and other permissions are set correctly for your goals. Be sure to select "Apply permissions to Enclosed Files". 

Depending on what your permissions are set as you may need to change them via Terminal. I have had cases where the changes didn't seem to take effect until I used the Terminal and Chmod or chown etc.

Otherwise another issue with Win7 and Vista is fixed with this info I found after hours of researching. Only to find a couple simple little fixes.

Basically, you have to add a DWORD value called LmCompatibilityLevel to: 

[COLOR="Red"]HKLM|System|CurrentControlSet|Control|Lsa and set the value to 2.
LmCompatibilityLevel [/COLOR]


Explanation:

HKLM\SYSTEM\CurrentControlSet\Control\Lsa 
Data type	
Range	
Default value

REG_DWORD 	
0–5 	
0 


Description 

Specifies the mode of authentication and session security to be used for network logons.
Value	
Meaning

0	
Clients use LM and NTLM authentication, but they never use NTLMv2 session security. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

1	
Clients use LM and NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

2	
Clients use only NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controller accepts LM, NTLM, and NTLMv2 authentication.

3	
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

4	
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM authentication responses, but it accepts NTLM and NTLMv2.

5	
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM and NTLM authentication responses, but it accepts NTLMv2.
Activation method 

You must restart Windows to make changes to this entry effective.

 Note

To set a client running Windows NT Service Pack 4 to level 3 security or higher, the domain controllers for the user's account domains must already be upgraded to Service Pack 4.

For more information about operating-system interoperability and session security settings , see the Microsoft Knowledge Base link on the Web Resources page. Search the Knowledge Base for Article Q147706 or for the keywords LM authentication. 






**** For inability to access password share as standard user

to configure the EnableLinkedConnections registry value 
Click Start, type regedit in the Start programs and files box, and then press ENTER.
Locate and then right-click the registry subkey 

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System.

Point to New, and then click DWORD Value.
Type EnableLinkedConnections, and then press ENTER.
Right-click EnableLinkedConnections, and then click Modify.
In the Value data box, type 1, and then click OK.

---

### Post by Morbius1 on 2012-09-15
> **Intacto said:**
> Hello. I recently installed linux mint on my acer aspire one d250 and I am in urgent need to share files between the linux and a windows7 OS. I used your how-to guide to configure my samba (with slide differences for the mint part) and it seems it worked. Users and passwords created normally and no errors occured BUT, when I write down \\ip-address of the linux PC\MyFiles and write down any of the created users and passwords i get this error in the windows PC: \\ip-address\Myfiles is not accessable. You may not have the rights to use this network resource. Try contacting the server administrator to gain access. 
The group name could not be found.

I am pretty sure I gave identical name to both the linux/win7 network groups and I never got any error while configuring the samba. 
Any ideas what might have gone wrong ?
Thanks in advance.
Intacto.
Before you start monkeying around the the registry in Win7 I would suggest the following:

** Start your own thread.

This thread is labeled "Outdated Tutorials and Tips" because the original author is no longer a member of the forum and no longer uses Ubuntu. BTW, despite it being called outdated it's still the best HowTo in this forum explaining how to set up a Linux WINS server ;).

** When you do start your own thread posting the output of the following commands will help in diagnosing your problem:

```
testparm -s
net usershare info --long
smbtree


```

---

