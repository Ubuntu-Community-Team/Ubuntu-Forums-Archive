---
title: "Accessing Windows8 Share Lubuntu"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by dino5 on 2015-01-23
Hello all, I'm very new to ubuntu, and especially Lubuntu.

Please keep that in mind if you are getting a bit technical in your answer, thank you.

I have a windows 8 machine, with a shared drive that I would like to be able to access from my Pavillion HP laptop, running Lubuntu 14.04. I have done this on other windows machines, I can do it from my android phone, and I have even done this successfully on Ubuntu using nautilus. However I cannot do this using the PCman 1.2.3 packaged with Lubuntu. When I click on "Go">"Network" I see "Win8-PC" and "Windows Network", when I click on win8, I get a box asking me to enter my credentials. I enter them, which works on all other machines, including the laptop when I boot windows 7 (dual boot), but nothing happens on Lubuntu. The box just goes away for 1 second and comes back asking for the password again. Please help me out, I've looked at videos, tried to "sudo apt-get install samba", and even installed gigolo trying to solve this on my own, obviously to no avail. Thank you in advance.

Added Notes: Laptop is on wifi, same subnet as my win8 main pc, I can ping the pc when I open terminal "ping IP address of pc", Pc can ping laptop when I tried same from cmd line, I'm trying the same credentials I log in with on the main pc since that's what I've always used to connnect to it from other machines.

---

### Post by Jordan_Cameron on 2015-01-24
Hey there!  Welcome to the Ubuntu Forums!

May I please point your attention to this link:
[https://help.ubuntu.com/community/Lubuntu/PCManFM#Browse_Windows_PCs_with_Samba](https://help.ubuntu.com/community/Lubuntu/PCManFM#Browse_Windows_PCs_with_Samba)

Usually, it would take the form of smb://<machine ip>/<share name>

To find the machine's ip, if it's running windows, run
```
ipconfig
``` in the Command Prompt.

If the machine has access to linux, run:
```
ifconfig
``` in the terminal.  You are looking for the inet address.  Use that for the machine name in the smb path.

Let us know if you need anymore assistance, and how it turns out for you!

Cheers,
Jordan

---

### Post by dino5 on 2015-01-24
Using your instructions I was successfully able to get directly to where  it is that I've been getting stuck. Instead of having me press  "go">"Network", you allowed me to go directly there, where it asks  for my credentials of the win8 machine. Same problem once I get there, I  enter the credentials, the box disappears for one second, comes right  back and asks for the credentials again. Thanks though for teaching me  how to bypass "go">"network" but the problem is still there.

Since no one answered, I thought I'd use Kububuntu. Same issue, the OS seems to work correctly but I cannot access my network drive on a windows 8 machine. I would like to just enter my credentials and access my files, for god's sake it does not have to be this hard. I JUST WANT TO ACCESS MY FILES! This works flawlessly on heavy, slow, windows7... it just connects! Asks for user name/password, then bam I'm there. I would like some help please to connect to my shares. ANYONE PLEASE>

---

### Post by sandyd on 2015-01-26
By any chance, are you using Homegroups on Windows 8?

Windows 8 has a default HomeGroup setup when you install it. Unfortunately, the software that Ubuntu uses to access shared folders (SAMBA) does not support Homegroups. If you are using HomeGroups, disable them, and see if the shares now work in Ubuntu.

---

### Post by dino5 on 2015-01-27
I have disabled homegroups, I'm still unable to get kubuntu 14.04 to connect to windows.

Could anyone please help me connect my laptop to my windows 8 shares on my desktop. I don't care if I use: Lubuntu, ubuntu, or Kubuntu. I just don't want to use windows 7 (which connects to the shares just fine, only needs to enter password) but still have access to my files. Thank you.

Well thank you for the great support :)

---

### Post by bab1 on 2015-01-30
> **dino5 said:**
> Well thank you for the great support :)

You do realize that this forum is NOT Ubuntu official support; right?  This is an all volunteer, interested user forum.

What errors do you get when you try to "connect" with the host that has  the Windows Shares.  Samba ( and Windows Shares) use the protocol SMB/CIFS.  It doesn't matter whether it is a Linux machine or a Windows machine.  The host that makes available the shares is always a SMB/CIFS server.  The host that is accessing the share is always a SMB/CIFS client.

An Ubuntu host uses the Samba client software via  the Gnome Virtual File System (gvfs) to access the share.  I don't use KDE (Kubuntu) but my guess is that the gvfs libraries are being used.  I use Ubuntu Gnome or Unity and have no problems accessing any SMB/CIFS share.  The Samba client software is installed by default.

If you still need help, post the output from your Linux host of this```
smbtree -d3
```

Use the [noparse]```
 
```[/noparse] blocks to to wrap the fixed width text to preserve the formatting.  You can do this by clicking  on the [SIZE=5]**#**[/SIZE] Icon and placing the text inside the code blocks using the ADVANCED Reply editor.

---

### Post by Morbius1 on 2015-01-30
> **dino5 said:**
> I have a windows 8 machine, with a shared drive that I would like to be able to access from my Pavillion HP laptop, running Lubuntu 14.04. I have done this on other windows machines, I can do it from my android phone, and I have even done this successfully on Ubuntu using nautilus. However I cannot do this using the PCman 1.2.3 packaged with Lubuntu. When I click on "Go">"Network" I see "Win8-PC" and "Windows Network", when I click on win8, I get a box asking me to enter my credentials. I enter them, which works on all other machines, including the laptop when I boot windows 7 (dual boot), but nothing happens on Lubuntu. The box just goes away for 1 second and comes back asking for the password again. 
> I thought I'd use Kububuntu. Same issue
I can easily reproduce your symptoms by setting the "encrypt passwords" parameter to "No" in smb.conf.

Every now and then a given users settings for samba flips the default setting of "yes" for that parameter to "no".  I have no idea why but it's easy to fix. 

What you might want to do is post the output of this command so the folks here can see how you are set up:
```
testparm -s
```
If "encrypt passwords = No" shows up you will know that's the problem because it's not the default. If it doesn't show up it's set to "yes" and the issue is something else. And if it's not that issue it might perhaps be something else mis-configured.

[COLOR=#0000cd] *Granted, It seems improbable that both the Lubuntu and Kubuntu installs would have the same exact issue and the Ubuntu install would not  ... but you never know ..... *[/COLOR]

---

### Post by dino5 on 2015-02-05
Thank you for replying, I know it's voluntary. I tried all I could to get it to work using lubuntu, or kubuntu but I could not. I sucked it up, and reinstalled Ubuntu 14.04 with unity, without changing anything on my network it just worked again. The os is sluggish on my laptop, but at least it works. I guess it's a question of familiarity, and having a great system which you can't fix that "one annoying problem". Right after install, I just went to network and connected with no issues whatsoever.

[[If "encrypt passwords = No" shows up you will know that's the  problem because it's not the default. If it doesn't show up it's set to  "yes" and the issue is something else. And if it's not that issue it  might perhaps be something else mis-configured.]] Wish I knew about that, searched but didn't see that as a solution, I think you might be right though, I do think opening that .conf file had it set to no.

---

### Post by bab1 on 2015-02-05
> **dino5 said:**
> Thank you for replying, I know it's voluntary. I tried all I could to get it to work using lubuntu, or kubuntu but I could not. I sucked it up, and reinstalled Ubuntu 14.04 with unity, without changing anything on my network it just worked again. The os is sluggish on my laptop, but at least it works. I guess it's a question of familiarity, and having a great system which you can't fix that "one annoying problem". Right after install, I just went to network and connected with no issues whatsoever.

You didn't need to do that.  You can install just the gvfs system on both Lubuntu and Kubuntu. The application is called ***gigolo***.  This installs the Gnome libraries for file sharing only.  I don't use Lubuntu or Kubuntu so I don't have ***gigolo*** installed anymore.  I have installed it in the past just to see how it works and it worked just fine.  The app is in the  the 14.04 LTS repos.  I just checked now with Synaptic Package Manager.

---

