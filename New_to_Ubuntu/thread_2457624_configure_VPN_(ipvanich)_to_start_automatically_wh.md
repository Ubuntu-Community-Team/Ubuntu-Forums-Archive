---
title: "configure VPN (ipvanich) to start automatically when starting ubuntu 20.04"
date: 2021-02-05
forum: New to Ubuntu
---

### Post by oliverjhonson on 2021-02-05
Dear friends, i have a contrat whit IPVanich vpn, but always i need start manually the VPN when i restart the computer, it may start automatically when i restart the computer.
[IMG]https://imagizer.imageshack.com/img922/3593/5fqy37.png[/IMG]

---

### Post by jcdenton1995 on 2021-02-05
I have a contract with Proton VPN, but I use the 'openvpn' command line program as the client, instead of the official Proton VPN client. You could create a command that starts the openvpn client, and set it to run each time you turn the computer on. As an example, the command I use is...```
sudo openvpn --config ~/.config/protonvpn/serverconfigs/[CONFIGURATION_FILE_HERE]
```The file path at the end is the path to the configuration file that determines which VPN server the openvpn client will connect with, and inside that file is a line which points to another file that contains my login information, so I don't need to enter the username and password every time the vpn connection starts. Proton VPN let you download these configuration files from their website, one file for each different server you can connect to, I'm guessing IPvanish will offer a similar thing?

If you press the 'super' key on your keyboard (on the bottom left, inbetween 'ctrl' and 'alt') and then type "Startup Applications" and press 'enter', it will open the application you can use to save commands that will run each time the computer starts. Here you can save a command similar to the one I wrote above which starts the openvpn client. Then all you have to do is add one line to the configuration file which points to another file that contains your login details (only the root user should have permission to read or write this file)

If all that makes sense I'm happy to go through the steps in more detail (or try to explain in my bad spanish), but you might want to wait for one or two days because somebody else on the forum might know a much easier way for you to do it, or possibly someone with better spanish will be able to help you :)

---

### Post by ActionParsnip on 2021-02-06
Could make a service file yo start and stop the VPN. You could then add the start command to /etc/rc.local to run at boot.

---

### Post by oliverjhonson on 2021-02-06
> **jcdenton1995 said:**
> I have a contract with Proton VPN, but I use the 'openvpn' command line program as the client, instead of the official Proton VPN client. You could create a command that starts the openvpn client, and set it to run each time you turn the computer on. As an example, the command I use is...```
sudo openvpn --config ~/.config/protonvpn/serverconfigs/[CONFIGURATION_FILE_HERE]
```The file path at the end is the path to the configuration file that determines which VPN server the openvpn client will connect with, and inside that file is a line which points to another file that contains my login information, so I don't need to enter the username and password every time the vpn connection starts. Proton VPN let you download these configuration files from their website, one file for each different server you can connect to, I'm guessing IPvanish will offer a similar thing?

If you press the 'super' key on your keyboard (on the bottom left, inbetween 'ctrl' and 'alt') and then type "Startup Applications" and press 'enter', it will open the application you can use to save commands that will run each time the computer starts. Here you can save a command similar to the one I wrote above which starts the openvpn client. Then all you have to do is add one line to the configuration file which points to another file that contains your login details (only the root user should have permission to read or write this file)

If all that makes sense I'm happy to go through the steps in more detail (or try to explain in my bad spanish), but you might want to wait for one or two days because somebody else on the forum might know a much easier way for you to do it, or possibly someone with better spanish will be able to help you :)




[COLOR=#000000]thanks for you response, but i am honest don't understand very good, i think i need to do a couse about Linux, any advice...[/COLOR]

---

### Post by oliverjhonson on 2021-02-06
> **ActionParsnip said:**
> Could make a service file yo start and stop the VPN. You could then add the start command to /etc/rc.local to run at boot.

i think this solution is easier, but i don't know how create a service file? someone cuold have a patience to explain me how i can create the connection service to the VPN, the file name for VPN connection is "ipvanish-ES-Madrid-mad-a15.ovpn", thank you very much for you support.;)

---

