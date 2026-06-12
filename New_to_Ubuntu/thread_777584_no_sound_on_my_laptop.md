---
title: "no sound on my laptop"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mayurmaheshwari on 2008-05-01
sir,
i've ubuntu ultimate on my laptop (HP DV6767TX). since i've installed ubuntu, there is no sound. music player shows progressing of file, sound buttons are also working properly. i've vista also in which my speakers works properly.
kindly suggest what should i do......

---

### Post by TeoBigusGeekus on 2008-05-01
Open a terminal and type
```
lspci
```
and post us the results.

---

### Post by mano cazalet on 2008-05-01
pls also post your soundcard

you can find it with lspci in terminal

and check if accidentally volume is not muted

---

### Post by mayurmaheshwari on 2008-05-01
i've done as u said and here is the result:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by TeoBigusGeekus on 2008-05-01
> **mayurmaheshwari said:**
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


Your sound card is recognised...
Hmmm...
Type
```
alsamixer
```
in terminal and see if your master volume is muted...

---

### Post by mayurmaheshwari on 2008-05-01
no it is not muted...

---

### Post by mano cazalet on 2008-05-01
as im not an expert i can only contribute with this [link]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")
and hope we can alltogether make this solved somehow

it suggests there method J, but im not sure if it also applies to hardy and kernel 2.6.24

---

### Post by mayurmaheshwari on 2008-05-01
i've downloaded a folder from the link given. can you plz tell me how to install that...

---

### Post by TeoBigusGeekus on 2008-05-01
What are the contents of the folder?

---

### Post by mayurmaheshwari on 2008-05-01
it has many other folders :: acore,alsa-kernel,aoa,arm,doc,drivers,hal2,i2c
include,isa,mips,misc,modules,perisc, etc....
  it has also some files : aclocal.m4, aciclude.m4, cards-status, configure.in, copying cvscompile, etc......

---

### Post by mano cazalet on 2008-05-01
update: i checked again the how to linked above, 
method J says its for HP dv6000 series but for Hp pavilion dv6500 it recommends method G

so i'm pretty unsure which is your model and which method to try

---

### Post by arunjr on 2008-05-01
I had the same problem with my HP dv2119.
now its fixed. seems like sound was muted was by default. 
In GNOME ALSA mixer just unmuted. its just works fine. :)

---

### Post by mormor on 2008-05-01
Try this?

> Originally Posted by Joshua Netterfield View Post
The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
Code:

chmod +x ./alsaconf.sh
sudo ./alsaconf.sh

7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (; 

Worked for me on my intel-laptop and for another guy who hat this to say:

> Looking thru the script, it appears to redo the entire ALSA sound stack and driver set up. Basically like killing a fly with a sledgehammer, although seems to be the only way to get ALSA back into working shape.

Hope it works: )

---

### Post by mayurmaheshwari on 2008-05-02
my laptop is of dv6000 series.........

i've done exactly what you had said, it doesn't work...........

---

### Post by mayurmaheshwari on 2008-05-02
how to apply method "j".......

---

### Post by mano cazalet on 2008-05-02
ok, for method J then:

download the driver:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2
```

next step is to extract:
```
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
```

then go into the new folder:
```
cd alsa-driver-1.0.16rc1
```

and run the commands:

```
./configure --with-cards=hda-intel
```

```
make
```

```
sudo make install
```

---

### Post by mayurmaheshwari on 2008-05-02
in order to apply method j, when i type first code, it is giving ::


--23:35:36--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
           => `alsa-driver-1.0.16rc1.tar.bz2'
Resolving ftp.alsa-project.org... failed: Name or service not known.

---

### Post by mayurmaheshwari on 2008-05-02
i have downloaded it myself, can you plz tell me in which folder i should extract it........

---

### Post by kwacka on 2008-05-02
As a firm believer in the KISS principle: by default 'external amplifer' is selected which means that the internal amp is by-passed.

Right-click on the speaker icon in the bottom right corner.

Select 'open volume control', select 'switches' then 'edit' & 'preferences'.

Is 'external amplifier' selected? If yes, move to other solutions.

If not select it.

Click 'close'.

Is the box marked 'external amplifier' selected? If yes, unselect it. 

If no, move on to other solutions.

---

### Post by mayurmaheshwari on 2008-05-02
there are four four options in edit>  "master","PCM","Caller ID","Off-hook", which one to choose......

---

### Post by kwacka on 2008-05-02
"Right-click on the speaker icon in the bottom right corner.

Select 'open volume control', **_select 'switches' then 'edit' & 'preferences_**'.

Is 'external amplifier' selected? If yes, move to other solutions."

---

### Post by mayurmaheshwari on 2008-05-02
as to apply method j (above), due to the error by terminal, i've downloaded the folder manually, plz tell me where i should extract it.......

---

### Post by stchman on 2008-05-02
Install the latest ALSA drivers.

I have a page on this.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by mayurmaheshwari on 2008-05-03
after going through all these step i finally get sound. but after starting ubuntu and playing the first song, sound stops just after 5 seconds, and then i restart my computer and again the same thing..
   i think it may be due to my setting in sound control.
 in sound control>open volume control there are seven option : "master","headphone","PCM","front","front mic boost","line in boost","mic boost".  Plz tell me the level at which i should keep all these..........

and how many of these i should choose in edit>preferences.......

and what should i choose in volume control preferences...

---

