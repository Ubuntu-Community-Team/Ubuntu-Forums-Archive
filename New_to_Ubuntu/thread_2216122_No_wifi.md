---
title: "No wifi"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by longshanks62 on 2014-04-10
I have installed Ubuntu 11.10 onto a spare drive on my Dell studio laptop, thus creating a dual boot giving me the option of learning Ubuntu, the problem is no wifi connection. In the network section on the wireless tab I am told "firmware missing" hardware address 00:22:5f:30:E7:CA.
  Some advice please.
regards
Brian

---

### Post by mörgæs on 2014-04-10
11.10 is out of support.
Your best option is a fresh install of 13.10 or 14.04 (beta) using wired internet access.

---

### Post by longshanks62 on 2014-04-10
hi.
this is a fresh install, yesterday in fact

---

### Post by plucky on 2014-04-10
> **longshanks62 said:**
> hi.
this is a fresh install, yesterday in fact

11.10 repositories are closed so you won't be able to update & upgrade.

Is it some other version? 13.10 perhaps?

Use a currently supported version.

Good Luck

---

### Post by varunendra on 2014-04-10
+1 to 13.10 or 14.04. I personally recommend 12.04.4, since it offers the same kernel (hence drivers) and xorg packages as 13.10 currently.

It won't automatically solve the 'firmware missing' problem, but would be much easier to solve on a supported version.

To let us see which firmware you need, please post the outputs of -
```
lspci -nnk | grep -iA2 net
dmesg | grep -i firmware
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by longshanks62 on 2014-04-10
I have got  12.04 downloaded, but we are talking absolute beginners here so " post outputs of" !!

---

### Post by varunendra on 2014-04-10
> **longshanks62 said:**
> I have got  12.04 downloaded, but we are talking absolute beginners here so " post outputs of" !!

..means to say the outputs of the commands that are entered in a terminal. To open a terminal, press Ctrl-Alt-T, then type those commands one-by-one (pressing 'Enter' after each one). They will return some outputs like -
```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e048]
	Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
	Kernel driver in use: atl1c
....
....
[    0.579989] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   37.860524] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   38.235496] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
```
Of course yours may be different. We need to see these outputs from your system to determine which wireless card you have and if there is some firmware error.

Using 'Code' tags will put the output in your post in a box like above one. Posting it like normal text (like this paragraph) won't preserve its formatting and make the output look dirty (sometime even very hard to read), hence the recommendation about the code tags. :)

---

