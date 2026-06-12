---
title: "can't connect to wifi on ubuntu 12.10"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by akuripin on 2013-04-18
Ive recently installed ubuntu on my pc. the problem is, i can't connect to my home wifi on ubuntu. i'm running ubuntu 12.10 now and i absolutely dont know how to fix this. my laptop use a broadcomm adapter. somebody please help me... :(

---

### Post by Impavidus on 2013-04-18
You may need a proprietary driver for that wifi hardware. Get a wired connection, go to additional drivers and they can be downloaded and installed automatically.

---

### Post by akuripin on 2013-04-18
> **Impavidus said:**
> You may need a proprietary driver for that wifi hardware. Get a wired connection, go to additional drivers and they can be downloaded and installed automatically.

thanx. but where can i find the additional driver? is it in the terminal or in the application part?

---

### Post by vishal goyal on 2013-04-18
find it here: System>Administration>Additional Drivers

---

### Post by DuckHook on 2013-04-18
Hi and welcome to the forums and to Ubuntu.

I swear that trouble comes in bunches. You are the fourth WIFI issue this week, which hopefully means that the solution is fresh in our minds :)

Broadcoms are known to be finicky. Please open up a terminal and do:```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```This will download a script, run it, and produce a file on your current directory (usually desktop) that generates a report stripped of personally identifiable info (like your MAC address). Please attach this report to your reply using the paperclip icon in the reply toolbar. It will tell us what broadcom chip you have as well as a wealth of other info that we can use to track down drivers, settings and configurations.

---

### Post by akuripin on 2013-04-18
> **vishal goyal said:**
> find it here: System>Administration>Additional Drivers

okay..i cant find system>administration>additional driver.. is it system setting? i also cant find that in system setting..

---

### Post by akuripin on 2013-04-18
> **DuckHook said:**
> Hi and welcome to the forums and to Ubuntu.

I swear that trouble comes in bunches. You are the fourth WIFI issue this week, which hopefully means that the solution is fresh in our minds :)

Broadcoms are known to be finicky. Please open up a terminal and do:```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```This will download a script, run it, and produce a file on your current directory (usually desktop) that generates a report stripped of personally identifiable info (like your MAC address). Please attach this report to your reply using the paperclip icon in the reply toolbar. It will tell us what broadcom chip you have as well as a wealth of other info that we can use to track down drivers, settings and configurations.

is this the report?

---

### Post by DuckHook on 2013-04-18
Yes, this is the right report. It shows that you are already using the correct driver, so no need to install another.

Please describe in detail how you tried to connect to your home router:

1. What security protocol is your router? Try setting it to WPA2-Personal or WPA2-AES
2. Did you try connecting through Network Manager?
3. Did you doublecheck to make sure your encryption key is accurate?

---

### Post by akuripin on 2013-04-18
> **DuckHook said:**
> Yes, this is the right report. It shows that you are already using the correct driver, so no need to install another.

Please describe in detail how you tried to connect to your home router:

1. What security protocol is your router? Try setting it to WPA2-Personal or WPA2-AES
2. Did you try connecting through Network Manager?
3. Did you doublecheck to make sure your encryption key is accurate?

WEP protocol. where can i find the network manager? yes i double checked the encryption key..

---

### Post by DuckHook on 2013-04-18
Network Manager is available on the top right of your global menu bar. It is the little icon with the up and down arrows. If you click on the icon, it will open a drop-down box. Make sure "Enable Wireless" is checked, then: Edit Connections...> Wireless

If your SSID already appears then: Select it > Edit > Make sure SSID is correct (case matters in Linux), Mode : Infrastructure > IP4 Settings > Method: Automatic (DHCP) > Wireless Security > Select WPA & WPA2 Personal > [Type in encryption key/passphrase] (remember: case matters) > Save

If not, then: > Add > [Type in your SSID], Mode: Infrastructure > IP4 Settings > Method: Automatic (DHCP) > Wireless Security > Select WPA & WPA2 Personal > [Type in encryption key/passphrase] > Save

If wireless does not come on, reboot your computer.

For above to work, you must have already set your router to WPA2 Personal AES, proper encryption key, saved, then rebooted your router.

<edit>

WEP protocol is the worst protocol in creation and can be broken literally in a few minutes. It lulls you into a false illusion of security while offering none at all. Use WPA2 personal with a good encryption phrase of at least 30 characters, mix of letters and numbers.

</edit>

---

### Post by Chase993 on 2013-04-18
Since Ubuntu 12.10 is the newest release it still has more bugs then its lts release. Unless you really need to upgrade. I suggest you back everything up you need and install Ubuntu 12.04 LTS. I'm sure all your drivers will be working out of the box =)

---

### Post by akuripin on 2013-04-18
> **DuckHook said:**
> Network Manager is available on the top right of your global menu bar. It is the little icon with the up and down arrows. If you click on the icon, it will open a drop-down box. Make sure "Enable Wireless" is checked, then: Edit Connections...> Wireless

If your SSID already appears then: Select it > Edit > Make sure SSID is correct (case matters in Linux), Mode : Infrastructure > IP4 Settings > Method: Automatic (DHCP) > Wireless Security > Select WPA & WPA2 Personal > [Type in encryption key/passphrase] (remember: case matters) > Save

If not, then: > Add > [Type in your SSID], Mode: Infrastructure > IP4 Settings > Method: Automatic (DHCP) > Wireless Security > Select WPA & WPA2 Personal > [Type in encryption key/passphrase] > Save

If wireless does not come on, reboot your computer.

For above to work, you must have already set your router to WPA2 Personal AES, proper encryption key, saved, then rebooted your router.

<edit>

WEP protocol is the worst protocol in creation and can be broken literally in a few minutes. It lulls you into a false illusion of security while offering none at all. Use WPA2 personal with a good encryption phrase of at least 30 characters, mix of letters and numbers.

</edit>

okay..i tried and it works!. thanks a lot for helping me...couldn't be happy more!! :D  thanks a lot guys!

---

### Post by DuckHook on 2013-04-18
Please mark thread [solved] (only OP can do so).

Good luck and happy Ubuntuing!

---

### Post by akuripin on 2013-04-18
> **DuckHook said:**
> Please mark thread [solved] (only OP can do so).

Good luck and happy Ubuntuing!

OKay.. Thanks a lot again. :)

---

### Post by akuripin on 2013-04-18
Thread solved.

---

### Post by DuckHook on 2013-04-18
The old way for doing this is not yet fixed. Please see this link.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by akuripin on 2013-04-18
> **DuckHook said:**
> The old way for doing this is not yet fixed. Please see this link.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

:)

---

