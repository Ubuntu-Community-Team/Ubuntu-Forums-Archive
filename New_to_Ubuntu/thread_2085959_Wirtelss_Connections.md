---
title: "Wirtelss Connections"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by briscoashe2845 on 2012-11-19
That should be Wireless Connections....Hi. I have loaded Ubuntu onto a new hard-drive ( I am logged in on my old one ). I have a Belkin wireless USB receiver. And a UPC wireless modem. The UsB is connected and is recognized on Ubuntu...But Ubuntu will not find any wireless networks???.....UPC use WAP security, if that is of any baring???...........Any advice would be greatly appreciated. Please bare in mind, i have never used Ubuntu before & i am a VERY basic Desk top user,so  "Idiot" terminology would would be useful if that suits........Thank you.

---

### Post by dannyboy79 on 2012-11-19
open a terminal session within your ubuntu install and issue the following command and then tell us what it outputted back to you
```
lshw -C network
```

---

### Post by briscoashe2845 on 2012-11-19
There's a ton of stuff. I can't copy and paste because i have to keep changing hard drives...It says i should run it as a "super user" ....A separate window did open up with the Modem name asking for authentication . I put in the correct password. The box disappears for like 30 seconds and comes back asking again. 
Description : wireless interface
Physical : is 2
Bus info : usb@1.3
Logical : Wlan@

---

### Post by dannyboy79 on 2012-11-19
what does this command show, the last command I asked for didn't show me what wifi chipset your usb card uses.

```
sudo lspci
```

I am first trying to determine if the kernel is auto loading the driver for your usb wifi card.

I notice you say that a password box appears, are you saying it's asking for your WPA password?

---

### Post by briscoashe2845 on 2012-11-19
I will try that one and get back to you. Thanks for your help.........The box appearing. OK, the supplier i have is called UPC. So when i put in the previous search you suggested, on the desktop it found my UPC account and tried to log onto it. The box appearing was asking me for my WiFi Modem password. As I've never been logged onto it on the new hard drive. I put it in correctly but it still would not fully log on. And after a couple of tries will disconnect. But it will acknowledge that UPC is transmitting, it just won't log onto it. On my old hard drive, when i had to set up my WiFi initially, the UPC security used "WAP". But i notice that is not an option on Ubuntu. They have several, but WAP on it's on does not appear....I'm sorry if my description of this problem is terrible...I'm not exactly a computer whiz.......I do appreciate your help.

---

### Post by dannyboy79 on 2012-11-19
if you're using the network manager in the upper right corner, you should just have to click on your WIFI signal and it'll open a prompt to enter your WAP passphrase. If you enter the correct passphrase it should just connect to it. THat's how my D-Link router works, it's WAP and my 12.04 Ubuntu Sony Vaio laptop connects just fine to WAP.

---

### Post by newb85 on 2012-11-19
To run a command as a superuser, simply prepend it with *sudo*, thus:
```
sudo lshw -C network
```

(It will ask for a password.  As you type your user password, it will not give any visual feedback.  That's normal.)

If you have both HDDs attached to your machine, you should be able to copy and paste the output into a text file you save on the Windows HDD.  Then you can open it from Windows to paste it into this thread.  (For that matter, you could just attach the text file.)

---

### Post by briscoashe2845 on 2012-11-19
Ok...I took a chance reinstalled the latest version. Now when i log on it picks up available wireless networks. When i click on my one it still asks for the password. And still, it won't connect. In the window where it says it is trying to connect to UPC, it confirms UPC uses WAP security. But in the options on the edit for Ubuntu they don't have WAP as an option. They have several. Including. WAP 40/128 bytes, Wap 128 bytes, etc. But Not WAP on it's own....I have tried them all....Still no luck....No Luck. Any further thoughts???...Thanks....

---

### Post by briscoashe2845 on 2012-11-19
Thanks. I can't have the 2 hard drives at the same time. It's not a great computer, and it's short of Sata ports....I just want to replace the old one anyway.........I took a chance reinstalled the latest version. Now when i log on  it picks up available wireless networks. When i click on my one it still  asks for the password. And still, it won't connect. In the window where  it says it is trying to connect to UPC, it confirms UPC uses WAP  security. But in the options on the edit for Ubuntu they don't have WAP  as an option. They have several. Including. WAP 40/128 bytes, Wap 128  bytes, etc. But Not WAP on it's own....I have tried them all....Still no  luck....No Luck. Any further thoughts???..It's mad frustrating. It is picking up and acknowledging the wire free network, but it just won't let me log in......Thanks....

---

### Post by newb85 on 2012-11-19
You might be confusing security types.  To my knowledge, there is no such thing as WAP.  There are WPA types and WEP types.  I'm guessing the option you need to try is "WPA & WPA2 Personal" or "WPA & WPA2 Enterprise".

---

### Post by sandyd on 2012-11-19
as the user mentioned above, you may be confusing the encryption scheme.

Here are a few major ones - any of the look familiar?

WEP (insecure)
WPS/WPA/2
LEAP

Actually, looked UPC up - Im pretty sure its WPA/2

Just select WPA/-2 (either WPA or WPA-2), and enter the pw

---

### Post by sandyd on 2012-11-19
Duplicate Threads merged (somewhat messily)
sorry 'bout that

---

### Post by newb85 on 2012-11-19
This isn't a big deal to me as I can correct it for this instance, but I had subscribed to the other thread (where I had posted), and when the discussion was moved to this thread, my subscription stayed with that other thread.  But then, maybe that's normal.

---

### Post by dannyboy79 on 2012-11-19
> **briscoashe2845 said:**
> Thanks. I can't have the 2 hard drives at the same time. It's not a great computer, and it's short of Sata ports....I just want to replace the old one anyway.........I took a chance reinstalled the latest version. Now when i log on  it picks up available wireless networks. When i click on my one it still  asks for the password. And still, it won't connect. In the window where  it says it is trying to connect to UPC, it confirms UPC uses WAP  security. But in the options on the edit for Ubuntu they don't have WAP  as an option. They have several. Including. WAP 40/128 bytes, Wap 128  bytes, etc. But Not WAP on it's own....I have tried them all....Still no  luck....No Luck. Any further thoughts???..It's mad frustrating. It is picking up and acknowledging the wire free network, but it just won't let me log in......Thanks....what are you using to connect? are you using the network manager in the upper right?

---

### Post by briscoashe2845 on 2012-11-20
Thanks..

---

### Post by briscoashe2845 on 2012-11-20
> **newb85 said:**
> This isn't a big deal to me as I can correct it for this instance, but I had subscribed to the other thread (where I had posted), and when the discussion was moved to this thread, my subscription stayed with that other thread.  But then, maybe that's normal.
Apologies about that. As it was my first day on here, i didn't realise it was frowned upon to post two similar threads. Sorry for any trouble i caused there......

---

### Post by briscoashe2845 on 2012-11-20
> **sandyd said:**
> as the user mentioned above, you may be confusing the encryption scheme.

Here are a few major ones - any of the look familiar?

WEP (insecure)
WPS/WPA/2
LEAP

Actually, looked UPC up - Im pretty sure its WPA/2

Just select WPA/-2 (either WPA or WPA-2), and enter the pw
Thanks...Yeah i have also tried WPA personal & enterprise. Apologies  i meant to write WEP not WAP....I am defiantly putting the password in  correctly. As i said the network security is WEP on it's own, i have  tried the other versions of WEP available to no avail. Also i spent a  long time with the network supplier on the phone, but they are not up to  speed on Ubuntu, surprise surprise. At this point i don't know what to  try???.....................Everything in theory should just work . It's  picking up the network. When asked for authentication i put in the  correct password. But it just won't log on. And it's not the modem as  when I'm logged on like now on the old hard drive i have zero  problems.....Any other advice would be massively appreciated. As i am  seriously frustrated at this stage.

---

### Post by briscoashe2845 on 2012-11-20
> **dannyboy79 said:**
> what are you using to connect? are you using the network manager in the upper right?
Yes, i'm using the upper right to connect....Thanks...Yeah i have also tried WPA personal & enterprise. Apologies  i meant to write WEP not WAP....I am defiantly putting the password in  correctly. As i said the network security is WEP on it's own, i have  tried the other versions of WEP available to no avail. Also i spent a  long time with the network supplier on the phone, but they are not up to  speed on Ubuntu, surprise surprise. At this point i don't know what to  try???.....................Everything in theory should just work . It's  picking up the network. When asked for authentication i put in the  correct password. But it just won't log on. And it's not the modem as  when I'm logged on like now on the old hard drive i have zero  problems.....Any other advice would be massively appreciated. As i am  seriously frustrated at this stage.

---

### Post by briscoashe2845 on 2012-11-20
> **newb85 said:**
> You might be confusing security types.  To my knowledge, there is no such thing as WAP.  There are WPA types and WEP types.  I'm guessing the option you need to try is "WPA & WPA2 Personal" or "WPA & WPA2 Enterprise".
Thanks...Yeah i have also tried WPA personal & enterprise. Apologies  i meant to write WEP not WAP....I am defiantly putting the password in  correctly. As i said the network security is WEP on it's own, i have  tried the other versions of WEP available to no avail. Also i spent a  long time with the network supplier on the phone, but they are not up to  speed on Ubuntu, surprise surprise. At this point i don't know what to  try???.....................Everything in theory should just work . It's  picking up the network. When asked for authentication i put in the  correct password. But it just won't log on. And it's not the modem as  when I'm logged on like now on the old hard drive i have zero  problems.....Any other advice would be massively appreciated. As i am  seriously frustrated at this stage.

---

### Post by newb85 on 2012-11-20
Hmm...this is odd.  Did some googling around, and it seems current UPC wireless modems ship with WPA security by default.
How old is the modem?
Was the security changed to WEP for some reason?
Does the modem have an ethernet port?

Perhaps you could connect to the modem with an ethernet cable and change the security to WPA (which would be better/more secure, anyways).

---

### Post by briscoashe2845 on 2012-11-20
Modem is about 2 years old.......I might ring them and check it out. I wouldn't have a clue how to change that myself......Thank,s for the help. I'll get back to you on it....

---

### Post by briscoashe2845 on 2012-11-20
> **newb85 said:**
> Hmm...this is odd.  Did some googling around, and it seems current UPC wireless modems ship with WPA security by default.
How old is the modem?
Was the security changed to WEP for some reason?
Does the modem have an ethernet port?

Perhaps you could connect to the modem with an ethernet cable and change the security to WPA (which would be better/more secure, anyways).
I rang UPC and it turns out they changed it to WEP ages ago when there was some issues. I don't remember this, but it was probably shortly after i got the wireless?... I've actually upgraded my package and a new modem is arriving tomorrow, and as you said, and i confirmed, the default will be WPA.....So hopefully that will all be problem solved.....Thanks very much for all the help. And thanks to the others who also advised.....Much Appreciated.....

---

### Post by wildmanne39 on 2012-11-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

