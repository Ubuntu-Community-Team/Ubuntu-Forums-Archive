---
title: "my shortcuts are not working"
date: 2019-08-26
forum: New to Ubuntu
---

### Post by nantia on 2019-08-26
Hello,

i changed the shortcut for opening the calculator application, from the settings menu, the shortcut is now **ctrl+shift+c**. But this doesnt seem to work. 
The same thing happens for a custom shortcut i created for rebooting my laptop (** ctrl+alt+r**), it doesnt work..

I have restarted my laptop in case that was the problem, but still nothing happens when i press these key combinations.
Please help, what am i doing wrong ?

Thank you

using Ubuntu 18.04.3 LTS

---

### Post by TheFu on 2019-08-26
I think these are called "keyboard accelerators".   How these keyboard accels are configured depends on the version of the OS and the specific DE you are running, so providing that information at the minimum will get better responses than mine. I know next to nothing about GUI stuff, except to suggest using the **Ubuntu Desktop Guide** for the specific release to see those instructions.

I initially came to this thread to help with symbolic links, which are called "shortcuts" on Windows. 
[https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by PaulW2U on 2019-08-26
Hi nantia, I've tested these on my Ubuntu 18.04 installation which from the screenshot I think you are also using and have found that Control-Shift-C does call up the calculator but which version of gnome-calculator do you have installed? Ubuntu 18.04 installs the snap version by default. My keyboard shortcut launches the deb version. May be if you install the deb version then your keyboard shortcut will work?
```
sudo apt install gnome-calculator
```
As far as I can see commands that run in a terminal, for example your **reboot** command, won't work without using something like the following in the Command box of the Add Custom Shortcut dialog:
```
gnome-terminal -e 'bash -c "sudo -H mc"'
```
Midnight Commander started for me in a terminal window after prompting me for my password. I didn't test the reboot command though. Hope that helps.

---

### Post by TheFu on 2019-08-26
sudo isn't needed for a calculator.  If it is, I'd wipe the OS and start over.

---

### Post by nantia on 2019-08-26
[**[COLOR=#DD4814][B]PaulW2U**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1078994") Hello!!
I am using the calculator that is installed by default in Ubuntu 18.04.3..
**I just installed the one you told me and the shortcut worked ****on the spot!!!**
&#932;hank you very much for this....

The command for the rebooting you gave me just open the terminal, promts me to insert password, and then does nothing.
I will search other ways..

---

### Post by nantia on 2019-08-26
m

---

### Post by PaulW2U on 2019-08-26
> **nantia said:**
> Hello!!
I am using the calculator that is installed by default in Ubuntu 18.04.3..
**I just installed the one you told me and the shortcut worked ****on the spot!!!**
&#932;hank you very much for this....
Excellent, glad to have helped.

---

### Post by TheFu on 2019-08-26
The command above with sudo in it is for a TUI file manager.  It if isn't installed, it won't work.

If you want to reboot from a terminal, use **sudo reboot**
If you want to shutdown from a terminal, use **sudo shutdown now**

---

### Post by nantia on 2019-08-26
Update: 

I typed in terminal:
sudo chmod u+s /sbin/shutdown

then assigned the command : **"shutdown -r now ** ,to my shortcut for rebooting and now this works also :)

all the problems solved

---

### Post by PaulW2U on 2019-08-26
> **nantia said:**
> The command for the rebooting you gave me just open the terminal, promts me to insert password, and then does nothing.
I've now tested your reboot requirement.

So, entering
```
gnome-terminal -e 'bash -c "sudo reboot"'
```
in the Command box **immediately** reboots the PC with the required keyboard shortcut after entering your password.

I didn't want to test the reboot command earlier as i was on a PC that I didn't want to actually reboot so I used another command as an example. Sorry for any confusion.

---

