---
title: "Create 2 layered PSD with Imagemagick"
date: 2012-12-14
forum: Programming Talk
---

### Post by Valpskott on 2012-12-14
So, I've googled it, and everywhere where I've found examples where people claim they managed to do this, when I try the same and then open the output file in GIMP, it only contains 1 of the layer.

Here are some of the examples I've tried that reportably have worked for others, but not me.

```
convert -alpha set pic1.png -alpha set pic2.png -adjoin output.psd

convert pic1.png pic2.png -alpha set output.psd

convert -size 100x100 -alpha set plasma:fractal -alpha set plasma:fractal -adjoin out.psd

```

I've tried this in both ImageMagick 6.6.9-7 (ubuntu 12.04) and under 6.7.6-3 (under cygwin).

Every time I get errors like this one:
> *** stack smashing detected ***: convert terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0xb7346045]
/lib/i386-linux-gnu/libc.so.6(+0x103ffa)[0xb7345ffa]
/usr/lib/ImageMagick-6.6.9/modules-Q16/coders/psd.so(+0x6e64)[0xb77c8e64]
/usr/lib/ImageMagick-6.6.9/modules-Q16/coders/psd.so(+0x3e25)[0xb77c5e25]
/usr/lib/libMagickCore.so.4(WriteImage+0x2f9)[0xb7590779]
/usr/lib/libMagickCore.so.4(WriteImages+0x1c2)[0xb7591092]
/usr/lib/libMagickWand.so.4(ConvertImageCommand+0x274b)[0xb744289b]
/usr/lib/libMagickWand.so.4(MagickCommandGenesis+0x22f)[0xb74b747f]
convert[0x8048636]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xb725b4d3]
convert[0x8048679]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:01 6825492    /usr/bin/convert
08049000-0804a000 r--p 00000000 08:01 6825492    /usr/bin/convert
0804a000-0804b000 rw-p 00001000 08:01 6825492    /usr/bin/convert
09d5d000-09da0000 rw-p 00000000 00:00 0          [heap]
b6a19000-b6a35000 r-xp 00000000 08:01 5768117    /lib/i386-linux-gnu/libgcc_s.so.1
b6a35000-b6a36000 r--p 0001b000 08:01 5768117    /lib/i386-linux-gnu/libgcc_s.so.1
b6a36000-b6a37000 rw-p 0001c000 08:01 5768117    /lib/i386-linux-gnu/libgcc_s.so.1
b6a37000-b6ab8000 rw-p 00000000 00:00 0 
b6ace000-b6b4f000 rw-p 00000000 00:00 0 
b6b53000-b6b75000 r--p 00000000 08:01 6824675    /usr/share/locale-langpack/sv/LC_MESSAGES/libc.mo
b6b75000-b6b9d000 r-xp 00000000 08:01 5768173    /lib/i386-linux-gnu/libpng12.so.0.46.0
b6b9d000-b6b9e000 r--p 00027000 08:01 5768173    /lib/i386-linux-gnu/libpng12.so.0.46.0
b6b9e000-b6b9f000 rw-p 00028000 08:01 5768173    /lib/i386-linux-gnu/libpng12.so.0.46.0
b6bb1000-b6bd3000 r-xp 00000000 08:01 8002840    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/png.so
b6bd3000-b6bd4000 r--p 00021000 08:01 8002840    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/png.so
b6bd4000-b6bd5000 rw-p 00022000 08:01 8002840    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/png.so
b6bd5000-b6dd5000 r--p 00000000 08:01 6823761    /usr/lib/locale/locale-archive
b6dd5000-b6dd7000 rw-p 00000000 00:00 0 
b6dd7000-b6ddc000 r-xp 00000000 08:01 6819729    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6ddc000-b6ddd000 r--p 00004000 08:01 6819729    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6ddd000-b6dde000 rw-p 00005000 08:01 6819729    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6dde000-b6ddf000 rw-p 00000000 00:00 0 
b6ddf000-b6de1000 r-xp 00000000 08:01 6819718    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b6de1000-b6de2000 r--p 00001000 08:01 6819718    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b6de2000-b6de3000 rw-p 00002000 08:01 6819718    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b6de3000-b6e1d000 r-xp 00000000 08:01 5768169    /lib/i386-linux-gnu/libpcre.so.3.12.1
b6e1d000-b6e1e000 r--p 00039000 08:01 5768169    /lib/i386-linux-gnu/libpcre.so.3.12.1
b6e1e000-b6e1f000 rw-p 0003a000 08:01 5768169    /lib/i386-linux-gnu/libpcre.so.3.12.1
b6e1f000-b6e26000 r-xp 00000000 08:01 5768182    /lib/i386-linux-gnu/librt-2.15.so
b6e26000-b6e27000 r--p 00006000 08:01 5768182    /lib/i386-linux-gnu/librt-2.15.so
b6e27000-b6e28000 rw-p 00007000 08:01 5768182    /lib/i386-linux-gnu/librt-2.15.so
b6e28000-b6e2b000 r-xp 00000000 08:01 5768109    /lib/i386-linux-gnu/libdl-2.15.so
b6e2b000-b6e2c000 r--p 00002000 08:01 5768109    /lib/i386-linux-gnu/libdl-2.15.so
b6e2c000-b6e2d000 rw-p 00003000 08:01 5768109    /lib/i386-linux-gnu/libdl-2.15.so
b6e2d000-b6e4c000 r-xp 00000000 08:01 6820310    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b6e4c000-b6e4d000 r--p 0001f000 08:01 6820310    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b6e4d000-b6e4e000 rw-p 00020000 08:01 6820310    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b6e4e000-b6e4f000 rw-p 00000000 00:00 0 
b6e4f000-b6e75000 r-xp 00000000 08:01 5768114    /lib/i386-linux-gnu/libexpat.so.1.5.2
b6e75000-b6e76000 ---p 00026000 08:01 5768114    /lib/i386-linux-gnu/libexpat.so.1.5.2
b6e76000-b6e78000 r--p 00026000 08:01 5768114    /lib/i386-linux-gnu/libexpat.so.1.5.2
b6e78000-b6e79000 rw-p 00028000 08:01 5768114    /lib/i386-linux-gnu/libexpat.so.1.5.2
b6e79000-b6f70000 r-xp 00000000 08:01 5768121    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
b6f70000-b6f71000 r--p 000f6000 08:01 5768121    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
b6f71000-b6f72000 rw-p 000f7000 08:01 5768121    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
b6f72000-b6f7a000 r-xp 00000000 08:01 6820086    /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
b6f7a000-b6f7b000 r--p 00008000 08:01 6820086    /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
b6f7b000-b6f7c000 rw-p 00009000 08:01 6820086    /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
b6f7c000-b6f8a000 r-xp 00000000 08:01 6819965    /usr/lib/i386-linux-gnu/libgomp.so.1.0.0
b6f8a000-b6f8b000 r--p 0000d000 08:01 6819965    /usr/lib/i386-linux-gnu/libgomp.so.1.0.0
b6f8b000-b6f8c000 rw-p 0000e000 08:01 6819965    /usr/lib/i386-linux-gnu/libgomp.so.1.0.0
b6f8c000-b6fb6000 r-xp 00000000 08:01 5768128    /lib/i386-linux-gnu/libm-2.15.so
b6fb6000-b6fb7000 r--p 00029000 08:01 5768128    /lib/i386-linux-gnu/libm-2.15.so
b6fb7000-b6fb8000 rw-p 0002a000 08:01 5768128    /lib/i386-linux-gnu/libm-2.15.so
b6fb8000-b6fb9000 rw-p 00000000 00:00 0 
b6fb9000-b6fcd000 r-xp 00000000 08:01 5768207    /lib/i386-linux-gnu/libz.so.1.2.3.4
b6fcd000-b6fce000 r--p 00013000 08:01 5768207    /lib/i386-linux-gnu/libz.so.1.2.3.4
b6fce000-b6fcf000 rw-p 00014000 08:01 5768207    /lib/i386-linux-gnu/libz.so.1.2.3.4
b6fcf000-b6fde000 r-xp 00000000 08:01 5768095    /lib/i386-linux-gnu/libbz2.so.1.0.4
b6fde000-b6fdf000 r--p 0000e000 08:01 5768095    /lib/i386-linux-gnu/libbz2.so.1.0.4
b6fdf000-b6fe0000 rw-p 0000f000 08:01 5768095    /lib/i386-linux-gnu/libbz2.so.1.0.4
b6fe0000-b7110000 r-xp 00000000 08:01 6819716    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b7110000-b7111000 r--p 0012f000 08:01 6819716    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b7111000-b7113000 rw-p 00130000 08:01 6819716    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b7113000-b7114000 rw-p 00000000 00:00 0 
b7114000-b7124000 r-xp 00000000 08:01 6819731    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b7124000-b7125000 r--p 0000f000 08:01 6819731    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b7125000-b7126000 rw-p 00010000 08:01 6819731    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b7126000-b7158000 r-xp 00000000 08:01 6819902    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b7158000-b7159000 r--p 00032000 08:01 6819902    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b7159000-b715a000 rw-p 00033000 08:01 6819902    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b715a000-b715b000 rw-p 00000000 00:00 0 
b715b000-b716d000 r-xp 00000000 08:01 6825482    /usr/lib/liblqr-1.so.0.3.1
b716d000-b716e000 r--p 00011000 08:01 6825482    /usr/lib/liblqr-1.so.0.3.1
b716e000-b716f000 rw-p 00012000 08:01 6825482    /usr/lib/liblqr-1.so.0.3.1
b716f000-b7204000 r-xp 00000000 08:01 6819910    /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
b7204000-b7208000 r--p 00094000 08:01 6819910    /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
b7208000-b7209000 rw-p 00098000 08:01 6819910    /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
b7209000-b723e000 r-xp 00000000 08:01 6820075    /usr/lib/i386-linux-gnu/liblcms.so.1.0.19
b723e000-b723f000 r--p 00034000 08:01 6820075    /usr/lib/i386-linux-gnu/liblcms.so.1.0.19
b723f000-b7240000 rw-p 00035000 08:01 6820075    /usr/lib/i386-linux-gnu/liblcms.so.1.0.19
b7240000-b7242000 rw-p 00000000 00:00 0 
b7242000-b73e5000 r-xp 00000000 08:01 5768096    /lib/i386-linux-gnu/libc-2.15.so
b73e5000-b73e6000 ---p 001a3000 08:01 5768096    /lib/i386-linux-gnu/libc-2.15.so
b73e6000-b73e8000 r--p 001a3000 08:01 5768096    /lib/i386-linux-gnu/libc-2.15.so
b73e8000-b73e9000 rw-p 001a5000 08:01 5768096    /lib/i386-linux-gnu/libc-2.15.so
b73e9000-b73ec000 rw-p 00000000 00:00 0 
b73ec000-b7403000 r-xp 00000000 08:01 5768176    /lib/i386-linux-gnu/libpthread-2.15.so
b7403000-b7404000 r--p 00016000 08:01 5768176    /lib/i386-linux-gnu/libpthread-2.15.so
b7404000-b7405000 rw-p 00017000 08:01 5768176    /lib/i386-linux-gnu/libpthread-2.15.so
b7405000-b7408000 rw-p 00000000 00:00 0 
b7408000-b7523000 r-xp 00000000 08:01 6825486    /usr/lib/libMagickWand.so.4.0.1
b7523000-b7524000 r--p 0011a000 08:01 6825486    /usr/lib/libMagickWand.so.4.0.1
b7524000-b7526000 rw-p 0011b000 08:01 6825486    /usr/lib/libMagickWand.so.4.0.1
b7526000-b7759000 r-xp 00000000 08:01 6825484    /usr/lib/libMagickCore.so.4.0.1
b7759000-b775a000 ---p 00233000 08:01 6825484    /usr/lib/libMagickCore.so.4.0.1
b775a000-b7764000 r--p 00233000 08:01 6825484    /usr/lib/libMagickCore.so.4.0.1
b7764000-b77a1000 rw-p 0023d000 08:01 6825484    /usr/lib/libMagickCore.so.4.0.1
b77a1000-b77c2000 rw-p 00000000 00:00 0 
b77c2000-b77ca000 r-xp 00000000 08:01 8002775    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/psd.so
b77ca000-b77cb000 r--p 00007000 08:01 8002775    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/psd.so
b77cb000-b77cc000 rw-p 00008000 08:01 8002775    /usr/lib/ImageMagick-6.6.9/modules-Q16/coders/psd.so
b77cc000-b77d3000 r--s 00000000 08:01 6820620    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b77d3000-b77d5000 rw-p 00000000 00:00 0 
b77d5000-b77d6000 r-xp 00000000 00:00 0          [vdso]
b77d6000-b77f6000 r-xp 00000000 08:01 5768076    /lib/i386-linux-gnu/ld-2.15.so
b77f6000-b77f7000 r--p 0001f000 08:01 5768076    /lib/i386-linux-gnu/ld-2.15.so
b77f7000-b77f8000 rw-p 00020000 08:01 5768076    /lib/i386-linux-gnu/ld-2.15.so
bf929000-bf94a000 rw-p 00000000 00:00 0          [stack]
Avbruten (SIGABRT) (minnesutskrift skapad)


---

### Post by lykeion on 2012-12-17
Thanks to [SO]("http://stackoverflow.com/a/13514555") I found this example that seems to work:

```
convert \( -page +0+0 -label "label1" pic1.png -background none -mosaic -set colorspace RGB \) \( -page +0+0 -label "label2" pic2.png -background none -mosaic -set colorspace RGB \) \( -clone 0--1 -background none -mosaic \) -alpha Off -reverse output.psd
```

Hope it helps

---

### Post by Valpskott on 2012-12-21
Ahh, thank you. I was about to give up hope. The line seems to work in creating PSD:s with several layers, I'll just have to do some tinkering to get it into my script the way I want it.

Thanks! :)

---

