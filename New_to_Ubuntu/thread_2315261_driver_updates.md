---
title: "driver updates"
date: 2016-02-27
forum: New to Ubuntu
---

### Post by alex502 on 2016-02-27
hi guys
i am new to Ubuntu and i wanted to ask u how do i update my ASUS laptop drivers?
  two of the problems that i noticed is:

1) when i am playing a video on you-tube (or any other media) my screen is going to sleep...
why is that? 
it should know that when its playing a movie or a song he shouldn't go off.

2)when i plugging the laptop to my TV (hdmi cable) its not displays the desktop correctly and even when i open the Firefox nothing happens (on the laptop screen i can see the browser and on the TV screen isn't).

tnx a lot :)

---

### Post by kc1di on 2016-02-27
Hi alex502  and welcome to Ubuntu,
The problems you listed are most likely not driver problems.
But just setting problems.  you can set the viedo to mirror you laptop on the HDMI by going to control center and clicking on Displays and adjust the setting there.

in the same place I believe their is a setting to stop the screen from blanking when playing videos.  good luck

---

### Post by mikewhatever on 2016-02-27
What "my ASUS laptop drivers" are you talking about specifically? Did Asus provide you with drivers, or did you make them yourself?
You might also want to expend on the topic of my Asus graphics? If not sure what that is, post the output of lspci from a terminal window.

---

### Post by Rob Sayer on 2016-02-27
"Updating drivers" seems to be the kneejerk reflex reaction of Windows users.  It doesn't actually work very well in Windows and definitely doesn't work very well in linux.

Having the screensaver come on while playing video isn't a driver issue.  It's a setting in the app you're using to inhibit the screensaver when playing full screen.

As far as the external monitor goes it's probably a simple setting but you haven't said what hardware you have ... the make/model name isn't very useful ... or which 'buntu version you have.  Read the stickies.

Whatever you do, do NOT go to the site of whoever made some hardware in your machine and download linux drivers.  The chances that they'll work for your release is pretty small.

---

### Post by grahammechanical on 2016-02-27
System Settings>Displays or Screen Display (whatever it is called) has an option Detect displays. If we are using a proprietary video driver there should also be a settings utility for that video driver and it will have a detect displays option.

If the external display is not connected when we load the OS, then the OS does not know it is there. To get sound coming out of the speakers of the HDMI connected external display we may need to go to the sound utility and select HDMI as the sound output.

Regards.

---

