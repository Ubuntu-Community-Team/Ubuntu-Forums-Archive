---
title: "help po, tungkol sa synaptic"
date: 2010-06-13
forum: Philippine Team
---

### Post by t0rp35t on 2010-06-13
help naman po,

hindi po kasi ako maka download ng applications sa pc ko gamit ang synaptic...

lagi po nalabas ay error>

"Got a single header line over 360 chars"

yan po yun laging nalabas...

ano po yun pwde kong gawin, salamat po sa tutulong... :confused::confused:

---

### Post by loell on 2010-06-13
nag-dagdag ka ba ng bagong repository lately?

---

### Post by t0rp35t on 2010-06-13
wala naman akong dinadagdag na repository, kaka install ko lang last week nitong OS
then naka pag download na nga ako ng apps,

pero nun Saturnday, nag eeror na xa at ganyan lagi nalabas until now...

kapag ina update ko naman error pa rin... 

kahit sa apt-get error pa rin...


pa help naman po,

---

### Post by antoniomiguel on 2010-06-14
maaari bang malaman kung anong app ang nadagdag mo na last week, tsaka kung anong app ang gusto mong idagdag na nagkakaroon ka lang lagi ng error

---

### Post by t0rp35t on 2010-06-14
nag download ako sa synaptic ng freemat, xoscope at libpopt yun ang mga last kong download

at nun saturday sana yun gpsim ayun nagloloko na xa... pati yung apt-get...


sya nga po pala ginagamit ko po now ay ubuntu 10.04 LTS...

---

### Post by antoniomiguel on 2010-06-14
try mo nga sa terminal..

sudo apt-get install -f

---

### Post by t0rp35t on 2010-06-14
eto po yun lumabas:

t0rp35t@desktop-ni-AMBO:~$ sudo apt-get install -f
[sudo] password for t0rp35t: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.

---

### Post by antoniomiguel on 2010-06-14
paki-try ulit sa terminal..

sudo apt-get update && sudo apt-get upgrade

note: dapat meron kang internet connection neto ha

---

### Post by t0rp35t on 2010-06-16
salamat po sa pag tulong, alam ko na po yun problem kaya nagloloko yun synaptic...

tungkol lang po sa IP address... thank you po

---

