---
title: "Update Manager Error"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-11-23
Hey guys, when I open the update manager, it finds about 20 new updates as per normal, and I click "Install Update Packs"

I then get an error, "You need to install an untrusted package. This action requires you install the package from a non-certified source"

Under the details, it says
"bamfdaemon libbamf0 libbamf3-0 light-themes make"

Why is this happening, and what to do?

Thanks!

---

### Post by Joentokyo on 2012-11-23
Don't know if it will work in this case, but the way I solved the problem when I got a similar or maybe the same message was that I opened Synaptic Package Manager. Then clicked on Edit from the toolbar menu and selected Fix Broken Packages, then Mark All Upgrades, then apply.

The system was upgraded.

---

### Post by linuxn00bface on 2012-11-23
> **Joentokyo said:**
> Don't know if it will work in this case, but the way I solved the problem when I got a similar or maybe the same message was that I opened Synaptic Package Manager. Then clicked on Edit from the toolbar menu and selected Fix Broken Packages, then Mark All Upgrades, then apply.

The system was upgraded.

Thanks for the suggestion. No dice, unfortunately... actually Synaptic just quits when I try and do it

Any other suggestions, please?

---

### Post by NikTh on 2012-11-23
Hi , 
please close ALL programs and open a terminal only (CTRL+ALT+T) and fire up these commands 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```If occurs any error , give the results back here
Click on **"New Reply"** and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by stinkeye on 2012-11-23
Where does update manager tell you your updates are coming from?

---

### Post by linuxn00bface on 2012-11-25
> **NikTh said:**
> Hi , 
please close ALL programs and open a terminal only (CTRL+ALT+T) and fire up these commands 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```If occurs any error , give the results back here
Click on **"New Reply"** and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

Thanks man, when I did that (sudo apt-get update) it got stuck here:
"&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/main amd64 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/restricted amd64 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/universe amd64 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/multiverse amd64 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/main TranslationIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/restricted TranslationIndex
&#30053;&#36942; [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) precise-backports/universe TranslationIndex
57%
"

And it just stayed at 57%... with the second command:
[del]@[del]-[del]:~$ sudo apt-get dist-upgrade
[sudo] password for [del]: 
&#27491;&#22312;&#35712;&#21462;&#22871;&#20214;&#28165;&#21934;... &#23436;&#25104;
&#27491;&#22312;&#37325;&#24314;&#30456;&#20381;&#38364;&#20418;          
&#27491;&#22312;&#35712;&#21462;&#29376;&#24907;&#36039;&#26009;... &#23436;&#25104;
&#31820;&#20633;&#21319;&#32026;&#20013;... &#23436;&#25104;
&#19979;&#21015;&#22871;&#20214;&#23559;&#26371;&#34987;&#21319;&#32026;&#65306;
  bamfdaemon firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en firefox-locale-zh-hans firefox-locale-zh-hant libbamf0
  libbamf3-0 light-themes make python-keyring skype skype-bin:i386 thunderbird
  thunderbird-globalmenu thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us thunderbird-locale-zh-cn thunderbird-locale-zh-hans
  thunderbird-locale-zh-hant thunderbird-locale-zh-tw xul-ext-ubufox
&#21319;&#32026; 24 &#20491;&#65292;&#26032;&#23433;&#35037; 0 &#20491;&#65292;&#31227;&#38500; 0 &#20491;&#65292;&#26377; 0 &#20491;&#26410;&#34987;&#21319;&#32026;&#12290;
&#38656;&#35201;&#19979;&#36617; 79.0 MB/79.1 MB &#30340;&#22871;&#20214;&#27284;&#12290;
&#27492;&#25805;&#20316;&#23436;&#25104;&#20043;&#24460;&#65292;&#26371;&#22810;&#20308;&#29992; 6,076 kB &#30340;&#30913;&#30879;&#31354;&#38291;&#12290;
&#26159;&#21542;&#32380;&#32396;&#36914;&#34892; [Y/n]&#65311;y
&#12304;&#35686;&#21578;&#12305;&#65306;&#28961;&#27861;&#39511;&#35657;&#19979;&#21015;&#22871;&#20214;&#65281;
  libbamf3-0 libbamf0 bamfdaemon light-themes make
&#26159;&#21542;&#19981;&#32147;&#39511;&#35657;&#23601;&#23433;&#35037;&#36889;&#20123;&#22871;&#20214;&#65311;[y/N]

The relevant part, &#12304;&#35686;&#21578;&#12305;&#65306;&#28961;&#27861;&#39511;&#35657;&#19979;&#21015;&#22871;&#20214;&#65281;,  says: "Warning, can't verify the kit below."

Then the last line is would you like to install the kit without verifying it.

Should I hit y?

The better question is, wtf is   libbamf3-0 libbamf0 bamfdaemon light-themes make , do I need it, and why is it unverified?

Cheers!

---

### Post by NikTh on 2012-11-26
> **linuxn00bface said:**
> 
Then the last line is would you like to install the kit without verifying it.

Should I hit y? 
Well, as those packages are included at Official repos of Ubuntu , I think y(es) will not harm your system. I don't know if you added any external PPA , where these packages included. 
Give the results of this command so we can see what you've added 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```> **linuxn00bface said:**
> The better question is, wtf is   libbamf3-0 libbamf0 bamfdaemon light-themes make , do I need it,
Probably yes , they are not essential packages , but optional . But these packages used by libraries and have a relation with themes.
 
> **linuxn00bface said:**
> and why is it unverified?
Maybe you had a long time to update your system ? Sometimes this can happen when for a long time not update your system. 
Try to re-import (refresh) the gpg-keys with bellow command and then run again the update commands
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --refresh-keys
``````
sudo apt-get update ; sudo apt-get dist-upgrade
```[CENTER]_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")[/CENTER]
 Thanks

---

### Post by linuxn00bface on 2012-11-28
> **NikTh said:**
> 
Give the results of this command so we can see what you've added 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```Probably yes , they are not essential packages , but optional . But these packages used by libraries and have a relation with themes.
```

:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     2    
     3    # newer versions of the distribution.
     4    deb http://sg.archive.ubuntu.com/ubuntu/ precise main restricted
     5    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb http://sg.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    10    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb http://sg.archive.ubuntu.com/ubuntu/ precise universe
    16    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise universe
    17    deb http://sg.archive.ubuntu.com/ubuntu/ precise-updates universe
    18    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb http://sg.archive.ubuntu.com/ubuntu/ precise multiverse
    26    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb http://sg.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    28    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    deb http://sg.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    36    deb-src http://sg.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    
    38    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    39    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    40    deb http://security.ubuntu.com/ubuntu precise-security universe
    41    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    42    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    43    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    44    
    45    ## Uncomment the following two lines to add software from Canonical's
    46    ## 'partner' repository.
    47    ## This software is not part of Ubuntu, but is offered by Canonical and the
    48    ## respective vendors as a service to Ubuntu users.
    49    # deb http://archive.canonical.com/ubuntu precise partner
    50    # deb-src http://archive.canonical.com/ubuntu precise partner
    51    
    52    ## Uncomment the following two lines to add software from Ubuntu's
    53    ## 'extras' repository.
    54    ## This software is not part of Ubuntu, but is offered by third-party
    55    ## developers who want to ship their latest software.
    56    # deb http://extras.ubuntu.com/ubuntu precise main
    57    # deb-src http://extras.ubuntu.com/ubuntu precise main

/etc/apt/sources.list.d/tikhonov-misc-precise.list

     1    deb http://ppa.launchpad.net/tikhonov/misc/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/tikhonov/misc/ubuntu precise main

/etc/apt/sources.list.d/webupd8team-java-precise.list

     1    deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/talkplugin/deb/ stable main

/etc/apt/sources.list.d/precise-partner.list

     1    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center

/etc/apt/sources.list.d/dropbox.list

     1    deb http://linux.dropbox.com/ubuntu precise main

```Any idea what the culprit might be? And is it important/should I delete it?

UPDATE, 
```

&#26159;&#21542;&#32380;&#32396;&#36914;&#34892; [Y/n]&#65311;y
&#12304;&#35686;&#21578;&#12305;&#65306;&#28961;&#27861;&#39511;&#35657;&#19979;&#21015;&#22871;&#20214;&#65281;
  libbamf3-0 libbamf0 bamfdaemon light-themes make
&#26159;&#21542;&#19981;&#32147;&#39511;&#35657;&#23601;&#23433;&#35037;&#36889;&#20123;&#22871;&#20214;&#65311;[y/N]y
&#37679;&#35492; http://sg.archive.ubuntu.com/ubuntu/ precise-updates/main libbamf3-0 amd64 0.2.118-0ubuntu0.3
  &#36899;&#32218;&#22833;&#25943;
&#37679;&#35492; http://sg.archive.ubuntu.com/ubuntu/ precise-updates/main libbamf0 amd64 0.2.118-0ubuntu0.3
  &#36899;&#32218;&#22833;&#25943;
&#37679;&#35492; http://sg.archive.ubuntu.com/ubuntu/ precise-updates/main bamfdaemon amd64 0.2.118-0ubuntu0.3
  &#36899;&#32218;&#22833;&#25943;
&#37679;&#35492; http://sg.archive.ubuntu.com/ubuntu/ precise-updates/main light-themes all 0.1.9.1-0ubuntu1.2
  &#36899;&#32218;&#22833;&#25943;
&#37679;&#35492; http://sg.archive.ubuntu.com/ubuntu/ precise-updates/main make amd64 3.81-8.1ubuntu1.1
  &#36899;&#32218;&#22833;&#25943;
&#28961;&#27861;&#21462;&#24471; http://sg.archive.ubuntu.com/ubuntu/pool/main/b/bamf/libbamf3-0_0.2.118-0ubuntu0.3_amd64.deb&#65292;&#36899;&#32218;&#22833;&#25943;
&#28961;&#27861;&#21462;&#24471; http://sg.archive.ubuntu.com/ubuntu/pool/main/b/bamf/libbamf0_0.2.118-0ubuntu0.3_amd64.deb&#65292;&#36899;&#32218;&#22833;&#25943;
&#28961;&#27861;&#21462;&#24471; http://sg.archive.ubuntu.com/ubuntu/pool/main/b/bamf/bamfdaemon_0.2.118-0ubuntu0.3_amd64.deb&#65292;&#36899;&#32218;&#22833;&#25943;
&#28961;&#27861;&#21462;&#24471; http://sg.archive.ubuntu.com/ubuntu/pool/main/l/light-themes/light-themes_0.1.9.1-0ubuntu1.2_all.deb&#65292;&#36899;&#32218;&#22833;&#25943;
&#28961;&#27861;&#21462;&#24471; http://sg.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_3.81-8.1ubuntu1.1_amd64.deb&#65292;&#36899;&#32218;&#22833;&#25943;
E: &#26377;&#37096;&#20221;&#22871;&#20214;&#27284;&#28961;&#27861;&#21462;&#24471;&#65292;&#35430;&#33879;&#22519;&#34892; apt-get update &#25110;&#32773;&#35430;&#33879;&#21152;&#19978; --fix-missing &#36984;&#38917;&#65311;

```

Basically what that's saying is
&#37679;&#35492; error 
&#36899;&#32218;&#22833;&#25943; connection failed
&#28961;&#27861;&#21462;&#24471; not available (left of websites)

Then at the end, it's saying there's part of the package file that isn't available, try to run apt-get update, or try to add --fix-missing option? 

It asks a question but I don't know what the answer is, nor how to answer it! ha..

Help, please!

---

### Post by monkeybrain2012 on 2012-11-28
Just means you have added a ppa and the gpg key is missing. No worries, just say yes. The easiest way to fix gpg errors is to install and run the script lauchpad-getkeys

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Or you can reimport the key with NikTh's commmand, though I can never remember it.

---

### Post by NikTh on 2012-11-28
Hi,
And what about this command ?

> **NikTh said:**
> 
Try to re-import (refresh) the gpg-keys with bellow command and then run again the update commands
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --refresh-keys
```
have you ran it ? Where are the results ? 

Thanks

---

### Post by linuxn00bface on 2012-11-28
> **NikTh said:**
> Hi,
And what about this command ?


have you ran it ? Where are the results ? 

Thanks

```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Ao2NJoBTs6 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --refresh-keys
gpg: &#26356;&#26032; 9 &#20221;&#37329;&#38000;&#20013; (&#24478; hkp://keyserver.ubuntu.com )
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; 437D05B5 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; FBB75451 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; 3E5C1192 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; 7FAC5991 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; EEA14886 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; B44C294F &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; 5044912E &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; C0B21F32 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; EFE21092 &#33258; hkp &#20282;&#26381;&#22120; keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out

```

gpg: &#26356;&#26032; 9 &#20221;&#37329;&#38000;&#20013; -- updating 9 keys
gpg: &#27491;&#22312;&#35531;&#27714;&#37329;&#38000; -- looking for key ______ from hkp server keyserver.ubuntu.com

---

### Post by NikTh on 2012-11-29
Hi , 
I don't know why , but this server seems not work. => ```
[http://**sg**]("http://<b>sg</b>").archive.ubuntu.com/ubuntu/
```Try to change server. Go to "update-manager" > settings > and change the **Download From:** to the **main** server. Then close update manager and open a terminal 

Run again this command
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --refresh-keys
```and then ```
sudo apt-get update
```and give full results here. 

Thank you.

---

### Post by linuxn00bface on 2012-11-30
> **NikTh said:**
> Hi , 
I don't know why , but this server seems not work. => ```
[http://**sg**]("http://<b>sg</b>").archive.ubuntu.com/ubuntu/
```Try to change server. Go to "update-manager" > settings > and change the **Download From:** to the **main** server. Then close update manager and open a terminal 

Run again this command
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --refresh-keys
```and then ```
sudo apt-get update
```and give full results here. 

Thank you.
It worked!

Damn the community here is great, thanks a ton Nik

---

