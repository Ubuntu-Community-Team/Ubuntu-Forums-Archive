---
title: "Gnome, ui problems"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by LouisChappell on 2012-02-25
I decided to give ubuntu another chance after 4 years. It's come a long way!
Basically, I want to use the gnome-shell UI, I downloaded and installed it through the terminal along with gnome tweak tool. I logged out and logged back in with gnome and many letters are missing, for example in the time/date bar as well as where you logout/shutdown. On top of that when you go anywhere near the dash home it pops up, and you can't click the top bar with file etc on. I'm on the latast version of ubuntu if that helps!
Thanks, Louis.

---

### Post by Frogs Hair on 2012-02-25
When you move the mouse to the top left the overview is activated  and bottom right activates the indicator panel. I don't what is meant by missing letters . From advanced settings > shell the date can be added the clock . 

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)


Allow scripts on this page .[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by winh8r on 2012-02-25
Have a look here:


[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")


hopr this helps

---

### Post by LouisChappell on 2012-02-26
Thanks for the replies, but I don't think you understand what I mean. 
Is there a way to take a real screenshot? When I take a screenshot it just takes a picture of my background... 
I wish to have the new gnome setup, gnome classic setting seems to work quite well. The new gnome has letters missing here and there and it isn't laid out correctly on my screen.
Thanks, Louis.

---

### Post by LouisChappell on 2012-02-26
The normal screenshot didn't work so took some with a camera. Sorry for the poor quality, screens are hard to take photographs of!

Firstly there is a gap between the wallpaper and the menu bar, no big problem though really.
As you can see, there is a rounded edge at the top left (and riht) of the wallpaper but under the menu bar, no idea what whis is.
You can see that the overview menu or side bar is overlapping the file, edit buttons, so you cannot press them.
I have enabled the time and date but they are just blocks, sometimes green sometimes black.
The logout etc menu is just crazy.

Thanks in advance.

---

### Post by kurt18947 on 2012-02-26
I'm not expert but I wonder if your machine's video system is up to the task.  What happens when you select "Ubuntu" from the logon menu?  If your display defaults to gnome-classic or Ubuntu 2D, I doubt you'll be able to use Gnome(shell).  If you want to use an up-to-date distro that's less demanding of system resources, you might create LiveCDs/LiveUSBs of Xubuntu or Lubuntu.  You can also add Xfce4 or LXDE to an Ubuntu install and choose one of those on logon. I don't know if that would help your display issue or not.

---

### Post by 23dornot23d on 2012-02-26
What graphics card is it that you use ..

 ..... there were some problems like this using ATI graphics cards

---

### Post by Bobhuber on 2012-02-26
> **LouisChappell said:**
> I decided to give ubuntu another chance after 4 years. It's come a long way!
Basically, I want to use the gnome-shell UI, I downloaded and installed it through the terminal along with gnome tweak tool. I logged out and logged back in with gnome and many letters are missing, for example in the time/date bar as well as where you logout/shutdown. On top of that when you go anywhere near the dash home it pops up, and you can't click the top bar with file etc on. I'm on the latast version of ubuntu if that helps!
Thanks, Louis.
Yes I've seen exactly what you are talking about (specificaly missing letters in the date) only not quite as bad as your examples.
Usually reloading the shell ALT+ F2 + r will solve it. You didn't give any info on your computer or graphics card but reloading or updating drivers might help if it's a persistent problem. Also make sure your extensions and the tweak tool are coming from the web8 PPA and not the ricotz testing PPA.

---

### Post by LouisChappell on 2012-02-26
It's a decent machine, should have no problems. It is indeed an ATI card, perhaps this is why it's a bit wild. I can't remember the name of the card off the top of my head, but it's 512mb and passive cooling. 
The driver I'm using is the system default: 
ATI/AMD proprietary FGLRX graphics driver.
It seems to run warcraft fine on ultra settings in opengl through wine (don't flame me hehe) so I think it should be fine.
ALT+F2+R doesn't work either.
I have no idea of how to select either web8 PPA or the ricotz testing PPA.
I'll try to find a more up-to-date driver for now, if you have any other suggestions please let me know.
Thanks for all the helpful replies.

EDIT: the driver I'm downloading is here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
Think it's the right one, my GPU says sapphire 4670 HD 512 and it's the closest thing I could find!

---

### Post by 23dornot23d on 2012-02-26
Keep a note of the ATI driver already installed incase you need to go back to it ....


Also do this in a terminal - it will give us more info on your setup and post back please

[B]
lspci


should give results back like this ( this is mine as a example )
[/B]> 
keith@keith-Aspire-7730ZG:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[COLOR=Red]**01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)**[/COLOR]
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
keith@keith-Aspire-7730ZG:~$ 



---

### Post by LouisChappell on 2012-02-26
Cheers, I'll make sure I take note, nothing a reinstall won't fix anyway!
> l@LU:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:01.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)


Cheers.

---

### Post by 23dornot23d on 2012-02-26
Ok thats it ..... [COLOR=Blue]**Radeon HD 4670**[/COLOR]

> 
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]


I have done a few[_[COLOR=Blue]** google searches **[/COLOR]_]("https://www.google.com/search?q=Radeon+HD+4670+gnome++shell+xedgers#hl=en&sclient=psy-ab&q=radeon+hd+4670+gnome+shell+xorg+edgers&pbx=1&oq=Radeon+HD+4670+gnome++shell+xorg+ed&aq=0w&aqi=q-w1&aql=&gs_sm=1&gs_upl=30596l34500l4l35651l7l6l1l0l0l0l137l618l0.5l7l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=89c626dd8ba41db5&biw=996&bih=513")and not seeing a proper solution for this so unless
newer drivers exist - than the ones you are already using ..... then it may be best waiting
for a while .... to see if the new release fixes it .....

---

### Post by LouisChappell on 2012-02-26
Thanks for looking. I thought it would just be the 11.11 version from the website link I posted. Is that incomplete? Is the driver different to an xorg edger?
I tried to install it but it said there was a previous version already installed, so I removed the old one (that came with ubuntu 11.10) through the UI and I got the same message, I then ran: 
sudo apt-get remove --purge xserver-xorg-video-radeon 
through the terminal but the 11.11 version of the driver I used still wouldn't work.
Is it a lost cause?
Thanks again for the help!

---

### Post by 23dornot23d on 2012-02-26
Possibly at this moment in time ... 

I always do searches for [[COLOR=Blue]_solved and the graphic card model in question_[/COLOR]]("https://www.google.com/search?q=Radeon+HD+4670+solved#hl=en&sclient=psy-ab&q=Radeon+HD+4670+solved+2012&pbx=1&oq=Radeon+HD+4670+solved+2012&aq=f&aqi=&aql=&gs_sm=3&gs_upl=40217l42289l0l42502l5l5l0l0l0l0l236l715l0.4.1l5l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=89c626dd8ba41db5&biw=996&bih=513") - often if there have been issues and they are soon resolved .....

But when searching on your card [COLOR=Blue]**Radeon HD 4670**[/COLOR]

 I did not have any luck with solutions .... to this problem with Gnome-shell ......

It seems its been here for a while too .... which is odd .....

Two things come to mind ..... if its really important to get gnome-shell and good graphics
consider a Nvidia card for the future .... but be careful of the hybrids too as they are a pain at the moment to set up - ( as I just recently found ).

Time often sorts things out .... but at the moment - unless you can find someone that managed to get it working on a thread and follow their recommendations - then it may be a lost cause ..... ( as far as I can see at this moment in time ) ..... 

* ( things are changing so quickly though - next week it may be ok - who knows )

---

### Post by LouisChappell on 2012-02-26
Ok, much appreciated. I had a search before making the thread and found nothing, anywhere... (well a load of stuff I didn't think was applicable to me) sad times but never mind. 
Thanks for your time and effort everyone, I'll try another day.

Edit: Add this to a solved pile... I removed the old one, purged it, restarted then installed the new one and it worked...
Cheers for helping out everyone, it turns out I was just being a moron.

---

### Post by 23dornot23d on 2012-02-26
Good to hear .... which one are you using .... post the driver so others know please
and mark this thread as solved ....

but glad you sorted it ....

---

### Post by LouisChappell on 2012-02-27
[This is the driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

I linked it in the last page but here it is again. Think I'm still in the windows mentality...

Cheers though for being a helpful community!

---

### Post by 23dornot23d on 2012-02-27
Ok cheers - will put the title here too incase the link changes ....

[B]AMD Catalyst&#8482; Proprietary Display Driver - Linux x86 & Linux x86_64 

[/B]revision 12.1

release date  1/25/2012

---

