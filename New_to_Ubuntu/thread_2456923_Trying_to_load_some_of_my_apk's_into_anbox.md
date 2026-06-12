---
title: "Trying to load some of my apk's into anbox"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by sdantonio on 2021-01-21
Another question

I have anbox and android device bridge installed.  I'm trying to install a few android programs into anbox.

[LIST]
[*]I start up anbox (graphically)
[*]start up adb (terminal window *adb start-server)*
[*]I change directories to Downloads which is where I have the program apk files
[*]try to install the programs using *adb install prog_name.apk *and this is what I get from the terminal for 2 separate programs
[/LIST]

sdantonio@sdantonio-OptiPlex-3010:~$ adb start-server
* daemon not running; starting now at tcp:5037
* daemon started successfully

sdantonio@sdantonio-OptiPlex-3010:~$ cd Downloads
sdantonio@sdantonio-OptiPlex-3010:~/Downloads$ adb install mx-player-1-32-1.apk
adb: failed to install mx-player-1-32-1.apk: Failure [INSTALL_FAILED_NO_MATCHING_ABIS: Failed to extract native libraries, res=-113]

sdantonio@sdantonio-OptiPlex-3010:~/Downloads$ adb install VLC-Android-3.3.0-arm64-v8a.apk
adb: failed to install VLC-Android-3.3.0-arm64-v8a.apk: Failure [INSTALL_FAILED_NO_MATCHING_ABIS: Failed to extract native libraries, res=-113]
sdantonio@sdantonio-OptiPlex-3010:~/Downloads$ 

Not sure what "no matching abis" means

Last week I did successfully install a mahjong program into anbox using these same steps, so I don't know why it's failing here

Note I'm running ubunto 20.4 lts, the most recent anbox (loaded last week) and the most recent adb also. The MX and VLC apk's are definitely in Downloads, and yes I've verified the spelling and capitalization of the apk's names carefully.

Thanks
Steven

---

### Post by deadflowr on 2021-01-21
Incompatible architecture.
You have arm64 version but your system can probably only run amd64, or x86_64.

---

### Post by Holger_Gehrke on 2021-01-22
Android programs use a virtual machine, similar to the one used for Java - a byte-code interpreter with a Just-In-Time compiler. But for programs which need to run fast(er) there's the option of running native code for the processor in the device. That code usually takes the form of one or more libraries found in lib/<architecture-name>abi/ inside the apk (apk files - similar to Java's jar files - are just renamed zip-archives). Anbox does **not** emulate any processor, it runs Android for x86. So if an Android program uses native code and does not include the libraries for x86 you'll see the kind of message you got. This also explains why that Mahjong program worked: it either didn't use any native code or it included code for x86.

Holger

---

### Post by sdantonio on 2021-01-22
OK, Thanks. This is all good to know. I'll look into what I have and get back here with the results.

---

### Post by grahammechanical on 2021-01-22
Anbox developers make these claims:

> Anbox puts the Android operating system into a container, abstracts                             hardware access and integrates core system services into a GNU/Linux                             system. Every Android application will be integrated with your                             operating system like any other native application.                         

> To achieve our goal we use standard Linux technologies like                             containers (LXC) to separate the Android operating system from                             the host. Any Android version is suitable for this approach                             and we try to keep up with the latest available version                             from the Android Open Source Project.

I am not sure if the comments about native code apply. But what do I know? I have Anbox and so far it is yet to to a dialog screen that I can direct to the location of an apk file.

The app window opens with the Android icon in the centre and underneath it the owrd: Starting .... and then after a few seconds the app blinks out of existence.

[https://anbox.io/](https://anbox.io/)

Regards

P.S. the Anbox web site has a FAQ and the answer to "Abnox doesn't on my device" is, effectively, it is still under development and has not been tested on many devices. File a bug report."

P.P.S  I have just found this official information

> The apk files you will sometimes find on the internet tend to only have arm support, and will therefore not work on x86_64.

I take back my above comment about native architecture. Sorry.

---

