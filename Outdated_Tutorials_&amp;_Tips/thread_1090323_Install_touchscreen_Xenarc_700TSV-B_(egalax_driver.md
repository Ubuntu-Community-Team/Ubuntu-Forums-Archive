---
title: "Install touchscreen Xenarc 700TSV-B (egalax driver)."
date: 2009-03-08
forum: Outdated Tutorials &amp; Tips
---

### Post by bbauto on 2009-03-08
The included CD was quit out of date and didn't work, it was also hard to find relevant info on internet until i stumbled upon a [French forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=257381&p=2"). In 1 of 2 computors the solution worked at once, the other one i had to manually edit the X-configuration.
Program->Accessories->Terminal:

```
wget http://liveusb.info/egalax/egalax.sh
chmod +x ./egalax.sh
sudo ./egalax.sh
```

Restart your computor and check if the touchscreen reacts to movements, othervise edit your X-configuration (copy and paste).
Program->Accessories->Terminal:
```
sudo gedit /etc/X11/xorg.conf
```

My configuration! append the section "ServerLayout" and "Touch..." i the bottom.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	InputDevice	"EETI" "SendCoreEvents"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
### Touch Configuration Begin ###
Section "InputDevice"
	Identifier "EETI"
	Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
	Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###
```

You will find the calibration and other tools under System->Administration->TouchKit->Tool->4 pt calibration..

Good luck! :D

---

