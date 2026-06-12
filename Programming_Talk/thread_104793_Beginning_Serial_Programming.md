---
title: "Beginning Serial Programming"
date: 2005-12-16
forum: Programming Talk
---

### Post by badtyprr on 2005-12-16
Hello all, I'm working on a project that requires me to do a few things in Linux.. I'd really appreciate any help that I can get to start this programming project. I want to be able to do two things essentially:

1. Modify the airo.c (Aironet wireless network adapter driver) to allow me to gain access to the signal strength of wireless networks in a site survey.
2. Use RS232 to communicate to a PICF452 microcontroller (using a MAX232 to maintain voltage levels)

I've looked through a lot of airo.c and have identified a key structure that contains the information I want:

```

typedef struct {
	u16 len;
	u8 mac[6];
	u16 mode;
	u16 errorCode;
	u16 sigQuality;
	u16 SSIDlen;
	char SSID[32];
	char apName[16];
	char bssid[4][6];
	u16 beaconPeriod;
	u16 dimPeriod;
	u16 atimDuration;
	u16 hopPeriod;
	u16 channelSet;
	u16 channel;
	u16 hopsToBackbone;
	u16 apTotalLoad;
	u16 generatedLoad;
	u16 accumulatedArl;
	u16 signalQuality;
	u16 currentXmitRate;
	u16 apDevExtensions;
**	u16 normalizedSignalStrength;**
	u16 _reserved[10];
} StatusRid;

```

I haven't yet figured out how to get the driver to do a site survey to allow me to see the signal strengths of surrounding APs. Most of the code is way over my head for now. Does anyone know how to properly use the driver to get this information?

Also, for the RS232 communications, I am again a complete noob on programming RS232. Can anyone give me a headstart? Resources and the like?

Thanks so much. :D

---

### Post by skirkpatrick on 2005-12-16
I found this page, [http://www.easysw.com/~mike/serial/serial.html#advanced](http://www.easysw.com/~mike/serial/serial.html#advanced) to be a good resource.  Been doing serial communication for a while now under Linux and can help you out if needed.

---

### Post by pearma on 2005-12-17
[QUOTE=skirkpatrick]I found this page, [http://www.easysw.com/~mike/serial/serial.html#advanced](http://www.easysw.com/~mike/serial/serial.html#advanced) to be a good resource.  Been doing serial communication for a while now under Linux and can help you out if needed.[/QUOTE]
sorry,the link is broken.

---

### Post by badtyprr on 2005-12-17
[QUOTE=skirkpatrick]I found this page, [http://www.easysw.com/~mike/serial/serial.html#advanced](http://www.easysw.com/~mike/serial/serial.html#advanced) to be a good resource.  Been doing serial communication for a while now under Linux and can help you out if needed.[/QUOTE]

The link is fine for me. I really appreciate the help. I'm sure I'll need to ask you more about this after I finish reading this article and writing a test program. Thanks.

---

