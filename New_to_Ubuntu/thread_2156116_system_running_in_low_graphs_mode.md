---
title: "system running in low graphs mode"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by okkie on 2013-06-20
I have checked all the available info on this subject and tried to use some to find myself in more trouble right now.my menue on the left is also gone.
When I upgraded to 13.04 the graphics was fine and the computer booted normal. As time went by I installed all the updates but one of them caused the graphics problem and I don't know which one.when I had the new motherboard installed they said I don't need a seperate graphs card as the onboard card is more than adequate which proved to be true.All Intell motherboard, just the background.
The first menue tells me there is a low graphics problem.The next menue offers run, reconfig, troubleshoot and exit.
only troubleshoot responds with:
fatal server error and remove /tmp/.xo-lock from the config file. xo-lock can however not be found anywhere in the file.
any suggestions will be appreciated please.
thanks.

---

### Post by Mark Phelps on 2013-06-20
It's hard to follow your monologue because you've run it together in one large block.  Best to separate out the different thoughts.

Did you have it working OK on an older motherboard, with Ubuntu 13.04 installed, and then "moved" to a new motherboard?

Did the old motherboard have the same Intel graphics as the new one?

Did you install any video drivers when it was using the old motherboard, before you moved it to the new one?

Or ... did you install fresh to the new motherboard?

---

### Post by okkie on 2013-06-21
I have been trying for years now to get a trouble free Ubuntu system up and running.Every time either an update/upgrade or 'things to do after upgrade' messes up everything. This goes hand in hand with my not being an expert and getting old I suppose.However, I struggeld with old components all along and have now decided to spend money and get all components as up to date as can be afforded which include a new Intell 4gig memory motherboard with an advanced processor, a 1t hard disk and a MSI flat screen. I Loaded 12.04 and all went fairly well until I was notified of 13.04 and I upgraded.
I have 13.04 ISO on a memory stick as I expected trouble. Maybe I should just do a new install if I can find a way to save my music, documents and photos.
I can get to a terminal which I used to sudo firefox which now enables me to correspond with you. If there is a thing called a '13.04 repair disk' I have my wife's windows computer available to download, or whatever.
This is pretty much my present state of affairs.
Thanks

---

### Post by okkie on 2013-06-21
here is the output of the config file if that will serve any purpose:lspci -nnk | grep -iA2 aphics; Xorg -version; sudo apt-get update; sudo apt-get install hwinfo mesa-utils hardinfo;  apt-cache show xserver-xorg | grep Version; xrandr; fglrxinfo; nvidia-settings -g |head -n 30 ; lspci -nnk | grep -iA2 VGA; sudo lshw -short; sudo lshw -C display; sudo hwinfo --gfxcard; dpkg -l | egrep 'fgl|intel|mesa|mesa-utils|nvidia|NVIDIA|nouveau|radeon|video-ati'; cat /etc/lsb-release; dmesg | egrep 'abort|ailed|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|NVIDIA|radeon|segment|VESA|VGA|wfb|\(EE\)|\(WW\)'; cat /proc/cpuinfo | grep -I model; cat /var/log/Xorg.0.log | egrep 'abort|ailed|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|NVIDIA|radeon|segment|VESA|VGA|wfb|\(EE\)|\(WW\)'; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; cat /etc/X11/xorg.conf; /usr/lib/nux/unity_support_test -p; sudo lsmod--------------------------------------okkie@okkie-desktop:~$  xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
okkie@okkie-desktop:~$ Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1400
No command 'Screen' found, did you mean:
 Command 'screen' from package 'screen' (main)
Screen: command not found
okkie@okkie-desktop:~$ VGA disconnected (normal left inverted right x axis y axis)
bash: syntax error near unexpected token `('
okkie@okkie-desktop:~$ LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
bash: syntax error near unexpected token `('
okkie@okkie-desktop:~$    1400x1050      60.0*+   50.0  
1400x1050: command not found
okkie@okkie-desktop:~$ [...]

---

### Post by Mark Phelps on 2013-07-01
I can't make any sense of the details because it appears you pasted the script commands as well as the results -- and they are all run together.

Please answer the questions I asked in my post -- don't just run a script.

Also, I need to know the make and model video chipset -- so open a terminal and enter "lspci" and look for the line containing "VGA" and post that info here.

---

### Post by okkie on 2013-07-01
1  00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
2 I installed 12.04 on the new motherboard and then upgraded to13.04 on the same motherboard
3 I have saved all the documents I need
4 I have 13.04 iso on disk but computer doesn't read it

thanks

---

### Post by Mark Phelps on 2013-07-01
Intel video drivers are installed by default when you set up Ubuntu; they aren't offered through Additional Drivers.

If you want to look for newer drivers, do so at the following link: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng")

---

