---
title: "Howto: Install WICD for wireless support w/ WPA1/2"
date: 2007-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by walkerk on 2007-08-16
[WICD]("http://wicd.sourceforge.net"). A **great** alternative to Network Manager (not at all a bash to the Network Manager devs, but on some of our systems this works much better). This Howto was tested using Feisty but WICD also works w/ Gutsy, Edgy, and Dapper.

**Many users have been having problems with Network Manager or just prefer WICD.** I find that it handles WPA much better and loads at boot up through init.d so there is no reason for the annoying keyring to ask you for your password at login.. you're already connected.

***[COLOR="DarkOrange"]Of course all the credit goes to the developer of WICD.[/COLOR]***

Before continuing be sure that your wireless works (even if it hardly works). If not you need to follow threads on the forum to install the correct drivers to enable yourwireless nics.

[COLOR="Red"]Disclaimer[/COLOR]: I can't see what would go wrong but of course I take no responsibility. :)

[SIZE="5"]The script...[/SIZE] @ the bottom of this post. 
**wicd.py** will backup new packages (or existing packages) of network-manager if you opt to, and then install WICD

Download and move to it's directory:
```
cd /path/to/file
```

Make it executable:
```
chmod +x wicd.py
```

Run it:
```
sudo python wicd.py
```
*[COLOR="YellowGreen"]If you don't use sudo the script will not work.[/COLOR]*

Enjoy :) See below to load tray icons..

[SIZE="5"]Or do it manually...[/SIZE]
**Backup**
First check to see if you have the network-manager and network-manager-gnome packages archived just in case you want to switch back to Network Manager:
```
cd /var/cache/apt/archives

ls | grep network-manager
```

If you don't see the packages you can download them to this folder using the -d option:
```
sudo apt-get -d --reinstall install network-manager network-manager-gnome
```

*When you install WICD it uninstalls Network Manager.. same deal the other way around as well.*

**To install WICD do the following: (for gutsy, edgy, or dapper replace feisty as needed)**
```
echo 'deb http://apt.wicd.net feisty extras' | sudo tee -a /etc/apt/sources.list

sudo apt-get update

sudo apt-get install wicd
```


Now just goto Applications > Internet > Wicd (or /opt/wicd/gui.py in terminal) to setup it up. If using WPA be sure to set the correct driver. Here are some choices (wext is the generic and works with my Broadcom.
```
**hostap**
(default) Host AP driver (Intersil Prism2/2.5/3). (this can also be used with Linuxant DriverLoader). 

**hermes**
Agere Systems Inc. driver (Hermes-I/Hermes-II). 

**madwifi**
MADWIFI 802.11 support (Atheros, etc.). 

**atmel**
ATMEL AT76C5XXx (USB, PCMCIA). 

**wext**
Linux wireless extensions (generic). 

**ndiswrapper**
Linux ndiswrapper. 

**broadcom**
Broadcom wl.o driver. 

**ipw**
Intel ipw2100/2200 driver. 

**wired**
wpa_supplicant wired Ethernet driver 

**bsd**
BSD 802.11 support (Atheros, etc.). 

**ndis**
Windows NDIS driver.
```

No need to load wicd manually at boot as init.d will load daemon.py (with root privledges, so you don't have to enter your password) at boot up.

If you want the systray icon you'll need to add it to System > Preferences > Sessions...

```
Name: WICD Tray
Command: /opt/wicd/tray.py
```

In KDE run the following in terminal:
```
sudo ln /opt/wicd/tray.py ~/.kde/Autostart/tray.py
```

> **[COLOR="RoyalBlue"]Having issues with the tray icon? Is it just a white box? There are two courses of action:**

1. Dano has fixed this issue in his latest SVN release 1.3.3 > [Here]("https://sourceforge.net/project/showfiles.php?group_id=194573")

2. Or, follow the instructions [here.]("http://ubuntuforums.org/showpost.php?p=3300317&postcount=29")
[/COLOR]



**Hopefully this worked for you. If not the network-manager packages should still be in you package archive. Do the following:**
```
cd /var/cache/apt/archive
```

Now identify network-manager and network-manager-gnome:
```
ls | grep network-manager
```

Now re-install them: 

**Where nm.deb = the network-manager.deb package.**
```
sudo dpkg -i nm.deb
```

**Where nmg.deb = the network-manager.deb package.**
```
sudo dpkg -i nmg.deb
```


If problems arise please let me know :)

**Updates**
12/26/07: *Updated the Repository location*
10/08/07: *Cleaned up the network test*
09/20/07: *Added a couple of tests to wicd.py*
09/18/07: *Updated the python script. Cleaned it up...*
09/08/07: *Cleaned up wicd.py*
09/07/07: *Replaced wicd.sh with wicd.py.. no real reason. :)*

---

### Post by EXCiD3 on 2007-08-23
The script didnt work for me. It told me it didnt find Network Manager's archives. I am using Network Manager right now. The script ran fine, but WICD did not install. I am using Feisty if that helps.

**UPDATE:**
I used the manual install and everything went correctly. WICD works great and beats NetworkManager hands down.

Awesome job on the scripts/tuts! They make it so much easier than taking the time to figure it out myself...Thanks again and don't stop making tutorials!

---

### Post by walkerk on 2007-08-23
> **EXCiD3 said:**
> The script didnt work for me. It told me it didnt find Network Manager's archives. I am using Network Manager right now. The script ran fine, but WICD did not install. I am using Feisty if that helps.

**UPDATE:**
I used the manual install and everything went correctly. WICD works great and beats NetworkManager hands down.

Awesome job on the scripts/tuts! They make it so much easier than taking the time to figure it out myself...Thanks again and don't stop making tutorials!

Thanks a lot man ..and I will continue :)

Also, the script looks for network-manager packages that might be archived on your system (you might not have them) and opt for you to download them as a backup.. just incase someone decides they don't like WICD (or it doesn't work).

I personally don't have the network manager packages but the script searches /var/cache/apt/archive for 'network-manager'... whats your output for the following?
```
ls /var/cache/apt/archive | grep network-manager
```

---

### Post by imdano on 2007-08-23
Nice guide walker.  One correction though, all versions of Ubuntu can use tray.py to launch the tray.  It decides based on the version of pygtk running on the machine whether to use edgy.py or dapper.py.  Right now tray-edgy.py and tray-dapper.py just symlink to tray.py, and are kept around for backwards compatibility.  We'll probably phase them out eventually.

---

### Post by walkerk on 2007-08-24
> **imdano said:**
> Nice guide walker.  One correction though, all versions of Ubuntu can use tray.py to launch the tray.  It decides based on the version of pygtk running on the machine whether to use edgy.py or dapper.py.  Right now tray-edgy.py and tray-dapper.py just symlink to tray.py, and are kept around for backwards compatibility.  We'll probably phase them out eventually.

Thanks :) Just trying to spread the word.

**FIXED:** I must have forgotten to remove that bit from the script..?  I noticed that and removed tray-edgy, dapper from the manual instructions.. I'll correct the script when I get home from work.

---

### Post by Ripfox on 2007-08-26
I have been trying to let people know as well...this app really does beat the pants off of Network Manager.

---

### Post by tact on 2007-08-27
Does wicd support VPN connections?  

I am currently using network-manager and its built in support for pptp VPN connections to access corporate LAN resources from outside the office.  Its an essential for me.

---

### Post by imdano on 2007-08-27
No, not yet.  There's work being done on it though.

---

### Post by Dark Star on 2007-08-27
Nope not working here too :( btw Appreciate the efforts nice guide :D Make it work for every1 :)

---

### Post by imdano on 2007-08-27
What's not working?

---

### Post by fab92fr on 2007-08-27
hi all,

it's working for me but i can't get the tray applet under updated feisty.
even just launching it from /opt/wicd doesn't work.
it says :

fabien@fabien-desktop:~$ /opt/wicd/tray.py 
attempting to connect daemon...
success

but nothing in the tray :(
(same with sudo )

any clue ?

---

### Post by imdano on 2007-08-27
Are you using Gnome?  Does the tray change at all when you launch tray.py (like a blank spot appears where the tray *should* be, but it never shows up?)

---

### Post by fab92fr on 2007-08-27
hi imdano,

I use gnome and unfortunatly nothing at all happens when I launch tray.py

---

### Post by imdano on 2007-08-27
What version of wicd are you using?

---

### Post by Dimitriid on 2007-08-27
When I do the ls /var/cache/apt/archive | grep network-manager my result is just blank. When I try sudo apt-get -d install network-manager network-manager-gnome to download it says they are already the newest version ( its not downloading ).

How do I download it for backup?

---

### Post by tact on 2007-08-27
> **Dimitriid said:**
> When I do the ls /var/cache/apt/archive | grep network-manager my result is just blank. When I try sudo apt-get -d install network-manager network-manager-gnome to download it says they are already the newest version ( its not downloading ).

How do I download it for backup?

*grin*   I had the same issue.  Could not get the packages to just download.  Didn't think it'd be an issue thinking "WICD will work easily anyway, no problem, I got access to unsecured simple wifi and wired connections"....  

Big mistake for me!   hehehe

So I just installed WICD.  Couldn't get it working and so was stuck unable to go back to network-manager.   

A lot of tinkering later (without NM or WICD) I got connected and reinstalled networkmanager.

Don't do what I did!  hehehe

Thinking about it more now - what if you go into synaptic package manager and elect to "reinstall" NM.   there is probably an apt-get equivalent but I dont know it.

Perhaps a "reinstall" will download packages and reinstall networkmanager.   To the ls | grep thing after to confirm the packages are in the archive.

---

### Post by fab92fr on 2007-08-28
@imdano. I use the 1.3.1 version found at [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by imdano on 2007-08-28
Try version 1.3.3 and see if there's any difference in behavior.

Is your internet connection already working when you try open up the tray?  I know there was a bug where the tray icon would appear as a blank space without a picture because of the autoconnect process taking a long time or failing, but it seems like your problem is a little different.

---

### Post by fab92fr on 2007-08-28
Hi there,

I reinstalled my feisty and now wicd seems to work properly.
I think the problem comes from gnome as i get (before reinstall and still) a gnome preference error message at my session startup.
note it works perfectly under another "as installed" session, with just amsn launching.
under my session, I added monitoring applets (cpu & mobo temp, system monitor, swap, memory,network & cpu usage)

another way to look is the sound card not working.
gnome might be waiting for an answer from this device which never comes...

I'll keep trying and keep you informed

Thanks indeed for your help

------------------------

yyeeeeeeeeeeeeeehaaaaaaaaaaaa !!!

As suspected, the problem came from the sound card not working.
i followed this link [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and everything works at the speed of light now

ubuntu forever ;)

---

### Post by NickXxRitzXxVamp on 2007-08-29
ok so I'm having trouble with my optiplex gx240 and its Proxim ORiNCO 802.1 b/g usb client..the light isn't coming on and I have no experience getting internet with ubuntu i can do it in windows xp but not in ubuntu 7.04 some one help! when i unlug the client from the cord and plug the cord back into it the light flashes but than dies out  sorry im a total n00b with linux

---

### Post by walkerk on 2007-08-29
> **NickXxRitzXxVamp said:**
> ok so I'm having trouble with my optiplex gx240 and its Proxim ORiNCO 802.1 b/g usb client..the light isn't coming on and I have no experience getting internet with ubuntu i can do it in windows xp but not in ubuntu 7.04 some one help! when i unlug the client from the cord and plug the cord back into it the light flashes but than dies out  sorry im a total n00b with linux

you'll probably need to use ndiswrapper to get your wireless working. this thread is meant for people with an already functioning wifi connection but I can steer you in the right direction..

in terminal what are the ouptputs of the following commands:
```
iwconfig
```
```
iwlist scanning
```
```
lspci
```
```
lshw -C network
```

---

### Post by NickXxRitzXxVamp on 2007-08-30
thank you! :D

---

### Post by maestrobwh1 on 2007-08-30
Elegance in simplicity.

It works very well for my atheros card.  Network-manager somehow made it very unstable.

---

### Post by maestrobwh1 on 2007-09-01
I use kubuntu, and in kde, when I run the line to put an icon in my tray... I get a little white square.  If I hover the mouse over it, I get info, but something is not working right with the graphic.  Suggestions?

---

### Post by walkerk on 2007-09-01
> **maestrobwh1 said:**
> I use kubuntu, and in kde, when I run the line to put an icon in my tray... I get a little white square.  If I hover the mouse over it, I get info, but something is not working right with the graphic.  Suggestions?

you can try using the version 1.3.3 from wicd.sourceforge.net.. other than that imdano is the best person to ask as he is the developer of wicd..

---

### Post by imdano on 2007-09-01
My understanding is this has something to do with symlinking to the tray icon.  If you run /opt/wicd/tray.py directly, does the icon picture show up?

---

### Post by sensimilla on 2007-09-02
Thanks for the tutorial.
It's working great for me with my broadcom pci card (fwcutter).

The apt-get command to download the network-manager packages did not work, it said I already had the latest version. I managed to get them downloaded by doing a force reinstall of them in synaptic package manager and ticking 'download packages only' and then after downloading unmarking them.

I didn't need them as it turned out but it may be useful for others

---

### Post by walkerk on 2007-09-02
> **sensimilla said:**
> Thanks for the tutorial.
It's working great for me with my broadcom pci card (fwcutter).

The apt-get command to download the network-manager packages did not work, it said I already had the latest version. I managed to get them downloaded by doing a force reinstall of them in synaptic package manager and ticking 'download packages only' and then after downloading unmarking them.

I didn't need them as it turned out but it may be useful for others

Good call.. I'll edit the apt-get to include --reinstall.. that should do the trick.

---

### Post by maestrobwh1 on 2007-09-03
> **maestrobwh1 said:**
> I use kubuntu, and in kde, when I run the line to put an icon in my tray... I get a little white square.  If I hover the mouse over it, I get info, but something is not working right with the graphic.  Suggestions?

The instructions on WICD's site tells you to run some code to create a symlink to tray.py in /home/[username]/.kde/Autostart.

This symlink does not work and creates the white artifact with no icon in the tray.

Solved --> [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=4&t=173&sid=5d10d0ec0eca8ce8c71e0ca355f9409]("http://wicd.sourceforge.net/phpbb/viewtopic.php?f=4&t=173&sid=5d10d0ec0eca8ce8c71e0ca355f9409")0 

In case you can't see the post here iw what you need to do: 

A desktop entry needs to be created (use Kate or Kwrite) and then saved to the /home/[username]/.kde/Autostart directory and made executable.  The synlink that was created to tray.py should be deleted.  Log out and then back in.  Oddly, the icon shows up, but with the white artifact behind it, although I looked in /opt/wicd/images and the .png files are created with transparency.  Go figure... but I can see signal strength now:-)

CODE (and if you are not familiar with this, the [Desktop Entry] line needs to be part of the text file:

[Desktop Entry]
Encoding=UTF-8
Name=Wicd
Exec=/opt/wicd/tray.py
Icon=
Type=Application
StartupNotify=false

---

### Post by ResumeMan on 2007-09-04
Could someone give a nickel summary of how this differs from Network Manager? I see from the reviews that it looks like there's more info displayed by the GUI.

Does it do a better job of resuming after suspend? That's the biggest networking problem I've had to date.

Also, I updated the kernel using walkerk's OTHER tutorial; does this daemon work properly with that?

Thanks!

---

### Post by walkerk on 2007-09-04
> **ResumeMan said:**
> Could someone give a nickel summary of how this differs from Network Manager? I see from the reviews that it looks like there's more info displayed by the GUI.

Does it do a better job of resuming after suspend? That's the biggest networking problem I've had to date.

Also, I updated the kernel using walkerk's OTHER tutorial; does this daemon work properly with that?

Thanks!
 
On my laptop the wireless resumes after suspend w/out issues.. and yes, it does work with the kernel upgrade :)

The nicest feature imo is that daemon.py loads at boot up via init.d (w/ root privileges) so your wireless is up, running, and waiting for you to hit the net. I hate the damn key-ring nonsense with Network-Manager. Also, of course it has WPA1/2 capabilities (very easy), nice GUI, does both wireless and wired... just a couple of options..

---

### Post by ntlam on 2007-09-04
WICD did not work for me. I have to go back to network-manager even I have to try connecting several times before it gets connected.

---

### Post by walkerk on 2007-09-05
> **ntlam said:**
> WICD did not work for me. I have to go back to network-manager even I have to try connecting several times before it gets connected.

Sorry to hear that..

---

### Post by EXCiD3 on 2007-09-06
I still was unable to install with the script...However the manual installation still works great!

Do you think we need to run the script with sudo?

---

### Post by walkerk on 2007-09-07
> **EXCiD3 said:**
> I still was unable to install with the script...However the manual installation still works great!

Do you think we need to run the script with sudo?

The script does use sudo..
```
sudo apt-get -y install wicd
```

I'll take a look at it when I get home from work.

---

### Post by kleeman on 2007-09-07
I used the manual install and wicd works great: Edgy with a thinkpad T60. Kudos to the developers, this works much more reliably with WPA than network-manager did....

---

### Post by master_kernel on 2007-09-17
Good job! Looks like you get another invite:

WalkerK, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

---

### Post by siralphred on 2007-09-17
thanks for the script walker, but like EXCIDE mentioned the script didnt work but the manual did for me, also i had to restart to get it going btw i use SONY AR520

---

### Post by walkerk on 2007-09-18
> **siralphred said:**
> thanks for the script walker, but like EXCIDE mentioned the script didnt work but the manual did for me, also i had to restart to get it going btw i use SONY AR520

Could you let me know where the script is hanging? I've been trying to re-create it but the darn script works everytime for me :P

Thanks

---

### Post by walkerk on 2007-09-18
> **EXCiD3 said:**
> The script didnt work for me. It told me it didnt find Network Manager's archives. I am using Network Manager right now. The script ran fine, but WICD did not install. I am using Feisty if that helps.

**UPDATE:**
I used the manual install and everything went correctly. WICD works great and beats NetworkManager hands down.

Awesome job on the scripts/tuts! They make it so much easier than taking the time to figure it out myself...Thanks again and don't stop making tutorials!

Where did the script hand for you? Did you use the old bash script or this python version?

---

### Post by walkerk on 2007-09-18
Ok.. no responses so I re-wrote parts of wicd.py .. Hopefully this will work for you guys. 

are you guys running wicd.py with sudo? it should be:
```
sudo python wicd.py
```

Otherwise it'll return an error...

---

### Post by hippomofatumas on 2007-09-18
hi all,

at the end of the script i get:

Would you like to run the WICD GUI at this time? yes
sh: /opt/wicd/gui.py: not found


what went wrong? im running gutsy. ive got an inspiron 1420 with a 4965 draft-n. its been a big problem gettig it to work. i think i finally got iwlwifi driver working ok for it, but need to install wicd for wpa2 support i believe.

mucho thanks

---

### Post by CAPLinux on 2007-09-19
Hey Walker, Thanks for the Help.  I finally have WPA on my network.  Thanks again!!

---

### Post by walkerk on 2007-09-19
> **hippomofatumas said:**
> hi all,

at the end of the script i get:

Would you like to run the WICD GUI at this time? yes
sh: /opt/wicd/gui.py: not found


what went wrong? im running gutsy. ive got an inspiron 1420 with a 4965 draft-n. its been a big problem gettig it to work. i think i finally got iwlwifi driver working ok for it, but need to install wicd for wpa2 support i believe.

mucho thanks

hmm.. what do you get with
```
ls /opt/wicd
```?

try running the tray.. double click the tray icon to get the gui..
```
/opt/wicd/tray.py
```

---

### Post by walkerk on 2007-09-19
> **CAPLinux said:**
> Hey Walker, Thanks for the Help.  I finally have WPA on my network.  Thanks again!!

Good to hear :)

---

### Post by hippomofatumas on 2007-09-20
it says there is no such directory. something is realllly screwy lol. ill try the manual setup.

---

### Post by hippomofatumas on 2007-09-20
ok got it installed fine now and the program can run. but it still cant connect to my network. its wpa2 i believe. what driver should i select to use with my intel 4965 draft-n? ndiswrapper a windows driver? why cant i select the iwlwifi/iwl4965 driver i spent so long setting up lol

---

### Post by imdano on 2007-09-20
It's not asking about your wireless driver specifically, it's asking which wpa_supplicant driver to use.  Normally you should use wext.

---

### Post by walkerk on 2007-09-21
> **hippomofatumas said:**
> ok got it installed fine now and the program can run. but it still cant connect to my network. its wpa2 i believe. what driver should i select to use with my intel 4965 draft-n? ndiswrapper a windows driver? why cant i select the iwlwifi/iwl4965 driver i spent so long setting up lol

Good. I'll have to put in some tests to ensure that the program is correctly installed. :/

---

### Post by ResumeMan on 2007-09-23
I'm running the script (downloaded last night) and it hangs when it tries to contact

> Connecting to cle.linux.org.tw (140.112.8.136)]

And eventually times out and returns an error. This happens several times. The script continues the install, but when it gets to the end and asks if I want to run the GUI, it responds

> sh: /opt/wicd/gui.py: not found

I have tried the script several times with the same result.

Any ideas? I have company coming in a few minutes, maybe later this afternoon I'll try the manual install.

Thanks!

---

### Post by walkerk on 2007-09-24
do you have [ cle.linux.org.tw ] somewhere in your sources.list?

```
 cat /etc/apt/sources.list | grep cle.linux.org.tw
```

The reason I ask is because the script doesn't try to download anything from that domain. More than likely this is some other repository you have enabled that is no longer responding.

```
gksu gedit /etc/apt/sources.list
```

If you see that domain comment it out by adding a # to the begining of the line..

---

### Post by ResumeMan on 2007-09-24
Oh, sorry, I forgot to respond. I did it manually, and it worked. I haven't checked the sources.lst, I'll do that this evening.

---

### Post by romaluca on 2007-09-25
I have remove network manager.
I have install wicd from deb
I try to connect to a wifi network with it both it not works.

So i run gnome netowk settings and i configure my wifi from it.

Now from wicd i can connect and disconnect to this network.
But if i want to connect to another network i must reconfigure gnome network settings.
Why?
What i can do to use only wicd without reconfigure gnome network settings every time?
Thanks

---

### Post by Depressed Man on 2007-09-29
What if my driver isn't listed? I have an Intel 3945 which isn't listed at all on there, and its in the restricted drivers.

---

### Post by walkerk on 2007-09-29
> **Depressed Man said:**
> What if my driver isn't listed? I have an Intel 3945 which isn't listed at all on there, and its in the restricted drivers.

try using 'wext' as the driver. its the generic linux driver..

---

### Post by Depressed Man on 2007-09-29
```
vforviktor@vendetta-laptop:~$ ls /opt/wicd
ls: /opt/wicd: No such file or directory
vforviktor@vendetta-laptop:~$ /opt/wicd/tray.py
bash: /opt/wicd/tray.py: No such file or directory
vforviktor@vendetta-laptop:~$ 

```

Kinda stuck there. :(.

---

### Post by walkerk on 2007-09-30
> **Depressed Man said:**
> ```
vforviktor@vendetta-laptop:~$ ls /opt/wicd
ls: /opt/wicd: No such file or directory
vforviktor@vendetta-laptop:~$ /opt/wicd/tray.py
bash: /opt/wicd/tray.py: No such file or directory
vforviktor@vendetta-laptop:~$ 

```

Kinda stuck there. :(.

Try the manual method on the OP.

---

### Post by ryno519 on 2007-09-30
> **Depressed Man said:**
> What if my driver isn't listed? I have an Intel 3945 which isn't listed at all on there, and its in the restricted drivers.

I use the Intel 3945 driver and WICD works fine for me.

---

### Post by neo.patrix on 2007-10-01
Thank you , good work.

---

### Post by rgunn on 2007-10-07
all working great for me and is far less problematic in Gutsy. But having purged the network-manager what are my options for re-establishing a vpn connection as this was handled quite well by nm ?

thanks

Richard

---

### Post by walkerk on 2007-10-08
at the moment WICD doesn't do VPNs. I do believe Dano is working on this though...

---

### Post by imdano on 2007-10-08
> **walkerk said:**
>  I do believe Dano is working on this though...I'm actually getting pretty close to having something ready for people to test.

---

### Post by codedmin on 2007-10-26
Any news???

---

### Post by imdano on 2007-10-26
Almost there.  This upcoming week is going to be really busy (midterms), but I might be able to finish enough that I can put it up on the experimental branch.

---

### Post by cb474 on 2007-10-30
I tried WICD on a Thinkpad T60 with the AR5212 card. It seemed nice. I was hoping it would solve my difficulties connecting to encrypted wireless routers. But I didn't really spend much time trying it out, because it broke my laptop's ability to restart correctly.

My Thinkpad has always been finicky about restarts in Ubuntu (works fine with XP). It will freeze at the BIOS boot screen on a restart. Then I have to power off using the power button and restart from a complete shutdown.

But I had just finally fixed this problem by adding a reboot=b command to the menu.lst entry for the kernel. After installing WICD the restart problem returned. So I'm going back to Network-Manager for now.

---

### Post by konti on 2007-10-31
I really need wicd. Thanks for a verry nice Wireless client. But I also need a PPTP Vpn client. I noticed that when you have installed wicd it removes the network manager and network-manager-pptp also doesn't work anymore.

does anybody know a Vpn client that i can use in conjunction with wicd? I really need them both.

---

### Post by walkerk on 2007-11-02
> **cb474 said:**
> I tried WICD on a Thinkpad T60 with the AR5212 card. It seemed nice. I was hoping it would solve my difficulties connecting to encrypted wireless routers. But I didn't really spend much time trying it out, because it broke my laptop's ability to restart correctly.

My Thinkpad has always been finicky about restarts in Ubuntu (works fine with XP). It will freeze at the BIOS boot screen on a restart. Then I have to power off using the power button and restart from a complete shutdown.

But I had just finally fixed this problem by adding a reboot=b command to the menu.lst entry for the kernel. After installing WICD the restart problem returned. So I'm going back to Network-Manager for now.

I can't imagine how Wicd would cause this. When you removed it and re-installed Network-Manager did all work well again?

---

### Post by kleeman on 2007-11-02
I have a T60 and wicd and Ubuntu work fine. Your problem sounds like either a kernel or hardware issue and unrelated to wicd. Personally I would use the T60 test facility to check my hardware. Another suggestion is to download and compile the latest kernel to see whether this causes the issue to go away. If one of the (standard Ubuntu) kernel modules for wireless is buggy this might help

---

### Post by hooah212002 on 2007-11-16
Not sure if anyone out there is still having issues with the system tray not showing up, but heres what I did. 

Go to /opt/wicd folder and drag the tray.py file to the panel. When I tried to run it from a terminal, it went away when I closed the terminal. I am an Ubuntu/Linux noob so I am almost positive this goes against some unwritten rule about writing script, but hey, it worked.

---

### Post by dadio on 2007-11-16
Hi!

I am running Gutsy with an AMD Turion 64. I ran your WICD script and here is the result:

-----------------------------------------------------------------------------

Installation complete.

To enable the systray icon at boot add the following
to System > Preferences > Sessions

Name: WICD
Command: /opt/wicd/tray.py

Press <ENTER> to continue...
Would you like to run the WICD GUI at this time? y
sh: /opt/wicd/gui.py: not found

-----------------------------------------------------------------------------

I checked and there is not even a wicd folder under /opt/.

I would love to use WICD because I'm sick of entering my keiring password at logon to enable Network Manager.

Anyone now what went wrong or how to fix it??

---

### Post by walkerk on 2007-11-17
Try doing it manually in terminal...

```
echo 'deb http://wicd.longren.org gutsy extras' | sudo tee -a /etc/apt/sources.list

sudo apt-get update

sudo apt-get install wicd
```

**If you're using another version replace gusty (above, first command) with feisty, edgy, etc...**

once you've done the above WICD will be in your gnome/kde menu but you can run the gui from the terminal like so...
```
/opt/wicd/gui.py
```

Let me know :)

---

### Post by linux4909 on 2007-11-29
Thanx!!!! This Was Very Helpful!!!


+1

---

### Post by cb474 on 2007-12-04
> **cb474]I tried WICD on a Thinkpad T60 with the AR5212 card. It seemed nice. I was hoping it would solve my difficulties connecting to encrypted wireless routers. But I didn't really spend much time trying it out, because it broke my laptop's ability to restart correctly.

My Thinkpad has always been finicky about restarts in Ubuntu (works fine with XP). It will freeze at the BIOS boot screen on a restart. Then I have to power off using the power button and restart from a complete shutdown.

But I had just finally fixed this problem by adding a reboot=b command to the menu.lst entry for the kernel. After installing WICD the restart problem returned. So I'm going back to Network-Manager for now.[/QUOTE]

[QUOTE=walkerk said:**
> I can't imagine how Wicd would cause this. When you removed it and re-installed Network-Manager did all work well again?

Yes, reinstalling Network-Manager fixed the problem. I'm also dual booting Debian Testing (I'm migrating to Debian from Ubuntu) and when I installed Wicd in Debian the same thing happened. It was clearly a Wicd issue, because the problem immediately appeared after install Wicd, without having made any other changes on the system. For the time being, I've gone back to accepting not having reboot work, because Wicd is much better for me with connecting to WPA encrypted routers. But I'd really love to resolve this problem. I posted messages about it on the Wicd forums and the Debian forums and have gotten no responses.

---

### Post by DeLaNooch on 2007-12-07
Greetings,

I am having similar problems with the tray as outline above.  

I am running updated Feisty on an HP notebook w/ a properly working Broadcim 4318 card.  Wicd seems to work great in the little time I have used it, and immediately after install the tray icon appeared and worked perfectly.  

Not sure when exactly it stopped working, but now when I boot, I get nothing at startup.  When I run the file the system hangs and my only option is a hard reboot.  When I run the file inside a shell I get an output similar to: "Connecting to daemon. Success." Then it hangs.  I do not have the exact output at the moment, but I can get it.  

I do not get a blank white square.  

As far as I know I am running the most recent version of Wicd.  

Any ideas?  Thanks.

---

### Post by DeLaNooch on 2007-12-12
Problem solved same day as my original post.  The Wicd tray icon was running fine the whole time, however the notification area was disabled from my panel. DOH! I was quick to jump to conclusions and blame Wicd.

---

### Post by walkerk on 2007-12-12
LOL. I'm glad its working. :)

---

### Post by howardf42 on 2007-12-26
> **dadio said:**
> Hi!

I am running Gutsy with an AMD Turion 64. I ran your WICD script and here is the result:

-----------------------------------------------------------------------------

Installation complete.

To enable the systray icon at boot add the following
to System > Preferences > Sessions

Name: WICD
Command: /opt/wicd/tray.py

Press <ENTER> to continue...
Would you like to run the WICD GUI at this time? y
sh: /opt/wicd/gui.py: not found

-----------------------------------------------------------------------------

I checked and there is not even a wicd folder under /opt/.


Anyone now what went wrong or how to fix it??

My situation is almost identical except I'm running on a Dell Inspiron 6000.  My WiFi stopped working recently and I was looking for a fix for that and decided to give WICD a look, but it's not loading for some reason.  

Also, my 2wire router supplied by my Mexican ISP doesn't support WPA.  Does WICD support a WEP incription?

Thanks for your help.

Howard

---

### Post by walkerk on 2007-12-26
> **howardf42 said:**
> My situation is almost identical except I'm running on a Dell Inspiron 6000.  My WiFi stopped working recently and I was looking for a fix for that and decided to give WICD a look, but it's not loading for some reason.  

Also, my 2wire router supplied by my Mexican ISP doesn't support WPA.  Does WICD support a WEP incription?

Thanks for your help.

Howard

I had to update the repository location as the developer had moved it...

You can re-download the script or just do it manually...

Install WICD manually:
```
echo 'deb http://apt.wicd.net feisty extras' | sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
```
```
sudo apt-get install wicd
```

Now run it from terminal like so:
```
/opt/wicd/gui.py
```

Or find it in your menus.

And yes, WICD supports WEP :)

---

### Post by fooman on 2007-12-26
i needed to assign a static address for my laptop's wireless and couldn't get it working right using network manager.

works great using WICD.....thanks!  :)

---

### Post by walkerk on 2007-12-26
Glad it worked out :)

---

### Post by DreamClown on 2008-02-16
Wow. Getting wireless to work on my HPdv9000 (Gutsy 7.10) has been a hassle! I'm so frustrated atm. I have a Broadcom 4312 card and just installed WICD...but it still doesn't find my wireless network. I've spent HOURS trying various How-To's and nothing has worked. I've tried ndiswrapper, using the restricted drivers, etc. and yet still no wireless. One thing I love about Ubuntu is the community. So, I'm hoping someone can help me work through this issue. Thanks in advance for your replies!

~DC~

---

### Post by corin.gs on 2008-02-16
Hi all,

I'm having some trouble getting WICD to work with my Lenovo T61. I recently installed AwesomeWM and can't run network manager anymore, so I switched to WICD. I run (or ran, with nm) the iwlwifi drivers for my Intel 4965, and haven't been able to figure out how to get WICD to run those drivers. I can do pretty much everything but actually connect to my WPA1/2 network. It just sticks at 'Obtaining IP Address...' for a while and then says 'Not Connected'. That's all done with using the wext drivers, or at least that is the one selected. Any ideas?

Thanks...
c

---

### Post by kleeman on 2008-02-17
> **DreamClown said:**
> Wow. Getting wireless to work on my HPdv9000 (Gutsy 7.10) has been a hassle! I'm so frustrated atm. I have a Broadcom 4312 card and just installed WICD...but it still doesn't find my wireless network. I've spent HOURS trying various How-To's and nothing has worked. I've tried ndiswrapper, using the restricted drivers, etc. and yet still no wireless. One thing I love about Ubuntu is the community. So, I'm hoping someone can help me work through this issue. Thanks in advance for your replies!

~DC~

Flaky driver for that card is the problem:
 [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

If I was you I would cut my losses and get a cheap PCMCIA wireless card that you know is compatible (find one you know uses the intel or madwifi driver) and pop it in the laptop slot.

---

### Post by kleeman on 2008-02-17
> **corin.gs said:**
> Hi all,

I'm having some trouble getting WICD to work with my Lenovo T61. I recently installed AwesomeWM and can't run network manager anymore, so I switched to WICD. I run (or ran, with nm) the iwlwifi drivers for my Intel 4965, and haven't been able to figure out how to get WICD to run those drivers. I can do pretty much everything but actually connect to my WPA1/2 network. It just sticks at 'Obtaining IP Address...' for a while and then says 'Not Connected'. That's all done with using the wext drivers, or at least that is the one selected. Any ideas?

Thanks...
c

May be some useful stuff here:

[http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

I have had issues with WPA on a T60 in the past and solved them by upgrading various kernel modules. Since I was running Ubuntu 6.10 my guess is that if you are running 7.10 you may not be having the same issues I did.

---

### Post by corin.gs on 2008-02-21
> **kleeman said:**
> May be some useful stuff here:

[http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

I have had issues with WPA on a T60 in the past and solved them by upgrading various kernel modules. Since I was running Ubuntu 6.10 my guess is that if you are running 7.10 you may not be having the same issues I did.

That's what I originally looked at, but I don't think that is whats going on. My wireless connection to the WPA network works rather well using network-manager, other than me having to type in my huge psk every time I want to connect. I don't know what else it could be other than WICD. It works great for my wired connection, but that's not doing much for me obviously. Any suggestions?

Like I said, it finds the network just fine, it just won't connect. It just says 'Obtaining IP Adress...' and chugs at that for about thirty seconds and then switches back to doing nothing. Any other ideas?

Again, thanks for the help.

---

### Post by imdano on 2008-02-21
You can try running wpa_supplicant from the command line, and see if that's the point of failure when wicd tries connecting.  Find you wpa_supplicant.conf file by navigating to /opt/wicd/encryption/configurations/<your access point's bssid>.  Open up that file in a text editor and make sure everything more or less looks normal.  Then run wpa_supplicant and check the output to see if it's able to associate with your access point.
```
sudo wpa_supplicant -i <wireless interface> -c /opt/wicd/encryption/configurations/<your ap bssid> -D wext
```Post the output of that here if you're not sure what it means.  You could also add -d or -dd on the end to get extra debugging output as well.

You mentioned that your psk is really long. Do you use a passphrase or the psk directly?  How long is it?  Are there any non-alphanumeric characters in it?

---

### Post by corin.gs on 2008-02-21
Edit: Yeah change of plan. I did something stupid. Here is the actual output of the commands you gave me.

```
corin@firesign:~$ sudo wpa_supplicant -i wlan0 -c /opt/wicd/encryption/configurations/000f66a05fe5 -D wext

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Trying to associate with 00:0f:66:a0:5f:e5 (SSID='******' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:0f:66:a0:5f:e5
WPA: Key negotiation completed with 00:0f:66:a0:5f:e5 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:0f:66:a0:5f:e5 completed (auth) [id=0 id_str=]

```

That's all I get. It just hangs out here, which I'm pretty sure it's supposed to do. Anyway, that's the output. Ideas? Also, that config file that WICD uses...it put '$_PSK' as my psk= value...I'm not sure if that was normal. wpa_supplicant woudn't parse that, so I dropped my acutal psk in there and it seems to have worked. Thought it was worth mentioning.

Thanks again for any help, I appreciate it.

---

### Post by imdano on 2008-02-22
Ah ok, that's what I thought was going on.  For some reason wicd doesn't generate the wpa_supplicant.conf files correctly for all people, and $_PSK shows up instead of the psk itself.  I think you can fix it by opening up /opt/wicd/encryption/templates/wpa, and changing the $_PSK to $_KEY. Then in the wicd gui you enter the psk (the long hexadecimal string) instead of a passphrase.

---

### Post by RxRated on 2008-03-09
When I installed wicd I was using a wired connection.  Now when I boot up to connect wireless, it refuses.  When I click on the tray icon to configure it it will not open.  Any ideas why?  It works great on my other laptop.  BTW I am running gutsy with a realtek 8180L card using ndiswrapper.  It connects fine with network manager, but I like the interface of wicd better.

---

### Post by imdano on 2008-03-10
Run /opt/wicd/gui.py from a terminal and post any error messages you see.

---

### Post by RxRated on 2008-03-10
I deleted my wired configuration file and it works great now!!  Thanks!

---

### Post by kleeman on 2008-03-16
I upgraded my Thinkpad T60 to Gutsy (from Edgy) and wicd which worked flawlessly before is now acting a little strange.

It lists the network interface for both wired and wireless as eth0 and connects wireless on this interface. In the tray it says that a wired connection is present even though it is wireless. I tried switching the wireless interface to eth1 (which is standard for a thinkpad) but no dice. No wireless networks detected even after a full reboot. 

Does /etc/network/interfaces need editing? It only has lo at present....

---

### Post by clsrskv on 2008-05-05
I have a problem with wicd when suspend/resume. Wicd does not find any networks/does not connect for 45 secs. I solve this by clicking the tray icon and refresh, but that is not good enough, even though using nm takes longer time than this exercise... Does someone have a solution for this?

---

### Post by John Jason Jordan on 2008-05-05
I just upgraded from Gutsy to Hardy. Because of continuing problems with Network Manager I decided to try it again. (I had tried it once a couple months ago, but it didn't solve my problems.) Hpwever, now it is not even listed in Synaptic. I have every conceivable repository enabled. Can someone tell me where it is?

---

### Post by kleeman on 2008-05-06
It has a third party repository. Add it manually with the line
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

---

### Post by jerick70 on 2008-05-06
> **imdano said:**
> Ah ok, that's what I thought was going on.  For some reason wicd doesn't generate the wpa_supplicant.conf files correctly for all people, and $_PSK shows up instead of the psk itself.  I think you can fix it by opening up /opt/wicd/encryption/templates/wpa, and changing the $_PSK to $_KEY. Then in the wicd gui you enter the psk (the long hexadecimal string) instead of a passphrase.

Thanks imdano.  I was getting the endless "obtaining IP address" in WICD.  This fixed my WPA issue with WICD and an Atheros 5418 card with the lastest Madwifi svn dirvers.

Jerick:)

---

### Post by johnswb on 2008-08-29
This works great for me, thanks

uname -r
2.6.22-15-generic

---

### Post by mikewhatever on 2008-08-29
Has anyone been able to autoconnect to the hidden network, wpa2 protected, using wicd? I've been trying to figure that out with intel 3945abg. I can manually connect to the network by entering the ESSID and hitting connect, but before that the network in not visible, and it seems that no attempt to connect is made by wicd.

---

### Post by kleeman on 2008-08-30
> **mikewhatever said:**
> Has anyone been able to autoconnect to the hidden network, wpa2 protected, using wicd? I've been trying to figure that out with intel 3945abg. I can manually connect to the network by entering the ESSID and hitting connect, but before that the network in not visible, and it seems that no attempt to connect is made by wicd.

Even though it is hidden it should show up (as hidden) on the list "Choose from the networks below". I have connected manually to a hidden network and the essid then appears next to the list item. If it does appear you can tick the radio button to connect automatically.

---

### Post by mikewhatever on 2008-08-30
> **kleeman said:**
> Even though it is hidden it should show up (as hidden) on the list "Choose from the networks below". I have connected manually to a hidden network and the essid then appears next to the list item. If it does appear you can tick the radio button to connect automatically.

That's how it works in Windows, but I found no evidence it did work that way with WICD.
I've clicked the autoconnect button, but the problem is, the network is not in the list until I go to Network->Hiddent network and type the ESSID. Then the network appear, but it wouldn't autoconnect at this point too. I have to click connect under the network.
It's not a major issue, just trying to figure out why it wouldn't autoconnect.

---

### Post by kleeman on 2008-08-30
> **mikewhatever said:**
> That's how it works in Windows, but I found no evidence it did work that way with WICD.
I've clicked the autoconnect button, but the problem is, the network is not in the list until I go to Network->Hiddent network and type the ESSID. Then the network appear, but it wouldn't autoconnect at this point too. I have to click connect under the network.
It's not a major issue, just trying to figure out why it wouldn't autoconnect.

Looks like a driver dependent bug


[http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=408&st=0&sk=t&sd=a&sid=e6fb960b142e90fccc200c1324e8ce40&start=0](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=408&st=0&sk=t&sd=a&sid=e6fb960b142e90fccc200c1324e8ce40&start=0)

You could try version 1.5.1 it is working for me....

---

### Post by mikewhatever on 2008-08-31
If that's a driver bug, I'll probably need a better driver. What's 1.5.1?

---

### Post by F86Sabre on 2008-08-31
you do not need to install anything for wifi or bluetooth. i know this because i have a laptop running ubuntu 8.04.
go to network button at the top and click on it then click on the network. then enter the password and type of password and leve open key there and click enter. wait a few minutes and u are in the internet with wifi

---

### Post by mikewhatever on 2008-09-01
> **F86Sabre said:**
> you do not need to install anything for wifi or bluetooth. i know this because i have a laptop running ubuntu 8.04.
go to network button at the top and click on it then click on the network. then enter the password and type of password and leve open key there and click enter. wait a few minutes and u are in the internet with wifi

Good to know. Is that how you connect to a wpa2 protected hidden network?

Having searched a bit, I found a post discussing exactly the problem.
[http://ubuntuforums.org/showthread.php?t=769829&highlight=wicd+hidden](http://ubuntuforums.org/showthread.php?t=769829&highlight=wicd+hidden)
No solution is offered yet though.
I've also found that all the relevant wireless info is in /opt/wicd/data/wireless-settings.conf. All was correct, but the only thing confusing was 'hidden = False' line.

---

### Post by kleeman on 2008-09-03
> **mikewhatever said:**
> If that's a driver bug, I'll probably need a better driver. What's 1.5.1? wicd version 1.5.1 i.e. the latest stable version. Sometimes these programs "workaround" driver glitches.

---

### Post by Bobrm2 on 2008-11-14
Have followed  the thread. I've Intrepid Ibex installed. Wicd is set to wext. External programs (all three) are set to automatic. Nothing set in "General Settings".

This home network is using WEP.  Router is a D-Link, WRB-1310,

I log off each evening. When restarting Wicd has difficultly connection to the IP.
 How should I tweak the settings. BTW, I have no connection problems after the connection is finally made. Connected rates average -57dBm.

Have looked for a "manual" to assist me setting up(?).

Thank you,

Bob

---

### Post by Yanlux on 2008-12-04
Hello,
Kubuntu Intrepid and WICD 1.5.5 here and white background box in the WICD tray icon...
Tried anything found on the web to fix this but unable to solve.
OPT directory in empty...
Any help would be really appreciated, thanks.

---

### Post by s3kt0r on 2009-01-19
I realize this a long running thread, but it's not closed yet so here it goes:

I was a NM-user until I've heard of WICD and got curious about it - followed some aspects of walkerk's howto, uninstalled Gnome's NM, and running for the moment WICD 1.5.8, no flaws whatsoever. :)
Much easier to use, wireless config very straight-forward, ethernet no need to configure at all.
Never going back to NM, not saying it isn't good, just that WICD works best on my system.

walkerk and other users, nice thread, thank you.

---

