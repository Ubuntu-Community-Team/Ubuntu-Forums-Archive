---
title: "A Wireless Problem I Am Having"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by D1988 on 2008-08-13
I am having a problem connecting to my wireless network in Kubuntu 8.04 Hardy. I have posted this up on kubuntuforums.net but the nice fella helping me is also running out of ideas on this one. I thought I would post it here to grab the attention of more people who can maybe throw a few more ideas my way to get this working.

First of all - 

Laptop - Dell Inspiron 1720
OS - Kubuntu 8.04 Hardy Heron
Network Manager - WICD (uninstalled knetworkmanager)
Router - Belkin F5D7632-4

The problem - When I try to connect to the wireless with any form of security enabled, it will fail. I have tried connecting with WEP, WPA and WPA2. It will fail to connect everytime. However, when I try connecting to the wireless when there is no security enabled, it works perfectly without any problems. 
Wired connections work all of the time. No problems here at all.

What I have tried - Installed WICD and got rid of knetworkmanager, applied MAC address filtering and enetered my laptops wireless card MAC, tried setting a specific wireless channel, tried all different forms of security that I can enable on my router (WPA, WPA2, WPA/2, WEP).

I am really really stuck on this and would really like to keep my wireless secure rather than leaving it open to everyone.

I know this is for Kubuntu but if anyone has any ideas or a solution I will be extremely happy!

Thanks in advance for any help that you can provide. :)

---

### Post by nicedude on 2008-08-13
You should first try getting it to work with WEP and without the MAC address filtering and then enable filtering after you figure this out. WICD should work to let you set your WEP key and connect, I am not using it now but used to use it and it worked OK for me. Make sure when you go into your router and turn on WEP that you understand how to do it, for one when you choose the password phrase for WEP that generates 4 different keys and it will list them, so make sure to select say key #1 to be used and then copy that long number to a text file as that is what you need to enter into WICD to gain access. Then in WICD select WEP and use that long number which is your key. 

So see if you can connect by doing this with just WEP and post back and I will help you more if I can.

---

### Post by D1988 on 2008-08-13
Thank you very much for your reply.

I tried doing as you suggested but have had no luck at all with connecting when WEP is enabled. I even followed some guides to setup WEP incase I was doing something wrong but it seems I was doing it correct in the first place.

But yeah, still just sits saying "obtaining IP address" and then fails. :(

---

### Post by nicedude on 2008-08-13
Then I have a suggestions, we can try some commands at the command line to try and setup your wifi adapter and make sure its in the right mode to work correctly. This is independent of any network manager and thereby should work.

Commands - replace [interface] with whatever your wifi is addressed as such as ath0 or wlan0 dont include the brackets though just replace the whole thing

THIS WILL MAKE SURE ITS IN MANAGED MODE
sudo iwconfig [interface] mode managed

HERE WE SET CHANNEL - replace [channel num] with the channel number your router is using
sudo iwconfig [interface] channel [channel num]

THIS WILL SET TO RIGHT NETWORK - use your routers broadcasting name like linksys or netgear
sudo iwconfig [interface] essid your-routers-essid

THIS WILL SET WEP KEY - replace XXXXXXX with your key, you could also try restricted in place of open if open doent work
sudo iwconfig [interface] key open XXXXXXXXXXXXXXXXXXXXXXXXXX

THIS WILL TRY TO CONNECT TO ROUTER AND GET AN IP
sudo dhclient [interface]


Also make sure you copy the WEP key correctly or it will just sit there and do nothing. For example o & 0 look very similar but will not interchange.

---

### Post by tl3000 on 2008-08-16
> **D1988 said:**
> I am having a problem connecting to my wireless network in Kubuntu 8.04 Hardy. I have posted this up on kubuntuforums.net but the nice fella helping me is also running out of ideas on this one. I thought I would post it here to grab the attention of more people who can maybe throw a few more ideas my way to get this working.

First of all - 

Laptop - Dell Inspiron 1720
OS - Kubuntu 8.04 Hardy Heron
Network Manager - WICD (uninstalled knetworkmanager)
Router - Belkin F5D7632-4

The problem - When I try to connect to the wireless with any form of security enabled, it will fail. I have tried connecting with WEP, WPA and WPA2. It will fail to connect everytime. However, when I try connecting to the wireless when there is no security enabled, it works perfectly without any problems. 
Wired connections work all of the time. No problems here at all.

What I have tried - Installed WICD and got rid of knetworkmanager, applied MAC address filtering and enetered my laptops wireless card MAC, tried setting a specific wireless channel, tried all different forms of security that I can enable on my router (WPA, WPA2, WPA/2, WEP).

I am really really stuck on this and would really like to keep my wireless secure rather than leaving it open to everyone.

I know this is for Kubuntu but if anyone has any ideas or a solution I will be extremely happy!

Thanks in advance for any help that you can provide. :)

Check the following bug report and if your situation is the same issue then you might try the recently posted workaround posted at the end of that thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

---

