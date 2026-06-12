---
title: "Compiling Fortran"
date: 2014-04-08
forum: Packaging and Compiling Programs
---

### Post by phu004 on 2014-04-08
Hi Guys,

I was trying to compile a piece of software written in fortran on my 64bits ubuntu 13.10.  I followed the author's instruction from [http://eqseis.geosc.psu.edu/~cammon/HTML/RftnDocs/thecodes01.html](http://eqseis.geosc.psu.edu/~cammon/HTML/RftnDocs/thecodes01.html), downloaded his independent SAC library (iSACio) from his home page ([http://eqseis.geosc.psu.edu/~cammon/Tools/isacio.tar.gz](http://eqseis.geosc.psu.edu/~cammon/Tools/isacio.tar.gz)).  But Unfortunately my compilation failed half way through.  (Please see the compilation message below. )

Could anyone give me some advice on what I am doing wrong here?

Thanks in advance!

```
fos@sstestlab6:~/Downloads/Rftn.Codes.Export$ sudo csh build.it.csh > log.txt
mkdir: cannot create directory ‘./bin’: File exists
   ask:
   asktxt:
   blank:
   coef8:
   coefsh:
   coord:
   daymo:
   dfftr:
   diffr:
   dot:
   doy:
   fft:
   fsorce:
   g1:
   g2:
   h12:
   iask:
   iniocm:
   juli:
   locast:
   lpyr:
   max:
   minmax:
   npowr2:
   qrbd:
   rdlyrs:
   rotate:
   sacio:
   seisio:
   sinc:
   sit2:
Warning on line 223: local variable test never used
   svdrs:
   yesno:
   zero:
   MAIN pwaveqn:
   window:
   MAIN:
   blank:
   vslow:
   cphs:
   rcvrfn:
   ifmat:
Warning on line 299: local variable test never used
Warning on line 1: local variable eps never used
Warning on line 1: local variable zero never used
Warning on line 1: local variable quartr never used
   qabm:
   vabm:
   MAIN:
Warning on line 205: local variable splt never used
   MAIN:
Warning on line 205: local variable splt never used
   MAIN vstack:
   blank:
   MAIN modstat:
Warning on line 80: local variable fil never used
Warning on line 80: local variable fileout never used
   blank:
   MAIN modstat:
Warning on line 80: local variable fil never used
Warning on line 80: local variable fileout never used
   blank:
   MAIN manyvplot:
   blank:
   MAIN vplot:
Warning on line 37: local variable qp never used
Warning on line 37: local variable qs never used
   MAIN ppstime:
Warning on line 45: local variable qp never used
Warning on line 45: local variable qs never used
   MAIN manyinv:
   rand0:
   cubic:
   jinv:
Warning on line 319: local variable wk never used
Warning on line 319: local variable yesno never used
   getmodl:
   getseis:
Warning on line 50: local variable yesno never used
   jsoln:
   wrtsoln:
Warning on line 26: local variable il never used
   putsyn:
Warning on line 23: local variable yesno never used
   putpartl:
   sacin:
   sacout:
Warning on line 74: local variable user0 never used
Warning on line 74: local variable user1 never used
   minmax:
   partials:
Warning on line 141: local variable rn never used
   spartials:
Warning on line 187: local variable lyroff never used
   qabm:
   vabm:
   delifm:
   delrcv:
Warning on line 536: local variable two never used
   ifmat:
Warning on line 1308: local variable test never used
Warning on line 1010: local variable eps never used
Warning on line 1010: local variable zero never used
Warning on line 1010: local variable quartr never used
   vslow:
   cphs:
   rcvind:
Warning on line 1332: local variable two never used
   rcvrdcn:
Warning on line 1850: local variable rn never used
Warning on line 1850: local variable plyr never used
Warning on line 1850: local variable perta never used
Warning on line 1850: local variable pertb never used
Warning on line 1850: local variable pertr never used
   rcvrfn:
   rcvrtd:
Warning on line 2197: local variable eps never used
Warning on line 2197: local variable two never used
Warning on line 2197: local variable quartr never used
   sfpartials:
Warning on line 2470: inconsistent calling sequences for sfpartials,
    arg 1: here complex variable, previously real variable.
Warning on line 2586: local variable rn never used
Warning on line 2586: local variable lyroff never used
   sfrcvrdcn:
Warning on line 2697: local variable rn never used
Warning on line 2697: local variable plyr never used
Warning on line 2697: local variable perta never used
Warning on line 2697: local variable pertb never used
Warning on line 2697: local variable pertr never used
Warning on line 2697: local variable lyroff never used
   srcvrdcn:
Warning on line 2711: inconsistent calling sequences for sfrcvrdcn,
    arg 1: here real variable, previously complex variable.
   dfftr:
Warning on line 2766: inconsistent calling sequences for dfftr,
    arg 1: here real variable, previously complex variable.
   fft:
   lowcas:
rftn_partials.f:2450:22: error: conflicting types for ‘sfpartials_’
      *                      nlmax, dt, ntmax,
                      ^
rftn_partials.f:155:33: note: previous declaration of ‘sfpartials_’ was here
       nft = 512
                                 ^
rftn_partials.f:2727:22: error: conflicting types for ‘dfftr_’
 c                                              a.shakal, 1/78, 15 jul 80
                      ^
rftn_partials.f:2623:18: note: previous declaration of ‘dfftr_’ was here
       delf = 2. * fny / nft
                  ^
/usr/bin/f77: aborting compilation
make: *** [rftn_partials.o] Error 25
fos@sstestlab6:~/Downloads/Rftn.Codes.Export$



```

---

### Post by oldos2er on 2014-04-08
Moved to Packaging & Compiling Programs.

---

### Post by steeldriver on 2014-04-08
What fortran compiler are you using? I had a quick play and was able to get it to build (with warnings) in a 13.10 VM using gfortran as f77 via a wrapper script... after fixing a bunch of non-compliant line continuations

No idea if it runs (or what it's supposed to do)

---

### Post by phu004 on 2014-04-09
Thanks for your time trying it out. I am using f77 also. (installed the compiler via "apt-get install fort77")   I got bunch of warning message as well, but the compilation eventually got aborted due to "[COLOR=#000000][FONT=Ubuntu Mono]conflicting types[/FONT][/COLOR]" errors.  

If you are able to generate all  11 executable under  /Rftn.Codes.Export/bin, then the installation is successful.

---

### Post by phu004 on 2014-04-09
> [COLOR=#000000]What fortran compiler are you using? I had a quick play and was able to get it to build (with warnings) in a 13.10 VM using gfortran as f77 via a wrapper script... after fixing a bunch of non-compliant line continuations[/COLOR]

[COLOR=#000000]No idea if it runs (or what it's supposed to do)[/COLOR]

Would you explain how you fix the "[COLOR=#000000]non-compliant line continuations"?  Could you send me the entire "[/COLOR][COLOR=#000000]Rftn.Codes.Export[/COLOR][COLOR=#000000]" folder after compilation[/COLOR][COLOR=#000000]? My email address is [email]p.hu@auckland.ac.nz[/email]


[/COLOR]

---

### Post by steeldriver on 2014-04-09
**NOTE: THESE INSTRUCTIONS ARE FOR BUILDING WITH gfortran NOT fort77** (as far as I know, fort77 is a front-end for f2c, which is a Fortran to C converter - gfortran is the current actual GNU Fortran compiler, replacing g77). Please also note that I don't really speak Fortran so this is provided without any guarantees of correctness.

I'm attaching a gzipped patch file that you can run to make all the necessary changes. Assuming you copy it into the directory containing the Rftn.Codes.Export and iSacIO_Export library directories i.e.

```

$ ls
[COLOR=#0000ff]bin  iSacIO_Export  Rftn.Codes.Export[/COLOR]  [COLOR=#ff0000]Rftn.Codes.Export.patch.gz[/COLOR]

```

you would do

```

gzip -d Rftn.Codes.Export.patch.gz

cd Rftn.Codes.Export/

patch -p1 < ../Rftn.Codes.Export.patch

```

After that, edit the build.it.csh script as per the original instructions to set your SACLIB path, and then run the script as

```

FC=gfortran csh build.it.csh > buildLog.txt

```

(note the additional FC=gfortran at the start). It should build, albeit with the following warnings:

```

$ FC=gfortran csh build.it.csh > buildLog.txt
mkdir: cannot create directory ‘./bin’: File exists
ask.f:18.21:

  100 format(80(a1,$))                                                  
                     1
Warning: $ should be the last specifier in format at (1)
asktxt.f:20.21:

  100 format(80(a1,$))                                                  
                     1
Warning: $ should be the last specifier in format at (1)
iask.f:12.21:

  100 format(80(a1,$))                                                  
                     1
Warning: $ should be the last specifier in format at (1)
rftn_partials.f:127.17:

      call dfftr(a(1,nlmax),nft,'inverse',cdelf)                        
                 1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:130.17:

      call dfftr(a(1,plyr),nft,'inverse',cdelf)                         
                 1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:2576.25:

              call dfftr(a(1,nlmax),nft,'inverse',cdelf)                
                         1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:2579.25:

              call dfftr(a(1,plyr),nft,'inverse',cdelf)                 
                         1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:158.23:

      call sfpartials( a, p0,  perta, pertb, pertr, nlyrs,              
                       1
Warning: Type mismatch in argument 'a' at (1); passed REAL(4) to COMPLEX(4)
rftn_partials.f:1842.17:

      call dfftr(a(1,nlmax),nft,'inverse',cdelf)                        
                 1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:2692.17:

      call dfftr(a(1,nlmax),nft,'inverse',cdelf)                        
                 1
Warning: Type mismatch in argument 'x' at (1); passed COMPLEX(4) to REAL(4)
rftn_partials.f:2711.22:

      call sfrcvrdcn( a, p0, nlyrs,                                     
                      1
Warning: Type mismatch in argument 'a' at (1); passed REAL(4) to COMPLEX(4)

```

If you prefer, you can apply the changes contained in the patch file manually using the following steps

```

# change literal f77 to $(FC) so we can override on commandline
find . -iname 'makefile' -exec sed -i 's/f77/\$(FC)/g' {} \;

# push the line continuation characters to column 6 where they belong
find . -iname '*.f' -exec sed -i 's/^&     /     \&/' {} \;

# fix the 'Initialization string starting at (1) was truncated to fit the variable (4/5)' warnings
sed -i 's/character\*4 suf/character\*8 suf/' ./RForward/Utilities/ppstime.f

```

Hope this helps - please let me know since I can't test the resulting binaries myself

[ATTACH]251881[/ATTACH]

---

### Post by phu004 on 2014-04-09
Thanks a lot! I will try it out in just a moment and let you know the result :p

---

### Post by phu004 on 2014-04-10
> Hope this helps - please let me know since I can't test the resulting binaries myself

Wow the patch you sent me just saved my day, it works like a charm!   I truely appricate the time you spent helping me out, thanks again!

---

