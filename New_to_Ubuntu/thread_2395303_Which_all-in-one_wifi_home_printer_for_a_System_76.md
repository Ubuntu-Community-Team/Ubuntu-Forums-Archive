---
title: "Which all-in-one wifi home printer for a System 76 Laptop running Ubuntu"
date: 2018-06-29
forum: New to Ubuntu
---

### Post by waltd on 2018-06-29
Hi, I have a System 76 laptop. Currently I have an Epson 600 ink jet, home printer and it's often problematic with Ubuntu. I want to buy a new, all-in-one, wifi enabled, home printer that can print, scan, copy and connect to my home network wifi, but that also works very well with Ubuntu with no problems. I welcome suggestions for printers. Thank you.

---

### Post by jeremy31 on 2018-06-29
I recently got a HP officejet 6962 and it works well in Ubuntu to replace an older all-in-one that developed printing issues.  It does 2 sided printing and I have done scans and copied with it and it is connected to my wifi network.  When I went to add the printer in the printer settings in Ubuntu 18.04, it was already listed but that might have been because the old printer was on wifi and also a HP.  It has a small color touchscreen for some features like manual copy and scan.  I haven't tried any photo printing with it but it doesn't have one of the photo ink cartridges or even a spot for one and I rarely print any photos out

---

### Post by waltd on 2018-06-29
Am I correct to say that HP printers are the best choice for Ubuntu for home use? I currently have an Epson 600 and it consistently causes problems with Ubuntu. So I'm looking for a new printer that's trouble free. Is HP the way to go?

---

### Post by jeremy31 on 2018-06-29
They seem to work as this is the second HP that I have had while using Ubuntu, the first was problem free, just had to add a network printer and Ubuntu found the printer on the network and it just worked.  It has been a long time since I owned anything other than a HP printer

---

### Post by oldfred on 2018-06-29
I have two different HP and they work well.
I used to have to add the hp driver directly from HP.
But with 18.04, it just recognizes printer. The live installer installs a printer drive automatically in it also (which I do not really want.).
But HP ink is expensive if you want to print a lot of pages.
I have debated getting a Laser printer, maybe just black & white, but do not print many pages anymore.

---

### Post by Autodave on 2018-06-29
I have never had a problem getting an HP printer to work. In fact, I have a Laser Jet M277dw. It is connected to this machine via wifi. When I installed Xubuntu 18.04 on this machine, the printer was on because my had been using it. Upon completing installation, not only did it work, but even the scan feature worked. I never touched the printer or any settings and everything worked.

---

### Post by bodhin2 on 2018-06-29
have a wireless hp my wife bought and when i installed 18.04  it found the network and worked so far on 3 different machines.  just checked - 8600 printer

---

### Post by The Cog on 2018-06-29
I got myself an HP 5030 (cheapest envy model available) last Christmas. Very happy with it - Ubuntu just found it first time I tried to print a document. It has a web server that lets you configure things, check the ink level, and download scans (to PDF or jpeg, sadly not png). I signed up for their instant ink service too, which seems reasonable: small monthly fee and they send you new cartridges when you are running low. As far as I can see, the whole 5000 envy series run the same software, so they should all be equally compatible. The cartridges have the head built in, so no danger of a clogged head leaving the whole printer useless.

I

---

### Post by ajgreeny on 2018-06-29
I also have an HP Envy printer (4520) and that was also found automatically in my Xubuntu 18.04 with no action from me. I use hplip-toolbox to configure and manage it; install hplip-gui for that if you want to do the same.

This model also has the ink-jets integrated in the cartridge so a new cartridge gives a new clean jet if they should get blocked.  I have used compatible cartridges only in my HP machines now for many years, with no problems and because of the integrated jets I feel there is no danger of poor ink causing blockages to permanent jets, which I did get in another old printer.

---

### Post by ajgreeny on 2018-06-29
Threads merged to avoid confusion.

---

### Post by bodhin2 on 2018-06-29
ajgreeny - if the printer is found and it seems to work any need for the hplip and also i take it the hplip-gui is what i need in synaptic.  is the printers in settings and devices printers - additional printer settings enough?  sorry to ask - new to ubuntu and do not want to tweak something by accident and then it all stops working.  as long as it works i do not want to explore too much - learned a long time ago and a few times since then with my linux experience.


copied from synaptic

This package contains utilities with graphical user interface (GUI) for
HPLIP: HP Toolbox, HP Fax, ...


Note that all GUI utilities are based on the Qt GUI environment. There
are currently no equivalent utilities based on GTK+.

so will it work with the main 18.04 runnng gnome i take it and is gtk3?

---

### Post by ajgreeny on 2018-06-30
There is a difference between **need** and **want**, and you are probably quite correct, there is no absolute need for hplip-gui; however I find it useful for things such as cleaning and aligning the ink-jets if they need it, and in all honesty, I am not sure if that is so easy using cups as I've always used hplip-toolbox.

It will certainly work fine in a gtk environment, eg, my Xubuntu, as it pulls in what it needs when you install it, but if you find cups printing works as you wish without the toolbox, (hplip-gui), don't bother to install it.

---

### Post by bodhin2 on 2018-06-30
Ok i may check it out.  aligning the print heads when installing new ink may be a needed aspect.  do not remember the last time i installed the ink on her printer.  Not sure what was available - and that was another E distro.  not being a command line junkie i need all the help i can get. Thanks AJ

---

### Post by Topsiho on 2018-06-30
For supported hp-printers see:

[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

for the hplip that is in your ubuntu repository: see synaptic

I think (not: know) that hp is the best choice for a printer when you are using a linux distribution, as HP seems to cooperate well with the open source developers of drivers for their printers.

Topsiho

---

### Post by Paddy Landau on 2018-07-03
HP has (in my opinion) made a good name for itself by supporting Linux including Android. Any modern network-enabled HP printer should work well.

Once you've decided on a model, but before you make a purchase, search the model number here and in [Ask Ubuntu]("https://askubuntu.com/") in case others have found problems.

On your system, ensure that you install [FONT=lucida console]hplip-gui[/FONT], if not already installed, from the standard repositories. It includes HP drivers.

---

