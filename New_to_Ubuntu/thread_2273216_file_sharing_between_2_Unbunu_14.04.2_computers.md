---
title: "file sharing between 2 Unbunu 14.04.2 computers"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by harlie_gilliam on 2015-04-11
Hi, I am very new to Ubuntu and I really need some help please. Here's the problem. I have set up 2 Ubuntu 14.04.2 computers. The first is a HP Stream Notebook with A WI-FI connection. The 2nd is a Dell Optiplex 620 desktop with a LAN (wired) connection. I am trying to set them up to share files over my local network via router. I have installed ssh client/server metapackage on both machines and followed a few different post that I have read and still no luck. I do have the files to share set up on both computers and they have the sharing arrows on them. I have opened nautilus server connect and have been able to find the other computer (laptop>desktop and desktop , laptop), got the password pop-up and signed in, but then the other computer doesn't show up. I would really appreciate any help. I must say the I have really been enjoying Ubuntu so far, I used to be a Windows fan until Windows 8.

---

### Post by dino99 on 2015-04-11
[http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/)

---

### Post by harlie_gilliam on 2015-04-11
Thank you for the reply, I'm going to try them out. I will update the results later. again thank you very much!

---

### Post by Bashing-om on 2015-04-11
harlie_gilliam; Hello;

In addition, here is some more thoughts on the mater.
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449) : easiest way to cp files 'tween two 'buntus that share the same router/house (Morbius1) - and other options.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Morbius1 on 2015-04-11
On the samba front in an all Linux network you might consider the following:

_Prerequisites_:
*** Make sure avahi is running:
```
sudo service ahavi-daemon start
```
*** And port 5353 must be open which it should be unless you've messed around with the firewall.

_Then_:
[1] Create an avahi service announcement file for samba:
```
gksu gedit /etc/avahi/services/samba.service
```
[2] Copy and paste the following into that file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SMB %h</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
*[COLOR=#0000cd]**Note**[/COLOR]: [COLOR=#0000cd]The only tricky thing about this is to make sure the very first line has no leading spaces in it or else it won't work. You will know you did it right when after saving it it changes colours like this:[/COLOR]*
[ATTACH=CONFIG]261227[/ATTACH]
On the other Ubuntu machine it will show up as "SMB *whatever-your-host-name-is*" under Browse Network.

As a side benefit it will also automatically show up under "Shared" on the side panel of Finder ( the OSX file manager ) should you have any MacBooks in the mix.

---

### Post by harlie_gilliam on 2015-04-11
I tried both of your suggestions with no luck. I have noticed that whenever I browse the network from either machine that neither one shows the other, but they do show both of my wireless printers. Thank you both for your replies, I have downloaded the Ubuntu manual and 6 other how to linux books to read. Knowledge is power.

---

### Post by Morbius1 on 2015-04-11
Can you ping one machine from the other this way:

From the laptop ping the desktop:
```
ping desktop.local
```
[COLOR=#0000cd]*Where: "desktop" is the host name of the desktop system. And don't forget the ".local" at the end.*[/COLOR]

---

### Post by harlie_gilliam on 2015-04-11
still not working

---

### Post by harlie_gilliam on 2015-04-12
Ok I have completely reloaded both machines with 14.o4.2 per Ubuntu manual. I have loaded ssh client/server meta package on both machines. I have installed wine and .net on both machines, not that it matters. When I browse the network, the only things showing up are my wireless printers and the windows network icon. I have pinged them and they are sending.

---

### Post by Morbius1 on 2015-04-12
SSH will not show up under Browse Network unless to tell it to so it's going to be the same process as it was before except with different modules and different ports:

[1] Create an avahi service announcement file for ssh:
```
gksu gedit /etc/avahi/services/ssh.service
```
[2] Copy and paste the following into that file:
```
<?xml version="1.0" standalone='no'?>
    <!DOCTYPE service-group SYSTEM "avahi-service.dtd">
    <service-group>
       <name replace-wildcards="yes">SSH %h</name>
       <service>
           <type>_sftp-ssh._tcp</type>
           <port>22</port>
       </service>
    </service-group>
```
You should see "SSH something"

Of course you can simply access the ssh server directly and bookmark it. Open up a terminal and run:
```
 nautilus ssh://host-name.local
```
Just change "host-name" to whatever the real host name is of the machine you are accessing.

---

### Post by harlie_gilliam on 2015-04-12
pin desktop. local replies unknown host

---

### Post by Morbius1 on 2015-04-12
*** What are the host names of each machine. Run the following command if you don't know:
```
hostname
```
*** Is avahi-daemon running:
```
sudo service avahi-daemon start
```
*** Turn off everybody's firewall:
```
sudo ufw disable
```
*** Can you ping each other by ip address. If you don't know what that is run this command:
```
nm-tool
```

---

