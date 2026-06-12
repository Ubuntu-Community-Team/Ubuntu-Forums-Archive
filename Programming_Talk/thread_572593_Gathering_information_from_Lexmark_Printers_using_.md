---
title: "Gathering information from Lexmark Printers using SNMP"
date: 2007-10-10
forum: Programming Talk
---

### Post by rhipwell on 2007-10-10
Hi Everyone, 

I am currently starting a small project to pull toner yeild information from a Lexmark printer. I have used tools such as Markvision and Web Jet Admin, but these are cumbersome and quiet frankly overkill for my needs. 

I have checked RFC 1759, but alas most of the options contained within seem to be unsupported. 

My question is as follows:

Has anyone successfully pulled toner cartridge information from a lexmark printer using snmp before? and if so, what commands did you use? 

Thanks in advance,

-Rob

---

### Post by dwhitney67 on 2007-10-10
You would use an SNMP getRequest or getNextRequest.  If you are unfamiliar with SNMP, then that might not make sense at all.  SNMP can be "simple" to use if you have an SNMP-agent software suite.  Without an agent, I personally would not know how to proceed.

It's been over 5 years since I've dealt with SNMP, but I do recall that there are free downloadable SNMP agents written in C++; just search the web.

Btw, does your printer not support the HTTP protocol?  Try connecting to your printer from your browser.  Use [http://IP-of-printer](http://IP-of-printer).

---

### Post by rhipwell on 2007-10-10
Thanks for the reply dwhitney67. Let me explain a bit better to why the printer web page and the various other tools do not scale to my need.

I am responsible for a site with over 500 printers of various makes and models, most of them are either HP or Lexmark. Recently we have noticed a trend with our lexmark machines where toner yield seems to corrospond to print quality issues. As such I need to find the toner yield of approx 68 machines. 

Markvision ( Lexmarks SNMP tool for printers ) takes approx 3 minutes to gather the data I need *per machine*. 

The printers native interface (i.e the web page) is quicker, taking approx 2 minutes for me to gather the data, however it does not support exporting the data to file.

Running smnpget or snmpwalk commands can gather the data in a blink of an eye - however I am unsure of the OID for the toner yield command. 

All the tests I ran earlier today for time used the following command: (IP has been changed to <IP> )
```

snmpget -v 2c -c public <IP> printer.prtgen.prtgenInfoTable.prtgenInfoEntry.prtgenSerialNo.1
```


That command returns the serial # in less then a second. Compared to 2 to 3 minutes per the other solutions. Plus I can pipe the data to file.

Anyone have any ideas?

Also - Would copying the toner yield commands from the RCF to a MIB file work? Thanks

-Rob

---

### Post by dwhitney67 on 2007-10-10
I sure wish I had more time on my hands to help you out.  I really would like to get back into SNMP realm.  Unfortunately it seems like you need your solution "yesterday".

I have source code for an SNMP agent (written in C++), but it was written 5+ years ago and I am not sure it will compile with gcc-4.1.x.

Btw, have you attempted to walk the MIB of a single printer?  Does it not report back the VB-pair (OID and Value)?  I would think that you would be able to deduce which OID pertains to the toner level.  Maybe it might help if you contacted Lexmark so see if they can send you the MIB.

---

### Post by rhipwell on 2007-10-11
Thanks again for the reply, 

The MIB Lexmark provides unfortunatly only has basic printer information on it, most of the MIB pertains to TCP/IP settings etc. 

I will try and walk to entire printer this morning and post any results. 

Thanks again.

-Rob

---

### Post by rhipwell on 2007-10-11
I walked the printer and the supported OINs are listed as follows (small subset) :

```

SNMPv2-SMI::mib-2.43.7.1.1.2.1.18 = STRING: "ZH"
SNMPv2-SMI::mib-2.43.7.1.1.2.1.19 = STRING: "ZH"
SNMPv2-SMI::mib-2.43.7.1.1.2.1.20 = STRING: "KO"
SNMPv2-SMI::mib-2.43.7.1.1.3.1.1 = STRING: "  "
SNMPv2-SMI::mib-2.43.7.1.1.3.1.2 = STRING: "  "
SNMPv2-SMI::mib-2.43.7.1.1.3.1.3 = STRING: "  "
SNMPv2-SMI::mib-2.43.7.1.1.4.1.1 = INTEGER: 2009
SNMPv2-SMI::mib-2.43.7.1.1.4.1.2 = INTEGER: 2009
SNMPv2-SMI::mib-2.43.7.1.1.4.1.3 = INTEGER: 2009
SNMPv2-SMI::mib-2.43.11.1.1.6.1.1 = STRING: "Cyan Toner"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.2 = STRING: "Magenta Toner"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.3 = STRING: "Yellow Toner"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.4 = STRING: "Black Toner"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.5 = STRING: "Photo Drum:Cyan"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.6 = STRING: "Photo Drum:Magenta"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.7 = STRING: "Photo Drum:Yellow"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.8 = STRING: "Photo Drum:Black"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.9 = STRING: "Waste Toner Box"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.10 = STRING: "Fuser"
SNMPv2-SMI::mib-2.43.11.1.1.6.1.11 = STRING: "Transfer Belt"
```

Does anyone know where I can find the information on what theses OIN's pertain to? Thanks

-Rob

---

### Post by gdesmet on 2007-10-18
More OID info can be found here:
```
http://www.oid-info.com/cgi-bin/display?tree=1.3.6.1.2.1.43
```

The 43.10 group contains Marker(=toner) info:

```
OID	Object	Type	Value	
1.3.6.1.2.1.43.10.2.1.2.1.1	prtMarkerMarkTech	INTEGER	4	
1.3.6.1.2.1.43.10.2.1.3.1.1	prtMarkerCounterUnit	INTEGER	8	
1.3.6.1.2.1.43.10.2.1.4.1.1	prtMarkerLifeCount	COUNTER	470285	
1.3.6.1.2.1.43.10.2.1.5.1.1	prtMarkerPowerOnCount	COUNTER	2879	
1.3.6.1.2.1.43.10.2.1.6.1.1	prtMarkerProcessColorants	INTEGER	1	
1.3.6.1.2.1.43.10.2.1.7.1.1	prtMarkerSpotColorants	INTEGER	0	
1.3.6.1.2.1.43.10.2.1.8.1.1	prtMarkerAddressabilityUnit	INTEGER	tenThousandthsOfInches(3)	
1.3.6.1.2.1.43.10.2.1.9.1.1	prtMarkerAddressabilityFeedDir	INTEGER	1200	
1.3.6.1.2.1.43.10.2.1.10.1.1	prtMarkerAddressabilityXFeedDir	INTEGER	1200	
1.3.6.1.2.1.43.10.2.1.11.1.1	prtMarkerNorthMargin	INTEGER	1667	
1.3.6.1.2.1.43.10.2.1.12.1.1	prtMarkerSouthMargin	INTEGER	1667	
1.3.6.1.2.1.43.10.2.1.13.1.1	prtMarkerWestMargin	INTEGER	1667	
1.3.6.1.2.1.43.10.2.1.14.1.1	prtMarkerEastMargin	INTEGER	1667	
1.3.6.1.2.1.43.10.2.1.15.1.1	prtMarkerStatus	INTEGER	4	

```

The 43.11 group contains MarkerSupplies info:
```
OID	Object	Type	Value	
1.3.6.1.2.1.43.11.1.1.2.1.1	prtMarkerSuppliesMarkerIndex	INTEGER	1	
1.3.6.1.2.1.43.11.1.1.3.1.1	prtMarkerSuppliesColorantIndex	INTEGER	1	
1.3.6.1.2.1.43.11.1.1.4.1.1	prtMarkerSuppliesClass	INTEGER	3	
1.3.6.1.2.1.43.11.1.1.5.1.1	prtMarkerSuppliesType	INTEGER	3	
1.3.6.1.2.1.43.11.1.1.6.1.1	prtMarkerSuppliesDescription	OCTET-STRING	"Diamond Fine Toner"	
1.3.6.1.2.1.43.11.1.1.7.1.1	prtMarkerSuppliesSupplyUnit	INTEGER	7	
1.3.6.1.2.1.43.11.1.1.8.1.1	prtMarkerSuppliesMaxCapacity	INTEGER	30000	
1.3.6.1.2.1.43.11.1.1.9.1.1	prtMarkerSuppliesLevel	INTEGER	-3	

```

And the 43.12 group contains MarkerColorant info:
```
OID	Object	Type	Value	
1.3.6.1.2.1.43.12.1.1.2.1.1	prtMarkerColorantMarkerIndex	INTEGER	1	
1.3.6.1.2.1.43.12.1.1.3.1.1	prtMarkerColorantRole	INTEGER	3	
1.3.6.1.2.1.43.12.1.1.4.1.1	prtMarkerColorantValue	OCTET-STRING	black	
1.3.6.1.2.1.43.12.1.1.5.1.1	prtMarkerColorantTonality	INTEGER	2	

```

Unfortunaly I don't see a value which indicates a toner level :(

The  1.3.6.1.2.1.1.1 OID gives more general info about your printer:
```
OID	Object	Type	Value	
1.3.6.1.2.1.1.1.0	sysDescr	OCTET-STRING	"IBM Infoprint 1130 version 54.10.21 kernel 2.4.0-test6 All-N-1"	
**1.3.6.1.2.1.1.2.0	sysObjectID	OID	1.3.6.1.4.1.641.1	**
1.3.6.1.2.1.1.3.0	sysUpTime	TIMETICKS	"19/09/2007 21:55:45"	
1.3.6.1.2.1.1.4.0	sysContact	OCTET-STRING		
1.3.6.1.2.1.1.5.0	sysName	OCTET-STRING	PREXP3	
1.3.6.1.2.1.1.6.0	sysLocation	OCTET-STRING		
1.3.6.1.2.1.1.7.0	sysServices	INTEGER	72	

```

But the 1.3.6.1.4.1.641 is a private/enterprise OID and the info is hard to find.

Can you give us some OID's of printers you find in the 1.3.6.1.2.1.1 branch? Are they all 1.3.6.1.4.1.641?

Geert

---

### Post by gdesmet on 2007-10-18
The Lexmark MIB file can be found here (and click on the ZIP icon) :
```
http://www.oidview.com/mibs/641/LEXMARK-PVT-MIB.html
```

Geert

---

### Post by rhipwell on 2007-10-18
Thanks for the Reply, that information is great. I have a meeting with Lexmark on Monday. I think im going to see if they have anything above and beyond the information you've provided thus far. Again thanks!

-Rob

---

