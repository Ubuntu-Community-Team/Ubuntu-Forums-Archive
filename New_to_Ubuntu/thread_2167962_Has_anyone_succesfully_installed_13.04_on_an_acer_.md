---
title: "Has anyone succesfully installed 13.04 on an acer aspire 5336-2524?"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by mawil10132 on 2013-08-15
Has anyone successfully installed 13.04 on an acer aspire 5336-2524?

I was here a year ago when trying to install 12.04 without success, blank screen issue which was beyond my abilities.

Before agonizing over the same issues with 13.04 I was hoping to get some positive input. I have no technical experience with linux. I've had older desktops that ran older versions of ubuntu with zero problems. But got slammed when I bought the aspire laptop.  Haven't worked with ubuntu since.

---

### Post by su:bhatta on 2013-08-16
[INDENT]                             OK, try this out and then inform....

On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
if you r using AMD, you may have to download proprietary drivers(Once installed) to get the right screen resolution n all....                         

Also, You might as well try with 13.04, which is the latest Ubuntu available !
[/INDENT]

---

### Post by mawil10132 on 2013-08-16
Greetings bhattabhishek,

Your instructions worked. I'm now running ubuntu off a USB.  I tried it first the normal way and the screen was black, then I restarted the laptop following your set of instructions and here I am.
 
I'm running 64bit amd version of 13.04 ubuntu.

Now I guess I need a "proprietary driver" you mentioned??  What's the process for that?

Regards,
Michael  




> **bhattabhishek said:**
> [INDENT]                             OK, try this out and then inform....

On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
if you r using AMD, you may have to download proprietary drivers(Once installed) to get the right screen resolution n all....                         

Also, You might as well try with 13.04, which is the latest Ubuntu available !
[/INDENT]


---

### Post by oldrocker99 on 2013-08-16
> **mawil10132 said:**
> Greetings bhattabhishek,

Your instructions worked. I'm now running ubuntu off a USB.  I tried it first the normal way and the screen was black, then I restarted the laptop following your set of instructions and here I am.
 
I'm running 64bit amd version of 13.04 ubuntu.

Now I guess I need a "proprietary driver" you mentioned??  What's the process for that?

Regards,
Michael

OK, assuming you have ATI graphics, you need to open a terminal and type:

sudo apt-get install fglrx

You'll be asked for your password, which is NOT echoed to the screen. Then it'll list the files needed and ask if you want to continue the installation; hit Y to continue. Once installed, you will need to reboot (one of the few times you ever need to reboot in Linux). 

Once you reboot, open the Catalyst Control Center and set your desired resolution, antialiasing, etc.

And good luck!

---

### Post by mawil10132 on 2013-08-17
According to this; [http://www.cnet.com/laptops/acer-aspire-5336-2524/4507-3121_7-34170323.html](http://www.cnet.com/laptops/acer-aspire-5336-2524/4507-3121_7-34170323.html)

They say, "Graphics Processor = GMA 4500M"

When I go to; System Resources/Display. It says; "Name; Mobile Intel 45 Express Chipset Family, Chip Type; Mobile Intel 4 Series Express Chipset Family"

Regards, Michael


> **oldrocker99 said:**
> OK, assuming you have ATI graphics, you need to open a terminal and type:

sudo apt-get install fglrx

You'll be asked for your password, which is NOT echoed to the screen. Then it'll list the files needed and ask if you want to continue the installation; hit Y to continue. Once installed, you will need to reboot (one of the few times you ever need to reboot in Linux). 

Once you reboot, open the Catalyst Control Center and set your desired resolution, antialiasing, etc.

And good luck!

---

### Post by mawil10132 on 2013-08-17
To bhatta;

According to this; [http://www.cnet.com/laptops/acer-asp...-34170323.html]("http://www.cnet.com/laptops/acer-aspire-5336-2524/4507-3121_7-34170323.html")

They say, "Graphics Processor = GMA 4500M"

When I go to; System Resources/Display. It says; "Name; Mobile Intel 45  Express Chipset Family, Chip Type; Mobile Intel 4 Series Express Chipset  Family"

Regards, Michael

---

### Post by Rob Sayer on 2013-08-17
For more detailed and reliable info about your video adapter open the terminal and type:

> sudo lshw -C video

and then your password.

Copy/paste the output of that and post it here (preferably use quote tags, it makes it much easier to read).

That way you can get a much better idea of what video driver you'd need.

---

### Post by mawil10132 on 2013-08-17
ubuntu@ubuntu:~$ sudo lshw -C video
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d34fffff



> **Rob Sayer said:**
> For more detailed and reliable info about your video adapter open the terminal and type:



and then your password.

Copy/paste the output of that and post it here (preferably use quote tags, it makes it much easier to read).

That way you can get a much better idea of what video driver you'd need.

---

### Post by su:bhatta on 2013-08-17
Sorry for the late reply, been busy with my troubles over installing 'elementary-desktop' on top of my Xfce!!

Do you have any issues with the open source drivers that are currently working? Wrong Screen resolution, laptop overheating, no refresh rate etc?

Have you given 'Software & Updates' a try? If you are using stock Ubuntu i.e. with Unity just search for 'Softwares & Updates'  from the dash, (The first icon on the dock on the left of your screen, haven't used Unity for months so may be glitchy here) 

Anyway, in 'Softwares & Updates' go to the last tab, "Additional Drivers', see if anything is listed/mentioned as proprietory drivers, If there are any options you can click on the radio button and give it a try, You have to reboot after the changes are applied for the driver to work...

See, if that helps!!

One more thing, When Pasting codes or results of Codes go to "Go Advanced' instead of 'Post Quick Reply' There you will get option # which wraps up the selected codes you paste!!!

Good Luck, Ubuntu is by far the easiest for using proprietary drivers ...

P.S. : Since your basic problem of installing Ubuntu is taken care of, it is suggested to mark this thread as 'solved' & open a new thread regards to your proprietary driver issue (if it still remians) mentioning your graphics card details, that will give you far better responses!

---

### Post by mawil10132 on 2013-08-17
No propriety drivers in use is what it says, thanks for your support!!

---

### Post by su:bhatta on 2013-08-17
ok, but are there any options to choose from? 
I suggest you open a new thread giving details of your graphics card, that will draw attention of people who are using same card and you will get better replies!

If open source drivers are working good, you may not require proprietary ones! 

Good luck mate, here my knowledge is limited, having only dealt with AMD/ATI graphics card!

Glad to be of any help, Michael! Happy 'Buntu-ing !!!

---

