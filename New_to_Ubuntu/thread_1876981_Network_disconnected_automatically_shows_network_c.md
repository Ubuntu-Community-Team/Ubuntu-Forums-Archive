---
title: "Network disconnected automatically shows network cable unplugged"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by NikS on 2011-11-07
Hi all,
I am facing an issue with my DSL connection. The connection is disconnected if remained idle for some time, which if good. But once disconnected the network applet in gnome shows no option to reconnect. In 'network settings' under the 'wired' option it shows 'cable unplugged' even though the cable is as is.
Restart solves the issue, I get the 'on/off' option back and the network works, but a restart every time it disconnects is not easy!

It just disconnected the connection, by itself, why does it say the cable is unplugged? Is there a way to make it detect the already connected cable?

---

### Post by westie457 on 2011-11-07
Hi instead of rebooting try unplugging and re plugging the cable, that might reset the ethernet port. 

In Network Manager > Edit Connections are the boxes checked to 'connect automatically' and 'available for all users'.

If it still does not reconnect then try using a different cable.

If the problem is still there then it might be a failing ethernet port on the motherboard.

After trying the above and it still does not work properly, hopefully someone will be able to help you.

Good luck.

---

### Post by NikS on 2011-11-07
Hi westie457, thank you for your response.

I have tried replugging the cable, it does not detect.
by the way, I just tried running pppoeconf from terminal and I am able to reconnect even when the applet says cable unplugged. So something to do with the applet itself, I guess...?

Any ideas?

---

### Post by westie457 on 2011-11-07
Unfortunately no more ideas from me on this issue. All my knowledge or lack of about DSL connections was in the first reply.

---

### Post by NikS on 2011-11-13
ohk! :)

Still have not been able to find a solution for this. Anyone has any idea?

---

### Post by grahammechanical on 2011-11-13
I am assuming that you are using 11.10 like me and that you are referring to the Network applet in System Settings.

I have just now unplugged my ethernet cable and the status changed to Cable Unplugged but as soon as I plugged the cable back in the status changed to Connected again. So, this should happen with your system.

I have found that sometimes the connection to the ISP breaks down. It has only happened a few times. I am guessing that certain web sites may give a time out signal that breaks the connection. The LED on the router that gives the Internet status of the router goes out. Is this happening to you?

In my case I sometimes have to restart the router. Other times I use the Network icon to disable Networking and then I enable Networking and I get back on the Internet. You should not need to reboot.

The Network applet knows that we have a cable connection but it cannot tell the difference between a broken connection due to the cable being unplugged, the router being switched off or the phone to the ISP breaking the connection.

May be this will help. Regards.

---

### Post by Cyclane on 2011-11-13
I'm confused, is your computer directly connected by DSL or is your computer connected by ethernet to a router?

---

### Post by NikS on 2011-11-13
> **grahammechanical said:**
> I am assuming that you are using 11.10 like me and that you are referring to the Network applet in System Settings.

I have just now unplugged my ethernet cable and the status changed to Cable Unplugged but as soon as I plugged the cable back in the status changed to Connected again. So, this should happen with your system.

I have found that sometimes the connection to the ISP breaks down. It has only happened a few times. I am guessing that certain web sites may give a time out signal that breaks the connection. The LED on the router that gives the Internet status of the router goes out. Is this happening to you?

In my case I sometimes have to restart the router. Other times I use the Network icon to disable Networking and then I enable Networking and I get back on the Internet. You should not need to reboot.

The Network applet knows that we have a cable connection but it cannot tell the difference between a broken connection due to the cable being unplugged, the router being switched off or the phone to the ISP breaking the connection.

May be this will help. Regards.

Yes, I am using 11.10 and the issue is with the applet (seems so).. The lights on router are still on when it shows disconnected..
Sadly, Once it starts showing 'unplugged' in this way, there is no way to get it back working other than restarting the computer... removing-reconnecting the cable, restarting the router has no effect.. :(

> **Cyclane said:**
> I'm confused, is your computer directly connected by DSL or is your computer connected by ethernet to a router?
My computer is connected to a router by ethernet.

Here is screenshot: [http://img851.imageshack.us/img851/5323/screenshotat20111114001.png]("http://img851.imageshack.us/img851/5323/screenshotat20111114001.png")

See the applet is showing disconnected, the settings show network cable is unplugged, USC shows disconnected (not in image), but I am still online, posting this message.. I can connect, but there is no way to convince USC/shell etc that I am online.. :confused:

Is there a way to restart the gnome3's network applet? It is not nm-applet is it? restarting gnome shell has no effect..

---

### Post by NikS on 2011-11-13
ohk.. from what I read at: [http://stackoverflow.com/questions/808560/how-to-detect-the-physical-connected-state-of-a-network-cable-connector]("http://stackoverflow.com/questions/808560/how-to-detect-the-physical-connected-state-of-a-network-cable-connector")
When I turn off power to my router, the carrier and operstate values do show 0 and down, when I turn is back on, they again show 1 and up! So its detecting the connection correctly..! What next?

---

### Post by Cyclane on 2011-11-13
So still no connection after the reboot of the router?

Could I see the output of the following?
```

ip link show
ip addr show
```

---

### Post by NikS on 2011-11-14
I am able to connect, just the connection is not detected by the shell/other softwares like USC.

Anyways, have found the solution by trial and error.
```
sudo killall NetworkManager
``` kills and restarts the applet. If it doesnt restart, typing
```
gksu NetworkManager
``` does it.

Thanks all for the help and suggestions..! :)

---

