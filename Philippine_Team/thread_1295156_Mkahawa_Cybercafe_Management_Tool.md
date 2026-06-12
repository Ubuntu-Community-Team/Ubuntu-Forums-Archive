---
title: "Mkahawa Cybercafe Management Tool"
date: 2009-10-19
forum: Philippine Team
---

### Post by Script Warlock on 2009-10-19
a new forked cclfox cybercafe timer is now available for download in sourceforge..
"howto" coming up.....

Update 6/10/2016: Repo has been moved to: [https://github.com/scriptwarlock/nordseye](https://github.com/scriptwarlock/nordseye)

---

### Post by dodimar on 2009-10-19
> **Script Warlock said:**
> a new forked cclfox cybercafe timer is now available for download in [sourceforge]("http://sourceforge.net/projects/mkahawa/") ..
"howto" coming up.....

:)

Boss, question, is this cross platform (XP and Linux)...?

---

### Post by Edgar Ilaga on 2009-10-19
Interesting piece of software. I tried to compile it on Ubuntu 9.04 this morning, but after resolving dependencies (or so I think... I'm using libccls-0.7.0 and from what I've read 0.7.2 is floating somewhere around the web) I got this error from my *make* step:

Making all in m4
make[1]: Entering directory `/home/edgar/Desktop/mkahawa-srv-0.0.1/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/edgar/Desktop/mkahawa-srv-0.0.1/m4'
Making all in src
make[1]: Entering directory `/home/edgar/Desktop/mkahawa-srv-0.0.1/src'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"cclfox\" -DVERSION=\"0.7.2\" -DENABLE_NLS=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DHAVE_LIBFOX_1_6=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBCCLS=1 -I. -I. -I/usr/local/include    -g -O2 -MT CCLWin.o -MD -MP -MF ".deps/CCLWin.Tpo" -c -o CCLWin.o CCLWin.cpp; \
    then mv -f ".deps/CCLWin.Tpo" ".deps/CCLWin.Po"; else rm -f ".deps/CCLWin.Tpo"; exit 1; fi
CCLWin.cpp:48: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp: In constructor ‘CCLWin::CCLWin(FX::FXApp*)’:
CCLWin.cpp:238: error: ‘CCL_INACTIVE’ was not declared in this scope
CCLWin.cpp:239: error: ‘CCL_ACTIVE’ was not declared in this scope
CCLWin.cpp:240: error: ‘CCL_PAUSED’ was not declared in this scope
CCLWin.cpp: In member function ‘virtual void CCLWin::create()’:
CCLWin.cpp:427: error: ‘CCL_INACTIVE’ was not declared in this scope
CCLWin.cpp:428: error: ‘CCL_ACTIVE’ was not declared in this scope
CCLWin.cpp:429: error: ‘CCL_PAUSED’ was not declared in this scope
CCLWin.cpp: In member function ‘void CCLWin::setAllClientMember(int)’:
CCLWin.cpp:528: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp: In member function ‘void CCLWin::setClientMember(int)’:
CCLWin.cpp:553: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:557: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp: In member function ‘FX::FXbool CCLWin::auth(int, FX::FXuchar*)’:
CCLWin.cpp:614: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp: In member function ‘FX::FXbool CCLWin::authemp(FX::FXuchar*, FX::FXuchar*)’:
CCLWin.cpp:647: error: ‘CCL_DATA_EMPLOYEE’ was not declared in this scope
CCLWin.cpp:647: error: ‘CCL_data_find_by_key_sval’ was not declared in this scope
CCLWin.cpp:676: error: ‘CCL_employee_exists’ was not declared in this scope
CCLWin.cpp:679: error: ‘CCL_employee_info_get’ was not declared in this scope
CCLWin.cpp: In function ‘FX::FXbool authemp2(FX::FXuchar*, FX::FXuchar*)’:
CCLWin.cpp:706: error: ‘CCL_employee_validate’ was not declared in this scope
CCLWin.cpp:710: error: ‘CCL_employee_info_get’ was not declared in this scope
CCLWin.cpp: In member function ‘uint CCLWin::getPageCount(char*, int*)’:
CCLWin.cpp:803: error: ‘CCL_client_ip_get’ was not declared in this scope
CCLWin.cpp:813: error: ‘CCL_client_ip_get’ was not declared in this scope
CCLWin.cpp: In function ‘void onEventCallback(int, FX::FXuint, void*, FX::FXuint, void*)’:
CCLWin.cpp:882: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp:895: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:899: error: ‘CCL_member_credit_set’ was not declared in this scope
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:927: error: at this point in file
CCLWin.cpp:934: error: ‘CCL_member_credit_set’ was not declared in this scope
CCLWin.cpp:957: error: ‘CCL_ACTIVE’ was not declared in this scope
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:963: error: at this point in file
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:969: error: at this point in file
CCLWin.cpp:971: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:973: error: ‘CCL_member_credit_set’ was not declared in this scope
CCLWin.cpp:994: error: ‘CCL_PAUSED’ was not declared in this scope
CCLWin.cpp:1009: error: ‘CCL_ntohl’ was not declared in this scope
CCLWin.cpp:1018: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp:1018: error: ‘CCL_data_find_by_key_sval’ was not declared in this scope
CCLWin.cpp:1032: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:1040: error: ‘CCL_PAUSED’ was not declared in this scope
CCLWin.cpp:1056: warning: format not a string literal and no format arguments
CCLWin.cpp:1103: error: ‘CCL_product_id_get’ was not declared in this scope
CCLWin.cpp:1104: error: ‘CCL_product_flags_get’ was not declared in this scope
CCLWin.cpp:1104: error: ‘CCL_DELETEDPRODUCT’ was not declared in this scope
CCLWin.cpp:1107: error: ‘CCL_INACTIVE’ was not declared in this scope
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:1119: error: at this point in file
CCLWin.cpp:1174: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp:1199: error: ‘CCL_ntohl’ was not declared in this scope
CCLWin.cpp:1235: warning: format not a string literal and no format arguments
CCLWin.cpp:1249: warning: format not a string literal and no format arguments
CCLWin.cpp: In function ‘void updateClientStatus(int)’:
CCLWin.cpp:1258: error: ‘CCL_ACTIVE’ was not declared in this scope
CCLWin.cpp:1264: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp:1274: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:1289: error: ‘CCL_DATA_MEMBER’ was not declared in this scope
CCLWin.cpp:1304: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::unBlockClient(int)’:
CCLWin.cpp:1341: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::blockClient(int)’:
CCLWin.cpp:1354: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::getUpdateFileName(char*, int*)’:
CCLWin.cpp:1368: error: ‘CCL_DATA_NONE’ was not declared in this scope
CCLWin.cpp: In member function ‘int CCLWin::startUpdateClient(int, char*)’:
CCLWin.cpp:1441: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp:1450: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp: In member function ‘long int CCLWin::updateClient(int)’:
CCLWin.cpp:1487: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp:1493: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp:1505: error: ‘CCL_ACTIVE’ was not declared in this scope
CCLWin.cpp:1512: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp:1520: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp:1542: warning: deprecated conversion from string constant to ‘char*’
CCLWin.cpp: In member function ‘long int CCLWin::setAllClientPass()’:
CCLWin.cpp:1579: error: ‘CCL_DATA_NONE’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onCommand(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1633: error: ‘CCL_PAUSED’ was not declared in this scope
CCLWin.cpp:1644: error: ‘CCL_ACTIVE’ was not declared in this scope
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:1657: error: at this point in file
CCLWin.cpp:1659: error: ‘CCL_member_credit_get’ was not declared in this scope
CCLWin.cpp:1661: error: ‘CCL_member_credit_set’ was not declared in this scope
/usr/local/include/ccls.h:244: error: too many arguments to function ‘int CCL_log_session(int, int, unsigned int)’
CCLWin.cpp:1666: error: at this point in file
CCLWin.cpp:1680: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp:1682: error: ‘CCL_INACTIVE’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onTime(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1811: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onAllowUserLogin(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1846: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onEnableAssist(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1863: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onEnableAllAssist(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1911: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::onAllowMemberLogin(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:1947: error: ‘CCL_htonl’ was not declared in this scope
CCLWin.cpp: In member function ‘void CCLWin::updateClientIcon(int)’:
CCLWin.cpp:2297: error: ‘CCL_ACTIVE’ was not declared in this scope
CCLWin.cpp: In member function ‘FX::FXbool CCLWin::employeeLogin(FX::FXObject*, FX::FXSelector, void*)’:
CCLWin.cpp:2412: error: ‘CCL_employee_name_get’ was not declared in this scope
CCLWin.cpp: In member function ‘long int CCLWin::sendUpdateChunk(int, long int)’:
CCLWin.cpp:2534: warning: deprecated conversion from string constant to ‘char*’
make[1]: *** [CCLWin.o] Error 1
make[1]: Leaving directory `/home/edgar/Desktop/mkahawa-srv-0.0.1/src'
make: *** [all-recursive] Error 1

Any helpful words of advice? Thanks!

---

### Post by Script Warlock on 2009-10-19
ay sorry di pa pala narelease ang deb installer, may inayos pa kc kagabi ang bug sa feature na "update client"...ako na muna bigay ng link para di na tayo magcompile... 

[mkahawa]("http://www.mediafire.com/file/3vygywjytym/mkahawa.tar.bz2")
[pem]("http://www.mediafire.com/?t2w5azgwtmi")  certificate
for winxp client(locked)   - this is an older version pero usable pa rin kaya kung sino may mga previous cclfox clients pwede to magamit with mkahawa minus some features lang like messaging and something else.


[COLOR=Red]client[/COLOR] is a xplatform and at the end of the month baka available na for win7...

@edgar ilaga, ang error kc nyan yung libccls mo dapat naka libccls-0.8.0 cge lang pm ko co-author about the issue baka nakalimutan lang nya upload sa sourceforge...

but if you really like to compile/change some lines then install via svn nasa sourceforge lang yan

---

### Post by Edgar Ilaga on 2009-10-21
Thanks for uploading all the files! I just want to note a minor correction in the pem shell script that you uploaded. In the file, the last instruction reads as such:

Copy cert.pem and CA.pem to ~/.cclfox on the server and to ~/.cclcfox on the clients

I think that ~/.cclfox should be ~/.mkahawa in this case. I tried the former first as per terminal output, pero di siya gumana. So I tried using the latter directory as per the instructions included in the source code, and it worked.

Otherwise, things are working out fine on my Ubuntu 9.04 and Karmic installs. I'll let you know if something comes up!

---

### Post by Script Warlock on 2009-10-21
yeah your right sorry for that...that pem actually galing talaga yan sa ccl, ang importante lang dyan ay yung tatlong file na ma-generate nya. simply change the permission sa properties ng pem "allow executing file as program" sa properties nyan tapos double click then run. at may lalabas na tatlong file na yun na ang ilagay mo sa .mkahawa folder. halos parehas lang ang procedure ng ccl at mkahawa but this time no more compilation kc may deb installer na.
kinulang talaga ako sa oras para sa howto ng mkahawa, dami pa kc skeds

note: tinanggal ko muna link for winxp kc may ginawang bago na parehas na rin sa features ng mkahawa client..

oi na upload na pala mga files sa sourceforge...

---

### Post by Samhain13 on 2009-10-23
Uy, local OSS project? Nice! Pagpalain sana kayo lalo. :guitar:

---

### Post by jaceleon on 2009-10-23
Guys, libre to? Saka pwede ba server ang Ubuntu Karmic Koala at clients ang XP?

Looks like it's a great software! Pang-internet cafe na ang Ubuntu! Nice!

at ano po yung CCL?

Telling the truth parang gusto ko na to iimplement kasi sa cafe na pinagbabantayan ko, more Advertisement for Linux Ubuntu to pag successful ang pagkakabuild sa Mkahawa Cybercafe Management Tool. Pero eto ang concerns ko po.

1. My boss is a loyalistang Windows XP user, though she can be bent to anything I advise, for the greater good. Madadalian kaya gamitin ito ng mga no-idea-what-in-the-name-of-heavens-is-Ubuntu type of people?

2. Free po ba ito? Please say yes!:mrgreen:

3. Ano po ang mga file dependecies nito, I mean like sa Cafe Manila, they need pa ng VB Runtimes, eto naman e ano?:confused:

4. As already asked, mataas po ba ang compatibility nito with a XP client? I mean, syempre kailangan kong XP yung mga gaming PCs ano po?

5. Installable po ba ang MS Word, Excel at Powerpoint 2007 sa Ubuntu Karmic Koala na gagawing server?

6. System requirements po ng Mkahawa, ano po?:confused:

7. Ano po ang maximum number ng clients nito?:P

Pasensya na po! Matanong lang po ako! More power po, bai!:popcorn:

---

### Post by Script Warlock on 2009-10-23
for ubuntu/linux yes it's free and unlimited machine........pls pm me about the details how to get a pack of this timer with ubuntu/linux. winxp and win7......linux walang problema libre na toh to the max!!!

pwede to install sa ubuntu 9.10 at pwede rin xp clients mo...

to answer your tanong:
1. ubuntu is now a user friendly and mkahawa is so simple to use na para ka lang naagpaandarng ipod na merong stop, pause play, continue, block timer, send message to the client, swap, etc...demo mo lang sa boss mo ang ubuntu and how it works and what advantages nito kung gagamitin as a server OS ng icafe nyo.
2. nasagot ko na po yan.
3. n da bigining .... [ccl]("http://ccl.sourceforge.net/")
     sqlite at glib
4. it is a x-platform cyber manager that runs on M$, linux and MacOsx
5. instalalabol - gamit ka lang wine or crossover
6. good for linux lang ang server pero clients are cross platform
7. unlimited....once ka lang kumuha ng mkahawa at sayo na yan habangbuhay...
8. kah kah kah...nasagot ko ba tanong mo ng tama?:-s

---

### Post by jaceleon on 2009-10-23
Hi po sir!

ndi ako makapagpm! ndi ko alam how, like noob ako sa foruming e....

Interested po ako dito! Paano po kasi, isa po akong bantay sa shop/manager/technician sa shop na pinapasukan ko. Nakastay-in ako dito at 7 months na.

Lahat ng computer ko dito e TinyXP. Ang boss ko ay M$ loyalist, pero naatract naman siya sa Ubuntu. Let's say na noobie ang kanyang level sa computing. Ilan beses ko na nabanggit ang Ubuntu sa kanya, pero like many others, takot siyang mag migrate sa Ubuntu dahil nga wala siyang idea.

Pero I'll change that! kung ako nga lang e, wish kong maging Ubuntu ang official OS ng cafe namin. Pero since games work only on XP, so needed ko talaga po if clients are XP, while I like our server to be Ubuntu, because of it's non-virii feature, aside from the fact na ambilis nito, as in! saka kaya nga rin nito patakbuhin ung isa sa fave games ko (Valkyrie Profile Tag on WINE).

So balik po tayo sa topic. Can I get the server and clients version of Mkahawa Cafe Management Tool? Pakisalihan po sana ng readme na madali lang maintindihan ng noobies like my boss, kasi ang gusto niya yung pag wala ako e kaya niyang mag-ayos on her own. Ayaw niyang maiwan na totally clueless sa isang bagong system. 1 month nga bago siya naging confident sa Cafe Manila, pero of course, illegal....

So let's make it Ubuntu! Saka ang galing nio po? how in the name of heavens nacreate to? Pero nonetheless, pde po kaya na matesting ko ito?

Ay opo nga pala! May way po ba na static po yung client IP para rito? saka may wallpaper mode siya pag walang gumagamit or nalock na yung pc dahil time na?

Meron din po ba tayong repo para sa printer drivers? Ngayon nga e, dugu-dugo na ang brain ko dahil pinag-aaralan ko ang mag-extract and install ng tarball! Pero may source po ba tayo nito. Brother po ang brand ng printer namin. saka paano yun? Wine ang M$ office 2k7, pero magprint sa isang linux-based printer? ay dami ko pang pag-aaralan!

thanks in advance. Sorry sa sobrang kadaldalan, este, sa sobrang haba ng text na ito. I'll experiment the server with my Karmic test computer.

---

### Post by Script Warlock on 2009-10-23
clik mo lang users id namin tapos may magpop  na options nandun ang "send a private message to.."...

---

### Post by Edgar Ilaga on 2009-10-27
Status update:

So far, nasubukan ko na yung server and client programs on a pure Ubuntu 9.04 setup, and I'm pretty happy with what I've been seeing for the past few days. Any chance for the Windows client binary coming out, or pwede ko bang i-compile na lang yung client source code via MinGW? (Haven't tried it yet, since sobrang busy ako ngayon sa mga RL affairs.) I want to try out the Windows-Ubuntu cross-compatibility thing asap.

---

### Post by Script Warlock on 2009-10-27
basta wala lang aberya may mkahawa client na for winxp..

---

### Post by Edgar Ilaga on 2009-10-27
> **Script Warlock said:**
> basta wala lang aberya may windows xp edition na ang mkahawa client.....

Okay, nawala ako dun ah. :( Di pa released bale yung mga Windows clients pending testing?

---

### Post by Script Warlock on 2009-10-27
release na sana kaso nagkaproblema sa dll, multi threading at messaging kaya hold muna....

---

### Post by torabian02 on 2009-11-01
I installed Mkahawa on 9.10

The client is good and I like the staff login changes.

Only trouble is there is no database if I go into sqlite3 command line. I am getting lots of CCL_client_owed_terminal: assertion 'c' failed messages (related to the fact it cannot write to a database I assume). 

Anyone any idea why the database problem? I think I got all the dependencies right :(

---

### Post by Script Warlock on 2009-11-01
have you tried sqlite browser? db is located inside the .mkahawa folder in your home folder...

---

### Post by princessmarisa on 2010-02-11
I really hope this thread isn't dead I need some help!


Using Mkahawa as part of a University Project


Few questions (silly things I can't get to work)


**How do you change the lock pic/blocker image?**


I have tried putting a file called lockpix.gif or just lockpix in the clients mkahawa-client directory and no luck

I have tried in the .mkahawa folder on the server also no luck

also the only mkahawa folder I can find on the client is

**/usr/share/doc/mkahawa-client**

is this correct?




on the server is it in

**/home/cafeserver/.mkahawa**

where cafeserver is my user for ubuntu


Really new to ubuntu here as well, so any help on these issues would be great! Can I just say this thread so far has been really helpful in getting it to install and run in the first place!

also when i click to enter the client session from the lock screen, there is no option to select a username and login.. is there meant to be... bit confused how to link users to terminals.

---

### Post by Script Warlock on 2010-02-11
kinda busy on my recent work at level8 restobar so i have little time writing the "howtos" of mkahawa, sorry for that.

---

### Post by princessmarisa on 2010-02-12
> **Script Warlock said:**
> kinda busy on my recent work at level8 restobar so i have little time writing the "howtos" of mkahawa, sorry for that.

thanks for replying anyway, good luck at work. :D

If you get any time to answer any of my questions it would really help.

(might be revelant when installing client deb i get 

*start runlevel arguments (4 5_ do no match LSB Default-Start values)* errors

Thanks

---

### Post by Script Warlock on 2010-02-12
> **princessmarisa said:**
> I really hope this thread isn't dead I need some help!


Using Mkahawa as part of a University Project


Few questions (silly things I can't get to work)


**How do you change the lock pic/blocker image?**


I have tried putting a file called lockpix.gif or just lockpix in the clients mkahawa-client directory and no luck

I have tried in the .mkahawa folder on the server also no luck

also the only mkahawa folder I can find on the client is

**/usr/share/doc/mkahawa-client**

is this correct?




on the server is it in

**/home/cafeserver/.mkahawa**

where cafeserver is my user for ubuntu


Really new to ubuntu here as well, so any help on these issues would be great! Can I just say this thread so far has been really helpful in getting it to install and run in the first place!

also when i click to enter the client session from the lock screen, there is no option to select a username and login.. is there meant to be... bit confused how to link users to terminals.

--->fixing the lockpix is almost complete dont worry for that we put some new things on lockpix, like the slideshow thing.

--->yes the location is in the right place..

--->hitting the enter button will pop-up the login screen must first register some username at the members tab of mkahawa server and the password is usually the members id.

---

### Post by princessmarisa on 2010-02-14
> **Script Warlock said:**
> --->fixing the lockpix is almost complete dont worry for that we put some new things on lockpix, like the slideshow thing.

--->yes the location is in the right place..

--->hitting the enter button will pop-up the login screen must first register some username at the members tab of mkahawa server and the password is usually the members id.

thanks 

do the *start runlevel arguments (4 5_ do no match LSB Default-Start values)* errors when installing client deb not matter then?

---

### Post by h00man1 on 2010-02-15
perhaps we should ask some people to get the program into the ubuntu repositories, it seems to work well enough by now

---

### Post by Script Warlock on 2010-02-16
yes this icafe software has a future but first lets support him in anyway we can, can reach him at mkahawa site(sourceforge). 

throw your feature request and if you would like to help coding please do so we need more coding artist for mkahawa:D.... this is just a c++ and the source code is available via svn.

---

### Post by princessmarisa on 2010-02-19
When I try to configure and make the client package I get

checking for fxfindfox in -lFOX-1.6... no
configure: error: please install fox 1.6

errors

latest version of libfox1.6 and libfox dev are both installed.

Running the latest version of ubuntu

(if you need any more info please tell me I'm new and trying to learn here)

Thanks

---

### Post by Script Warlock on 2010-02-19
> **princessmarisa said:**
> When I try to configure and make the client package I get

checking for fxfindfox in -lFOX-1.6... no
configure: error: please install fox 1.6

errors

latest version of libfox1.6 and libfox dev are both installed.

Running the latest version of ubuntu

(if you need any more info please tell me I'm new and trying to learn here)

Thanks

try to type sudo ldconfig then proceed

---

### Post by princessmarisa on 2010-02-19
I fixed my problems

Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include

as it was looking for them only in usr/local/lib and usr/local/include

also added -prefix='/usr' to install it where I wanted it



However I still cannot get a login screen to appear
the lock screen says unwiretechnologies.net (the install from deb just says mkahawa) and click to begin

when you press enter key nothing happens, when you click it just starts the session, not a login screen even though I added users in the server programme.

---

### Post by Script Warlock on 2010-02-19
> **princessmarisa said:**
> I fixed my problems

Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include

as it was looking for them only in usr/local/lib and usr/local/include

also added -prefix='/usr' to install it where I wanted it



However I still cannot get a login screen to appear
the lock screen says unwiretechnologies.net (the install from deb just says mkahawa) and click to begin

when you press enter key nothing happens, when you click it just starts the session, not a login screen even though I added users in the server programme.

does mkahawa client autolocks the desktop when launched?

---

### Post by masdjo on 2010-02-20
I have used CCL for 2 years, and this afternoon I found mkahawa and I have tried to install on the server. But when I try to run mkahawa, the staff login window appear .
What username and password?
Thanks :)

---

### Post by Script Warlock on 2010-02-20
user: admin 
paswd: admin

---

### Post by aweblab on 2010-02-21
Athlon 64 x2 AMD not supported?! kc try ko e install i got architecture error.:(

---

### Post by Script Warlock on 2010-02-21
> **aweblab said:**
> Athlon 64 x2 AMD not supported?! kc try ko e install i got architecture error.:(

timer pang 32bit pa lang if your talking about mkahawa.

---

### Post by Script Warlock on 2010-02-27
in a few days the latest mkahawa (former cclfox) will be available for download... sino interesado punta lang po kayo sa mkahawa.sourceforge.net libre wala pong bayad para sa mga ubuntu/linux users. 

some of the screenshots:
[http://img193.imageshack.us/img193/5913/addingastaff.png](http://img193.imageshack.us/img193/5913/addingastaff.png)
[http://img193.imageshack.us/img193/9300/loginbyticket.png](http://img193.imageshack.us/img193/9300/loginbyticket.png)
[http://img190.imageshack.us/img190/2151/mkahawaservere.png](http://img190.imageshack.us/img190/2151/mkahawaservere.png)
[http://img714.imageshack.us/img714/739/reportd.png](http://img714.imageshack.us/img714/739/reportd.png)
[http://img130.imageshack.us/img130/3427/tariff.png](http://img130.imageshack.us/img130/3427/tariff.png)
[http://img256.imageshack.us/img256/7978/ticketsjj.png](http://img256.imageshack.us/img256/7978/ticketsjj.png)

---

### Post by utux_utux on 2010-03-02
hi guys.. 

i want to asking about Mkahawa.. im new on ubuntu 9.10 and use .deb package to install it. installation & dependencies are completed.. but i didt find the program to launch it.
when i type mkahawa @ terminal it says: [E]File "cert.pem" not found!!

so what should i do?  :confused: 

some help please ? 

thx before..

---

### Post by Script Warlock on 2010-03-02
> **utux_utux said:**
> hi guys.. 

i want to asking about Mkahawa.. im new on ubuntu 9.10 and use .deb package to install it. installation & dependencies are completed.. but i didt find the program to launch it.
when i type mkahawa @ terminal it says: [E]File "cert.pem" not found!!

so what should i do?  :confused: 

some help please ? 

thx before..

mkahawa server:

mkahawa-srv_0.0.1.1_i386.deb
libccls_0.8.0.1-1_i386.deb

after the installation run sudo ldconfig which might help then launch by typing in the terminal mkahawa -nossl or create a launcher in the desktop with the same command.
[URL="http://www.mediafire.com/file/ynnmxy2ejw3/mkahawa-srv_0.0.3-1_i386.deb"]
[/URL]

---

### Post by utux_utux on 2010-03-04
> **Script Warlock said:**
> mkahawa server:

mkahawa-srv_0.0.1.1_i386.deb
libccls_0.8.0.1-1_i386.deb

after the installation run sudo ldconfig which might help then launch by typing in the terminal mkahawa -nossl or create a launcher in the desktop with the same command.

if you like to try this pre-release version download here then pls send me feedback asap before we release this to sourceforge.

[http://www.mediafire.com/file/zayziayjgiy/libccls_0.8.1-1_i386.deb](http://www.mediafire.com/file/zayziayjgiy/libccls_0.8.1-1_i386.deb)
[http://www.mediafire.com/file/ynnmxy2ejw3/mkahawa-srv_0.0.3-1_i386.deb](http://www.mediafire.com/file/ynnmxy2ejw3/mkahawa-srv_0.0.3-1_i386.deb)

thanks for the reply warlock.. :p
done with installation & run sudo ldconfig > type mkahawa -nossl & it works !! the mkahawa server show up.. but then  found some message @ terminal 

** (process:2690): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2690): CRITICAL **: CCL_client_time_left: assertion `c' failed


is this ok? & how bout the client installation? same process with the server?

thanks in advance

---

### Post by Script Warlock on 2010-03-04
never mind the error.... make a launcher in the desktop right click and choose "create a launcher" then name(any), the command is mkahawa -nossl then description(any)... 

yes client installation is simple just double click the mkahawa-client debs, during installation find the little arrow and click it there you can see 3 questions mkahawa will ask supply them according to your client machine info. wait until the timer icon appears then alt+c to close the installation.. log out or reboot

---

### Post by utux_utux on 2010-03-04
> **Script Warlock said:**
> never mind the error.... make a launcher in the desktop right click and choose "create a launcher" then name(any), the command is mkahawa -nossl then description(any)... 

yes client installation is simple just double click the mkahawa-client debs, during installation find the little arrow and click it there you can see 3 questions mkahawa will ask supply them according to your client machine info. wait until the timer icon appears then alt+c to close the installation.. log out or reboot

launcher ready, server done...

but still have problem about installing the client, here i paste the screenshot.

still need help.. :(

 [IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Script Warlock on 2010-03-04
> **utux_utux said:**
> launcher ready, server done...

but still have problem about installing the client, here i paste the screenshot.

still need help.. :(

 [IMG]file:///tmp/moz-screenshot.png[/IMG]

so the owner or username of this machine is test01?

---

### Post by utux_utux on 2010-03-04
> **Script Warlock said:**
> so the owner or username of this machine is test01?

username: warnet
client name: TEST01
server address: 192.168.1.10

---

### Post by Script Warlock on 2010-03-05
> **utux_utux said:**
> username: warnet
client name: TEST01
server address: 192.168.1.10

reinstall the client with the files i sent not the final but usable... the latest mkahawa source was uploaded last night if you know how to compile pls do but if not just use the client file i gave.. if you can wait in a few days debs and exe are available for download....

---

### Post by utux_utux on 2010-03-05
> **Script Warlock said:**
> reinstall the client with the files i sent not the final but usable... the latest mkahawa source was uploaded last night if you know how to compile pls do but if not then just use the client file i gave to you.. if you can wait then in a few days debs and exe are available for download....

thnks warlock.. sorry if im make u busy.. ;)
i'll try the client file that u gave to me.. but,
im also looking forward for the final & stable release.. well, i'll wait.. :D
thanks again.. long live the community !!

---

### Post by Script Warlock on 2010-03-06
mkahawa is now available for download please visit [here]("http://sourceforge.net/projects/mkahawa/files/"):D

---

### Post by sabitha on 2010-03-07
i've got this when first install on 9.04
> Selecting previously deselected package libccls.
(Reading database ... 239337 files and directories currently installed.)
Unpacking libccls (from libccls_0.8.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of libccls:
 libccls depends on libsqlite3-0 (>= 3.6.16); however:
  Version of libsqlite3-0 on system is 3.6.10-1ubuntu0.2.
dpkg: error processing libccls (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libccls
nabil@nabil-laptop:~/mkahawa$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ijsgutenprint python-ipy hplip-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libccls
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 135kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 239342 files and directories currently installed.)
Removing libccls ...


any help??

---

### Post by Script Warlock on 2010-03-07
> **sabitha said:**
> i've got this when first install on 9.04


any help??

pls download again the libccls sorry i forgot to replace..

---

### Post by m4z on 2010-03-08
> **Script Warlock said:**
> pls download again the libccls sorry i forgot to replace..
i try to download on sourceforge.net but the file libccls.deb is missing

---

### Post by Script Warlock on 2010-03-08
> **m4z said:**
> i try to download on sourceforge.net but the file libccls.deb is missing

use the link i post here..

---

### Post by sabitha on 2010-03-09
> **Script Warlock said:**
> use the link i post here..

unable download from your link post !
can you reupload to another file host

---

### Post by Script Warlock on 2010-03-09
ok done...

---

### Post by sabitha on 2010-03-09
> **Script Warlock said:**
> ok done...

forget about it, i think mediafire seems to be down for a while in here :D

---

### Post by princessmarisa on 2010-03-18
I finally got the last release working really well, ready to write up up for my Uni project and then there is a new release!
Oh well it is all learning, and all more info for my report. :D

---

### Post by Script Warlock on 2010-03-18
> **princessmarisa said:**
> I finally got the last release working really well, ready to write up up for my Uni project and then there is a new release!
Oh well it is all learning, and all more info for my report. :D

thats nice...

---

### Post by mgcardinal01 on 2010-03-20
> **Script Warlock said:**
> for ubuntu/linux [SIZE=5]YES ITS FREE!!![/SIZE]:P [SIZE=5]UNLIMITED MACHINES!!!![/SIZE]........pls pm me about the details how to get a pack of this timer with ubuntu/linux. winxp and win7......linux walang problema libre na toh to the max!!!

pwede to install sa ubuntu 9.10 at pwede rin xp clients mo...

to answer your tanong:
1. ubuntu is now a user friendly and mkahawa is so simple to use na para ka lang naagpaandarng ipod na merong stop, pause play, continue, block timer, send message to the client, swap, etc...demo mo lang sa boss mo ang ubuntu and how it works and what advantages nito kung gagamitin as a server OS ng icafe nyo.
2. nasagot ko na po yan.
3. n da bigining .... [ccl]("http://ccl.sourceforge.net/")
     sqlite at glib
4. it is a x-platform cyber manager that runs on M$, linux and MacOsx
5. instalalabol - gamit ka lang wine or crossover
6. good for linux lang ang server pero clients are cross platform
7. unlimited....once ka lang kumuha ng mkahawa at sayo na yan habangbuhay...
8. kah kah kah...nasagot ko ba tanong mo ng tama?:-s


Is the client for windows XP also FREE? When will it be released?
If it's FREE then it's time to switch server OS to Linux/Ubuntu.

---

### Post by cong06 on 2010-03-24
Just starting to use mkahawa here in Kenya. Looks like pretty sweet software...

---

### Post by princessmarisa on 2010-03-26
What is the default password for when you create a member?

I have tried the User ID, just blank, the username again and the Login ID and none seem to work?

Any documentation for how the ticketing system works?
Also

Sometimes on the client PC, the mkahawa timer/status box will freeze and end up just displaying the graphic of the window above it

eg, when you load the ubuntu applications menu then close it again the timer gets stuck with an image from that menu of 
accessories >
games >
etc >

After this happens the server seems to no longer have any control over the client,

is there anyway to fix this?


Otherwise great software, thanks :KS

---

### Post by WannabeFantasma on 2010-03-26
wow cool, a must-test! :D

---

### Post by Script Warlock on 2010-03-26
> **princessmarisa said:**
> What is the default password for when you create a member?

I have tried the User ID, just blank, the username again and the Login ID and none seem to work?

Any documentation for how the ticketing system works?
Also

Sometimes on the client PC, the mkahawa timer/status box will freeze and end up just displaying the graphic of the window above it

eg, when you load the ubuntu applications menu then close it again the timer gets stuck with an image from that menu of 
accessories >
games >
etc >

After this happens the server seems to no longer have any control over the client,

is there anyway to fix this?


Otherwise great software, thanks :KS

noted....

---

### Post by Script Warlock on 2010-03-30
> **princessmarisa said:**
> What is the default password for when you create a member?

I have tried the User ID, just blank, the username again and the Login ID and none seem to work?

Any documentation for how the ticketing system works?
Also

Sometimes on the client PC, the mkahawa timer/status box will freeze and end up just displaying the graphic of the window above it

eg, when you load the ubuntu applications menu then close it again the timer gets stuck with an image from that menu of 
accessories >
games >
etc >

After this happens the server seems to no longer have any control over the client,

is there anyway to fix this?


Otherwise great software, thanks :KS

adding member:

1. member tab
2. add new member
3. add login - could be member name 
4. add credit to the member
5. set the tariff for the member
6. save
7. login the member account
8. default password is the members id

member can also set their own password after logging in can be located just beside the assist and end session button right click the client icon and set member can start the session. if ever they forgot their password just highlight a certain member in the members tab and reset the password which is the members id.

---

### Post by totoyko on 2010-04-09
Hi! I am a new member of this forum.... I successfully install the mkahawa server and client... it is successfully running! i will use this in our internet cafe, starting this summer class.... Thanks! GOD and to all! My problem is "How to change the client lock picture?"

Anyone can help!!!

Thanks in Advance...

---

### Post by Script Warlock on 2010-04-09
OT: wattah handle :lolflag: .. @totoyko [here]("http://mkahawa.net/faqs.php") or [here]("http://www.mkahawa.net/member.php")

---

### Post by cong06 on 2010-04-11
I would like to help Mkahawa, by (at the very least) submitting bug reports.

Is there someplace I can do this? Any official website?

I sent an e-mail to the e-mail address posted on the source forge page, and while I shouldn't expect an answer, I'm curious if the e-mail address is dead.
Or is that just the best place to submit bugs?

---

### Post by Script Warlock on 2010-04-11
bug reporting is very welcome for mkahawa please post [here]("http://sourceforge.net/projects/mkahawa/forums/forum/955736") .. be aware that the messaging feature and printing a ticket with a 51 digit can crash mkahawa...

---

### Post by totoyko on 2010-04-12
Thanks Boss Warlock Script.... I upload my client blocker image....
How many days, i receive the update of the client?


Thanks! in Advance....

---

### Post by Script Warlock on 2010-04-12
> **totoyko said:**
> Thanks Boss Warlock Script.... I upload my client blocker image....
How many days, i receive the update of the client?


Thanks! in Advance....

3seconds after you upload your lockpix may matanggap ka na email sa email account na binigay mo...

---

### Post by cong06 on 2010-04-14
I wanted to make posts to the sourceforge.net forum, but as I'm having troubles logging in, I'll just list them here.

1) The Tariff box is too small. It doesn't even list a full name.
2) It seems as computers use it more and more, the "total" keeps increasing. Which means you have to rely on the individual posts.
3) Messaging is working, except that when a user clicks "ok" Mkahawa freezes, and (while the dialog stays there) they have have infinite time and the server looses control over clients.
4) A few of the options don't quite work...

I would suggest that in the case of a crash, Mkahawa should lock up the computer... I wonder if that's possible.

I'm a bit confused with the "products" categories... I can't quite see how it works with the computers. Is that if they want to print something, or buy a flash drive? (ie: none-direct computer usage)

As it stands, it seems like it's great for keeping track of how long they use it, and then everything else can be done manually. It's also strong as far as controlling computer usage from a separate desk (ie as long as it didn't freeze--which only happens from messaging--you can block their control, basically turn off the screen)

---

### Post by dannydynx on 2010-05-03
Does mkahawa run smoothly on ubuntu 10.04?

---

### Post by Script Warlock on 2010-05-03
> **dannydynx said:**
> Does mkahawa run smoothly on ubuntu 10.04?

yes, if ever you encounter some libfox thing duriong the installation sa server please install libfox1.6...

---

### Post by cong06 on 2010-05-05
I'm not sure what's going on anymore.

I've tried this with several different versions of mkahawa, and can't figure out what I'm missing.

I've installed:
build-essentials
libfox-1.6-dev
libssl-dev

and I've downloaded libccls_0.8.2-1_i386.deb off the website.

everytime I try and compile mkahawa, I get the error:
```

checking for CCL_init in -lccls... no
configure: error: please install libccls
```
So I check:
```
root@kimende-s:~# aptitude search libccls
i   libccls                                                                     - Cafe Con Leche Server Library   

```
and there it is.

I've tried compiling libccls, but I get the error:
```

checking for sqlite3_open in -lsqlite3... no
configure: error: please install sqlite3

```
So I check:
```
root@kimende-s:~/libccls# aptitude search sqlite3 | grep ^i
i   libsqlite3-0                    - SQLite 3 shared library                   
i   sqlite3                         - A command line interface for SQLite 3  
```
And there it is.

Everything It claims I don't have installed is installed...

---

### Post by cong06 on 2010-05-05
I installed with the debian package, and now I'm getting segfaults:
```

May  5 16:17:58 kimende-s kernel: [  807.723395] mkahawa[7125]: segfault at 128 ip 080556f7 sp b4f302c0 error 4 in mkahawa[8048000+79000]
May  5 16:18:22 kimende-s kernel: [  831.689866] mkahawa[7151]: segfault at 28b1e4a4 ip b76e500b sp bfb49e20 error 6 in libccls.so.0.8.0[b76df000+15000]
May  5 16:18:43 kimende-s kernel: [  852.656545] mkahawa[7153]: segfault at 299804a4 ip b76ee00b sp bff07790 error 6 in libccls.so.0.8.0[b76e8000+15000]
May  5 16:18:49 kimende-s kernel: [  858.768584] mkahawa[7155]: segfault at 287514a4 ip b782000b sp bff19aa0 error 6 in libccls.so.0.8.0[b781a000+15000]

```

Edit:
Now this is interesting:
```

root@kimende-s:~# mkahawa -nossl

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
^C
root@kimende-s:~# mkahawa -nossl
Segmentation fault

```
It worked in an "old" terminal for a bit, and then when I canceled it, and tried again, it seg faulted again...

Edit2:
So I removed, and re-installed mkahawa-srv_0.0.4-1_i386.deb libccls_0.8.2-1_i386.deb to get a more helpful error:
```
mkahawa: error while loading shared libraries: libccls.so.0: cannot open shared object file: No such file or directory
```
for now I'm back on mkahawa-srv_0.0.3-1_i386.deb libccls_0.8.1-1_i386.deb.
I think my previous errors were because I had 0.0.4 with 0.8.1 installed.

---

### Post by cong06 on 2010-05-05
sorry for all the posts.
I was wrong. I can get mkahawa running once, but after this time, all subsequent times (up until a re-install) show up with segmentation faults.
Maybe missing software? It was working before I did a re-install...

---

### Post by Script Warlock on 2010-05-05
> **cong06 said:**
> I installed with the debian package, and now I'm getting segfaults:
```

May  5 16:17:58 kimende-s kernel: [  807.723395] mkahawa[7125]: segfault at 128 ip 080556f7 sp b4f302c0 error 4 in mkahawa[8048000+79000]
May  5 16:18:22 kimende-s kernel: [  831.689866] mkahawa[7151]: segfault at 28b1e4a4 ip b76e500b sp bfb49e20 error 6 in libccls.so.0.8.0[b76df000+15000]
May  5 16:18:43 kimende-s kernel: [  852.656545] mkahawa[7153]: segfault at 299804a4 ip b76ee00b sp bff07790 error 6 in libccls.so.0.8.0[b76e8000+15000]
May  5 16:18:49 kimende-s kernel: [  858.768584] mkahawa[7155]: segfault at 287514a4 ip b782000b sp bff19aa0 error 6 in libccls.so.0.8.0[b781a000+15000]

```Edit:
Now this is interesting:
```

root@kimende-s:~# mkahawa -nossl

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:7424): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
^C
root@kimende-s:~# mkahawa -nossl
Segmentation fault

```It worked in an "old" terminal for a bit, and then when I canceled it, and tried again, it seg faulted again...
you only need to install the libccls and mkahawa server and libfox1.6,  mkahawa server cannot start immediately after it is stopped (or crashes)  when the clients were connected to it. You have to wait for about 2  mins for the OS to recover the broken TCP connections back to the system. and you dont need to be root to launch mkahawa /usr/bin/mkahawa -nossl

---

### Post by cong06 on 2010-05-05
Ok. working.

---

### Post by Script Warlock on 2010-05-05
> **cong06 said:**
> Ok. working.

** (process:7424): CRITICAL **: CCL_client_time_left: assertion `c' failed

that's just an assertion...
not to worry about as long as the program is running some variables are initialized
before the admin/user logs in.. no harm to your computer.

---

### Post by dannydynx on 2010-05-11
I have tried to run mkahawa server on lubuntu 10.04 but doesnot run what could be the problem? It doesnot display the main window but  the client runs

---

### Post by Script Warlock on 2010-05-11
terminal launch:

/usr/bin/mkahawa -nossl

post the errors here.

---

### Post by masdjo on 2010-05-21
Why the price is  always plus one, for example, I use the system's first 20 minutes with  the price of 1000 rupiah, when the client click start  session, the price  on the server is 1001, should be 1000.
Why did  this happen?
I am using the latest mkahawa.

regards
Masdjo

Here is my screenshot of mkahawa server
[http://ubuntu-indonesia.com/public/My Mkahawa Cyber Manager.jpg]("http://ubuntu-indonesia.com/public/My%20Mkahawa%20Cyber%20Manager.jpg")[URL="http://ubuntu-indonesia.com/public/Mkahawa%20Cyber%20Manager.jpg"]
[/URL]

---

### Post by Script Warlock on 2010-05-21
we wait for ouwor to fix the tariff issue...

---

### Post by aristsag on 2010-06-06
> **Script Warlock said:**
> we wait for ouwor to fix the tariff issue...

Mkahawa is been updated to :guitar: 0.0.4-2
tariffs works fine with new debs

---

### Post by mbuotidem on 2010-06-07
I'm running Ubuntu 10.0 and I'm trying out Mkahawa and  experiencing some difficulty. For some reason, after installing my clients, when i log into the account which i designated as the mkahawa account, it does not lock down or show me anything related to Mkahawa. It simply boots up and shows the desktop as it would have done had i logged into my administrator account.I also don't know how to activate it from the Applications menu or the terminal. The package installed successfully and all the dependencies are installed. I am wondering what could be responsible. 

Then, on my server, Mkahawa installed successfully after I installed the dependencies. The server software runs but I was a bit surprised to find that clicking on new client only gave me an option to insert a name. There is no way for me to verify from withing Mkahawa that Mkahawa can actually communicate with my clients.


But when using ping from network tools, I can ping all my clients successfully. So how do I verify that the Mkahawa clients can speak to my Mkahawa server?:(

---

### Post by Script Warlock on 2010-06-07
> **mbuotidem said:**
> I'm running Ubuntu 10.0 and I'm trying out Mkahawa and  experiencing some difficulty. For some reason, after installing my clients, when i log into the account which i designated as the mkahawa account, it does not lock down or show me anything related to Mkahawa. It simply boots up and shows the desktop as it would have done had i logged into my administrator account.I also don't know how to activate it from the Applications menu or the terminal. The package installed successfully and all the dependencies are installed. I am wondering what could be responsible. 

Then, on my server, Mkahawa installed successfully after I installed the dependencies. The server software runs but I was a bit surprised to find that clicking on new client only gave me an option to insert a name. There is no way for me to verify from withing Mkahawa that Mkahawa can actually communicate with my clients.


But when using ping from network tools, I can ping all my clients successfully. So how do I verify that the Mkahawa clients can speak to my Mkahawa server?:(

mkahawa needs a static ip from the server....

---

### Post by Script Warlock on 2010-06-07
> **masdjo said:**
> Why the price is  always plus one, for example, I use the system's first 20 minutes with  the price of 1000 rupiah, when the client click start  session, the price  on the server is 1001, should be 1000.
Why did  this happen?
I am using the latest mkahawa.

regards
Masdjo

Here is my screenshot of mkahawa server
[http://ubuntu-indonesia.com/public/My Mkahawa Cyber Manager.jpg]("http://ubuntu-indonesia.com/public/My%20Mkahawa%20Cyber%20Manager.jpg")[URL="http://ubuntu-indonesia.com/public/Mkahawa%20Cyber%20Manager.jpg"]
[/URL]

try the latest release and use the .00 for the round-off... please see the tariff setting:

[http://www.youtube.com/watch?v=BHG0eHgg4ow](http://www.youtube.com/watch?v=BHG0eHgg4ow)

---

### Post by mbuotidem on 2010-06-07
> **Script Warlock said:**
> mkahawa needs a static ip from the server....

Yeah. My server has a static IP! And i can ping it from my clients network tools! I added this setting to my  /etc/network/interfaces

auto eth0
iface eth0 inet static
address 10.8.16.1
netmask 255.255.255.0        
broadcast 10.8.16.0
network 10.8.16.0

So right now i'm quite confused. Or could the fact that I have 2 nic's on my server and a usb modem be a problem. I use on of the nic's to share internet to my router and the other to connect to my network. The one connected to my network is the one that is statically configured using the above setting!


And for some reason, my clients do not lock down when i boot into them using the account i designated as the account for Mkahawa during setup.

---

### Post by Script Warlock on 2010-06-07
this is my servers eth0 and eth1

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0                                      <------ server is dynamic from the dsl modem
iface eth0 inet dhcp

auto eth1                                       <------ static going to 16 port switch
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1 

and after doing the networking thing i installed firestarter.

clients default gateway is 192.168.0.1 (eth1)...

---

### Post by masdjo on 2010-06-07
I have installed the latest mkahawa and tarif works fine, and little surprise is client background ...celebrate FIFA world cup ... :D

But I still have one question, how to set member correctly ?
I have made member, but the member couldn't login to server, although I've entered a user name and  password (user name).

Btw, thanks for your effort :D

---

### Post by dafir06 on 2010-06-08
I have installed latest mkahawa on my ubuntu 10.4, it works fine on server and client.
thanks for everyone who created this very useful tool

---

### Post by Script Warlock on 2010-06-08
> **masdjo said:**
> I have installed the latest mkahawa and tarif works fine, and little surprise is client background ...celebrate FIFA world cup ... :D

But I still have one question, how to set member correctly ?
I have made member, but the member couldn't login to server, although I've entered a user name and  password (user name).

Btw, thanks for your effort :D

noted..

---

### Post by mbuotidem on 2010-06-08
Working perfectly now. :guitar:

---

### Post by Script Warlock on 2010-06-08
> **mbuotidem said:**
> Working perfectly now. :guitar:
how did you figure out the trouble... please share.

---

### Post by mbuotidem on 2010-06-08
it occurred to me to visit the mkahawa sourcforge page and then browse to the help forum/section. There I found that people had already faced a similar problem. Contrary to what i thought, my networks were okay. There was a missing "dependency" on my clients called libfox. once i installed libfox, Voila! my clients showed up on the server.


The difficulty i am currently facing is understanding the tariff and ticket settings. Do you have something like a simple guide any where?

a screen shot is attached.



and why does 2 show me a red colour? :confused: just wondering

---

### Post by aljoriz on 2010-06-08
June 28 mag sisimula ang Pilipinas Anti Piracy Team (PAPT) PIRACY crackdown sa CEBU.  

So sa mga internet cafe jan.. May Linux na kayo!!!

I find it odd that PAPT will confiscate the monitor at printer ng pc's running pirated softwares.

---

### Post by Script Warlock on 2010-06-08
> **mbuotidem said:**
> it occurred to me to visit the mkahawa sourcforge page and then browse to the help forum/section. There I found that people had already faced a similar problem. Contrary to what i thought, my networks were okay. There was a missing "dependency" on my clients called libfox. once i installed libfox, Voila! my clients showed up on the server.


The difficulty i am currently facing is understanding the tariff and ticket settings. Do you have something like a simple guide any where?

a screen shot is attached.



and why does 2 show me a red colour? :confused: just wondering

your client 2 is disconnected...

---

### Post by Script Warlock on 2010-06-08
> **aljoriz said:**
> June 28 mag sisimula ang Pilipinas Anti Piracy Team (PAPT) PIRACY crackdown sa CEBU.  

So sa mga internet cafe jan.. May Linux na kayo!!!

I find it odd that PAPT will confiscate the monitor at printer ng pc's running pirated softwares.

OT: oo nga mahal pa naman ng monitor.. o school nyo sir baka masali ubuntu mo na yan lahat hehehe pakisabi kay sir dodong... license nila pang M$ lang naman yan at paano kaya nila maregulate ang linux?.. linux is copyleft.

---

### Post by aljoriz on 2010-06-08
> **Script Warlock said:**
> oo nga mahal pa naman ng monitor.. o school nyo sir baka masali ubuntu mo na yan lahat hehehe pakisabi kay sir dodong...

If mahuhuli yan like USJ-R (for using pirated VBsoftware circa2000), yung IT head ang tatagain hindi ako bwahahaha nasa social sciences ako eh.  Hobby ko lang tlga Fully Open Source System.  Sayang nga di ako ang BS-IT.

---

### Post by Script Warlock on 2010-06-08
> **aljoriz said:**
> If mahuhuli yan like USJ-R (for using pirated VBsoftware circa2000), yung IT head ang tatagain hindi ako bwahahaha nasa social sciences ako eh.  Hobby ko lang tlga Fully Open Source System.  Sayang nga di ako ang BS-IT.

hehehe buy orig or go open source...

---

### Post by mbuotidem on 2010-06-09
I guess this might sound crazy, but the truth is, even though i've gotten my clients and server to communicate and can login from any client as a member, **I am still unable to generate/print tickets, not to talk of using a ticket to log in!** i hope someone can help me understand.

When i go to the ticket section and i click on Generate, it opens a window where i can enter details about the ticket i want to use. when i click generate, it shows me a list of tickets depending on the specifications i entered. then i click save and it tells me that the tickets have been saved in the DB. 

After that, i click ok and click exit. however, the just created tickets do not appear. neither do i know where to print them! please help, i'm totally confused.

---

### Post by mbuotidem on 2010-06-09
):Psorry o! i guess am a bit of a thick head. all i needed to do was click the refresh button. 

but under the tariff section there is stuff i don't understand.

what exactly does fraction after mean? :confused:

what does the start time box mean and how should it be used. (if its not asking too much, an example would be appreciated)

and how does the days of the week stuff under **Tariff Elements **work?

It's kind of difficult to work with a program that has no documentation. I guess when i master Mkahawa i might devote time to writing a little how-to.:p

---

### Post by machakos on 2010-07-06
Im trying to install Mkahawa client on these two machines, the instal goes on well until it gets to launching the apllication....when running the mkahawa -nossl command, the output says the mkahawa folder is not found.What is the issue and how can i work around it?

---

### Post by Script Warlock on 2010-07-06
> **machakos said:**
> Im trying to install Mkahawa client on these two machines, the instal goes on well until it gets to launching the apllication....when running the mkahawa -nossl command, the output says the mkahawa folder is not found.What is the issue and how can i work around it?

terminal launch mkahawa server with this /usr/bin/mkahawa -nossl btw mkahawa shortcut is found under the application>other>mkahawa and right click it to add shortcut on your desktop.

---

### Post by jarenme on 2010-07-08
Hai guys!!! Congratulations to everyone for the success of this mkahawa cyber manager!!

My concerned is this... "Is there any possible way for me to change the ip address i've used in installing the mkahawa client. I hav'nt advice my collegue to make an static ip address for the mkahawa server.. the problem now is... i can't open the client from my server nor i can't open my client in the client pc itself...

Pls i need ur help... thanks a lot!!!

---

### Post by Script Warlock on 2010-07-08
> **jarenme said:**
> Hai guys!!! Congratulations to everyone for the success of this mkahawa cyber manager!!

My concerned is this... "Is there any possible way for me to change the ip address i've used in installing the mkahawa client. I hav'nt advice my collegue to make an static ip address for the mkahawa server.. the problem now is... i can't open the client from my server nor i can't open my client in the client pc itself...

Pls i need ur help... thanks a lot!!!

1. boot to safe mode
2. drop to root shell prompt
3. cd /home/jarenme
4. locate the file with  ----    ls
5. if the file was saved in Downloads folder then cd /home/jarenme/Downloads
6. start installing with this command  ---  sudo dpkg -i mkahawa_whatever_i386.deb and reconfigure
7. sudo reboot

some howto clips on my youtube channel hope it helps... [youtube]("http://www.youtube.com/user/scriptwarlock")

---

### Post by jarenme on 2010-07-09
:D Thanks a lot script warlock. My clients and server  are doing fine and gud now...!!

;)

---

### Post by mbuotidem on 2010-10-11
[SIZE=3]Hi, please this is my current problem with Mkahawa server. What could be wrong? I have uninstalled it and re-installed the latest version from sourceforge but im still getting this error.

[/SIZE]```
 

[SIZE=3]mbuotidem@Server:~$ mkahawa
[E]File "cert.pem" not found!!
Aborted
mbuotidem@Server:~$ mkahawa
[E]File "cert.pem" not found!!
Aborted
mbuotidem@Server:~$ mkahawa
[E]File "cert.pem" not found!!
Aborted
mbuotidem@Server:~$[/SIZE]
```[SIZE=3]
[/SIZE]

---

### Post by mbuotidem on 2010-10-11
sorry, should have searched the forums first before posting! answer to my questions is already on this thread.

---

### Post by eddykasirye on 2010-11-15
Hi all,
 I too need help here.
i have my clients running zencafe, but i have installed the server module of mkahawa on ubuntu.
the problem here is that when you start mkahawa server, it comes on for a few seconds and goes off. when you have no client running, it won't go off. pliz help. check this output here

d-town@d-town-1:~$ /usr/bin/mkahawa -nossl

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

GLib-ERROR **: /build/buildd/glib2.0-2.24.0/glib/gmem.c:157: failed to allocate 2155282691 bytes
aborting...
Aborted
d-town@d-town-1:~$

---

### Post by Script Warlock on 2010-11-15
may i know what version of mkahawa server are you using?

---

### Post by eddykasirye on 2010-12-05
> **script warlock said:**
> may i know what version of mkahawa server are you using?

i downloaded the latest deb version

---

### Post by yewo on 2010-12-20
hi, i'm having trouble logging into my clients.

i have tried using the Login ID, also tried the User ID to no avail.

I'm using server 0.0.4-2 and client 0.0.4-1 on ubuntu 10.10

I also seem unable to login using tickets, when i click on the text field to enter the ticket number on the client, i don't get a curser - i can't type any thing.

Any ideas?

Yewo

---

### Post by Script Warlock on 2010-12-23
> **eddykasirye said:**
> Hi all,
 I too need help here.
i have my clients running zencafe, but i have installed the server module of mkahawa on ubuntu.
the problem here is that when you start mkahawa server, it comes on for a few seconds and goes off. when you have no client running, it won't go off. pliz help. check this output here

d-town@d-town-1:~$ /usr/bin/mkahawa -nossl

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:1649): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

GLib-ERROR **: /build/buildd/glib2.0-2.24.0/glib/gmem.c:157: failed to allocate 2155282691 bytes
aborting...
Aborted
d-town@d-town-1:~$

are you using 64bit?

---

### Post by Script Warlock on 2010-12-23
this is just the alpha release of gtk-mkahawa-client not yet good for production machines....
tested on meerkat....

[IMG]http://img9.imageshack.us/img9/5066/screenshotgy.png[/IMG]

[IMG]http://img222.imageshack.us/img222/8874/screenshotep.png[/IMG]

[IMG]http://img132.imageshack.us/img132/6771/screenshot1yet.png[/IMG]

---

### Post by willyn on 2011-01-06
Does Mkahawa work in Xubuntu 10.04?

I have been trying to make Mkahawa work in Xubuntu 10.04 these past few days but nothing seems to work.

1. Server is installed properly and Admin Panel is displayed
2. A client can connect properly to the Server
3. Server can initiate session of client

But this is all it can do. When I try to stop the session or do other things such as reboot machine, the server hangs.

I am using:
server:
mkahawa_srv_0.04-2_i386.deb
libccls_0.8.2-2_i386.deb
libfox-1.6-0_1.6.36-2_i386.deb

client:
mkahawa-client_0.0.4-3_i386.deb
libcclc_0.8.0-1_i386.deb

Please help.

---

### Post by cong06 on 2011-01-06
For 10.04 I had to use mkahawa-client 0.0.4-2 instead of -3
for 10.10 I had to use both Mkahawa-cleint 0.0.4-3 and gtk-mkahawa-thingy.

There must have been a major change in 10.10 to cause the the updated software to not work in previous versions.

---

### Post by Script Warlock on 2011-01-06
> **willyn said:**
> Does Mkahawa work in Xubuntu 10.04?

I have been trying to make Mkahawa work in Xubuntu 10.04 these past few days but nothing seems to work.

1. Server is installed properly and Admin Panel is displayed
2. A client can connect properly to the Server
3. Server can initiate session of client

But this is all it can do. When I try to stop the session or do other things such as reboot machine, the server hangs.

I am using:
server:
mkahawa_srv_0.04-2_i386.deb
libccls_0.8.2-2_i386.deb
libfox-1.6-0_1.6.36-2_i386.deb

client:
mkahawa-client_0.0.4-3_i386.deb
libcclc_0.8.0-1_i386.deb

Please help.

yes it will, use mkahawa-client 0.0.4-2 not 4-3...

---

### Post by willyn on 2011-01-07
> **Script Warlock said:**
> yes it will, use mkahawa-client 0.0.4-2 not 4-3...

I followed the suggestion to use 4-2 and I was able to make it work to some extent.

But at the client side, I can not activate a session by logging in using login ID and password of member.

I tried to override the client password with admin password yet I still cannot login.

Note that I created a member with  login ID and password as suggested. 

Another thing, is there a way I can track the time usage of each member? 

I am actually trying to implement this in a school setting where we need to control the time usage of the students.

Thanks for all the help.

---

### Post by Script Warlock on 2011-01-07
will check that after next week... very busy for sinulog events.

---

### Post by willyn on 2011-01-09
> **Script Warlock said:**
> will check that after next week... very busy for sinulog events.

hmmm... taga Cebu diay mo bay?  Good work!

---

### Post by Script Warlock on 2011-01-09
@willyn, yes ikaw asa man ka karon? asa dapit inyoha.

---

### Post by cong06 on 2011-01-20
I have a friend that wants to set up an mkahawa server on windows, and then use it on linux clients.

Unfortunetly I can't find a server package for windows. Or even source code for 0.0.4. Could it be uploaded?

---

### Post by Script Warlock on 2011-01-20
here you can find the win32 binaries...

[https://www.unwiretechnologies.net/downloads.php](https://www.unwiretechnologies.net/downloads.php)

---

### Post by interbuzz on 2011-01-21
Hi everyone and thanks for this great tool. I have been using it for a couple of months now on ubuntu 10.04 and 10.10 and it works great. 
The only things is that the world cup is over now and it was great event here in South Africa, but I would like to change the blocker screen now. I have done like this thread says and also the website. My pics are uploaded, downloaded and clients updated. It did work on some clients but not all of them. What do you thing may be the problem here?

---

### Post by Script Warlock on 2011-01-21
regarding the member logins please follow the ff steps..

a howto for the members login... a quick workaround is to press the "reset password" located at the mkahawa server members pane.. remember to hit enter/return if you want to login at the clients lockscreen...

[http://www.youtube.com/watch?v=cGr-PwEa-tM](http://www.youtube.com/watch?v=cGr-PwEa-tM)

and some screenshots for ticket logins...

---

### Post by Script Warlock on 2011-01-21
> **interbuzz said:**
> Hi everyone and thanks for this great tool. I have been using it for a couple of months now on ubuntu 10.04 and 10.10 and it works great. 
The only things is that the world cup is over now and it was great event here in South Africa, but I would like to change the blocker screen now. I have done like this thread says and also the website. My pics are uploaded, downloaded and clients updated. It did work on some clients but not all of them. What do you thing may be the problem here?

try to put your lockpix.gif inside the file system or /

---

### Post by Script Warlock on 2011-01-21
> **yewo said:**
> hi, i'm having trouble logging into my clients.

i have tried using the Login ID, also tried the User ID to no avail.

I'm using server 0.0.4-2 and client 0.0.4-1 on ubuntu 10.10

I also seem unable to login using tickets, when i click on the text field to enter the ticket number on the client, i don't get a curser - i can't type any thing.

Any ideas?

Yewo

the ticket login does work just click on the white box and type something and never press login just hit the enter/return key...

---

### Post by Script Warlock on 2011-01-21
> **willyn said:**
> I followed the suggestion to use 4-2 and I was able to make it work to some extent.

But at the client side, I can not activate a session by logging in using login ID and password of member.

I tried to override the client password with admin password yet I still cannot login.

Note that I created a member with  login ID and password as suggested. 

Another thing, is there a way I can track the time usage of each member? 

I am actually trying to implement this in a school setting where we need to control the time usage of the students.

Thanks for all the help.

you can use the log and report.... report can be save as html..

---

### Post by Script Warlock on 2011-01-24
please visit [http://www.youtube.com/watch?v=HYT9L5NOTzk](http://www.youtube.com/watch?v=HYT9L5NOTzk) for mkahawa print server setup...

---

### Post by Script Warlock on 2011-01-24
anyone wants to volunteer(free time lang) translating mkahawa english to tagalog? simple lang ang mga gamit na words like "total time", "canel", "enter the member id", etc...under the [COLOR=Blue]msgstr "local translation"[/COLOR] dyan [COLOR=Black]translation[/COLOR] natin.. pm me...

eto ang sample:
> # Filipino translation of mkahawa package.
# Copyright (C) 2011 yourname
# This file is distributed under the same license as the mkahawa package.
# yourname  <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: yourname\n"
"POT-Creation-Date: 2011-1-1 15:30-20:00\n"
"PO-Revision-Date: 2011-05-27 22:08+0300\n"
"Last-Translator: FULL NAME <EMAIL@ADDRESS>\n"
"Language-Team: Filipino <email@address>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: src/CashingFrame.cpp:76 src/CashingFrame.cpp:375
msgid "Client:"
msgstr ""

#: src/CashingFrame.cpp:78 src/CashingFrame.cpp:89 src/ProductsFrame.cpp:61
msgid "Edit"
msgstr ""

#: src/CashingFrame.cpp:83 src/CashingFrame.cpp:427
msgid "Workstation time:"
msgstr ""

#: src/CashingFrame.cpp:94 src/CashingFrame.cpp:421 src/CCLWin.cpp:185
#: src/LogFrame.cpp:163
msgid "Products:"
msgstr ""

#: src/CashingFrame.cpp:107 src/CCLWin.cpp:153 src/ProductsFrame.cpp:84
#: src/ProductsFrame.cpp:100 src/TarifFrame.cpp:469
msgid "Name"
msgstr ""

#: src/CashingFrame.cpp:108 src/LogFrame.cpp:64 src/LogFrame.cpp:544
#: src/ProductsFrame.cpp:101
msgid "Amount"
msgstr ""

---

### Post by yewo on 2011-02-02
thanks, yes my ticketing functionality is working - i think the fact i wasn't getting a cursor was what threw me

however i am still having the problem of not being able to login as a user - any ideas?

cheers

> **Script Warlock said:**
> the ticket login does work just click on the white box and type something and never press login just hit the enter/return key...

---

### Post by Script Warlock on 2011-02-02
> **yewo said:**
> thanks, yes my ticketing functionality is working - i think the fact i wasn't getting a cursor was what threw me

however i am still having the problem of not being able to login as a user - any ideas?

cheers

heres the link for that... [http://www.youtube.com/watch?v=cGr-PwEa-tM](http://www.youtube.com/watch?v=cGr-PwEa-tM)

---

### Post by yewo on 2011-02-03
many thanks, my problem was lack of funds for my test user - duh!

> **Script Warlock said:**
> heres the link for that... [http://www.youtube.com/watch?v=cGr-PwEa-tM](http://www.youtube.com/watch?v=cGr-PwEa-tM)

---

### Post by yewo on 2011-02-09
I am trying to migrate from a windows based cybera system to mkahawa on linux. 
is there a way to move all my members into mkahawa? i am trying to avoid manually entering about 1000 records

cheers

---

### Post by Script Warlock on 2011-02-09
your starting point: [http://www.lampsig.org/new/archives/102-Integrating-Linux,-Apache,-MySQL,-PHP-with-Mkahawa-Cyber-Manager-and-SQLite.html](http://www.lampsig.org/new/archives/102-Integrating-Linux,-Apache,-MySQL,-PHP-with-Mkahawa-Cyber-Manager-and-SQLite.html)

---

### Post by pmwangi80ke on 2011-02-16
Hello,
i have been using mkahawa on 10.04 both server and client. I just changed the clients to 10.10 and realised that mkahawa-client is not starting automatically on bootup as it used to on 10.04. Can anyone help me out here?.....
Also how do i set up the lockpix image?...

---

### Post by Script Warlock on 2011-02-16
> **pmwangi80ke said:**
> Hello,
i have been using mkahawa on 10.04 both server and client. I just changed the clients to 10.10 and realised that mkahawa-client is not starting automatically on bootup as it used to on 10.04. Can anyone help me out here?.....
Also how do i set up the lockpix image?...

[http://ubuntuforums.org/showpost.php?p=10384765&postcount=121](http://ubuntuforums.org/showpost.php?p=10384765&postcount=121)

i'll see what i can do for the mkahawa startup issue on 10.10.

---

### Post by pmwangi80ke on 2011-02-16
> **Script Warlock said:**
> [http://ubuntuforums.org/showpost.php?p=10384765&postcount=121](http://ubuntuforums.org/showpost.php?p=10384765&postcount=121)

i'll see what i can do for the mkahawa startup issue on 10.10.

Thanks alot Script Warlock for the prompt reply,currently i start it on the terminal with the command 'sudo mkahawa-client -host 192.168.1.1 -name comp1 -nossl'
When i add the command in the startup list it will launch but the icon will disappear.

---

### Post by Script Warlock on 2011-02-18
the solution is to let ubuntu load first all his necessary components, apps and etc. and mkahawa-client be the last.. make a script that delays the launching of mkahawa-client to 30sec or more..

heres an example:

#!/bin/bash 

sleep 30 && mkahawa-client -nossl -name whatever -host server_ip;

and save as .blahblah.sh then chmod a+x blahblah.sh and add in STARTUP APPLICATIONS pointing the command to your saved startup script..

---

### Post by pmwangi80ke on 2011-02-21
> **Script Warlock said:**
> the solution is to let ubuntu load first all his necessary components, apps and etc. and mkahawa-client be the last.. make a script that delays the launching of mkahawa-client to 30sec or more..

heres an example:

#!/bin/bash 

sleep 30 && mkahawa-client -nossl -name whatever -host server_ip;

and save as .blahblah.sh then chmod a+x blahblah.sh and add in STARTUP APPLICATIONS pointing the command to your saved startup script..
Hello,

Thanks alot Script warlock. You have helped me a great deal here. This method worked like a charm for me.

---

### Post by Script Warlock on 2011-02-21
cheers :)

---

### Post by Zemunelo on 2011-02-28
Can i sell (add) time to member and see that in log/report without  clicking on clients, only on Mkahawa server to do action or do i need  clients to be log on to server to complete this action?

To explain,
I can't sell anything and there is no log or report. 
Maybe i am doing something wrong but when i create member and add time  to member or create code or product (i do not care about product,only want to sell time to members) and click sell/complete sell there  is nothing in cashing? 
There are some members with credits on member account and there are some  tickets with some value (credit or time) on them but there is nothing  in log or report even with refresh clicked. 

So what is that i am doing wrong? 
I have tariff, tried default and also my own tariff, have product with  price but nothing is going on and on cashing there is nothing to click. 
Do i need to have clients logged on server to complete payment or i can  sell anything only on server and see report/log? 
And if member have time on his account (explained before that i can add time but there is no report of cashing)  
is that he has free time without payment? 

He can login on client and start using his "free" time because nothing is going on when you add time to member,it's not recorded on log/report.

---

### Post by Script Warlock on 2011-03-01
give me time to check how mkahawa handles all the account and logs..

---

### Post by Script Warlock on 2011-03-01
> I can't sell anything and there is no log or report. 
Maybe i am doing something wrong but when i create member and add time to member or create code or product (i do not care about product,only want to sell time to members) and click sell/complete sell there is nothing in cashing? the only way you can sell a product is to choose a running workstation and double click the product to sell and heres how to view the sold product:
1. register the session to the logs/report by pressing the cash button note: only prepaid and postpaid session is visible to the session table
2. go to report pane and adjust all necessary settings
3. press the product button
4. and press the refresh button

note: sell and complete sale buttons are not functional...

> I have tariff, tried default and also my own tariff, have product with price but nothing is going on and on cashing there is nothing to click. 
Do i need to have clients logged on server to complete payment or i can sell anything only on server and see report/log? 
And if member have time on his account (explained before that i can add time but there is no report of cashing) 
is that he has free time without payment?  see the attached screenshots of the report i generated. you can see 4 sessions different account.
1. U2 - prepaid
2. U2 - postpaid
3. 3TEN - ticket
4. U2:john doe - members account

> There are some members with credits on member account and there are some tickets with some value (credit or time) on them but there is nothing in log or report even with refresh clicked.  use SQLITE database browser to view the ticket and member details..

> He can login on client and start using his "free" time because nothing is going on when you add time to member,it's not recorded on log/report. every members and ticket transactions are recorded inside mkahawa's .db. 
heres how to view: 
open sqlite database browser>open .mkahawa db>browse data>table>members

....sqlite database browser is available in ubuntu software center

---

### Post by Zemunelo on 2011-03-03
> **Script Warlock said:**
> the only way you can sell a product is to choose a running workstation...

I really don't care about product as i said.

I want to sell/add time or credit to member and want to see that in log/report.
Simple.

**Can i do it only on server without any connected client?**
Because i can't, or i am missing something.

I can see on server member time or credit /i call it time/ and i can add credit to member but that is not in log/report.
I can see it,member has it and can login and use his credit.
No report of that.

From that point of view member has free time because adding credit on his account is not registered in report.

Forget tickets,products,forget all that.
I need simple solution for net cafe.

-Add/sell credit or time to member on server,
-Member login start using his credit/time,
-When he deplete his time/credit/ client is locked/restarted and ready for another member.
-At the end i can see report for that.

But when i go on server to:
members/member name/add credit,
i can add credit to that specific member and i can see his credit there i don't need SQLITE database browser for that.
I just don't see any report for that action.
So as i said he can use that credit as free time :D.


p.s. Thanks for your effort

---

### Post by Zemunelo on 2011-03-03
I attached 4 screenshots because i figured it is easier to explain what is happening.

If you find time to look at the pictures hopefully we can identify the problem.

Thank you once again.
Wishing you a nice day :D.

p.s. Let me know if i am doing something wrong
p.s.s. 
picture one-member with no credit on his account,
picture two-adding credit to members account /100/,
picture three-member has 100 credits,
picture four-there is no report even if i put a date from last year till today.

I noticed that the member can log in a client computer and start using his credits /100/ i added.
If you need an additional screenshot of this,let me know.

---

### Post by Script Warlock on 2011-03-03
> and want to see that in log/report. sorry, not yet possible.. will add this on the next release.

as of the moment members credit balance can only be viewed thru members pane..

[http://www.youtube.com/watch?v=92Jpolfiy-M]("http://www.youtube.com/watch?v=92Jpolfiy-M")

---

### Post by Zemunelo on 2011-03-03
Looking forward to the new version, very excited to use the program one day.
I hope I will eventually be able to add time/credit to member accounts that will appear in the log/reports so that I can monitor sales.
I plan to use linux for my internet and gaming club, a good cyber cafe program is essential for that like mkahawa.

I wish I knew enough programming so that I can help developing the program.
Keep up with the good work.:KS

---

### Post by marcosamson on 2011-03-08
i though that the winxp client side is already running. i am very much interested with your work because i have an internet cafe and i have been using handycafe eversince. i wanted a linux based cafe timer which could "control" windows based pc because i plan to migrate some pc to linux especially the older pc's i have. though i can not migrate all to linux because my clientele is more on windows people ie. lan-based & online games which have issues with linux. been learning about linux especially ubuntu for a while now...

keep up the good work sir! hinaot pa nga buligan ka sa Ginoo ug dugang pasensya, maayong panglawas ug dugang kusog para makasugakod sa pagpalambo ani nga imo gitrabaho!

:P

---

### Post by Script Warlock on 2011-03-09
its ouwors work not mine so all credit goes to him for continuing the work of Bruno Deferrari the author of CCL.. 

my job is to support you guys na gumagamit ng mkahawa para sa cyber cafe na ubuntu/linux, kumbaga my shop is just a lab for mkahawas development. if you have any request, suggestions and bug report please email ouwor or me..

@marcosamson, windows version of mkahawa supposed to work pero we concentrate more on linux. thanks buddy we hope to see more shops like you migrates to ubuntu.

---

### Post by marcosamson on 2011-03-09
in my research, most if not all windows based cafe timer will install in wine but will either not run or will not beable to see the clients. i was & still am looking for the cafe timer that can manage both linux & windows clients pc... i hope mkahawa will be the ONE.

for me the advantage of using linux is very attractive for us cafe owners because its free, no virus to think about, most pc hardware are recognized by linux especially ubuntu out of the box. 

though one problem is webcams & video chat. i read somewhere that there is a software that more or less can be used as a video chat client... my solution, because i was seriously considering using ubuntu, was use tokbox at tokbox.com... a flash-based video chat client. but webcams were the major block that stopped me.  can't install my webcams, especially the old one's. though no driver  webcams just do that, they work out of the box but i have a couple of  old webcams that need drivers...

when i was exploring that idea, it was facebook games that were the rage. so no problem with using ubuntu, firefox was all you need but what stopped me was as mentioned above webcams & video chat.

also as mention in my previous post, that my clientele is more on windows based offline & online games, so i have to have a couple of windows based pc but the surfing & etc pc can be ubuntu... just have to find solutions to what is hindering the migration to open source software

---

### Post by Script Warlock on 2011-03-09
try searching sa winehq meron akong na submit dati sa kanila regarding sa cyber timer.

---

### Post by Ollegon on 2011-03-22
Hi! Install the server and client on 4 computers. And ran into problems:
1. On the client in idikatorah stopped showing the time and money is always on zero.
2. At the end of time the client is not blocked and continues to work, even though the server indicator lights red.

I am sorry, I do not speak English so use a translator from Google ...

Ubuntu 10.10
Server mkahawa-srv_0.0.4-2_i386
Client mkahawa-client_0.0.4-2_i386.deb

---

### Post by Script Warlock on 2011-03-22
> **Ollegon said:**
> Hi! Install the server and client on 4 computers. And ran into problems:
1. On the client in idikatorah stopped showing the time and money is always on zero.
2. At the end of time the client is not blocked and continues to work, even though the server indicator lights red.

I am sorry, I do not speak English so use a translator from Google ...

Ubuntu 10.10
Server mkahawa-srv_0.0.4-2_i386
Client mkahawa-client_0.0.4-2_i386.deb

please view this link it might help.. [http://www.youtube.com/user/scriptwarlock](http://www.youtube.com/user/scriptwarlock)

---

### Post by ronlo on 2011-03-24
> **Script Warlock said:**
> try to put your lockpix.gif inside the file system or /



hi i came across the same problem too,
tried putting the lockpix.gif into system or / but it doesn't work, any more suggestion?

---

### Post by Script Warlock on 2011-03-25
may i know how you put the lockpix inside the / perhaps a logout/reboot might do the trick
heres the other howto [URL="https://www.mkahawa.net/member.php"]https://www.mkahawa.net/member.php 
[/URL]

---

### Post by slashdotfx on 2011-03-29
Hi there,

I'm currently installing mkahawa on Lucid LTSP,
using libfox from repo and using the latest stable packages
from sf.net.

I got into problem, whenever the user session begin,
mkahawa-client is not updating its status, always displaying
zero on the time used and how much the client owed.

on the operator side, it's showing just fine.

[S]on my previous jaunty LTSP, I'm using CCL and it works just fine,
but when I try to install CCL from the source,
it has the same problem as mkahawa, timer and owe is not updated.[/S]
update: CCL does update the timer, sorry for my mistake.

any idea?

thanks

---

### Post by Script Warlock on 2011-03-30
did you try the mkahawa multiplier? it's for the LTSP setup.

---

### Post by slashdotfx on 2011-03-30
Hi script warlock, thanks for the quick response,

if you are referring to the latest available .deb from sf.net,
and according to mkahawa.net,

mkahawa-client_0.0.4-3_i386.deb

yes I did install from that version.

---

### Post by Script Warlock on 2011-03-30
i mean this one [http://mkahawa.sourceforge.net/downloads.php](http://mkahawa.sourceforge.net/downloads.php)

---

### Post by slashdotfx on 2011-03-30
I believe, sf.net and mkahawa.net referring to the same .deb file,
I did compare the md5sum and its a match.

---

### Post by Script Warlock on 2011-03-30
let me check the issue.

---

### Post by slashdotfx on 2011-04-11
Hi Script Warlock,

any hint so far?

---

### Post by guillelozoya on 2011-06-02
Hi,
First of all thanx for the app and thanx for keeping it free.
Question: are members kept in a database file to control with an external application?
(I'm using Cybera and I want to switch to mkahawa, and I need to set up a lot of members)
Thanks a lot.

---

### Post by Script Warlock on 2011-06-02
> **guillelozoya said:**
> Hi,
First of all thanx for the app and thanx for keeping it free.
Question: are members kept in a database file to control with an external application?
(I'm using Cybera and I want to switch to mkahawa, and I need to set up a lot of members)
Thanks a lot.

yes

---

### Post by victorhugofg on 2011-06-03
(Hey! This is my first post! =D )

First of all, I'd like to thank you all for this amazing software.

I recently am using Mkahawa and 'til now (almost) everything is working fine, both server and clients. I'm just having trouble when sending messages to the clients. It just doesn't appear on the client-side. What would be happening? Is there anyone who had the same problem here?

Thanks in advance.

---

### Post by Script Warlock on 2011-06-04
> **victorhugofg said:**
> (Hey! This is my first post! =D )

First of all, I'd like to thank you all for this amazing software.

I recently am using Mkahawa and 'til now (almost) everything is working fine, both server and clients. I'm just having trouble when sending messages to the clients. It just doesn't appear on the client-side. What would be happening? Is there anyone who had the same problem here?

Thanks in advance.

i have successfully compiled mkahawa in ubuntu 11.04 server and client  then tried the messaging feature and its working fine for me...

---

### Post by Script Warlock on 2011-06-05
for some reason the deb installer failed to work on 11.04 so i think compile is an option.

---

### Post by victorhugofg on 2011-06-06
Well, seems it would work if I could compile libccls. I've tried everything and I couldn't (the deb installer doesn't work too). It just seems it won't compile: I get the same error every time.

```
root@dae-desktop:/home/dae/Área de Trabalho/Projeto LAN/Source/libccls# make
 cd . && /bin/bash "/home/dae/Área de Trabalho/Projeto LAN/Source/libccls/missing" 
--run automake-1.11 --gnu
eeconfigure.in:19: version mismatch.  This is Automake 1.11.1,
configure.in:19: but the definition used by this AM_INIT_AUTOMAKE
configure.in:19: comes from Automake 1.11.  You should recreate
configure.in:19: aclocal.m4 with aclocal and run automake again.
eWARNING: `automake-1.11' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `automake-1.11' program.
make: ** [Makefile.in] Erro 1
``` (I've downloaded 'automake' again)
Thanks a lot. =)

---

### Post by Script Warlock on 2011-06-06
version mismatch and he needs 1.11 just add .1 inside this files:

Makefile
# Makefile.in generated by automake 1.11.1 from Makefile.am.

Makefile.in
# Makefile.in generated by automake 1.11.1 from Makefile.am.

---

### Post by victorhugofg on 2011-06-10
Which version should I compile? I've tried everything and didn't work. :(
Should the client be compiled too or just the server?

Well, anyways... I've tried to fix it my way (not so good) and when I got the client version installed I sent a message from server and the first one I sent were ok, but the followed ones I got these assertion errors (for each message I sent):

```
intLogoText(): (371, 1000), ff00000008 -> ffffffff08

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(process:3201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(process:3201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(process:3201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(process:3201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (process:3201): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(process:3201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Is there anyway I can fix it and still using the deb installer or is there any tutorial on how to compile Mkahawa without getting so many errors?

Thanks in advance.

---

### Post by Script Warlock on 2011-06-11
i'll make another one for 11.04/11.10...

---

### Post by geo2306 on 2011-07-26
> **Script Warlock said:**
> for some reason the deb installer failed to work on 11.04 so i think compile is an option.


my Server is Ubuntu 11.04 (natty)
I Installed this programs
mkahawa-srv_0.0.4-2_i386.deb
libccls_0.8.2-2_i386.deb
and seems to run fine

The Clients is the same OS 11.04
I Installed this programs
libcclc_0.8.0-1_i386.deb
I have libcclc-dev_0.8.0-1_i386 but is not installed.
and here is the problem...i tried install diferents versions like that:

mkahawa-client_0.0.4-1_i386.deb the problem here is image blocking appears and is online with the server but when press the button start session nothing happens, by the way doesn&#7831; appear in the image block client options like member id, password, start session,ticket id.

then I Tried with mkahawa-client_0.0.4-2_i386.deb here the problem is the same the previous version.

Then I tried with mkahawa-client_0.0.4-3_i386.deb getting this error:
Desempaquetando mkahawa-client (de mkahawa-client_0.0.4-3_i386.deb) ...
dpkg-deb (subproceso): lectura insuficiente en buffer_copy para fallo al escribir a la tubería en la copia
dpkg-deb: error: el subproceso copiado devolvió el código de salida de error 2
dpkg: error al procesar mkahawa-client_0.0.4-3_i386.deb (--install):
 lectura insuficiente en buffer_copy para error en dpkg-deb durante `./usr/bin/mkahawa-client'
Se encontraron errores al procesar:
 mkahawa-client_0.0.4-3_i386.deb

and Then finally try with mkahawa-client-0.0.4.tar.bz2 gettin this error:
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... no
no
configure: error: 

You must have GLib 2.4.0 or newer development headers installed to build.

If you have these installed already you may need to install pkg-config so. I can find them.

I Chek in synaptics and pkg-config is intalled, but GLIB is&#324;t.

libglibmm-2.4 and others is installed but i don know if this is sufficient.

I Hpe your HELPS! and thank for all

---

### Post by kjshoot2ill on 2011-07-27
hi everyone,
this is my first post..^^
im planning to shift my clients' OS to linux, ubuntu OS, and install userful multi seat softie.
is mkahawa timer supported for thin clients?
like 1CPU = 2 monitors +keyboard and mouse with different user functions
tia

---

### Post by Script Warlock on 2011-07-27
> **kjshoot2ill said:**
> hi everyone,
this is my first post..^^
im planning to shift my clients' OS to linux, ubuntu OS, and install userful multi seat softie.
is mkahawa timer supported for thin clients?
like 1CPU = 2 monitors +keyboard and mouse with different user functions
tia

yes try the multiplier/ncomputing on this site [http://mkahawa.sourceforge.net/downloads.php]("http://mkahawa.sourceforge.net/downloads.php")

---

### Post by Script Warlock on 2011-07-27
> **geo2306 said:**
> my Server is Ubuntu 11.04 (natty)
I Installed this programs
mkahawa-srv_0.0.4-2_i386.deb
libccls_0.8.2-2_i386.deb
and seems to run fine

The Clients is the same OS 11.04
I Installed this programs
libcclc_0.8.0-1_i386.deb
I have libcclc-dev_0.8.0-1_i386 but is not installed.
and here is the problem...i tried install diferents versions like that:

mkahawa-client_0.0.4-1_i386.deb the problem here is image blocking appears and is online with the server but when press the button start session nothing happens, by the way doesn&#7831; appear in the image block client options like member id, password, start session,ticket id.

then I Tried with mkahawa-client_0.0.4-2_i386.deb here the problem is the same the previous version.

Then I tried with mkahawa-client_0.0.4-3_i386.deb getting this error:
Desempaquetando mkahawa-client (de mkahawa-client_0.0.4-3_i386.deb) ...
dpkg-deb (subproceso): lectura insuficiente en buffer_copy para fallo al escribir a la tubería en la copia
dpkg-deb: error: el subproceso copiado devolvió el código de salida de error 2
dpkg: error al procesar mkahawa-client_0.0.4-3_i386.deb (--install):
 lectura insuficiente en buffer_copy para error en dpkg-deb durante `./usr/bin/mkahawa-client'
Se encontraron errores al procesar:
 mkahawa-client_0.0.4-3_i386.deb

and Then finally try with mkahawa-client-0.0.4.tar.bz2 gettin this error:
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... no
no
configure: error: 

You must have GLib 2.4.0 or newer development headers installed to build.

If you have these installed already you may need to install pkg-config so. I can find them.

I Chek in synaptics and pkg-config is intalled, but GLIB is&#324;t.

libglibmm-2.4 and others is installed but i don know if this is sufficient.

I Hpe your HELPS! and thank for all

compile... i'll make some video clips for 11.04 in a while.

---

### Post by geo2306 on 2011-08-01
Script Warlock Did you compile or make videos makahawa for 11.04?

Please HELP!!!

---

### Post by Script Warlock on 2011-08-02
> **geo2306 said:**
> Script Warlock Did you compile or make videos makahawa for 11.04?

Please HELP!!!

heres for the client.. [mkahawa-client]("http://www.vimeo.com/27259104")
heres for the server.. [mkahawa-srv]("http://www.youtube.com/user/scriptwarlock#p/a/u/0/PCLFAsDpJH0")
checking connection.. [server-client]("http://www.youtube.com/watch?v=5q0aeDJMdH8")

hope to shed some light regarding the "[E]File cert.pem not found" at 0:10 server-client clip.

---

### Post by solarnetone on 2011-08-04
> **Script Warlock said:**
> heres for the client.. [mkahawa-client]("http://www.vimeo.com/27259104")
heres for the server.. [mkahawa-srv]("http://www.youtube.com/user/scriptwarlock#p/a/u/0/PCLFAsDpJH0")
checking connection.. [server-client]("http://www.youtube.com/watch?v=5q0aeDJMdH8")

hope to shed some light regarding the "[E]File cert.pem not found" at 0:10 server-client clip.


this is like apache's cert file for ssl.  perhaps the same mechanism one uses to generate this for apache could generate a usable cert.

thank you for the videos... very informative.  to install this on LTSP clients, would one put the script in /etc/rc.local to have mkahawa-client run at LTSP client boot, or run it with ltsp-localapps in your Xsession?

thanx!

---

### Post by Script Warlock on 2011-08-04
i'll make a video clips for mkahawa LTSP in a few days...

---

### Post by timpire on 2011-09-17
hi all, thanks for providing such as great tutorial.
i am facing this problem while "make" mkahawa-client:

gui.cpp: In member function ‘void ClientWin::dispMessage(FX::FXString&, int)’:
gui.cpp:373:14: error: too many arguments to function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)’
/usr/include/libnotify/notification.h:114:21: note: declared here
make[1]: *** [gui.o] Error 1
make[1]: Leaving directory `/home/ibrowse/mkahawa/mkahawa-client/src'
make: *** [all-recursive] Error 1


any solutions? thanks.

---

### Post by Script Warlock on 2011-09-17
> **timpire said:**
> hi all, thanks for providing such as great tutorial.
i am facing this problem while "make" mkahawa-client:

gui.cpp: In member function ‘void ClientWin::dispMessage(FX::FXString&, int)’:
gui.cpp:373:14: error: too many arguments to function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)’
/usr/include/libnotify/notification.h:114:21: note: declared here
make[1]: *** [gui.o] Error 1
make[1]: Leaving directory `/home/ibrowse/mkahawa/mkahawa-client/src'
make: *** [all-recursive] Error 1


any solutions? thanks.
i think you need to install libnotify-dev

---

### Post by timpire on 2011-09-18
[LEFT]Thank you Script Warlock.
[/LEFT]
I've found out that i accidentally install "libnotify4-dev" instead of "libnotify-dev". This solve my problems, thanks again :D
Now i have successfully install mkahawa server and client.

Everything work fine except  i cannot remote shut down or reboot the client machine. When i click reboot/shutdown client, there is nth happen. Is there any step that i've missed? Or any changes needed to be made on the system file permission?

--------------
Btw, FYI, i am using Ubuntu 11.04 Natty.

---

### Post by Script Warlock on 2011-09-18
> **timpire said:**
> [LEFT]Thank you Script Warlock.
[/LEFT]
I've found out that i accidentally install "libnotify4-dev" instead of "libnotify-dev". This solve my problems, thanks again :D
Now i have successfully install mkahawa server and client.

Everything work fine except  i cannot remote shut down or reboot the client machine. When i click reboot/shutdown client, there is nth happen. Is there any step that i've missed? Or any changes needed to be made on the system file permission?

--------------
Btw, FYI, i am using Ubuntu 11.04 Natty.

try chmod the client with 

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

---

### Post by timpire on 2011-09-18
> **Script Warlock said:**
> try chmod the client with 

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot


Thank you, now everthing work perfectly. Thanks for your help, your effort (the tutorial, the script & etc). I really appreciate it. Thanks!

---

### Post by Script Warlock on 2011-09-18
no problemo :)

---

### Post by pmwangi80ke on 2011-10-26
Hello):P

i installed mkahawa-client_0.0.4-1_i386.deb on lubuntu 11.04(LXDE). The problem is it never autostarts on booting until i have to manually launch the LXterminal. Am thinking of putting the LXterminal in the autostart list but its also not easy for a newbie like me. Anyone out there with suggestions?????

---

### Post by Script Warlock on 2011-11-02
> **pmwangi80ke said:**
> Hello):P

i installed mkahawa-client_0.0.4-1_i386.deb on lubuntu 11.04(LXDE). The problem is it never autostarts on booting until i have to manually launch the LXterminal. Am thinking of putting the LXterminal in the autostart list but its also not easy for a newbie like me. Anyone out there with suggestions?????

try..
gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart and add like this at the end of the line @mkahawa-client -host.... save and reboot or logout.

---

### Post by pmwangi80ke on 2011-11-04
hi
thanks alot scriptwarlock, my problem got sorted out after i compiled from svn and installed all required dependencies then added client launch command in the /etc/xdg/lxsession/Lubuntu/autostart as you suggested. Now am all lubuntu and enjoying it alot. 

Thanks...

---

### Post by Script Warlock on 2011-11-05
so all your client machine are lubuntu and the server is ubuntu 11.10?

---

### Post by cchester on 2011-11-05
First I would like to say thank you for this software. I am trying to convert my job from Smart Launch to Mkahawa.

We are running Ubuntu 11.10 64bit and I converted the deb files from i386 to amd64 that were on the website. I installed them and everything went fine.

I am getting this error when I run "/usr/bin/mkahawa -nossl".

Error:

"/usr/bin/mkahawa: error while loading shared libraries: libFOX-1.6.so.0: wrong ELF class: ELFCLASS64"

I am not sure what this means? Is it because of it being converted to 64bit debs from 32bit debs? If so, is there a way to get this to work on a 64bit machine?

Thanks for any help on this.

---

### Post by Script Warlock on 2011-11-05
> **cchester said:**
> First I would like to say thank you for this software. I am trying to convert my job from Smart Launch to Mkahawa.

We are running Ubuntu 11.10 64bit and I converted the deb files from i386 to amd64 that were on the website. I installed them and everything went fine.

I am getting this error when I run "/usr/bin/mkahawa -nossl".

Error:

"/usr/bin/mkahawa: error while loading shared libraries: libFOX-1.6.so.0: wrong ELF class: ELFCLASS64"

I am not sure what this means? Is it because of it being converted to 64bit debs from 32bit debs? If so, is there a way to get this to work on a 64bit machine?

Thanks for any help on this.

never used 64 bit on my shop but for tests sake i'll get back to you after i run mkahawa on a 64bit environment. but according to [this]("http://mkahawa.net/features.php") it will support 64bit. by the way this is ouwors project and i have no contact 2mons ago, hope he's in good condition.

---

### Post by Script Warlock on 2011-11-05
i think theres a problem running mkahawa server in ubuntu 11.10. launching may result to  FXComposeContext: illegal window parameter
Aborted

---

### Post by pmwangi80ke on 2011-11-06
> **Script Warlock said:**
> so all your client machine are lubuntu and the server is ubuntu 11.10?



hi,
yeah all of the clients are lubuntu 11.04 & 10.04 since they are old p3 comps only the server is ubuntu 11.04

---

### Post by David006 on 2011-11-07
WORKS FOR ME

I installed Mkahawa server, on Ubuntu 11.10 (Oneiric) 32bit + Unity (3D).

steps:

1. download binaries
[http://sourceforge.net/projects/mkahawa/files/](http://sourceforge.net/projects/mkahawa/files/)


2. install

:~$  **sudo dpkg -i libfox-1.6-0_1.6.36-2_i386.deb**
:~$  **sudo dpkg -i libccls_0.8.2-2_i386.deb**

:~$  **sudo dpkg -i mkahawa-srv_0.0.4-2_i386.deb**


3. Ensure any shared libraries are properly registered.

:~$  **sudo ldconfig**


4. launch (or dock to launcher, after search in dash)

:~$  **mkahawa -nossl**


5.  adjust behavior

create user-copy for launcher
```
cp /usr/share/applications/mkahawa.desktop ~/.local/share/applications/
```

edit, as required
```
gedit ~/.local/share/applications/mkahawa.desktop &
```

---

### Post by Script Warlock on 2011-11-07
> **David006 said:**
> I have been able to install Mkahawa server, on Ubuntu 11.10 (Oneiric) 32bit + Unity (3D).

steps:

1. download binaries
[http://sourceforge.net/projects/mkahawa/files/](http://sourceforge.net/projects/mkahawa/files/)


2. install

:~$  **sudo dpkg -i libfox-1.6-0_1.6.36-2_i386.deb**
:~$  **sudo dpkg -i libccls_0.8.2-2_i386.deb**

:~$  **sudo dpkg -i mkahawa-srv_0.0.4-2_i386.deb**


3. Ensure any shared libraries are properly registered.

:~$  **sudo ldconfig**


4. launch (or dock to launcher, after search in dash)

:~$  **mkahawa -nossl**


UNABLE TO SUCCEED for Mkahawa client, on Ubuntu 11.10 + Unity.

-   ( Details to follow )

> libfox-1.6-0_1.6.36-2_i386.deb the current libfox1.6 cannot run mkahawa-srv anymore that's why launching mkahawa -nossl failed or aborted.

---

### Post by David006 on 2011-11-07
Sorry, yes I caught that my self (by accident).


I ran:

~:  **sudo apt-get update && sudo apt-get upgrade**

which loaded a newer version of libfox 1.6

---

### Post by David006 on 2011-11-07
(deleted)

---

### Post by Script Warlock on 2011-11-07
> **David006 said:**
> What can I do to get Mkahawa client to work?  (on Ubuntnu 11.10)
try to compile the mkahawa client, i made a video clip please read back a couple of posts and already filed a bug report regarding libfox1.6.

---

### Post by David006 on 2011-11-07
(deleted)

---

### Post by David006 on 2011-11-07
Compiling mkahawa-client, for Ubuntu 11.0 (Oneiric):

./configure
> checking for a BSD-compatible install... /usr/bin/install -c
:
config.status: creating po/Makefile.in
config.status: WARNING:  'po/Makefile.in.in' seems to ignore the --datarootdir setting
:
config.status: error: po/Makefile.in.in was not created by intltoolize.

This WARNING can be ignored.


make
> Making all in m4
:
gui.cpp: In member function ‘void ClientWin::dispMessage(FX::FXString&, int)’:
gui.cpp:373:14: error: too many arguments to function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)’
/usr/include/libnotify/notification.h:114:21: note: declared here
make[1]: *** [gui.o] Error 1
make[1]: Leaving directory `### ###/mkahawa/mkahawa-client/src'
make: *** [all-recursive] Error 1


**EXPERTS ONLY:** This is a known bug, and was fixed for qBittorrent back in Jun/Jul.
see:
[https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff](https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff)

---

### Post by David006 on 2011-11-07
> **Script Warlock said:**
> the current libfox1.6 cannot run mkahawa-srv anymore that's why launching mkahawa -nossl failed or aborted.

This appears to be fixed, from updates.

eg.
~: **sudo apt-get update && sudo apt-get upgrade**

---

### Post by dannydynx on 2011-11-09
:confused:

Hi All,

I would like to install Mkahawa in a Cyber Cafe this weekend. I want to install Xubuntu 10.04 LTS on the clients and Ubuntu 10.04 on the Server Computer. 

1. Is this ok? so that clients can run faster since Xubuntu is lighter than Ubuntu.

2. Please advice on which packages to use for the clients and the server. 

3. Also I want to have the software launch automatically when the computers start without requesting for admin password(i have had this problem with CafeCon Leche when i use the command gksudo 'cclcfox -nossl -name $Comp1 -host $192.168.0.1' as the launch command). I also want the computers to be identifed by names i.e Comp1, Comp2 etc.

4. Also I have had a problem of computers hanging sometimes what might be the problem?

5. Also please advice can I have all the computers be allocated IP addresses automatically via DHCP but have the server computer on a static IP 192.168.0.1 will this work for the software?

Thanks for all you are doing to all other guys Script Warlock.

Regards,

---

### Post by David006 on 2011-11-09
> **dannydynx said:**
> 
I would like to install Mkahawa in a Cyber Cafe this weekend. I want to install Xubuntu 10.04 LTS on the clients and Ubuntu 10.04 on the Server Computer.

1. Is this ok? so that clients can run faster since Xubuntu is lighter than Ubuntu.
For **Ubuntu 10.04 LTS** the difference is only minor, so I would suggest just the standard version.  What are your hardware spec's?  brand/model cpu/ram/hdd


> 2. Please advice on which packages to use for the clients and the server.
Try the download page first (under 'Ubuntu')
[http://mkahawa.sourceforge.net/downloads.php](http://mkahawa.sourceforge.net/downloads.php)

> 3. Also I want to have the software launch automatically when the computers start without requesting for admin password(i have had this problem with CafeCon Leche when i use the command gksudo 'cclcfox -nossl -name $Comp1 -host $192.168.0.1' as the launch command). I also want the computers to be identifed by names i.e Comp1, Comp2 etc.
(I'll let someone else answer that.)

> 4. Also I have had a problem of computers hanging sometimes what might be the problem?
What hardware spec., what OS, what cpu/RAM/HDD?

When does it crash/lockup?  Can this be easily repeated?

GOOD LUCK ..

---

### Post by dannydynx on 2011-11-10
> **David006 said:**
> For **Ubuntu 10.04 LTS** the difference is only minor, so I would suggest just the standard version.  What are your hardware spec's?  brand/model cpu/ram/hdd

Pentium 4 3.0Ghz/40Gb/512MB but 1024MB for server computer

Try the download page first (under 'Ubuntu')
[http://mkahawa.sourceforge.net/downloads.php](http://mkahawa.sourceforge.net/downloads.php)


(I'll let someone else answer that.)


What hardware spec., what OS, what cpu/RAM/HDD?

When does it crash/lockup?  Can this be easily repeated?

GOOD LUCK ..

I hope this is all you needed

---

### Post by Script Warlock on 2011-11-10
please check again how i [compiled]("http://ubuntuforums.org/showpost.php?p=11110114&postcount=173") mkahawa...

---

### Post by Script Warlock on 2011-11-10
> **dannydynx said:**
> :confused:

Hi All,

I would like to install Mkahawa in a Cyber Cafe this weekend. I want to install Xubuntu 10.04 LTS on the clients and Ubuntu 10.04 on the Server Computer. 

1. Is this ok? so that clients can run faster since Xubuntu is lighter than Ubuntu.

2. Please advice on which packages to use for the clients and the server. 

3. Also I want to have the software launch automatically when the computers start without requesting for admin password(i have had this problem with CafeCon Leche when i use the command gksudo 'cclcfox -nossl -name $Comp1 -host $192.168.0.1' as the launch command). I also want the computers to be identifed by names i.e Comp1, Comp2 etc.

4. Also I have had a problem of computers hanging sometimes what might be the problem?

5. Also please advice can I have all the computers be allocated IP addresses automatically via DHCP but have the server computer on a static IP 192.168.0.1 will this work for the software?

Thanks for all you are doing to all other guys Script Warlock.

Regards,

1. xubuntu or any linux is fine. except ubuntu 11.10 which i'm trying to figure out why i have errors launching mkahawa.
2. mkahawa deb only needs libfox1.6
3. yes you can rename during mkahawa installation.
4. it's a hardware related problem i guess and not mkahawas unless it hinders your machines operation, does it?
5. yes you can.

---

### Post by Script Warlock on 2011-11-10
by the way theres an ongoing development of mkahawa lately and i'm trying to rewrite everything in python. hope i'm on the right track and if everything goes well then i'm going to share this by next year. awtz i'm a slow learner :P please help :(

---

### Post by David006 on 2011-11-10
> **dannydynx said:**
> Pentium 4 3.0Ghz/40Gb/512MB but 1024MB for server computer

For "***Ubuntu 10.04 LTS***", I have found an Intel **P4 2.8GHz** with **1GB** RAM and **40GB** runs very well.

With you having only **512MB** RAM, that will slow down the PC when using both OpenOffice AND browser, particularly if more than one document/spreadsheet are open.  It will also be slow when you play videos, if any other software is running.


You should use **1GB** for the PC running Mkahawa server, but I would try with only **512MB** for the clients - and later upgrade (over time) until each have **1GB**.

---

### Post by David006 on 2011-11-10
> **Script Warlock said:**
> by the way theres an ongoing development of mkahawa lately and i'm trying to rewrite everything in python. hope i'm on the right track and if everything goes well then i'm going to share this by next year. awtz i'm a slow learner :P please help :(

Happy to help in any way I can ..

---

### Post by David006 on 2011-11-10
> **Script Warlock said:**
> please check again how i [compiled]("http://ubuntuforums.org/showpost.php?p=11110114&postcount=173") mkahawa...

SNAPSHOT: Ubuntu 11.10 (32bit)

I am able to run Mkahawa Server, with only minor ascertion errors (to term).

> :~$ **mkahawa -nossl**

** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_time_left: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_products: assertion `c' failed
** (process:2946): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed


I have not been able to get Mkahawa Client to compile (see earlier post), but believe I have identified the cause of the issue with: gui.cpp "error: too many arguments".  (see UPDATE, to earlier post).

I am happy to retry comple, but the code (from SVN) still says its revision 51 (unchanged).

---

### Post by Script Warlock on 2011-11-10
wow you did it!.. thats right svn still unchanged.

---

### Post by David006 on 2011-11-10
> **Script Warlock said:**
> wow you did it!.. thats right svn still unchanged.

What next?

How do I escalate the 'gui.cpp', to get it resolved?

---

### Post by David006 on 2011-11-10
Attempting to compile Mkahawa Server (mkahawa-srv) from SVN source (rev. 51), for Ubuntu 11.10 (Oneiric), I get this error:

> :~/.bin/source/mkahawa/mkahawa-srv$ **make**       
Making all in m4
:
Making all in po
make[1]: Entering directory `/home/######/.bin/source/mkahawa/mkahawa-srv/po'
make[1]: *** No rule to make target `id_ID.gmo', needed by `all-yes'.  Stop.
make[1]: Leaving directory `/home/######/.bin/source/mkahawa/mkahawa-srv/po'
make: *** [all-recursive] Error 1

Any ideas?

---

### Post by Script Warlock on 2011-11-10
> **David006 said:**
> Attempting to compile Mkahawa Server (mkahawa-srv) from SVN source (rev. 51), for Ubuntu 11.10 (Oneiric), I get this error:



Any ideas?

open the src>linguas and delete id_ID.. to make it easier please check my signature below.

---

### Post by David006 on 2011-11-10
> **Script Warlock said:**
> heres for the client.. [mkahawa-client]("http://www.vimeo.com/27259104")
heres for the server.. [mkahawa-srv]("http://www.youtube.com/user/scriptwarlock#p/a/u/0/PCLFAsDpJH0")
checking connection.. [server-client]("http://www.youtube.com/watch?v=5q0aeDJMdH8")

In the middle of the 'client' video, there is a command typed.

You can only see:  **sudo apt-get install** ?? **tool**

2 or more characters are off-screen.


Can we assume this should be:
> **sudo apt-get install intltool**

---

### Post by Script Warlock on 2011-11-10
yes thats intltool

---

### Post by David006 on 2011-11-11
> **Script Warlock said:**
> open the src>linguas and delete id_ID.. to make it easier please check my signature below.

I needed to remove: id_ID ja it
( from ./mkahawa/mkahawa-srv/po/LINGUAS )

It now compiles from source, Thanks.

---

### Post by dannydynx on 2011-11-11
Thanks for this David

Cheers!!!

---

### Post by David006 on 2011-11-11
> **David006 said:**
> Compiling mkahawa-client, for Ubuntu 11.0 (Oneiric):

make

STILL UNABLE TO GET WORKING, for Ubuntu 11.10 (Oneiric)

**UPDATE:** This is a known bug, fixed in qBittorrent ..
see:
[https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff](https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff)

I have fixed issue with change to:

.bin/source/mkahawa/mkahawa-client/src/gui.cpp
```
    /* try the mkahawa-client notification */

    // BUGFIX:: too many arguments

/*  notification = notify_notification_new (
					    "Message from Cyber Admin:",
					    msgstr.text(),
					    "/usr/share/pixmaps/mkahawa-icon.png",
					    NULL);  */

    notification = notify_notification_new (
					    "Message from Cyber Admin:",
					    msgstr.text(),
					    "/usr/share/pixmaps/mkahawa-icon.png"
#if !defined(NOTIFY_VERSION_MINOR) || (NOTIFY_VERSION_MAJOR == 0 && NOTIFY_VERSION_MINOR < 7)
					    , NULL
#endif
					    );
    // end BUGFIX
```

How do I get this back onto SourceForge ?

---

### Post by Script Warlock on 2011-11-11
lets ask ouwor to include the fix, how did you get that bug because i can't reproduce that on my machines.

---

### Post by David006 on 2011-11-12
> **Script Warlock said:**
> lets ask ouwor to include the fix, how did you get that bug because i can't reproduce that on my machines.

I am using Ubuntu 11.10 (latest updates), and I have verified this on a test machine (with a fresh install of OS).

There is a parameter conflict between:
```
./mkahawa/mkahawa-client/src/gui.cpp:373:14
```
function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)'

and
```
/usr/include/libnotify/notification.h:114:21
```
where the function is declared.


I looks like Gnome v3 (used in Ubuntu 11.10 + Unity) now uses: **libnotify-0.7**

see:
[https://github.com/jtniehof/syslog-notify/issues/11](https://github.com/jtniehof/syslog-notify/issues/11)

look for:
"patch that works with any of libnotify-0.4.* and 0.5.* and 0.7.*"

---

### Post by David006 on 2011-11-12
similar issue for:

.bin/source/mkahawa/gtk-mkahawa-client/src/mca_info_panel.c :
```
  /* try the mkahawa-client notification */

  // BUGFIX:: too many arguments

/*
  notification = notify_notification_new (
					  "Message from Cyber Admin:",
					  infostr,
					  PACKAGE_DATA_DIR"/pixmaps/mkahawa-icon.png",
					  NULL); */

  notification = notify_notification_new (
					  "Message from Cyber Admin:",
					  infostr,
					  PACKAGE_DATA_DIR"/pixmaps/mkahawa-icon.png"
#if !defined(NOTIFY_VERSION_MINOR) || (NOTIFY_VERSION_MAJOR == 0 && NOTIFY_VERSION_MINOR < 7)
					  , NULL
#endif
					  );

  // end BUGFIX
```

---

### Post by dannydynx on 2011-11-14
> **Script Warlock said:**
> 1. xubuntu or any linux is fine. except ubuntu 11.10 which i'm trying to figure out why i have errors launching mkahawa.
2. mkahawa deb only needs libfox1.6
3. yes you can rename during mkahawa installation.
4. it's a hardware related problem i guess and not mkahawas unless it hinders your machines operation, does it?
5. yes you can.

Hi,

I installed the timer on Saturday and had some few issues:-

1. The client screen flickers with lines running down when a computer boots up. After a cold restart it starts fine. But sometimes one might even restart up to 3times the computer for the client to start ok. What could be the Problem? OS Xubuntu 10.04

2. I tried to install the print monitor module it installed fine but could not calculate automatically a print charge when the client prints what could be the problem? There is also a place on the FAQ written "Remember to put the value of on print-out as the price of the printer product." where is this applied?

3. How do I change the Lock picture on the clients?

regards,

Dan

---

### Post by Script Warlock on 2011-11-14
> **dannydynx said:**
> Hi,

I installed the timer on Saturday and had some few issues:-

1. The client screen flickers with lines running down when a computer boots up. After a cold restart it starts fine. But sometimes one might even restart up to 3times the computer for the client to start ok. What could be the Problem? OS Xubuntu 10.04

2. I tried to install the print monitor module it installed fine but could not calculate automatically a print charge when the client prints what could be the problem? There is also a place on the FAQ written "Remember to put the value of on print-out as the price of the printer product." where is this applied?

3. How do I change the Lock picture on the clients?

regards,

Dan
2. have you seen my clips for print server?
3. for the meantime you can put the lockpix inside your / dir,  this is not the proper place for the lockpix to reside but this is just a temporary place. we will correct this in the coming releases.

---

### Post by dannydynx on 2011-11-14
> **Script Warlock said:**
> 2. have you seen my clips for print server?

Yes I have seen it and used it actually to do the install. The printer is located at the server computer. Please help me or just write me a small manual on installation if there is anything i am to do extra.

Rgds,

Dan

---

### Post by kimeunice on 2011-11-15
> **Script Warlock said:**
> yes thats intltool

hi  i did the things that in the video but when i open again the terminal and try the mkahawa-client it only says mmkahawa-client command not found
can you please help...:confused:

---

### Post by David006 on 2011-11-15
> **kimeunice said:**
> hi  i did the things that in the video but when i open again the terminal and try the mkahawa-client it only says mmkahawa-client command not found
can you please help...:confused:

What operating system?  eg. RHEL, Ubuntu 11.04


Did you complete all 3 steps?

eg.
```
  ./configure
  make
  sudo make install
```

---

### Post by kimeunice on 2011-11-15
> **David006 said:**
> What operating system?  eg. RHEL, Ubuntu 11.04


Did you complete all 3 steps?

eg.
```
  ./configure
  make
  sudo make install
```

i am using ubuntu 11.10

i think i did all the steps. help..:confused:

---

### Post by David006 on 2011-11-15
> **kimeunice said:**
> i am using ubuntu 11.10

i think i did all the steps. help..:confused:

Did you get the same error I did, for step 2?

see:
[http://ubuntuforums.org/showpost.php?p=11435856&postcount=196](http://ubuntuforums.org/showpost.php?p=11435856&postcount=196)

eg.
```
~$ **make**
Making all in m4
:
gui.cpp: In member function ‘void ClientWin::dispMessage(FX::FXString&, int)’:
gui.cpp:373:14: error: too many arguments to function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)’
/usr/include/libnotify/notification.h:114:21: note: declared here
make[1]: *** [gui.o] Error 1
make[1]: Leaving directory `### ###/mkahawa/mkahawa-client/src'
make: *** [all-recursive] Error 1 
```

---

### Post by kimeunice on 2011-11-16
> **David006 said:**
> Did you get the same error I did, for step 2?

see:
[http://ubuntuforums.org/showpost.php?p=11435856&postcount=196](http://ubuntuforums.org/showpost.php?p=11435856&postcount=196)

eg.
```
~$ **make**
Making all in m4
:
gui.cpp: In member function ‘void ClientWin::dispMessage(FX::FXString&, int)’:
gui.cpp:373:14: error: too many arguments to function ‘NotifyNotification* notify_notification_new(const char*, const char*, const char*)’
/usr/include/libnotify/notification.h:114:21: note: declared here
make[1]: *** [gui.o] Error 1
make[1]: Leaving directory `### ###/mkahawa/mkahawa-client/src'
make: *** [all-recursive] Error 1 
```


and also this
 E: Unable to locate package libccls

haay... dont know what to do?

---

### Post by David006 on 2011-11-16
> **kimeunice said:**
> and also this
 E: Unable to locate package libccls

haay... dont know what to do?

**Note:** Mkahawa Server (for manager) needs two packages to be already installed: **libccls**, **libfox**.  Whereas, Mkahawa Client (for each workstations) needs two packages to be already installed: **libcclc**, **libfox**.


QUICK SUMMARY: ( specific for Ubuntu 11.10 )

For Mkahawa Server, you can just download the '.deb' files:

```
install

(download .deb files from Internet)

  [b]sudo apt-get install libfox-1.6-0

  sudo dpkg -i libccls_0.8.2-2_i386.deb

  sudo dpkg -i mkahawa-srv_0.0.4-2_i386.deb[/b]


Ensure any shared libraries are properly registered.

  **sudo ldconfig**


launch

  **mkahawa -nossl**

adjust behavior

create user-copy for launcher
  **cp /usr/share/applications/mkahawa.desktop ~/.local/share/applications/**

edit, as required
  **gedit ~/.local/share/applications/mkahawa.desktop &**
```

For Mkahawa Client, you need to compile from source.  There also some edits required (specific to Ubuntu 11.10) ..

---

### Post by kimeunice on 2011-11-16
> **David006 said:**
> Compiling mkahawa-client, for Ubuntu 11.0 (Oneiric):

./configure


**UPDATE:** I think this can just be ignored.
see:
[http://osdir.com/ml/web.bluefish.devel/2006-10/msg00043.html](http://osdir.com/ml/web.bluefish.devel/2006-10/msg00043.html)
[http://osdir.com/ml/web.bluefish.devel/2006-10/msg00030.html](http://osdir.com/ml/web.bluefish.devel/2006-10/msg00030.html)


make


STILL UNABLE TO GET WORKING, for Ubuntu 11.10 (Oneiric)

**UPDATE:** This is a known bug, fixed in qBittorrent ..
see:
[https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff](https://bugs.launchpad.net/qbittorrent/+bug/671769/+attachment/1724682/+files/libnotify-070-fix.diff)



hi what will i do with the link of the qbittorrent...

---

### Post by Script Warlock on 2011-11-16
> **kimeunice said:**
> hi  i did the things that in the video but when i open again the terminal and try the mkahawa-client it only says mmkahawa-client command not found
can you please help...:confused:

install libssl-dev when compiling mkahawa

---

### Post by David006 on 2011-11-16
> **kimeunice said:**
> hi what will i do with the link of the qbittorrent...

That link was for EXPERTS, as background information ONLY.

( I have now re-worded it. )
[http://ubuntuforums.org/showpost.php?p=11435856&postcount=196](http://ubuntuforums.org/showpost.php?p=11435856&postcount=196)


The fix (for Ubuntu 11.10) is in my earlier comment:
[http://ubuntuforums.org/showpost.php?p=11445987&postcount=215](http://ubuntuforums.org/showpost.php?p=11445987&postcount=215)

( You may want to wait for an update, by the developer. )

---

### Post by David006 on 2011-11-16
> **Script Warlock said:**
> lets ask ouwor to include the fix, how did you get that bug because i can't reproduce that on my machines.

Any update from developer?

---

### Post by kimeunice on 2011-11-17
i think i already launch it but i am now lost
is there manual on how to use this???

---

### Post by kimeunice on 2011-11-17
i receive themkahawa-client command not found again but i already launch the mkahawa

---

### Post by kimeunice on 2011-11-17
> **Script Warlock said:**
> install libssl-dev when compiling mkahawa


i already install the libssl-dev

libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 241 not upgraded.
itcenter@itcenter-System-Product-Name:~$ mkahawa-client
mkahawa-client: command not found

that's the message i got..

i am so sorry for asking you again and again
i know i am being makulit but i cant help it...

sorry....:(



also do i need to have a ubuntu server for the mkahawa server?

---

### Post by Script Warlock on 2011-11-17
> **kimeunice said:**
> i already install the libssl-dev

libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 241 not upgraded.
itcenter@itcenter-System-Product-Name:~$ mkahawa-client
mkahawa-client: command not found

that's the message i got..

i am so sorry for asking you again and again
i know i am being makulit but i cant help it...

sorry....:(





also do i need to have a ubuntu server for the mkahawa server?

did you receive any errors while compiling?.. ubuntu desktop lang pwede na.

---

### Post by Script Warlock on 2011-11-17
let me recall what i did.
install:
sqlite3 libsqlite3-dev
libssl-dev
libglib2.0-dev  -- if needed
libfox-1.6.0 libfox-1.6-dev

then compile:
./configure
make
sudo make install

reply if you have errors on my procedure.

---

### Post by kimeunice on 2011-11-17
> **Script Warlock said:**
> let me recall what i did.
install:
sqlite3 libsqlite3-dev
libssl-dev
libglib2.0-dev  -- if needed
libfox-1.6.0 libfox-1.6-dev

then compile:
./configure
make
sudo make install

reply if you have errors on my procedure.

pasensiya ka na ah..

wala naman akong naging error..
natapos ko nga yung vdeo mo kaya lang nung sa server-client na tiype ko lang yung mkahawa-client tpos command not found na yung lumabas

kailangan ba may nakainstall na kong mkahawa-client sa isang pc.?

---

### Post by Script Warlock on 2011-11-17
try vmware for the client

---

### Post by Script Warlock on 2011-11-17
an error occurred 

./configure
 --- > checking how to run the C++ preprocessor... /lib/cpp
configure: error: in `/home/client01/mkahawa/mkahawa-client':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details. install build-essential

---

### Post by Script Warlock on 2011-11-17
> **David006 said:**
> I have fixed issue with change to:

.bin/source/mkahawa/mkahawa-client/src/gui.cpp
```
    [COLOR="Blue"]/* try the mkahawa-client notification */[/COLOR]

    [COLOR="Magenta"]// BUGFIX:: too many arguments[/COLOR]

/*  notification = notify_notification_new (
					    "Message from Cyber Admin:",
					    msgstr.text(),
					    "/usr/share/pixmaps/mkahawa-icon.png",
					    NULL);  */

    notification = notify_notification_new (
					    "Message from Cyber Admin:",
					    msgstr.text(),
					    "/usr/share/pixmaps/mkahawa-icon.png"
#if !defined(NOTIFY_VERSION_MINOR) || (NOTIFY_VERSION_MAJOR == 0 && NOTIFY_VERSION_MINOR < 7)
					    , NULL
#endif
					    );
    [COLOR="Magenta"]// end BUGFIX[/COLOR]
```

How do I get this back onto SourceForge ? wow a nice bug fix, i did found out that this was really a bug while compiling the client inside vmware, big thanks to David006. unfortunately we can't put this back to the source yet, ouwor is not around. i'm going to save this one for our future references.

---

### Post by Script Warlock on 2011-11-17
> kimeunice]hi i did the instruction in the mkahawa srv in youtubeand almost cry when you type hehehe o the screen...
i just want to ask what will happen next. ???

tnx.:D hmmm the world ends? :P

---

### Post by kimeunice on 2011-11-17
> **Script Warlock said:**
> hmmm the world ends? :P

ah no...
 think the world would not end ....

i am gonna live for many years pa..

---

### Post by kimeunice on 2011-11-17
whats vmware?
what will i do if with this..


config.status: error: po/Makefile.in.in was not created by intltoolize.



help before the world ends;)

---

### Post by Script Warlock on 2011-11-17
> **kimeunice said:**
> whats vmware?
what will i do if with this..


config.status: error: po/Makefile.in.in was not created by intltoolize.



help before the world ends;)
try sa terminal intltoolize --force and then make

"akala ko kasi wala kang machine pang client at iisang pc lang ang pinaglalagyan mo sa mkahawa server at client kaya nirecommend ko ang vmware pang test mo sa mkahawa-client before install sa production machine."

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> try sa terminal intltoolize --force and then make

"akala ko kasi wala kang machine pang client at iisang pc lang ang pinaglalagyan mo sa mkahawa server at client kaya nirecommend ko ang vmware pang test mo sa mkahawa-client before install sa production machine."


force?
what will i type?

intltoolize: 'po/Makefile.in.in' exists: use '--force' to overwrite

how?

---

### Post by Script Warlock on 2011-11-18
> **kimeunice said:**
> force?
what will i type?

intltoolize: 'po/Makefile.in.in' exists: use '--force' to overwrite

how?
intltoolize --force

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> intltoolize --force

tnx for the  help.

sana hindi ka magsawa sa mga tanong ko hehehe

sana gumana narin siya sa akin....

---

### Post by kimeunice on 2011-11-18
> **kimeunice said:**
> tnx for the  help.

sana hindi ka magsawa sa mga tanong ko hehehe

sana gumana narin siya sa akin....



yehey...

ipagcoconnect ko na lang sila....

sna gumana na..:p

---

### Post by Script Warlock on 2011-11-18
> **kimeunice said:**
> tnx for the  help.

sana hindi ka magsawa sa mga tanong ko hehehe

sana gumana narin siya sa akin.... working na?

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> working na?


yes...


yes...
yes.

pno nga uli palitan ang desktop pics

---

### Post by kimeunice on 2011-11-18
> **kimeunice said:**
> yes...


yes...
yes.

pno nga uli palitan ang desktop pics

bat ganon pag tinanggal ko yung terminal hindi na rin siya makokontrol...
eh di masaya na sila..

wala bang way para hindi na ako mag paulit-ulit na terminal pag magoopen?

---

### Post by Script Warlock on 2011-11-18
> **kimeunice said:**
> bat ganon pag tinanggal ko yung terminal hindi na rin siya makokontrol...
eh di masaya na sila..

wala bang way para hindi na ako mag paulit-ulit na terminal pag magoopen?
nice, learned the hard way? pero sulit naman right?... 

prepare your lockpix and put it inside the /(root).. lockpix mo should be the same dimension sa desktop at of course your logo or something para masaya. make a scipt for that

#!/bin/bash
sleep 30 && mkahawa-client -name ANYNAME -host SERVERIP -nossl;

and save as mkahawawhatever.sh put it inside your home folder and chmod x mkahawawhatever.sh. launch the cog icon> start application.
name - whatever
command - pointing to your mkahawawhatever.sh or browse home
comments - any comments or no comments:) logout or restart kung ganahan ka.

to make it simple do the gui way. type in the terminal gksudo nautilus and simply copy paste your lockpix to /(root) and close the nautilus. and your done.. be very careful.

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> nice, learned the hard way? pero sulit naman right?... 

prepare your lockpix and put it inside the /.. lockpix mo should be the same dimension sa desktop at of course your logo or something para masaya. make a scipt for that

#!/bin/bash
sleep 30 && mkahawa-client -name ANYNAME -host SERVERIP -nossl;

and save as mkahawawhatever.sh put it inside your home folder and chmod x mkahawawhatever.sh. launch the cog icon> start application.
name - whatever
command - pointing to your mkahawawhatever.sh or browse home
comments - any comments or no comments:) logout or restart kung ganahan ka.




ahm.... saan po ba ito nakikita sorry po hindi ko maintindihan..

bago lang po

---

### Post by Script Warlock on 2011-11-18
sorry, launch text editor and type those #!bin bash thing and save as whatfile.sh at your home folder and launch terminal and type chmod +x whatfile.sh.

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> sorry, launch text editor and type those #!bin bash thing and save as whatfile.sh at your home folder and launch terminal and type chmod +x whatfile.sh.

pano kung gusto nmin pagon ng client, yung comp name niya nagddisplay na sa server?, hindi ko n kelangan itype sa terminal ito ..

 mkahawa-client -host serverip -name something -nossl

meron bang paraan?

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> sorry, launch text editor and type those #!bin bash thing and save as whatfile.sh at your home folder and launch terminal and type chmod +x whatfile.sh.


ito lang nangyayari..

itcenter@itcenter-System-Product-Name:~$ chmod +x mkahawa.sh.
itcenter@itcenter-System-Product-Name:~$ chmod +x mkahawa.sh.
itcenter@itcenter-System-Product-Name:~$ 


walang nalabas..

---

### Post by Script Warlock on 2011-11-18
ginawa lang executable ang file.
another way of doing that is to right click the file.sh and press properties> permission> check the "allow executing files as program".

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> ginawa lang executable ang file.
another way of doing that is to right click the file.sh and press properties> permission> check the "allow executing files as program".


para saan ba siya...???

alam mo kasi ubuntu kasi ang gagawin naming s ng itcenter ng school nmin..
para maiba naman tsaka matutuhan ng students yung ubuntu ...

kaya nga gusto kong maparun na ito ng maayos para naman  kahit papaano makapagsimula na kame.


pano kung gusto nmin pag-on ng client, yung comp name niya nagddisplay na  sa server?, hindi ko n kelangan itype sa terminal ito ..

 mkahawa-client -host serverip -name something -nossl

meron bang paraan?
tsaka yung hindi makikita ng students yung terminal para hindi nila ma exit at gumana pa rin ng maayos yung  mkahawa..???


salamat..:P

---

### Post by Script Warlock on 2011-11-18
we made a  startup script for mkahawa-client to start with ubuntu. backread #252 and you can view more clips on my youtube channel for more details. any name you assigned to the client will reflect to the server. after all this tedious setup of yours :) limit the account you created for your students to avoid messing with the system.

---

### Post by kimeunice on 2011-11-18
> **Script Warlock said:**
> we made a  startup script for mkahawa-client to start with ubuntu. backread #252 and you can view more clips on my youtube channel for more details. any name you assigned to the client will automatically reflect to the server. after all this tedious setup of yours :) limit the account you created for your students to avoid meesing with the system.


are 36 computer ok for the mkahawa?

---

### Post by Script Warlock on 2011-11-18
> **kimeunice said:**
> are 36 computer ok for the mkahawa? even a hundred.

---

### Post by ysNoi on 2011-11-18
> **Script Warlock said:**
> let me recall what i did.
install:
sqlite3 libsqlite3-dev
libssl-dev
libglib2.0-dev  -- if needed
libfox-1.6.0 libfox-1.6-dev

then compile:
./configure
make
sudo make install

reply if you have errors on my procedure.

Thanks sa recall bai...

Gusto ko rin try to for future use. So of course, I need to know how to install properly.

Questions:
1. Yung sa install, kailangan bang sunod-sunod ang sequence ng mga yan (unahin muna ang sqlite3 libsqlite3-dev then libfox-1.6.0 libfox-1.6-dev ang panghuli?)
2. How to compile? Hindi ko kasi alam pa yan...
3. Kailangan bang may naka-install muna na server at client before mag-run yung server?

Plan ko testing yung server sa host OS ko (Ubuntu 11.10) then yung client naman sa guest OS (WinXP).

Hope you still have time...

Daghang salamat bai...

---

### Post by David006 on 2011-11-19
> **Script Warlock said:**
> .. prepare your lockpix[.gif] and put it inside the /(root) .. should be the same dimension [as] desktop ..

type .. **gksudo nautilus** and simply copy paste your lockpix[.gif] to ..

CORRECTION:

The 'screen locked' image needs to be in: **~/.mkahawa**

eg. (assuming image file is in Pictures folder.)

```
  **mkdir ~/.mkahawa**  (unless already exists!)

  **cp ~/Pictures/MyLockImage.gif ~/.mkahawa/lockpix.gif**
```

---

### Post by Script Warlock on 2011-11-19
> **David006 said:**
> CORRECTION:

The 'screen locked' image needs to be in: **~/.mkahawa**

eg. (assuming image file is in Pictures folder.)

```
  **mkdir ~/.mkahawa**  (unless already exists!)

  **cp ~/Pictures/MyLockImage.gif ~/.mkahawa/lockpix.gif**
``` well according to ouwor there has been a flaw in putting the lockpix inside .mkahawa so he told me to put it inside the root as a "workaround" just in case.

---

### Post by Script Warlock on 2011-11-19
> **ysNoi said:**
> Thanks sa recall bai...

Gusto ko rin try to for future use. So of course, I need to know how to install properly.

Questions:
1. Yung sa install, kailangan bang sunod-sunod ang sequence ng mga yan (unahin muna ang sqlite3 libsqlite3-dev then libfox-1.6.0 libfox-1.6-dev ang panghuli?)
2. How to compile? Hindi ko kasi alam pa yan...
3. Kailangan bang may naka-install muna na server at client before mag-run yung server?

Plan ko testing yung server sa host OS ko (Ubuntu 11.10) then yung client naman sa guest OS (WinXP).

Hope you still have time...

Daghang salamat bai...
1. random pwede
2. quick view "my sig"
3. don't launch the client without the server.

i did encounter errors during compile on ubuntu 11.10 like the one David says gui.cpp. let's also ask him if he can pack mkahawa for us para dretso na ta install di na ta compile, hehehe.

---

### Post by Script Warlock on 2011-11-19
@David006, can't launch mkahawa-server in ubuntu 11.10 still stuck with this thing FXComposeContext: illegal window parameter
Aborted

---

### Post by kimeunice on 2011-11-20
wala ibang paraan para maging executable yung mkhawa sa client..
yung pag nagopen ka ng computer lalabas na agad doon yung logo ng mkahawa sa client ng hindi na gumagamit ng terminal? baka kasi maexit nila yung terminal tpos mawawalan na ng pkinabang yung server hindi na niya makikita yung client niya.

paano kaya yun?

---

### Post by Script Warlock on 2011-11-20
> **kimeunice said:**
> wala ibang paraan para maging executable yung mkhawa sa client..
yung pag nagopen ka ng computer lalabas na agad doon yung logo ng mkahawa sa client ng hindi na gumagamit ng terminal? baka kasi maexit nila yung terminal tpos mawawalan na ng pkinabang yung server hindi na niya makikita yung client niya.

paano kaya yun? what about the script we made? thats how we autolaunch mkahawa-client on startup.

---

### Post by kimeunice on 2011-11-21
> **Script Warlock said:**
> what about the script we made? thats how we autolaunch mkahawa-client on startup.


ginawa ko siya kahit nga yung lockpix kaya lang hindi ko naman alam kong paano siya papaganahin.
automatic na ba yun ?
pag nagbukas ako ng computer magautolaunch na yung client paano?

sorry ha!

---

### Post by Script Warlock on 2011-11-21
lahat naka automatic kung susundin ang lahat na instructions sa previous post natin :)

---

### Post by David006 on 2011-11-21
> **Script Warlock said:**
> @David006, can't launch mkahawa-server in ubuntu 11.10 still stuck with this thing FXComposeContext: illegal window parameter
Aborted

What do you need?

The source files.

An archive file, with folders, source, edited-source.

---

### Post by Script Warlock on 2011-11-21
> **David006 said:**
> What do you need?

The source files.

An archive file, with folders, source, edited-source. i think it's the latest libfox that causes not to run.

---

### Post by David006 on 2011-11-21
files, as suggested.

---

### Post by Script Warlock on 2011-11-21
we need to share the cleaned and corrected mkahawa source, allow me to share the files via mediafire. @David006 still no luck running mkahawa-srv on my 11.10 vmware.

---

### Post by kimeunice on 2011-11-21
> **Script Warlock said:**
> lahat naka automatic kung susundin ang lahat na instructions sa previous post natin :)


hehehe... sorry medyo eng-eng kasi ako eh..

hehehehe
nga pala yung bin/bash thing saan siya gagawin sa server ba o sa client?:P

---

### Post by Script Warlock on 2011-11-21
> **kimeunice said:**
> hehehe... sorry medyo eng-eng kasi ako eh..

hehehehe
nga pala yung bin/bash thing saan siya gagawin sa server ba o sa client?:P all clients must have those script if you want them to start at login.

---

### Post by kimeunice on 2011-11-22
> **Script Warlock said:**
> all clients must have those script if you want them to start at login.



isa pa pala

paano pag ganito ang error
E:Package 'uuid-dev' has no installation candidate

---

### Post by Script Warlock on 2011-11-22
> **kimeunice said:**
> isa pa pala

paano pag ganito ang error
E:Package 'uuid-dev' has no installation candidate installed something not related to mkahawa?

---

### Post by kimeunice on 2011-11-22
> **Script Warlock said:**
> installed something not related to mkahawa?



hindi naman doon pa lang kasi sa svn nagkakaproblema na eh..

The following packages have unmet dependencies:
 subversion : Depends: libsvn1 (= 1.6.12dfsg-4ubuntu2.1) but it is not going to be installed
E: Broken packages

yan yung error

---

### Post by Script Warlock on 2011-11-22
> **kimeunice said:**
> hindi naman doon pa lang kasi sa svn nagkakaproblema na eh..

The following packages have unmet dependencies:
 subversion : Depends: libsvn1 (= 1.6.12dfsg-4ubuntu2.1) but it is not going to be installed
E: Broken packages

yan yung error you can fix those with > sudo apt-get -f install

---

### Post by ysNoi on 2011-11-23
> **Script Warlock said:**
> 1. random pwede
2. quick view "my sig"
3. don't launch the client without the server.

i did encounter errors during compile on ubuntu 11.10 like the one David says gui.cpp. let's also ask him if he can pack mkahawa for us para dretso na ta install di na ta compile, hehehe.

Ok bro...Noted.

@David006:
Requesting here that you pack mkahawa for the direct installation...Hehehe... :)

Thanks in advanced bro...

---

### Post by David006 on 2011-11-23
The edited source files, and the executable binaries (for **Ubuntu 11.10 32bit**, were in the archive file I posted.

I can probably put together some modified '.deb' files, but it would be simpler for someone to have rights to the Source Forge site.

**@Script Warlock:** Can we ask the previous maintainer for rights?

---

### Post by Script Warlock on 2011-11-23
i have no idea of his whereabouts, maybe you can just add your name as the maintainer of the new package including ouwors as the author. by the way it's hard for me to daemonize mkahawa-client maybe you can help me for this, any idea?.

---

### Post by David006 on 2011-11-23
What we still need is a software developer, to actively maintain the codebase - as well as to look at cross-platform support, and release updates.

**STAGE 1:** I have broad experience in code review, and have written some C/C++ software, so I should be able to meet out short-term requirements. *I'm an information-security consultant (IT policy, governance) and software designer (functions, capabilities, product roadmap), so maintaining code isn't really my area of expertise.*

**STAGE 2:** I want to improve some of the product's features: configuration files, data usage (logging) and speed limits (per client), improved logging, etc.  I can probably write example code for these features, but someone needs to test all this and provide support.

**STAGE 3:** I want to develop a Mkahawa daemon (background task), with only command-line control, to run on Linux server.  This would need a new protocol and messages/status codes - to include data-usage (costs), data speed (variable, rate limiting), and other new features. This would also allow remote access (over SSH), and support multiple front-end GUI managers (based on current design).

---

### Post by ysNoi on 2011-11-23
> **David006 said:**
> What we still need is a software developer, to actively maintain the codebase - as well as to look at cross-platform support, and release updates.

**STAGE 1:** I have broad experience in code review, and have written some C/C++ software, so I should be able to meet out short-term requirements. *I'm an information-security consultant (IT policy, governance) and software designer (functions, capabilities, product roadmap), so maintaining code isn't really my area of expertise.*

**STAGE 2:** I want to improve some of the product's features: configuration files, data usage (logging) and speed limits (per client), improved logging, etc.  I can probably write example code for these features, but someone needs to test all this and provide support.

**STAGE 3:** I want to develop a Mkahawa daemon (background task), with only command-line control, to run on Linux server.  This would need a new protocol and messages/status codes - to include data-usage (costs), data speed (variable, rate limiting), and other new features. This would also allow remote access (over SSH), and support multiple front-end GUI managers (based on current design).

Wow... :KS

Those three stages are really awesome...Great contributions yan...

Ang magiging role ko dyan is to test and to provide support also pag na master na...

---

### Post by Script Warlock on 2011-11-23
if you have an urge to help mkahawa please do so, we need more like you. this is an open source project everyone is welcome to join unfortunately i can't locate ouwor(admin) yet. he told me the last time we talked that he is working in Kenya.

my only offer to his project mkahawa is to test, report, support, proposes some gui improvements(i even started to write my verions of gui using python), recommends and do other things nasty. and if ever you like me to try something i can likewise offer my cyber shop as our lab.. i got 7units of clients and a server all running 10.04lts desktop, a spare pc running ubuntu oneiric for testing some mkahawa stuff. and maybe i can run windows for the sake of testing, why not.

---

### Post by kimeunice on 2011-11-23
> **Script Warlock said:**
> if you have an urge to help mkahawa please do so, we need more like you. this is an open source project everyone is welcome to join unfortunately i can't locate ouwor(admin) yet. he told me the last time we talked that he is working in Kenya.

my only offer to his project mkahawa is to test, report, support, proposes some gui improvements(i even started to write my verions of gui using python), recommends and do other things nasty. and if ever you like me to try something i can likewise offer my cyber shop as our lab.. i got 7units of clients and a server all running 10.04lts desktop, a spare pc running ubuntu oneiric for testing some mkahawa stuff. and maybe i can run windows for the sake of testing, why not.


wow...
=D>=D>the people here  are  genius!! applause:guitar:=D>=D>

by the way thanks for the effort and time to answer my questions...Script Warlock
i really appreciate all that... and because of you we can  start tomorrow the it center with the ubuntu as O.S ..
thankyou so much ..

ps: pls help pag nag kaproblema ulit....[-o<  salamat ulit..[COLOR=Cyan] [COLOR=Red]ikaw na![/COLOR][/COLOR]:-$\\:D/

---

### Post by Script Warlock on 2011-11-23
tulong tulong lang tayo mga sir, ty din at sana dadami pa mga tutulong sa mkahawa para masaya. katulad ni David006 kung sakaling eager siyang magjoin sa project. meron nga akong nagawa na bagong gui ng mkahawa di pa lang matapos dahil nga sa sked ng gigs. at kung sakaling may problema man takbo na lang tayo sa ubuntu fb or g+ dun pwede tayo magpost siguro basta regarding mkahawa at ubuntu lang.

---

### Post by kimeunice on 2011-11-25
im here again

magtatanong lang...

bigla kasing hindi na gumana yung mkahawa...

hindi na niya nakikita ang client niya..



help naman!!!

---

### Post by mexndlovu on 2011-11-27
Lam also stuck on the below any solution to the problem
can't launch mkahawa-server in ubuntu 11.10 still stuck with this thing FXComposeContext: illegal window parameter
Aborted

---

### Post by Script Warlock on 2011-11-27
> **mexndlovu said:**
> Lam also stuck on the below any solution to the problem
can't launch mkahawa-server in ubuntu 11.10 still stuck with this thing FXComposeContext: illegal window parameter
Aborted already reported the matter to launchpad and foxtoolkit, dunno if it's a bug or what but for sure mkahawa has made no changes. let's wait for their response.

---

### Post by lacipapa on 2011-12-16
There are two problems:
Server does not shut down the client nor the shotdown or a reboot does not work.
I can not find either the server or the client's name or similar names lockpix.gif lock screen.
Unfortunately, I do not speak English, so the Google translate.

---

### Post by Script Warlock on 2011-12-16
> **lacipapa said:**
> There are two problems:
Server does not shut down the client nor the shotdown or a reboot does not work.
I can not find either the server or the client's name or similar names lockpix.gif lock screen.
Unfortunately, I do not speak English, so the Google translate.

open client machine terminal:

$ chmod 7755 /sbin/shutdown
$ chmod 7755 /sbin/reboot

---

### Post by GaryMac on 2012-01-07
Hi       
 
Am in Spain being hounded by Sogelise (Microsoft Watchdogs) have installed Mkahawa on Ubuntu 10.04 (both server & client) .. my problem is the Tariff Settings ..
Have watched Scriptwarlords Videos ..  have searched Mkahawa Sourceforge site.
Cannot get these tariffs set up correctly.
Sometimes the server says one price & the client another.
 
We have a minimum price 0.60 cents for 20 mins
Price per hour = 2 euro 
 
Whatever I try does not work.  I have experimented over the last two days ..  changing the Tariff Settings and Cyber Settings without success - not even getting close.
 
Anyone any ideas ... it should be straightforward - right ??
I thought ...
Hourly Rate = 2.00
Fraction After = 21
Add Price =   at 20 mins  = 0.60
 
Rounding Off = tried everything - nothing works - not even sure what it means.
But I would "think" it should be set to zero?
 
I have made sure that after every change - changes have been Saved & Applied.
 
FOR THE SETTINGS I THOUGHT I SHOULD USE ...
Server starts at 1.00 euro .. client starts at 1.00 euro
 
 
I have tried Adding Prices for EVERY minutue ..  with zero Fraction  zero Hour Rate
So this should reflect my price each minute ... I would have thought ..
Added these ...
0 = 0.20
2 = 0.40
4 = 0.60
20 = 0.80
 
Result =  0.00 euro  on both server & client  ....   from 0 to 5 minutes. 
 
Mkahawa also changes the prices I input from time to time ..  on the above example the 4 = 0.60  was altered to  4 = 0.59
 
 
Am I doing something wrong ..  ??   Do I need to re-install Mkahawa ??
Am I stupid ??
 
Sorry to be a pain ...

---

### Post by Script Warlock on 2012-01-08
> **GaryMac said:**
> Hi       
 
Am in Spain being hounded by Sogelise (Microsoft Watchdogs) have installed Mkahawa on Ubuntu 10.04 (both server & client) .. my problem is the Tariff Settings ..
Have watched Scriptwarlords Videos ..  have searched Mkahawa Sourceforge site.
Cannot get these tariffs set up correctly.
Sometimes the server says one price & the client another.
 
We have a minimum price 0.60 cents for 20 mins
Price per hour = 2 euro 
 
Whatever I try does not work.  I have experimented over the last two days ..  changing the Tariff Settings and Cyber Settings without success - not even getting close.
 
Anyone any ideas ... it should be straightforward - right ??
I thought ...
Hourly Rate = 2.00
Fraction After = 21
Add Price =   at 20 mins  = 0.60
 
Rounding Off = tried everything - nothing works - not even sure what it means.
But I would "think" it should be set to zero?
 
I have made sure that after every change - changes have been Saved & Applied.
 
FOR THE SETTINGS I THOUGHT I SHOULD USE ...
Server starts at 1.00 euro .. client starts at 1.00 euro
 
 
I have tried Adding Prices for EVERY minutue ..  with zero Fraction  zero Hour Rate
So this should reflect my price each minute ... I would have thought ..
Added these ...
0 = 0.20
2 = 0.40
4 = 0.60
20 = 0.80
 
Result =  0.00 euro  on both server & client  ....   from 0 to 5 minutes. 
 
Mkahawa also changes the prices I input from time to time ..  on the above example the 4 = 0.60  was altered to  4 = 0.59
 
 
Am I doing something wrong ..  ??   Do I need to re-install Mkahawa ??
Am I stupid ??
 
Sorry to be a pain ...

are you using the latest libccls and mkahawa?

---

### Post by GaryMac on 2012-01-09
Hi Scriptwarlock ...    (great work by the way)
 
I installed both the Server & Clients as per your videos ...


Server was installed Nov 18th

Clients were installed in Dec 
 
Nowhere in the videos does it mention libccls 
 
I assume therefore that the libccls is installed with the initial  [FONT=Courier New][SIZE=2]command  ....[/SIZE][/FONT]
[FONT=Calibri][FONT=Courier New]svn co [https://mkahawa.svn.sourceforge.net/svnroot/mkahawa](https://mkahawa.svn.sourceforge.net/svnroot/mkahawa) mkahawa 


I will try today with two fresh installs .. again as per your videos ..[/FONT][/FONT]
[FONT=Calibri][FONT=Courier New]CLIENT :  [FONT=Segoe UI]**[http://vimeo.com/27259104](http://vimeo.com/27259104)**[/FONT][/FONT][/FONT]
[FONT=Calibri][FONT=Courier New][FONT=Segoe UI]**SERVER : [FONT=Segoe UI][[B][COLOR=#0000ff]http://www.youtube.com/user/scriptwarlock#p/u[/COLOR]**]("http://www.youtube.com/user/scriptwarlock#p/u")[/FONT][/B][/FONT][/FONT][/FONT]
[FONT=Calibri][FONT=Courier New][FONT=Segoe UI]**[FONT=Segoe UI][/FONT]**[/FONT][/FONT][/FONT] 
[FONT=Calibri][FONT=Courier New][FONT=Segoe UI]**[FONT=Segoe UI]And will see if I can then set the Tariff ...  let you know ..  thanks.[/FONT]**[/FONT]    [/FONT][/FONT]

---

### Post by GaryMac on 2012-01-09
[SIZE=2]Well ... the compiling of Mkahawa this time gave different results to the last install.[/SIZE]
 
[SIZE=2]Many more errors .. which I tried to second guess ...[/SIZE]
 
[SIZE=2]On the last install of Mkahawa SERVER .. things went exactly as Scriptwarlocks video.[/SIZE]
 
[SIZE=2]TODAY I again follow the video .. installing Mkahawa on a "clean" install of Ubuntu 10.04 [/SIZE]
[SIZE=2]But today ..... four new errors which I tried to correct .. the last one though had me stuck.[/SIZE]
 
[SIZE=2]1. After the SQLITE3 install ... [/SIZE]
[SIZE=2]I got configure error : please install glib2 - So I install libglib2.0-dev[/SIZE]
 
[SIZE=2]2. Straight after the error above ...[/SIZE]
[SIZE=2]please install openssl and openssl is already installed [/SIZE]
[SIZE=2]So ... I look for other possible packages ... I install libssl-dev[/SIZE]
 
[SIZE=2]3. After the install of [FONT=Segoe UI]intltool ...[/FONT][/SIZE]
[FONT=Segoe UI][FONT=Verdana][SIZE=2]configure: error: in ‘/home/server/mkahawa/mkahawa-srv’:[/SIZE][/FONT]
[SIZE=2][FONT=Segoe UI]Configure: error: C++ pre-processor “/lib/cpp” fails sanity check[/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI]See ‘config.log’ for more details[/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI]So I installed g++-4.4 (a wild guess – The GNU C++ compiler for Ubuntu)[/FONT][/SIZE]
 
[SIZE=2][FONT=Segoe UI]4. After the [FONT=Segoe UI]libfox-1.6-dev install ....[/FONT][/FONT][/SIZE]
[FONT=Segoe UI][SIZE=2][FONT=Segoe UI][FONT=Verdana][SIZE=2]checking for iconv... no, consider installing GNU libiconv[/SIZE][/FONT][/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI][SIZE=2][FONT=Segoe UI]checking for GNU gettext in libintl... no[/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI]checking whether to use NLS... no[/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI]checking for fxfindfox in -lFOX-1.6... no[/FONT][/SIZE]
[SIZE=2][FONT=Segoe UI]configure: error: please install fox 1.6[/FONT][/SIZE][/FONT][/SIZE][/FONT][/FONT]
 
[SIZE=2]Here I have no idea what to do. There is nothing called fox 1.6 to install.[/SIZE]
 
[SIZE=2]I am a complete novice with Ubuntu ... but having to learn fast.[/SIZE]

 

[SIZE=2]So ... the reason for the "extra" errors must be a Mkahawa update ?[/SIZE]
 
[SIZE=2]I will try the Client install .. tomorrow first thing (Spanish time).[/SIZE]

---

### Post by GaryMac on 2012-01-09
Sorry should have done the search on this ...
Although princessmarisa is configuring the CLIENT here .. it is the same error. 
 
Posted By : princessmarisa #25 #26 #27
 
When I try to configure and make the client package I get
checking for fxfindfox in -lFOX-1.6... no
configure: error: please install fox 1.6
errors
latest version of libfox1.6 and libfox dev are both installed.
Running the latest version of ubuntu
 
I fixed my problems
Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include
as it was looking for them only in usr/local/lib and usr/local/include
also added -prefix='/usr' to install it where I wanted it
 
[SIZE=3]PROBLEM : I have not got a clue what princessmarisa means in the last paragraph ..[/SIZE]
[SIZE=3]Could someone explain this please ... are these terminal commands ? [/SIZE]
 
*Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include*
*as it was looking for them only in usr/local/lib and usr/local/include*
*also added -prefix='/usr' to install it where I wanted it*

---

### Post by princessmarisa on 2012-01-09
> **GaryMac said:**
> Sorry should have done the search on this ...
Although princessmarisa is configuring the CLIENT here .. it is the same error. 
 
Posted By : princessmarisa #25 #26 #27
 
When I try to configure and make the client package I get
checking for fxfindfox in -lFOX-1.6... no
configure: error: please install fox 1.6
errors
latest version of libfox1.6 and libfox dev are both installed.
Running the latest version of ubuntu
 
I fixed my problems
Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include
as it was looking for them only in usr/local/lib and usr/local/include
also added -prefix='/usr' to install it where I wanted it
 
[SIZE=3]PROBLEM : I have not got a clue what princessmarisa means in the last paragraph ..[/SIZE]
[SIZE=3]Could someone explain this please ... are these terminal commands ? [/SIZE]
 
*Just incase anyone else has the same ones the solution was when doing the ./configure to use -x-libraries usr/lib and -x-includes usr/include*
*as it was looking for them only in usr/local/lib and usr/local/include*
*also added -prefix='/usr' to install it where I wanted it*

This was a long time ago, but IIRC I am talking about directories, when i depacked and installed it i added the /usr line to the mkahwa config file so that it would install it in the correct place
If anyone knows better what I might have meant feel free to remind me.

---

### Post by GaryMac on 2012-01-10
Thanks for the reply princessmarisa  ...
 
Can you possible elaborate a little though ..
 
I have a configure file inside the Home/Mkahawa folder ...
 
And on this file I can see this ...
 
 --x)
    # Obsolete; use --with-x.
    with_x=yes ;;
  -x-includes | --x-includes | --x-include | --x-includ | --x-inclu \
  | --x-incl | --x-inc | --x-in | --x-i)
    ac_prev=x_includes ;;
  -x-includes=* | --x-includes=* | --x-include=* | --x-includ=* | --x-inclu=* \
  | --x-incl=* | --x-inc=* | --x-in=* | --x-i=*)
    x_includes=$ac_optarg ;;
  -x-libraries | --x-libraries | --x-librarie | --x-librari \
  | --x-librar | --x-libra | --x-libr | --x-lib | --x-li | --x-l)
    ac_prev=x_libraries ;;
  -x-libraries=* | --x-libraries=* | --x-librarie=* | --x-librari=* \
  | --x-librar=* | --x-libra=* | --x-libr=* | --x-lib=* | --x-li=* | --x-l=*)
    x_libraries=$ac_optarg ;;
 
 
I have to type in   usr/lib  and    usr/include   somewhere ...  is this correct ?

But where ?
 
 
Would love to get Mkahawa up & running ..  then I can move all the PCs over to Ubuntu.
 
Cheers in advance for any help you can provide.
Gary

---

### Post by GaryMac on 2012-01-11
[SIZE=2]Installed Mkahawa Server on Ubuntu 11.10 today ... got same errors as on 10.04.[/SIZE]
[SIZE=2]
But this time the packages I installed in the compile process were ...[/SIZE]

libsqlite3-dev (3.7.7-2ubuntu2)
sqlite3 (3.7.7-2ubuntu2)

libglib2.0-dev (2.30.0-0ubuntu4)
zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu3)

libssl-dev (1.0.0e-2ubuntu4)
libssl-doc (1.0.0e-2ubuntu4)

intltool (0.41.1-2)

g++-4.6 (4.6.1-9ubuntu3)

libfox-1.6-dev (1.6.44-1.1ubuntu1)

g++ (4:4.6.1-2ubuntu5)

This seemed to solve all errors.


[SIZE=2]But I now get the Launch Error ...[/SIZE]
FXComposeContext: illegal window parameter
Aborted


[SIZE=3]And I assume that this has not been solved yet ?[/SIZE]

---

### Post by Script Warlock on 2012-01-11
> **GaryMac said:**
> [SIZE=2]Installed Mkahawa Server on Ubuntu 11.10 today ... got same errors as on 10.04.[/SIZE]
[SIZE=2]
But this time the packages I installed in the compile process were ...[/SIZE]

libsqlite3-dev (3.7.7-2ubuntu2)
sqlite3 (3.7.7-2ubuntu2)

libglib2.0-dev (2.30.0-0ubuntu4)
zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu3)

libssl-dev (1.0.0e-2ubuntu4)
libssl-doc (1.0.0e-2ubuntu4)

intltool (0.41.1-2)

g++-4.6 (4.6.1-9ubuntu3)

libfox-1.6-dev (1.6.44-1.1ubuntu1)

g++ (4:4.6.1-2ubuntu5)

This seemed to solve all errors.


[SIZE=2]But I now get the Launch Error ...[/SIZE]
FXComposeContext: illegal window parameter
Aborted


[SIZE=3]And I assume that this has not been solved yet ?[/SIZE] yes..

---

### Post by GaryMac on 2012-01-11
Sorry ... Mr Script W ...
 
 
 
You mean ...
 
no the problem has not been solved 
 
OR 
 
yes the problem HAS been solved
 
 
Cheers

---

### Post by GaryMac on 2012-01-12
#272    Script warlock  =  i think it's the latest libfox that causes not to run.


I tried - unsucessfully to install    from here :  [http://www.fox-toolkit.org/](http://www.fox-toolkit.org/)
 
[fox-1.4.35.tar.gz]("ftp://ftp.fox-toolkit.org/pub/fox-1.4.35.tar.gz") (OLD STABLE).

But got errors which I did not understand & could not fix.
 
 
 
Is there any way to get Mkahawa up & running at the moment ??

---

### Post by GaryMac on 2012-01-13
[COLOR=black][FONT=Segoe UI]I managed to Install Mkahawa SERVER on Ubuntu 11.10 today ...[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]And without the FXComposeContext: illegal window parameter error[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]Hoping that this would solve my TARIFF issues ...[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]As previously mentioned ... BUT it did not.[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]Impossible to set Tariff correctly ... [/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]Most times Server says one thing & Client another.[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]Clients are Unbuntu 10.04.[/FONT][/COLOR]
 
[COLOR=black][FONT=Segoe UI]I will now try to reinstall one of the Client PCs and see if this fixes the Tariff Issue.[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]If not then this has to be the end of the line for Mkahawa (for me) ....[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI]Wasting too much time on this.[/FONT][/COLOR]
 
[FONT=Segoe UI][COLOR=black]For anyone who wants to install Mkahawa SERVER on Ubuntu 11.10 without the FXComposeContext: illegal window parameter error ...[/COLOR][/FONT]
 
[FONT=Segoe UI][COLOR=black]Heres how :[/COLOR][/FONT]
 
[FONT=Segoe UI]sudo apt-get install subversion[/FONT]
 
[FONT=Segoe UI]svn co [https://mkahawa.svn.sourceforge.net/svnroot/mkahawa](https://mkahawa.svn.sourceforge.net/svnroot/mkahawa) mkahawa[/FONT]
 
[FONT=Segoe UI][COLOR=black][[COLOR=#0000ff]http://www.mkahawa.net/downloads/libfox-1.6-0_1.6.36-2_i386.deb[/COLOR]]("http://www.mkahawa.net/downloads/libfox-1.6-0_1.6.36-2_i386.deb") [/COLOR][/FONT]
[COLOR=black][FONT=Segoe UI]Download & install libfox-1.6-0_1.6.36-2_i386.deb[/FONT][/COLOR]
 
[FONT=Segoe UI][COLOR=black]cd mkahawa >> cd libccls >> ./configure [/COLOR][/FONT]
 
[FONT=Segoe UI][COLOR=black]ON error - install glib2 install libglib2.0-dev >> ./configure = no errors[/COLOR][/FONT]
 
[FONT=Segoe UI][COLOR=black]>> make ON [makefile.in] error 1 Go Home/mkahawa/libccls/makefile.ini ... and change 1.11 to 1.11.1 & save file >> make >> sudo make install[/COLOR][/FONT]
 
[FONT=Segoe UI][COLOR=black]cd mkahawa-srv >> ./configure ON intltool error install intltool >> ./configure [/COLOR][/FONT]
 
[FONT=Segoe UI][COLOR=black]Then we come to the error ...[/COLOR][/FONT]
[COLOR=black][FONT=Segoe UI]checking for fxfindfox in -lFOX-1.6... no[/FONT][/COLOR]
[FONT=Segoe UI][COLOR=black]configure: error: please install fox 1.6[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=black]errors[/COLOR][/FONT]
[COLOR=black][FONT=Segoe UI]Download & install libfox-1.6-dev_1.6.36-2_i386.deb[/FONT][/COLOR]
[COLOR=black][FONT=Segoe UI][[COLOR=#0000ff]http://packages.ubuntu.com/lucid/i386/libfox-1.6-dev/download[/COLOR]]("http://packages.ubuntu.com/lucid/i386/libfox-1.6-dev/download")[/FONT]
 
[FONT=Segoe UI]>> ./configure = no errors[/FONT]
 
[FONT=Segoe UI]>> make [all-recursive] Error 1 [/FONT][/COLOR]
[FONT=Segoe UI]Go Home – mkahawa – mkahawa-srv - po folder - Linguas document .. delete these id-ID ja it and save file.[/FONT]
 
[FONT=Segoe UI]>> make >> sudo make install [/FONT]
[FONT=Segoe UI]THATS IT.[/FONT]
[FONT=Segoe UI]To launch .... in terminal ... mkahawa -nossl [/FONT]

---

### Post by pmwangi80ke on 2012-01-13
Hi guys
I installed mkahawa-printer following Scriptwarlock's video [http://www.youtube.com/watch?v=HYT9L5NOTzk&noredirect=1](http://www.youtube.com/watch?v=HYT9L5NOTzk&noredirect=1). My print server is running on ubuntu 11.04 and clients on lubuntu 11.04(lxde). The issue is am able to launch the mkahawa-printer but when I print, I dont get any printout counts. I use the command mkahawa-printer -nossl -name printserver -host 192.168.1.3. under -name i have  Epson-Stylus-T50(which is my printer). Also tried naming it PrintServer. I also did creat a new product in the mkahawa server with the printer details. Finally i tried renaming and reinstalling the printer but nothing does it. Is there something am not doing right.

Please help me here....

br..

---

### Post by Script Warlock on 2012-01-14
@pmwangi80ke, missed something?

---

### Post by pmwangi80ke on 2012-01-14
> **Script Warlock said:**
> @pmwangi80ke, missed something?

Hi
My question is whether there is something am not doing right coz i dont get any printout counts on the server. FYI installation part was ok. I highly suspect am missing a step at the operational stage.

br..

---

### Post by Script Warlock on 2012-01-17
"FXComposeContext: illegal window parameter Aborted" was fixed by ouwor please update your svn...

---

### Post by ireri on 2012-01-23
already installed mkahawa libraries on the server,fixed the libfox issue but even after managing to get the mkahawa GUI after typing mkahawa -nossl on the terminal am still getting this message...(process:3104): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

ubuntu 11.10 is so not making my day...i have installed mkahawa on all ubuntu distros but on 11.10 ???????

---

### Post by Script Warlock on 2012-01-24
> **ireri said:**
> already installed mkahawa libraries on the server,fixed the libfox issue but even after managing to get the mkahawa GUI after typing mkahawa -nossl on the terminal am still getting this message...(process:3104): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_time_left: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_owed_products: assertion `c' failed

** (process:3104): CRITICAL **: CCL_client_owed_terminal: assertion `c' failed

ubuntu 11.10 is so not making my day...i have installed mkahawa on all ubuntu distros but on 11.10 ??????? assertions... nothing to worry i guess, for now, unless it crashes mkahawa. same assertions with "update-manager -d" in the terminal on ubuntu 11.10.

---

### Post by tonix1975 on 2012-02-10
bossing pede ba ma terminate ang application sa client?:D

---

### Post by Script Warlock on 2012-02-11
> **tonix1975 said:**
> bossing pede ba ma terminate ang application sa client?:D may patch na ginawa yung isang user ng mkahawa na pwede nga autokill kung sakaling mag logout ang client di pa lang naimpliment. but if you mean na makikita at materminate ang mga running processes sa client from server yun ang wala pa sa mkahawa and we will include that also sa wishlist.

---

### Post by tonix1975 on 2012-02-12
> **Script Warlock said:**
> may patch na ginawa yung isang user ng mkahawa na pwede nga autokill kung sakaling mag logout ang client di pa lang naimpliment. but if you mean na makikita at materminate ang mga running processes sa client from server yun ang wala pa sa mkahawa and we will include that also sa wishlist.

salamat sa reply bossing..ok kaayo.

may ask pa ako boss? 

paano ba gamitin ang tarrif for example gawin kung 10php\hr wala kasi  .17  

ang gawin ko kasi ganito

may: 15\hr    .25  meron na nito
     10\hr    .17
     12.50\hr .21
     11.25\hr .19
     5.7\hr   .10
mga ganyan po bossing paano ba gawin sa tarrif yan?

---

### Post by Script Warlock on 2012-02-12
> **tonix1975 said:**
> salamat sa reply bossing..ok kaayo.

may ask pa ako boss? 

paano ba gamitin ang tarrif for example gawin kung 10php\hr wala kasi  .17  

ang gawin ko kasi ganito

may: 15\hr    .25  meron na nito
     10\hr    .17
     12.50\hr .21
     11.25\hr .19
     5.7\hr   .10
mga ganyan po bossing paano ba gawin sa tarrif yan? pwede ka makagawa ng sariling tariff rate pero sa source mo gagawin before compiling mkahawa server.

---

### Post by tonix1975 on 2012-02-13
> **Script Warlock said:**
> pwede ka makagawa ng sariling tariff rate pero sa source mo gagawin before compiling mkahawa server.

ah ok po bossing salamat ng marami...:o

---

### Post by tonix1975 on 2012-02-16
bossing [B]Script Warlock paano ba gawin kung down po ang mkahawa-srv tapos gusto kung mag log in sa mkahawa-client paano ba maka log in? hindi kasi maka pasok sa member log in kung down ang server nya any idea?:(
[/B]

---

### Post by tonix1975 on 2012-02-21
3 days until now gamit ko ubuntu 11.10 with mkahawa cafe timer cool. thanks bossing Script Warlock in all devs. see more development to come. :popcorn:

---

### Post by tonix1975 on 2012-02-22
wew i notice when i remote shutdown machine , the client cannot tottaly shutdown i see power always on in also power light. i always press the power button when i off the cpu.. pls help! sayang ang kuryent lagi naka On ang cpu huhuhu:(

---

### Post by Script Warlock on 2012-02-22
> **tonix1975 said:**
> wew i notice when i remote shutdown machine , the client cannot tottaly shutdown i see power always on in also power light. i always press the power button when i off the cpu.. pls help! sayang ang kuryent lagi naka On ang cpu huhuhu:( try [this]("http://ubuntuforums.org/showpost.php?p=11262291&postcount=179")

---

### Post by tonix1975 on 2012-02-23
> **Script Warlock said:**
> try [this]("http://ubuntuforums.org/showpost.php?p=11262291&postcount=179")


ginawa ko na po pero ganon pa rin po bali naka shut down lang ang machine pero whole power ng cpu talaga at maging ang ilaw ng cpu naka power pa rin po..

---

### Post by Script Warlock on 2012-02-23
> **tonix1975 said:**
> ginawa ko na po pero ganon pa rin po bali naka shut down lang ang machine pero whole power ng cpu talaga at maging ang ilaw ng cpu naka power pa rin po.. try to shutdown the client without using mkahawa. para malaman natin saan nanggaling ang problema.

---

### Post by tonix1975 on 2012-02-23
> **Script Warlock said:**
> try to shutdown the client without using mkahawa. para malaman natin saan nanggaling ang problema.

try ko na pong ginamit sa client mismo ako nag shut down ok naman po ma shut down xa at pati power naka off naman po pati ilaw ng cpu., tottaly shut down or power down talaga. pero kapag sa mkahawa server napo ako mag client shut down may power pong naiiwan..paano kaya ito?:(

---

### Post by tonix1975 on 2012-02-24
saan ba dito ang tama?

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

or ito

sudo chmod 7755 /sbin/shutdown
sudo chmod 7755 /sbin/reboot

pag ito kasi ang i type ko sa terminal
chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

ganito po ang error \sbin\shutdown not permitted po..

baka dito po ako nagka problem sa power shut down po. any idea po bossing?
:(

cnxa napo kayo noob lang talaga galing po kasi ako kay m$ huhuhu

---

### Post by Script Warlock on 2012-02-26
> **tonix1975 said:**
> saan ba dito ang tama?

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

or ito

sudo chmod 7755 /sbin/shutdown
sudo chmod 7755 /sbin/reboot

pag ito kasi ang i type ko sa terminal
chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

ganito po ang error \sbin\shutdown not permitted po..

baka dito po ako nagka problem sa power shut down po. any idea po bossing?
:(

cnxa napo kayo noob lang talaga galing po kasi ako kay m$ huhuhu use sudo.

---

### Post by tonix1975 on 2012-02-26
> **Script Warlock said:**
> use sudo.

ok po yun po ginamit ko po, ganon po ayaw parin talaga mag tottaly shutdown yung pc po meron talaga naiiwan na power umaandar parin po yung power supply, pero pag manually press ko yung power shut down sa cpu mag shut down naman po xa. ano kaya problem nito? sayang kasi ang kuryente. :confused:

---

### Post by Script Warlock on 2012-02-27
> **tonix1975 said:**
> ok po yun po ginamit ko po, ganon po ayaw parin talaga mag tottaly shutdown yung pc po meron talaga naiiwan na power umaandar parin po yung power supply, pero pag manually press ko yung power shut down sa cpu mag shut down naman po xa. ano kaya problem nito? sayang kasi ang kuryente. :confused: we will investigate further sa issue sir kasi di ko pa na experience sa mga machines ko except lang kung may problema ang OS. i'm trying to reproduce the problem, anong ubuntu release ang ginamitan mo sa mkahawa server at client.

---

### Post by tonix1975 on 2012-02-27
> **Script Warlock said:**
> we will investigate further sa issue sir kasi di ko pa na experience sa mga machines ko except lang kung may problema ang OS. i'm trying to reproduce the problem, anong ubuntu release ang ginamitan mo sa mkahawa server at client.

Ubuntu 11.10 yung ginamit sir. oo nga sir talagang ayaw mag tottaly shutdown yung client pc ko hinahanapan ko rin ng sulosyun, ang ginawa ko nalang ay manually shut nalang para tottaly mag turn off ang pc ko.. salamat ng marami sir sa mga replys..

---

### Post by tonix1975 on 2012-03-01
bossing script baka dito ako nag kamali,.? 

may ubuntu server at ubuntu desktop kahit saan ba dyan pede gamitin? o gamitin talaga ang ubuntu server para sa mkahawa srv? :confused:

---

### Post by Script Warlock on 2012-03-01
> **tonix1975 said:**
> bossing script baka dito ako nag kamali,.? 

may ubuntu server at ubuntu desktop kahit saan ba dyan pede gamitin? o gamitin talaga ang ubuntu server para sa mkahawa srv? :confused: of course sa server at client magkaiba so dapat mga dependencies ng mkahawa-srv at client kailngan ay nasa tamang machine. doble ba pagkainstall?

---

### Post by tonix1975 on 2012-03-05
bossing ok naman hindi naman doble pagka install i mean kung ubuntu server ba dapat mkahawa-srv din ang i install at kung ubuntu desktop ay dapat mkahawa-client ang naka install?
ok bossing script salamat ng marami sorry now ko lang ito nabasa busy din kasi..:)

---

### Post by tonix1975 on 2012-03-09
@bossing script ito latest na napansin ko tungkol parin sa hindi ma shut na tottaly yung client ko, pag i shut down ko ang client gamit ang mkahawa server parang naka hung lang yung pc tapos may logo ng ubuntu naka apear. wew ano kaya yun?:confused:

---

### Post by Script Warlock on 2012-03-10
> **tonix1975 said:**
> @bossing script ito latest na napansin ko tungkol parin sa hindi ma shut na tottaly yung client ko, pag i shut down ko ang client gamit ang mkahawa server parang naka hung lang yung pc tapos may logo ng ubuntu naka apear. wew ano kaya yun?:confused: will check tomorrow pasensya na at medyo busy sa trabaho. work natin bukas sa hapon ang para sa 11.10 at 12.04LTS.

---

### Post by tonix1975 on 2012-03-12
> **Script Warlock said:**
> will check tomorrow pasensya na at medyo busy sa trabaho. work natin bukas sa hapon ang para sa 11.10 at 12.04LTS.

ok bossing salamat ng marami.

---

### Post by Script Warlock on 2012-03-13
> **tonix1975 said:**
> ok bossing salamat ng marami.
without launching anything except sa terminal can you try 
"sudo shutdown now"

---

### Post by tonix1975 on 2012-03-15
> **Script Warlock said:**
> without launching anything except sa terminal can you try 
"sudo shutdown now"

try ko na ito bossing shutdown naman xa. :confused:

---

### Post by Script Warlock on 2012-03-15
papalitan lang natin ang sa server na command dahil nagbago ata yung sa ubuntu security kaya siguro di ma power down ng completo ang sytem as command ng mkahawa server.

---

### Post by tonix1975 on 2012-03-16
> **Script Warlock said:**
> papalitan lang natin ang sa server na command dahil nagbago ata yung sa ubuntu security kaya siguro di ma power down ng completo ang sytem as command ng mkahawa server.

bossing di ko gets ito. paano ba ito? very nobei pa talaga ako.:confused:

---

### Post by antonio148 on 2012-03-25
> **Script Warlock said:**
> "FXComposeContext: illegal window parameter Aborted" was fixed by ouwor please update your svn...



hello.
i'm facing this error too
i'm using mkahawa-srv_0.0.4-2_i386.deb  on Ubuntu 11.10 all was working about 5 days, but today server not start. i have lot of members already registered on system.


thanks in advance for any guidance



edit:

uninstalled. deb, and installed the svn is working, but I can not view the tickets, when I click the refresh button the program freezes, and the terminal prints repeatedly: CRITICAL **: CCL_client_owed_terminal: assertion `c 'failed.


thanks.

---

### Post by gracey143 on 2012-03-26
hi, any idea on why the blank screen option in mkahawa server functions but the reboot or shutdown option wont function? Pasenxa na po noob eh.. Thanks =)

OS: Zorin 5.2 32bit

---

### Post by tonix1975 on 2012-03-27
> **gracey143 said:**
> hi, any idea on why the blank screen option in mkahawa server functions but the reboot or shutdown option wont function? Pasenxa na po noob eh.. Thanks =)

OS: Zorin 5.2 32bit

try this on client side type in terminal

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot

---

### Post by gracey143 on 2012-03-27
> **tonix1975 said:**
> try this on client side type in terminal

chmod 7755 /sbin/shutdown
chmod 7755 /sbin/reboot



Is there any other way to control it using the Mkahawa Server? Kasi i don't want to individually shut down the computers... I have 20 computers and i want to control the reboot or shutdown option using the Mkahawa server. Actually i tried to work all these last month with the same OS and everything went fine. I could reboot or shutdown my computers at home using the Mkahawa Server but when i tried it again this time hindi na po nagfufunction... except po sa blank screen option po pag e-right click ung client name sa Mkahawa Server ung lang po ang nagfufunction... :(  

Thank you for your time. :)

---

### Post by Script Warlock on 2012-03-28
sorry sa abala nabusy lang sa business gusto sana ng developer na isabay na ang release ng mkahawa sa ubuntu 12.04. pero titingnan natin ang workaround sa isyong yan. you can connect with us sa [COLOR="Magenta"][COLOR="Blue"]mkahawa_support[/COLOR][/COLOR] click yung link sa sig ko at login lang sa skype available ako dun anytime.

---

### Post by Script Warlock on 2012-03-29
> **gracey143 said:**
> Is there any other way to control it using the Mkahawa Server? Kasi i don't want to individually shut down the computers... I have 20 computers and i want to control the reboot or shutdown option using the Mkahawa server. Actually i tried to work all these last month with the same OS and everything went fine. I could reboot or shutdown my computers at home using the Mkahawa Server but when i tried it again this time hindi na po nagfufunction... except po sa blank screen option po pag e-right click ung client name sa Mkahawa Server ung lang po ang nagfufunction... :(  

Thank you for your time. :) already solved via [tonix1975]("http://ubuntuforums.org/showpost.php?p=11796745&postcount=341") suggestion

---

### Post by Script Warlock on 2012-03-29
@tonix, try this workaround for incomplete client shutdown...

fire up gedit and open > mkahawa > mkahawa-client > src > cclcfox.cpp

find: line-331 col-17
> system("/sbin/halt"); and change to > system("/sbin/poweroff"); exit and recompile the mkahawa-client only. this also applies to Ubuntu 12.04. again this is only a temporary fix. if you have the time to drop by to my [channel]("http://www.youtube.com/user/scriptwarlock?ob=0&feature=results_main") i have prepared some video clips compiling mkahawa for ubuntu 12.04beta1.

---

### Post by Script Warlock on 2012-03-30
> **antonio148 said:**
> hello.
i'm facing this error too
i'm using mkahawa-srv_0.0.4-2_i386.deb  on Ubuntu 11.10 all was working about 5 days, but today server not start. i have lot of members already registered on system.


thanks in advance for any guidance



edit:

uninstalled. deb, and installed the svn is working, but I can not view the tickets, when I click the refresh button the program freezes, and the terminal prints repeatedly: CRITICAL **: CCL_client_owed_terminal: assertion `c 'failed.


thanks. fix is on the way thanks for reporting the problem. we will get back to you as soon as i am through on  reviewing the cause.

---

### Post by tonix1975 on 2012-04-02
> **Script Warlock said:**
> @tonix, try this workaround for incomplete client shutdown...

fire up gedit and open > mkahawa > mkahawa-client > src > cclcfox.cpp

find: line-331 col-17
 and change to  exit and recompile the mkahawa-client only. this also applies to Ubuntu 12.04. again this is only a temporary fix. if you have the time to drop by to my [channel]("http://www.youtube.com/user/scriptwarlock?ob=0&feature=results_main") i have prepared some video clips compiling mkahawa for ubuntu 12.04beta1.

thank you very much d2 bossing its working ang tagal ko hinintay ito..hindi na masasayang yung kuryente ko. again thanks in more power to you...:guitar:

---

### Post by Script Warlock on 2012-04-02
> **tonix1975 said:**
> thank you very much d2 bossing its working ang tagal ko hinintay ito..hindi na masasayang yung kuryente ko. again thanks in more power to you...:guitar: cheers :) regarding sa tanong mong ym chat ang alam ko lang is yung web based na ym like the imo.im gumana naman voice dun pero kung empathy ang paguusapan gtalk can handle the voice and video.

---

### Post by tonix1975 on 2012-04-09
yung gyachi kasi ginamit ko ayaw gumana yung voice nya.hinahanapan ko pa ng sulusyon.. pero ok bossing salamat ng marami. :p

---

### Post by David006 on 2012-04-25
> **David006 said:**
> Any update from developer?

Sorry, been busy in Canberra (capital city of) AUSTRALIA.  Just started new role with .. (cant' say).

Will try to get back up to speed on ***Mkahawa Cyber Café Client*** (and *Server*) fairly shortly ..

---

### Post by tonix1975 on 2012-05-02
any body kung anong balita sa 12.04 lts para sa timer natin? hindi muna ako nag palit baka ma nose bleed nanaman ako nito ^_^

---

### Post by coevlad on 2012-05-03
mga boss gumagana na po ba ung mkahawa client sa 12.04?
at sang version stable ung mkahawa client?

---

### Post by Script Warlock on 2012-05-04
> Hi, men

Thanks for mkahawa support!

I would like to help and add new features to the project, only that I am new to Linux, what tools I need to modify the source code? Obviously it's a long way, but I want to start something. Again thank you very much and I send you greetings from Mexico. @rbemmanuel, your favorite linux text editor can do the job..

---

### Post by Script Warlock on 2012-05-04
> **coevlad said:**
> mga boss gumagana na po ba ung mkahawa client sa 12.04?
at sang version stable ung mkahawa client? use the svn source

---

### Post by Script Warlock on 2012-05-04
> **tonix1975 said:**
> any body kung anong balita sa 12.04 lts para sa timer natin? hindi muna ako nag palit baka ma nose bleed nanaman ako nito ^_^ just came back from my long vacation at babalikan ulit natin to sooner, hows your mkahawa?

---

### Post by coevlad on 2012-05-04
> **Script Warlock said:**
> use the svn source

master eto po ba yung tinutukoy niyo                         svn co [https://mkahawa.svn.sourceforge.net/svnroot/mkahawa](https://mkahawa.svn.sourceforge.net/svnroot/mkahawa) mkahawa
noob po aku dito sa linux need guidance ^^

---

### Post by coevlad on 2012-05-05
master warlock ok na ung mkahawa-client ^^ salamat sa video ^^ gumagana na sa 12.04..and d ku mapagana ung reset and shutdown ng client gamit server hmmmmmmmmmm

---

### Post by Script Warlock on 2012-05-05
> **coevlad said:**
> master warlock ok na ung mkahawa-client ^^ salamat sa video ^^ gumagana na sa 12.04..and d ku mapagana ung reset and shutdown ng client gamit server hmmmmmmmmmm if ever you have an issue on shutdown take a look at this [_[COLOR="Blue"]workaround[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=11802301&postcount=345")

---

### Post by coevlad on 2012-05-05
thank you master...i have an issue on my server the lan connection starts to drop..but wen i disconnect it and use my wifi i can browse the web but with my lan connection at first yes but after a few minutes i cannot. googled it and found and tried disabling ipv6 but i have no luck..

---

### Post by coevlad on 2012-05-05
master warlock can you give me some suggestions about using 12.04, 11.10 or 10.04. which of this is more like mkahawa will run smoothly? by the way can i use linuxmint counterpart?? since linux mint lisa and isadora is base on 11.10 and 10.04 respectively...

---

### Post by Script Warlock on 2012-05-05
> **coevlad said:**
> master warlock can you give me some suggestions about using 12.04, 11.10 or 10.04. which of this is more like mkahawa will run smoothly? by the way can i use linuxmint counterpart?? since linux mint lisa and isadora is base on 11.10 and 10.04 respectively... yung bago sa svn ang gamitin dahil sa mga naayos na issues sa dating release ng mkahawa, pwede ya compile sa ibang linux.

---

### Post by tonix1975 on 2012-05-06
> **Script Warlock said:**
> just came back from my long vacation at babalikan ulit natin to sooner, hows your mkahawa?


bossing ok naman yung mkahawa timer ko ... baka i try ko narin mag 12.04 LTS.
:P

---

### Post by Script Warlock on 2012-05-06
> **tonix1975 said:**
> bossing ok naman yung mkahawa timer ko ... baka i try ko narin mag 12.04 LTS.
:P yes go ahead mas maganda na 12.04 ang hinahanap ko na lang ay paano to ma lock ang dash para ba pang cafe na ang dating total surf at games lang naman mga tomer natin so di na necessarily kelangan pang makita ang bituka ng ubuntu. a few months ko pa migrate lahat machines from 10.04 pagkatapos maging deb na tong nasa svn kaso di pa ata tapos si ouwor sa paghanting ng critical bug ng mkahawa.

---

### Post by tonix1975 on 2012-05-15
bossing script succes yung timer ko bali hindi ko muna ginawang 12.04 yung server ko bali yung mga client lang muna sa ngayong ang 12.04 ok naman xa.:)

---

### Post by Script Warlock on 2012-05-16
nice tonix...

---

### Post by falconrambo on 2012-05-24
> **Script Warlock said:**
> please check again how i [compiled]("http://ubuntuforums.org/showpost.php?p=11110114&postcount=173") mkahawa...
  hey..if you wud be kind enuf to help with steps in seetting up a cyber cafe with mint 10 in both server and client and with mkahawa as timer management i wud be very grateful..how can initiate a network between client and server?

---

### Post by Script Warlock on 2012-05-25
> **falconrambo said:**
> hey..if you wud be kind enuf to help with steps in seetting up a cyber cafe with mint 10 in both server and client and with mkahawa as timer management i wud be very grateful..how can initiate a network between client and server? set your server ip to static and your client to dynamic if you want to and then compile mkahawa. [link]("http://ubuntuforums.org/showpost.php?p=11110114&postcount=173")

---

### Post by naehk21 on 2012-08-30
good efternoon..

how can we manage the mkahawa cyber manager..

na hindi mo sya nawawala .. ang problema po kasi namin kapag nirun po sya nawawala .. my timelimit po ang pag gamit nito ???

---

### Post by naehk21 on 2012-08-30
> **Script Warlock said:**
> set your server ip to static and your client to dynamic if you want to and then compile mkahawa. [link]("http://ubuntuforums.org/showpost.php?p=11110114&postcount=173")


yun nga po yung ginawa namin eh .. but still the mkahawa server ay nag auautomatic logout.. may limitation po ba yung time ng mahawa server??

---

### Post by naehk21 on 2012-09-28
what do you think is the best way to limit the time of mkahawa cebercafe ..
and how to fixed the automatic shut down of this server..
----> we need your answer badly .. so please.. help me/.. tnx

---

### Post by Script Warlock on 2012-09-30
let's talk more sa irc channel na ginawa ni ouwor sa baba lang ng sig ko. be there. tapos wrap up ko na lang solution ng problema ninyo para maipost ko dito.

---

### Post by Script Warlock on 2012-10-01
> **naehk21 said:**
> what do you think is the best way to limit the time of mkahawa cebercafe ..
and how to fixed the automatic shut down of this server..
----> we need your answer badly .. so please.. help me/.. tnx quick fix, go to .mkahawa folder and rename the db to db.old? what do we mean limit the time.

@jcka005 same procedure with naehk21.

---

### Post by pmwangi80ke on 2012-12-20
Hello,
I have mkahawa server on ubuntu 10.04 compiled from svn and some clients all running ubuntu 10.04. I want to add a few clients running windows xp. I did manage to install the xp mkahawa-client version from mkahawa.net. The problem is i have no idea how the client connects to the server. Is there anyone who has successfully used xp mkahawa client? any suggestion is welcome.

---

### Post by David006 on 2013-07-12
Anyone working on updates / support for **Mkahawa Cybercafe** at the moment?

---

### Post by icebox25 on 2014-04-25
> **pmwangi80ke said:**
> Hello,
I have mkahawa server on ubuntu 10.04 compiled from svn and some clients all running ubuntu 10.04. I want to add a few clients running windows xp. I did manage to install the xp mkahawa-client version from mkahawa.net. The problem is i have no idea how the client connects to the server. Is there anyone who has successfully used xp mkahawa client? any suggestion is welcome.

Yes, the client (the old CCL client) for XP works with Ubuntu 10.04/12.04 server. However, when I tried it on Win7, it didn't. Can someone help me? Thanks.

---

### Post by Script Warlock on 2015-02-20
long time no hear... i'm back with some bug fixes only :(. mkahawa runs well on a 32bit machine but how about 64bit arch? ](*,) looking for a solution.

---

