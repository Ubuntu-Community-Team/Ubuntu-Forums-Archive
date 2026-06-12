---
title: "help me what to do..."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by erdinnaya on 2008-07-07
I had Ubuntu 7.10 installed on my seperate hard disk and i was trying to download & install libssl 0.98 for some reason. But it gave a "dependency etc.." error and i was suggested to install it from "synaptic package manager". So i did it by checking the mark near libssl 0.98 and pressing "apply". But i guess it didnt work. So i assumed that this synaptic thing was nothing else but just a downloader like flashget in windows (horrifying part is coming..) and thought that it would be nice to check the libssl tag, delete it and re-download. Then i did it but the process was taking too long. It was saying "removed: lib..something.. , removed: ssl..something.." and it just hit me when i saw "removed: rhythmbox" that it was removing simply everything on linux... I hit log out button panicked and saw many error messages. I hit reset switch on pc and tried to boot linux but GUI was gone... 

So.. what can i do now? can anyone help??..

---

### Post by PriceChild on 2008-07-07
log into the cli (press ctrl+alt+f1 if no screen appears) then
```
sudo apt-get install ubuntu-desktop
```
Once done,```
sudo invoke-rc.d gdm restart && exit
```

---

### Post by annda on 2008-07-07
boot into recovery mode (you will see the option in GRUB) and once you are there, type:
```
apt-get update
```
after it is finished, type:
```
apt-get install ubuntu-desktop
```

this should restore your gnome desktop. reboot. good luck!

---

### Post by cosine352 on 2008-07-07
try 
> startx

---

### Post by erdinnaya on 2008-07-07
i tried apt-get update and install but it gave many errors saying "failed to fetch http://...." i have my live cd near me. Is there a way to install it from there?

---

### Post by erdinnaya on 2008-07-07
up

---

### Post by annda on 2008-07-07
if you have problems with internet connection, try synaptic and enable the cd as repository:
system>administration>synaptic
edit>add cdrom

then reinstall ubuntu-desktop

---

### Post by erdinnaya on 2008-07-08
by "enable the cd as repository" do you mean that i should boot from my live cd? I dont think i have internet connection problem, it can download some of the files when i say "apt-get install" or "apt-get update" but for most of the files it says "failed to fetch". And what exactly should i do after "add cdrom". Can you tell me all the steps?

---

### Post by erdinnaya on 2008-07-08
reminder: when i boot linux, i dont get anything with graphics. Just a full screen command line. So i cant try synaptic or anything else. 

Please tell me a way to reinstall ubuntu from my live cd again (preferably using the command line).

---

### Post by renzokuken on 2008-07-08
when you get to the command line you can edit your sources directly

```
sudo nano /etc/apt/sources.list
```

this opens a terminal text editor. now make sure the lines near the top which start with

```
deb cdrom: .....etc
```

are uncommented, i.e. do NOT have a # in front of them. edit as needed then press Ctrl+X, Y, Enter to save and exit.

then put the ubuntu install cd in and run

```
sudo apt-get update
```
followed by
```
sudo apt-get install ubuntu-desktop
```

---

### Post by erdinnaya on 2008-07-08
I opened the list. There was not "#" in front of "deb cdrom..." line (the first line). The two lines below were commented but they were saying: "see [http://.](http://.).. for help.. etc.." I deleted all "#" signs in front of lines with "deb". But when i tried apt-get update again, still it looked for the web site and gave "failed to fetch" error. I dont think editing that list will make linux stop looking for the files from the internet and make it install from live cd.

The thing i dont understand: i have a live cd in drive, i can use linux with command line, there MUST be a way to reinstall it from there. Please tell me the way..

---

### Post by renzokuken on 2008-07-08
i suppose you could comment out all the lines that start "deb http://" leaving only the cd-rom ones, then try updating and installing ubuntu-desktop again from there?

---

### Post by erdinnaya on 2008-07-08
i already commented out all the lines with a "deb... (web link)". I dont understand what you mean by "cd-rom ones" There are no cd lines except the first line of the list. Another thing i noticed, there is the same sentence at the end of all deb lines: "main restricted". Is that normal?

---

### Post by renzokuken on 2008-07-08
ok, in that case, stick the cd in the drive and run the following

```
sudo apt-cdrom add
```

this will look for package info on the disc and once complete you could do

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by erdinnaya on 2008-07-08
Nope.. didnt work. I did apt-cdrom add, it all went good, then i wrote apt-get update and install all over and again "failed to fetch http://..." and "packages not authenticated.. etc.." error came. 

Why does it try to retrieve the files from the net in the first place? I have the cd, isnt there a way to tell the program to look first into hard drives, then the net if necessary.

---

### Post by erdinnaya on 2008-07-08
Another thing; i assume the code "apt-cdrom add" should have changed the sources.list file. But there is nothing different in the list. Or is it wrong the way i think?

Is there any other way to tell apt-get install to look for files from the cd-rom drive instead of internet? Please answer yes or no. If the answer is no, then i have to wait till the moment i can (or have to) format the hard disk (maybe next year) or maybe say farewell to this distribution.

---

### Post by erdinnaya on 2008-07-08
up

---

### Post by erdinnaya on 2008-07-08
I commented all the lines except the first line in source.list. Tried to install again and here is my error: 
E: package ubuntu-desktop has no installation candidate

what is the problem now? Help me please just tell me what you know.

---

### Post by erdinnaya on 2008-07-08
up

---

### Post by erdinnaya on 2008-07-08
Finally formatted the partition and installed the OS all over. I guess the files were corrupted in the hard disk when i hit the reset button while they were being deleted. No one could help that.

---

