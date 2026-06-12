---
title: "[SOLVED] New to Ubuntu (Wubi)"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Atallicus on 2008-06-26
I used the Wubi installer last night to install Ubuntu on my Windows vista sp2 machine last night.  I must add that the installation was simple, and went off without a hitch.  What an excellent way to get started using a linux type OS.

Now to my issue.  Tried to connect to Pidgin and the internet and I am apparently not getting my wireless internet connection(therefore typing this from the Windows side).  I have NEVER used linux before, so any advice you give me needs to be very newbie :D

From the instructions I have to assume it should automatically detect my wireless internet connection, except it doesn't.  Can anyone please get me pointed in the right direction.  I'm not a computer genius, but I've learned a few things from my husband, who was a computer science major.  I know he has run linux, but never used Wubi or Ubuntu.  

Thanks for any help you may provide.

---

### Post by avtolle on 2008-06-26
This is likely related to your wireless card. At the terminal (Applications>>Accessories>>Terminal) enter```
lspci
```and post the results so we can see what wireless card your computer uses.

EDIT: You will need to do this within your Ubuntu install. Alternatively, could you look in Windows (I'm not familiar with Windows, but I know you can find this out somewhere) and post which wireless card the computer has?

---

### Post by Canis familiaris on 2008-06-26
Which Wireless Card are you using? 
Try System->Administration->Hardware Drivers and see whether it lists your wireless card. If it does you may easily install it.

---

### Post by Atallicus on 2008-06-26
Alright, so I am assuming this is bad.  To the first poster, the ispce command says its invalid.  To the second post, the only driver listed is my nvidia driver, no wireless one.  I am assuming this is about to get very confusing.  But i am always ready for a challenge, so what is my next step?

Thankyou for your time by the way.

Edit: Sorry didn't list my card Intel(R) Wireless WiFi Link 4965AGN
Connected to a Dlink Router.

---

### Post by Tomatz on 2008-06-26
> **Atallicus said:**
> Alright, so I am assuming this is bad.  To the first poster, the ispce command says its invalid.  To the second post, the only driver listed is my nvidia driver, no wireless one.  I am assuming this is about to get very confusing.  But i am always ready for a challenge, so what is my next step?

Thankyou for your time by the way.

Edit: Sorry didn't list my card Intel(R) Wireless WiFi Link 4965AGN
Connected to a Dlink Router.

The command is:

**[SIZE="5"]lspci[/SIZE]**

---

### Post by Atallicus on 2008-06-26
> **Tomatz said:**
> The command is:

**[SIZE="5"]lspci[/SIZE]**

Sorry I type bad.  I used Ispci. Which I am seeing now is apparently wrong also. Be back with more info.

---

### Post by Atallicus on 2008-06-26
Okay so.  lspci lists my Intel corporation ProWireless 4965AG or AGN Newtork Connection.  But its not listed in hardware drivers in system.

---

### Post by Tomatz on 2008-06-26
**L**ima **S**iera **P**apa **C**harlie **I**ndego


Not **I**spci ;)

Its easily done also to save time and confusion you can copy and paste commands off the forum.

---

### Post by avtolle on 2008-06-26
I was under the impression that drivers for intel wireless cards were contained in the kernel. I have an Atheros 5007 card in my laptop that required a bit of work to get going, so I am not familiar with yours. Can you access the net from your Ubuntu install wired? You mentioned you were posting from Windows, thus the query.

---

### Post by Atallicus on 2008-06-26
Except I can't copy and paste because I'm on Windows and I have no internet on the ubuntu side :P so i have to restart the computer every time I want to give you guys information.

So I ran lspci and it listed everything including my wireless card.  What is my next step?  

Sorry to be so new at this, I searched through the forums and google, and found some similar problems, but not quite the same, most of them without any clear answers.

---

### Post by Tomatz on 2008-06-26
I think a macbook uses that adaptor. Below is a link that should get you up and running:

[http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/)

Just copy and paste the commands one by one into the terminal (without the numbers on the left). After just l-click on the network icon in the system tray (top r-hand corner) and connect to your network.


;)

---

### Post by Atallicus on 2008-06-26
> **avtolle said:**
> I was under the impression that drivers for intel wireless cards were contained in the kernel. I have an Atheros 5007 card in my laptop that required a bit of work to get going, so I am not familiar with yours. Can you access the net from your Ubuntu install wired? You mentioned you were posting from Windows, thus the query.

Well here is the thing.  My husband really deals with all of the internet things, so I wouldn't have a clue to begin where to hook up wired internet.  The house is set up for wireless, and honestly I think the router is probably in the basement.  So running a wire really isn't an option.

Yes I am posting on windows from the same computer.  Which is why I am confused as to why the internet doesn't work on the ubuntu side.

---

### Post by Atallicus on 2008-06-26
> **Tomatz said:**
> I think a macbook uses that adaptor. Below is a link that should get you up and running:

[http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/)

Just copy and paste the commands one by one into the terminal (without the numbers on the left). After just l-click on the network icon in the system tray (top r-hand corner) and connect to your network.


;)

However, will it make a difference that this is an HP and not a mac?

---

### Post by Tomatz on 2008-06-26
> **Atallicus said:**
> However, will it make a difference that this is an HP and not a mac?

Nah

Its the same card as yours and mac use the same intel chipset found in pc's.

:)

---

### Post by Atallicus on 2008-06-26
> **Tomatz said:**
> Nah

Its the same card as yours and mac use the same intel chipset found in pc's.

:)

Okay, so since I am great at screwing things up, before I try this. I just type each line in and hit enter after every one?  I feel so like i am asking dumb questions.  Thankyou again.

---

### Post by avtolle on 2008-06-26
OK, you will need to d/l the tar file (the wget instruction) under Windows, then get it to your Ubuntu installation before doing anything else. Do you have access to a usb "stick" to copy the file from madwifi to so you can get it to your Ubuntu side?

EDIT: all the instructions in the tutorial assume you are working in Ubuntu, using the terminal. Since you have posted that you are in Windows for access to the internet, I thought I should point out that you will need to have net access to d/l the file referenced in the wget command. BTW, when installing through Wubi, did you let Wubi d/l the iso and install it, or were you working from the CD? I ask that because to get build-essential you will need to have internet access on the Ubuntu side unless you have the CD, which, I believe, has build-essential on it, and you can use it for your source to get and install it. You likely could d/l build -essential using the Windows browser from a Ubuntu mirror, if it isn't on the CD. Otherwise, you may need to download a package in Windows (I'll try to find the link) and burn it to a CD to load on the Ubuntu side. All this, BTW, is why I was asking whether you could get to a wired connection. :-)

---

### Post by Tomatz on 2008-06-26
> **Atallicus said:**
> Okay, so since I am great at screwing things up, before I try this. I just type each line in and hit enter after every one?  I feel so like i am asking dumb questions.  Thankyou again.

Your not dumb, just new to this ;)

You can hilight, copy and paste them into the terminal. And yes you press enter after each one.

---

### Post by Atallicus on 2008-06-26
> **avtolle said:**
> OK, you will need to d/l the tar file (the wget instruction) under Windows, then get it to your Ubuntu installation before doing anything else. Do you have access to a usb "stick" to copy the file from madwifi to so you can get it to your Ubuntu side?

I don't have a USB stick, but I have an external drive I can copy it to, will that work?

I'm not seeing where to download the file from though.

---

### Post by Tomatz on 2008-06-26
> **avtolle said:**
> OK, you will need to d/l the tar file (the wget instruction) under Windows, then get it to your Ubuntu installation before doing anything else. Do you have access to a usb "stick" to copy the file from madwifi to so you can get it to your Ubuntu side?

Yeah thats right :)

Click the following link and **download**. Then **put it onto a flash drive.**

[http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)

**Boot ubuntu**

Then put the file onto your **desktop** (ubuntu)

Open a **terminal**

In the terminal type:

```
cd ~/Desktop
```

Then go to the howto and just **miss out step 2** ;)

---

### Post by avtolle on 2008-06-26
[http://packages.ubuntu.com/hardy/devel/build-essential](http://packages.ubuntu.com/hardy/devel/build-essential) is the link to the build-essential package. Given the size of it, you could also use a usb stick to transfer it to the Ubuntu side, and install it from there. Only if you need to do this; hopefully, it is on the CD (if that's how you installed under Wubi) and you can simply install it from there using Synaptic (System>>Administration>>Synaptic Package Manager).

---

### Post by piousp on 2008-06-26
Houston, we have a problem...

I dont think you will be able to do the first 2 steps:

> ```
sudo aptitude install build-essential
wget -c http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz
```

They already posted the solution for step 2, but there's still the same problem for step 1. You'll need an internet access for downloading that package.

---

### Post by avtolle on 2008-06-26
Yes, you can put in on an external drive.

---

### Post by toolzen on 2008-06-26
> **Atallicus said:**
> 

So I ran lspci and it listed everything including my wireless card.  What is my next step? 

You need to know what channel/frequency your wireless router is set  to, and you need to know what the name of your wireless network is. If everything is still the default on your router, you could probably find that information by googling: <router manufacturer> <router model> default channel. For example in a google search box I type:

linksys wrt54g default channel

and now I know my default channel is 6.

If your husband originally set up the network, ask him the network name. The name of my home network is "hyper" for instance.

If you can find out these two bits of inormation (channel and network name(also known as essid)), then you can do the following:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid hyper channel 6 mode managed
sudo ifconfig wlan0 up
sudo dhclient wlan0

Then wait for that last command to finish, then type:
ping google.com

Of course you would change "hyper" to whatever your network       is and "6" to whatever channel you use.

---

### Post by Atallicus on 2008-06-26
> **toolzen said:**
> You need to know what channel/frequency your wireless router is set  to, and you need to know what the name of your wireless network is. If everything is still the default on your router, you could probably find that information by googling: <router manufacturer> <router model> default channel. For example in a google search box I type:

linksys wrt54g default channel

and now I know my default channel is 6.

If your husband originally set up the network, ask him the network name. The name of my home network is "hyper" for instance.


If you can find out these two bits of inormation (channel and network name(also known as essid)), then you can do the following:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid hyper channel 6 mode managed
sudo ifconfig wlan0 up
sudo dhclient wlan0

Then wait for that last command to finish, then type:
ping google.com

Of course you would change "hyper" to whatever your network       is and "6" to whatever channel you use.

Okay I did all of this, finding out that my default channel was 11.  Here is what I got.

Internet Systems consortium dhclient v3.06

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

Listening on LPF wlan0/00.ld/:e0:36:63:0f
sending on LPF wlan0/00.ld:e0:36:63:0f
sending on socket/fallback

DHCP discover on wlan0 to 255.255.255.255 port 67 interval 3
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 5
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 11
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 12

No DHCPoffers received.
no working leases in persistent database - sleeping


when pinging I get
unknown host google.com



This is not copy pasted, I typed it all out as I have no idea how to save a copy when I restart the computer though I am sure I could save it somewhere and paste it here.

Edit: Does it matter that I am typing 11 for the channel when it is really 11n? Our internet name is Qorey, but should it be capitalized or not?

Edit2: Also, its encrypted internet with a key, that is going to matter too I think.

Will this work?
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

---

### Post by toolzen on 2008-06-26
> **Atallicus said:**
> Okay I did all of this, finding out that my default channel was 11.  Here is what I got.

Internet Systems consortium dhclient v3.06

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

Listening on LPF wlan0/00.ld/:e0:36:63:0f
sending on LPF wlan0/00.ld:e0:36:63:0f
sending on socket/fallback

DHCP discover on wlan0 to 255.255.255.255 port 67 interval 3
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 5
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 11
DHCP discover on wlan0 to 255.255.255.255 port 67 interval 12

No DHCPoffers received.
no working leases in persistent database - sleeping


when pinging I get
unknown host google.com



This is not copy pasted, I typed it all out as I have no idea how to save a copy when I restart the computer though I am sure I could save it somewhere and paste it here.

Edit: Does it matter that I am typing 11 for the channel when it is really 11n? Our internet name is Qorey, but should it be capitalized or not?

I certainly know how much of a pain it can be to not have internet working - when I had trouble with mine I would have to read/post threads on my brother's windows machine, then run up to my room to try possible solutions - it took forever! Hang in there though - we'll get this up and running. Remember, things in linux are meant to be powerful and highly customizable, but not necessarily easy.

As far as the channel - 11 should be what you need. Try this:

sudo iwlist wlan0 scan

This should give you the names of all available wireless networks in your area - use your network and when connecting type it in as it is listed as you see it in the scan. Another thing you need to know is if your husband put a key code on your router. This is like a password, except usually it is some randomly generated hexadecimal number. If you do have a key code, then:

-type
sudo ifconfig wlan0 down

sudo iwconfig wlan0 essid qorey channel 11 mode managed key 012-34-5678

sudo ifconfig wlan0 up

sudo dhclient wlan0

Again change 012-34-5678 to whatever your key code is.

You should either get the same error message (meaning we need to try something else) or you'll get something along the lines of "wlan0 bound to address blah blah." If you get that second message - success! otherwise - curses!! 

I'm at work and get notified as soon as you reply, so we can probably get this going pretty soon - hang in there.

---

### Post by Atallicus on 2008-06-26
Thankyou so much for the help, right now I am on the search for my network key on another computer in the house.  Then I will try your advice.

---

### Post by Atallicus on 2008-06-26
Okay :D running iwlist does INDEED list my internet.

I put in the commands, entering my key.  It gives me the same error as before.  Does it matter that Qorey is capitalized? And other places I read say put the essid in quotes.  Will these things make a difference?  Thanks again.

Edit: Some people in my wow guild forums are saying this also

Quote
From: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Use:

sudo iwconfig <ath0> essid <essid> ap <xx:xx:xx:xx:xx:> key <XXX> mode <> commit

Then

sudo dhclient <ath0>

Check cat /etc/resolv.conf to see if theres a DNS server registered

you can test connection resolution w:

search google.com
nameserver 209.53.4.130

Quote

---

### Post by Atallicus on 2008-06-26
Also one other thing.  If I co to system-administration-network, choose wireless network and click properties.  I can put qorey in for the internet name, choose hexadecimal for my key and Automatic DHCP, however, my hexadecimal key doesn't fit into the windo provided.  It's too long. So I can enable it from in there, but it doesn't work because my key doesn't fit.

Edit: also I should mention that when I get that error, it does say there is already a pid file /var/run/dhclient.pid with pid 0

---

### Post by toolzen on 2008-06-26
> **Atallicus said:**
> Also one other thing.  If I co to system-administration-network, choose wireless network and click properties.  I can put qorey in for the internet name, choose hexadecimal for my key and Automatic DHCP, however, my hexadecimal key doesn't fit into the windo provided.  It's too long. So I can enable it from in there, but it doesn't work because my key doesn't fit.

Putting the essid in quotes should not make a difference, but you can try it.

Try logging into your router and see what key it has there. This can be done by opening firefox and in the address bar you type in the IP address of your router, and then the user name/password. All of this information can be found on google, unless at some point somebody changed the default username and password for your particular router model.

My router has this web interface that comes up with all sorts of buttons and checkboxes for different things. I can go to wireless>security and change the type of security I have. That is where you want to assign/find the key code.

Lets try a different approach:

unplug your cable/dsl modem.
unplug your router
count to 20
plug in your modem and let it finish connecting
plug in your router and let it get all the way up and running.

sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid Qorey mode managed channel 11 key 123456
sudo ifconfig wlan0 up
sudo dhclient wlan0

If that doesn't work, the only other thing I know to do is for either you or your husband to log onto the router, and set up a different means of security - such as MAC filtering. You may even want to restore your router to all of it's factory default settings - which should be possible through the router's web interface. I know this sounds a bit extreme, but I had the same problem you did - where all my hardware seemed to be functioning, and all of my setting on ubuntu seemed to be correct, but I still couldn't connect. I restored my router, set up my method of security, and connected using the commands listed above - then I connected with no problems.

---

### Post by Atallicus on 2008-06-26
Well, I guess I will have to keep you updated on this situation over the next few days(have little ones running around I need to tend to also).  My husband is out of town, and he would have to be the one to do all the unplugging with it being in the basement and everything.  I'm sure the encryption is what is causing the issue.  Though where we live I am not entirely sure why we have MACK TRUCK encryption on our internet, silly nerdy computer husband :D

I truly appreciate all of your help and when I get a chance to speak with my husband this evening I will have him help me through the rest of the steps of changing the encryption.  Thankyou again!  I actually am at least understanding now why it doesn't work.

---

### Post by eriqjaffe on 2008-06-26
This may be a little late, but you don't have to move things around via an external drive - your C: drive will be available to Ubuntu directly, just navigate to \host in Nautilus (or "cd \host" in a terminal).

Might help save you a bit of extra file copying.

---

### Post by Atallicus on 2008-06-26
> **eriqjaffe said:**
> This may be a little late, but you don't have to move things around via an external drive - your C: drive will be available to Ubuntu directly, just navigate to \host in Nautilus (or "cd \host" in a terminal).

Might help save you a bit of extra file copying.

This is good advice t6hankyou, however it's looking like my internet is a problem with the gazillion bit encryption my husband felt he needed to put on the network.  Hopefully if we change that or reset the settings it will work.  I'll let you guys know after we have time to take alook at it later on.  Thankyou again :D

---

### Post by Atallicus on 2008-06-26
My husband is wondering if Ubuntu doesn't support 128 bit encryption, because he appears to be unwilling to reset the router config or change the encryption.

---

### Post by Atallicus on 2008-06-26
Coming to you from sunny UBUNTU, Minnesota.  It works guys!!!!  And for a dumb reason I think.  I went back through my commands, and capitalized my network name in properties and it works.  Not really sure why it works, but it does.

Thankyou guys for all of your help, it was very kind of you to help a newbie through some things I totally didn't understand what they even meant.  I learned some stuff today.  So cheers to you!

Sarah

---

### Post by avtolle on 2008-06-26
Great. Would you please mark this thread as "Solved" using the thread tools in the upper left corner, to save others time (both those volunteering and those looking for an answer)? Thank you.

---

