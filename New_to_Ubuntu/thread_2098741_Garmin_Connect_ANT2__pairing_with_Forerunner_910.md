---
title: "Garmin Connect ANT2  pairing with Forerunner 910"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by hollywoodpete on 2012-12-27
I am an admitted triathlon-nerd.  I had only saved one windows computer to upload Garmin data from my USB 305 until I discovered [http://www.andreas-diesner.de/garminplugin/doku.php](http://www.andreas-diesner.de/garminplugin/doku.php). It has served me well and I no longer have any  computers running windows. (about 10 running Linux). For Christmas this year my wife gave me a Garmin 910 which relies on an ANT2 USB stick to upload data. So far I have been unable to get the stick paired or working in Ubuntu. If I can simply get the data into a file on my computer so I can upload it Training Peaks, I would be grateful. 

In a nutshell, what I am looking for is a way to pair the 910 to the ANT2 stick in Ubuntu 12.10. Any help would be appreciated.

 lsusb
Bus 001 Device 002: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 005 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 007 Device 003: ID 0fcf:1008 Dynastream Innovations, Inc. 
Bus 008 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

The Dynastream is the ANT2 stick

---

### Post by lt_gustavsen on 2013-01-18
Have you seen this [http://blog.trails4you.de/2012/04/forerunner-910xt.html](http://blog.trails4you.de/2012/04/forerunner-910xt.html)

It describe a way to download fit files from the device to computer.

With the latest gpsbabel you can also convert the fit files to gpx. Like this
~/src/gpsbabel-1.4.4/gpsbabel  -i garmin_fit -f inputfile.FIT -o gpx,gpxver=1.1,garminextensions -F output.gpx

Personally I have the 305 and I'm happy with it.

---

### Post by hollywoodpete on 2013-01-18
> **lt_gustavsen said:**
> Have you seen this [http://blog.trails4you.de/2012/04/forerunner-910xt.html](http://blog.trails4you.de/2012/04/forerunner-910xt.html)

It describe a way to download fit files from the device to computer.

With the latest gpsbabel you can also convert the fit files to gpx. Like this
~/src/gpsbabel-1.4.4/gpsbabel  -i garmin_fit -f inputfile.FIT -o gpx,gpxver=1.1,garminextensions -F output.gpx

Personally I have the 305 and I'm happy with it.

I have the Edge 305 with a USB port which is no problem. I just can't seem to get the Garmin-extractor to work

---

### Post by lt_gustavsen on 2013-01-18
I can not test this, but maybe removing the ubuntu version of python-usb
```
sudo apt-get remove  python-usb
```
and install the one as described.

```
sudo apt-get install python-pip
sudo pip install pyusb
```

then try as root to run the script:

```
sudo python garmin.py
```

If it works then you can copy the udev rules and run garmin.py as normal user. 
I can not guarantee that this will work but I tested without the device and the script executes well.

---

### Post by hollywoodpete on 2013-01-18
Thanks for the help. I still seem to have an issue.

$ sudo python garmin.py
python: can't open file 'garmin.py': [Errno 2] No such file or directory

---

### Post by lt_gustavsen on 2013-01-18
You have to be in the same catalog as garmin.py. Garmin.py is a file from the Garmin-Forerunner-610-Extractor package. Just unpack it. And don't be afraid to ask.

---

### Post by hollywoodpete on 2013-01-18
Thanks, it looks I'm getting a little closer.  garmin.py ran and generated  a debug log file. It  created a garmin-extractor file in .config which contained a file called Script but there were no Fit or data files.

---

### Post by lt_gustavsen on 2013-01-19
Do you mind sharing the output from

```
python --version
sudo python garmin.py

ls ~/.config/garmin-extractor/
```

;)

---

### Post by hollywoodpete on 2013-01-19
xxxxxxxxxx@xxxxxx:~$ python --version
Python 2.7.3
xxxxxxxxxx@xxxxxx:~$ sudo python garmin.py
[sudo] password for xxxxxxxxxx: 
python: can't open file 'garmin.py': [Errno 2] No such file or directory
xxxxxxxxxx@xxxxx:~$ ls ~/.config/garmin-extractor/
scripts

The word scripts is in blue

---

### Post by lt_gustavsen on 2013-01-19
You still have to be in the Garmin-Forerunner-610-Extractor folder before you run 
```
sudo python garmin.py
``` ;)

---

### Post by hollywoodpete on 2013-01-19
> **lt_gustavsen said:**
> You still have to be in the Garmin-Forerunner-610-Extractor folder before you run 
```
sudo python garmin.py
``` ;)


I'm not sure how to do this? Sorry. The way I get the extractor to run is to go into the folder and then click on the garmin.py folder. I am getting even closer because my watch asked me if I wanted to pair with garmin-extractor. I said yes and it looks like the log file said there was new data. I am about to go on a run anyway so I can gather some data.

If you don't mind checking in later, that would be great. Your help has been fantastic. If there is something I should try now, I will hold off on running at this time

---

### Post by lt_gustavsen on 2013-01-19
You must use the cd command to change directory. On my system I can do something like
```
cd
cd Downloads/Garmin-Forerunner-610-Extractor-master/
sudo python garmin.py
```

The first cd brings you to home. Soon we are there :)

---

### Post by hollywoodpete on 2013-01-19
> **lt_gustavsen said:**
> You must use the cd command to change directory. On my system I can do something like
```
cd
cd Downloads/Garmin-Forerunner-610-Extractor-master/
sudo python garmin.py
```The first cd brings you to home. Soon we are there :)


Sooner then I thought:p. I had already moved the program into a hidden folder named .garmin-extractor in my home directory from previous instruction I had followed. cd garmin-extractor followed by garmin.py worked fine. I paired and downloaded all of the data and it showed up in my .config file as a fit file. I just need to figure out how to get the file uploaded into TrainingPeaks and this will be golden.

Thanks for all your help. This has been a great learning experience for me. If I was able to reproduce all of the steps to make  a guide for others, I would but I doubt I could make a working guide.

Thanks again for the help

---

### Post by plasman on 2013-07-03
This is a long shot, but the advice given here seems to have helped hollywoodpete.  I have a forerunner 610, but I can't even get it to pair.  When I enter:

sudo python garmin.py
From the correct directory, I get the following (which means nothing to me):


Traceback (most recent call last):
  File "garmin.py", line 205, in main
    g = Garmin()
  File "garmin.py", line 56, in __init__
    Application.__init__(self)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/fs/manager.py", line 64, in __init__
    self._node = Node(0x0fcf, 0x1008)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/easy/node.py", line 48, in __init__
    self.ant = Ant(idVendor, idProduct)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/base/ant.py", line 49, in __init__
    raise ValueError('Device not found')
ValueError: Device not found
Interrupted
Traceback (most recent call last):
  File "garmin.py", line 214, in <module>
    sys.exit(main())
  File "garmin.py", line 210, in main
    g.stop()
UnboundLocalError: local variable 'g' referenced before assignment



It also generates a log file in the directory which contains the following:
MainThread 2013-07-04 00:23:41,215  garmin.ant.base.ant  DEBUG     USB Find device, vendor 0xfcf, product 0x1008 (ant.py:44)

Please can anyone help?  I really don't want to have to dual boot into windows just for this one thing, but without being able to even view my GPS traces this rather expensive piece of kit is just a watch.

---

### Post by hollywoodpete on 2013-07-06
I wish I could help but I am pretty weak at this. Hopefully lt_gustavsen will jump in and help. My Garmin was then only thing left that kept me on Windows. After getting my 910 to pair with Ubuntu I am Golden. It has worked without fail. I even created a nice icon on my desktop that I click on then it pairs and saves the file as a .fit that I save and upload to my logs. I took me a while to get it working but in the end it was worth the fustration

---

### Post by hollywoodpete on 2013-07-06
> **plasman said:**
> This is a long shot, but the advice given here seems to have helped hollywoodpete.  I have a forerunner 610, but I can't even get it to pair.  When I enter:

sudo python garmin.py
From the correct directory, I get the following (which means nothing to me):


Traceback (most recent call last):
  File "garmin.py", line 205, in main
    g = Garmin()
  File "garmin.py", line 56, in __init__
    Application.__init__(self)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/fs/manager.py", line 64, in __init__
    self._node = Node(0x0fcf, 0x1008)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/easy/node.py", line 48, in __init__
    self.ant = Ant(idVendor, idProduct)
  File "/home/tim/Garmin-Forerunner-610-Extractor-master/ant/base/ant.py", line 49, in __init__
    raise ValueError('Device not found')
ValueError: Device not found
Interrupted
Traceback (most recent call last):
  File "garmin.py", line 214, in <module>
    sys.exit(main())
  File "garmin.py", line 210, in main
    g.stop()
UnboundLocalError: local variable 'g' referenced before assignment



It also generates a log file in the directory which contains the following:
MainThread 2013-07-04 00:23:41,215  garmin.ant.base.ant  DEBUG     USB Find device, vendor 0xfcf, product 0x1008 (ant.py:44)

Please can anyone help?  I really don't want to have to dual boot into windows just for this one thing, but without being able to even view my GPS traces this rather expensive piece of kit is just a watch.

Did you try lsusb?

---

### Post by lrohr on 2013-08-24
I had a similar problam, the product id is 1009 for the 610 and not 1008 so you have to change the product id in the files "~/Garmin-Forerunner-610-Extractor-master/garmin.py" and "~/Garmin-Forerunner-610-Extractor-master/ant/fs/manager.py"

if that's really the problem for you, one can check with

"lsusb | grep Dynastream"
which should give you something like
"Bus 003 Device 002: ID 0fcf:1009 Dynastream Innovations, Inc. "
the 1009 is the case for my new 610 it may be that older or newer gps clocks have different numbers ...

---

