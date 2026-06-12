---
title: "Is there a CUPS alternative?"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by d17ub on 2011-12-14
I want to print with a rusty Lexmark Z55 machine. I went through the convoluted process of downloading a generic driver last year and got it to work fine on maverick 10.10 before losing everything I had on the system. I don't want to do the whole process again and would really like to find out: is there an a way to get the printer to work with my 10.10 that does not involve CUPS? 

I know that:

**"CUPS** (formerly an [acronym]("http://en.wikipedia.org/wiki/Acronym") for **Common Unix Printing System**, ... is a modular [printing]("http://en.wikipedia.org/wiki/Computer_printer") system for [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") computer [operating systems]("http://en.wikipedia.org/wiki/Operating_systems") which allows a computer to act as a [print server]("http://en.wikipedia.org/wiki/Print_server")" (Wikipedia)

... But is it the only printing system for Unix-like OSs?

Any ideas or links appreciated.

Thanks :)

---

### Post by mastablasta on 2011-12-15
sometimes manufacturers provide their own Linux drivers. 
 
sometimes you can get drivers online that 3rd parties made , but you would need to pay for those (for example drivers for some cannon printers, forgot what is called).
 
Sometimes they have no support for linux.

---

### Post by Sigma1 on 2011-12-15
Looks a little involved, but here it is:

[http://www.unixmen.com/hardware-linux/339-howto-setup-lexmark-z55-printer-in-ubuntudebianmint](http://www.unixmen.com/hardware-linux/339-howto-setup-lexmark-z55-printer-in-ubuntudebianmint)

---

### Post by d17ub on 2011-12-16
Thanks for the replies. Lexmark withdrew their drivers for this machine a while ago. There was a third party driver that you could download for a while but not any more. 

Thanks for the link Sigma 1, looks like a good guide through the convoluted process of installing the driver, but I would need to be able to download the Z55 cups driver to use the guide. All of the links to it online go to 404s. I posted about this a few months ago and someone suggested the Z600 cups driver which is a generic one that is supposed to work on most machines. It didn't work with mine although I might have done something wrong. 

Assuming the Z600 drive will work but I want to try to use my printer without going though this whole CUPS process, what other options might be available to me? Links and ideas appreciated.

Thanks 
[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

---

### Post by HermanAB on 2011-12-16
The problem isn't with CUPS.  The problem is that there isn't a packaged driver for Ubuntu, so you got to convert a Red Hat packaged driver for installation on your Debian based system.  Whether you use CUPS or LPD won't make any diff.

---

### Post by d17ub on 2011-12-19
It makes more sense now why setting up a driver to work in Ubuntu is so complicated. Thanks for answer to my main question re whether there is an alternative to CUPS. I never heard of LPD before. I've looked at a few pages about it (e.g. [https://wiki.linuxfoundation.org/en/OpenPrinting/Database/LPDDocumentation#Printing_with_LPD.2C_LPRng.2C_or_GNUlpr](https://wiki.linuxfoundation.org/en/OpenPrinting/Database/LPDDocumentation#Printing_with_LPD.2C_LPRng.2C_or_GNUlpr)) and it looks like this might get even more complicated than CUPS maybe because its older. I am still interested in finding out how to prepare a driver for Ubuntu with LPD in case anyone knows of any guides.

---

