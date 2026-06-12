---
title: "compiz"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-05-02
Hi. how do you use compiz?

---

### Post by MattBD on 2008-05-02
If you're using Ubuntu, it's already installed and should already be working. If you want to get cool effects like the cube, you need to install a package using the following:
```
sudo apt-get install compizconfig-settings-manager
```
Once that's installed it should appear in your System menu (I'm afraid I don't know exactly where it will be as I use Kubuntu). You can then use that to set up the effects you want.

---

### Post by Fatal Equinox on 2008-05-02
Install the compiz icon via  add/remove   or synaptic   system>admin>synaptic packet manger.

Then once that is installed you can open compiz and tinker with the options.... applications> system tools> compiz icon...

in your open tool bar left click and open settings manager....

[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

Check out the wiki for more specifics....

Like said above... compiz is pre-installed... you just need to install the icon to access it.

I also just learned of this one myself.... if you don't want the icon..
```

sudo compiz --replace
```

---

### Post by pikabuntu on 2008-05-02
ok, how would i go about enabling the avant window navigator then?

---

### Post by MattBD on 2008-05-02
AWN is now in the repositories, and there's also another application to manage it:
```
sudo apt-get install avant-window-navigator awn-manager
```
Once that's done, you should be able to launch it easily enough as I think it appears under Applications.

---

### Post by pikabuntu on 2008-05-02
i have it already, but i cant get it to work :(


(sorry i only got ubuntu 2 weeks ago and i dont know much yet :))

---

### Post by pikabuntu on 2008-05-02
if i type avant-window-navigator in the terminal, i get:

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by MattBD on 2008-05-02
> **pikabuntu said:**
> i have it already, but i cant get it to work :(


(sorry i only got ubuntu 2 weeks ago and i dont know much yet :))

Fair enough, it's always hard to get everything working when you're first starting out!

Can you elaborate? Does it not start at all if you click on it in the menu? If you try Alt+F2 to bring up the launcher and type avant-window-navigator, does it come up then?

---

### Post by pikabuntu on 2008-05-02
ok. i get :

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

(what do i do?! :))

---

### Post by MattBD on 2008-05-02
> **pikabuntu said:**
> if i type avant-window-navigator in the terminal, i get:

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

I think [this link]("https://help.ubuntu.com/8.04/desktop-effects/C/compiz-configure.html") should get you going. If you enable normal or extra effects as shown in the link, you should then be able to use AWN.

---

### Post by pikabuntu on 2008-05-02
> **MattBD said:**
> I think [this link]("https://help.ubuntu.com/8.04/desktop-effects/C/compiz-configure.html") should get you going. If you enable normal or extra effects as shown in the link, you should then be able to use AWN.

my computer will not allow me to enable normal or advanced effects :(
if i try it says:
Desktop effects could not be enabled
(im running hardy now and it did not do this on gutsy, it let me enable desktop effects)


does this mean i cant use avn?

---

### Post by MattBD on 2008-05-02
> **pikabuntu said:**
> my computer will not allow me to enable normal or advanced effects :(
if i try it says:
Desktop effects could not be enabled

does this mean i cant use avn?

If you can't enable normal or advanced effects, then you won't be able to use AWN as this does depend on having a compositing window manager.

All I can think of that maybe your graphics card isn't sufficient to support it. What type is it?

---

### Post by pikabuntu on 2008-05-02
> **MattBD said:**
> If you can't enable normal or advanced effects, then you won't be able to use AWN as this does depend on having a compositing window manager.

All I can think of that maybe your graphics card isn't sufficient to support it. What type is it?

 
how would i find out?

---

### Post by NightwishFan on 2008-05-02
Try hardinfo:
```
sudo apt-get install hardinfo
```

It _should_ appear under System -> Administrator -> System Information and Benchmarking tool (something like that) It should have info on your display.

---

### Post by pikabuntu on 2008-05-03
Is this what you need?

-Display-
Resolution		: 1024x768 pixels
Vendor		: The X.Org Foundation
Version		: 1.4.0.90
-Monitors-
Monitor 0		: 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
Extended-Visual-Information
GLX
MIT-SCREEN-SAVER
MIT-SHM
MIT-SUNDRY-NONSTANDARD
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
TOG-CUP
X-Resource
XAccessControlExtension
XC-APPGROUP
XC-MISC
XFIXES
XFree86-Bigfont
XFree86-DGA
XFree86-DRI
XFree86-Misc
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor		: Tungsten Graphics, Inc.
Renderer		: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
Version		: 1.3 Mesa 7.0.3-rc2
Direct Rendering		: Yes

---

### Post by MattBD on 2008-05-03
Ok, I think the line you need is this one:
```
Renderer : Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
```
As far as I know, the Radeon is an ATI card. Unfortunately ATI aren't great for Linux support, so I suspect that what's happened is that Ubuntu hasn't been able to get that graphics card working and without that can't get Compiz working.

I suggest you try using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Basically, this is a utility that will detect your card, install the right drivers and configure your X window server for you. If you can get the driver for your graphics card working then that should solve the problem.

It's actually in the repositories so you can get it with the following command:
```
sudo apt-get install envyng-gtk
```
Then just follow the instructions on the website, and hopefully that should resolve the issue.

---

### Post by pikabuntu on 2008-05-03
Ok, I tried envy.  :(  The automatic detection said my graphics card wasn't supported, and it said it could do it manually, and I said ok.  
  Now, my screen is little, and it said that it is running in low graphics mode.
  How can I fix this?? 


(also the first line of code you gave me did not work it said: bash: !+/SSE: event not found
)

---

### Post by m_ad on 2008-05-03
I just got a new laptop with Ubuntu installed it, found out my video card is Blacklisted :mad:

and I like smaller resolutions as well, this 1280x800 is too big :sad:


if I get a new one (which I'm planning on doing), what is best supported by Ubuntu?

---

### Post by MattBD on 2008-05-03
Sorry, the first line wasn't something I meant you to enter, it was just a line in the output that showed your wireless card.

If Envy doesn't work, then I can't suggest very much other than Googling the name and make of your card to find a solution.

---

### Post by MattBD on 2008-05-03
> **m_ad said:**
> I just got a new laptop with Ubuntu installed it, found out my video card is Blacklisted :mad:

and I like smaller resolutions as well, this 1280x800 is too big :sad:


if I get a new one (which I'm planning on doing), what is best supported by Ubuntu?

ATI are supposed to be a bit dodgy for Linux drivers - I think Nvidia are generally supposed to be better supported. But I think the best support is for Intel's integrated graphics cards.

---

### Post by pikabuntu on 2008-05-03
> **m_ad said:**
> I just got a new laptop with Ubuntu installed it, found out my video card is Blacklisted :mad:

and I like smaller resolutions as well, this 1280x800 is too big :sad:


if I get a new one (which I'm planning on doing), what is best supported by Ubuntu?



Does this help?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

### Post by pikabuntu on 2008-05-03
i am not going to be on here for a while because i am going to revert to 7.10

---

### Post by m_ad on 2008-05-03
Intel integrated is best supported? Weird..

in xorg.conf the identifier says..
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller


the list provided says that my card should be fully supported....?

However I am running 7.10

---

### Post by khr on 2008-05-03
I've had the same problem with Hardy but i managed to solve it...
I'm using an ATi card and i think this is the way i got compiz to work:

1. Open a terminal and enter "sudo dpkg-reconfigure -phigh xserver-xorg".
2. Reboot Ubuntu, then System > Administration > Hardware Drivers, then enable your graphic card driver by ticking the box.
3. Reboot again and then enable Desktop Effects and it should work!

It was something like that...

---

### Post by m_ad on 2008-05-03
I actually tried doing the reconfigure, and it didn't do anything

---

### Post by m_ad on 2008-05-03
I wonder if upgrading to 8.04 will do the trick..


any ideas on how to get higher resolutions with this graphics card?

---

