---
title: "modem help?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Kalawala on 2008-05-17
hi im pretty much new to ubuntu i have ubuntu 7.04 and 7.10 installed on my harddrive dually but i have absolutely no idea how to hook up my dial up modem my modem is also used for my windows which is how i am able to be on here so i am pretty sure it is a winmodem and that sucks because it will be difficult to manage but i cannot get a new one so how exactly so i make this work for me to be able to connect to the internet i believe if i did this right the information i wrote down was chip set is 
class = class 0780:127a:1025 
Name = communication controller : rockwell international HCF 56k data/fax/voice/2pkp
subsys = 148a:1025
DCIDEV = 127a:1025
IRQ = 11 Ident = HCF.HSF 
Device ID : 127a:1025
Type HCF.HSF

but i really have no idea what that means or what exactly i need to do with it or for it and etc. plz someone send help and a very detailed instructional method on how i can set up my dialup modem

---

### Post by HotShotDJ on 2008-05-17
> **Kalawala said:**
> Device ID : 127a:1025
Type HCF.HSFOk... this is a Conexant softmodem (formerly Rockwell).  If you have a Dell, you are in luck, as they make the linux drivers available for free.  If you have some other system, you will need to purchase the drivers from [Linuxant]("http://www.linuxant.com/drivers/hcf/index.php")

---

### Post by spiderbatdad on 2008-05-17
Rockwell modems generally have excellent linux support. This is an external modems...correct?
You should be able to install it fairly easily with gnome-ppp, kppp, or ppp-config: in that order of preference, I believe. There are many good how-tos:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

The easiest way is to install gnome-ppp, but configure the modem from the command line:```
sudo wvdialconf
gksu gedit wvdial.conf

(input your credentials, and save)

sudo wvdial
```

---

### Post by Kalawala on 2008-05-18
ah im sorry i forgot to mention that it is a modem that goes inside my computer is that going to make a difference in how it needs to be installed? will it have some different methods or? and also my computer is a hp compaq not a dell but just the shell is an hp ive built it on my own so is that going to matter? is there anyway to still get a driver to work for it without paying for it or anything?

---

### Post by Kalawala on 2008-05-18
i believe i have installed the modem correctly but also i have downloaded gnome-ppp 0.3.23 onto my usb drive and brought it over to my ubuntu but i do not know how to install it from there can you tell me what to do?

---

### Post by spiderbatdad on 2008-05-18
Gnome-ppp is a graphical frontend for wvdial. Please try to configure wvdial and start your modem from the command line as I outlined in the previous post.

---

### Post by Kalawala on 2008-05-18
ok i did everything i could and did the gksu gedit wvdial.conf thing and it gave me a blank document and idk if it was suppose to but i copied what was in the format sudo gedit /etc/wvdial.conf because well im not really sure i just thought i remembered reading that i was suppose to in one of the billions of tutorials i tried yet it says i have my password and username and telephone is wrong yet they are the ones i used to set up my windows dialup are they different or? what could i have done wrong

---

### Post by spiderbatdad on 2008-05-18
no. you should not have had a blank document after running ```
sudo wvdialconf
```That command should detect the modem and write a file called: /etc/wvdial.conf. In that file you would add your credentials. If sudo wvdialconf failed to write the file, you need to run scanModem from one of the tutorials above and read the output files. Unfortunately dial up can be a task in linux.

---

### Post by spiderbatdad on 2008-05-18
Here is an archive of scanModem. See this link for instructions:[http://132.68.73.235/linmodems/index.html](http://132.68.73.235/linmodems/index.html)
Scroll down to the section: How To Use ScanModem.

---

### Post by Kalawala on 2008-05-18
it is not the sudo wvdial conf that is giving me a blank document it writes it and says it was written to the etc/wvdial.conf it's when i use the gksu gedit wvdial.conf that gave me a blank document but i do have scanmodem and used it i believe i used it correctly anyways but i was told previously to do a sudo gedit /etc/wvdial.conf is that wrong or srry i know im probably being impossible but sudo wvdial conf does work and does write the information or w/e what exactly do i need to next and ill start from there

---

### Post by Kalawala on 2008-05-20
hey um its just been a few days i know everyone has a busy life i was just wondering if theres any hope for me yet since i really really wanna try ubuntu

---

### Post by spiderbatdad on 2008-05-20
so, when you run:```
sudo wvdial
```it says incorrect username/password?

---

### Post by spiderbatdad on 2008-05-20
Try adding this line at the end of /etc/wvdial.conf

Carrier Check = no


The file should look something like this:

[Dialer Defaults]
Phone = 555-5555
Username = Your username
Password = Your password
New PPPD = yes
Modem = /dev/ttySL0
Baud = 460800
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Carrier Check = no

The order isn't all important, but Phone, user, password should be in order.

---

### Post by Kalawala on 2008-05-20
ok i figured out what was wrong with that it at a ; Username and the same type of thing for password and phone number so i had to backspace those three things to the start of the line (they were there as a default) except my new problem is that when it goes out to dial it doesnt dial the numbers just gives a dial tone for awhile then says something along the lines of your time allowed to dial out has expired or something (thank you very much for coming back to help i was worried ;)

---

### Post by SlappyPappy on 2008-05-20
Should look something like:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS1
ISDN = 0
Phone = 6853734
Password = 123456
Username = slappypappy

---

### Post by spiderbatdad on 2008-05-20
is there some easy way for you to post your /etc/wvdial.conf here? If not no problem

Make sure /etc/wvdial.conf also has the line:

Stupid Mode = yes

so add:

Carrier Check = no
Stupid Mode = yes

---

### Post by Kalawala on 2008-05-21
well im not exactly sure how i post it but if you tell me how i will try i have a usb stick that i could used but by adding those 2 lines at the bottom didnt help its still not giving me dial tones just the dial tone and then the time allotted for you to dial has expired it says something in the terminal as ATDT(thephonenumber) and then it doesnt dial out just gives the dial tone through the speakers its like its attempting to though its just missing something?

---

### Post by spiderbatdad on 2008-05-21
No doubt modems can be frustrating. Try adding ATDT in front of your phone number:

ATDT 5555555

---

### Post by Kalawala on 2008-05-21
no it didnt help basically the terminal says something like
--> Modem Initialized
--> Dialing (i think thats the word dialing could be wrong) ATDT 5555555
ATDT55555555

(no i didnt use that 5555555 as my number or w/e just idk just the number i picked) any other hopeful suggestions?

---

### Post by Kalawala on 2008-05-21
i believe it mentions something about carrier in it instead of dialing maybe im not sure where im srry :S 

i believe its 
modem initialized 
Sending ATDT 5555555
ATDT5555555

---

### Post by Kalawala on 2008-05-21
um it appears that i have the same problem that you did from [http://ubuntuforums.org/showthread.php?t=678361&highlight=dialtone](http://ubuntuforums.org/showthread.php?t=678361&highlight=dialtone)

how exactly did you overcome it??????????

---

### Post by spiderbatdad on 2008-05-21
> **Kalawala said:**
> um it appears that i have the same problem that you did from [http://ubuntuforums.org/showthread.php?t=678361&highlight=dialtone](http://ubuntuforums.org/showthread.php?t=678361&highlight=dialtone)

how exactly did you overcome it??????????

LOL. with that particular softmodem (winmodem) I never did overcome the problem. Turned out the modem was unusable in linux. I did get past the carrier check, and even past the handshsake, but then the call would drop. You may have to get an external modem.

There was one interesting post regarding an "ungrab-winmodem driver" I never looked into it.

---

### Post by Kalawala on 2008-05-23
how um did you get past the carrier check thing or w/e?

---

### Post by spiderbatdad on 2008-05-23
> **Kalawala said:**
> how um did you get past the carrier check thing or w/e?

Carrier Check = no
should have done it.
I also tried some custom flags to this line:```
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
``` The source of which I no longer have. And I don't even remember what they mean. Google that line might help.
 I spent a good week trying to get that modem to work. Found some custom scripts for touching pap and chap secrets, countless hours of reading and trying different drivers and libs...it always seemed like I was just on the verge of a break through...but it never worked beyond dropping the call immediately after the connection was established.

I would strongly encourage looking into an external modem (conexant)
Wish I had a better solution. I try help others get their modems going...sometimes successfully, but not with an internal modem yet.

I don't remember you mention trying the restricted driver in System>>Administration>>Hardware Drivers, if there is one listed. You might also check that you have the sl-modem-daemon installed: ```
 sudo apt-get install sl-modem-daemon
``` Though you might need to look for it and get it on a usb stick, if you have no internet access for synaptic package manager...

---

### Post by spiderbatdad on 2008-05-23
sl-modem-daemon here:[http://packages.debian.org/sarge/i386/sl-modem-daemon/download](http://packages.debian.org/sarge/i386/sl-modem-daemon/download)

but it has dependencies...[http://packages.debian.org/sarge/sl-modem-daemon](http://packages.debian.org/sarge/sl-modem-daemon)

debconf
libasound2
libc6

---

### Post by Kalawala on 2008-05-23
ok i was able to download the first one and i downloaded the debconf but um where exactly do i find the libasound2 and libc6 i click on it then it sends me to more pages with more items to download and well im just kinda lost for those (i havent tried to install them yet)

---

### Post by spiderbatdad on 2008-05-23
Actually, you may have the dependencies already. Click on the slmodemd package to install it. The installer will tell you if the package has unmet dependencies.

---

### Post by Kalawala on 2008-05-23
yeah it says i still need them

---

### Post by Kalawala on 2008-05-24
yeh um that libc6 wont let me install because it has a conflict with tzdata what do i do

---

### Post by Kalawala on 2008-05-25
but um i found some site that had dialer defaults so i changed mine to this 
[Dialer Defaults] 
Modem = /dev/modem
Baud = 460800 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem 
Carrier Check = No
Stupid mode = yes
Dial Command = ATDP 
Phone = <Target Phone Number> 
Username = <Your Login Name> 
Password = <Your Password> 

and it does dial now except it like gets stuck in a beeping noise idk how to descripe it a loud button pressing like noise and then says no carrier or something

---

### Post by Kalawala on 2008-05-26
ok ive basically given up on this modem so now im looking for a modem that for sure is linux capable and cheap as in hopefully 10 or less? is that even like possible??

---

