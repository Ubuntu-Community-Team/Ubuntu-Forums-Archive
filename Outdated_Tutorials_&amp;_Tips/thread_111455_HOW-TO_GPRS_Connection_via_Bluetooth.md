---
title: "HOW-TO: GPRS Connection via Bluetooth"
date: 2006-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by emperon on 2006-01-02
Hello, i have just succeeded to connect gprs via bluetooth. Currently i am writing from there.

I have read wirless hacks of oreilly and 
found the solution

1-) Make sure that you have the appropriate hardware ready. (I tried same phone and notebook in windows it was working.)

2-) Makesure that bluez-utils is installed via package manager

3-)open a console and type   **hcitool scan** this should give you the  BD address of your phone, take a note of this number

4-)type ** sdptool search DUN ** from the out put take a note of channel number

5-)make sure that you have written your pin number in /etc/bluetooth/pin (any 4 digit number is ok , you will use the same number through the phone)

6-) type ** rfcomm bind /dev/rfcomm0 X:X:X:X:X:X *channel_number_noted* **  using the channel number noted earlier as X denotes BD address.

7-) test it by typing ** rfcomm **  you should see the channel is clear or closed, both are ok e.g.   rfcomm0: X:X:X:X:X:X channel 1 clean

8 -) create the following file as  root : /etc/ppp/peers/gprs

9-) Put the following inside:
```

 
/dev/rfcomm0
connect '/usr/sbin/chat -v -f /etc/ppp/peers/gprs.chat' 
        noauth 
        defaultroute 
        usepeerdns 
        lcp-echo-interval 65535 
        debug 

```

10-) Create the following file as root: /etc/ppp/peers/gprs.chat' and put the following
```

TIMEOUT                 15         
ECHO                    ON 
HANGUP                  ON       
''                              AT 
OK                              ATZ      
OK                              ATD*99*# 

```
Here you may need to change *99*#, it should be the number you dial. In Turkey it is that, in some countries it is *99# or *99***1#, consult your GSM provider.

11-) Go to your phone and initiate pairing by using the same pin and confirm all things from phone

12-) type ** sudo pppd nomagic call gprs ** and confirm the connection with your phone

That's it, your gprs connections should be working now, enjoy surfing

---

### Post by keikoh on 2006-01-17
I've followed the steps and it seems to work fine until I tried to dial using "sudo pppd nomagic call gprs". The phone ask to accept the connection but does not initiate GPRS. 

RFCOMM0 channel 1 is clean (assume this means its working)
The phone and notebook is ok (verified to on Win XP).
Bluetooth seems ok (can transfer files in/out)

I'm a newbie in linux. What could be wrong?

---

### Post by emperon on 2006-01-19
[QUOTE=keikoh]I've followed the steps and it seems to work fine until I tried to dial using "sudo pppd nomagic call gprs". The phone ask to accept the connection but does not initiate GPRS. 

RFCOMM0 channel 1 is clean (assume this means its working)
The phone and notebook is ok (verified to on Win XP).
Bluetooth seems ok (can transfer files in/out)

I'm a newbie in linux. What could be wrong?[/QUOTE]

Hello, I also have encountered similar problems. You may try "sudo pppd call gprs" instead of last step. In my computer  samething happen when i don't use nomagic option. I thought it fixes an echo bug in pppd.

Now to get further information you have to carefully analyze /var/log/messages and /var/log/syslog and figure out why pppd terminates. Post the log files here and i will also try to  understand.

But shortly, usually problem is because of pppd (as if it is normal dial-up) not because of gprs or bluetooth.

Also make sure that the number (e.g. *99*# ) you dialed matches to your GSM provider's

Additionally always remove the pairing  that remains from windows and make a fresh pairing process and if your bluetooth device has a button a physical restart may fix your problem.

---

### Post by keikoh on 2006-01-19
Hi, Thank you for your response. I think its pppd also. New pairing is always done everytime before I try this. Pls note below, From console, taidaniel@TaiDaniel:~$ rfcomm rfcomm0: 00:E0:03:42:DB:1D channel 1 clean taidaniel@TaiDaniel:~$ sudo pppd call gprs taidaniel@TaiDaniel:~$

Syslog
Jan 19 20:22:59 localhost kernel: [4298533.155000] PPP generic driver version 2.4.2
Jan 19 20:22:59 localhost pppd[21235]: pppd 2.4.3 started by root, uid 0
Jan 19 20:23:03 localhost hcid[8252]: link_key_request (sba=00:10:C6:77:C2:9F, dba=00:E0:03:42:DB:1D)
Jan 19 20:23:03 localhost pppd[21235]: Failed to open /dev/rfcomm0: Connection refused
Jan 19 20:23:03 localhost pppd[21235]: Exit.
Jan 19 20:29:29 localhost kernel: [4298922.870000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:29:29 localhost kernel: [4298922.870000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:36 localhost dhclient: DHCPREQUEST on eth1 to 192.168.1.1 port 67
Jan 19 20:32:36 localhost dhclient: DHCPACK from 192.168.1.1
Jan 19 20:32:36 localhost dhclient: bound to 192.168.1.22 -- renewal in 1466 seconds.
Jan 19 20:32:55 localhost kernel: [4299129.154000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:55 localhost kernel: [4299129.154000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:57 localhost kernel: [4299130.906000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:57 localhost kernel: [4299130.906000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:57 localhost kernel: [4299131.172000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:57 localhost kernel: [4299131.172000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:58 localhost kernel: [4299132.105000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:58 localhost kernel: [4299132.105000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:00 localhost kernel: [4299134.115000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:00 localhost kernel: [4299134.115000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:00 localhost kernel: [4299134.653000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:00 localhost kernel: [4299134.653000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:05 localhost kernel: [4299139.725000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:05 localhost kernel: [4299139.725000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299140.787000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299140.787000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299141.181000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299141.181000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299141.414000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299141.414000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:08 localhost kernel: [4299142.033000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:08 localhost kernel: [4299142.033000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:08 localhost kernel: [4299142.226000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:08 localhost kernel: [4299142.226000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:09 localhost kernel: [4299142.965000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:09 localhost kernel: [4299142.965000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:11 localhost kernel: [4299145.004000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:11 localhost kernel: [4299145.004000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:13 localhost kernel: [4299147.621000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:13 localhost kernel: [4299147.621000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:14 localhost kernel: [4299148.369000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:14 localhost kernel: [4299148.369000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:15 localhost kernel: [4299149.314000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:15 localhost kernel: [4299149.314000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:23 localhost kernel: [4299157.225000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:23 localhost kernel: [4299157.225000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:23 localhost kernel: [4299157.586000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:23 localhost kernel: [4299157.586000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:24 localhost kernel: [4299157.875000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:24 localhost kernel: [4299157.875000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:25 localhost kernel: [4299158.832000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:25 localhost kernel: [4299158.832000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:25 localhost kernel: [4299159.339000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:25 localhost kernel: [4299159.339000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299159.813000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299159.813000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299160.232000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299160.232000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299160.682000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299160.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299160.923000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299160.923000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.164000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.164000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.357000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.357000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.558000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.558000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:28 localhost kernel: [4299161.968000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:28 localhost kernel: [4299161.968000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:29 localhost kernel: [4299162.868000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:29 localhost kernel: [4299162.868000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:30 localhost kernel: [4299164.605000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:30 localhost kernel: [4299164.605000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:31 localhost kernel: [4299165.144000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:31 localhost kernel: [4299165.144000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:33 localhost kernel: [4299167.174000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:33 localhost kernel: [4299167.174000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.151000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.151000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.384000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.384000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.561000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.561000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.762000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.762000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:14 localhost kernel: [4299327.940000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:14 localhost kernel: [4299327.940000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:14 localhost kernel: [4299328.116000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:14 localhost kernel: [4299328.116000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299328.945000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299328.945000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.137000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.137000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.330000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.330000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.507000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.507000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.716000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.716000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:16 localhost kernel: [4299330.175000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:16 localhost kernel: [4299330.175000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:16 localhost kernel: [4299330.367000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:16 localhost kernel: [4299330.367000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:17 localhost kernel: [4299331.505000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:17 localhost kernel: [4299331.505000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:17 localhost kernel: [4299331.762000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:17 localhost kernel: [4299331.762000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

messages
Jan 19 20:22:03 localhost kernel: [4298477.484000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Jan 19 20:22:03 localhost kernel: [4298477.484000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Jan 19 20:22:03 localhost kernel: [4298477.589000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Jan 19 20:22:03 localhost kernel: [4298477.589000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Jan 19 20:22:04 localhost kernel: [4298478.186000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Jan 19 20:22:04 localhost kernel: [4298478.572000] Bluetooth: HCI USB driver ver 2.8
Jan 19 20:22:04 localhost usb.agent[20898]:      hci_usb: already loaded
Jan 19 20:22:05 localhost usb.agent[20914]:      hci_usb: already loaded
Jan 19 20:22:05 localhost kernel: [4298478.670000] usbcore: registered new driver hci_usb
Jan 19 20:22:05 localhost usb.agent[20908]:      hci_usb: loaded successfully
Jan 19 20:22:05 localhost usb.agent[20876]:      hci_usb: already loaded
Jan 19 20:22:59 localhost kernel: [4298533.152000] CSLIP: code copyright 1989 Regents of the University of California
Jan 19 20:22:59 localhost kernel: [4298533.155000] PPP generic driver version 2.4.2
Jan 19 20:22:59 localhost pppd[21235]: pppd 2.4.3 started by root, uid 0
Jan 19 20:23:03 localhost pppd[21235]: Exit.
Jan 19 20:29:29 localhost kernel: [4298922.870000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:29:29 localhost kernel: [4298922.870000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:55 localhost kernel: [4299129.154000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:55 localhost kernel: [4299129.154000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:57 localhost kernel: [4299130.906000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:57 localhost kernel: [4299130.906000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:57 localhost kernel: [4299131.172000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:57 localhost kernel: [4299131.172000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:32:58 localhost kernel: [4299132.105000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:32:58 localhost kernel: [4299132.105000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:00 localhost kernel: [4299134.115000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:00 localhost kernel: [4299134.115000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:00 localhost kernel: [4299134.653000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:00 localhost kernel: [4299134.653000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:05 localhost kernel: [4299139.725000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:05 localhost kernel: [4299139.725000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299140.787000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299140.787000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299141.181000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299141.181000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:07 localhost kernel: [4299141.414000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:07 localhost kernel: [4299141.414000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:08 localhost kernel: [4299142.033000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:08 localhost kernel: [4299142.033000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:08 localhost kernel: [4299142.226000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:08 localhost kernel: [4299142.226000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:09 localhost kernel: [4299142.965000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:09 localhost kernel: [4299142.965000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:11 localhost kernel: [4299145.004000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:11 localhost kernel: [4299145.004000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:13 localhost kernel: [4299147.621000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:13 localhost kernel: [4299147.621000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:14 localhost kernel: [4299148.369000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:14 localhost kernel: [4299148.369000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:15 localhost kernel: [4299149.314000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:15 localhost kernel: [4299149.314000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:23 localhost kernel: [4299157.225000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:23 localhost kernel: [4299157.225000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:23 localhost kernel: [4299157.586000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:23 localhost kernel: [4299157.586000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:24 localhost kernel: [4299157.875000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:24 localhost kernel: [4299157.875000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:25 localhost kernel: [4299158.832000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:25 localhost kernel: [4299158.832000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:25 localhost kernel: [4299159.339000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:25 localhost kernel: [4299159.339000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299159.813000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299159.813000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299160.232000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299160.232000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:26 localhost kernel: [4299160.682000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:26 localhost kernel: [4299160.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299160.923000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299160.923000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.164000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.164000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.357000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.357000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:27 localhost kernel: [4299161.558000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:27 localhost kernel: [4299161.558000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:28 localhost kernel: [4299161.968000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:28 localhost kernel: [4299161.968000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:29 localhost kernel: [4299162.868000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:29 localhost kernel: [4299162.868000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:30 localhost kernel: [4299164.605000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:30 localhost kernel: [4299164.605000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:31 localhost kernel: [4299165.144000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:31 localhost kernel: [4299165.144000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:33:33 localhost kernel: [4299167.174000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:33:33 localhost kernel: [4299167.174000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.151000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.151000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.384000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.384000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.561000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.561000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:13 localhost kernel: [4299327.762000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:13 localhost kernel: [4299327.762000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:14 localhost kernel: [4299327.940000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:14 localhost kernel: [4299327.940000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:14 localhost kernel: [4299328.116000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:14 localhost kernel: [4299328.116000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299328.945000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299328.945000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.137000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.137000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.330000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.330000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.507000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.507000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:15 localhost kernel: [4299329.716000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:15 localhost kernel: [4299329.716000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:16 localhost kernel: [4299330.175000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:16 localhost kernel: [4299330.175000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:16 localhost kernel: [4299330.367000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:16 localhost kernel: [4299330.367000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:17 localhost kernel: [4299331.505000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:17 localhost kernel: [4299331.505000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan 19 20:36:17 localhost kernel: [4299331.762000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan 19 20:36:17 localhost kernel: [4299331.762000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

---

### Post by emperon on 2006-01-20
Clearly there's very little info in your log files. But know i also consider it as a bluetooth problem rather than a pppd. If it was because of pppd then you should have seen some more detailed messages. 

At this point it even doesn't run your chat scripts and terminates. The connection is refused to device. I have got exactly the same error, and searching down it through google and this forum gave me nothing. Finally i realized that it was either because of my previous pairing remains or I have to restart the bluetooth physically. In my laptop I have a bluetooth button (hp nx7010). And after I log in, I turn it of and turn it on (and remove the previous pairing from the phone and research and pair it again). Remember you should initiate pairing from the phone. Otherwise you have to use a pinhelper progam (which is designated in /etc/bluetooth/hcid.conf) and it even doesn't work at all. When I have time I will post my own configuration files and my logs so that you can compare.

To sum up, I say concentrate on bluetooth, as told, your scripts even doesn't start.

I hope it helps

---

### Post by juriise on 2006-02-14
I had the same symptom as keikoh, and in my case I had forgot to connect from the  phone to the pc (your point 11 above).

Also, I changed the pincode in /etc/bluetooth/pin, after that something had to be restarted, don't know what.

I also think there should be a CONNECT statement at the botom of the chat script, else the ppp connection will disconnect immediately (indicated on phone), and the ppp daemon will endlessly repeat the first lcp-message.

---

### Post by keikoh on 2006-03-06
Finally got it! I figured I did everything right as suggested so it must be the earlier things I did that was screwing bluetooth. I removed /var/lib/bluetooth/xxx and paired again with the phone.
Rebooted, Dial with KPPP, VOILA! I'm typing this message 8D

---

### Post by Chris Tucker on 2006-03-06
oh yay, now i want a bluetooth cellphone :/

---

### Post by warpforge on 2006-04-08
I've posted a more complete guide to the wiki:
[https://wiki.ubuntu.com/BluetoothDialup](https://wiki.ubuntu.com/BluetoothDialup)

---

### Post by mhafren on 2006-07-11
Could anybody tell me how to disconnect after you have your computer connected to the internet via your phone with bluetooth?

---

### Post by mjrmua on 2007-01-11
Has anyone tried this recently?
I have problems with 
" sudo pppd nomagic call gprs"
The phone asks for a passkey after which the connection dies, 

According to syslog:

 pppd[5175]: pppd 2.4.4 started by root, uid 0
 hcid[4956]: pin_code_request (sba=00:08:1B:84:C3:1F, dba=00:15:A0:43:2C:F7)
 hcid[4956]: call_passkey_agent(): no agent registered
 pppd[5175]: Failed to open /dev/rfcomm0: Connection refused
 pppd[5175]: Exit.

Has anyone else had this problem?
Does anyone know what a passkey agent is?

---

### Post by mjrmua on 2007-01-11
Phew, Solved!
Seems to be this bug:
[http://lists.alioth.debian.org/pipermail/pkg-bluetooth-maintainers/2006-July/000388.html](http://lists.alioth.debian.org/pipermail/pkg-bluetooth-maintainers/2006-July/000388.html)
 running
sudo passkey-agent --default /usr/bin/bluez-pin &
Before connecting sorts out all my problems.

---

### Post by pangos on 2007-04-30
does kppp have a place to put in the GPRS APN? My provider requires it for it to work.

---

### Post by vonjoost on 2007-05-29
Hello... need some help... just can't figure this out!

I have the bluetooth connection all set up.  I've made it as far as my laptop prompting my phone to ask whether or not to allow dial up networking, to which i respond "Yes".

however, the connection still fails.

the log basically says this (i'd copy it but i'm typing from a different computer):

> pppd 2.4.4 started by justin, uid 1000
link_key_request (sba=mac#, dba=phones mac#)
Connect script failed
Exit.

So... if anyone has any ideas why this may be happening, I would appriciate it.  Thanks.

---

### Post by emperon on 2007-06-04
Hi I've started this thread but it was a long time ago. Regarding your error (which is insufficient) your bluetooth works but there is a problem with your pppd script. Read the beggining of this thread and dig the log files accordingly

---

### Post by BatPenguin on 2007-08-12
Great guide, thanks. I have a question, though:

I've set this up on two computers, a laptop and a desktop. On the laptop, I can get it working nicely by using network manager to disable wireless - the gprs connection works fine then. On the desktop, however, I'm having problems: it's normally connected through ethernet, and I'd only like to use the bluetooth/gprs on rare occasions to check mail etc. when my cable modem goes down (it's been having some problems...). But with the desktop, it seems like it's still trying to use the ethernet connection even when it's down and the GPRS has been setup.  Everything seems to work fine, phone connects, I see GPRS connecting and even route -n tells me that there's an IP and all for the ppp connection. But still, can't use it - I believe it's because of the wired network still being "there".

So could somebody please help me figure out what I should do to make sure my computer is not trying to use the ethernet anymore to connect but would instead just use the GPRS? I installed network manager and tried to use that to disable the wired network, but that didn't work either. 

I'd appreciate any tips! Thanks.

---

### Post by gonsolo on 2008-03-19
Not exactly bluetooth but anyway:

I connected my old Samsung SGH-E300 via USB cable to my Dell Inspiron.
I tried wvdial, pon, gnome-ppp, etc..
Nothing worked out of the box.
Then I tried gprsec: [http://darrenalbers.com/gprsec/](http://darrenalbers.com/gprsec/)
Worked out of the box.

---

### Post by JohnDMJ on 2008-06-15
I'm trying to do this on a fresh installation of 8.04.

I get as far as stage 6 but get an error when issuing the rfcomm bind: Can't create device: Operation not permitted.

How should I proceed from here please? I've tried sudo and su but they just yield authorisation errors.

Later addition - problem sorted out; computer domain was incorrect!

---

### Post by Rayaz on 2008-09-15
gprsec rocks     :guitar:

---

### Post by mohitsoni on 2009-02-10
Check out [CodeBasket]("http://codebasket.blogspot.com/2008/12/connecting-to-internet-on-ubuntu-linux.html") for a detailed guide. :KS

---

