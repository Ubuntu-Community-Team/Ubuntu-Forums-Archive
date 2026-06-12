---
title: "App not opening to desktop"
date: 2017-07-26
forum: New to Ubuntu
---

### Post by rudybaby on 2017-07-26
I was trying to open Kodi and the icon shows in the left toolbar, but Kodi doesn't open to the desktop.
Tried several time closing and opening it. Tried restarting. No help.:mad:

---

### Post by BenginM on 2017-07-26
what happens if you open it from terminal.. it might help fix it after you re-install it ..!

---

### Post by Bucky Ball on 2017-07-26
Hard to give a lot of help without some more detail. Which release and flavour of Ubuntu are you using and which version of Kodi have you installed? Did you install Kodi from the official Ubuntu repositories ('Software' or terminal) or from a third-party site?

Suggest you try these three commands in a terminal and see if it makes any difference. This will NOT upgrade your release to a newer one, just the software you already have installed. ;)

```
sudo apt update
sudo apt full-upgrade
sudo apt install --reinstall kodi
```

Reboot and see what happens. Having said that, it is important that you let us know the release/flavour of Ubuntu you are using and the Kodi version.

---

### Post by rudybaby on 2017-07-27
Bucky Ball
I tried what you suggested. Then I tried running Kodi from terminal. Neither worked. The icon shows on the left toolbar with little arrows on both sides of the icon. I can click on the icon, nothing.  

Maybe the Kodi window is open but I can't see it on the desktop?

---

### Post by QIII on 2017-07-27
Hello!

When you attempt to run Kodi from the terminal, are any messages displayed?  If so, can you post them?

---

### Post by rudybaby on 2017-07-27
No message, just the icon appears on the left toolbar. I have now uninstalled kodi, kodi-bin and kodi-data
I am going to reinstall it with these commands: 
[COLOR=#C20CB9]**sudo**[/COLOR][COLOR=#C20CB9]**apt-get install**[/COLOR][COLOR=#000000] software-properties-common
[/COLOR][COLOR=#C20CB9]**sudo**[/COLOR] add-apt-repository ppa:team-xbmc**/**ppa
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get update**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] kodi

Are these the correct commands?

---

### Post by Frogs Hair on 2017-07-27
When I experimented with kodi it had it's own session selected during login from the greeter , that could have changed though.

---

### Post by rudybaby on 2017-07-27
Frogs Hair, could you translate that to newbie please.

---

### Post by rudybaby on 2017-07-27
It's weird because I can open Firefox from the taskbar, but not Kodi. What do those arrows by the icon on the taskbar?

---

### Post by #&amp;thj^% on 2017-07-27
One important question...Do you have Dual Monitors?

---

### Post by rudybaby on 2017-07-27
No I am using this stand alone computer with a Vizio TV. No additional monitors.

---

### Post by Frogs Hair on 2017-07-27
> **rudybaby said:**
> Frogs Hair, could you translate that to newbie please.

If installed as a session it would be selected during login.

---

### Post by #&amp;thj^% on 2017-07-27
> **rudybaby said:**
> No I am using this stand alone computer with a Vizio TV. No additional monitors.

Ok I'm assuming it is installed now "Kodi".
From the terminal run this one line at a time hitting enter after each:
```
cd ~/.kodi/userdata
ls 
```
Copy that from the terminal and paste back here please. Using Code tags.

---

### Post by rudybaby on 2017-07-27
rm@rm-Rugged-Mini-Vi:~$ cd ~/.kodi/userdata
[email]rm@rm-Rugged-Mini-Vi:~/.kodi[/email]/userdata$ ls
addon_data  guisettings.xml  library          playlists     RssFeeds.xml
Database    keymaps          peripheral_data  profiles.xml  Thumbnails
[email]rm@rm-Rugged-Mini-Vi:~/.kodi[/email]/userdata$

---

### Post by #&amp;thj^% on 2017-07-27
This next request is really going to need you use the Code Tags for the output so please read in my Signature How to use Code Tags.
Then I will need to see the output from running this in that same terminal you are now in.
```
gedit guisettings.xml
```
Paste that whole file back here please.

---

### Post by rudybaby on 2017-07-27
```
[COLOR=#000000][FONT=&amp]gedit guisettings.xml[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

is it like this exactly in terminal?

can i attach a .xml file to a post?[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-07-27
Yes exactly like that but you would still need to be in the same Directory you was in.
What Desktop are you using?
Lets cut to chase here, Post back the return from the terminal:
```
 echo $XDG_CURRENT_DESKTOP
```

---

### Post by rudybaby on 2017-07-27
Unity:Unity7

---

### Post by #&amp;thj^% on 2017-07-27
Ok Great.
Now run this one line at time:
```
cd ~/.kodi/userdata
gedit guisettings.xml
```
Paste that info back here please.

---

### Post by rudybaby on 2017-07-27
it's too long and security token is missing

---

### Post by #&amp;thj^% on 2017-07-27
Thats funny heres mine.
Notice I wrap the text in Code tags
```
<settings>
    <accessibility>
        <audiohearing default="true">false</audiohearing>
        <audiovisual default="true">false</audiovisual>
        <subhearing default="true">false</subhearing>
    </accessibility>
    <addons>
        <unknownsources default="true">false</unknownsources>
    </addons>
    <audiocds>
        <autoaction default="true">0</autoaction>
        <ejectonrip default="true">true</ejectonrip>
        <encoder default="true">audioencoder.xbmc.builtin.wav</encoder>
        <recordingpath default="true"></recordingpath>
        <trackpathformat default="true">%A/%A - %B/[%N. ][%A - ]%T</trackpathformat>
        <usecddb default="true">true</usecddb>
    </audiocds>
    <audiooutput>
        <ac3passthrough default="true">true</ac3passthrough>
        <ac3transcode default="true">false</ac3transcode>
        <atempothreshold default="true">2</atempothreshold>
        <audiodevice>ALSA:hdmi:CARD=NVidia,DEV=1</audiodevice>
        <channels default="true">1</channels>
        <config default="true">2</config>
        <dspaddonsenabled default="true">false</dspaddonsenabled>
        <dtshdpassthrough default="true">false</dtshdpassthrough>
        <dtspassthrough default="true">false</dtspassthrough>
        <eac3passthrough default="true">false</eac3passthrough>
        <guisoundmode default="true">1</guisoundmode>
        <maintainoriginalvolume default="true">true</maintainoriginalvolume>
        <passthrough default="true">false</passthrough>
        <passthroughdevice default="true">ALSA:hdmi:CARD=PCH,DEV=0</passthroughdevice>
        <processquality default="true">30</processquality>
        <samplerate default="true">48000</samplerate>
        <stereoupmix default="true">false</stereoupmix>
        <streamnoise default="true">true</streamnoise>
        <streamsilence default="true">1</streamsilence>
        <truehdpassthrough default="true">false</truehdpassthrough>
        <volumesteps default="true">90</volumesteps>
    </audiooutput>
    <bluray>
        <playerregion default="true">1</playerregion>
    </bluray>
    <cache>
        <harddisk default="true">256</harddisk>
    </cache>
    <cacheaudio>
        <dvdrom default="true">256</dvdrom>
        <internet default="true">256</internet>
        <lan default="true">256</lan>
    </cacheaudio>
    <cachedvd>
        <dvdrom default="true">2048</dvdrom>
        <lan default="true">2048</lan>
    </cachedvd>
    <cacheunknown>
        <internet default="true">4096</internet>
    </cacheunknown>
    <cachevideo>
        <dvdrom default="true">2048</dvdrom>
        <internet default="true">4096</internet>
        <lan default="true">2048</lan>
    </cachevideo>
    <debug>
        <extralogging default="true">true</extralogging>
        <screenshotpath default="true"></screenshotpath>
        <setextraloglevel default="true">32768</setextraloglevel>
        <showloginfo default="true">false</showloginfo>
    </debug>
    <disc>
        <playback default="true">0</playback>
    </disc>
    <dvds>
        <automenu default="true">false</automenu>
        <autorun default="true">false</autorun>
        <playerregion default="true">0</playerregion>
    </dvds>
    <epg>
        <daystodisplay default="true">3</daystodisplay>
        <epgupdate default="true">120</epgupdate>
        <hidenoinfoavailable default="true">true</hidenoinfoavailable>
        <ignoredbforclient default="true">false</ignoredbforclient>
        <preventupdateswhileplayingtv default="true">false</preventupdateswhileplayingtv>
        <selectaction default="true">2</selectaction>
    </epg>
    <eventlog>
        <enabled default="true">true</enabled>
        <enablednotifications default="true">false</enablednotifications>
    </eventlog>
    <filelists>
        <allowfiledeletion default="true">false</allowfiledeletion>
        <ignorethewhensorting default="true">true</ignorethewhensorting>
        <showaddsourcebuttons default="true">true</showaddsourcebuttons>
        <showextensions default="true">true</showextensions>
        <showhidden default="true">false</showhidden>
        <showparentdiritems default="true">true</showparentdiritems>
    </filelists>
    <general>
        <addonbrokenfilter default="true">true</addonbrokenfilter>
        <addonforeignfilter default="true">false</addonforeignfilter>
        <addonnotifications default="true">false</addonnotifications>
        <addonupdates default="true">0</addonupdates>
        <settinglevel>3</settinglevel>
        <eventlog>
            <level>0</level>
            <showhigherlevels>true</showhigherlevels>
        </eventlog>
        <systemtotaluptime>6468</systemtotaluptime>
    </general>
    <input>
        <asknewcontrollers default="true">true</asknewcontrollers>
        <controllerpoweroff default="true">false</controllerpoweroff>
        <enablemouse default="true">true</enablemouse>
        <rumblenotify default="true">false</rumblenotify>
    </input>
    <locale>
        <audiolanguage default="true">original</audiolanguage>
        <charset default="true">DEFAULT</charset>
        <country default="true">USA (12h)</country>
        <keyboardlayouts default="true">English QWERTY</keyboardlayouts>
        <language default="true">resource.language.en_gb</language>
        <longdateformat default="true">regional</longdateformat>
        <shortdateformat default="true">regional</shortdateformat>
        <speedunit default="true">regional</speedunit>
        <subtitlelanguage default="true">original</subtitlelanguage>
        <temperatureunit default="true">regional</temperatureunit>
        <timeformat default="true">regional</timeformat>
        <timezone default="true">America/Denver</timezone>
        <timezonecountry default="true">United States</timezonecountry>
        <use24hourclock default="true">regional</use24hourclock>
    </locale>
    <lookandfeel>
        <enablerssfeeds default="true">false</enablerssfeeds>
        <font default="true">Default</font>
        <rssedit default="true"></rssedit>
        <skin default="true">skin.estuary</skin>
        <skincolors default="true">SKINDEFAULT</skincolors>
        <skintheme default="true">SKINDEFAULT</skintheme>
        <skinzoom default="true">0</skinzoom>
        <soundskin default="true">resource.uisounds.kodi</soundskin>
        <startupwindow default="true">10000</startupwindow>
        <stereostrength default="true">5</stereostrength>
    </lookandfeel>
    <masterlock>
        <maxretries default="true">3</maxretries>
        <startuplock default="true">false</startuplock>
    </masterlock>
    <musicfiles>
        <findremotethumbs default="true">true</findremotethumbs>
        <librarytrackformat default="true"></librarytrackformat>
        <nowplayingtrackformat default="true"></nowplayingtrackformat>
        <trackformat default="true">[%N. ]%A - %T</trackformat>
        <usetags default="true">true</usetags>
    </musicfiles>
    <musiclibrary>
        <albumsscraper default="true">metadata.album.universal</albumsscraper>
        <artistsscraper default="true">metadata.artists.universal</artistsscraper>
        <backgroundupdate default="true">false</backgroundupdate>
        <downloadinfo default="true">false</downloadinfo>
        <overridetags default="true">false</overridetags>
        <showallitems default="true">true</showallitems>
        <showcompilationartists default="true">true</showcompilationartists>
        <updateonstartup default="true">false</updateonstartup>
    </musiclibrary>
    <musicplayer>
        <autoplaynextitem default="true">true</autoplaynextitem>
        <crossfade default="true">0</crossfade>
        <crossfadealbumtracks default="true">true</crossfadealbumtracks>
        <queuebydefault default="true">false</queuebydefault>
        <replaygainnogainpreamp default="true">89</replaygainnogainpreamp>
        <replaygainpreamp default="true">89</replaygainpreamp>
        <replaygaintype default="true">1</replaygaintype>
        <seekdelay default="true">750</seekdelay>
        <seeksteps default="true">-60,-30,-10,10,30,60</seeksteps>
        <visualisation default="true">visualization.spectrum</visualisation>
    </musicplayer>
    <mymusic>
        <defaultlibview default="true"></defaultlibview>
        <songthumbinvis default="true">false</songthumbinvis>
        <playlist>
            <repeat>false</repeat>
            <shuffle>false</shuffle>
        </playlist>
        <needsupdate>0</needsupdate>
    </mymusic>
    <myvideos>
        <extractchapterthumbs default="true">true</extractchapterthumbs>
        <extractflags default="true">true</extractflags>
        <extractthumb default="true">true</extractthumb>
        <flatten default="true">false</flatten>
        <replacelabels default="true">true</replacelabels>
        <selectaction default="true">1</selectaction>
        <stackvideos default="true">false</stackvideos>
        <watchmodemovies>0</watchmodemovies>
        <watchmodetvshows>0</watchmodetvshows>
        <watchmodemusicvideos>0</watchmodemusicvideos>
        <playlist>
            <repeat>false</repeat>
            <shuffle>false</shuffle>
        </playlist>
        <needsupdate>0</needsupdate>
    </myvideos>
    <network>
        <bandwidth default="true">0</bandwidth>
        <httpproxypassword default="true"></httpproxypassword>
        <httpproxyport default="true">8080</httpproxyport>
        <httpproxyserver default="true"></httpproxyserver>
        <httpproxytype default="true">0</httpproxytype>
        <httpproxyusername default="true"></httpproxyusername>
        <usehttpproxy default="true">false</usehttpproxy>
    </network>
    <pictures>
        <displayresolution>16</displayresolution>
        <generatethumbs default="true">true</generatethumbs>
        <showvideos default="true">true</showvideos>
        <usetags default="true">true</usetags>
    </pictures>
    <powermanagement>
        <displaysoff default="true">0</displaysoff>
        <shutdownstate default="true">0</shutdownstate>
        <shutdowntime default="true">0</shutdowntime>
        <wakeonaccess default="true">false</wakeonaccess>
    </powermanagement>
    <pvrmanager>
        <backendchannelorder default="true">true</backendchannelorder>
        <hideconnectionlostwarning default="true">false</hideconnectionlostwarning>
        <syncchannelgroups default="true">true</syncchannelgroups>
        <usebackendchannelnumbers default="true">false</usebackendchannelnumbers>
    </pvrmanager>
    <pvrmenu>
        <closechannelosdonswitch default="true">true</closechannelosdonswitch>
        <displaychannelinfo default="true">5</displaychannelinfo>
        <iconpath default="true"></iconpath>
    </pvrmenu>
    <pvrparental>
        <duration default="true">300</duration>
        <enabled default="true">false</enabled>
        <pin default="true"></pin>
    </pvrparental>
    <pvrplayback>
        <channelentrytimeout default="true">0</channelentrytimeout>
        <confirmchannelswitch default="true">false</confirmchannelswitch>
        <enableradiords default="true">true</enableradiords>
        <fps default="true">0</fps>
        <playminimized default="true">true</playminimized>
        <scantime default="true">10</scantime>
        <signalquality default="true">true</signalquality>
        <startlast default="true">0</startlast>
        <trafficadvisory default="true">false</trafficadvisory>
        <trafficadvisoryvolume default="true">10</trafficadvisoryvolume>
    </pvrplayback>
    <pvrpowermanagement>
        <backendidletime default="true">15</backendidletime>
        <dailywakeup default="true">false</dailywakeup>
        <dailywakeuptime default="true">00:00:00</dailywakeuptime>
        <enabled default="true">false</enabled>
        <prewakeup default="true">15</prewakeup>
        <setwakeupcmd default="true"></setwakeupcmd>
    </pvrpowermanagement>
    <pvrrecord>
        <defaultlifetime default="true">99</defaultlifetime>
        <defaultpriority default="true">50</defaultpriority>
        <grouprecordings default="true">true</grouprecordings>
        <instantrecordaction default="true">0</instantrecordaction>
        <instantrecordtime default="true">120</instantrecordtime>
        <marginend default="true">0</marginend>
        <marginstart default="true">0</marginstart>
        <preventduplicateepisodes default="true">0</preventduplicateepisodes>
        <timernotifications default="true">true</timernotifications>
    </pvrrecord>
    <pvrtimers>
        <hidedisabledtimers default="true">false</hidedisabledtimers>
    </pvrtimers>
    <scrapers>
        <moviesdefault default="true">metadata.themoviedb.org</moviesdefault>
        <musicvideosdefault default="true">metadata.local</musicvideosdefault>
        <tvshowsdefault default="true">metadata.tvdb.com</tvshowsdefault>
    </scrapers>
    <screensaver>
        <mode default="true">screensaver.xbmc.builtin.dim</mode>
        <time default="true">3</time>
        <usedimonpause default="true">true</usedimonpause>
        <usemusicvisinstead default="true">true</usemusicvisinstead>
    </screensaver>
    <services>
        <airplay default="true">false</airplay>
        <airplaypassword default="true"></airplaypassword>
        <airplayvideosupport default="true">true</airplayvideosupport>
        <airplayvolumecontrol default="true">true</airplayvolumecontrol>
        <devicename default="true">Kodi</devicename>
        <esallinterfaces default="true">false</esallinterfaces>
        <escontinuousdelay default="true">25</escontinuousdelay>
        <esenabled default="true">true</esenabled>
        <esinitialdelay default="true">750</esinitialdelay>
        <esmaxclients default="true">20</esmaxclients>
        <esport default="true">9777</esport>
        <esportrange default="true">10</esportrange>
        <upnpannounce default="true">true</upnpannounce>
        <upnpcontroller default="true">false</upnpcontroller>
        <upnplookforexternalsubtitles default="true">false</upnplookforexternalsubtitles>
        <upnprenderer default="true">false</upnprenderer>
        <upnpserver default="true">false</upnpserver>
        <useairplaypassword default="true">false</useairplaypassword>
        <webserver default="true">false</webserver>
        <webserverpassword default="true"></webserverpassword>
        <webserverport default="true">8080</webserverport>
        <webserverusername default="true">kodi</webserverusername>
        <webskin default="true">webinterface.default</webskin>
        <zeroconf default="true">true</zeroconf>
    </services>
    <slideshow>
        <displayeffects default="true">true</displayeffects>
        <highqualitydownscaling default="true">false</highqualitydownscaling>
        <shuffle default="true">false</shuffle>
        <staytime default="true">5</staytime>
    </slideshow>
    <smb>
        <winsserver default="true">0.0.0.0</winsserver>
        <workgroup default="true">WORKGROUP</workgroup>
    </smb>
    <subtitles>
        <align default="true">0</align>
        <charset default="true">DEFAULT</charset>
        <color default="true">1</color>
        <custompath default="true"></custompath>
        <downloadfirst default="true">false</downloadfirst>
        <font default="true">arial.ttf</font>
        <height default="true">28</height>
        <languages default="true">English</languages>
        <movie default="true"></movie>
        <overrideassfonts default="true">false</overrideassfonts>
        <parsecaptions default="true">false</parsecaptions>
        <pauseonsearch default="true">true</pauseonsearch>
        <stereoscopicdepth default="true">0</stereoscopicdepth>
        <storagemode default="true">0</storagemode>
        <style default="true">1</style>
        <tv default="true"></tv>
    </subtitles>
    <system>
        <playlistspath>special://profile/playlists/</playlistspath>
    </system>
    <videolibrary>
        <actorthumbs default="true">true</actorthumbs>
        <backgroundupdate default="true">false</backgroundupdate>
        <flattentvshows default="true">1</flattentvshows>
        <groupmoviesets default="true">false</groupmoviesets>
        <groupsingleitemsets default="true">false</groupsingleitemsets>
        <showallitems default="true">true</showallitems>
        <showemptytvshows default="true">false</showemptytvshows>
        <showunwatchedplots default="true">true</showunwatchedplots>
        <tvshowsincludeallseasonsandspecials default="true">0</tvshowsincludeallseasonsandspecials>
        <tvshowsselectfirstunwatcheditem default="true">0</tvshowsselectfirstunwatcheditem>
        <updateonstartup default="true">false</updateonstartup>
    </videolibrary>
    <videoplayer>
        <adjustrefreshrate default="true">0</adjustrefreshrate>
        <autoplaynextitem default="true">false</autoplaynextitem>
        <errorinaspect default="true">0</errorinaspect>
        <hqscalers default="true">20</hqscalers>
        <preferdefaultflag default="true">true</preferdefaultflag>
        <prefervaapirender default="true">true</prefervaapirender>
        <quitstereomodeonstop default="true">true</quitstereomodeonstop>
        <rendermethod default="true">0</rendermethod>
        <seekdelay default="true">750</seekdelay>
        <seeksteps default="true">-600,-300,-180,-60,-30,-10,10,30,60,180,300,600</seeksteps>
        <stereoscopicplaybackmode default="true">0</stereoscopicplaybackmode>
        <stretch43 default="true">0</stretch43>
        <teletextenabled default="true">true</teletextenabled>
        <teletextscale default="true">true</teletextscale>
        <useamcodec default="true">true</useamcodec>
        <useamcodech264 default="true">0</useamcodech264>
        <useamcodecmpeg2 default="true">0</useamcodecmpeg2>
        <useamcodecmpeg4 default="true">800</useamcodecmpeg4>
        <usedisplayasclock default="true">false</usedisplayasclock>
        <usedxva2 default="true">true</usedxva2>
        <usemediacodec default="true">true</usemediacodec>
        <usemediacodecsurface default="true">true</usemediacodecsurface>
        <useomx default="true">true</useomx>
        <useomxplayer default="true">true</useomxplayer>
        <usevaapi default="true">true</usevaapi>
        <usevaapimpeg2 default="true">true</usevaapimpeg2>
        <usevaapimpeg4 default="true">true</usevaapimpeg4>
        <usevaapivc1 default="true">true</usevaapivc1>
        <usevdpau default="true">true</usevdpau>
        <usevdpaumixer default="true">true</usevdpaumixer>
        <usevdpaumpeg2 default="true">true</usevdpaumpeg2>
        <usevdpaumpeg4 default="true">false</usevdpaumpeg4>
        <usevdpauvc1 default="true">true</usevdpauvc1>
        <usevtb default="true">true</usevtb>
    </videoplayer>
    <videoscreen>
        <blankdisplays default="true">false</blankdisplays>
        <cms3dlut default="true"></cms3dlut>
        <cmsenabled default="true">false</cmsenabled>
        <cmsgamma default="true">220</cmsgamma>
        <cmsgammamode default="true">0</cmsgammamode>
        <cmslutsize default="true">6</cmslutsize>
        <cmsmode default="true">0</cmsmode>
        <cmsprimaries default="true">0</cmsprimaries>
        <cmswhitepoint default="true">0</cmswhitepoint>
        <delayrefreshchange default="true">0</delayrefreshchange>
        <displayprofile default="true"></displayprofile>
        <dither default="true">false</dither>
        <ditherdepth default="true">8</ditherdepth>
        <fakefullscreen default="true">true</fakefullscreen>
        <limitedrange default="true">false</limitedrange>
        <monitor>HDMI-0</monitor>
        <noofbuffers default="true">3</noofbuffers>
        <preferedstereoscopicmode default="true">100</preferedstereoscopicmode>
        <resolution default="true">16</resolution>
        <screen default="true">0</screen>
        <screenmode default="true">DESKTOP</screenmode>
        <stereoscopicmode default="true">0</stereoscopicmode>
    </videoscreen>
    <weather>
        <addon default="true"></addon>
        <currentlocation default="true">1</currentlocation>
    </weather>
    <window>
        <height>1056</height>
        <width>1873</width>
    </window>
    <viewstates>
        <musicfiles>
            <viewmode>720896</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </musicfiles>
        <musiclastfm>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </musiclastfm>
        <musicnavalbums>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </musicnavalbums>
        <musicnavartists>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </musicnavartists>
        <musicnavsongs>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </musicnavsongs>
        <pictures>
            <viewmode>131126</viewmode>
            <sortmethod>45</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </pictures>
        <programs>
            <viewmode>720896</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </programs>
        <videofiles>
            <viewmode>720896</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videofiles>
        <videonavactors>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavactors>
        <videonavepisodes>
            <viewmode>720896</viewmode>
            <sortmethod>23</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavepisodes>
        <videonavgenres>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavgenres>
        <videonavmusicvideos>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavmusicvideos>
        <videonavseasons>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavseasons>
        <videonavtitles>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavtitles>
        <videonavtvshows>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavtvshows>
        <videonavyears>
            <viewmode>65536</viewmode>
            <sortmethod>1</sortmethod>
            <sortorder>1</sortorder>
            <sortattributes>0</sortattributes>
        </videonavyears>
    </viewstates>
    <resolutions />
    <defaultvideosettings>
        <interlacemethod>12</interlacemethod>
        <scalingmethod>1</scalingmethod>
        <noisereduction>0.000000</noisereduction>
        <postprocess>false</postprocess>
        <sharpness>0.000000</sharpness>
        <viewmode>4</viewmode>
        <zoomamount>1.000000</zoomamount>
        <pixelratio>0.997531</pixelratio>
        <verticalshift>0.000000</verticalshift>
        <volumeamplification>18.000000</volumeamplification>
        <outputtoallspeakers>false</outputtoallspeakers>
        <showsubtitles>false</showsubtitles>
        <brightness>50.000000</brightness>
        <contrast>50.000000</contrast>
        <gamma>20.000000</gamma>
        <audiodelay>0.000000</audiodelay>
        <subtitledelay>0.000000</subtitledelay>
        <nonlinstretch>false</nonlinstretch>
        <stereomode>0</stereomode>
    </defaultvideosettings>
    <defaultaudiosettings>
        <masterstreamtype>7</masterstreamtype>
        <masterstreamtypesel>7</masterstreamtypesel>
        <masterstreambase>0</masterstreambase>
        <masterprocess_0_0>0</masterprocess_0_0>
        <masterprocess_0_1>0</masterprocess_0_1>
        <masterprocess_0_2>0</masterprocess_0_2>
        <masterprocess_0_3>0</masterprocess_0_3>
        <masterprocess_0_4>0</masterprocess_0_4>
        <masterprocess_0_5>0</masterprocess_0_5>
        <masterprocess_0_6>0</masterprocess_0_6>
        <masterprocess_0_7>0</masterprocess_0_7>
        <masterprocess_0_8>0</masterprocess_0_8>
        <masterprocess_0_9>0</masterprocess_0_9>
        <masterprocess_0_10>0</masterprocess_0_10>
        <masterprocess_1_0>0</masterprocess_1_0>
        <masterprocess_1_1>0</masterprocess_1_1>
        <masterprocess_1_2>0</masterprocess_1_2>
        <masterprocess_1_3>0</masterprocess_1_3>
        <masterprocess_1_4>0</masterprocess_1_4>
        <masterprocess_1_5>0</masterprocess_1_5>
        <masterprocess_1_6>0</masterprocess_1_6>
        <masterprocess_1_7>0</masterprocess_1_7>
        <masterprocess_1_8>0</masterprocess_1_8>
        <masterprocess_1_9>0</masterprocess_1_9>
        <masterprocess_1_10>0</masterprocess_1_10>
        <masterprocess_2_0>0</masterprocess_2_0>
        <masterprocess_2_1>0</masterprocess_2_1>
        <masterprocess_2_2>0</masterprocess_2_2>
        <masterprocess_2_3>0</masterprocess_2_3>
        <masterprocess_2_4>0</masterprocess_2_4>
        <masterprocess_2_5>0</masterprocess_2_5>
        <masterprocess_2_6>0</masterprocess_2_6>
        <masterprocess_2_7>0</masterprocess_2_7>
        <masterprocess_2_8>0</masterprocess_2_8>
        <masterprocess_2_9>0</masterprocess_2_9>
        <masterprocess_2_10>0</masterprocess_2_10>
        <masterprocess_3_0>0</masterprocess_3_0>
        <masterprocess_3_1>0</masterprocess_3_1>
        <masterprocess_3_2>0</masterprocess_3_2>
        <masterprocess_3_3>0</masterprocess_3_3>
        <masterprocess_3_4>0</masterprocess_3_4>
        <masterprocess_3_5>0</masterprocess_3_5>
        <masterprocess_3_6>0</masterprocess_3_6>
        <masterprocess_3_7>0</masterprocess_3_7>
        <masterprocess_3_8>0</masterprocess_3_8>
        <masterprocess_3_9>0</masterprocess_3_9>
        <masterprocess_3_10>0</masterprocess_3_10>
        <masterprocess_4_0>0</masterprocess_4_0>
        <masterprocess_4_1>0</masterprocess_4_1>
        <masterprocess_4_2>0</masterprocess_4_2>
        <masterprocess_4_3>0</masterprocess_4_3>
        <masterprocess_4_4>0</masterprocess_4_4>
        <masterprocess_4_5>0</masterprocess_4_5>
        <masterprocess_4_6>0</masterprocess_4_6>
        <masterprocess_4_7>0</masterprocess_4_7>
        <masterprocess_4_8>0</masterprocess_4_8>
        <masterprocess_4_9>0</masterprocess_4_9>
        <masterprocess_4_10>0</masterprocess_4_10>
        <masterprocess_5_0>0</masterprocess_5_0>
        <masterprocess_5_1>0</masterprocess_5_1>
        <masterprocess_5_2>0</masterprocess_5_2>
        <masterprocess_5_3>0</masterprocess_5_3>
        <masterprocess_5_4>0</masterprocess_5_4>
        <masterprocess_5_5>0</masterprocess_5_5>
        <masterprocess_5_6>0</masterprocess_5_6>
        <masterprocess_5_7>0</masterprocess_5_7>
        <masterprocess_5_8>0</masterprocess_5_8>
        <masterprocess_5_9>0</masterprocess_5_9>
        <masterprocess_5_10>0</masterprocess_5_10>
        <masterprocess_6_0>0</masterprocess_6_0>
        <masterprocess_6_1>0</masterprocess_6_1>
        <masterprocess_6_2>0</masterprocess_6_2>
        <masterprocess_6_3>0</masterprocess_6_3>
        <masterprocess_6_4>0</masterprocess_6_4>
        <masterprocess_6_5>0</masterprocess_6_5>
        <masterprocess_6_6>0</masterprocess_6_6>
        <masterprocess_6_7>0</masterprocess_6_7>
        <masterprocess_6_8>0</masterprocess_6_8>
        <masterprocess_6_9>0</masterprocess_6_9>
        <masterprocess_6_10>0</masterprocess_6_10>
        <masterprocess_7_0>0</masterprocess_7_0>
        <masterprocess_7_1>0</masterprocess_7_1>
        <masterprocess_7_2>0</masterprocess_7_2>
        <masterprocess_7_3>0</masterprocess_7_3>
        <masterprocess_7_4>0</masterprocess_7_4>
        <masterprocess_7_5>0</masterprocess_7_5>
        <masterprocess_7_6>0</masterprocess_7_6>
        <masterprocess_7_7>0</masterprocess_7_7>
        <masterprocess_7_8>0</masterprocess_7_8>
        <masterprocess_7_9>0</masterprocess_7_9>
        <masterprocess_7_10>0</masterprocess_7_10>
    </defaultaudiosettings>
    <audio>
        <mute>false</mute>
        <fvolumelevel>1.000000</fvolumelevel>
    </audio>
</settings>
```
I'm going to take a break here I have a Appointment>>> Please take this time to learn How to Use Code Tags, [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)
 I'll be back in couple of hours.

---

### Post by QIII on 2017-07-27
Hello!

Please use pastebin.ubuntu.com and then give us a link.

Cheers!

---

### Post by rudybaby on 2017-07-27
[http://pastebin.ubuntu.com/25186989/](http://pastebin.ubuntu.com/25186989/)

---

### Post by Bucky Ball on 2017-07-27
> **rudybaby said:**
> 
I am going to reinstall it with these commands: 
[COLOR=#C20CB9]**sudo**[/COLOR][COLOR=#C20CB9]**apt-get install**[/COLOR][COLOR=#000000] software-properties-common
[/COLOR][COLOR=#C20CB9]**sudo**[/COLOR] add-apt-repository ppa:team-xbmc**/**ppa
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get update**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] kodi

Are these the correct commands?

Why are you doing this? Kodi is in the repositories. All you need is

```
sudo apt install kodi
```

That is it. Avoid installing from third-party sites unless no other options. You may get different results with the version in your releases repo if not the same version as the one you're downloading.

---

### Post by rudybaby on 2017-07-28
OK, now I removed Kodi thru Ubuntu software and checked list of apps installed, then also removed thru terminal kodi-bin. I then installed kodi thru Ubuntu software and still the same problem. I tried to right click the icon on the taskbar and tried fullscreen and tried standalone. Same thing, don't see Kodi and icon has those two arrows. HELP

---

### Post by #&amp;thj^% on 2017-07-28
What cable are you using to hook up to the TV?
VGA, HDMI,  DVI.

---

### Post by rudybaby on 2017-07-28
HDMI cable to TV
Should I try another distro like Fedora? or is that a waste of time?

---

### Post by #&amp;thj^% on 2017-07-28
First lets see if we can force kodi to use that HDMI.
where your guisettings.xml now reads like this**"<monitor default="true">Default</monitor>"**
Try changing that value to:
```
<monitor>HDMI-0</monitor>
```
Exactly like the above.
Now if you need a jog where that file is in:
```
cd ~/.kodi/userdata
gedit guisettings.xml
```
No need for sudo here.
And please make sure kodi is not showing in the top panel, if it is right click it and Close first.
This is not a guaranty it will solve this but something to see if we can force it to display now.
Fingers Crossed

---

### Post by rudybaby on 2017-07-28
do i replace that whole line? monitor default = "true">Default</monitor>
with just this?
[COLOR=#000000][FONT=&quot]<monitor>HDMI-0</monitor>[/FONT][/COLOR]
or  
monitor default =  [COLOR=#000000][FONT=&quot]<monitor>HDMI-0</monitor>[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-07-28
Exactly like this: "<monitor>HDMI-0</monitor>"

---

### Post by rudybaby on 2017-07-28
Didn't work. I noticed that my desktop says "Ubuntu Desktop" on the very top left, but when I open Kodi, the icon appears in the left toolbar and the Ubuntu Desktop disappears. Also it takes about 10 seconds for my mouse to reappear. Not sure if that gives you any clues.

---

### Post by #&amp;thj^% on 2017-07-28
Sounds like it is segfaulting. You can try right clicking it in the top panel now and hit close.
What version of kodi are you using, paste back this form the terminal:
```
apt policy kodi
```

---

### Post by rudybaby on 2017-07-28
kodi:
  Installed: 2:17.3+git20170525.0741-final-0zesty
  Candidate: 2:17.3+git20170525.0741-final-0zesty
  Version table:
 *** 2:17.3+git20170525.0741-final-0zesty 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main i386 Packages
        100 /var/lib/dpkg/status
     2:17.1+dfsg1-1ubuntu0.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
     2:17.1+dfsg1-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages

---

### Post by #&amp;thj^% on 2017-07-28
Well this is being very stubborn on giving us any clues here.
Just one more thing to try here, run this in the terminal and paste back any info it returns:
```
kodi --verbose
```

---

### Post by rudybaby on 2017-07-28
kodi icon appears in left toolbar, but not on desktop. terminal seems to freeze after.

---

### Post by #&amp;thj^% on 2017-07-28
In the terminal hit Keys <ctrl +c>
See if it reports anything now.

---

### Post by rudybaby on 2017-07-28
nothing. what kind of dog is that? he's beautiful!

---

### Post by #&amp;thj^% on 2017-07-28
Thanks that's Old Jake he is a French Mastiff and eats more than me and my wife together. ;)
I'm just at a loss here on the kodi debacle.
We can try to looks through the logs I guess, and you seem to find using Paste Bin easier to paste long text like QIII showed you>
```
cd ~/.kodi/temp
gedit kodi.log
```
It might show something useful?

---

### Post by rudybaby on 2017-07-28
[http://pastebin.ubuntu.com/25192883/](http://pastebin.ubuntu.com/25192883/)

---

### Post by #&amp;thj^% on 2017-07-28
Well from the logs it thinks it is running.
Is there a chance it is showing on another workspace or Screen?
Try opening again, and in the panel try selecting show in this workspace or even workspace left or right.

---

### Post by rudybaby on 2017-07-28
Where exactly are those commands? When I right click the icon, not there and right click the desktop, not there.

---

### Post by #&amp;thj^% on 2017-07-28
Well do you see in the launcher (On the Left hand Side) at the bottomish a work space indicator?

---

### Post by rudybaby on 2017-07-28
there is no workspace indicator anywhere i can find on my desktop or toobars

---

### Post by Frogs Hair on 2017-07-28
> **rudybaby said:**
> there is no workspace indicator anywhere i can find on my desktop or toobars

Workspaces are enabled in appearance preferences and might be under the behavior tab.

---

### Post by #&amp;thj^% on 2017-07-28
It should be there without jumping through any hoops.
See my screenshot to see what it looks like.

---

### Post by rudybaby on 2017-07-28
OK. the workspace 4 square icon is on the taskbar:)
It shows only one workspace in the upper left corner of the foursquare. When I click on the icon, 8 workspaces are shown. The upper left one is Kodi:), while the other 7 are blank desktops. When I click on the Kodi workspace, it returns to a blank desktop.  Should I have 8 workspaces? I tried to close them but nothing happens. Right click does nothing. Tried to drag them away. Nope.

---

### Post by #&amp;thj^% on 2017-07-28
This is so very odd that a icon for kodi is there, but shows a blank when clicking it.
Have you tried settings in your Vizio menu? (I'm just stabbing here now)

---

### Post by rudybaby on 2017-07-28
But other apps like Mozilla or Libre open fine. I don't know any settings in Vizio TV to change b/c it is working for everything else.  When you click on the workspaces, are there always 8? How do you close one?

There is an app Unity Tweak which has workspaces, but I don't know if the answer is in there. Kodi is opening in a workspace but I can't bring that workspace to the desktop.

I'm going to open a new thread on workspaces and see if someone knows what to do.

Thanks 1fallen for all you help!

---

### Post by #&amp;thj^% on 2017-07-28
> **rudybaby said:**
> Thanks 1fallen for all you help!

Your Very Welcome, but i wish we had a success story here. :(

---

### Post by vasa1 on 2017-07-28
> **rudybaby said:**
> kodi:
  Installed: 2:17.3+git20170525.0741-final-0zesty
  Candidate: 2:17.3+git20170525.0741-final-0zesty
  Version table:
 *** 2:17.3+git20170525.0741-final-0zesty 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main i386 Packages
        100 /var/lib/dpkg/status
     2:17.1+dfsg1-1ubuntu0.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
     2:17.1+dfsg1-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
You've been asked at least once to use code tags. Please do so.

See the difference for yourself:
[center]Without code tags[/center]

kodi:
  Installed: 2:17.3+git20170525.0741-final-0zesty
  Candidate: 2:17.3+git20170525.0741-final-0zesty
  Version table:
 *** 2:17.3+git20170525.0741-final-0zesty 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main i386 Packages
        100 /var/lib/dpkg/status
     2:17.1+dfsg1-1ubuntu0.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
     2:17.1+dfsg1-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages

[center]***** With code tags *****[/center]
```
kodi:
  Installed: 2:17.3+git20170525.0741-final-0zesty
  Candidate: 2:17.3+git20170525.0741-final-0zesty
  Version table:
 *** 2:17.3+git20170525.0741-final-0zesty 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main i386 Packages
        100 /var/lib/dpkg/status
     2:17.1+dfsg1-1ubuntu0.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
     2:17.1+dfsg1-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
```

---

### Post by Bucky Ball on 2017-07-28
Here's something:

> Go to
Accesories/ File manager> .kodi> User data> Database> Then delete textures13.db from the file.

[From here]("https://askubuntu.com/questions/623056/kodi-loads-on-ubuntu-14-04-but-doesnt-open"). 

You never know. What I do know from my experience with Xbmc/Kodi, and it has been quite a bit (I have had this issue before a few years ago but can't remember how I fixed), when Kodi doesn't open, it is generally an issue with a setting in Kodi config file - usually a simple tweak - rather than an issue with any setting, graphics or otherwise, in or of the Ubuntu OS.

If you start changing the Ubuntu global vid settings around, which doubtfully have anything to do with this, then you may create a new problem. ;) 

Is the rest of Ubuntu working fine and also all it's apps? Yes? Then this is Kodi specific. It usually is.

---

### Post by again? on 2017-07-29
You can also try starting with fresh user settings by moving them to a backup folder.
Close kodi then run in terminal
```
killall kodi
mv ~/.kodi ~/.kodi.bak
```
Then try starting kodi again.

Did you try to run the default Ubuntu zesty version of kodi first?

How you have 8 workspaces without knowing how you got there is puzzling.
You can set your workspaces in unity-tweak-tool.
```
sudo apt install unity-tweak-tool
```

I installed the default Ubuntu(zesty) and xbmc/ppa versions of kodi in Ubuntu/unity 17.04 and both
start without issue. (even if I set 8 workspaces :p)

---

### Post by #&amp;thj^% on 2017-07-29
> **guber2 said:**
> You can also try starting with fresh user settings by moving them to a backup folder.
Close kodi then run in terminal
```
killall kodi
mv ~/.kodi ~/.kodi.bak
```
Then try starting kodi again.

Did you try to run the default Ubuntu zesty version of kodi first?

How you have 8 workspaces without knowing how you got there is puzzling.
You can set your workspaces in unity-tweak-tool.
```
sudo apt install unity-tweak-tool
```

I installed the default Ubuntu(zesty) and xbmc/ppa versions of kodi in Ubuntu/unity 17.04 and both
start without issue. (even if I set 8 workspaces :p)
+1
> **Bucky Ball said:**
> Here's something:



[From here]("https://askubuntu.com/questions/623056/kodi-loads-on-ubuntu-14-04-but-doesnt-open"). 

**_If you start changing the Ubuntu global vid settings around, which doubtfully have anything to do with this, then you may create a new problem. ;) _**

Is the rest of Ubuntu working fine and also all it's apps? Yes? Then this is Kodi specific. It usually is.

Nah it always defaults to the working display. Never had any issues with changing that, but it has helped forcing the right screen.(FWIW :)) 
However this sounds interesting ".kodi/userdata/Database/" then remove "Textures13.db" sounds like a neat trick. :)
I just put that in my bag of future tips Thanks!

---

### Post by deadflowr on 2017-07-29
> When you click on the workspaces, are there always 8? How do you close one?

The 8 workspaces is something I'd look into.
Most desktops set with only 4 as the default selection, so unless you toggled and added 4 more it could have something to do with that.
In Ubuntu, you can try turning off workspaces by going into Appearance > Behavior there should be a mark for Enable Workspaces, unchecking it will turn workspaces off and leave you with a single desktop workspace.

I would also suggest while in System Settings to take a quick look at Displays, just to make sure there isn't some phantom display (monitor) which may explain why it is showing 8 workspaces.
(If by some odd chance there is some extra monitor showing, turning that off is fairly self-explanatory on that Displays page; only a matter of toggling a button from on to off)

---

### Post by rudybaby on 2017-07-30
I don't have that much into this Ubuntu install, just my VPN setup. If I reinstall fresh, where should I get the correct updated version of Kodi? from the wiki or from Ubuntu Software? PPA?

---

### Post by Frogs Hair on 2017-07-30
Kodi is in the repository and that's safest way to go . I just installed and started Kodi from the menu icon.  

```
sudo apt install kodi 
```

---

### Post by rudybaby on 2017-07-30
BINGO!!!!!!!!!!!!!!!!!!!!  There were two displays - my Vizio TV and a "built in display". I turned off the built in and KODI showed up on the desktop.  Damn that was easy. ):P

Thank you all for your patience. Sometimes the simplest thing is the answer.

---

