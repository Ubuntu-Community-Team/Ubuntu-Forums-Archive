---
title: "Modifying airo.c to get Signal Strength"
date: 2005-12-17
forum: Programming Talk
---

### Post by badtyprr on 2005-12-17
I guess I should have posted this as a separate thread in the first place, but anyways..

I wanted to be able to modify the airo.c (Aironet wireless network adapter driver) to allow me to gain access to the signal strength of wireless networks in a site survey.

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

I haven't yet figured out how to get the driver to do a site survey to allow me to see the signal strengths of surrounding APs. Most of the code is way over my head for now. Does anyone know how to properly use the driver to get this information? Am I going about this in the right way?

---

### Post by toojays on 2005-12-17
You are probably best off asking this question on the development list for the driver.

---

### Post by badtyprr on 2005-12-18
> You are probably best off asking this question on the development list for the driver.

Is that on sourceforge or something? I've never worked with driver code before.

---

### Post by badtyprr on 2005-12-19
*bump* Sorry, could someone direct me to a development list for this driver? I've google'd it, but don't have much luck.

---

### Post by toojays on 2005-12-21
Maybe there is an email address in the file you are editing? They might know the answer.

---

