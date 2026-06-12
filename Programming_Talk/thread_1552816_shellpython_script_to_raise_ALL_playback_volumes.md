---
title: "shell/python script to raise ALL playback volumes"
date: 2010-08-14
forum: Programming Talk
---

### Post by l.capriotti on 2010-08-14
I'm trying to code a general script raising the playback volume of all alsa output controls but cannot discriminate between capture and playback controls from amixer output. The script has to run on different HW so hardcoding mixer control names is not an option.

I have tried the following:

```

volumeLevel = 80

mixerList = runAndGetStdOutput("amixer scontrols")
arMixers = mixerList.split('\n')
for aMixer in arMixers:
	nameStart = aMixer.find("'")
	if nameStart>0:
		# print "Mixer name=" + aMixer[nameStart:]
		output = runAndGetStdOutput("amixer sget " + aMixer[nameStart:])
		if output.find("pvolume") > 0:
			output = runAndGetStdOutput("amixer sset " + aMixer[nameStart:] + " " + volumeLevel + "% unmute")
			if output.find("pswitch") > 0:
				output = runAndGetStdOutput("amixer sset " + aMixer[nameStart:] + " unmute")

```

but with that code also the volume of input controls is increased.

Grateful for any advice.

Luigi

---

