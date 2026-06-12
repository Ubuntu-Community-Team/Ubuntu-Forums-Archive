---
title: "dhcp settings"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by evertonmint on 2012-07-28
I have just installed ubuntu 12.04, after installation the guide says I must install 'vim' and also Ubuntu installer has configured our system to get its network settings via DHCP, Now we will change that to a static IP address for this you need to edit

Edit /etc/network/interfaces and enter your ip address details (in this example setup I will use the IP address 172.19.0.10): Why do I have to do this and how? Do I just type in /etc/network/interfaces  and press enter or do I have to look for a line to physically edit?

---

### Post by Zill on 2012-07-28
evertonmint:  I don't know which "guide" you are referring to but I doubt if you *must* install vim!  This, along with emacs, is a very powerful text editor that, while useful to developers and "power users", is really too cryptic for general use.  When you do need to use a text editor then I suggest you use either "gedit" (for GUI use) or "nano" (for CLI terminal use).  Both of these editors are far more intuitive and should provide all the capability you need.  Just remember that if you are editing system files (i.e. those owned by "root") then you must use the prefix "gksudo" for gedit or "sudo" for nano, as this allows you to save files as the superuser.

The default network settings should be DHCP so if you want to change this to a static IP you *can* do this via the /etc/network/interfaces file.  If you wish to do this then I suggest you *first* copy the original file so that you have a good backup:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
```
Then edit the file with the "nano" text editor:
```
sudo nano /etc/network/interfaces
```
The editor will then show the existing file and you should change it as required. e.g.
```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

[COLOR="Red"]iface eth0 inet static
address 172.19.0.10  #This should show your static IP
netmask 255.255.255.0
gateway 172.19.0.1  #This should show your router address[/COLOR]

auto eth0
```
(Note that "#" signifies comments that are to be ignored)

Save the file with Ctrl-o then quit nano with Ctrl-x.

Reboot the PC and you should now have your required static IP.

Note that editing the /etc/network/interfaces file is a rather "old fashioned" way of specifying connections as later versions of Ubuntu use the "Network Manager" GUI to do this.  Personally, I *prefer* to edit the interfaces file as I find this more reliable than using the NM widget. ;-)

---

### Post by evertonmint on 2012-07-29
> **Zill said:**
> evertonmint:  I don't know which "guide" you are referring to but I doubt if you *must* install vim!  This, along with emacs, is a very powerful text editor that, while useful to developers and "power users", is really too cryptic for general use.  When you do need to use a text editor then I suggest you use either "gedit" (for GUI use) or "nano" (for CLI terminal use).  Both of these editors are far more intuitive and should provide all the capability you need.  Just remember that if you are editing system files (i.e. those owned by "root") then you must use the prefix "gksudo" for gedit or "sudo" for nano, as this allows you to save files as the superuser.

The default network settings should be DHCP so if you want to change this to a static IP you *can* do this via the /etc/network/interfaces file.  If you wish to do this then I suggest you *first* copy the original file so that you have a good backup:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
```
Then edit the file with the "nano" text editor:
```
sudo nano /etc/network/interfaces
```
The editor will then show the existing file and you should change it as required. e.g.
```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

[COLOR="Red"]iface eth0 inet static
address 172.19.0.10  #This should show your static IP
netmask 255.255.255.0
gateway 172.19.0.1  #This should show your router address[/COLOR]

auto eth0
```
(Note that "#" signifies comments that are to be ignored)

Save the file with Ctrl-o then quit nano with Ctrl-x.

Reboot the PC and you should now have your required static IP.

Note that editing the /etc/network/interfaces file is a rather "old fashioned" way of specifying connections as later versions of Ubuntu use the "Network Manager" GUI to do this.  Personally, I *prefer* to edit the interfaces file as I find this more reliable than using the NM widget. ;-)

Thx for that Zill, the guide is the 'step by step Ubumtu 12.04 (precise) here is an extraction;
This will complete the Ubuntu 12.04 (Precise) LAMP Server Installation and your server is ready for installing applications which supports apache,mysql and php.

[B]Configuring Static ip address in Ubuntu server
[/B]
If you want to install vim editor use the following command

sudo apt-get install vim

Ubuntu installer has configured our system to get its network settings via DHCP, Now we will change that to a static IP address for this you need to edit

Edit /etc/network/interfaces and enter your ip address details (in this example setup I will use the IP address 172.19.0.10):

sudo vi /etc/network/interfaces

and enter the following save the file and exit (In vi, ESC, then ZZ to save and exit)

# The primary network interface

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1

I am a newbie especially to dos, the server is a second hand HP ML 310 with no O/S till now. The guide doesn't explain why I need a static IP? I have a couple of wyse (used) terminals attached, that need to be set up also.

---

### Post by Zill on 2012-07-29
> **evertonmint said:**
> ...I am a newbie especially to dos, the server is a second hand HP ML 310 with no O/S till now. The guide doesn't explain why I need a static IP? I have a couple of wyse (used) terminals attached, that need to be set up also.
Let's just rewind a bit.  I have taken a look at your [previous posts]("http://ubuntuforums.org/showthread.php?t=2025141") where you referred to "freeDOS" and you have also referred to "dos" in this thread.  FYI, Ubuntu (and all Linux systems) do *not* run "dos" as this is a Microsoft thing.  When accessing a Linux system via a terminal, the OS commands can look *similar* to MS DOS but the commands and usage are totally different and, arguably, more powerful.  e.g.  To list a directory in DOS you use the "dir" command whereas in Linux you use the "ls" command.

Assuming you did manage to install Ubuntu, it seems that you wanted the server version.  May I ask why you specifically wanted this version?  The reason for the question is that both the "desktop" and the "server" versions are fundamentally similar and each one *can* perform the same functions.  The primary difference is the desktop version has a GUI by default, whereas the server version does not - all commands must be entered via a terminal.  However, simply by adding packages, identical functionality *can* be added to both versions.

If need to run a server exclusively then it is probably best to install the server version, as this has many server packages installed by default.  However, if you either want to use the PC for other tasks that require a GUI (such as web browsing), *or*, if you want the ease of use from using a GUI, then the desktop version may be a better bet.  Then you just need to add a few server packages.

If you need to ask "why I need a static IP?" then I suggest that you may not *need* one!  With servers, these are often desirable to ensure consistent network routing.  With desktops this is not normally required as DHCP (dynamic IP) is perfectly adequate.

I suggest you advise exactly what you are trying to achieve here and, in particular, what kind of data you wish to distribute.  e.g. Are you just wishing to share files to other PCs or do you wish to run a full web server etc.  Specifically, are you intending to share files locally (within your LAN) or globally (via the internet)?

How much knowledge do you currently have of server administration e.g. on Windows?

---

### Post by evertonmint on 2012-07-29
Hi again Zill and thanks for the prompt replies,
We have a little 8 office unit with a possibility of 40+ terminals the intent is mainly local lan based pc's but with the capacity to go global. We also have another office at the other end of town in Jaguar, what was Ford Halewood. My knowledge on servers is very limited. We thought it would be nice to be able to access files at both places rather than sending emails. Reading your reply it would be advantageous to us to place ubuntu desktop on the server also, as I would be more at home with a gui functionality.
All advice is gratefully accepted.
Regards
evertonmint

---

### Post by Zill on 2012-07-29
evertonmint:  Thank you for the additional info.  It seems that your primary requirement is to share files to other PCs via your LAN.  If your network only uses Linux PCs then I suggest [Network File System (NFS)]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is the best way to do this.  However, if your network includes any Windows PCs then you should use [Samba]("https://help.ubuntu.com/community/Samba/SambaServerGuide") as this works with both Linux and Windows.

Both NFS and Samba will be fine to share files across your LAN but if you need to share files to other sites (eg. via the internet) then I believe you will need to use a [Virtual Private Network (VPN)]("https://help.ubuntu.com/community/OpenVPN").

While using a single file server *can* be a good idea I suggest you remember that you will then be "putting all your eggs in one basket".  As such, you *must* have a reliable system to back up all your data on a very regular basis.  You will also need to have redundancy within the system so that, in the event of your server failing, you can rapidly bring a replacement machine on line.

The other main factor to consider is security.  While Linux systems within a LAN are generally very secure, the risk of attack increases considerably when you open ports to the internet.  This risk increases if you introduce more services, such as web servers etc.

Linux servers are very secure by design but this can be negated by bad configuration by the administrator.  As you have said that you have limited knowledge of server administration I therefore strongly recommend that you obtain the assistance of a Linux "guru" in the initial configuration and administration.

Going back to your original post, I suggest you need to map out exactly how you will configure your network.  Personally, I use static IPs for each PC as this makes configuration simpler on my home LAN (running NFS).  However, as yours is a larger "enterprise level" system, you may find other methods of addressing your PCs more suitable.  Unfortunately, I am hitting the limits of my knowledge here so I hope others can now pick this thread up with more info.

---

### Post by evertonmint on 2012-07-30
Thanks for your help and advice Zill, I will certainly take it on board.
So a quick recap, I would be most suited to downloading:Samba, a VPN and a security, maybe also a DNS server and configure a static IP. Going back to my 1st post, I don't need VIM? Would it make any difference in the 'address' if eth0 was plugged direct into the router rather than the switch?
Again thanks.

Regards
evertonmint

---

### Post by Zill on 2012-07-30
evertonmint:  You have referred to "downloading" various apps.  Although technically correct, in Linux we refer to *installing* a *package*, which automatically includes the "downloading" part.  This is because Linux apps are held on centralised repositories (repos), rather than scattered around the WWW as with Windows apps.  As Linux uses a [package management system]("https://help.ubuntu.com/11.04/serverguide/package-management.html") this means that, in addition to the core program, any required dependencies, such as libraries, are also installed automatically.

As stated earlier, if you use only Windows clients, or a mix of Linux and Windows, then a Samba server is the way to go.  However, NFS is, IMHO, preferable if your network *only* uses Linux clients.

I do not understand what you mean by "a security" as there is no *single* application that provides security.  Network security is a specialised subject that involves many different tools that all have to be configured correctly.  As each network (and its server applications) is different each one needs expert knowledge to ensure good security.  I suggest you should [read-up on this]("http://ubuntuforums.org/showthread.php?t=510812/") and, as suggested earlier, obtain help from a Linux guru.

Unless you intend running a web-server, I doubt if you need a DNS server.  From a security viewpoint, the fewer servers you run the better as each one is an additional security risk that needs hardening.

While it might be possible to run servers with dynamic IP addresses, in my view a static IP would make things far simpler.  I explained how to do this in my [post #2]("http://ubuntuforums.org/showpost.php?p=12135388&postcount=2") above.

You can, if you wish, use the vim editor.  However, this is unnecessary in my view as other editors out there are perfectly adequate for your purposes *and* more intuitive!  [Nano]("http://www.debianadmin.com/nano-editor-tutorials.html") is installed by default and is a really simple command-line editor that is ideal for your usage IMHO.
> Would it make any difference in the 'address' if eth0 was plugged direct into the router rather than the switch?
I don't know how your network is currently configured and so I cannot really comment on this one.  You need to establish what range of IP addresses you wish to use and then configure your router, server(s) and clients accordingly.  Router IP address configuration is generally done via a web-browser and the server/client PCs can be configured either by editing the /etc/network/interfaces file *or* via a GUI on each machine.

---

### Post by evertonmint on 2012-07-31
Zill, Thanks for the technical heads up, I installed ubuntu 12.04 and also installed a couple of packages namely; OpenSSH, LAMP, print and Samba.When I entered the sudo cp /etc/network/interfaces /etc/network/interfaces_bak, it came back 'do not recognise _bak'?
I tried that sudo nano code and it open up in another page/file, with a grey header titled GWH or something like that, anyway I typed in the code but it wouldn't save, I eventually got out and back to home page, so I entered the sudo vi/etc/ code and the code you gave above came up with the # tag lines in turquoise blue. I editor'd the code and saved but,a line came up some interfaces may not work 'it didn't recognise a line' some components of interfaces may not work. I had to leave the office here so will look at it tomorrow.
Yes, I understand the security has to be set up when addressing the terminals and writing the plan. Can I install ubuntu 'desktop' on top of the server?

I have now come in and couldn't get the info I needed so I reinstalled the whole program again, at least now it is fresh. It is telling me 120 packages can be updated and 55 of these are security updates.
Again thanks for help and advice.

Regards
evertonmint

---

### Post by Zill on 2012-07-31
evertonmint:  I don't understand the error you received in copying the original /etc/network/interfaces file as you can specify *any* filename for the copy!  I suggest you check the syntax is exactly as I gave it, preferably by copy & paste from this forum.  Similarly, if you get any error messages then please paste them here with "CODE" tags.

To save a file with Nano, hit "Ctrl-o", followed by "Ctrl-x" to exit.

Similarly, please paste any errors here in full as it is easier to see what is happening with all the text.

Yes, you should be able to [install Ubuntu Desktop]("http://www.ubuntugeek.com/how-to-install-gui-on-ubuntu-12-04-precise-server.html").

---

### Post by evertonmint on 2012-08-06
Hi Zill, sorry it was my fault a space to many. I have it up and running there are some good intuitive guides on you-tube that I managed to catch hold of. I seem to have managed the static IP, have installed 'webmin'. I need to map my terminals now.I have come in this morning and logged on, it tells me there are 84 updates, when I try to install them it comes up error,
E: some index files failed to download. They have been ignored, or old ones used instead.
Reading the lines on the screen; 
Failed to fetch [http://gb](http://gb) archive.ubuntu/dlists/precisebackports/universe/i18n/Translation-en Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with host name.
Have you any idea what this is about? This is along side nearly all lines.

Regards

evertonmint

---

### Post by Zill on 2012-08-06
> **evertonmint said:**
> ...I have come in this morning and logged on, it tells me there are 84 updates, when I try to install them it comes up error,
E: some index files failed to download. They have been ignored, or old ones used instead...
Please enter the following command and then paste *all* the output into a new reply on this thread.  Make sure the output is contained within "CODE" tags to make it easier to read. (use the "#" icon near the top of the box)
```
sudo apt-get update
```
Then please repeat with the following command:
```
sudo apt-get upgrade
```
Finally, repeat with the following command:
```
cat /etc/apt/sources.list
```

---

### Post by evertonmint on 2012-08-08
Thanks for that Zill, I'm having a couple of days off for a family bereavement, sort it by weekend.

---

### Post by Zill on 2012-08-08
> **evertonmint said:**
> Thanks for that Zill, I'm having a couple of days off for a family bereavement, sort it by weekend.
Thanks for the update and I fully understand - you have my sympathies.

No rush here so please just post back when you are ready and we can resume then.

---

### Post by evertonmint on 2012-08-17
Hi Zill I'm back. I had a chat with a friend at the wake and he suggested has there was nothing on it to start again, which I did, instead of jumping in, I took it steady and when it loaded I read the instructions and updated and upgraded. I then installed desktop, I came across a guide things to do after installing ubuntu. So I 'm carefully following that, I was installing [ 
sudo apt-get install flashplugin-installer gsfonts-x11 ] It finished and gave me a notice that I have duplicates and suggest update to repair. I have updated but, still have 2 lines;
[Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems]
Do you have any suggestions? The things to do doesn't explain when things go wrong.
Notice I can now copy and paste in ubuntu  as I found out how to access terminal! I told you I was new. ;-)

---

### Post by Zill on 2012-08-17
evertonmint:  It seems to me that you have mixed both 32 and 64 bit repositories in your sources.list.  You must decide on which system you want.  i.e. If you have a 64-bit processor then you can use *either* 64-bit *or* 32-bit software.  However, if you only have a 32-bit processor then you *must* use 32-bit software.  Then you must use *only* the appropriate repos for your software choice.

You can read up on the pros and cons of 64 vs 32 bit software elsewhere but, personally, I find 32-bit works for me, even when using a 64-bit processor.  The terminology may seem a bit strange but, in Ubuntu, "amd64" means *all* 64-bit processors, not just AMD.  Similarly, "i386" means *all* 32-bit processors, not just Intel.

If 64 and 32 bit repos *are* mixed up in your /etc/apt/sources.list then I suggest it may be simpler to re-install rather than try to untangle and replace the many different programs currently installed.

To confirm this, please post the output of the following command:
```
cat /etc/apt/sources.list
```
Please remember to wrap the output in "code" tags as this makes things easier to read in the thread.  Simply highlight the text and then hit the "#" icon in the editing window.

ps.  I am not sure what your guide "things to do after installing ubuntu" recommends but I suggest you proceed with caution.  AIUI, your primary requirement is for a work server and, as such, I suggest the fewer irrelevant programs the better.  Many other (home) users will want full multimedia and eye-candy but these packages are probably not appropriate for a work server.  You may like to concentrate on the basics initially and then only install additional packages later as required.  An initial default server install of Ubuntu should have (more or less!) everything you need to get started.

---

### Post by evertonmint on 2012-08-17
Hi Zill, I don't see how as the server is 64 and I installed desktop from the terminal, here is what you asked for;
[ [sudo] password for bill: 
# 

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner ]
bill@crownunit:~$
What do I have to do to Uncomment? It says the following two lines but, in the last case there are 4 lines?
I go to Greece on Tuesday for 2 weeks.

---

### Post by Zill on 2012-08-17
> **evertonmint said:**
> Hi Zill, I don't see how as the server is 64 and I installed desktop from the terminal...
I was concerned by this...
> **evertonmint said:**
> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner [COLOR="Red"]amd64[/COLOR] Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner [COLOR="Red"]i386[/COLOR] Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)...
Unfortunately, as I only use 32-bit software I cannot comment on the veracity of your sources.list.  Maybe some other 64-bit users can verify this.

In the meantime, please post the output of the following command in order to show exactly what is installed:
```
uname -a
```
As I requested earlier, *please* enclose your output text in code tags as this makes things much easier to read, particularly with long listings.

---

### Post by Zill on 2012-08-17
> **evertonmint said:**
> ...## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [COLOR="Red"]precise partner[/COLOR]
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [COLOR="Red"]precise partner ][/COLOR]
bill@crownunit:~$
What do I have to do to Uncomment? It says the following two lines but, in the last case there are 4 lines?
It looks to me like the "partner" repos have been duplicated (plus a slight corruption!) on the last two lines of the "extras" repo.  I would try commenting these two lines out.  First copy the sources.list file so that you have a good(!) backup:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```
and edit the sources.list with nano by adding a "#" at the start of each line you wish to comment out:
```
sudo nano /etc/apt/sources.list
```
(ctrl-o to save then ctrl-x to exit)
The sources.list should then look like:
```
...## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner ]
```
Then update the sources.list:
```
sudo apt-get update
```
and upgrade the packages:
```
sudo apt-get upgrade
```
See if it now runs OK without any errors.

---

### Post by evertonmint on 2012-08-17
Thanks for the help Zill but, I have left the office and wont be back till 5/6th Sept.(holiday head on) I will bookmark this for reference when I return. 
The server is amd 64 bit and I installed from the 64 bit cd. I can only assume (one should never assume) that when I installed the desktop it installed 32 bit, should I have specified? I did down load both 32 & 64 bit iso's and saved them to disk but, as I said I installed from terminal. Regards, this will play on my mind now, till Tuesday. (flight day).

---

### Post by evertonmint on 2012-08-19
Hi Zill, I came across this on the web as an example of how a sources.list should look. I notice that mine, with the exception of the last two lines, is the same except for //de. (mine is //gb.) What is the significance of de. & gb. Is it the country of residence? I am going to go and have a look at your suggestions tomorrow about dinner time.
Cheers

evertonmint

> #

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


---

### Post by Zill on 2012-08-19
> **evertonmint said:**
> Hi Zill, I came across this on the web as an example of how a sources.list should look. I notice that mine, with the exception of the last two lines, is the same except for //de. (mine is //gb.) What is the significance of de. & gb. Is it the country of residence?...
The Ubuntu repos are mirrored on servers throughout the world.  While you *can* use any mirror, it is generally best to use one close to you as this enables the fastest internet connection.  On this basis, Ubuntu will select, by default, the servers close to the country you have entered when installing the system.  So, in the UK we get the "gb" servers while a German user will get the "de" servers.  HTH.

---

### Post by pablolie on 2012-08-19
Why not simply right click on the network icon up top, and edit the connections you need? (oops just saw the discussion turned into Ubuntu Server)

I am not shy to sudo away when it's needed, but if available I'd rather go for a user friendly GUI.

---

### Post by Zill on 2012-08-19
> **pablolie said:**
> Why not simply right click on the network icon up top, and edit the connections you need? (oops just saw the discussion turned into Ubuntu Server)...
Even though this thread is primarily about an Ubuntu server installation, AIUI the OP has actually now installed the desktop GUI.

On this basis, the Network-Manager applet *should* be available for network configuration.  Having said that, I would not recommend use of the Network-Manager applet for a server as I believe this is a user-space tool that only works while a user is logged in.  This is not always the case with servers, which often run unattended 24/7.

The "traditional" method of editing the /etc/network/interfaces file is the best approach in this case as it ensures permanent connectivity irrespective of user logins.

---

### Post by evertonmint on 2012-08-20
> **Zill said:**
> I was concerned by this...

Unfortunately, as I only use 32-bit software I cannot comment on the veracity of your sources.list.  Maybe some other 64-bit users can verify this.

In the meantime, please post the output of the following command in order to show exactly what is installed:
```
uname -a
```As I requested earlier, *please* enclose your output text in code tags as this makes things much easier to read, particularly with long listings.
The out-put for uname -a
[HTML]Linux crownunit 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[/HTML]

---

### Post by evertonmint on 2012-08-20
Zill,
Here is the end result
> bill@crownunit:~$ cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
bill@crownunit:~$ 

regards
evertonmint

---

### Post by Zill on 2012-08-20
evertonmint:  So, what happens when you update/upgrade as I requested in post [#19]("http://ubuntuforums.org/showpost.php?p=12178587&postcount=19")?
Do you get any errors now or does the system update correctly?

If so, please post the output of any errors.  At the risk of sounding pedantic it really does help if you use "code" tags, rather than the "quote" or "HTML" tags you have previously used.  The text is easier to read because a "code" box will include a scroll bar.```

```

---

### Post by evertonmint on 2012-08-20
Updated, upgraded and the result is no error messages. Seems to be ok now thanks Zill.

I don't have the # in my reply box only the quote window. I must have the cheap version  ;) You will have to stay pedantic, it reads the same just says "Quote" instead of "code"

---

### Post by Zill on 2012-08-20
> **evertonmint said:**
> Updated, upgraded and the result is no error messages. Seems to be ok now thanks Zill.
Good.  I'm pleased that you have got things working.
> **evertonmint said:**
> I don't have the # in my reply box only the quote window. I must have the cheap version  ;) You will have to stay pedantic, it reads the same just says "Quote" instead of "code"
I suggest that this is because you are using the "Quick reply" icon at the bottom right of the message which only produces a limited editing screen.

If you use either the "New Reply" button at the bottom left of the webpage *or* the "Quote" icon at the bottom right of a message then you should get a full edit box with all the additional functionality.

Would you now please use the "Thread Tools" pull-down menu near the top right of the webpage to "Mark this thread as solved".  This is something that can *only* be done by the original poster.

---

### Post by evertonmint on 2012-08-20
> **Zill said:**
> Good.  I'm pleased that you have got things working.

I suggest that this is because you are using the "Quick reply" icon at the bottom right of the message which only produces a limited editing screen.

If you use either the "New Reply" button at the bottom left of the webpage *or* the "Quote" icon at the bottom right of a message then you should get a full edit box with all the additional functionality.

Would you now please use the "Thread Tools" pull-down menu near the top right of the webpage to "Mark this thread as solved".  This is something that can *only* be done by the original poster.

```
OK, AND CHEERS.
``` :lolflag:  COYB and Hello Greece!

---

