---
title: "SDLMAME v0.108"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by benbruscella on 2006-08-31
Get SDL MAME and unzip it:
[http://rbelmont.mameworld.info/sdlmame0108.zip]("http://rbelmont.mameworld.info/sdlmame0108.zip")

Install compilers:
```
sudo apt-get install build-essential
```

Install zlib development:
```
sudo apt-get install zlib1g-dev
```

Install expat:
```
sudo apt-get install libexpat1-dev
```

Install SDL:
```
sudo apt-get install libsdl1.2-dev
```

Build sdlMAME:
```
make
```

---

### Post by bplus on 2006-09-04
ok i ve run the make and everything completed fine.

does this install xmame? where should it be?

---

### Post by mulperi on 2006-09-05
Usually you install programs with ```
make install
```

This usually installs the binary into /usr/bin 

I prefer to use checkinstall instead of that to get a .deb package that can easily then be installed and deleted using package management. The package manager is also able to show exactly what files belong to which package.

---

### Post by benbruscella on 2006-09-06
OK, that description was a little brief, so here is a little more detail.

SDL MAME doesnt need to be "installed".  It has been designed (beautifully IMHO) to be more like the windows version. :)

When the build has completed, you will see the binary in the root directory called mamepm.  Here is what I see:

```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ls -l makefile
-rw-rw-r-- 1 admin admin 11629 2006-08-12 10:51 makefile
admin@mario:~/Desktop/sdlmame0108$ ls -l mamepm
-rwxr-xr-x 1 admin admin 34416765 2006-08-31 14:56 mamepm

```

The executable that you want to run is mamepm.  Here is the basic usage:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm -help
M.A.M.E. v0.108 (Aug 31 2006) - Multiple Arcade Machine Emulator
Copyright (C) 1997-2006 by Nicola Salmoria and the MAME Team
....

```

To get a basic configuration file, you would do something like this:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm -createconfig
admin@mario:~/Desktop/sdlmame0108$ head mamepm.ini

#
# CONFIGURATION OPTIONS
#
readconfig                1
skip_gameinfo             0

#
# PATH AND DIRECTORY OPTIONS
#

```

So, now it built OK, you need some ROMS to test with!  There are actually some free ones available legally at mame.net.  Be sure to download this as is to the roms subdirectory, so MAME can see them:

```

admin@mario:~/Desktop/sdlmame0108/roms$ pwd
/home/admin/Desktop/sdlmame0108/roms
admin@mario:~/Desktop/sdlmame0108/roms$ wget http://www.mame.net/roms/robby.zip
--15:56:12--  http://www.mame.net/roms/robby.zip
           => `robby.zip'
Resolving www.mame.net... 64.237.35.239
Connecting to www.mame.net|64.237.35.239|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28,175 (28K) [application/zip]

100%[====================================================================================>] 28,175        51.06K/s

15:56:13 (51.00 KB/s) - `robby.zip' saved [28175/28175]

admin@mario:~/Desktop/sdlmame0108/roms$ ls -l
total 28
-rw-r--r-- 1 admin admin 28175 2000-04-19 23:44 robby.zip

```


To run this game fullscreen, you would type:
```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby
Using SDL single-window soft driver (SDL 1.2)

```

To run this game in a window, you would type:
```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -window
Using SDL single-window soft driver (SDL 1.2)

```

The mamepm.ini file has *heaps* of options for you to play with.  Some more information.  If you want to see what MAME is looking for inside the ROM zip file, you would type something like this:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -listroms
This is the list of the ROMs required for driver "robby".
Name            Size Checksum
rotox1.bin      4096 CRC(a431b85a) SHA1(3478da56addba1cdd98cbef7a15b17fca9aed2cd)
rotox2.bin      4096 CRC(33cdda83) SHA1(ccbc741a2fc0b7385ca42afe5b377432249b44cb)
rotox3.bin      4096 CRC(dbf97491) SHA1(11574baf04af02b38ae147be8409de7c34e87611)
rotox4.bin      4096 CRC(a3b90ac8) SHA1(8c585d26011c9ea047895a0388835ff2bb80e1ff)
rotox5.bin      4096 CRC(46ae8a94) SHA1(218edcc5257c9cc58c5e667fff64767b313daaab)
rotox6.bin      4096 CRC(7916b730) SHA1(c5166625a404da4a93a1a7ae21d01fdb6e78680e)
rotox7.bin      4096 CRC(276dc4a5) SHA1(d740b30c28f6a94ee2348291e80d57af5c2e2d99)
rotox8.bin      4096 CRC(1ef13457) SHA1(4dc1ee9ce2a28c4ba75e630fbfe4659cd68d3a66)
rotox9.bin      4096 CRC(370352bf) SHA1(72cd35b4306b46de3d2a3e4e46fa4917ed9d18cb)
rotox10.bin     4096 CRC(e762cbda) SHA1(48c274a859963097a90f80c48366250301eddb5f)

```

And this should be the list of files in the zip:

```

admin@mario:~/Desktop/sdlmame0108$ zipinfo roms/robby.zip
Archive:  roms/robby.zip   28175 bytes   10 files
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox1.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox10.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox2.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox3.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox4.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox5.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox6.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox7.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox8.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox9.bin
10 files, 40960 bytes uncompressed, 26931 bytes compressed:  34.3%

```

If you want to make sure the ROMS are ok, you could do:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -verifyroms
romset robby is good
1 romsets found, 1 were OK.

```

Hope that helps?  Enjoy MAME! :)

---

### Post by marx2k on 2006-11-02
How does one throw a front end on this?

---

### Post by 3dxtrip on 2006-11-03
Sdlanza front-End for linux SDLMAME
[http://it.geocities.com/pinguinogoloso/](http://it.geocities.com/pinguinogoloso/)

---

### Post by NESFreak on 2006-11-21
> **marx2k said:**
> How does one throw a front end on this?

make one yourself:D 
[as i did]("http://www.ubuntuforums.org/showthread.php?t=298084")

NESFreak

---

### Post by loupgarou21 on 2006-11-27
I tried this with sdlmame v.110 and the build failed with error "cannot find -lXinerama." 
I then installed libgtk2.0-dev and sdlmame built just fine.

Just thought someone might like to know if they try it themselves.

[edit]I also found a front end that works well, [Wah!cade.]("http://www.anti-particle.com/wahcade.shtml")  The only goofy part is that after you -createconfig you need to edit the config so it has the full paths to any files/directories you point it to and move it to ~/.mame/. for some reason when launching sdlmame from wah!cade it doesn't use the config file that is actually in the folder with sdlmame

---

### Post by c.falco on 2007-02-26
As posted on the [SDLMame  forum]("http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1"), I uploaded the source package on REVU for reviews.
I hope they will be included in the official universe/multiverse repository in the future. :)

Binary are also available for dapper, edgy and feisty [here]("http://wallyweek.altervista.org").

---

### Post by i23098 on 2007-09-15
0.109 is out :)
AMD64 packages aren't :(

---

### Post by aashay on 2007-11-16
I installed MAME from the .deb packages in the site above. Hovewer, on running mame or sdlmame, i get the following error:

```
mame: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```
Edit: never mind. fixed it

---

### Post by hamsteroid on 2007-11-18
I must try SDL Mame next weekend. Speedwise, how does it compare to Mame in XP?

---

### Post by Moonfrost on 2008-03-02
> **benbruscella said:**
> OK, that description was a little brief, so here is a little more detail.

SDL MAME doesnt need to be "installed".  It has been designed (beautifully IMHO) to be more like the windows version. :)

When the build has completed, you will see the binary in the root directory called mamepm.  Here is what I see:

```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ls -l makefile
-rw-rw-r-- 1 admin admin 11629 2006-08-12 10:51 makefile
admin@mario:~/Desktop/sdlmame0108$ ls -l mamepm
-rwxr-xr-x 1 admin admin 34416765 2006-08-31 14:56 mamepm

```

The executable that you want to run is mamepm.  Here is the basic usage:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm -help
M.A.M.E. v0.108 (Aug 31 2006) - Multiple Arcade Machine Emulator
Copyright (C) 1997-2006 by Nicola Salmoria and the MAME Team
....

```

To get a basic configuration file, you would do something like this:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm -createconfig
admin@mario:~/Desktop/sdlmame0108$ head mamepm.ini

#
# CONFIGURATION OPTIONS
#
readconfig                1
skip_gameinfo             0

#
# PATH AND DIRECTORY OPTIONS
#

```

So, now it built OK, you need some ROMS to test with!  There are actually some free ones available legally at mame.net.  Be sure to download this as is to the roms subdirectory, so MAME can see them:

```

admin@mario:~/Desktop/sdlmame0108/roms$ pwd
/home/admin/Desktop/sdlmame0108/roms
admin@mario:~/Desktop/sdlmame0108/roms$ wget http://www.mame.net/roms/robby.zip
--15:56:12--  http://www.mame.net/roms/robby.zip
           => `robby.zip'
Resolving www.mame.net... 64.237.35.239
Connecting to www.mame.net|64.237.35.239|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28,175 (28K) [application/zip]

100%[====================================================================================>] 28,175        51.06K/s

15:56:13 (51.00 KB/s) - `robby.zip' saved [28175/28175]

admin@mario:~/Desktop/sdlmame0108/roms$ ls -l
total 28
-rw-r--r-- 1 admin admin 28175 2000-04-19 23:44 robby.zip

```


To run this game fullscreen, you would type:
```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby
Using SDL single-window soft driver (SDL 1.2)

```

To run this game in a window, you would type:
```

admin@mario:~/Desktop/sdlmame0108$ pwd
/home/admin/Desktop/sdlmame0108
admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -window
Using SDL single-window soft driver (SDL 1.2)

```

The mamepm.ini file has *heaps* of options for you to play with.  Some more information.  If you want to see what MAME is looking for inside the ROM zip file, you would type something like this:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -listroms
This is the list of the ROMs required for driver "robby".
Name            Size Checksum
rotox1.bin      4096 CRC(a431b85a) SHA1(3478da56addba1cdd98cbef7a15b17fca9aed2cd)
rotox2.bin      4096 CRC(33cdda83) SHA1(ccbc741a2fc0b7385ca42afe5b377432249b44cb)
rotox3.bin      4096 CRC(dbf97491) SHA1(11574baf04af02b38ae147be8409de7c34e87611)
rotox4.bin      4096 CRC(a3b90ac8) SHA1(8c585d26011c9ea047895a0388835ff2bb80e1ff)
rotox5.bin      4096 CRC(46ae8a94) SHA1(218edcc5257c9cc58c5e667fff64767b313daaab)
rotox6.bin      4096 CRC(7916b730) SHA1(c5166625a404da4a93a1a7ae21d01fdb6e78680e)
rotox7.bin      4096 CRC(276dc4a5) SHA1(d740b30c28f6a94ee2348291e80d57af5c2e2d99)
rotox8.bin      4096 CRC(1ef13457) SHA1(4dc1ee9ce2a28c4ba75e630fbfe4659cd68d3a66)
rotox9.bin      4096 CRC(370352bf) SHA1(72cd35b4306b46de3d2a3e4e46fa4917ed9d18cb)
rotox10.bin     4096 CRC(e762cbda) SHA1(48c274a859963097a90f80c48366250301eddb5f)

```

And this should be the list of files in the zip:

```

admin@mario:~/Desktop/sdlmame0108$ zipinfo roms/robby.zip
Archive:  roms/robby.zip   28175 bytes   10 files
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox1.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox10.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox2.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox3.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox4.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox5.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:46 rotox6.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox7.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox8.bin
-rw-a--     2.2 ntf     4096 bx defX 24-Mar-97 17:47 rotox9.bin
10 files, 40960 bytes uncompressed, 26931 bytes compressed:  34.3%

```

If you want to make sure the ROMS are ok, you could do:

```

admin@mario:~/Desktop/sdlmame0108$ ./mamepm robby -verifyroms
romset robby is good
1 romsets found, 1 were OK.

```

Hope that helps?  Enjoy MAME! :)

Well, I know how to run sdlmame...I just need instruction on how should I compile kxmame which is a frontend for sdlmame...

EDIT: SORRY!!!! WRONG THREAD!!!

---

