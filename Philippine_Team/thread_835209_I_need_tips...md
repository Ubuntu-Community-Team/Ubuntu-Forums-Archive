---
title: "I need tips.."
date: 2008-06-20
forum: Philippine Team
---

### Post by ache109 on 2008-06-20
I want to change to fluxbox because i'm havin'problems with ubuntu by means of graphics.. saka mukhang nd sya kaya ng box ko,

my question:

may possibility ba na mai-save ko ung files ko at hindi mabura ung installed apps ko (e.g flash and sunjava, also limewire) kse para hindi na ako mag re-install ng apps, or i'll be using the live cd since na lower nanan ang required specs nya. 

and one question anong system is running in fluxbuntu? does it run GNOME desktop or a KDE?

thanks.
ache109

---

### Post by ache109 on 2008-06-20
another question (kung meron lang..)
meron kayang live cd and winxp? la lng,, naisip-isip ko lang, kasi i still rely on xp in a such matter.

---

### Post by jeffimperial on 2008-06-20
Post mo naman system specs mo, para mas maganda maibigay na tips ng ating mga experts dito :)

---

### Post by ache109 on 2008-06-20
MSI P4MAM2V Motherboard, Intel P4, 40 GB HDD, S3 GRAPHICS PROSAVAGE 8 VIDEO CARD, VIA TECH. SOUND CARD. I'll post nlng ung detailed specs ksi yan ay sa pagkakaalam ko.

---

### Post by ache109 on 2008-06-20
or view my another thread entitled "suggestion lang" .. meron akong specs dun. just find it on page 3 or 2..

thanks!!
ache109

---

### Post by jsgotangco on 2008-06-20
> **ache109 said:**
> another question (kung meron lang..)
meron kayang live cd and winxp? la lng,, naisip-isip ko lang, kasi i still rely on xp in a such matter.

Not an official one, but I'm pretty sure I encountered one before. You need to your original XP disc and slipstream some stuff to it to boot the system. And I believe its not even a full system but the basics to be able to do diagnostic stuff.

---

### Post by king leoric on 2008-06-20
> **ache109 said:**
> 
my question:

may possibility ba na mai-save ko ung files ko at hindi mabura ung installed apps ko (e.g flash and sunjava, also limewire) kse para hindi na ako mag re-install ng apps, or i'll be using the live cd since na lower nanan ang required specs nya. 

and one question anong system is running in fluxbuntu? does it run GNOME desktop or a KDE?



Yes you can install fluxbox sa ubuntu at masasave mo rin files mo
[http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/)

fluxbuntu is running fluxbox which is another window manager just like desktop or KDE.

Then walang live cd ang xp...you can either dual boot or use virtual box to use xp ....Pero kung pwede mo naman di gamitin ang xp, mas okay yun. Marami namang apps alternative sa windows eh. as Mr. Google lang :):lolflag:

pero don't expect na maganda ang fluxbox...try using LXDE which is better view than fluxbox..

[http://ubuntuforums.org/showthread.php?t=707008](http://ubuntuforums.org/showthread.php?t=707008)
[http://ubuntuforums.org/showthread.php?t=746131](http://ubuntuforums.org/showthread.php?t=746131)

ang distros running LXDE by default is ubuntu lite, Myah OS, GOS???, PUD etc

hope this helps :)

---

### Post by Nhatz on 2008-06-20
[QUOTE=ache109]MSI P4MAM2V Motherboard, Intel P4, 40 GB HDD, S3 GRAPHICS PROSAVAGE 8 VIDEO CARD, VIA TECH. SOUND CARD. I'll post nlng ung detailed specs ksi yan ay sa pagkakaalam ko. [/QUOTE]

Yeah mabilis na yan pag fluxbox gagamiting mo... im running fluxbox on a P3 box mabilis sya even sa P2 siguro mabilis din sya. hehehehe :)

[QUOTE=ache109]may possibility ba na mai-save ko ung files ko at hindi mabura ung installed apps ko (e.g flash and sunjava, also limewire) kse para hindi na ako mag re-install ng apps, or i'll be using the live cd since na lower nanan ang required specs nya. 

and one question anong system is running in fluxbuntu? does it run GNOME desktop or a KDE?[/QUOTE]

yup pwede rin install ka ng fluxbox sa terminal
```
sudo apt-get install fluxbox
```

then pag reboot mo sa login screen may option dun then sa session piliin mo lang fluxbox then piliin mo na flux ang default DE mo everytime na maglogin ka.. ang yung mga installed apps mo nandun parin.. configure mo nalang fluxbox menu mo. hehehe :)

ASTIG! :guitar:

---

### Post by markjensen on 2008-06-20
> **ache109 said:**
> I want to change to fluxbox because i'm havin'problems with ubuntu by means of graphics.. 
...
and one question anong system is running in fluxbuntu? does it run GNOME desktop or a KDE?
Fluxbox does not run KDE or Gnome.  It is used *instead* of KDE or Gnome.  You select it as your 'session' at your kdm/gdm/xdm login screen.


> **king leoric said:**
> ...try using LXDE which is better view than fluxbox..
LXDE is just another *box (in this case Openbox) but with bundled apps, such as a panel and a text editor (not very impressive to bundle a text editor, but more power to them).

---

### Post by PCMan on 2008-06-20
> **markjensen said:**
> Fluxbox does not run KDE or Gnome.  It is used *instead* of KDE or Gnome.  You select it as your 'session' at your kdm/gdm/xdm login screen.



LXDE is just another *box (in this case Openbox) but with bundled apps, such as a panel and a text editor (not very impressive to bundle a text editor, but more power to them).

No, it's not only another *box. It uses openbox by default.
However, you can replace it with anything since all components in LXDE are independent. They can work properly without each other. This is the major difference from other desktops.

---

### Post by king leoric on 2008-06-20
Actually if you install LXDE environment under ubuntu, in the GDM
sessions you can select LXDE, or Gnome with openbox window manager, or openbox lang ata...can't remember na kasi try ko lang last time eh...out of curiosity pero I remove it cause I still like Gnome-compiz eh he he... It performs well naman din dito sa centrino ko and I can't nearly recognize the difference in speed sa lighter desktop (e.g. XFCE, fluxbox, LXDE) in terms of loading applications and while using video editors..

---

### Post by ache109 on 2008-06-20
> **jsgotangco said:**
> Not an official one, but I'm pretty sure I encountered one before. You need to your original XP disc and slipstream some stuff to it to boot the system. And I believe its not even a full system but the basics to be able to do diagnostic stuff.

sir jerome, can you help me kung pano sya gagawin.. I have my winxp installation cd.

:guitar:
thanks!,
ache109

---

### Post by ache109 on 2008-06-20
and also how can i uninstall fluxbox?

thru terminal?

pag ayaw ko na sya...(malay mu)

thanks,
ache109

---

### Post by Nhatz on 2008-06-20
[QUOTE=ache109]and also how can i uninstall fluxbox?

thru terminal?

pag ayaw ko na sya...(malay mu)
[/QUOTE]

```
sudo apt-get remove fluxbox
```

ASTIG! :guitar:

---

### Post by ache109 on 2008-06-20
e2 nalang,

pano nalang mag shift from ubuntu to fluxbuntu without removing my installed apps and files.. (may important pics kase ako dyan hindi na kasya sa pendrive ko at wla na akong extra blank cd... or suggest me kung what is the best linux OS for my pc..

thanks, 
ache109

---

### Post by king leoric on 2008-06-21
> **ache109 said:**
> e2 nalang,

pano nalang mag shift from ubuntu to fluxbuntu without removing my installed apps and files.. (may important pics kase ako dyan hindi na kasya sa pendrive ko at wla na akong extra blank cd... or suggest me kung what is the best linux OS for my pc..

thanks, 
ache109

After you install ang fluxbuntu while using ubuntu then successfully login under fluxbox, u can remove na ang ubuntu :-)
it wont affet ang home folder you assuming yung sinasabi mo ng files ay nasa home folder:)

---

### Post by ache109 on 2008-06-21
so pano naman ang mga installed apps tulad ng sunjava at flash player?

---

### Post by king leoric on 2008-06-21
I don't think it wont affect cause hindi naman gagalawin ang browser mo.

---

### Post by ache109 on 2008-06-21
pano naman kung ang gusto mong tanggalin ung fluxbuntu?

at meron bang eyecandy para maging magmukhang ubuntu ang win xp

---

### Post by pendletone on 2008-06-21
> **ache109 said:**
> another question (kung meron lang..)
meron kayang live cd and winxp? la lng,, naisip-isip ko lang, kasi i still rely on xp in a such matter.

Merong Windows Preinstallation Environment (WinPE) from M$ which is basically a lightweight version of the Windows OS.  Pero it is not intended to be a livecd similar to that of Ubuntu.  Ginagamit siya mainly for diagnostics and recovery.

If you're looking for a Windows bootable cd *preloaded* with apps instead, you can try [BartPE]("http://www.nu2.nu/pebuilder/") or [UBCD4Win]("http://www.ubcd4win.com/").

---

### Post by king leoric on 2008-06-21
> **ache109 said:**
> pano naman kung ang gusto mong tanggalin ung fluxbuntu?

at meron bang eyecandy para maging magmukhang ubuntu ang win xp

you mean u want your XP to look like ubuntu????? Why on earth would you like to do that...Isn't it better if you will change ur ubuntu desktop to look like XP or vista??

SImple lang kung gusto you remove ang fluxbuntu....--reformat your drive :lolflag:

---

### Post by ache109 on 2008-06-22
> **pendletone said:**
> Merong Windows Preinstallation Environment (WinPE) from M$ which is basically a lightweight version of the Windows OS.  Pero it is not intended to be a livecd similar to that of Ubuntu.  Ginagamit siya mainly for diagnostics and recovery.

If you're looking for a Windows bootable cd *preloaded* with apps instead, you can try [BartPE]("http://www.nu2.nu/pebuilder/") or [UBCD4Win]("http://www.ubcd4win.com/").

sir pede po ba i-run tong UBCD4win.exe file via wine kase kahit papaano ayaw kong mag dual boot. At pati ung autostreamer??

T.Y,
Ache109

_____________
Ubuntu ROCKS!! :guitar:

---

### Post by xebian on 2008-06-22
> **king leoric said:**
> 
SImple lang kung gusto you remove ang fluxbuntu....--reformat your drive :lolflag:

This is no laughing matter, and it's not acceptable here.

Calling on the Philippine team mods.

---

### Post by loell on 2008-06-22
> **xebian said:**
> This is no laughing matter, and it's not acceptable here.

Calling on the Philippine team mods.

there's nothing there.. yes that single phrase may mean none advisable advice.

but actually you have to understand the whole flow of the conversation. which is mixed by local language and humor..


your concern is highly appreciated. :)

---

### Post by pendletone on 2008-06-22
> **ache109 said:**
> sir pede po ba i-run tong UBCD4win.exe file via wine kase kahit papaano ayaw kong mag dual boot. At pati ung autostreamer??

Well nde ko pa nasubukan i-run yung UBCD4Win under wine, so I can't tell for sure.  It might install successfully pero I doubt that it would run *smoothly* once you're in the process of building your bootable cd and updating its plugins.  Give it a try...I might be wrong. :)

Sa case naman ng autostreamer, baka pwede kasi magsli-slipstream ka lang naman ng service pack eh.

In any case, do tell me if it worked.

:popcorn:

---

### Post by xebian on 2008-06-22
> **loell said:**
> there's nothing there.. yes that single phrase may mean none advisable advice.

but actually you have to understand the whole flow of the conversation. which is mixed by local language and humor..


your concern is highly appreciated. :)

I understand your point, but you have to understand that even though it's for local users, it's part of the Ubuntu Forums, and any post is viewable by anyone globally.  Local or not every member is bound to the high Ubuntuforums standards.

---

### Post by Nhatz on 2008-06-22
Peace out man! 

[QUOTE=xebian]I understand your point, but you have to understand that even though it's for local users, it's part of the Ubuntu Forums, and any post is viewable by anyone globally. Local or not every member is bound to the high Ubuntuforums standards.[/QUOTE]

dude kahit naman siguro mabasa ng iba yun hindi nman nila maintindihan yun eh at kung noypi naman makakabasa alam nya rin naman na pinoy humor yun at joke joke lang yun... ask natin si ache109 kung sinunod nya nga yun. hehehe :)

cool lang lahat!!! :guitar:
[QUOTE=achel09]
sir pede po ba i-run tong UBCD4win.exe file via wine kase kahit papaano ayaw kong mag dual boot. At pati ung autostreamer??[/QUOTE]

maybe... kasi na-try ko na office 2k3, macromedia flash 8 atpb. sa wine gumagana naman.. baka pwede rin yun hindi ko palang na-try.


[QUOTE=achel09]pano nalang mag shift from ubuntu to fluxbuntu without removing my installed apps and files.. (may important pics kase ako dyan hindi na kasya sa pendrive ko at wla na akong extra blank cd... or suggest me kung what is the best linux OS for my pc..[/QUOTE]

hmmm... best Linus Distro ba? it depends on what u need... hehehe :)

ASTIG! :guitar:

---

### Post by Nessa on 2008-06-22
There are just some things other people won't understand. Bayaan niyo nalang. Hindi niya ma-gets yung joke eh. Concerned lang siya. We all know that we won't push our fellow Pinoy into doing something that would cause harm to him or to his data. But this is a local forum. We're given the luxury of talking into our language. My advice is not to read too much into the english words. Kasi kung ganun ang gagawin mo, hala wala kang mapapala. Ang laki kaya ng LOL nun. Sumasayaw pa! Translate mo nga ito aber. :D

Back on topic... Ano na ang balita dito? Ok na ba yung tips?

---

### Post by Nhatz on 2008-06-22
[QUOTE=Nessa]There are just some things other people won't understand. Bayaan niyo nalang. Hindi niya ma-gets yung joke eh. Concerned lang siya. We all know that we won't push our fellow Pinoy into doing something that would cause harm to him or to his data. But this is a local forum. We're given the luxury of talking into our language. My advice is not to read too much into the english words. Kasi kung ganun ang gagawin mo, hala wala kang mapapala. Ang laki kaya ng LOL nun. Sumasayaw pa! Translate mo nga ito aber. [/QUOTE]

Isang malaking KORAK ka jan sister.....hehehe :) mas maganda siguro kung kung pwede tagalugin... tagalugin nalang natin kasi yung iba may problem na sa box nila hindi pa ma-gets yung magawa kasi hidi nila ma-gets yung reply sa forum. hehehehe :) kung pupwede lang naman.

ASTIG! :guitar:

---

### Post by ache109 on 2008-06-22
anong problema dito sa thread na ito???

hayyy...

ache109

---

### Post by ache109 on 2008-06-22
> **pendletone said:**
> Well nde ko pa nasubukan i-run yung UBCD4Win under wine, so I can't tell for sure.  It might install successfully pero I doubt that it would run *smoothly* once you're in the process of building your bootable cd and updating its plugins.  Give it a try...I might be wrong. :)

Sa case naman ng autostreamer, baka pwede kasi magsli-slipstream ka lang naman ng service pack eh.

In any case, do tell me if it worked.

:popcorn:
sir pendletone, 

e2 ung lumalabas when I try to run the autostreamer (see the attached file)
 at pano po mag slipstream ng service pack???

thanks,
ache109

---

### Post by ache109 on 2008-06-22
here's the attached file:
 sa tingin ko ayaw magload ng DLL..

tnx,
ache109

---

### Post by pendletone on 2008-06-23
> **ache109 said:**
> sir pendletone, 

e2 ung lumalabas when I try to run the autostreamer (see the attached file)
 at pano po mag slipstream ng service pack???

thanks,
ache109

That means that wine can't load or find the MSVBVM60.DLL file from its system32 folder. Kung titignan mo yung system32 folder ng wine, you won't find that file there. I think Autostreamer needs MS Visual Basic Virtual Machine 6.0 for it to run. Google 'vbrun60sp6.exe' and install it.

Tungkol naman sa slipstreaming, there are various ways to do it. One is to use a slipstreaming tool (such as Autostreamer) which is simpler, and the other is to do it manually from the command line.

Ako mas pinili ko yung sa command line kasi ayoko mag-install ng app just to do that. Either way, they both do the same thing.

Basically, you'll just need your Windows CD and a service pack. Extract both to a folder of their own, then combine the two. Tapos burn it to a cd and, *Voila!,* may SP2 (or SP3) cd ka na! :)

Here's a step-by-step procedure on how to do it --> [Slipstreaming Windows XP with SP2]("http://www.winsupersite.com/showcase/windowsxp_sp2_slipstream.asp")

---

### Post by king leoric on 2008-06-24
> **xebian said:**
> This is no laughing matter, and it's not acceptable here.

Calling on the Philippine team mods.

Do you know the reason why I said that phrase?? look for the above advices first...Okay I'll make a recap here.

A guy ask he has an ubuntu. He wants to change to fluxbx without changes to his home folder. I said install fluxbox then remove ubuntu-dektop. So he has only running fluxbuntu now right??? Then he ask how about if he don't want fluxbuntu now?? Is it wrong to say reformat drive and install a new distro???? IS IT WRONG TO ADVICE ON THAT??

---

### Post by king leoric on 2008-06-24
> **Nhatz said:**
> Isang malaking KORAK ka jan sister.....hehehe :) mas maganda siguro kung kung pwede tagalugin... tagalugin nalang natin kasi yung iba may problem na sa box nila hindi pa ma-gets yung magawa kasi hidi nila ma-gets yung reply sa forum. hehehehe :) kung pupwede lang naman.

ASTIG! :guitar:

Sensiya na ngayon lang ako nabuhay ulit at di ko nadepensahan yung sinabi ko eh he he...thanks sa pagdepensa niyo....eh masama ba yung advice ko na yun?? eh di ba ayaw na niya yung current distro eh anung gagawin? db tanggalin ang current? simple lang naman ang common sense nun...hay naku nawala kasi ang connection ko eh hu hu hu hu...

sensiya na na apektuhan ako sa sinabi nun...pero sinunod mo nga ba yung advice ko na yun ache :)

---

### Post by Nhatz on 2008-06-24
Yeah... ako ginagawa ko rin yun.... pag talagang may problema reformat ko HDD ko then clean install para walang problema (pero syempre backup muna). dudes kaya nga may loco forum tayo para i-share knowledge natin at hindi yung mag mayabang na may alam tayo.. ako masasabi ko na newbie parin ako kahit mga 2 years nako gumagamit ng Linux (Ubuntu). SHARE THE LOVE NALANG!!! hehehehe :)
ASTIG! :guitar:

---

### Post by king leoric on 2008-06-25
Eh kasi iyon lang nakita niya at nabasa..yung post ko na reformat and drive eh hindi naman niya alam ang previous trend... Eh kaya nga share share lang naman tayo ng nalalaman eh.. Yan ang linux world, nobody is hopeless :-)

---

### Post by ache109 on 2008-06-25
> **king leoric said:**
> Do you know the reason why I said that phrase?? look for the above advices first...Okay I'll make a recap here.

A guy ask he has an ubuntu. He wants to change to fluxbx without changes to his home folder. I said install fluxbox then remove ubuntu-dektop. So he has only running fluxbuntu now right??? Then he ask how about if he don't want fluxbuntu now?? Is it wrong to say reformat drive and install a new distro???? IS IT WRONG TO ADVICE ON THAT??
Sir sa tingin ko he disagereed about your "LOL" thing.. kase wala namang reason na yung tanong ko ung dahilan?? O mali ang interpretation ko...

---

### Post by king leoric on 2008-06-25
> **ache109 said:**
> Sir sa tingin ko he disagereed about your "LOL" thing.. kase wala namang reason na yung tanong ko ung dahilan?? O mali ang interpretation ko...


di nag disagree siya sa comment ko na reformat yung HDD mo kung ayaw mo na ng fluxbuntu... db? Kasi nag ask ka lately about installing fluxbox sa ubuntu. Then ask ka rin paano tanggal ng ubuntu right? Then I commented na tanggalin mo na yung ubuntu-desktop....so I pressumed na fluxbox na lang or should I say Fluxbuntu na lang natira db?? Then you ask how about if nagsawa ka na sa fluxbuntu? Then I simply said reformat HDD...

Well I may say may mali rin ako kasi dapat ang sabi ko eh reformat your drive and install a new distro..yun lang mali ko...dapat may pahabol...Pero kasi kung titignan at babasahin ang trend ng thread na to eh masusundan mo rin yung trend.. Kasi ang nangyari eh parang one on one na nagtanungan eh ... 

But anyway, next time eh magiging serious na rin ako kung mag comment...:)...nadala kasi nagkakasayahan kami dito nun nung nag comment ako nun eh..saka dapat tinagalog ko na lang :lolflag:

---

### Post by ache109 on 2008-07-12
o e2 bagong tanong...,

I'd recently installed cairo-dock (since i can't install AWN because of my compiz problem). All worked fine. only these black Background of it that is irritable and space eater. (refer to the attached file.) Can I remove these black background?? (Baka kasi dahil sa wala akong compiz???)

Thanks,
Ache109

---

### Post by ache109 on 2008-07-12
Here is the picture:

---

### Post by pendletone on 2008-07-12
> **ache109 said:**
> o e2 bagong tanong...,

I'd recently installed cairo-dock (since i can't install AWN because of my compiz problem). All worked fine. only these black Background of it that is irritable and space eater. (refer to the attached file.) Can I remove these black background?? (Baka kasi dahil sa wala akong compiz???)

Thanks,
Ache109

Since wala kang compositing manager like compiz or beryl, you won't have transparency effects on your cairo-dock. Pero pwede ka pa rin magkaroon ng transparency by using other compositors. Try mo i-install ang **xcompmgr** via synaptic. Then add it to your startup list: System->Preferences->Sessions->Startup Programs->Add, then type under the 'Command' textbox:

```
xcompmgr -c -f -n
```

Hopefully, this would add a basic transparency to your desktop. :)

---

### Post by killer_d76 on 2008-07-12
have you tried "Avant Windows Navigator"?.. [http://wiki.awn-project.org/Installation]("http://wiki.awn-project.org/Installation")

---

### Post by ache109 on 2008-07-12
> **killer_d76 said:**
> have you tried "Avant Windows Navigator"?.. [http://wiki.awn-project.org/Installation]("http://wiki.awn-project.org/Installation")

Tried that but no luck :):guitar:

---

### Post by ache109 on 2008-07-12
Maraming salamat po!!! gumana po sya!! Gandang pabertdey to...

---

### Post by pendletone on 2008-07-13
Walang anuman bro. Birthday mo ba?

[COLOR="Red"][SIZE="5"]HAPPY BIRTHDAY!!![/SIZE][/COLOR]

burger..burger..burger... :)

---

### Post by king leoric on 2008-07-13
[SIZE="5"][COLOR="Green"]HAPPY HAPPY BIRTHDAY ACHE:-({|=\\:D/:guitar::popcorn:[/COLOR][/SIZE]

---

### Post by ache109 on 2008-07-13
well, thanks sa mga bati pero sa friday pa...!!!

---

### Post by jeffimperial on 2008-07-13
> **ache109 said:**
> well, thanks sa mga bati pero sa friday pa...!!!
Advanced **[COLOR="Red"]HAPPY BIRTHDAY[/COLOR]**!!!

---

### Post by rjmdomingo2003 on 2008-07-13
> **ache109 said:**
> well, thanks sa mga bati pero sa friday pa...!!!
Add ko sa reminders ko.. :KS

---

### Post by fabounet on 2008-07-15
"cairo-dock -F"
to run it with the fake transparency support (no need of Compiz or xcompmgr) ;-)

---

### Post by rjmdomingo2003 on 2008-07-17
> **rjmdomingo2003 said:**
> Add ko sa reminders ko.. :KS
Happy Birthday, ache! So, si ache110 ka na ba?:KS

---

### Post by king leoric on 2008-07-18
> **rjmdomingo2003 said:**
> Happy Birthday, ache! So, si ache110 ka na ba?:KS

parang sinabi mo namang 110 years old na siya :lolflag: peace tayo ache:)

---

### Post by Nhatz on 2008-07-18
Happy Birthdat ache110! pahabol ko lang.. heheheheh:)
ASTIG! :guitar:

---

