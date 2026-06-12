---
title: "Sending files from Ubuntu 12.04 to Windows Vista via bluetooth"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-12-15
Hey guys. 

I'm trying to send a huge file from my Ubuntu 12.04 netbook to a Windows Vista laptop via bluetooth. 
The file in question is a 4.5gb .iso and I don't have a pendrive or any other external gadget big enough to fit it in. Neither do I have a CD drive on my netbook. I did think about just re-downloading it, but that would take forever - that would be my last option if I can't pull this off. 

So, I thought about sending it through bluetooth. 
Both bluetooth devices are working and recognize each other, but when the file sending pop-up window appears, after choosing the Bluetooth (OBEX Push) option - underneath where it reads "send to" I cannot click on the drop down bar to choose a device? (See attached image)
Is there any reason for this? Maybe the file is too big? ...

Thank you kindly.

K.m

---

### Post by kabukiM0n0 on 2012-12-15
I managed to get the connection established. 
but now I get this answer, when trying to send the file.

---

### Post by techvish81 on 2012-12-15
you will have to enable 'personal file sharing'.   type 'share in dash and go to personal file sharing, enable bluetooth share options as required.

---

### Post by Cheesemill on 2012-12-15
If you do get the transfer to work you should be aware that the ***maximum*** practical transfer rate of bluetooth is around 2Mb/s. This means it will take at least 5 hours to transfer a 4.5GB file. Also these are bluetooth 2 speeds, if your devices are only bluetooth 1 then it will take at least 3 times longer.

Also I don't think bluetooth supports resuming either so if anything happens during the transfer you'll have to start the whole thing again.


If both machines have wireless networking then this would be a far superior method to send your file.

---

### Post by techvish81 on 2012-12-15
a cable network is also a good choice,  it would be difficult but fruitful.

---

### Post by Impavidus on 2012-12-15
You could also split the .iso in multiple parts, transfer by memory stick and merge them on the windows machine. I believe several archive formats support multi-part archives, although I don't know the specifics. Google should know.

---

