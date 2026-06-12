---
title: "Configure GPRS/EDGE via Bluetooth"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by mukherjee.siddhartha on 2006-09-14
[SIZE=2][COLOR=DimGray]How to configure internet access through GPRS/EDGE, using bluetooth connection with your GSM phone.

I am using ubuntu and Nokia 6630 phone with Airtel Connection, but this will work with any distribution and any bluetooth capable phone.. 

_** * Requirements:**_
  
   1) GPRS/EDGE Enabled Phone (Here Nokia 6630)
  2) GPRS Connection (Here Airtel, Kolkata, India)
  3) BlueTooth Dongle
  4) bluez-utils 
       [/COLOR][/SIZE][SIZE=2][COLOR=DimGray]> sudo apt-get install bluez-utils[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  5) openobex 
[/COLOR][/SIZE]> [SIZE=2][COLOR=DimGray][Download here]("http://sourceforge.net/projects/openobex") and compile, 
      You need gawk and gcc, 
sudo apt-get install gawk 
sudo apt-get install gcc[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  6) ppp
      [/COLOR][/SIZE]> [SIZE=2][COLOR=DimGray]sudo apt-get install ppp[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  7) latest 2.6 kernel

[/COLOR]_**[COLOR=DimGray] * Now the simple easy steps:[/COLOR]**_[/SIZE][SIZE=2]
[/SIZE][SIZE=2][COLOR=DimGray]
_**Step 1.**_
Plugin The bluetooth dongle and activate the bluetooth on your mobile
_**Step 2.**_
**       Kernel Configuration** 
You may ignore this part if your hardware is recognised, Ubuntu Magic;)
[/COLOR][/SIZE][SIZE=2]> CONFIG_BT=y 
CONFIG_BT_L2CAP=m 
CONFIG_BT_SCO=m 
CONFIG_BT_RFCOMM=m 
CONFIG_BT_RFCOMM_TTY=y 
CONFIG_BT_BNEP=m 
CONFIG_BT_BNEP_MC_FILTER=y 
CONFIG_BT_BNEP_PROTO_FILTER=y 
CONFIG_BT_HIDP=m 
## Bluetooth device drivers 
CONFIG_BT_HCIUSB=m 
CONFIG_BT_HCIUSB_SCO=y 
CONFIG_BT_HCIUART=m 
CONFIG_BT_HCIUART_H4=y 
CONFIG_BT_HCIUART_BCSP=y 
CONFIG_BT_HCIBCM203X=m 
CONFIG_BT_HCIBPA10X=m 
CONFIG_BT_HCIBFUSB=m 
CONFIG_BT_HCIDTL1=m 
CONFIG_BT_HCIBT3C=m 
CONFIG_BT_HCIBLUECARD=m 
CONFIG_BT_HCIBTUART=m 
CONFIG_BT_HCIVHCI=m 
## PPP 
CONFIG_PPP=y 
CONFIG_PPP_ASYNC=y 
CONFIG_PPP_SYNC_TTY=m 
CONFIG_PPP_DEFLATE=m 
CONFIG_PPP_BSDCOMP=m 
CONFIG_PPP_MPPE=m [/SIZE][SIZE=2][COLOR=DimGray]    [U][B]Step 3.
[/B][/U]Issue this command
[/COLOR][/SIZE][SIZE=2]> hcitool scan It will give you an output like this
> Scanning ...
        00:11:9F:D1:05:A4       Nokia 6630 [COLOR=Blue]Note/Copy the address **"00:11:9F:D1:05:A4" **somewhere.
This is the bluetooth address of the phone.
[/COLOR]
[U][B]Step 4.
[/B][/U]Issue this command> sudo vi /etc/bluetooth/pin-helper Put this on that file and save
[/SIZE]> [SIZE=2]#!/bin/sh[/SIZE][SIZE=2]
echo -n "PIN:" cat /etc/bluetooth/pin[/SIZE][SIZE=2][COLOR=Blue]also remember to check the file "[/COLOR][COLOR=Blue]/etc/bluetooth/pin"
which should have something like this "1234", If it is not there create that files and put "1234"
[/COLOR]

[U][B]Step 5.
[/B][/U]Issue this
> sudo vi /etc/bluetooth/rfcomm.conf Put this
> rfcomm0 {
 bind yes;
 device 00:11:9F:D1:05:A4;
 channel 1;
 comment "Nokia";
} [/SIZE][SIZE=2][COLOR=Red]Remember to replace this "00:11:9F:D1:05:A4" with the address you copied in step 3.[/COLOR][/SIZE][SIZE=2] 

[U][B]Step 6.

[/B][/U] Create a file > sudo  vi /etc/ppp/peers/airtel Put this
> /dev/rfcomm0 115200 
connect '/usr/sbin/chat -v -f /etc/ppp/chat-gprs'
crtscts
modem -detach
noccp
defaultroute
usepeerdns
noauth
ipcp-accept-remote
ipcp-accept-local
noipdefault  

_** Step 7.**_
Create a file
> sudo vi /etc/ppp/chat-gprs Put this
> '' ATZ OK 
AT+CGDCONT=1,"IP","airtelgprs.com"
OK "ATD*99***1#"
CONNECT '' [/SIZE][SIZE=2][COLOR=Red]You need to ask your service provider and replace the "airtelgprs.com"
and "*99***1#", these are the IP/host name of gprs provider and dialup no.
[/COLOR][/SIZE][SIZE=2][U][B]
Step 8.[/B][/U]
**[COLOR=Red]YOU ARE DONE! THATS IT? YEAH....[/COLOR]**
just issue this command
> pppd call airtel 
Thanks..Enjoy Ubuntu.


[/SIZE]

---

### Post by bodhi.zazen on 2006-10-30
Nice How-to mukherjee.siddhartha.

This thread has been added to the UDSF wiki.

[How-to Internet Access Bluetooth GSM Phone](http://doc.gwos.org/index.php/HowToInternetAccessBluetoothGSMPhone)

---

### Post by mukherjee.siddhartha on 2006-10-30
Thanks, Internet is a nice place, full with nice people :mrgreen:

---

### Post by mukherjee.siddhartha on 2006-11-03
I tried this on edgy, :(
Its not possible there, you wont be able to pair the phone with ubuntu.
Any help help on this will be great.

BTW, I did not like Edgy, SO rollback to dapper again. Everything works on Dapper.

---

### Post by stranger1121 on 2006-11-05
> **mukherjee.siddhartha said:**
> I tried this on edgy, :(
Its not possible there, you wont be able to pair the phone with ubuntu.
Any help help on this will be great.

BTW, I did not like Edgy, SO rollback to dapper again. Everything works on Dapper.

I installed Edgy month ago, but I still have problem with pairing my phone with PC. There is some problem with passkey in hcid.conf , I think.

---

### Post by mukherjee.siddhartha on 2006-11-05
I think its impossible to pair in Edgy :(

---

### Post by sv452 on 2006-11-06
does anybody know how to get gprs and bluetooth working for edgy ????

btw, all the info is in here to get it working on dapper except that u must change pin-helper to /usr/bin/bluepin

[http://www.howtoforge.org/linux_internet_access_gprs_edge_via_bluetooth_gsm_phone](http://www.howtoforge.org/linux_internet_access_gprs_edge_via_bluetooth_gsm_phone)

---

### Post by mukherjee.siddhartha on 2006-11-06
I do what exactly same is here, no need for change the pin helper

---

### Post by frisket on 2006-11-14
> **mukherjee.siddhartha said:**
> I think its impossible to pair in Edgy :(

I just managed it (6.10). I plugged in my USB Bluetooth dongle and turned on Bluetooth on my phone (SE Z5201). 

I followed the instructions in the earlier post to do a hcitool scan and it could see the phone, so I edited pin-helper and rfcomm.conf as suggested, and added a number to bluetooth/pin. Set the phone to scan and it found the laptop. Requested a pairing and a window popped up and asked me to enter the passcode, and it paired.

Only trouble is, a scan for services shows the laptop offering nothing. What software is needed on Edgy to offer remote cursor/enter control (eg for presentations)? File transfer already worked OK before this (unpaired), using the installed Bluetooth File Sharing application.

---

### Post by pavel_kbc on 2006-11-30
pppd: In file /etc/ppp/peers/gp: unrecognized option '/dev/rfcomm0'

sucks

---

### Post by pavel_kbc on 2006-12-02
i have connected to cell phone . and its need passkey .its mean it works . but its not connecting to internet :(

---

### Post by mukherjee.siddhartha on 2006-12-26
> **mukherjee.siddhartha said:**
> I think its impossible to pair in Edgy :(I was wrong, somethiing was messed up (May be I did)
Now I can do everything, with a fresh install of edgy.

---

### Post by igb on 2007-01-10
Thanks for the HowTo. I had this all working in Dapper, but couldn't get it to work in Edgy. The additional steps I required over Dapper were to include:

```
modem -detach
noccp
ipcp-accept-remote
ipcp-accept-local
noipdefault
```

in my /etc/ppp/peers/BluetoothDialup script. I also had to create /dev/rfcomm0 as it isn't there by default in Edgy:

```
sudo mknod —mode 666 /dev/rfcomm0 c 216 0
```

Ian.

---

### Post by online14230 on 2007-01-12
I dont know, maybe Im just thinking with the wrong head...
Shouldnt your PHONE offer services to the laptop with the laptop offering no services to the phone? I know with my N70 on WinXP/200/98SE (that means ALL 3 os's) my laptop offers absolutely no services to the phone. Yet, all 3 pick up a host of services from the phone (modem, serialcon etc) (cant remember them all right now, been a while since ive used it). I'm sure if you check, you can transfer files/data/music etc from the PC/laptop to the phone, but you wont be able to browse the PC/laptop with the phone.

Or am I wrong?

I CANT WAIT to get flamed :)

---

### Post by Tourmaline on 2007-06-10
Thanks a lot Mukherjee ! 

Your howto worked perfectly for me on Edgy 6.10. I am using GPRS/EDGE with DTAC in Thailand. For people who wants to setup "/etc/ppp/chat-gprs" for DTAC here is the configuration to use :

'' ATZ OK 
AT+CGDCONT=1,"IP","www.dtac.co.th"
OK "ATD*99***1#"
CONNECT ''

---

### Post by nooor7772000 on 2007-06-24
thanks but after write that: pppd call airtel

it say
pppd: In file /etc/ppp/peers/airtel: unrecognized option '/dev/rfcomm0'

what that mean?

---

### Post by igb on 2007-06-25
It probably means that /dev/rffcomm0 doesn't exist. You can create it manually:

```
sudo mknod —mode 666 /dev/rfcomm0 c 216 0
```

Ian.

---

### Post by nooor7772000 on 2007-06-25
thanks but it say

mknod: extra operand `216'
Try `mknod --help' for more information.


and when type  mknod --help
it say:
Usage: mknod [OPTION]... NAME TYPE [MAJOR MINOR]
Create the special file NAME of the given TYPE.

  -Z, --context=CONTEXT   set security context (quoted string)
Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set permission mode (as in chmod), not a=rw - umask
      --help     display this help and exit
      --version  output version information and exit

Both MAJOR and MINOR must be specified when TYPE is b, c, or u, and they
must be omitted when TYPE is p.  If MAJOR or MINOR begins with 0x or 0X,
it is interpreted as hexadecimal; otherwise, if it begins with 0, as octal;
otherwise, as decimal.  TYPE may be:

  b      create a block (buffered) special file
  c, u   create a character (unbuffered) special file
  p      create a FIFO

Report bugs to <bug-coreutils@gnu.org>.
[COLOR="Black"][SIZE="6"]............. what that mean please,,,,,,,help me doing that?[/SIZE][/COLOR]

---

### Post by Tourmaline on 2007-06-26
Don't worry about the message "pppd: In file /etc/ppp/peers/airtel: unrecognized option '/dev/rfcomm0". By default the file /dev/rfcomm0 does not exist. Just reboot your system and the file will be created at the next start. 

I have the same problem when I try to create this file with the command "mknod" under Kubuntu 6.10. On the other hand this command with the arguments "c 216 0" seems to work perfectly under Kubuntu 7.04. 

I am now re-installing my laptop with Kubuntu 7.04 and I have to reconfigure the gprs and rfcomm connections. I will post my method in a few hours, if it works of course :-)

---

### Post by nooor7772000 on 2007-06-26
[SIZE="6"]thanks a lot dear i will wait ur post soon please as i need that a lot in my study thanks a lot [/SIZE]

as it say another one again 

CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jun 27 00:32:10 2007
--> Pid of pppd: 9425
--> Using interface ppp0
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> pppd: &#65533;[08][06][08][08][11][06][08]@ [06][08]
--> Disconnecting at Wed Jun 27 00:32:17 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
..............
i do not know what is the problem???

---

### Post by Tourmaline on 2007-06-27
Well, here is the way I got a gprs connection via bluetooth with my Nokia N70 phone and my laptop running under Kubuntu 7.04. 

- use "hcitool scan" to retrieve the MAC address of your phone

- use "sdptool browse" followed by the MAC address you got with "hcitool scan"

- look for "Service Name: Dial-up Networking". This is the the service provided by your phone and take note of the channel number. 

Pair your phone with your computer. Do this from your phone, KDE will detect the pairing attempt and ask you for the pin code. I assume you know this manipulation. 

- Use the method from Mukherjee Siddhartha to create all the files needed.  

Be careful when editing rfcomm.conf, don't forget to put the good MAC address and channel number :

rfcomm0 {
bind yes;
device MAC-ADDRESS-FROM-YOUR-PHONE;
channel CHANNEL-FROM-YOUR-PHONE;
comment "Nokia";
} 

- You can replace the name "airtel" by any other name, usually your provider name. 

When all files are created you can try to connect by typing "pppd call YOUR-PROVIDER-NAME"
and you may end with a message like "pppd: In file /etc/ppp/peers/airtel: unrecognized option '/dev/rfcomm0". In my case I just restarted the system and the file "/dev'rfcomm0" has been created automatically. Or you can try by restarting your bluetooth device by typing "sudo /etc/init.d/bluetooth restart" for K/Ubuntu 6.10 and 7.04 or "sudo /etc/init.d/bluez-utils restart" on previous versions, this seems to create the file "/dev/rfcomm0" too. 
Sometimes your bluetooth connection can be broken on your computer or your phone, so "sudo /etc/init.d/bluetooth restart" is a very useful command to reset rfcomm since just turning off/on your bluetooth device is not enough.  


Thanks to Mukherjee Siddhartha for his "how to". 

Useful links : [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

### Post by Tourmaline on 2007-06-27
Try the method I posted and let me know the result. The message you got look like an error of modem communication, meaning rfcomm is working on your computer but pppd encountered a problem with the modem. 

MAN PPPD : EXIT STATUS 16 The link was terminated by the modem hanging up.

I'm not expert in Point-to-Point Protocol, maybe you should ask to people who knows about on this forum.

---

### Post by nooor7772000 on 2007-06-27
first i would like to thank from my heart for ur kind dealing and reply for my problem ...but the  last erorr i post was about using usb cable which seem near to get work better than bluetooth

as i still have that crazy error in using bluetooth connection even after restart everything .....
...................................
pppd: In file /etc/ppp/peers/airtel: unrecognized option '/dev/rfcomm0'

what that mean i hope understand is that error in kernel or what i want understand it ,,,,,,

i even try ur post but also still say that....it seem not read '/dev/rfcomm0'

but listen when i type gksudo gedit /dev/rfcomm0
 i get blank file of rfcomm0.............is it must have something in it????
i hope that help ..........

[SIZE="5"]for give me a lot if i bother you[/SIZE] but i feel that you seem kind brother will help me in it.....and i fear of unstall ubuntu and be back for crazy windows for this option as i need it so much in my study...............

thanks again

---

### Post by Tourmaline on 2007-06-28
The file "/dev/rfcomm0" is empty, this is normal. Maybe the permissions of the file are not set correctly. If you cannot create the file in a shell you can use a filemanager like Krusader which work under Gnome too even if it is a KDE application. Use your package manger to install it or in a shell type "sudo apt-get install krusader". When installed type "sudo krusader" this will start the programm in root mode. Be careful by using Krusader in root mode, you have access to all your system files and deleting or changing something without knowing what you are doing can have disastrous consequences on your system ! 

- go to /dev and look for the file rfcomm0 right click on the file and go to "properties" 

- go to the "permissions" tab 

- the file should have the following permissions :

Owner : can read&write
Group : can read&write
Others : Forbidden

the file is not set as executable and the Ownership fields must contain for User : root and for Group : dialout

Type "sudo /etc/init.d/bluetooth restart" or restart your computer.

Try it and let me know. 

On which version of Ubuntu are you running ? 

The method I've posted works both on 6.10 and 7.04 It has been tested on a fresh install of 6.10 and 7.04 last sunday when re-installing my laptop, so I am pretty sure it should work on every computers equiped with bluetooth.

---

### Post by wieman01 on 2007-06-28
A question on my part... How would you interpret this error message:
> btsco v0.42
Device is 1:0
Voice setting: 0x0060
[COLOR="Red"]Can't connect RFCOMM channel: Permission denied[/COLOR]
Anything to do with the PIN or file ownership?

Advice is appreciated.

---

### Post by nooor7772000 on 2007-06-28
i search for the file by that browser u send after install it i did not find it in dev/
but find it in :///dev/.static/dev/rfcomm0 

and i try to apply permission to it and try again it not work at all.......

it must be in this direct 

 /dev/rfcomm0

it is not there for me

but it is there in 

dev/.static/dev/rfcomm0

[SIZE="6"]what can i do ,,,,,,,,,,,,,,,,,,,,,,for giveme again for bothering[/SIZE]

---

### Post by Tourmaline on 2007-06-29
Try creating the file with "sudo mknod —mode 666 /dev/rfcomm0" without the parameters "c 216 0" then apply the permitions I've indicated in the previous post.

---

### Post by Tourmaline on 2007-06-29
[COLOR="Red"]btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied[/COLOR]

Did you use the good channel number in "/etc/bluetooth/rfcomm.conf" ?

Try to turn off bluetooth on your phone and type "sudo /etc/init.d/bluetooth restart" or restart your computer then turn on bluetooth on your phone again. 

I don't think that it can be a pairing problem although it cost nothing to give a try. I used the same pin code "/etc/bluetooth/pin" as during the pairing sequence from my phone.

---

### Post by wieman01 on 2007-06-29
> **Tourmaline said:**
> [COLOR="Red"]btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied[/COLOR]

Did you use the good channel number in "/etc/bluetooth/rfcomm.conf" ?

Try to turn off bluetooth on your phone and type "sudo /etc/init.d/bluetooth restart" or restart your computer then turn on bluetooth on your phone again. 

I don't think that it can be a pairing problem although it cost nothing to give a try. I used the same pin code "/etc/bluetooth/pin" as during the pairing sequence from my phone.
It turned out to be a pairing problem after all. Very odd, but this is apparenly to do a bug in Kubuntu Feisty. I have documented my findings and a solution here:

[http://ubuntuforums.org/showthread.php?t=486087]("http://ubuntuforums.org/showthread.php?t=486087")

---

### Post by nooor7772000 on 2007-06-29
:(
 sudo mknod —mode 666 /dev/rfcomm0

mknod: missing operand after `/dev/rfcomm0'
Try `mknod --help' for more information.

---

### Post by popeye on 2007-07-21
Hi,

The pairing did not succeed for me as wel.

From this thread [http://ubuntuforums.org/showpost.php?p=2897851&postcount=11]("http://ubuntuforums.org/showpost.php?p=2897851&postcount=11")

this worked:

This is how I got the PIN popup working on feisty: call (even as a normal user)

```
passkey-agent --default /usr/bin/bluez-pin
```

before initiating the connection. This will register bluez-pin as the pin helper.

N.B. Including in /etc/bluetooth/hcid.conf a line like

```
pin_helper /usr/bin/bluez-pin;
```

does not help - for some reason, this option is not recognized any more

---

### Post by be_placid on 2007-07-30
I've got pairing setup (I was receiving Connection refused), so I had to run:
```
rfcomm connect 0 00:16:B8:47:52:DC
```
to get the device to pair.

Unfortunately, after running `pppd call airtel`, I received the following error:
```
moo:/home/alex# pppd call airtel
Connect script failed
moo:/home/alex# 

```

Any ideas?

(Sorry for 'necroing' this thread, but I thought it would be most appropriate here, as all the relevant info is around)

---

### Post by arifiqbal7 on 2007-08-03
i have the same problem that as noor. rfcomm not present in /dev. i did all as suggested above and failure,failure,failure... still whating for a suitable solution. wondering know how Mr Mukherjee did thats?

---

### Post by nolodude on 2007-08-03
Hi, I'm running Feisty and I was having trouble pairing devices. I have Jabra A320s USB BT dongle and Nokia 6120 classic.

Nothing worked until I did this:
> **popeye said:**
> Hi,

```
passkey-agent --default /usr/bin/bluez-pin
```

before initiating the connection. This will register bluez-pin as the pin helper.

But I didn't realize I should leave passkey-agent running. By pairing from the phone while passkey-agent was active, I got devices to pair. 

Now I'm getting "Connect script failed" error. When I try to connect, I get this in syslog:
```

Aug  3 19:07:48 NAKKIDELL hcid[6772]: link_key_request (sba=00:16:38:5E:50:AA, dba=00:1B:AF:5E:AF:4C)
Aug  3 19:07:49 NAKKIDELL chat[8006]: send (ATZ^M)
Aug  3 19:07:49 NAKKIDELL chat[8006]: expect (OK)
Aug  3 19:07:49 NAKKIDELL chat[8006]: warning: read() on stdin returned 0
Aug  3 19:07:49 NAKKIDELL chat[8006]: Failed
Aug  3 19:07:49 NAKKIDELL chat[8006]: Can't restore terminal parameters: Input/output error
Aug  3 19:07:49 NAKKIDELL pppd[8000]: Connect script failed
Aug  3 19:07:51 NAKKIDELL pppd[8000]: Exit.

```

---

### Post by arifiqbal7 on 2007-08-03
is there a way to instal a fresh copy of rfcomm0 in /dev. how?
:confused:

---

### Post by arifiqbal7 on 2007-08-04
look i did this.
1.i reinstalled bluez-utils and obenobex
2.since i am using MOTOROLA SLVR L6,i install p2kmoto.
3.i added  the following file as root: /etc/ppp/peers/chat.gprs' 
```

TIMEOUT                 15         
ECHO                    ON 
HANGUP                  ON

```
4.i typed ```
 # rfcomm bind /dev/rfcomm0 X:X:X:X:X:X CHANNEL

```
then typing ```
# rfcomm
```
and response is 
> rfcomm0: 00:17:00:73:1b:88  channel 1 clean
now i am able to see /dev/rfcomm0 but this is temporary.when i switch of my computer,/dev/rfcomm0 also vanishes. u gotta give the bind command again.
5.i typed ```
#pppd call AIRTEL
```
i get the response > fail to open /dev/rfcomm0: permission denied
also when i type ```
#rfcomm connect /dev/rfcomm0 00:17:00:73:1b:88 1
```
the response is 
> cannot connect to rfcomm socket: permission denied  
[COLOR="Red"]any idea why its happening like this?[/COLOR]

---

### Post by lobner on 2007-08-17
Thank you very much mukherjee.siddhartha!!

Thank you for this EXCELLENT how-to on GPRS connections over bluetooth.
I have been struggling with that issue for month. And then someone showed me that how to, and bada-bing it was working right away!

Just wanted to express my gratitude :)

---

### Post by bradmayne on 2007-08-27
i tried to do what you said.  This is a copy of the error message:

brad@brad-laptop:~$ pppd call cingular
pppd: In file /etc/ppp/peers/cingular: unrecognized option '/dev/rfcomm'

Can you help?

---

### Post by kusumba on 2008-05-08
:confused: :confused: :confused: :confused: :confused: :confused:

After tooo many attempts and efforts, I have given-up the GPRS connection on my IBM X60 / Nokia E90 + Airtel now...

UNLESS 

Some HERO here is willing to help me.. 

Here are some of the details:

kusumba@kusumba:~$ sdptool search DUN
> 
Inquiring ...
Searching for DUN on 00:1A:89:CD:BD:2F ...
Service Name: Dial-Up Networking
Service RecHandle: 0x1001b
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100


kusumba@kusumba:~$ sudo gedit /etc/ppp/peers/airtel

> /dev/rfcomm0 115200
connect '/usr/sbin/chat -v -f /etc/ppp/chat-gprs'
crtscts
modem -detach
noccp
defaultroute
usepeerdns
noauth
ipcp-accept-remote
ipcp-accept-local
noipdefault

kusumba@kusumba:~$ sudo gedit /etc/bluetooth/rfcomm.conf

> rfcomm0 {
bind yes;
device 00:1A:89:CD:BD:2F;
channel 4;
comment "Nokia";
}

kusumba@kusumba:~$ sudo gedit /etc/ppp/chat-gprs

> "ATZ OK
AT+CGDCONT=1,"IP","airtelgprs.com"
OK "ATD*99***1#"
CONNECT"

Finally, this is what I get:

kusumba@kusumba:~$ pppd call airtel

> Connect script failed


To check if my bluetooth is able to establish communication with Nokia E90, I went to Bluetooth Manager and Clicked on BROWSE and then CONNECT. I am able to access the files on my mobile.

I will really appreciate if someone can help me set the same...

Greetings, Kusumba S

---

### Post by xyepblra on 2009-04-09
This is what I encountered while installing obexfs-0.11:
```
checking for FUSE... configure: error: Package requirements (fuse) were not met:

No package 'fuse' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FUSE_CFLAGS
and FUSE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```Please help.

---

### Post by ndihmo on 2009-04-10
Hi all,

has anyone used this how-to with 9.04?

I'm having some problems. When I run the command to start communication this is what I get:

```

# pppd call vodafone
Connect script failed
#

```

while /var/log/syslog shows:
```

Apr 10 11:32:07 fujis pppd[3997]: pppd 2.4.5 started by ed, uid 0
Apr 10 11:32:09 fujis bluetoothd[2616]: link_key_request (sba=00:00:00:00:00:00, dba=00:00:00:00:00:00)
Apr 10 11:32:11 fujis chat[4001]: unterminated quote (line 1)
Apr 10 11:32:11 fujis pppd[3997]: Connect script failed
Apr 10 11:32:12 fujis pppd[3997]: Exit.

```

I'm wondering if the problem is in:
chat-gprs (line 1)?

Thanks,
Ed.

---

### Post by xyepblra on 2009-04-11
This is what I encountered while installing obexfs-0.11:
```
checking for FUSE... configure: error: Package requirements (fuse) were not met:

No package 'fuse' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FUSE_CFLAGS
and FUSE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```I downloaded debian packages listed in the first thread, but I cannot find a way to compile them as it mentioned there. Synaptic packages manager does not find package called FUSE. Please help.

---

### Post by xyepblra on 2009-04-11
> **mukherjee.siddhartha said:**
> [SIZE=2][COLOR=DimGray]
_**Step 2.**_
**       Kernel Configuration** 
You may ignore this part if your hardware is recognised, Ubuntu Magic;)There was no Ubuntu Magic this time for me...
> **mukherjee.siddhartha said:**
> [/COLOR][/SIZE][SIZE=2][/SIZE][SIZE=2][COLOR=DimGray]    [U][B]Step 3.
[/B][/U]Issue this command
[/COLOR][/SIZE][SIZE=2] It will give you an output like this
 [COLOR=Blue]Note/Copy the address **"00:11:9F:D1:05:A4" **somewhere.
This is the bluetooth address of the phone.
[/COLOR]Didn't work either...
And it doesn't work despite the fact that I installed everything you mentioned. Did I have to reboot after installing any of the packages you mentioned?

---

### Post by Amutha on 2009-06-25
Any solution for "Connect script failed" error?

---

### Post by Doogle_42 on 2010-01-05
[SIZE=1]Hi all.
I am running Ubuntu 9.10.
These instructions do not work.
A lot of them just say directory not found etc.
Does anyone know how i can set up a dial-up network with my phone via bluetooth on Ubuntu 9.10?
Thnx
David
[/SIZE]

---

### Post by abhayadevs on 2010-04-22
hi all,

came across this thread while trying to configure the GPRS access from my Ubuntu 9.10 Karmic Koala. I use FRONTECH Bluetooth Dongle to connect to the Nokia 6300.
-- I ddid all the steps in the intitial post bu Mukherjee.
-- Found no device node,hence created one. 
   crw-rw---- 1 root dialout 216, 0 2010-04-22 23:10 /dev/rfcomm0
-- then, 
     $ rfcomm connect 00:24:7C:2D:F4:79
     Connected /dev/rfcomm0 to 00:24:7C:2D:F4:79 on channel 1
-- now i have the error in script (as per the syslog in previous posts)
-- edited the chat-gprs to avoid the ". No i have ATZ OK instead "ATZ OK
-- Now if i issue pppd call airtel, it hangs for couple of seconds and throws like, "Connect script failed".
-- syslog says,
Apr 22 23:24:08 abhay-laptop pppd[5836]: pppd 2.4.5 started by root, uid 0
Apr 22 23:24:10 abhay-laptop chat[5838]: expect (ATZ)
Apr 22 23:24:55 abhay-laptop chat[5838]: alarm
Apr 22 23:24:55 abhay-laptop chat[5838]: Failed
Apr 22 23:24:55 abhay-laptop pppd[5836]: Connect script failed
Apr 22 23:24:56 abhay-laptop pppd[5836]: Exit.

ANY IDEA ? NEED HELP !!! :(

regards,
abhayadev s

---

