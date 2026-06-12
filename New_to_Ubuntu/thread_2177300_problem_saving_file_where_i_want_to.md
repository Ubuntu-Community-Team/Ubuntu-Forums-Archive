---
title: "problem saving file where i want to?"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by poppys-boat on 2013-09-28
hi there, i am a very new user of UBUNTU having always used the dreaded windows and i now need to learn ubuntu i am trying to run a couple of programs that read and write to a  eprom burner one is:-
 [https://code.google.com/p/eepe/](https://code.google.com/p/eepe/)
eePe and the other is Arduino:-
[http://www.arduino.cc/](http://www.arduino.cc/)
and both of them require me to read and write to the usb port my problem is i cannot get either to access the port, on eePe it gives help to use on ubuntu:-

[h=1]Fixes in Linux/Ubuntu[/h][COLOR=#000000][FONT=arial]To run properly you need to enable AVRDUDE to run without being root.
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Plug in the programmer and run[/FONT][/COLOR]
lsusb [COLOR=#666600]|[/COLOR] grep libusb[COLOR=#000000][FONT=arial]You should get a line like this:[/FONT][/COLOR]
[COLOR=#660066]Bus[/COLOR] [COLOR=#006666]003[/COLOR] [COLOR=#660066]Device[/COLOR] [COLOR=#006666]002[/COLOR][COLOR=#666600]:[/COLOR] ID [COLOR=#006666]16c0[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#006666]05dc[/COLOR] VOTI shared ID [COLOR=#000088]for[/COLOR] [COLOR=#000088]use[/COLOR] [COLOR=#000088]with[/COLOR] libusb[COLOR=#000000][FONT=arial]Notice the two numbers after ID.
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Create a file called **10-usbasp.rules** in directory **/etc/udev/rules.d**[/FONT][/COLOR]
 SUBSYSTEM[COLOR=#666600]==[/COLOR][COLOR=#008800]"usb"[/COLOR][COLOR=#666600],[/COLOR] ATTR[COLOR=#666600]{[/COLOR]idVendor[COLOR=#666600]}==[/COLOR][COLOR=#008800]"XXXX"[/COLOR][COLOR=#666600],[/COLOR] ATTR[COLOR=#666600]{[/COLOR]idProduct[COLOR=#666600]}==[/COLOR][COLOR=#008800]"YYYY"[/COLOR][COLOR=#666600],[/COLOR] GROUP[COLOR=#666600]=[/COLOR][COLOR=#008800]"adm"[/COLOR][COLOR=#666600],[/COLOR] MODE[COLOR=#666600]=[/COLOR][COLOR=#008800]"0666"[/COLOR][COLOR=#000000][FONT=arial]*replace **XXXX** and **YYYY** with the numbers from before. (ID XXXX:YYYY)*

Then execute:[/FONT][/COLOR]
 sudo restart udev[COLOR=#000000][FONT=arial]Alternatively just run this line:[/FONT][/COLOR]
sudo echo [COLOR=#008800]'SUBSYSTEM=="usb", ATTR{idVendor}=="16c0", ATTR{idProduct}=="05dc", GROUP="adm", MODE="0666"'[/COLOR] [COLOR=#666600]>[/COLOR] [COLOR=#008800]/etc/[/COLOR]udev[COLOR=#666600]/[/COLOR]rules[COLOR=#666600].[/COLOR]d[COLOR=#666600]/[/COLOR][COLOR=#006666]10[/COLOR][COLOR=#666600]-[/COLOR]usbasp[COLOR=#666600].[/COLOR]rules
but i cannot get my computer to save the file where it asks me to it just comes up with a big no entry sign i have searched all over and cannot find what i have to do to be able to access the directory it says, i can save the file in my own directory but i have no idea how to get permission to use any other directory's.

the main reason i installed ubuntu was to use these programs as windows will not allow me to run programs that have drivers that are unsigned and every one i spoke to said use ubuntu as it is much easier to do than on windows.

regards Poppy Ann.

---

### Post by Impavidus on 2013-09-28
I don't know anything about udev rules, but indeed using the sudo echo command with output redirect to write to a root-writeable directory doesn't work.

Run the command **gksu gedit /etc/udev/rules.d/10-usbasp.rules**, type your password and then a text editor will open. Write that line of text, save the file and exit. This should work.

---

### Post by poppys-boat on 2013-09-29
Many thanks Impavidus that worked great, or i think it did.
 
i still cannot manage to connect to my programmer but at least i managed to save the file as it told me to i just cannot find the settings to connect to the programmer but that is a different problem, i know i have much to learn with Ubuntu.

---

