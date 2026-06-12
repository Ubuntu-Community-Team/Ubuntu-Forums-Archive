---
title: "Ubuntu 12.10 Freezes On Startup - May Be Wifi Drivers (?)"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by nicraz on 2013-03-14
Hi guys, 

I apologize in advance if this has already been discussed. I've searched and searched but haven't been able to find the right answer.

This is my second time installing Ubuntu,the first time I installed it as a test drive on an eMachine I no longer have. Now I have a Lenovo IdeaCentre K430 running Win7. Last night I installed Ubuntu 12.10 with a bootable USB stick. The installation went fine and it looked beautiful. I tried to install updates but it wasn't moving, so I x'd out of that and switched to Windows, then shut off the computer.

This morning I turned it on, got the GRUB menu nicely (the first time I tried I had a heck of a time with that), selected Ubuntu and once it started up and showed the password field for me to enter my password it froze. The mouse doesn't work neither does the keyboard. Tried REISUB, tried Ctrl + Alt + F1 but nothing happens, the keyboard doesn't seem to respond at all. I unplugged and plugged the USB receiver for the mouse/keyboard but that didn't help, they work fine when booting Windows. I did notice that it disconnected from the Wifi even though I had configured that last night. I found a thread that said that may be wifi drivers are messed up, they suggested to open terminal but I can get it to appear since the keyboard seems to be completely unresponsive. 

What can I do at this point? I don't know if it's possible to just install Ubuntu again, but what would be the process if at this moment I already have Windows and Ubuntu installed alongside each other. 

Any insight you can give, I'll really appreciate it. If you need more info from me please let me know. Thank you again.

---

### Post by grahammechanical on 2013-03-14
Please do not assume that it is a WiFi driver issue. In trying to put right something that is not wrong you may create a more complicated situation that can only be fixed by a re-install. So, to recap.

The loading gets to the Ubuntu login screen. Yes? Then you are nearly almost there. You put in your password and press enter and the screen does not change. Correct? And you cannot use the USB mouse or keyboard. Yes?

May I suggest that you use power off to reboot (Linux is robust enough not to bust). Then at the grub menu you select Advance options for Ubuntu and press enter. That will open a submenu. Look for Recovery Mode and select that. At the Recovery Mode screen select Resume. That should get to the login screen and may be this time get you further - on to a working desktop. Then search for Update Manager in the Dash and run an update. Also check to see if you have a working WiFi. 

Regards

---

### Post by nicraz on 2013-03-14
Thank you for your response, grahammechanical. 

I mentioned the wifi drivers because that's the only thing that I found online that may be related.

The loading gets to Ubuntu login screen, yes. I cannot put in my password. The cursor is frozen, I am not able to even enter the first letter. 

The Wifi is working fine, several other devices are connected and working, Wifi works fine in Windows. 

I will try your suggestion of Recovery mode and will report back with results. 

Thank you again.

---

### Post by nicraz on 2013-03-14
> **grahammechanical said:**
> Please do not assume that it is a WiFi driver issue. In trying to put right something that is not wrong you may create a more complicated situation that can only be fixed by a re-install. So, to recap.

The loading gets to the Ubuntu login screen. Yes? Then you are nearly almost there. You put in your password and press enter and the screen does not change. Correct? And you cannot use the USB mouse or keyboard. Yes?

May I suggest that you use power off to reboot (Linux is robust enough not to bust). Then at the grub menu you select Advance options for Ubuntu and press enter. That will open a submenu. Look for Recovery Mode and select that. At the Recovery Mode screen select Resume. That should get to the login screen and may be this time get you further - on to a working desktop. Then search for Update Manager in the Dash and run an update. Also check to see if you have a working WiFi. 

Regards

So I tried your suggestion. When I went into Advanced Options I had 4 choices:

Ubuntu, with Linux 3.5.0-25-generic
Ubuntu, with Linux 3.5.0-25-generic (recovery mode)
Ubuntu, with Linux 3.5.0-17-generic
Ubuntu, with Linux 3.5.0-17-generic (recovery mode)

I don't know what they mean, but since you said Recovery Mode, first I tried Ubuntu, with Linux 3.5.0-25-generic (recovery mode) and that didn't work. Then I selected Ubuntu, with Linux 3.5.0-17-generic (recovery mode) and that one did give me the option to Resume. It didn't log me in to the Desktop, it gave me the terminal, or at least it looked like the terminal. I had to enter my login and password. Then I typed 'sudo apt-get update' and it started updating, then the screen just turned black, I couldn't do anything. I had dinner and didn't touch it because I thought maybe it was doing something. But after 30 minutes or so it was still black. So I had to turn off the computer manually. 

I tried logging in normal again and it's the same, no keyboard or mouse. The Wi-Fi does say Not Connected to Network, or something along those lines. The cursor in the password box is frozen, I can't do anything.

Any other ideas? What can I do? I saw other options when in Recovery Mode but I have no idea what they mean.

---

### Post by nicraz on 2013-03-14
I went back to Recovery Mode, this time I selected 'dpkg' and it was finally doing something. After it was done, I thought it was going to boot, but the screen went black. I had to turn it off again, try to boot normal and again it keeps getting stuck in the login screen. No joy, I have no idea what else to do. If anybody can please help me, I would appreciate it.

---

### Post by varunendra on 2013-03-15
Welcome to the forums nicraz!

> **nicraz said:**
> ....it started up and showed the password field for me to enter my password it froze.
> **nicraz said:**
> ....Then I selected Ubuntu, with Linux 3.5.0-17-generic (recovery mode) and that one did give me the option to Resume. It didn't log me in to the Desktop, it gave me the terminal, or at least it looked like the terminal..
Can you boot with the normal **Linux 3.5.0-17-generic** option (not its recovery mode)? Post back if yes.

If not, there must be another option "**drop to root prompt**" at the bottom of the **recovery menu**, select that. It will again drop you to terminal like screen but the prompt will end with **#** instead of **$**. Do the following there -

Check the disk space left on the root partition (/)-
```
df -h
```
Make sure there is enough space on the drive.

Remove downloaded packages (some of them may be broken)-
```
apt-get clean
apt-get autoremove
```

Then retry the update -
```
apt-get update
apt-get dist-upgrade
```
If it fails (maybe due to internet connectivity), try the previous recovery mode and update from there.
Post back if it worked or not.

---

### Post by nicraz on 2013-03-15
> **varunendra said:**
> Welcome to the forums nicraz!

Can you boot with the normal **Linux 3.5.0-17-generic** option (not its recovery mode)? Post back if yes.



Hi varunendra!!! Thank you for the warm welcome ;)

YES!! I am able to boot and login when selecting the **Linux 3.5.0-17-generic** option.

I'm logged in and writing you from Ubuntu. What should I do now? Should I update?

---

### Post by varunendra on 2013-03-15
> **nicraz said:**
> Hi varunendra!!! Thank you for the warm welcome ;)

YES!! I am able to boot and login when selecting the **Linux 3.5.0-17-generic** option.

I'm logged in and writing you from Ubuntu. What should I do now? Should I update?
Of course your earlier update didn't go well for some reason. I believe you should remove that kernel and start a fresh update.

Including that, ensure a few other obvious things as well just to be extra sure -

[LIST=1]
[*]Remove the newer kernel that gave you trouble, as it may have been broken somehow (**sudo apt-get purge linux-image-3.5.0-25-generic**)
[*]Make sure there is enough space (preferably the size of download + the size after installation + 200 MB or more) in the root partition (**df -h**)
[*]Remove already downloaded packages, as some of them may be broken (**sudo apt-get clean && sudo apt-get autoremove**)
[*]Then do the update (**sudo apt-get update && sudo apt-get dist-upgrade**)
[/LIST]
Let us know of the outcome :)

---

### Post by nicraz on 2013-03-15
THANK YOU SO MUCH Varun!
Awesome, followed all of your steps and I'm back in. Oh Ubuntu how I've missed you! I just bought a 2 TB machine to enjoy Ubuntu without worrying about space. I'm running it along Windows. 

Thank you again!

---

### Post by varunendra on 2013-03-15
You're most welcome!

It's 7:22 am here and you just made my morning a good one with the nice feedback! Thank YOU for that. :D

---

### Post by nicraz on 2013-03-16
You got nothing to thank me for, Varun!
Enjoy your Saturday and thanks again!!

---

