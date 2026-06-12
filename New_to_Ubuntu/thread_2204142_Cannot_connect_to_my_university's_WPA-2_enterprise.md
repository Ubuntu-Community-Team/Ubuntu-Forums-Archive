---
title: "Cannot connect to my university's WPA-2 enterprise network"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by jordan12 on 2014-02-07
Hello all,

I recently installed Unbuntu 12.04 on an old laptop of mine and I'm trying to get it up and running. Unfortunately my university does not provide us with a wired connection and they only use 802.1x so I cannot share a port on my macbook with my other laptop. I searched for some help and found a thread for my laptop with the driver which I downloaded in a zip file (the old laptop is a Dell Inspiron 1525). I moved them over via usb drive and now I am trying to connect to the WiFi. So I added the network and configured all the security (wpa2 enterprise, peap, i copied the security cert from my mac, and i entered in my username and password). When it goes to connect it just plain wont and it keeps popping up saying I need a login and password (which it has saved already in the window). I click continue and the window comes up again, I had read that you need to delete a line that asks for the cert but i do not know how to do this. 

Any help?

---

### Post by varunendra on 2014-02-07
Hello Jordan12! Welcome to the forums ! :)

> **jordan12 said:**
> I had read that you need to delete a line that asks for the cert but i do not know how to do this.

If you added the certificate file correctly, you shouldn't need to delete that line. But let's check it anyway. Please open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo grep system-ca-cert "/etc/NetworkManager/system-connections/*<the name of your connection>*"
```
Do you see a line that says "system-ca-certs=true" ? If yes, we may try to change its value to "false" or delete the line altogether. To change the value -
```
sudo sed -i '/system-ca-cert/ s/true/false/' "/etc/NetworkManager/system-connections/*<the name of your connection>*"
```

To delete it -
```
"/etc/NetworkManager/system-connections/*<the name of your connection>*"
```

But like I said, it shouldn't be necessary if you provided the required certificate file correctly. So if you don't see such a line, or modifying/deleting it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by jordan12 on 2014-02-07
hi, [COLOR=#000000]varunendra,[/COLOR]

[COLOR=#000000]Thanks for the reply, whenever I type in the first command the only thing I receive back is a prompt to type in another command under that directory. It doesn't come back with any information.
 
I ran the wireless script and it came up with these results that are attached
[/COLOR]

---

### Post by varunendra on 2014-02-07
> **jordan12 said:**
> whenever I type in the first command the only thing I receive back is a prompt to type in another command under that directory.

You mean "Sudo" asking for your password? Because that's the only thing that the terminal would ask you back when running the first command. It is asking for your user password for authentication to be able to read your connection's "KeyFile". Authentication is required because these files contain sensitive data (your connection's password).

Just type in your login password at 'sudo' prompt and press 'Enter'. It won't show anything on the screen while typing your password, that's a security feature and is normal.

If you already did that and the command returned nothing, then your connection file doesn't have that line in it. In that case, could you post a screenshot of your wireless security settings in Network Manager? Do they look like the screenshot posted in this post : [http://ubuntuforums.org/showthread.php?t=2203794&p=12922093#post12922093](http://ubuntuforums.org/showthread.php?t=2203794&p=12922093#post12922093) ?? The "Ca Certificate" may or may not be applicable to your network.

And for a test, could you please also try what is suggested in this post about "binding an Access-Point's BSSID with Network Manager" : [http://ubuntuforums.org/showthread.php?t=2203727&p=12922057#post12922057](http://ubuntuforums.org/showthread.php?t=2203727&p=12922057#post12922057) ??

---

### Post by jordan12 on 2014-02-07
I took a screenshot of both what I was typing into command prompt and the settings for my wireless network. I'm going to attempt to go to a university computer lab, use one of the ethernet cables plugged into one of the computers and try and re download my wifi driver. The problem with that thinking is that it can connect to my university's guest network no problem. It brings up the need for a username and password in firefox and its a university site. Therefore i know I can access the internet but i just cannot access the regular student connection. 

Here are the files:

---

### Post by varunendra on 2014-02-07
The "system-ca-certs=true" clearly doesn't exist in your keyfile as per the terminal output.

Where did you get the CA Certificate from? From university authorities?
And are you sure the username is just the user id? Not something like "userid@university.domain"?

I believe you have already confirmed these, but please do if you haven't.

As for the driver, if it is able to connect and work nicely with ANY other network, then it is fine. Although you may try the latest version of the proprietary "sta" (or "wl") driver if you doubt the current native one. We here prefer the one you are currently using, but a couple of recent posts mentioned the sta driver also worked with this card, better or not, I'm not sure. But to be honest, to me the problem seems to be in settings, not in the driver.

---

### Post by jordan12 on 2014-02-07
When i log into my university's wifi for the first time this is the chain of events. 1. enter DuqNet as ssid 2. select wpa2 enterprise peap security 3. enter username "byersj" 4. enter password ************ 5. click ok connect or whatever. 6. open chrome or firefox and type in a random page. 7. A page from the university comes up and asks if you want to authenticate this computer, you enter in your username and password again and click authenticate. 7. go along with your business. At one point they asked students to download a program called CGagent gatekeeper which was an endpoint compliance system to make sure your computer had compatible hardware. My security certificate came from my mac. I copied it from my keychain access file list in a .cer file. They dont provide the certificate online. I can link how they suggest connection to the network via mac or pc as they do not have linux steps listed but say it is supported. 

Would there be a page I could download a new wifi driver that I could transfer from my mac to the unbuntu laptop, as of right now thats my only way of downloading files and transferring

[http://www.duq.edu/about/campus/computers-and-technology/network/duqnet-wifi](http://www.duq.edu/about/campus/computers-and-technology/network/duqnet-wifi).

---

### Post by jordan12 on 2014-02-07
do you think that updating my laptop to 13.10 would help?

---

### Post by jordan12 on 2014-02-07
So, the problem is strictly on connections that require passwords. I tried to tether my iphone to the laptop and it wouldnt accept it with a wpa2 personal password

---

### Post by varunendra on 2014-02-09
> **jordan12 said:**
> do you think that updating my laptop to 13.10 would help?

There is an alternative driver for your card that you may try. Although most of us here believe what you are currently using is actually the correct one and the alternate "sta" driver doesn't work correctly with with the BCM4312 card, yet a couple of users recently reported it to be working just fine with their cards.

I am more doubtful about your CA Certificate *(1st, its name seems to contain characters not recognised by Ubuntu, I wonder if same maybe the case with its contents too; 2) It may not be applicable to Ubuntu at all)*. Have you tried settings without CA Certificate yet?

A few users at a bug report page (or AskUbuntu, I don't remember now) had also reported that manually adding the "system-ca-certs=false" line worked for them. May sound odd, but I personally have absolutely no experience with this kind of Enterprise networks yet, and so don't yet know where exactly to add this line in the keyfile. I can not experiment with a Virtual Machine since one of my RAM modules failed and I am currently running on 2GB RAM onle. It is not sufficient to run an Ubuntu instance in a VM.

So if you wish to try once more the 'ca certificate' fix, you'd have to help me help you. **Please post the entire contents of your keyfile (/etc/NetworkManager/system-connections/DuqNet)**. It also contains some sensitive information like your **[COLOR="#FF0000"]Password[/COLOR]. Obscure or remove it before posting here**. Same with the MAC ID if you wish.

For reference, the **comment #131** and following ones on this bug report page may be interesting : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476)

And if you still wish to try an alternative driver (I seriously doubt it is going to help, especially if you can connect to other networks fine), you may try -
```
sudo apt-get install bcmwl-kernel-source
```
..then reboot. If, as I suspect, it fails to work too, revert back by purging it -
```
sudo apt-get purge bcmwl-kernel-source
```

---

