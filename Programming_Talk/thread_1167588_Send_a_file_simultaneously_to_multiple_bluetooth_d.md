---
title: "Send a file simultaneously to multiple bluetooth devices"
date: 2009-05-23
forum: Programming Talk
---

### Post by eng_akyq on 2009-05-23
Hi to all
I am working in a project that detect all bluetooth nearby devices and simultaneously send a text file to them.
I want to add this feature to the following code ```


import bluetooth
import os

print "performing inquiry..."

nearby_devices = bluetooth.discover_devices(lookup_names = True)

print "found %d devices" % len(nearby_devices)

for name, addr in nearby_devices:
    print "  %s - %s" % (addr, name)
for name, addr in nearby_devices:
    os.system('obexftp -b -p a.txt')

```
As you can see I have tried with obexftp but it's only send to one defined bluetooth device and I want to send to all bluetooth devices
Any idea to implement that
Thank you very much

---

### Post by kidders on 2009-05-24
Hi there,

Bluetooth is a round robin protocol ... afaik, conventional multicasting is impossible by design. You'll probably have to send your file to one device at a time.

---

### Post by eng_akyq on 2009-05-24
I am totally agree with you
Would you suggest a method for send a file one by one until it would be no bluetooth device around?
Thanks in advance

---

### Post by kidders on 2009-05-24
The biggest problem you're likely to run into is the amount of time it will take to perform tasks. For instance ...[LIST]
[*]Let's say you scan for obex-capable devices. There may be 11 or 12 in range, but you might only pick up 10 of them, because of the length of time it takes to perform all the inquiries.
[*]Now, suppose you start sending your file, one device at a time. If you hit one that requires user intervention to accept the transfer (eg a mobile phone or pda), it could take up to a minute to complete it. So, by the time you get round to your 6th device, it may no longer be in range.
[*]Worse still, while you're busy sending files to the 10 devices you know about, others may be entering & leaving range completely undetected.
[/LIST]
Chances are you already know all that though, or you wouldn't be asking the question hehe!!

Some suggestions...

[LIST]
[*]Ideally, you would use more than one bluetooth radio. That would give you the option of continuously scanning for new devices, or transmitting to multiple devices simultaneously.
[*]If you're only using one radio, you could try prioritising detected devices in order of the length of time you think they'll occupy it for & how long you feel they'll stay in range. For example, a desktop computer is probably never going to let you send it a file without user confirmation, and the user may not even be sitting in front of it. It's very unlikely to move out of range. That makes it the last device you should try to talk to, imo.
[*]While typing this post, I've been trying to make up my mind whether you should (a) scan, transmit to all detected devices & scan again, or (b) scan, send to one device, scan again, send to another, and so on. I'm inclined to think (b) is a better option. Each time you scan, you could push devices you've seen before down your file transfer queue & insert new devices into the top of it. It seems to me that the longer a device is in range, the longer it is likely to *stay* in range, so getting around to sending them your file it less urgent.
[/LIST]

Is that any help?

---

### Post by eng_akyq on 2009-05-25
That's helping very much to make to make the idea very clear, thank you very much for your concern. I hope if you may to indicate how I add a feature that try to send a file to detected device for once if the client accepted the bluetooth connection then the server tries to catch another bluetooth device and do the same procesure until it would be no bluetooth device.
The time is not important for me.
Now the concept is clear, but I don't know how to implement it to the code.
I hope if you may help me or at least show me the way to continue and thanks again for your concern.

---

### Post by kidders on 2009-05-26
Sorry... looks like Python, which isn't a language I'm particularly familiar with.

---

### Post by eng_akyq on 2009-05-28
Dear Kidder
As you know all programming language could share the same core idea.
Could you please indicate what is the function or package or module or command that could satisfy what we discussed before in any language you prefer?

I hope you help me as you done previously.
Thank you very much

---

### Post by soltanis on 2009-05-28
Layout your code thusly:

1) Scan for devices in range
2) Initialize a list of all the devices found, ordered from top to bottom in decreasing likelihood of the device leaving the vicinity. Cell phones/mobile devices should get higher priority, followed by laptop computer, then stationary devices. It follows from this order that even if the devices require confirmation to accept a file, the user is more likely to be there to accept it.
3) Send a file to the first device in the list, then remove it from the list if the transfer is successful. Timeout after a while so that you don't hang waiting for someone to accept the transfer.
4) Remove the device from the list, put it in a list of devices who have gotten the file (or who take too long).
5) Rescan for devices in range. Devices that are not in the sending queue but who are in the list of devices with the file are ignored. New devices should be sorted (among new devices only) then placed on the top of the sending queue. Devices already in the queue are ignored.
6) Repeat steps 3-5 until no more devices remain.

This isn't a perfect implementation of the algorithm mentioned by the earlier poster (it doesn't "push down" devices which have stayed in range, since that's actually pointless, if a device leaves range then you won't be able to send a file to it, so bumping up its priority does nothing). It is a very close approximation, and is detailed enough to get you started.

As you can see, the most difficult part is going to be arranging the lists. I suggest you use a language powerful for doing that (Python is fine, not optimal).

---

### Post by UbuKunubi on 2009-05-29
Just out of curosity, I looked at the python API for bluetooth, and connot see a way to use more than 1 radio, is there a way?

Thanks,
Ubu

---

### Post by eng_akyq on 2009-05-29
As I have seen with python there's radio channels functionality. I have seen it with Blueproximity software and it's open source you can download it directly by Ubuntu terminal by the command *sudo apt-get install blueproximity*

---

### Post by nnsjw702 on 2012-11-01
can we implement the algorithm mentioned above using JAVA and J2ME ?

Please throw some light. I am very much in need of help, since it is important for our final year project.


Thanks in advance

---

