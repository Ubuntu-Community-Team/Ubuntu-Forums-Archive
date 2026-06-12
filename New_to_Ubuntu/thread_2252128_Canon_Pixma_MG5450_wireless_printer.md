---
title: "Canon Pixma MG5450 wireless printer"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by Peter_Davies on 2014-11-09
you guys solved my password problem so quickly, it's time to move to my next challenge. We have a small home network that only seems to have one problem; my laptop is dual booted with Ubuntu/Vista; Vista is fine, but Ubuntu is not recognising the printer. When I ask it to find network printer and type in the Hub SSID (BTHub*****) it says there is no printer. Am I entering the wrong information for the Host? Or some other elementary mistake??

---

### Post by coldraven on 2014-11-09
You probably should be entering the IP address of the printer, not the SSID  of your wi-fi. You could look at the printer properties in Vista or use your browser to log in to the router. Somewhere in the router will be a list of connected devices and their IP address'. You might want to make the printer's address a static one.

---

### Post by oldrocker99 on 2014-11-09
I have a somewhat old Epson NX420, and I use it wirelessly, but I did install Epson's own drivers.

---

### Post by sammiev on 2014-11-09
What make an model printer do you have?

---

### Post by howefield on 2014-11-09
After clicking on Add printer > expand Network Printer - is it not in there ?

Failing that, as coldraven suggests, use the printer ip to find it.

---

### Post by Peter_Davies on 2014-11-09
It's a Canon Pixma MG5450. I was looking for the URL address and could not find that. I have IP, and MAC, information; are we talking IPv4 or IPv6 address?

---

### Post by sammiev on 2014-11-09
I can say I never had any experience with Canon printers. :(

---

### Post by Peter_Davies on 2014-11-09
It is sometimes recognised. I just added the printer and there it was, and it says, connected to local host. It's kidding me, it won't print.

---

### Post by sammiev on 2014-11-09
> **Peter_Davies said:**
> It is sometimes recognised. I just added the printer and there it was, and it says, connected to local host. It's kidding me, it won't print.

That is the same thing that happen with me with the Epson printers, as soon as you add the drivers from there site you were good to go.

---

### Post by Peter_Davies on 2014-11-10
It recognises the printer, I can even check the ink levels, but it won't print. Asks me if I want to do test print etc. Shows printer idle, waiting for job to complete. Not showing a print queue, despite telling me that it is the twenty something job I have tried to print.
What is "aeroplane mode"? This seems to be some sort of option when I check out the network.

---

### Post by pdc on 2014-11-10
so Peter; there seem to be a few "need to" things for you to print through a wireless printer; 

1) the printer needs to be recognised and connected to the router: the older wireless printers had a screen that you entered the password of the network; that has been abbreviated now to pressing the WPS button to drop security briefly; 

2) you need printer drivers installed: on your computer; if it is the only one in the network;

_________________________________________

if you click here [http://localhost:631/printers/](http://localhost:631/printers/) it opens CUPS (printer admin); on your system; look in the right-hand column; can you see Canon 3.8 5400 series?

_________________________________

if you install the Canon drivers, they need [COLOR="#0000FF"]libtiff4[/COLOR] and you get that from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) where you go about 14 or 18 down the list and choose either 32bit or 64bit libtiff4 that matches your system

______________________

once that is done, to get the Canon driver go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html)

download and SAVE: by default, it should end up in your Downloads directory; assuming that, if you open a terminal and paste these commands in line by line, hitting the ENTER key after each paste 

```
cd Downloads
tar -zxvf cnijfilter-mg5400series-3.80-1-deb.tar.gz
cd cnijfilter-mg5400series-3.80-1-deb
./install.sh
```

that will run an install script; that install the printer driver

---

### Post by Peter_Davies on 2014-11-10
The printer is recognised by the router, did the press WPS button and it prints from our PC and my laptop when it is running Windows.
I did download drivers from Canon last night, but I suspect they are in a file and not installed.
I am prepared to give the above a try, but it does look complicated, to me! I'm a bit of a plug and play boy!
How about I try and short cut that by hard wiring my laptop to the printer and letting it sort out its own drivers?

---

### Post by pdc on 2014-11-10
I understand you feel it is all a bit hard ............

the install script will run well for both usb and wireless: it will just ask you which you want:

to run the install script; you need to:

1) download and save the file
2) copy each command; then paste it into the terminal; hit the ENTER key;
3) repeat the above

.........it may all seem a bit daunting; but you will be pleasantly surprised how well it goes;

---

### Post by Peter_Davies on 2014-11-10
Hi, complicated ,I think I meant complex!
When you say "open a terminal", what does that mean? Or, will it all come apparent as I follow your instructions?

---

### Post by sammiev on 2014-11-10
> **Peter_Davies said:**
> Hi, complicated ,I think I meant complex!
When you say "open a terminal", what does that mean? Or, will it all come apparent as I follow your instructions?

Ctrl + Alt + T at the same time.

---

### Post by JeQhdMD on 2014-11-10
The "Terminal" in Linux (& Ubuntu) is very similar to the "dos-prompt or command line" in Windows.   It IS NOT required that you learn all the detail of Terminal commands, but just learning a few can help speed things up like in this case.   There is also a graphical way - using wizards to install printer drivers . . . but just try what has been suggested . . . it is different than what you're obviously used to . . . . but on the other hand, it's not exactly rocket-science either.

---

### Post by snowmobiler on 2014-11-11
Peter,
I had an issue trying to connect to a USB printer (on a Ubuntu PC) from a Ubuntu laptop. I saw in your post that you said sometimes it would be there and sometimes not. I got it to work and then weeks later it wouldn't. I was using CUPS as suggested to me to make the printer "shareable". But even though I could access internet from every device, I still couldn't get the test page to print. For some reason I tried to browse my windows network on the ubuntu machines and it wouldn't recognize it (when it did before). Long story short, although windows network and all internet capability was fine, all I needed to do was reboot the router and it cleared all the printing problems.

---

### Post by Peter_Davies on 2014-11-11
re libtiff4; I chose i386deb. Just because it rang a bell with other stuff I have seen. Not sure it is the right one for 32 bit system. Any comments?

---

### Post by Peter_Davies on 2014-11-11
tried re booting the router, cheap and cheerful, no luck.
When I try to save the drivers from Canon asia support, I am denied because I don't have the "right permissions"

---

### Post by pdc on 2014-11-11
You did well with libtiff4

> When I try to save the drivers from Canon asia support, I am denied because I don't have the "right permissions" 

.........but you downloaded and installed libtiff4 successfully?

Perhaps you tell us a little about the version of Ubuntu? you are using................the computer it runs on is yours.............and you installed the Ubuntu............. etc

_________________________________

> When I try to save the drivers from Canon asia support, I am denied because I don't have the "right permissions" 

.............I envisage that you are going to the link I gave you; that you are clicking on the Download button; and that your system should leap in at that point and say: do you want to "open" this file, or "save" it? ............and when you select save .............it is refusing you??

---

### Post by Peter_Davies on 2014-11-12
running latest LTS (14.04) on Acer Aspire 9300, which I think is a 32 bit machine.I loaded Ubuntu alongside existing W Vista.
Yes, seemed to download libtiff4 ok. Going to the asian link it was denying me "save". I have now asked for "open" which it has done. The software centre has installed both the "common" and "series 5400".
Still no printing. The printer says it is processing and please wait. Sometimes it whirs away. It has done that right from the start.
Going into the software centre and asking for printing, shows a lot of CUPS and HP drivers installed. Should I be uninstalling them? They could be confusing things. There is no sign of the Canon drivers in the driver list, even when I ask for"cnijfilter". I haven't done the install command on the terminal, assume that if the software centre says they are installed, they are.

---

### Post by pdc on 2014-11-12
"Going into the software centre and asking for printing, shows a lot of CUPS and HP drivers installed. Should I be uninstalling them? They could be confusing things."              leave those drivers; they are fine

_______________

can you open a terminal? If not, a good time to learn: go to the Dash search function on your Desktop: do you know about it? ...........and type in terminal.............

...............or as another poster suggested to you earlier, hold down the Control key; keeping that held down, now press down the Alt key, and keeping those two keys pressed down, press the t key ................ 

that should open a terminal ..........now copy this command > [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR] ............and paste it into the terminal; use your mouse and top line of the terminal ie File and along to Edit and down to paste

.........if you get a result printed out, please copy that; and paste it back here ..................

__________________________________________________________________________

and with your new-found proficiency at pasting commands into a terminal, paste this one too to help us > [COLOR="#FF0000"]cnijnetprn --search auto[/COLOR]

---

### Post by Peter_Davies on 2014-11-12
yes,can open terminal, and do the copy and paste. Had to do the CUPS and Canon asian support.
Will try your next steps in the morning.

---

### Post by Peter_Davies on 2014-11-13
Have not done your latest copy and paste but just seen something new in CUPS. It is saying that the couple of times I tried to print today (after I put back the CUPS drivers I should not have removed yesterday) were aborted "cannot specify model number". Sounds like that might be fixable beforeI do copy and paste.

---

### Post by Peter_Davies on 2014-11-14
is there another way, apart from the web address, of getting into the CUPS controls?

---

### Post by Peter_Davies on 2014-11-16
This is the current situation;
I am offered 2 network printers, Canonmg5400(95CDC9000000), which has always been there, and CanonMG5400seies 88-87-17-9, which, I think, is the result of an attempt to put the Canon drivers in. The first printer connects by IP network via DNS.SD, the second by .cnijnet88-87-17-9. Whichever printer, when I come to do the copy and paste command line thing the second command (tar......) gets "cannot open:no such file. Now that file sits in "home" and "recent" not in the download library, and it does not seem to want to be moved there. The net result is that the first printer will say "processing, please wait momentarily" then nothing. The second printer does not respond at all. I know it sounds like I am talking about two printers. There is, of course,only one which has two different descriptions. Somewhere along the way, I havelost the ability to read the ink levels in the printer, of no real concern if I can't get the little devil to print! Comments appreciated.

---

### Post by pdc on 2014-11-16
so Peter; we need to know if the Canon printer driver for the MG5400 was installed; 

can we ask you again to paste this command into a terminal: it is looking to see if the Canon drivers were installed > [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR]

.............and if you could please copy and paste back here the results...................... use your mouse and the top line of the terminal.................

___________________________

can we see if we can find the driver package with the command > [COLOR="#FF0000"]locate cnijfilter-mg5400series-3.80-1-deb.tar.gz[/COLOR]

.............so again, please copy this command; open a terminal; use your mouse; paste the command into the terminal; if you get a result that [COLOR="#008000"]cnijfilter-mg5400series-3.80-1-deb.tar.gz[/COLOR] is somewhere on your computer, can you please copy where it is; and paste the result back here;

---

### Post by Peter_Davies on 2014-11-17
this is the result of the copy and paste

peter@peter-Aspire-9300:~$ 
peter@peter-Aspire-9300:~$ dpkg -l | grep cnijfilter
ii  cnijfilter-common                                     3.80-1                                              i386         IJ Printer Driver for Linux.
ii  cnijfilter-mg5400series                               3.80-1                                              i386         IJ Printer Driver for Linux.
peter@peter-Aspire-9300:~$ 
peter@peter-Aspire-9300:~$ 

and the locate command

peter@peter-Aspire-9300:~$ 
peter@peter-Aspire-9300:~$ locate cnijfilter-mg5400series-3.80-1-deb.tar.gz
peter@peter-Aspire-9300:~$ 
peter@peter-Aspire-9300:~$ 

Does this mean that one moment they have been found and the next moment lost? I know that they are on my "home" screen, not in the download file, and they do not want to be moved.

---

