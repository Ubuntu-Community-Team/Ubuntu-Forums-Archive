---
title: "earlier thread about bluetooth keyboard"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by gbswales on 2013-01-05
Since someone took it on themselves to close my thread about issues installing with bluetooth keyboard - I thought I would share what I have found

The keyboard I have is the new Logitech bluetooth illuminated K810 which is a brilliant device as it allows you to toggle between three bluetooth devices (my PC, and my Android phone and tablet) the adjustable illumination comes on as your fingers hover over the keys and it runs for about a month on a charge - as far as I could find no one else produces a keyboard this versatile.

Ufortunately it has been designed for windows, Android and iOS so there are no linux drivers for it.  Just thought I would point this out in case anyone else with this keyboard wanted to install Ubuntu.

Whether drivers will come in time who knows but I hope they do as I would really like to run Ubuntu as a secondary system to Win 8. For now however there doesn't seem to be anything I can do as there is no alternative at the moment to this keyboard which ticks every other box for me

---

### Post by The Spectre on 2013-03-13
I just bought the Logitech Bluetooth K810 Keyboard even though it was uncertain if I would be able to get it to work with Ubuntu 12.10.

I bought it Locally just in case I was unsuccessful so it would be easy to return.  

I was able to get it to work with allot of trial and error but it now works perfectly, in fact I am using it right now.:D
 
I really like this Keyboard, it is solidly built and I was looking for one that had a small footprint to free up some room on my desk but still be functional and comfortable to type on. 

I found a couple websites with info on how to get it to work and listed below are the steps that I followed to get it working.

Hopefully this info will be helpful to anyone else that has bought this Keyboard.


Logitech Bluetooth Illuminated Keyboard K810 Setup:

You may need to Install bluez-hcidump.

1. Turn on the Bluetooth keyboard.

2. Press the Bluetooth connect button.
   • The lights above the Bluetooth keys blink blue.

3. Press a Bluetooth key to assign your first device to that key:
   • The light above the selected key continues to blink blue.
   • The Bluetooth keyboard is discoverable for 15 minutes.

4. In a new terminal type:
```
hcitool scan
```
   and copy the mac address that is found.

5. Now in a second terminal type:
```
sudo hcidump -at
```

   You should get something like (followed by a blinking cursor):
   HCI sniffer - Bluetooth packet analyzer ver 2.4
   device: hci0 snap_len: 1028 filter: 0xffffffffffffffff

6. Switch back to your Original terminal and type:
```
sudo bluez-simple-agent hci0 [COLOR=#ff0000]your mac address[/COLOR]
```

   In the hcidump terminal you will see a few things scroll past that looks like:
   2013-02-07 15:35:40.653393 > HCI Event: User Passkey Notification (0x3b) plen 10
   bdaddr XX:XX:XX:XX:XX:XX passkey 66235

7. Type the 'passkey' that is displayed in terminal in to the K810 Keyboard and press ENTER
   On success you should get "Release" and "New device (/org/bluez/1177/hci0/dev_*"

8. Now in the Original terminal set device as trusted:
```
sudo bluez-test-device trusted [COLOR=#FF0000]y[/COLOR][COLOR=#FF0000]our mac address[/COLOR] yes
```

9. You might have a connection now, but still need to:
```
sudo bluez-test-input connect [COLOR=#FF0000]y[/COLOR][COLOR=#FF0000]our mac address[/COLOR]
```

---

### Post by drw06g0w7-frank on 2013-10-23
Sadly this is still needed in 13.04. I have never been able to get the Bluetooth gui tool to work for the Logitech.

Step 5 might be better written as:

sudo hcidump -at  sudo hcidump -at | grep -i passkey

Otherwise the line containing "passkey" will likely scroll off of the screen.

I have also noticed that I periodically lose the connection and have to manually delete the keyboard (I use the gui tool for this) and then recreate it using the steps here.

---

### Post by rykel98 on 2013-11-01
Hi, I am finally able to use the best Bluetooth keyboard in the world with Ubuntu!

However, it still behooves the question... is this a Ubuntu or Logitech problem?

---

### Post by g-vincentip on 2013-12-23
Hey all,

I seem to get a different output when I do step 6:
```
sudo bluez-simple-agent hci0 68:A8:6D:10:3B:1BRequestConfirmation (/org/bluez/490/hci0/dev_68_A8_6D_10_3B_1B, 063035)
Confirm passkey (yes/no):
```

whether I say yes or no, both give me:
```
CancelRelease
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout

```

Anyone an idea what I am doing wrong?

_**edit:**_ I got it working on 13.10 using: [http://blog.chschmid.com/?p=1537](http://blog.chschmid.com/?p=1537)

---

