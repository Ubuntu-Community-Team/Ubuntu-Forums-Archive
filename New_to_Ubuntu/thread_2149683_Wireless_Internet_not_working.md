---
title: "Wireless Internet not working"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by zak100 on 2013-05-29
Hi,
I have a usb for wireless internet. It was previously working with windows 7. But now i have installed ubuntu and its not working. I cant install the software. Kindly guide me. Its configuration file contents are:

> 


[Install]
DefDir=Broadband
AppTitle=Broadband
AppName=Broadband.exe
Publisher=Huawei Technologies Co.,Ltd
URLInfoAbout=http://www.huawei.com
HelpLink=http://mobile.huawei.com
 
[DRIVER]
WLAN=0
 
[FinishPage]
run=
runtext=
 
[shortcut]
dest1=Broadband.exe
name1=Broadband
dest2=uninst.exe
name2=Uninstall
usermanual=User Manual
usermanualfile=
 
[regedit]
TCPWindowSize=129940
Tcp1323Opts=3
reboot=false
 
[customize]
operator=PTCL_C172
simtype=SIM/USIM
uimtype=UIM
FindDevice=false
LaunchDashboard=false
 
[language]
name1=English
 
[System]
FileVersion=1
VVersion=100
RVersion=006
BuildVersion=001
DebugVersion=06
SPVersion=00
CustomizeVersion=172
 
[SPLASH]
SHOW_PROMPT=2
PROMPT_MESSAGE=PromptInfo.exe
LANGPATH=PromptInfo
LANGFILE=English.dat
FORBID_POP=YES
 
[PNPCTRL]
EXEC_REWIND=YES
DEFAULT_TIMEOUT=10
WIN2000_TIMEOUT=10
 
[EHIDS_PRODUCT_VERSION]
COMMENT=
INSTALL_SERVICE=NO
RUN_INSTALL_APP=YES
RUN_CLIENT_APP=YES
L_REG_PATH=SOFTWARE\Huawei technologies\Broadband
APP_FILE_NAME=Broadband.exe
SETUP_NAME=setup.exe
APP_INSTALL_PATH=Broadband
VALUE=16.001.06.00.172
 
[SD_INFORMATION]
SD_DETECT=YES
ANTI_VIRUS_REG_PATH=SOFTWARE\Symantec\SPBBC
ANTI_VIRUS_FILE_PATH=\Norton\NIS081550.exe
REMIND_SENTENCE=Remind you to install antivirus software?
 
[VIRCDROM_INFORMATION]
ANTI_VIRUS_TREND_EXE=\AntiVirus\TmSyn


Somebody plz help me.

Zulfi.

---

### Post by ajgreeny on 2013-05-29
The software you have is for windows; that is why you can't install it.

In ubuntu open a terminal and run the command ```
lsusb
``` and report back here the output you get in code tags, please, using the # icon in the toolbar at top of text entry box. Copy the output in terminal by highlighting it with your cursor and copy with right click and "Copy".  Paste it into your reply, highlight it there and click on the #.  It makes a lot of copied terminal output much easier to read.

EDIT:
Sorry, I missed the fact that it is a usb adapter in your post, and have edited my command suggestion above; sorry about that.

---

### Post by squakie on 2013-05-29
Also do a search on the forum for huawei - there have been many threads on that.  You may need to read several threads to find your answer.  Also, since you said it's via USB, the lspci won't show what is needed. Instead, post back the output of lsusb.

---

### Post by zak100 on 2013-06-02
Hi,
Thanks for your time. I searched for ce0197 but i did not get any match. I dont know if i have to search for e620. When i executed lsusb i got following output:
 
```

Bus 002 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 002 Device 005: ID 0c45:6321 Microdia
Bus 002 Device 002: ID 8087:0024 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:21e3 Broadcom Corp.
Bus 001 Device 002: ID 8087:0024 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Kindly help me. 

Zulfi.

---

### Post by zak100 on 2013-06-03
Hi,
I searched again and i found that this problem was not solved earlier also. Kindly check the following link:
[http://ubuntuforums.org/showthread.php?t=1908898&highlight=E620](http://ubuntuforums.org/showthread.php?t=1908898&highlight=E620)

Kindly guide me how to solve this problem

Zulfi.

---

### Post by zak100 on 2013-06-04
Hi,

I have found another link related to huawei e620
[http://ubuntuforums.org/showthread.php?t=1787453](http://ubuntuforums.org/showthread.php?t=1787453)

This has done more work but i dont know about the outcome of this work i.e. whether the guy was able to run internet. Kindly guide me with this problem.

Zulfi.

---

### Post by Hadaka on 2013-06-04
Hi, here is a link with your usb modem.
[http://ubuntuforums.org/showthread.php?t=1473228&page=2](http://ubuntuforums.org/showthread.php?t=1473228&page=2)
post #4

for your usb product id's you would need to do this.
*Copy and paste.
```
sudo gedit  /lib/udev/rules.d/61-option-modem-modeswitch.rules
```
add this one line
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

```
Save and close gedit.
boot your computer..
Hope this helps.

---

