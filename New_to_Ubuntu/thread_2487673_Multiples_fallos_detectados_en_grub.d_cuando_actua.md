---
title: "Multiples fallos detectados en grub.d cuando actualizas"
date: 2023-06-12
forum: New to Ubuntu
---

### Post by aorus23 on 2023-06-12
Hello,


I detected a diferents errors in all scripts in /etc/grub.d. This errors in apply when to run this command update-grub when update the OS. 
If remove the quick boot this viewed all errors the boot.


Remove the quick boot


$ cd /etc/grub.d/
$ ls
$ nano 00_header
quick_boot="1&#8221; a quick_boot="0" y lanzamos $ sudo grup-update




I replace
&#8220;x&#8221; &#8594; &#8220;0&#8221;
&#8220;x\&#8221; &#8594; &#8220;\&#8221;
xy &#8594; y
&#8220;xsaved&#8221; &#8594; &#8220;saved&#8221;
&#8220;xtrue&#8221; &#8594; &#8220;true&#8221;
x\ &#8594; \
x$ &#8594; $
x1 &#8594; 1
x* &#8594; *
xC &#8594; C
x&#8221; &#8594; &#8220; ( NO REPLACE text with LINUX&#8221; and conditional [ xxx ] )
&#8220;x0&#8221; &#8594; &#8220;0&#8221;
&#8220;xmenu&#8221; &#8594; &#8220;menu&#8221;
xsimple &#8594; simple
xrecovery &#8594; recovery
xxen &#8594; xen
x0 &#8594; 0
xi?86 &#8594; i?86 (? by 386 and 486 but it can't work. The solution available is fixed 386 and create 486)
xx86_64 &#8594; x86_64






Other detected fails with problems the detection of resolution screen, the possible solution
&#8230; file &#8216;/boot/grub/i386-pc/efi_gop.mod&#8217; no found
&#8230; file &#8216;/boot/grub/i386-pc/eif_uga,mod no found
&#8230; file &#8216;/boot/grub/i386-pc/ieee1275_fb.mod&#8217; no found




Original
# If all_video.mod isn't available load all modules available
# with versions prior to introduction of all_video.mod
cat <<EOF
if [ $feature_all_video_module = "y" ]; then
insmod all_video
else
insmod efi_gop
insmod efi_uga
insmod ieee1275_fb
insmod vbe
insmod vga
insmod video_bochs
insmod video_cirrus
fi
EOF
fi












Solution
# If all_video.mod isn't available load all modules available
# with versions prior to introduction of all_video.mod
cat <<EOF
if [ $feature_all_video_module = "y" ]; then
insmod all_video
else
if [ -f &#8220;/boot/grub/i386-pc/efi_gop.mod&#8221; ]; then
insmod efi_gop
fi
if [ -f &#8220;/boot/grub/i386-pc/efi_uga.mod&#8221; ];then
insmod efi_uga
fi
if [ -f &#8220;/boot/grub/i386-pc/ieee1275_fb.mod&#8221; ]; then
insmod ieee1275_fb
fi
if [ -f &#8220;/boot/grub/i386-pc/vbe.mod&#8221; ]; then
insmod vbe
fi
if [ -f &#8220;/boot/grub/i386-pc/vga.mod&#8221; ]; then
insmod vga
fi
if [ -f &#8220;/boot/grub/i386-pc/video_bochs.mod&#8221; ]; then
insmod video_bochs
fi
if [ -f &#8220;/boot/grub/i386-pc/video_cirrus.mod&#8221; ]; then
insmod video_cirrus
fi
fi
EOF
fi


Other detected fails with ACPI BIOS when run. The possible fail is when load firm UEFI when the BIOS is old.




[ I working ...]


[SPANISH (SPAIN)] It's not available Spain LoCo Teams :( [Europe, Middle East, and African (EMEA) LoCo Teams (ubuntuforums.org)]("https://ubuntuforums.org/forumdisplay.php?f=388")
Hola,
 
 
 He detectado diferentes errores en todos los scripts de /etc/grub.d. Estos errores se aplican cuando se lanza el comando update-grub cuando actualizas el OS. Si quitamos el arranque rápido se muestran todos los fallos de arranque.
 Quitar el modo arranque rápido  
 
 
 $ cd /etc/grub.d/
 $ ls
 $ nano 00_header
 quick_boot="1&#8221; a quick_boot="0" y lanzamos $ sudo grup-update
 
 
 He remplazado  
 &#8220;x&#8221; &#8594; &#8220;0&#8221;
 &#8220;x\&#8221; &#8594; &#8220;\&#8221;
 xy &#8594; y
 &#8220;xsaved&#8221; &#8594; &#8220;saved&#8221;
 &#8220;xtrue&#8221; &#8594; &#8220;true&#8221;
 x\ &#8594; \
 x$ &#8594; $
 x1 &#8594; 1
 x* &#8594; *
 xC &#8594; C
 x&#8221; &#8594; &#8220; ( NO REMPLAZAR texto con LINUX&#8221;  y condicionales [ xxx ] )
 &#8220;x0&#8221; &#8594; &#8220;0&#8221;
 &#8220;xmenu&#8221; &#8594; &#8220;menu&#8221;
 xsimple &#8594; simple
 xrecovery &#8594; recovery
 xxen &#8594; xen
 x0 &#8594; 0
 xi?86 &#8594; i?86 (? para 386 y 486 pero puede no funcionar posible solución fijar 386 y crear 486)
 xx86_64 &#8594; x86_64
 
 
 
 
 Otros fallos detectados problemas con la detección de resolución de la pantalla
 &#8230; file &#8216;/boot/grub/i386-pc/efi_gop.mod&#8217; no found
 &#8230; file &#8216;/boot/grub/i386-pc/eif_uga,mod no found
 &#8230; file &#8216;/boot/grub/i386-pc/ieee1275_fb.mod&#8217; no found
 
 
 Original
 # If all_video.mod isn't available load all modules available
 # with versions prior to introduction of all_video.mod
 cat <<EOF
   if [ $feature_all_video_module = "y" ]; then
     insmod all_video
   else
     insmod efi_gop
     insmod efi_uga
     insmod ieee1275_fb
     insmod vbe
     insmod vga
     insmod video_bochs
     insmod video_cirrus
   fi
 EOF
 fi
 
 
 
 
 
 
 Solución
 # If all_video.mod isn't available load all modules available
 # with versions prior to introduction of all_video.mod
 cat <<EOF
   if [ $feature_all_video_module = "y" ]; then
     insmod all_video
   else
     if [ -f &#8220;/boot/grub/i386-pc/efi_gop.mod&#8221; ]; then
         insmod efi_gop
     fi
     if [ -f &#8220;/boot/grub/i386-pc/efi_uga.mod&#8221; ];then
         insmod efi_uga
     fi
     if [ -f &#8220;/boot/grub/i386-pc/ieee1275_fb.mod&#8221; ]; then
         insmod ieee1275_fb
     fi
     if [ -f &#8220;/boot/grub/i386-pc/vbe.mod&#8221; ]; then
         insmod vbe
     fi
     if [ -f &#8220;/boot/grub/i386-pc/vga.mod&#8221; ]; then
         insmod vga
     fi
     if [ -f &#8220;/boot/grub/i386-pc/video_bochs.mod&#8221; ]; then
         insmod video_bochs
     fi
     if [ -f &#8220;/boot/grub/i386-pc/video_cirrus.mod&#8221; ]; then
         insmod video_cirrus
     fi
   fi
 EOF
 fi
 
 
 Otro fallo detectado problemas con ACPI BIOS cuando arranca posible fallo al cargar firm UFEI cuando es una BIOS antigua.
 
 
 [ Trabajando ...]

---

### Post by QIII on 2023-06-12
Hello.

You have posted in an English-speaking sub-forum.

Please choose between the following:

1.  Try to use English, even if you are not good with it.  We will do everything we can to overcome any language barrier.  We realize that this is a world-wide community of people who come from different backgrounds and we are here to help all.

2.  See if you can find a recently active local community (LOCO) sub-forum [here]("https://ubuntuforums.org/forumdisplay.php?f=183") in your native tongue.  Unfortunately, those forums are not generally very active.

Again, we will try our very best to help if you can use any English at all.

---

### Post by aorus23 on 2023-06-12
Sorry:( I'm new in this community. I'm super n00b :o and my english is regular.
I have create a new post with new title in english
[[ubuntu] The multiples detected fails in grub.d when update (ubuntuforums.org)]("https://ubuntuforums.org/showthread.php?t=2487686")

Sorry but the LoCo Team is not available in my language SPANISH (SPAIN)
[https://ubuntuforums.org/forumdisplay.php?f=388](https://ubuntuforums.org/forumdisplay.php?f=388)

---

### Post by TheFu on 2023-06-13
> **aorus23 said:**
> Sorry:( I'm new in this community. I'm super n00b :o and my english is regular.
I have create a new post with new title in english
[[ubuntu] The multiples detected fails in grub.d when update (ubuntuforums.org)]("https://ubuntuforums.org/showthread.php?t=2487686")

Sorry but the LoCo Team is not available in my language SPANISH (SPAIN)
[https://ubuntuforums.org/forumdisplay.php?f=388](https://ubuntuforums.org/forumdisplay.php?f=388)

It seems that you posted a solution. Is that true?

BTW, there are other areas of the world that use Spanish, so maybe post in one of those LoCo forums?  CentroAmerica has a LoCo here. [https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183) I've seen some posts there the last month.

---

### Post by aorus23 on 2023-06-25
Hi TheFu,

I reply in this post, continue in [https://ubuntuforums.org/showthread.php?t=2487686](https://ubuntuforums.org/showthread.php?t=2487686)

Thnks

---

