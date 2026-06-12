---
title: "Belkin N300 wireless modem router - constantly asking for password but can't connect"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Uncle_John on 2011-12-08
Hey

i am constantly prompted to enter the password but computer just can't connect with the router. I ve got no idea at all what to do, tried to install driver from the disc through wine, i get the error
in the middle of the installation saying: C:\windows\system32\netsh.exe, 
CreateProcess failed; code 2
i'm using Ubuntu 10.04

Can anyone help??

---

### Post by Uncle_John on 2011-12-10
here are the results of sudo iwlist scan:

Cell 02 - Address: 08:86:3B:74:8A:62
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"belkin.7a64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000240a838171
                    Extra: Last beacon: 3076ms ago
                    IE: Unknown: 000B62656C6B696E2E37613634
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010D10
                    IE: Unknown: DD1E00904C336C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3408000400000000000000000000000000000000000000
                    IE: Unknown: DDB70050F204104A0001101044000102103B00010310470010BC329E001DD811B2860108863B748A621021001A42656C6B696E20496E7465726E6174696F6E616C2C20496E632E1023001A5375726620576972656C657373204D6F64656D20526F75746572102400075332414B5433581042000E31323131333948323130303036361054000800060050F20400011011001C42656C6B696E20576972656C65737320526F75746572202857464129100800020084103C000101

and, also results from nm-tool:

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:1E:65:BB:71:DA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


I don't know, maybe the problem is that iwlagen doesn't support CCMP protocol. Any comments are very welcome:)

---

### Post by 3rdalbum on 2011-12-10
Wine won't run the driver even if you get it installed, so don't waste any more of your time trying that method.

The "constantly asks for password" doesn't necessarily mean that you've typed the password wrong; it might be another problem that's causing Network Manager to believe that the authentication failed.

Can you attempt to connect, type your password, and then when you get the second password prompt click Cancel and type this into the terminal:

```
dmesg
```

Copy and paste the last twenty lines into a message here so we can have a look at it. Thanks.

---

### Post by Uncle_John on 2011-12-10
I copied all lines concerning wlan0:

[32817.640553] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32817.641798] r8169: eth0: link down
[32817.641998] ADDRCONF(NETDEV_UP): eth0: link is not ready
[32829.139106] wlan0: deauthenticating from 08:86:3b:74:8a:62 by local choice (reason=3)
[32829.139386] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32829.145539] wlan0: direct probe responded
[32829.145551] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32829.156160] wlan0: authenticated
[32829.156209] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32829.174515] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32829.174525] wlan0: associated
[32829.176191] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32830.176282] UDF-fs: Partition marked readonly; forcing readonly mount
[32830.217798] UDF-fs INFO UDF: Mounting volume 'Belkin Setup CD', timestamp 2011/05/16 17:35 (103c)
[32835.486235] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[32838.859414] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32838.864932] wlan0: direct probe responded
[32838.864943] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32838.875588] wlan0: authenticated
[32838.875650] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32838.902143] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32838.902152] wlan0: associated
[32839.684038] wlan0: no IPv6 routers present
[32845.509866] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[32848.919197] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32848.924661] wlan0: direct probe responded
[32848.924671] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32848.938437] wlan0: authenticated
[32848.938480] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32848.967860] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32848.967869] wlan0: associated
[32855.533796] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[32858.894702] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32859.092049] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 2)
[32859.097784] wlan0: direct probe responded
[32859.097789] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32859.111433] wlan0: authenticated
[32859.111464] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32859.129913] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32859.129918] wlan0: associated
[32865.557748] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[32868.918636] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32868.924123] wlan0: direct probe responded
[32868.924132] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32868.937664] wlan0: authenticated
[32868.937685] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32868.969807] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32868.969814] wlan0: associated
[32875.581622] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[32878.952145] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[32878.957626] wlan0: direct probe responded
[32878.957634] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[32878.971287] wlan0: authenticated
[32878.971341] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[32878.991364] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=2)
[32878.991370] wlan0: associated
[32884.216060] wlan0: deauthenticating from 08:86:3b:74:8a:62 by local choice (reason=3)
[32986.301996] r8169: eth0: link up
[32986.302473] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[32996.353085] eth0: no IPv6 routers present
[40156.225543] r8169: eth0: link down
[40475.321521] r8169: eth0: link up
[40620.390986] wlan0: deauthenticating from 08:86:3b:74:8a:62 by local choice (reason=3)
[40620.430311] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40620.435789] wlan0: direct probe responded
[40620.435798] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40620.446327] wlan0: authenticated
[40620.446374] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40620.464642] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40620.464651] wlan0: associated
[40627.546954] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[40630.915511] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40630.920971] wlan0: direct probe responded
[40630.920980] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40630.931559] wlan0: authenticated
[40630.931608] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40630.951392] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40630.951398] wlan0: associated
[40637.458821] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[40640.931372] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40640.938040] wlan0: direct probe responded
[40640.938050] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40640.948519] wlan0: authenticated
[40640.948541] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40640.966784] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40640.966788] wlan0: associated
[40647.575723] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[40650.969620] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40650.975055] wlan0: direct probe responded
[40650.975059] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40650.985793] wlan0: authenticated
[40650.985816] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40651.006146] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40651.006154] wlan0: associated
[40657.600582] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[40661.032986] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40661.045607] wlan0: direct probe responded
[40661.045613] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40661.059184] wlan0: authenticated
[40661.059210] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40661.077363] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40661.077367] wlan0: associated
[40667.624364] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[40671.000815] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[40671.006382] wlan0: direct probe responded
[40671.006391] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[40671.016900] wlan0: authenticated
[40671.016948] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[40671.035460] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[40671.035468] wlan0: associated
[40677.216112] wlan0: deauthenticating from 08:86:3b:74:8a:62 by local choice (reason=3)

---

### Post by Uncle_John on 2011-12-10
I'm posting another output, thist time without eth0 interuptions.:




[45383.621627] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45383.627235] wlan0: direct probe responded
[45383.627245] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45383.652670] wlan0: authenticated
[45383.652708] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45383.671242] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45383.671250] wlan0: associated
[45383.676105] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[45390.203044] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[45393.583339] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45393.623315] wlan0: direct probe responded
[45393.623322] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45393.645409] wlan0: authenticated
[45393.645455] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45393.678309] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45393.678319] wlan0: associated
[45393.833085] wlan0: no IPv6 routers present
[45400.226771] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[45403.645193] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45403.664890] wlan0: direct probe responded
[45403.664895] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45403.680769] wlan0: authenticated
[45403.680807] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45403.736370] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45403.736380] wlan0: associated
[45410.250632] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[45413.637077] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45413.646529] wlan0: direct probe responded
[45413.646535] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45413.715519] wlan0: authenticated
[45413.715597] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45413.834300] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45413.834310] wlan0: associated
[45420.274533] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[45423.672379] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45423.678332] wlan0: direct probe responded
[45423.678342] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45423.690129] wlan0: authenticated
[45423.690169] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45423.739703] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45423.739712] wlan0: associated
[45430.298398] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)
[45433.735604] wlan0: direct probe to AP 08:86:3b:74:8a:62 (try 1)
[45433.741463] wlan0: direct probe responded
[45433.741473] wlan0: authenticate with AP 08:86:3b:74:8a:62 (try 1)
[45433.772937] wlan0: authenticated
[45433.773023] wlan0: associate with AP 08:86:3b:74:8a:62 (try 1)
[45433.844806] wlan0: RX AssocResp from 08:86:3b:74:8a:62 (capab=0x11 status=0 aid=1)
[45433.844816] wlan0: associated
[45440.322469] wlan0: deauthenticated from 08:86:3b:74:8a:62 (Reason: 15)

---

### Post by gandaran on 2011-12-10
> - Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: iwlagn
State: disconnected
Default: no
what brand is the PC wireless chipset? Intel?
find out and post the output
> lspci
internal devices
```
lsusb
```
usb devices

---

### Post by Mark Phelps on 2011-12-11
From the first log, it looks like you're STILL trying to use the Belkin setup CD.  You can't use that -- it is only for Windows.  And as already mentioned, you can't use Wine to install Windows drivers.

---

