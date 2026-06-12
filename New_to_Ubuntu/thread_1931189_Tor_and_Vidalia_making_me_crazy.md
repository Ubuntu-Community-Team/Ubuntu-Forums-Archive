---
title: "Tor and Vidalia making me crazy"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by pchelar on 2012-02-25
Hello All,
  I just got Ubuntu installed a couple weeks ago at the urging of my wife, and now I'm getting down to the nitty-gritty of semi-securing my internet (also for my wife, who is more paranoid than I).  Anyhow, I've managed to get Vidalia and Tor installed, or so I thought.  I have the Vidalia icon in my apps and on my quick-launch tray, as well as the little onion icon at the top of the screen.  I can launch Vidalia and connect to Tor, and everything is fine.  However, when I go to the Tor website to check my tor connection, it tells me I'm NOT connected to Tor.  So thinking I've done something wrong, I download the Tor browser bundle.  The intstructions say, just download and run it, but when I open it with archive manager I unzip all the file and launch what I think is the right thing.  Low and behold after a second Vidalia connects and the Tor browser opens, with the Tor button on it and all.  When I check at the Tor website, it says I'm connected.  Everything is fine, except as soon as I close that browser window, it's like everything is forgotten.  If I reopen Firefox, it looks like it did before, no Tor button, and if I close and reopen Vidalia, it never opens a browser window and reopening Firefox keeps me Tor-less.
If anyone can tell me what I'm doing wrong and how to get my Tor-secure browser to open every time I'll be most grateful.

Many thanks

---

### Post by akareilly on 2012-03-01
Hello,
  When you close the Tor Browser, it is supposed to disappear. This feature was put in for people who are using Tor at Internet cafes in countries where circumventing censorship can get them in trouble. You can run Tor from a USB stick, and if the censors show up in person you can exit Tor and yank out the drive in a few seconds. 

 Clicking on "Start Tor" in the browser bundle should load Vidalia and the version of Firefox configured to send traffic through Tor. 

Loading your non-Tor Firefox will not work. Loading just Vidalia will not work. You can download all the bits of Tor separately, but it is not recommended since Torbutton does a lot of things to thwart browser fingerprinting and potentially malicious plugins.  

You got it right when you used the Tor Browser Bundle (TBB), and the disappearing act is on purpose. It's possible that there is something buggy going on, but if you can repeat the process of using TBB, you should be good to go.

---

### Post by youngunix on 2012-03-04
> **pchelar said:**
> Hello All,
  I just got Ubuntu installed a couple weeks ago at the urging of my wife, and now I'm getting down to the nitty-gritty of semi-securing my internet (also for my wife, who is more paranoid than I).  Anyhow, I've managed to get Vidalia and Tor installed, or so I thought.  I have the Vidalia icon in my apps and on my quick-launch tray, as well as the little onion icon at the top of the screen.  I can launch Vidalia and connect to Tor, and everything is fine.  However, when I go to the Tor website to check my tor connection, it tells me I'm NOT connected to Tor.  So thinking I've done something wrong, I download the Tor browser bundle.  The intstructions say, just download and run it, but when I open it with archive manager I unzip all the file and launch what I think is the right thing.  Low and behold after a second Vidalia connects and the Tor browser opens, with the Tor button on it and all.  When I check at the Tor website, it says I'm connected.  Everything is fine, except as soon as I close that browser window, it's like everything is forgotten.  If I reopen Firefox, it looks like it did before, no Tor button, and if I close and reopen Vidalia, it never opens a browser window and reopening Firefox keeps me Tor-less.
If anyone can tell me what I'm doing wrong and how to get my Tor-secure browser to open every time I'll be most grateful.

Many thanks

If you have downloaded Tor from the Ubuntu Software Center, you most likely got the obsolete version.
First, forget about the bundle you got.
2nd, remove Tor and Vidalia that you downloaded from "U.S.C".
3rd, you need to do the following to install Tor and Vidalia:

Open the Terminal (Ctrl+alt+t), type ```
sudo -i 
``` this drops you to root environment, so you don't have to be entering your password every few seconds...
Now, you need to edit your source list: ```
gedit /etc/apt/sources.list
``` once you get the file up, go to the end (or where you want to add this source) and enter: ```
deb     http://deb.torproject.org/torproject.org oneiric main
``` save and close.
Still in Terminal, type:  ```
gpg --keyserver keys.gnupg.net --recv 886DDD89
``` ```
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```  ```
apt-get install deb.torproject.org-keyring
``` ```
apt-get update
``` Finaly: ```
apt-get install tor
```For Vidalia, type: ```
apt-get install vidalia deb.torproject.org-keyring
```To set up Tor to work with your browser (firefox): 
go to **Edit**-->**Preferences**-->**Advanced**-->**Network** tab-->under "**Connection**"-->click on "**Settings**"-->select "**Manual Proxy Configuration**"-->go down to "**SOCKS Host**"-->type "**127.0.0.1**"-->**Port** "**9050**"-->"**No Proxy For**" should have "**localhost, 127.0.0.1**".

I hope this helps.

---

