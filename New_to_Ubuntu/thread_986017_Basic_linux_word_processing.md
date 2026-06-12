---
title: "Basic linux word processing"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by too_funky on 2008-11-18
Hi, i have a grandpa that loves to type but is in his 90's and finds it impossible to navigate his way around new computers even for simple tasks such as loading up a word document. He used to have a basic word processor, which was essentially a very basic computer that could only run a word processing application. I'm a big fan of linux and am very familiar with the likes of ubuntu etc becuase they're so easy to use. However i'm after something even more basic that my grandpa could easily use.

I have an old computer with 256mb ram, pentium 3 600mhz and a 16gb hdd, cd/floppy drives usb ports etc. I currently have ubuntu hardy heron installed on it. But am considering swapping it to xubuntu to speed it up.

I want to try and replicate my grandpa's old word processor as much as possible so there's nothing new for him to learn. Are there any stable distros like that?

If not could you advise me on how tweak xubuntu or another easy to use, fast, stable distro so that it boots directly into a word proceing aplication such as open office but can also hide all other desktop menus etc to remove any other confusing things for him. But if possible i could still acess them incase i want to adjust a setting.

Thanks in advance

---

### Post by too_funky on 2008-11-18
ooh just read about something called a floppy boot disk, whats that, is it what im after?

---

### Post by Simian Man on 2008-11-18
I'd recommend using abiword as the word processor over openoffice.  For one it has a simpler interface, and second it uses less resources, which would make a big difference on that machine.

You could set up a start up program that launches abiword as soon as he logs in.  It would be better if abiword was started up in fullscreen mode, but I couldn't find an option for that.  I guess worst comes to worst you can add that yourself.

If you go that route, you can use something lighter than Gnome or XFCE such as Fluxbox, since he won't need the desktop anyway.

---

### Post by 3rdalbum on 2008-11-18
You might want to do some research into getting Linux to work like a kiosk. It'll involve setting up an X session script; hopefully there should be a HOWTO. The X session script you would create will just start a minimal window manager and the word processor (Abiword might be a good choice for this rather than openoffice.org)

Or, KDE has a kiosk mode, but KDE might be too heavy. Hopefully in kiosk mode it should be lightweight. Once again, Google will be your friend as I've never tried it.

---

### Post by mike555 on 2008-11-18
For an old computer I would say " Puppy " linux  might be good, you could remove the extra desktop icons and set Abiword to start automatically if you wanted   ...

---

### Post by starcannon on 2008-11-18
+1 to the Abiword suggestion, Open Office is very nice, but if he doesn't need all of its bells and whistles Abiword is much liter, more stable, and sports a much cleaner, simpler interface.

The computer you spec'd will handle xubuntu fine, and you can add Abiword to its session manager so that it opens when the computer is booted and logged into a desktop. I'm not currently on a machine with abiword but if you run ```
man abiword
``` you can find out if it has a full screen flag that you could have the session manager open it in, to escape it you would either press F11 or Esc key, not sure which, it varies from program to program, but those are the common ones with F11 being the most common.
GL

---

### Post by DieB on 2008-11-18
a

---

### Post by Tomatz on 2008-11-18
Try fluxbuntu (ubuntu based around fluxbox). Its targeted at machines like yours. Its simple and has abiword installed by default:

[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

---

### Post by Sef on 2008-11-18
I would use Xubuntu, which has Abiword installed by default.

---

### Post by Helios1276 on 2008-11-18
Xfce and Abiword seem like the right way to go but just for kicks,

[http://www.makeuseof.com/tag/8-great-alternative-desktop-managers-for-linux/](http://www.makeuseof.com/tag/8-great-alternative-desktop-managers-for-linux/)

---

### Post by too_funky on 2008-11-18
wow, i think thats the fastest and most comprehensive reply i ever had on any forum. thanks alot. im currently downloading xubuntu and will probably try just doing some basic thngs like removing desktop icons, unmapping shortcut keys etc. i havent used abiword before but it seems to have a general thumbs up so ill give it a go. if all that fails ill ty the kiosk method, cos im already familiar with the workings of ubuntu so should in theory make things easier for me. 

ill let you know how i get on, again thanks!

---

### Post by philinux on 2008-11-18
No need to reinstall. Take a look here.
[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Dedoimedo on 2008-11-18
Hello,

First, kudos to your grandpa! Not that many people that age are willing to use computers. Really cool.

Second, I fourth Abiword. It's fast and simple.

Dedoimedo

---

### Post by vanadium on 2008-11-18
Have just a text console installed and install joe. joe acts and feels like venerable Wordstar 3. Your grandpa will feel right at home, and the system will fly.

---

### Post by Tomatz on 2008-11-18
IMO xfce will be well too clunky for those specs. I would recommend fluxbox.

---

### Post by too_funky on 2008-11-18
thanks for the concern Tomatz, but as i already have hardy heron running fairly well i think it should be able to run xubuntu with ease, and (i believe) ubuntu and xubuntu have a larger support base so as i wont be the end user of the computer ill play it safe and stick with what i know.

And thanks Dedoimedo, you made my grandpa smile, he deffinetly appreciated the kudos after i explained to him what it meant:p

Also appreciate the tip philinux but ill think ill go for a clean install anyway just to get rid of my old hardy heron clutter.

I'm unfamiliar with JOE and wordstar 3 aswell and i think id prefer just tha bit of extra customisation i can achieve with full xubuntu os.

---

### Post by philinux on 2008-11-18
> **too_funky said:**
> thanks for the concern Tomatz, but as i already have hardy heron running fairly well i think it should be able to run xubuntu with ease, and (i believe) ubuntu and xubuntu have a larger support base so as i wont be the end user of the computer ill play it safe and stick with what i know.

And thanks Dedoimedo, you made my grandpa smile, he deffinetly appreciated the kudos after i explained to him what it meant:p

**Also appreciate the tip philinux but ill think ill go for a clean install anyway just to get rid of my old hardy heron clutter.**

I'm unfamiliar with JOE and wordstar 3 aswell and i think id prefer just tha bit of extra customisation i can achieve with full xubuntu os.
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
It's easier than you think. But I know a clean install is also nice.

---

### Post by too_funky on 2008-11-18
another quick question, just noticed after xubuntu install, is there away to remove the log on screen and just boot straight to the desktop, it seems silly if there is only going to be one user and they have to log on every time

---

### Post by philinux on 2008-11-18
Yes.

system>Admin>Login Window.
Security tab. Enable auto login.

---

