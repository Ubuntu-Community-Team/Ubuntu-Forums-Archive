---
title: "New, Very new and very stuck"
date: 2017-01-31
forum: New to Ubuntu
---

### Post by doehurden on 2017-01-31
Hello all,

I am very new to all this linux but am hoping to get on to using open foam and believe this is the way to start.

today i bought a new ssd and rusing my machine in windows to make a usb with ubuntu on.

I then turned off my machine and unplugged my windows ssd and storage hdd and plunged in my new ssd and the usb i made.

Turned on and hay presto i was installing linux. Very happy i was.

Then once installed i turned the machine on and off, set up my email, checked the internet was still there and all seemed to be running well.

Then i hit a problem. 

I turned of the computer, unplugged the usb and turned it back on but now my password doesn't work. I input the password on login and the screen flashes black for a brief second, wings and won't let me in. I purposely input an incorrect password and this brings up a red message "invalid password, please try again" but no flash or bing.

this happens with the usb stick in or not, bios is set to boot from ssd again not usb.

This is not the best start, what should i try next??

all the best, Leon

---

### Post by DuckHook on 2017-01-31
Welcome to the forums doehurden,

[LIST=1]
[*]Did you install using uefi?
[*]If your previous install was Windows, have you turned off secure boot?
[*]Does the new install boot up from a LiveUSB?
[*]Can you bring up a console with <Ctrl>+<Alt>+<F1>?
[*]What are your computer HW specs, especially the video card?
[*]What do you mean by "…wings and won't let me in"? Does it go black, or kick you back to the login screen or what?
[/LIST]
Please answer all of the above.

---

### Post by parkado on 2017-01-31
Hey Leon!

Can You please explain "flashes black for a brief second, wings and won't let me in". What happens after it? A new prompt?

Did You set up encrypted disk during installation?

---

### Post by doehurden on 2017-02-01
hi all. thanks for the replies.

i got a bit further with this before going to bed......

hopefully i can answer you questions in the hope you can answer mine. 

First off the 'wings and won't let me in' was meant to reed BINGS and won't let me in... i.e. when i enter my password in makes a noise like a bell bing, the screen flashes black and then i am presented with the same screen asking for my password. note not saying incorrect password.

I did not set up encryption

I don't know about UEFI
My previous install was windows. However. I took the hard drives out of the machine and installed ubuntu on a new hard drive. (i have got further)
Does not boot from usb any moor
i didn't try bringing up a console.

So what i have done since.
 Because it was all so early on i put the usb back in and reinstalled linux opting to delete all data on hard drive. This worked.
Then i took out the usb stick and rebooted. This worked.
Then i went to system settings>software and updates> additional drivers where it says my graphics card "(NVIDIA Quadro K2200) is using X.Org X server" and "Unknown device is using 'processor microcode firmware for intel CPU's" 
I changed the Graphics card to use a NVIDIA driver listed and rebooted.....

Exactly the same problem arose.

So i reinstalled linux using the same delete all option and went through the process again but thistle using the other NVIDIA driver listed however the result was the same.....

I reinstalled Linux for a third time and and have left the driver for graphics card allows this time using the X.Org X server driver.

I have then gone ahead and started plugging hard drives back in and an now with a machine that i can boot as ether windows or linux and am happy with that all though am wondering if the graphics card is functioning properly? There are lots of other questions but ill google them first......

---

### Post by parkado on 2017-02-01
Great to hear everything turned out fine enough. 

Looks like You might have a issue with graphics card driver. 
Here is bit of advice: [http://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)

Welcome to the community! : )

---

### Post by Geoffrey_Arndt on 2017-02-01
It seems as if you may be running the hybrid dual-graphics system "Optimus Prime" . . . not an especially Linux friendly system as nVidia has opted out of providing proper dual gpu Linux drivers.[B]

However, IF SO[/B], there are several informative threads available via standard google search, however, the thread that I particularly like due to it's clarity and up-to-date-ness is by Dell

. . . [http://www.dell.com/support/Article/us/en/4/SLN298431/EN](http://www.dell.com/support/Article/us/en/4/SLN298431/EN)

---

### Post by HermanAB on 2017-02-04
Hmm... Nvidia is 'Linux hostile', but the reverse engineered free driver works pretty good.  If it works - don't change it.

---

### Post by Geoffrey_Arndt on 2017-02-04
Good advice.

---

