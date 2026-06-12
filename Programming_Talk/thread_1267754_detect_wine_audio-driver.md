---
title: "detect wine audio-driver"
date: 2009-09-16
forum: Programming Talk
---

### Post by Sandsound on 2009-09-16
The short version :

How do I detect which audio-driver is set in wine ?

The long version :

If I try to access my audio-settings in winecfg it stalls for about a minute, which is pretty annoying, so I have build a little Python app ( [http://www.sandgreen.dk/index.php?side=python_switch](http://www.sandgreen.dk/index.php?side=python_switch) ) that run in the tray so I can change the audio-driver smoothly without starting winecfg.

I can change the settings by running a .reg file, and have made a alsa.reg and a oss.reg.
The alsa.reg look like this :

```
REGEDIT4
[HKEY_CURRENT_USER\Software\Wine\Drivers]
"Audio"="alsa"
```

To run it in Python I use :

```
os.system('wine regedit oss.reg')
```

But it would be nice to have a radio-button that detect the current driver, this would allow me to use the tray icon to show a alsa-icon when the alsa-driver is selected and oss-icon when the oss-driver is selected.



BTW. I use alsa (wineasio) for work, and oss for playing games like Guild Wars.
I know that some might think that I should use my energy trying to solve why winecfg stalls when entering the audio-tab, but I have tried numerous asoundrc configurations and spent hours of banging my head against the keyboard trying to solve this, so I have decided to leave it as it is, and just use this workaround.

---

### Post by phrostbyte on 2009-09-16
You could pull it out of the Wine registry I guess.

This *might* help you. [http://wiki.jswindle.com/index.php/Wine_Registry](http://wiki.jswindle.com/index.php/Wine_Registry)

---

### Post by Sandsound on 2009-09-17
> **phrostbyte said:**
> This *might* help you. [http://wiki.jswindle.com/index.php/Wine_Registry](http://wiki.jswindle.com/index.php/Wine_Registry)

Thanks.

this might not be elegant, but this works :

```
os.system('wine regedit /E test.reg "HKEY_CURRENT_USER\Software\Wine\Drivers"')
for line in fileinput.input("test.reg",inplace =1):
	line = line.strip()
	if not 'Audio' in line:
		print line
	if 'Audio' in line:
		print line 			
		s= line.split('"')
		driver = str(s[3])
		self.wTree.get_widget("label1").set_text("Wine is set to use " + driver)
	fileinput.close
```

---

