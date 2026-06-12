---
title: "can't install JMF from bin file"
date: 2009-04-25
forum: Programming Talk
---

### Post by bandito40 on 2009-04-25
Hi,

I am having trouble installing Java Media Framework.  I followed this tutorial [http://www.luniks.net/luniksnet/html/java/jtvd/doc/jmf.html](http://www.luniks.net/luniksnet/html/java/jtvd/doc/jmf.html) to install JMF on Intrepid. When I gave the following command **sh ./jmf-2_1_1e-linux-i586.bin** it created the folder **JMF-2.1.1e**.  I didn't like the folder that it was opened in so I delete it.  
Now ever time I try to run the jmf bin file it does not recreate the folder.  

Does anyone know how I can fix this?

Thanks,

---

### Post by leonox on 2009-04-29
What is the size of the .bin file?... it's probably 0... you will need to download it again. 

Why do you need to use JMF?

---

### Post by bandito40 on 2009-04-29
You are right about the file size.  I downloaded the bin file again and installed it which gave the following errors:

Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.6017: 1: cannot open ==: No such file
./install.sfx.6017: 1: ==: not found
./install.sfx.6017: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
Done.


I am trying to run the video output from my WinTV capture card.  I was hoping to use Quicktime with the XawTV plugin but I have not been able to find the executable for QT in Ubuntu so Firefox will call it instead of another player.

I chose JMF because apparently google's Video4linux4java ([http://code.google.com/p/v4l4j/](http://code.google.com/p/v4l4j/)) supports capture cards better.

I tried VLC but it rarely works and MPlayer never works.

Thanks,

bandito

---

### Post by faskunji on 2009-05-18
same problem here, on 9.04

chmod u+x jmf-2_1_1e-linux-i586.bin

./jmf-2_1_1e-linux-i586.bin

after answering dialog questions, I have this output

```
Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.12459: 1: cannot open ==: No such file
./install.sfx.12459: 1: ==: not found
./install.sfx.12459: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
Done.

```
and after this bin file becomes 0 size.

Because of this I have to use JMF on Windows where it works fine. Please help...

---

### Post by Eestlane on 2009-05-19
Solution is here: [http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1](http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1)
> First rename the .bin file to .zip
Then with any tool, decompress the zip. It gives a comment that the beginning of the file has bytes that are not part of the zip (this is the script), but it decompress it correctly. It places the file in its subdirectory.
Then rename the file again to .bin, and execute it. It works!

EDIT: This is the real solution:
[https://bugs.edge.launchpad.net/ubuntu/+bug/104511](https://bugs.edge.launchpad.net/ubuntu/+bug/104511)

[QUOTE="Giovani"]1 - Erase any jmf.bin file that you had download. Download a new one and put in a folder, and check file size:

ls -l

This is a probably result:
-rwxr-xr-x 1 nobody nogroup 2419679 2009-03-07 11:52 jmf-2_1_1e-linux-i586.bin

filezise: 2419679 bytes

2 - Give permission to file:
chmod +x jmf-2_1_1e-linux-i586.bin

THIS IS THE MOST IMPORTANT STEP
3 - Edit jmf-2_1_1e-linux-i586.bin downloaded file with vim as root
vim -b jmf-2_1_1e-linux-i586.bin (YOU HAVE TO USE THIS COMMAND -b BECAUSE IT'S A BINARY FILE)

4 - At vim type this:
```
/tail
```*Press ENTER.*

Then press the key l to move to the left on that line, until the sign +.

Press i to insert text, and insert -n , with a space. *Press ENTER.*

The new line should be like this:
```
tail -n +309 $0 > $outname
```
5 - Now press ESC and type:
```
:wq
```*Press ENTER.*
6 - Now execute the jmf bin file.

That's it.[/QUOTE]

---

### Post by faskunji on 2009-05-20
Thanks Eestlane!   and Thanks to giovani to :)
Installed fine! I will check how webcam works later, but JMF installed well on 9.04.

Small note: for me downloaded file size is 2419676, not 2419679. But after vim editing it becames 2419679.

Thanks again.

---

### Post by Lucias_Wong on 2009-08-13
java.lang.Error: Can't open video card 1
java.lang.Error: Can't open video card 2
java.lang.Error: Can't open video card 3
java.lang.Error: Can't open video card 4
java.lang.Error: Can't open video card 5
java.lang.Error: Can't open video card 6
java.lang.Error: Can't open video card 7
java.lang.Error: Can't open video card 8
java.lang.Error: Can't open video card 9
Done.

i have report from install right this, is this a problem?
then i still can't use webcam on my thinkpad with mercury messenger.

best regard

---

### Post by faskunji on 2009-08-15
For me JMF installed ok as I wrote in my previous post.

But when I start JMF Studio and go to this menu:
File -> Preferences -> Capture Devices
I see only "JavaSound Audio Capture" in the list.
Pressing "Detect Capture Devices" button below the lits, shows this output in console. Below you can see same java.lang.Error: Can't open video card N errors.


```

JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
Name = v4l:UVC Camera (046d:0991):0
Trying 4 320 240
Trying 3 160 120
Trying 3 320 240
Trying 3 640 480
Trying 3 176 144
Trying 3 352 288
Trying 3 768 576
Trying 4 160 120
Trying 4 320 240
Trying 4 640 480
Trying 4 176 144
Trying 4 352 288
Trying 4 768 576
Trying 5 160 120
Trying 5 320 240
Trying 5 640 480
Trying 5 176 144
Trying 5 352 288
Trying 5 768 576
Trying 6 160 120
Trying 6 320 240
Trying 6 640 480
Trying 6 176 144
Trying 6 352 288
Trying 6 768 576
Trying 7 160 120
Trying 7 320 240
Trying 7 640 480
Trying 7 176 144
Trying 7 352 288
Trying 7 768 576
Trying 8 160 120
Trying 8 320 240
Trying 8 640 480
Trying 8 176 144
Trying 8 352 288
Trying 8 768 576
Trying 9 160 120
Trying 9 320 240
Trying 9 640 480
Trying 9 176 144
Trying 9 352 288
Trying 9 768 576
Trying 10 160 120
Trying 10 320 240
Trying 10 640 480
Trying 10 176 144
Trying 10 352 288
Trying 10 768 576
Trying 11 160 120
Trying 11 320 240
Trying 11 640 480
Trying 11 176 144
Trying 11 352 288
Trying 11 768 576
Trying 12 160 120
Trying 12 320 240
Trying 12 640 480
Trying 12 176 144
Trying 12 352 288
Trying 12 768 576
Trying 13 160 120
Trying 13 320 240
Trying 13 640 480
Trying 13 176 144
Trying 13 352 288
Trying 13 768 576
Trying 14 160 120
Trying 14 320 240
Trying 14 640 480
Trying 14 176 144
Trying 14 352 288
Trying 14 768 576
Trying 15 160 120
Trying 15 320 240
Trying 15 640 480
Trying 15 176 144
Trying 15 352 288
Trying 15 768 576
java.lang.Error: Can't open video card 1
java.lang.Error: Can't open video card 2
java.lang.Error: Can't open video card 3
java.lang.Error: Can't open video card 4
java.lang.Error: Can't open video card 5
java.lang.Error: Can't open video card 6
java.lang.Error: Can't open video card 7
java.lang.Error: Can't open video card 8
java.lang.Error: Can't open video card 9
java.lang.ClassNotFoundException: v4l:UVC
java.lang.ClassNotFoundException: (046d:0991):0
java.lang.ClassNotFoundException: 046d:0991
java.lang.ClassNotFoundException: /dev/video0


```

in dev folder I see /dev/video0 device but cannot connect with VLC too.
My webcam has also microphone so I have also /dev/audio1 there.
With VLC I can connect to audio1 and hear sound that is captured from webcam microphone.

Here's my dmesg output just after plugging in USB Webcam:

```

[ 2828.444080] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 2828.705155] usb 1-3: configuration #1 chosen from 1 choice
[ 2829.101589] Linux video capture interface: v2.00
[ 2829.183151] usbcore: registered new interface driver snd-usb-audio
[ 2829.183365] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[ 2829.187833] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input10
[ 2829.218412] usbcore: registered new interface driver uvcvideo
[ 2829.218419] USB Video Class driver (v0.1.0)

```

---

### Post by pechan98 on 2010-04-27
I have same problem :s

---

