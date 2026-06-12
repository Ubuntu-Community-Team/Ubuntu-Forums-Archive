---
title: "enabling linux boot logo"
date: 2009-02-15
forum: Programming Talk
---

### Post by magon on 2009-02-15
Hi all,
I want to enable the linux penguin logo at boot to have the good old boot console with tux displayed on the upper left  corner. I have enabled all the kernel settings but the logo still does not appear :
- my boot line is as follows:
/boot/vmlinuz-2.6.27-11-custom root=UUID=223f95a8-2185-433e-a778-27c9b0d47bb6 ro vga=788 loglevel=7
 in the kernel configuration I have the following paramters set:
[*]boot logo:
      [*]   Standard 16-color 
      [*]   Standard 224-color Linux
[*] framebuffer console compiled in
[*] CONFIG_FB_VESA

Still the logo does not show up. I am compiling the kernel with the debian package system. 
I don't know if this the right forum to ask my question but i would appreciate if someone have some tips about this or point to another forum or documentation,
thank you all

---

### Post by magon on 2009-02-15
any answer to this?

---

### Post by Reiger on 2009-02-15
Very stupid question alert: does Ubuntu actually *have* that splash screen?

Otherwise you'll need to make a PNG and compile your own (which is where my 'knowledge' ends and which is obtained from reading something somewhere here). There was a thread about this not too long ago, and anyway this ought to be documented on the www. Google is your friend, I guess. ;)

---

### Post by magon on 2009-02-15
well actually there is no stupid questions but there is people stupid enough to not understand questions. Cos I am not talking about the splash screen that comes with ubuntu right out of the box but about the little penguin logo that appears in the upper left corner when you boot in text mode (to see the kernel boot messages). all I have found on google was this:
[URL="http://howtodoc.blogspot.com/2005/06/customizing-linux-boot-logo.html"]. (because I obviously searched on google before posting here !!)
thx!

---

### Post by Reiger on 2009-02-15
Yes, I understood that -- but that *too* is a kind of splash screen AFAIK. Just one which has the penguin on top, and a shell of shorts below.

Now, if Ubuntu does not have that particular penguin-style anymore (note that the boot images also contain something which tells linux to use what splash screen or otherwise incorporate the splash screen) you would need to grab/make your own somewhere/somehow. That's just my assumption based on my limited understanding: Ubuntu chucked out the penguin, to get it back you must compile your own splash.

---

### Post by magon on 2009-02-15
sorry you still don't get it !! this has nothing to do with ubuntu spalsh screen but with the kernel configuration: the [bootup logo] configuration option nothing to deal with ubuntu settings it exists even before ubuntu distro appeared just check the link I've put in the previous post to see what I am talking about
thanks anyway

---

### Post by evran on 2009-04-07
Yes, I have the same problem, pls someone help me. [Knoppix does it well, displaying tux while detect the hardware...]("http://upload.wikimedia.org/wikipedia/commons/9/9e/Knoppix-3.8-boot.png") How to do it on Ubuntu?

---

