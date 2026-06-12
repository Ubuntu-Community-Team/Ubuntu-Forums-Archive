---
title: "Send SMS through USB modem"
date: 2011-02-19
forum: Philippine Team
---

### Post by argiebong on 2011-02-19
How to send SMS through globe tatoo usb modem?

---

### Post by Script Warlock on 2011-02-19
try wammu or umtsmon..

---

### Post by PaulReaver on 2011-02-19
what version of ubuntu are you using?

and what model of modem is it? globe tatoo???

what does the globe show up as if you do

$lsusb


?

---

### Post by jepong on 2011-02-20
> **PaulReaver said:**
> and what model of modem is it? globe tatoo???

Globe Tattoo is not a model? Usually broadband kits (from the big 3 networks) are Huawei or ZTE.

---

### Post by madcSPYnX on 2011-02-20
nasubukan nyo na guys yan sa wine??? nagtry kasi ako hehehehe pero di na read ung modem :) ung mismong application lang nag install... guys turuan nyo nga ako maglagay nung globe tattoo to vmware image ung kagaya nung IDM na nakalagay sa vm image

---

### Post by jepong on 2011-02-21
it won't work... i tried it using virtualbox and hindi na ddetect yung huawei modem so no use din... try [WAMMU]("http://en.wikipedia.org/wiki/Wammu"). it works pero it's all trial and error for me kaya i don't really recommend it.

saan mo ba gagamitin? para makapag SUPERSURF? with Globe's [Fair Usage Policy]("http://site.globe.com.ph/broadband/fup?sid=TWH2k8uxpRYAAFSLwkkAAACZe")... parang gusto ko na lang mag wimax or other providers na lang.

---

### Post by Script Warlock on 2011-02-21
eto na lang wammu at the3g-tools(monitoring tools) ang di ko pa nasubukan, ma try nga kung hiyang ba sa meerkat.

@jepong, onli in da pilipins lang ang globe tattoo kung sakaling taga ibang bansa si PaulReaver di gumagamit yan.

---

### Post by jepong on 2011-02-21
may na basa ako KDE application [KMobileTools ]("http://kde-apps.org/content/show.php/KMobileTools?content=15259")kaso hindi pa rin ata ported to Qt4 kaya di ko pa na try. 

Yung UMTSmon mukhang ok kaso tinatamad ako gawing deb yung rpm package using Alien. ;)

---

### Post by Script Warlock on 2011-02-21
> **jepong said:**
> may na basa ako KDE application [KMobileTools ]("http://kde-apps.org/content/show.php/KMobileTools?content=15259")kaso hindi pa rin ata ported to Qt4 kaya di ko pa na try. 

Yung UMTSmon mukhang ok kaso tinatamad ako gawing deb yung rpm package using Alien. ;)

actually yung umtsmon pwede na di compile dretso gamit lang like ./umtsmon, paano ba yan sa kubuntu.. nice tong KMobileTools.

---

### Post by jepong on 2011-02-21
talaga? same as sa ubuntu din naman... sabagay ganyan din yung ginawa ko sa dropbox ko since wala naman version for qt and dolphin.

cge try ko later. ):P

---

### Post by argiebong on 2011-02-21
> **jepong said:**
> it won't work... i tried it using virtualbox and hindi na ddetect yung huawei modem so no use din... try [WAMMU]("http://en.wikipedia.org/wiki/Wammu"). it works pero it's all trial and error for me kaya i don't really recommend it.

saan mo ba gagamitin? para makapag SUPERSURF? with Globe's [Fair Usage Policy]("http://site.globe.com.ph/broadband/fup?sid=TWH2k8uxpRYAAFSLwkkAAACZe")... parang gusto ko na lang mag wimax or other providers na lang.

gusto ko lang magregister ng mga internet promo either globe or sun. kasi as of now nagsesend ako ng message through windows pa. baka kasi may way sa ubuntu. ang gamit ko is Huawei E1550 ata.

---

### Post by jepong on 2011-02-21
hindi pa ba namin nasagot?

---

### Post by argiebong on 2011-02-21
> **jepong said:**
> hindi pa ba namin nasagot?

sinagot ko lang question mo. salamat sa input. etry ko pa yung wammu. mejo nangangapa pa ako eh. Thanks.

---

### Post by jepong on 2011-02-21
I see... i stand corrected. :P

---

