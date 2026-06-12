---
title: "Help installing Mupen64 Plus"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Rocko262c on 2012-06-01
Dear Everyone,

Does anyone know how to install Mupen64plus on Ubuntu 12.04? 

I am having a hard time with this new upgrade and it seems that Mupen64plus has also been removed from the repositories. 

Can anyone kindly help?

Cheers,
Rocko262c

---

### Post by oldos2er on 2012-06-01
Post moved to its own thread.

---

### Post by forrestcupp on 2012-06-01
It's still in the repos. The dummy package installs all of the necessary packages to use it. Open up a terminal and type:
```
sudo apt-get install mupen64plus
```

Edit: Maybe your problem is that you didn't know that Mupen64plus is a command-line program, and there is no GUI frontend included. You have to run the mupen64plus command from the terminal and supply it with a filepath to your game ROM.

---

### Post by santtu1 on 2012-06-19
Where does this mupen64plus go after installing? :O

---

### Post by Rocko262c on 2012-06-22
Dear Forrestcupp,

Yeah, I have no idea how it was not in my repositories, but it just wasn't there after my recent bad upgrade. I am sure you as most other ubuntu/linux users have come across this during a bad upgrade.  I sure know this hasn't been the first time something like this has happened to me.  So as always, I waited for a few updates and for some magical and inconvenient reason I could install Mupen64plus via command line or synaptic.

Now I have a new dilemma. With the most recent install of Mupen64plus, I was unable to get the GUI that I  had before. I recently upgraded from 11.10 to 12.04 and encountered this along with a lot of other issues (dual screen support being #1 issue). I know Mupen64plus doesn't come with a GUI, but for some unknow/magical reason, it came with the install thatI did in 11.10. The GUI I am talking about looks like:
[http://offenerdesktop.files.wordpress.com/2010/01/spiele-mupen64plus-001.png](http://offenerdesktop.files.wordpress.com/2010/01/spiele-mupen64plus-001.png)

How do I re install this?  Nothing works.

Before I installed Mupen64plus via Synaptic and I repeated this after the most recent updates I performed. I was only able to execute a ROM via the command line, but couldn't get the GUI to configure the plugins.

I was easily able to configure my USB controllers before the upgrade and now that I don't have that GUI with some unknown programs/packages supporting it, I can't get my controllers to work. I have edited the config file that has support for like 30 controllers in it and have been unsuccessful following information found on Mupen64plus Wiki and other forums.

Whatever packages support that GUI were able to help me configure my USB controllers. Can anyone help?

Cheers,
Rocko262c

---

### Post by Rocko262c on 2012-06-22
One other thing, when I ran Mupen64plus in Ubuntu 11.10 I saw a Mupen64plus icon in the Dash. Now I see nothing.

Not sure if this matters, but it is different.

Cheers,
Rocko262c

---

### Post by Rocko262c on 2012-06-26
Dear Everyone,

I couldn't install that super nice interface with the super wonderful and nice plugin that easily configured my controller before, so I spent time to get my controller to work.

First my controller looks like:
[http://img.diytrade.com/cdimg/768564/6833845/0/1220668585/USB_Joypad_USB_Joystick_USB_controller_USB_gamepad.jpg](http://img.diytrade.com/cdimg/768564/6833845/0/1220668585/USB_Joypad_USB_Joystick_USB_controller_USB_gamepad.jpg)
I am not sure how long that picture will stay up on the internet, but the controller has the following buttons:
DPad (up, down, left, right)
Select
Start
4 buttons on the right hand side of the pad
2 left and 2 right index trigger buttons

As per the instructions on the Mupen64plus Controller Setup page:
[http://code.google.com/p/mupen64plus/wiki/ControllerSetup](http://code.google.com/p/mupen64plus/wiki/ControllerSetup)
I configured this controller with the following configuration:

[USB Gamepad ]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768
DPad R = hat(0 Right)
DPad L = hat(0 Left)
DPad D = hat(0 Down)
DPad U = hat(0 Up)
Start = button(9)
Z Trig = button(7)
B Button = button(3)
A Button = button(2)
C Button R = button(1)
C Button L = button(0)
C Button D = button(5)
C Button U = button(4)
R Trig = button(6)
L Trig = button(8)
Mempak switch =
Rumblepak switch =
X Axis = axis(0-,0+)
Y Axis = axis(1-,1+)

Good luck to anyone trying to configure their controller,
Rocko262c

---

### Post by Arendyl on 2012-06-29
bumping this. would like to know the answer to why there is no GUI interface.

---

### Post by darthideut on 2012-09-22
Does anyone know where I can find the InputAutoCfg.ini file that is supposed to be there in either the /usr/local/share/mupen64plus or /usr/share/mupen64plus folders that is referenced in Rocko262c's post? I looked and neither of the locations exist and I'm running 12.04.

---

### Post by whochismo on 2012-10-15
Bump. I am also interested in the disappearance of the GUI.

EDIT: The package is called cutemupen and it can be found here: [http://sourceforge.net/projects/cutemupen/](http://sourceforge.net/projects/cutemupen/)
There is another front end called m64py, here: [http://sourceforge.net/projects/m64py/](http://sourceforge.net/projects/m64py/)

EDIT: I installed mupen64plus_1.5, which comes with ubuntu 10.04. You can find it here: [https://launchpad.net/ubuntu/lucid/+package/mupen64plus](https://launchpad.net/ubuntu/lucid/+package/mupen64plus)
You'll also need these libraries: [https://launchpad.net/ubuntu/+source/libxdg-basedir/1.1.1-2](https://launchpad.net/ubuntu/+source/libxdg-basedir/1.1.1-2) and [https://launchpad.net/ubuntu/lucid/i386/liblzma1](https://launchpad.net/ubuntu/lucid/i386/liblzma1) (check if you need the i386 or amd64 version)

---

