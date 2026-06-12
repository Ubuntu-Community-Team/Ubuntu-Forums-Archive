---
title: "Anyone able to stream Quicktime in Oneiric"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-10-07
I have been trying to watch some vids on the Apple site and they aren't playing at all.
If I boot Natty, all vids play just fine inside both firefox and chromium windows using gecko-mediaplayer plugins.

Different story in Oneiric though...

In chromium:
I get a pop-out gnome-mplayer window which has player controls but is otherwise dead, no content, no window borders and inside the browser window it has a loading type spinner on the page with the words "Missing plug-in".

In firefox:
The media player appears embedded in the web page but again refuses to play, just an endless loading spinner and no vid ever plays.

Using 64-bit edition here.  I have tried installing w64 codecs to no avail.

---

### Post by cariboo on 2011-10-07
It works here, I'm on 64-bit too. All I did was install the ubuntu-restricted-extras. I'm using chromium.

---

### Post by effenberg0x0 on 2011-10-07
Works here, tested same site as Cariboo. I'm on 64bit too.
720p video looks like a much lower resolution thou. Don't know if that's the expected quality for Quicktime streams. Very grainy.


[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) might help.

Regards,
Effenberg

---

### Post by x-shaney-x on 2011-10-07
Forgot to mention one important factor, I'm on kubuntu.
I do have restricted extras and addons installed though.

Can only assume something in the ubuntu restricted pack does it, though it needs to download 104 items to do it.

---

### Post by mc4man on 2011-10-07
kubuntu may have some issue - easy to test
If you're using the gecko plugin then you're using mplayer  so maybe try mplayer from cli & see
Picking one from site, the caching is optional but usually a good idea
```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://trailers.apple.com/movies/independent/theraven/theraven-tlr1_h720p.mov -cache 4096
```

Or if you have a decent connection do a wget & then see if the file in your home dir. is playable by anything you have installed. (took 45 sec. here to dl

```
 wget -U QuickTime/7.6.2 http://trailers.apple.com/movies/independent/theraven/theraven-tlr1_h720p.mov
```

(the totem Mozilla plugin may have a current issue with the apple site though totem it self works fine if given the url & actually caches very quickly & completely in /tmp

---

### Post by x-shaney-x on 2011-10-07
Hmm, the trouble is the vids I tried do not seem to have file extensions as such.

Here is a typical example:  [http://www.apple.com/ipad/built-in-apps/ibooks.html](http://www.apple.com/ipad/built-in-apps/ibooks.html)
Near the top of that page is "Watch the video" link.
Anyone get that to play?

---

### Post by mc4man on 2011-10-07
Those work fine here, (in browser), though using FF & the totem plugin

Edit: there's nothing unusual about those vid's, see screen, so likely a browser or plugin issue

---

### Post by x-shaney-x on 2011-10-08
Hmm, after checking back today and doing some exploring, it turns out most vids ARE playing normally.
Just certain sections of the site throw up the problem described above.

None of the videos in are I linked to will play but as far as I can tell all other parts of the site and trailers etc do play.

---

### Post by xeizo on 2011-10-08
I have the same problems, there seems to be some dependency hell going in which can explain things. I get this when I try to install restricted-extras. I already installed it  a week ago, but there seem to be some regression as it wants to install more packages - and remove lots of stuff.

```
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad-multiverse kubuntu-restricted-extras 
  libavcodec-extra-53{b} libavutil-extra-51{ab} libfaac0{a} 
  libopenjpeg2{a} libvo-aacenc0{a} libvo-amrwbenc0{a} 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3 116 kB of archives. After unpacking 7 537 kB will be used.
The following packages have unmet dependencies:
  libavutil-extra-51: Står i konflikt med: libavutil51 but 4:0.7.2-1ubuntu1 is installed.
  libavcodec-extra-53: Står i konflikt med: libavcodec53 but 4:0.7.2-1ubuntu1 is installed.
open: 27; closed: 1047; defer: 6; conflict: 7                        .The following actions will resolve these dependencies:

       Remove the following packages:                              
1)       flashplugin-downloader                                    
2)       flashplugin-installer                                     
3)       ia32-libs-multiarch                                       
4)       libacl1                                                   
5)       libasound2                                                
6)       libasound2-plugins                                        
7)       libasyncns0                                               
8)       libatk1.0-0                                               
9)       libattr1                                                  
10)      libaudio2                                                 
11)      libavahi-client3                                          
12)      libavahi-common3                                          
13)      libavcodec53                                              
14)      libavutil51                                               
15)      libc6                                                     
16)      libcairo2                                                 
17)      libcomerr2                                                
18)      libcups2                                                  
19)      libcupsimage2                                             
20)      libcurl3                                                  
21)      libdatrie1                                                
22)      libdb5.1                                                  
23)      libdbus-1-3                                               
24)      libdrm2                                                   
25)      libexpat1                                                 
26)      libffi6                                                   
27)      libflac8                                                  
28)      libfontconfig1                                            
29)      libfreetype6                                              
30)      libgcc1                                                   
31)      libgcrypt11                                               
32)      libgdbm3                                                  
33)      libgdk-pixbuf2.0-0                                        
34)      libgl1-mesa-glx                                           
35)      libglapi-mesa                                             
36)      libglib2.0-0                                              
37)      libgnutls26                                               
38)      libgpg-error0                                             
39)      libgssapi-krb5-2                                          
40)      libgtk2.0-0                                               
41)      libice6                                                   
42)      libidn11                                                  
43)      libjack-jackd2-0                                          
44)      libjasper1                                                
45)      libjpeg62                                                 
46)      libjson0                                                  
47)      libk5crypto3                                              
48)      libkeyutils1                                              
49)      libkrb5-3                                                 
50)      libkrb5support0                                           
51)      liblcms1                                                  
52)      libldap-2.4-2                                             
53)      libmng1                                                   
54)      libnspr4                                                  
55)      libnspr4-0d                                               
56)      libnss3                                                   
57)      libnss3-1d                                                
58)      libogg0                                                   
59)      libpango1.0-0                                             
60)      libpcre3                                                  
61)      libpixman-1-0                                             
62)      libpng12-0                                                
63)      libpulse0                                                 
64)      libqt4-dbus                                               
65)      libqt4-declarative                                        
66)      libqt4-designer                                           
67)      libqt4-network                                            
68)      libqt4-opengl                                             
69)      libqt4-qt3support                                         
70)      libqt4-script                                             
71)      libqt4-scripttools                                        
72)      libqt4-sql                                                
73)      libqt4-svg                                                
74)      libqt4-test                                               
75)      libqt4-xml                                                
76)      libqt4-xmlpatterns                                        
77)      libqtcore4                                                
78)      libqtgui4                                                 
79)      librtmp0                                                  
80)      libsamplerate0                                            
81)      libsasl2-2                                                
82)      libsasl2-modules                                          
83)      libselinux1                                               
84)      libsm6                                                    
85)      libsndfile1                                               
86)      libspeexdsp1                                              
87)      libsqlite3-0                                              
88)      libssl1.0.0                                               
89)      libstdc++6                                                
90)      libtasn1-3                                                
91)      libthai0                                                  
92)      libtiff4                                                  
93)      libuuid1                                                  
94)      libvorbis0a                                               
95)      libvorbisenc2                                             
96)      libwrap0                                                  
97)      libx11-6                                                  
98)      libxau6                                                   
99)      libxcb-render0                                            
100)     libxcb-shm0                                               
101)     libxcb1                                                   
102)     libxcomposite1                                            
103)     libxcursor1                                               
104)     libxdamage1                                               
105)     libxdmcp6                                                 
106)     libxext6                                                  
107)     libxfixes3                                                
108)     libxft2                                                   
109)     libxi6                                                    
110)     libxinerama1                                              
111)     libxrandr2                                                
112)     libxrender1                                               
113)     libxss1                                                   
114)     libxt6                                                    
115)     libxxf86vm1                                               
116)     nspluginviewer                                            
117)     nspluginwrapper                                           
118)     zlib1g                                                    

       Leave the following dependencies unresolved:                
119)     ia32-libs recommends ia32-libs-multiarch                  
120)     kubuntu-restricted-addons recommends flashplugin-installer


Accept this solution? [Y/n/q/?] 

```

What would be the best way to solve this mess? Thankful for any thoughts.

---

### Post by xeizo on 2011-10-08
Oh, the message above only happens with aptitude, if I run apt-get instead it installs just fine:

```
Följande ytterligare paket kommer att installeras:
  gstreamer0.10-plugins-bad-multiverse libavcodec-extra-53
  libavutil-extra-51 libfaac0 libopenjpeg2 libvo-aacenc0
  libvo-amrwbenc0
Föreslagna paket:
  libfaad0
Följande paket kommer att TAS BORT:
  libavcodec53 libavutil51
Följande NYA paket kommer att installeras:
  gstreamer0.10-plugins-bad-multiverse kubuntu-restricted-extras
  libavcodec-extra-53 libavutil-extra-51 libfaac0 libopenjpeg2
  libvo-aacenc0 libvo-amrwbenc0
0 att uppgradera, 8 att nyinstallera, 2 att ta bort och 0 att inte uppgradera
```I get a shitload of error messages, most seemingly related to VLC. But the install completes alright.

edit. on a sidenote, as you can see so is apt-get translated but aptitude not.

---

### Post by xeizo on 2011-10-08
> **mc4man said:**
> kubuntu may have some issue - easy to test
If you're using the gecko plugin then you're using mplayer  so maybe try mplayer from cli & see
Picking one from site, the caching is optional but usually a good idea
```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://trailers.apple.com/movies/independent/theraven/theraven-tlr1_h720p.mov -cache 4096
```Or if you have a decent connection do a wget & then see if the file in your home dir. is playable by anything you have installed. (took 45 sec. here to dl

```
 wget -U QuickTime/7.6.2 http://trailers.apple.com/movies/independent/theraven/theraven-tlr1_h720p.mov
```(the totem Mozilla plugin may have a current issue with the apple site though totem it self works fine if given the url & actually caches very quickly & completely in /tmp

This is exactly what happens with me, following your links it plays well in mplayer but visiting Apples site I just get a message stating that I should get Quicktime if I want to watch the clips.  That's on Firefox.

---

### Post by xeizo on 2011-10-08
The same thing happens in Chromium, "get Quicktime"!

BUT, this is interesting, in Rekonq all the Apple clips plays without a hitch. So, it's most likely a plugin issue with booth Firefox and Chromium.

Could it be that the Kubuintu-devs gives more love to Rekonq ie it is intented to be the preferred browser in Kubuntu?

Anyway, I would like to know how to fix the issue because personally I would rather like to use Firefox.

---

### Post by cariboo on 2011-10-08
When running:

```
about:plugins
```

in chromium, I see:

> QuickTime Plug-in 7.6.6
The Totem 3.0.1 plugin handles video and audio streams.

could it be that quicktime doesn't work, because totem isn't installed on Kubuntu?

---

### Post by xeizo on 2011-10-08
Sure it was! I guess we can mark this as solved now ....

```
Följande ytterligare paket kommer att installeras:
  gir1.2-peas-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gnome-desktop3-data gnome-icon-theme-symbolic
  gnome-settings-daemon hwdata libgdata-common libgdata13
  libgnome-desktop-3-2 libgnomekbd-common libgnomekbd7 liboauth0
  libpeas-1.0-0 libpeas-common libtotem0 libxklavier16 nautilus-data
  totem-common totem-mozilla totem-plugins
Föreslagna paket:
  gnome-screensaver nautilus gnome-codec-install gromit
Följande NYA paket kommer att installeras:
  gir1.2-peas-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gnome-desktop3-data gnome-icon-theme-symbolic
  gnome-settings-daemon hwdata libgdata-common libgdata13
  libgnome-desktop-3-2 libgnomekbd-common libgnomekbd7 liboauth0
  libpeas-1.0-0 libpeas-common libtotem0 libxklavier16 nautilus-data
  totem totem-common totem-mozilla totem-plugins
0 att uppgradera, 22 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
Behöver hämta 2 862 kB arkiv.
Efter denna åtgärd kommer ytterligare 14,3 MB utrymme användas på disken.
Vill du fortsätta [J/n]? y

```Quicktime works excellent in Firefox after the above update, just wonder if it breaks anything else instead  ;)

---

### Post by x-shaney-x on 2011-10-08
@ cariboo907

Although totem isn't installed, chromium DOES list quicktime under the gecko-mediaplayer plugin.


@ xeizo

Just tried rekonq myself and it does indeed play EVERYTHING, including the specific vis that won't work in firefox or chromium.
Just a pity I really don't like rekonq :(

---

### Post by mc4man on 2011-10-08
At least here (ubuntu), using  the gecko-mediaplayer plugin, chromium-browser & firefox do not play the **ipad2 vids**, if switching back to the totem-mozilla plugin they play in c-b & ff

Edit:
 the trailers on the itunes site work fine in elther browser with either plugin from the watch now menu
At some point in the past the watch now wasn't working here but the download ones would (in browser). Now the opposite though the download links can obviously be used directly in some players & to actually download with wget

---

