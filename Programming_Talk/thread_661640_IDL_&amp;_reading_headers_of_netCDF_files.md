---
title: "IDL &amp; reading headers of netCDF files"
date: 2008-01-08
forum: Programming Talk
---

### Post by hoofbeat on 2008-01-08
I'm a 4th year Physics UG trying to get to grips with IDL ready for my
research project involving atmospheric data next term.  I'm trying to
read the header contents of some netCDF files and am at a complete
loss (it doens't help that I have never worked with netCDF files
before and don't know what I'm actually trying to look for!). I have
done some very basic C-Programming before, but am a novice at
programming and have no exerience with UNIX.

I've been using Liam Gumley's book and have read the section on
reading and writing netCDF files but can't get the information I
want.  I've managed to obtain a list of the variables my files
contain, but my supervisors have asked me to use the ncdump -h command
to read what the header is. So here are my problems:

1. I'm a Mac OS X user so have tried during the ncdump - h command in
my terminal but it fails.  I understand this is because I need some
netCDF software on my computer. I tried to download this but got
completely lost in the detailed instructions relating to Unix - it
seemed to imply that I required a C-compiler on my computer for the
installation to work (I don't have a C-compiler) and the files it told
me to use did not exist in the folder I had just downloaded.

2. Is there any way of avoiding UNIX and being able to read the
contents of the header directly in IDL's Development Environment?

3. I have downloaded Panoply ( [http://www.giss.nasa.gov/tools/panoply/](http://www.giss.nasa.gov/tools/panoply/))
which seems to open the netCDF files very easily and provides me with
information about the variables contained and also seems to be able to
plot data onto maps very easily.  Is this essentially doing what the
ncdump - h command does?

If anyone could guide me through a step-by-step guide to downloading
the netCDF software onto my Mac and also letting me know whether I can
do the equivalent command directly in IDLDE I would be very grateful.

Thanks
Chloé

---

### Post by aJayRoo on 2008-01-08
I work with netCDF files of atmospheric and oceanographic mode/observational data. I found it very important to understand a little bit about the format first before attempting to work with it so I would recommend that as a starting point for you (the Wikipedia entry is a fairly good basic overview).  Essentially the header is the part of the netCDF file that describes the rest of the file. It tells you what axes and variables are contained within and their types, units, sizes etc. Basically it tells you everything you could need to know about the actual data contained within the file. Here is an example of a netCDF header:
```
netcdf mslp {
dimensions:
        time0 = UNLIMITED ; // (841 currently)
        z16_msl = 1 ;
        latitude0 = 145 ;
        longitude1 = 192 ;
variables:
        double time0(time0) ;
                time0:units = "days since 1970-01-01 00:00:0" ;
                time0:calendar = "360_day" ;
                time0:axis = "T" ;
        float z16_msl(z16_msl) ;
                z16_msl:units = "" ;
                z16_msl:axis = "Z" ;
        double latitude0(latitude0) ;
                latitude0:point_spacing = "even" ;
                latitude0:standard_name = "latitude" ;
                latitude0:units = "degrees_north" ;
                latitude0:axis = "Y" ;
        float longitude1(longitude1) ;
                longitude1:point_spacing = "even" ;
                longitude1:standard_name = "longitude" ;
                longitude1:axis = "X" ;
                longitude1:units = "degrees_east" ;
                longitude1:modulo = "360.0" ;
                longitude1:topology = "circular" ;
        float p_3(time0, z16_msl, latitude0, longitude1) ;
                p_3:stash_item = 222 ;
                p_3:missing_value = -1.073742e+09f ;
                p_3:stash_model = 1 ;
                p_3:lookup_source = "defaults (cdunifpp V0.8)" ;
                p_3:referrer = "cdat" ;
                p_3:stash_section = 16 ;
                p_3:long_name = "PRESSURE AT MEAN SEA LEVEL" ;
                p_3:cell_methods = "time0: mean" ;
                p_3:units = "Pa" ;
                p_3:name = "p_3" ;
```

Unfortunately I neither own a Mac or an IDL license! Therefore cannot give you any specific advice for reading headers in IDL (I use Matlab/CDAT for my data analysis).
As regards installation of ncdump (netCDF), you might be able to install it via the ports system if that is any easier than compiling from the source code. Again I don't have any experience of this so you would have to search around for yourself a bit.
If the program you downloaded gives you all the information you need about a netCDF file in order to be able to work on it with IDL then you don't need to worry about ncdump.
Also I would imagine you won't be able to do a lot of the work on your Mac anyway unless you are allowed to install IDL on it (unlikely I would have thought). This kind of work is usually done on some kind of central unix/linux server (is that where IDL is run from?) and that might have the netCDF tools already installed.
For example I do all of my work on the central server which I connect to remotely from my Linux workstation.
I hope that helps you a little bit!

---

### Post by hoofbeat on 2008-01-08
Thanks so much - that actually helps quite a lot as the programme I got off the NASA website basically provided me with much of the same information as you've shown me in the code, so hopefully I can use this package to read the header's sufficiently.

> **aJayRoo said:**
> Also I would imagine you won't be able to do a lot of the work on your Mac anyway unless you are allowed to install IDL on it (unlikely I would have thought). This kind of work is usually done on some kind of central unix/linux server (is that where IDL is run from?) and that might have the netCDF tools already installed.
For example I do all of my work on the central server which I connect to remotely from my Linux workstation.
I hope that helps you a little bit!
I've already got IDL installed on my Mac as my Uni had a copy and license of the software to run the IDL Development Environment (IDLDE) for Macs as well as a Windows version and I've been learning the basics on that (how to plot a graph etc).  My supervisors said they were happy to let me use my own laptop so hopefully I can carry on using that (because I don't know anything about UNIX/LINUX), but if not I can always install another operating system on it (I already also run Windows Parallel) but if not I'll just use their  computers in the lab.

Thanks :)

---

### Post by aJayRoo on 2008-01-08
Well, its good to see that you are well prepared for IDL! As long as you are able to find the information you need about the contents of a netCDF file, it doesn't really matter how you get the information. I responded to your post mainly because at the time of reading I was working on a data extracting program (Matlab) and had that ncdump output I posted already on the screen. I like to use ncdump because its probably the quickest way to examine a file. However sometimes I use python (well, CDAT to be more specific) to examine the files in more detail, before writing my analysis code. There are many tools you could use for examining data files, and it really is totally up to you. I'm sure you will soon find out that IDL can do pretty much anything you want it to do! Once you have got to grips with the basics you will start to understand the more complex things like reading and writing netCDF files a lot more quickly and easily. Good luck with your project.

---

