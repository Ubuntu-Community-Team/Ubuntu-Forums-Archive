---
title: "[SOLVED] Networked printer no longer working"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by asgard_command on 2008-11-06
I have a Epson C66 connected to an Ubuntu desktop and working fine from there. However I can no longer print from the laptop over the network. This seems to be since I updated to Intrepid though I was sure I had set it up and used successfully since then, so something must have happened since.

When searching for printers the networked printer no longer shows up automatically, I have tried setting it up manually inputing the IP address of the desktop computer and leaving the port as default.

When trying to print I just get an error 'the printer may not be connected'

Anybody aware of any new issues regarding networked printing or can you walk me through a correct setup if I am suddenly doing something wrong.

---

### Post by bscbrit on 2008-11-06
I noticed a slight difference in the behaviour of the Install Printer applet in 8.10 with my network printer.  It might be related to the problem you have identified.  I haven't got a solution but I am going to spend some time this afternoon on a spare machine trying to pin down what is happening.  I will follow this thread to see if you find a answer and if I discover anything useful I will come back and let you know.

Good Luck.

---

### Post by Kellemora on 2008-11-06
Hi AC

Have you checked to make sure the printer is still shared?

If so, try unsharing it and resetting the share again.

Also, LOOK for a second instance of the same printer.  Somehow I wound up three instances of the same printer and only one was the right one.
So I uninstalled the other two and things have worked fine ever since.

TTUL
Gary

---

### Post by asgard_command on 2008-11-06
As far as I can tell my printer is still shared, and on the laptop I have show printers shared by other systems checked.
Still nothing shows up on autosearch.
Am I right to leave the port number as 9100 and just put the IP address of the desktop pc as Host?

There isn't anything new by way of firewall installed by default in intrepid that could be causing problems is there?

---

### Post by bscbrit on 2008-11-06
My networked printer shows 

socket://192.168.121.60:9100

as the connection.

Open System->Administration->Printers

Right click on your printer and select properties.  Check the format of the 'Device URI' which on my working system is in the format above.  If it is not, try manually editing it and see if this helps.

---

### Post by bobnutfield on 2008-11-06
I have always had the best luck with network printing using the ipp protocol.  To use it, just enter it this way:

> ipp://(ipAddressOfPrinter):631/printers/(name of printer)

I have been doing it that way for years and have never had an issue.  You can also open the Cups browser and set the printer up there to be networked.  Just open Firefox and type in the address bar:

> localhost:631

---

### Post by bscbrit on 2008-11-06
Looking more closely at your printer , I'm not sure that you have the correct mode selected.  The port 9100 is designed, I think, for a genuine networked computer i.e. one that has its own ethernet connection and is not connected to any particular computer.

Your C66 connects either to the printer socket or via a USB cable.  As I haven't got one I cannot test my theory but I think that you have to share it as a shared resource from the computer to which it is attached.  I'm at my limit of knowledge with USB printers so perhaps someone with more knowledge than I have can jump in and confirm how it should be set up?

bobnutfield's suggestion seems to be a likely path to follow...

---

### Post by asgard_command on 2008-11-07
ipp://(ipAddressOfPrinter):631/printers/(name of printer) 

That is the correct url I remembered it from when it used to automatically find the printer but I was still having no luck. Then I once again turned sharing off and back on again, and the printer was suddenly picked up automatically and is now working fine.
Something must have happened when I updated the desktop but I have no idea what the problem was or why it is now working fine. Hope it stays that way.
Thanks everyone for the help and suggestions.

---

### Post by bscbrit on 2008-11-07
I'm glad that your problem is solved.  Please use the Thread Tools selection near the top of the page to change the title to [SOLVED].

Did the computer prompt you to input a URL using port 9100 or did you make a guess at the setting?  If it is the former then I would consider putting in a bug report.  It shouldn't have suggested something that was not the appropriate way to connect to your printer.

Good Luck, and see you around the forums.  (By the way, I'm not sure where you live but looking at your posting patterns you are an early riser! EDIT - I should read more closely, you live in Nottingham!)

---

### Post by asgard_command on 2008-11-07
It didn't suggest anything port 9100 seems to be just the default port on the network setup protocol but as you said I think that is for full network printers.
Once the printer was recognized it automatically fills in the full url and connects without any manual input.

I think I may have figured out the main change in behavior that first caused some confusion. When I used to print from the laptop if the desktop wasn't on I would just power it on and the printer would become accessible. Now I have to actually log in to the desktop, I assume the cups server now doesn't start till after login.

---

### Post by bscbrit on 2008-11-07
There shouldn't be any difference in the printer operation between 8.04 and 8.10 - at least as far as I am aware.  Whether you want to pursue that further it up to you.  Come back if the current method of using the printer proves impractical and we will look at making it work the way you want it to.

---

### Post by asgard_command on 2008-11-07
I think I will just manage the way it is now, don't print too much anyway.
I just like to understand why things happen, always a little frustrating to be unsure why things are behaving in a certain way.
Thanks again.

---

