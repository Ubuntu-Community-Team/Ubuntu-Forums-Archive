---
title: "tar.gz?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by lockerhaxor on 2008-06-30
EDIT: PLEASE GO LOOK AT LATEST POSTS. I'M CURRENTLY TRYING TO INSTALL A NETGEAR W311V3, AND EVERYTHING IS GOING WRONG. IF YOU CAN OFFER HELP TAKE A LOOK AT MY LATEST POSTS HERE.

I'm really confused, and everything I found on this made no sense. How do I install tarballs? I want to install ndiswraper, but it comes in tar.gz format, which I cannot install for whatever reason.

If you have a guide, or can just tell me how to install this, please post it here. I'm extremely comfused when it comes to this, and I rather just get it done.

Thanks,
Lockerhaxor

PS. This is 8.04 Hardy Heron if anyone needs it.

---

### Post by tamoneya on 2008-06-30
typically that means you need to compile the program from scratch:  

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by nowshining on 2008-06-30
untar it first with the incl. gui archive manger or

in

terminal

```
 
cd towhereyoudownloadedit

tar -xf filename

or

tar -xf pathtoffile_file

```

alas usually installing a tarball means u may have to compile the app., but i'm not sure tho.

---

### Post by Paqman on 2008-06-30
> **lockerhaxor said:**
> I want to install ndiswraper, but it comes in tar.gz format, which I cannot install for whatever reason.


Er, ndiswrapper is in the repos, isn't it?

---

### Post by lockerhaxor on 2008-06-30
> **Paqman said:**
> Er, ndiswrapper is in the repos, isn't it?

Not sure what repos is, but if I think I understand, it wasn't installed with the system. Idk what's going on, but you would assume that would be an included program by now. 

Thanks for the help. I'm looking through those guides. Hopefully they are better then other ones I have found.

---

### Post by Vadi on 2008-06-30
In the repos means you can install it either via Appliactions - Add/Remove, or System - Administration - Synaptic Package manager, or by clicking on this link ([click]("apt:ndisgtk")).

All 3 are way easier than installing a .tar.gz :)

---

### Post by lockerhaxor on 2008-06-30
> **Vadi said:**
> In the repos means you can install it either via Appliactions - Add/Remove, or System - Administration - Synaptic Package manager, or by clicking on this link ([click]("apt:ndisgtk")).

All 3 are way easier than installing a .tar.gz :)

Ah, I see. Yup I found it in there and that should help. Maybe I can live out my Linux life by just avoiding tar.gz's LOL. Anyway I appreciate the help, and I'll continue working on this.

I'm trying to install the drivers for my Netgear WG311v3. Hopefully this works out.

---

### Post by kansasnoob on 2008-06-30
> **Paqman said:**
> Er, ndiswrapper is in the repos, isn't it?

Yes, and it's always advisable to use programs from the repos if possible.

But otherwise:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by lockerhaxor on 2008-06-30
Wait I can't find it in the add/remove list for some reason. It says cannot find program. Err help plxthx?

Edit NVM I found it. Internet was being a butt...

---

### Post by bab1 on 2008-06-30
Applications>AddRemove or System>Administration>Synaptic

---

### Post by lockerhaxor on 2008-06-30
New problems. How do I open up a console? According to the directions I see I have to open up a console windows, but I can only find terminal.

EDIT: I know I'm a n00bzor. But I'm determined to learn Ubuntu. As soon as I get this wireless working, I can put this computer in a more practicle place, so I can learn Ubuntu faster. ^_^ Yay!

---

### Post by Sonic Reducer on 2008-06-30
> **lockerhaxor said:**
> New problems. How do I open up a console? According to the directions I see I have to open up a console windows, but I can only find terminal.

EDIT: I know I'm a n00bzor. But I'm determined to learn Ubuntu. As soon as I get this wireless working, I can put this computer in a more practicle place, so I can learn Ubuntu faster. ^_^ Yay!

the terminal is the console, console is like "command line", it's the description of the program we use. it's like saying "game" instead of "command and conquer"

the console is (by default) Applications -> Accessories -> Terminal

if you haven't already deduced it, tar.gz's are compressed folders or files, like .zip's or .rar's. the only difference is it's open source so it contains more leet.

.:EDIT:. just out of curiosity, what wireless card are you trying to install? you have to be pretty sure of the chipset before you do anything (unfortunately with linux you can't just throw the disk in and run setup.exe) if you have a RaLink RT2500 chip in your card i can walk you through the steps over AIM or MSN if you want

---

### Post by lockerhaxor on 2008-06-30
> **Sonic Reducer said:**
> the terminal is the console, console is like "command line", it's the description of the program we use. it's like saying "game" instead of "command and conquer"

the console is (by default) Applications -> Accessories -> Terminal

if you haven't already deduced it, tar.gz's are compressed folders or files, like .zip's or .rar's. the only difference is it's open source so it contains more leet.

.:EDIT:. just out of curiosity, what wireless card are you trying to install? you have to be pretty sure of the chipset before you do anything (unfortunately with linux you can't just throw the disk in and run setup.exe) if you have a RaLink RT2500 chip in your card i can walk you through the steps over AIM or MSN if you want

Hey thanks for letting me know. I'm installing a Netgear WG311v3, which according to the Ubuntu wiki is supported on Ubuntu (But through much struggle.) I'm using the guide found here: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3). So far I've gone through a mess of commands, and I think it may have worked.

EDIT: No after much trouble, this is still not working. I'm not positive what's wrong with it. It won't read as installed, and I've followed all the directions listed. Any ideas everybody? It doesn't even give me errors, it just gives me a list of commands that I can enter, none of which actually do anything.

EDIT EDIT: I never thought this would be easy, but then again I never expected every single thing to go wrong. Lemme get some error messages up.

---

### Post by lockerhaxor on 2008-06-30
```
ubuntu:~$ lspci -n
00:00.0 0600: 1039:0730 (rev 02)
00:00.1 0101: 1039:5513 (rev d0)
00:01.0 0601: 1039:0018
00:01.2 0c03: 1039:7001 (rev 07)
00:01.4 0401: 1039:7018 (rev 02)
00:02.0 0604: 1039:0001
00:0d.0 0780: 11c1:044e
00:0e.0 0300: 1002:5159
00:0f.0 0200: 10ec:8139 (rev 10)
00:10.0 0200: 11ab:1faa (rev 03)
01:00.0 0300: 1039:6300 (rev 31)
-ubuntu:~$ ndiswrapper -l wg311v3 : driver installed
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
-ubuntu:~$ ndiswrapper -a 11ab:1faa wg311v3
ls: cannot access /etc/ndiswrapper/wg311v3/: No such file or directory
driver 'wg311v3' is not installed (properly)!
-ubuntu:~$ 

```

These are my unsuccseful atempts using the link I posted above as my guide. Any suggestions anyone? If you need more info I could always get it. NOTE: I did remove my name from the code. So at certain places you will not see myname@myname. Also sorry for double posting. Just wanted code to stick out here.

---

### Post by Sonic Reducer on 2008-06-30
> **lockerhaxor said:**
> Hey thanks for letting me know. I'm installing a Netgear WG311v3, which according to the Ubuntu wiki is supported on Ubuntu (But through much struggle.) I'm using the guide found here: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3). So far I've gone through a mess of commands, and I think it may have worked.

EDIT: No after much trouble, this is still not working. I'm not positive what's wrong with it. It won't read as installed, and I've followed all the directions listed. Any ideas everybody? It doesn't even give me errors, it just gives me a list of commands that I can enter, none of which actually do anything.

one thing i did, and i don't know if it actually did anything productive, but everything worked after i did it was enter these commands in terminal:

```
sudo depmod -a
```
which handles the dependencies of modules (ndiswrapper is a module of the kernel itself). the "-a" tells it to depmod everything (instead of *depmod somethingspecific*)

```
sudo modprobe ndiswrapper
```
which will insert the ndiswrapper module into the kernel.

then you'll have to blacklist the default driver from loading and conflicting with ndiswrapper, but we'll get the that when you are ready.

once you've ran those first two commands, enter **ndiswrapper -v** to see if ndiswrapper is installed. using the -v flag tells ndiswrapper to spit out the version info, and it wouldn't have a version if it wasn't installed right?

ndisgtk is nice and everything, but i had problems with it before (it didn't delete the containing folder when i removed a driver, and i guess it thought the driver was still installed because the folder was still there). ndiswrapper is one of those apps that run best in the terminal. type "ndiswrapper" to see a list of commands for it, the ones you will need to worry about are -l (list installed drivers), -i (install specified driver), and -r (remove specified driver)

i'm sure you already have it, but since you were having difficulty with archives i trimmed out what you don't need.

ironically enough, i can't just attach an unzipped folder, so download this then right-click and choose "Extract here"

---

### Post by yipperzz on 2008-06-30
Do you have the right driver?  It's difficult the first time working with ndiswrapper.  but once you understand it, it's not too bad.  Pretty much you just want to use ndiswrapper to install the Windows driver for it.  Do you have that part already done and it's not seeing your access point?  An error message would help to troubleshoot the issue.

Edit: too slow haha.  I'll go read your screenshot now.

---

### Post by yipperzz on 2008-06-30
looks like the driver is installed.  now make sure ndiswrapper is running like Sonic mentioned.  if it is running, make sure you have a good working driver.  are you using network manager?  is it not seeing any wireless networks?

---

### Post by lockerhaxor on 2008-06-30
So it says ndiswrapper is installed, but when I try to run any of it's commands NONE of them work. Seriously, -i, or just i. -l or just l. Nothing works. Any ideas?

> **yipperzz said:**
> Do you have the right driver?  It's difficult the first time working with ndiswrapper.  but once you understand it, it's not too bad.  Pretty much you just want to use ndiswrapper to install the Windows driver for it.  Do you have that part already done and it's not seeing your access point?  An error message would help to troubleshoot the issue.

Edit: too slow haha.  I'll go read your screenshot now.

Nope I don't have the driver installed. This is a nightmare, nothing is working right lol.

---

### Post by lockerhaxor on 2008-06-30
> **yipperzz said:**
> looks like the driver is installed.  now make sure ndiswrapper is running like Sonic mentioned.  if it is running, make sure you have a good working driver.  are you using network manager?  is it not seeing any wireless networks?

If it is seeing the driver, Idk what's going on. It's not appearing anywhere.

EDIT: Not only is it not appearing, but also the lights on the card isn't working. Err, this is getting more confusing the more I chug along here.

EDIT EDIT: I extracted the Driver you provided, but I'm not sure exactly what to do here. Oh well I guess this is all part of the learning process :)

---

### Post by yipperzz on 2008-06-30
Well your output for ndiswrapper -l shows that it has the driver installed.  I would try removing that driver and seeing if the driver that Sonic posted makes any difference.  But the quickest thing to do first is try the depmod and modprobe.

---

### Post by lockerhaxor on 2008-06-30
> **yipperzz said:**
> Well your output for ndiswrapper -l shows that it has the driver installed.  I would try removing that driver and seeing if the driver that Sonic posted makes any difference.  But the quickest thing to do first is try the depmod and modprobe.

The demod and modprobe didn't actually do anything. I entered them, and they just created a new line. Didn't even ask for sudo pw. 

Also how would I go about installing the driver sonic provided me? I got so confused in the steps, I just basically made sure I copied and pasted the right things.

EDIT: So the depmod asked for the Sudo PW this time around. However the modprobe didn't do anything. Just made a new command line.

---

### Post by Sonic Reducer on 2008-06-30
> **lockerhaxor said:**
> ```
ubuntu:~$ lspci -n
00:00.0 0600: 1039:0730 (rev 02)
00:00.1 0101: 1039:5513 (rev d0)
00:01.0 0601: 1039:0018
00:01.2 0c03: 1039:7001 (rev 07)
00:01.4 0401: 1039:7018 (rev 02)
00:02.0 0604: 1039:0001
00:0d.0 0780: 11c1:044e
00:0e.0 0300: 1002:5159
00:0f.0 0200: 10ec:8139 (rev 10)
00:10.0 0200: 11ab:1faa (rev 03)
01:00.0 0300: 1039:6300 (rev 31)
-ubuntu:~$ ndiswrapper -l wg311v3 : driver installed
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' **(dangerous)**
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
-ubuntu:~$ ndiswrapper -a 11ab:1faa wg311v3
ls: cannot access /etc/ndiswrapper/wg311v3/: No such file or directory
driver 'wg311v3' is not installed (properly)!
-ubuntu:~$ 

```

These are my unsuccseful atempts using the link I posted above as my guide. Any suggestions anyone? If you need more info I could always get it. NOTE: I did remove my name from the code. So at certain places you will not see myname@myname. Also sorry for double posting. Just wanted code to stick out here.

that bolded part should have been a warning right there, you want to just to just "-i" the driver so it installs (everytime i've used it) automatically.

the "-a" flag tells your computer to sit down and shut up about the driver. it forces your computer to use this driver for that DevID, if you really wanted to muck it up you could use a keyboard driver with that command, which is a case of "not good"

try this
```
ndiswrapper -v
```
(insures ndiswrapper module is installed)

```
ndiswrapper -l
```
to see if anything is listed as installed, we want to try from a clean slate, so this is how you wipe everything

[QUOTE=Do this if the previous command lists something installed]```
ryan@ryan-desktop:~$ ndiswrapper -l
[COLOR="Red"]rt2500[/COLOR] : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
```

see the name i've colored red? thats the name for the driver on my own computer, if i wanted to remove it i would enter:

```
sudo ndiswrapper -r rt2500
```
but i don't, so i won't
[/QUOTE]

once you get something like "no drivers found" you can proceed

first make sure you're terminal is in the folder with your drivers (type "cd" then the path to the .inf file, or copy it into your home folder because thats where terminal starts in). you can find out what path your terminal is in by typing "pwd" and hitting enter, it will spit out the current path to the folder.

you're a newbie (as i once was too) so i'll customize this a bit for you

firefox by default downloads stuff to your desktop, and extracting like i told you would put the folder on your desktop as well. you'll want to navigate to where the folder is, so tell terminal to go there

```
cd "~/Desktop/WG311v3 V1.0 XP Driver"
```
your username may vary.

make sure you're at the right path by entering "pwd"

install the driver:
```
sudo ndiswrapper -i WG311v3.INF
```

then check it:
```
ndiswrapper -l
```

does it say something about an alternate drive like how mine did? remove the module. you can do this on-the-fly (i switch from my default driver to one that supports packet injection when i'm PenTesting wireless networks)

```
sudo modprobe -r whateveritsaidisanalternate
```

thats enough for now, i don't want to give you all the directions at once. lets do a little bit with frequent updates so we can help you with whatever step you get stuck at (that, and i also need to go make another fajita =] )

also, you were mentioning that it didn't ask for sudo when you entered the commands before, thats most likely because you entered your sudo password recently. once you enter it you'll be cool for another 15 minutes or so. the same works with admin programs. open synaptic package manager then exit, try again in a few minutes and you won't have to enter your password

.:EDIT:. added a tilde to simplify things for him

---

### Post by lockerhaxor on 2008-06-30
```
name@name-ubuntu:~$ cd "name/Desktop/WG311v3 V1.0 XP Driver"
bash: cd: name/Desktop/WG311v3 V1.0 XP Driver: No such file or directory
name@name-ubuntu:~$ cd name/Desktop/WG311v3 V1.0 XP Driver
bash: cd: name/Desktop/WG311v3: No such file or directory
name@name-ubuntu:~$ pwd
/home/name
name@name-ubuntu:~$ cd cd "name@name/Desktop/WG311v3 V1.0 XP Driver"
bash: cd: cd: No such file or directory
name@name-ubuntu:~$ cd "name@name/Desktop/WG311v3 V1.0 XP Driver"
bash: cd: name@name/Desktop/WG311v3 V1.0 XP Driver: No such file or directory
name@name-ubuntu:~$ 

```

So I tried following you code directions, which I do appreciate by the way, however I keep running into this problem. I've tried with quotes, and without, I've tried changing paths, etc. etc. But every time I hit pwd I get home/name. It just wasn't running. Something I was doing wrong?

Yes, I replaced my name with the word name. But you get the point.

EDIT: Even further, when I tried to just skip ahead, hoping it would just install I tried this. Observe the magic code lol ^_^.

```

name@name-ubuntu:~$ sudo ndiswrapper -i WG311v3.INF
couldn't open WG311v3.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
name@name-ubuntu:~$ 

```

The only thing I find significant here, is that it is not looking at /home but it's looking in /usr/sbin/ndiswrapper-1.9 line 219. Anything significant there? Just throwing this out there,

EDIT EDIT: Further more, it seems not to detect any currently installed drivers.

```

name@name-ubuntu:~$ ndiswrapper -l
name@name-ubuntu:~$ 

```

The second line was after I hit the first line. As you can see nothing happened. That means no drivers installed right?

EDIT EDIT EDIT: There's such a sense of accomplishment here ^_^!

```

name@name-ubuntu:~$ cd "/home/name/Desktop/WG311v3 V1.0 XP Driver"
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ pwd
/home/name/Desktop/WG311v3 V1.0 XP Driver
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ sudo ndiswrapper -i WG311v3.INF
installing wg311v3 ...
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

Yay! What next? lol

EDIT EDIT EDIT EDIT: Oh COMMON! Ok so I looked for an alternate in the code, so I could preform the last step you gave me.

```

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

See it doesn't actually list an alternate, like you said I need to put into the command. Hmm...

EDT EDIT EDIT EDIT EDIT (WOW) : Because it doesn't list an alternate there, does that mean I don't have to do that step? Because it's already complete. According to the directions, you just need remove the alternate. But I don't have to remove what's not there. 

Cool, so now what? Or is there anything. Because it doesn't seem to be reading my card yet. >_< /me is so impatient lol.

---

### Post by Sonic Reducer on 2008-07-01
> **lockerhaxor said:**
> EDIT EDIT EDIT EDIT: Oh COMMON! Ok so I looked for an alternate in the code, so I could preform the last step you gave me.

```

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

See it doesn't actually list an alternate, like you said I need to put into the command. Hmm...

EDT EDIT EDIT EDIT EDIT (WOW) : Because it doesn't list an alternate there, does that mean I don't have to do that step? Because it's already complete. According to the directions, you just need remove the alternate. But I don't have to remove what's not there. 

Cool, so now what? Or is there anything. Because it doesn't seem to be reading my card yet. >_< /me is so impatient lol.

yeah, you dont need to blacklist anything.

try typing **iwconfig** and look for a wireless interface. here's mine for comparison:

```
ryan@Ryan-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"<My Access Point>"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: <My MAC Addy>   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=65/100  Signal level=-68 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by lockerhaxor on 2008-07-01
```

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

I dunno what exactly this means. Evedentily it needs to be configured lol. So err yeah. I'm sorta stuck there, because it's not letting me set-up a wireless network.Buut I asume I can just enter a command to enable it? Help lol.

---

### Post by Sonic Reducer on 2008-07-01
> **lockerhaxor said:**
> ```

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

name@name-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

I dunno what exactly this means. Evedentily it needs to be configured lol. So err yeah. I'm sorta stuck there, because it's not letting me set-up a wireless network.Buut I asume I can just enter a command to enable it? Help lol.

"lo" is the loopback interface. some programs use ports on your computer to communicate with... your computer, i guess. i know a program called Kismet runs like that. thats not your wireless.

i'm assuming your computer has an ethernet port, and that is most likely what eth0 is (ports start getting named from 0, so if you had a second interface it would be eth1)

does **ndiswrapper -l** list your wireless driver?

---

### Post by lockerhaxor on 2008-07-03
> **Sonic Reducer said:**
> "lo" is the loopback interface. some programs use ports on your computer to communicate with... your computer, i guess. i know a program called Kismet runs like that. thats not your wireless.

i'm assuming your computer has an ethernet port, and that is most likely what eth0 is (ports start getting named from 0, so if you had a second interface it would be eth1)

does **ndiswrapper -l** list your wireless driver?

Sorry it took so long to get back to you. I went out of town.

```

oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

I've given up removing my name. I takes to long lolz.

This is what it says when I put ndiswrapper-l. So it says it's installed, but it doesn't actually read the device as there. It won't let me connect to the wireless network, and it won't let me even see it, though it says it's installed.

The wireless card doesn't even light up.

---

### Post by cariboo on 2008-07-03
Your driver is installed, but you have to load the module before it will work. In a terminal:

```
sudo modprobe ndiswrapper
```

this will not give you a message unless there is an error.

Jim

---

### Post by Sonic Reducer on 2008-07-03
> **lockerhaxor said:**
> I've given up removing my name. I takes to long lolz.

there really isn't any reason to remove your name, if anyone is skilled enough to hack into your computer with just that is skilled enough to not need the username, if you know what i mean

---

### Post by lockerhaxor on 2008-07-03
> **Sonic Reducer said:**
> there really isn't any reason to remove your name, if anyone is skilled enough to hack into your computer with just that is skilled enough to not need the username, if you know what i mean

Yeah it was just keeping mah' real name from getting out there, but lol It took to long to actually change it to name@name each time. I wasn't so much worried about hackers there lol.

Anyway I will try this when I get back to that computer. Actually right now. Hang on ^_^! I'll edit if it worked.

---

### Post by lockerhaxor on 2008-07-03
```

oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ sudo modprobe ndiswrapper
[sudo] password for oliver: 
oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

oliver@oliver-ubuntu:~/Desktop/WG311v3 V1.0 XP Driver$ 

```

It's still not working though. I'll see what I can do about it, but if anyone has any ideas let me know. I'm going to restart this computer to see what happens.

---

