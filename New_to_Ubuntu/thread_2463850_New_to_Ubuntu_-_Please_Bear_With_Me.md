---
title: "New to Ubuntu - Please Bear With Me"
date: 2021-06-19
forum: New to Ubuntu
---

### Post by jackdusty on 2021-06-19
HI Guy's and Girl's

Please forgive me for posting and being a little lit long winded but I need to tell you a little bit about myself before I go on to tell you what help I need. I am approaching my 66 birthday and about to bite the bullet and finally retired, I did try that once but that is another story.

I have spent the last 40 years working in the IT Industry firstly operating mainframe IBM computers then moving into the Microsoft world, I have never had any exposure to either Linux or Unix. - I though as money will not be so forthcoming in future it might be an idea to economise, and I though rather than choosing to follow the never ending Microsoft update routine I would look at Ubuntu..

Now I dbit about the setup I am trying to run, I have an HP Probook which I have successfully installed Ubuntu 20.04, connect to this I have a Del 6000 docuking startion that gives me one HDMI and two display port sockets and 4 x USB3 sockets, into these I have the dongle for my wireless Keyborad and Mouse a dongle for my wireless headset and a USN Camera. THis all works fine when my laptop was running Windows 10.

I want to get the following working:-

My Two monitors connected to my dock do not work.   
I want to sync with my OneDrive
Install the Drivers for my Canon IR1028 Laser printer
Get Whatsapp working from Ubuntu with my Iphone

And apart from that I think Ubuntu has everything I need.

I have read somewhere that I need to get DisplayLink USB Graphic working to get my monitors to work - the mouse and keyboard and camera all work ok.

Now the problem is I don't really understand the sytax or command in linux.

I have followed a guide for setting up onedrive and it tells you to log into your onedive then paste a URL generated in terminal, it then tell you to paste the URL returned but I am getting an error message which I post below, and thats before I try the syncing -

Initializing the OneDrive API ...
Authorize this app visiting:


[https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=22c49a0d-d21c-4792-aed1-8f163c982546&scope=Files.ReadWrite%20Files.ReadWrite.all%20Sites.ReadWrite.All%20offline_access&response_type=code&redirect_uri=https://login.microsoftonline.com/common/oauth2/nativeclient](https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=22c49a0d-d21c-4792-aed1-8f163c982546&scope=Files.ReadWrite%20Files.ReadWrite.all%20Sites.ReadWrite.All%20offline_access&response_type=code&redirect_uri=https://login.microsoftonline.com/common/oauth2/nativeclient)


Enter the response uri: [https://login.microsoftonline.com/common/oauth2/nativeclient?code=M.R3_BAY.3f687353-2f3f-ddbb-c0eb-da7aa1904050](https://login.microsoftonline.com/common/oauth2/nativeclient?code=M.R3_BAY.3f687353-2f3f-ddbb-c0eb-da7aa1904050)
OneDrive returned a 'HTTP 400 - Bad Request' - gracefully handling error
onedrive.OneDriveException@src/onedrive.d(874): HTTP request returned status code 400 (Bad Request)
{
    "correlation_id": "89ae7d09-a781-4701-95e7-2f49b9c442d4",
    "error": "invalid_grant",
    "error_codes": [
        70000
    ],
    "error_description": "AADSTS70000: The provided value for the 'code' parameter is not valid.\r\nTrace ID: 4c8c7b95-1bd5-428d-af55-e1e14e14a300\r\nCorrelation ID: 89ae7d09-a781-4701-95e7-2f49b9c442d4\r\nTimestamp: 2021-06-19 18:23:22Z",
    "error_uri": "https:\/\/login.microsoftonline.com\/error?code=70000",
    "timestamp": "2021-06-19 18:23:22Z",
    "trace_id": "4c8c7b95-1bd5-428d-af55-e1e14e14a300"
}
----------------
?? [0x55c204da79d9]
?? [0x55c204da6cb5]
??:? [0x55c204da7b65]
??:? [0x55c204da5f58]
??:? [0x55c204db37a8]
??:? void rt.dmain2._d_run_main2(char[][], ulong, extern (C) int function(char[][])*).runAll() [0x7f377a77b9db]
??:? _d_run_main2 [0x7f377a77b7ee]
??:? _d_run_main [0x7f377a77b65d]
??:? __libc_start_main [0x7f377a3670b2]
??:? [0x55c204d7e5ed]
pat@HP-ProBook:~$ 


In sort I am after a dummies guide to urgently get my monitors working and I really don't want to spend any more money on any more hardware and Iso far I need help getting my Onedrive syncing.

I can see I may need help with the other things but hopefully as time goes on I will learn more.

Thanks for your patience in reading and you anticipated help.



Regards




Jack

---

### Post by GhX6GZMB on 2021-06-19
I think your basic premise is off.
OneDrive is a Microsoft product/service, and I'm pretty sure it will never work with Linux in any form.
First, you'll need to find a different cloud service that's non-proprietary.

---

### Post by oldfred on 2021-06-19
Your HP Probook may need UEFI update. 
Dell has updates for docks.

XPS 13 [SOLVED] dock Dell TB16 does not work  - needed Firmware updates & UEFI setting Dell
[https://ubuntuforums.org/showthread.php?t=2431141](https://ubuntuforums.org/showthread.php?t=2431141)
[https://ubuntuforums.org/showthread.php?t=2433026](https://ubuntuforums.org/showthread.php?t=2433026)

Some smaller Cloud companies just have gone out of business. And even a larger one may not decide to say in that business. So I do not trust cloud, but if desired it can be one of your backup locations.
I backup to multiple drives, flash drives, DVDs, and via sneakernet to another system  in another state. (via Copy of flash drive).

---

### Post by jackdusty on 2021-06-19
Thanks for the reply - please read this :-

  [https://www.linuxuprising.com/2020/02/how-to-keep-onedrive-in-sync-with.html](https://www.linuxuprising.com/2020/02/how-to-keep-onedrive-in-sync-with.html)

---

### Post by ActionParsnip on 2021-06-20
Some onedrive options here
[https://itsfoss.com/use-onedrive-on-linux/](https://itsfoss.com/use-onedrive-on-linux/)

---

### Post by jackdusty on 2021-06-20
So youy rather pleased with myself - managed to get my Onedrive sync today and also managed to install VMWAre Worstation but could really do with some help getting my external monitors working Pretty Please

---

### Post by oldfred on 2021-06-20
Did you update UEFI & firmware on dock as posted above?

---

### Post by jackdusty on 2021-06-20
Not yet my next job

---

### Post by scorp123 on 2021-06-20
> **ml9104 said:**
> OneDrive is a Microsoft product/service, and I'm pretty sure it will never work with Linux in any form.


You're wrong.

[https://rclone.org/onedrive/]("https://rclone.org/onedrive/")

---

### Post by scorp123 on 2021-06-20
> **jackdusty said:**
>   Enter the response uri: [https://login.microsoftonline.com/common/oauth2/nativeclient?code=M.R3_BAY.3f687353-2f3f-ddbb-c0eb-da7aa1904050](https://login.microsoftonline.com/common/oauth2/nativeclient?code=M.R3_BAY.3f687353-2f3f-ddbb-c0eb-da7aa1904050)
OneDrive returned a 'HTTP 400 - Bad Request' - gracefully handling error
onedrive.OneDriveException@src/onedrive.d(874): HTTP request returned status code 400 (Bad Request)
{
    "correlation_id": "89ae7d09-a781-4701-95e7-2f49b9c442d4",
    "error": "invalid_grant",
    "error_codes": [
        70000
    ],
    "error_description": "AADSTS70000: The provided value for the 'code' parameter is not valid.\r\nTrace ID: 4c8c7b95-1bd5-428d-af55-e1e14e14a300\r\nCorrelation ID: 89ae7d09-a781-4701-95e7-2f49b9c442d4\r\nTimestamp: 2021-06-19 18:23:22Z",
    "error_uri": "https:\/\/login.microsoftonline.com\/error?code=70000",
    "timestamp": "2021-06-19 18:23:22Z",
    "trace_id": "4c8c7b95-1bd5-428d-af55-e1e14e14a300"
}
----------------
?? [0x55c204da79d9]
?? [0x55c204da6cb5]
??:? [0x55c204da7b65]
??:? [0x55c204da5f58]
??:? [0x55c204db37a8]
??:? void rt.dmain2._d_run_main2(char[][], ulong, extern (C) int function(char[][])*).runAll() [0x7f377a77b9db]
??:? _d_run_main2 [0x7f377a77b7ee]
??:? _d_run_main [0x7f377a77b65d]
??:? __libc_start_main [0x7f377a3670b2]
??:? [0x55c204d7e5ed]



I'm just guessing here but it could be that Microsoft has done some changes on their side and the client you want to use hasn't caught up with those changes yet, e.g. it is trying to reach a Microsoft URL that no longer exists on Microsoft's side. I had a similar problem once with Google and "Google Drive", so this experience is what I am basing my guess on.

You could maybe try a different OneDrive client and try if that gets you any further?
[https://rclone.org/onedrive/]("https://rclone.org/onedrive/")

Yes, I know. It's a terminal-based client and it might not look so super "user-friendly" to someone who is not used to this kind of program. As I said above: the idea here is not that you be using this for all eternity, it is just to troubleshoot the problem and find out if there was a change of API (or whatever) on Microsoft's side. Because if this program does work then it could mean that the other client you were trying to use might also get updated sooner or later and work again.

And for the record: "rclone" does offer a web-based GUI that one could install on top. 
[https://rclone.org/gui/]("https://rclone.org/gui/")

Screenshot:
[https://raw.githubusercontent.com/rclone/rclone-webui-react/master/screenshots/dashboard.png]("https://raw.githubusercontent.com/rclone/rclone-webui-react/master/screenshots/dashboard.png")

---

### Post by jackdusty on 2021-06-22
Right I have upgraded the firmware in my D6000 not made a bit of difference - read from the Dell website I need to install the Displaylink Drives - downloaded it but as yet cannot seem to get the syntax right to install them - keep getting the message command not found when running the sudo ./ command - will progress when I have more time

---

### Post by scorp123 on 2021-06-23
> **jackdusty said:**
> keep getting the message command not found when running the sudo ./ command 

Check permissions? *"Execute"* permission needs to be set on programs and scripts, etc. or else the system will not be able to recognise those files as being executable. Also make sure you get the syntax right and there are no superfluous spaces where none need to be. **"sudo ./command"** and **"sudo ./ command"** are NOT the same thing.

Just guessing here.

---

### Post by TheFu on 2021-06-23
I can't help with much of the issues, but [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle Linux book that can be used as a reference. Available in many different languages. Free.

In my "beginning Linux" classes, we do the first 200-ish pages and spend 2 full lessons on Unix permissions, forcing people to learn that stuff.  It is the core for everything else, running programs, access rights, and security.

My first real job was programming for a modified IBM-360 but using a different Amdahl IBM clone.  That background isn't very useful, I'm sorry to say.  Your MS-Dos and Windows skills are closer, but still often way off.   JES2 and JES3 and JCL just aren't used in Linux.  I think there's a Rexx interpreter, but python, ruby and perl are more useful.

---

