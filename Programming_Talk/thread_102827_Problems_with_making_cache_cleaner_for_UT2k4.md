---
title: "Problems with making cache cleaner for UT2k4"
date: 2005-12-12
forum: Programming Talk
---

### Post by BLTicklemonster on 2005-12-12
Okay, I'm a total noob, so be easy on me. 

I play UT, and couldn't find a cache cleaner for UT so that files downloaded from a server in the /Cache folder as *.uxx could be referenced against a cache.ini file with the correct names and extensions listed so that they could be correctly named and moved to their respective folders, so I asked at UnrealAdmin.org for help, and ~V~ gave me this nice tidbit:

```
#!/bin/bash
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ] ; then
{
export utdir="/home/bill/ut/" # change this to your main UT folder
gawk -F= ' 
utdir = "${utdir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " utdir targ substr($2, 1, length($2)-1) | "sh";
}
{
if(match($2,".unr")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".umx")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
}
END { close("sh") }' cache.ini
rm *.uxx cache.ini
}
fi;
if [ -f $utdir"System/De.u" ]; then rm $utdir"System/De.u" ;fi  
if [ -f $utdir"System/de.u" ]; then rm $utdir"System/de.u" ;fi
#if [ -f $utdir"System/den_p1p0-Hack.u" ]; then rm $utdir"System/den_p1p0-Hack.u" ;fi
# end script

```

which when chmod +x filename from the terminal works great.

So I thought I'd try it with 2k4. Slightly different setup, but I edited the file to this:

```
#!/bin/bash
cd ~/.ut2004/Cache || exit 1 # change this to your ut2004 user dir
if [ -f cache.ini ] ; then
{
export ut2004dir="/home/bill/ut2004/" # change this to your main ut2004 folder
gawk -F= ' 
ut2004dir = "${ut2004dir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " ut2004dir targ substr($2, 1, length($2)-1) | "sh";
}
{
if(match($2,".ut2")) moveit("/Maps/");
else if(match($2,".utx")) moveit("/Textures/");
else if(match($2,".uax")) moveit("/Sounds/");
else if(match($2,".ogg")) moveit("/Music/");
else if(match($2,".u")) moveit("/System/");
else if(match($2,".usx")) moveit("/StaticMeshes/");
else if(match($2,".ukx")) moveit("/Animations/");
}
END { close("sh") }' cache.ini
#rm *.uxx cache.ini
}
fi;
#if [ -f $utdir"System/De.u" ]; then rm $utdir"System/De.u" ;fi  
#if [ -f $utdir"System/de.u" ]; then rm $utdir"System/de.u" ;fi
#if [ -f $utdir"System/den_p1p0-Hack.u" ]; then rm $utdir"System/den_p1p0-Hack.u" ;fi
# end script

```

I have put everything the way it is, there's no .loki folder, it's .ut2004, and I'm sure it's okay pathwise, because when I run it, sure enough, it takes everything and puts it in it's respective folders, except that it does this:

```
bill@ubuntu:~$ ./2k4cleaner
[Cache]
75E688FF467F6B5B98DDBA9AF0BDAE77-1=ONSNewTank-A.ukx
737B4F0A4A301A836D3EED875526052A-7=OnslaughtBP.u
AD99272845FD0FF995A8E7ACDB5550E6-1=ONSBPTextures.utx
5DA978E541043C5A7AEE378D8FAD8DC8-1=AW-2k4XP.utx
5C383E264A56472FCA40569AA3C83194-1=ONSBP_DestroyedVehicles.utx
93B8BE7744133BBBDD06FD99F5947439-1=ONSBPSounds.uax
A08F92FB4D7CD27EB15634BB0FDBB026-1=CicadaTex.utx
1161EFC840336F04BE6022B7B5D26B4B-1=ONS-BPJW1.usx
438364044447D49F85EBF19C09F9EE8F-1=BonusParticles.utx
60ACA38C4F1918C535075C9060742C6C-1=ONSBPAnimations.ukx
79B289B84758C0F5E4A65EB3DCDDDA5B-1=CicadaSnds.uax
0EF69B434315EA66ECB7739013E67A50-1=DistantBooms.uax

`75E688FF467F6B5B98DDBA9AF0BDAE77-1.uxx' -> `/home/bill/ut2004//System/ONSNewTank-A.uk'
`737B4F0A4A301A836D3EED875526052A-7.uxx' -> `/home/bill/ut2004//System/OnslaughtBP.'
`AD99272845FD0FF995A8E7ACDB5550E6-1.uxx' -> `/home/bill/ut2004//Textures/ONSBPTextures.ut'
`5DA978E541043C5A7AEE378D8FAD8DC8-1.uxx' -> `/home/bill/ut2004//Textures/AW-2k4XP.ut'
`5C383E264A56472FCA40569AA3C83194-1.uxx' -> `/home/bill/ut2004//Textures/ONSBP_DestroyedVehicles.ut'
`93B8BE7744133BBBDD06FD99F5947439-1.uxx' -> `/home/bill/ut2004//Sounds/ONSBPSounds.ua'
`A08F92FB4D7CD27EB15634BB0FDBB026-1.uxx' -> `/home/bill/ut2004//Textures/CicadaTex.ut'
`1161EFC840336F04BE6022B7B5D26B4B-1.uxx' -> `/home/bill/ut2004//System/ONS-BPJW1.us'
`438364044447D49F85EBF19C09F9EE8F-1.uxx' -> `/home/bill/ut2004//Textures/BonusParticles.ut'
`60ACA38C4F1918C535075C9060742C6C-1.uxx' -> `/home/bill/ut2004//System/ONSBPAnimations.uk'
`79B289B84758C0F5E4A65EB3DCDDDA5B-1.uxx' -> `/home/bill/ut2004//Sounds/CicadaSnds.ua'
`0EF69B434315EA66ECB7739013E67A50-1.uxx' -> `/home/bill/ut2004//Sounds/DistantBooms.ua'
bill@ubuntu:~$

```

Reference the top portion with what it says it put in the directories. It leaves stuff off. UTX files are now UT files, UAX files are now UA, etc. Can anyone see anything wrong with the code that would make it lose the final letter off the extension? It works okay in ut, and the extensions in it are 3 letter extensions. I don't get it.

Ideas?

---

### Post by toojays on 2005-12-13
In the moveit function, there is "length($2)-1". That's the kind of thing that would cut the last letter off. Try getting rid of the "-1".

---

### Post by BLTicklemonster on 2005-12-14
Bingo, thanks. ~V~ at unrealadmin said the same thing.

```
#!/bin/bash
cd ~/.ut2004/Cache || exit 1 # change this to your ut2004 user dir
if [ -f cache.ini ] ; then
{
export ut2004dir="/home/bill/ut2004/" # change this to your main ut2004 folder
gawk -F= ' 
ut2004dir = "${ut2004dir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " ut2004dir targ $2 | "sh";
}
{
if(match($2,".ut2")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".ogg")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
else if(match($2,".usx")) moveit("StaticMeshes/");
else if(match($2,".ukx")) moveit("Animations/");
}
END { close("sh") }' cache.ini
#rm *.uxx cache.ini
}
fi;
# end script
```

---

### Post by BLTicklemonster on 2005-12-15
What if I wanted to make that into a ui(?)? Glade or something would be great to use to make it, but I tried it and I don't see what I was expecting to see. Adjunta has a nice wizard to it, but I don't think it liked that script. I'm a total newb, but figured that since I have that code sitting there, why not try to make it into something.

---

### Post by KhaaL on 2008-01-31
I know this is a ***very*** old thread, but since I'm a regular 2k4 player, how far have you got with your GUI ambitions? So far my attempts at manually un-caching files been futile.

---

