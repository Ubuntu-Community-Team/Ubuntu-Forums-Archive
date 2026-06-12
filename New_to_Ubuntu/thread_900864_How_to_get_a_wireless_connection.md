---
title: "How to get a wireless connection"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ireland4ever04 on 2008-08-25
Hey everyone! I am completely new to linux and everything. I have Ubuntu 7.10 and its pretty cool! But my problem is that I have a Wireless router connection that worked fine in windows vista but now that I have made the move to Ubuntu its no where to be found? I dont know anything and I installed the NdisWrapper? but I have no idea what that is or what it does. Im kinda new to this computer stuff I have an idea on what stuff is but really no clue the innerworkings of it all! If someone can help me get a connection again that would be great or point me in the right direction and remember I have no idea what im doing! lol Thanks everyone!

---

### Post by niccholaspage on 2008-08-25
We need more info.Please post your wireless card specs.

---

### Post by nickgaydos on 2008-08-25
If you or one of your friends have an ethernet cable and router lying around, plug it in and go to Add/Remove. Install Windows Wireless Drivers. Next, go to your wireless cards website and download the drivers for it. Go to Windows wireless Drivers in Administration and click "install". Search through the wireless drivers for a .inf extension. This will install the driver. This worked for me hopefully it works for you :)

---

### Post by ireland4ever04 on 2008-08-25
umm ok... im really new to this and kinda embarrassed but ow do i find that?

---

### Post by ireland4ever04 on 2008-08-25
Ok i went to system,admin, but there isnt Device Manager and there isnt Windows wireless drivers in the list?

---

### Post by niccholaspage on 2008-08-25
Do you know what your Wireless Card's Specs are?

---

### Post by nickgaydos on 2008-08-25
> **ireland4ever04 said:**
> Ok i went to system,admin, but there isnt Device Manager and there isnt Windows wireless drivers in the list?
You have to install it from Add/Remove, get a friend to loan you his ethernet cable and install it

---

### Post by ireland4ever04 on 2008-08-25
ok hmm one thing i have noticed is when i boot my comp up it says Failed:PCI allocating memory resourses? I have no idea what that means but isnt PCI aprat of network cards and stuff?

---

### Post by niccholaspage on 2008-08-25
Idk Anything About PCI..And Not to be mean or anything but PLEASE Post your Wireless Card's Specs.

---

### Post by ireland4ever04 on 2008-08-25
I dont know what my wireless card specs are I dunno how to get them? Im on a windows comp now with the same card thats in my ubuntu comp so i dunno if that helps?

---

### Post by niccholaspage on 2008-08-25
Hm...What Windows Version are you running?(XP,Vista Eh...)

---

### Post by grEnAlEins on 2008-08-25
> **ireland4ever04 said:**
> I dont know what my wireless card specs are I dunno how to get them? Im on a windows comp now with the same card thats in my ubuntu comp so i dunno if that helps?

Open up the device manager in windows and you will see info about your wireless card.

You could also boot Ubuntu, open terminal, type "lspci" and paste the output here.  That should get you on your way.

Like everyone here is saying, you are going to need an Ethernet cable in order to get things working.

---

### Post by ireland4ever04 on 2008-08-25
well im running xp on this one but I just remebered this is the comp that the modem is hooked up to so it wouldnt have a wireless card in it i dont think...

---

### Post by niccholaspage on 2008-08-25
You need to boot Windows On the Laptop and Than Go to the Device Manager And you will be able to see the details for the driver.Oh and you can also Boot Ubuntu And like grEnAlEins said Open a terminal and type lspci

---

### Post by ireland4ever04 on 2008-08-25
ok so i did the erminal thing and the output was Command not found?

---

### Post by ireland4ever04 on 2008-08-25
alright I know that my network card is belkin?

---

### Post by niccholaspage on 2008-08-25
Hm..Boot into Windows On the LAPTOP and go into Device Manager and tell us the details for your wireless driver.

---

### Post by grEnAlEins on 2008-08-25
> **ireland4ever04 said:**
> ok so i did the erminal thing and the output was Command not found?

Heh, I did the same thing that I think you just did my first time running the command.  That first letter is not an upper-case "I" but a lower-case "L".

The phonetic spelling of the command is:
l-Lincoln, s-Sam, p-Paul, c-Charles, i-Ida
lspci

---

### Post by ireland4ever04 on 2008-08-25
i dont have a laptop lol and ok thank you Grenaleins! it worked but now its on my other comp soo i cant really get the code over here but what should i be looking for i see umm Vga controller,network controller,communication controller, USB controlled,PCI controller?

---

### Post by grEnAlEins on 2008-08-26
> **ireland4ever04 said:**
> i dont have a laptop lol and ok thank you Grenaleins! it worked but now its on my other comp soo i cant really get the code over here but what should i be looking for i see umm Vga controller,network controller,communication controller, USB controlled,PCI controller?

You should see something about a wireless card or something similar.  Post the output when you get a chance and we'll get you squared away.

Alternatively, you can go to "Start" > "Control Panel" > "System" > Under the "Tasks" pane on the left, click "Device Manager" > "Network Adapters"

Also, just for the record, I finally had a legitimate reason to boot from Vista!  This has only occurred a handful of times before...

---

### Post by nicedude on 2008-08-26
My god it is true that there is more than one way to skin a cat, if you don't believe me then try installing wifi in Linux :-)

You should start off with what wifi chipset you have and then go from there. Try telling everyone if it is a PCI wifi adapter or a USB wifi adapter or if neither then it would have to be a Motherboard based wifi so give your Mobo model # or if this is a premade machine then give the brand name and model etc so we can all find out what wifi you have. Without that knowledge no one can help you and I mean just that.

---

### Post by delanov on 2008-08-29
> **nicedude said:**
> My god it is true that there is more than one way to skin a cat, if you don't believe me then try installing wifi in Linux :-)

You should start off with what wifi chipset you have and then go from there. Try telling everyone if it is a PCI wifi adapter or a USB wifi adapter or if neither then it would have to be a Motherboard based wifi so give your Mobo model # or if this is a premade machine then give the brand name and model etc so we can all find out what wifi you have. Without that knowledge no one can help you and I mean just that.

This is great stuff, I'll remember it.

Thanks and regards.

---

