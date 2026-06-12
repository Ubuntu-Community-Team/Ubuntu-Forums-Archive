---
title: "invalid network driver"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by wbrokow1 on 2008-05-02
under "Wireless network drivers" I get an error:
Currently Installed Windows Drivers:
netwg511 : invalid driver

This is the windows driver that came with the card. It is a netgear wg511 v1.

The wireless card is not functioning under Ubuntu.

Thanks for any help.

---

### Post by wbrokow1 on 2008-05-04
anyone?

thanks

---

### Post by RequinB4 on 2008-05-04
It would help people more if they knew what your card is.

Run:
```

lspci

```

It sounds like ndiswrapper isn't liking you, or you have the wrong driver.

Edit: Sorry, you do say what card you have.  How did you install the driver origionally?

---

### Post by iAtari on 2008-05-04
What are you using to run the card driver? 

Have you tried using ndiswrapper?

---

### Post by wbrokow1 on 2008-05-05
I copied the .inf file for the card to an accessible directory
on the Ubuntu machine then loaded it using the "Window Wireless
Drivers" menu in "Administration" .

Whether I use the gui or commandline to load the driver with ndiswrapper I still get the invalid driver error.
 

I am not at the machine right now, it's at home.  So I will try 
all suggestions later on.

Thanks for all the responses.

---

### Post by wbrokow1 on 2008-06-17
I still can't this going.
anymore suggestions?
thanks

---

### Post by wbrokow1 on 2008-06-17
ok nevermind. got it working1
i just put 
p54pci in modules.

---

