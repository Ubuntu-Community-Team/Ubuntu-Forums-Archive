---
title: "Internet connection problem"
date: 2011-10-12
forum: Philippine Team
---

### Post by Dyimz on 2011-10-12
Hi there mga bro, I know this is not the right place pero ask ko na din kasi alam ko Mga pro mga Tao dito :)

Nakadual boot po kasi ako ng ubuntu 11.04 at windows 7. Tapos bigla na LNG Nawala ung net ung windows 7 ko. Sabe is currently connected to unidentified network: no Internet access.  Pero pag lumipat ako sa ubuntu nakakasurf naman ako ng net.  Nag try na din ako mag system restore pero ganun pa din.  Ano po kayang reason bak it nagkaganun at ano po Kaya ang pwedeng gawin? Thanks in advance!

---

### Post by Lord Kaiaphas on 2011-10-12
1. *Open* **[COLOR="Blue"]Network and Sharing Center[/COLOR]**

2. *From the Network and Sharing Center window*: Click **[COLOR="blue"]Change Adapter Settings[/COLOR]**

3. *From the Network Connection window*: Right click **[COLOR="blue"]Local Area Connection[/COLOR]** then **[COLOR="blue"]Disable[/COLOR]** and after a few seconds **[COLOR="blue"]Enable[/COLOR]** it.


:guitar: Nice to be back, ayt... apir...

---

### Post by Dyimz on 2011-10-12
Apir tyo bro salamat pero same pa din yung lumalabas e :( di p dn nkkakonek :(

---

### Post by Dyimz on 2011-10-12
Try ko run ung troubleshooting at nareceive ko ung message na to "local area network doesn't have a valid ip configuration. Pano po ba mgkaroon ng valid ip configuration?

---

### Post by Lord Kaiaphas on 2011-10-12
[COLOR="Magenta"]**Question**[/COLOR]:

- What is your ISP?


[COLOR="Magenta"]**Troubleshoot**[/COLOR]:

**[COLOR="Red"]Step One[/COLOR]**
1. Go to **[COLOR="Blue"]Control Panel[/COLOR]**, click [COLOR="blue"]**Internet Options**[/COLOR]

2. *From the Internet Properties window*: click **[COLOR="Blue"]Connections[/COLOR]** tab
[LIST]**[COLOR="Blue"]Dial-up and Virtual Private Network settings[/COLOR]** *box - must be empty, delete any value*[/LIST]
[LIST][COLOR="blue"]**Never dial a connection**[/COLOR] - *should be marked*
[/LIST]
[LIST]click **[COLOR="Blue"]LAN settings[/COLOR]**
[/LIST]
[INDENT][LIST]*From the Local Area Network (LAN) settings window*
[LIST]**[COLOR="Blue"]Automatically detect settings[/COLOR]** must be the only one check box marked[/LIST]
[/LIST][/INDENT]


**[COLOR="red"]Step Two[/COLOR]**
1. Open **[COLOR="Blue"]Network and Sharing Center[/COLOR]**

2. *From the Network and Sharing Center window*: Click **[COLOR="blue"]Change Adapter Settings[/COLOR]**

3. *From the Network Connection window*: Right click **[COLOR="blue"]Local Area Connection[/COLOR]** select **[COLOR="blue"]Properties[/COLOR]**
4. *From the Local Area Connection Properties window*:
[INDENT][LIST]**[COLOR="Blue"]Networking[/COLOR]** tab
[/LIST]
[LIST]Double click **[COLOR="Blue"]Internet Protocol Version 4 (TCP/IPv4)[/COLOR]**
[LIST]*From the Internet Protocol Version 4 (TCP/IPv4) Properties window* **[COLOR="Blue"]General[/COLOR]** tab select[/LIST]
[LIST]**[COLOR="blue"]Obtain an IP address automatically[/COLOR]**[/LIST]
[LIST]**[COLOR="blue"]Obtain DNS server address automatically[/COLOR]**[/LIST]
[/LIST][/INDENT]
[INDENT][LIST]**[COLOR="Blue"]Alternate Configuration[/COLOR]** tab
[/LIST]
[INDENT][LIST]*select* **[COLOR="blue"]Automatic private IP address[/COLOR]**[/LIST][/INDENT]
[/INDENT]


**[COLOR="red"]Step Three[/COLOR]**
1. Open **[COLOR="Blue"]Command Prompt[/COLOR]** (*Start > All Programs > Accessories*)
2. *From the Command Prompt window type*
[INDENT][LIST]**[COLOR="Blue"]ipconfig /release[/COLOR]** and *press enter*[/LIST]
[LIST]**[COLOR="Blue"]ipconfig /renew[/COLOR]** and *press enter*
[/LIST][/INDENT]

---

### Post by Dyimz on 2011-10-13
Bro Maraming salamat. Nag ISP ko is pldt @home

Ito po lumalabas pag ginagawa ko ung steps po : an error occurred while releasing loopback pseudo interface 1: the system cannot find the file specified :(

---

### Post by Lord Kaiaphas on 2011-10-13
Check this [[**[COLOR="Blue"]Link[/COLOR]**]("http://answers.microsoft.com/en-us/windows/forum/windows_vista-networking/an-error-occurred-while-releasing-interface/4261cacb-e924-4d74-a349-4f3b898c27a9")] it may help.

---

### Post by killer_d76 on 2011-10-13
Can you connect to internet using Ubuntu?..if so, you may also want to try disabling your Anti-virus Software ;)

---

### Post by Dyimz on 2011-10-13
> **Lord Kaiaphas said:**
> Check this [[**[COLOR="Blue"]Link[/COLOR]**]("http://answers.microsoft.com/en-us/windows/forum/windows_vista-networking/an-error-occurred-while-releasing-interface/4261cacb-e924-4d74-a349-4f3b898c27a9")] it may help.

Ginawa ko n rin po kaso same issue pa din po :(

---

### Post by Dyimz on 2011-10-13
> **killer_d76 said:**
> Can you connect to internet using Ubuntu?..if so, you may also want to try disabling your Anti-virus Software ;)

Natry ko din po kaso same pa din. Oh well, siguro stick muna ako sa ubuntu. Tutal iTunes LNG ang habol ko sa windows :)

---

### Post by Lord Kaiaphas on 2011-10-14
Can you give me screen-shots of your Windows 7:

[LIST]
[*][COLOR="Blue"]**Network and Sharing Center**[/COLOR]
[*] [COLOR="Blue"]**Network Connection**[/COLOR] (*Network and Sharing center > Change adapter settings*)
[*] **[COLOR="Blue"]Local Area Connection properties[/COLOR]** or [COLOR="Blue"]**Connection details**[/COLOR]
[/LIST]

Also you are using PLDT, AFAIK it is a PPoE connection... Does it require a User-name and Password?

---

### Post by Dyimz on 2011-10-19
Hi Sir,

PLDT internet @home po yung connection ko.  parang router/modem po siya, tas pag kinabit po sa PC, automatic na po na magkakaroon ng internet connection.

Sir, ito nga pala yung screen shot. sinama ko na rin po yung mga errors na nakikita ko pag nattroubleshoot.  thanks!

Maraming salamat :)

---

### Post by pinoyskull on 2011-10-19
Have you tried **Windows Network Diagnostic**?

---

### Post by Lord Kaiaphas on 2011-10-23
Hi,

Have you tried resetting to factory defaults your modem?

---

### Post by cris@smp.com.ph on 2011-10-25
Bro try mo kunin yung configuration ng IP sa ubuntu tapos yun yung gamitin mo sa window7 ifconfig lang yan...

---

### Post by JCyberinux on 2011-10-28
What does the PLDT said to your internet connection, it seems wala ka raw default gateway and also the network can be detected but not totally connected. :D 

first question, modem/router ba sya? - kung yes, ibig sabihin it has a configuration like PPOE configuration like username and password, etc... :D

can you access your own modem/router? like administration.

did you tried another pc or laptop in that case, para ma-test yung connection.

hmm... so both ubuntu and windows ba wala internet connection? - gumana pala sa ubuntu :D

(if everything fails, i think you should call PLDT baka sa kanila mismo yung may problema..) :D - ito gawin mo logon ka sa ubuntu brad, then from there go to terminal, type mo ifconfig... tapos kopyahin mo lahat ng internet / network configuration...

then boot ka ulit sa windows, tapos from network connection, then network adapter mo, right-click and properties, tapos dun sa internet protocol tcp/ip properties mo, type or ilagay mo yung exact information nandun sa ubuntu ifconfig mo. :D then see the results.

---

### Post by Dyimz on 2011-12-15
hi mga sir..salamat sa pag reply...naayos na din yung connection ko..pasensya na ulit sa bala..long live ubuntu! :D

---

