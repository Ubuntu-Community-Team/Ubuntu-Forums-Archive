---
title: "[SOLVED] error accessing digital camera"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by stevek123 on 2008-11-05
I just tried to attach and access/use my digital camera to my ubuntu 8.04 system for the first time. I guess i was first surprised that it didnt 'mount' like my mp3 players. It did detect the camera and identify it. It gave me a menu to 'import pictures from detected camera' thru fspot import. When I went ahead it gave me an error message = could not claim the USB device while connecting to camera (no message code or number with it). I tried also with gthumb image viewer and got the same message - but it included this also 

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

I'm still a noob at ubuntu/linux and dont have any idea how to check this. FWIW, the camera is a Kodak C533. How do I get my camera functions operational?
Steve

---

### Post by chrisod on 2008-11-05
When I've seen that error in the past a simple reboot solved it for me. Did you try that? Also check properties on the camera once it's mounted and make sure that you have read/write access to it.

---

### Post by stevek123 on 2008-11-05
? ... reboot with the camera attached and on? or just a std reboot?

If this camera is mounted I sure dont see it. It does not show up in my 'places' menu....

---

### Post by Bölvaður on 2008-11-05
<added>
What I wrote below is wrong.
Make sure the camera is sending signals to the computer which alowes it to mount. Some cameras have "connect" button on them that gives access to the harddisk.
</added>

Was this camera improperly disconnected from windows the last time you used it?
You may need to use "safely remove" on windows in order for ubuntu.
If that would be the problem it actually should have given you very detailed error message, so this might not be it, worth checking though.

Also check if you can access the camera from nautilus (file manager)

---

### Post by stevek123 on 2008-11-05
I looked in system->preferences->hardware info and my camera and a fair amount of data about it are logged there (kodak easyshare c533 digital camera with usb interface.....)  . It does not show up in my places menu as a mounted usb device and does not show up on the desktop like my mp3 players. there is no 'connect' button and my comp sees that it is there as soon as I turn it on - just wont access the kodak as I stated above...

---

### Post by philinux on 2008-11-05
This is a problem with 8.04 I had to buy a card reader.
[http://www.amazon.co.uk/Hama-USB-2-0-Card-Reader/dp/B000IH1W20](http://www.amazon.co.uk/Hama-USB-2-0-Card-Reader/dp/B000IH1W20)
For the price marvellous.

Having seen this thread made me realise I had some pics to transfer. However I'm on Intrepid now so I plugged in the cam, Canon G5 and a nice little camera icon popped up on the desktop. I've got preference set to do nothing in nautilus. Bingo the bug got fixed.

However I unmounted it to use gthumb and guess what, the timestamps got todays date. So i raised a bug. Nautilus copied them fine with the October dates.

---

### Post by chrisod on 2008-11-05
My camera is a Kodak EZ Share and it just works with 8.04. I've never done anything beyond plug it in. I have seen that error message once or twice - disconnecting the camera and rebooting solved it.

---

### Post by stevek123 on 2008-11-05
I tried rebooting with the camera disconnected and got the same error message. I tried rebooting with the camera attached and on - and got the same error message.   I may end up trying Phil's idea of a separate card reader, as these pics are on the inserted 2G mem card... I havent checked if it will work with pics in internal memory instead of the card.... that mat make a difference (it does with my sansa260 mp3 - but on that it reads the card only - firmware is not linux compatible...)
any other suggestions out there???
Steve

---

### Post by RJARRRPCGP on 2008-11-05
I get an error, too, but it's the following error message:

```
Error stating file '/home/rjarrrpcgp/Photos': No such file or directory
```

But after turning the camera off then back on, I then saw a photo appear in F-Spot! 

Thus, it looks like I don't require Windows and .Net framework 2.0 anymore! Hooray!

---

### Post by stevek123 on 2008-11-05
FWIW, I changed the camera setting to 'internal memory' and tried again with the same result. I went and added the libgphoto-dev files thru Synaptic to see if they would help - and they did not. I looked in System->HardwareInfo and when camera is on it is listed as usb device thru HAL with all of the device ID info you could want. It still does not show up on my computer at all in the Places menu. Not sure what to do next???.... guess I may be stuck with Phil's idea......

I think this may be an issue with the camera not mounting. I'm a windoze convert and very unfamiliar with use of terminal. Is there a way to manually mount from terminal? If so, what commands would I use?

---

### Post by stevek123 on 2008-11-19
bump
(if this action is inappropriate for the ubuntu forums I am sorry....still havent gotten this worked out...)

---

### Post by timcredible on 2008-11-19
what program are you using to access the camera?  ubuntu recognizes most cameras and won't mount them as an external drive, but lets photo programs access it as a camera.  try using digikam for this.  if that doesn't work, try setting the camera to a different usb mode, most all cameras have 2 different usb modes.

---

### Post by stevek123 on 2008-11-26
ok ... so i installed digikam and tried that too. It detected the camera immediately and identified it using 'add camera' and 'autodetect'. When I went to browse the 'usb media' in the 'Camera' dropdown menu, it said there were images detected on the camera, and it went to download them. It gave me a popmsg that read 'failed to connect to camera' with options to retry or abort (progress bar showed 19% completion every time I tried). I tried reconnecting thru digikam with camera on before attach and without... same results.

this is a Kodak C533 easyshare and it works fine in winXP - I searched the internal menus and didnt see any way to change usb modes. 

Other ideas?

---

### Post by unutbu on 2008-11-26
Good news: The Kodak C533 is on the list of gphoto2 supported cameras:
[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Given your experiences with fspot and gthumb, I don't have a lot of confidence this will work, but perhaps it is worth a try:

Click on Applications>Accessories>Terminal to open a terminal. Then type
```
mkdir ~/images              # makes a directory called images
cd ~/images                 # changes directory  

```
Try either of these commands:
```

gphoto2 --port usb --camera "Kodak C533" -P      # hopefully downloads pictures
gphoto2 --port usb: --get-all-files
```

Not all cameras are mountable. Nevertheless, the gphoto2 command should allow you to download pics from supported cameras.

Although it is not absolutely necessary, some people choose to avoid this problem by buying a USB card reader. The USB card reader makes any card mountable, just like a hard drive.

Edit: Try the above command with the camera set to PTP generic.

---

### Post by stevek123 on 2008-11-26
I redid camera menus - definitly no way to change setting for usb type - i.e. to mtp... so back to digikam. I tried a couple of different camera settings in the 'add camera' menu (PTP generic, mtp, kodak 530, kodak 533) and got the same error msg every time. FWIW, the camera didnt like all this and I had to pull the battery and reinstall to get it to turn on.

---

### Post by stevek123 on 2008-11-26
Unutbu, I installed gphoto2. and it ran as below...

steve@ubuntudesktop:~$ gphoto2 --port usb --camera "Kodak C533" -P
                                                                               
*** Error ***              
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
*** Error (-53: 'Could not claim the USB device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --port "usb" --camera "Kodak C533" -P

Please make sure there is sufficient quoting around the arguments.

steve@ubuntudesktop:~$ env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --port "usb" --camera "Kodak C533" -P
                                                                               
*** Error ***              
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
*** Error (-53: 'Could not claim the USB device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --debug --debug-logfile=my-logfile.txt --port "usb" --camera "Kodak C533" -P

Please make sure there is sufficient quoting around the arguments.

steve@ubuntudesktop:~$ 

As far as i can tell from system->preferences->hardware info, it is not 'being used' as sd#. I have no clue how to look for permissions for unmounted devices. It would be best if I could get it to mount but dont know how.

---

### Post by unutbu on 2008-11-26
Hm. The error message seems to imply that some other program is trying to access the camera. 

Perhaps try this: shutdown the machine. Unplug the camera. Reboot the machine. Log in. Plug in the camera, then turn it on. When GNOME asks you if you want to download the pictures using fspot some other app, say no. Open a terminal and then try the gphoto2 command again.

Do you get the same error?

---

### Post by stevek123 on 2008-11-26
yep... & I looked at the error msg again... its not the kernel blocking it or it would show as mounted (thats the sd#...) It says another prog may be using it - I've no clue how to chekc that. Also says error in io-library - any way to read this as text? where is it?

---

### Post by unutbu on 2008-11-26
[http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb](http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb)

---

### Post by stevek123 on 2008-11-27
Hey !!! that link looks like its what I need.... BUT, when I ran up to gedit and opened the file that is to be editted, its empty. I looked in Places->Comp->filesystem->etc->udev->rules.d it is not listed there either. I dbl checked in Synaptic and it shows I've installed libgphoto2-2 and the -dev and -port0 progs... but no 'rules' folder that matches libgphoto2. There are similar looking folders under the '45' class rules = liblip, libmtp, libnjp for usb devices, but when I read these, they dont look like they include any of the HUGE kodak list of products that should be similar. Not sure what to do next. It appears I'm missing some prog files that this camera may need...

---

### Post by unutbu on 2008-11-27
I'm not sure why you are missing /etc/udev/rules.d/45-libgphoto2.rules.

Attached you will find mine.

---

### Post by stevek123 on 2008-11-27
THAT was the solution!!! Thanks unutbu!

I downloaded and opened the rules file you supplied. (seems odd that it wasn't in my library). I could see that my camera was included in the list - thanks to the link you supplied earlier (when I searched earlier in this thread I didnt find that thread :shrug:). so... I used Nautilus and copied the supplied 'rules' file into the path /etc/udev/rules.d. When I turned on the camera it accessed the files/images automatically and without a glitch.

Best Regards & Happy Thanksgiving unubtu!
Steve
11/27/08

---

