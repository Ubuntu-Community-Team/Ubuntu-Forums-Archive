---
title: "list drivers"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-05
is there a command to list all drivers?  I'm looking to download the drivers to my computer just in case

[http://support.gateway.com/support/drivers/search.asp?st=pn&param=104572](http://support.gateway.com/support/drivers/search.asp?st=pn&param=104572)

---

### Post by Elfy on 2008-07-06
Not sure about the first - but it will be pointless downloading windows drivers for ubuntu as they won't work. If you have specific issues then ask about them. :)

---

### Post by aktiwers on 2008-07-06
What hardware do you need drivers for?

---

### Post by sdennie on 2008-07-06
Your question may not mean what you think it means in Ubuntu.  If you want to see all the "drivers" you can use:

```

lsmod

```

That's going to be a lot of information that may not be useful to you.  Another way to look at what Ubuntu thinks about your hardware is:

```

lshw -html > hardware.html

```

And then open "hardware.html" in a web browser.  

Except for a few cases, the idea of "drivers" is not really relevant for the average Ubuntu user.  Out of the box, Ubuntu supports most hardware devices and the only reason you'd need to install something special is usually to fix video or wifi problems (wifi being the more common).

---

