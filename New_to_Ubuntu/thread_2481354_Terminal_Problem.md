---
title: "Terminal Problem"
date: 2022-11-27
forum: New to Ubuntu
---

### Post by pussekatt on 2022-11-27
I can type certain commands into the termanal,like eject but when I try to type Iscpu it asks for my password but I cant enter anything.I get the blinking cursor but when I type nothing goes on screen.What am I doing wrong ?

---

### Post by ajgreeny on 2022-11-27
Absolutely nothing wrong!

When you type the user password in terminal it is never echoed on the screen, not even as asterisks or any other character, so just type it carefully and hit Enter.
Assuming you typed it correctly it will be entered and will work.

PS.
The command **lscpu** does not request my password so I do not understand why you are asked for yours

---

### Post by coley9225 on 2022-11-27
Hello. You are not doing anything wrong, it does that for security reasons. When you type you password, the terminal is 'reading' your input but will not show anything on the screen. Just type your password and hit enter, and it will run the commands without any issues. Hope this helps.

---

### Post by oldos2er on 2022-11-27
An oldie but goodie: [https://www.psychocats.net/ubuntu/passwordinterminal](https://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by mIk3_08 on 2022-11-28
> **pussekatt said:**
> I can type certain commands into the termanal,like eject but when I try to type Iscpu it asks for my password but I cant enter anything.I get the blinking cursor but when I type nothing goes on screen.What am I doing wrong ?

> **ajgreeny said:**
> Absolutely nothing wrong!
When you type the user password in terminal it is never echoed on the  screen, not even as asterisks or any other character, so just type it  carefully and hit Enter.

ajgreeny is exactly right. Theirs nothing wrong with it. When typing a password on terminal you can't see any character on the terminal and that is perfectly normal. Regards and cheers.

---

### Post by yetimon_64 on 2022-11-28
> **oldos2er said:**
> An oldie but goodie: [https://www.psychocats.net/ubuntu/passwordinterminal](https://www.psychocats.net/ubuntu/passwordinterminal)

The conclusions in that posting from 2012 or possibly earlier were probably valid then. However [[COLOR=#0000ff]--this link--[/COLOR]]("https://ubuntuhandbook.org/index.php/2014/08/ubuntu-display-asterisks-when-typing-password-terminal/") from [noparse]ubuntuhandbook.org[/noparse] from around 2014 is how I used to enable password feedback in the terminal.

I used that technique for a few years around 2015 to 2018 until I read how at the time on certain kernel versions enabling the feedback could possibly introduce a security vulnerability. As a result of reading about that possible vulnerability I stopped enabling it. It has been a long time since I used that technique and I don't know how to check if enabling password feedback is still a potential problem.

Unless someone here can confirm there is no security risk involved nowadays I **DO NOT** recommend enabling password feedback, this post is only to inform users it is possible but DOES contain some risks.

As per ajgreeny's post ...
> ...The command lscpu does not request my password so I do not understand why you are asked for yours ...
I get the same result, no password is needed for that command here as well.

---

### Post by pussekatt on 2022-11-28
Thanks guys.As I am new to Ubuntu I cant recall when/why it asked me for my password.Anyway I typed iscpu again and recieved this reply:
command Iscpu not found,did you mean command Iscpu from deb- Linux 2.34 - 0 1ubuntu9.3)
try sudo apt install deb name.

I am completely lost now.I havent a clue what the PC is talking about.What I am trying to do is find out if my laptop supports visualization ( I want to run Oracle Virtual box) Is the Iscpu command a capital I

---

### Post by The Cog on 2022-11-28
It's a lower-case L:
```
lscpu
```
ls is short for list: lscpu, lspci (PCI cards), lsusb (USB things), lshw (hardware), and just ls lists the files in the current directory.

---

### Post by TheFu on 2022-11-28
> **pussekatt said:**
> Thanks guys.As I am new to Ubuntu I cant recall when/why it asked me for my password.Anyway I typed iscpu again and recieved this reply:
command Iscpu not found,did you mean command Iscpu from deb- Linux 2.34 - 0 1ubuntu9.3)
try sudo apt install deb name.

I am completely lost now.I havent a clue what the PC is talking about.What I am trying to do is find out if my laptop supports visualization ( I want to run Oracle Virtual box) Is the Iscpu command a capital I

All files, directories and commands are case-sensitive on Unix systems.
I haven't used virtualbox in some time, but there are 2 types of hardware virtualization support - Intel's VT-x and AMD's AMD-V.
I've never used the lscpu command, but there are specific tools just for this:
```
$ egrep -oE  'vmx|svm'   /proc/cpuinfo
```
if anything is returned, then either Intel's or AMD's virtualization support is enabled.  If not and the CPU is capable of that feature, check the BIOS settings have SVM or VT-x enabled.

BTW, virtualbox only needs trhose CPU capabilities to run 64-bit OSes.  For 32-bit OSes, the software emulation is fast, usually faster than the hardware context switching.

---

### Post by pussekatt on 2022-11-30
I typed in egrep etc and got "command not found"
what does that mean and what do I do now ?
If its any help,I am using a Lenovo G40 laptop that had Windows 8.1 installed.

---

### Post by TheFu on 2022-11-30
Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
If 'egrep' doesn't exist, something really bad happened to the system, but there isn't enough information to troubleshoot for me.  Or you didn't input spaces between each part of the command as show.

Perhaps someone else can help?

---

### Post by pussekatt on 2022-12-03
I found out ( by accident ) that I do have virtualization but it is turned off.In very small writing at the top of the screen it says "vmx (outside txt ) disabled by BIOS".Is there a way to a access the BIOS from the terminal because I cant get into my BIOS.I have tried various keys,F1/F2 etc but no luck.

---

### Post by tea for one on 2022-12-03
> **pussekatt said:**
> Is there a way to a access the BIOS from the terminal
Try this terminal command:-
```
sudo systemctl reboot --firmware-setup
```

---

### Post by TheFu on 2022-12-03
> **pussekatt said:**
> I found out ( by accident ) that I do have virtualization but it is turned off.In very small writing at the top of the screen it says "vmx (outside txt ) disabled by BIOS".Is there a way to a access the BIOS from the terminal because I cant get into my BIOS.I have tried various keys,F1/F2 etc but no luck.

Not to my knowledge.  You'll need to find the motherboard manual for how to enter the BIOS, get into it and find whatever that specific BIOS calls the hardware support for virtualization.  In my Asus B450 motherboards, it is buried deep at the bottom of a page (scrolling down is required) and called "SVM", which is NOT what I expected.  I expected something like VT-x or AMD-v to be listed, because that's what the CPU makers advertise. Sigh.

Cheap systems often don't make the hardware virtualization support setting available in the BIOS and theirs no other way to get it enabled.  Without it, you cannot run any 64-bit virtual machine and 32-bit VMs will only use software virtualization.  Ubuntu abandoned 32-bit releases on x86 platforms around 2019, so you'll need to run some other distro to does provide 32-bit releases.  Debian is the choice that comes to mind.  32-bit limits each single process to 4GB of RAM, but not the entire OS.  I don't give any of my VMs more than 4G of RAM, so that wouldn't be an issue for my needs.  Perhaps it isn't a big deal for you, unless you want to run Windows and only 64-bit releases are available.  IDK what arbitrary limitations MSFT does.  I did have a 32-bit Win7, but I also had a few 64-bit Win7 systems too.

---

### Post by pussekatt on 2022-12-04
Im not sure if I am making myself clear here.
I have a Windows 8.1 laptop that I installed Ubuntu on.The Ubuntu instilation takes up all the HDD space,except for the "Factory reset"partition.My problem is that I can press the "novo"button and I get 4 choices Boot to CD/DVD.... BIOS....Factory reset and 1 other.The trouble is that Factory reset and BIOS do nothing.The boot option works ( thats how I installed Ubuntu" I want to use this laptop to run Orical virtual box,so I ned to know if there is any other way that I can enter the BIOS and turn virtualization back on ?According to the internet I can take the cmos battery out and replace it and that will reset the BIOS but I have no idear where this is in a Lenovo G40 laptop.

---

### Post by TheFu on 2022-12-04
If you are entering the correct BIOS-entry key(s) at the appropriate times during the boot process and nothing happens, there are 4 possible answers.
a) what you are doing isn't correct. I bang on the known key about 20 times during startup to enter the BIOS.
b) the motherboard is breaking/broke.  Had a Gigabyte motherboard with this issue.  About 1 in 20 reboot attempts, I was able to get into the BIOS.
c) the keyboard isn't activated quickly enough to be seen, get a PS2 keyboard, connect it, and try again.  USB keyboards can be much delayed for being recognized, IME.
d) the BIOS is locked down, so that you cannot enter it to change anything.  This is common for enterprise laptops and desktops.

There are different keys for boot selection BIOS menu and entering the BIOS.

Until you get into the BIOS and toggle the VT-x or AMD-v support, you won't be running any Virtualbox VMs that have 64-bit OSes.  Sorry.

---

### Post by tea for one on 2022-12-05
> **pussekatt said:**
> so I ned to know if there is any other way that I can enter the BIOS and turn virtualization back on ?
What happened when you tried my suggestion in post 13?

---

### Post by pussekatt on 2022-12-05
The laptop re-started and all I got was a black screen with a very small cursor at the very top left hand corner of the screen.
As I said the BIOS worked perfectly "before I installed Ubuntu"

---

### Post by TheFu on 2022-12-05
> **tea for one said:**
> What happened when you tried my suggestion in post 13?

When I did it (had a convenient time and need to reboot a system this morning for new kernels), the result was:
```
$ sudo systemctl reboot --firmware-setup
Cannot indicate to EFI to boot into setup mode: Operation not supported
```

---

### Post by TheFu on 2022-12-05
> **pussekatt said:**
> The laptop re-started and all I got was a black screen with a very small cursor at the very top left hand corner of the screen.
As I said the BIOS worked perfectly "before I installed Ubuntu"

I know of no method that any OS can modify/harm the BIOS in the motherboard unless you have a specific tool, created for the specific BIOS, that runs under the specific OS and use that tool.  The only way that I know to update a BIOS is by down loading new firmware/bios code using **any** OS, placing that binary file onto a floppy disc or usb flash drive (FAT32 is usually required), then booting and banging on the "Enter BIOS" key, going to the "Update BIOS" tab, saying to update the BIOS from a list of devices, picking either the USB storage or floppy disc, finding the .bin file to be used, selecting it and confirming to write that file over the existing firmware of the motherboard.  As you can see, it isn't going to happen accidentally. Too many specific steps.

When I first got an Asus B450 motherboard, it came with the ability to do an internet download and install of new BIOS code and that was excellent. No need to hunt for a floppy or USB flash drive to load the firmware binary onto.  Sadly, Asus removed that direct internet update feature in a later BIOS update for some reason. Guess is was breaking some people's setups, but I don't know why.  I really was a nice capability.  Again, this update wasn't something that was started from any OS. It was started from inside the BIOS and impossible to happen accidentally.

In short, any issue getting into the BIOS on your system is likely a coincidence, not caused by Ubuntu.

---

