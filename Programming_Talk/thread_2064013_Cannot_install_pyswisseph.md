---
title: "Cannot install pyswisseph"
date: 2012-09-28
forum: Programming Talk
---

### Post by jw37 on 2012-09-28
Ubuntu 10.04 - Python 2.6.5 - gcc 4.4.3

Package: [http://pypi.python.org/pypi/pyswisseph](http://pypi.python.org/pypi/pyswisseph)

I downloaded and extracted the source. Then tried to install:

```
.../pyswisseph-1.77.00-0**$** sudo python setup.py install
```The output:

```
running install
running build
running build_ext
building 'swisseph' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Isrc -Iswephelp -I/usr/include/python2.6 -c pyswisseph.c -o build/temp.linux-i686-2.6/pyswisseph.o -std=gnu99
pyswisseph.c:56:20: error: Python.h: No such file or directory
pyswisseph.c:74: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:210: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:252: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:277: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:303: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:329: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:356: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:383: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:399: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:455: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:534: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:561: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:616: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:635: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:660: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:678: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:703: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:720: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:752: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:774: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:785: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:802: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:829: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:882: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:908: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:960: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:985: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1010: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1063: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1088: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1167: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1191: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1216: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1252: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1271: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1294: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1315: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1334: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1353: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1368: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1383: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1398: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1428: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1445: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1460: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1475: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1505: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1520: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1535: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1565: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1583: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1618: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:1642: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2033: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2433: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2445: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2463: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2481: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2520: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2542: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2564: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2591: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2629: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2660: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2699: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2739: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2808: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2879: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:2959: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3039: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3065: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3092: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3147: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3172: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3241: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3259: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3280: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3295: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3310: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3327: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3348: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3363: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3378: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3393: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3408: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3430: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3481: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3523: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyswisseph.c:3539: error: array type has incomplete element type
pyswisseph.c:3540: error: ‘PyCFunction’ undeclared here (not in a function)
pyswisseph.c:3540: error: expected ‘}’ before ‘pyswe_set_ephe_path’
pyswisseph.c:3542: error: expected ‘}’ before ‘pyswe_set_jpl_file’
pyswisseph.c:3544: error: expected ‘}’ before ‘pyswe_set_topo’
pyswisseph.c:3546: error: expected ‘}’ before ‘pyswe_set_sid_mode’
pyswisseph.c:3548: error: expected ‘}’ before ‘pyswe_get_ayanamsa’
pyswisseph.c:3550: error: expected ‘}’ before ‘pyswe_get_ayanamsa_ut’
pyswisseph.c:3552: error: expected ‘}’ before ‘pyswe_get_ayanamsa_name’
pyswisseph.c:3554: error: expected ‘}’ before ‘pyswe_close’
pyswisseph.c:3556: error: expected ‘}’ before ‘pyswe_get_planet_name’
pyswisseph.c:3558: error: expected ‘}’ before ‘pyswe_calc’
pyswisseph.c:3560: error: expected ‘}’ before ‘pyswe_calc_ut’
pyswisseph.c:3562: error: expected ‘}’ before ‘pyswe_fixstar’
pyswisseph.c:3564: error: expected ‘}’ before ‘pyswe_fixstar_ut’
pyswisseph.c:3566: error: expected ‘}’ before ‘pyswe_nod_aps’
pyswisseph.c:3568: error: expected ‘}’ before ‘pyswe_nod_aps_ut’
pyswisseph.c:3570: error: expected ‘}’ before ‘pyswe_sidtime’
pyswisseph.c:3572: error: expected ‘}’ before ‘pyswe_sidtime0’
pyswisseph.c:3574: error: expected ‘}’ before ‘pyswe_houses_armc’
pyswisseph.c:3576: error: expected ‘}’ before ‘pyswe_houses_ex’
pyswisseph.c:3578: error: expected ‘}’ before ‘pyswe_house_pos’
pyswisseph.c:3580: error: expected ‘}’ before ‘pyswe_gauquelin_sector’
pyswisseph.c:3582: error: expected ‘}’ before ‘pyswe_julday’
pyswisseph.c:3584: error: expected ‘}’ before ‘pyswe_date_conversion’
pyswisseph.c:3586: error: expected ‘}’ before ‘pyswe_revjul’
pyswisseph.c:3588: error: expected ‘}’ before ‘pyswe_utc_to_jd’
pyswisseph.c:3590: error: expected ‘}’ before ‘pyswe_jdet_to_utc’
pyswisseph.c:3592: error: expected ‘}’ before ‘pyswe_jdut1_to_utc’
pyswisseph.c:3594: error: expected ‘}’ before ‘pyswe_deltat’
pyswisseph.c:3596: error: expected ‘}’ before ‘pyswe_get_tid_acc’
pyswisseph.c:3598: error: expected ‘}’ before ‘pyswe_set_tid_acc’
pyswisseph.c:3600: error: expected ‘}’ before ‘pyswe_houses’
pyswisseph.c:3602: error: expected ‘}’ before ‘pyswe_time_equ’
pyswisseph.c:3604: error: expected ‘}’ before ‘pyswe_sol_eclipse_when_loc’
pyswisseph.c:3606: error: expected ‘}’ before ‘pyswe_lun_occult_when_loc’
pyswisseph.c:3608: error: expected ‘}’ before ‘pyswe_sol_eclipse_when_glob’
pyswisseph.c:3610: error: expected ‘}’ before ‘pyswe_sol_eclipse_how’
pyswisseph.c:3612: error: expected ‘}’ before ‘pyswe_sol_eclipse_where’
pyswisseph.c:3614: error: expected ‘}’ before ‘pyswe_lun_occult_when_glob’
pyswisseph.c:3616: error: expected ‘}’ before ‘pyswe_lun_occult_where’
pyswisseph.c:3618: error: expected ‘}’ before ‘pyswe_lun_eclipse_when’
pyswisseph.c:3620: error: expected ‘}’ before ‘pyswe_lun_eclipse_how’
pyswisseph.c:3622: error: expected ‘}’ before ‘pyswe_rise_trans’
pyswisseph.c:3624: error: expected ‘}’ before ‘pyswe_pheno’
pyswisseph.c:3626: error: expected ‘}’ before ‘pyswe_pheno_ut’
pyswisseph.c:3628: error: expected ‘}’ before ‘pyswe_refrac’
pyswisseph.c:3630: error: expected ‘}’ before ‘pyswe_refrac_extended’
pyswisseph.c:3632: error: expected ‘}’ before ‘pyswe_set_lapse_rate’
pyswisseph.c:3634: error: expected ‘}’ before ‘pyswe_azalt’
pyswisseph.c:3636: error: expected ‘}’ before ‘pyswe_azalt_rev’
pyswisseph.c:3638: error: expected ‘}’ before ‘pyswe_cotrans’
pyswisseph.c:3640: error: expected ‘}’ before ‘pyswe_cotrans_sp’
pyswisseph.c:3642: error: expected ‘}’ before ‘pyswe_degnorm’
pyswisseph.c:3644: error: expected ‘}’ before ‘pyswe_csnorm’
pyswisseph.c:3646: error: expected ‘}’ before ‘pyswe_radnorm’
pyswisseph.c:3648: error: expected ‘}’ before ‘pyswe_rad_midp’
pyswisseph.c:3650: error: expected ‘}’ before ‘pyswe_deg_midp’
pyswisseph.c:3652: error: expected ‘}’ before ‘pyswe_split_deg’
pyswisseph.c:3654: error: expected ‘}’ before ‘pyswe_difcsn’
pyswisseph.c:3656: error: expected ‘}’ before ‘pyswe_difdegn’
pyswisseph.c:3658: error: expected ‘}’ before ‘pyswe_difcs2n’
pyswisseph.c:3660: error: expected ‘}’ before ‘pyswe_difdeg2n’
pyswisseph.c:3662: error: expected ‘}’ before ‘pyswe_difrad2n’
pyswisseph.c:3664: error: expected ‘}’ before ‘pyswe_csroundsec’
pyswisseph.c:3666: error: expected ‘}’ before ‘pyswe_d2l’
pyswisseph.c:3668: error: expected ‘}’ before ‘pyswe_day_of_week’
pyswisseph.c:3670: error: expected ‘}’ before ‘pyswe_cs2timestr’
pyswisseph.c:3672: error: expected ‘}’ before ‘pyswe_cs2lonlatstr’
pyswisseph.c:3674: error: expected ‘}’ before ‘pyswe_cs2degstr’
pyswisseph.c:3676: error: expected ‘}’ before ‘pyswe_fixstar_mag’
pyswisseph.c:3678: error: expected ‘}’ before ‘pyswe_heliacal_ut’
pyswisseph.c:3680: error: expected ‘}’ before ‘pyswe_vis_limit_mag’
pyswisseph.c:3685: error: expected ‘}’ before ‘pyswe__jdnow’
pyswisseph.c:3687: error: expected ‘}’ before ‘pyswe__julday’
pyswisseph.c:3689: error: expected ‘}’ before ‘pyswe__revjul’
pyswisseph.c:3691: error: expected ‘}’ before ‘pyswe__degsplit’
pyswisseph.c:3693: error: expected ‘}’ before ‘pyswe__signtostr’
pyswisseph.c:3695: error: expected ‘}’ before ‘pyswe__house_system_name’
pyswisseph.c:3697: error: expected ‘}’ before ‘pyswe__min_retro_time’
pyswisseph.c:3699: error: expected ‘}’ before ‘pyswe__max_retro_time’
pyswisseph.c:3701: error: expected ‘}’ before ‘pyswe__next_retro’
pyswisseph.c:3703: error: expected ‘}’ before ‘pyswe__go_past’
pyswisseph.c:3705: error: expected ‘}’ before ‘pyswe__next_aspect’
pyswisseph.c:3707: error: expected ‘}’ before ‘pyswe__next_aspect2’
pyswisseph.c:3709: error: expected ‘}’ before ‘pyswe__next_aspect_with’
pyswisseph.c:3711: error: expected ‘}’ before ‘pyswe__next_aspect_with2’
pyswisseph.c:3713: error: expected ‘}’ before ‘pyswe__next_aspect_cusp’
pyswisseph.c:3715: error: expected ‘}’ before ‘pyswe__next_aspect_cusp2’
pyswisseph.c:3717: error: expected ‘}’ before ‘pyswe__match_aspect’
pyswisseph.c:3719: error: expected ‘}’ before ‘pyswe__match_aspect2’
pyswisseph.c:3721: error: expected ‘}’ before ‘pyswe__match_aspect3’
pyswisseph.c:3723: error: expected ‘}’ before ‘pyswe__match_aspect4’
pyswisseph.c:3725: error: expected ‘}’ before ‘pyswe__years_diff’
pyswisseph.c:3727: error: expected ‘}’ before ‘pyswe__geoc2d’
pyswisseph.c:3729: error: expected ‘}’ before ‘pyswe__geolat2c’
pyswisseph.c:3731: error: expected ‘}’ before ‘pyswe__geolon2c’
pyswisseph.c:3733: error: expected ‘}’ before ‘pyswe__raman_houses’
pyswisseph.c:3735: error: expected ‘}’ before ‘pyswe__lord’
pyswisseph.c:3737: error: expected ‘}’ before ‘pyswe__long2rasi’
pyswisseph.c:3739: error: expected ‘}’ before ‘pyswe__long2navamsa’
pyswisseph.c:3741: error: expected ‘}’ before ‘pyswe__long2nakshatra’
pyswisseph.c:3743: error: expected ‘}’ before ‘pyswe__get_nakshatra_name’
pyswisseph.c:3745: error: expected ‘}’ before ‘pyswe__rasinorm’
pyswisseph.c:3747: error: expected ‘}’ before ‘pyswe__rasi_dif’
pyswisseph.c:3749: error: expected ‘}’ before ‘pyswe__rasi_dif2’
pyswisseph.c:3751: error: expected ‘}’ before ‘pyswe__tatkalika_relation’
pyswisseph.c:3753: error: expected ‘}’ before ‘pyswe__naisargika_relation’
pyswisseph.c:3755: error: expected ‘}’ before ‘pyswe__residential_strength’
pyswisseph.c:3757: error: expected ‘}’ before ‘pyswe__ochchabala’
pyswisseph.c:3760: error: expected ‘}’ before ‘pyswe__lock’
pyswisseph.c:3762: error: expected ‘}’ before ‘pyswe__unlock’
pyswisseph.c:3764: error: expected ‘}’ before ‘pyswe__trylock’
pyswisseph.c:3795: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initswisseph’
error: command 'gcc' failed with exit status 1
```Did I something wrong?

---

### Post by jw37 on 2012-09-28
Well I didn't introduce the topic very well, maybe I should tell what it is about.

The package is a python binding to an astronomical/astrological ephemeris library, written in C. It is meant to find out planet positions and solar eclipses and things like that. The ephemeris home site is: [http://www.astro.com/swisseph/](http://www.astro.com/swisseph/)

The pyswisseph Readme-file says:

"This directory contains the source of the Python extension to the Swiss Ephemeris (pyswisseph), **along with the swisseph source itself**, created by AstroDienst."

Thus I thought I don't need to first install the original (C language) swisseph program. (I tried that, too. Didn't succeed at all. There was a Makefile but no configure script. The 'make' produced  hundreds of warnigns but no errors. The 'make install' was bad: "make: *** No rule to make target `install'.  Stop.")

Have you guys any experience with these ephemeris libraries? Or can you see what's the problem just by looking at the errors produced by setup.py? I'm totally helpless.

---

### Post by spjackson on 2012-09-28
Your first error:
```

pyswisseph.c:56:20: error: Python.h: No such file or directory

``` is the likely cause of your remaining errors.

Does /usr/include/python2.6/Python.h exist? If not, you probably need to install the python-dev package (or python2.6-dev).

---

### Post by jw37 on 2012-09-28
That was extremely helpful! Thank you very much!

---

### Post by vedavrata on 2013-08-18
> **spjackson said:**
> Your first error: ```
 pyswisseph.c:56:20: error: Python.h: No such file or directory 
``` is the likely cause of your remaining errors.

Does /usr/include/python2.6/Python.h exist? If not, you probably need to install the python-dev package (or python2.6-dev).

I have the same problem:
Package: [http://pypi.python.org/pypi/pyswisseph](http://pypi.python.org/pypi/pyswisseph)

I have installed the python-dev package: ```
# sudo apt-get install python-dev
``` and this is the fix!

Thank you, Spjackson!

---

