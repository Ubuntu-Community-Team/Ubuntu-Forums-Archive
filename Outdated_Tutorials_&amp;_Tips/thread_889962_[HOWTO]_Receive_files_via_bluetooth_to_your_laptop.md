---
title: "[HOWTO] Receive files via bluetooth to your laptop/desktop (Ubuntu Hardy)"
date: 2008-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by sayakb on 2008-08-14
[SIZE=5][COLOR=Sienna]Receive files via bluetooth to your laptop/desktop (Ubuntu Hardy)[/COLOR][/SIZE][B]


1. [/B]Switch on bluetooth on both: the laptop/desktop and the mobile device.

**2. **The bluetooth icon should appear in the notification area:
[ATTACH]81579[/ATTACH]

**3. **Right click on the bluetooth icon, and select [B]Browse Device...

4. [/B]A list of available bluetooth devices in range should appear. Find your phone/mobile device in the list. If you can't find it there, make sure you have public discovery enabled for your mobile device.

**5.** Click on your phone's name in the list and click the **Connect** button. Sometimes, you might not see the name but a OBEX path value like *00:16:b8:b6:bd:ae. *This should be your mobile device (This happens since Ubuntu cannot resolve the names of some devices for the first time you connect to it)

**6.** You may be prompted for entering the passkey. Enter a common passkey on both devices.

**7.** You may be then prompted by the mobile device whether to *Accept bluetooth connections from your laptop or not.* Select **Yes** to procees.

**8. **On selecting Yes, the phone would open up like a folder/location in your ubuntu machine. You may browse different folders and copy contents from the mobile device to the laptop. Though, in some cases, you may not be able to write to the phone (Use Sent to -> Mobile device in such cases)

---

### Post by bhavi on 2008-08-20
What about hidd and bluez utils?

---

### Post by sayakb on 2008-08-20
I don't think you need to downgrade bluez-utils as some people advise..

---

### Post by clegends on 2008-08-22
Hi, not having much luck with this. I'm able to follow everything through to 'connect' after choosing my device (nokia phone). Then on the phone I'm prompted for the passcode, which in /etc/bluetooth/hcid.conf is set to "1234". Security is: security none.

So I enter 1234 in my phone, and after a few seconds get a message back on Ubuntu saying 'no message answer received'. What do I need to do?

edit: more accurate error message:

Couldn't display "obex://[00:17:E5:77:BA:1C]/".
Error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

---

### Post by sayakb on 2008-08-22
After you enter the passcode on your phone, you should be asked to enter passcode on the computer. Just click on the bluetooth icon in the notification area if it doesn't and a tooltip should appear which will have a button for "Enter Passcode".

Alternatively: 
Switch ON bluetooth on both ends. Now on your nokia device, goto Bluetooth->Paired Deviced(Trusted Devices). Now goto Options->New Paired Device and find your laptop. You will be prompted for passcode. Enter it on your phone and on the computer.

---

