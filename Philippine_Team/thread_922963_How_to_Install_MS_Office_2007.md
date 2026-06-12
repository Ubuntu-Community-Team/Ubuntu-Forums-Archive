---
title: "How to: Install MS Office 2007"
date: 2008-09-17
forum: Philippine Team
---

### Post by killer_d76 on 2008-09-17
I just wanted to share how i did it, my wife been bugging me to install it  on Ubuntu since she's beginnig to like it, except that she's really familiar using MS Office and ito din yung ginagamit nya sa Office.. i've tried all the possible ways on installing it, i even tried using CrossoverLinux kaso may bayad :(.. then ganito ginawa ko..

i totally remove my old wine version, i even deleted the .wine on the home folder, then i downloaded Wine ver 1.1.4 if you have installed winetricks,i would suggest for you to delete it as well.


to get Wine ver 1.1.4
[PHP]sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list[/PHP] 

tapos....
[PHP]sudo apt-get update[/PHP]

once done type in.. 

[PHP]sudo apt-get install wine[/PHP]

- this will install "wine" on your system

then download winetricks..
[PHP]wget www.kegel.com/wine/winetricks
[/PHP]

tapos..
[PHP]sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
[/PHP]

it will install some DLL na kailangan for you to install MS Office

tapos..
[PHP]winecfg[/PHP] 

change Windows version to "**Vista**"

change rpcrt4.dll ng Wine with rpcrt4 that i got from windows ([COLOR="Blue"]attached file at the bottom of this post[/COLOR])

when all are done, place you Ms Office 2007 CD installer (i still use the  trial version downloaded from M$) then click on "**setup**"

and wait mo lang matapos mag-install, minsan at 70% kala mo nag-hang pero bayaan mo lang it will push thru.. 

once installed.. run 
[PHP]winecfg[/PHP] tapos change mo ulit yung Windows version to "XP".. 

your done!.. 

fix on fonts, bullet and numbering.. punta ka sa Word options 

Applications> wine> programs> Microsoft Office> Microsoft Office Tools> Microsoft Office 2007> Language Settings

then delete all the language that you have there except dun sa ginagamit mo.. i'm using English (US).. restart mo pc mo.

yung Equation Editor, Acces and Outlook di gumagana pa.

check this out...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85585&d=1221701314[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85586&d=1221701314[/IMG]


Additional tip to those who have it installed and having issues with fonts and bullet points, am not sure if this is legal.. but you could give this a try..

what you need:

a. USB thumbdrive (at least 512mb)

b. Computer or laptop with Windows XP or Vista OS and with MS Office 2007 installed (even trial version is ok)



1. find someone who uses MS Office 2007 (trial version is ok) on their Windows Machine or laptop.

2. go to "Fonts" by clicking Start> Control Panel > Fonts

3. select all the Font and make sure you just "copy" all the fonts files in the "Fonts" folder.

4. on your USB drive create "new folder" and name it as "Fonts".

5. paste all the fonts files you have copied to the "Fonts" folder you have created in your USB thumbdrive.

6. once you done, safely remove your thumbdrive

7. plug in the USB drive on your Ubuntu rig..

8. then click Applications > Wine > C:\drive > windows > Fonts

9. right click on the Fonts folder and save a copy of it just in case you have done something wrong

10. copy and paste all the fonts files you have from your USB thumbdrive to the "Fonts" folder.

----- Your Done! -------

---

### Post by Nhatz on 2008-09-17
Nice Dude!!!
ASTIG! :guitar:

---

### Post by wersdaluv on 2008-09-17
Woow. Wala bang bugs? Lahat, gumagana?

---

### Post by rjmdomingo2003 on 2008-09-18
Magpasalamat tayong lahat. :KS

---

### Post by killer_d76 on 2008-09-18
wala pong anuman.. gusto ko lang pong ma-ibalik yung tulong na binigay sa'kin ng mga members din dito!.. :guitar:

gumagana naman lahat so far.. except Equation Editor, Acces at Outlook.. i don't use it naman since i use "**thunderbird**" for email, and yung ibang applications naman di namin nagagamit talaga.

with regard to replacing the rpcrt4.dll sa wine
.. extract the rpcrt4.dll that is included on this post on your desktop, then go to...

[COLOR="Red"]home/username/.wine/drive_c/windows/system32[/COLOR]

replace the rpcrt4.dll there with the one that you have extracted on your desktop.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85611&d=1221715679[/IMG]

---

### Post by loell on 2008-09-18
nicey nicey.. :D

---

### Post by dodimar on 2008-09-18
Printer ko na lang ang kailangan ko mapagana and I'm 80% leaving Windows XP.

Pero I'll check this pa, di ko pa na-install Ubuntu (kaka format lang ng PC ko).

---

### Post by wersdaluv on 2008-09-18
How about OneNote? Super important for me eh. hehe

---

### Post by killer_d76 on 2008-09-19
jsgotangco and some of the forumer were able to resolve the issue with my printer :popcorn:.. and i'm also 80% certain leaving XP since i'm planning to upgrade my HDD to 160GB!(no dual booting.. 160GB of ubuntu!) , kasi almost all of online games na nilalaro ng anak ko works on wine now! :guitar:

with regard to "OneNote" i haven't tried it yet.. subukan kong mag-download ng trial version, then i'll keep you posted! ;)

hhmm... after a few googling.. i found this.. [http://ubuntuforums.org/showthread.php?t=913064&highlight=onenote]("http://ubuntuforums.org/showthread.php?t=913064&highlight=onenote") it mentioned OneNote worked for him.. except using it on his tablet for handwriting.. though am not sure what version of wine he's using.

---

### Post by Nhatz on 2008-09-19
Dudes... dati ko pa na-install MS Office pero 2003 at may problema ako sa printing esply yung margin nung paper. hehehe :) pero try nyo rin kung gagana sa inyo.

ASTIG! :guitar:

---

### Post by killer_d76 on 2008-09-19
okey naman margin when printing documents on MS Office 2007..

---

### Post by ppruden on 2008-09-19
Got Wine 1.1.4 installed (looked to go ok), got Office 07 Pro installed (again, looked ok), changed Wine back to XP emulation, went to run Office and ..... All I see is a wait icon and in the "taskbar" it says Starting MS Office for about 15 secs then it goes away.

Also tried Vista Emulation after XP flopped.

Er?

Paul
HP DV6000, 2.0ghz, 2GB, 160GB, Dual-booted: Ubuntu 8.04 / Vista HomePrem

---

### Post by killer_d76 on 2008-09-19
did you followed the whole procedure?.. if you have wine installed already i would suggest for to totally remove it!.. 

[PHP]sudo rm -rf ~./wine[/PHP]

then follow the whole procedure.. works fine with me.

---

### Post by Recursion_1209 on 2008-09-22
@killer_d76 galing ng howto mo. Di ko na kailangan VMware pag open ng docs na di ok sa openoffice.

Salamat!

---

### Post by killer_d76 on 2008-09-23
walang anuman bro! ;)

---

### Post by zoomy942 on 2008-09-23
> **ppruden said:**
> Got Wine 1.1.4 installed (looked to go ok), got Office 07 Pro installed (again, looked ok), changed Wine back to XP emulation, went to run Office and ..... All I see is a wait icon and in the "taskbar" it says Starting MS Office for about 15 secs then it goes away.

Also tried Vista Emulation after XP flopped.

Er?

Paul
HP DV6000, 2.0ghz, 2GB, 160GB, Dual-booted: Ubuntu 8.04 / Vista HomePrem

me too :(

---

### Post by killer_d76 on 2008-09-23
just make sure you have *removed* ***all*** the old wine version and *winetricks* files you have and then follow the whole procedure.. i have tried several times as well and almost got frustrated, i have removed the old wine version and installed the 1.1.4 version but did not work either (i got an error when installation process begins)  until i removed the ***winetricks*** that i have previously installed (located on your Home folder) and download a new one.. then i tried re-installing MS Office 2007 and boom!.. installation process was a success.. :guitar:

---

### Post by Lord Kaiaphas on 2008-10-06
ei, thanks.. just did it and its working just fine.

[[img]http://i280.photobucket.com/albums/kk192/diablosinmusika/Ubuntu%20forums/1223315623-1.png[/img]](http://i280.photobucket.com/albums/kk192/diablosinmusika/Ubuntu%20forums/1223315623.png)

---

### Post by dodimar on 2008-10-06
killer_d76, where did you get ms office 2007, you're using professional, right? can you pm me a link or something..

Thanks... :) :) :)

---

### Post by killer_d76 on 2008-10-06
@Lord Kaiaphas, astig di'ba?! :guitar:

@dodimar - PM sent ;)

---

### Post by ysNoi on 2008-10-06
> **dodimar said:**
> killer_d76, where did you get ms office 2007, you're using professional, right? can you pm me a link or something..

Thanks... :) :) :)

siR, ako din po siR...! Please pm me naman...! I did it already but it didn't work..! Baka sa installer ko ung may problem..! I realy want to make it fine...

Thanks in advance... :guitar:

---

### Post by Lord Kaiaphas on 2008-10-06
> **killer_d76 said:**
> **@Lord Kaiaphas, astig di'ba?!** :guitar:

@dodimar - PM sent ;)


yap.. thanks to you i was able to install it properly.. i have tried it once but it failed, and now its working just fine, if you will take a closer look at my screenshot you will notice that some of the control buttons are a bit distorted. i used Office 2007 Enterprise.. anyways, the real deal is that your Guides works. 

kampai at apir..

[[img]http://i280.photobucket.com/albums/kk192/diablosinmusika/Ubuntu%20forums/1223315623-1.png[/img]](http://i280.photobucket.com/albums/kk192/diablosinmusika/Ubuntu%20forums/1223315624.png)

---

### Post by Lord Kaiaphas on 2008-10-06
Monday October 6, 2008 2320

I made my first print using Microsoft Office 2007 Enterprise and HP Deskjet F4100.. awesome.. apir.. 

:guitar:

---

### Post by killer_d76 on 2008-10-07
ysNoi- PM sent bossing! ;)

Lord Kaiaphas - nice bro!.. medyo tricky talaga installation process.. minsan i think it has something to do with winetricks.. last time i have tried it, i need to re-do the download to make it install properly.. i'm not quite sure but if it has something to do with wine version.. if you look closely on my MS Office all the buttons are ok :confused:.

---

### Post by Shippou on 2008-10-07
Cool desktop! I want it! (THe theme, of course.) 

I'm a black addict too! :)

---

### Post by Lord Kaiaphas on 2008-10-07
> **killer_d76 said:**
> ysNoi- PM sent bossing! ;)

L**ord Kaiaphas - nice bro!.. medyo tricky talaga installation process.. minsan i think it has something to do with winetricks.. last time i have tried it, i need to re-do the download to make it install properly.. i'm not quite sure but if it has something to do with wine version.. if you look closely on my MS Office all the buttons are ok** :confused:.

thanks.. i guess i have to figure it out, how it will work. i think it just need some reconfiguration. i also need to work on this. you already did your part now its my turn, bwa ha ha ha ha ha.. apir.. :guitar:

---

### Post by killer_d76 on 2008-10-07
@Lord Kaiaphas- with regard to Raptor.. use the one that i have attached here, this is the one that i use on my desktop :guitar:

---

### Post by killer_d76 on 2008-10-07
@ysNoi - PM sent bro! ;) just tell me if it works!.. :guitar:

---

### Post by ysNoi on 2008-10-07
Okey bro killer_d76... Will Update you ASAP....!

Thanks a lot... :guitar:

---

### Post by dodimar on 2008-10-07
> **killer_d76 said:**
> @Lord Kaiaphas, astig di'ba?! :guitar:

@dodimar - PM sent ;)

Thanks, waiting for your PM para dun sa , alam mo na.. hehehe...

---

### Post by ysNoi on 2008-10-07
I got it..! Thanks to bro killer_d76 and bro Lord Kaiaphas....You'Re the man guys...! Thanks a loT... :guitar::guitar:

BTW, I added ***sudo apt-get install wine*** after the second step of bro killer_d76's... That's it and it works...!

---

### Post by killer_d76 on 2008-10-07
> **dodimar said:**
> Thanks, waiting for your PM para dun sa , alam mo na.. hehehe...

PM sent bro! ;).. :guitar:

---

### Post by killer_d76 on 2008-10-07
@ysNoi - astig di'ba?!.. :guitar:

---

### Post by ysNoi on 2008-10-07
> **killer_d76 said:**
> @ysNoi - astig di'ba?!.. :guitar:

Super astig bro...! Pero mas astig sana kapag ma-open na yung mga .xls files kahit hindi na e-save sa FILES Folder sa .Wine/drive C...!

:guitar::guitar:

---

### Post by killer_d76 on 2008-10-07
> **ysNoi said:**
> Super astig bro...! Pero mas astig sana kapag ma-open na yung mga .xls files kahit hindi na e-save sa FILES Folder sa .Wine/drive C...!

:guitar::guitar:

hhmm.. i'll have a look at it.. and see if there is a work around it.. i'll keep you posted ;)

---

### Post by ysNoi on 2008-10-08
> **killer_d76 said:**
> hhmm.. i'll have a look at it.. and see if there is a work around it.. i'll keep you posted ;)

Thanks for the inputs siR..! Actually, some of my co-workers really like to try Ubuntu... Eto lang ang bottle-neck namin, yung paggamit ng MS Office..! :guitar:

---

### Post by killer_d76 on 2008-10-08
> **ysNoi said:**
>  I added ***sudo apt-get install wine*** after the second step of bro killer_d76's... That's it and it works...!


..hehehe for some reason i don't how i missed that part!, i have editted the process and added it up!.. thanks

---

### Post by killer_d76 on 2008-10-08
>  Originally Posted by ysNoi  View Post
Super astig bro...! Pero mas astig sana kapag ma-open na yung mga .xls files kahit hindi na e-save sa FILES Folder sa .Wine/drive C...!

@ysNoi- try to open open up MS Excel first, them click on open and then browse to where you have saved the xls files!.

---

### Post by ysNoi on 2008-10-08
> **killer_d76 said:**
> @ysNoi- try to open open up MS Excel first, them click on open and then browse to where you have saved the xls files!.

Yup bro, it works indeed...! I haven't realized it before..! :lolflag:

I'll update heRe later for the stability..! Thanks bro... :guitar:

---

### Post by killer_d76 on 2008-10-08
> **Shippou said:**
> Cool desktop! I want it! (THe theme, of course.) 

I'm a black addict too! :)

i'm using Blackfate theme and Raptor.. ;) you can find nice theme and wallpaper at Gnomelook.org! :guitar:

---

### Post by killer_d76 on 2008-10-10
***update: 10/11/08***

Found minor bug on MS Office 2007 running on Wine using the procedure i have posted, fonts being used here is for [COLOR="Blue"]MS Office 2003[/COLOR] whereas it should be for [COLOR="Red"]2007[/COLOR]!.. i'll be uploading **[COLOR="Blue"]2007 Font package[/COLOR]** soon so you could update the font package that you have.

---

### Post by deoxyna on 2008-10-11
easier way to do it, no wine, install OpenOffice....peace...

---

### Post by killer_d76 on 2008-10-11
thanks for the info bro.. but if you have read the first post you'll have an idea why i have done this.. and you don't need to install OpenOffice on Ubuntu.. it is **pre-installed**! :guitar: rock on!

---

### Post by dynastywarrior on 2008-10-11
thank you killer for this very nice how-to!!!

it rocks!!!!!


MABUHAY MGA PINOY!!!!!

---

### Post by ysNoi on 2008-10-12
> **killer_d76 said:**
> ***update: 10/11/08***

Found minor bug on MS Office 2007 running on Wine using the procedure i have posted, fonts being used here is for [COLOR="Blue"]MS Office 2003[/COLOR] whereas it should be for [COLOR="Red"]2007[/COLOR]!.. i'll be uploading **[COLOR="Blue"]2007 Font package[/COLOR]** soon so you could update the font package that you have.

Thanks for the updaTes bro...! Hehehe :guitar::guitar:

---

### Post by dodimar on 2008-10-12
> **killer_d76 said:**
> ***update: 10/11/08***

Found minor bug on MS Office 2007 running on Wine using the procedure i have posted, fonts being used here is for [COLOR="Blue"]MS Office 2003[/COLOR] whereas it should be for [COLOR="Red"]2007[/COLOR]!.. i'll be uploading **[COLOR="Blue"]2007 Font package[/COLOR]** soon so you could update the font package that you have.

Accountability and responsibility...

Good job killerd76...

---

### Post by killer_d76 on 2008-10-12
Guys i'll be uploading 300MB+ (compressed)of Font Package Files.. any suggestion on how/where to upload this file with this speed of Broadband Connection?.. tried rapidshare but it'll take me the whole day just to upload this!

[[IMG]http://www.speedtest.net/result/337943878.png[/IMG]]("[URL=http://www.speedtest.net)"][[IMG]http://www.speedtest.net/result/337943878.png[/IMG]](http://www.speedtest.net)[/URL]

---

### Post by dodimar on 2008-10-13
> **killer_d76 said:**
> Guys i'll be uploading 300MB+ (compressed)of Font Package Files.. any suggestion on how/where to upload this file with this speed of Broadband Connection?.. tried rapidshare but it'll take me the whole day just to upload this!

[[IMG]http://www.speedtest.net/result/337943878.png[/IMG]]("[URL=http://www.speedtest.net)"][[IMG]http://www.speedtest.net/result/337943878.png[/IMG]](http://www.speedtest.net)[/URL]

Maybe nhatz has a good upload connection, you could ask him to upload this for you. Really would like to help, but I can't bring CDs at work. And my connection at home is terribly bad.

---

### Post by killer_d76 on 2008-10-14
thanks dodimar.. i'll try to ping Nhatz and see what we could come up with! ;)

---

### Post by killer_d76 on 2008-10-14
M$ Sound Recorder anyone?, when i accidentally removed it from MS (on utilities) i have been searching and looking over the net where to get this, i know there is a better recorder that can be used on ubuntu but for those who needs it.. here you go!.. :guitar:..

---

### Post by killer_d76 on 2008-10-14
some pics.. here you go!


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88269&d=1223974648[/IMG]

---

### Post by pendletone on 2008-10-15
> **killer_d76 said:**
> Guys i'll be uploading 300MB+ (compressed)of Font Package Files.. any suggestion on how/where to upload this file with this speed of Broadband Connection?.. tried rapidshare but it'll take me the whole day just to upload this!

[[IMG]http://www.speedtest.net/result/337943878.png[/IMG]]("[URL=http://www.speedtest.net)"][[IMG]http://www.speedtest.net/result/337943878.png[/IMG]](http://www.speedtest.net)[/URL]

try mo [MediaFire]("http://www.mediafire.com/"). okay yung upload speed niya and it offers unlimited storage, but you need to split your archived file into 100MB chunks.

[edit]
re: MS sound recorder on linux...hehe nakakaaliw naman niyan :)

---

### Post by dynastywarrior on 2008-10-15
Mabuhay ka Killer_d76!!!!

---

### Post by dynastywarrior on 2008-10-15
I'm sorry i forgot to mention.... i used wine 1.1.6 and it works perfectly too.....


**Thanks again Killer_d76 !**

---

### Post by killer_d76 on 2008-10-16
cheers to  you too bro!.. nice desktop!.. i'll give pendletone's suggestion a try later so i could upload the 2007 font package to update the 2003 we have!

---

### Post by dodimar on 2008-10-20
muzta font package.. na upload na?

(di ako nagmamadali,,, take your time :) )

thanks killer_d76

---

### Post by killer_d76 on 2008-10-21
di pa bossing... medyo busy pa eh hehehe.

---

### Post by ekss on 2008-11-13
i got mine working on wine 1.1.8. problema ko lang ngayon ay yung margin pero di na bale basta na installed ko na.

yahooooo!!!maraming maraming salamat po sa guide. :)

---

### Post by mocha on 2008-11-14
Thank you!  Appears to be working good on Intrepid with Wine 1.1.8.

---

### Post by b3n0 on 2008-11-30
Bravo dude! I've been looking for somthing like this for a while.
;D

---

### Post by j_shaga on 2008-12-02
Sorry for asking this. But i didn't understand, which programs of MS office 2007 works, which not. does outlook, access works?

---

### Post by latev on 2008-12-02
Wow man that's amazing indeed!
Do you think I stand a chance with Autodesk CAD programs?

---

### Post by b3n0 on 2008-12-03
I tried following the tutorial, but it didn't work. I was however running the latest version of wine (1.1.8) should I downgrade to 1.1.4?
I tried this command but it didn't remove wine at all.
```
sudo rm -rf ~./wine
```
I managed to install it but I couldn't run the programs. The icons would appear in the task bar, and it would appear as though it was loading then it would just give up.
Thanks, in advance.

---

### Post by b3n0 on 2008-12-03
Thanks, Never mind about the last post. I have it working now great tutorial! +1 for you!
1 problem I'm having is, under applications there is no wine menu. I tried system > preferences > main menu but it wasn't available for selection.
any ideas?

In the mean time I have to launch my office 12 apps like this.

```
nautilus .wine
```
then navigate to /drive_c/Program Files/Microsoft Office/Office12
Then right click on say WINWORD.EXE and select open with "wine windows program launcher".

Please help.

---

### Post by pendletone on 2008-12-03
@b3no: try to uninstall wine via synaptic and reinstall it again, it should recreate its menus.

if you want, however, you can just manually add a wine entry on your applications menu:

1. right-click top panel, select 'Edit Menus'
2. click 'New Menu', and type 'Wine' under Name
3. under 'Wine' menu entry, create a 'Program' folder under which create, say, 'Microsoft Office' folder, then browse for your winword.exe to create an item there.

*you may also want to add these items under your Wine menu...*

4. 'Browse C:\ Drive' --> under command:
```
xdg-open .wine/dosdevices/c:
```
   'Configure Wine' --> under command:
```
winecfg
```
   'Uninstall Wine Software' --> under command:
```
uninstaller
```

Hope that helps! :)

---

### Post by mocha on 2008-12-03
If you want to associate documents to automatically open with Word or Excel for example, you can do the following (this works in Gnome/KDE).  Make an empty text file called "winword" for example and put in the following:

```
#!/bin/bash
wine "C:\program files\microsoft office\office12\winword.exe" "`winepath -w "$@"`"
```

Then make the script executable.  Then use the Gnome or KDE method to associate doc files to open with this script, you can do a similar script for excel or whatever...

---

### Post by b3n0 on 2008-12-04
Thanks pendletone, by simply right clicking on the applications menu I was able to find that the wine menu was hidden.
Quick fix thanks mate.

---

### Post by halovivek on 2008-12-04
wow thanks dude. i will install these to my friends ubuntu also.

---

### Post by Anbin89 on 2008-12-06
Awesome, now the installation begins... thanks man

---

### Post by talofo on 2008-12-07
> **j_shaga said:**
> Sorry for asking this. But i didn't understand, which programs of MS office 2007 works, which not. does outlook, access works?

Same question here. :s

Any help?

Thanks.

---

### Post by otniuqyrreg on 2008-12-11
Very impressive tutorial, pero para sa akin OpenOffice pwede na kaya lang, problema kung paano gagana ang printer ko dito sa Ubuntu. :confused: :guitar:

---

### Post by LinnetLegs on 2008-12-13
Forgive me for being a bit slow, I can follow your instructions to:


change rpcrt4.dll ng Wine with rpcrt4


I don't understand what that is or how to do it. :confused:

---

### Post by pendletone on 2008-12-13
@LinnetLegs: what the original poster meant was to overwrite the file 'rpcrt4.dll' inside the windows/system32 directory of wine with this [one]("http://ubuntuforums.org/attachment.php?attachmentid=85590&d=1221701664").

to do this, go to Applications->Wine->Browse C:\ Drive, go to 'windows/system32' folder. there should be an rpcrt4.dll file there. untar killer_d76's attached file into that directory. however, i suggest that you backup (or rename) the original 'rpcrt4.dll' file, just in case.

> I don't understand what that is or how to do it.

as to what it is or what it is for, we don't have to know. it's just-one-of-those M$ files. :lolflag:

---

### Post by LinnetLegs on 2008-12-13
Thanks. But for some reason, nothing happens when I go to  Applications->Wine->Browse C:\ Drive

---

### Post by pendletone on 2008-12-13
well let's just try doing this inside the terminal. probably you downloaded the rpcrt4.dll tarball in your 'Desktop' folder, if so:

1. fire up your terminal and type:

```
cd Desktop
```

2. extract the tarball:

```
tar xfvz rpcrt4\ from\ windows.tar.gz
```

3. copy/paste the extracted 'rpcrt4.dll' file to windows/system32

```
cp rpcrt4\ from\ windows/rpcrt4.dll ~/.wine/drive_c/windows/system32
```

hope this helps

---

### Post by LinnetLegs on 2008-12-15
Thanks for getting back to me. I am still having problems. I guess I should get to grips with open office. If it has everything MS Office has - I shouldn't worry too much.

It is tantalising though because I see the icons for MS office in applications>other menu


(sigh)

---

### Post by Anbin89 on 2008-12-16
Guys, i have successfully installed Office 2007. But Whenever i try to drag and choose multiple objects in powerpoint, the screen turns black. It is really irritating as you cannot see what you are choosing.. Does anyone have solution for this?

---

### Post by killer_d76 on 2009-02-06
sorry for the very late reply.. for those whose having issues with installed MS Office 2007, i would suggest you to report it directly to Winehq website.. 

@ LinnetLegs - were you able to install Ms Office on your rig?.. are you getting errors?



**Additional tip to those who have it installed and having issues with fonts and bullet points**, am not sure if this is legal.. but you could give this a try..

what you need:

a. USB thumbdrive (at least 512mb)

b. Computer or laptop with Windows XP or Vista OS and with MS Office 2007 installed (even trial version is ok)



1. find someone who uses MS Office 2007 (trial version is ok) on their Windows Machine or laptop. 

2. go to "Fonts" by clicking Start> Control Panel > Fonts

3. select all the Font and make sure you just **"copy"** all the fonts files in the "Fonts" folder.

4. on your USB drive create "new folder" and name it as "Fonts".

5. paste all the fonts files you have copied to the "Fonts" folder you have created in your USB thumbdrive.

6. once you done, safely remove your thumbdrive 

7. plug in the USB drive on your Ubuntu rig..

8. then click Applications > Wine > C:\drive > windows > Fonts

9. right click on the Fonts folder and save a copy of it just in case you have done something wrong

10. copy and paste all the fonts files you have from your USB thumbdrive to the "Fonts" folder.

                       ----- Your Done! -------

---

### Post by Duranxl on 2009-03-24
So i just found this guide..and like all the other guides on the net it says you need to do:
```
./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2
```

or
```
sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1  
```

But all i get is
```
:~/.wine/drive_c$ sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1  
Using native,builtin override for following DLLs: msxml3
Executing wine regedit ~/.wine/drive_c/winetrickstmp/override-dll.reg
Executing wine msiexec /i ~/.winetrickscache/msxml3.msi
Note: command 'wine msiexec /i ~/.winetrickscache/msxml3.msi' returned status 103.  Aborting.
:~/.wine/drive_c$ 
```

any help?

---

### Post by san20july on 2009-04-08
> **killer_d76 said:**
> 

change rpcrt4.dll ng Wine with rpcrt4 that i got from windows (attached file at the bottom of this post)

----- Your Done! -------

This fix has been resolved in the higher versions of wine i used 1.0.18 and things worked fine. with the same procedure except replacing the DLL

---

### Post by izzyz on 2009-04-10
I have problems with installing it! I have followed the steps in the guide till winecfg command. this is what shows up:

izzy@izzy-desktop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
izzy@izzy-desktop:~$ 


what do I do? Sorry Im new to linux and havent got much experience with it. Any help much appreciated.

---

### Post by JonyBoyct on 2009-04-21
Kamusta!
This Helped me to install Office 2007.
Really easy.  Check it out.
It's an up to date version.  Using wine version 1.1.16.
[http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

---

### Post by emvarona on 2009-04-22
> **killer_d76 said:**
> I just wanted to share how i did it, my wife been bugging me to install it  on Ubuntu since she's beginnig to like it, except that she's really familiar using MS Office and ito din yung ginagamit nya sa Office.. i've tried all the possible ways on installing it, i even tried using CrossoverLinux kaso may bayad :(.. then ganito ginawa ko..

i totally remove my old wine version, i even deleted the .wine on the home folder, then i downloaded Wine ver 1.1.4 if you have installed winetricks,i would suggest for you to delete it as well.


to get Wine ver 1.1.4
[PHP]sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list[/PHP] 

tapos....
[PHP]sudo apt-get update[/PHP]

once done type in.. 

[PHP]sudo apt-get install wine[/PHP]

- this will install "wine" on your system

then download winetricks..
[PHP]wget www.kegel.com/wine/winetricks
[/PHP]

tapos..
[PHP]sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
[/PHP]

it will install some DLL na kailangan for you to install MS Office

tapos..
[PHP]winecfg[/PHP] 

change Windows version to "**Vista**"

change rpcrt4.dll ng Wine with rpcrt4 that i got from windows ([COLOR="Blue"]attached file at the bottom of this post[/COLOR])

when all are done, place you Ms Office 2007 CD installer (i still use the  trial version downloaded from M$) then click on "**setup**"

and wait mo lang matapos mag-install, minsan at 70% kala mo nag-hang pero bayaan mo lang it will push thru.. 

once installed.. run 
[PHP]winecfg[/PHP] tapos change mo ulit yung Windows version to "XP".. 

your done!.. 

fix on fonts, bullet and numbering.. punta ka sa Word options 

Applications> wine> programs> Microsoft Office> Microsoft Office Tools> Microsoft Office 2007> Language Settings

then delete all the language that you have there except dun sa ginagamit mo.. i'm using English (US).. restart mo pc mo.

yung Equation Editor, Acces and Outlook di gumagana pa.

check this out...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85585&d=1221701314[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85586&d=1221701314[/IMG]


Additional tip to those who have it installed and having issues with fonts and bullet points, am not sure if this is legal.. but you could give this a try..

what you need:

a. USB thumbdrive (at least 512mb)

b. Computer or laptop with Windows XP or Vista OS and with MS Office 2007 installed (even trial version is ok)



1. find someone who uses MS Office 2007 (trial version is ok) on their Windows Machine or laptop.

2. go to "Fonts" by clicking Start> Control Panel > Fonts

3. select all the Font and make sure you just "copy" all the fonts files in the "Fonts" folder.

4. on your USB drive create "new folder" and name it as "Fonts".

5. paste all the fonts files you have copied to the "Fonts" folder you have created in your USB thumbdrive.

6. once you done, safely remove your thumbdrive

7. plug in the USB drive on your Ubuntu rig..

8. then click Applications > Wine > C:\drive > windows > Fonts

9. right click on the Fonts folder and save a copy of it just in case you have done something wrong

10. copy and paste all the fonts files you have from your USB thumbdrive to the "Fonts" folder.

----- Your Done! -------

Might as well try "Open Office" from "Source Forge". It's a free software very compatible with Ubuntu. It has the same features of MS Office with slightly different language and commands but easy to learn. They send upgrade notification when available. I use Windows Vista, however, my office and graphics softwares are all free from Source Forge (Open Office, Gimp - photoshop, and Inkscape - like coreldraw). One constraint is that Ubuntu has to be connected to the internet to install. I have Ubuntu only in my other computer but I couldn't connect it to the internet by PLDT DSL so I could not upgrade the Open Office there. But with Vista, Open Office works perfectly well.

---

### Post by joshua.solidum on 2009-04-28
sana nakita ko ang post nato agad
yung Ubuntu hardy heron ko installed as virtual machine(using VMWARE)..gagana ba yung advice mo dito or E install ko lang yung MSOFFICE 2007 using an emulator? how would I go around?any advice?

---

### Post by dmbminaret on 2009-06-10
Works finally. Just a couple of notes to reiterate op's points:

Get wine 1.1.4 from wine debs page.
Uninstall any other version and winetricks. This is what did it for me:

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm


as the menu was still showing up from previous failed attempts.
Then bang, works a charm and copy over fonts from vista.
Even prints first go.


Thanks.

---

### Post by Ravskie on 2009-06-12
Sir may problem ba if M$ Office 07 standard edition ang gamit ko kasi di mag tuloy ang installation ko po.... ?



> **killer_d76 said:**
> sorry for the very late reply.. for those whose having issues with installed MS Office 2007, i would suggest you to report it directly to Winehq website.. 

@ LinnetLegs - were you able to install Ms Office on your rig?.. are you getting errors?



**Additional tip to those who have it installed and having issues with fonts and bullet points**, am not sure if this is legal.. but you could give this a try..

what you need:

a. USB thumbdrive (at least 512mb)

b. Computer or laptop with Windows XP or Vista OS and with MS Office 2007 installed (even trial version is ok)



1. find someone who uses MS Office 2007 (trial version is ok) on their Windows Machine or laptop. 

2. go to "Fonts" by clicking Start> Control Panel > Fonts

3. select all the Font and make sure you just **"copy"** all the fonts files in the "Fonts" folder.

4. on your USB drive create "new folder" and name it as "Fonts".

5. paste all the fonts files you have copied to the "Fonts" folder you have created in your USB thumbdrive.

6. once you done, safely remove your thumbdrive 

7. plug in the USB drive on your Ubuntu rig..

8. then click Applications > Wine > C:\drive > windows > Fonts

9. right click on the Fonts folder and save a copy of it just in case you have done something wrong

10. copy and paste all the fonts files you have from your USB thumbdrive to the "Fonts" folder.

                       ----- Your Done! -------

---

### Post by Darkaiser on 2009-06-13
**"almost all of online games na nilalaro ng anak ko works on wine now!"**

Pati rin ba Level Up Games, My Game, E-games, iam-interactive games po:)?

---

### Post by Script Warlock on 2009-06-13
> **Darkaiser said:**
> **"almost all of online games na nilalaro ng anak ko works on wine now!"**

Pati rin ba Level Up Games, My Game, E-games, iam-interactive games po:)?

not with game guard....

---

### Post by ysNoi on 2009-06-23
Here's the error that I got last night..! Can anyone help me...? :D

---

