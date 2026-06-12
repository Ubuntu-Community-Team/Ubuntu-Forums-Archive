---
title: "Writing a SPI driver in Ubuntu"
date: 2017-01-11
forum: Programming Talk
---

### Post by riverrock on 2017-01-11
Hi, 

  Does Ubuntu have a spi driver? How do I use it?

  I have an Intel Joule module which I have Ubuntu 16.04 running on and the spi pins are brought out via an expansion board.

[URL="http://www.intel.com/content/www/us/en/support/boards-and-kits/000022494.html"]http://www.intel.com/content/www/us/en/support/boards-and-kits/000022494.html
[/URL]
I want to communicate with a device connected to the SPI pins with C program in Ubuntu. Is this feasible?
 
Many thanks
Stev

---

### Post by floydg on 2017-01-19
Hi,

I am also very interested with Integrating the SPI interface using spidev. Currently lsmod does not indicate a spi device. "$mraa-gpio list" indicate two spi devices and the associated pin assignments.

Are these operational, and are there any documents?

---

