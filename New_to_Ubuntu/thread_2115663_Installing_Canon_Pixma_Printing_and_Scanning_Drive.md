---
title: "Installing Canon Pixma Printing and Scanning Drivers"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by green white blue on 2013-02-13
Using **Ubuntu 12.10** on my laptop I also have a **Canon Pixma MG 3200**, which is connected wirelessly to my router.

I don't really need extra drivers for printing since I can simply add a printer through the "add printer" dialogue in system setting/printer and choose network printer and then the older 3100 model.

So far so good. Now I also want to use the Pixma's scanning ability. How do I do this? Thankfully Canon provides Linux drivers here:
[U][Printer](http://www.canon.de/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:83-994675&page=1&type=download)
[Scanner](http://www.canon.de/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:83-994707&page=1&type=download#)[/U]
*(clickable links above)*

I downloaded both and managed to extract the archive, creating two new folders (*packages* & *resources*) as well as a *install.sh *file.

I tried to run the install.sh and *something* happens, but it vanishes too fast for me to see whether it's an error messages or not. Nothing else changes.

My question: What exactly (I am very new to this) do I do with this file?

I understand that once the scanner driver is installed it should be recognised when using "simple scan", right? Right now it doesn't.

Thank you for reading and if you could give me a hint I'd be grateful.

---

### Post by JiuJitsu500 on 2013-02-13
The scanner part is almost always done only through wired.

I have a photosmart 5510 and printing works flawlessly through wireless on my ubuntu, mac, and my other ubuntu laptop. Windows, oddly enough, simply won't do it for some reason.

Either way though, all of them, 2ubuntus and a mac need to have the wired connection for scanning to work. If your printer driver is fine out-of-the-box, then your scanner should be too. I'm willing to bet a little that yours also must be wired to scan.

Which sucks. I've been looking for a way to wirelessly scan too, but can't find a lot on it, and no help yet.

---

### Post by deadflowr on 2013-02-13
I scan wirelessly through GIMP.

I have a pixma mp495.
When I extracted the scangearmp I open the package folder and first install the common deb file(for the arch of the system:i386, or amd64), and then install the scangear deb file.
I then open gimp and then file >> create >> scangear mp.
It opens a scan list and I click on update scanner and a minute later my scan is connected. then I scan.

---

### Post by JiuJitsu500 on 2013-02-13
Hmmm.... damn it then. I stand corrected - past two printers I had could scan wirelessly.

I'm now off to go find out if mine can do that!

---

### Post by pdc on 2013-02-14
hello greenwhiteblue; welcome to the ubuntu forums;

you ask

> [COLOR="Magenta"]My question: What exactly (I am very new to this) do I do with this file?[/COLOR]

........we can hope that the install worked for you:

you can check the files are in place by copying and pasting this into a terminal

> [COLOR="Red"]sudo dpkg -l | grep scangear[/COLOR]

......and it should show if the scangear files are installed .......

......but for you.......more importantly.........to check if it works....... type in your terminal

> [COLOR="Red"]scangearmp[/COLOR]

and if the programme is happily installed, the Canon programme that is called ScanGearMP should open, and recognise your printer/scanner and let you scan.......

a launcher will help you do this time and time again.......

as advised here

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

the commands are

> [COLOR="Red"]sudo apt-get install gnome-panel[/COLOR]

and that installs the ability to create a launcher and 

> [COLOR="Red"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

opens a new launcher for you and its **COMMAND** must be [COLOR="Red"]scangearmp[/COLOR]

---

### Post by deadflowr on 2013-02-14
You don't need gnome-panel to create launchers, though it's a far easier way of doing so.
Basically what the method above does is creates a .desktop file.
You can do this manually by opening gedit and adding the following for a basic launcher:

```
[Desktop Entry]
Name=what ever you want to call it
Exec=the command
Type=Application
Icon=any image you like
```

When saving, use the save as feature and name it whatever you want, followed by the extension .desktop.
Typically you would put it in the /home/username/.local/share/applications folder.


But plus one for the scangearmp command, I forgot about that, as I've been using GIMP for the basic reason as I usually need to do some cleaning of the image anyway.

---

### Post by green white blue on 2013-02-20
It took a while for me to figure out how things work, but thanks to you I finally figured it out. Thank you very much, you are very friendly!

Only remaining thing is I can't install the Canon drivers as I get a message that there was a problem with a package that hasn't been found. Maybe a mistake on Canon's side writing their script, who knows. It doesn't matter much since I can simply install the Pixma MG3100's drivers from the database and I don't think I'm missing much (although I haven't tried duplex printing). Anyway, it works now, though only through the scangear software. SimpleScan still does not find the scanner, but it hardly matters. Thanks again!

---

### Post by pdc on 2013-02-20
...........I am not clear what you are trying to tell us greenwhite&blue..

If I just do simple things..

If I go here 

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download)

it is a link for the [COLOR="Magenta"]debian package[/COLOR] for the [COLOR="Magenta"]Canon MG3200 serie[/COLOR]s (which would include yours)

...... the package is [COLOR="SeaGreen"]scangearmp-mg3200series-2.00-1-deb.tar.gz
[/COLOR]
......so that would drive the printer, and allow duplex printing

(as I have on my MG3100 series printer.......)

so........if you .................

1) turned the printer off

2) deleted any existing drivers from Menu: Administration: Printing

3) downloaded this file to your Downloads directory by selecting save 

4) then copied and pasted these commands into a terminal

> [COLOR="Red"]cd Downloads[/COLOR] 

> [COLOR="Red"]tar -zxvf scangearmp-mg3200series-2.00-1-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd scangearmp-mg3200series-2.00-1-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

........the script should do it all........watch it......about half way through its actions.......it will ask you to turn the printer on....and ask you to indicate if you want USB or wifi.......

you should have a working printer 

AND: .......and wait ............there's more ......!!

if you copied and pasted this command

> [COLOR="Red"]cngpij P MG3200[/COLOR]

it is a utility that Canon supply (the utility is [COLOR="Blue"]cngpij[/COLOR] ) 

.......it allows you to clean ink nozzles etc and if you make a launcher you can launch it as needed.........

(see thumbnail)

---

