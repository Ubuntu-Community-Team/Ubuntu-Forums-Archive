---
title: "Brother DCP 7010L - Floundering with the Scanner Bit"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Andavane on 2008-10-01
I have acquired a Brother Printer Scanner, and am floundering with getting the scanner bit to work, as it is not XSANE.

I have "cheated" with the printer bit - 1st I tried the Ubuntu Driver for my previous printer, the Brother HL 1430, and it printed fine on DCP 7010L.

I have been trying to follow the guide here:


[http://ubuntuforums.org/showthread.php?t=590793&highlight=libsane+rules]("http://ubuntuforums.org/showthread.php?t=590793&highlight=libsane+rules")

and have followed the "sudo apt-get install tcsh" bit.

Regarding the next steps, I am afraid I have got lost and am floundering.
Relatively new to Ubuntu, I doubt I'll ever get to really understanding it, but would like to have my printer-scanner running so I get on with my articles. ;)

I'd sure appreciate some help getting out of the maze!

Regards

John

---

### Post by Andavane on 2008-10-01
Additional Information:
I am in Gutsy: 7.10

---

### Post by Andavane on 2008-10-02
I have made a bit of progress: Been to the brother site and downloaded their
drivers: the printer bit is now working properly with the correct driver.
Before going there I had installed the cups wrapper for the model. 

Previous when I had gone to Applications/Graphics/XSane Image Scanner I had had the message: "No devices available even", even when the machine was switched on.

Now I am getting *some*thing, namely:

[B][COLOR="Navy"]Failed to open device 'brother2:bus2;dev1':
Error during device I/O[/COLOR][/B]

Looking this up I see various suggestions which I tried last night, but to no avail.

I am beginning to balk at the prospect of trying again.

Help would be much appreciated.

kind regards

John

---

### Post by Andavane on 2008-10-04
Latest weep:

I found out what to do, as in in the following:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9")

namely:

> # [For Ubuntu 7.10, 7.04, 6.10 and 6.06]

1. Open "/etc/udev/rules.d/45-libsane.rules"
2. Add the following 2 lines before 'LABEL="libsane_rules_end"':

Lines to be added----------------
#Brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

3. Restart the OS.


however when I try to do that I get the message:
"Could not save the file /etc/udev/rules.d/45-libsane.rules.
You do not have the necessary permissions"

I know I should know this, but things have gone blank.
Can someone tweak my memory?

I CAn use the scanner, but only by booting into Windows XP:frown:

Regards

John

---

### Post by Vitrinus on 2008-10-16
use the command

sudo nano /etc/udev/rules.d/40-basic-permissions.rules


edit and save with Ctrl o





Koen

---

### Post by Andavane on 2008-10-17
Thank you.
At what point should this command be used?

I see you are a "new user"...  1 cup, first post?

Could you clarify?

Regards

John

---

### Post by Vitrinus on 2008-10-18
Hello

It was indeed my first post, I apology for my lack of experience.


Oh I now see you use 7.10. Not sure how it works there, but with the command 'sudo nano' you can edit documents as a root. So when you don't have enough permissions to do so, this will help.

So I guess you must do:

sudo nano /etc/udev/rules.d/45-libsane.rules

edit the document with the 

#Brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

stuff and then press Ctrl o to save the document. 


I did it with my Brother DCP 135C on 8.04:

1. I use Synaptic to download the drivers -> search on DCP 135C and installed the cups and lpr drivers

2. Installed the drivers (.deb) from this page:
[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html#model](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html#model)

from this point Xsane worked for me only with 

sudo xsane

So it was clear it was a permission problem.

3. Then I edit the document (for you /etc/udev/rules.d/45-libsane.rules)  with sudo nano

4. Restarted OS

Hope this will solve it.


greetings



Koen

---

### Post by Andavane on 2008-10-19
Thanks very much, koen. This is now very clear.
As I need assistance with insertion of wires and switches, I'll need to arrange this; will do so and the  revert to this thread.
I trust it will solve the problem, it *sounds* right! ;)

Until then

Kind regards

John

---

### Post by MrMojoRisin on 2009-05-08
For anyone owning the Brother DCP-7010L and upgrading to Ubuntu 9.04 (Jaunty): I came from 8.10 where I modified a file in /etc/udev/rules.d/ to allow users to connect to the scanner.

After the upgrade to 9.04 I had issues again with accessing the scanner as a non-root user.

I solved it by adding a line to /lib/udev/rules.d/50-udev-default.rules  -  after modification the libusb section looked like this:

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

Restarted my system and now gscan2pdf and xsane can properly access my scanner again...

Regards,

Michiel

---

### Post by Andavane on 2009-05-08
Much appreciated,  Michiel.
It's this funny printer scanner which makes me stay where I am -cautious of upgrading. I'll  go on to Jaunty to another part of my PC, see what happens and report back.
(I keep different distros: install a new one first to see if everything works OK, and once it's working, move over there. A kind of retro-leap-frog I guess).

Regards

John

---

### Post by Andavane on 2010-08-07
Hi... although we got there in the end, the same headache arose every time the distro of Ubuntu changed.
I tried the method on this guy's blog:

[http://krp90.wordpress.com/2010/03/10/brother-dcp-7010-scanner-ubuntu-10-04/#comment-104]("http://krp90.wordpress.com/2010/03/10/brother-dcp-7010-scanner-ubuntu-10-04/#comment-104")

and it started scanning, straight away, like a charm.

I see no reason why this should work for future distros (and any scanner, remember to use lsusb to get the scanner model) checking of cpurse that the libsane rule file is still in the same place in future distros (they seem to move the files around a bit, sometimes giving different initial numbers to the file name.

---

