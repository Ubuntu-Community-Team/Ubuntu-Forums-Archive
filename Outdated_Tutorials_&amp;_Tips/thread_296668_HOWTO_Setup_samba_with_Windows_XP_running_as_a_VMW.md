---
title: "HOWTO: Setup samba with Windows XP running as a VMWare server guest"
date: 2006-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Ziggy72 on 2006-11-09
The full title of this howto should be:

"How to setup samba peer to peer with Windows XP which is running as a VMWare server guest on a Ubuntu Dapper host to share files easily"

Using VMWare server to run Windows programs which are not available on Linux will enable you to never have to dual boot again to run your essential Windows applications. 

To install VMWare server, follow the directions at:
	[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

Once VMWare is successfully installed and you have Windows XP installed as a guest, you should read Stormbringer's howto at:
	[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

This howto is very largely based on Stormbringer's work, but because I had so much difficulty in getting samba to connect to my Windows XP guest I thought some people might appreciate knowing what steps I finally used.

If you don't use Gnome, you'll have to make a few adjustments.

Ok, here we go...
1)Use Synaptic Package Manager to install samba, samba-common, smbclient and smbfs.

2)Use System -> Administration -> Shared folders to make a shared folder. I suggest you use /home/YOUR_NAME/samba. In Properties:
   a) Share with: SMB
   b) Name: MyFiles
   c) Tick Allow browsing folder
   d) In Windows sharing settings, &#8220;Domain/Workgroup&#8221; is MsHome (or     whatever your guest XP  machine is) and select &#8220;This computer is a WINS server&#8221;.
   e) Press OK, OK

3)Set permissions on your shared file:
```

sudo chmod 0777 /home/YOUR_NAME/samba

```

4)Stop samba:
```

sudo /etc/init.d/samba stop

```

5)Backup the original smb.conf file:
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.backup

```

6)Make a new smb.conf file:
```

sudo touch /etc/samba/smb.conf

```

7)Open smb.conf for editing:
```

sudo gedit /etc/samba/smb.conf

```

8)Paste the following into your smb.conf file (mostly copied from Stormbringer)...
(I've put *** (no)against the entries you may need to change immediately. Please remove the ***(nos) when you've finished editing.)
```

[global]
;General server settings
netbios name = Ubuntu***(1)
workgroup = Mshome***(2)
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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
path = /home/YOURNAME/samba***(3)
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = paul***(4)
force group = paul***(5)
available = yes
public = yes
writable = yes

```

9)Personalise your new smb.conf file by editing the ***(nos). You can do any other editing you want to do later when everything is up and running.
***(1) Use any sensible name, but remember what it is.
***(2) Use the same workgroup name as Windows XP (usually Mshome).
***(3) This is the  shared folder you created earlier
***(4 & 5) This is the username you use for Windows XP. Don't use spaces. If necessary, modify the username you use for your guest XP machine (Explorer->Control Panel->User Accounts).

10)Start samba:
```

sudo /etc/init.d/samba start

```

11)Add yourself as a samba user:
NOTE: You will be asked for a password - make sure you use the same as you use for login
```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

That's all for samba, now for the Windows part:
	
12)In the Windows XP machine VM -> Settings -> Ethernet, I chose Nat

13)Find out the ip of your linux box and the vmware connections by typing ifconfig in a Ubuntu terminal. You will probably see 4 or more ip addresses. Write down each of the 4 (or more) inet addr addresses.

14)In the Windows guest machine:
- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in each of the ip addresses you copied down from 13) above & click &#8220;Add&#8221; for each one
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot the guest Windows

15)In the Windows guestmachine:
- Click &#8220;Start&#8221;
- Right-click &#8220;My Computer&#8221;
- Click &#8220;Map Network Drive&#8221;
- Choose a folder letter
- In the Folder field type \\Ubuntu (or the netbios name you chose)\MyFiles(the name chosen for the Ubuntu shared folder)
- Tick &#8220;Reconnect at logon&#8221;
- Press &#8220;Finish&#8221;

If all has gone well, whatever you see in the Ubuntu shared drive will be seen in the nominated XP drive. Copying or moving files from/to Ubuntu and the XP guest is now very straightforward.

I've given these instructions in good faith and they represent what I had to do to get my samba connection working between my Ubuntu partition and its Win XP VMWare guest. If they don't work for you, I'm sorry but I doubt if there's a lot I can do to help because I am very new to Ubuntu. and I had to struggle for more than a day to get this working. Huge Credits to Peturr for the Howto:VMWare installation, and to Stormbringer for his Howto:Setup Samba Peer to Peer from which I borrowed freely.

Good luck...:)

---

### Post by boban on 2006-11-10
Good howto... But if you are a little paranoid about security, then I would suggest running samba only for interfaces supplied by vmware. To do it you should add to lines in global section of smb.config:

```

interfaces = vmnet8 vmnet1
bind interfaces only = true

```

Of course names of the interfaces can differ - see output of ifconfig...

---

### Post by Pitt Stains on 2006-11-28
> **Ziggy72 said:**
> 
***(4 & 5) This is the username you use for Windows XP. Don't use spaces. If necessary, modify the username you use for your guest XP machine (Explorer->Control Panel->User Accounts).

Wow, this might be the first time I post with useful information rather than a solicitation for assistance.

Changing your XP username as described above will not work as expected.  Let's say my XP username is "Pitt Stains" and I decide to change it to "pstains" to eliminate the space and make life with Samba easier.  When I click my start bar in Windows, it will now say "pstains" at the top rather than "Pitt Stains," but Samba will still require me to manually log in each time I try to connect to a network drive.  The old username is still the "official" system username; the new username is more of a display name or an alias.

This knowledge base article ([http://support.microsoft.com/default.aspx?scid=kb;en-us;811151](http://support.microsoft.com/default.aspx?scid=kb;en-us;811151)) helped me transfer most of the settings of "Pitt Stains" to a newly created account called "pstains."  It's not quite perfect, but I believe the only setting I had to change manually in the new account was the desktop background.

Best of luck!
-Pitt

---

### Post by Pitt Stains on 2006-12-19
And here's an even better solution: Don't change either of your usernames!

I'm not sure how I came across this, but here's the correct way to make Samba understand a Windows username with spaces.

In the [global] section of your smb.conf file, add this line:
```

username map = /etc/samba/smbusers

```

Then create a file called smbusers, put it in the appropriate directory, and write this to it:
```

#Unix_name = "Windows name with spaces"
pittstains = "Pitt Stains"

```

The line that begins with a # is just a comment, if you're new to all this, and obviously you should use your usernames and not mine!

---

### Post by amborle on 2006-12-20
Really nice guide! Worked out of the box for me! Thank you!

---

### Post by lastrite on 2006-12-28
Great guide! Got XP running via Vmware server on Kubuntu sharing files and printers flawlessly with other computers on my windows network.

Much appreciated Ziggy72! :D

---

### Post by kadalz on 2007-01-01
Hello:

I'm a nob here. I tried many times to follow this How To. I always stuck in the last step, where I tried to setup Map Network Drive. When I tried to put in Forder field: \\server\shared, I got the following error message: The network path \\server\shared could not be found. Here is my smb.conf. Hope somebody can give guidance, which I did wrong. BTW, I use Kubuntu 6.10.

```

[global]
;General server settings
netbios name = server
workgroup = home
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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

[Shared]
path = /home/altari/Shared
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = rais
force group = rais
available = yes
public = yes
writable = yes

```

Thank you,
Kadalz

---

### Post by likerice on 2007-01-02
thanks for the HowTo. these types of instructions are invaluable to n00bs such as myself.

i might suggest, however, that you add a note ("***(no)") next to the [MyFiles] field in your smb.conf file. i myself chose a different folder name in step 15 of your instructions when mapping the network drive on windows, while failing to amend my smb.conf file. 

but then again, i was inebriated at the time :cool:

---

### Post by Foxmike on 2007-01-05
Hi!  Thank you for the great guide!  Just a question: does "NAT" networking or "Bridged" networking makes a difference?  I'm using NAT networking, followed all those steps but I cannot access shared folders from an OS to the other.  The only shared folders I can access now are: in Windows, shared folders from Windows, and in Ubuntu, shared folders in Ubuntu.  I am using Edgy, if that makes a difference.

Thank you!

-FM

---

### Post by polkadotchickens on 2007-01-11
i have diligently followed these instructions, with no results.  i apparently don't have an internet connection from within my windows xp -- could this be the problem, potentially?  i don't really see how it would be, but it's just a guess, and i have to say i've beaten my head against this for a day, as has a much more linux-experienced friend, and i'm getting nowhere.  any help or ideas would be much appreciated.

---

### Post by baldercm on 2007-01-11
Hi everybody!
first, some answers:

@Foxmike: bridged networking creates a "bridge" like if your using your physical network card twice, once in the host OS (Ubuntu) and once in the guest OS (WinXP). NAT networking, instead, creates a local sub-net (with different ip addresses than the local network between your PC and the router) between the host and the guest OS. Take a look to the WinXP's ip setup I explain next:

@polkadotchickens: have you checked you have correctly setup your ip configuration in WinXP? Take a look at the VMWare's "Guest Operating System Installation Guide" ([here]("http://www.vmware.com/support/pubs/server_pubs.html")), where you will find a detailed guide to setup the ip's. Here's the NAT configuration from that guide:
> If you chose network address translation (NAT) for the virtual machine, look up the host machine&#697;s 
IP address. 
At a command prompt on a Windows host, type
```
ipconfig /all
```
At a command prompt on a Linux host, type
```
ifconfig
```
Note the host’s IP address for VMnet8 and change the last octet so it is greater than the last octet in 
the IP address of the host.
For example, if the host IP address is 192.168.160.1, the virtual machine’s IP address is 
192.168.160.###, where ### is any number greater than 2 and less than 128.
For the subnet mask, enter 255.255.255.0.
For the router gateway, enter the NAT service’s IP address (192.168.160.2 in this example).
Note that with Network Address Translation, there are two IP addresses in use on the host:
The IP address assigned to the interface for VMnet8 shows up in the ipconfig output with a 1 in the 
last octet.
The IP address used by the NAT device itself always uses 2 as the last octet.

I am using the router gateway ip as my primary DNS server, but you can use any DNS server of your choice.

Next, I have a question: I've setup my NAT networking ok, but in WinXP I only can see my VMWare host PC, and not all the other computers in my home network. They're all in the same workgroup. Any ideas?

Thank you

---

### Post by Xizor on 2007-01-14
This is a really great write-up and I appreciate it. Unfortunately I get an error at Map Network Drive when I enter my username and password. The error reads: 
"The mapped network drive could not be created because the following error has occurred: An extended error has occurred."

Does anyone know what this means and how I might fix it? Thanks.

---

### Post by redyaky on 2007-01-20
Just wanted to leave a quick thank you. This was so very helpful, and worked like a charm.

---

### Post by daverave999 on 2007-01-21
Worked perfectly for me too-thanks!

---

### Post by toGoq on 2007-01-23
@kadalz: do you have your firewall enabled? Smb uses ports 137-139 and 445, which have to be opened. By default these ports are open on XP built-in firewall, but on your Linux-host you'd need to set them open too.

---

### Post by Foxmike on 2007-01-23
@baldercm: thank you!  It finally worked out but I had to re-dualboot winxp anyway for video accel (which I didn't knew I would finally need...)  Anyway, setting up this thing was great learning!:) Thanks!

-FM

---

### Post by frogotronic on 2007-02-07
> **toGoq said:**
> @kadalz: do you have your firewall enabled? Smb uses ports 137-139 and 445, which have to be opened. By default these ports are open on XP built-in firewall, but on your Linux-host you'd need to set them open too.

Firstly, let me say a big THANKS for this HOWTO; it worked beautifully.  But, after shutting my machine down, I found I had to open this ports (via FIRESTARTER) to have the drive(s) connect.

Thanks Again.

---

### Post by frogotronic on 2007-02-09
> **boban said:**
> Good howto... But if you are a little paranoid about security, then I would suggest running samba only for interfaces supplied by vmware. To do it you should add to lines in global section of smb.config:

```

interfaces = vmnet8 vmnet1
bind interfaces only = true

```

Of course names of the interfaces can differ - see output of ifconfig...

If I add this command to my smb.config file, it breaks the file sharing.  WindowsXP cannot connect to the samba directory on my linux box

- CH

---

### Post by misha680 on 2007-02-15
> **cement_head said:**
> If I add this command to my smb.config file, it breaks the file sharing.  WindowsXP cannot connect to the samba directory on my linux box

- CH

One thing that is a problem is that samba starts before vmware does, so the vmnet1 and vmnet8 interfaces don't exist yet when samba starts and it doesn't recognize their creation later on. A quick solution for this is:
```
sudo /etc/init.d/samba restart
```
A more permanent fix:
```
sudo gedit /etc/rc.local
```
And add the following lines somewhere:
```
# Restart samba so it takes into consideration VMWare network interfaces
/etc/init.d/samba restart
```
This will just restart samba as the last thing that happens when your machine is booting, ensuring that the vmware networking devices are loaded.

Misha

---

### Post by jabbar on 2007-03-09
Followed the guide and things (eventually) worked. Had some little scares which required me resetting premissions on my /home/user directory and .dmrc file, but that was my fault. 

Which brings me to my main point here: I don't think you need to do a "chmod 0777 /home/USER/samba" - my setup seemed to work without doing any such operation. I would suggest against playing around with chmod - especially your home directory. Trust me on this :)

---

### Post by jabbar on 2007-03-09
> **cement_head said:**
> If I add this command to my smb.config file, it breaks the file sharing.  WindowsXP cannot connect to the samba directory on my linux box

- CH

This case warrants a criticism of the original post. Whoever posted the suggestion to amend the smb.conf this way should have actually TESTED to see if the solution works. Lots of people (myself included) have followed similar advise only to get more and more confused. I implore all posters to please verify your solution before posting as much heart-ache can be avoided.

Thanks.

---

### Post by jmvidalvia on 2007-03-25
For those who just copy-paste howto's, this line is wrong:

sudo chmod 0777 /home/YOUR_NAME/samba

It should be:

sudo chmod 777 /home/YOUR_NAME/samba 

The problem is that no error is shown when doing it, but you are not really changing permissions of the directory.

Great guide: it works great! Thank you very much!

---

### Post by golebara on 2007-04-02
This is a perfect guide. Thanks very much.

---

### Post by spacetree on 2007-04-09
Excellent, it worked in edgy with no need of editing the smb.conf, just adding and enabling the usr.

---

### Post by MysterMDD on 2007-04-15
Ziggy72: AWESOME HOWTO!!!!  I have been searching Google and the Forums for a couple of days now trying to find something to set this up (even had to take a break last night because my head hurt so much).  I wasn't searching for the right subject, I guess, but I came across your thread and, OMG IT WORKS!!!  You're awesome!  (Kudos also to the person who lead you to the solution [sorry, but I don't remember the screenname].)  It asked me to login, but if that's all I have to do every time, then so be it; that's completely fine with me.  I'm just thrilled that it's working.  Thanks again.

> **kadalz said:**
> Hello:

I'm a nob here. I tried many times to follow this How To. I always stuck in the last step, where I tried to setup Map Network Drive. When I tried to put in Forder field: \\server\shared, I got the following error message: The network path \\server\shared could not be found. Here is my smb.conf. Hope somebody can give guidance, which I did wrong. BTW, I use Kubuntu 6.10.

```

[global]
;General server settings
netbios name = server
workgroup = home
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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

[Shared]
path = /home/altari/Shared
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = rais
force group = rais
available = yes
public = yes
writable = yes

```

Thank you,
Kadalz

Kadalz:  I'm not sure if you've been told this yet or not, but one thing I notice right off hand is that you stated that you're trying to map (from the WinXP VM guest) to \\server\shared, but in the smb.conf file you have the share name listed as Shared (with a capital S instead of lower).  I'm fairly new to Linux, but one thing I've learned repeatedly is that it's very picky about matching cases, so it's entirely possible that this might be part of the problem.

Additionally here's the only noticable difference between your smb.conf file and mine (other than I have a couple of lines in the global settings that restrict connections to only my VM, because I'm kinda anal about unwanted connection... even to just a VM guest.  I think the big difference comes from the fact that I setup my share to allow my VM to write to it because I have a software repo folder in there that houses both Windows and Linux software, so I'd like the WinXP guest to be able to write to it directly as opposed to having to download the software twice just to be able to store it.

```

[hdd1$]
path = /media/hdd1
available = yes
browsable = yes
public = yes
writable = yes

```

Other than that, it looks like you're doing it right.  Hope this helps, if you haven't already gotten it solved.

---

### Post by andyturn on 2007-05-05
> **Xizor said:**
> This is a really great write-up and I appreciate it. Unfortunately I get an error at Map Network Drive when I enter my username and password. The error reads: 
"The mapped network drive could not be created because the following error has occurred: An extended error has occurred."

Does anyone know what this means and how I might fix it? Thanks.


I am having the exact same problem.  Does anyone have any suggestions?

---

### Post by Tookelso on 2007-05-17
Just a note -- I booted into my Windoze VMWare box, and installed the latest security updates.  I'm running Feisty with VMWare, and have a Windows XP installation on my VMWare.  I was previously able to see a share on my Ubuntu box that I'd set up using the instructions in this thread.  However, after this security update, I kept getting denied when trying to access the share folder from my Windows XP VMWare installation.

I found that the Windows firewall settings were preventing my Windoze box from connecting via Samba.  (Maybe the firewall was installed on the security "update".)  

This might not be the correct/best fix, but I went to my Windoze VMWare computer, and went to the Control Panel.

Then, I went to Security Center, and selected "Windows Firewall" from the options on the main screen.  Then, I selected the "Exceptions" tab from the top of the screen.  I Checked the "File and Printer Sharing" box.

I was then able to connect to my host Ubuntu Samba share :-/

if I'm doing this the wrong way, please let me know.  Hope this helps someone else.

--Nate

---

### Post by laser_in_your_eye on 2007-10-31
Something fishy is going on with my samba configuration.  Everything has been running smoothly for 2 weeks, but now I cannot map the shared drive in xp.  I did not change any other settings.  Since then, I've tried deleting my previous shared folder and recreating one by following the tutorial again--no luck!  As far as I can tell, I haven't changed anything.  Can anyone help?!  I'm desperate.  I also tried the firewall exception listed above but that didn't fix it.  


THANKS!

UPDATE: After rebooting the host computer I was able to prompt the username/password box in XP, but I get the following error message:

The mapped network drive could not be created because the following error has occured:

An extended error has occured.


I know one other person posted about this, but does anyone know of a fix yet?

thanks

---

### Post by laser_in_your_eye on 2007-10-31
Problem fixed?

I have things working again.  I think the original problem (nothing mapping after it had been mapping fine before) was caused by the suspend function.  This usually works, but I think the network connections didn't quite return to normal after coming out of suspend.  

I eliminated the "extended error" by commenting out the "force user" and "force group" lines in the config file.  *Is that a major security risk?*  I put in the suggested "interface" lines in the global section to compensate for any loss in security, but I'm not sure it is enough.  

Thanks

---

### Post by DefianceX on 2007-11-04
> **laser_in_your_eye said:**
>  

I eliminated the "extended error" by commenting out the "force user" and "force group" lines in the config file.  *Is that a major security risk?*  I put in the suggested "interface" lines in the global section to compensate for any loss in security, but I'm not sure it is enough.  

Thanks

Thanks for this tip though I too would like to know any security issue concerning this.

---

### Post by mitchellmagro on 2007-11-16
HI thks for all! everything worked but when coming to map the ubuntu folder \\Ubuntu\myname it prompts me for the username and the password an when I fill and press enter it tells me cannot map drive or drive path not found! what is that?? Also I want to try and work the other way around and map an Xp folder and access it from ubuntu!! Anyone can help??

---

### Post by elec999 on 2007-11-17
I am able to see my ubuntu samba on the network, but when I click on myshare "Files" it says permssion denied.
Thanks

---

### Post by veloce on 2007-11-17
> **elec999 said:**
> I am able to see my ubuntu samba on the network, but when I click on myshare "Files" it says permssion denied.
Thanks

Sounds like a permissions issue on the directory - check that everyone has at least read access to the directory.

---

### Post by veloce on 2007-11-17
> **mitchellmagro said:**
> HI thks for all! everything worked but when coming to map the ubuntu folder \\Ubuntu\myname it prompts me for the username and the password an when I fill and press enter it tells me cannot map drive or drive path not found! what is that?? Also I want to try and work the other way around and map an Xp folder and access it from ubuntu!! Anyone can help??

No idea on the first, unless it is a permissions issue.

For the second, if you set sharing in XP you should be able to connect to it from Ubuntu.

---

### Post by abrichr on 2007-11-22
In the Map Network Drive dialogue, when I click finish, a window appears saying "Attempting to connect to \\Ubuntu\rda...", and a dialogue appears requesting my username and password.

My windows and ubuntu usernames are both rda.  I put in my username and password, but the dialogue reappears, with the username changed to "UBUNTU\rda".  I can enter the password in as many times as I want, and the dialogue reappears.

Any ideas?

---

### Post by veloce on 2007-11-22
> **abrichr said:**
> In the Map Network Drive dialogue, when I click finish, a window appears saying "Attempting to connect to \\Ubuntu\rda...", and a dialogue appears requesting my username and password.

My windows and ubuntu usernames are both rda.  I put in my username and password, but the dialogue reappears, with the username changed to "UBUNTU\rda".  I can enter the password in as many times as I want, and the dialogue reappears.

Any ideas?

Sorry, I have never done it that way round - I think I tried early on and had difficulties - I always connect from the host (ubuntu) to the vm (xp).

---

### Post by BirdZerk on 2007-12-01
When I do the last step in Windows guest I get this error

\\Ubuntu\MyFiles is not accessible
The user name could not be found

does anyone have an idea where to look?

My guest is windows 2000 pro
I am trying to connect to /media/hda2
and I am using bridge instead of nat
other than that everything is just as you wrote.

Do you need anymore info?

---

### Post by mwiley63 on 2008-03-31
Great guide!

I was able to set this up on 2 different virtual machines running 7.10 (one for my desktop and the other for my note book) by following the steps on the first post.  I now use my network drive mapped to an external usb as a way to manage code when I work on it from different computers :)

---

### Post by mwiley63 on 2008-03-31
> **BirdZerk said:**
> When I do the last step in Windows guest I get this error

\\Ubuntu\MyFiles is not accessible
The user name could not be found

does anyone have an idea where to look?

My guest is windows 2000 pro
I am trying to connect to /media/hda2
and I am using bridge instead of nat
other than that everything is just as you wrote.

Do you need anymore info?

Check your /etc/samba/smb.conf file.  Look for the following line:

netbios name = Ubuntu

if it is something else, then use that value instead of \\Ubuntu

Also go to system -> Administration -> Shared Folders
Select your folder (or drive in this case) and hit properties.  Then you should see this in the name text box:
MyFiles
If you called it something different then replace \MyFiles with your value.  

Hope this helps.

---

### Post by cosine352 on 2008-04-14
This is a perfect how to. It works like a charm in Ubuntu 7.10 with windows XP on Vmware.
Thanks a lot :popcorn::guitar:

---

### Post by mwiley63 on 2008-04-30
I have quoted the first thread below for convenience.  If it makes this post too long, I will edit it and take it out.

I was able to get this to work on Ubuntu 8.04 with some minor tweaks (the samba services that is, vmware-server is a whole different story).

The difference between my setup and this tutorial is that my set up is sharing an external USB hard drive's partition.  Sharing is different in 8.04 then it is in previous versions of Ubuntu.  For starters, you can only share folders under your own home directory (the directory you own).  You can't even share files that aren't owned by you that exist in your home directory by default.  So here is 4 steps I had to add on to the original tutorial to get this to work:

1)  Install the right dependencies

In 8.04 make sure you have samba, samba-common, and nautilus-share installed through synaptic manager (or use sudo apt-get install [name]).
```
sudo apt-get install samba samba-common nautilus-share
```

2) Manually mount your USB drive to your home directory

First run:
 ```
sudo fdisk -l
```
 to see the name of your USB device.  It should be something like /dev/sdX# where X is a letter and # is a number.  You then mount that drive to a folder that exists in your home directory like so:
```
mount /dev/sdX# /home/user_name/yourfolder
```

3)  Allow samba to share folders which a user does not own

```
sudo /etc/init.d/samba stop
```
Now edit your smb.conf file just like you would on the first thread of this tutorial, but add one line to the global section:
```
usershare owner only = False
```
Make sure the path matches your new folder and the name for that section matches the name you will give the shared folder.  When you are done run:
```
sudo /etc/init.d/samba stop
```

4) Share the folder containing the mounted device

Right click on the folder and select sharing options.  Give it the same name you gave for the section in your smb.conf file. 

After following the rest of the steps on the opening post of this thread everything should be working fine.


NOTE:

I used a fresh 8.04 install with an old vm disk, so the vm had everything configured already, I just had to update the path to the network drive since I changed the name of the shared folder.

Feel free to correct me if I missed anything or add to it.

> **Ziggy72 said:**
> The full title of this howto should be:

"How to setup samba peer to peer with Windows XP which is running as a VMWare server guest on a Ubuntu Dapper host to share files easily"

Using VMWare server to run Windows programs which are not available on Linux will enable you to never have to dual boot again to run your essential Windows applications. 

To install VMWare server, follow the directions at:
	[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

Once VMWare is successfully installed and you have Windows XP installed as a guest, you should read Stormbringer's howto at:
	[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

This howto is very largely based on Stormbringer's work, but because I had so much difficulty in getting samba to connect to my Windows XP guest I thought some people might appreciate knowing what steps I finally used.

If you don't use Gnome, you'll have to make a few adjustments.

Ok, here we go...
1)Use Synaptic Package Manager to install samba, samba-common, smbclient and smbfs.

2)Use System -> Administration -> Shared folders to make a shared folder. I suggest you use /home/YOUR_NAME/samba. In Properties:
   a) Share with: SMB
   b) Name: MyFiles
   c) Tick Allow browsing folder
   d) In Windows sharing settings, &#8220;Domain/Workgroup&#8221; is MsHome (or     whatever your guest XP  machine is) and select &#8220;This computer is a WINS server&#8221;.
   e) Press OK, OK

3)Set permissions on your shared file:
```

sudo chmod 0777 /home/YOUR_NAME/samba

```

4)Stop samba:
```

sudo /etc/init.d/samba stop

```

5)Backup the original smb.conf file:
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.backup

```

6)Make a new smb.conf file:
```

sudo touch /etc/samba/smb.conf

```

7)Open smb.conf for editing:
```

sudo gedit /etc/samba/smb.conf

```

8)Paste the following into your smb.conf file (mostly copied from Stormbringer)...
(I've put *** (no)against the entries you may need to change immediately. Please remove the ***(nos) when you've finished editing.)
```

[global]
;General server settings
netbios name = Ubuntu***(1)
workgroup = Mshome***(2)
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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
path = /home/YOURNAME/samba***(3)
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = paul***(4)
force group = paul***(5)
available = yes
public = yes
writable = yes

```

9)Personalise your new smb.conf file by editing the ***(nos). You can do any other editing you want to do later when everything is up and running.
***(1) Use any sensible name, but remember what it is.
***(2) Use the same workgroup name as Windows XP (usually Mshome).
***(3) This is the  shared folder you created earlier
***(4 & 5) This is the username you use for Windows XP. Don't use spaces. If necessary, modify the username you use for your guest XP machine (Explorer->Control Panel->User Accounts).

10)Start samba:
```

sudo /etc/init.d/samba start

```

11)Add yourself as a samba user:
NOTE: You will be asked for a password - make sure you use the same as you use for login
```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

That's all for samba, now for the Windows part:
	
12)In the Windows XP machine VM -> Settings -> Ethernet, I chose Nat

13)Find out the ip of your linux box and the vmware connections by typing ifconfig in a Ubuntu terminal. You will probably see 4 or more ip addresses. Write down each of the 4 (or more) inet addr addresses.

14)In the Windows guest machine:
- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in each of the ip addresses you copied down from 13) above & click &#8220;Add&#8221; for each one
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot the guest Windows

15)In the Windows guestmachine:
- Click &#8220;Start&#8221;
- Right-click &#8220;My Computer&#8221;
- Click &#8220;Map Network Drive&#8221;
- Choose a folder letter
- In the Folder field type \\Ubuntu (or the netbios name you chose)\MyFiles(the name chosen for the Ubuntu shared folder)
- Tick &#8220;Reconnect at logon&#8221;
- Press &#8220;Finish&#8221;

If all has gone well, whatever you see in the Ubuntu shared drive will be seen in the nominated XP drive. Copying or moving files from/to Ubuntu and the XP guest is now very straightforward.

I've given these instructions in good faith and they represent what I had to do to get my samba connection working between my Ubuntu partition and its Win XP VMWare guest. If they don't work for you, I'm sorry but I doubt if there's a lot I can do to help because I am very new to Ubuntu. and I had to struggle for more than a day to get this working. Huge Credits to Peturr for the Howto:VMWare installation, and to Stormbringer for his Howto:Setup Samba Peer to Peer from which I borrowed freely.

Good luck...:)

---

### Post by Brian96 on 2008-05-29
> **mwiley63 said:**
> I have quoted the first thread below for convenience.  If it makes this post too long, I will edit it and take it out.

I was able to get this to work on Ubuntu 8.04 with some minor tweaks (the samba services that is, vmware-server is a whole different story).

The difference between my setup and this tutorial is that my set up is sharing an external USB hard drive's partition.  Sharing is different in 8.04 then it is in previous versions of Ubuntu.  For starters, you can only share folders under your own home directory (the directory you own).  You can't even share files that aren't owned by you that exist in your home directory by default.  So here is 4 steps I had to add on to the original tutorial to get this to work:

1)  Install the right dependencies

In 8.04 make sure you have samba, samba-common, and nautilus-share installed through synaptic manager (or use sudo apt-get install [name]).
```
sudo apt-get install samba samba-common nautilus-share
```

2) Manually mount your USB drive to your home directory

First run:
 ```
sudo fdisk -l
```
 to see the name of your USB device.  It should be something like /dev/sdX# where X is a letter and # is a number.  You then mount that drive to a folder that exists in your home directory like so:
```
mount /dev/sdX# /home/user_name/yourfolder
```

3)  Allow samba to share folders which a user does not own

```
sudo /etc/init.d/samba stop
```
Now edit your smb.conf file just like you would on the first thread of this tutorial, but add one line to the global section:
```
usershare owner only = False
```
Make sure the path matches your new folder and the name for that section matches the name you will give the shared folder.  When you are done run:
```
sudo /etc/init.d/samba stop
```

4) Share the folder containing the mounted device

Right click on the folder and select sharing options.  Give it the same name you gave for the section in your smb.conf file. 

After following the rest of the steps on the opening post of this thread everything should be working fine.


NOTE:

I used a fresh 8.04 install with an old vm disk, so the vm had everything configured already, I just had to update the path to the network drive since I changed the name of the shared folder.

Feel free to correct me if I missed anything or add to it.

You mentioned that in 8.04 you can only share folders in your home directory. I did not know that.

In Gutsy and Feisty I shared a folder on a partition I use for file storage. Could I, in theory, use your instructions to mount that partition in my home folder? If so, can you think of any obvious modifications?

---

### Post by Brian96 on 2008-05-29
> **Brian96 said:**
> You mentioned that in 8.04 you can only share folders in your home directory. I did not know that.

In Gutsy and Feisty I shared a folder on a partition I use for file storage. Could I, in theory, use your instructions to mount that partition in my home folder? If so, can you think of any obvious modifications?

Well, I got brave and tried it and it worked fine.

Here is what I did:

1. Created a folder ("Big") in my home directory.
2. Made a backup of my fstab (sudo cp /etc/fstab /etc/fstab.backup).
3. Edited the line for my storage partition from "/media/Storage" to "/home/rutland/Big".

Then I edited my smb.conf to reflect the path.

When I re-booted, my storage partition was mounted in my home directory, and my samba shares (I used a different howto--which I can no longer find--to configure samba) now work perfectly in my XP guest.

Maybe this will help another newbie like myself. :)

---

### Post by msayed2004 on 2008-06-24
Nothing work for me, because of this ->> **abrichr said:**
> In the Map Network Drive dialogue, when I click finish, a window appears saying "Attempting to connect to \\Ubuntu\rda...", and a dialogue appears requesting my username and password.

My windows and ubuntu usernames are both rda.  I put in my username and password, but the dialogue reappears, with the username changed to "UBUNTU\rda".  I can enter the password in as many times as I want, and the dialogue reappears.

Any ideas?

---

### Post by frogotronic on 2008-06-24
> **msayed2004 said:**
> Nothing work for me, because of this ->

check and see that your permissions on/in your smb.conf file allow you access - in other words, make sure there is no "access=no" statements.

also, check and make sure firestarter is running and that you've got permissions turned on (in your policies section) for your samba share.

- CH

---

### Post by msayed2004 on 2008-06-24
Thanks, I found no "access=no" entries & opened the ports, same error appeared about 3 times then I had this msg:> The mapped network drive could not be created because the following error has occurred:

An extended error has occurred.& no more info about that error (Microsoft really make strange error msgs!)

---

### Post by frogotronic on 2008-06-24
> **msayed2004 said:**
> Nothing work for me, because of this ->

it should read "Attempting to connect to \\xxx.xxx.xxx.xx\rda", not "\\name\rda"

when you set your mapped drive you have to enter in the IP address of the host (ubuntu) machine

also make sure you've got "reconnect with a different logon name checked"

Enter the IP address of the Ubuntu Host machine.  What is the IP address?  look here: [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/) 



- CH

---

### Post by DonnyB4e56 on 2008-07-06
Thanks I was going nuts trying to do this without a tutorial. I'm a newbie to Ubuntu although I've been with it sence 7.04.. Not to long ago but my knowlage dosnt go far with Ubuntu

---

### Post by mdpalow on 2008-07-12
> **misha680 said:**
> One thing that is a problem is that samba starts before vmware does, so the vmnet1 and vmnet8 interfaces don't exist yet when samba starts and it doesn't recognize their creation later on. A quick solution for this is:
```
sudo /etc/init.d/samba restart
```
A more permanent fix:
```
sudo gedit /etc/rc.local
```
And add the following lines somewhere:
```
# Restart samba so it takes into consideration VMWare network interfaces
/etc/init.d/samba restart
```
This will just restart samba as the last thing that happens when your machine is booting, ensuring that the vmware networking devices are loaded.

Misha

excellent. Thanks.

Quoting to save in my history. :)

---

### Post by calibre97 on 2008-07-13
Great tutorial. As with many here, I had to make some tweaks to get it to work. Here's what I did:
1. I'm running Kubuntu so my NetBios name is Kubuntu.
2. Again with Kubuntu so I couldn't follow this step exactly:
  2)Use System -> Administration -> Shared folders to make a
    shared folder. I suggest you use /home/YOUR_NAME/samba. 
    In Properties:
    a) Share with: SMB
    b) Name: MyFiles
    c) Tick Allow browsing folder
    d) In Windows sharing settings, “Domain/Workgroup” is 
       MsHome (or whatever your guest XP machine is) 
       and select “This computer is a WINS server”.
    e) Press OK, OK
  I didn't have anywhere to specify a workgroup and I don't know what it is anyway. Doesn't appear to be one in the XP guest.
3. I followed everything else but when it came time to connect in the XP guest, I got the same "extended error" message so I removed the force user and force group items (From Kubuntu's System Settings rather than editing the .conf directly.) Actually, only the user I'd specified was there to remove; the group was blank anyway.

One other thing. I understood the instructions to mean put the same login name as I use for the XP guest (which is also the same I use for Kubuntu host-maybe that's bad?) and so when I log into the XP guest I get an error that there's a duplicate user on the network but it logs in anyway and the Samba mapping occurs (tested with copying file in Kubuntu and seeing it in XP).

So, it works now, but may be open due to the lack of force user.
Oh and one last thing: my XP guest is a result of using VMWare's Converter on my laptop's original installation partition. That install included ZoneAlarm which I haven't had the courage to uninstall yet but everytime I start XP, I have to shut it down so I have internet access through the NAT interface. So no computer condom and no force user for the Samba connection. I hope i'm not in too much trouble and if this was Slashdot, I'd be getting about a thousand requests for my IP address and ISP right about now.

---

### Post by halogentan on 2008-09-19
Thanks for sharing that.  I was able to get this working on 8.0.4 Hardy Heron, although there's no System -> Administration -> Shared folders.  You have to navigate to the folder and right click -> Sharing Options now.

---

### Post by sgla1 on 2008-09-25
> **kadalz said:**
> Hello:

I'm a nob here. I tried many times to follow this How To. I always stuck in the last step, where I tried to setup Map Network Drive. When I tried to put in Forder field: \\server\shared, I got the following error message: The network path \\server\shared could not be found. Here is my smb.conf. Hope somebody can give guidance, which I did wrong. BTW, I use Kubuntu 6.10.

```

[global]
;General server settings
netbios name = server
workgroup = home
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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

[Shared]
path = /home/altari/Shared
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = rais
force group = rais
available = yes
public = yes
writable = yes

```

Thank you,
Kadalz

Try renaming your box from 'server' which I believe is a reserved word for Windows.  You might want to pick a new name for your workgroup also, for similar reasons.  Remember there is a /home dir in Linux.

---

### Post by sgla1 on 2008-09-25
> **Foxmike said:**
> Hi!  Thank you for the great guide!  Just a question: does "NAT" networking or "Bridged" networking makes a difference?  I'm using NAT networking, followed all those steps but I cannot access shared folders from an OS to the other.  The only shared folders I can access now are: in Windows, shared folders from Windows, and in Ubuntu, shared folders in Ubuntu.  I am using Edgy, if that makes a difference.

Thank you!

-FM
Try mapping your share to the gateway address of your nat rather than the IP of eth0.  I believe that will be the IP of vmnet 8

inet addr:172.16.166.1  Bcast:172.16.166.255  Mask:255.255.255.0

---

