---
title: "set up for network xp to ubuntu via ethernet"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by 3blaxcatz on 2008-08-19
Hello,
I so hope i get a response to my question - i am at the stage of trying out ubuntu - after a few hiccups i got ubuntu running off of the cd as per the many instructions.

i want to check that all my hardware etc works before i install fully - i plan to totally replace windows xp on a 2nd computer that i use for a tape disk that i have installed which then coverts my old mix tapes to mp3 and browsing/sharing these files between the 2 computers and share internet access

i had both computers networked using a ethernet/crossover cable in windows xp and according to the blurb these setting should have been configured automatically

but i can not access the internet in unbuntu on reboot - although i can check the network connection in both computer and it shows as being connected and active on both (its listed as windows network in ubuntu) & i can even seen the windows shared folders, i get to the stage of asking for permission!

so i rebooted in safe mode with networking to be able to access the support directly from ubuntu

i have run the terminal check (ifconfig) all o.k and network tools (ping 182) 0% success and ubuntu.com (ping) 100% success

so with my non computer person head on it should be fine in normal mode

it is not

i can see the network device and if i go to set properties i do not have  option to enable this connection only enable roaming

i can enter all of the settings as in the beginners tutorial but get lost at the local host bit

i spent 1 hour 'watching' the chat on the ubuntu IRC but it's like standing in the middle of a forest - no one can hear you scream :o)

---

### Post by ggaaron on 2008-08-19
If I got it right, do you have the Internet -> Ubuntu -> 2nd Ubuntu?
And you say that 1st Ubuntu is well configured as in safe mode 2nd Ubuntu works and in normal mode it doesn't?

---

### Post by 3blaxcatz on 2008-08-19
i have internet on computer 1 with windows xp via cable modem

computer 2 with ubuntu connects to internet via cross over cable from computer 1

computer 1 does not have ubuntu

i re-booted computer 2 in safe mode (with networking opion) and then can access internet on computer 2

---

### Post by ggaaron on 2008-08-19
You use static ip on the second machine or you get it by dhcp from first one?

---

### Post by 3blaxcatz on 2008-08-19
i did use static ip on the 2nd

wot do i do on the 1st?

---

### Post by ggaaron on 2008-08-19
Possible problem is that NetworkManager doesn't support static ip in current version. I don't really know how does the secure mode look like, but have you tried turning off roaming in NetworkManager and setting it's ip and gateway somewhere there? (I don't use GNOME, nor Ubuntu actually co I can't be more accurate=)

It you can't set it there in gui then:
Turn off NetworkManager roaming on your device - this should make it possible to use static ip on this device
Edit as root /etc/network/interfaces and make it look something like this (file from my Debian system, on Ubuntu should be the same):

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth0
auto eth0
iface eth0 inet static
        address         153.19.140.20
        netmask         255.255.255.0
        network         153.19.140.0
        broadcast       153.19.140.255
        gateway         153.19.140.254
```

Change address to your ip, network = ip with 0 on the end broadcast = ip with 255 on the end, gateway is your first machine's ip. Then run sudo /etc/init.d/eth0 restart. Network should work.

---

### Post by 3blaxcatz on 2008-08-19
thanks so much
i went with your first suggestion 

lost internet connetion on both machines 

rebooted in normal mode on computer 2 and i have internet access on it!! amazing i don't know what i did right!

i think you're right re the settings as i was wondering why it kept coming up with different numbrs to those on computer 1

as this is my very first time in any other os except windows i can't comment on 'new' interface

the reviews i read encouraged me enough to give ubuntu a good and i am very pleased that i did - if all goes well - i may uninstall windows from computer 1

can you please tell me where i find the network manager?
i have 2 options under admin-> network & admin -> network tools

 the tutorial i was following said it looks like signal bar but i can not see it

i do have a pictue of 2 computers (network connections) on desktop

---

### Post by ggaaron on 2008-08-19
I must say that I'm confused about your post... So did it work? If yes then why are you searching for NM?

The two monitors on your panel is NetworkManager's applet to control it - you can choose what net interface to use if you have more than one, configure wifi and so on. For more configuration I'd try this menu option.

---

### Post by 3blaxcatz on 2008-08-19
yes all is well - i want to make sure i understood the instructions - just in case i need to make change in the future -

thanks for yur help 

very much apprcited

---

### Post by ggaaron on 2008-08-19
Ah, then I'm happy I was able to help=)

---

