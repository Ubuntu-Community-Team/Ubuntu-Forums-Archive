---
title: "Problem Loading DVD Movie Program"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by Peter_Cucchiara on 2013-08-01
While trying to install software through Terminal that would allow     me to play commercial DVD movies on Ubuntu 13.04, I encountered a     problem that froze my system. I found the command:**[COLOR=#009900] sudo apt-get jnstall ubuntu-restricted-extras[/COLOR]**     on the Liberian Geek website.  Canonical made the code available.     When I executed the command the program downloaded most of the     codes. However when it reached a certain point it showed: **[COLOR=#cc0000]Configuring ttf-mscorefonts-installer[/COLOR]**     with the MS EULA text and an <OK> symbol that is inactive and     froze. When I close the Terminal and then reopen it to enter any     code, it will not allow me to enter my password but advises that I     must enter the code **[COLOR=#009900]'sudo dpkg --configure         -a'[/COLOR]** that brings up the ELUA text again in the     Terminal window. I need help to allow the program to continue or     terminate the process. Any help will be greatly appreciate since I     am a total novice with Ubuntu /Linux code.

---

### Post by VMC on 2013-08-01
I don't load anything but [VLC]("http://www.videolan.org/vlc/download-ubuntu.html"). It plays everything - music, video, you name it.  No more mucking around with all that restricted nonsense.

Just in case you need further assistance you can check out the [Comprehensive Multimedia ]("http://ubuntuforums.org/showthread.php?t=766683") section.

---

### Post by newb85 on 2013-08-01
VLC is a great program, but it's not very useful without audio or video codecs.  :)

The terminal didn't "freeze" when configuring ttf-mscorefonts-installer.  It needed you to agree to the EULA for the MS fonts before downloading and installing them from Microsoft's website.  (Of course, you could opt out of these fonts by not agreeing to the EULA and everything else in Restricted Extras would install just fine, but it was waiting for some response from you.)

Go ahead and follow the advice given:
```
sudo dpkg --configure -a
```
and then accept or refuse the MS font EULA when prompted.  That should finish installing all the codecs you need, including libdvdcss2, which is used to play DVDs.  

You will need to run one more command to equip your system to read commercial video DVDs:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

After that, you should be able to watch DVDs to your heart's content, using VLC, or whatever video player you choose.

---

### Post by Petro Dawg on 2013-08-01
I think you can get the restricted extras package from the Ubuntu software repository (no terminal commands needed).

Once the restricted extras are installed, open terminal and enter the following...

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

That worked for me anyways.

Update:
awww... newb85 beat me to it :(

Also which ubuntu flavor are you using?  There are different packages for different 'buntus...

If you are using regular, stock Ubuntu: 
```
sudo apt-get install ubuntu-restricted-extras
```

If you are using Kubuntu: 
```
 sudo apt-get install kubuntu-restricted-extras
```

If you are using Xubuntu: 
```
 sudo apt-get install xubuntu-restricted-extras
```

If you are using Lubuntu: 
```
 sudo apt-get install lubuntu-restricted-extras
```

---

### Post by 3rdalbum on 2013-08-02
When you get the EULA thing, hit Tab and then the spacebar.

To play DVDs you also need VLC.

---

### Post by Peter_Cucchiara on 2013-08-02
> **newb85 said:**
> VLC is a great program, but it's not very useful without audio or video codecs.  :)

The terminal didn't "freeze" when configuring ttf-mscorefonts-installer.  It needed you to agree to the EULA for the MS fonts before downloading and installing them from Microsoft's website.  (Of course, you could opt out of these fonts by not agreeing to the EULA and everything else in Restricted Extras would install just fine, but it was waiting for some response from you.)

Go ahead and follow the advice given:
```
sudo dpkg --configure -a
```
and then accept or refuse the MS font EULA when prompted.  That should finish installing all the codecs you need, including libdvdcss2, which is used to play DVDs.  

You will need to run one more command to equip your system to read commercial video DVDs:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

After that, you should be able to watch DVDs to your heart's content, using VLC, or whatever video player you choose.

My problem is that there is no place for me to accept the EULA as I have done with many software packages. Usually you see two boxes, one for accept and one for decline. Totally puzzled by this problem. I have installed VLC already so I still need the AV Codecs.

---

### Post by Peter_Cucchiara on 2013-08-02
> **3rdalbum said:**
> When you get the EULA thing, hit Tab and then the spacebar.

To play DVDs you also need VLC.

Your reply of hitting Tab and then Spacebar worked, enabling me to accept the EULA and finish the download. After executing the other commands I was able to watch a movie using VLC which I had previously downloaded. Many thanks !!!

---

