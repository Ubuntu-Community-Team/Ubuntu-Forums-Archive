---
title: "Re: Internet Connection Sharing Documentation"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by SlickClick on 2012-05-12
Ok im a total newbie w/ LINUX & just installed Ubuntu on a windows XP machine just to get my feet wet with this OS; my intent is to further my skills in this new arena of IT so I can move towards Android kernal programming...

So I have installed ver 12.x on my machine I actually like the interface except for the complicated command line gibberish found in this "guide":
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

For the most part I figured out how to edit files using the terminal, which for a newbie it would have been nice if in the "guide" it mentioned editing files this way...

So I get to the point of "ubuntu Internet Gateway Method (iptables)" gateway setup & well basically the example code makes no sense and doesnt work at all & now im getting crash reports that I dont know what have to do with what anymore now....

Here is my setup & im sure for many others its a common setup that seems to be complicated by a simple "disabled" settings area in the GUI portion of "network settings" panel...

After trying to follow the above links "guide" it seems to me that IF when the "share connection" is selected in the ipv4 tab of the network card to be shared that IF there in the GUI I could simply input my IP, sub-net, & gateway info there none of this other confusing command line giberish would be needed... But its all shaded out & not accessible...

I have 2 NICs one wifi which works fine & is my internet connection to my ISP router the other is the onboard wired NIC to feed a second router... 

All I need for is the wired/onboard nic (eth0) to be "shared" & to have the following settings:
IP 192.168.0.1
Subnet 255.255.255.0
Gateway 92.168.10.x

Its my understanding from the "guide" this has to be set/done from a terminal command line, but the guides references dont work or set the "eth0" to anything; im a total newbie to LINUX but no rookie to the IT world...

Any clarification from the "gateway" setup instructions from the "guide" will helps tons..! Id also be willing to rewrite something for newbies trying to setup "ics" whom too have no prior LINUX/Ubuntu experience...

---

### Post by lisati on 2012-05-12
Moved to own thread from [http://ubuntuforums.org/showthread.php?t=503287](http://ubuntuforums.org/showthread.php?t=503287)

---

