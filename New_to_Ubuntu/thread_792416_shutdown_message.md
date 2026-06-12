---
title: "shutdown message"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by mardangga on 2008-05-12
Hello Everyone.....

I'm using Ubuntu 8.04. I dunno, is this a problem or not. But when I try to shutdown or restart my Ubuntu, 
usually it only showing bar then the notebook is restart or shutdown. But, right now it's showing message:

===================================================================================================================================

* Starting periodic command scheduler crond			[ OK ]
* Checking battery state...					[ OK ]
* Running local boot scripts (/etc/rc.local) 			[ OK ] <===== I must waiting long enough after this step
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught terminiation signal

NetworkManager: <debug> [1210586047.043763] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1210586047.043995] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device wlan0.

NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

===================================================================================================================================

This make my notebook shutdown or restart slower. Is there anything wrong with my Ubuntu? Please help me to fix these. 
Coz I'm a newbie. And sorry for my poor English. Thx......

---

### Post by corevette on 2008-05-12
check the posting on this [page]("https://answers.launchpad.net/ubuntu/+question/16914") by marcobra
supposedly it works

---

### Post by dizee on 2008-05-12
If that fails this thread may be of use [http://ubuntuforums.org/showthread.php?t=772733](http://ubuntuforums.org/showthread.php?t=772733)

---

### Post by High Roller on 2008-05-13
There's a workaround to this bug [here]("http://ubuntuforums.org/showpost.php?p=4934956&postcount=10").

---

