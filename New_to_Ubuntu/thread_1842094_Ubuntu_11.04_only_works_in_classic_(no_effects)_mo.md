---
title: "Ubuntu 11.04 only works in classic (no effects) mode, why is that?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Ofernand on 2011-09-10
Greetings,
 
After installing Ubuntu 11.04, nothing on the desktop works when I click on it. I can only access 'Ubuntu classic (no effects)' mode which works fine and recovery mode.
 
Why is this?
 
All help is sincerely appreciated :)

---

### Post by mikewhatever on 2011-09-10
Your graphics card is probably unsupported. What you describe is similar to a known bug with Nvidia 7xxx cards + Unity.

---

### Post by coffeecat on 2011-09-10
Or perhaps your card needs a proprietary driver to be capable of running the 3d acceleration needed for Unity. What graphics card do you have?

---

### Post by snip3r8 on 2011-09-10
What Graphics Card do you have?

---

### Post by wildmanne39 on 2011-09-10
Hi, if you are not sure please run this command in a terminal:
```
lspci | grep VGA
```
and this one:
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Ofernand on 2011-09-11
Thank you all for your replies. I ran those commands wildmanne39 mentioned and this is what I got: ```

[SIZE=2][COLOR=black][FONT=Batang]oscar@oscar-M5300-Series:~$ lspci | grep VGA[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]oscar@oscar-M5300-Series:~$ /usr/lib/nux/unity_support_test &#8722;p[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]Error: unknown command-line option `&#8722;p'[/FONT][/COLOR][/SIZE][SIZE=2]
 
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]Check for Unity support on a X11 display.[/FONT][/COLOR][/SIZE][SIZE=2]
 
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]Usage:[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang] unity-support-test [ options ][/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]   -d, --display name: Specify the X11 display[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]   -i, --indirect:     Force an indirect rendering context[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]   -p, --print:        Print detection results on stdout[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]   -c, --compiz:       Only check for Compiz support[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]   -h, --help:         Show help[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]oscar@oscar-M5300-Series:~$ lsmod[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]Module                  Size  Used by[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]nls_iso8859_1          12617  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]nls_cp437              12751  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]vfat                   17335  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]fat                    55505  1 vfat[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]usb_storage            43946  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]uas                    17676  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]binfmt_misc            13213  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]radeon                896428  2 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_ali5451            23506  2 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_ac97_codec        105614  1 snd_ali5451[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]ac97_bus               12642  1 snd_ac97_codec[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_pcm                80244  2 snd_ali5451,snd_ac97_codec[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]arc4                   12473  2 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]ttm                    65184  1 radeon[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]b43                   296610  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_seq_midi           13132  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]drm_kms_helper         40745  1 radeon[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_rawmidi            25269  1 snd_seq_midi[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]joydev                 17322  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]mac80211              257001  1 b43[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]ppdev                  12849  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_seq_midi_event     14475  1 snd_seq_midi[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]drm                   180037  4 radeon,ttm,drm_kms_helper[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_timer              28659  2 snd_pcm,snd_seq[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]cfg80211              156212  2 b43,mac80211[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]pcmcia                 39671  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]i2c_ali15x3            12878  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]psmouse                73312  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]parport_pc             32111  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]serio_raw              12990  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]i2c_algo_bit           13184  1 radeon[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd                    55295  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]video                  18951  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]yenta_socket           27230  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]i2c_ali1535            12777  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]pcmcia_rsrc            18292  1 yenta_socket[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]soundcore              12600  1 snd[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]shpchp                 32345  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]snd_page_alloc         14073  1 snd_pcm[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]ati_agp                13202  1 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]lp                     13349  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]parport                36746  3 ppdev,parport_pc,lp[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]firewire_ohci          31504  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]b44                    35301  0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]firewire_core          56138  1 firewire_ohci[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]ssb                    45942  2 b43,b44[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]pata_ali               13564  2 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [SIZE=2][COLOR=black][FONT=Batang]crc_itu_t              12627  1 firewire_core[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE] [COLOR=black][FONT=Batang][SIZE=3][SIZE=2]oscar@oscar-M5300-Series:~$[/SIZE] [/SIZE][/FONT][/COLOR]

```Thanks again for the help!

---

### Post by Paqman on 2011-09-11
> **Ofernand said:**
> Thank you all for your replies. I ran those commands wildmanne39 mentioned and this is what I got: 
 
Thanks again for the help!

You have an AMD graphics card. You may find that if you open up Additional Drivers you can install a driver that will give you full 3D performance. There may also be a little icon at the top of the screen telling you that such a driver is available.

---

### Post by wildmanne39 on 2011-09-11
Hi, here is a link for your card.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Thank you

---

### Post by wildmanne39 on 2011-09-11
> **Ofernand said:**
> Thank you all for your replies. I ran those commands wildmanne39 mentioned and this is what I got: ```

[COLOR=black][FONT=Batang][SIZE=3]oscar@oscar-M5300-Series:~$ lspci | grep VGA[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]oscar@oscar-M5300-Series:~$ /usr/lib/nux/unity_support_test &#8722;p[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]Error: unknown command-line option `&#8722;p'[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Batang][SIZE=3]Check for Unity support on a X11 display.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Batang][SIZE=3]Usage:[/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang] unity-support-test [ options ][/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang]   -d, --display name: Specify the X11 display[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang]   -i, --indirect:     Force an indirect rendering context[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang]   -p, --print:        Print detection results on stdout[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang]   -c, --compiz:       Only check for Compiz support[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang]   -h, --help:         Show help[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]oscar@oscar-M5300-Series:~$ lsmod[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]Module                  Size  Used by[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]nls_iso8859_1          12617  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]nls_cp437              12751  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]vfat                   17335  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]fat                    55505  1 vfat[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]usb_storage            43946  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]uas                    17676  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]binfmt_misc            13213  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]radeon                896428  2 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_ali5451            23506  2 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_ac97_codec        105614  1 snd_ali5451[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]ac97_bus               12642  1 snd_ac97_codec[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_pcm                80244  2 snd_ali5451,snd_ac97_codec[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]arc4                   12473  2 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]ttm                    65184  1 radeon[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]b43                   296610  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_seq_midi           13132  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]drm_kms_helper         40745  1 radeon[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_rawmidi            25269  1 snd_seq_midi[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]joydev                 17322  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]mac80211              257001  1 b43[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]ppdev                  12849  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_seq_midi_event     14475  1 snd_seq_midi[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]drm                   180037  4 radeon,ttm,drm_kms_helper[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_timer              28659  2 snd_pcm,snd_seq[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]cfg80211              156212  2 b43,mac80211[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]pcmcia                 39671  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]i2c_ali15x3            12878  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]psmouse                73312  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]parport_pc             32111  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]serio_raw              12990  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]i2c_algo_bit           13184  1 radeon[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd                    55295  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]video                  18951  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]yenta_socket           27230  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]i2c_ali1535            12777  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]pcmcia_rsrc            18292  1 yenta_socket[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]soundcore              12600  1 snd[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]shpchp                 32345  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]snd_page_alloc         14073  1 snd_pcm[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]ati_agp                13202  1 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]lp                     13349  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]parport                36746  3 ppdev,parport_pc,lp[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]firewire_ohci          31504  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]b44                    35301  0 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]firewire_core          56138  1 firewire_ohci[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]ssb                    45942  2 b43,b44[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]pata_ali               13564  2 [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]crc_itu_t              12627  1 firewire_core[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Batang][SIZE=3]oscar@oscar-M5300-Series:~$ [/SIZE][/FONT][/COLOR]

```
 
Thanks again for the help!Hi, just copy and paste this command to make sure it is correct.
```
/usr/lib/nux/unity_support_test -p
```

Also have a look at the link I posted above.
Thank you

---

### Post by Ofernand on 2011-09-13
Thank you very much for all this info wildmanne39 and paqman!!! You just made my day! :D

---

### Post by wildmanne39 on 2011-09-13
Hi, your very welcome!

---

### Post by dfarrell07 on 2011-09-14
Might want to mark this thread as solved.

---

### Post by wildmanne39 on 2011-09-15
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

