---
title: "HOWTO: Zyair B-101 PCMCIA WIRELESS"
date: 2005-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by metafor on 2005-11-03
This HOWTO is about setting up the Zyair B-101 wireless-card in Ubuntu Breezy Badger, it could work also on Hoary, but i have not tested this. I had some hassle with this card on Debian and finally came out with a solution, unfortunately in Breezy you have to do a bit more work.

The Card uses the prism chipset and can be configured with orinoco_cs driver. 

1. Check if pcmcia is working on your laptop. you can use cardinfo to do so. first open a terminal. *Applications ->System Tools -> Terminal*
**[INDENT]metafor@ubuntu:~$  cardinfo[/INDENT]**
now you see all your pcmcia slots, if the Zyair is inside, it will say usupported card. thats ok. if cardinfo is not working you have to install pcmcia properly, which is not covered in this howto.

2. now you have to find out the proper manufacturer info, to bind it to the driver in Breezy.
**[INDENT]metafor@ubuntu:~$ cardctl ident[/INDENT]**
you should see something similar to this:
[INDENT]Socket 0:
  product info: " ", "IEEE 802.11 Wireless LAN/PC Card", "", ""
  manfid: 0xd601, 0x0010
  function: 6 (network)[/INDENT]

3. Now we have to add this information to the pcmcia-config file. use your prefered editor to do so. (you have to be superuser!) This step tells the pcmcia manager to bind the orinoco_cs driver to your pcmcia-wireless-card.
**[INDENT]metafor@ubuntu:~$ sudo vim /etc/pcmcia/config[/INDENT]**

Add an entry similar to this one:
[INDENT]card "IEEE 802.11 Wireless LAN/PC Card"
  manfid 0xd601, 0x0010
  bind "orinoco_cs"[/INDENT]

It is important that the manfid is the same as cartctl showed you, best is to just copy paste. 

4. Now we have to edit the same file again, as this card also uses the hermes driver. don't ask me why, but i just figured out that without this step there will be no success. on Debian this was not necessarly (2.4.27).

Find this part in the file (etc/pcmcia/config)
[INDENT]device "orinoco_cs"
  #class "network" module "hermes", "orinoco", "orinoco_cs"
  class "network" module "orinoco_cs"[/INDENT]

and uncomment the first line and comment out the second one, the part should look no like this. save the file and exit.
[INDENT]device "orinoco_cs"
  class "network" module "hermes", "orinoco", "orinoco_cs"
  #class "network" module "orinoco_cs"[/INDENT]

5. This was it. now you have to restart pcmcia-service as superuser, to activate the changes.
**[INDENT]metafor@ubuntu:/$ sudo /etc/init.d/pcmcia restart[/INDENT]**

6. Now your card should be regocnized by the system, check it with iwconfig.
**[INDENT]metafor@ubuntu:/$ iwconfig[/INDENT]**

you should see  something similar:
[INDENT]eth1      IEEE 802.11-DS  ESSID:"YOURNETWORK"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:C0:49:E8:59:26
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/92  Signal level=-16 dBm  Noise level=-139 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:414  Invalid misc:0   Missed beacon:0[/INDENT]

If you see it you should be happy as your card is running. otherwise reboot to really restart the pcmcia-manager and eject reinsert the card to load the driver. 

7. Now you can configure your card with dhcp or static ip. You can do this by hand and edit the file /etc/network/interfaces, or using gnome-network assistant. *System -> Administration -> Networking*

Most important is to enter the proper ESSID and a key if your network is secured. 

Hope you will enjoy networking with Breezy.

---

