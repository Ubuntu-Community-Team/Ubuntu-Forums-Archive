---
title: "WiFi"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-08-06
Hey Guys!
 How do I turn my wifi on? I always use my cable, but need to travel in the morning and would like to find some wifi along the way. I am not even sure where to begin?

---

### Post by loboc on 2008-08-06
first see if your wifi card is reconized by opening a terminal and typing

```
iwconfig
```

if its in there then you should be able to configure it using network-manager

```
 sudo apt-get install network-manager
```

and the network manager applet ( right click on the panel and add it)

---

### Post by tamoneya on 2008-08-06
well first of all check for any switches on the side of the laptop.  Most laptops have a physical switch (or button combination) that enables and disables wireless.  Then when you are sure you have it enabled type:```
ifconfig
```If you see the interface "wlan0" you should be set.  If you dont then type:```
lspci
```In there look for your wireless adapter.  Then google: "ubuntu <wireless adapter>".  That should get you a solution.

---

### Post by duckfeet on 2008-08-06
...and of course, if none of this works, *then* you get to do the interesting stuff some of us had to do, trying to get these wirless doodads to work...sleepless nights, and a fast and severe learning curve, as you download Windows apps, and try to get them to make friends w/unix...so if that little blue light *doesn't* come on, and there is no "wireless" in yer network manager...then the fun begins....

---

### Post by LindaLou on 2008-08-07
I entered the code " sudo apt-get install network-manager" into a terminal and received this response:

linda@laptop:~$ sudo apt-get install network manager
[sudo] password for linda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network


What is my resolve to this??  Thanks in advance.

---

### Post by halitech on 2008-08-07
are you connected to the internet right now with that machine?

edit: think you had a typo in your command, it should have been
```
sudo apt-get install network-manager
```
not 
```
sudo apt-get install network manager
```

---

### Post by LindaLou on 2008-08-08
Hi halitech,

Yes, I am wired to the internet as my router got "cooked" and is no longer usable.  I do want to connect to my office neighbour's wifi which I was doing when I was running Windows.  Thanks for the correction! copied and pasted the proper code and this is the result

vale@laptop:~$ sudo apt-get install network-manager
[sudo] password for vale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libartsc0 liblualib50 kdelibs-data liblua50 libaudio2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
vale@laptop:~$ 

Not sure what this all means, but I am desperate to have a wifi connection.  The office signal is practically 100%.  So, what do I do next?  I really hope this is going to painless and easy!!  I've been reading thru soo many posts in the forum for a few weeks now but they are all related to at home wireless routers.  
Thanks in advance for the help.

---

### Post by okey666 on 2008-08-08
> network-manager is already the newest version.
That mean that as you have not removed it, the network manager is already as default. Then (if you have not removed it) look at your status bar area and you will see a little picture of a pc (or such like). (left)Clicking on this icon will bring up a menu. You will probably see a option for wired connections. Below that (if your card has been recognised) will be a list of all networks available. Click on the one you want and then enter in any other info needed.

If you don't see wireless options do:
```
sudo iwconfig
```
This will then print out all the networking interfaces on your machine. If they are wireless, it will then print information about them. If they are not wireless it will simply say "no wireless extension".

If you only have non wireless interfaces displayed, then you will have to configure your card...:mad::mad::mad:

edit:
yes its also probably a good idea to look for a wireless switch on your laptop (and also make sure it has wlan). Another reason for networks not showing could be that your wireless is not in roaming mode. You may want to enable this...
system>>admin>>network then select your wireless connection (if it is there) and go properties then tick the "roaming" check box.

---

### Post by LindaLou on 2008-08-08
ok, when I right click on the pc icon Enable Wireless is checked off. I have checked that my card is recognized.

Terminal response from "sudo iwconfig"

vale@laptop:~$ sudo iwconfig
[sudo] password for vale: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The wireless button is on and glowing a very nice shade of blue.  (Learned the button mistake a few years back after a rather embarrassing Blonde moment at a HP tech shop:oops:)

And, after all of this, I took the day off from the office and am home and I know definitely that there is not wifi near by!!  

Am I correct in saying that I will have to do this:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4306)

with this as Step 2b
 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)
I have a BCM4306 (v 3) on my HP pavilion zv5000 Athlon AMD64

I have read and printed out the alex_kent_18 info and was reaaaaaalllllly hoping that I could some how just avoid allllll of this!!

Maybe not, huh??

---

### Post by okey666 on 2008-08-08
simply right click on the network-manager icon and click the wireless check box, this will enable it. Then left click on it to select your network...

```
wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2346 B
Encryption keyff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

That shows that your wireless drivers are ready to go. This means that you just need to enable it by clicking that check box.

edit:
DON'T do what it says on that other thread, that basically reinstalls the drivers on your system, replacing them with windows drivers (a last resort). Hopefully, the drivers will work fine. The only problem is is that you have not enabled wireless networking with the manager.

---

### Post by LindaLou on 2008-08-08
I am sooooo happy that I don't have to go through the steps outlined in the links I mentioned!!\\:D/

OK, did a right click on the icon and Enable Wireless has a Check Mark next to it.  Left click give shwos me that Wired Network is enabled (dot next to it) and underneath is 
Wireless Networks, 
Connect to Other Wireless Networks... 
Create a New Wireless Network...
Connect to 802.1X Protected Wired Network...
Manual Configuration

---

### Post by okey666 on 2008-08-10
Under where it says "wireless networks" should appear a list of all the wireless networks in range. If there are not any, then the list will not appear. If you think the network manager is wrong, you can run:
```
sudo iwlist wlan0 scan
```

This will show a list of all the networks in range. (note: the command may have to be run a few times to pick up all networks).

But... I think you said you were at home with no network, so wait until you get one to try it out. I'll be waiting for results... (and ready to help if it all goes wrong)

---

### Post by LindaLou on 2008-08-12
It wasn't until late afternoon that I was able to try the wifi.  My partner brought his laptop running Win XP.  There were 6 wireless connections - 1 unsecured at 100% (the neighbour). I followed all your instructions and none of the wifi's were listed. I even clicked on Connect to Other Wireless Networks,and entered the neighbours listing.  All to no avail.  None of the connections appeared in the scan thru the terminal.

Unfortunately, this all took place at the end of the day.  I wont be able to get back to this wifi issue until tomorrow or Thursday.  If you have any more suggestions, questions, etc. please let me know.  It would be super if I could have my laptop connected at the office.  
I appreciate allll your time and efforts-immensely.

---

### Post by Renovatio on 2008-08-12
I'm not sure if this will help, but I had the same problem - my wireless card was enabled, the blue light was on, but there would be no wireless networks listed under "Wireless Networks". I was able to make Network Mnager "see" all available wireless networks only after leaving the wirless card on "roaming mode".

---

### Post by LindaLou on 2008-08-12
Hi Renovatio, thanks for the info.  I did check to see if "Roaming" was enable and it was.  While i wait for some further threads/comments I'll continue to do some more surfing on this.  I'm sure it is something simple that will resolve :-k  this but MAN!!  I would love to have wireless!!!  [-o<

---

### Post by okey666 on 2008-08-12
Hmm... well if you are sure the networks are not showing up in the terminal (do it several times to make sure) then its a bigger problem. With Hardy though it seems most drivers work now and I can't help you with them. Whats the out put you get from the terminal scan? I would suggest trying a different wireless manager (like wicd) but if the networks are not showing up after several scans through the terminal they probably wont help you.

---

### Post by LindaLou on 2008-08-12
I'm going to use your advice - several attempts at the terminal ("scan) and see what happens.  Once I'm back at the office I'll see what happens, using your advice and post the results.  Keep your fingers crossed!!  It's just unfortunate that there is no wifi close to my home!!  Would certainly solve this issue much quicker.

---

### Post by Slug71 on 2008-08-12
moved

---

### Post by okey666 on 2008-08-14
> **Slug71 said:**
> moved
what? You are not admin?

---

### Post by LindaLou on 2008-08-15
Thanks Oscar!  I was a bit confused with the "moved" and annoyed as I am still wanting to work with the thread in resolving my wifi connection!

:)

---

### Post by Slug71 on 2008-08-17
> **okey666 said:**
> what? You are not admin?


Lol, nah i dont know how to delete a post so i just edited it and wrote moved since you have to write something.:lolflag:

---

### Post by Slug71 on 2008-08-17
And sorry bout that Linda, unfortunately i cant help you either as im have the same trouble as you are which is why i was gonna post something and then realized that may damn card wasnt even on. But now i have it on and cant connect.

---

### Post by okey666 on 2008-08-18
If the network manager fails, you can always try Wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by nicedude on 2008-08-18
Unfortunatly WICD is not going to solve this problem. If "sudo iwlist wlan0 scan" finds nothing when you know there are wifi networks nearby ( and wlan0 is what shows up in iwconfig as your wifi ) then it means that something is not right with your Wifi adapters driver. I have seen this several times and I am in the proccess the last day of helping another guy here who's wifi does the same thing ( shows up in iwconfig - but never will show anything from iwlist scan ). Out of all the posts here I don't see where either Andrew or Linda have given their Wifi adapter models ( this is of critical importance as the different chipsets take different drivers etc ). So please list both of your wifi adapter chipsets ( if you can't find out then list your laptop model # & series i.e. I have a ACER 5520-5716 this info is on the bottom of your laptop ) armed with that info I will find out what wifi adapter your machines use and help you get your wifi working properly.

I only use Atheros based chipsets ( I have a guide I wrote here in the forums for my model ) but I am actually getting good at diagnosing Broadcom etc as well due to helping others. Monday afternoon/evening I will check back here and if you post your model numbers & or wifi chipset info ( just tell me the chipset if you are 100% sure as it saves me googling it ) then I will help you and we will get your wifi going.

---

### Post by stalkingwolf on 2008-08-18
If your wifi connection is showing up and configured in 
System > Admin > Network, and you still cannot connect
you might give WIFIRadar a try.  It is in the repository.

---

### Post by LindaLou on 2008-08-18
hi nicedude,

My HP Pavilion zv5000 has a BCM 4306 (v.3), 32 bit, driver 8139too, driver version 0.9.28. 
I can't for the life of me find my Ubuntu notebook which had the terminal code listed to display the above info.  I jotted down the above info in my day planer but not the code.  :oops: If you would like a terminal display, please tell me the code and I will post the info.

---

### Post by nicedude on 2008-08-18
Ok Linda you have a newer Broadcom chipset wifi, allot of people report problems with your chipset with Ubuntu and Linux in general. I think I found the answer why and how to fix. You see Ubuntu comes with a couple of Broadcom drivers that are supposed to work, but don't with newer adapters. This is why I believe your card shows up in iwconfig but does not work. So the answer is a package called b43-fwcutter which is a utility to download a driver from Broadcom for your chipset, which for legal reasons Ubuntu could not include.


HERE IS THE COMMAND TO INSTALL IT

sudo apt-get install b43-fwcutter

AFTER YOU INSTALL THAT HERE IS THE COMMAND TO GET IT TO DOWNLOAD A DRIVER FOR YOU

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

When you run that command it will launch a script that should download your correct driver and install it. You may need to reboot for changes to take effect, but I am unsure.

Please do this and then run the following 2 commands

iwconfig

change ??? to whatever your iwconfig output listed as your wifi adapter ( wlan0 ath0 etc )

sudo iwlist ??? scan

and post the result ( note there must be some kind of wifi nearby for list to see something )

TRY THIS AND POST BACK

---

### Post by sirius1980 on 2008-09-24
hey nicedude... 
 
I have the same problem as linda.. i tried sudo apt-get install b43-fwcutter
and it gave me  
E: Couldn't find package b43-fwcutter

please help me get my wifi going... 
thanx

---

