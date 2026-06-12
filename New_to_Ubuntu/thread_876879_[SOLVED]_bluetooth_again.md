---
title: "[SOLVED] bluetooth again"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by im new here on 2008-08-01
[http://ubuntuforums.org/showthread.php?t=874150](http://ubuntuforums.org/showthread.php?t=874150)

i made this thread 2 days ago and no replies tell now somebody please look at it i really need bluetooth to work

---

### Post by kpkeerthi on 2008-08-01
Install bluetooth support. Open a terminal window and type

```
sudo aptitude update && sudo aptitude install bluetooth gnome-bluetooth bluez-gnome
```

Reboot.

Turn-on bluetooth in your mobile and make sure it is 'discoverable'.

You should now see a bluetooth icon in your system tray. Right-click and choose Browse. It should find your mobile. Everything from here is pretty intuitive.

*Note: Enable universe and multiverse repository from System -> Admin -> Software Sources

---

### Post by kpkeerthi on 2008-08-01
You may also try [blueman]("http://blueman.tuxfamily.org/"). Installation instructions for *buntu is available [here]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56")

---

### Post by im new here on 2008-08-01
i allready downloaded blue man but o dont know how to install it

---

### Post by kpkeerthi on 2008-08-01
> **im new here said:**
> i allready downloaded blue man but o dont know how to install it

Read the installation instructions at the link I posted earlier.

---

### Post by im new here on 2008-08-01
it didnt work im using xubuntu ok

---

### Post by im new here on 2008-08-01
i guess nobody knows how to make a bluetooth stick work on xubuntu

---

### Post by c2olen on 2008-08-01
Wow, such a conclusion after having posted your question only 2 hours ago.

I don't know about you, but i don't think everybody is sitting behind their workstation/laptop or whatever waiting for your questions to be answered your questions at lightspeed...
Everybody here likes to help, but you should have at least a bit more patience before jumping to a conclusion like this.

Does your box actually show the bluetooth device if it is plugged in?
How about showing us some output, like `lsusb` or `lshw`. This will help us greatly in helping you.

---

### Post by im new here on 2008-08-01
hhhhhhh c2olen there was 2 other posts beside the one i put its link here anyway i didnt mean what u understood i just wanted to make the thread more active
here is the output 
Bus 001 Device 003: ID 15d9:0a33  
Bus 001 Device 002: ID 1caa:0001  
Bus 001 Device 001: ID 0000:0000

---

### Post by im new here on 2008-08-01
one device is the usb bluetooth and the other is the usb mouse

---

### Post by c2olen on 2008-08-01
Does your box actually know or see the dongle?
Try this command and let us know if the device is recognized?

```

c2olen@okinawa:~$ hcitool dev
Devices:
    hci0    00:10:60:D0:06:F6

```

---

### Post by im new here on 2008-08-01
Devices:
        hci0    AA:BB:CC:56:34:12

this is the output only

---

### Post by c2olen on 2008-08-01
Have you checked /etc/defaults/bluetooth for : BLUETOOTH_ENABLED=1

to see if bluetooth is enabled at boot time?

Can you see your phone (assuming it has its bluetooth service detectable) when you do
```
hcitool scan
```

---

### Post by gn2 on 2008-08-01
> **im new here said:**
> i guess nobody knows how to make a bluetooth stick work on xubuntu

[**Try this**]("http://ubuntuforums.org/showthread.php?t=669171")

---

### Post by im new here on 2008-08-02
1- BLUETOOTH_ENABLED=1 yea thats ok 
2-Scanning ...
        00:60:57:B1:55:6D       (my bluetooth name for mobile)

---

### Post by im new here on 2008-08-03
c2olen heeeeeeeeeeey where r u

---

### Post by c2olen on 2008-08-04
I am back...
I am not online all-weekend, i have a family you know :-)

---

### Post by im new here on 2008-08-04
ok now what ? ?

---

### Post by c2olen on 2008-08-04
It seems like your hardware and bluetooth drivers work, since you can communicate (scan).

Install bluemon if you haven't already. It should be in your repositories by default.

Start the bluemon gui from System -> Preferences (gnome) or your Xfce session somewhere. (or do bluemon in a terminal).

You should see your phone by now in the bottom of the panel.

You should be able to right-click your file of choise and select "Sent to..." and select the "Obex Push" protocol. Below the protocol box, should be a list of bluetooth devices discovered, including your phone. See the screenshots.

You probablu have to exchange some PIN code settings. You can handle this later when you have it all running.

Give it a try.

---

### Post by im new here on 2008-08-04
The program 'bluemon' is currently not installed.  You can install it by typing:
sudo apt-get install bluemon
bash: bluemon: command not found

so i installed bluemon by sudo apt-get install bluemon 
 i opened my phone bluetooth and nothing happened

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> 
so i installed bluemon by sudo apt-get install bluemon 
 i opened my phone bluetooth and nothing happened

What do you mean by this exactly?
At this point you cannot yet start sending from you phone. You should now first test the connection from you computer to your phone, by selecting some file (small one preferably) and select "send to...".

If this works, you can configure your computers bluetooth for recieving also.
I'll screenprint my bluemon settings for you, so you can see what I've configured.
You can of course configure all the services you like.

You can also configure these settings from the corresponding files in /etc/bluetooth.

---

### Post by im new here on 2008-08-04
i dont have this send to option

---

### Post by im new here on 2008-08-04
i have it but not on my desktop i have it inside file seystem and i didnt have bluetooth inside the send to but i made it now when i select it it dosnt locate any devices

---

### Post by c2olen on 2008-08-04
Can you do a 
```
dpkg -l | grep -i blue
```
and post me the output?

I'd like to verify the packages that are installed.

Cheers

---

### Post by im new here on 2008-08-04
ii  bluemon                                    1.4-3                                              Activate or deactivate programs based on Bluetooth link quality

ii  bluetooth                                  3.26-0ubuntu6                                      Bluetooth stack utilities
ii  bluez-audio                                3.26-0ubuntu6                                      Bluetooth audio support
ii  bluez-cups                                 3.26-0ubuntu6                                      Bluetooth printer driver for CUPS
ii  bluez-gnome                                0.25-0ubuntu1                                      Bluetooth utilities for GNOME
ii  bluez-utils                                3.26-0ubuntu6                                      Bluetooth tools and daemons
ii  gnome-bluetooth                            0.11.0-0ubuntu1                                    GNOME Bluetooth tools.
ii  kdebluetooth                               1.0~beta9~r769275-0ubuntu1                         KDE Bluetooth Framework
ii  libbluetooth2                              3.29-0ubuntu1                                      Library to use the BlueZ Linux Bluetooth stack
ii  libbtctl4                                  0.9.0-2                                            GObject Bluetooth library
ii  libgnomebt0                                0.11.0-0ubuntu1                                    GNOME Bluetooth library
ii  libkbluetooth0                             1.0~beta9~r769275-0ubuntu1                         shared libs for kdebluetooth

---

### Post by gn2 on 2008-08-04
> **im new here said:**
> i dont have this send to option

You don't have the bluetooth send-to listed because you are using Xubuntu.

You have to create your own send-to bluetooth entry, how to do it is explained in my previous link.

---

### Post by im new here on 2008-08-04
i allready made that list as i said in the last post

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> c2olen heeeeeeeeeeey where r u

> **im new here said:**
> i have it but not on my desktop i have it inside file seystem and i didnt have bluetooth inside the send to but i made it now when i select it it dosnt locate any devices

Yes, That's what i meant, it should be in your filebrowser's  context menus.
Ok, then it seems like we first need to make a pair between you computer and mobile.

Your package list seems to match mine, so I assume everything you need is installed.
Have you tried blueman, like I suggested a couple of posts earlier.
This tool has far more features that include scanning and bonding.

---

### Post by im new here on 2008-08-04
as i answered u before i have blueman but i dont know how to install it

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> as i answered u before i have blueman but i dont know how to install it

No no, I mean blueman, not bluemon.

Just go "apt-get install blueman"

Then lauch it using "blueman" in the terminal or "Applications -> Accessories -> Blueman Bluetooth Manager".

The GUI is very intuitive.

---

### Post by im new here on 2008-08-04
i knnnnnnnnnowwwwwwwwwwww i have it bluemAn but cant install

---

### Post by im new here on 2008-08-04
Applications -> Accessories -> Blueman Bluetooth Manager".
 no such thing i have 

Applications -> Accessories -> Bluetooth file sharing

which only opens an icon in the tray

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> i knnnnnnnnnowwwwwwwwwwww i have it bluemAn but cant install


Ah. Oops. Now I get it. It isn't in the default repositories. Sorry about that :-#
Follow [this ]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56")link and the instructions in there, to get BlueMAN installed.

---

### Post by im new here on 2008-08-04
hhhhhhhhhhhhhhhhh i already said before that this method didnt work with xubuntu

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> hhhhhhhhhhhhhhhhh i already said before that this method didnt work with xubuntu

[This guy got it to work on Xubuntu]("http://ph.ubuntuforums.com/showpost.php?p=5034268&postcount=27"). Maybe you can ask him for some assistense.

---

### Post by im new here on 2008-08-04
is it such a big problem to make bluetooth work im really bored

---

### Post by im new here on 2008-08-04
this guy wanted to connect a headset not a mobile

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> this guy wanted to connect a headset not a mobile
I know, but het got BlueMAN on Xubuntu to run, that's what I tried to tell you.

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> is it such a big problem to make bluetooth work im really bored


Your bluetooth is working but you cant see your cellphone. 
I am not sure what it really is you tried, and what not, because your responses are very minimal. We can't possibly know what it is your are trying, because we get no logging, screenshots or other important information from you.
You can do some more connection attempts from the commandline using hcitool, to see if you can communicate with your phone. 

Just see 'man hcitool' or [google ]("http://www.google.nl/search?q=hcitool&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:nl:official&client=firefox-a")for more information on this.

---

### Post by im new here on 2008-08-04
ok solved download blueman and and folow the instructions at the download page

---

### Post by im new here on 2008-08-04
thanks alot c2olen nice to meet u

---

### Post by c2olen on 2008-08-04
> **im new here said:**
> thanks alot c2olen nice to meet u

Your welcome, glad i could help.

---

