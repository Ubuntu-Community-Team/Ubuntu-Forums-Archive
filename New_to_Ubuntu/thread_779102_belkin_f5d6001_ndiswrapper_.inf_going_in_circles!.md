---
title: "belkin f5d6001? ndiswrapper? .inf? going in circles!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by alexnublet85 on 2008-05-02
Hi all,

I realise I am completely out of my element here and am on the verge of giving up as have tried everything but i can't understand any of the help.

I have a Belking F5D6001 wireless card. I have installed Hardy Heron. I have the driver for Windows...

From what I have read I need to get ndiswrapper to use the wireless driver. So I have ndiswrapper (I think) but it needs the .inf file. All I get from Belkin is an .exe file.

Everywhere just says, use ndiswrapper on the .inf file and job done, but how do I get the .inf file? I've been going in circles and have read so much info but I am a complete noob and have no idea how to even install a new program on Ubuntu (tar.gz is what now?).

I am sure I am being completely stupid but I need a real basic answer here. I have read as much as I can before tearing my hair out :(

please help, i want to spread the word of Ubuntu.

---

### Post by anewguy on 2008-05-02
I think you'll find that the .exe file is either an installer or more likely a self-extracting compressed file containing all of those files. if you tell me the name of the file and where to download it, I'll try to get the files you need for your driver to you.

It may be a little while - my social security disability came in today so I've got to pay bills.  :):)

---

### Post by alan34 on 2008-05-02
Have you tried just double clicking on the exe file should come up with a program to extract the files you want. Just in case did you go here to get the exe file

[http://www.belkin.com/support/downlo/downloaddetails.asp?download=1001&lang=1](http://www.belkin.com/support/downlo/downloaddetails.asp?download=1001&lang=1)

Here are files from there for the XP driver just double click to extract.

There is a good guide to ndiswrapper in the help (lifebuoy at the top).

---

### Post by alexnublet85 on 2008-05-02
Hey,

When I click the .exe file it just begins setup and installs it, I can't choose manual install or anything it just does it straight away. I got it from the Belkin website, Version 3. I would like (LINK!*) you but for some reason I can't load the Belkin website on my laptop. The file is called f5d6001_ver3.exe

Thanks for the file alan, I transferred it across and (here is how basic I don't understand stuff) now what? :P

Sorry to be completely useless, I'm embarrassed for myself! lol

---

### Post by anewguy on 2008-05-02
> **alan34 said:**
> Have you tried just double clicking on the exe file should come up with a program to extract the files you want. Just in case did you go here to get the exe file

[http://www.belkin.com/support/downlo/downloaddetails.asp?download=1001&lang=1](http://www.belkin.com/support/downlo/downloaddetails.asp?download=1001&lang=1)

Here are files from there for the XP driver just double click to extract.

There is a good guide to ndiswrapper in the help (lifebuoy at the top).

Thanks for picking up the files for them.  I was going to suggest trying to open the .exe file, but a lot of times I find I need to rename them to .zip files to do so, and I just didn't want to confuse them.

Again, thanks much for your help!!  :):):)

---

### Post by alexnublet85 on 2008-05-02
er,

i'm still stuck :P hehe

---

### Post by alan34 on 2008-05-02
Put the WinXp.tar file on the Desktop then go Applications - Accessories - Terminal (sorry about this) then copy and paste this line

cd Desktop

Then copy and paste

tar xvf WinXp.tar

Keep the files together you need them both. If you cant follow the guide in the help if you dont get any help tonight I will post more tomorrow.

Ps use this new file think the last one was bad sorry.

---

### Post by alexnublet85 on 2008-05-02
Thank you!

Ok so I think I got the driver installed, it says it is there, but now it says there isn't the hardware! Even though I typed the stuff in the terminal to see my hardware and it says it is there.

Also when I go into Network etc, I don't get a Wireless Network option like I had before in 6.04 (or whatever it was), just Point-to-Point connection?

Am I making this ridiculously difficult for myself?

---

### Post by alan34 on 2008-05-03
Can you open a terminal and type

ndiswrapper -l

you should get something like this, please post the result.

net8185 : driver installed
	device (10EC:8185) present

this shows that the driver is associated with the hardware. If you do not get this perhaps we have the wrong driver for the wireless card and have to try other drivers. Sometimes ndiswrapper will not work with XP drivers and trying say the windows 98 drivers will work.

Here is a list of commands that I used to install my wireless card. Is it what you did? You can always copy and paste these. (I put your file in the command).

cd tothedirectorywhere**both**yourfilesare

sudo ndiswrapper -i net6001p.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

To put nidiswrapper in the kernel 

sudo gedit /etc/modules

At the bottom of the file add, on a line on its own

ndiswrapper

save and exit then reboot the computer. Hopefully you should see your card in the Network Manager, but you may have to try other drivers to get it to work.

Good Luck

To check what chipset your wireless card is using - in a terminal enter

lspci

for a wireless pci card

lsusb

for a wireless usb

You should see your chipset somewhere there so you know what driver to use. By the way have you got the cd that came with your wireless card/usb the correct drivers will be on there - something.inf and something.sys are what you need.

---

### Post by alexnublet85 on 2008-05-04
Hi Alan, 

Thanks so much for spending time trying to help me!

Just to warn you I have been having a bit of an experiment...

So when I type ndiswrapper -| I get this:

aivw@aivw-desktop:~$ ndiswrapper -|
bel6001 : invalid driver!
net6001p : invalid driver!
netw4x32 : driver installed
w29n51 : driver installed


bel6001 is the .inf file i downloaded from another forum 
[I][http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D6001_ver_3_wireless_pci_adapter_using_ndiswrapper_for_Slackware_10_0](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D6001_ver_3_wireless_pci_adapter_using_ndiswrapper_for_Slackware_10_0)
incase that helps.[/I]
The net6001p is the file you linked WinXP earlier.
netw4x32 and w29n51 are some .inf files I found but I can't remember where I got them from now I've messed around so much! Although I assume this doesn't matter as when I go into Wireless Network Drivers I get this:

bel6001 (with big red cross over icon)
Invalid Driver!
net6001p (with big red cross over icon)
Invalid Driver!
netw4x32
Hardware present: No
w29n51
Hardware present: No

ok so this is what I get when I do lspci...
aivw@aivw-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
   (rev 80)
00:01.0 PCI Bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0b.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001
   (rev 20)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! Game Port (rev 01)
00:10.0 USB Controller: VIA Technolgies, Inc. VT82xxxxx UHCI USB 1.1 Controller
   (rev 80)
00:10.1 USB Controller: VIA Technologies.....repeat
00:10.2 USBController .... repeat
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc, VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

you can see how old my computer is from that lol!

I don't have the original CD with the driver on :/ and when I download the driver from Belkin it's just an .exe that sets it up automatically and I don't know how to explore it.

Do you need any other information?

Am I being completely retarded? lol

---

### Post by alan34 on 2008-05-05
Hello alex

It looks like none of the drivers you have installed has worked, so you might as well remove them - like this

sudo ndiswrapper -r bel6001
sudo ndiswrapper -r net6001p
sudo ndiswrapper -r netw4x32
sudo ndiswrapper -r w29n51

I put "Belkin Wireless PCI Card - F5D6001 (rev 20)" in google and it seems that your chipset might be Realtek RTL8180 which odd as it is the same chipset as my wireless card uses. I have attached a zip file from the Realtek site. Double click the file and extract the drivers.

So to try these new drivers copy and paste

cd to wherethefilesare

sudo ndiswrapper -i net8180.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

To put ndiswrapper in the kernel

sudo gedit /etc/modules

At the bottom of the file add, on a line on its own

ndiswrapper

An extra file to edit here

sudo gedit /etc/modprobe.d/blacklist

At the bottom of the file add, on a line on its own

blacklist r8180

remember ndiswrapper -l will tell you if the driver has loaded and the hardware is present

best of luck

Alan

driver site

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L)


Also have a look here

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147897](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147897)

so instead of

sudo ndiswrapper -i net8180.inf

you may have to go 

sudo ndiswrapper -d 1799:6001 net8180     (or net8180.inf) I'm not sure try both :-)

---

### Post by alexnublet85 on 2008-05-06
Hey,

Ok so I did everything you said, and just incase it matters when I typed:

sudo ndiswrapper -m

I got this:

module configuration already contains alias directive

module configuration already contains alias directive

Well I carried on and did everything you said which I assume all worked fine... except that while it says the driver is installed, it still says the hardware isn't present?

:(

[I]ok so I did some stuff in root and now it says it is there and I can begin trying to set it up! for anyone with the same problem I had to use the root commands from [http://xenodium.com/blog/?p=62](http://xenodium.com/blog/?p=62) to get the driver to recognise the card.


THANK YOU THANK YOU THANK YOU ALAN! I couldn't have done any of this without your help! :D :D :D[/I]

---

