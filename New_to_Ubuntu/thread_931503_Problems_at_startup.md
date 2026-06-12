---
title: "Problems at startup"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by malebolges on 2008-09-27
Hello, I am new with Ubuntu and I was doing pretty good until I started getting the next error almost each time I try to start Ubutu
ACPI: EC: apci_ec_wait timeout, status=0 expect_event=1
ACPI: EC: read timeout, command=128
Can someone tell me what I need to do to correct this error, as getting it almost every time I try to use Ubuntu is getting frustrating.

---

### Post by phidia on 2008-09-27
Look at the boot options [here]("https://help.ubuntu.com/community/BootOptions?highlight=%28acpi%29") and particularly sections 3 & 4.

ACPI is causing some problem on your system-I'm not sure why (there were no hits searching the 1st error you listed) You might have problem with the acpi=off boot option also but let cross our fingers and hope that fixes it.

---

### Post by malebolges on 2008-10-05
I added the acpi=off to the kernel and now I have issues with the usb mouse and the sound, I have been reading other posts and seems this is related, but as I am really new to this I am not sure, is there another option as updating the kernel to a new version that wont give me issues with the acpi?
If I only have to update the kernel how I do it and where you get the new versions of the kernel?

Thanks for any help you can provide

---

