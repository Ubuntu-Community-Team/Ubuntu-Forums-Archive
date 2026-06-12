---
title: "Bluetooth Help ASAP PLEASE"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Absolute4Zero on 2008-09-07
Hi there 

I just bought a bluetooth device (Advent class 1 v2 + EDR) 

I a trying to send and receive files from my mobile phone (Motorola Razor V8)

the bluetooth device doesn't get recognized and nothing appears i tiried using kde and gnome one still nothing

can anyone help me please, i dont want to use wine to install additional software that came with this

---

### Post by Sycron on 2008-09-07
> **Absolute4Zero said:**
> Hi there 

I just bought a bluetooth device (Advent class 1 v2 + EDR) 

I a trying to send and receive files from my mobile phone (Motorola Razor V8)

the bluetooth device doesn't get recognized and nothing appears i tiried using kde and gnome one still nothing

can anyone help me please, i dont want to use wine to install additional software that came with this
 Shutdown your computer, plug-in the bluetooth device and turn on the computer. Boot Ubuntu , login. and you should see a bluettoth icon on the top panel.

If doesn't work go to System-Administrtion-Bluetooth-i-don't-know what...
 or System-Preferences-Bluetooth-i-don't-know what...

---

### Post by Absolute4Zero on 2008-09-07
When i rebooted my computer it told me that files are ready to transfer something similar but i still cant figure out how to send

when i tried searching from my mobile for devices it doesnt find anything

---

### Post by Sycron on 2008-09-07
Make sure your phone is visible. You may scan for bluetooth deices with```
sudo hcitool scan
```

---

### Post by Absolute4Zero on 2008-09-07
What do u mean visible, i have the power on ?

---

### Post by Absolute4Zero on 2008-09-07
What do i do next

---

### Post by nothingspecial on 2008-09-07
If you want to transfer from a mobile phone etc to your computer try gnome-bluetooth, it`s in synaptic. I couldn`t find anything that worked until I tried this.
 It will appear in your menus under accessories as Bluetooth file sharing. Try to scan for devices again and it should see your computer.

Hopes this helps.

---

### Post by Absolute4Zero on 2008-09-07
It doesnt work, it just simply doesnt detect anythin

---

### Post by Cresho on 2008-09-07
Here is how I bonded my device.

1.  open up your motorola razr and go into the "connection settings".  click on bluetooth and tell it to 'find me"

2. There is an icon on the upper right on a default panel of gnome that looks like a bluetooth.  right click on it and click on "browse for device".

3. highlight your phone.  click on connect and wait a few seconds.  your phone will ask for key pass.  make one up and ok on the phone.  your pc will come up with a pop up and ask for a passphrase.  clickn on enter key and enter one and okay it.

YOUR DONE!

read my part 2 on how to send recieve files.  its so easy its stupid!!

---

### Post by Cresho on 2008-09-07
now that your phone is paired, you want to send a file.  all you do is right click on the pc bluetooth icon and "send file".highlight phone and click connect.  a nautilus browser will pop up and you can send a file.  NOTICE IT SENDS SEND A FILE!  this is important because at the moment, obex is not fully implemented.  you can only send one file at a time!  but you can grab full directories and download them in bulk easily!

now that you are done with what ever you are doing, to turn of the pairing, on the desktop you will notice a phone icon.  right click and select "unmount"  now your phone and pc have stopped the connections

---

### Post by Absolute4Zero on 2008-09-07
Its not working for me i guess i am going to have to install wine and use windows software to get this working, my phone bluetooth is on, the stick that i bought is in the computer, and nothing recognizes when i search for devices cant find my computer, and when i go browse device nothing appears there

---

### Post by Sycron on 2008-09-07
> **Absolute4Zero said:**
> Its not working for me i guess i am going to have to install wine and use windows software to get this working, my phone bluetooth is on, the stick that i bought is in the computer, and nothing recognizes when i search for devices cant find my computer, and when i go browse device nothing appears there

No! It will not work under wine.  And everything is fine at your computer. It doesn't work just because you missed something ;) .

---

### Post by Cresho on 2008-09-07
[B]You did not click on "browse for device!"

you did not follow directions!  If gnome sees your bluetooth, it works![/B]

---

### Post by Sycron on 2008-09-07
> **Cresho said:**
> [B]You did not click on "browse for device!"

you did not follow directions!  If gnome sees your bluetooth, it works![/B]

Yes, it sure WORKS. I don't get it, if something don't work then why people migrate to windoze   ?

---

### Post by nothingspecial on 2008-09-07
> **Absolute4Zero said:**
> It doesnt work, it just simply doesnt detect anythin

From the phone

---

### Post by Cresho on 2008-09-08
from the phone, select image, then click on options, then send, then via bluetooth.

new menu pops up and asks you which device or "look for devices"

at this point, it will not see ubuntu bluetooth pc because you need to do this stip.  Right click and select preferences and then select under mode of operation, "visible and connectable for other devices. in General, select "recieve files from remote devices" and "automatically authorize incoming requests"

---

### Post by Sycron on 2008-09-09
> **Cresho said:**
> from the phone, select image, then click on options, then send, then via bluetooth.

new menu pops up and asks you which device or "look for devices"

at this point, it will not see ubuntu bluetooth pc because you need to do this stip.  Right click and select preferences and then select under mode of operation, "visible and connectable for other devices. in General, select "recieve files from remote devices" and "automatically authorize incoming requests"

Do what Cresho told you and it will work ;) .

---

