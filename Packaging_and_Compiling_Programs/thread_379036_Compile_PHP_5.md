---
title: "Compile PHP 5"
date: 2007-03-08
forum: Packaging and Compiling Programs
---

### Post by man4mac on 2007-03-08
Hello,

I'm trying to compile and install PHP5 from its source code. I've downloaded the latest copy of the source, and successfully run the configure file with this command:
```
'./configure' '--prefix=/usr/local' '--with-xml' '--enable-bcmath'
'--enable-calendar' '--with-curl' '--with-dom' '--with-dom-xslt' '--with-dom-exslt'
'--enable-ftp' '--with-gd' '--with-jpeg-dir=/usr/local' '--with-png-dir=/usr'
'--enable-magic-quotes' '--with-mysqli' '--with-mysql=/usr' '--with-openssl'
'--enable-discard-path' '--with-pear' '--enable-sockets' '--enable-track-vars' 
'--with-ttf' '--with-freetype-dir=/usr' '--with-zlib'
```

Unfortunately when I try to "make" this, I get the following error:

```
collect2: ld returned 1 exit status
make: *** [sapi/cgi/php] Error 1
```

I'm pretty much a noob at compiling things. The problem is my current LAMP server doesn't have all the GD functions. I'm trying to compile the PHP source because I hear everything is included in that distro. All help will be appreciated.

---

### Post by hod139 on 2007-03-08
That error message isn't really useful, are you sure that's the entire message?

---

### Post by man4mac on 2007-03-11
Ok, sorry, well, first it compiles will all kinds of gibberish I don't understand, then these lines come up:
```
ext/gd/gd.o: In function `zif_imagepstext':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3578: undefined reference to `T1_AASetBitsPerPixel'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3586: undefined reference to `T1_AAHSetGrayValues'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3587: undefined reference to `T1_AASetLevel'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3599: undefined reference to `T1_GetExtend'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3600: undefined reference to `T1_GetCharOutline'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3610: undefined reference to `T1_GetKerning'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3614: undefined reference to `T1_GetMoveOutline'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3615: undefined reference to `T1_ConcatOutlines'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3617: undefined reference to `T1_GetCharOutline'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3618: undefined reference to `T1_ConcatOutlines'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3620: undefined reference to `T1_AAFillOutline'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3624: undefined reference to `T1_errno'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3582: undefined reference to `T1_AASetGrayValues'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3583: undefined reference to `T1_AASetLevel'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3622: undefined reference to `T1_AASetString'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3595: undefined reference to `T1_RotateMatrix'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3625: undefined reference to `T1_StrError'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3603: undefined reference to `T1_errno'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3604: undefined reference to `T1_StrError'
ext/gd/gd.o: In function `zm_startup_gd':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:408: undefined reference to `T1_SetBitmapPad'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:409: undefined reference to `T1_InitLib'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:410: undefined reference to `T1_SetLogLevel'
ext/gd/gd.o: In function `php_free_ps_font':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3292: undefined reference to `T1_DeleteFont'
ext/gd/gd.o: In function `zm_shutdown_gd':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:394: undefined reference to `T1_CloseLib'
ext/gd/gd.o: In function `zif_imagepsbbox':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3703: undefined reference to `T1_GetCharWidth'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3711: undefined reference to `T1_GetCharBBox'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3712: undefined reference to `T1_GetCharWidth'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3743: undefined reference to `T1_GetStringBBox'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3746: undefined reference to `T1_errno'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3714: undefined reference to `T1_GetKerning'
ext/gd/gd.o: In function `zif_imagepsslantfont':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3489: undefined reference to `T1_SlantFont'
ext/gd/gd.o: In function `zif_imagepsextendfont':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3459: undefined reference to `T1_DeleteAllSizes'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3466: undefined reference to `T1_ExtendFont'
ext/gd/gd.o: In function `zif_imagepsencodefont':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3426: undefined reference to `T1_LoadEncoding'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3431: undefined reference to `T1_DeleteAllSizes'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3432: undefined reference to `T1_ReencodeFont'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3433: undefined reference to `T1_DeleteEncoding'
ext/gd/gd.o: In function `zif_imagepsloadfont':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3320: undefined reference to `T1_AddFont'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3326: undefined reference to `T1_LoadFont'
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3323: undefined reference to `T1_StrError'
ext/gd/gd.o: In function `php_free_ps_enc':
/home/jpschroeder/php-5.1.6/ext/gd/gd.c:3303: undefined reference to `T1_DeleteEncoding'
collect2: ld returned 1 exit status
make: *** [sapi/cgi/php] Error 1
```

I really have no idea what this means.

---

### Post by drynish on 2007-03-27
Hummm why do you want to compile php 5?

Just install php5-gd

Look at this thread: 

[http://ubuntuforums.org/showthread.php?t=252842](http://ubuntuforums.org/showthread.php?t=252842)

Don't forget to restart your apache...

michel

---

