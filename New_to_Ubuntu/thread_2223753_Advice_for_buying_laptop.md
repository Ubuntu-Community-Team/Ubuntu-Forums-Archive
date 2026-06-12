---
title: "Advice for buying laptop"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by alexander31 on 2014-05-12
Hey guys,

I'm looking for a new laptop and was settling on a windows 8 one.

But I came across one on ebuyer at a great price running Ubuntu 12.04

now what I would like to know is if I buy that laptop :
1. Can I upgrade to 14.04 easily?
2. Can I use photos on my iPhone and transfer and manipulate them on ubuntu?
3. How easily can I pick the os up and what primarily can I use Ubuntu for?

thanks guys Alex.

---

### Post by pfeiffep on 2014-05-12
@alexander31, 
1) yes you should be able to upgrade to Ubuntu 14.04 in July
2) Transfering photos from iPhone to Linux can be done, but not with iCloud or iTunes since neither on run on Linux. I'm dual booting Win 7 - photos are one reason
3) Probably fairly easily...here's a quick list for you
[SIZE=1]
[/SIZE][TABLE="width: 624"]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]**_Program On Windows_**[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]**_Free Alternative working on Windows / Ubuntu_**[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Internet Explorer[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Fire Fox & Chrome[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Outlook / Outlook Express[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Thunderbird[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Quicken[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Mint online[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Microsoft Office[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Open Office / Libre Office[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Photo Shop Elements[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]GIMP[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Windows Explorer[/FONT][/COLOR][/SIZE]
[/TD]
[TD][SIZE=1][COLOR=#000000][FONT=Arial]Nautilus (Ubuntu only)[/FONT][/COLOR][/SIZE]
[/TD]
[/TR]
[/TABLE]


Good luck! - let us know how you progress

---

### Post by alexander31 on 2014-05-12
@pfeiffep

thanks for the reply, why is it July and not now? Also for transferring photos is it still fairly easy to do?


alex.

---

### Post by pfeiffep on 2014-05-12
July is when the LTS version 12.04 is upgradeable to 14.04.1 
How do you transfer photos now?

---

### Post by alexander31 on 2014-05-12
I see....can I set up on 12.04 and when I upgrade to 14.04 keep all my data or would it be a clean wipe for 14.04?

i use an iPad ATM and cannot transfer, another reason I'm getting a laptop for this..


Alex.

---

### Post by monkeybrain20122 on 2014-05-12
I would worry more about hardware compatibility than whether Ubunbtu update. For laptops that come with Win8 uefi and secure boot is something to watch out for. 

graphic card is another main thing to consider. In general Intel works out of the box, but crappy driver. Nvidia has the best performance (even better than Windows I am told) if use the proprietary driver, it is in general not hard to install and upgrade. The downside is Optimus and laptops with Nvidia card tend to be expensive. Well AMD is interesting, depending on the card model the open driver can be almost as good as (or better in some cases) the proprietary driver but probably does not work for the really new cards yet, the proprietary fglrx driver is kind of a pain to install and upgrade comparing to Nvidia (even though it is supposed to be just as easy if you install from repo or ppa, but it is never the case for my brief experience with AMD card)

---

### Post by monkeybrain20122 on 2014-05-12
> **alexander31 said:**
> I see....can I set up on 12.04 and when I upgrade to 14.04 keep all my data or would it be a clean wipe for 14.04?

i use an iPad ATM and cannot transfer, another reason I'm getting a laptop for this..


Alex.

You can keep your data if you have a separate /home partition. In that case do manual install (something else) over the / partition (still use as /) and don't format the /home.

---

### Post by gifford on 2014-05-12
In my opinion it is always better to do a clean install of the OS.
14.04 is working just fine for most folks and any problems can be addressed here in the forum.

---

### Post by pqwoerituytrueiwoq on 2014-05-12
you can upgrade 12.04 to 14.04 now, 12.04 will not start bugging you about it till july
just run [FONT=courier new]do-release-upgrade[/FONT]

---

### Post by pfeiffep on 2014-05-12
> **alexander31 said:**
> I see....can I set up on 12.04 and when I upgrade to 14.04 keep all my data or would it be a clean wipe for 14.04?

i use an iPad ATM and cannot transfer, another reason I'm getting a laptop for this..


Alex.If you choose this laptop there's probably nothing on it of a personal nature so a clean wipe would be my choice;)

I thought iPads were equipped to run iCLoud and as such photos from you iPhone should transfer automatically.

---

### Post by monkeybrain20122 on 2014-05-12
> **pqwoerituytrueiwoq said:**
> you can upgrade 12.04 to 14.04 now, 12.04 will not start bugging you about it till july
just run [FONT=courier new]do-release-upgrade[/FONT]

You can. But IMO not advisable. A clean install is always a lot faster and safer.

The dilemma is people who customize and tweak their systems a lot have a strong incentive to "upgrade" because they want to keep their configurations, but in those cases "upgrade" almost always fails unless you reverse the customized configurations to a "pristine" state. On the other hand upgrade will work but takes a lot longer still than a clean install if system is close to vanilla state, but in that case why even "upgrade"?

---

