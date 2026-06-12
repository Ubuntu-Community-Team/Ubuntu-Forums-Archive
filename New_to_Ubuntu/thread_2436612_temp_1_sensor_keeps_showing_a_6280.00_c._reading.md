---
title: "temp 1 sensor keeps showing a 6280.00 c. reading"
date: 2020-02-10
forum: New to Ubuntu
---

### Post by pierreu1 on 2020-02-10
[COLOR=White].[/COLOR]
I have just moved from Windows 10 to Ubuntu. I had some fan issue that made me panicked. I managed to install everything and make everything work, so far. Here is one issue that I don't know how to resolve.

Find below a HardInfo report on my sensors. All sensors' reading are being given properly in Psensor, but not Temp 1 ! I would guess that the 6280.00 c. reading (in Psensor too) is related to a 64 c to 80 c degrees. Is it broken? Can I tweak something to make it "read" or "work"? 

EDIT: That reading does not change. The others do.

Thank you in advance.

```
-Sensors-


../../thermal_zone0/temp1    Temperature    64,00°C    
../../BAT0/in0    Voltage    7,20V    
coretemp/temp2    Temperature    53,00°C    
coretemp/temp3    Temperature    53,00°C    
coretemp/temp4    Temperature    54,00°C    
coretemp/temp5    Temperature    54,00°C    
asus-nb-wmi/fan1    Fan    2700,00RPM    
asus-nb-wmi/temp1    Temperature    6280,00°C    
../../thermal_zone1/temp1    Temperature    53,00°C    
../../thermal_zone2/temp1    Temperature    54,00°C    
thermal/thermal_zone2    Temperature    54,00°C    
thermal/thermal_zone0    Temperature    64,00°C    
thermal/thermal_zone1    Temperature    54,00°C
```

---

### Post by CatKiller on 2020-02-10
Sensor chip outputs have to be reverse-engineered. The manufacturers have zero interest in helping linux read those outputs, and the people who do the reverse-engineering have limited time and limited access to every variation to document whatever weird quirks a particular implementation has.

Your 6280 °C is probably really 62.8 °C.

---

### Post by pierreu1 on 2020-02-10
Thanks for that. I agree that this is a problem. 

Btw, the temperature does not change, so I doubt that it is 62.8 c

---

### Post by daniewicz on 2020-02-13
I also get a few unrealistic temperature readings (which never change) when using [COLOR=#000000]Psensor[/COLOR]

---

