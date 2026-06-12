---
title: "HOWTO: Setup the CX6600 multifunction under linux."
date: 2006-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-04-16
This guide is for pre-dapper versions of Ubuntu only - for newer versions please use the new guide here: [http://hjmills.co.uk/computers/linux/cx6600.php](http://hjmills.co.uk/computers/linux/cx6600.php)

I set one of these up earlier and it was a bit of a struggle for me (as a linux n00b) so I thought I would post what to do for anybody else who needs to know.
Where I have given something to type into a terminal it is formatted as code and where I have given text to type into a file it is in quotes. Don't enter the quotes when you type it in, just enter the stuff in between.

1. Plug it in and turn it on (make sure all the tapes and tags are taken off first, the USB port is inside)

2. Fill it with ink and paper as instructed in the little guide you get with it

3. Navigate to System -> Administration -> Printing

4. Select "New Printer" in the window that appears

5. Select it in the list of detected printers (I can't help if its not detected, sorry)

6. Click "Forward"

7. Change the Model to the "Stylus CX-6400" and click "Apply" (Leave the drive as the gimp-print default)

8. You now have a printer working! Yay! Shame scanning isn't so easy to do...

This scanning section was put together from material on the [www.clasohm.com](www.clasohm.com) blog ([permalink to article](http://www.clasohm.com/blog/one-entry?entry%5fid=12616) ). I assume you have a default linux installation with sane and xsane installed. (Obviously I assume you are using sane as your scanning program)

9. Run the following on a terminal:
```
sudo gedit /etc/hotplug/usb/libsane.usermap
``` 
Search for "0x04b8 0x0813" and if it doesn't appear in the document add the following to the end:
"libusbscanner 0x0003 0x04b8 0x0813 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000"

10. Save and close back to the terminal.

11. Run another line through the terminal:
```
sudo gedit /etc/sane.d/epson.conf
``` 
Then add the following to the end of the file: "usb 0x04b8 0x0813".

12. Check that you have specified the correct backend in /etc/sane.d/dll.conf (It should be epson) If it is not there, add it on a new line. [Thanks to Glenn Sommer for this]

13. Restart saned using ```
/usr/sbin/saned restart
```

**Troubleshooting**
If your scanner still does not work:
1. Try entering "sane-find-scanner" into a terminal. It should say something about an unknown flatbed scanner. If it manages this then try "scanimage -L" in a terminal. If this comes up with no scanners found then the scanner is only appearing to root users. If you type "sudo scanimage -L" then your scanner should appear. To fix this enter "lsusb". It should output something like the following:
```

billgates@linuxBase:~$ lsusb
Bus 003 Device 004: ID 0457:0151 Silicon Integrated Systems Corp.
Bus [COLOR="Red"]003[/COLOR] Device [COLOR="Red"]003[/COLOR]: ID 04b8:0813 Seiko Epson Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:0a01 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```
In the example above my scanner is the second device. Note down the two red numbers (bus id and device id) and enter the following:
```

sudo chmod 666 /proc/bus/usb/<bus_id>/<device_id>

```
(Make sure you fill in the bus id and device id)
Note - this is a temporary fix only which will be lost when you restart! I have created a script to change the permissions and then launch xsane but you will need to edit it to use your bus and device ids. It needs to be placed in /usr/local/bin (or somewhere similar - thats the best place imho) and given executable permissions. You can then create a launcher or edit the xsane menu entry to run "xsane-launcher". I attached the file...

[ I won't remove the troubleshooting section above but I am pretty sure that the errors people were having were caused by trying to use hotplug stuff on dapper (which uses udev instead of hotplug). This is all my fault as I was not aware of it at the time but now I am so please use the new guide (see above) for dapper and any versions since then.]

Your scanner should now work, if it doesn't go eat a mars bar (compulsory) and email me (hjmills@gmail.com) (optional)

---

### Post by new2linux9 on 2006-05-05
Hello would you mind explaining this part in more detail: 

> 12. Check that you have specified the correct backend in /etc/sane.d/dll.conf (It should be epson) If it is not there, add it on a new line. [Thanks to Glenn Sommer for this]


as I am trying to use your guide to get the scanner part working for an Epson ME100 (possibly also known as a CX1500). 

Thank you

---

### Post by Haegin on 2006-05-05
Ok - do the following from a terminal:
```

ls /etc/sane.d|grep epson

```
That should list a single file called epson.conf. If it doesn't post what it does list in this thread.
```

sudo nano /etc/sane.d/dll.d

```
This will open a file in nano. Just check there is the line "epson" in that document.
If its not there and epson.conf does exist just add "epson" on a new line within the document.
Press Ctrl+O to save the document and the Ctrl+X to close it.

---

### Post by Haegin on 2006-05-29
Ok, I have just installed kubuntu dapper drake so I can confirm the printer setup works. The scanner was much easier to set up and I only had to add "usb 0x04b8 0x0813" in the /etc/sane.d/epson.conf file by
```

sudo nano /etc/sane.d/epson.conf

```
Then just add (on a new line at the end):
```

usb 0x04b8 0x0813

```

If this doesnt work then please follow the rest of the guide and if you still have problems then please post here. Testing is still very much required so please notify me of your success or failure.

---

### Post by teaker1s on 2006-06-06
new driver out from epson which I have successfully used alien to create and install converted deb packages for both which now will run the epson cx6600 driver and print, later version of Iscan needed with dapper as old version doesn't work
pips-scx6500-6600s-cups_2.6.2-3_i386.deb  
and
iscan_2.0.0-1_i386.deb

---

### Post by new2linux9 on 2006-06-06
Thanks for the advice.  I'm currently in England at the moment and my printer is in China.  Will check it out when I go back.

---

### Post by teaker1s on 2006-06-06
glorious sunny weather in somerset uk:D

---

### Post by Haegin on 2006-06-06
I'm in Wiltshire and the weather is great at the moment. Really nice and sunny for a change.

---

### Post by Haegin on 2006-10-11
Just added a script to install the scanner for you so now its even easier. Its all explained in the original post.

---

### Post by teaker1s on 2006-10-11
Have to say the cx6600 has exceeded my expectations I bought mine cheap with an extended warrany as end of line-what can I say cheap printers are trash. the cx6600 rocks with iscan or gimp only issue I had was driver needed updating to work with dapper

---

