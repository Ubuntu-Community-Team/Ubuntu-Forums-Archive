---
title: "Temperature Monitoring causing WiFi Disconnects"
date: 2018-06-26
forum: New to Ubuntu
---

### Post by crockman on 2018-06-26
_I'm Brand New to Linux, as of about 3 Days ago_. A Friend gave me a Gateway LT2104u Netbook. It had 7-Starter on it, Microsoft said Starter was unsupported so I bought a $10 7-Home Premium Download/Key from Bonanza. 7-HP didn't run well enough on the old netbook. Did some web surfing for options, came across Lubuntu 18.04... *Hello to you All*.

I'm an Intermediate PC User, I build my own PC's & generally know what Windows Softwares to use. But for 'Inner-Workings', diagnostics, repairs, in-depth software & Linux are beyond me at this time

Anyway, Yesterday I tried to Install Comodo Anti-Virus for Linux & PSensor. I wasn't paying close enough attention but one of those started causing constant WiFi Disconnects. Also one of those caused a 2nd Network Status Icon to appear on the Taskbar. I fiddled with everything for hours then just decided to re-install Lubuntu for I had not much on the HDD yet. After Lubuntu reinstall the 2nd Network Status Icon was still present but the Disconnects went away.

I thought Comodo had caused it so did not reinstall it, but when I re-installed PSensor the Disconnects returned. Received a Message in terminal that I had to Purge 2 Files from the PSensor install, did the purge, the 2nd Status Window then went away but the Disconnects continued. I then uninstalled PSensor and the Disconnects slowly went away.

So PSensor caused the Trouble ?, Apparently not so. Because I've since learned I could just use the Temperature Monitor from Add/Remove Panel Items. **Soon as I turned on the Temperature Monitor in Panel the Disconnects returned and have not yet gone away.**

[U]How the Heck can Monitoring Temperatures have anything to do with Wifi Disconnects ?
[/U]
Any Solutions would be welcome; I do wish to end up with some sort of Temp Monitoring if possible.

Thanks in Advance

---

### Post by NM5TF on 2018-06-28
have you considered [COLOR="#FF0000"]lm-sensors[/COLOR] ???  

```
sudo apt-get install lm-sensors
``` 

Run [COLOR="#FF0000"]sudo sensors-detect[/COLOR] and choose YES to all YES/no questions

you can monitor temps in a terminal  like this: if you want/need temps in Fahrenheit  then use [COLOR="#FF0000"]sensors -f[/COLOR]

```
[tommy@tommy ~]$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +55.0°C  
Core0 Temp:   +53.0°C  
Core1 Temp:   +56.0°C  
Core1 Temp:   +51.0°C  

acpitz-virtual-0
Adapter: Virtual device
temp1:        +34.0°C  (crit = +95.0°C)

f8000-isa-0290
Adapter: ISA adapter
+3.3V:        +3.39 V  
3VSB:         +3.33 V  
Vbat:         +3.01 V  
fan1:        1750 RPM
fan2:        1762 RPM
fan3:           0 RPM  ALARM
fan4:           0 RPM
temp1:        +49.0°C  (high = +70.0°C, hyst = +60.0°C)
temp2:        +40.0°C  (high = +100.0°C, hyst = +85.0°C)
temp3:        +34.0°C  (high = +100.0°C, hyst = +85.0°C)

```

tommy

---

### Post by NM5TF on 2018-06-28
if you want to display the temps on your desktop, you could use the handy desktop monitor app [COLOR="#FF0000"]conky[/COLOR]....

it could look something like this screenie below...you can place it anywhere on the monitor....

you say that you are a  newb with *nix......we ALL were newbs once.....

do you feel ready for a challenge ???

---

### Post by crockman on 2018-06-30
> sudo apt-get install lm-sensors

Did that, that went fine.

> sudo sensors-detect

Answered yes to all, that went fine

Was going to Install Conky afterwards but decided to install psensor again to see what happens

Hard Drive Temp Monitor did not work last time I had psensor installed so I ran:
    sudo apt-get install hddtemp

That seemed to go fine.

Then I did:
    sudo apt-get install psensor

Then the Weird Problems started all over again.
  1. I now have 2 Wifi Information Icons in Task Bar instead of the Usual 1
   2. Again now my WiFi will Randomly Disconnect, then Auto Reconnect.

I find those 2 Problems very odd.

Do you know whats causing it and how to fix it ?

Thanks

---

### Post by NM5TF on 2018-06-30
@crockman

soooooooo.......you say that psensor causes your wifi to drop out....yet you still want to use psensor even after being given 2 alternatives....

does not compute....

no, I don't know what causes it, nor how to fix it.....

maybe try a web search.....

---

### Post by Habitual on 2018-07-02
gKrellm may be another solution.

---

