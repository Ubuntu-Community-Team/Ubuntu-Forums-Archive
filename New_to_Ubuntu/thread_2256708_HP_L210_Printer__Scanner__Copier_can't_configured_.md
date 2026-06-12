---
title: "HP L210 Printer / Scanner / Copier can't configured in Ubuntu 11.10"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by urvi on 2014-12-14
Dear Sir,

I recently bought
EPSON L210 Series Printer cum Scanner cum Copier Machine.
but unfortunately,
my Ubuntu 11.10 cannot identify above Machine.
I tried a lot but failed to connect the above mentioned Machine to my OS Ubuntu 11.10.
Kindly guide me to enable all Services of -
EPSON L210 series Printer cum Scanner cum Copier Machine.

 With hope of kind support.

 Thanking you.


 Regards,
Urvi


Attachment : [http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#](http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#)

---

### Post by pqwoerituytrueiwoq on 2014-12-14
11.10 is eol please upgrade to 14.04

---

### Post by urvi on 2014-12-14
sir,
request to give some help for 11.10 ubuntu please.
i don't want to upgrade my old system to 14.04 ubuntu.
kindly help me.

thanking you.

---

### Post by howefield on 2014-12-14
I would generally agree with upgrading to a supported version of Ubuntu, however in any case, if the driver isn't being recognised out of the box you can download the linux driver deb package from the Epson website.

---

### Post by urvi on 2014-12-14
sir,
i downloaded driver from epson website.
and tried to install it through gdebi.
but it denied to install.[http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#](http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#)

---

### Post by howefield on 2014-12-14
There are times when brevity is a good thing, but when asking for support it often isn't.

What was the error ?

---

### Post by urvi on 2014-12-14
sir, 
i can't install drivers or configure my EPSON L210 PRINTER

---

### Post by urvi on 2014-12-14
request to solve the problem while configuring below mentioned product in ubuntu 11.10

[http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#](http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#)

---

### Post by DuckHook on 2014-12-14
urvi,

What @howefield is saying is that it is not possible to help you without a fuller dscription of your problem. You must tell us what precise steps you took to install in exact detail without leaving anything out, and precisely at which step the install failed. If you come on the forums and just yell "Help!" (which is essentially what you've done here), no one has enough info to help you.

I second @pqwoerituytrueiwoq's&#8213;wow, how do we parse this acronym (if acronym it is)?&#8213; suggestion and recommend updating to 14.04. If your HW is too ancient to run Ubuntu, I would highly recommend Lubuntu, which is now also LTS for 14.04. Since Lubuntu is super lightweight, it may work on your machine without any further tweaks. It may even already come with drivers for your model of printer and solve your problem right out of the box. 11.10 also leaves you wide open to severe security bugs that will never get fixed: Heartbleed and Shellshock come to mind. This is just an open invitation for disaster.

At any rate, my own contribution to a 11.10 solution will be very limited. I don't remember 11.10 anymore. But then, it's getting so I don't remember what I had last night for dinner.

---

### Post by urvi on 2014-12-14
dear sir,
i downloaded drivers packages from Epson website listed below :

[http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#](http://www.epson.co.in/epson_india/ink_tank_system_printers/product.page?product_name=Epson_L210#)

then downloaded below mentioned driver 

epson-inkjet-printer-201207w_1.0.0-1lsb3.2_i386.deb

then try to install it 
via 
software centre 
and 
via 
gdebi package installer

but both are not capable to install necessary drivers 
and fail to start my printer cum scanner cum copier 
namely EPSON L210

with hope of kind response from your side to resolve the problem 
while i already buy this PRINTER
and cannot configure it well.

thanks and regards,
urvi

---

### Post by Frogs Hair on 2014-12-14
> gdebi package installer

but both are not capable to install necessary drivers
and fail to start my printer cum scanner cum copier
namely EPSON L210

What is the error message displayed by gdebi and the software center?

---

### Post by ajgreeny on 2014-12-14
The .deb files you downloaded from Epson probably require dependency packages which will now be almost impossible to find as 11.10 is no longer supported, as many have already told you, and the repositories that it used when supported no longer exist at their old web address.

Sorry to say again what you don't want to hear, but **you really must update your distro version** in order to be able to get further support.

---

### Post by pdc on 2014-12-19
hi urvi;

if you are still out there; you need to know if your computer has a 32bit or 64bit system: and you need the debian package

so for a 32bit, you need [COLOR="#008000"]epson-inkjet-printer-201207w_1.0.0-1lsb3.2_i386.deb
[/COLOR]
and for 64bit, you need [COLOR="#008000"]epson-inkjet-printer-201207w_1.0.0-1lsb3.2_amd64.deb
[/COLOR]
both from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822)

I wonder if getting that issue sorted would help you

---

