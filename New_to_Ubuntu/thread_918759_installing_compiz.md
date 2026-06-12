---
title: "installing compiz ?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by eric489 on 2008-09-13
Hi all !

I've switched to kde thanks to your guys help, and now I'm thinking of  installing compiz successfully with your help once again.

When I go to system> desktop effects i'm told that compiz is already installed and i get to choose between  several effects levels.

The main reason i want compiz is the cube thing :D
But since i'm on a pretty old computer with a pretty unknow graphic card 

( it's an S3 graphics with 32 mb, i managed to play cs pretty well on xp, so i think it's enough to run a compiz cube )

So where do i find the appropriate driver ?
Is a driver necessary ? Or can i just run the cube like that ?

---

### Post by northern lights on 2008-09-13
Can you please post the output of ```
sudo lshw -C display
```

Thank you.

---

### Post by Troll_the_Great on 2008-09-13
Is your card installed?If you go to System-Administration-Hardware Drivers is it enabled?If yes, and if compiz is already installed go to System-Preferences-CompizConfig Settings Manager and choose the cube effect.
Cheers!

---

### Post by benerivo on 2008-09-13
You may need to install compizconfig-settings-manager (sudo apt-get install compizconfig-settings-manager in konsole). Then it wil appear in the main kde menu.

---

### Post by northern lights on 2008-09-13
> **Troll_the_Great said:**
> Is your card installed?If you go to *System-Administration-Hardware Drivers* is it enabled?
The OP is on KDE. You're navigating him through the GNOME menu, Troll...

---

### Post by eric489 on 2008-09-13
> **northern lights said:**
> Can you please post the output of ```
sudo lshw -C display
```

Thank you.

here's what I got when typing the command :

*-display
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=prosavage_smbus latency=32 maxlatency=255 mingnt=4 module=i2c_prosavage


And for the other post : when I open hardware drivers, the window is empty...

---

### Post by Troll_the_Great on 2008-09-13
> **northern lights said:**
> The OP is on KDE. You're navigating him through the GNOME menu, Troll...

OOpsss...Sorry, I didn't see it was Kubuntu....

---

### Post by northern lights on 2008-09-13
I'm not too certain compiz will run under that card.

Can you also post the outputs of ```
glxinfo | grep rendering
``` and ```
compiz --replace
```

Let's see whether glx works.

---

### Post by eric489 on 2008-09-13
> **northern lights said:**
> I'm not too certain compiz will run under that card.

Can you also post the outputs of ```
glxinfo | grep rendering
``` and ```
compiz --replace
```

Let's see whether glx works.

For the first line i get :
eric@eric-desktop:~$ glxinfo | grep rendering
direct rendering: Yes


and the second line : 
eric@eric-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine
eric@eric-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine

So, bad news doc ? :confused: :(

---

### Post by northern lights on 2008-09-13
Well, the first one is good news.

The second output explains why compiz is not working, even though direct rendering is available with your card and setup.

The crucial complaint here is > No whitelisted driver foundWhich, fortunately, we can alter.

In a terminal, run ```
gksu gedit /usr/bin/compiz
```

then add your driver to the Driver whitelist section.

At first it will look something like this:
```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810"
...
```

When you supplied the output of 'lshw -C display' (the very first output I had asked for), it read that you're using the 'prosavage_smbus' driver. So that's what we're going to add:
```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810 prosavage_smbus"
...
```

Save the file, quit gedit, try running compiz again. Now what?

---

### Post by eric489 on 2008-09-13
> **northern lights said:**
> Well, the first one is good news.

The second output explains why compiz is not working, even though direct rendering is available with your card and setup.

The crucial complaint here is Which, fortunately, we can alter.

In a terminal, run ```
gksu gedit /usr/bin/compiz
```

then add your driver to the Driver whitelist section.

At first it will look something like this:
```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810"
...
```

When you supplied the output of 'lshw -C display' (the very first output I had asked for), it read that you're using the 'prosavage_smbus' driver. So that's what we're going to add:
```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810 prosavage_smbus"
...
```

Save the file, quit gedit, try running compiz again. Now what?


I insered the first line, which is : gksu gedit /usr/bin/compiz

It opened a text file

"then add your driver to the Driver whitelist section."

Sorry for not understanding what you mean. What is a whitelist section ?
And how do i add my driver to this section ? :confused:
sorry again for asking basic questions, i'm just new on linux.

---

### Post by northern lights on 2008-09-13
> **eric489 said:**
> Sorry for not understanding what you mean. What is a whitelist section ?
And how do i add my driver to this section ? :confused:
sorry again for asking basic questions, i'm just new on linux.
Apart from a reason to feel sorry being nonexistent, this is what I wanted you to do:
Open the textfile as you did. Find the part of the file similar to
> **northern lights said:**
> ```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810"
...
```

And manually add the part in *italics*

> **northern lights said:**
> ```
...
#Driver whitelist
WHITELIST="nvidia intel ati radeon i810 *prosavage_smbus*"
...
```

Save. Try to use compiz now. If it fails, reboot or log out and try again. Works?

---

### Post by eric489 on 2008-09-13
> **northern lights said:**
> Apart from a reason to feel sorry being nonexistent, this is what I wanted you to do:
Open the textfile as you did. Find the part of the file similar to


And manually add the part in *italics*



Save. Try to use compiz now. If it fails, reboot or log out and try again. Works?

I rebooted, checked if custom effects was enabled in system>desktop effects.

But what now ? What key do I hit to get the cube view ? Or should I first find and check an option for enabling the cube ?

---

### Post by northern lights on 2008-09-13
The cube is not enabled by default, even if compiz is running properly.

From a terminal, run ```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

Your manu will now have a new entry: System > Preferences > Advanced Desktop Effects Settings

Here, navigate to 'General Options' and under the 'Desktop Size' tab, set 'Horizontal Virtual Size' to 4.

Then, under the Desktop category, enable 'Desktop Cube' and 'Rotate Cube'.

---

### Post by eric489 on 2008-09-13
> **northern lights said:**
> The cube is not enabled by default, even if compiz is running properly.

From a terminal, run ```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

Your manu will now have a new entry: System > Preferences > Advanced Desktop Effects Settings

Here, navigate to 'General Options' and under the 'Desktop Size' tab, set 'Horizontal Virtual Size' to 4.

Then, under the Desktop category, enable 'Desktop Cube' and 'Rotate Cube'.

Done, but still no cube hen i hold ctrl+alt + arrow key :/....

---

### Post by benerivo on 2008-09-13
Do you have any desktop effects? For example do you have wobbly windows, or any window animations such as the minimizing effect or the fading in/out of windows?

---

### Post by eric489 on 2008-09-14
> **benerivo said:**
> Do you have any desktop effects? For example do you have wobbly windows, or any window animations such as the minimizing effect or the fading in/out of windows?

Nope :/

---

