---
title: "Error Message while shutdown about NetworkManager"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by adnansanni on 2008-05-06
from today I have got a error message while shutdown my laptop. Anybody has idea to solve it? Here is the code that I have. I'm using hadry heron.

* Starting periodic command scheduler crond [OK]
* Checking batterystate... [OK]
* Running local boot scripts (/etc/rc.local) [OK]
NetwokManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetwokManager: <info> Caught terminiation signal
NetwokManager: <debug>[1210091816.740501] nm_print_open_socks(): Open Sockets List:
NetwokManager: <debug>[1210091816.740687] nm_print_open_socks(): Open Sockets List:
NetwokManager: <info> Deactivating device eth0.
NetwokManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetwokManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus deamon is running!
NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb-data->data->dbus_connection' failed

---

### Post by macaholic on 2008-05-06
I get similar stuff on shutdown from network manager, if it isn't causing issues with your system, I wouldn't worry about it too much, my guess is the dbus daemon is shutting down before Network manager and it's gettings angry because of that.

---

### Post by VoodooLoveDog on 2008-05-06
Same thing happens to my laptop. It doesn't seem to be a problem.

---

### Post by sujoy on 2008-05-06
but it ought to be resolved though, i had similar issues in gutsy also

---

### Post by adnansanni on 2008-05-07
So are there no ways to solve that?

---

### Post by kpkeerthi on 2008-05-07
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691)

---

### Post by tedrogers on 2008-05-08
I've got this too on an IBM T42 running Hardy on a USB drive (just testing you see!).

Couldn't see a definite solution on the bug report.

I don't feel right with a screen full of errors - even though it doesn't make that much difference for me as it shuts down ok.

Might try and see if the proposed updates on the bug report fix it. Hoping I can just enable the proposed updates in SOURCES and let it do the work.

If you don't hear from me again then you can assume it didn't work....I will be back to explain otherwise.

---

### Post by sujoy on 2008-05-09
and becuase of it, it takes ages to shutdown my laptop, it just waits till that message finally comes, after which its just a matter of seconds before the computer shutdowns.

---

### Post by tedrogers on 2008-05-11
I thought I'd post anyway...and those proposed updates made naff all difference here! Oh well. No solution then?

---

### Post by prinknash on 2008-05-11
> **adnansanni said:**
> So are there no ways to solve that?

You might want to try this:

1. Go to System - Administration - Login Window.

2. Under 'General', press "Edit commands ...'

3. Select 'Halt command' - in 'Path' box, cut the text in quotes (I.e. "Shut down via gdm") - press "Apply command change" - paste the text back - press 'Apply command change'

4. Select 'Reboot command' and do as for 3. above

Try restarting a couple of times and see if this has fixed the problem. It seems to have done so for a number of people, including me - although I wouldn't care to have to explain exactly how it's fixed the problem!

p

---

### Post by nick_h on 2008-05-12
This is the same problem described in [this](http://ubuntuforums.org/showthread.php?t=772733) thread.

---

### Post by maramot on 2008-05-12
I have the same problem since I installed ubuntu 8.04, only that since yesterday I also lost my wireless. The driver is installed, the device is listed in the ifconfig/iwconfig, lspci, I even get to choose from wireless networks, only that I can't ping even my router and the network always stays at 0%.

I haven't changed anything manually so I suspect I've downloaded some update which "upgraded" me from "waiting a bit until wireless starts after login" to "no wireless at all". Boy, I should never have updated to this messed up release!

It says something about disabling wlan0 but I can't read it fast enough. Can anyone tell me how can I see this output when I'm shutting down? Save it somewhere to read it perhaps?

---

### Post by zvonkojaz on 2008-06-03
Hi!

I got the same error...but its not that easy to deal with...because it caouses my internet connection to fail ...it apears that after the latest update the system doesnt recognize my network connection device..eth0? any ideas...help?..pls...because without any connection to internet i cannot download any repairs.

tnx

---

### Post by XMAG on 2008-06-17
I had the same error here. Here's how I solved it:

I removed packages **network-manager** and **network-manager-gnome** and installed them again. Be sure to download the 2 .deb files before removing the packages since it will disable your network connectivity.

You can find both packages at **packages.ubuntu.com** . Search for them, select your distro and download the package for your CPU architecture (link at the bottom of the page).

After you have them

```
sudo apt-get remove network-manager network-manager-gnome
```

reboot, then

```
sudo dpkg -i package_name_here
``` for each package

reboot and see if the problem goes away. Mine seems to be gone!

---

### Post by happyisland on 2008-07-13
> **prinknash said:**
> You might want to try this:

1. Go to System - Administration - Login Window.

2. Under 'General', press "Edit commands ...'

3. Select 'Halt command' - in 'Path' box, cut the text in quotes (I.e. "Shut down via gdm") - press "Apply command change" - paste the text back - press 'Apply command change'

4. Select 'Reboot command' and do as for 3. above

Try restarting a couple of times and see if this has fixed the problem. It seems to have done so for a number of people, including me - although I wouldn't care to have to explain exactly how it's fixed the problem!

p

This solution worked for me. Thanks for the fix!

---

### Post by fletch31337 on 2008-08-09
> **macaholic said:**
> I get similar stuff on shutdown from network manager, if it isn't causing issues with your system, I wouldn't worry about it too much, my guess is the dbus daemon is shutting down before Network manager and it's gettings angry because of that.

I have a dirty hack to fix this. In the /etc/init.d/dhcdbd file, add the following line straight under the "stop)" line:

killall NetworkManager # Dirty hack to avoid nasty error messages!

Nasty I know, but until it is fixed, this will terminate the daemon BEFORE D-BUS terminates.

---

### Post by oyvindaa on 2008-08-09
> **prinknash said:**
> You might want to try this:

1. Go to System - Administration - Login Window.

2. Under 'General', press "Edit commands ...'

3. Select 'Halt command' - in 'Path' box, cut the text in quotes (I.e. "Shut down via gdm") - press "Apply command change" - paste the text back - press 'Apply command change'

4. Select 'Reboot command' and do as for 3. above

Try restarting a couple of times and see if this has fixed the problem. It seems to have done so for a number of people, including me - although I wouldn't care to have to explain exactly how it's fixed the problem!

p

That fixed the problem on my computer. Thank you prinknash!

---

