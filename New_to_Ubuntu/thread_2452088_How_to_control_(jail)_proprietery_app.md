---
title: "How to control (jail) proprietery app?"
date: 2020-10-16
forum: New to Ubuntu
---

### Post by rajan222 on 2020-10-16
Hi 

Unfortunately, I have installed  Microsoft team because government forced student to teach from that, 
I found no choice than installing :( . 

I see It had added several privacy corrupting things such as
1) a update link directly to software updater app ( I've disabled it)
2) using my webcam and microphone
3) seeing all my files 
4) directly opening when start( I've immediately disabled it)

Also I have weird problem of it ,
I have placed in dock, and when i right click it It directly shows, "Quit team", but again, I didnt opened it, open when i do same thing to other software nothing like `Quit transmission` came,
I doubt, It is doing malicious thing on my computer 




Although I only open it on study time, but I am worried, 
If it also run on background ,
use my webcam or microphone even app is not opened, 
 Send information to microsoft all the time even app is not opened


But I want to control it or keep it on Jail so that it couldnt do anything on my files unless i want for some occasions like saving study videos, 
I want a police software which monitor it like no webcam authority, no microphone authority, no sending information to microsoft authority, 
That police would control every activities of msteam, like completely close when quit, not even small particles of it on background.
Just put it in jail, Even if I am on internet. 
Shutting down internet is not on choice.

---

### Post by ActionParsnip on 2020-10-16
You could run it in a docker

---

### Post by SeijiSensei on 2020-10-16
If you run Windows in a [VirtualBox]("http://www.virtualbox.org/") virtual machine, the application will only be able to see the files in the VM and cannot touch ones on the host machine. For a webcam, read this: [https://docs.oracle.com/en/virtualization/virtualbox/6.0/admin/webcam-passthrough.html](https://docs.oracle.com/en/virtualization/virtualbox/6.0/admin/webcam-passthrough.html)

---

### Post by rajan222 on 2020-10-16
How docker?
doest docker only run command line? I have to run msteam gui , Please tell how can i do this?

---

### Post by rajan222 on 2020-10-16
It takes alot of memory ram, :(

---

