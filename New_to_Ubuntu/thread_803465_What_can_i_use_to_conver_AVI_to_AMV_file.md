---
title: "What can i use to conver AVI to AMV file?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-22
What can i use to conver AVI to AMV file?

---

### Post by shifty_powers on 2008-05-22
[http://ubuntuforums.org/showthread.php?t=646164](http://ubuntuforums.org/showthread.php?t=646164)

should get you started ;)

---

### Post by HotShotDJ on 2008-05-22
> **appoloin said:**
> What can i use to conver AVI to AMV file?Here is all I could find out:[QUOTE="http://en.wikipedia.org/wiki/AMV_video_format"]Documentation for this format is not publicly available, but Dobrica Pavlinuši&#263; reverse engineered the format to produce a Perl-based decoder and Pavlinuši&#263;, Tom Van Braeckel and Vladimir Voroshilov produced a version of FFmpeg that works on AMV files. The AMV code has been sent upstream to the main FFmpeg project.[/QUOTE]

---

### Post by appoloin on 2008-05-22
this is good stuff!!! now can someone explain to me how to do this? i have downloaded FFmpeg and installed it downloaded the google tool and installed it but how do u use it? do i have to do it in terminal?

Using patched FFmpeg
(for that try to see here [http://code.google.com/p/amv-codec-tools/](http://code.google.com/p/amv-codec-tools/))

In common case command line will look like

ffmpeg -i <input> -f amv -s <width>x<height> -r 16 -ac 1 -ar 22050 -qmin 3 -qmax 3 <output>

FFmpeg accepts any picture resolutions, but hardware players supports only:

* 128x90
* 128x128
* 160x120

Input file can be any video format supported by FFmpeg.

Note: if output file has 'amv' extention, -f amv option can be omitted.

Option -r 16 sets framerate to 16 frames/sec (other values seems to be not supported by hardware players).

Options -ac 1 and -ar 22050 sets 22050 Hz mono sound. Other formats are not supported.

Options -qmin 3 and -qmax 3 forces quantizer to be equal to 3. This will give you good quality with acceptable file size.

Example 1. Converting AVI file into AMV with 160x120 picture size:

ffmpeg -i file.avi -s 160x120 -ac 1 -ar 22050 -qmin 3 -qmax 3 file.amv

---

### Post by Maximiliano on 2009-01-06
Hay un excelente programa con entorno gráfico que funciona a las mil maravillas en Ubuntu.
Es GNU, hay que bajar la versión Linux, descomprimirla en una carpeta y darle click al archivo MPxConverter y listo!!
El tamaño del archivo es de unos 2MB

[http://www.bytessence.com/bmpxc.html](http://www.bytessence.com/bmpxc.html)
(great GNU software for Linux (Ubuntu), unzip the file, double click MPxConverter and enjoy converting videos to AMV)

---

