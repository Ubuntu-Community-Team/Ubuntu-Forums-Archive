---
title: "cant's link libalsa09 statically."
date: 2007-10-26
forum: Programming Talk
---

### Post by eantoranz on 2007-10-26
I want to add alsa code to a shared object I'm creating (so I can use alsa with java).

After looking around for a while, I found out I can tell gcc to use a .a file directly, and so I did:

```

$ gcc -shared -o lib/libwmagic_alsa.so -Wl,-soname,libmagic_alsa.so -I /usr/lib/jvm/java-1.5.0-sun/include/ -I /usr/lib/jvm/java-1.5.0-sun/include/linux/ src/wmagic/alsa/wmagic_alsa.c /usr/lib/ao/plugins-2/libalsa09.a -static -lc

```

Perfect. However, when I run java, here's the output:
```

      8759:     file=/home/antoranz/eclipse/europa/workspace/wmagic/lib/libwmagic_alsa.so [0];  generating link map
      8759:       dynamic: 0xb1ff96f8  base: 0xb1ff8000   size: 0x00001824
      8759:         entry: 0xb1ff84e0  phdr: 0xb1ff8034  phnum:          4
      8759:
      8759:     /home/antoranz/eclipse/europa/workspace/wmagic/lib/libwmagic_alsa.so: error: symbol lookup error: undefined symbol: snd_pcm_open (fatal)
      8759:
      8759:     file=/home/antoranz/eclipse/europa/workspace/wmagic/lib/libwmagic_alsa.so [0];  destroying link map
Can't load library wmagic_alsa
java.lang.UnsatisfiedLinkError: /home/antoranz/eclipse/europa/workspace/wmagic/lib/libwmagic_alsa.so: Can't load IA 32-bit .so on a IA 32-bit platform
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at wmagic.basic.SoundOutput.initializeAlsa(SoundOutput.java:87)
        at wmagic.basic.SoundOutput.<init>(SoundOutput.java:29)
        at wmagic.basic.Wave.main(Wave.java:61)

```

There you go, it's still undefined.

If I look at my so:
```

$ objdump -x lib/libwmagic_alsa.so | grep snd
00000000         *UND*  00000000              snd_pcm_close
00000000         *UND*  00000000              snd_pcm_open

```

That shouldn't happen, right?

But If I look in libalsa09.a, they are undefined in the SYMBOL TABLE as well:
```

00000000 l    d  .data  00000000 .data
00000000 l     O .data  00000024 ao_alsa_info
00000000 l    d  .rodata.str1.4 00000000 .rodata.str1.4
00000000 l    d  .rodata.str1.1 00000000 .rodata.str1.1
00000000 l    d  .rodata.cst8   00000000 .rodata.cst8
00000300 l     F .text  0000026d alsa_set_hwparams
00000570 l     F .text  000000f8 alsa_set_swparams
00000024 l     O .data  00000010 ao_alsa_options
00000102 l       .rodata.str1.1 00000000 .LC32
00000127 l       .rodata.str1.1 00000000 .LC36
0000012b l       .rodata.str1.1 00000000 .LC37
00000134 l       .rodata.str1.1 00000000 .LC40
00000132 l       .rodata.str1.1 00000000 .LC39
00000000 l    d  .text  00000000 .text
00000000 l    d  .bss   00000000 .bss
00000000 l    d  .comment       00000000 .comment
00000000 l    d  .note.GNU-stack        00000000 .note.GNU-stack
00000000 g     F .text  0000000a ao_plugin_driver_info
00000010 g     F .text  000000cd ao_plugin_device_clear
00000000         *UND*  00000000 free
00000000         *UND*  00000000 stderr
00000000         *UND*  00000000 fwrite
000000e0 g     F .text  000000c3 ao_plugin_close
00000000         *UND*  00000000 snd_pcm_drain
00000000         *UND*  00000000 snd_pcm_close
000001b0 g     F .text  000000fd ao_plugin_play
00000000         *UND*  00000000 snd_strerror
00000000         *UND*  00000000 fprintf
00000000         *UND*  00000000 sleep
00000000         *UND*  00000000 snd_pcm_resume
00000000         *UND*  00000000 snd_pcm_prepare
000002b0 g     F .text  00000043 ao_plugin_test
00000000         *UND*  00000000 snd_pcm_open
00000000         *UND*  00000000 snd_pcm_hw_params_sizeof
00000000         *UND*  00000000 memset
00000000         *UND*  00000000 snd_pcm_hw_params_any
00000000         *UND*  00000000 snd_pcm_hw_params_set_access
00000000         *UND*  00000000 snd_pcm_hw_params_set_format
00000000         *UND*  00000000 snd_pcm_hw_params_set_channels
00000000         *UND*  00000000 snd_pcm_hw_params_set_rate_near
00000000         *UND*  00000000 snd_pcm_hw_params_set_buffer_time_near
00000000         *UND*  00000000 snd_pcm_hw_params_set_period_time_near
00000000         *UND*  00000000 snd_pcm_hw_params
00000000         *UND*  00000000 snd_pcm_hw_params_get_period_size
00000000         *UND*  00000000 snd_pcm_hw_params_get_buffer_size
00000000         *UND*  00000000 __stack_chk_fail
00000000         *UND*  00000000 snd_pcm_sw_params_sizeof
00000000         *UND*  00000000 snd_pcm_sw_params_current
00000000         *UND*  00000000 snd_pcm_sw_params_set_start_threshold
00000000         *UND*  00000000 snd_pcm_sw_params_set_avail_min
00000000         *UND*  00000000 snd_pcm_sw_params_set_xfer_align
00000000         *UND*  00000000 snd_pcm_sw_params
00000670 g     F .text  0000012e ao_plugin_open
000007a0 g     F .text  000000b7 ao_plugin_device_init
00000000         *UND*  00000000 malloc
00000000         *UND*  00000000 snd_pcm_writei
00000000         *UND*  00000000 calloc
00000860 g     F .text  00000214 ao_plugin_set_option
00000000         *UND*  00000000 __strtol_internal
00000000         *UND*  00000000 __strdup
00000000         *UND*  00000000 snd_pcm_mmap_writei

```

As far as I can see, most functions are undefined. Is that right? Or did I do something wrong?

---

### Post by eantoranz on 2007-10-26
I was told to use libasound.a instead, but now when I try to compile, I get this:

```

$ LANG=en gcc -shared -o lib/libwmagic_alsa.so -Wl,-soname,libmagic_alsa.so -I /usr/lib/jvm/java-1.5.0-sun/include/ -I /usr/lib/jvm/java-1.5.0-sun/include/linux/ src/wmagic/alsa/wmagic_alsa.c /usr/lib/libasound.a -static -lc
/usr/bin/ld: lib/libwmagic_alsa.so: version node not found for symbol snd_pcm_sw_params_get_start_threshold@ALSA_0.9
/usr/bin/ld: failed to set dynamic section sizes: Bad value
collect2: ld returned 1 exit status

```

What's that supposed to mean?

---

### Post by geraldm on 2007-10-27
I suppose it could mean that you are using two control words:
-shared and -static
and you stuck libasound.a in the area controlled by -shared.
It belongs after the -static keyword.

Gerald

---

