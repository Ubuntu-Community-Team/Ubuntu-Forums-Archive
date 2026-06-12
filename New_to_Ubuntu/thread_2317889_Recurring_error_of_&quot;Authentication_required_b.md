---
title: "Recurring error of &quot;Authentication required by Wi-Fi Network&quot;"
date: 2016-03-21
forum: New to Ubuntu
---

### Post by FatFluffyBunny on 2016-03-21
I've just installed Ubuntu 14.10 on my Lenovo laptop and encoutered problem using Wif. I can't connect to the internet via wireless capability but I can go online with internet cable. 
Whenever I click on the Wifi name i want to connect, this error appears. I typed in the correct password but this error message keeps coming back. 
I've tried searching online for solutions but I discovered other problems when fixing it. For example, when i want to install ndiswrapper, it would says that the computer unable to locate. I've also noticed that sudo apt-get update doesn't seem to work because it "failed to fetch..." and "error 404". 
Please help. Thanks.

---

### Post by howefield on 2016-03-21
First thing to do would be to use a supported version of Ubuntu, either the Long Term Supported 14.04 or the current interim 15.10. 14.10 is well past its end of life.

Next thing would be to read the sticky [here]("http://ubuntuforums.org/showthread.php?t=370108") and run the "*wireless info script*" which you post back here.

---

### Post by grahammechanical on 2016-03-21
> I typed in the correct password but this error message keeps coming back.

That message is not an error message but an authentication request. The password is not our Ubuntu user password but the router's passphrase. It is also called wireless key & WPA-PSK key. If you look on the base of the router you may find a sticker with the information that you need.

Also, the "404 Failed to fetch" error message is what we get if a URL is incorrect. And you are getting it because each version of Ubuntu has its own set of software repositories. When a version reaches the end of its support period the repositories for that version of Ubuntu are closed. And that is the situation with Ubuntu 14.10. End of life July 23rd 2015.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The closure of those repositories is also the reason for the "cannot locate" error message when you try to install ndiswrapper. Which, by the way, you do not need as Ubuntu already has a driver for the WiFi adapter. If Ubuntu was not activating the WiFi adapter you would not be being seeing any WiFi access points. You would not be able to attempt to connect to the router. Which you are able to do because the router is requiring authentication for the connection.

 So, there is wireless transmission and receiving between Ubuntu and the router. That would not be happening if the WiFi adapter was not working because the OS did not have a driver for it.

Regards

---

