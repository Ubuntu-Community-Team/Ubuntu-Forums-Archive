---
title: "Without wireless"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by ConconDoesGaming on 2013-04-05
Hello forum,

I am a new user to Ubuntu (yesterday) and am struggling to connect wirelessly to my WiFi. Coming from Macs + Pc's I am used to having all my connections that are available where the internet sign is. Unfortunately as of creating this thread I am wired into my router, I have also tried connecting manually and failed, however I don't wish to connect that way in future (connecting to hotel WIFI's etc).

Any suggestions would be great and appreciated!

:KSConor:KS

---

### Post by TechGeekT on 2013-04-05
If you are connected to the router run the updates. It'll download what you need for the wireless. I'm and new user and had the same issue, but thankfully I could connect directly to the router to run the updates. After they installed and a restart, it found my WiFi.

---

### Post by Perfect Storm on 2013-04-05
You can also check if there's an available restricted driver for your wireless.

Click the 'super key' (the windows key).

On Ubuntu 12.04 type: drivers. Click on 'additional drivers'.

On Ubuntu 12.10 type: sources. Click 'Software Sources'. ---> go to 'addtional drivers' tab.

---

### Post by mörgæs on 2013-04-05
Please don't double post. 
The other one has been deleted.

---

### Post by ConconDoesGaming on 2013-04-05
Ubunut 12.10?

---

### Post by ConconDoesGaming on 2013-04-05
Where + what updates need to be installed?

---

### Post by TechGeekT on 2013-04-05
I have 12.04 LTS. There should be a cog wheel in the upper right corner. You should see it listed there.

---

### Post by ConconDoesGaming on 2013-04-05
Updates installed... "[COLOR=#000000]It'll download what you need for the wireless." 
Not sure how much of a difference it's made, what did you do next? nothing showed up differently for me.[/COLOR]

---

### Post by TechGeekT on 2013-04-05
Click Edit Network Settings -> Go to Wireless and add your WiFi info

---

### Post by ConconDoesGaming on 2013-04-05
I already had that and couldn't get it to work, I was wondering if I can get all the available networks open to me at that time (like pc + mac) to automaticly show. If i can't get this to work I might have to switch back.

---

### Post by TechGeekT on 2013-04-05
Well don't give up. There's a way. What system are you using? I'm using a Mac w/ Mountain Lion and partitioned Ubuntu as well as a shared data drive to share my files between the two.

---

### Post by ConconDoesGaming on 2013-04-05
I'm using a Compaq Presario V6000 Laptop partitioned 80% - 20% Ubuntu, I'm running 12.10 version I believe. (as well as a mac) (the 20 = Windows).

---

### Post by TechGeekT on 2013-04-05
Do you know what network card you have? If not here's a way to find out using the terminal [http://ubuntuforums.org/showthread.php?t=828709](http://ubuntuforums.org/showthread.php?t=828709). Assuming you know how to use the terminal. I do not mean that in any way as an insult if you do. I'm just trying to assess how comfortable you are with computers.

---

### Post by ConconDoesGaming on 2013-04-05
[http://postimg.org/image/6dmzofxvr/](http://postimg.org/image/6dmzofxvr/)
So no way to show the open networks in my area on linux?

---

### Post by TechGeekT on 2013-04-05
Check to see if there are anymore updates. Have you found out about the wireless card yet?

---

### Post by TechGeekT on 2013-04-05
How about this install a device manager [http://ask.ubuntu-mm.net/index.php/62/how-to-install-device-manager-on-ubuntu-12-10-04](http://ask.ubuntu-mm.net/index.php/62/how-to-install-device-manager-on-ubuntu-12-10-04)

---

### Post by wildmanne39 on 2013-04-05
Sure there is, most likely we can fix your issue, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

