---
title: "Can not access Windows shares"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by RandyN on 2013-03-15
When I was evaluating ubuntu 12.1 with the LiveCD I was able to access shares on my Win7 machine. Now with ubuntu fully installed I can not...I get a "Failed to mount windows share" error.

I've tried to follow various guides on the forums but have gotten nowhere. Running smbtree in a terminal window shows

WORKGROUP
      //DAMBOMB

I've turned off the Win7 HOMEGROUP feature. Using the Home Folder and Browse Network shows the shares but I can't connect with the aforementioned error.

Any suggestions?
TIA,
Randy

---

### Post by solarghost on 2013-03-16
Is the share you are trying to connect to on a computer connected to a Windows Domain?

In Nautilus (assuming you are using Nautilus) try going to File -> Connect To Server, then select Windows share. If you are connecting to a computer that's on a Windows domain make sure you type the domain in ALL CAPS.

EDIT:
Also now that I've thought of it have any configurations changed since your live cd session? Can you ping your Windows box from you linux box?

---

### Post by RandyN on 2013-03-16
I was able to connect to the windows box via the path you mentioned but it still failed to mount the share. I'm not sure about being able to ping (on my win7 pc atm).

On the LiveCD the wired network connection was not working but the wireless adapter was and once installed the Ubuntu machine used the wired connection. Didn't really take notice of that until you asked about a change up in configuration. Maybe there in lies a hint.

What I ended up doing was a 'reverse' share. I had initially tried to install samba through the terminal (most online suggestions use the terminal for installing stuff) but ended up with an error message. After a bit more reading I installed Samba using Software Center and sharing the folder on the ubuntu machine. I had no problems seeing that share from the windows pc and was able to drag the files I needed to it that way.

I'll have to satisfy myself with that for now but if you have an idea about why the wireless connection worked for shares over the wired one I'd be interested to hear as I will be attempting this again at some point.

---

### Post by prodigy_ on 2013-03-16
Well, you really need to check some things if you want to understand what's happening. First of all, can you can ping the Windows machine by its host name? If not, you probably want to use some sort of name resolution (e.g. Avahi/Bonjour).

---

### Post by RandyN on 2013-03-16
Ok...I can not ping the host name (tried in ALL CAPS and Proper Case) but I can ping the (static) IP address. I can ping our ISP hostname.

The two machines are connected by a switch (and a pfsense router also connects to the switch but does not sit between the two pc's).

Personal File Sharing is installed and I just installed Avahi Zeroconf Browser.

I don't know if this makes a difference but the Win7 machine is set to a static IP and not a DHCP assigned address whereas the Ubuntu 12.1 machine is DHCP. Our iPad (also DHCP) shows up in the Avahi Discovery screen but so far no Win7 which seems odd since I can see the shares via Nautilus (just can't mount them).

---

### Post by prodigy_ on 2013-03-16
> **RandyN said:**
> I can ping the (static) IP address
If you use static IPs, you can simply edit hosts file. In Linux it's **/etc/hosts**, in Windows it's **%windir%\system32\drivers\etc\hosts**. Format: **ip-address hostname**. Example:
```
192.168.0.1 myhosthame
```

---

### Post by RandyN on 2013-03-16
Well things got a little bit stranger. I added the static IP address for the win7 machine to etc/hosts and I can now ping it by hostname but still can't mount any of the shares (I also tried to do so with the McAfee firewall(on the win7 pc) turned off).

Now for the odd part. I have a WinXP machine (which has a dynamic IP address) on the network, which was on a different workgroup called group1. I changed it to WORKGROUP to put everything on the same group. There are two music directories shared on that machine  and I can access those files and play them just fine. Oddly enough I can not access the 'SharedDocs' folder.

To give you a better idea of the network layout:
192.168.1.1 - pfsense router with  static WAN IP plugged into a
gigabit switch which then has plugged into it
192.168.1.2 - wireless access point
192.168.1.3 - win7 machine (contains videos and photos). The win7 pc can see the ubuntu share setup with Samba.
I have the router assign dynamic addresses to the kids machines 192.168.1.100 - 192.168.1.125 so I don't have to mess with static ip's when they come to visit.

Thanks for the input so far...very much appreciated.

---

### Post by prodigy_ on 2013-03-17
Need to do some more diagnostics. Try these command (from the Linux box):
```
smblient //name/share -u username # substitute actual machine, share and user names
```
If you get no error, quit and proceed to:
```
sudo apt-get install cifs-utils
sudo mount -t cifs //name/share /mnt -o workgroup=WORKGROUP,user=username
```

If this also works, unmount with: ```
sudo umount /mnt
``` and make this a permanent solution via /etc/fstab as described [here](http://ubuntuforums.org/showthread.php?t=288534).

> Oddly enough I can not access the 'SharedDocs' folder.
What error message do you get?

---

### Post by RandyN on 2013-03-17
Ok...you may have to dumb down that first line for me as I'm not sure I'm doing it right. I enter:
```
smbclient //name/share -u randy # dabomb,win7share,randy
``` 
Connection to name failed (Error NT_STATUS_BAD_NETWORK_NAME) 

*edit* Light bulb goes on...everything after the # is a comment. Next post is corrected*edit*


When I try to connect to the "SharedDocs" on the WinXP machine I get the "Unable to mount location" "Failed to mount Windows Share" error.

I ran smbtree again and it now shows:

WORKGROUP
    \\RADOFF                 
        \\RADOFF\Printer            hp LaserJet 1320 PCL 6
        \\RADOFF\MP3                
        \\RADOFF\OlderTunes         
        \\RADOFF\SharedDocs         
        \\RADOFF\print$             Printer Drivers
        \\RADOFF\IPC$               Remote IPC    
    \\DABOMB

---

### Post by RandyN on 2013-03-18
```
smbclient //dabomb/win7share -U randy%mypass
```
Returned:
Domain=[DABOMB] OS=[Windows 7 Home Premium 7601 Service Pack 1] Server=[Windows 7 Home Premium 6.1]
and the prompt dropped to:
smb: />

Exited and went to next step. Already on the latest cifs-utils so went to the next command:

```
sudo mount -t cifs //dabomb/win7share /mnt -o workgroup=WORKGROUP,user=randy
```
This returns:
[sudo] password for randy: I entered my su password and it returns:
Password: I assume this is for the share so I enter my Win7 password and it returns:

 A blinking cursor and it just sits there. After 5-10 minutes I hit CTRL+C and got dumped back to the randy@dellcore2:~$ prompt. This all took a few tries but I hope I did everything correctly. Good thing this is all in the absolute beginners section ;)

A bit more reading and went back a step to the smb: /> prompt and did a directory listing:
smb: /> dir 
This returned the following error:
NT_STATUS_IO_TIMEOUT listing \*
smb: \> SMBecho failed (NT_STATUS_CONNECTION_RESET). The connection is disconnected now

---

### Post by prodigy_ on 2013-03-19
Looks like something's blocking SMB traffic. Firewall, perhaps? Try:
```
telnet dabomb 139
telnet dabomb 445
```

You should see something like:
```
Trying 192.168.0.1...
Connected to dabomb.
Escape character is '^]'.
```
in the output. If you don't, definitely check your firewall settings.

---

### Post by RandyN on 2013-03-20
Both:```

telnet dabomb 139
telnet dabomb 445 
```

With and without the McAfee firewall turned on resulted in:

```
Trying 192.168.1.3...
Connected to dabomb.
Escape character is '^]'.
Connection closed by foreign host.

```

The connection was closed after about 15 seconds or so.

---

### Post by RandyN on 2013-03-22
```
randy@dellcore2:~$ smbclient -L 192.168.1.3
Enter randy's password: 

Domain=[DABOMB] OS=[Windows 7 Home Premium 7601 Service Pack 1] Server=[Windows 7 Home Premium 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$       Disk      Remote Admin
    C$              Disk      Default share
    E$              Disk      Default share
    IPC$            IPC       Remote IPC
    K$              Disk      Default share
    PIcs            Disk      
    print$          Disk      Printer Drivers
    Q$              Disk      Default share
    Win7Share     Disk      
 
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

A clue here perhaps...

I checked and NetBIOS over TCP is enabled on the Win7  NIC.

---

### Post by RandyN on 2013-03-23
As per this [thread]("http://ubuntuforums.org/showthread.php?t=88206") I edited the /etc/nsswitch.conf and changed the line
```
hosts:          files dns
```
to
```
hosts:          files wins dns
```

Also made sure that winbind was installed and I can now browse the Win7 shares! Hurray! 

Thank you for your efforts to help me resolve this...you kept me going until persistence finally paid off. :)

---

