---
title: "Slow Internet!! :("
date: 2012-08-11
forum: New to Ubuntu
---

### Post by hkmy on 2012-08-11
Hi there, 
I really need help because I am confused. Ever since I downloaded Ubuntu 11.10 on to my HP Mini 110 netbook the internet speed has been starting to run slow. Anybody who can help/try helping me, I want to say thanks for your time ahead.
 
[[IMG]http://www.speedtest.net/result/2114841053.png[/IMG]](http://www.speedtest.net)

Here are some basic information from my terminal:


wan@Wan-Inspiron-910:~$ iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:199
          Rx invalid nwid:0  invalid crypt:1583  invalid misc:0

wan@Wan-Inspiron-910:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1507]
	Kernel driver in use: wl
--
02:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Kernel driver in use: atl1c
wan@Wan-Inspiron-910:~$ lsmod
Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17240  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2646601  0 
i915                  513798  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19069  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36690  0

---

### Post by bjorn.aigen on 2012-09-30
Hello hkmy.   I also had a slow ethernet connection on Ubuntu 10.10 and fixed it using the following methods that I found on the internet.

[SIZE=3]1. Disable IPv6 via Firefox setting or kernel parameter[/SIZE]
a. Turn it off temporarily in Firefox by navigating to "about:config".
Create a boolean setting "network.dns.disableIPv6" with value "true".

See Mozilla's instructions
[http://support.mozilla.org/en-US/kb/firefox-cant-load-websites-other-browsers-can#w_ipv6](http://support.mozilla.org/en-US/kb/firefox-cant-load-websites-other-browsers-can#w_ipv6)

b. Disable IPv6 permanently using a boot time parameter passed via 'grub', the boot loader, to the kernel.
Edit the GRUB2 user settings file **/etc/default/grub**
Add the "ipv6.disable" parameter as follows:
[FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"[/FONT]

See this thread for an explanation of the solution
[https://answers.launchpad.net/ubuntu/+question/89485](https://answers.launchpad.net/ubuntu/+question/89485)

See this explanation of the problem
[http://sirupsen.com/slow-internet-under-ubuntu-or-linux/](http://sirupsen.com/slow-internet-under-ubuntu-or-linux/)


[SIZE=3]2. Specify DNS nameservers in Ubuntu[/SIZE]
Even though your router may be set up to contain the DNS servers, you should set it up on your Ubuntu host.  There are several ways to do this.  Note that I've listed example IP addresses of Bigpond's DNS servers 61.9.211.33 and 61.9.211.1 in Queenland, Australia.

Option a. The simplest and probably best way is to add the server IP addresses in the Network Manager GUI.
R-click on the 'Network Connections' icon and select 'Edit connections...'.
Select the 'auto eth0' connection and click 'Edit'.
Select the 'IPv4' tab.
Select 'Automatic (DHCP) addresses only'.
Type in the DNS nameservers IP addresses separated by a comma.
Click on the 'Network Connections' icon to update.

See this thread on how to edit 'Network Manager'
[URL="http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip"]http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip
[/URL]

Option b. Edit the **/etc/network/interfaces** file.
It should contain the following text:
[FONT=Courier New]auto lo
iface lo inet loopback[/FONT]

Add something like this:
[FONT=Courier New]auto eth0
iface eth0 inet dhcp
dns-nameservers 61.9.211.33 61.9.211.1[/FONT]

In this case 'eth0' is my wired connection and I've listed two DNS nameservers separated by a space.

Restart your connection using
[FONT=Courier New]sudo ifdown eth0
sudo ifup eth0[/FONT]

Go to the heading 'Name Resolution' of this Ubuntu wiki page to see a full explanation
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution)


Option c. You can install and use the "resolvconf" package.
[FONT=Courier New]sudo apt-get install resolvconf[/FONT]

Add line/s to **/etc/resolvconf/resolv.conf.d/head**
[FONT=Courier New]nameserver 61.9.211.33
nameserver 61.9.211.1[/FONT]

Then update the configuration files with:
[FONT=Courier New]sudo resolvconf -u[/FONT]

---

### Post by dude123dude on 2012-09-30
@bjorn.aigen post above.

You can use google DNS servers instead:
8.8.8.8
8.8.4.4

They are free and fast.

Also, I'd like to comment on bjorn.aigen phrase "b. Disable IPv6 permanently in the 'grub' boot setting".

You don't disable it with "grub boot setting". You are able to supply kernel with parameters (cheatcodes) when its started and grub allows that. 

So, should not be called
"b. Disable IPv6 permanently in the 'grub' boot setting", 

but
"b. Disable IPv6 permanently using kernel parameter. This is passed via 'grub', the boot loader."

Thats solely to help you understand things better. Good suggestions otherwise.

Also, your connection might be illegally throttled by your provider if they detect you P2P, regardless which content.

---

### Post by bjorn.aigen on 2012-09-30
re: dude123dude's corrections
Thanks!   It's encouraging to see a peer review on technical semantics.  I thought this thread was dead when there was no response to the initial query after 7 weeks.    I've adjusted the wording and if there's still some ambiguity, please reply.

re: slow internet on Ubuntu compared to Windows
My internet was slow with Ubuntu from day one of ADSL.  But, my ISP, Telstra Bigpond, and I verified that the connection speed between the exchange and my wall socket was high using  another OS i.e. Windows.    Most of the retardation was at the  initial loading of a page not the download of content, which is symptomatic of a DNS issue.

re: ISP throttling P2P traffic
Throttling would not have caused such  a slow page load that I was experiencing.    Call me 'obtuse' but I've never seen evidence of this happening in Australia.  I am aware of ISP filtering of illegal content but that is off-topic.__[URL="http://paritynews.com/web-news/item/163-isps-throttling-bittorrent-traffic-study-finds"]
[/URL]

---

