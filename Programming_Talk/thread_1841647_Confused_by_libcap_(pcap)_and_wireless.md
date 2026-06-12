---
title: "Confused by libcap (pcap) and wireless"
date: 2011-09-09
forum: Programming Talk
---

### Post by gnometorule on 2011-09-09
[FONT=Arial][SIZE=2]Background: I'm teaching myself about packet sniffing. I run a  very simple server in one shell, telnet to it from another, then try  different methods to sniff on traffic. When I use raw sockets  (IPPROTO_TCP), I capture what I send fine. I capture merely what I send,  nothing else from the internet. libcap's behavior confuses me as  follows:[/SIZE][/FONT]
  
[FONT=Arial][SIZE=2](1) First, to check it out, I capture all devices with  pcap_findalldevs (see (2) below as well). I find wlan0 fine. If I  connect to 'all traffic' (per the man page) using[/SIZE][/FONT]
  ```

if ( !( pcap_handle = pcap_open_live(NULL, 4096, 1, 0, errbuf) ) )
  
```[FONT=Arial][SIZE=2], I capture what I send (plus more, see (3)). When I try to connect to it using[/SIZE][/FONT]
  ```

if ( !( pcap_handle = pcap_open_live("wlan0", 4096, 1, 0, errbuf) ) )
  
```[FONT=Arial][SIZE=2], which to me seems the proper way of doing this, not 'all', I capture lots of general traffic, but nothing I send. Ideas? [/SIZE][/FONT]
  
[FONT=Arial][SIZE=2](2) I first find all devices using pcap_findalldevs. As the pcap_if_t  structure possibly [/SIZE][/FONT][FONT=Arial][SIZE=2]has several elements, I print all those out, to see  the following:[/SIZE][/FONT]
  ```

Devices found:

1. eth0 - None:
    family: 17, address: 2.0.0.0
2. wlan0 - None:
    family: 17, address: 3.0.0.0
    family: AF_INET, address: 192.168.0.159
    family: 10, address: 0.0.0.0
3. usbmon1 - USB bus number 1:
4. usbmon2 - USB bus number 2:
5. usbmon3 - USB bus number 3:
6. usbmon4 - USB bus number 4:
7. usbmon5 - USB bus number 5:
8. any - Pseudo-device that captures on all interfaces:
9. lo - None:
    family: 17, address: 1.0.0.0
    family: AF_INET, address: 127.0.0.1
    family: 10, address: 0.0.0.0
  
```[FONT=Arial][SIZE=2]I am all new to this. Some devices offer capturing of AF_INET  (=IPv4), IPv6 (10), and packet (17). when I connect to "wlan0", how is  it ensured I connect to the proper of the 'addresses' of some device? Is  that related to the problem?[/SIZE][/FONT]
  
[FONT=Arial][SIZE=2](3) When using raw sockets, I really only capture what I sent to my  server. When I use libcap, I also capture what, from the bytes printed  out, must be internet headers. I am all new to this. If someone could  elaborate what exactly I capture here which i don't capture on raw  sockets, this would be appreciated. Are those UDP or ICMP packets which,  by definition, my IPPROTO_TCP socket would not capture, which would be  why I didn't see those using raw sockets?[/SIZE][/FONT]
  
If you'd like me to post the code, i can do that; but I dont' think it'll help much as the line that drives this is really above. It's not long, but a little lengthy.

[FONT=Arial][SIZE=2]Many thanks.[/SIZE][/FONT]
  
[FONT=Arial][SIZE=2]P.S.: I work under Ubuntu 10.04 on a Toshiba netbook, using gcc/gdb combo.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]P.P.S.: I had this up for a while on stackoverflow, but no one seems to know the answer; so I'm hoping for my good old Ubuntu experts to help me out.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

