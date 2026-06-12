---
title: "FFMPEG comands via php's exec()"
date: 2009-10-09
forum: Programming Talk
---

### Post by supernath on 2009-10-09
Hi!
I have installed ffmpeg on ubuntu 9.04 and it seems to be working via the terminal and i have managed to convert an .mpg into a .flv via terminal. However the same ffmpeg command that worked in the terminal silently fails when called from php's **exec()**. I have also tried calling it via shell_exec(), system() and various others but they all fail. I have checked php.ini and safe_mode is turned off. When i look in the apache error log i see the following error:

/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet


The command i am trying to execute with exec() is:

/usr/local/bin/ffmpeg -i /var/www/ffmpeg-demo-site/uploads/toycom13.mpg -b 600kb -r 60 -s 320x240 -ar 44100 -ab 64k -aspect 4:3 -f flv /var/www/ffmpeg-demo-site/videos/toycom13.flv

Have recompiled ffmpeg and created the file /etc/ls.so.conf.d/ffmpeg.conf and placed the line /usr/local/lib inside it but nothing seems to fix it. I've exhausted all my options. Please help! :)

---

### Post by Arndt on 2009-10-09
> **supernath said:**
> Hi!
I have installed ffmpeg on ubuntu 9.04 and it seems to be working via the terminal and i have managed to convert an .mpg into a .flv via terminal. However the same ffmpeg command that worked in the terminal silently fails when called from php's **exec()**. I have also tried calling it via shell_exec(), system() and various others but they all fail. I have checked php.ini and safe_mode is turned off. When i look in the apache error log i see the following error:

/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet


The command i am trying to execute with exec() is:

/usr/local/bin/ffmpeg -i /var/www/ffmpeg-demo-site/uploads/toycom13.mpg -b 600kb -r 60 -s 320x240 -ar 44100 -ab 64k -aspect 4:3 -f flv /var/www/ffmpeg-demo-site/videos/toycom13.flv

Have recompiled ffmpeg and created the file /etc/ls.so.conf.d/ffmpeg.conf and placed the line /usr/local/lib inside it but nothing seems to fix it. I've exhausted all my options. Please help! :)

I guess that ffmpeg uses some dynamically loaded library, and that when running under php, it doesn't find it. Use 'ldd' to see what library it wants. Rebuilding ffmpeg with static linking is one possibility. Does calling from php fail both in a browser and when using php from the command line?

---

### Post by supernath on 2009-10-09
OK, i am an experienced php programmer but a linux newbie. Sorry. What is ldd? I'm guessing its a command i type in the terminal? Is it possible for you to tell me the exact command i need to type in the terminal to carry out that test? Also this happens when called from a php script loaded in the browser. Not quite sure how to execute php from the command line but am willing to learn. Any help would be greatly appreciated. Thanks.

---

### Post by Arndt on 2009-10-09
> **supernath said:**
> OK, i am an experienced php programmer but a linux newbie. Sorry. What is ldd? I'm guessing its a command i type in the terminal? Is it possible for you to tell me the exact command i need to type in the terminal to carry out that test? Also this happens when called from a php script loaded in the browser. Not quite sure how to execute php from the command line but am willing to learn. Any help would be greatly appreciated. Thanks.

Open a terminal window, and type this command

```
ldd /usr/local/bin/ffmpeg
```

To run a php script on the command line, just do

```
php whateverscript.php
```

If your script expects to be called as a GET or POST command, you will probably have to modify it a little.

---

### Post by supernath on 2009-10-12
ok did the ldd command and the output was as follows:

linux-gate.so.1 =>  (0xb7fe2000)
    libavfilter.so.0 => /usr/local/lib/libavfilter.so.0 (0xb7fda000)
    libpostproc.so.51 => /usr/local/lib/libpostproc.so.51 (0xb7fca000)
    libavdevice.so.52 => /usr/local/lib/libavdevice.so.52 (0xb7fc0000)
    libavformat.so.52 => /usr/local/lib/libavformat.so.52 (0xb7ea4000)
    libavcodec.so.52 => /usr/local/lib/libavcodec.so.52 (0xb7427000)
    libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0xb7413000)
    libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0xb73d8000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb73a3000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb738a000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7227000)
    libasound.so.2 => /usr/lib/libasound.so.2 (0xb715e000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0xb706f000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0xb705f000)
    libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb704d000)
    libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb6fd8000)
    libschroedinger-1.0.so.0 => /usr/lib/libschroedinger-1.0.so.0 (0xb6f67000)
    libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb6f16000)
    libogg.so.0 => /usr/lib/libogg.so.0 (0xb6f10000)
    libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb6e16000)
    libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb6dec000)
    libx264.so.76 => /usr/local/lib/libx264.so.76 (0xb6d22000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6d1e000)
    /lib/ld-linux.so.2 (0xb7fe3000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb6d15000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6cfb000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0xb6cf7000)
    liboil-0.3.so.0 => /usr/lib/liboil-0.3.so.0 (0xb6c88000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6c82000)


Also i ran the php script from the terminal and it worked fine! However running the same script from the browser still failed!

I recompiled ffmpeg  today. And at first i was getting the same error
(symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet)
 in both terminal and browser when i executed the the command:

/usr/local/bin/ffmpeg -i /var/www/ffmpeg-demo-site/uploads/toycom13.mpg -b 600kb -r 60 -s 320x240 -ar 44100 -ab 64k -aspect 4:3 -f flv /var/www/ffmpeg-demo-site/videos/toycom13.flv

But when i  entered these commands 

[B]LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
[/B]**export**** **[B]LD_LIBRARY_PATH
[/B][B]sudo ldconfig

[/B]
into the terminal then the ffmpeg command (from terminal) worked and converted fine but still wouldn't work from the browser. The php script also worked fine when called from the terminal. Very strange. Any idea why? Does this help at all?

Thanking you in advance

---

### Post by Arndt on 2009-10-12
> **supernath said:**
> ok did the ldd command and the output was as follows:

linux-gate.so.1 =>  (0xb7fe2000)
    libavfilter.so.0 => /usr/local/lib/libavfilter.so.0 (0xb7fda000)
    libpostproc.so.51 => /usr/local/lib/libpostproc.so.51 (0xb7fca000)
    libavdevice.so.52 => /usr/local/lib/libavdevice.so.52 (0xb7fc0000)
    libavformat.so.52 => /usr/local/lib/libavformat.so.52 (0xb7ea4000)
    libavcodec.so.52 => /usr/local/lib/libavcodec.so.52 (0xb7427000)
    libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0xb7413000)
    libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0xb73d8000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb73a3000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb738a000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7227000)
    libasound.so.2 => /usr/lib/libasound.so.2 (0xb715e000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0xb706f000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0xb705f000)
    libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb704d000)
    libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb6fd8000)
    libschroedinger-1.0.so.0 => /usr/lib/libschroedinger-1.0.so.0 (0xb6f67000)
    libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb6f16000)
    libogg.so.0 => /usr/lib/libogg.so.0 (0xb6f10000)
    libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb6e16000)
    libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb6dec000)
    libx264.so.76 => /usr/local/lib/libx264.so.76 (0xb6d22000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6d1e000)
    /lib/ld-linux.so.2 (0xb7fe3000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb6d15000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6cfb000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0xb6cf7000)
    liboil-0.3.so.0 => /usr/lib/liboil-0.3.so.0 (0xb6c88000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6c82000)


Also i ran the php script from the terminal and it worked fine! However running the same script from the browser still failed!

I recompiled ffmpeg  today. And at first i was getting the same error
(symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet)
 in both terminal and browser when i executed the the command:

/usr/local/bin/ffmpeg -i /var/www/ffmpeg-demo-site/uploads/toycom13.mpg -b 600kb -r 60 -s 320x240 -ar 44100 -ab 64k -aspect 4:3 -f flv /var/www/ffmpeg-demo-site/videos/toycom13.flv

But when i  entered these commands 

[B]LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
[/B]**export**** **[B]LD_LIBRARY_PATH
[/B][B]sudo ldconfig

[/B]
into the terminal then the ffmpeg command (from terminal) worked and converted fine but still wouldn't work from the browser. The php script also worked fine when called from the terminal. Very strange. Any idea why? Does this help at all?

Thanking you in advance

Setting LD_LIBRARY_PATH only has effect in the shell where you do it, and processes started from there. When you call the script from a browser, it is really called from the http server, presumably Apache. So doing

```
# /etc/init.d/apache2 stop
the LD_LIBRARY_PATH things
# /etc/init.d/apache2 start
```

may work. I'm not sure, though.

---

### Post by supernath on 2009-10-12
tried what you said but still didn't work. Any other ideas?

---

### Post by Arndt on 2009-10-12
> **supernath said:**
> tried what you said but still didn't work. Any other ideas?

Not really. Can you use the PHP function phpinfo() to see any interesting details about the PHP environment?

---

### Post by Sn3akyP3t3 on 2009-11-09
I spent hours trying to find a solution to the problem you are encountering.  I'm an inexperienced programmer and a mediocre Ubuntu user, but I'm stubborn and keep trying things until I find a solution or an alternative.

**Here is what I did to run ffmpeg from within a PHP script:**
```
//path to ffmpeg executable
define('FFMPEG_LIBRARY', '/usr/local/bin/ffmpeg ');
```[B]Thats it!  It should work with that added in.

My other two attempts below were unsuccessful:[/B]
1.)```
//path to ffmpeg executable (failed)
$ffmpegExecPath = "/usr/local/bin/ffmpeg";
```2.) Use of ffmpeg-php, [http://ffmpeg-php.sourceforge.net/](http://ffmpeg-php.sourceforge.net/), would work too, but for my project I didn't want any extra baggage that would cause breaks on updates or something I didn't think of.  Also, requires more required knowledge to code properly within PHP.  You may find ffmpeg-php suitable for your project though.

---

### Post by raptor2552 on 2009-11-09
This is how I use ffmpeg from a php script. The following grabs a frame from a video to create a thumbnail but may be modified for your use:
[PHP]$ffmpegcmd = sprintf("ffmpeg -i %s -ss %s -vcodec png -vframes 1 -an -f rawvideo -s 168x124 -y %s", $src_dir.$src_file, $seek, $dest_dir.$src_file.$thumb_ext);

shell_exec($ffmpegcmd);[/PHP]

---

