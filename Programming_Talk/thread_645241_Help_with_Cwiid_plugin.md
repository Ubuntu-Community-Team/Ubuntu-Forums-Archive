---
title: "Help with Cwiid plugin"
date: 2007-12-19
forum: Programming Talk
---

### Post by fake_punk on 2007-12-19
Hello all.

I am a complete programing n00b.
I installed Cwiid 0.6.0 and it seems to work well, however i would like to install a plugin (led plugin) so i can add a switch in the config file.
Well, I found this, [http://abstrakraft.org/cwiid/ticket/43]("http://abstrakraft.org/cwiid/ticket/43") however i dont know how to implement it...

Someone please help.

---

### Post by nfox on 2008-01-29
So a month to the day later and I think I can help you:

Make sure you have these installed properly first:

> REQUIREMENTS:
awk, bison, flex, bluez-libs, gtk+-2 dev libs, python 2.4 or greater, uinput kernel support, kernel sources


Get the file, extract it to a folder, 'cd' into the folder and then do this in Konsole/Terminal/Children:

```
./configure
make
sudo make install
```

to install it. To use its goodness:


> EXECUTION
------------------------------------------------------------------------------------------------
wmgui [-h] [bdaddr]
wminput [-h] [-c config] [bdaddr]

The bluetooth device address (bdaddr) of the wiimote can be specified on the command-line, or through the WIIMOTE_BDADDR environment variable, in that order of precedence.  If neither is given, the first wiimote found by hci_inquiry will be used.
See wminput/README for more information on wminput configuration and execution.


However, I only need run 'sudo wminput &' which lets it use the default I've customized and run it in the background (the & lets you close the shell window and keep the program running). It automatically is connecting. 

[EDIT:] I forgot about this part, I'd recommend it. From the Community Docs:
> It is not wise to run wminput as superuser, so when you have finished testing change your udev rules to allow access to /dev/input/uinput. I'm going to assume you are a member of the admin group but you can always create a dedicated group for uinput users and use that instead.

sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"admin\"" > /etc/udev/rules.d/50-cwiid-input.rules'
/etc/init.d/udev restart




So, I have not used this at all-- I just read the readme. It seems like all it is doing is adding new variables to the program. You then define their actions with your config script. Let me know how you do the LED install.

---

