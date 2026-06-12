---
title: "Cant find/run app i installed(Povray)"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-04
Just installed Povray via the instructions here  [http://www.povray.org/download/linux.php](http://www.povray.org/download/linux.php)  Now i dont know where it is to run it and use the app. It didnt appear anywhere in the applications menue, and i cant find anywhere to run it in the file.

Any help?

---

### Post by jemate18 on 2008-09-04
> **Codemastadink said:**
> Just installed Povray via the instructions here  [http://www.povray.org/download/linux.php](http://www.povray.org/download/linux.php)  Now i dont know where it is to run it and use the app. It didnt appear anywhere in the applications menue, and i cant find anywhere to run it in the file.

Any help?


or type
```
find / -name "povray"
```

or type
```
which povray
```

or type
```
locate povray
```

what are the results?

---

### Post by aloshbennett on 2008-09-04
1. Look under Applications -> Graphics

2. From command prompt, type povray and hit tab like crazy (actually, 2 times would do)

That will list all commands starting with povray. If you find something that sounds like it, run the command from the prompt.

3. cd to ~/povray/povray-3.6 and type > ls -l povray*

If you see a povray or a povrray3.6 or povray.sh file with execute permissions ( the output of the ls command would be -rwx.... something), run that from the command line.

Hope this helps

---

### Post by Codemastadink on 2008-09-04
> **aloshbennett said:**
> 1. Look under Applications -> Graphics

2. From command prompt, type povray and hit tab like crazy (actually, 2 times would do)

That will list all commands starting with povray. If you find something that sounds like it, run the command from the prompt.

3. cd to ~/povray/povray-3.6 and type 

If you see a povray or a povrray3.6 or povray.sh file with execute permissions ( the output of the ls command would be -rwx.... something), run that from the command line.

Hope this helps

#2 just comes up with 

```
cody@cody-laptop:~$ povray
povray
cody@cody-laptop:~$ povray

```

This is what i get for #3 
IDK exactly what to do, i think the first line is what  i need, how do i open it tho?

```
-rwxr-xr-x 1 cody cody 2971828 2004-08-03 09:47 povray
-rw-r--r-- 1 cody cody   19985 2004-08-03 09:18 povray.1
-rw-r--r-- 1 cody cody    4267 2004-08-03 09:18 povray.conf
-rw-r--r-- 1 cody cody    2555 2004-08-03 09:18 povray.ini

```

---

### Post by aloshbennett on 2008-09-04
Cool!
Open a terminal and type 'povray' and hit enter :)

---

### Post by Codemastadink on 2008-09-04
> **aloshbennett said:**
> Cool!
Open a terminal and type 'povray' and hit enter :)

Tried that already, heres what i get

```
cody@cody-laptop:~$ povray
povray: cannot open the user configuration file /home/cody/.povray/3.6/povray.conf: No such file or directory
Persistence of Vision(tm) Ray Tracer Version 3.6.1 (g++ 3.4.1 @
 i686-pc-linux-gnu)
This is an official version prepared by the POV-Ray Team. See the
 documentation on how to contact the authors or visit us on the
 internet at http://www.povray.org/.
POV-Ray is based on DKBTrace 2.12 by David K. Buck & Aaron A. Collins
Copyright 1991-2003 Persistence of Vision Team
Copyright 2003-2004 Persistence of Vision Raytracer Pty. Ltd.

Primary POV-Ray 3.5/3.6 Developers: (Alphabetically)
  Chris Cason         Thorsten Froehlich  Nathan Kopp         Ron Parker        

Contributing Authors: (Alphabetically)
  Steve Anger         Eric Barish         Dieter Bayer        Steve A. Bennett  
  David K. Buck       Nicolas Calimet     Aaron A. Collins    Chris Dailey      
  Steve Demlow        Andreas Dilger      Alexander Enzmann   Dan Farmer        
  Mark Gordon         Christoph Hormann   Mike Hough          Chris Huff        
  Kari Kivisalo       Lutz Kretzschmar    Jochen Lippert      Pascal Massimino  
  Jim McElhiney       Douglas Muir        Juha Nieminen       Bill Pulver       
  Eduard Schwan       Wlodzimierz Skiba   Robert Skinner      Yvo Smellenbergh  
  Zsolt Szalavari     Scott Taylor        Massimo Valentini   Timothy Wegner    
  Drew Wells          Chris Young       

Other contributors are listed in the documentation.

Support libraries used by POV-Ray:
  ZLib 1.2.1, Copyright 1995-1998 Jean-loup Gailly and Mark Adler
  LibPNG 1.2.5, Copyright 1998-2002 Glenn Randers-Pehrson
  LibJPEG 6b, Copyright 1998 Thomas G. Lane
  LibTIFF 3.6.1, Copyright 1988-1997 Sam Leffler, 1991-1997 SGI

Usage: POVRAY [+/-]Option1 [+/-]Option2 ... (-h or -? for help)

  Example: POVRAY scene.ini +Iscene.pov +Oscene.tga +FT +W320 +H200
  Example: POVRAY +Iscene.pov +Oscene.tga +FT +W160 +H200 +V -D +X

The n or n.n (0.n) notation following a command-line option listed
below denotes an integer or a floating-point number, respectively.
Brackets mean that this number is optional.

The help screen is divided into several parts. To access one part
just enter the number of the screen after the -? option or the
-help option.

E.g. use -?5 or -help5 to see the help screen about the tracing
options.

  Number  Part
    1     Parsing Options
    2     Output Options
    3     Output Options - display related
    4     Output Options - file related
    5     Tracing Options
    6     Animation Options
    7     Redirecting Options

Parsing options

  I<name> = input file name
  HI<name>= header include file name
  L<name> = library path prefix
  MVn.n   = set compability to version n.n
  SU      = split bounded unions if children are finite
  UR      = remove unnecessary bounding objects

Output options

  Hn      = image height of n pixels
  Wn      = image width of n pixels

  SRn|0.n = start at row n | start row at n percent of image
  ERn|0.n = end   at row n | end   row at n percent of image
  SCn|0.n = start at col n | start col at n percent of image
  ECn|0.n = end   at col n | end   col at n percent of image

  C       = continue aborted trace
  P       = pause before exit
  V       = verbose messages on
  WLn     = set warning level to n
  X[n]    = enable early exit by key hit (every n pixels)

Output options - display related

  D[xy]   = display rendering (in format x, using palette option y)
  SPn     = display mosaic preview, start grid size = 2, 4, 8, 16, ...
  EPn     = display mosaic preview, end grid size   = 2, 4, 8, 16, ...
  UD      = draw vista rectangles

Output options - file related

  B[n]    = Use buffer (of n KB) for output file
  F[x]    = write output file (in format x)
            FC    - Compressed Targa with 24 or 32 bpp
            FN[n] - PNG (n bits/color, n = 5 to 16, default is 8)
            FP    - PPM
            FS    - System specific
            FT    - Uncompressed Targa with 24 or 32 bpp
  O<name> = output file name

  HTx     = write CPU utilization histogram in format x
            HTC - Comma separated values (CSV - spreadsheet)
            HTN - PNG grayscale
            HTP - PPM heightfield
            HTS - System specific
            HTT - Uncompressed TGA heightfield
            HTX - No histogram output
  HN<name>= histogram filename
  HSx.y   = histogram grid number of x, y divisions

Tracing options

  MB[n]   = use bounding slabs (if more than n objects)
  Qn      = image quality (0 = rough, 9 = full)

  A[0.n]  = perform antialiasing (if color change is above n percent)
  AMn     = use non-adaptive (n=1) or adaptive (n=2) supersampling
  J[n.n]  = set antialiasing-jitter (and amount)
  Rn      = set antialiasing-depth (use n X n rays/pixel)

  UA      = use alpha channel
  UL      = use light buffer
  UV      = use vista buffer

Animation options

  Kn.n    = set frame clock to n.n
  KFIn    = set initial frame number to n
  KFFn    = set final frame number to n
  KIn.n   = set initial clock value to n.n
  KFn.n   = set final clock value to n.n
  SFn|0.n = start subset at frame n | start at n percent in sequence
  EFn|0.n = end subset at frame n | end at n percent in sequence
  KC      = calculate clock value for cyclic animation

  UF      = use field rendering
  UO      = use odd lines in odd frames

Redirecting options

  GI<name>= write all .INI parameters to file name
  Gx<name>= write stream x to console (and/or optional file name)
            GA - All streams (except status)
            GD - Debug stream
            GF - Fatal stream
            GR - Render stream
            GS - Statistics stream
            GW - Warning stream

```

Problem is with this i think at the top.

```
povray: cannot open the user configuration file /home/cody/.povray/3.6/povray.conf: No such file or directory 
```

Maybe its looking in the wrong place? The file is in ```
/home/cody/povray/povray-3.6/povray.conf
```

Do i need to modify where it is looking for this file? I dont even know what the file does or if this is even the problem, just throwing it out here

I do have the file though. Screenshot here of it

---

### Post by aloshbennett on 2008-09-04
well, usually when a program is run for the first time, it wouldnt find the /home/cody/.povray folder as it wouldnt be created yet.

It would then go about creating the folder.  Note the '.' in front of the name which means its a hidden folder.

Open your home folder, hit CTRL H. This would show all the hidden folders. See if the .povray folder is there now.

My guess is that povray application requires some parameters to be passed when it is launched
> Usage: POVRAY [+/-]Option1 [+/-]Option2 ... (-h or -? for help)

  Example: POVRAY scene.ini +Iscene.pov +Oscene.tga +FT +W320 +H200
  Example: POVRAY +Iscene.pov +Oscene.tga +FT +W160 +H200 +V -D +X

Do you know what these options are? Can you try passing these arguments when invoking povray?

PS:
In case you dont find a .povray folder, and that you can confirm by trying> cd ~/.povray/

we can try to trick the program by creating the folder and conf file
> mkdir -p /home/cody/.povray/3.6/
cp /home/cody/povray/3.6/povray.conf /home/cody/.povray/3.6/povray.conf

Theres no guarantee this would work though

---

### Post by AkiraBergman on 2009-02-16
.ini and .conf files also exist in the /etc/povray/3.6/* directory. I just copied them to home/.povray/3.6/* and it stopped the "cannot open the user configuration file" message. I think Povray has a priority protocol in reading them. It still works without the user .conf and .ini files, but with the message. They should have labelled the message a warning. Maybe the creation of these files in the user directory should also be included in the installation of the program.

---

### Post by grj23 on 2010-03-06
Last time I checked, POVray for Linux does not have a GUI like the windows version does.  So if you're expecting that nice thing where you can add template code with pull-down menus, and render with the press of a button, then think again!

Basically you need to make your POVray code in whatever editor you're after.  Then open the terminal at the file and run your povray command there to render it.  That will create the graphics file in the same directory.

Sorry for sketchy reply, but can give more details later if you need them... Post back.

Good luck!

---

