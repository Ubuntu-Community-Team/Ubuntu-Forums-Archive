---
title: "Stuck trying to get my printer working."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by L Campbell on 2008-07-10
I'm using Hardy 8.04 on a PC and I have an Epson stylus PHOTO 820 printer which I have been unable to get to work.   

I do System > Administration > Printing and the Printer Configuration window opens but this about as far as I can get.

On the Printer Configuration window, under make and model,  it does show Epson stylus PHOTO 820 and also includes ' Cups+Gutenprint v5.0.2 simplified ' however, if I remove the printer cord from my computer and then re-boot with the cord disconnected, it still 'sees' the printer and so I'm kind of stuck here.

I would appreciate it if someone would advise me as to what to try next and/or recommend a printer that would work well with my computer.

TIA.

---

### Post by appi2012 on 2008-07-10
I had a epson stylus photo 825, and that worked. That's interesting.:confused:

---

### Post by fatality_uk on 2008-07-10
I hope I am reading your post correctly.

1) The printer will work well: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_820](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_820)

2) You have installed a printer into Ubuntu! That means the configuration for that printer is stored. I am not sure why you are trying to ***see*** if it removes it when the USB cord is unplugged?

---

### Post by L Campbell on 2008-07-10
> **fatality_uk said:**
> I hope I am reading your post correctly.

1) The printer will work well: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_820](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_820)

2) You have installed a printer into Ubuntu! That means the configuration for that printer is stored. I am not sure why you are trying to ***see*** if it removes it when the USB cord is unplugged?

OK, I can see how that would be confusing.  I thought I might have made some kind of error, which was the reason that the printer would not print and I wanted to clear out the information I had entered and give it another try.

Kind regards.

---

### Post by fatality_uk on 2008-07-10
> **L Campbell said:**
> OK, I can see how that would be confusing.  I thought I might have made some kind of error, which was the reason that the printer would not print and I wanted to clear out the information I had entered and give it another try.
Kind regards.

Ok got ya ;) I was scratching my head there thinking you had some kind of uber-cool wireless module attached :)

Anyway, can you see the printer if you enter CUPS?
[http://localhost:631/](http://localhost:631/)
Click this link and see if it's in there under "Manage Printers"

If it is, make sure all cables are in ;) and click "Print Test Page"
And lets know if any joy?

---

### Post by L Campbell on 2008-07-10
> **fatality_uk said:**
> Ok got ya ;) I was scratching my head there thinking you had some kind of uber-cool wireless module attached :)

Anyway, can you see the printer if you enter CUPS?
[http://localhost:631/](http://localhost:631/)
Click this link and see if it's in there under "Manage Printers"

If it is, make sure all cables are in ;) and click "Print Test Page"
And lets know if any joy?

Thanks for your continued interest.

Under 'Manage Printers' I can see my printer information but is states "unable to locate".

I hope the screenshot will help here.

Kind regards.

---

### Post by fatality_uk on 2008-07-10
Two things to try:

1) Click the start printer button in CUPS. Worth a shot ;)
2) Assuming your connecting via a SUB cable, make sure its plugged in before starting your PC. When logged in, type > lsusb into a terminal. It should show up on there.
3) If it shows up, try #1 again.
4) If that fails, then assuming it is visible after lsusb, then try adding the printer dirctly from CUPS and not gnome.

---

### Post by L Campbell on 2008-07-10
> **fatality_uk said:**
> Two things to try:

1) Click the start printer button in CUPS. Worth a shot ;)
2) Assuming your connecting via a SUB cable, make sure its plugged in before starting your PC. When logged in, type  into a terminal. It should show up on there.
3) If it shows up, try #1 again.
4) If that fails, then assuming it is visible after lsusb, then try adding the printer dirctly from CUPS and not gnome.

Unfortunately, my printer doesn't have a USB connection.  It has the '25 pin' type.

Everything I have tried in CUPS still shows 'unable to locate printer' so I removed the printer and re-installed it again.

This time I had some success and was able to print the 'test page'.  Excited, I tried to "clean the print heads" but got this error message:- "/usr/lib/cups/filter/pstoraster failed"

Nothing else seemed to work except the test page and deleting stuff but at least I have taken another step forward.

Many thanks.

---

### Post by fatality_uk on 2008-07-10
Don't worry, we'll get there!!! :)

---

### Post by fatality_uk on 2008-07-10
Checking the specs for it, I think your best course of action will be to get a USB cable. I am guessing Ubuntu is struggling with parrallel cable. They aare a couple of bucks for most PC shops unless you have one lying around.

If you have, try using that instead of the parrallel cable and then re-run CUPS to install the printer again.

---

### Post by cariboo on 2008-07-10
When you setup you're printer did you chose lpt #1?

Jim

---

### Post by L Campbell on 2008-07-10
> **fatality_uk said:**
> Checking the specs for it, I think your best course of action will be to get a USB cable. I am guessing Ubuntu is struggling with parrallel cable. They aare a couple of bucks for most PC shops unless you have one lying around.

If you have, try using that instead of the parrallel cable and then re-run CUPS to install the printer again.

It had never occurred to me that I had an option of using a USB cable on my printer.  Thanks for pointing that out.

Unfortunately, it didn't do anything that the old cable didn't do.  In fact it wouldn't even print the test page but I think that part of the reason for that is that the ink heads need cleaning and the utility to do that wouldn't work either.

Thanks again.

---

### Post by fatality_uk on 2008-07-10
Hmm. Last try before I go to bed. It's 1:30am here :lol:
when you had the other cable in, was the test print page like this one?
Did you get a colour print and was the images sharp?

---

### Post by L Campbell on 2008-07-11
> **fatality_uk said:**
> Hmm. Last try before I go to bed. It's 1:30am here :lol:
when you had the other cable in, was the test print page like this one?
Did you get a colour print and was the images sharp?

Yes, that is the test page that I got, except that mine was CUPS v1.3.

The image was rather faint, probably indicating that the print heads need cleaning and I couldn't get the utility for that to work.

Hope you had a good snooze.   :-)

---

### Post by alienexplorers on 2008-07-11
First do you have the parallel cable plugged in correctly.  Second do you have lpt turned on and set to the newest options.  Did you select lpt1 when you set up your printer.  Do you have the correct driver selected.

---

### Post by L Campbell on 2008-07-11
> **alienexplorers said:**
> First do you have the parallel cable plugged in correctly.  Second do you have lpt turned on and set to the newest options.  Did you select lpt1 when you set up your printer.  Do you have the correct driver selected.

Hi, thanks for your interest.

I'm sure that I have the cable plugged in correctly but I don't know what you mean by ' lpt ' and ' lpt1 '.  I didn't notice anything like that but will try looking for it.

---

### Post by alienexplorers on 2008-07-11
lpt and lpt1 are refering to the line printer port.

---

### Post by L Campbell on 2008-07-11
> **alienexplorers said:**
> lpt and lpt1 are refering to the line printer port.

I'm sorry but I do not understand and don't re-call having heard this term before.

When I google ' lpt1 ' I don't see anything that I can understand.

Should I find ' lpt1' in CUPS?  Through ' Terminal '? or from System > Administration > Printing?

TIA

---

