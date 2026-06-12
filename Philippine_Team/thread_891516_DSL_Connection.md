---
title: "DSL Connection"
date: 2008-08-16
forum: Philippine Team
---

### Post by initial_m on 2008-08-16
sana matulungan nyo ko, kasi may prob ako sa connection ko, everytime na mag start ako ng pc/restart minsan naka connect ung wired network ko sa dalawang connection: ppp0 saka ppp1, naguguluhan ako, nanghula lang kasi ko nung setup ko ung dsl. dati kasi my router tapus kinuha na sakin, direct nako, tapus un, kung anu anu na ginawa ko, di ko na lam, minsan disconnected sya, tapus nag karoon ako ng dial up connection options sa network ko pag click ko ung icon nka wired pero sa baba meron dial-up connections.
di ko lam gagawin ko kasi minsan hassle ayaw mag connect, sa dialup connections ako pupunta tapus my mga options dun tulad ng connect to ppp0 via modem, meron ding connect via dsl-provider.. pls guys help me.. tnx:confused:

---

### Post by loell on 2008-08-16
gumamit ka ba nang **pppoeconf**?

---

### Post by initial_m on 2008-08-16
yup, di ko na nga lam panu mawala ung mga dial up connections tapus lagi pa na didisconect net ko then mag coconect ung ppp1 instead of ppp0..:confused:

---

### Post by ch1c0dj on 2008-08-16
ano internet connection provider mo? smart bro? pldt dsl? globe broadband? digitel netvantage?

---

### Post by initial_m on 2008-08-16
> **chicodj said:**
> ano internet connection provider mo? smart bro? pldt dsl? globe broadband? digitel netvantage?

Bayantel bro BayanDSL:( hassle talga bro eh

---

### Post by ch1c0dj on 2008-08-16
ano modem or router gamit mo? ung brand or model name nya ano?

---

### Post by initial_m on 2008-08-16
> **chicodj said:**
> ano modem or router gamit mo? ung brand or model name nya ano?

naka ADSL Modem bro.
Brand: HUAWEI 
model: SmartAX MT880

---

### Post by ch1c0dj on 2008-08-16
Modem router yan, dapat pre-configure na yan ng BayanTel eh, at hindi mo na kailangan pang mag dial, pwede mo ba disable muna ung dialup connection (point to point connection) mo,

go to System-Administration-Network

**Other Option**
meron ako na search check mo ito baka makatulong [http://www.pinoydsl.net/viewtopic.php?t=4803](http://www.pinoydsl.net/viewtopic.php?t=4803)

No need no modify the modem config settings if tama naman ung naka set.
> Disconnect the broadband connection that the installer configured on your computer (probably a built-in PPPoE client). Just remember your username and password by writing it down on a piece of paper.

You should set your pc to have the following:

ip address: 192.168.1.100
subnet mask: 255.255.255.0
default gateway: 192.168.1.1

Open a web browser and on the address bar type:

[http://192.168.1.1](http://192.168.1.1)

When asked for a login, the username is "admin" and the password is also "admin" (w/o the quotes, of course).

On the page, expand the "Basic" area on the sidebar by clicking on the plus sign.

Click on "WAN Settings" then click on the pencil at the PVC-0 row.

Your settings should be the following:

VPI/VCI: 0/33
Mode: PPPoE
IGMP: Disable
Service Name: BayanDSL
username: <please type the username that you wrote down a while ago>
password: <please type the password that you wrote down a while ago>

Click the "Submit" button at the bottom.

Expand the "Tools" area in the sidebar and and choose "Save & Reboot".

Choose the "Reboot" option and wait until the modem re-initializes itself.

++ You may choose to change all the other settings on the router such as turning on the DHCP server option and all the other NAT niceties so long as you know what your doing. ++

Other Option 
try mo kung sa Live CD kung ganun parin ung na e-encounter mo na di-disconnect pa rin,

---

### Post by initial_m on 2008-08-16
o nga eh, pati sa windows nag didial pako ng dialer di sya automatic pag open ko ng pc, after nun sir what are the things i need to do.?

---

### Post by ch1c0dj on 2008-08-16
Follow mo ung edited na reply ko, dun sa instruction nya, un na ung katumbas ng Dialer, bale un Modem router na ung mag dada-dial para syo, automatic naman un eh, nun nasa isp support ako na ganyan gamit namin kaya hindi na kami nag install pa ng PPPOE client software para nag dial, applicable din dapat yan sa BayanTel using modem router basta tama ung settings,

more info sa modem na gamit mo Huawei MT880 modem/router: [http://www.huawei.com/products/terminal/products/view.do?id=87](http://www.huawei.com/products/terminal/products/view.do?id=87)

ito ung importante setting dyan eh,

VPI/VCI: 0/33
Mode: PPPoE
IGMP: Disable
Service Name: BayanDSL(kahit ano name nito mas ok kung descriptive)
username:
password:

Kung may makita ka na "Idle Time Out" set mo at may value sya, pwede mo i-set sa 0(zero) para hindi sya na di-disconnect kung wala internet activity ung modem router.

---

### Post by initial_m on 2008-08-16
tnx chicodj, pero bro panu ung mga settings na andito sakin ngyn, i mean ung mga dialup connections di ko lam panu mawawala eh, dati wala naman un,.di ko padin ma gets panu ko mag start.. hehehe..

EDITED: panu ko pala gagawin ung instructions bro, dito sa UBuntu? tnx

---

### Post by ch1c0dj on 2008-08-16
pareho lang din sa Windows yan eh, kasi ung settings eh nasa modem router mo na kung susundin mo ung Quoted Instruction [.]("http://ubuntuforums.org/showthread.php?t=421288") [.]("http://tek4dpipol.blogspot.com/2008/02/connecting-ubuntu-to-adsl-bayantel.html") [.]("https://help.ubuntu.com/community/ADSLPPPoE") [.]("http://broadbandforum.in/bsnl-broadband/8182-bsnl-dataone-configuring-adsl-connection-linux/") [.]("http://broadbandrouterconfiguration.blogspot.com/2006/05/type-i-modem-configuration-huawei.html")

open mo Terminal
type mo ifconfig
ano ung ip address? o un value ng "inet addr"?

---

### Post by initial_m on 2008-08-16
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:121.96.111.98 

- yan bro

---

### Post by ch1c0dj on 2008-08-16
sorry di ko na specify eh, yung eth0 ano ung ip address/inet addr?

---

### Post by initial_m on 2008-08-16
eth0:avahi Link encap:Ethernet  HWaddr 00:19:db:c0:fd:64  
          inet addr:169.254.9.248 

-yan bro baka may mang hack na skin nyan, hehehe...

---

### Post by ch1c0dj on 2008-08-16
hmmm?, dhcp disabled ung modem router mo?,
pwede mo open [http://192.168.1.1](http://192.168.1.1) try lng baka ito ung ip add nya, yan kasi ung default ip address ng HUAWEI SmartAX MT880 modem router mo eh, pero baka iba ginawa config ng BayanTel, pinahirap nila buhay ng client nila sa ginawa nila na dapat gumamit pa ng Dialer to connect.

---

### Post by initial_m on 2008-08-16
di ko pa disabled, kasi diba nag uusap pa tyo dito forums.
try ko open ung ip na un ung link na bingay mo pero error cannot connect to remote server.. :(

---

### Post by ch1c0dj on 2008-08-16
ok, hindi mo sya ma open kasi magka iba ip class ung modem router at lancard/ethernet card pc mo.
ppaano ka ba mag connect sa internet? automatic na ba pag nag boot sya nag dial na ung pppoeconf?

[COLOR="blue"]alam mo ang pinaka madali nyan i-reset mo ung config ng modem router mo eh, then sundan mo ung qouted instruction sa mga unang reply ko, o link na ito [http://www.pinoydsl.net/viewtopic.php?t=4803](http://www.pinoydsl.net/viewtopic.php?t=4803),

kaso **wag na muna** kasi madi-disconnect ka sa internet at saka baka hindi mo ma set ng tama, magka problem pa lalo, pero iyon talaga ung pinaka madali paraan sa internet connection setup mo na hindi ka na gagamit pa ng dialer na pppoeconf o another router para mag connect sa internet[/COLOR]

as of now pwede mo i-try instruction dito sa link para mapadali un pag-dial/connect mo, >  [http://ubuntuforums.org/showthread.php?t=421288](http://ubuntuforums.org/showthread.php?t=421288)
ang gagawin lang nito is ii-enable nya ung GUI ng pppoeconf
> sudo apt-get install xdialog

anyway paki answer narin po ung mga questions ko para mas clear din po sa akin kung paano ung setup mo, oki po, thanks

---

### Post by killer_d76 on 2008-08-16
try ko lang help din.. thru windows (if you are still on dual-boot) click start> run> cmd> this will open up command prompt, tapos type mo ```
ipconfig
``` then click [COLOR="black"][COLOR="Red"]enter[/COLOR][/COLOR] look for default gateway, open up a browser (IE,Opera or FireFox etal), clear mo yung address bar, tapos type mo yung default gateway, this will open up your modem configuration page, hope this help bro.

---

### Post by initial_m on 2008-08-17
thanks sa help, anyways sa windows ko na lang cguro babaguhin, kaso naiinis ako dito sa ubuntu ko, kasi gusto ko matangal ung mga dial up connections na nadagdag dahil nag pppoeconf ako dati nung direct nako nag coconnect, kakainis, sisi ako..:(

@chicodj
-nag aautomatic dial na sya bro, kaya lang ung prob ko kasi nag oopen ng ppp1 imbis na ppp0, lumalabas na dalawa ung settings, kasi i remember 2-3 times ata ako ng pppoeconf. Then my times din na nag load pako ng **sudo pon dsl-provider**, kaya cguro nagkagulogulo...:mad:

-sana matulungan nyo ko mga bros..:confused:

---

