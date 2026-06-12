---
title: "Using 12.04 &amp; Unable to get Canon D480 printer to work"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by chadwick72 on 2014-04-30
I have tried a few things to get a driver to load for the Canon D480 but I am new and don't know what I am doing.  I have seen some posts similar to this issue and have tried to understand some them but truly do not understand.  Any help would be appreciated!!!

---

### Post by pdc on 2014-05-02
so you need the Canon UFR driver; 

it is here on the US Canon website [http://www.usa.canon.com/cusa/support/consumer/copiers_fax/multifunction_copiers/imageclass_d480#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/copiers_fax/multifunction_copiers/imageclass_d480#DriversAndSoftware) but this may just give you the cover page so you need to tap into drivers; linux; UFR .................download and save

___________________

are you using 32bit ubuntu? If so, it is a little easier..................

_____________

is your printer connected by usb cable: 

______________

do you know how to open a terminal, and paste commands into it .........

if you can, please copy and paste this > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] and copy and paste back what you get 

______________

maybe if you just get back to me with the above; and then I can give you some commands to copy and paste into a terminal; 

__________________

if you subscribe to a thread; using the button a few down .........you can perhaps keep in touch with a thread more easily

---

### Post by chadwick72 on 2014-05-02
Thank you for the reply!!!!  This is what I got after I pasted that into the terminal:
 network socket
network ipp14
network ipp
network ipps
network beh
network https
network http
network lpd
network smb
direct hp

---

### Post by chadwick72 on 2014-05-02
I am using 32bit Ubuntu 12.04 and it is connected via USB cable.

---

### Post by pdc on 2014-05-02
thanks; 

1) can you just ensure the printer is connected to the computer; that it is turned on; and then again run the command 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

..............I would sort of expect to see > [COLOR="#EE82EE"]direct usb:/dev/usb/lp0[/COLOR] or something similar

please tell me if you get something like that; and copy and paste back exactly what it is ................................
__________________________________________

2) ..............32bit is good: thanks
__________________________________________

3) why don't you go ahead and download the file I suggested: if you elect to [COLOR="#0000FF"]SAVE[/COLOR] it when you click to download it; and it should by default be saved into your Downloads directory: it should come down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V280_us_EN.tar.gz[/COLOR] and you could practice opening a terminal and pasting this command

> [COLOR="#FF0000"]cd Downloads[/COLOR] (and then hit the Enter key)

and if you now copy or type > [COLOR="#FF0000"]ls[/COLOR]      .........that asks the computer to LIST what is in that directory; and you should see the file I mention in green above

---

### Post by chadwick72 on 2014-05-03
This is what I get when printer is connected via USB:
network lpd
network ipps
network http
network ipp
network socket
network ipp14
network smb
network beh
network https
direct hp
direct hpfax
direct usb://Canon/D460-490%20(UFRII%20LT)?serial=SJ3008490941Q&interface=1
direct usb://Canon/D460-490%20(FAX)?serial=SJ3008490941Q&interface=2

I also downloaded that US file and it did show up in the directory.

---

### Post by pdc on 2014-05-03
great; sorry for the delay; 

so three steps:
1) install drivers
2) restart cups 
3) register printer

if the commands to paste in are in red..

__________________

step 1)

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V280_us_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V280_us_EN/32-bit_Driver/Debian[/COLOR]         and that gets you inside the directory where the needed drivers are: the command [COLOR="#FF0000"]ls[/COLOR] should show you [COLOR="#008000"]cndrvcups-common_2.80-1_i386.deb[/COLOR] and [COLOR="#008000"]cndrvcups-ufr2-us_2.80-1_i386.deb[/COLOR] and to install...........

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.80-1_i386.deb[/COLOR]        (you will be asked for your sudo password)

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-ufr2-us_2.80-1_i386.deb[/COLOR]

-________________-

step 2) > [COLOR="#FF0000"]sudo /etc/init.d/cups restart[/COLOR]

________________

step 3) > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v direct usb://Canon/D460-490%20(UFRII%20LT)[/COLOR]        (Canon call that registering the printer (PPD) with the print spooler.)

...........that should create something for you to click on and print..........here's hoping ....................

---

### Post by chadwick72 on 2014-05-05
Thank you for helping me with this!  This is what I get when I copy/paste the last command:
chad@chad-desktop:~/Downloads/Linux_UFRII_PrinterDriver_V280_us_EN/32-bit_Driver/Debian$  sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v direct  usb://Canon/D460-490%20(UFRII%20LT)
bash: syntax error near unexpected token `('
chad@chad-desktop:~/Downloads/Linux_UFRII_PrinterDriver_V280_us_EN/32-bit_Driver/Debian$ 

Not sure what it is doing.  I appreciate your time!  It did everything as you said it would up until the last command.

---

### Post by pdc on 2014-05-06
sorry;

when I look at the command, the [COLOR="#0000FF"]direct[/COLOR] I feel should not be there; and we should add the -E at the end.............

the format should be 

> sudo /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -E

so let's try

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v usb://Canon/D460-490%20(UFRII%20LT) -E[/COLOR]

is that any better?

---

### Post by chadwick72 on 2014-05-06
This is what I get when I paste that into the terminal with the printer on:
chad@chad-desktop:~$ sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v usb://Canon/D460-490%20(UFRII%20LT) -E
bash: syntax error near unexpected token `('
chad@chad-desktop:~$

---

### Post by chadwick72 on 2014-05-06
I did a search and saw in a post that they recommended "" around the parenthesis.  I tried the quotes around "(UFRII%20LT)" and it worked!!!!  Thanks alot!  I could not have done it without you!!!

---

### Post by pdc on 2014-05-06
I am sorry about this: I was quoting what Canon recommended in their readme;

what you gave was > usb://Canon/D460-490%20(UFRII%20LT)?serial=SJ3008490941Q&interface=1 and Canon seem to foreshorten it 

In contrast, in CUPS, on our computer our MG3100 is registered as Connection:	usb://Canon/MG3100%20series?serial=402E18&interface=1

..............so if we give the full name in the registration and see if > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v usb://Canon/D460-490%20(UFRII%20LT)?serial=SJ3008490941Q&interface=1 -E[/COLOR] is good

 (there was a space between the final = and the 1 and I have removed that space)

any joy? If not, ............
__________________________________________________________________________________________________________________--
I had thought we might see > /dev/usb/lp0 in the initial > /usr/sbin/lpinfo -v data that you pasted;

Canon say the format is > /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -E

..............so............if you only have one printer? ..................connected by USB cable to your computer............it should be .............../dev/usb/lp0......and the registration script below......should find it.............

so if we see if > sudo /usr/sbin/lpadmin -p CANON-D480 -m CNCUPSD490ZS.ppd -v usb://dev/usb/lp0 -E is acceptable:

---

