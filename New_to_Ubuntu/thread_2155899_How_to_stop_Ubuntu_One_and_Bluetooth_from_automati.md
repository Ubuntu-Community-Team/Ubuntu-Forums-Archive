---
title: "How to stop Ubuntu One and Bluetooth from automatically starting up"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by MaxxABillion on 2013-06-19
I've searched throughout settings but I cannot find out how to stop Ubuntu One and Bluetooth from starting up when I turn on my computer.  I have to manually turn them off, and it get a little annoying after while.  

Does anyone know how to prevent these two from starting up?

---

### Post by stinkeye on 2013-06-19
If not shown in startup applications. run this too show all.
```
cd /etc/xdg/autostart/ && sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

The bluetooth entry in startup  applications is just the bluetooth-applet manager.
Additionally you can disable the bluetooth service from starting if you don't use.
Create an override file for the service with "manual" in the config..
```
sudo sh -c "echo 'manual' > /etc/init/bluetooth.override"
```

...will not start at boot but you can still start manually if needed with...
```
sudo service bluetooth start
```
and to stop...
```
sudo service bluetooth stop
```

to check bluetooth service status, use 
```
status bluetooth
```

To allow the bluetooth service to run at startup again, remove /etc/init/bluetooth.override...
```
sudo rm /etc/init/bluetooth.override
```

---

