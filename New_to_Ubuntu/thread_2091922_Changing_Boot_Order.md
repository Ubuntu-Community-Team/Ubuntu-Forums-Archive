---
title: "Changing Boot Order"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Merisi on 2012-12-06
I feel so ashamed to ask how to do this for various reasons but how do you change it so that you boot into Windows by default rather than Ubuntu?

I have tried looking at solutions such as on this forum and elsewhere but I just can't seem to manage it.

---

### Post by dannyboy79 on 2012-12-06
which line is your windows boot entry within your grub menu? it start at 0, so say ubuntu is first, then the recovery line is 2nd, then windows is 3rd, that would make windows 2 within grub menu. so open /etc/default/grub and change the default boot number from 0 to 2, then issue sudo update-grub and then it shold make your 3 boot entry boot automatically.

---

### Post by sandyd on 2012-12-06
So, when you boot up your computer, you get a screen that shows you all the available boot options.

It will look something like

Ubuntu ....
Ubuntu ....
Ubuntu ....
Windows ....

In the above example, Windows is on line 4. Grub refers to the first line as 0, not 1. Find the line number that Windows is on in your machine

So,

Boot up into Ubuntu.

and press Alt+F2.

Type in
```

gksudo gedit /etc/default/grub
```

Type in the password when it asks.

Now, change GRUB_DEFAULT to the line number.

Save the file, press Alt+f2 again, and enter in gnome-terminal.

Run
```

sudo update-grub
```
and your next boot should start with windows.

Note that this will be offset when Ubuntu installs a new kernel, so I advise this method instead.

Press Alt + F2.

Type in 'gnome-terminal' (no quotes)
and enter the following (if it asks for a password, and you enter it, the input is invisible!)
```

sudo mv /etc/grub.d/10_linux /etc/grub.d/31_linux
sudo mv /etc/grub.d/20_memtest86+ /etc/grub.d/32_memtest86+
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/10_os-prober
sudo update-grub
```
that should move your windows entry to the first line, and Windows should boot by default ;)

---

### Post by raja.genupula on 2012-12-06
Grub customizer , a good solution for you .[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

---

### Post by Merisi on 2012-12-08
> **sandyd said:**
> So, when you boot up your computer, you get a screen that shows you all the available boot options.

It will look something like

Ubuntu ....
Ubuntu ....
Ubuntu ....
Windows ....

In the above example, Windows is on line 4. Grub refers to the first line as 0, not 1. Find the line number that Windows is on in your machine

So,

Boot up into Ubuntu.

and press Alt+F2.

Type in
```

gksudo gedit /etc/default/grub
```Type in the password when it asks.

Now, change GRUB_DEFAULT to the line number.

Save the file, press Alt+f2 again, and enter in gnome-terminal.

Run
```

sudo update-grub
```and your next boot should start with windows.

Note that this will be offset when Ubuntu installs a new kernel, so I advise this method instead.

Press Alt + F2.

Type in 'gnome-terminal' (no quotes)
and enter the following (if it asks for a password, and you enter it, the input is invisible!)
```

sudo mv /etc/grub.d/10_linux /etc/grub.d/31_linux
sudo mv /etc/grub.d/20_memtest86+ /etc/grub.d/32_memtest86+
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/10_os-prober
sudo update-grub
```that should move your windows entry to the first line, and Windows should boot by default ;)

I went for your first solution and got it working and I'm happy to change things around when the kernel changes again.  Thank you.

> **raja.genupula said:**
> Grub customizer , a good solution for you .[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

I did try this method first but couldn't get it working at all and not sure why.

---

### Post by dannyboy79 on 2012-12-10
use the thread tools and mark it solved. glad you got it sorted

---

