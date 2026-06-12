---
title: "How do I approach linux os"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Noniyobis on 2011-09-30
Im not havinf much fun wirh my linuz exp because I cant seem to use for anyrhing well. Im running two versions from pendrives and though a kernal update maybe in order, basically are linux versions needing configuration to simply use? Or should it work out of the box like say, win 7.if there are versions like that what are they and rheir requirements. Im running eeebuntu on an eee so why so many problems? How can I get the best out of linux if the operating system is more scattered than me?.

---

### Post by Rex Bouwense on 2011-09-30
I am running Ubuntu 10.04 and Lubuntu 11.04 on my Eee PC and they work out of the box or at least they are for me.  Minor problems arise but they can be solved without too much trouble.  Which versions of Ubuntu are you trying to run from flash drives?  How large are the flash drives? Did you make them persistent when you created them?

---

### Post by cariboo on 2011-09-30
Do you actually have a linux distribution installed on one of you usb devices, or are you just running a Live session from the device? 

You can do an installation to a usb device just like you can on a hard drive, I'd suggest trying that first, and keep in mind that most of what you know about running Windows, doesn't transfer to a linux distribution. Be prepared to spend some time learning how to use it.

---

### Post by Noniyobis on 2011-09-30
Ok I downloaded an iso of eeebuntu and used a universal usb installer to run it on a 2gb making it persistant by choosing 842 mb for store changes. Eeebuntu runs fine vut it cant use it bwcausw it says my atheros wireless is unclaimed would less space hwlpwd here? The other one qas done for me and its ultimate ubunt 2.8 yes alot havent heard of it. Sont know if its persistent yet how can I find out by lokking at rhe 4gbs properties? Here  if I just start wireshark it crashes or at least gets quirky. heee though theres am icon that notices my wireless connection and loses it in about four mins have to reboot to get icon because netwoek tools dont see my network. If I havw to configure it then how and why the loss of the netwoek. Could it be my isp? Id really like suggestions to resolvw an issue if this is what rhe foeum is for. Just seema to me so complicated people just dont want get into rhe nitty gritty. What is a live session? Is thar what im doing or am I eunning from a usb? I want to learn as much as I can but would like a level playing field. How can I fix something if I dont know why rits wrong? Help? Where do people do live chat for linux help. Doesnt aeem alot of people know it. It is cryptic but its unix based, rhe original tcpip os.

---

### Post by williejones on 2011-09-30
> Where do people do live chat for linux help

[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

---

### Post by jtarin on 2011-09-30
Out of curiosity is English your native language?

---

### Post by bvr421 on 2011-09-30
:popcorn:):P

---

### Post by dFlyer on 2011-09-30
I'm not sure what type of problems your having. My question to you is what do you want to use linux for. I like to remind people that linux is not windows and they shouldn't expect it to work like windows. I suggest people take it slow and have fun. When they have problems, ask for help and be specific about the problem so people can help. You should approach it like a new OS. The same way you did when you first used windows/mac or what ever OS your use to. Go slow, use google and this forum to help solve problems.

---

### Post by anewguy on 2011-10-01
See if module ath9k is loaded via lsmod.  If not, try sudo modprobe ath9k and see if your wireless works.  Keep a couple of things in mind:

- you're running with VERY limited space

- most Atheros work out of the box in the newer Ubuntu releases, but I don't know about what you are running

- you would probably be much better served to install linux as dual boot or by itself.  In addition, if you are just trying things out, then if your hardware supports it I would try something like virtualbox and run these other operating system in virtual machines instead of from a USB flash drive.  (Don't use Wubi).


Dave ;)

---

### Post by Noniyobis on 2011-10-01
Ok, thanks, will try it yes english is native language but these small keyboards make spellchicking a hassle so alot of garbled words emerge. Enough with the social engineering though, I want to use linux for its applications and other capabilities inherent like wireshark, winedoors and all rhose other goodies but again am very new to this am not pit off by command oriented os's I liked msdos alot and still use it for games. Id ask what can linux do for me rather than what I want. To connect to the internet would be nice use fireox and filezilla, and all that stuff you do on any os see media, play music overall just use it to aquire more skills in networking especially. I want to create a network of different os's and versions. Problem now is I juat cant get a simple devixe ro work its not the device its rhe os, so using linux and dealing with issues will be delt with as they arise but cant get out of the gate without a connection to see how the os behaves in a network enviro. Caught up wirh juat trying to get the wireless going. Thanks for the lsmod command will try, thats rhe type of advice I need, right to the heart of the matter. Not start a discussion regarding distros that are better than others or how well it works for you, I dont know WHAT you even do wirh linux ubuntu...

---

### Post by Noniyobis on 2011-10-01
I feel like someone gave me a deflated football and says, I know rhis is your first time playing, but Cmon!!

---

### Post by Noniyobis on 2011-10-01
I feel like I was given a deflated football and beimg asked, yea. Your the new guy but never seen such bad playing

---

### Post by wildmanne39 on 2011-10-01
Hi, I will try to help you get your wireless working, you will need a wired connection on the computer that has ubuntu.

Please run these commands in the terminal by hitting ctrl+alt+t then copy and paste the results here, please include the complete results from each command:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep -i 14e4
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
```
dmesg | egrep 'ath|firm|wlan0'
```
by clicking on new reply and click # and paste the information between the brackets.

---

