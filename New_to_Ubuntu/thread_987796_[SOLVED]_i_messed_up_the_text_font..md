---
title: "[SOLVED] i messed up the text font."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-19
hey, i did a 
> sudo dpkg -reconfigure -a

and i messed up the settings of my web browsers. The appearance of the fonts of the operating system is fine. 

but the web browsers of the text looks weird.
it looks italics but it has "stepping stairs in the outline of each text." like broken words and it is hurting my eyes.

can someone tell me the terminal bash command lines to get it fix to the default ubuntu settings for the fonts.

btw, please don't tell me to change the different font on firefox. i did that and it doesn't help. (implies towards the novice here on this board)

---

### Post by shiningkenmonster on 2008-11-20
i have a dell mini 9 customize edition from dell btw

---

### Post by nhasian on 2008-11-20
can you try:

```
sudo dpkg-reconfigure gnome-desktop-data gnome-control-center gnome-menus gnome-system-tools gnome-applets gnome-session
```

---

### Post by shiningkenmonster on 2008-11-20
> # You are using the editor-based debconf frontend to configure your system. See the end of this document for detailed
# instructions.
############################################################################################################################

# The 'cpufreq-selector' program, part of the CPU Frequency Scaling Monitor, can be set up to use superuser privileges when
# it is run ('SUID root').
#
# If you choose this option, any ordinary user will have the power to set the processor's clock frequency. However, this may
# also be potentially exploitable in security attacks.
#
# The applet will continue to work if you choose to disable SUID for cpufreq-selector, but only for monitoring the CPU clock
# frequency. The applet may need to be restarted for a change to take effect.
#
# If in doubt, accept the default of no SUID root. To change this setting later, run 'dpkg-reconfigure gnome-applets'.
#
# (Choices: yes, no)
# Should cpufreq-selector run with root privileges?
gnome-applets/cpufreq_SUID_bit="no"


############################################################################################################################
# The editor-based debconf frontend presents you with one or more text files to edit. This is one such text file. If you are
# familiar with standard unix configuration files, this file will look familiar to you -- it contains comments interspersed
# with configuration items. Edit the file, changing any items as necessary, and then save it and exit. At that point, debconf
# will read the edited file, and use the values you entered to configure the system.
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
Type  :quit<Enter>  to exit Vim


i got this, and i couldn't do anything afterwards. I tried to scroll down. nothing. the text on firefox is still the same. its hard to read

---

### Post by shiningkenmonster on 2008-11-21
this is still unsolved for me. does anyone know a solution to this?

i was thinking about uploading the whole dell mini 9 restore image, but i heard it isn,t an iso.

someone on this forum had trouble loading it with unetbootin.

so i am thinking of maybe sending it back to dell and have them reformat it and reinstall the custom dell version of ubuntu. but that would take a long time.

---

