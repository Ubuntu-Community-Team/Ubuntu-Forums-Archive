---
title: "Can I switch from LXDE to Gnome 3.0?"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by rks99 on 2011-10-21
Is it possible to switch from LXDE to Gnome 3.0 in Lubuntu 11.10? 

I'm asking because I came across a rad Tron theme that said it only worked with Gnome 3.0? 

-fairly a noob at Linux, it's fun and I'm willing to learn ;)



also, I've recently switched over from Vista to Ubuntu, then to Lubuntu, because of how choppy the first two ran on this laptop. 

my specs: 
[B]
Toshiba Satellite A135-S4527 [/B]
**RAM:** 1GB PC2-4200 DDR2 RAM
**Hard Drive:** 120GB Hitachi SATA
**Screen: **15.4” Tru-Brite WXGA (1280x800)
**Optical Drive:**  DVD±RW/DVD-RAM Drive
**Graphics: ** Intel GMA950 Graphics
**Slots:** Type II PCMCIA (left), 5-in-1 Card Reader (front)
**Ports: **4 USB 2.0 (two right, one left, one back), 1 4-pin (left), 1 VGA output (left), 1 S-Video output (left), 1 Headphone jack (front), 1 Microphone jack (front), 1 RJ-11 phone jack (back), 1 Power jack (back), 1 RJ-45 LAN jack (back)
**Wireless: ** Atheros 802.11g

---

### Post by 23dornot23d on 2011-10-21
Post back the results of this if you would please .....

in a terminal Ctrl+Alt+T

Type in

lsb_release -a

and

uname -a

You are running 11.10 so you should be able to do this in a terminal .... as long as you 
loaded gnome-shell from the software centre

gnome-shell --replace

whether your graphics card is ok though .... ? guess you have to try it to see .......

---

### Post by IWantFroyo on 2011-10-21
```
sudo apt-get install gnome-shell
```

If your computer has problems with Unity, Gnome-shell (otherwise known as Gnome 3.0) might stutter as well, but in my experience it is more responsive than Unity.

---

### Post by arpanaut on 2011-10-21
The real issue is going to be IF your graphics card supports 3d acceleration.
That I don't know.

---

### Post by LinuxFan999 on 2011-10-21
What CPU does your laptop have?
How fast is it?

---

### Post by bodhi.zazen on 2011-10-21
> **arpanaut said:**
> The real issue is going to be IF your graphics card supports 3d acceleration.
That I don't know.

He listed the graphics card in the first post ( Graphics: Intel GMA950 Graphics ) , I know it is not obvious.

That card should run gnome-shell.

---

### Post by rks99 on 2011-10-21
> **LinuxFan999 said:**
> What CPU does your laptop have?
How fast is it?

**Processor:** 2x Genuine Intel(R) CPU 2080 @ 1.73GHz

---

### Post by rks99 on 2011-10-21
> **IWantFroyo said:**
> ```
sudo apt-get install gnome-shell
```

If your computer has problems with Unity, Gnome-shell (otherwise known as Gnome 3.0) might stutter as well, but in my experience it is more responsive than Unity.

done, shall i reboot now?

---

### Post by rks99 on 2011-10-21
> **23dornot23d said:**
> Post back the results of this if you would please .....

in a terminal Ctrl+Alt+T

Type in

lsb_release -a

and

uname -a

You are running 11.10 so you should be able to do this in a terminal .... as long as you 
loaded gnome-shell from the software centre

gnome-shell --replace

whether your graphics card is ok though .... ? guess you have to try it to see .......

Thanks everyone for the quick response! 

Here' what I did: i ran in the terminal "sudo apt-get install gnome-shell" then the above commands^ 

here's the results: 



(gnome-shell:8333): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Fri Oct 21 2011 18:41:27 GMT-0700 (PDT)
    JS ERROR: !!!   Exception was: Error: Error invoking TelepathyGLib.prepare_finish: The name org.freedesktop.Telepathy.AccountManager was not provided by any .service files
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Error invoking TelepathyGLib.prepare_finish: The name org.freedesktop.Telepathy.AccountManager was not provided by any .service files")@gjs_throw:0
([object _private_TelepathyGLib_AccountManager],[object _private_Gio_SimpleAsyncResult])@/usr/share/gnome-shell/js/ui/telepathyClient.js:371
"'
    JS ERROR: !!!     message = '"Error invoking TelepathyGLib.prepare_finish: The name org.freedesktop.Telepathy.AccountManager was not provided by any .service files"'


hmmm did i do something wrong ?

---

