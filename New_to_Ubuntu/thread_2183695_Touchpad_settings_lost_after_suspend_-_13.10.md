---
title: "Touchpad settings lost after suspend - 13.10"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by sgtstabbin on 2013-10-25
After recently updating to 13.10 from 10.10, I noticed that multitouch settings seemed to be quite different in Saucy. The three finger tap seems to be gone and the two finger tap defaults to right click. Three finger tap isn't important, but having two finger tap function as a middle click is a must for me. 

I installed Synaptiks and gained this functionality with no issue at all. The settings persist through restarts and shut downs, however they do not persist through a suspend and resume. I've tried countless solutions I've found online, but none of them seem to work with 13.10. Everything from attempting to run a synclient TapButton2=2 type script at startup to adding the desired TapButton info in the 50-synaptics conf file. I haven't had any luck with all my searching, so I'm coming to you forum users for help.

I'm running an Asus U43Jc if that makes any difference. 

Thanks!

---

### Post by Toz on 2013-10-26
Hello and welcome to the forums.

Are you able to reset the settings after resume via Synaptiks? Or do you have to restart to get them back?

Maybe you can try unloading and reloading the psmouse module during the suspend cycle. Here is how:
1. With root privlidges, create the file /etc/pm/config.d/modules:
```
sudo -i gedit /etc/pm/config.d/modules
```
...enter your password when prompted.

2. Copy/paste the following content:
```
SUSPEND_MODULES="psmouse"
```

3. Save the file.

4. Make the file executable:
```
sudo chmod +x /etc/pm/config.d/modules
```

5. Try a suspend/resume cycle.

---

### Post by sgtstabbin on 2013-10-26
I am able to reset the settings after resume via either Synaptiks or the synclient TapButton 2=2 command. A restart is not necessary to get the settings back, but it does work.

I followed your steps to unload and reload the psmouse module. I still lost those settings after a suspend and resume.

---

### Post by Toz on 2013-10-26
Okay, then lets try this.

First, delete the modules file that we created.

Then:
1. Create a new suspend hook:
```
sudo -i gedit /etc/pm/sleep.d/0000trackpad
```

2. Copy/paste the following content:
```
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su USER -c '/usr/bin/synclient TapButton 2=2' ;;
esac
```
...and replace the word "USER" with your actual system username.

3. Save the file.

4. Make the file executable:
```
sudo chmod +x /etc/pm/sleep.d/0000trackpad
```

5. Try suspending again.

---

### Post by sgtstabbin on 2013-10-26
Same result. 

Do you know where it loads the settings from on resume? It's obviously different that what it loads on start up. This whole thing just has me really confused. Especially given all the info I've read for past versions where touchpad settings were as simple as editing the .conf file and adding the options in. I'm not 100% confident 13.10 is using those synaptics .conf files at all. I first tried to set this option up by editing that file, but it had no effect. The settings didn't change until using terminal command or Synaptiks.

---

### Post by Toz on 2013-10-26
The suspend process doesn't really "reload" any settings. It basically puts devices to sleep and then re-awakens them. In your case, something is hanging up during the resume process. The two methods that we've tried generally work to get the trackpad to re-awaken properly. In fact, the second one resets the settings.

Can you post back the contents of the /etc/pm/sleep.d/0000trackpad file so that I can verify it? And also, can you post back your suspend log via:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated? Maybe there is something in there that will help identify the problem.

---

### Post by sgtstabbin on 2013-10-26
Contents of 0000trackpad:
```
#!/bin/shcase "$1" in
    resume)
        DISPLAY=:0.0 su rhett -c '/usr/bin/synclient TapButton 2=2' ;;
esac
```

Suspend log link: [http://paste.ubuntu.com/6307269/](http://paste.ubuntu.com/6307269/)

---

### Post by Toz on 2013-10-26
oops. Typo. Try this version of the script:
```
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su rhett -c '/usr/bin/synclient TapButton2=2' ;;
esac
```
...(no space between "TapButton" and "2") + "case" should be on a line of its own.

After trying again, post back again the pastebin link to /var/log/pm-suspend.log.

---

### Post by sgtstabbin on 2013-10-26
Good news and bad news. 

The correction in 0000trackpad seems to have worked! I now have two finger middle click upon resume. However, I now have a wi-fi problem on resume. When I resume, networking is disabled and enabling it does not do anything. I have to restart to get wireless back. Even after a restart it is disabled by default, but enabling it does work. I don't know if this is related to what we've done at all, but it certainly seems like it could be. I've had immediate and automatic connection to wireless upon booting and resuming since installing 13.10.

Link: [http://paste.ubuntu.com/6307622/](http://paste.ubuntu.com/6307622/)

---

### Post by sgtstabbin on 2013-10-26
A quick test shows that these two things are most likely related. I commented out the 0000trackpad file and did a suspend-resume cycle. Upon resume, wireless connected without issue. I then "uncommented" 0000trackpad and tried again. The wireless problem was back.

---

### Post by Toz on 2013-10-26
> **sgtstabbin said:**
> A quick test shows that these two things are most likely related. I commented out the 0000trackpad file and did a suspend-resume cycle. Upon resume, wireless connected without issue. I then "uncommented" 0000trackpad and tried again. The wireless problem was back.
At least we're getting closer, even though I don't understand how the two are connected. Anyways, maybe we can try something similar with the wireless driver and get them both to work after resume. But first, what module is your wireless using?
```
lspci -k | grep -iA2 network
```

This should show which kernel driver is in use for your wireless connection. Then lets re-do the first set of steps we did earlier, but this time for the wireless driver:
1. With root privlidges, create the file /etc/pm/config.d/modules:
```

sudo -i gedit /etc/pm/config.d/modules
```
...enter your password when prompted.

2. Copy/paste the following content:
```

SUSPEND_MODULES="WIRELESS_DRIVER"
```
...and replace **WIRELESS_DRIVER** with the actual module that is being used

3. Save the file.

4. Make the file executable:
```

sudo chmod +x /etc/pm/config.d/modules
```

5. Try a suspend/resume cycle.

If it doesn't work, please post back your /var/log/pm-suspend.log and the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by sgtstabbin on 2013-10-26
That didn't do it.

Wireless driver is "iwlwifi". Contents of modules file:
```
SUSPEND_MODULES="iwlwifi"
```

Suspend log: [http://paste.ubuntu.com/6308374/](http://paste.ubuntu.com/6308374/)

syslog: 
```
Oct 26 12:35:21 rhett-U43Jc kernel: [  362.776642] PM: Saving platform NVS memoryOct 26 12:35:21 rhett-U43Jc kernel: [  363.089505] PM: Restoring platform NVS memory
Oct 26 12:35:21 rhett-U43Jc kernel: [  363.690214] PM: noirq resume of devices complete after 159.517 msecs
Oct 26 12:35:21 rhett-U43Jc kernel: [  363.690371] PM: early resume of devices complete after 0.114 msecs
Oct 26 12:35:21 rhett-U43Jc kernel: [  366.577230] PM: resume of devices complete after 2884.715 msecs
Oct 26 12:35:21 rhett-U43Jc kernel: [  366.577516] PM: Finishing wakeup.
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216139] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216145] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216147] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216148] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216149] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216150] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.216151] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 26 12:36:33 rhett-U43Jc kernel: [    0.859806] PM: Hibernation image not present or could not be loaded.
Oct 26 12:37:31 rhett-U43Jc kernel: [   73.367628] PM: Syncing filesystems ... done.
Oct 26 12:37:31 rhett-U43Jc kernel: [   73.540765] PM: Preparing system for mem sleep
Oct 26 12:37:44 rhett-U43Jc kernel: [   73.843791] PM: Entering mem sleep
Oct 26 12:37:44 rhett-U43Jc kernel: [   75.263527] PM: suspend of devices complete after 1387.946 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   75.263755] PM: late suspend of devices complete after 0.225 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   75.359305] PM: noirq suspend of devices complete after 95.477 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   75.383813] PM: Saving platform NVS memory
Oct 26 12:37:44 rhett-U43Jc kernel: [   75.696653] PM: Restoring platform NVS memory
Oct 26 12:37:44 rhett-U43Jc kernel: [   76.297373] PM: noirq resume of devices complete after 159.513 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   76.297528] PM: early resume of devices complete after 0.113 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   79.187569] PM: resume of devices complete after 2887.896 msecs
Oct 26 12:37:44 rhett-U43Jc kernel: [   79.187833] PM: Finishing wakeup.
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216239] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216246] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216247] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216248] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216249] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216250] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.216252] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 26 12:38:52 rhett-U43Jc kernel: [    0.859933] PM: Hibernation image not present or could not be loaded.
Oct 26 12:50:25 rhett-U43Jc kernel: [  706.068802] PM: Syncing filesystems ... done.
Oct 26 12:50:25 rhett-U43Jc kernel: [  706.176952] PM: Preparing system for mem sleep
Oct 26 12:50:35 rhett-U43Jc kernel: [  706.450347] PM: Entering mem sleep
Oct 26 12:50:35 rhett-U43Jc kernel: [  708.000574] PM: suspend of devices complete after 1503.882 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  708.000774] PM: late suspend of devices complete after 0.194 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  708.096428] PM: noirq suspend of devices complete after 95.581 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  708.120933] PM: Saving platform NVS memory
Oct 26 12:50:35 rhett-U43Jc kernel: [  708.433778] PM: Restoring platform NVS memory
Oct 26 12:50:35 rhett-U43Jc kernel: [  709.034510] PM: noirq resume of devices complete after 159.525 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  709.034671] PM: early resume of devices complete after 0.118 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  711.913443] PM: resume of devices complete after 2876.635 msecs
Oct 26 12:50:35 rhett-U43Jc kernel: [  711.913761] PM: Finishing wakeup.
Oct 26 12:52:00 rhett-U43Jc kernel: [  796.624875] PM: Syncing filesystems ... done.
Oct 26 12:52:00 rhett-U43Jc kernel: [  796.770058] PM: Preparing system for mem sleep
Oct 26 12:52:18 rhett-U43Jc kernel: [  796.880472] PM: Entering mem sleep
Oct 26 12:52:18 rhett-U43Jc kernel: [  798.262324] PM: suspend of devices complete after 1379.929 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  798.262537] PM: late suspend of devices complete after 0.210 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  798.358272] PM: noirq suspend of devices complete after 95.613 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  798.382804] PM: Saving platform NVS memory
Oct 26 12:52:18 rhett-U43Jc kernel: [  798.695728] PM: Restoring platform NVS memory
Oct 26 12:52:18 rhett-U43Jc kernel: [  799.296774] PM: noirq resume of devices complete after 159.547 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  799.296930] PM: early resume of devices complete after 0.114 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  802.204781] PM: resume of devices complete after 2904.238 msecs
Oct 26 12:52:18 rhett-U43Jc kernel: [  802.205070] PM: Finishing wakeup.
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216633] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216640] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216641] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216642] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216643] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216644] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.216646] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 26 12:53:16 rhett-U43Jc kernel: [    0.860655] PM: Hibernation image not present or could not be loaded.
Oct 26 13:57:07 rhett-U43Jc kernel: [ 3847.630767] PM: Syncing filesystems ... done.
Oct 26 13:57:07 rhett-U43Jc kernel: [ 3847.889895] PM: Preparing system for mem sleep
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3848.172784] PM: Entering mem sleep
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3849.614042] PM: suspend of devices complete after 1391.816 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3849.614277] PM: late suspend of devices complete after 0.231 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3849.710026] PM: noirq suspend of devices complete after 95.676 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3849.734525] PM: Saving platform NVS memory
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3850.047367] PM: Restoring platform NVS memory
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3850.648110] PM: noirq resume of devices complete after 159.522 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3850.648266] PM: early resume of devices complete after 0.113 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3853.467179] PM: resume of devices complete after 2816.820 msecs
Oct 26 14:02:19 rhett-U43Jc kernel: [ 3853.467494] PM: Finishing wakeup.
Oct 26 14:16:27 rhett-U43Jc kernel: [ 4701.579075] PM: Syncing filesystems ... done.
Oct 26 14:16:27 rhett-U43Jc kernel: [ 4701.684078] PM: Preparing system for mem sleep
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4701.977865] PM: Entering mem sleep
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4703.452441] PM: suspend of devices complete after 1427.959 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4703.452648] PM: late suspend of devices complete after 0.204 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4703.548274] PM: noirq suspend of devices complete after 95.552 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4703.576789] PM: Saving platform NVS memory
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4703.889644] PM: Restoring platform NVS memory
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4704.490309] PM: noirq resume of devices complete after 159.513 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4704.490465] PM: early resume of devices complete after 0.114 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4707.305276] PM: resume of devices complete after 2812.721 msecs
Oct 26 14:58:58 rhett-U43Jc kernel: [ 4707.305540] PM: Finishing wakeup.
Oct 26 15:04:59 rhett-U43Jc kernel: [ 5068.423176] PM: Syncing filesystems ... done.
Oct 26 15:04:59 rhett-U43Jc kernel: [ 5068.567047] PM: Preparing system for mem sleep
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5068.855916] PM: Entering mem sleep
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5070.397567] PM: suspend of devices complete after 1495.873 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5070.397791] PM: late suspend of devices complete after 0.221 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5070.477478] PM: noirq suspend of devices complete after 79.624 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5070.501947] PM: Saving platform NVS memory
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5070.814779] PM: Restoring platform NVS memory
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5071.399483] PM: noirq resume of devices complete after 143.241 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5071.399640] PM: early resume of devices complete after 0.115 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5074.232744] PM: resume of devices complete after 2831.000 msecs
Oct 26 15:05:17 rhett-U43Jc kernel: [ 5074.233004] PM: Finishing wakeup.
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216035] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216042] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216043] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216044] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216045] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216046] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.216048] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 26 15:08:15 rhett-U43Jc kernel: [    0.863651] PM: Hibernation image not present or could not be loaded.
```

---

### Post by Toz on 2013-10-26
Try with this list of modules:
```
SUSPEND_MODULES="iwldvm iwlwifi"
```

From your suspend log, I also see:
> Running hook /usr/lib/pm-utils/sleep.d/49tlp resume suspend:
Error: TLP power save is disabled because laptop-mode-tools is installed.
       Please uninstall laptop-mode-tools.

Not sure why both are installed, but maybe you could try uninstalling them both. TLP can be problemmatic and most of the functions of laptop-mode-tools are now built in.

---

### Post by sgtstabbin on 2013-10-26
TLP and laptop-mode-tools have been uninstalled. I made the change to the modules file, but the wireless problem is still there.

---

### Post by Toz on 2013-10-26
Try it manually.

```
sudo rmmod iwldvm 
sudo rmmod iwlwifi
sudo pm-suspend
```
...and on resume:
```
sudo modprobe iwlwifi
sudo modprobe iwldvm
```

Post back any error messages that might show up entering those commands. And check the touchpad and wireless.

---

### Post by sgtstabbin on 2013-10-26
No error messages and everything works after doing that.

---

### Post by Toz on 2013-10-26
Okay. Once again, delete the /etc/pm/config.d/modules file (which doesn't seem to be working). Then edit the /etc/pm/sleep.d/0000trackpad file to look like this:
```
#!/bin/sh
case "$1" in
    suspend)
        rmmod iwldvm
        rmmod iwlwifi
        ;;
    resume)
        modprobe iwlwifi
        modprobe iwldvm
        DISPLAY=:0.0 su rhett -c '/usr/bin/synclient TapButton2=2' 
        ;;
esac
exit 0

```

Hopefully this is the magic combination.

---

### Post by sgtstabbin on 2013-10-26
It seems like that should do the trick, but networking is still disabled and won't enable on resume.

EDIT: I commented out the trackpad line and it worked just fine (other than the two finger middle click). There's something the system doesn't like about that synclient TapButton2=2 command on resume.

---

### Post by Toz on 2013-10-26
Can you post /var/log/pm-suspend.log?

---

### Post by sgtstabbin on 2013-10-26
Here you go: [http://paste.ubuntu.com/6309935/](http://paste.ubuntu.com/6309935/)

---

### Post by Toz on 2013-10-26
> **sgtstabbin said:**
> Here you go: [http://paste.ubuntu.com/6309935/](http://paste.ubuntu.com/6309935/)
From the log file:
> Running hook /etc/pm/sleep.d/0000trackpad resume suspend:
Failed to connect to X Server.
/etc/pm/sleep.d/0000trackpad resume suspend: success.
Funny how sometimes it works and other times it doesn't.

> **sgtstabbin said:**
> EDIT: I commented out the trackpad line and it worked just fine (other than the two finger middle click). There's something the system doesn't like about that synclient TapButton2=2 command on resume.
Can you uncomment and try again to see if it works? Check the log file for that error message.

---

### Post by sgtstabbin on 2013-10-27
After a few tries, networking is still disabled. The 0000trackpad hook looks to have been successful in the log file, though.

---

### Post by Toz on 2013-10-27
So to summarize:
- with no special pm hooks, on resume, trackpad touch settings are lost
- with hook to re-enable trackpad settings in place, trackpad works but wireless is disabled
- with trackpad + wireless hook, wireless works but trackpad settings are lost (same as first case)

Hmmm. Interesting. I don't see how the two can be related.

Lets try separating the modules. We'll need two files:
**/etc/pm/sleep.d/0000trackpad:**
```
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su rhett -c '/usr/bin/synclient TapButton2=2' ;;
esac
exit 0
```

**/etc/pm/sleep.d/50wifi:**
```
#!/bin/sh
case "$1" in
    suspend)
        rmmod iwldvm
        rmmod iwlwifi
        ;;
    resume)
        modprobe iwlwifi
        modprobe iwldvm
        ;;
esac
exit 0
```
...and make sure that both are executable.

If you don't mind, can you post back /var/log/pm-suspend.log once more and just in case:
```
cat /var/log/syslog | grep PM:
```

---

### Post by sgtstabbin on 2013-10-27
> **Toz said:**
> So to summarize:
- with no special pm hooks, on resume, trackpad touch settings are lost - **CORRECT**
- with hook to re-enable trackpad settings in place, trackpad works but wireless is disabled - **CORRECT**
- with trackpad + wireless hook, wireless works but trackpad settings are lost (same as first case) - **JUST THE OPPOSITE. TRACKPAD SETTINGS ARE FINE, WIRELESS IS DISABLED**


I made the two separate files. Same as before. Trackpad works fine, but wireless is disabled.

Suspend log: [http://paste.ubuntu.com/6313774/](http://paste.ubuntu.com/6313774/)

```
Oct 27 07:36:03 rhett-U43Jc kernel: [  285.234324] PM: noirq resume of devices complete after 143.526 msecsOct 27 07:36:03 rhett-U43Jc kernel: [  285.234480] PM: early resume of devices complete after 0.113 msecs
Oct 27 07:36:03 rhett-U43Jc kernel: [  288.082244] PM: resume of devices complete after 2844.228 msecs
Oct 27 07:36:03 rhett-U43Jc kernel: [  288.082527] PM: Finishing wakeup.
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212883] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212889] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212891] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212892] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212893] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212894] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.212895] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 27 07:37:10 rhett-U43Jc kernel: [    0.860535] PM: Hibernation image not present or could not be loaded.
Oct 27 07:47:37 rhett-U43Jc kernel: [  646.625394] PM: Syncing filesystems ... done.
Oct 27 07:47:37 rhett-U43Jc kernel: [  646.751777] PM: Preparing system for mem sleep
Oct 27 07:48:03 rhett-U43Jc kernel: [  647.017265] PM: Entering mem sleep
Oct 27 07:48:03 rhett-U43Jc kernel: [  648.518621] PM: suspend of devices complete after 1500.018 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  648.518843] PM: late suspend of devices complete after 0.219 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  648.598456] PM: noirq suspend of devices complete after 79.552 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  648.622919] PM: Saving platform NVS memory
Oct 27 07:48:03 rhett-U43Jc kernel: [  648.935840] PM: Restoring platform NVS memory
Oct 27 07:48:03 rhett-U43Jc kernel: [  649.520516] PM: noirq resume of devices complete after 143.510 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  649.520673] PM: early resume of devices complete after 0.114 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  652.407851] PM: resume of devices complete after 2885.033 msecs
Oct 27 07:48:03 rhett-U43Jc kernel: [  652.408113] PM: Finishing wakeup.
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216241] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216248] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216249] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216250] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216251] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216252] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.216254] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 27 07:49:07 rhett-U43Jc kernel: [    0.859906] PM: Hibernation image not present or could not be loaded.
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216025] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216032] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216033] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216035] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216036] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216037] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.216038] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 27 11:08:34 rhett-U43Jc kernel: [    0.859658] PM: Hibernation image not present or could not be loaded.
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216634] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216641] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216642] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216643] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216644] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216645] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.216647] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 27 13:03:15 rhett-U43Jc kernel: [    0.864309] PM: Hibernation image not present or could not be loaded.
Oct 27 13:10:28 rhett-U43Jc kernel: [  458.944501] PM: Syncing filesystems ... done.
Oct 27 13:10:28 rhett-U43Jc kernel: [  459.100697] PM: Preparing system for mem sleep
Oct 27 13:10:44 rhett-U43Jc kernel: [  459.367101] PM: Entering mem sleep
Oct 27 13:10:44 rhett-U43Jc kernel: [  460.764447] PM: suspend of devices complete after 1396.109 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  460.764672] PM: late suspend of devices complete after 0.222 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  460.844086] PM: noirq suspend of devices complete after 79.353 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  460.872549] PM: Saving platform NVS memory
Oct 27 13:10:44 rhett-U43Jc kernel: [  461.185469] PM: Restoring platform NVS memory
Oct 27 13:10:44 rhett-U43Jc kernel: [  461.770152] PM: noirq resume of devices complete after 143.522 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  461.770307] PM: early resume of devices complete after 0.113 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  464.656527] PM: resume of devices complete after 2884.076 msecs
Oct 27 13:10:44 rhett-U43Jc kernel: [  464.656812] PM: Finishing wakeup.
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb585000-0xbb5effff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f0000-0xbb5f7fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb5f8000-0xbb5fffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb600000-0xbb617fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb618000-0xbb618fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb619000-0xbb62cfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb62d000-0xbb62ffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb630000-0xbb631fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb632000-0xbb632fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb633000-0xbb636fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb637000-0xbb639fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63a000-0xbb63dfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb63e000-0xbb64cfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb64d000-0xbb66cfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66d000-0xbb66dfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb66e000-0xbbffffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbc000000-0xbddfffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213093] PM: Registering ACPI NVS region [mem 0xbb585000-0xbb5effff] (438272 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213100] PM: Registering ACPI NVS region [mem 0xbb5f8000-0xbb5fffff] (32768 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213101] PM: Registering ACPI NVS region [mem 0xbb618000-0xbb618fff] (4096 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213102] PM: Registering ACPI NVS region [mem 0xbb62d000-0xbb62ffff] (12288 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213103] PM: Registering ACPI NVS region [mem 0xbb632000-0xbb632fff] (4096 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213104] PM: Registering ACPI NVS region [mem 0xbb63e000-0xbb64cfff] (61440 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.213106] PM: Registering ACPI NVS region [mem 0xbb66d000-0xbb66dfff] (4096 bytes)
Oct 27 13:12:14 rhett-U43Jc kernel: [    0.856742] PM: Hibernation image not present or could not be loaded.

```

---

### Post by Toz on 2013-10-27
Everything with your log files looks good. No errors or any indication of why its not working. Its hard to believe how the two can be interconnected, and I can't seem to separate them.

Lets try taking a different approach here. Delete both of the files you added to /etc/pm/sleep.d (this should return us to the first state where wireless works after suspend but the touchpad settings are lost).

Then create this new python script as **reset_touchpad** in your home directory with the following content (adapted from [http://askubuntu.com/questions/183516/how-do-i-detect-when-my-system-wakes-up-from-suspend-via-dbus-or-similar-in-a-py]("http://askubuntu.com/questions/183516/how-do-i-detect-when-my-system-wakes-up-from-suspend-via-dbus-or-similar-in-a-py")):
```
#!/usr/bin/python
# This is some example code on howto use dbus to detect when the system returns
#+from hibernation or suspend.()

import os          # for running a system command
import dbus      # for dbus communication (obviously)
import gobject   # main loop
from dbus.mainloop.glib import DBusGMainLoop # integration into the main loop

def handle_resume_callback():
    print "System just resumed from hibernate or suspend"
    os.system("/usr/bin/synclient TapButton2=2")

DBusGMainLoop(set_as_default=True) # integrate into main loob
bus = dbus.SystemBus()             # connect to dbus system wide
bus.add_signal_receiver(           # defince the signal to listen to
    handle_resume_callback,            # name of callback function
    'Resuming',                        # singal name
    'org.freedesktop.UPower',          # interface
    'org.freedesktop.UPower'           # bus name
)

loop = gobject.MainLoop()          # define mainloop
loop.run()                         # run main loop

```
...and make the file executable.

Then, in a terminal window, run:
```
$HOME/reset_touchpad
```
...and do a suspend/resume and see what happens.

---

### Post by sgtstabbin on 2013-10-27
I made the reset_touchpad file and placed it in /home/rhett. I assume that is correct since that is where the $HOME command seems to be looking. However, when I ran the $HOME/reset_touchpad it didn't seem to run. It acted like it was trying, but the process wouldn't complete.

A suspend/resume gave us condition 1 where the touchpad settings were lost, but wireless works.

---

### Post by Toz on 2013-10-27
> **sgtstabbin said:**
> I made the reset_touchpad file and placed it in /home/rhett. I assume that is correct since that is where the $HOME command seems to be looking.
Yes, correct.
> However, when I ran the $HOME/reset_touchpad it didn't seem to run. It acted like it was trying, but the process wouldn't complete.
Try this version of the script:
```
#!/usr/bin/python
# This is some example code on howto use dbus to detect when the system returns
#+from hibernation or suspend.()

import os          # for running a system command
import dbus      # for dbus communication (obviously)
import gobject   # main loop
from dbus.mainloop.glib import DBusGMainLoop # integration into the main loop

print "Running..."

def handle_resume_callback():
    print "System just resumed from hibernate or suspend"
    os.system("/usr/bin/synclient TapButton2=2")

DBusGMainLoop(set_as_default=True) # integrate into main loob
bus = dbus.SystemBus()             # connect to dbus system wide
bus.add_signal_receiver(           # defince the signal to listen to
    handle_resume_callback,            # name of callback function
    'Resuming',                        # singal name
    'org.freedesktop.UPower',          # interface
    'org.freedesktop.UPower'           # bus name
)

loop = gobject.MainLoop()          # define mainloop
loop.run()                         # run main loop
```

When you execute **$HOME/reset_touchpad** in a terminal window, you should see:
> Running...
...(the script should then wait - nothing visibly happening) then after suspending and resuming you should see printed in the same terminal window:
> System just resumed from hibernate or suspend

Are you seeing this?

---

### Post by sgtstabbin on 2013-10-27
I got the "Running..." message upon executing $HOME/reset_touchpad. I suspended then resumed and did not see the "System just resumed from hibernate or suspend" message. It still appears to be running just as it was before the suspend.

No change in functionality either. Touchpad settings lost, but wireless works.

---

### Post by Toz on 2013-10-28
I don't get it - this should work.

Came across this [post]("http://ubuntuforums.org/showthread.php?t=2182128&p=12830153&viewfull=1#post12830153") last night that looked promising. Can you recreate** /etc/pm/sleep.d/0000trackpad**"
```

#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su rhett -c '/usr/bin/synclient TapButton2=2' ;;
esac
exit 0
```
...and create **/etc/pm/sleep.d/wakenet** with this content:
```
#!/bin/bash
case "$1" in
   thaw|resume)
      nmcli nm sleep false
      ;;
   *)
      ;;
esac
exit $?
```
...make both scripts executable and try once more?

---

### Post by sgtstabbin on 2013-10-28
I believe you've found the magic combination! After multiple suspend/resume cycles, I've had correct touchpad settings and connected wireless upon resuming every time. I believe I can go on and mark this one solved.

I really appreciate all you've done to help me out with this seemingly small issue. Thanks!

---

### Post by tiliqua_au on 2014-01-12
Old post, but I had this issue from 10.04 - 11.10 when I finally figured it out - gnome-settings-daemon hardcodes some touch pad settings. See [this post ]("http://ubuntuforums.org/showthread.php?t=1576714&p=11363755#post11363755")for the fix.

---

