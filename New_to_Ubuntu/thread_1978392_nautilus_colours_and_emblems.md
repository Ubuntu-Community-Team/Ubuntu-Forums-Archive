---
title: "nautilus colours and emblems"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by traditionalist on 2012-05-11
I keep seeing references to "colours and emblems" for nautilus. Is this all old stuff?  Or is it supported in nautilus in 12.04?

Regards...Trad

---

### Post by Lisiano on 2012-05-11
I'm guessing you mean Icons the system uses and the color scheme used by your windows, if that is what you meant, then yes.
I attached a screenshot with Nautilus displaying the Lubuntu theme and Oxygen icons (From KDE). Easiest way to tweak those settings is to install a tool called [Gnome Tweak Tool]("apt://gnome-tweak-tool"), just press the name to open up Ubuntu Software Center and install it, you can then find the options in the "Theme" menu.

---

### Post by Enigmapond on 2012-05-11
No he's referring to wallpaper and emblems which seem to be an issue of not working in 12.04. I've install nautilus-wallpaper and it doesn't work...there are no emblems anymore for some reason...or I've yet to find them.

---

### Post by traditionalist on 2012-05-11
> **Lisiano said:**
> I'm guessing you mean Icons the system uses and the color scheme used by your windows, if that is what you meant, then yes.
I attached a screenshot with Nautilus displaying the Lubuntu theme and Oxygen icons (From KDE). Easiest way to tweak those settings is to install a tool called [Gnome Tweak Tool]("apt://gnome-tweak-tool"), just press the name to open up Ubuntu Software Center and install it, you can then find the options in the "Theme" menu.

Thanks, but that is not what I meant. There are lots of references on the web to nautilus "Colours and Emblems".  I can't find anything like this in my file manager, or a package to customise it.  

Example references;

 [http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x?prevpoll=1](http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x?prevpoll=1)

[http://ubuntugenius.wordpress.com/2010/05/23/change-nautilus-window-backgroundscoloursgradients-folder-emblems-in-ubuntu/](http://ubuntugenius.wordpress.com/2010/05/23/change-nautilus-window-backgroundscoloursgradients-folder-emblems-in-ubuntu/)

Regards....Trad

---

### Post by Lisiano on 2012-05-11
Oh, it looks like assinging emblems was dropped in Nautilus 3.0, but it looks like it's still possible to make them, I haven't tried since I don't use emblems but give it a go
[http://ubuntuguide.net/add-emblems-to-nautilus-files-folders-in-ubuntu-12-04-11-10](http://ubuntuguide.net/add-emblems-to-nautilus-files-folders-in-ubuntu-12-04-11-10) EDIT: The PPA in that page is obsolete, use ppa:nae-team/ppa instead.
```
sudo add-apt-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-actions nautilus-actions-extra
nautilus -q
nautilus
```
Per the wallpaper, a workaround for now is to open the images on eog first then set as wallpaper from it. EDIT: Judging by the files in the PPA, might also be fixed by that PPA.

---

### Post by traditionalist on 2012-05-11
> **Enigmapond said:**
> No he's referring to wallpaper and emblems which seem to be an issue of not working in 12.04. I've install nautilus-wallpaper and it doesn't work...there are no emblems anymore for some reason...or I've yet to find them.

Yes, that's correct.  

Regards....Trad

---

### Post by traditionalist on 2012-05-11
> **Lisiano said:**
> Oh, it looks like assinging emblems was dropped in Nautilus 3.0, but it looks like it's still possible to make them, I haven't tried since I don't use emblems but give it a go
[http://ubuntuguide.net/add-emblems-to-nautilus-files-folders-in-ubuntu-12-04-11-10](http://ubuntuguide.net/add-emblems-to-nautilus-files-folders-in-ubuntu-12-04-11-10)
Per the wallpaper, a workaround for now is to open the images on eog first then set as wallpaper from it.

Thanks, tried that immediately, unfortunately it doesn't work, gives the following error;

```

The following packages have unmet dependencies:
 nautilus-actions-extra : Depends: nautilus-gksu but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Regards....Trad

---

### Post by Lisiano on 2012-05-11
The PPA in that page is obsolete, use ppa:nae-team/ppa instead.
```
sudo add-apt-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-actions nautilus-actions-extra
nautilus -q
nautilus
```
This will fix both emblems and wallpaper changing.

---

### Post by Enigmapond on 2012-05-11
> **traditionalist said:**
> Thanks, tried that immediately, unfortunately it doesn't work, gives the following error;

```

The following packages have unmet dependencies:
 nautilus-actions-extra : Depends: nautilus-gksu but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Regards....Trad

That package is currently not available to 12.04...I tried as well some time ago.

Cool I will try those thanx Lisiano!

---

### Post by Lisiano on 2012-05-11
Tried myself, emblems work, wallpaper works and even "Open Terminal Here" works (It was annoying without it), though emblems don't appear until after a refresh (F5)

---

### Post by Enigmapond on 2012-05-11
Well that's not an option as it wants to remove all these before it will install:

```
       Remove the following packages:                                          
1)       bluez-alsa:i386                                                       
2)       glib-networking:i386                                                  
3)       google-earth-stable                                                   
4)       gstreamer0.10-fluendo-mp3:i386                                        
5)       gstreamer0.10-plugins-base:i386                                       
6)       gstreamer0.10-plugins-good:i386                                       
7)       gstreamer0.10-x:i386                                                  
8)       gtk2-engines:i386                                                     
9)       gtk2-engines-murrine:i386                                             
10)      gtk2-engines-oxygen:i386                                              
11)      gtk2-engines-pixbuf:i386                                              
12)      gvfs:i386                                                             
13)      gvfs-libs:i386                                                        
14)      ia32-libs                                                             
15)      ia32-libs-multiarch:i386                                              
16)      ibus-gtk:i386                                                         
17)      libaa1:i386                                                           
18)      libacl1:i386                                                          
19)      libao4:i386                                                           
20)      libasn1-8-heimdal:i386                                                
21)      libasound2:i386                                                       
22)      libasound2-plugins:i386                                               
23)      libasyncns0:i386                                                      
24)      libatk1.0-0:i386                                                      
25)      libattr1:i386                                                         
26)      libaudio2:i386                                                        
27)      libaudiofile1:i386                                                    
28)      libavahi-client3:i386                                                 
29)      libavahi-common3:i386                                                 
30)      libavc1394-0:i386                                                     
31)      libbz2-1.0:i386                                                       
32)      libc6:i386                                                            
33)      libcaca0:i386                                                         
34)      libcairo-gobject2:i386                                                
35)      libcairo2:i386                                                        
36)      libcanberra-gtk-module:i386                                           
37)      libcanberra-gtk0:i386                                                 
38)      libcanberra0:i386                                                     
39)      libcap2:i386                                                          
40)      libcapi20-3:i386                                                      
41)      libcdparanoia0:i386                                                   
42)      libcomerr2:i386                                                       
43)      libcroco3:i386                                                        
44)      libcups2:i386                                                         
45)      libcupsimage2:i386                                                    
46)      libcurl3:i386                                                         
47)      libdatrie1:i386                                                       
48)      libdb5.1:i386                                                         
49)      libdbus-1-3:i386                                                      
50)      libdbus-glib-1-2:i386                                                 
51)      libdbusmenu-qt2:i386                                                  
52)      libdrm-intel1:i386                                                    
53)      libdrm-nouveau1a:i386                                                 
54)      libdrm-radeon1:i386                                                   
55)      libdrm2:i386                                                          
56)      libdv4:i386                                                           
57)      libelf1:i386                                                          
58)      libesd0:i386                                                          
59)      libexif12:i386                                                        
60)      libexpat1:i386                                                        
61)      libffi6:i386                                                          
62)      libflac8:i386                                                         
63)      libfontconfig1:i386                                                   
64)      libfreetype6:i386                                                     
65)      libgail-common:i386                                                   
66)      libgail18:i386                                                        
67)      libgcc1:i386                                                          
68)      libgconf-2-4:i386                                                     
69)      libgcrypt11:i386                                                      
70)      libgd2-xpm:i386                                                       
71)      libgdbm3:i386                                                         
72)      libgdk-pixbuf2.0-0:i386                                               
73)      libgettextpo0:i386                                                    
74)      libgl1-mesa-dri:i386                                                  
75)      libgl1-mesa-glx:i386                                                  
76)      libglapi-mesa:i386                                                    
77)      libglib2.0-0:i386                                                     
78)      libglu1-mesa:i386                                                     
79)      libgnome-keyring0:i386                                                
80)      libgnutls26:i386                                                      
81)      libgomp1:i386                                                         
82)      libgpg-error0:i386                                                    
83)      libgphoto2-2:i386                                                     
84)      libgphoto2-port0:i386                                                 
85)      libgpm2:i386                                                          
86)      libgssapi-krb5-2:i386                                                 
87)      libgssapi3-heimdal:i386                                               
88)      libgstreamer-plugins-base0.10-0:i386                                  
89)      libgstreamer0.10-0:i386                                               
90)      libgtk2.0-0:i386                                                      
91)      libgudev-1.0-0:i386                                                   
92)      libhcrypto4-heimdal:i386                                              
93)      libheimbase1-heimdal:i386                                             
94)      libheimntlm0-heimdal:i386                                             
95)      libhx509-5-heimdal:i386                                               
96)      libibus-1.0-0:i386                                                    
97)      libice6:i386                                                          
98)      libidn11:i386                                                         
99)      libiec61883-0:i386                                                    
100)     libieee1284-3:i386                                                    
101)     libjasper1:i386                                                       
102)     libjpeg-turbo8:i386                                                   
103)     libjpeg8:i386                                                         
104)     libjson0:i386                                                         
105)     libk5crypto3:i386                                                     
106)     libkeyutils1:i386                                                     
107)     libkrb5-26-heimdal:i386                                               
108)     libkrb5-3:i386                                                        
109)     libkrb5support0:i386                                                  
110)     liblcms1:i386                                                         
111)     libldap-2.4-2:i386                                                    
112)     libllvm3.0:i386                                                       
113)     libltdl7:i386                                                         
114)     libmad0:i386                                                          
115)     libmikmod2:i386                                                       
116)     libmng1:i386                                                          
117)     libmpg123-0:i386                                                      
118)     libmysqlclient18:i386                                                 
119)     libncurses5:i386                                                      
120)     libncursesw5:i386                                                     
121)     libnspr4:i386                                                         
122)     libnss3:i386                                                          
123)     libodbc1:i386                                                         
124)     libogg0:i386                                                          
125)     liboil0.3:i386                                                        
126)     libopenal1:i386                                                       
127)     liborc-0.4-0:i386                                                     
128)     libp11-kit0:i386                                                      
129)     libpango1.0-0:i386                                                    
130)     libpciaccess0:i386                                                    
131)     libpcre3:i386                                                         
132)     libpixman-1-0:i386                                                    
133)     libpng12-0:i386                                                       
134)     libproxy1:i386                                                        
135)     libpulse-mainloop-glib0:i386                                          
136)     libpulse0:i386                                                        
137)     libpulsedsp:i386                                                      
138)     libqt4-dbus:i386                                                      
139)     libqt4-declarative:i386                                               
140)     libqt4-designer:i386                                                  
141)     libqt4-network:i386                                                   
142)     libqt4-opengl:i386                                                    
143)     libqt4-qt3support:i386                                                
144)     libqt4-script:i386                                                    
145)     libqt4-scripttools:i386                                               
146)     libqt4-sql:i386                                                       
147)     libqt4-sql-mysql:i386                                                 
148)     libqt4-svg:i386                                                       
149)     libqt4-test:i386                                                      
150)     libqt4-xml:i386                                                       
151)     libqt4-xmlpatterns:i386                                               
152)     libqtcore4:i386                                                       
153)     libqtgui4:i386                                                        
154)     libqtwebkit4:i386                                                     
155)     libraw1394-11:i386                                                    
156)     libroken18-heimdal:i386                                               
157)     librsvg2-2:i386                                                       
158)     librsvg2-common:i386                                                  
159)     librtmp0:i386                                                         
160)     libsamplerate0:i386                                                   
161)     libsane:i386                                                          
162)     libsasl2-2:i386                                                       
163)     libsdl-image1.2:i386                                                  
164)     libsdl-mixer1.2:i386                                                  
165)     libsdl-net1.2:i386                                                    
166)     libsdl-ttf2.0-0:i386                                                  
167)     libsdl1.2debian:i386                                                  
168)     libselinux1:i386                                                      
169)     libshout3:i386                                                        
170)     libslang2:i386                                                        
171)     libsm6:i386                                                           
172)     libsndfile1:i386                                                      
173)     libsoup-gnome2.4-1:i386                                               
174)     libsoup2.4-1:i386                                                     
175)     libspeex1:i386                                                        
176)     libspeexdsp1:i386                                                     
177)     libsqlite3-0:i386                                                     
178)     libssl0.9.8:i386                                                      
179)     libssl1.0.0:i386                                                      
180)     libstdc++5:i386                                                       
181)     libstdc++6:i386                                                       
182)     libtag1-vanilla:i386                                                  
183)     libtag1c2a:i386                                                       
184)     libtasn1-3:i386                                                       
185)     libtdb1:i386                                                          
186)     libthai0:i386                                                         
187)     libtheora0:i386                                                       
188)     libtiff4:i386                                                         
189)     libtinfo5:i386                                                        
190)     libudev0:i386                                                         
191)     libunistring0:i386                                                    
192)     libusb-0.1-4:i386                                                     
193)     libuuid1:i386                                                         
194)     libv4l-0:i386                                                         
195)     libv4lconvert0:i386                                                   
196)     libvisual-0.4-0:i386                                                  
197)     libvisual-0.4-plugins:i386                                            
198)     libvorbis0a:i386                                                      
199)     libvorbisenc2:i386                                                    
200)     libvorbisfile3:i386                                                   
201)     libwavpack1:i386                                                      
202)     libwind0-heimdal:i386                                                 
203)     libwrap0:i386                                                         
204)     libx11-6:i386                                                         
205)     libx11-xcb1:i386                                                      
206)     libxau6:i386                                                          
207)     libxaw7:i386                                                          
208)     libxcb-glx0:i386                                                      
209)     libxcb-render0:i386                                                   
210)     libxcb-shm0:i386                                                      
211)     libxcb1:i386                                                          
212)     libxcomposite1:i386                                                   
213)     libxcursor1:i386                                                      
214)     libxdamage1:i386                                                      
215)     libxdmcp6:i386                                                        
216)     libxext6:i386                                                         
217)     libxfixes3:i386                                                       
218)     libxft2:i386                                                          
219)     libxi6:i386                                                           
220)     libxinerama1:i386                                                     
221)     libxml2:i386                                                          
222)     libxmu6:i386                                                          
223)     libxp6:i386                                                           
224)     libxpm4:i386                                                          
225)     libxrandr2:i386                                                       
226)     libxrender1:i386                                                      
227)     libxslt1.1:i386                                                       
228)     libxss1:i386                                                          
229)     libxt6:i386                                                           
230)     libxtst6:i386                                                         
231)     libxv1:i386                                                           
232)     libxxf86vm1:i386                                                      
233)     nautilus-open-terminal                                                
234)     odbcinst1debian2:i386                                                 
235)     skype                                                                 
236)     skype-bin:i386                                                        
237)     sni-qt:i386                                                           
238)     xaw3dg:i386                                                           
239)     zlib1g:i386  
```

---

### Post by traditionalist on 2012-05-11
> **Lisiano said:**
> The PPA in that page is obsolete, use ppa:nae-team/ppa instead.
```
sudo add-apt-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-actions nautilus-actions-extra
nautilus -q
nautilus
```This will fix both emblems and wallpaper changing.

Excellent!  Thank you very much indeed, that worked.

Regards....Trad

---

### Post by traditionalist on 2012-05-11
QUOTE=Enigmapond;11927201]Well that's not an option as it wants to remove all these before it will install:
UNQUOTE

It didn't ask me to remove anything.

Regards...Trad

---

### Post by Lisiano on 2012-05-11
Same, didn't ask to remove anything. That output doesn't look like it came from Synaptic or Apt, did you try Aptitude or something else? Try using Apt or Synaptic or USC instead.

---

### Post by traditionalist on 2012-05-11
What I actually wanted, was to do this;

[http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x?prevpoll=1](http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x?prevpoll=1)

so I can colour code some files. But I needed the emblems to do it.  I am going to try it now and see if it works.

Thanks for the input!

Regards....Trad

---

### Post by traditionalist on 2012-05-11
Basically like this;

[[IMG]http://img593.imageshack.us/img593/8238/documents002.th.png[/IMG]](http://img593.imageshack.us/i/documents002.png/)

( That is the Marlin file manager  [https://launchpad.net/marlin](https://launchpad.net/marlin)  )

but preferably globally according to file type.  All text files green for instance.

Regards...Trad

---

### Post by vexorian on 2012-08-28
Hello. Just in case someone googling finds this thread

nautilus-actions-extra installs a lot of things, some of which are not that great (imageshack uploading? really? That site bans views from my country so no thanks).

So, here is what I did for a "minimal" install of emblems:

```

sudo add-apt-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get --no-install-recommends install nautilus-advanced-menu emblemize
nautilus -q
nautilus

```

---

