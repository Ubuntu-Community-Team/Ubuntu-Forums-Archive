---
title: "HowTo: Canon Drivers in Hardy"
date: 2008-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by T0N3 on 2008-05-27
As I've discovered getting Ubuntu Hardy to print in colour to a Canon iRC 2880i can be a bit of a nightmare. Now that I've figured it out I thought I should put it here. 
This guide should work for most Canon printers and most versions of Ubuntu.

If you only want to print in black & white then it is fairly straight forward.

```
1. Goto System->Administration->Printing
2. Create a new printer queue
3. Select the type of connection to the printer (mine is Windows Printer via SAMBA)
4. Input the printer settings eg: 10.0.0.1/NameOfPrinter and authentication if needed
5. For drivers use Generic->PCL 5c->Generic PCL 5c Printer Foomatic/hpijs
6. Give it a name and you're set to go
```

If you would also like to print in colour then this is where the fun begins.

You will need the UFR Printer Drivers from Canon in Australia. The PostScript drivers are also there but I haven't tried them but I can't see why this guide won't work for them.
If you're using the iRC 2880 then you can go straight here 
[http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc2880_drivers.aspx]("http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc2880_drivers.aspx")
otherwise just go here and select your model
[http://www.canon.com.au/support/default.aspx]("http://www.canon.com.au/support/default.aspx")

Once you have the drivers and have extracted them then follow these steps.
Note: If you are using a version of Ubuntu that is older than Hardy you should just be able to run the deb file in the Debian folder and then you can skip to step 6

```
1. If you try and run the deb file in the Debian folder in Hardy it will give a dependency error regarding libcupsys2-gnutls10. So...
2. Run sudo apt-get install alien
3. Go to the extracted drivers RPM directory in a Terminal
4. Run sudo alien -c *.rpm (The -c will include any scripts in the package)
5. Run your newly created deb packages. First the cups common one then the driver one.
6. Follow the intructions above for the setting up of only black & white printing up to and including step 4
7. For drivers use Canon->iR C2880/C3380 UFR II->iR C2880/C3380 UFR II (or whatever model you are using)
8. Give it a name and you should now be printing in colour
```

In case you were wondering why you get the dependency error in step 1, the reason is that the Debian package was converted from a RPM one, using alien. Alien picked up the dependencies that where present on the system that the package was initially created.

Like I said at the beginning, this should work for most Canon printers because I found the link for the Canon Australia on a forum explaining how to get a different model of Canon printer installed on Ubuntu Edgy.

---

### Post by mramirez_fidesol on 2008-09-19
After following these steps, it still doesn't work for printing in color. If I folow these steps for the generic driver, I can only print b/w documents, but if i install the canon color drivers it doesn't print anything.

Can anyone help me?

Thanks in advance.


P.D.: Sorry about my English. u_u'

---

### Post by Thomy23 on 2008-10-08
Hi guys


I'm currently having am similar problem with my IRC2880. It's connected directly to the network, and i firstly wanted to try the generic PS driver. I entered

socket://xxx.xxx.xxx.xxx:9100

as the device IP (i hope this is correct) but got not output. When i then tried the PS Drivers from canon i got no output either. Can it be that i have to enbale PS support via the WebGUI first or does anyone know where the problem is?

Greetings 

Thomy

---

### Post by tgyorgyi on 2008-10-08
Thank you, it worked for IR 2022i network printer, I tried Canon drivers before, but those did not work, and the Linux driver available on the Cannon support site gave error message upon installation (on both a Xubuntu-running old desktop and an Ubuntu-running Amilo laptop). When I clicked on new printer, the Canon  was already in the list.

One minor thing: if I leave under the "printer settings" tab the default tray on "printer default", the printing job is sent to the manual tray (which is not the default of the printer). I changed it to upper tray, since this is where we keep A4.

---

### Post by TSJason on 2009-07-15
Big thanks for this thread! Worked for me great.

---

