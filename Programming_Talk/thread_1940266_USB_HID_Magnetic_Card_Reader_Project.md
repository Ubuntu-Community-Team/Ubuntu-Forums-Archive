---
title: "USB HID Magnetic Card Reader Project"
date: 2012-03-13
forum: Programming Talk
---

### Post by finch127 on 2012-03-13
Hey guys,

So I recently bought a cheap MSR100 model USB HID Magnetic Card Reader [3 tracks] off of Amazon, it's from a Chinese manufacturer with no manuals or disks, and I have to reprogram it and have no clue what I am doing, so here are some very general questions:

1. I scan an ID card and it outputs some numbers I don't want, and some numbers I can work with. Is there anyway I can just make it output the first track or filter its input to the system? It is a keyboard emulator / wedge device.

2. I was thinking of reprogramming the reader to only send out track 1 information but I have no clue how these work. I know I need to send a command to /dev/usb/hiddevice0 or something like that but I used the "printf <command> > /dev/usb..." method and it failed.

3. I was also thinking of writing some python code to act as a driver and filter the input before it reaches X11 and prints to the screen. It outputs in the format: %IDNUM;USELESSGARBAGE% and it's trivial to filter the incoming input string and make it access the device but I have no clue how to get this code to run before X registers the keypress events or prevent X from seeing the scanner [can I just disable it as a keyboard then have the python program interface with X?]. 

Any way you guys can give me a USB tutorial and a rundown of X's structure? Also is there anyway I can monitor X keypress events? If worse comes to worse I can just remove the % and ? and ; signs from the keyboard map for the device so I get 1 big long number and I can deal with that.

---

### Post by Zugzwang on 2012-03-13
What are you actually doing with the stuff you read in?

Typically, you will have some application in which you feed the data that you read from the swipe cards. The canonical way is to have your application filter the data for you before processing it. This will remove all requirements of you to modify drivers or hardware, which is typically much more messy than implementing the filtering into the application layer.

---

### Post by finch127 on 2012-03-13
Well it's an ID reader, and what I am doing is reading ID numbers off of track 1 to input directly into a web form for checking out books in a personal library. I could use java to filter the text input? I do not know but ideally I would like to remove it completely from the output so I can re-purpose these readers for other things.

---

### Post by Zugzwang on 2012-03-14
> **finch127 said:**
> Well it's an ID reader, and what I am doing is reading ID numbers off of track 1 to input directly into a web form for checking out books in a personal library. I could use java to filter the text input? I do not know but ideally I would like to remove it completely from the output so I can re-purpose these readers for other things.

The point is that the web form will be sent to some server. If you can modify the scripts/servlets/whatever for the web forms, then stripping the unneeded "garbage" should be easy. Depending on the way the whole thing is built, the garbage truncation could also be made with JavaScript.

---

### Post by Damascushead on 2012-03-15
Also note, that many times the reader itself will encrypt whatever you are scanning. This is usually a way for them to force you to use their proprietary software as a means of reading the data. If you can find a key, you may be able to figure out the encryption. That is possibly what all that giberish is that you don't want.
 
Hope that helps :)

---

### Post by anewguy on 2012-03-15
Also keep this in mind:  most devices need a device driver - in your case you are sort of writing one if you are trying printf's redirect to the logical device.  To really do things with a USB device, you need to be familiar with USB endpoints of the device, what command structure it takes on those endpoints, and therefore also what data is emits back out the endpoints.  You will need libusb for this, and if you haven't ever used low-level USB communications before you're in for a learning curve.

You should also post the maker and model of the card reader (unless of course that's in Chineese, someone else may be able to help you with the Chineese).  You'd be surprised at the stuff we can dig up.

Dave ;)

---

### Post by Zugzwang on 2012-03-16
> **anewguy said:**
> Also keep this in mind:  most devices need a device driver - in your case you are sort of writing one if you are trying printf's redirect to the logical device.  To really do things with a USB device, you need to be familiar with USB endpoints of the device, what command structure it takes on those endpoints, and therefore also what data is emits back out the endpoints.  You will need libusb for this, and if you haven't ever used low-level USB communications before you're in for a learning curve.


In this case, this is probably not necessary, as according to the starting post, the device "behaves as a keyboard", and thus is handled by Linux' default keyboard driver already.

---

### Post by anewguy on 2012-03-16
Hmmmmm....if this one works like that, that's great!  Years ago (like about 1991) I had to write the driver side code for time clocks that had the card swiper.  I never thought about the swiper being separate and using a simpler communications method.  With the time clocks, they obviously held a lot more information internally so retrieving information wasn't a real-time read of swiper.  I just know from past experience with low-level USB communications with some non-standard cameras and some home-built things that it has required using libusb functions and reading/writing on the endpoints.  I wish I could have communicated with those devices by just treating them as a keyboard - would have made life much easier!

Great to know!  Thanks!

Have a good one!
Dave ;)

---

