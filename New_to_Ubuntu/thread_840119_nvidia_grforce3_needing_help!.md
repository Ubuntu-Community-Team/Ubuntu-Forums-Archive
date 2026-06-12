---
title: "nvidia grforce3 needing help!"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by griffabear on 2008-06-25
Hello all. I have been trawling these pages for a few days and tried alot of stuff... i am still getting into ubuntu and not getting on with my grafix card. The problem is this. I have a geforce3 nvidia with a tv out. i cannot install the card! i am aware that there are several different guides for this but i keep getting errors and have no idea where i am now, what is installed and what to do next... help

---

### Post by forestpixie on 2008-06-25
Has the hardware driver been installed from system >admin >hardware drivers.

Have you run nvidia-settings?

Have you tried to use envy?

If you search for nvidia in synaptic what does it say is installed?

---

### Post by davidsrsb on 2008-06-25
This is an old card so either use the nv driver or the nvidia-glx-legacy

---

### Post by forestpixie on 2008-06-25
Geforce 4 uses nvidi-glx , I know because I still using mine :) 

It will be of use to know exactly what has been installed and tried though I think.

---

### Post by griffabear on 2008-06-26
Good evening,

Here are my responses to those who asked me questions



1. Has the hardware driver been installed from system >admin >hardware drivers.
2. Have you run nvidia-settings?
3. Have you tried to use envy?
4. If you search for nvidia in synaptic what does it say is installed?
5. This is an old card so either use the nv driver or the nvidia-glx-legacy

Answers
1. If I open that application it shows nothing
2. Not sure... I have tried a few things that were suggested elsewhere but kept getting errors
3. I tried to install envy using synaptic and it said successful but i don't see any different option (and no way to select my "tv out")
4.Nvidia-kernal-common
nvidia-new-kernal-source-envy
nvidia-settings
nvidia-xconfig
nvtv
5. i think i tried the legacy drivers... i think

Thanks for any input

---

### Post by Elfy on 2008-06-26
What happens if you use nvidia-settings from aterminal

```
nvidia-settings
```

Does it run, if it does do you see both monitors on the Display Configuration screen.

If that does work - run it as root to make the changes you need and make changes to x configuration file.

If not post back

---

### Post by griffabear on 2008-06-26
When i type "nvidia-settings" in terminal. i get and error - "You do not appear to be using the NVIDIA X driver. Please edit your X configuration 
file (just run `nvidia-xconfig` as root), and restart the X server." 

so in terminal i typed

nvidia-xconfig

and got -

Using X configuration file: "/etc/X11/xorg.conf".
WARNING: The CorePointer device was not specified explicitly in the layout;using the first mouse device.
WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in default configuration.
ERROR: Unable to write to directory '/etc/X11'.

---

### Post by Elfy on 2008-06-26
I've never needed to run that - it would appear that you're not using the driver. 


To run the nvidia-xconfig as root you need to use it with sudo 

```
sudo nvidia-xconfig
```

That said I would use envy to uninstall the driver it thinks it's installed, reboot as necessary.

Then check that there are no installed nvidia instances in synaptic - at that point you should be running with either the vesa or nv driver.

Then use hardware driver in sys>admin first to see if there are avilable drivers, if not check envy again to install the driver.

You will be able towatch as it downloads and installs - check out what it is actually doing.

---

### Post by griffabear on 2008-06-26
ok.... i uninstalled all nvidia stuff using synaptic
rebooted
installed envy 
went to terminal to try nvidia-settings and got the same error abd told to do nvidia-xconfig and got the following...

dan@griffbuntu:~$ sudo nvidia-xconfig
Using X configuration file: "/etc/X11/xorg.conf".
WARNING: The CorePointer device was not specified explicitly in the layout;using the first mouse device.
WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

thanks again!

---

### Post by Elfy on 2008-06-26
Ok, hopefully now you should be able to run the nvidia-settings

```
gksudo nvidia-settings
```

that should allow you to setup your monitor and tv - I'm not sure if you'll be able to do twinview - I just use it as a seperate x screen anyway to watch movies as I work.

Edit - maybe make a quick backup so you can get back, it should do it but you can never tell

sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.2606

---

### Post by griffabear on 2008-06-26
tried "gksudo nvidia-settings"

and i still get told to do nvidia-xconfig....

i feel we are closer!!

I am done for tonight but will be back....

thanks for the help so far!

---

### Post by Elfy on 2008-06-26
Ok - good rest now :)

When you next boot see if you get a nvidia splash screen - if you do it should be using the driver, if you don't...

I'll check tomorrow as it's mid afternoon here

---

### Post by griffabear on 2008-06-30
when i rebooted today i had to "configure" the monitor resolution but it did not pick nvidia. i chose it and logged in and i still don't seem to have any drivers! still lost!

---

### Post by griffabear on 2008-07-02
Still me and still the same problem... i am sure that i am missing some vital step but could really do with some help. at the moment i am back at the start!

---

### Post by stchman on 2008-07-02
> **griffabear said:**
> Hello all. I have been trawling these pages for a few days and tried alot of stuff... i am still getting into ubuntu and not getting on with my grafix card. The problem is this. I have a geforce3 nvidia with a tv out. i cannot install the card! i am aware that there are several different guides for this but i keep getting errors and have no idea where i am now, what is installed and what to do next... help

Install the driver.

```
sudo apt-get install nvidia-glx
```

---

### Post by griffabear on 2008-07-02
done... seemed all good .... restarted.... still don't seem to have tv out options or any other screen res choices... what should i try next?

Thanks heaps

---

### Post by Tomatz on 2008-07-02
<snip>

---

### Post by Tomatz on 2008-07-02
> **griffabear said:**
> done... seemed all good .... restarted.... still don't seem to have tv out options or any other screen res choices... what should i try next?

Thanks heaps



Run the command:
```

gksu nvidia-settings
```

---

### Post by griffabear on 2008-07-02
ok, if i run 

gksu nvidia-settings in terminal

i get a warning saying 

you do not appear to be using the nvidia x driver. please edit your x config file. 

i followed the instruction

tried just 

nvidia-xconfig

nothing

then 

sudo nvidia-xconfig

but i still get the same warning if i then type

gksu nvidia-setting

---

### Post by Elfy on 2008-07-02
This is rapidly turning into a circular thread I think :)

---

### Post by Tomatz on 2008-07-02
> **griffabear said:**
> ok, if i run 

gksu nvidia-settings in terminal

i get a warning saying 

you do not appear to be using the nvidia x driver. please edit your x config file. 

i followed the instruction

tried just 

nvidia-xconfig

nothing

then 

sudo nvidia-xconfig

but i still get the same warning if i then type

gksu nvidia-setting


Ahh you have a geforce 3.

I'm pretty sure you need nvidia glx legacy.

Your best bet to install the drivers properly is to use envyng. It will automatically select the appropriate drivers, install and configure them.


[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

;)

---

### Post by Elfy on 2008-07-02
> Your best bet to install the drivers properly is to use envyng.

We tried that route :( when I was forestpixie the first

From what I've seen GeForce3 can be a bit problematic, could be that it's not going to work properly and the best he's going to get is nv.

---

### Post by griffabear on 2008-07-02
:) you're telling me! I am starting to feel that i might have to go back to windows!

---

### Post by Elfy on 2008-07-02
> **griffabear said:**
> :) you're telling me! I am starting to feel that i might have to go back to windows!
 So now you make it a competition :D

---

### Post by griffabear on 2008-07-02
gotta keep the brains trust interested somehow!

---

### Post by Tomatz on 2008-07-02
> **forestpixie said:**
> We tried that route :(

From what I've seen GeForce3 can be a bit problematic.

Yeah i've seen reports of this in hardy.


OP.

Download this driver:

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

And refer to this howto to install it:

[http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/)


Hope that helps ;)

---

### Post by griffabear on 2008-07-02
ok, i downloaded the file and then moved it to my home folder

 i was off and doing well then i got to this point

[I]Log in as user and become root or use sudo and key in

killall gdm

or

killall kdm

to kill your X session.

Now you can install your NVIDIA driver with the command as root (Ubuntu users use sudo)

sh /path/to/NVIDIA-Linux-x86-100.14.11.pkg1.run[/I]


after that last line i get the error - 

NVIDIA-Linux-x86-100.14.11.pkg1.run:command not found

this is a newbie mistake... i know it... what am doing wrong?

Ta as always!!!

---

### Post by Tomatz on 2008-07-02
> **griffabear said:**
> ok, i downloaded the file and then moved it to my home folder

 i was off and doing well then i got to this point

[I]Log in as user and become root or use sudo and key in

killall gdm

or

killall kdm

to kill your X session.

Now you can install your NVIDIA driver with the command as root (Ubuntu users use sudo)

sh /path/to/NVIDIA-Linux-x86-100.14.11.pkg1.run[/I]


after that last line i get the error - 

NVIDIA-Linux-x86-100.14.11.pkg1.run:command not found

this is a newbie mistake... i know it... what am doing wrong?

Ta as always!!!

You need to put the driver into your **home** folder (where the terminal/cli is open) before killing gdm. That is all ;)

---

