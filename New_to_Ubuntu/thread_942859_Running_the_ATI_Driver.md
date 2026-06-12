---
title: "Running the ATI Driver"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-09
I am trying to run the ATI driver that I just downloaded off the ATI Website.  I saved it to my desktop as:

ati-driver-installer-8-9-x86.x86_64.run

The Instructions on ATI's site say:

# Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
# Enter the command ati-driver-installer-8-9-x86.x86_64.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.

How do I navigate to the driver download?  I'm a noob and not sure what they mean by navigating to it in the terminal.

---

### Post by baizon on 2008-10-09
Open a Terminal (ALT+F2 and type: "gnome-terminal"), then go the the Desktop: 
```
cd /Desktop
```
then run the ATi Driver:
```
sudo ./ati-driver-installer-8-9-x86.x86_64.run
```

---

### Post by porchrat on 2008-10-09
it means go to the directory into which you downloaded the file.  How did you download it?...is the file sitting on your desktop?

If I were you I would follow this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

It works perfectly for me...you would read the part entitled "Method 2: Manual Method (installing Catalyst 8.8 or 8.9)"

but to do that you should know where you downladed that driver to.  You could always run a "find" command to find where you installed it.  Do this by opening the terminal (do that by going to "Applications" --> "Accessories" --> "Terminal") then type this into the terminal and press enter:

```
sudo find / -name ati-driver-installer-8-9-x86.x86_64.run
```

seeing as you have already downloaded the driver all you need to do is run it (as mentioned in the post before mine) and it will create some .deb files.  Then you would need to run dpkg on the .deb files that that downloaded file creates...perhaps remove the mesa drivers and then update your xorg.conf and you will be good to go.

---

### Post by RussW210 on 2008-10-09
I get the following message when I type "cd /Desktop" in the terminal:

bash: cd: /Desktop: No such file or directory

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> I get the following message when I type "cd /Desktop" in the terminal:

bash: cd: /Desktop: No such file or directory

type this:

```
cd ~/Desktop
```

---

### Post by porchrat on 2008-10-09
Actually lets rather start from the beginning...how exactly did you download the driver?  Did you use a web browser?

---

### Post by RussW210 on 2008-10-09
OK, I typed "cd ~/Desktop" then got this:

russell@russell-desktop:~/Desktop$

So I tried:

russell@russell-desktop:~/Desktop$ sudo ./ati-driver-installer-8-9-x86.x86_64.run

and got:

sudo: ./ati-driver-installer-8-9-x86.x86_64.run: command not found

then tried:

russell@russell-desktop:~/Desktop$ ati-driver-installer-8-9-x86.x86_64.run

then got:

bash: ati-driver-installer-8-9-x86.x86_64.run: command not found

---

### Post by RussW210 on 2008-10-09
Yes, Porchrat... I downloaded it straight from the ATI Website:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by RussW210 on 2008-10-09
The thing is, I am problems with the fglrx video card in the "Hardware Devices"... so I want to install the one straight from the website.

My current driver for my ATI Radeon HD 2400 keeps glitching when running 3d applications and I can't get it to stop.  Someone suggested to try the one on the ATI site.

---

### Post by porchrat on 2008-10-09
OK type this:

```

sudo apt-get update
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
cd ~/Desktop
sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy

```

obviously all one after each other on separate lines

---

### Post by RussW210 on 2008-10-09
The first thing I did was add "nv fglrx" to the /etc/default/linux-restricted-modules-common...

Then I did a "sudo apt-get purge xorg-driver-fglrx" to remove my current driver.

Now I'm trying to install the driver off the ATI website.

---

### Post by porchrat on 2008-10-09
The first line update your repositories just to make sure you download the most recent packages.

The second line installs the packages you will need to unpack and install your new driver.

The third line navigates you to your desktop.

The fourth line will unpack the driver file you downloaded (you will notice some .deb files appear on your Desktop)

---

### Post by RussW210 on 2008-10-09
OK, I put all that in - now I see a whole bunch of .deb files on my desktop:

xorg-driver-fglrx-dev_8.532-0ubuntu1_i386.deb
xorg-driver-fglrx_8.532-0ubuntu1_i386.deb
fglrx-modaliases_8.532-0ubuntu1_i386.deb
fglrx-kernel-source_8.532-0ubuntu1_i386.deb
fglrx-installer_8.532-0ubuntu1_i386.changes
fglrx-amdcccle_8.532-0ubuntu1_i386.deb

---

### Post by Nxion on 2008-10-09
> **RussW210 said:**
> The first thing I did was add "nv fglrx" to the /etc/default/linux-restricted-modules-common...

Then I did a "sudo apt-get purge xorg-driver-fglrx" to remove my current driver.

Now I'm trying to install the driver off the ATI website.


Also to let you know if I am not mistaken you also have to make it excuetable.

```
chmod a+x ati-driver-installer-8-9-x86.x86_64.run
```

Also I am just noticing, are you running a 64Bit version of Ubuntu or a 32Bit?

---

### Post by porchrat on 2008-10-09
Awesome...then you did it all correctly :)

now we need to blacklist the drivers in the ubuntu repository...open the file we need to edit using this command:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

Then add "fglrx" to the line "DISABLED_MODULES" and save the file and close that gedit window.

Note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated graphics driver" not enabled (unticked, it's totally normal, don't be freaked.

---

### Post by RussW210 on 2008-10-09
I am running a 32-bit version of Ubuntu... even though the package says x86 and x86_64... I guess it is for both.

---

### Post by RussW210 on 2008-10-09
I added "nv fglrx" to the DISABLED_MODULES... is that OK or should I just be using "fglrx"?

---

### Post by porchrat on 2008-10-09
> **Nxion said:**
> Also to let you know if I am not mistaken you also have to make it excuetable.

```
chmod a+x ati-driver-installer-8-9-x86.x86_64.run
```

Also I am just noticing, are you running a 64Bit version of Ubuntu or a 32Bit?

That is a good point Nxion!  Well spotted thankfully we haven't messed with the kernel yet :)

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> I added "nv fglrx" to the DISABLED_MODULES... is that OK or should I just be using "fglrx"?

no only add "fglrx" ...without the quotes

---

### Post by RussW210 on 2008-10-09
OK, should I run Nixon's command to make it executable or will that mess with what I have done thus far?

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> OK, should I run Nixon's command to make it executable or will that mess with what I have done thus far?

It has generated the .deb files...therefore it already was executable...you would not have been able to run it otherwise.

By the way is it a 64bit version of ubuntu that you're running?  I see you have downloaded a 64bit driver

---

### Post by RussW210 on 2008-10-09
Done... DISABLED_MODULES="fglrx"

---

### Post by RussW210 on 2008-10-09
"By the way is it a 64bit version of ubuntu that you're running? I see you have downloaded a 64bit driver"

That's just it... I selected Linux x86 on the website (not the 64-bit one) and that is the package they gave me to download.  Maybe it is for both the 32 and 64-bit?

---

### Post by RussW210 on 2008-10-09
How can I make sure I am running 32-bit... I'm pretty sure I installed the 32-bit version.

---

### Post by porchrat on 2008-10-09
Before we carry on I need to be sure you are running a 64bit ubuntu...are you? (check this by using the command "uname -a")

Just do a quick check to see if these files exist:

sudo ls /etc/modprobe.d/blacklist-restricted
sudo ls /etc/modprobe.d/blacklist-local

if they don't then that's fine (they shouldn't exist).  If they do exist you're going to have to put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration.

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> "By the way is it a 64bit version of ubuntu that you're running? I see you have downloaded a 64bit driver"

That's just it... I selected Linux x86 on the website (not the 64-bit one) and that is the package they gave me to download.  Maybe it is for both the 32 and 64-bit?

Sorry didn't read that post let me check the ATI website quick

EDIT:  OK that driver is for both 32bit and 64bit so it is fine...no worries :)

---

### Post by RussW210 on 2008-10-09
OK, I ran uname -a and got:

Linux russell-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Neither of those files that you asked me to check exist... so I guess none of this pertains to me: "If they do exist you're going to have to put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration."

---

### Post by porchrat on 2008-10-09
OK so now lets make sure you are in the Desktop directory by using this command that I'm sure you're already very familiar with by now:

```
cd ~/Desktop
```

please then post the ouput of this command so I can see the names of your .deb files (just ot be sure we load the correct ones):

```
ls -l ~/Desktop
```

---

### Post by RussW210 on 2008-10-09
Here is the output of that last command:

total 84416
-rw-r--r-- 1 russell russell 66269347 2008-10-09 16:50 ati-driver-installer-8-9-x86.x86_64.run
-rw-r--r-- 1 russell russell  6604216 2008-10-09 17:31 fglrx-amdcccle_8.532-0ubuntu1_i386.deb
-rw-rw-r-- 1 russell russell     1400 2008-10-09 17:31 fglrx-installer_8.532-0ubuntu1_i386.changes
-rw-r--r-- 1 russell russell  1346618 2008-10-09 17:31 fglrx-kernel-source_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell     9350 2008-10-09 17:31 fglrx-modaliases_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell 12010686 2008-10-09 17:31 xorg-driver-fglrx_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell    76442 2008-10-09 17:31 xorg-driver-fglrx-dev_8.532-0ubuntu1_i386.deb

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> Here is the output of that last command:

total 84416
-rw-r--r-- 1 russell russell 66269347 2008-10-09 16:50 ati-driver-installer-8-9-x86.x86_64.run
-rw-r--r-- 1 russell russell  6604216 2008-10-09 17:31 fglrx-amdcccle_8.532-0ubuntu1_i386.deb
-rw-rw-r-- 1 russell russell     1400 2008-10-09 17:31 fglrx-installer_8.532-0ubuntu1_i386.changes
-rw-r--r-- 1 russell russell  1346618 2008-10-09 17:31 fglrx-kernel-source_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell     9350 2008-10-09 17:31 fglrx-modaliases_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell 12010686 2008-10-09 17:31 xorg-driver-fglrx_8.532-0ubuntu1_i386.deb
-rw-r--r-- 1 russell russell    76442 2008-10-09 17:31 xorg-driver-fglrx-dev_8.532-0ubuntu1_i386.deb

Perfect that is exactly what we should be seeing :)

Now we need to load all of your hard work into the kernel and get you some working drivers!

Do that using this command:

```
sudo dpkg -i xorg-driver-fglrx_8.532-0ubuntu1_i386.deb fglrx-kernel-source_8.532-0ubuntu1_i386.deb fglrx-amdcccle_8.532-0ubuntu1_i386.deb

```

Let me know when you're done with this as we do need to make one or two more changes to ensure you don't have any problems.

---

### Post by RussW210 on 2008-10-09
Done.  Everything there went smooth.

---

### Post by porchrat on 2008-10-09
OK now that the drivers have been loaded we need to let Ubuntu know that it needs to use them (in place of it's rubbish ones).

To do this edit the xorg.conf file using this command:

```
sudo gedit /etc/X11/xorg.conf
```

You then need to add this section to the file.

```
Section "Device"
	[...]
	Driver		"fglrx"
	[...]
EndSection
```

Please don't include the "[...]" in your modification of the file those are just used to show you that there may be one or two other lines in between those lines.

This piece should already exist...except that "fglrx" should have something else written there...you should merely need to replace it with "fglrx" (please include the "" this time).

When you're done save the file and close the gedit window.

---

### Post by RussW210 on 2008-10-09
OK...

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

That is what was already in my Xorg.conf.

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> OK...

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

That is what was already in my Xorg.conf.

OK forgot you had an older ati driver installed before.  That is fine you don't need to edit it then.

You can now run this command to get the ati driver to use the xorg.conf file to configure itself:

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

---

### Post by RussW210 on 2008-10-09
I got the following error after entering that code:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  146 (ATIFGLEXTENSION)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  8
  Current serial number in output stream:  8

---

### Post by porchrat on 2008-10-09
Try something a little simpler:

```
sudo aticonfig --initial -f
```

---

### Post by RussW210 on 2008-10-09
Same Error:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  146 (ATIFGLEXTENSION)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  8
  Current serial number in output stream:  8

---

### Post by RussW210 on 2008-10-09
Could it be that my DISABLED_MODULES="fglrx"

Because there is quotes in there...?

---

### Post by porchrat on 2008-10-09
OK that error seems to happen sometimes...and no one seems to have an answer to it, in some cases a restart has sorted it out though.

Please note though that we have been messing with your video drivers already at this point so if **_and only if_** something goes wrong when you restart, don't panic.  You can boot the recovery mode and run: 

```
sudo dpkg-reconfigure xserver-xorg 
```

use all the default settings if it asks.

Booting to recovery mode involves using GRUB...usually involves presing ESC while your machine is booting (you will be prompted to press ESC to see the GRUB menu so don't worry it is easy to follow)...it will bring up a menu from which you can select "recovery mode".  It is sort of like windows safe mode.

When you have restarted try running this again:

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

Wether or not that is successful please post the output of this command:

```
fglrxinfo
```

Let me know what happens and remember...don't panic :)

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> Could it be that my DISABLED_MODULES="fglrx"

Because there is quotes in there...?

No that is exactly the way it is supposed to be...besides, if it doesn't work out in the end, everything that we have done can be very easily undone ...with one simple command. Although it would be great if we could get you onto the latest catalyst drivers...they rock:)

---

### Post by RussW210 on 2008-10-09
OK, the first code was successful and it had an output of:

Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5

FGLRXINFO returned:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 1.4 (2.1.7979 Release)

---

### Post by RussW210 on 2008-10-09
> No that is exactly the way it is supposed to be...besides, if it doesn't work out in the end, everything that we have done can be very easily undone ...with one simple command. Although it would be great if we could get you onto the latest catalyst drivers...they rock

Yea, that would be awesome... the only reason I am shying away from the driver in ubuntu's repositories is because 3d graphics are glitchy.  Reading the wiki website you gave me earlier in this post I read "Note that when Visual Effects (Compiz) are active, flickering and artifacts may occur in OpenGL applications and hardware accelerated video windows (particularly with R300 chipset). To prevent this, disable Visual Effects."  I was hoping this new driver would fix that flickering problem...

Is it better that I install this graphics driver or the one in the ubuntu repository as on the Wiki guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)   ?

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> OK, the first code was successful and it had an output of:

Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5

FGLRXINFO returned:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 1.4 (2.1.7979 Release)

That is awesome...it worked!  The "doesn't affect running session" just means you need to restart for the changes to take effect!  

All you need to do is restart your machine now and you will be good to go!

Congratulations you just manually installed a driver, something a lot of people battle with. :)

EDIT: By the way out of interest if for some reason you ever want to uninstall this driver there is an uninstall script in the /etc/ATI directory (I think...100% certain it is under /etc and has "ATI" in the filename).  I think it is called "uninstallATI.sh" or something but I can't remember exactly now.  Just run that script and it will be as if you never installed this thing, it will undo ALL changes so you don't have to worry about changing xorg.conf etc. again.

---

### Post by Nxion on 2008-10-09
> **porchrat said:**
> That is a good point Nxion!  Well spotted thankfully we haven't messed with the kernel yet :)

Thanks :) I didn't see the post you made where you turned it into .debs. You guys have been busy since I last check in here :)

---

### Post by RussW210 on 2008-10-09
OK, the new driver is installed and I am having the same problems as when I installed EnvyNG... my VLC player flickers now and and I can't watch movies without the Visual Effects turned off... when I had the Ubuntu ATI Accelerated Driver I could still watch videos.

Is there any way to reverse everything we just did... you said there was a command?

---

### Post by porchrat on 2008-10-09
> **Nxion said:**
> Thanks :) I didn't see the post you made where you turned it into .debs. You guys have been busy since I last check in here :)

Yea lol pretty much finished, but I'm glad for your input though if you hadn't said anything I would not have checked up on the 64bit thing and it is so important to check...turns out you downloaed one driver script and it checks your system and only unpacks the .debs that correlate to your system.  A amd64.deb if you're running that or an i386 if you're running that.  Pretty clever and foolproof if I do say so myself :)

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> OK, the new driver is installed and I am having the same problems as when I installed EnvyNG... my VLC player flickers now and and I can't watch movies without the Visual Effects turned off... when I had the Ubuntu ATI Accelerated Driver I could still watch videos.

Is there any way to reverse everything we just did... you said there was a command?

I added it to the end of post#43...but before you do that please run one last fglrxinfo for me.

EDIT: I'm sorry it didn't work out for you as the 8.9 catalyst drivers have some awesome functions.  You can always try the standard ubuntu drivers from the repository but I doubt the result will be different I'm afraid :(

---

### Post by RussW210 on 2008-10-09
Here is the fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 1.4 (2.1.7979 Release)

... it is no problem at all that it didn't really work out.  I know there are problems with ATI's drivers.  However, I really do appreciate all the help you have been giving me... you and Nixon have been really responsive and you really took some good time down to teach me a few things and I cant thank you enough...

so post #43 will reverse this?

---

### Post by RussW210 on 2008-10-09
Is "authatieventsd.sh" what you were talking about?  If so, how do I run that script from the terminal?

---

### Post by Nxion on 2008-10-09
> **RussW210 said:**
> Here is the fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 1.4 (2.1.7979 Release)

... it is no problem at all that it didn't really work out.  I know there are problems with ATI's drivers.  However, I really do appreciate all the help you have been giving me... you and Nixon have been really responsive and you really took some good time down to teach me a few things and I cant thank you enough...

so post #43 will reverse this?

That is what we are here for, to help as much as we can :)

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> Here is the fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 1.4 (2.1.7979 Release)

... it is no problem at all that it didn't really work out.  I know there are problems with ATI's drivers.  However, I really do appreciate all the help you have been giving me... you and Nixon have been really responsive and you really took some good time down to teach me a few things and I cant thank you enough...

so post #43 will reverse this?

Yup used the script myself just this week.  To get to /etc/ATI type:

```
cd /etc/ATI
```

To check the contents of the directory you are in use this command:

```
ls
```

Then to run the script (the one with uninstall in its name) use this:

```
sh name_of_script
```

where name_of_script is the name of the uninstall script

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> Is "authatieventsd.sh" what you were talking about?  If so, how do I run that script from the terminal?

No that isn't what I'm talking about...please post the ouput of this command:

```
ls /etc/ATI/
```

Then we can get an idea of which one will run...I can't remember its name and I'm not in fron tof the ubuntu machine at the moment.

---

### Post by RussW210 on 2008-10-09
Is "authatieventsd.sh" what you were talking about? If so, how do I run that script from the terminal?

And also, will it install my previous graphics driver or will I have to install that over again?

---

### Post by RussW210 on 2008-10-09
Here is everything in /etc/ati/:

amdpcsdb          atiogl.xml         control                logo.xbm.example
amdpcsdb.default  authatieventsd.sh  logo_mask.xbm.example  signature

---

### Post by porchrat on 2008-10-09
OK lets see if that uninstall is perhaps in another subdirectory that I can't recall...try this:

```
sudo find / -name "*uninstall*.sh" | grep "ati"
```

It may take a few minutes as it is going to scan the entire drive to find any shellscript with the word uninstall in the filename, then search that list again to see if any have ati in the filename.

EDIT: post the ouput if you don't mind...forgot to mention that

---

### Post by RussW210 on 2008-10-09
The code you posted didn't return anything... then I tried this:

russell@russell-desktop:~$ sudo find / -name "*ati*.sh" | grep "ati"
/etc/ati/authatieventsd.sh
/usr/share/fglrx/atigetsysteminfo.sh
/usr/share/pmi/stop-applications.sh
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/ati-powermode.sh
/usr/share/doc/xorg-driver-fglrx/examples/etc/init.d/atieventsd.sh

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> The code you posted didn't return anything... then I tried this:

russell@russell-desktop:~$ sudo find / -name "*ati*.sh" | grep "ati"
/etc/ati/authatieventsd.sh
/usr/share/fglrx/atigetsysteminfo.sh
/usr/share/pmi/stop-applications.sh
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/ati-powermode.sh
/usr/share/doc/xorg-driver-fglrx/examples/etc/init.d/atieventsd.sh

it didn't return anything because there is no file containing both uninstall and ati.  Must only come with the amd64 version...damn you ati!

---

### Post by RussW210 on 2008-10-09
"it didn't return anything because there is no file containing both uninstall and ati. Must only come with the amd64 version...damn you ati!"

Is there any other way to uninstall this new driver and get the old one back?it didn't return anything because there is no file containing both uninstall and ati. Must only come with the amd64 version...damn you ati!

---

### Post by RussW210 on 2008-10-09
Perhaps I can uninstall it by going to the synaptic package manager and unchecking xorg-driver-fglrx?

Then check the box to install again from the repository like I had it?

---

### Post by porchrat on 2008-10-09
Unfortunately I don't know...can't find anything on the net regarding it either.  You don't really need to know how to remove it in particular...just how to remove third party drivers from the kernel in general (the ati driver will become self evident as we know the names of the .deb files).  Will check again in the morning as it is getting rather late (nearly 2am) and I need to sleep as I have work in the morning.

Another way to try get around it is to install the ubuntu xorg-fglrx-driver package in synaptic ("System" --> "Administration" --> "synpatic package manager")...the Ubuntu driver should just take over from the ati one we installed just now.  You can install it like this:

```
sudo apt-get install xorg-fglrx-driver
```

It is a quick way to solve it and of course it is always easy to reverse:
```
sudo apt-get remove xorg-fglrx-driver
```

It just means that you will have the packages we installed stuck in kernel doing nothing.

Another way to remove them would be to find them in the /var/cache/apt/archives directory.  This contains a list of all .deb packages installed (through apt-get, I don't know if it will contain the ones we just loaded, but it can't hurt to check)  If they are in there it is a simple case of using:

[CODE]sudo apt-get remove name_of_package

where name_of_package is the name of the package containing those .deb files.

---

### Post by porchrat on 2008-10-09
> **RussW210 said:**
> Perhaps I can uninstall it by going to the synaptic package manager and unchecking xorg-driver-fglrx?

Then check the box to install again from the repository like I had it?

lol basically that is what I just said in my last post.  Yours is a much easier way of doing it.  Sorry I'm very command-line intensive and I try to avoid the GUI at all costs.

---

### Post by porchrat on 2008-10-09
OK I seriously need to get out of here and get some sleep, but I will check in on the thread tomorrow and see how you are doing.  So keep me posted. :)

---

### Post by dew5 on 2008-10-09
perhapps the drivers are under applications>system tools

maybe

hope this helps 

dew5.

---

### Post by RussW210 on 2008-10-09
Well I tried rebooting after reinstalling the xorg-driver-fglrx and it wont let me log in.  It doesnt even load the login screen.  I finally got in under safe mode with scripts not running but cant seem to get things going.

I am going to try removing the fglrx from DISABLED_MODULES.  Maybe it is not recognizing the old driver...

---

### Post by GeorgeVita on 2008-10-09
Hi RussW210,

I am attending this thread from your first post 3 + 1/2 hours ago! (I have ... an ATI chipset with some "flickers" on my Toshiba Laptop).

I don't have any technical advice to give you but if you need an answer and you have more time to spend, try a new thread on "Multimedia & Video" category which is more typical than the "Absolute Beginner Talk".

Use a 'catchy' title like "PLEASE HELP! I lost my ATI DRIVER & running on SAFE MODE"

As ubuntuforums.org is international you may find a person from another timezone to help!

Good Luck!

---

### Post by RussW210 on 2008-10-09
Thank you George... I was able to load up my old driver...

I actually installed the Envy version, then uninstalled Envy and then checked my ATI Accelerated Graphics Driver lol.

The only problem I seem to be having now is that my Cairo Dock at the bottom of my desktop is a bit unresponsive... do you have any idea?

---

### Post by RussW210 on 2008-10-09
I fixed the Cairo Dock problem.  Just closed and opened it again.  Everything seems to be back to normal now.  It's good to know other people are monitoring the conversation too... I can't believe it wen't on that long!  Only to uninstall everything and start from scratch =/  The temporary fix for my 3d graphics flickering would be to uncheck custom visual effects and go to none.  I will have to live with that for now I guess =/

---

### Post by porchrat on 2008-10-10
Hi Russ

I came back to check up on you, but I see you have it all covered.  I'm sorry the new drivers didn't work out for you.  I know the ATI drivers are not yet perfect (I personally run a HD4850 on which the fan just won't run unless I manually tell it to run on each startup), but they are getting better and better with each version.  That and a new version of the driver becomes available once every couple of months.  Eventually they will solve you r issues I'm sure.

At least you managed to learn something about dpkg, build-essential and a few of the other packages on ubuntu.  That in the end is half the fun of Ubuntu.

Best of luck for the future :)

---

### Post by RussW210 on 2008-10-10
Thank you again porchrat... luckily I got everything to run back like normal.  Still can't get 3d games to work properly.  I turn virtual desktop effects off and I am able to interact with 3d games using the keyboard but my mouse wont even mouse over the window, it just hides behind =/

---

### Post by RussW210 on 2008-10-10
One thing I didn't understand porchrat... why did I add "fglrx" to the DISABLED_MODULES when I was later adding "fglrx" to the Xorg.conf file for my driver?

---

### Post by sdowney717 on 2008-10-10
flickering video on VLC means set the video output module to x11.
that fixed mine in the past.

I will never buy another ATI card again. always a problem, an nvidia card I had laying around worked perfectly.

---

### Post by porchrat on 2008-10-10
> **RussW210 said:**
> One thing I didn't understand porchrat... why did I add "fglrx" to the DISABLED_MODULES when I was later adding "fglrx" to the Xorg.conf file for my driver?

Basically it means that the fglrx module that is contained in the "linux-restricted-modules" package is not no longer enabled, but another fglrx module (the ATI catalyst 8.9 module) is being used.

Hope that clears up any confusion.  In other words it disables the default linux ATI drivers, allowing the manually installed ones to take over.

By the way I looked it up and uninstalling xorg-fglrx-driver package from synaptic should have worked to properly remove the drivers.  I have no idea why it didn't work, as all you are doing is replacing the xorg-fglrx-driver package with this manually installed one.

EDIT: This is probably a better description: The file that you edited (adding that line to) has the filename /etc/default/linux-restricted-modules-common and as you can see from the filename, it only has to do with "linux-restricted-modules", not the modules that have been manually installed by you, so by adding the "fglrx" to that file you were basically saying disable "fglrx" from the "linux-restricted-modules" module.

---

### Post by RussW210 on 2008-10-10
I got you now porchrat, thank you for clearing that up.  I believe uninstalling and reinstalling the xorg-fglrx-driver from the synaptic package manager didn't work because I didn't have the "ATI Accelerated Graphics Driver" checked under Hardware Drivers, and because "fglrx" was still a restricted module.  So I had a driver installed that was being restricted by DISABLED_MODULES="fglrx".  All good now though.  Hopefully in the future ATI can fix this driver problem... but do either of you think it is worth it to buy a NVIDIA Graphics Card?  I can get a good one for $80:

ASUS EN9600GT TOP/HTDI/512M GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

    * Chipset Manufacturer: NVIDIA
    * Core clock: 720MHz
    * Stream Processors: 64
    * Memory Clock: 1800MHz
    * DirectX: DirectX 10
    * OpenGL: OpenGL 2.0
    * HDMI: 1 via Adapter
    * DVI: 2

........ but is that even much of an upgrade over my ATI Radeon 128MB 2400 HD?

---

### Post by sdowney717 on 2008-10-10
yes, nvidia works better!
many people on these forums will tell you this.

I have one box running ibex using the free radeon driver, which has 3d and compiz working on an x1300.
nothing but disappointment's with ATI fglrx for me.

---

### Post by RussW210 on 2008-10-10
I have tried 3 ATI Drivers thus far for my Radeon HD 2400 Pro 128MB:

FGLRX = glitching with Google Earth, 3d Screen Savers, SuperTuxKart, etc.

Driver off ATI Website = Glitching with VLC Media Player and all videos/music

Driver off Envy = Glitching with VLC Media Player and all videos/music

The problem I'm having is I want to make sure the Graphics Card fits into my Dell Inspiron 530.  I was told to look out for the prongs and make sure I get the right connector.  I think my Graphics Card is PCI-e, but is there a way I can tell using the terminal or some software in Ubuntu?  I don't want to buy a graphics card and not have it compatible.  My computer is 1 month old.

---

### Post by porchrat on 2008-10-10
> **RussW210 said:**
> but do either of you think it is worth it to buy a NVIDIA Graphics Card?

Honestly...I'll be the first to admit that ATI has a lot of problems and that traditionally nvidia has been the best card to buy for Linux support (regardless of distro), however I believe that is changing.  Ever since it was bought by AMD, ATI has changed it's attitude towards Linux.  Drivers are now available and ATI is becoming more and more open-source-conscious.

As an example their firestream technology allows the use of the Brook language to program for GPU computing, while nvidia remains very closed-source on this front, erring on the side of their own language CUDA.

So for now I think nvidia is probably going to be a little more hassle-free, but in 6 months time I really believe it will be the other way around.  ATI is adding more and more functionality every day.  Another example is that you can now run ATI Crossfire in linux, something that wasn't possible until very recently.

It is something you will need to research and decide for yourself on though.

P.S. God $80 I envy you...in my country I pay a lot more than that.  More like $150 dollars for the same card.

---

### Post by porchrat on 2008-10-10
By the way Russ have you tried this suggestion?

> **sdowney717 said:**
> flickering video on VLC means set the video output module to x11.
that fixed mine in the past.

I will never buy another ATI card again. always a problem, an nvidia card I had laying around worked perfectly.

---

### Post by RussW210 on 2008-10-10
I haven't tried the x11... since I don't get flickering VLC movies on the older repository fglrx.  To test x11 I would have to go through installing the new driver again (this time I would probably install it through Envy though) and see if that works.

How would I set the video output module to x11?

I was looking at the NVIDIA card on NewEgg.com.  They have some spectacular deals there.

Let me ask you a question that I know has had a ton of debate... does restarting your computer multiple times throughout the day testing all these updates hurt the system (hard drive, etc)?  I just like to play it careful with my hardware!

---

### Post by porchrat on 2008-10-10
> **RussW210 said:**
> I haven't tried the x11... since I don't get flickering VLC movies on the older repository fglrx.  To test x11 I would have to go through installing the new driver again (this time I would probably install it through Envy though) and see if that works.

How would I set the video output module to x11?

I was looking at the NVIDIA card on NewEgg.com.  They have some spectacular deals there.

Let me ask you a question that I know has had a ton of debate... does restarting your computer multiple times throughout the day testing all these updates hurt the system (hard drive, etc)?  I just like to play it careful with my hardware!

Your machine is designed to be restarted.  Personally I always prefer the good old complete shutdown with a cold boot after 12 or 13 seconds.

---

### Post by Nxion on 2008-10-10
> **RussW210 said:**
> I have tried 3 ATI Drivers thus far for my Radeon HD 2400 Pro 128MB:

FGLRX = glitching with Google Earth, 3d Screen Savers, SuperTuxKart, etc.

Driver off ATI Website = Glitching with VLC Media Player and all videos/music

Driver off Envy = Glitching with VLC Media Player and all videos/music

The problem I'm having is I want to make sure the Graphics Card fits into my Dell Inspiron 530.  I was told to look out for the prongs and make sure I get the right connector.  I think my Graphics Card is PCI-e, but is there a way I can tell using the terminal or some software in Ubuntu?  I don't want to buy a graphics card and not have it compatible.  My computer is 1 month old.


If your machine is only a month old. I am 100% sure you have a PCI-e (PCI EXPRESS) connection. So if you decide the byu the NVIDIA card then it WILL work. I was looking at buying that model computer a while ago. It is a sweet machine.

---

### Post by Nxion on 2008-10-10
If the machine is only a month old than the card you wanted to get from NewEgg should be fine. Your machine has a PCI-E connection, I am positive of that. Most machine now come with that, No more AGP. I think it is a sweet machine. I want one :)

---

### Post by Nxion on 2008-10-10
Excuse the double quote. my post wasnt showing up at all so I thought it didnt save it.

---

### Post by RussW210 on 2008-10-11
Yea, I love the computer.  Got a good deal and only ended up paying around $943 after taxes and shipping.  The graphics card thing drives me nuts though.

---

### Post by Nxion on 2008-10-11
> **RussW210 said:**
> Yea, I love the computer.  Got a good deal and only ended up paying around $943 after taxes and shipping.  The graphics card thing drives me nuts though.

I know how you feel, ATI can be a pain, but they arr getting better. I myself will alway choose Nvidia over ATI, For me I never had any trouble and there just seems to be more support for Nvidia ranter than ATI.

---

### Post by RussW210 on 2008-10-11
Well, I figured it out!

The fglrx in the repository wasn't working well.  So I used Envy to install the new driver.  VLC Media was glitchy but someone suggested to use X11 video output and it plays flawless.  And now I can use the Fusion Icon to select Metacity whenever I want to run 3d Graphics without a hitch.  AWESOME!!!

Sucks I have to switch to Metacity but at least it is working!

---

### Post by Nxion on 2008-10-11
> **RussW210 said:**
> Well, I figured it out!

The fglrx in the repository wasn't working well.  So I used Envy to install the new driver.  VLC Media was glitchy but someone suggested to use X11 video output and it plays flawless.  And now I can use the Fusion Icon to select Metacity whenever I want to run 3d Graphics without a hitch.  AWESOME!!!

Sucks I have to switch to Metacity but at least it is working!


That is awesome, I'm glad it is working for you, Are you still going to buy the card, or just use the ATI for now?

---

### Post by RussW210 on 2008-10-11
Now that I got this working, I will stick with ATI... someone told me that down the line they will get the drivers right and with this temporary fix I can pretty much get everything to run except 3d screensavers (will still be glitchy because I leave my computer with Compiz on...

If it gets intolerable again, I might go ahead and buy a NVIDIA.

---

### Post by Muffinabus on 2008-10-11
This thread helped A LOT.  I had previously installed the ATI drivers with little to no success, this I did in 10 minutes and worked flawlessly.  Just thought I'd mention that and post so I can refer to the thread later if need be (:

---

### Post by markbuntu on 2008-10-11
With some cards, you can fix the flickering windows by using the TexturedVideo "off" option. I used this with previous drivers and it worked for my HD3650 card but I have been preoccupied with other things and have not tried any tweaking of the 8.8 or 8.9 driver. 

There are some other tweaks here that can be tried, just be aware that these are not official and may cause you problems and this OP has not been updated since 8.6:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by Maheriano on 2008-10-11
I tried running this same tutorial on the driver I downloaded from the ATI website and got to here:
```
sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy
```

Where I got the error:
```
deemar@chugger:~/Desktop$ sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/hardy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/hardy
Requested package is not supported.
Removing temporary directory: fglrx-install
deemar@chugger:~/Desktop$ 

```

---

### Post by porchrat on 2008-10-12
> **Maheriano said:**
> I tried running this same tutorial on the driver I downloaded from the ATI website and got to here:
```
sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy
```

Where I got the error:
```
deemar@chugger:~/Desktop$ sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/hardy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/hardy
Requested package is not supported.
Removing temporary directory: fglrx-install
deemar@chugger:~/Desktop$ 

```

What graphics card are you running?

---

### Post by porchrat on 2008-10-12
Just thought I would add...92 posts! That's amazing!

By the way Russ I am so glad you finally got everything sorted out.

---

### Post by RussW210 on 2008-10-12
Hey porchrat... yea, I'm real happy too.  You helped me out and got me interested in getting the new driver installed.  I think i might have got my cairo-dock problem fixed (it would freeze sometimes on startup)... the command in sessions was "compiz" instead of "compiz --replace"... now I have restarted twice and haven't noticed anything.  94 posts IS amazing!

---

### Post by porchrat on 2008-10-12
> **RussW210 said:**
> Hey porchrat... yea, I'm real happy too.  You helped me out and got me interested in getting the new driver installed.  I think i might have got my cairo-dock problem fixed (it would freeze sometimes on startup)... the command in sessions was "compiz" instead of "compiz --replace"... now I have restarted twice and haven't noticed anything.  94 posts IS amazing!

That's what this community is here for, luckily there are so many people that are passionate about Linux, that you will always receive advice and help.  I was lucky to find that ATI guide quickly, however my first time around with an ATI driver it took me 3 attempts,using 3 different methods before I got it right. :p

---

### Post by porchrat on 2008-10-12
There are over a thousand views on this thread!

It has become like an ATI installation guide for people lol.

---

### Post by Nxion on 2008-10-12
> **porchrat said:**
> There are over a thousand views on this thread!

It has become like an ATI installation guide for people lol.

Awesome!

---

### Post by Maheriano on 2008-10-13
> **porchrat said:**
> What graphics card are you running?

I'm happy you came back to help me! Thanks! I got the ATI Radeon 9250 with VGA/DVI/S-video out......PCI.

---

### Post by porchrat on 2008-10-13
> **Maheriano said:**
> I'm happy you came back to help me! Thanks! I got the ATI Radeon 9250 with VGA/DVI/S-video out......PCI.

OK a moment of searching and I already know what your problem is.  You can't use the new catalyst 8.9 drivers as your video card is too old.  The link for the drivers you need is here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run")

Unfortunately they won't unpack for you because as you can see your hardware is not supported by this driver:

> Requested package is not supported.


Sorry about that :(

---

### Post by porchrat on 2008-10-13
Just a note for all those reading this in the future.  You can find out which driver is best suited for your card by visiting this page and filling in the details of your card:

[http://ati.amd.com/support/driver.HTML]("http://ati.amd.com/support/driver.HTML")

---

### Post by bobnutfield on 2008-10-13
Excellent guide for getting these drivers.  Since I am running Intrepid, it would be nice to know WHEN we will get the drivers for the new Xorg.  The open source radeon is mildly adequate. but no where near the performance I got with Hardy and the fglrx driver.

---

### Post by seatownflyer on 2008-10-14
I followed all the directions to the letter and everything went smoothly until I executed fglrxinfo.  I got this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I have a Radeon X1950 Pro.  I chose the X1900 series driver from the ati website.  I rebooted and got a message saying i was in low res mode and the server couldn't detect my monitor or video card.  I put everything back to defaults via the recovery mode but I'd like to get this driver working if possible.  any suggestions?

Thanks

---

### Post by porchrat on 2008-10-14
> **seatownflyer said:**
> I followed all the directions to the letter and everything went smoothly until I executed fglrxinfo.  I got this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I have a Radeon X1950 Pro.  I chose the X1900 series driver from the ati website.  I rebooted and got a message saying i was in low res mode and the server couldn't detect my monitor or video card.  I put everything back to defaults via the recovery mode but I'd like to get this driver working if possible.  any suggestions?

Thanks

You need to remove the Mesa drivers.  It is covered in the guide I posted, but basically the summary is that you need to use this command:

```
sudo apt-get remove xserver-xgl
```

That unfortunately is luck-of-the-draw.  Some machines stop using the mesa after you install the drivers, while some don't and the mesa drivers need to be removed.

---

### Post by seatownflyer on 2008-10-14
> **porchrat said:**
> You need to remove the Mesa drivers.  It is covered in the guide I posted, but basically the summary is that you need to use this command:

```
sudo apt-get remove xserver-xgl
```

That unfortunately is luck-of-the-draw.  Some machines stop using the mesa after you install the drivers, while some don't and the mesa drivers need to be removed.

oops, guess i should have read the guide.  well I went back and read the guide, noticed I forgot to edit the blacklist-local file and add the # in front of "blacklist-fglrx".  So I did that, completed the rest of the steps, which went smoothly, rebooted and now I just get a black screen. I can use ctrl-alt-delete and the system will restart at this point.

After using the recovery mode and selecting the repair X server option I can get back into my desktop.  However, fglrxinfo still says the mesa drivers are being used.  I did the apt-get remove xserver-xgl but it says its not installed.  

checking the hardware drivers under the system-adminstration menu shows that the ATI accelerated graphics drivers are in use (green checkmark) and the enabled button is not checked.

/confused!

---

### Post by porchrat on 2008-10-14
> **seatownflyer said:**
> oops, guess i should have read the guide.  well I went back and read the guide, noticed I forgot to edit the blacklist-local file and add the # in front of "blacklist-fglrx".  So I did that, completed the rest of the steps, which went smoothly, rebooted and now I just get a black screen. I can use ctrl-alt-delete and the system will restart at this point.

After using the recovery mode and selecting the repair X server option I can get back into my desktop.  However, fglrxinfo still says the mesa drivers are being used.  I did the apt-get remove xserver-xgl but it says its not installed.  

checking the hardware drivers under the system-adminstration menu shows that the ATI accelerated graphics drivers are in use (green checkmark) and the enabled button is not checked.

/confused!

Could you post the ouput of this command for us please:

```
cat /etc/X11/xorg.conf
```

I just want to see what driver it is using there.

I know it is sort of a return to basics, but I think we should start with what you did, and then decide what you still need to do to get this sucker working.

---

### Post by seatownflyer on 2008-10-14
> **porchrat said:**
> Could you post the ouput of this command for us please:

```
cat /etc/X11/xorg.conf
```

I just want to see what driver it is using there.

I know it is sort of a return to basics, but I think we should start with what you did, and then decide what you still need to do to get this sucker working.

Here is the conf file that is currently working properly.  i.e. after 'fixing' the xserver via the recovery method.

[I]# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
[/I]

Here is the conf file that causes the black screen after I follow the guide for installing the ATI driver.

[I]# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
[/I]

Thanks for the help!

oh, an edit on this post.  
After a reboot and selecting the normal bootup via grub the system now goes into low res mode.
Rebooting again then going into the recovery mode and choosing to fix the xserver then selecting resume normal boot will allow it to boot into normal res mode with the ati driver listed as "in-use" but the enable box not selected.  fglrxinfo still reports the mesa drivers.

if i reboot again and select normal boot method then it goes into low res.  so the only way i can get it to boot into a normal resolution is to go through the recovery console and have it redetect everything for the xserver then select resume boot.  maybe i should start over on a fresh install?  i dont know.

---

### Post by sdowney717 on 2008-10-14
xv video output, compiz and fglrx dont work together.

the reason x11 video output works when playing videos with compiz running is it does not use accelerated video out xv 
But you can use xv video output with the free drivers.

you know what, you can completely remove everything from xorg.conf and it will autodetect and use the free drivers. Even though xorg now autoconfigs monitors and resolutions. it is not 100% reliable.

Depending on your card and what you want to do, they might be good enough!
but you must get rid of any nvidia and fglrx packages.
And then you can tweak xorg adding in things to see how it goes.

you can read thru xorg.log in /var/log and see what is going on. 'EE' signals an error has occured and sometimes researching the error can point you to a solution.

With Ibex, you can run compiz on the free drivers. I am doing it!
I have several machines running various versions of fglrx and the free drivers right now.
this is my xorg.conf

```


Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "off"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "1"
        Option		"EnablePageFlip"
        Option 		"ColorTiling"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"        
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "ServerFlags"
   Option "IgnoreABI" "True"
EndSection

```

here is my glxgears with an ati x1300 on ibex with free driver

```


with compiz
scott@scott-desktop:~$ glxgears
10874 frames in 5.0 seconds = 2174.797 FPS
11112 frames in 5.0 seconds = 2222.229 FPS
11089 frames in 5.0 seconds = 2217.660 FPS
11111 frames in 5.0 seconds = 2222.122 FPS

with metacity
scott@scott-desktop:~$ glxgears
9773 frames in 5.0 seconds = 1954.399 FPS
10109 frames in 5.0 seconds = 2021.653 FPS
9919 frames in 5.0 seconds = 1983.772 FPS
9779 frames in 5.0 seconds = 1955.646 FPS
10523 frames in 5.0 seconds = 2104.406 FPS


```

---

### Post by porchrat on 2008-10-15
sdowney what card are you running?  I get half of that on a laptop with an X1250 (not my main machine) running 8.04 with the catalyst drivers.

There are plenty of guides out there for mesa drivers, unfortunately I've never suffered from the mesa problem before...well OK I did once, but a quick removal of the drivers (as I mentioned above) solved the problem.  So unfortunately seatownflyer this is a question I don't have the answer to. :( I will look into it though and I don't want to be caught unawares when it happens to me (and it will as it is quite common)

---

### Post by seatownflyer on 2008-10-16
BINGO!  I got it!  I followed some of the steps from this post.

> **SpaTule said:**
> Solved for me ! :tongue:

But I didn't follow my previous method. 

I've just change the Agp texture Size in BIOS to 128Mo. It works with 32, and 64 too but not with 256Mo. (My card is a PowerColor 1950 pro AGP 512Mo)

And I ve edited my kernel options in menu.lst like this :

```
title		Debian GNU/Linux, kernel 2.6.25-2-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.25-2-686 root=UUID=9abeaf31-f7dd-4db1-bf38-79601a8a6ff6 ro quiet [COLOR="Red"]**vmem=512**[/COLOR]
initrd		/boot/initrd.img-2.6.25-2-686
```

And xorg.conf

```
Section	"ServerFlags"
	Option "AIGLX" "on"
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "XVideo" "off"
EndSection

```

*Option	    "XVideo" "off"*  otherwise video don't work with compiz-fusion


I use 8.50.3v for fglrx driver. It's the lenny repository version


All I did was change my AGP texture size to 512.  Nothing else.  mine was already set to 128.  as far as installing the driver, I just did it via the system->administration->hardware drivers menu.  I just used the proprietary drivers.  works fine.

---

### Post by cupcake4170 on 2008-11-27
Thanks for the information

---

