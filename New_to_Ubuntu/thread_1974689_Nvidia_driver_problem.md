---
title: "Nvidia driver problem"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by rajplay on 2012-05-06
Hi folks,

I just upgraded to Ubuntu 12.04 and somehow I'm not at all happy with it. I'm just running in to problems one after the other. First it was a problem with WiFi and then now with Nvidia drivers. When I install Nvidia drivers from "Additional Drivers" tool, all the colors of any videos I play(may it be in totem player/youtube videos on browser, etc.) just get screwed. I read somewhere that it might be because of the problem with the way Nvidia drivers handle hue or something. But everything seems to be fine when I remove the driver. 

Does anyone know how to get the Nvidia drivers installed without screwing up my video colors?!
 
PS : I have a dell inspiron 1520 with the following graphics card,
```

>sudo lshw -C display
*-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:fea00000-fea1ffff

```

Any help would be very much appreciated! 
Thanks in advance..

---

### Post by bogan on 2012-05-06
Hi!, **rajplay**,

 The nvidia-current driver you loaded is probably v295.40 which is bugged ,especially for 7xxx & 8xxx series cards.

From a tty text terminal, ie without the GUI screen, run ```
sudo nvidia-installer --latest
```This will not alter anything, but will tell you what is installed, and the latest available from nvidia itself.

You can then , if you wish, run ```
sudo nvidia-installer-f
```Which will un-install the existing driver and install the new one.

If you get the normal Unity GUI Screen you can get a tty login by opening a terminal and entering:```
 sudo service lightdm stop
``` and pressing Ctrl+Alt+F1, login with your username and enter your password - nothing will show - press enter, then add the above commands.

Afterwards, reboot: ```
 sudo reboot
```Chao!,** bogan**.

---

### Post by rajplay on 2012-05-06
> **bogan said:**
> 

From a tty text terminal, ie without the GUI screen, run ```
sudo nvidia-installer --latest
```

Hi bogan,
Thanks for the reply. But `nvidia-installer` returns command not found error! I could not find which package has the command!

---

### Post by Cavsfan on 2012-05-06
This is what works for me on 10.04.
Someone on 12.04 did this yesterday with success.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

---

### Post by linuxmatt7 on 2012-05-06
If you do not like Ubuntu and you are a newbie to Linux I would recommend you try Linux Mint Debian XFCE Edition. I think you will like it. If you are a advanced user than try Fedora 16, you might like it.

If you need the drivers you might want to look on CNET or some other download sites. This way you do not have use the Terminal in Ubuntu. If you constantly run into this you might want to switch to one of the above.

I have had way to much Ubuntu. Enough to make :popcorn:

---

### Post by rajplay on 2012-05-06
> **linuxmatt7 said:**
> If you do not like Ubuntu and you are a newbie to Linux I would recommend you try Linux Mint Debian XFCE Edition. I think you will like it. If you are a advanced user than try Fedora 16, you might like it.

If you need the drivers you might want to look on CNET or some other download sites. This way you do not have use the Terminal in Ubuntu. If you constantly run into this you might want to switch to one of the above.

I have had way to much Ubuntu. Enough to make :popcorn:

LOL! To be honest, I got so bugged of the issues popping up in 12.04 I even downloaded an iso of Fedora 16! but somehow I wanted to get a workaround for the problems I was facing just because I kind of get a satisfaction in solving these problems(even with a lot of help :D).. so i've decided to keep using ubuntu for a few more days atleast..(Although I'm running a VM of fedora on VirtualBox.)

---

### Post by rajplay on 2012-05-06
> **Cavsfan said:**
> This is what works for me on 10.04.
Someone on 12.04 did this yesterday with success.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

Thanks a lot Cavsfan! It worked like a charm to me too!

---

### Post by Cavsfan on 2012-05-06
> **Cavsfan said:**
> This is what works for me on 10.04.
Someone on 12.04 did this yesterday with success.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

> **rajplay said:**
> Thanks a lot Cavsfan! It worked like a charm to me too!


Happy to help! Glad to know it works with 12.04.

---

### Post by kelvin spratt on 2012-05-06
> **rajplay said:**
> Hi folks,

I just upgraded to Ubuntu 12.04 and somehow I'm not at all happy with it. I'm just running in to problems one after the other. First it was a problem with WiFi and then now with Nvidia drivers. When I install Nvidia drivers from "Additional Drivers" tool, all the colors of any videos I play(may it be in totem player/youtube videos on browser, etc.) just get screwed. I read somewhere that it might be because of the problem with the way Nvidia drivers handle hue or something. But everything seems to be fine when I remove the driver. 

Does anyone know how to get the Nvidia drivers installed without screwing up my video colors?!
 
PS : I have a dell inspiron 1520 with the following graphics card,
```

>sudo lshw -C display
*-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:fea00000-fea1ffff

```Any help would be very much appreciated! 
Thanks in advance..
If its any help I use the self same card as you with no trouble at all.
after using jockey and getting all sorts of problems.
I manually downloaded and install from the Nvidia site.
I also removed the  Nouveau display driver

---

### Post by Cavsfan on 2012-05-06
If you mean youtube videos look sort of blue tinted, just right click on the screen and click on settings and uncheck hardware acceleration.
It is called the Smurf effect. I have the same problem with that box checked.
Then close and open another video and that should fix it.

If you mean the driver, the link above should provide everything you need to know.

---

### Post by rajplay on 2012-05-06
> **Cavsfan said:**
> This is what works for me on 10.04.
Someone on 12.04 did this yesterday with success.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

Just a small alternative to shutdown the X server, I found
**sudo service lightdm stop** to be more effective compared to the **telinit 3** in the steps as
1. While rebooting, my system did not show any error saying it can't load Nvidia drivers - I manually had to get into the root shell through recovery mode
2. When in the root shell, after **telinit 3**, my keyboard started acting weird(it started inserting some characters that I didn't type at all) and so I couldn't login after that.

So instead, I logged into a tty terminal and stopped the X server using ```
sudo service lightdm stop
``` and followed the rest of your steps.

Also, the NVIDIA*.run file disabled the Noveau display driver by itself and then installed the NVIDIA driver.

---

### Post by rajplay on 2012-05-06
Thanks kelvin! I got it working!

---

### Post by Cavsfan on 2012-05-06
> **rajplay said:**
> Just a small alternative to shutdown the X server, I found
**sudo service lightdm stop** to be more effective compared to the **telinit 3** in the steps as
1. While rebooting, my system did not show any error saying it can't load Nvidia drivers - I manually had to get into the root shell through recovery mode
2. When in the root shell, after **telinit 3**, my keyboard started acting weird(it started inserting some characters that I didn't type at all) and so I couldn't login after that.

So instead, I logged into a tty terminal and stopped the X server using ```
sudo service lightdm stop
``` and followed the rest of your steps.

Also, the NVIDIA*.run file disabled the Noveau display driver by itself and then installed the NVIDIA driver.

Right, if you have previously installed a driver in this manner, you boot into recovery and go to root shell.
The only reason I mention enter **telinit 3** (and you have to give it about 15 seconds to take effect) before logging in, is that I have tried installing it without that command.
When I did, the nVidia driver installer program told me to exit the installer and enter **telinit 3** before attempting to install the driver.

I have also tried logging in first and then entered **telinit 3** and it went nuts and stop accepting commands. I had to reboot and start over.
That sounds like what you did.
Then once it is installed, you enter **sudo service gdm start** and you are looking at your regular login screen.

Only the first time you remove the default driver via **sudo apt-get --purge remove nvidia-*** you will not have to enter **telinit 3**.
But, I put it in there anyway because it is not going to hurt anything.

So, reboot, enter **telinit 3**, wait until 5-7 lines display and then login and install the driver.

---

### Post by rajplay on 2012-05-07
> I have also tried logging in first and then entered telinit 3 and it went nuts and stop accepting commands. I had to reboot and start over.
That sounds like what you did.


First time, I did do it after logging in. But later I rebooted and then tried it without logging in first. I went into to recovery root terminal from the boot options itself and there I entered **telinit 3**. It stopped various services and then gave me a login prompt where I could not enter my credentials properly.

Although I somehow got it working, I just want to know if I did anything wrong?

---

### Post by SeijiSensei on 2012-05-07
Ubuntu doesn't use runlevel 3, so using "telinit 3" to switch that level could lead to confusion.  The standard multiuser level is 2, and no distinction is made between text-mode and X as is the case in RedHat-flavored systems where 3 and 5 are used respectively. Levels 0, 1, and 6 have their usual meanings of halt, single-user, and reboot.  See [http://manpages.ubuntu.com/manpages/precise/man7/runlevel.7.html](http://manpages.ubuntu.com/manpages/precise/man7/runlevel.7.html) for details.

---

### Post by rajplay on 2012-05-07
> **SeijiSensei said:**
> Ubuntu doesn't use runlevel 3, so using "telinit 3" to switch that level could lead to confusion.  The standard multiuser level is 2, and no distinction is made between text-mode and X as is the case in RedHat-flavored systems where 3 and 5 are used respectively. Levels 0, 1, and 6 have their usual meanings of halt, single-user, and reboot.  See [http://manpages.ubuntu.com/manpages/precise/man7/runlevel.7.html](http://manpages.ubuntu.com/manpages/precise/man7/runlevel.7.html) for details.

Hi SeijiSensei,

Thanks for the info!
 [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html) -- here I read that runlevels 2-5 are same, then how could it lead to confusion?

---

### Post by SeijiSensei on 2012-05-07
I just tested and determined that I can put my system into runlevel 3 from 2 using "sudo telinit 3" with no apparent change.  I just wondered if his system "going nuts" when he entered "telinit 3" reflected something about the fact that it's not a standard level in Ubuntu.

I was so used to the more nuanced set of runlevels in RedHat that I found the absence of levels 3 and 5 in Ubuntu confusing at first.

---

### Post by kelvin spratt on 2012-05-07
> **SeijiSensei said:**
> I just tested and determined that I can put my system into runlevel 3 from 2 using "sudo telinit 3" with no apparent change.  I just wondered if his system "going nuts" when he entered "telinit 3" reflected something about the fact that it's not a standard level in Ubuntu.

I was so used to the more nuanced set of runlevels in RedHat that I found the absence of levels 3 and 5 in Ubuntu confusing at first.

sudo stop lightdm is a much better command, but you must only use these commands after you log out, or boot to the login screen then press Ctrl+Alt+f2 enter. then login and enter sudo stop lightdm etc. If you put the nvidia driver in your /home folder [do "sh NVIDIA-Linux-x86_64-295.49.run --no-x-check" without quotes run installer then reboot to load driver thats it.   Distro upgrades are also safer using this method as the xserver is not running [ala Aptosid/Siduction].

---

### Post by rajplay on 2012-05-07
> **kelvin spratt said:**
> sudo stop lightdm is a much better command, but you must only use these commands after you log out, or boot to the login screen then press Ctrl+Alt+f2 enter. then login and enter sudo stop lightdm etc. If you put the nvidia driver in your /home folder [do "sh NVIDIA-Linux-x86_64-295.49.run --no-x-check" without quotes run installer then reboot to load driver thats it.   Distro upgrades are also safer using this method as the xserver is not running [ala Aptosid/Siduction].

Thanks **kelvin**. I did follow the same steps.


> I just tested and determined that I can put my system into runlevel 3 from 2 using "sudo telinit 3" with no apparent change. I just wondered if his system "going nuts" when he entered "telinit 3" reflected something about the fact that it's not a standard level in Ubuntu.

My system also "went nuts" but instead of stopping to accept commands all together, mine just inserted characters that were never entered. For example say, if I entered a username as **abcdef** it would take the input as **abcdefr** or something like that (I never entered 'r').

So I was just wondering if by switching to runlevel 3, are any of the services responsible for keyboard I/O affected?

---

### Post by Cavsfan on 2012-05-07
The only reason I mentioned to enter **telinit 3** before logging in is from experience.
The first time you perform these steps to install the nVidia driver manually, you do not need to enter **telinit 3** because you have uninstalled the driver via **sudo apt-get --purge remove nvidia-***.

You boot up and there is no driver, you go by step 5:
5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

Then you mavigate to the directory where the driver is and install the driver.
Then enter **sudo service gdm start** and you are looking at your login screen. Mission accomplished - driver installed.

But, upon subsequent installations of the driver using this method, since there is an nVidea driver installed, you have to boot into recovery mode and drop to a root shell to install the driver.
The first time I tried to do this and when the installer got to a certain point,
[SIZE="3"][COLOR="Red"]The nVidia driver installer itself told me to quit the installation process and enter **telinit 3** and then start the installation process again.[/COLOR][/SIZE]
I am not just making these things up. I maybe should have mentioned that if it is not your first time installing the driver in this manner, you will need to enter **telinit 3** before logging in.
But, again from experience, you must enter this before logging in or you won't be able to proceed.

---

### Post by bogan on 2012-05-07
Hi!, **cavsfan**,

I have used 'sh' and the nvidia...run file dozens of times, and the few times I forgot to close down the X-server before doing so, I never got a message telling me to enter **'telinit 3**': only to exit and close the X-server.

I do not dispute what you reported, I think it probably depends entirely on your set-up and how nvidia sees it, eg what desktop manager you are using, and which distribution & version etc. or on what level you are operating.

I tried it the other day and it did nothing, I waited a good minute and got no response; I still had to enter```
 sudo service lightdm stop
```Also, I have never used the '--no-x-check' option. What does that do?

Is it an option of 'sh' ?  I could not find it in the nvidia Read.me.

Edit: Reading your last post again: how **can** you enter telinit 3 before logging in? you** have **to be logged in on my installations to be allowed access to a terminal or console: Recovery mode no longer allows you to drop to root without entering your root password.

Chao!,** bogan**

---

### Post by Cavsfan on 2012-05-07
> **bogan said:**
> Hi!, **cavsfan**,

I have used 'sh' and the nvidia...run file dozens of times, and the few times I forgot to close down the X-server before doing so, I never got a message telling me to enter **'telinit 3**': only to exit and close the X-server.

I am on Ubuntu 10.04 64 bit and I get that message if the old driver is still installed and I guess the x server is running. Not quite sure why you do not.
But, I am only entering **telinit 3** because the nVidia installer will go no further until I do. Maybe the installer program has changed and the next time you 
update your driver try to install it without stopping the x server and see what you get.
I would hope that you get the same thing I do as that would be even more perplexing if you do not.

> Also, I have never used the '--no-x-check' option. What does that do?I am not aware that I used the '--no-x-check' option on any command.

> Edit: Reading your last post again: how **can** you enter telinit 3 before logging in? you** have **to be logged in on my installations to be allowed access to a terminal or console: Recovery mode no longer allows you to drop to root without entering your root password.I am referring to booting into recovery mode and then selecting the bottom option of root shell. You get a prompt. 
I enter **telinit 3** at that point, wait several seconds until I see some feedback then enter login, then my userid and 
password and I am logged in to the console which looks like terminal.
I then navigate to where the driver is located and enter the sh command.

The link I provided in post #4 of this thread is not really mine. I simply put some links in it to provide people with a way to manually install 
a newer nVidea driver. There have been many people use it and you are the first to mention that your experience is different.

I say whatever works! As long as it works.

---

### Post by bogan on 2012-05-07
Hi!, **cavsfan**.

You Posted:> the next time you 
update your driver try to install it without stopping the x server and see what you get.
I would hope that you get the same thing I do as that would be even more perplexing if you do not.
I just tried it out with a full Gui running and this is what I got:>  NVIDIA Accelerated Graphics Driver for Linux-x86 (295.49)

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").

                                       .                                       <OK>  
  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com]("http://www.nvidia.com") Chao!, **bogan**.

---

### Post by vkmaxx on 2012-05-07
I have the similar problem. Installing drivers newer than 280.13 on 11.10 results in no graphic user interface (no xserver).
After updating to 12.04 my drivers where updated to 295.xx, and guess what - no gfx interface :(

I can't install 280.13 on 12.04 :(

BTW:
Very interesting thin it that I also can't install any driver newer than 285.xx on windows (I get "code 43" in device manager). It looks like a major problem with older nvidia cards (just google for "nvidia code 43", every one with the problem have nvidia FX, 8 or 9 series card).

I have MSI Core2Duo with mobile 8600GT nVidia card.

---

### Post by Cavsfan on 2012-05-08
> **vkmaxx said:**
> I have the similar problem. Installing drivers newer than 280.13 on 11.10 results in no graphic user interface (no xserver).
After updating to 12.04 my drivers where updated to 295.xx, and guess what - no gfx interface :(

I can't install 280.13 on 12.04 :(

BTW:
Very interesting thin it that I also can't install any driver newer than 285.xx on windows (I get "code 43" in device manager). It looks like a major problem with older nvidia cards (just google for "nvidia code 43", every one with the problem have nvidia FX, 8 or 9 series card).

I have MSI Core2Duo with mobile 8600GT nVidia card.

That is odd, my card is a Geforce 9800 GT and I am able to update the driver in Ubuntu 10.04 and windows 7 notifies me when a new driver is 
available and asks if I want to download it.

---

### Post by MickeyPilgrim on 2012-05-08
My clean install to 12.04 went very well. I get occasional horizontal distortion when scrolling, but it's shortlived. The Nvidia driver questions had scared me away from trying to improove things, but I'm braver now.

-How can I know what driver would be best? Is there a way to select the best or should I let the above directions have a chance? How will I know what driver I ended up with?

*-display               
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:fb000000-fbffffff memory:fc000000-fc01ffff

---

### Post by Cavsfan on 2012-05-08
> **MickeyPilgrim said:**
> My clean install to 12.04 went very well. I get occasional horizontal distortion when scrolling, but it's shortlived. The Nvidia driver questions had scared me away from trying to improove things, but I'm braver now.

-How can I know what driver would be best? Is there a way to select the best or should I let the above directions have a chance? How will I know what driver I ended up with?

*-display               
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:fb000000-fbffffff memory:fc000000-fc01ffff

The nVidia link will give you the latest driver: 295.49.
This thread has served it's purpose and the OP has resolved it.
You should probably open your own thread about this.

---

### Post by bogan on 2012-05-10
Hi!, **Cavsfan**,

Reverting to the[COLOR=Red] telinit3 [/COLOR]issue:

I was fussing with the Recovery mode, trying to get round the 'Read only' problem, the activate network not working, and 'Drop to root terminal' requiring a root password.

Afterwards, instead of selecting the recovery mode entry in grub menu, I high-lighted the normal 12.04 entry, pressed 'e' and added 'single' to the Linux line. That used to give the recovery menu.

Now it does not but goes direct to a request for a "Root Password for maintenance" or 'Ctrl+d' to exit to the recovery menu.

Entering the Root Password - [I had set one first to get round this] - gave me a root prompt without further log-in.

I then ran```
 nvidia-installer --latest
``` to check if the internet connection was working - it was not when I ran recovery normally - and  nvidia-installer gave the message you spoke of: "You appear to be running at Level 1 .......Please enter 'telinit3' and retry..." or words to that effect, even though graphics mode and the Xserver were not running.

So it would appear this warning depends on which level is in operation rather than on the Xserver status.

Thought you might like to know this.

Chao!, bogan.

---

### Post by Cavsfan on 2012-05-10
According to this Archlinux site, [COLOR=Red]telinit 3[/COLOR] stops the x server.

[[COLOR=blue]_https://wiki.archlinux.org/index.php/XLayout_[/COLOR]]("https://wiki.archlinux.org/index.php/XLayout")

The nVidea driver installer program is what told me to enter [COLOR=Red]telinit 3[/COLOR] before proceeding, unless you do not have any nVidia driver whatsoever installed on your system.

[[COLOR=blue]_http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
(Although this mentions 10.04, it works on any version of Ubuntu.)

It is also why the above instructions do not mention [COLOR=Red]telinit 3[/COLOR] because it assumes you are installing the driver after completely removing the default Ubuntu driver.
If the driver is completely gone, upon reboot the x server is not running.

I mention the need to enter [COLOR=Red]telinit 3[/COLOR] during subsequent driver updates from my own experience.

I do not want to argue whether [COLOR=Red]telinit 3[/COLOR] does or does not stop the x server.
In fact, I no longer care what [COLOR=Red]telinit 3[/COLOR] does.

Although it is rather nice to see that another person has witnessed the need for [COLOR=Red]telinit 3[/COLOR] besides me.

Thank you.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

