---
title: "Need Help Writing a Script to Automatically Start VPN"
date: 2015-05-03
forum: New to Ubuntu
---

### Post by Wadcutter on 2015-05-03
I've spent as much time as I can trying to figure this out and fix by myself without asking someone else for his/her time. I've read many posts in various sites and have struggled trying to rise above my newbie ++ status with no success. It's like I know just enough to think I can make it work, but it doesn't. And now other responsibilities are saying I have to fix it or forget it.
 

 I want my VPN (Open VPN with PIA as the provider) to start automatically at boot or soon thereafter. Another person asked for help in, I believe, an Ubuntu forum a few years ago. The solution presented was to learn the uuid of your device and then write the following command: 'nmcli con up uuid  c34fXXXX-5ed2-XXbe-a46b-5eaaXXXXXb71'. The proof that it works is that if I enter it into a terminal, it will switch on my VPN. The poster then suggested that to make it work, all one had to do was enter the command into your Startup Applications as a new program and all would be good.

 

 But all is not good. It doesn't work as a Startup. Don't know why but am guessing it has something to do with timing in that my wired connection to my ISP has to occur first before I can switch on the VPN. I'm guessing that this startup command might happen too soon before the ISP  automatically connects. Just a guess at some logical reason for it to fail. Might be some other problem. Perhaps it worked with earlier versions of Ubuntu. I am running 64 bit Precise LTS on a homemade desktop.
 

 So I've been trying to teach myself to put this command into a shell script file to start automatically. It looks like having crontab start it with '@reboot' command would work, but the correct syntax with that and with making a shell.sh file and where to put it is still quite a bit above my pay grade. It all seems so simple because I know that command will turn on the VPN but how to get it to launch by itself is escaping me. It's like I know just enough so that I don't know what it is that I don't know. I would be grateful for help or suggestions.

---

### Post by nerdtron on 2015-05-03
You can write your exact command script on the .sh file like this:

```
#!/bin/bash
sleep 30
nmcli con up uuid  c34fXXXX-5ed2-XXbe-a46b-5eaaXXXXXb71

```

Then save that file as for example vpn-up.sh and save in you home directory. The 30 seconds delay during startup should let your system connect to network before attempting to connect the VPN.

Then from the command line. Make the script executable
```
chmod +x /home/user/vpn-up.sh
```

To test that the script works, disconnect you vpn and then run the script. (it will take more than 30 seconds)
```
/bin/bash /home/user/vpn-up.sh
```

If all is good, then add this to your startup applications. On the program/command box. The command above that you just ran.

---

### Post by Wadcutter on 2015-05-04
That works fine. Thank you, nerdtron. I had most of the pieces but I put them in the wrong places and wrote a wrong command in the Startup. But I did begin to learn more about shell scripts.

---

### Post by ofnuts on 2015-05-04
If your VPN has a matching plugin (most do... and I think OpenVPN has one) to integrate it with the Network Manager then it's just a matter of ticking a checkbox to have it started when some specified connection is started. The plugin also makes the VPN very easy to start/stop from the network widget in the system tray.

If you use a script, you can have this script started from a network connection notification (in KDE: System settings>Common Appearance and behavior>Application and system notification/Event source: "Notifies about network errors"/State: "Active connection state changed".

---

