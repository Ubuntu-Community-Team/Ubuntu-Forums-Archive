---
title: "Help with vlc remote"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by mattymoomoo on 2011-10-26
Hello all,
fairly new to Ubuntu and new to forums but a friend told me this would be a good place to start to learn.

I'm trying to set up vlc remote. I followed the linux instructions on [http://hobbyistsoftware.com/VLCSetup-linux](http://hobbyistsoftware.com/VLCSetup-linux) but when I try to connect the phone I get java.net.ConnectException: /192.168.1.1:8080 - Connection refused.

If anyone would be willing to help an absolute beginner and endure some dumb questions I would really appreciate it.

---

### Post by khelben1979 on 2011-10-26
How does the information looks like in here: /usr/share/vlc/http/.hosts ? According to what I read on the webpage, your phone haveto allow the permission for the file access.

Also, can you mention something about the phone, it might differ depending on the model number, I don't know.

To note, I haven't done this myself but I'm gonna try to help out, so everything you've tried in accordance with the guide itself would be good to know.

---

### Post by krijg87 on 2011-11-15
What is the IP of the computer you are running the VLC server on? I'm guessing not 192.168.1.1, find out the (private!) IP address this computer has on your network. The private IP address is in the range from 192.168.0.0 to 192.168.255.255. Use that IP to connect with your phone.

---

### Post by hungry_pete on 2012-04-05
I had problems with getting all this to work so I guess others have too. It must have taken me a day in all!

First of all, check you've done all this:

[URL="http://hobbyistsoftware.com/VLCSetup-linux"]http://hobbyistsoftware.com/VLCSetup-linux
[/URL]

Then try as many of these steps as you can:

[http://wiki.hobbyistsoftware.com/wiki/VLC_connection_troubleshooting]("http://wiki.hobbyistsoftware.com/wiki/VLC_connection_troubleshooting")

It basically checks 3 main things:

1. That the server is running on the vlc PC (using localhost and therefore ignoring any ip address problems)
2. Checks the server's function with using the correct ip
3. Checks that it will run across your network.

My setup fell down when testing across my WIFI home network. This was because my router was blocking access to ports, nothing to do with the PCs using the router at all. The solution to this is to change the firewall settings within the router to make sure there is the correct access to port 8080. I used this website to help me out:

[URL="http://portforward.com/"]http://portforward.com/
[/URL]

This link was hard to find from the VLC help pages, but seems to be a fairly critical problem. I've found a few forums where connections have failed to work at this stage, and no clear solution presented.

Although the right combination of router and application wasn't available on this site, I followed a guide for my router model and the VNC/Generic guide to give me the idea. If you can't remember your router password, then its probably still at its default and you can normally find that through a google search.

Hope this helps someone!

---

