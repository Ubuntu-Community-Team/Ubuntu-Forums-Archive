---
title: "internet stopping"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-12
I'm an idiot and installed something and then forgot what it was i installed which is causing problems with my internet it stops and then i have to restart it from the wireless menu i remember seeing something in the thread about using two commands to fix this but i just cant remember what the application was :( i can remember installing moblock and mobloquer as well as k9copy can anyone help please!!!!:lolflag:

---

### Post by licensedorchid on 2008-05-12
If you install apps using the command line, you could just type ```
history
``` and the command line, and look through there for something that looks familiar.
If you used synaptic, you could try looking through the logs in /var/log/apt/ using ```
sudo less /var/log/apt/term.log
```
That being said, I don't know what you could install that would disconnect your wireless connection. Maybe WICD and NetworkManager are fighting?

---

### Post by Aearenda on 2008-05-12
If it was a regular package you installed, you can look in the history - open system->administration->synaptic package package manager and choose 'history' on the file menu.

EDIT: licensedorchid beat me to it! Same idea :-)

---

### Post by kamitsukai on 2008-05-12
```
  142  lspci
  143  sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
  144  gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
  145  gpg --export --armor 9072870B | sudo apt-key add -
  146  sudo gedit /etc/apt/sources.list
  147  sudo apt-get update
  148  sudo apt-get install moblock-nfq
  149  sudo apt-get update
  150  sudo apt-get install moblock mobloquer
  151  history
  152  sudo less /var/log/apt/term.log
  153  history
dreamsofubuntu@dreamsofubuntu-desktop:~$     
```

Thia is from when the problems started happening so i think it must be one of those programs causing the problem also i have firestarter installed alongside moblock which apparently conflict with each other and moblock isn't blocking anything please help!

---

### Post by licensedorchid on 2008-05-12
moblock blocks traffic, but it shouldn't kill your internet connection!
Have you tried power cycling the wireless, or eve better, when you get disconnected, open up a console, and type
```
 sudo tail -25 /var/log/messages 
```
That will tell you why you are getting disconnected, more than likely.

---

### Post by kamitsukai on 2008-05-12
ok next time i get kicked off i will check

---

### Post by jimtb on 2008-05-13
Probably moblock is blocking the IP of your router. Open mobloquer and check which IPs are being blocked when you are trying to connect to a website. 

If you see IPs like 192.168.178.1 then stop blocking them using the appropriate button in mobloquer. You may also want to whitelist outgoing connections to the http and https ports through the settings tab.

Restart moblock for the changes to take effect.

Hope I helped.

:-)

---

