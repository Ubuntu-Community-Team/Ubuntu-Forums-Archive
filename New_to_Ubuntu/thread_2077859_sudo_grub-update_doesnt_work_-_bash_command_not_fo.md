---
title: "sudo grub-update doesnt work - bash command not found?"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by blueorange10 on 2012-10-29
hello!
i tried to configure the boot menu to set windows as default, as i saw in a forum, i renamed 30_os-prober to 09_os-prober in the grub.d folder.

nothing happend, then i tried sudo update-grub and got command not found

how is it possible? does anyone have an idea, what to do?

---

### Post by COMECON on 2012-10-29
You say **grub-update** on your title and **update-grub** on the post. Are you sure you wrote *sudo update-grub*? 
If you did and it still doesn't recognise the command, you could try this:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
I hope it works for you!

---

### Post by grahammechanical on 2012-10-29
You should also know that 30_os-prober is only a script. It examines the hard disk for other operating systems and then the information is written to the configuration file that produces the grub menu.

I doubt very much if renaming 30_os-prober will put Windows at the top of the menu. It will prevent update-grub from identifying any other operating systems.

Anyone who wants to edit the Grub menu should study this:

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

Look for section 5.1 - Simple configuration file handling

Note this:

> &#8216;GRUB_DEFAULT&#8217;
The default menu entry. This may be a number, in which case it identifies
the Nth entry in the generated menu counted from zero, or the title of a menu
entry, or the special string &#8216;saved&#8217;. Using the title may be useful if you want
to set a menu entry as the default even though there may be a variable number
of entries before it.

This is the file to mess with:

> The file &#8216;/etc/default/grub&#8217; controls the operation of grub-mkconfig.
Regards.

---

### Post by oldos2er on 2012-10-29
> **blueorange10 said:**
> hello!
i tried to configure the boot menu to set windows as default, as i saw in a forum, i renamed 30_os-prober to 09_os-prober in the grub.d folder.


Can you provide a link to the info you used? Which version of Ubuntu are you running?

---

### Post by oldfred on 2012-10-30
Grub will run all the scripts that are executable that start with 2 numbers & and underscore in number order. So renumbering os prober should work for a while. But what eventually happens is a major grub update and it writes a new 30_os-prober and you get double entries.

 I think it is just easier to copy the Windows  entry into a copy of 40_custom as 06_custom.

If you save the file you create with the custom entry to, say, 06_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries]("http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries")

and from Herman's site if your name it 06_custom to be near the top of grub.cfg:
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo chmod 755 /etc/grub.d/06_custom
Use a command something like this to change the file permissions to make your file executable.

Finally, don't forget to run either the 'sudo update-grub' or 'sudo grub-mkconfig' command.
sudo grub-mkconfig -o /boot/grub/grub.cfg

And if you know you do not need to run os-prober all the time, turn it off.

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

or a new file that will be first in the menu
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy entrie(s) to and edit if desired:
gksudo gedit /etc/grub.d/06_custom
Then do:
sudo update-grub

---

### Post by blueorange10 on 2012-10-30
I must apologize my fault. I thougt that ubuntu and linux is the same, but apparently it is not. Because of problems with my graphics card - nvidia gtx 560 i changed to fedora 17 - and there update-grub is not existing.

the command there that works is 
grub2-mkconfig -o /boot/grub2/grub.cfg                 as superuser

rename 30_os-prober to 09 os-prober works for the boot list - windows is now default. that should also work in ubuntu. i had serious problems with the startup-manger too - so this was necessary.

Thank you for your help and again i do apologize.

---

