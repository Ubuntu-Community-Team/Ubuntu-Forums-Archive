---
title: "The multiples detected fails in grub.d when update"
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
quick_boot="1” a quick_boot="0" y lanzamos $ sudo grup-update








I replace
“x” &#8594; “0”
“x\” &#8594; “\”
xy &#8594; y
“xsaved” &#8594; “saved”
“xtrue” &#8594; “true”
x\ &#8594; \
x$ &#8594; $
x1 &#8594; 1
x* &#8594; *
xC &#8594; C
x” &#8594; “ ( NO REPLACE text with LINUX” and conditional [ xxx ] )
“x0” &#8594; “0”
“xmenu” &#8594; “menu”
xsimple &#8594; simple
xrecovery &#8594; recovery
xxen &#8594; xen
x0 &#8594; 0
xi?86 &#8594; i?86 (? by 386 and 486 but it can't work. The solution available is fixed 386 and create 486)
xx86_64 &#8594; x86_64












Other detected fails with problems the detection of resolution screen, the possible solution
… file ‘/boot/grub/i386-pc/efi_gop.mod’ no found
… file ‘/boot/grub/i386-pc/eif_uga,mod no found
… file ‘/boot/grub/i386-pc/ieee1275_fb.mod’ no found








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
if [ -f “/boot/grub/i386-pc/efi_gop.mod” ]; then
insmod efi_gop
fi
if [ -f “/boot/grub/i386-pc/efi_uga.mod” ];then
insmod efi_uga
fi
if [ -f “/boot/grub/i386-pc/ieee1275_fb.mod” ]; then
insmod ieee1275_fb
fi
if [ -f “/boot/grub/i386-pc/vbe.mod” ]; then
insmod vbe
fi
if [ -f “/boot/grub/i386-pc/vga.mod” ]; then
insmod vga
fi
if [ -f “/boot/grub/i386-pc/video_bochs.mod” ]; then
insmod video_bochs
fi
if [ -f “/boot/grub/i386-pc/video_cirrus.mod” ]; then
insmod video_cirrus
fi
fi
EOF
fi




Other detected fails with ACPI BIOS when run. The possible fail is when load firm UEFI when the BIOS is old.








[ I working ...]:popcorn::popcorn:




[SPANISH (SPAIN)] It's not available Spain LoCo Teams  Europe, Middle East, and African (EMEA) LoCo Teams (ubuntuforums.org):(
Hola,




He detectado diferentes errores en todos los scripts de /etc/grub.d. Estos errores se aplican cuando se lanza el comando update-grub cuando actualizas el OS. Si quitamos el arranque rápido se muestran todos los fallos de arranque.
Quitar el modo arranque rápido




$ cd /etc/grub.d/
$ ls
$ nano 00_header
quick_boot="1” a quick_boot="0" y lanzamos $ sudo grup-update




He remplazado
“x” &#8594; “0”
“x\” &#8594; “\”
xy &#8594; y
“xsaved” &#8594; “saved”
“xtrue” &#8594; “true”
x\ &#8594; \
x$ &#8594; $
x1 &#8594; 1
x* &#8594; *
xC &#8594; C
x” &#8594; “ ( NO REMPLAZAR texto con LINUX” y condicionales [ xxx ] )
“x0” &#8594; “0”
“xmenu” &#8594; “menu”
xsimple &#8594; simple
xrecovery &#8594; recovery
xxen &#8594; xen
x0 &#8594; 0
xi?86 &#8594; i?86 (? para 386 y 486 pero puede no funcionar posible solución fijar 386 y crear 486)
xx86_64 &#8594; x86_64








Otros fallos detectados problemas con la detección de resolución de la pantalla
… file ‘/boot/grub/i386-pc/efi_gop.mod’ no found
… file ‘/boot/grub/i386-pc/eif_uga,mod no found
… file ‘/boot/grub/i386-pc/ieee1275_fb.mod’ no found




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
if [ -f “/boot/grub/i386-pc/efi_gop.mod” ]; then
insmod efi_gop
fi
if [ -f “/boot/grub/i386-pc/efi_uga.mod” ];then
insmod efi_uga
fi
if [ -f “/boot/grub/i386-pc/ieee1275_fb.mod” ]; then
insmod ieee1275_fb
fi
if [ -f “/boot/grub/i386-pc/vbe.mod” ]; then
insmod vbe
fi
if [ -f “/boot/grub/i386-pc/vga.mod” ]; then
insmod vga
fi
if [ -f “/boot/grub/i386-pc/video_bochs.mod” ]; then
insmod video_bochs
fi
if [ -f “/boot/grub/i386-pc/video_cirrus.mod” ]; then
insmod video_cirrus
fi
fi
EOF
fi




Otro fallo detectado problemas con ACPI BIOS cuando arranca posible fallo al cargar firm UFEI cuando es una BIOS antigua.




[ Trabajando ...]:popcorn::popcorn:

---

### Post by aorus23 on 2023-06-25
Hi guys,

I repair the files the grub.d and detected more fails in grub-mkconfig. This now it's fixed.

I attachment the zip with the fixed files.

Regards

---

