---
title: "[SCRIPT] Easily (un)mounting ISO images without sudo"
date: 2008-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-22
While there are many tutorials regarding ISO mounting, I insist posting this howto script, because I believe this script provides more convenient way to mounting/unmounting ISO files.


**[SIZE=4]_Introduction_[/SIZE]**

This script will automatically creates shortcut (of the mounted ISO) to your desktop, so you can easily open and unmount the images later, by right clicking the shortcut itself. Yes, you CAN unmount the (mounted) ISO by right-clicking the desktop shortcut -- without having to browse to the origin folder and unmount from there (but you can do that way too, if you insist :) ).
This script will automatically remove the desktop shortcut when you've unmounted the images.
So you know which ISO's are mounted by looking your desktop.

This script use the fuseiso as a backend.


[SIZE=4]**_Test Machine / Compatible System_**[/SIZE]

I tested this on **[SIZE=2]Ubuntu Gutsy (7.10)[/SIZE]** and **[SIZE=2]Ubuntu Hardy (8.04)[/SIZE]**, with latest update applied.

**Update:**
Also works on:
[LIST]
[*]**[SIZE=2]Debian Leny[/SIZE]**
(Credits to era506 for confirming this)
[*]**[SIZE=2]Kubuntu[/SIZE]**
(Credits to #!/bin/bash for porting this)
[*]**[SIZE=2]Slackware 12.0[/SIZE]**
(Credits to #!/bin/bash for confirming this)
[*]**[SIZE=2]Vector Linux 5.9[/SIZE]**
(Credits to #!/bin/bash for confirming this)
[*][B]SUSE Linux Enterprise Desktop 11
[/B](Credits to arizonagroovejet for confirming this)
[*]Probably working on Gnome and KDE on all latest distro, please confirm if you have tried in your distro.
[/LIST]


[SIZE=4]**_Requirements_**[/SIZE]

[LIST=1]
[*]**[SIZE=3]You must have these programs installed:[/SIZE]**
[LIST]
[*]fuseiso
[*]nautilus-actions
[*]zenity
[/LIST]
To install the requirement, open terminal:
```
Applications -> Accessories -> Terminal
```then type:
```
sudo apt-get install fuseiso nautilus-actions zenity
```and press "Enter". Note: this will also install additional requirement that needed by the above programs.
[*]**[SIZE=3]You have to be a member of "fuse" group.[/SIZE]**
Open Terminal and type:
```

sudo gpasswd -a **yourusername** fuse

```Of course, change "yourusername" to your username.
[*][SIZE=3]**Logout and Login to apply the changes.**[/SIZE]
To gain (apply) the "fuse" privilege, you must to logout and re-login.
[/LIST]


[SIZE=4]**_Installation_**[/SIZE]

**Update:** This section is for Gnome only (nautilus),
- for Gutsy's KDE, please follow #!/bin/bash 's instruction on [#14]("http://ubuntuforums.org/showpost.php?p=4415216&postcount=14"). 
- for Hardy's KDE, please follow Gutsy's KDE instruction and then made little modification on [#36]("http://ubuntuforums.org/showpost.php?p=5189521&postcount=36"). 
(KDE user only need to download the attachment from this post).


[LIST=1]
[*]**[SIZE=3]Create directory called "bin/nautilus-actions" in your home directory[/SIZE]**
Copy and paste this command in Terminal will do that.
```
mkdir -p /home/`whoami`/bin/nautilus-actions
```E.g. if your username is "ladiesman", the resulting directory must be:
```
/home/ladiesman/bin/nautilus-actions
```Note: You must create the directory with the exact name (bin/nautilus-actions), because the script's dependencies currently hard-coded to /home/`whoami`/bin/nautilus-actions/
[*]**[SIZE=3]Download the attachment (fusemounter.tar.gz)[/SIZE]**
**If you're using Ubuntu Hardy 8.04 (or Gnome 2.22.1), please download the fusemounter-hardy.tar.gz instead.**
The tar.gz file contains 2 files:
- fusemounter/fusemounter
- fusemounter/tpl  (will shown as fusemounter/**iso.name** in nautilus, refer to post #5 for explanation)
[*]**[SIZE=3]Extract the attachment to the previously created directory (bin/nautilus-actions)[/SIZE]**
This will put directory called "fusemounter" inside the bin/nautilus-actions.
[*]**[SIZE=3]Open the "Nautilus Actions Configuration"[/SIZE]**
```
System -> Preferences -> Nautilus Actions Configuration
```
[LIST=1]
[*]**Add the "Mount ISO" action**
Press "Add" and enter the values like in this image to the **Menu Item & Action** Tab and the **Conditions** Tab respectively.

[[IMG]http://img395.imageshack.us/img395/952/41zc3.th.png[/IMG]]("http://img395.imageshack.us/my.php?image=41zc3.png")

**Note:** Change "tanto" (in the left picture, on the "Path:" field) to your user name.
[*]**Add the "Unmount ISO" action** (For .iso files)
Press "Add" and enter the values like in this image to the **Menu Item & Action** Tab and the **Conditions** Tab respectively.

[[IMG]http://img355.imageshack.us/img355/231/42vw3.th.png[/IMG]]("http://img355.imageshack.us/my.php?image=42vw3.png")

**Note:** Change "tanto" (in the left picture, on the "Path:" field) to your user name.
[*]**Add the "Unmount ISO" action** (For desktop shortcuts files)
Press "Add" and enter the values like in this image to the **Menu Item & Action** Tab and the **Conditions** Tab respectively.

[[IMG]http://img391.imageshack.us/img391/5342/43fl8.th.png[/IMG]]("http://img391.imageshack.us/my.php?image=43fl8.png")

**Note:** Change "tanto" (in the left picture, on the "Path:" field) to your user name.
[/LIST]
 
[*]**[SIZE=3]Open the "Sessions Configuration"[/SIZE]**
```
System -> Preferences -> Sessions
```
[LIST=1]
[*]Press "Add" and enter the values like in this image to the **Startup Programs** Tab.

_[[IMG]http://img94.imageshack.us/img94/1417/511.th.png[/IMG]]("http://img94.imageshack.us/i/511.png/")_

**Note:** Change "tanto" (on the "Command:" field) to your user name.
[/LIST]
 
[/LIST]


[SIZE=4]**_Usage_**[/SIZE]

[LIST=1]
[*][SIZE=3]**Mounting ISO Image**[/SIZE]
OK, now the fun part, if everything's installed correctly, now you can mount any ISO images file by right-clicking them and choose "Mount ISO". This will automatically creates the desktop shortcut, that you can use to re-open the images or unmount in later time.
[*][SIZE=3]**Unmounting ISO Image**[/SIZE]
Simply right click the desktop shortcut or the original ISO image file, and select "Unmount ISO". This will unmount and removes the desktop shortcut instantly.
[/LIST]

**Update:** There's usage screenshot on the #2 post.


[SIZE=4]**_Uninstallation_**[/SIZE]

[LIST=1]
[*]**[SIZE=3]Remove the Nautilus Action[/SIZE]**
[LIST]
[*]Open the "Nautilus Actions Configuration"
[*]Remove the "Mount ISO", and both the "Unmount ISO" from the list (by pressing "Delete").
[/LIST]
 
[*]**[SIZE=3]Remove the directory "bin/nautilus-actions/fusemounter" from your home directory[/SIZE]**
[/LIST]


[SIZE=4]**_Known Issue_**[/SIZE]
[LIST=1]
[*]**[SIZE=3]SOLVED IN VERSION 1.2[/SIZE]** : If you forget to unmount the ISO images before restart/turn off the computer, the next time you login to your computer, the desktop shortcut is not removed, but you will not be able to open the image, you must manually re-mount the ISO image.
Solution: Don't forget to unmount each time you turn off your computer, BUT, if you really forget, you can simply remove (delete) the desktop shortcut at the next login -- nothing bad will happen.
[/LIST]


[SIZE=4]**_Support_**[/SIZE]

I WILL TRY my best to answer your question regarding this script's installation and usage. BUT -- as usual -- I don't give any WARRANTY for a particular FITNESS NOR RESPONSIBLE for any damage cause by using this script and/or follow this installation guide.


[SIZE=4]**_Bugs Report / Features Request_**[/SIZE]

Please post to this thread if you discover any bugs.
And please post if you have idea to improve this script.
Also, I'm not a bash guru, so if you can improve the script, please do so, and post the enhancement.



Well, that's all, I hope you like this script, and hope this script can help to simplify your desktop experience :p . Feedbacks are welcomed.


**EDIT:**
Changelog
21/11/2009
- Re-upload image for step 5.1 since it seems to be lost from the server somehow.
- Added tested on SUSE Linux Enterprise Desktop 11.
- Gee, it's been a very long time since the last time I visited this forum.

16/06/2008
- Added link to Hardy's KDE modification script.

16/05/2008
- Uploaded the fusemounter-hardy.tar.gz, a compatible version for Hardy Heron (Gnome 2.22.1)
- Removed warning about script "malfunction" and added Hardy Heron as a tested machine for this script.

15/05/2008
- Added warning about script "malfunction" in Hardy Heron.

08/03/2008
- Switch source version to 1.2 & **re-uploaded the new fusemounter.tar.gz attachment**.
- Support for auto-delete (a.k.a. auto-remove) the desktop shortcut for unmounted iso.
- Change the tmppath structure, so there won't be any interfere if two or more user mounting the same ISO (with the same ISO's filename, of course).
- Change the tpl file structure, so it can adapt comply with the new tmppath structure.
- Change the screenshots in main post, so I can upload another picture.

01/03/2008
- Added tested on Slackware 12 & Vector Linux 5.9

28/02/2008
- Added tested on Debian Leny.
- Added link to #!/bin/bash 's post for porting to Kubuntu.

23/02/2008
- Added uninstallation steps.
- Fixed "not working" add-to-group fuse command (from usermod to gpasswd).
- Added the fusemounter/tpl alias shown in nautilus explanation.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-22
I can't post this images to the previous post (because of the forum's restriction I think). Now, here's the some screenshots of the usage:

[LIST=1]
[*]**[SIZE="3"]Mounting ISO image[/SIZE]**

[[IMG]http://img254.imageshack.us/img254/5066/scbeforejj0.th.png[/IMG]](http://img254.imageshack.us/my.php?image=scbeforejj0.png)

You can see in the 2nd image, the shortcut for the ISO appears instantly on the desktop.


[*]**[SIZE="3"]Unmounting (mounted) ISO from desktop[/SIZE]**

[[IMG]http://img258.imageshack.us/img258/2121/scafterki8.th.png[/IMG]](http://img258.imageshack.us/my.php?image=scafterki8.png)

After you select "Unmount ISO", the shortcut will be removed, and the ISO will be unmounted.
[/LIST]

---

### Post by Voidhawk9 on 2008-02-22
I can't get this to work...yet.
As far as I can tell, I've done everything as laid out in your post, but when I click 'Mount' nothing happens.
One discrepancy I noted: The files you attached are 'fusemounter' and 'iso.name' instead of the claimed 'fusemounter' and 'tpl'. Perhaps this is the issue?

I hope this can be resolved, I really like the idea!

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-23
> **Voidhawk9 said:**
> I can't get this to work...yet.
As far as I can tell, I've done everything as laid out in your post, but when I click 'Mount' nothing happens.
One discrepancy I noted: The files you attached are 'fusemounter' and 'iso.name' instead of the claimed 'fusemounter' and 'tpl'. Perhaps this is the issue?

I hope this can be resolved, I really like the idea!

Hi Voidhawk9, thanks for trying this script!

Sorry, seems that the mistake is this command:
"sudo usermod -a fuse -G yourusername"

Please execute this command in the terminal:
```

sudo gpasswd -a **yourusername** fuse

```
Note: change "yourusername" to your username.

Logout and re-login.
Sorry for the inconvenience, I have fixed the original thread now.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-23
Voidhawk9, forget to mention, the included files:
- fusemounter/fusemounter
- **fusemounter/tpl**

will appear like this in nautilus:
- fusemounter/fusemounter
- **fusemounter/iso.name**

This is normal, if you see from terminal, it will print the "original" name, which is fusemounter/tpl. This happens because the "tpl" file actually is a *.desktop (configuration) file, and nautilus will automatically display the name according to the value inside this file (which is Name=iso.name) in this case.

---

### Post by Voidhawk9 on 2008-02-23
That's got it, works perfectly. Thanks for posting this! :)

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-23
You're welcome :)

---

### Post by nilarimogard on 2008-02-23
It works, thank you!

---

### Post by handy on 2008-02-26
It works perfectly for me. :-D

Thank you very much for posting the great how-to for us.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-26
> **nilarimogard said:**
> It works, thank you!

> **handy said:**
> It works perfectly for me. :-D

Thank you very much for posting the great how-to for us.

Hi, thank you for trying this script!

---

### Post by era506 on 2008-02-26
WOW!! This is so cool!! Works great on Debian Lenny. Thank you very much!!!!

---

### Post by handy on 2008-02-26
> **Milk & Toast & Honey said:**
> Hi, thank you for trying this script!

I gave it a really good work out last night & it is absolutely brilliant when used to check a dvd.iso that you have just ripped with K9Copy.

Your script really should be incorporated into Ubuntu I think.

---

### Post by nilarimogard on 2008-02-27
> **handy said:**
> I gave it a really good work out last night & it is absolutely brilliant when used to check a dvd.iso that you have just ripped with K9Copy.

Your script really should be incorporated into Ubuntu I think.

I agree... it would be great for new users. Just one click to mount an .iso

---

### Post by #!/bin/bash on 2008-02-27
First, thanks to Milk & Toast & Honey

> # anybody can tell me how to do this more "right" ?
isopath=`cat "$isopath" | grep PathToIso | sed "s/PathToIso=//"`

isopath=$(grep PathToIso $isopath| sed "s/PathToIso=//")


I took the liberty to adapt this to Kubuntu.  I changed the fusemounter dir to $HOME/.fusemounter, if you change this then change the fusemounter script also.
The template file needs a slight change before you can unmount the iso from the Desktop Icon:

$HOME/.fusemounter/tpl
```
[Desktop Action Unmount]
Exec=$HOME/.fusemounter/fusemounter unmount path.to.iso
Name=Unmount
Icon=cdtrack

[Desktop Entry]
Actions=Unmount
Encoding=UTF-8
Version=1.0
Type=Link
URL=/tmp/iso.name
Name=iso.name
Icon=cdimage
PathToIso=path.to.iso
```

To make it work you need to change file associations in Konqueror:

Settings -> Configure Konqueror -> File Associations 
 Click the + next to applications and scroll down and click on x-iso
Click Add in Application Preference Order
Browse to $HOME/.fusemounter/ and click on fusemounter script and click OK
Back in Application Preference Order select fusemounter and click Edit then click Application tab.
Change Name to Mount ISO or whatever you like.
In Command box you should have this:
/home/<user>/.fusemounter/fusemounter mount %U
Click OK then Apply.

The Unmount application is the same except the name will be Unmount ISO and the command will be:
/home/<user>/.fusemounter/fusemounter unmount %U

NOTE: This also changes associations for dolphin. Also in the fusemounter script you can change 
browser=konqueror or dolphin if you like.

[color=blue][font=bold]Also Works in New KDE4[/font][/color]
To make this work with the new KDE4 only requires a few minor changes to the original procedure for KDE3.

The file associations are set using System Settings;
On my computer its KMenu -> System -> System Settings
Click on Advanced tab then on File Associations.
Open the Applications and look for x-cd-image.
Under Application Preference Order you would add /path/to/fusemounter then select fusemounter and Edit. Change the name to Mount and do this one more time and name it UnMount and set the Commands like this:
Mount command would be /path/to/fusemounter mount %U
and
UnMount command would be /path/to/fusemounter unmount %U

To unmount from the file on the desktop is a little trickier. Maybe there is another way but what I did was to create a new file association, I called it x-fusemounter. The way you do this is under Known Types you click Add, select Applications for the group and choose a unique name, like I said I chose x-fusemounter. Now in the Filename Patterns you click Add and the extension would be *.fusemounter.desktop. You can give it a description if you like. Then in Application Preference Order you add /path/to/fusemounter click OK then select fusemounter and Edit the entry and name it UnMount and change the command to this:
Command = /path/to/fusemounter unmount-desktop %U

EDIT:
Oops! It seems the default action when clicking on the desktop icon is to unmount the iso file which should not be the default. The default action should be to open the mounted iso image with our default browser. To do this we have to add another application to the Application Preference Order in file associations for x-fusemounter. 

Select Add in Application Preference Order. Choose /path/to/fusemounter as the application. Click Ok and then edit the fusemounter entry. I changed the name to Open. Then in the command put this /path/to/fusemounter open %U. Save and Apply.

Now you have to edit the fusemounter script and add a function to open. Put the function below in the script. I put it right after the conf_open function.

```
# Open the target dir using default browser
browser_open() {
desktopfile="$isopath"
# $isopath is in the *.iso.fusemounter.desktop file, read the template.
isopath=$(grep PathToIso $desktopfile| sed "s/PathToIso=//")
isoname=$(basename "$isopath")
tmppath="/tmp/$isoname"
exec $browser "$tmppath"
return 1;
}
```

Also in the case section add an open) section like this:

```
        open)
                browser_open
                ;;


```
Make sure when you are done that Open is at the top of Application Preference Order so it will be the default action.


[color=blue]Making a ServiceMenu[/color]
The Mount and UnMount actions can also be accomplished using a ServiceMenu. 

```
[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/x-cd-image;
Actions=MountWithFuse;

[Desktop Action MountWithFuse]
Exec=/path/to/fusemounter mount %F
Name=Mount ISO Image with fusemounter...
Name[af]=Skryf CD of DVD beeld lêer m.b.v. K3b...
Name[ar]= &#1575;&#1603;&#1578;&#1576; &#1589;&#1608;&#1585;&#1577; &#1593;&#1604;&#1609; &#1575;&#1604;&#1602;&#1585;&#1589; &#1575;&#1604;&#1605;&#1583;&#1605;&#1580; (CD) &#1575;&#1608; &#1593;&#1604;&#1609; &#1575;&#1604;&#1602;&#1585;&#1589; &#1575;&#1604;&#1605;&#1585;&#1574;&#1610; &#1575;&#1604;&#1585;&#1602;&#1605;&#1610; (DVD) &#1576;&#1608;&#1575;&#1587;&#1591;&#1577;  K3b .
Name[bg]=&#1047;&#1072;&#1087;&#1080;&#1089; &#1085;&#1072; CD &#1080;&#1083;&#1080; DVD &#1086;&#1073;&#1088;&#1072;&#1079; &#1089; K3b...
Name[bn]=&#2453;&#2503;-&#2469;&#2509;&#2480;&#2495;-&#2476;&#2495; &#2470;&#2495;&#2527;&#2503; &#2488;&#2495;&#2465;&#2495; &#2437;&#2469;&#2476;&#2494; &#2465;&#2495;&#2477;&#2495;&#2465;&#2495; &#2439;&#2478;&#2503;&#2460; &#2482;&#2503;&#2454;&#2507;...
Name[br]=srivañ ur skeudenn CD pe DVD gant K3b*...
Name[ca]=Escriu imatge de CD o DVD amb el K3b...
Name[cs]=Vypálit obraz CD nebo DVD pomocí K3b...
Name[da]=Skriv cd- eller dvd-billede med K3b...
Name[de]=CD/DVD-Abbild mit K3b brennen ...
Name[el]=&#917;&#947;&#947;&#961;&#945;&#966;&#942; &#949;&#953;&#954;&#972;&#957;&#945;&#962; CD &#942; DVD &#956;&#949; &#964;&#959; K3b...
Name[eo]=Skribu KD a&#365; DVD imagon per K3b...
Name[es]=Grabar imagen de CD o DVD con K3b...
Name[et]=Kirjuta CD- või DVD-tõmmis K3b abil plaadile...
Name[fa]=&#1606;&#1608;&#1588;&#1578;&#1606; &#1578;&#1589;&#1608;&#1740;&#1585; &#1583;&#1740;&#1587;&#1705; &#1601;&#1588;&#1585;&#1583;&#1607; &#1740;&#1575; &#1583;&#1740; &#1608;&#1740; &#1583;&#1740; &#1576;&#1575; K3b...
Name[fi]=Polta levykuva cd- tai dvd-levylle K3b:llä...
Name[fr]=Graver une image CD ou DVD avec K3b...
Name[gl]=Escrever unha Imaxe de CD ou DVD con K3b...
Name[hu]=CD- vagy DVD-képmásfájl írása a K3b-vel...
Name[is]=Skrifa CD eða DVD mynd með K3b...
Name[it]=Scrivi immagine CD o DVD con K3b...
Name[ja]=K3b &#12391; CD/DVD &#12452;&#12513;&#12540;&#12472;&#12434;&#26360;&#12365;&#36796;&#12415;...
Name[ka]=K3b-&#4312;&#4311; CD &#4304;&#4316; DVD &#4306;&#4304;&#4315;&#4317;&#4321;&#4304;&#4334;&#4323;&#4314;&#4308;&#4305;&#4312;&#4321; &#4329;&#4304;&#4332;&#4308;&#4320;&#4304;...
Name[km]=&#6047;&#6042;&#6047;&#6081;&#6042;&#8203;&#8203;&#6042;&#6076;&#6036;&#6039;&#6070;&#6038;&#8203;&#6047;&#6090;&#6072;&#6028;&#6072; &#6060;&#8203;&#6028;&#6072;&#6044;&#6072;&#6028;&#6072;&#8203;&#6026;&#6084;&#6041;&#8203;&#6036;&#6098;&#6042;&#6078; K3b...
Name[lt]=&#302;ra&#353;yti CD ar DVD atvaizd&#261; su K3b...
Name[mk]=&#1047;&#1072;&#1087;&#1080;&#1096;&#1077;&#1090;&#1077; CD &#1080;&#1083;&#1080; DVD-&#1089;&#1083;&#1080;&#1082;&#1072; &#1089;&#1086; K3b...
Name[ms]=Tulis Imej CD atau DVD dengan K3b...
Name[nb]=Skriv CD- eller DVD-bilde med K3b . . .
Name[nds]=CD- oder DVD-Afbild mit K3b schrieven...
Name[nl]=CD of DVD-image schrijven met K3b...
Name[nn]=Brenn CD- eller DVD-bilete med K3b &#8230;
Name[pa]=K3b &#2600;&#2622;&#2610; CD &#2588;&#2622;&#2562; DVD &#2602;&#2637;&#2608;&#2596;&#2624;&#2604;&#2623;&#2672;&#2604; &#2610;&#2623;&#2582;&#2635;...
Name[pl]=Nagraj obraz p&#322;yty CD lub DVD na p&#322;yt&#281; za pomoc&#261; K3b...
Name[pt]=Escrever uma Imagem de CD ou DVD com o K3b...
Name[pt_BR]=Gravar Imagem de CD ou DVD com o K3b...
Name[ru]=&#1047;&#1072;&#1087;&#1080;&#1089;&#1072;&#1090;&#1100; &#1086;&#1073;&#1088;&#1072;&#1079; CD &#1080;&#1083;&#1080; DVD, &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1103; K3b...
Name[sk]=Zapísa&#357; obraz CD alebo DVD pomocou K3b...
Name[sr]=&#1059;&#1087;&#1080;&#1096;&#1080; CD &#1080;&#1083;&#1080; DVD &#1086;&#1076;&#1088;&#1072;&#1079; &#1087;&#1086;&#1084;&#1086;&#1115;&#1091; K3b-&#1072;...
Name[sr@Latn]=Upi&#353;i CD ili DVD odraz pomo&#263;u K3b-a...
Name[sv]=Skriv cd- eller dvd-avbild med K3b...
Name[tg]=&#1057;&#1072;&#1073;&#1090; &#1082;&#1072;&#1088;&#1076;&#1072;&#1085;&#1080; &#1090;&#1072;&#1089;&#1074;&#1080;&#1088;&#1080; CD &#1105; DVD &#1073;&#1086; &#1080;&#1089;&#1090;&#1080;&#1092;&#1086;&#1076;&#1072;&#1073;&#1072;&#1088;&#1080;&#1080; K3b...
Name[tr]=K3b ile CD ya da DVD görüntüsü Yazd&#305;r...
Name[uk]=&#1047;&#1072;&#1087;&#1080;&#1089;&#1072;&#1090;&#1080; &#1096;&#1090;&#1072;&#1084;&#1087; &#1050;&#1044; &#1072;&#1073;&#1086; DVD &#1091; K3b...
Name[uz]=K3b yordamida CD yoki DVD tasvirini yozish
Name[uz@cyrillic]=K3b &#1105;&#1088;&#1076;&#1072;&#1084;&#1080;&#1076;&#1072; CD &#1105;&#1082;&#1080; DVD &#1090;&#1072;&#1089;&#1074;&#1080;&#1088;&#1080;&#1085;&#1080; &#1105;&#1079;&#1080;&#1096;
Name[zh_CN]=&#29992; K3b &#21051;&#24405; CD &#25110; DVD &#26144;&#20687;...
Name[zh_TW]=&#20351;&#29992; K3b &#29138;&#37636; CD &#25110; DVD &#24433;&#20687;...
Icon=cdimage

```Paste the above code into a file called fusemounter-mount-iso-image.desktop. Make a copy called fusemounter-unmount-iso-image.desktop then edit it and change these lines
```
Actions=UnMountWithFuse;

[Desktop Action UnMountWithFuse]
Exec=/path/to/fusemounter unmount %F
Name=UnMount ISO Image with fusemounter...

```
Now put both of the files in /usr/share/kde4/services/ServiceMenus/

Make sure you correct the /path/to/fusemounter to match your system.

---

### Post by handy on 2008-02-27
> **nilarimogard said:**
> I agree... it would be great for new users. Just one click to mount an .iso

Why just new users?  

Do the old users prefer to do things the slow way?

I expect that there are only a tiny percentage of computer users that would not want to take advantage of such an elegant script that mounts & unmounts .iso's in one click of the left mouse button. :-D

---

### Post by resadent on 2008-02-27
Nice work! What is your gtk2 theme? I like it!

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-27
Hi all, thank you for the comments and for using this script!
I hope this script can be very helpful for many people, so it can be incorporated to Ubuntu :p or should I fill some form?
Your comments really gives me spirit, thank you.


> **#!/bin/bash said:**
> 
isopath=$(grep PathToIso $isopath| sed "s/PathToIso=//")

Thank you for this! I really forget that "grep" can read files on it's own. Also, thank you for taking the time to adapt this script for Kubuntu, I'll update the first post to refer to your post.

[QUOTE=resadent]Nice work! What is your gtk2 theme? I like it![/QUOTE]
I'm using:
- [aero-clone]("http://www.gnome-look.org/content/show.php/Aero-clone?content=57352") for the "Controls Theme".
- [Murrina-AeroSky]("http://www.gnome-look.org/content/show.php/Murrina-AeroSky?content=65677") for the "Window Border Theme".
- [nuoveXT 2]("http://www.gnome-look.org/content/show.php/nuoveXT+2?content=56625") for the "Icon Theme".

---

### Post by handy on 2008-02-27
Your script should be incorporated into Hardy, I don't know how to do it, I will ask how, you should too Milk & Toast & Honey.

---

### Post by #!/bin/bash on 2008-02-28
The Kubuntu version will probably work on any KDE based distro. I have checked it on Slackware-12.0 and VectorLinux-5.9 and they both work.

---

### Post by handy on 2008-02-28
Beautiful

---

### Post by Milk &amp; Toast &amp; Honey on 2008-03-01
> **#!/bin/bash said:**
> The Kubuntu version will probably work on any KDE based distro. I have checked it on Slackware-12.0 and VectorLinux-5.9 and they both work.

Thanks for checking this! I'll update the first post.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-03-08
Hi all, I've added some minor improvement for this script, which are:
[LIST]
[*]Automatically removes the desktop shortcut after restarting the computer.
[*]Enhanced the "tmp" directory structure so won't clash with multiuser mount.
[/LIST]

For you who have downloaded the previous version, please redownload the "fusemounter.tar.gz", extract and replace the 2 files from previous version, and follow the "Installation" instruction step number 5. **EDIT**: Oops, forget to mention, please unmount all ISO files before you update the fusemounter.tar.gz.

For you who are new user :), just follow the instructions from the #1 post.

For complete changelog, refer to #1 post.

Thank you.

---

### Post by red_five on 2008-05-12
This works nicely for me. I think I made a couple of tweaks to the script, but I don't remember offhand what they might have been. I played around for a while to see if I could read the autorun.inf file on the CD (if it existed) and display the appropriate CD icon, but some CDs don't have a something.ico file, but instead use a resource inside the exe file (if it's an ISO for a Windows app). I suppose that I could go ahead and make it work with ICO files anyway.

UPDATE: I re-read a note in the script, function autoremove_desktop_file():
```
# according fuseiso manual, we can get the info about 
# the mounted fuseisos from ~/.mtab.fuseiso, but I don't know
# how to convert ' ' (space) to \040 notation from ~/.mtab.fuseiso or
# /etc/mtab, nor how to `grep`-ing `mount` output, so I made one 
# temporary file from the `mount` command output
```

I just took a look at my .mtab.fuseiso file, and it already has the \040 encoding for spaces. But I'm not sure you'd need to worry about that, because I've got a quick line to parse the output of mount:
```
mount | grep -i "$i" | sed -e 's/fuseiso on //' -e 's/"$i".*/"$i"/'
```
At any rate, here's my modification of autoremove_desktop_file():
```

autoremove_desktop_file() {
for i in $HOME/Desktop/*.fusemounter.desktop
	do
		if [ -z $(mount | grep -i "$i" | sed -e 's/fuseiso on //' -e 's/"$i".*/"$i"/') ]
		then
			rm "$i"
		fi
	done
}

```

Hope that helps.

---

### Post by red_five on 2008-05-12
I've taken the liberty of exporting my Nautilus Actions configurations for the three actions you mention in the initial post. Everyone should be able to import these config files into their own Nautilus Actions panels, assuming that the script is in ~/bin/fusemounter/*.

---

### Post by Peter Great on 2008-05-13
I wish in a future Ubuntu distribution Nautilus would have this 'right click' mounting functionality installed by default. That would make it much easier to use for new users.

---

### Post by Attentah on 2008-05-13
Hello, I use Ubuntu Hardy (8.04) and nearly everything works !
But (yeah there's a "but") there are no desktop icons when I mount an ISO image. I tried with several ISO and rebooted many times but I can't see the shortcuts on my Desk...
Could someone help me?

(I also hope this tweak will be integrated in Ubuntu 8.10..!)

---

### Post by rekado on 2008-05-14
This script is wonderful, thanks man!
I'm missing the last picture for the session modification (should be [http://img247.imageshack.us/my.php?image=511ob7.png](http://img247.imageshack.us/my.php?image=511ob7.png)). Is it just me?


EDIT: yes, it was just me. Couldn't open the picture on imageshack. Can see it now.

Rekado

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-14
red_five, thank you for your suggestion and the attachment. I haven't tried your suggestion yet, but it looks promising :) , and we don't need to create a temporary file anymore.

Peter Great, I agree with you, I think it would be nice if the default nautilus has this functionality. And, AFAIK, many people already implement that functionality through scripts, but I never seen any of those script included in linux distribution, at least not in SuSE 9,10 or Ubuntu.

Attentah, I just upgraded my machines to Hardy (from Gutsy) today, I got the desktop shortcut shown, although it's not working like in Gutsy, e.g. the ISO content isn't displayed, showing this message: "There is no application installed for this file type". But it did mount though, so I think there's some changes the way nautilus handles the *.desktop files. I'll investigate this as soon as I have the time.

rekado, yes, that is the image for the session modification. I changed my desktop themes recently, but forget to revert back to match to the previous pictures, sorry for that confusion.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-15
Howdy all...

I've updated the script for Ubuntu Hardy 8.04.

If you're using Hardy and want to use this script, please follow the instruction and download the fusemounter-hardy.tar.gz, otherwise, the fusemounter.tar.gz will work for previous version of Ubuntu.

If you already install this script and want to upgrade your machine to Hardy, simply download the fusemounter-hardy.tar.gz and extract it (overwrite the previous installation). No additional steps required.

For complete changelog, refer to #1 post

Thank you.

PS. Feedbacks are welcome guys, please do post comments if you're using this script :) .

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-15
> **Attentah said:**
> Hello, I use Ubuntu Hardy (8.04) and nearly everything works !
But (yeah there's a "but") there are no desktop icons when I mount an ISO image. I tried with several ISO and rebooted many times but I can't see the shortcuts on my Desk...
Could someone help me?

(I also hope this tweak will be integrated in Ubuntu 8.10..!)

Attentah, I've updated the script, please download the fusemounter-hardy.tar.gz.

Does the update fix your problem?

PS. I would be happy to assist you or anyone to fix the problem that may exist regarding the script installation / usage.

---

### Post by red_five on 2008-05-18
I noticed one thing about the exported actions I attached above: they saved the absolute path to the scripts from my work system, so when I imported them onto my laptop at home, I had to change the paths. Just watch for that if anyone decided to import my actions.

---

### Post by Attentah on 2008-05-20
Hum... Both scripts work, but aren't they the same?
There is still no desktop icon for me... :(

---

### Post by Attentah on 2008-05-20
I forget to ask: how do I make FIFA believe the mounted ISO is a false "real" CD ? (I hope you understood me xD)

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-20
> 
Hum... Both scripts work, but aren't they the same?

Both are the same, but the hardy version contains some small addition.

> 
There is still no desktop icon for me... 

Have you set the nautilus to show the desktop (in gconf-editor) ?
Usually the default Ubuntu comes with this value set to checked, but checked it for sure tho.
Open gconf-editor and navigate to:
```

apps -> nautilus -> preferences -> show_desktop = checked (true)

```
make sure that show_desktop is checked.

> 
I forget to ask: how do I make FIFA believe the mounted ISO is a false "real" CD ? (I hope you understood me xD) 

Well, I don't know how, but usually people use the so-called NO-CD hack/crack, which can by pass the CD check thingy.

---

### Post by digitall.doc on 2008-06-14
This is my first post in this forum...

I'm running Kubuntu Hardy. Not a experienced user: I dual-booted for a year with Feisty, and finally decided to switch to Kubuntu-only (well, with some virtualization of XP 'needed' applications...). A lot to learn.

I followed post #14 to install in kubuntu. Fuseiso already in default installation, my user a member of fuse... Changed fusemounter and tpl to .fusemounter dir, and changed the scripts:
In .fusemounter/fusemounter changed
```
...
browser="dolphin"
...
tpldesktopfile="/home/$whoami/.fusemounter/tpl"
...
```
In .fusemounter/tpl I pasted the code suggested in #14.

When I select mount ISO in context menu, it shows the 'jumping icon', but nothing happens, no desktop icon created. And when I browse to /tmp/fusemounter-user/, there's no file or directory.

I'm doing something wrong, for sure, but I couldn't discover what... :(

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
Hi digitall.doc, 

for Hardy version, you have to modify the fusemounter/tpl file to something
like this (the bold part):

```

[Desktop Action Unmount]
Exec=$HOME/.fusemounter/fusemounter unmount path.to.iso
Name=Unmount
Icon=cdtrack

[Desktop Entry]
Actions=Unmount
Encoding=UTF-8
Version=1.0
Type=Link
**URL=file://url.to.tmp**
Name=iso.name
Icon=cdimage
PathToIso=path.to.iso
```Also makes sure to have these packages installed:
fuseiso & zenity .

Please note that fuseiso9660 is different with fuseiso.

---

### Post by digitall.doc on 2008-06-15
Thanks for your help.
Now I managed to mount iso in /tmp. I'm afraid fuseiso wasn't installed (I would have sweared it was...).

But I doesn't get a desktop icon yet.
I modified tpl the way you advised, and tried again with #!/bin/bash version (...just in case), but with no success.
In file associations I already added to x-iso mount and unmount.

There's another difference between your code and that of #!/bin/bash: your command is mount %d/%f, and #!/bin/bash is mount %U. I'm using this last one, and as it is mounting well, I guess is correct.
What am I doing wrong now?.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
Hi digitall.doc,

which version of KDE are you using? The 3.5 or the 4.0 ?
I've tried with the 3.5, and the icon showing properly on the desktop.
But with 4.0, sometimes the icons indeed not showing, I have to refresh the desktop to get the icon shown. Also, the "Unmount ISO" don't seems to working with KDE 4.0.

Some notes, if you're downloaded the Hardy version, you should modified the "tpl" file according to my advise -- for the "URL" section, if not, the ISO won't properly opened or unmounted at later time. (The "URL" part is slightly different with the Gutsy's version).

Also, can you go to your "Desktop" folder from Konqueror or Dolphin? (The full path is /home/<yourname>/Desktop.) Are there any icons for the mounted ISO there?

---

### Post by digitall.doc on 2008-06-15
Hi M&T&H,
I'm using KDE 3.5

Already modified tpl following your last code.

When I mount an iso, I can't see the icon on Desktop ('Escritorio' in my spanish Kubuntu), neither when I browse to desktop folder.

It does unmount well when I right click on iso file and select unmount iso.

Will it be anything wrong in file associations cofiguration?.

Thanx for your help.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
> 
When I mount an iso, I can't see the icon on Desktop ('**Escritorio**' in my spanish Kubuntu), neither when I browse to desktop folder.
Now, there's the problem is. LOL. Sorry, when making this script, I must be thinking that all users are using the English version of Ubuntu (I know it's stupid, my mistake, sorry).

Here's the modified script for your language (Spanish):
```

#!/bin/bash
#
# FuseMounter
# Mount ISO file to /tmp and open it with nautilus, and show the mounted
# file to user's desktop, for conveniently opening / unmounting for later.
#
# Parameter(s): 
# #1 : operation (mount,unmount,unmount-desktop,auto-remove)
# #2 : full path to iso (includes the file name) or the desktop shortcut CREATED using this script
#
#
# @author Sutanto Kurniawan (tanto@lugi.or.id) a.k.a. "Milk & Toast & Honey" from ubuntuforums.org
# @version $Revision: 1.3 $
#
# Bug Reports & Ideas:
# Please report if you find any, by posting it to http://ubuntuforums.org/showthread.php?t=704350
#
# Changelog:
# 16/05/2008
# - Compatible version for Hardy Heron (Gnome 2.22)
#   It seems to open shortcut from desktop files, the URL must written in the form of
#   file://<path> as of Gnome 2.22's Nautilus.
# - Change the tpl file value for URL section.
#
# 08/03/2008
# - Support for auto-delete (a.k.a. auto-remove) the desktop shortcut for unmounted iso.
# - Change the tmppath structure, so there won't be any interfere if two or more user mounting
#   the same ISO (with the same ISO's filename, of course).
# - Change the tpl file structure, so it can adapt comply with the new tmppath structure.
# - Small fix on the return values and grep format (based on "!/bin/bash" from ubuntuforums.org 
#   recommendation).
#
# 22/02/2008
# - Initial commit.

title="Fuse Mounter"
browser="nautilus"
desktop_name="**Escritorio**"
isopath=$2
isoname=`basename "$2" 2> /dev/null`
whoami=`whoami`
tmppath="/tmp/fusemounter-$whoami/$isoname"
tpldesktopfile="/home/$whoami/bin/nautilus-actions/fusemounter/tpl"

# mkdir in /tmp and mount the iso to there
mount_iso() {
    mkdir -p "$tmppath"
    if fuseiso "$isopath" "$tmppath"
    then
        return 0;
    else
        rmdir "$tmppath"
        return 1;
    fi
}

# Unmount & rm tmp dir, fusermount.desktop file (when right-clicked from the origin iso file)
unmount_iso() {
    desktopfile="/home/$whoami/$desktop_name/$isoname.fusemounter.desktop"
    rm "$desktopfile"

    unmount_real
}

# Umount & rm tmp dir, fusermount.desktop file (when right-clicked from the desktop), and
# removes the *.iso.desktop file.
# Basically this function just "correcting" the required
# variable used by unmount_real() , and simply calling the 
# unmount_real() afterwards.
unmount_iso_from_desktop() {
    desktopfile="$isopath"

# $isopath now contained the *.iso.desktop file, read the template.
# thanks to "#!/bin/bash" from ubuntuforums.org for this grep code :)
    isopath=$(grep PathToIso "$desktopfile" | sed "s/PathToIso=//")

    isoname=`basename "$isopath"`
    tmppath=$(grep URL "$desktopfile" | sed "s\\URL=file://\\\\")
    rm "$desktopfile"

    unmount_real
}

# Unmount & rm tmp dir
unmount_real() {
    if !(test -d "$tmppath")
    then
        zenity --info --title "$title" --text "$isoname is not mounted."
    else
        if fusermount -u "$tmppath"
        then
            rmdir "$tmppath"
            zenity --info --title "$title" --text "$isoname Unmounted."
        fi
    fi
    return 0;
}

# Creates nice desktop shortcut that can be used for opening and unmounting.
create_desktop_file() {
    sed "s\\iso.name\\$isoname\\" "$tpldesktopfile" \
        | sed "s\\path.to.iso\\$isopath\\" \
        | sed "s\\url.to.tmp\\$tmppath\\" \
        > "/home/$whoami/$desktop_name/$isoname.fusemounter.desktop"
}

# Auto-delete the unmounted desktop shortcut file (preferably call this when 
# logon,e.g. put this on the auto-started in session config)
autoremove_desktop_file() {
# according fuseiso manual, we can get the info about 
# the mounted fuseisos from ~/.mtab.fuseiso, but I don't know
# how to convert ' ' (space) to \040 notation from ~/.mtab.fuseiso or
# /etc/mtab, nor how to `grep`-ing `mount` output, so I made one 
# temporary file from the `mount` command output
    mounted="/tmp/fusemounter.mounted"
    mount > $mounted

    for i in /home/$whoami/$desktop_name/*.fusemounter.desktop; do
        url=`grep 'URL' "$i" | sed "s\\URL=file://\\\\"`
        if !(grep -iq "$url" $mounted)
        then
            rm "$i"
        fi
    done

    rm $mounted
}

# Confirm whether the user wants to open the target dir or not
conf_open() {
    if `zenity --question --title "$title" --no-wrap --text "$isoname Mounted. Open?\n\nNote: You can open later by double-clicking the icon on your desktop."`
    then
        exec $browser "$tmppath"
    fi
    return 0;
}

# main()
case "${1:-}" in
    mount)
        if mount_iso; then
            create_desktop_file
            conf_open
        fi
        ;;
    unmount)
        unmount_iso
        ;;
    unmount-desktop)
        unmount_iso_from_desktop
        ;;
    auto-remove)
        autoremove_desktop_file
        ;;
    *)
        usage="Usage $0 {mount|unmount|unmount-desktop|auto-remove} /path/to/iso/file"
        zenity --info --title "$title" --text "$usage" &
        echo "$usage"
esac

exit 0

```Open your /home/<yourname>/.fusemounter/fusemounter file with "Text Editor", and replace the contents with the code above.

---

### Post by digitall.doc on 2008-06-15
Great!,
a step forward. Now I have a desktop icon, called 'DISK4.iso.fusemounter'.

But when I selecy OK, it opened /tmp/fusemounter/iso in file browser previously. Now it just puts an icon on desktop. When I click on the desktop icon, it throws an error:
```
El archivo de entradas del escritorio /home/ximo/Escritorio/DISK4.iso.fusemounter.desktop
no tiene entrada Tipo=...
```
and doesn't open the /tmp/fusemounter/iso (that is correctly created).
When right-click on desktop icon, there's no unmount option (don't know if this is right)
When right-click on iso, and select unmount, correctly unmounts and disappear desktop icon...

Sorry me for being such a pain...:confused:

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
That's strange, it's just working as expected in my machine.
Can you post the content of /home/ximo/Escritorio/DISK4.iso.fusemounter.desktop file?
Open the file using the "Text Editor" and paste the output here.

No need to feel sorry :) , I'll try to assist you the best I can.
Actually, I created this for Gnome desktop, so I'm really sorry if this not working "out-of-box" in KDE.

---

### Post by digitall.doc on 2008-06-15
Hi,
when I open the fusemounter.desktop file with kate, it's empty!.

I also don't know if this is the normal behaviour, but when I right-click on iso file, mount and unmount iso options appear under 'Abrir con' ('Open with'), and not under 'Acciones' ('Actions').

I keep believing maybe I did something wrong with configuration of file associations. What I did:
Kmenu > System configuration > Default applications > File associations > Application > x-iso > General tab. Under Applications preference order > Add > fusemounter. Then Edit > Application > $home/.fusemounter/fusemounter mount %U

Is this OK?.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
Hi digitall.doc, 

The previous code I posted, I forget to tell you, that I wasn't change the "tpldesktopfile" value, so you have to adjust the value to your setup, which is:
```

tpldesktopfile=**"/home/$whoami/.fusemounter/tpl"**

```It's located in line 43 inside the ".fusemounter/fusemounter" file.

As for right clicking the ISO file, yes, the "actions" located in the "Open with..." menu, same thing happened on my KDE test machine. But for the desktop icon, the "Unmount" will be located in the "Action" menu.
You didn't do anything wrong with the configuration, that's exactly what I did in my setup.

Also, for the existing desktop icon (the empty / error ones), you can safely delete them from your desktop. After you restarted your machine, the mounted ISO will be unmounted.

---

### Post by digitall.doc on 2008-06-16
Hi M&T&H,

we're getting there!.

After correcting fusemounter code, I'm getting a desktop icon. And when I click it, I get to the iso mounted!!.

When I 'answer' OK to the question whether I want to open the mounted iso (when right-clicking on iso file, before getting a desktop icon), I still don't get to the /tmp folder (I used to, before). But when I click on desktop icon, I open the /tmp folder.

And when I right click on desktop icon and Action > Unmount, it says unmounted, but desktop icon persists, and iso keeps mounted. If I right click on iso and select Unmount, it then unmounts iso, disappear /tmp folder, and disappear desktop icon... So it unmounts well from iso file, but badly from desktop icon.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-17
Hi digitall.doc, 

> 
When I 'answer' OK to the question whether I want to open the mounted iso (when right-clicking on iso file, before getting a desktop icon), I still don't get to the /tmp folder (I used to, before). But when I click on desktop icon, I open the /tmp folder.
Have you change the "browser" value to "dolphin" or "konqueror"? I've should told you that you should change the browser to your prefered browser (following !#/bin/bash instruction), the default value is nautilus, which I'm sure the default Kubuntu won't install it ;p
It's on .fusemounter/fusemounter file on line 37.

> 
And when I right click on desktop icon and Action > Unmount, it says unmounted, but desktop icon persists, and iso keeps mounted. If I right click on iso and select Unmount, it then unmounts iso, disappear /tmp folder, and disappear desktop icon... So it unmounts well from iso file, but badly from desktop icon.
For this problem, I'm not quite sure why is this happened, as this don't happened in my machine, it could be because of the language problem though. For starting point, mount an ISO file, and later open the "Desktop Icon" with "Text Editor".
You'll find the file contains something like this:
```

[Desktop Action Unmount]
Exec=**$HOME/.fusemounter/fusemounter unmount /path/to/youriso.iso**
Name=Unmount
Icon=cdtrack

[Desktop Entry]
etc etc..

```Copy the bold part, and paste it to the terminal, press Enter, and paste the output here.
Also, please post the exact content of the "Desktop File" here.


Regards,
MTH.

---

### Post by digitall.doc on 2008-06-17
> **Milk & Toast & Honey said:**
> Have you change the "browser" value to "dolphin" or "konqueror"? I've should told you that you should change the browser to your prefered browser...
You're right. In the beginnig I had changed browser to dolphin, but I forgot to change it again after using your fusemounter version. Now it is working OK.

Related to the remaining problem, I think I have some clue to solve it. Iso file was in a folder that that had a long name, with spaces in title. After copying it to home folder, or a new subfolder called iso (short title, no spaces), it mounts and unmounts well from desktop icon. So I really believe it's a problem with folder/subfolders name. But I don't know how it can be solved. By now, I'll put my isos in home folder or short-named folders.

---

### Post by ctcabm on 2008-06-21
I get a error message after about 1 minute when  am browsing through the folders in my iso file

here is the error 

Sorry, couldn't display all the contents of "********.ISO": Transport endpoint is not connected

Does anybody know what this means?

Thanks in advance

---

### Post by andrea.dolcini on 2008-07-27
I've tryed on Ubuntu 8.04 and a got this error tyng to mount :

fgn is not mounted

tying to mount manually with fuseiso works great...

but i can' get this scrtip works...

what is fng ?

And how to mount it?


Thanks

Andrea

---

### Post by RandyRandola on 2008-10-25
My eyes are square and I am frustrated.

Downloaded fuseiso-20070708 and extracted to a subdir from the desktop.
Went to that directory and tried the command 

sudo apt-get install fuseiso nautilus-actions zenity

Error message is: 

E: Couldn't find package fuseiso

And I have to agree, there is no file in the directory called that.

aclocal.m4    config.log    depcomp       linux        mkinstalldirs  zAppRun
AUTHORS       config.sub    fuseiso.spec  ltmain.sh    NEWS
ChangeLog     configure     INSTALL       Makefile.am  README
config.guess  configure.in  install-sh    Makefile.in  src
config.h.in   COPYING       libtool       missing      TODO

These are the files in that directory.

I am at a loss (typical noob) and would like assistance please.

Thanks!

---

### Post by RobOrr on 2008-10-27
how depressing to realise that I only found this after ages of fiddling, cursing and giving up via using AcetoneISO. great tutorial, cheers :D

---

### Post by Mouth on 2008-10-28
> **Milk & Toast & Honey said:**
> While there are many tutorials regarding ISO mounting, I insist posting this howto script, because I believe this script provides more convenient way to mounting/unmounting ISO files.


**[SIZE=4]_Introduction_[/SIZE]**

This script will automatically creates shortcut (of the mounted ISO) to your desktop, so you can easily open and unmount the images later, by right clicking the shortcut itself. Yes, you CAN unmount the (mounted) ISO by right-clicking the desktop shortcut -- without having to browse to the origin folder and unmount from there (but you can do that way too, if you insist :) ).
This script will automatically remove the desktop shortcut when you've unmounted the images.
So you know which ISO's are mounted by looking your desktop.

This script use the fuseiso as a backend.

Thanks! Worked perfectly for me on Intrepid RC (x86_64) with the fusemounter-hardy.tar.gz

---

### Post by Paresh on 2008-10-31
Thank you for this.  It works fine on my laptop with Intrepid.

I just made some simple changes to the script to get rid of the confirmation dialogs when mounting & unmounting.

One nice feature would be for the mounted iso to appear in the places list.  can this be done?

---

### Post by jARLAXL on 2008-11-02
Thanks a lot indeed!
and also for hinting some nice themes!

---

### Post by Barky on 2008-11-05
I r confused

does the image get mounted on a virtual drive? Can it be explored like a virtual drive? My only experience with iso mounting is daemon tools for windows, and that was the way it worked.

---

### Post by Fuzzy_Logic on 2008-11-12
I'm having the same problem Attentah had, no desktop shortcut to the mounted image.

> **Milk & Toast & Honey said:**
> Have you set the nautilus to show the desktop (in gconf-editor) ?
Usually the default Ubuntu comes with this value set to checked, but checked it for sure tho.
Open gconf-editor and navigate to:
```

apps -> nautilus -> preferences -> show_desktop = checked (true)

```
make sure that show_desktop is checked.


I did this, and the box was already checked, so that's not the problem, at least not for me.

Other than that tiny bug, I really love the script. :) It makes mounting a lot easier and more convenient. Such a script should have been added to Ubuntu by default long ago.

Btw, do you know if there are similar scripts for mounting other image file formats?

---

### Post by maduranga on 2008-11-29
great tutorial!! worked for me!

---

### Post by sad_iq on 2008-12-31
Great job on this one:) Works nice on intrepid for me.
 It has one small glitch in it thou...it doesn't work on .ISO files(capital ISO) because nautilus doesn't add the mount/unmount options in the menu, so I had to rename my disk.ISO to disk.iso

---

### Post by era506 on 2009-02-21
Works great on Debian Squeeze (new Testing since Lenny became Stable) using fusemounter-hardy version.

---

### Post by cheesepenguins on 2009-05-25
Works on Jaunty 9.04, used the Hardy script.

Thanks :)

---

### Post by #!/bin/bash on 2009-06-17
Working on Kubuntu 9.04 with KDE4.

I edited post no. [14](http://ubuntuforums.org/showpost.php?p=4415216&postcount=14) and added steps needed to make this work.  

One question still, I cant seem to change the icon of the desktop file?

---

### Post by arizonagroovejet on 2009-07-14
Nice script, saved me the effort of writing one myself. I'm using the hardy script on SUSE Linux Enterprise Desktop 11.

Couple of comments:

- Is there a specific reason why you use:
```
whoami=`whoami`
```
to get the username rather then just using the environment variable $USER?

- I've changed 
```
title="Fuse Mounter"
```
to
```
title="Fuse ISO Mounter"
```
since 'Fuse Mounter' is too vague for my liking. The script is specifically for use with fuseiso, not Fuse in general as a title of 'Fuse Mounter' implies.

---

### Post by Grps on 2009-09-09
Hello. I've got a problem with the sessions configuration screenie. I can't see it. Not in the original post and not by the link posted by rikkado, so basically i haven't installed this yet. If you could repost the picture or otherwise show me what to do in sessions config would be a great help.

Thank you in advance and great job with the scrips.


(just as a side note: I've had linux/Ubuntu for less than 2 months now so be gentle)

---

### Post by gummih on 2009-10-13
Hi, I followed these steps on Linux Mint 7
 and now nautilus wont work - I geta a segmentation fault.
any ideas how I might fix it?

---

### Post by Milk &amp; Toast &amp; Honey on 2009-11-20
Hi all, at first, apologize me for leaving this thread for such a long time. It's been a long time since the last time I visited this forum.

> **#!/bin/bash said:**
> Working on Kubuntu 9.04 with KDE4.

I edited post no. [14]("http://ubuntuforums.org/showpost.php?p=4415216&postcount=14") and added steps needed to make this work.  

One question still, I cant seem to change the icon of the desktop file?
You can change the value "Icon" in the "tpl" file. Use the terminal to browse the folder and change the file, since the "tpl" file won't shown as "tpl" in nautilus.


> **arizonagroovejet said:**
> Nice script, saved me the effort of writing one myself. I'm using the hardy script on SUSE Linux Enterprise Desktop 11.

Thanks, I'll update the Compatible System in the first post.

> **arizonagroovejet said:**
> 
Couple of comments:

- Is there a specific reason why you use:
```
whoami=`whoami`
```to get the username rather then just using the environment variable $USER?

Simply because I'm a noob in the shell ;p

> **arizonagroovejet said:**
> 
- I've changed 
```
title="Fuse Mounter"
```to
```
title="Fuse ISO Mounter"
```since 'Fuse Mounter' is too vague for my liking. The script is specifically for use with fuseiso, not Fuse in general as a title of 'Fuse Mounter' implies.
I didn't think for that when I wrote the script, should gave a clearer title next time, thanks for the input.

> **Grps said:**
> Hello. I've got a problem with the sessions configuration screenie. I can't see it. Not in the original post and not by the link posted by rikkado, so basically i haven't installed this yet. If you could repost the picture or otherwise show me what to do in sessions config would be a great help.

Thank you in advance and great job with the scrips.


(just as a side note: I've had linux/Ubuntu for less than 2 months now so be gentle)
Hi, I've reuploaded the 5.1's picture.

> **gummih said:**
> Hi, I followed these steps on Linux Mint 7
 and now nautilus wont work - I geta a segmentation fault.
any ideas how I might fix it?
You can proceed to the "Uninstallation" steps to undo the steps you've done.

---

### Post by era506 on 2010-05-02
Well this is a bit old but still works with my 64bit Lucid Lynx install xD thanks!

---

### Post by Sylntnyt on 2010-07-04
I tried both scripts with Karmic and followed all suggestions minus KDE ones and I still get nothing when I try to mount the ISO, nothing appears in the /tmp/fusemounter-********* folder either, any suggestions or fixes?

---

