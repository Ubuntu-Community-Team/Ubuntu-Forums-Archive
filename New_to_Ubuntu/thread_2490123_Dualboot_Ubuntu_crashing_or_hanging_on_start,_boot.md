---
title: "Dualboot Ubuntu crashing or hanging on start, boot says *ERROR* nvidia-drm"
date: 2023-08-23
forum: New to Ubuntu
---

### Post by verexe on 2023-08-23
Hello! I am completely new to Ubuntu, and Linux in general. I have a Dell Precision 5540 laptop running windows 10, with a single drive that I partitioned to also run Ubuntu 22.04.3. I installed the Ubuntu iso, and put it onto a usb with Rufus. Shortly after installation, I could not successfully launch either Ubuntu or windows 10. I solved this for windows 10 by using windows recovery settings, and then I updated to windows 11. Windows is now working, but when I try to launch Ubuntu, it either hangs on some booting messages forever or the screen freezes a couple minutes after starting up.  

 
 
 I am not aware of a way that I can take a screenshot of the booting messages that would let me access them as i cannot fully access Ubuntu, so I have attempted to transcribe them below. This is what I see when Ubuntu startup hangs:

 
```

 
 [ 0.264775] APCI Error: AE_Error, Returned by Handler for [PCI_CONFIG] (20221020/evregion-300)

 [ 0.264810] APCI Error: Aborting method \_SB.PCI0._INI due to previous error (AE_ERROR) (20221020/psparse-539)

 [ 0.264822] APCI Error: AE_EROR, during \_SB_PCI0._INI execution (20221020/nsinit-657)

 */*dev*/**nvme0n1p5: clean, 196182*9830400 files, 4683399/39321600 blocks

 [ 3.835950]
 [ 4.396406] [drm:nv_drm_load [nvidia_drm]] * ERROR * [nvidia-drm] [GPU ID 0x00000100] Failed to allocate NvKmsKapiDevice
 [ 4.396529] [drm:nv_drm_probe_devices [nvidia_drm]] * ERROR * [nvidia-drm] [GPU ID 0x00000100] Failed to register device
 [  4.875428] Bluetooth: hci0: Malformed MSFT vendor event: 0x02

```

 

 
 I have run “system-info” in the pinned post from the Ubuntu usb I used for installation (in “try Ubuntu” mode) as I cannot launch Ubuntu proper, and I will put the results below.

 
 
 The code listed missing programs: curl, pastebinit
 
 
 report file: [http://termbin.com/trpp](http://termbin.com/trpp)

Thank you for your support!

---

### Post by oldfred on 2023-08-23
Did you originally install with Secure Boot off?
And with Windows 11 turn on Secure Boot or an UEFI update reset to defaults which probably turned it on.

If you want nVidia with Secure boot you have to set a MOK - machine owners key. That is saying that you confirm the nVidia software is secure.
sudo mokutil --sb-state

Many just turn UEFI Secure Boot off. Windows should still work.

See MOK section:
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

---

### Post by verexe on 2023-08-23
Hello! I originally installed Ubuntu with Secure Boot off, and checking  my bios the "secure boot enable" option is still unticked so I assume  that secure boot has remained disabled after the windows 11 update.

---

### Post by MAFoElffen on 2023-08-23
On boot, do you get a Grub2 Menu? If so, then at the Grub2 menu, press the <E> key to get into the menu edit mode. <Arrow-Down> to the line that stats with the word "linux". <Arrow-Right> to the words "quite splash". Replace the word "quiet" with "--" (two dashes). <Arrow-Right until after the word "splash". Append with "nvidia.modeset=1". Press <Cntrl><X> to boot.

When it boots, go to "Applications". Start typing in "Software & Updates". Go to the "Additional Drivers" tab. select "nvidia-driver-525". Press the install button. After the install, reboot to test.

If it does not boot, At the Grub2 Menu in edit mode, replace the words "quiet splash" with "-- 3". Press the keys <Cntrl><X> to boot. At the console prompt, login.
```

sudo apt-update
sudo apt remove --purge nvidia*
sudo apt install nvidia-driver-525
sudo reboot

```

---

### Post by verexe on 2023-08-23
I do have a Grub2 menu. Unfortunately, neither method seems to have solved the issue. The first caused the booting to hang indefinitely at "Starting Show Plymouth Boot Screen". After that I proceeded to the second solution.

(quick note: i typed "sudo apt update" instead of "sudo apt-update" as the latter was not recognized as a command. I assume the "-" was just a minor typo, but I want to make note of it just in case I made a mistake here.)

the given commands executed with no issues, but after sudo reboot and attempting to boot ubuntu again, I received the same 2 nvidia_drm messages, but this time the bluetooth message after was not present, and two new messages were present in its place:

```

  	 	 	 	   [36.113085] APCI Error: Aborting method \_SB.PCIO.PGON due to previous error (AE_AML_LOOP_TIMEOUT) (20221020/psparse-529)

 [36.113128] APCI Error: Aborting method \_SB.PCIO.PEGO._ON due to previous error (AE_AML_LOOP_TIMEOUT) (20221020/psparse-529)


```


Upon a second attempt to boot Ubuntu, instead of the boot messages it stayed at a splash screen of the Dell and Ubuntu logos.

upon a third attempt, Ubuntu successfully booted. After a couple of minutes however, the screen froze and the laptop powered off.

Upon one more attempt to boot Ubuntu, it hung at the original series of messages detailed in my first post once more, and the laptop powered off automatically after a short time at this stage.

---

### Post by MAFoElffen on 2023-08-24
You removed "quiet splash" and replaced with "-- 3" and it hung at the Plymouth Splash screen? That would have told it not to load the splash screen, not to load any graphics, and jst load a console in mode init 3...

What happens if you, at the Gurb2 Boot menu, You select Advanced options > Select a kernel with Recovery mode > Select "network" > Selec "root"... Are you able to remove and reinstall the nvidia drivers?

---

### Post by verexe on 2023-08-24
sorry, I spoke somewhat unclearly. after replacing just "quiet" with "--", I was stuck at the Plymouth Splash screen. After that, I rebooted and instead tried replacing "quiet splash" with "-- 3". In that case, I was not stuck at the Plymouth Splash screen and instead was able to execute the commands in the console. That is what i meant by the "first" and "second" solution respectively. I will try what you have just recommended and report back.

---

### Post by verexe on 2023-08-24
I removed and reinstalled the nvidia drivers though the advanced options menu and the commands you gave previously. after sudo reboot, ubuntu successfully booted to the desktop but appears to have immediately frozen, and is not responsive to any mouse or keyboard inputs. After waiting on this screen for about 10 minutes to see if anything would happen, I powered down the system and attempted to boot ubuntu once more, and it is now showing the same error message as in my original post. After about 1 minute of hanging at the error message, the machine shut down automatically.

---

### Post by MAFoElffen on 2023-08-25
Okay... So now you know how it will start to be able to change video drivers, and to be able to test them. Now lets find one that works.

On the next boot... After removing the drivers, do
```

sudo ubuntu-drivers list

```
Copy them down and post them... Then go done the list, one by one, and try each, to see if one works better than another. For example
```

sudo ubuntu-driver install nvidia-driver-535 

```
That is just an example. Got off of the driver names it lists as compatible with your GPU.

---

### Post by verexe on 2023-08-25
drivers:

nvidia-driver-535-open
nvidia-driver-525
nvidia-driver-418-server
nvidia-driver-535-server-open
nvidia-driver-470-server
nvidia-driver-535
nvidia-driver-470
nvidia-driver-525-open
nvidia-driver-450-server
nvidia-driver-534-server
nvidia-driver-525-server

I will try the non server drivers first.

---

### Post by oldfred on 2023-08-25
Is one recommended? That usually is the better one.

Auto install recommended.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

to see what is installed.
#What is installed
dkms status

---

### Post by verexe on 2023-08-25
I tried manually installing all the drivers. Most did not work at all. 535 and 525-open work once, but after powering down the system the error returns and ubuntu will not restart. The version given by "sudo ubuntu-drivers autoinstall" is 535.86.05. When I run dkms status, it also says (WARNING! Diff between built and installed module!) multiple times. Despite saying this however, it appears to be working with the autoinstall version, as this is the first time the system has booted successfully multiple times. I will use it for a few hours and if no issues come up, I will mark the thread as solved.

---

