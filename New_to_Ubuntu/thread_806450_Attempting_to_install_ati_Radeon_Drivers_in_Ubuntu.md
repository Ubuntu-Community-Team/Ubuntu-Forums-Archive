---
title: "Attempting to install ati Radeon Drivers in Ubuntu 8.04"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Lord Scythe on 2008-05-24
I am attempting to Install the drivers from ATI ti fix a graphics issue I have in WoW. I have managed to install wine, Get Pokerstars.com software and WoW software installed. They both work however the graphics in WoW are messed up and I know I require the Drivers from ATI.  

I went to this site:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html)

And began to follow the instructions. 

> 1) -POSIX Shared Memory (/dev/shm) support is required for 3D apps. - I am pretty sure this is there! I typed a command I found on the net and the message they said would show up did come up.  

> 2) glibc version 2.2 or 2.3 -I installed this using Synaptic Package Manager.

> 3) Linux kernel 2.4 or higher. I am sure Ubuntu 8.04 uses this kernel.2.6.24

> 4) XOrg 6.7,6.8,6.9,7.0 or 7.1; XFree86 version 4.3.  When I check SPM (Synaptic Package Manager) it says I have Xorg-dev 7.3 installed.

Note it has taken around 14 hours of research to get to this point.  I prefer attempting stuff myself before asking for help.  

Now I am not sure but I think this step may be the one I am having issues with. 

> 5) Note: If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel was built with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the 'agpgart' module loaded. - I have searched to find out how to do this but every post or web page I have checked is in Linux Geek Speak and most are for linux versions I have not heard of.  

I also tried this page for help too 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Their solution is:

> install from ati.com (latest version of drivers)

Instructions for Ubuntu 8.04 (Hardy)

To be determined.

Which I have to say was not very useful.  But At least I know it will be done in the future. 

The error I get when I actually run the ati driver program is this: 

> Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install


Anyone have any suggestions as to why this error comes up?  And is it possible for you to post step by step instructions on how to get my ati card installed.  Be advised I am very new to Linux (3 days) with some exp many many many years ago! I have a feeling this might be more advanced question than this forum may deal with.

I may have posted this in the wrong forum.  Dunno if this would be here since I am new to linux or in the general help forum!  If it is better to be placed there could a Moderator move it if needed.

---

### Post by trebor on 2008-05-25
> **Lord Scythe said:**
> I am attempting to Install the drivers from ATI ti fix a graphics issue I have in WoW. I have managed to install wine, Get Pokerstars.com software and WoW software installed. They both work however the graphics in WoW are messed up and I know I require the Drivers from ATI.  

I went to this site:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html)

And began to follow the instructions. 

 - I am pretty sure this is there! I typed a command I found on the net and the message they said would show up did come up.  

 -I installed this using Synaptic Package Manager.

 I am sure Ubuntu 8.04 uses this kernel.2.6.24

  When I check SPM (Synaptic Package Manager) it says I have Xorg-dev 7.3 installed.

Note it has taken around 14 hours of research to get to this point.  I prefer attempting stuff myself before asking for help.  

Now I am not sure but I think this step may be the one I am having issues with. 

 - I have searched to find out how to do this but every post or web page I have checked is in Linux Geek Speak and most are for linux versions I have not heard of.  

I also tried this page for help too 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Their solution is:



Which I have to say was not very useful.  But At least I know it will be done in the future. 

The error I get when I actually run the ati driver program is this: 



Anyone have any suggestions as to why this error comes up?  And is it possible for you to post step by step instructions on how to get my ati card installed.  Be advised I am very new to Linux (3 days) with some exp many many many years ago! I have a feeling this might be more advanced question than this forum may deal with.

I may have posted this in the wrong forum.  Dunno if this would be here since I am new to linux or in the general help forum!  If it is better to be placed there could a Moderator move it if needed.

To get your drivers for your graphics card working...

Go to system...
administration....
Hardware drivers...
Then enable the Driver listed there.

---

### Post by evertsfnic on 2008-05-25
Ubuntu has a great idea, but there is a problem, i try to install it in my computer, but it did not work, why? becouse of my video card.

Ubuntu need to put this driver, that they call proprietor, and codecs, like mp3, etc...........
For me the best linux distro it's FREESPIRE...
it's so easy........  
But i wish good luck to ubuntu, and tell my friends about this distro and freespire

---

### Post by Lord Scythe on 2008-05-25
> **trebor said:**
> To get your drivers for your graphics card working...

Go to system...
administration....
Hardware drivers...
Then enable the Driver listed there.

Okay I go to System and then Administration I do not see Hardware Drivers.  

I see

Authorizations
Hardware Testing
Language Support
Login Window
Network
Network Tools
Printing
Services
Software Sources
Synaptic Package Manager
System Log
System Monitor
Time and Date
Update Manager
Users and Groups

Am I missing something?

---

### Post by trebor on 2008-05-25
> **Lord Scythe said:**
> Okay I go to System and then Administration I do not see Hardware Drivers.  

I see

Authorizations
Hardware Testing
Language Support
Login Window
Network
Network Tools
Printing
Services
Software Sources
Synaptic Package Manager
System Log
System Monitor
Time and Date
Update Manager
Users and Groups

Am I missing something?

It should be between the top two.  As you do not have it try this.

Go back to administration..
go down to the package manager...
click on search...
type envy..
click on envy core and envy gtk...
click apply
After it is done installing
Go to applications...
system tools...
there you will see EnvyNG...
Click on that and it will give you the option to install driver for the hardware detected.  Click apply.  It should insall the driver you need automatically.  If it does not detect your card.  We will have to try something else.

---

### Post by Tatty on 2008-05-25
What card is it you are using?  Ati historically have poor support for their linux drivers and their official drivers dont support cards earlier than the radeon 9500.

Although, saying that, i did somehow manage to get the proprietry driver working in gutsy for a 9200.  But Im afraid i cant remember how.

---

### Post by Lord Scythe on 2008-05-25
> **trebor said:**
> It should be between the top two.  As you do not have it try this.

Go back to administration..
go down to the package manager...
click on search...
type envy..
click on envy core and envy gtk...
click apply
After it is done installing
Go to applications...
system tools...
there you will see EnvyNG...
Click on that and it will give you the option to install driver for the hardware detected.  Click apply.  It should insall the driver you need automatically.  If it does not detect your card.  We will have to try something else.


Ok I did do as you said and ran it.  It does detect my card correctly however it attempts to install the 8.3 Catalyst driver.  For my driver I need to install the 8.28.8 driver.  Even trying to install manually will not work, I only get the option to install version 8.3!

---

### Post by Lord Scythe on 2008-05-25
Found this link!

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Trying method @ substituting the driver for my specific card!  Wish me luck!

---

### Post by trebor on 2008-05-25
> **Lord Scythe said:**
> Ok I did do as you said and ran it.  It does detect my card correctly however it attempts to install the 8.3 Catalyst driver.  For my driver I need to install the 8.28.8 driver.  Even trying to install manually will not work, I only get the option to install version 8.3!

Envy just detected that as being the best fit for your card.  Go ahead and install it.  We can always uninstall if it comes to that.

---

### Post by Lord Scythe on 2008-05-25
Ok I attempted to install as you instructed and I still get error.  Here is what EnvyNG says:

> Your Graphic Card has been detected as a Radeon 8500 Series
Your Graphic Card is supported by the legacy Driver
EnvyNG ERROR: ATI's Legacy driver does not support your operating system

Thats what I get when I attempt to install!

Is it possible to get it to install a different version of driver?

It is now late and I have to be up early AM to make an appointment.  I will try back tomorrow and see what you post.  Thanks very much for your attempts at helping me.

---

### Post by trebor on 2008-05-25
> **Lord Scythe said:**
> Ok I attempted to install as you instructed and I still get error.  Here is what EnvyNG says:



Thats what I get when I attempt to install!

Is it possible to get it to install a different version of driver?

It is now late and I have to be up early AM to make an appointment.  I will try back tomorrow and see what you post.  Thanks very much for your attempts at helping me.

Try going back to your package manager

Click on settings...
repositories...
Click on the updates tab..
make sure that you have all four of the check boxes under updates checked.
Ubuntu will tell you that you have to reload as you made a change, click OK.
After that Click Reload, this will find all the new updates for your computer.  Click on mark all upgrades.  This will tell if you have any upgrades that can be done.  This may help as you may need your restricted modules in place to use the driver.

---

### Post by Lord Scythe on 2008-05-25
Ok did that step and then proceeded to retry EnvyNG.  I get the same error message that I did before. Though it is now trying to install 8.4 not 8.3.

Attempted to run the auto installer from ATI for the radeon 8500 and I still get the same error message with that too.  

I am sure my issue has something to do with this:

> Note: 	If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel was built with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the 'agpgart' module loaded. 

or this:

> Note: 	In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances. 

I am pretty sure these issues are well above my head! 

Gonna see if I can add other files to envyNG!

---

### Post by trebor on 2008-05-25
> **Lord Scythe said:**
> Ok did that step and then proceeded to retry EnvyNG.  I get the same error message that I did before. Though it is now trying to install 8.4 not 8.3.

Attempted to run the auto installer from ATI for the radeon 8500 and I still get the same error message with that too.  

I am sure my issue has something to do with this:



or this:



I am pretty sure these issues are well above my head! 



Gonna see if I can add other files to envyNG!

I know that Ubuntu drivers are not very compatible with Graphics cards older the 9500.  I was hoping these steps would take care of your problem.  It might be a good idea to go and buy a new Card.  Other than that i am at the end of my knowledge.

---

### Post by Lord Scythe on 2008-05-25
Thanks for the Help.  This is an old machine and I am upgrading to a new system this week.  I may pick up an older agp card for this machine in the future but for now I just wanted to mess around with Linux and I was told this version was easier to learn!

---

### Post by Tatty on 2008-05-25
Unfortunately I have had to go out and get a new (nvidia!) gfx card this week too, because I could not install the fglrx drivers for my radeon 9200.

Its odd though because, as I said in my last post, I was able to install them before under gutsy... although I have no idea how I did it.  I tried re-installing gutsy but couldnt get them to install this time.  I might have installed the drivers in feisty then upgraded to gutsy... i cant remember.


In conclusion, dont buy ATI.  Not until they start giving proper linux support for their hardware.

---

### Post by trebor on 2008-05-25
> **Tatty said:**
> Unfortunately I have had to go out and get a new (nvidia!) gfx card this week too, because I could not install the fglrx drivers for my radeon 9200.

Its odd though because, as I said in my last post, I was able to install them before under gutsy... although I have no idea how I did it.  I tried re-installing gutsy but couldnt get them to install this time.  I might have installed the drivers in feisty then upgraded to gutsy... i cant remember.


In conclusion, dont buy ATI.  Not until they start giving proper linux support for their hardware.

Actually ATI cards do work with hardy.  I have a 9600 that works flawlessly.  Like with everything else as technology gets old there is less and less support for it.

---

### Post by Tatty on 2008-05-25
> **trebor said:**
> Actually ATI cards do work with hardy.  I have a 9600 that works flawlessly.  Like with everything else as technology gets old there is less and less support for it.

Yes, ATI supports cards from the Radeon 9500 up.

---

