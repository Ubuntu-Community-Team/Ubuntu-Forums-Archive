---
title: "No IM Clients (Pidgin, Kopete) Can Connect - Please Help!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2008-10-31
I recently upgraded to Intrepid, and for some reason none of my IM clients can connect to any networks.  They try for a long time and then say the connections timed out.  Everything else online works perfectly, but not the IM clients.

I've seen many solutions to similar problems, none of which work for me.  I've tried re-installing Pidgin and all of its components, starting my configuration from scratch, changing the permissions on something (I don't know, it was a solution listed somewhere), downloading the smileys package (again, it was a solution posted somewhere), and everything else I could find or think of.  Please help!

---

### Post by lH)4~mK0e on 2008-11-01
I am not sure if you tried this or not.  

Under the Synaptic Package Manager, in System --> Administration, click on Search and change the Look In dropdown menu to Name.  Type in pidgin and click search.  Click on the entry that just says pidgin and choose Mark for Complete Removal.  It will give you the name of another installation dependency (pidgin-otr).  Scroll down and perform these same steps for each installed pidgin application.  Then click Apply.  

Now we need to run something in terminal (under Applications --> Accessories) to make sure your stale configuration settings for pidgin are gone.  This will REMOVE your usernames and passwords:

```

rm -r ~/.purple
```

When it is finished, close synaptic and hold down the Ctrl and Alt key and hit the Backspace.  This should bring you back to your login prompt.  

Log in again and open Synaptic as stated before.  Then perform the search again for pidgin and click on the pidgin entry to choose Install.  Allow it to install what it needs automatically.  Keep in mind, you will probably need to reconfigure your accounts again.  Once you have done this please let us know what happens.  Good luck.

---

### Post by unknownwarrior33 on 2008-11-01
Thanks very, very much; I'll try that in the morning.  

For right now, it seems like it works fine when I'm on a wired connection, but not on wireless.  Given that, if the solution given by miwarlock doesn't work, anyone have any ideas given this new information?  Thanks again.

---

### Post by lH)4~mK0e on 2008-11-01
Well, if it will connect through wired but not wireless, then it is a hardware issue and the previous post will not change that.  We need to know what kind of wireless card you have.  Please run these in the terminal application:

```

lspci | grep Net
iwconfig
iwlist

```

and copy and paste them into the reply.  Then we can help determine the wireless issue.  Again, it is not necessary to go through those steps I outlined previously if you can connect using a cable.  Your wireless card is probably not working correctly.

---

### Post by unknownwarrior33 on 2008-11-01
It's weird, though, because everything else works perfectly on wireless.  Anyway, here's what it gives me:

> 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
jake@jake-laptop:~$ iwconfig                                                    
lo        no wireless extensions.                                               

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"GrinnellCollegeGuest"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:5A:1E:DE:52
          Bit Rate=24 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=90/100  Signal level:-45 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

jake@jake-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation


Thanks again for your help.

---

### Post by lH)4~mK0e on 2008-11-02
On the last command I forgot to add this bit:

```

iwlist wlan0 scan

```

Please try that.  Also it seems you have a Broadcom 43xx based card which works in some cases (for me anyway).  Was it working in Hardy?  Why the switch?  I have seen some cases where that card works beautifully and some cases where it was very flaky.  But I definitely think that since it's working, no modification to Pidgin is necessary.  One thing you might try is moving around (if it's a laptop) to see if it's a reception issue.  Even if you got absolutely perfect reception where you were, driver changes can sometimes affect the card's reception quality.

---

### Post by unknownwarrior33 on 2008-11-02
The new command gives me this:
> wlan0     Scan completed :
          Cell 01 - Address: 00:17:5A:1E:DE:52
                    ESSID:"GrinnellCollegeGuest"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=88/100  Signal level:-46 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Extra:tsf=000004d3fe290132
                    Extra: Last beacon: 32ms ago

My connection is usually wired, so I don't even remember if I ever tried it in Hardy, but I think it worked.  In any case, I'll see if it works elsewhere.

---

