---
title: "HOWTO: Build Audacious media player from SVN!"
date: 2007-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Tine on 2007-04-27
Current version in repos is way outdated and doesn't include the new features!
**Audacious switched to mercurial, and i switched to fedora so this is last update from me to this!**
**SVN Version is not updated anymore so switch to mercurial**
Building audacious from mercurial requires few steps, but after making the right choice and trying, it will be pleasant
to use teh best music-player around :).
It supports many many different filetypes, it has last.fm plugin, OSD-plugin, support for winamp 2.x and xmms skins and much more, give it a try!
Audacious homepage: [http://audacious-media-player.org/]("http://audacious-media-player.org/")

This howto is designed for feisty x86 and gnome. Other users may have to change something.
So let's get started with commands:

Enable universe repos!
For the full install you need to do the following:
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential mercurial subversion autoconf automake1.9 cogito bison gettext
sudo aptitude install libgconf2-dev libgtk2.0-dev libpango1.0-dev libglade2-dev libdbus-1-dev libdbus-glib-1-dev libxcomposite-dev libxrender-dev libxxf86vm-dev libimlib2-dev libglib2.0-dev libsdl1.2-dev libnotify-dev
sudo aptitude install libsamplerate0-dev libpulse-dev libmikmod2-dev libmad0-dev liblircclient-dev libbinio-dev libvorbis-dev libflac-dev libwavpack-dev libsndfile1-dev libtag1-dev libjack0.100.0-dev libsidplay1-dev libasound2-dev libfluidsynth-dev libcurl3-dev libmms-dev liblame-dev libogg-dev libsmpeg-dev libmpcdec-dev mpg123 ladspa-sdk libfaac-dev libadplug-dev

```

Then we need to build libmcs and libmowgli:

```
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmcs-devel libmcs-devel
cd libmcs-devel
sudo ./autogen.sh
./configure --enable-gconf
make
sudo make install
```

```
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmowgli.git
cd libmowgli
sudo ./autogen.sh
./configure
make
sudo make install
```

Then let's grab the program itself and compile it

```
cd ~/Desktop
hg clone http://hg.atheme.org/audacious/trunk audacious-devel
cd audacious-devel
sudo ./autogen.sh
sudo ./configure --enable-samplerate
sudo make
sudo make install
```

Then audacious need audacious-plugins to work:

```
cd ~/Desktop
hg clone http://hg.atheme.org/audacious-plugins/trunk audacious-plugins-devel
cd audacious-plugins-devel
sudo ./autogen.sh
sudo ./configure
sudo make
sudo make install
```

Optionally you can install audacious-plugins-ugly also, these are still using subversion!
```
cd ~/Desktop
svn co http://svn.atheme.org/audacious-plugins/ugly-trunk audacious-plugins-ugly-devel
cd audacious-plugins-ugly-devel
./autogen.sh
./configure 
make
sudo make install

```

After this you can start audacious!

If you download new skin it should be put in: ~/.local/share/audacious/Skins
To use last.fm plugin, enable Audioscrobbler-plugin from properties->Plugins->general
and you will see new menu "Scrobbler".

To update mercurial and build new version if new features came up then,
go to your audacious-devel directory

```
hg pull
hg update
sudo ./configure
make distclean
make
sudo make install
```

then go to your audacious-plugins-devel directory

```
hg pull
hg up
sudo ./configure
make distclean
make
sudo make install
```

To update audacious-plugins-ugly, go to audacious-plugins-ugly directory

```
svn up
sudo ./configure
make distclean
make
sudo make install
```


*NOTICE* "make distclean" command can be left out, but if you're having troubles with new install i suggest try make distclean first and compile again.
If you are updating from very old version and you get some weird error after make, i suggest you remove your audacious-devel and audacious-plugins-devel
and run the commands again to download from svn

No support from me anymore, i ditched ubuntu.
My first how-to btw.

Edit: Mercurial
Edit: added lots of stuff according to Artificial Intelligence's post, thank you!
Edit: added libflac-dev
Edit: added instructions for liblame and liblame0-dev
Edit: added libdbus-glib-1-dev libdbus-1-dev, thanks hexo1125
Edit: Corrected some commands to better way
Edit: Corrected some typos and dependencies, and added gettext to apt-get, thanks sphatiga

---

### Post by sphatiga on 2007-05-01
Hi there thanks for the HOWTO

I had 2 problems with this. 

First in the apt-get with Fiesty I was not able to get "libmad". Not sure what that is for but it doesn't seem like I needed it

Secondly you need to add in "gettext" for the apt-get. Without that people have been having problems compiling. I read a few posts on the Audacious Boards with people running into the same compile error I had. It looked like this 
```
m -f br.gmo && : -c --statistics -o br.gmo br.po
mv: cannot stat `t-br.gmo': No such file or directory
make[2]: *** [br.gmo] Error 1
make[1]: *** [stamp-po] Error 2
make: *** [build] Error 2 
```

So adding in gettext as a dependancy fixes that compile error. After that I was able to get the 1.3.2 version up and running. 

As a side note, I downloaded directly from the Audacious site the official stable 1.3.2 release and 1.3.3 plugins. I didn't go thru the SVN dev releases as I was having some issues with the autogen.sh files, and plus I rather just use the stable releases than the dev release.

Thanks again for the HOWTO

---

### Post by Tine on 2007-05-04
Ok, it seems there were few typos. 
Like libmad, when it should have been libmad0 ...
sh autogen.sh didn't work because there were automake missing from apt-get command line. It should work after installing that (correct now in first post).

Please try this howto so we can make in perfect!

---

### Post by hsmwrv on 2007-05-12
I got this error.

```
Configuration:

  Install path:                           /usr/local
  Current Audacious executable:           /usr/local/bin/audacious
  Legacy configuration path:              $HOME/.audacious

  Use one plugin dir:                     no
  Allow user plugin dir:                  yes

  Automatic character code detection:     yes
  Sample rate upconversion:               no
  D-Bus support:                          no

#:~/libmcs-devel/libmowgli/audacious-devel$ sudo make
[generating dependencies for objective: guess.c]
[generating dependencies for objective: librcd.c]
[generating dependencies for objective: widget.c]
[generating dependencies for objective: sbutton.c]
[generating dependencies for objective: pbutton.c]
[generating dependencies for objective: tbutton.c]
[generating dependencies for objective: textbox.c]
[generating dependencies for objective: hslider.c]
[generating dependencies for objective: menurow.c]
[generating dependencies for objective: monostereo.c]
[generating dependencies for objective: vis.c]
[generating dependencies for objective: svis.c]
[generating dependencies for objective: number.c]
[generating dependencies for objective: playstatus.c]
[generating dependencies for objective: playlist_list.c]
[generating dependencies for objective: playlist_slider.c]
[generating dependencies for objective: eq_graph.c]
[generating dependencies for objective: eq_slider.c]
[generating dependencies for objective: skin.c]
[generating dependencies for objective: auddrct.c]
[generating dependencies for objective: build_stamp.c]
[generating dependencies for objective: configdb.c]
[generating dependencies for objective: dnd.c]
[generating dependencies for objective: dock.c]
[generating dependencies for objective: effect.c]
[generating dependencies for objective: fft.c]
[generating dependencies for objective: formatter.c]
[generating dependencies for objective: general.c]
[generating dependencies for objective: genevent.c]
[generating dependencies for objective: glade.c]
[generating dependencies for objective: hints.c]
[generating dependencies for objective: hook.c]
[generating dependencies for objective: iir.c]
[generating dependencies for objective: iir_cfs.c]
[generating dependencies for objective: iir_fpu.c]
[generating dependencies for objective: input.c]
[generating dependencies for objective: logger.c]
[generating dependencies for objective: main.c]
[generating dependencies for objective: memorypool.c]
[generating dependencies for objective: output.c]
[generating dependencies for objective: pixbuf_effects.c]
[generating dependencies for objective: playback.c]
[generating dependencies for objective: playlist.c]
[generating dependencies for objective: playlist_container.c]
[generating dependencies for objective: pluginenum.c]
[generating dependencies for objective: rcfile.c]
[generating dependencies for objective: signals.c]
[generating dependencies for objective: strings.c]
[generating dependencies for objective: titlestring.c]
[generating dependencies for objective: ui_about.c]
[generating dependencies for objective: ui_albumart.c]
[generating dependencies for objective: ui_credits.c]
[generating dependencies for objective: ui_equalizer.c]
[generating dependencies for objective: ui_fileinfo.c]
[generating dependencies for objective: ui_fileinfopopup.c]
[generating dependencies for objective: ui_fileopener.c]
[generating dependencies for objective: ui_jumptotrack.c]
[generating dependencies for objective: ui_main.c]
[generating dependencies for objective: ui_manager.c]
[generating dependencies for objective: ui_playlist.c]
[generating dependencies for objective: ui_playlist_manager.c]
[generating dependencies for objective: ui_preferences.c]
[generating dependencies for objective: ui_skinned_cursor.c]
[generating dependencies for objective: ui_skinned_window.c]
[generating dependencies for objective: ui_skinselector.c]
[generating dependencies for objective: ui_urlopener.c]
[generating dependencies for objective: urldecode.c]
[generating dependencies for objective: util.c]
[generating dependencies for objective: vfs.c]
[generating dependencies for objective: vfs_buffer.c]
[generating dependencies for objective: vfs_buffered_file.c]
[generating dependencies for objective: vfs_common.c]
[generating dependencies for objective: visualization.c]
[generating dependencies for objective: xconvert.c]
[generating dependencies for objective: compat.c]
[generating dependencies for objective: debug.c]
[generating dependencies for objective: file.c]
[generating dependencies for objective: frametype.c]
[generating dependencies for objective: latin1.c]
[generating dependencies for objective: render.c]
[generating dependencies for objective: ucs4.c]
[generating dependencies for objective: utf8.c]
[generating dependencies for objective: version.c]
[generating dependencies for objective: crc.c]
[generating dependencies for objective: field.c]
[generating dependencies for objective: frame.c]
[generating dependencies for objective: genre.c]
[generating dependencies for objective: parse.c]
[generating dependencies for objective: tag.c]
[generating dependencies for objective: utf16.c]
[generating dependencies for objective: util.c]
        CC     guess.c             
      LINK     libguess.a          
        CC     librcd.c            
      LINK     librcd.a            
        CC     widget.c            
        CC     sbutton.c           
        CC     pbutton.c           
        CC     tbutton.c           
        CC     textbox.c           
        CC     hslider.c           
        CC     menurow.c           
        CC     monostereo.c        
        CC     vis.c               
        CC     svis.c              
        CC     number.c            
        CC     playstatus.c        
        CC     playlist_list.c     
        CC     playlist_slider.c   
        CC     eq_graph.c          
        CC     eq_slider.c         
        CC     skin.c              
      LINK     libwidgets.a        
        CC     auddrct.c           
        CC     build_stamp.c       
        CC     configdb.c          
        CC     dnd.c               
        CC     dock.c              
        CC     effect.c            
        CC     fft.c               
        CC     formatter.c         
        CC     general.c           
        CC     genevent.c          
        CC     glade.c             
        CC     hints.c             
        CC     hook.c              
        CC     iir.c               
        CC     iir_cfs.c           
        CC     iir_fpu.c           
        CC     input.c             
        CC     logger.c            
        CC     main.c              
main.c: In function ‘handle_cmd_line_options’:
main.c:898: warning: unused variable ‘filenames’
        CC     memorypool.c        
        CC     output.c            
        CC     pixbuf_effects.c    
        CC     playback.c          
        CC     playlist.c          
        CC     playlist_container.c
        CC     pluginenum.c        
        CC     rcfile.c            
        CC     signals.c           
        CC     strings.c           
        CC     titlestring.c       
        CC     ui_about.c          
        CC     ui_albumart.c       
        CC     ui_credits.c        
        CC     ui_equalizer.c      
        CC     ui_fileinfo.c       
        CC     ui_fileinfopopup.c  
        CC     ui_fileopener.c     
        CC     ui_jumptotrack.c    
        CC     ui_main.c           
        CC     ui_manager.c        
        CC     ui_playlist.c       
        CC     ui_playlist_manager.c
        CC     ui_preferences.c    
        CC     ui_skinned_cursor.c 
        CC     ui_skinned_window.c 
        CC     ui_skinselector.c   
        CC     ui_urlopener.c      
        CC     urldecode.c         
        CC     util.c              
        CC     vfs.c               
        CC     vfs_buffer.c        
        CC     vfs_buffered_file.c 
        CC     vfs_common.c        
        CC     visualization.c     
        CC     xconvert.c          
/usr/bin/ld: cannot find -laudclient
collect2: ld returned 1 exit status
make[3]: *** [audacious] Error 1
make[2]: *** [build] Error 2
make[1]: *** [build] Error 2
make: *** [build] Error 2

```

---

### Post by Tine on 2007-05-12
hsmwrv,
that error should have been fixed in latest svn version.
so follow my instructions in first post how to update from svn and try again

-Tine

---

### Post by hsmwrv on 2007-05-13
> **Tine said:**
> hsmwrv,
that error should have been fixed in latest svn version.
so follow my instructions in first post how to update from svn and try again

-Tine

I did follow the first post by copying and pasting all the codes.  I've tried again and still got the same error.  What else might I have missed?

---

### Post by Tine on 2007-05-13
Weird indeed.
Maybe you try this:
go to audacious-devel directory, then try this:

```

sudo svn up -r 4442
sudo make distclean
sudo sh autogen.sh
sudo ./configure
sudo make
sudo make install

```

---

### Post by hexo1125 on 2007-05-13
I had the same problem with latest version...

but label 4442 works

---

### Post by Tine on 2007-05-13
*deleted*

---

### Post by Tine on 2007-05-13
Latest SVN should work now

---

### Post by hexo1125 on 2007-05-13
yup, revision 4442 works
I was stupid and didn't copy and paste your code, accidentally got revision 4444

Thanks!

EDIT: nevermind

---

### Post by Next.Step on 2007-05-13
Everytime I start Audacious I get this:

```

audacious: error while loading shared libraries: libaudacious.so.5: cannot open shared object file: No such file or directory

```

What should I do?

---

### Post by Tine on 2007-05-13
laudclient error has been fixed in latest SVN!

If you are updating from 4442 then do the following to get the latest!

```

sudo rm -rf audacious-devel
svn co http://svn.atheme.org/audacious/trunk audacious-devel
cd audacious-devel
sudo sh autogen.sh
sudo ./configure
sudo make
sudo make install

```

---

### Post by Tine on 2007-05-13
> **Next.Step said:**
> Everytime I start Audacious I get this:

```

audacious: error while loading shared libraries: libaudacious.so.5: cannot open shared object file: No such file or directory

```

What should I do?

Are you sure you did
```

sudo make install

```
when needed?

---

### Post by hexo1125 on 2007-05-13
I did an svn update and the latest version of audacious works...


For the plugins, if anyone has a problem at ./configure complaining about dbus_glib install the libdbus-glib-1-dev package.

I'm still stuck though, at
```

        CC     mp3.c               
mp3.c:25:23: error: lame/lame.h: No such file or directory
mp3.c:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mp3.c: In function ‘mp3_open’:
mp3.c:193: error: ‘gfp’ undeclared (first use in this function)
mp3.c:193: error: (Each undeclared identifier is reported only once
mp3.c:193: error: for each function it appears in.)
mp3.c:193: warning: implicit declaration of function ‘lame_init’
mp3.c:197: warning: implicit declaration of function ‘id3tag_init’
mp3.c:205: warning: implicit declaration of function ‘id3tag_set_title’
mp3.c:208: warning: implicit declaration of function ‘id3tag_set_artist’
mp3.c:211: warning: implicit declaration of function ‘id3tag_set_album’
mp3.c:214: warning: implicit declaration of function ‘id3tag_set_genre’
mp3.c:217: warning: implicit declaration of function ‘id3tag_set_year’
mp3.c:220: warning: implicit declaration of function ‘id3tag_set_track’
mp3.c:223: warning: implicit declaration of function ‘id3tag_add_v2’
mp3.c:228: warning: implicit declaration of function ‘lame_set_in_samplerate’
mp3.c:229: warning: implicit declaration of function ‘lame_set_num_channels’
mp3.c:232: warning: implicit declaration of function ‘lame_set_out_samplerate’
mp3.c:236: warning: implicit declaration of function ‘lame_set_bWriteVbrTag’
mp3.c:237: warning: implicit declaration of function ‘lame_set_quality’
mp3.c:242: warning: implicit declaration of function ‘lame_set_mode’
mp3.c:245: warning: implicit declaration of function ‘lame_set_mode_automs’
mp3.c:247: warning: implicit declaration of function ‘lame_set_errorf’
mp3.c:248: warning: implicit declaration of function ‘lame_set_debugf’
mp3.c:249: warning: implicit declaration of function ‘lame_set_msgf’
mp3.c:252: warning: implicit declaration of function ‘lame_set_brate’
mp3.c:254: warning: implicit declaration of function ‘lame_set_compression_ratio’
mp3.c:258: warning: implicit declaration of function ‘lame_set_copyright’
mp3.c:259: warning: implicit declaration of function ‘lame_set_original’
mp3.c:260: warning: implicit declaration of function ‘lame_set_error_protection’
mp3.c:261: warning: implicit declaration of function ‘lame_set_strict_ISO’
mp3.c:265: warning: implicit declaration of function ‘lame_set_VBR’
mp3.c:268: warning: implicit declaration of function ‘lame_set_VBR_q’
mp3.c:269: warning: implicit declaration of function ‘lame_set_VBR_mean_bitrate_kbps’
mp3.c:270: warning: implicit declaration of function ‘lame_set_VBR_min_bitrate_kbps’
mp3.c:271: warning: implicit declaration of function ‘lame_set_VBR_max_bitrate_kbps’
mp3.c:272: warning: implicit declaration of function ‘lame_set_VBR_hard_min’
mp3.c:275: warning: implicit declaration of function ‘lame_init_params’
mp3.c: In function ‘mp3_write’:
mp3.c:285: warning: implicit declaration of function ‘lame_encode_buffer’
mp3.c:285: error: ‘gfp’ undeclared (first use in this function)
mp3.c:290: warning: implicit declaration of function ‘lame_encode_buffer_interleaved’
mp3.c: In function ‘mp3_close’:
mp3.c:303: warning: implicit declaration of function ‘lame_encode_flush_nogap’
mp3.c:303: error: ‘gfp’ undeclared (first use in this function)
mp3.c:308: warning: implicit declaration of function ‘lame_close’
make[3]: *** [mp3.o] Error 1
make[2]: *** [build] Error 2
make[1]: *** [build] Error 2
make: *** [build] Error 2

```

---

### Post by Tine on 2007-05-13
hexo1125:
maybe you need liblame0 & liblame-dev ?

you can get them doing the following if you're on feisty
```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -
deb http://seveas.imbrandon.com feisty-seveas all
sudo apt-get update
sudo apt-get install liblame0 liblame-dev

```

if not feisty, then read first post, i added information!

and thanks for the info for libdbus-glib-1-dev package!

---

### Post by hexo1125 on 2007-05-13
thanks, lame problem solved

another one though, flac error
```

      LINK     libfilewriter.so    
/usr/bin/ld: cannot find -lFLAC
collect2: ld returned 1 exit status
make[3]: *** [libfilewriter.so] Error 1
make[2]: *** [build] Error 2
make[1]: *** [build] Error 2
make: *** [build] Error 2

```

solution:
```
sudo apt-get install libflac++-dev
```


... and now that I installed the new audacious and plugins...
here comes the worst, I can't add any song to the playlist it seems... so I can't play any of my mp3s.

no idea what's wrong

---

### Post by Tine on 2007-05-13
hexo1125, never experienced that before so i'm kinda helpless.
Maybe try using "Use XMMS-style file selector..."
that option can be found in options->appearance

---

### Post by Perfect Storm on 2007-05-13
It's happen when using SVN versions, it's for testing and things breaks, so just be patience until they fix it.

By the way, here's a full fix for your howto, with this all plugins and options will be available in audacious;
(tested on Feisty x86)


sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential subversion autoconf automake1.9 cogito bison 
sudo aptitude install libgconf2-dev libgtk2.0-dev libpango1.0-dev libglade2-dev libdbus-1-dev libdbus-glib-1-dev libxcomposite-dev libxrender-dev libxxf86vm-dev libimlib2-dev libglib2.0-dev libsdl1.2-dev libnotify-dev
sudo aptitude install libsamplerate0-dev libpulse-dev libmikmod2-dev libmad0-dev liblircclient-dev libbinio-dev libvorbis-dev libflac-dev libwavpack-dev libsndfile1-dev libtag1-dev libjack0.100.0-dev libsidplay1-dev libasound2-dev libfluidsynth-dev libcurl3-dev libmms-dev liblame-dev libogg-dev libsmpeg-dev libmpcdec-dev mpg123 ladspa-sdk libfaac-dev libadplug-dev



libmcs
-------------------
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmcs-devel libmcs-devel
cd libmcs-devel
./autogen.sh
./configure --enable-gconf
make
sudo make install


libMowgli
-----------------
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmowgli.git
cd libmowgli
./autogen.sh
./configure
make
sudo make install


Audacious
-----------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious/trunk](http://svn.atheme.org/audacious/trunk) audacious-devel
cd audacious-devel
./autogen.sh
./configure --enable-samplerate
make
sudo make install


Audacious Plugin
------------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious-plugins/trunk](http://svn.atheme.org/audacious-plugins/trunk) audacious-plugins-devel
cd audacious-plugins-devel
./autogen.sh
./configure
make
sudo make install


Audacious Ugly-plugin
--------------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious-plugins/ugly-trunk](http://svn.atheme.org/audacious-plugins/ugly-trunk) audacious-plugins-ugly-devel
./autogen.sh
./configure 
make
sudo make install



For those who want stable audacious 1.3.2 add the following to sourcelist:
[b]#### Morgoth Feisty Backports ####
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main[/b]

works both for edgy and feisty  - arch x86

[[img]http://www.imageviper.com/displayimage/79713/0/Audacious-v1.3.2-pre.png[/img]](http://www.imageviper.com/displayimage/79711/0/Audacious-v1.3.2.png)
*click to enlarge*

---

### Post by hexo1125 on 2007-05-13
I tried your suggestion and it still doesn't work.
I don't think it's the file selector problem.

The song I "add" just doesn't seem to register on the playlist.

I also tried loading from an old list (playlist.xspf) the songs are listed, but they just don't play.

Thanks for your help btw...

---

### Post by Perfect Storm on 2007-05-13
> **Artificial Intelligence said:**
> It's happen when using SVN versions, it's for testing and things breaks, so just be patience until they fix it.

By the way, here's a full fix for your howto, with this all plugins and options will be available in audacious;
(tested on Feisty x86 geared towards gnome).


sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential subversion autoconf automake1.9 cogito bison 
sudo aptitude install libgconf2-dev libgtk2.0-dev libpango1.0-dev libglade2-dev libdbus-1-dev libdbus-glib-1-dev libxcomposite-dev libxrender-dev libxxf86vm-dev libimlib2-dev libglib2.0-dev libsdl1.2-dev libnotify-dev
sudo aptitude install libsamplerate0-dev libpulse-dev libmikmod2-dev libmad0-dev liblircclient-dev libbinio-dev libvorbis-dev libflac-dev libwavpack-dev libsndfile1-dev libtag1-dev libjack0.100.0-dev libsidplay1-dev libasound2-dev libfluidsynth-dev libcurl3-dev libmms-dev liblame-dev libogg-dev libsmpeg-dev libmpcdec-dev mpg123 ladspa-sdk libfaac-dev libadplug-dev



libmcs
-------------------
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmcs-devel libmcs-devel
cd libmcs-devel
./autogen.sh
./configure --enable-gconf
make
sudo make install


libMowgli
-----------------
cd ~/Desktop
cg-clone git://git.atheme.org/gitroot/libmowgli.git
cd libmowgli
./autogen.sh
./configure
make
sudo make install


Audacious
-----------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious/trunk](http://svn.atheme.org/audacious/trunk) audacious-devel
cd audacious-devel
./autogen.sh
./configure --enable-samplerate
make
sudo make install


Audacious Plugin
------------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious-plugins/trunk](http://svn.atheme.org/audacious-plugins/trunk) audacious-plugins-devel
cd audacious-plugins-devel
./autogen.sh
./configure
make
sudo make install


Audacious Ugly-plugin
--------------------
cd ~/Desktop
svn co [http://svn.atheme.org/audacious-plugins/ugly-trunk](http://svn.atheme.org/audacious-plugins/ugly-trunk) audacious-plugins-ugly-devel
./autogen.sh
./configure 
make
sudo make install


For those who want stable audacious 1.3.2 add the following to sourcelist:
[b]#### Morgoth Feisty Backports ####
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main[/b]

works both for edgy and feisty  - arch x86

---

### Post by hexo1125 on 2007-05-13
> **Artificial Intelligence said:**
> For those who want stable audacious 1.3.2 add the following to sourcelist:
[b]#### Morgoth Feisty Backports ####
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main[/b]

works both for edgy and feisty  - arch x86

GPG Key
```
wget -O - http://morgoth.free.fr/files/morgoth-signkey.gpg.asc | sudo apt-key add -
```

---

### Post by Tine on 2007-05-13
> **Artificial Intelligence said:**
> 
...

By the way, here's a full fix for your howto, with this all plugins and options will be available in audacious;
(tested on Feisty x86)
...


Thank you, i updated the first post according to your information!

---

### Post by Tine on 2007-05-13
hexo1125,
Are you sure you have libmad0-dev ?
You may need libmad0 also, not sure

---

### Post by Perfect Storm on 2007-05-13
By the way what I wrote earlier is aimed towards gnome, so KDE and Enlightenment should make some minor changes.

---

### Post by hexo1125 on 2007-05-13
Tine, thanks for your help.

I have the latest version of libmad0-dev already. BTW I'm running Xubuntu, if it matters.

It still doesn't work on my comp, altho everything seem to have compiled and installed properly.
I even tried the deb source Artificial Intelligence mentioned, and have the same result.

I think it's just my comp being weird.

I've had enough for now. I'll work on it again sometime later.

Thanks for the howto!!

---

### Post by Perfect Storm on 2007-05-13
Another option (which I prefer) - Download the stable source from their homepage: [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads)
just follow the guide but leave out the autogen stuff as it not needed there. 
I'm not sure with XFCE, but leave out the --enable-gconf flag

---

### Post by hsmwrv on 2007-05-14
> **Tine said:**
> Weird indeed.
Maybe you try this:
go to audacious-devel directory, then try this:

```

sudo svn up -r 4442
sudo make distclean
sudo sh autogen.sh
sudo ./configure
sudo make
sudo make install

```

I got it.  Thanks Tine!

I was stuck at the code for audacious-plugins-ugly until I added the following line(begins with "***"):
```
cd ~/Desktop
svn co http://svn.atheme.org/audacious-plugins/ugly-trunk audacious-plugins-ugly-devel
***cd Desktop/audacious-plugins-ugly-devel
./autogen.sh
./configure 
make
sudo make install/
```

---

### Post by hexo1125 on 2007-05-14
I gave up and downgraded back to the one in ubuntu repository. hahaha

BTW, how come I can't find the change log online?
What's new in the recent versions?

---

### Post by Tine on 2007-05-14
hexo1125, must have been tough call after all the hustle.

Here are the Changelogs:
[http://svn.atheme.org/audacious/trunk/ChangeLog]("http://svn.atheme.org/audacious/trunk/ChangeLog")
[http://svn.atheme.org/audacious-plugins/trunk/ChangeLog]("http://svn.atheme.org/audacious-plugins/trunk/ChangeLog")
[http://svn.atheme.org/audacious-plugins/ugly-trunk/ChangeLog]("http://svn.atheme.org/audacious-plugins/ugly-trunk/ChangeLog")

---

### Post by Tine on 2007-05-14
> **hsmwrv said:**
> I got it.  Thanks Tine!

I was stuck at the code for audacious-plugins-ugly until I added the following line(begins with "***"):
```
cd ~/Desktop
svn co http://svn.atheme.org/audacious-plugins/ugly-trunk audacious-plugins-ugly-devel
***cd Desktop/audacious-plugins-ugly-devel
./autogen.sh
./configure 
make
sudo make install/
```

thanks, i added that line it to first post now.

---

### Post by 3dxtrip on 2007-05-21
Works fine!

But, how can i create deb packages from SVN?

Thanks

---

### Post by el_itur on 2007-05-24
Well firstly thanks for the tips, I could compile audacious and dependencies without a problem. Still I can't run it. BAh, It runs but doesn't play anything, it just fades and crashes without a sign, even on the console I've got no output of whats going on.

Any clue on how can I work around it?

Edit: Just restarted and everything runs just fine.
Edit 2: any hint about scrobler? how do I listen to last.fm?

---

### Post by Dale Cooper on 2007-05-30
Hi peeps,
I've followed this excellent how-to and all works well except that I can't use pulseaudio as the output... It doesn't even appear in the output list. However the pulse plugin has been compiled and installed normally. I have libpulse-dev installed, and i can find the libpulse.so on my system...
Any suggestion?
Thanks in advance

---

### Post by mimihu88 on 2007-06-05
How to uninstall the audacious which install by the way of "make install" ?

---

### Post by Dale Cooper on 2007-06-05
> **mimihu88 said:**
> How to uninstall the audacious which install by the way of "make install" ?

there's no rule for "make uninstall"...

i did it the boring way :
locate audacious
then rm -rf them one by one

have fun :)

---

### Post by NoVista on 2007-06-11
ahh

---

### Post by saygin on 2007-06-11
thanks a lot! I've tried to compile it before but I couldn't do it. Now, except plugins-ugly, everything works great! thanks again...

---

### Post by NoVista on 2007-06-13
Ok, I have a non working after effect. This may have been caused by an earlier install of audacious.

When I right click on a playable mp3 file, and select audacious as the prog to open with, it won't bring up the player. Nothing happens. Also, it is listed twice here!

Bringing up the prog on it's own and selecting a file always works.

Where can I edit the right click menu, and correct this?

---

### Post by 3dxtrip on 2007-06-17
libpulse don't work for me too

> Ok, I have a non working after effect. This may have been caused by an earlier install of audacious.

When I right click on a playable mp3 file, and select audacious as the prog to open with, it won't bring up the player. Nothing happens. Also, it is listed twice here!

Bringing up the prog on it's own and selecting a file always works.

Where can I edit the right click menu, and correct this?

I have the same problem

Seems a bug of devel source, anyway you can report in:
[http://bugs-meta.atheme.org/](http://bugs-meta.atheme.org/)

---

### Post by 3dxtrip on 2007-06-18
For update source code from mercurial you must:

in you directory

First
> hg pull

Second
> hg update

---

### Post by tombug on 2007-06-21
```
tom@spaz:~/Desktop$ hg clone http://svn.atheme.org/audacious/trunk audacious-devel
real URL is http://svn.atheme.org/audacious/trunk/
abort: 'http://svn.atheme.org/audacious/trunk/' does not appear to be an hg repository!
```

just go to [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads) and download it and same thing for the plugins

---

### Post by cb474 on 2007-07-31
I'm sure this is a very obvious question. I followed the how-to. I didn't get any errors. But now where is Audacious? How do I run it?

---

### Post by NoVista on 2007-07-31
It should have installed a link for it in the main menu, under Sound and Video.

To make sure it did install right, simply typing  'audacious'  in the terminal will bring it up.

---

### Post by cb474 on 2007-07-31
hmm. i guess it did not install correctly. there's not a link and nothing comes up when i type "audacious" in the terminal.

if it's not showing up, do i need to uninstall it (and how?) before trying again?

---

### Post by Theimon on 2007-07-31
> **cb474 said:**
> hmm. i guess it did not install correctly. there's not a link and nothing comes up when i type "audacious" in the terminal.

if it's not showing up, do i need to uninstall it (and how?) before trying again?

Well, you can't really. Only thing to do is start from scratch. Follow the how-to step by step, but when you configure something, it doesn't hurt to check for errors or missing libs when it's done.
When you got missing libs, install those anyway and do ./configure again. When you think you got it go for make and make install.

I followed the how-to as well. had some errors in ./configure in both plugin "sections". I can't remember which tho, but with a terminal in one hand and Synaptic in the other I managed to get it right. Whenever it missed something, I just looked it up in Synaptic.

---

### Post by ariel on 2009-03-08
This post needs some updating.

libmcs and libmowgli are now included in ubuntu (8.10); libmcs-dev and libmowgli can be installed with apt-get.

Also plugins-ugly in audacious is no longer in svn, it is now in mercurial (hg clone ...) as the main audacious app.

---

