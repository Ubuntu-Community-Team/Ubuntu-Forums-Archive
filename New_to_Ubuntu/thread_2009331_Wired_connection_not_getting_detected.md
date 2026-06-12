---
title: "Wired connection not getting detected"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Nikki5 on 2012-06-24
My wired connection is not getting detected in ubuntu 10.04.On trying the command :sudo dhclient eth0 something like this comes in the end:

No DHCP offers received
Ping statistics:	
1 packets transmitted,0 received, +1errors,100% packet loss, time 0ms
No working leases in persistent database - sleeping

I also tried: Choose edit connections eth0 and check Automatic DHCP.It is automatic.Any sort of help would be greatly appreciated.thanks in advance

---

### Post by sudodus on 2012-06-24
Wired connection is something that works almost all the time. Could the problem be related to hardware or software?

Did it work before, and now it has stopped working? What could have caused it (did you do something at the same time)? Could there have been a high voltage spike from the power network or phone network?

Can you test if it works when you boot a live session from an Ubuntu CD or USB drive?

---

### Post by Nikki5 on 2012-06-27
@sudodus yes actually i had installed ubuntu 12.04 before and my wired network was working properly at that time.but now i have uninstalled 12.04 and installed 10.04 and suddenly it shows wired network disconnected.

---

### Post by sudodus on 2012-06-27
Can you test if it works when you boot a live session from an Ubuntu CD or USB drive?

---

### Post by Nikki5 on 2012-06-27
yes i just tested it's not working then also.although it doesn't show network disconnected but when i open a particular site say google it says "can't find server at google.com" whereas on my windows XP net is working perfectly  fine.

---

### Post by sudodus on 2012-06-27
Did you run Ubuntu 12.04 or 10.04 live?

As I understand it, you had internet with 12.04 but not 10.04 when installed. Furthermore, is Windows XP ***on the same machine***?

If it doesn't work with any operating system on the same machine, I would suspect the hardware is bad (anything from a wire or electric connection to some electronic component).

If the wired network only works with Windows XP, probably the hardware is not compatible with Ubuntu. But this is very seldom the case.

If the problem is only related to 10.04, try again with 12.04, but ***test various flavours live*** before installing: Kubuntu, Lubuntu, Xubuntu and Ubuntu.

---

### Post by cortman on 2012-06-27
I'm curious what the output of

```
lspci
```

and

```
lspci -k
```

and

```
ifconfig
```

would be.

---

### Post by gordintoronto on 2012-06-27
It sounds like you are trying to use an old operating system on a new computer. The Ethernet port on my computer won't work with Ubuntu 10.04, but I have not used 10.04 for about 20 months.

If you didn't like Ubuntu 12.04, there are alternatives: Xubuntu, Lubuntu, Linux Mint with Cinnamon.

---

### Post by Nikki5 on 2012-06-28
@gordintoronto how do i test whether my computer is new for 10.04?I need 10.04 as it is compatible with work m focussing on.12.04 is not so i have no option but to use 10.04

---

### Post by Nikki5 on 2012-06-28
@sudodus yes windows xp and ubuntu are on same machine.right now my internet works on windows xp and it was also working with 12.04.the problem only started when i installed 10.04.Using a LIVE CD of 10.04 internet was not working.can u please tell me how to test whether the hardware is compatible with ubuntu?

---

### Post by Nikki5 on 2012-06-28
@cortman: can u please tell me how to copy the output of commands you told me from terminal.I tried by selecting the whole thing and then right clicking but the things selected get deselected.please excuse my ignorance but i am new to ubuntu.

---

### Post by cortman on 2012-06-28
> **Nikki5 said:**
> @cortman: can u please tell me how to copy the output of commands you told me from terminal.I tried by selecting the whole thing and then right clicking but the things selected get deselected.please excuse my ignorance but i am new to ubuntu.

Selecting and right click>copy should work- be sure you're right clicking on the selected text itself.

---

### Post by sudodus on 2012-06-28
> **Nikki5 said:**
> @sudodus yes windows xp and ubuntu are on same machine.right now my internet works on windows xp and it was also working with 12.04.the problem only started when i installed 10.04.Using a LIVE CD of 10.04 internet was not working.can u please tell me how to test whether the hardware is compatible with ubuntu?
I think you have done that test now, and the result is that the hardware is compatible with ubuntu 12.04 but not with 10.04.

     -o-

Why and how do you need 10.04? How is it compatible with work you are focusing on and how is 12.04 not so? Maybe there is a way to do what you need with 12.04.

---

### Post by wildmanne39 on 2012-06-28
Hi, I imagine you have an Atheros AR8151 or AR8152 ethernet adapter that does not come with the driver in 10.04 but can be installed if you have a wireless connection that is working, to confirm this please post the information that cortman asked for.
Thanks

---

### Post by Nikki5 on 2012-06-29
@wildmanne39 My ethernet adapter is: Realtek Rtl-8139d PCI Fast Ethernet adapter.sorry but i am not able to paste here the o/p of commands cortman mentioned as i am not able to copy from the terminal.I am selecting and doing right click>copy  on the selected text.But as i mentioned before the selected text gets deselected.However,if i just select the text and do shift+insert on terminal itself the o/p of the commands gets pasted but on gedit it does not.Thanks in advance

---

### Post by gordintoronto on 2012-06-29
> **Nikki5 said:**
> @gordintoronto how do i test whether my computer is new for 10.04?I need 10.04 as it is compatible with work m focussing on.12.04 is not so i have no option but to use 10.04

Open Accessories/Terminal and type this command:
lspci

It should produce about a dozen lines of output. One of them should look something like this:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

In fact, it might look exactly like that. The interesting line will include "Ethernet controller" and will not include "802."

On my system, "RTL8111" identifies the hardware device. I would then Google:
RTL8111 ubuntu solved
and expect to find a useful result.

Oops, you have made some progress. Have a look at this message thread:
[http://ubuntuforums.org/showthread.php?t=1537889&page=3](http://ubuntuforums.org/showthread.php?t=1537889&page=3)

---

### Post by Nikki5 on 2012-06-29
@gordintoronto I get something like this with the command lspci: 01:00.0 Ethernet Controller:Hangzhou Silan Microelectronics Co., Ltd. SC92031 PCI Fast Ethernet Adapter (rev 01)
01:01.0 Multimedia Controller: Philips Semiconductors SAA7130 Video Broadcast Decoder(rev 01)
with lspci -k i get this in addition:
Kernel driver in use:sc92031
Kernel Modules:sc92031
Kernel Modules:saa7134
and in /etc/network/interfaces:
auto lo
iface lo inet loopback

---

### Post by gordintoronto on 2012-06-29
Previously you said, "My ethernet adapter is: Realtek Rtl-8139d PCI Fast Ethernet adapter..." Now it looks like you have an SC92031.

I think there was a suggestion that you should abandon 10.04 and concentrate on using 12.04 (or Linux Mint 13). I think that was a great suggestion.

---

### Post by wildmanne39 on 2012-06-29
Hi, that is a very strange one indeed, please post the results of:
```
lspci -nnk | grep -iA2 net
```
There is information that we need to see so please post the whole output.
Thanks

---

### Post by Nikki5 on 2012-06-30
@wildmanne39 This is what i get with command:lspci -nnk | grep -iA2 net: 
 01:00.0 Ethernet controller [0200]: Hangzhou Silan Microelectronics Co., Ltd. SC92031 PCI Fast Ethernet Adapter [1904:2031] (rev 01) 
	Kernel driver in use: sc92031 
	Kernel modules: sc92031

---

### Post by Nikki5 on 2012-06-30
@gordintoronto I have to use 10.04 coz it's compatible with 32-bit machine for building android source code while 12.04 is not.

---

### Post by Nikki5 on 2012-06-30
Thanks all of you.My problem is solved now.I referred the site:[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/94038](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/94038). I had the same problem.But now the only problem is that my net on ubuntu is working too slow as compared to that on windowsXP.

---

### Post by wildmanne39 on 2012-06-30
Hi go into network manager settings and change your wired settings to match the settings in the screenshots they are of wireless settings but they apply to wired as well.
Thanks

---

### Post by Nikki5 on 2012-07-01
@[[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533") Thank o so much!!Your screenshots solved my little remaining problem.Thanks a lot!!:):)

---

### Post by wildmanne39 on 2012-07-01
Hi, your welcome! glad the issue is resolved.
Enjoy

---

### Post by Nikki5 on 2012-07-03
Hi my internet connection is again gone.It was working perfectly fine yesterday and as i was downloading something in the middle of that my net stopped working.Unlike before when in internet manager above it used to say wired network disconnected,now it says CONNECTION ESTABLISHED(shows 2 arrows) but when i open firefox it says "Can't find server at ....com".Please help me.Do i need an Internet download manager?

---

### Post by Nikki5 on 2012-07-03
Also as i was downloading java5 so i added a line in sources.list file.Does that create a problem?but after inserting that line my internet worked for quite a long time.please help me!!I am really frustrated with ubuntu now:(

---

### Post by sudodus on 2012-07-03
> **Nikki5 said:**
> @gordintoronto I have to use 10.04 coz it's compatible with 32-bit machine for building android source code while 12.04 is not.

> **Nikki5 said:**
> Also as i was downloading java5 so i added a line in sources.list file.Does that create a problem?but after inserting that line my internet worked for quite a long time.please help me!!I am really frustrated with ubuntu now:(

This is my suggestion now: Have both versions installed ;-)

* Run 10.04 for building android source code, and

* Install 12.04 and run it for most other tasks including internet access.

I hope there is space enough on your hard drive for that.

---

### Post by wildmanne39 on 2012-07-03
Hi, try:
```
sudo modprobe sc92031
```
does it come on?
Thanks

---

### Post by Nikki5 on 2012-07-04
Hi,Thanks.
I dont know how but my net on ubuntu has started working.I wonder how these miracles happen:):)

---

### Post by wildmanne39 on 2012-07-04
Hi, I imagine it is the last command I gave you to run, if it started working after that command was performed you may need to make it permanent by doing:
```
sudo su 
echo sc92031 >> /etc/modules 
exit
```
Thanks

---

### Post by Nikki5 on 2012-07-04
@wildmanne39 Thanks i'l run these commands.But my net started working itself.I didn't run any command.when i started ubuntu net was there.but now again it's gone.I am really not understanding the problem...
Actually i am downloading android source code and it takes a lot of time to download but everytime the net goes in between.I'll be really thankful to you if you can help me with this.

And also is there a way so that i save whatever has been downloaded from the terminal coz it's the 3rd time that my net has gone while download is taking place.Eagerly waiting for your reply!Thanks in advance!!

---

### Post by sudodus on 2012-07-04
If your computer is powerful enough, you can install Ubuntu 12.04 as the main operating system. Then install Oracle VirtualBox (from Oracle's web site, and install Ubuntu 10.04 in a virtual machine. That way 12.04 will make it possible to connect to the internet and 10.04 will connect via its host system.

And you can have internet connection and run your special software at the same time.

Now in order to decide if this is a feasible option, please post the specs of your computer or at least

- CPU, RAM, graphics card

---

### Post by wildmanne39 on 2012-07-04
+1 that is a great idea sudodus.

---

### Post by Nikki5 on 2012-07-05
Thanks sudodus and wildmanne39  for your suggestions.I'll definitely do that in case my problem persists for very long.But right now again my net is back:):)Can u please help me with this:
I had put my computer on hibernate mode coz my internet connection had  stopped while download was taking place.Now the internet is working.How  do i check whether it is downloading?Or do i have to do something to  resume the download process?

---

### Post by wildmanne39 on 2012-07-05
Hi, you will need to start the download again if it was interrupted, unless it is being downloaded with a download manager like in firefox and if the internet goes down while updating you should run.
```
sudo apt-get autoclean
sudo apt-get clean
```
Thanks

---

### Post by Nikki5 on 2012-07-09
Thanks
Does anyone know about what to do with following error while downloading android source code?
error: RPC failed; result=52, HTTP code=0

---

