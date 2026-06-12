---
title: "Home server building"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by toadinapintglass on 2013-03-28
Hi
I'm after building a home server so that i can watch films on my TV and download torrents,
I just wondering what software be best for doing this as I've just installed Ubuntu
I want to be able to excess the server via a computer and laptop and able to play films
on the server which will be directly connectted to the Tv

thanks for your time
Toadinapintglass

---

### Post by csurlee on 2013-03-28
I think if you can connect your TV to your network with ethernet cable you can do it simple. Intall ubuntu server and for torrent transmission with GUI(totorial [http://1000umbrellas.com/2010/04/21/transmission-install-on-ubuntu-10-04-server-lucid](http://1000umbrellas.com/2010/04/21/transmission-install-on-ubuntu-10-04-server-lucid)), and for file sharing use Samba (a little totorial [http://ubuntuforums.org/archive/index.php/t-26438.html](http://ubuntuforums.org/archive/index.php/t-26438.html)). The only thing you need to do is to set your download directory in samba to be shared.

---

### Post by 3rdalbum on 2013-03-28
I did exactly the same for many years.

Just install system-config-samba on the server computer, and you'll have a nice easy GUI for setting up a basic Samba server that any other networked computer will be able to access. Most/all networked media boxes can access Samba servers. Perhaps even your smart TV if you have one, although you mention you'll be plugging the server directly to the TV.

For downloading torrents, you can use Transmission or Deluge. I tried both, and eventually settled on Transmission for its very easy-to-use web interface. With that, you can manage your torrents from any other computer on your network. You do need to enable the Transmission web UI in the Transmission settings.

---

### Post by mastablasta on 2013-03-28
then there is also interfaces such as XBMC and similar.

---

### Post by toadinapintglass on 2013-03-28
Sorry guys should of made myself clearer....My Tv is not a smart one and has no internet connection so really want the display of the server on my Tv via HDMI
I'm not going to have any keyboard or mouse connectted so I would need remote excess via laptop/desk pc or even a mobile phone..mobile phone i doubt it be possible.


Thanks for your prevoius answers i'm reading and trying them out now

I installed deluge but cant excess it thru my comp/laptop using 

[https://192.168.0.11:8112/](https://192.168.0.11:8112/)
I've enabled WebUi plugin  and abled both web interface and ssl..port i'm using is 8112

---

### Post by Choragos on 2013-03-28
Regarding mobile phone, you can indeed connect via ssh--I use connectbot (you will either have to access it from outside your network if you're using your dataplan, or you can hit it from within your network as long as you're connected to wifi).  In either case, you'll need openssh daemon running.  If you want to use your phone as the keyboard and mouse with the TV as your monitor, that's a different story however.

Just a quick check regarding your latest post--are you sure you should be using https?  I'm not familiar with deluge so I don't know what port you need to be using.  It seems like overkill to be using https from within your home network.

---

