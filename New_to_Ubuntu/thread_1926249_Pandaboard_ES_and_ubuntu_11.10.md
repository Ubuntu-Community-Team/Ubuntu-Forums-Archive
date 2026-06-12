---
title: "Pandaboard ES and ubuntu 11.10"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by jimerickso on 2012-02-15
i have followed the wiki to install ubuntu-11.10-preinstalled-desktop-armel+omap4.img to a sdhc card. insert card in panadaboard and it boots fine. but it only boots to the system configuration session over and over no matter how many times i go through the configuration. how do i get it to boot to a login screen?

---

### Post by jimerickso on 2012-02-17
i figured it out. when pandaboard resizes the rootfs at boot it creates all sorts of problems. so i built an ubuntu image from the linaro packages and made the rootfs take up the whole card. boots fine. at any rate the ubuntu netboot method is buggy and the ubuntu-11.10-preinstalled-desktop-armel+omap4.img i never got to work due to the resizing issue. so stick with the linaro ubuntu build.

---

### Post by DamiankS72 on 2012-02-23
How does one go about doing what you did? I am having the same issue.
I am not a linux newbie, but am new to building images and all the fancy stuff.

Any help is greatly appreciated.

---

### Post by DamiankS72 on 2012-02-23
The "ubuntu-11.10-preinstalled-server-armel+omap4.img" seemed to work fine. 
Just installing the gui packages on top of that.

If you wouldn't mind pointing me in the right direction on how to build my own image I would be very grateful.

---

### Post by DamiankS72 on 2012-02-23
Had the gui working but once i installed the sgx packages I didn't get a display anymore.
Try again tomorrow.

---

### Post by bmy on 2012-02-24
I've got the same problem. I looked up several guides and tutorials on the internet, telling me that i should "upgrade" and "dist-upgrade" the system first, but nothing. I guess i tried  ten times different constellations and but my ubuntu gets broken every time i install sgx graphics meta package. I also tried pre-build images of ubuntu 12.10, even though the installation of TI  OMAP4 extras was possible, the java installation was broken after wards.  I really need the SGX hardware acceleration for XRender support under java 7.

---

### Post by DamiankS72 on 2012-02-24
Decide[FONT=Arial]d to go blee[/FONT]ding edge and installed 
precise-preinstalled-desktop-armel+omap4.img.gz 

[FONT=Arial]seems to unpack and install properly. Updating at the moment.

Will report back on how the sgx packages work.[/FONT]

---

### Post by jiapei100 on 2012-03-13
Have no idea why on my shell, minicom output some messy code like:

> Press CTRL-A Z for help on special keys                                                       
                                                                                              
+lzT                                                                                          
    J&#65533;._+&#65533;Z{&#65533;&#65533;&#65533;jz)&#65533;5C&#65533;+lzT                                                                    
                          J&#65533;._+&#65533;Z{&#65533;&#65533;&#65533;jz)&#65533;5C&#65533;+lzT                                              
                                                J&#65533;._+&#65533;Z{&#65533;&#65533;&#65533;jz)&#65533;5C&#65533;+lzT                        
                                                                      J&#65533;._+&#65533;Z{&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;jz)&#65533;5C&#65533;+lzT  
                                                                                            J&#65533;._+&#65533;Z{&#1131;&#65533;&#65533;jz)&#65533;5C&#65533;+lzT
                                                                                                                  J&#65533;._+&#65533;T

....


AT S=45 S0=0 L1 VLE21 E1 Q0
Mi&#65533;icom2>5Miicom2>5Mmicom2>5Miicom2>5MZicom2>5C&#65533;&#65533;T&#1104;S=45 S0=0 L1 V1 E21 E1 Q0
Miicom2>5Miicom2>5&#65533;SZcom2>5Miicom2>MSZico[&&#65533;j&#65533;&#65533;icom2>&#65533;SZicom2>5Miicom2>MSZicom2>5Miicom2>5MiicoMiicom2>5Miicom2>5Miicom&&#65533;&#33223;&#65533;&#65533;L-A Z for help |115200 8N1 | NOR | Minicom 2.5    | VT102 |      Offline                                            


Don't know how to configure the encoding?

Cheers
Pei


---

### Post by jiapei100 on 2012-03-14
Yes, 
precise-preinstalled-server-armhf+omap4.img.gz
is working. But as for me, I still got a lot of messy code as in my last post.

Does it have something to do with the system encoding? Or, is there something wrong with my serial cable?


>  de_k&#65533;&#65533;4O[ OK }
 * S&#65533;a&#65533;&#65533;io cofio}e e&#65533;&#65533;&#65533;&#65533;k de_k&#65533; &#65533;ec&#65533;&#65533;i&#65533;y&#65533;jz- }
 * S&#65533;a&#65533;&#65533;io cofio}e e&#65533;o&#65533;k de_k&#65533;m[?4O[ OK }
 * S&#65533;a&#65533;&#65533;io cofio}e e&#65533;&#65533;&#65533;&#65533;k de_k&#65533;m[?4O[ OK }
 * S&#65533;a&#65533;&#65533;io Mo&#65533;n&#65533; e&#65533;&#65533;&#65533;&#65533;k file&#65533;y&#65533;>_Vk4O[ OK }
 * S&#65533;a&#65533;&#65533;io Fail&#65533;afe Boo"&#65533;&#65533;/&#65533;m[4O[ OK }
 * S&#65533;oio Mo&#65533;n&#65533; file&#65533;y&#65533;&#65533;em&#65533; o boo&#65533;4O[ OK }
 * S&#65533;oio Mo&#65533;n&#65533; e&#65533;o&#65533;k file&#65533;y&#65533;&#65533;em&#65533;4O[ OK }
 * S&#65533;oio Failsafe Boo&#65533; Delay&#65533;&#65533;4O[ OK }
 * S&#65533;oio cofio}e &#65533;i&#65533;&#65533;}X&#65533;eto&#65533;k de_k&#65533;&#65533;&#65533;jz- }
 * S&#65533;a&#65533;&#65533;io Sy&#65533;&#65533;em V ii&#65533;iali&#65533;a_&#65533;&#65533; coma_K&#65533;&#65533;&#65533;&#65533;y4G[ OK }
 * S&#65533;a&#65533;&#65533;io &#65533;e&#65533;y&#65533;c&#65533;2&#65533;om /e&#65533;c/&#65533;y&#65533;c&#65533;l>cof4O[ OK }
 * S&#65533;oio&#65533;e&#65533;y&#65533;ck f&#65533;om /ec/&#65533;y&#65533;c&#65533;&#65533;&#65533;f[ OK }
o &#65533;s&#65533;a&#65533;&#65533;4O[ OK }
&#65533;+io &#65533;&#65533;ofile i /e&#65533;c/a&#65533;a&#65533;mo&#65533;.d/di&#65533;ablez }..&#65533;bi>&#65533;&#65533;y&#65533;lood
&#65533; * S&#65533;oio Sy&#65533;&#65533;em V ii&#65533;iali&#65533;aio coma_K&#65533;&#65533;&#65533;&#65533;&#65533;y4O[ OK }
RS&#65533;a&#65533;&#65533;io Sy&#65533;&#65533;em V &#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a_[4O[ OK }
hed&#65533;le&#65533;&#65533;&#65533;jz- }o&#65533;la&#65533; backo&#65533;o}d &#65533;oo&#65533;am &#65533;&#65533;oce&#65533;&#65533;io daemo4O[ OK }
emo4O&#65533;z- }
 * S&#65533;a&#65533;&#65533;io E&#65533;d-&#65533;e&#65533; cofio}a_{&#65533; af&#65533;e&#65533; ii_+&#65533;z5 is&#65533;alla_&#65533;{k&#65533;?4O[ OK }
RS&#65533;oio &#65533;a_&#65533;Z&#65533;&#65533;nel me&#65533;&#65533;aoe&#65533;4O[ OK }
Sk&#65533;E&#65533;jm[1{24&#65533;&#65533;)m[1{1H&#65533;m[45m        1H      




Cheers
Pei


> **DamiankS72 said:**
> Decide[FONT=Arial]d to go blee[/FONT]ding edge and installed 
precise-preinstalled-desktop-armel+omap4.img.gz 

[FONT=Arial]seems to unpack and install properly. Updating at the moment.

Will report back on how the sgx packages work.[/FONT]

---

### Post by lizSter on 2012-06-17
Using minicom, I also see messy characters on screen while 11.10 or 12.04 server goes thru the install/setup.  

> **jiapei100 said:**
> Have no idea why on my shell, minicom output some messy code like:

Anyone know what settings need to be changed?

Using 115200 N81, No Flow Control, VT102

---

### Post by wkulecz on 2012-06-20
I never had any success with any variation of 11.10 on my Pandaboard ES.  

The 12.04 armhf release installed and configured fine, but despite a large number of updates it still has random lockups.  Basically this is the least reliable Linux system I've ever encountered, it will lockup about once a day, doesn't seem to matter if its being actively used or just sitting idle overnight.

Another problem:  I tried installing LXDE on the Pandaboard ES figuring it might be a "Unity" issue but it crashes to the login window whenever I try to open a terminal window.  On a dual core AMD 64-bit x86 system 12.04 is rock solid using either Unity or LXDE and the proprietary Nvidia drivers.

The boards also seem very fragile, our students have killed two of them already while probing SPI signals on the header while trying to interface some SPI devices.

I had high hopes for the Pandaboard, especially since Ubuntu was one of its "supported" OSes, but frankly its been a big disappointment so far.


Unfortunately I can't really help with your serial terminal problem as it worked fine for me.  You might try changing from VT102 to ANSI.  I've never reconnected the serial cable since the initial reboot and setup completed, just never found it all that useful.

---

