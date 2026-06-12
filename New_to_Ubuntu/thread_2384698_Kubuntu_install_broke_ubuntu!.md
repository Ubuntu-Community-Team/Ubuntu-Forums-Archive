---
title: "Kubuntu install broke ubuntu?!"
date: 2018-02-10
forum: New to Ubuntu
---

### Post by hairymann on 2018-02-10
I installed ubuntu a few days ago from a flashdrive borrowed from a friend, and after install I wanted to switch to kubuntu because I find unity pretty ugly. So I opened up command line and typed the install command in. It seemed to work at first, but when it finished I got an error message saying something about a failed install. I restarted my pc to switch to it but when I selected kubuntu and started it, it never got past the loading screen. I restarted again and I got an error message. “The system is running in low-graphics mode” “Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself” when I select “Try running with default graphical mode, it takes me back to the first screen. When I select “reconfigure graphics, both the options take be back to the first screen also. There is a third troubleshoot button but none of the options are anything I can figure out the meaning of.

---

### Post by oldos2er on 2018-02-10
What command did you use to install Kubuntu? What was the error message? What are your hardware specs, particularly graphics hardware?

---

### Post by hairymann on 2018-02-10
The command was apt get install kubuntu. My specs are 16gb ddr4, nvidia 1070, and intel core i7 6700k. I didn&#8217;t take note of the error message at the time because I didn&#8217;t think it would amount to anything.

---

### Post by N3d on 2018-02-12
I had exactly this problem yesterday, and I'm afraid I didn't manage to fix KDE, but I did get back to a working Gnome3. I installed kubuntu-desktop with 

sudo apt-get install kubuntu-desktop

then logged out to switch to kde, but the display manager (I chose to stick with gdm3 - was that a crime?) wouldn't even come up. Rebooting just left it hung at a black screen. 

Eventually I rebooted and picked "with advanced options" from the grub menu, dropped into a root shell, and did

apt-get purge kubuntu-desktop

The next reboot got me back to gdm3 and gnome but at 800x600 screen res. I had to reboot a few times and magically after a few times my screen res came back and my stock gnome3 seems to be okay. The boot splash still says "kubuntu" though, but I can live with that.

---

### Post by mastablasta on 2018-02-12
> **hairymann said:**
> The command was apt get install kubuntu. My specs are 16gb ddr4, nvidia 1070, and intel core i7 6700k. I didn&#8217;t take note of the error message at the time because I didn&#8217;t think it would amount to anything.

errors are logged in logs.

you should probably purge nvidia drivers and then reinstall them. hopefully that will solve it.


otherwise you installed the whole Kubuntu. this is not a good idea. especially since KDE uses QT while gnome uses GTK libraries. you could end up with two network monitors for example.

if you just want to try it using live session USB or loading it in virtual box (or similar virtualisation program) is a better option (VM can also load just Live session). if you want to really use it then new install is better. particularly now that they both use different key programs (such as desktop manager and similar). i don't think Gnome pays attention to be max. compatible with KDE and vice versa. in theory they should be able to coexist but i am not sure how much testing is being done and both of these two platforms have quite fast developement lately with plenty new features introduced with each version.

---

### Post by vasa1 on 2018-02-12
> **hairymann said:**
> The command was apt get install kubuntu. My specs are 16gb ddr4, nvidia 1070, and intel core i7 6700k. I didn’t take note of the error message at the time because I didn’t think it would amount to anything.

```
apt get install kubuntu
```shouldn't have worked at all. In any case, developers of desktop environments probably don't take into account users mixing desktop environments. Just keeping a single desktop environment in good shape isn't trivial.

---

