---
title: "ubuntu 17.10 update problem: not enough space in boot?"
date: 2018-01-07
forum: New to Ubuntu
---

### Post by k28 on 2018-01-07
hi

recently i got ean error while trying to install updates. i allready did sudo apt autoremove and it removed a bunch of things... but now it i still cant update and got the same error. now it wants me set "compress....." and this sounds a bit skatchy...i mean why in the hell i need do such thing manually anyways? why is the bootfolder is not larger by default? i did a fresh installation just a few mount ago.

so my question is: how can i resize the boot folder so dont have to make manual labor in a 2017 OS in the future? thx

---

### Post by Impavidus on 2018-01-07
You don't really need a /boot partition unless you want LVM or full disk encryption, but if you do, the default for /boot is a bit small. Yes, that's not so good. sudo apt autoremove is the right thing to do, it should remove the old kernels taking space in /boot, but maybe it missed something, which sometimes happens like after a release upgrade. Maybe you have to remove an old kernel yourself.

Run```
uname -r
df -h /boot
dpkg --list | egrep 'linux-image|linux-signed-image'
```Post the output here in code tags. The first shows which kernel you're currently running, the second the size of your /boot partition and the third which kernels are installed. Maybe one can be removed.

Resizing the /boot partition is something best done before install.

---

### Post by k28 on 2018-01-07
thx for the quick answer:

```
x:~$ uname -r4.13.0-21-generic
x:~$ df -h /boot
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/sdb2       465M    395M   42M   91% /boot
x:~$ dpkg --list | egrep 'linux-image|linux-signed-image'
rc  linux-image-4.10.0-19-generic              4.10.0-19.21                                amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-35-generic              4.10.0-35.39                                amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-37-generic              4.10.0-37.41                                amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-16-generic              4.13.0-16.19                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-17-generic              4.13.0-17.20                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-19-generic              4.13.0-19.22                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-21-generic              4.13.0-21.24                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-19-generic        4.10.0-19.21                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-35-generic        4.10.0-35.39                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-37-generic        4.10.0-37.41                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-16-generic        4.13.0-16.19                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-17-generic        4.13.0-17.20                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-19-generic        4.13.0-19.22                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-21-generic        4.13.0-21.24                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.13.0.21.22                                amd64        Generic Linux kernel image
rc  linux-signed-image-4.10.0-35-generic       4.10.0-35.39                                amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-37-generic       4.10.0-37.41                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-16-generic       4.13.0-16.19                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-17-generic       4.13.0-17.20                                amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-19-generic       4.13.0-19.22                                amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-21-generic       4.13.0-21.24                                amd64        Signed kernel image generic
ii  linux-signed-image-generic                 4.13.0.21.22                                amd64        Signed Generic Linux kernel image





```

---

### Post by Impavidus on 2018-01-07
Autoremove always keeps 2 kernels, the latest one and an old one as fallback. But your /boot partition is too small to hold 3 kernels, so you have to uninstall one before you can install anything new. As you're running the latest, it should be relatively safe to uninstall 4.13.0-19. But sometimes, very rarely, a kernel gets patched without making it a new package, and when that happens you've lost your only known working kernel.
```
sudo apt purge linux-image-4.13.0-19-generic linux-image-extra-4.13.0-19-generic linux-signed-image-4.13.0-19-generic
```
Unfortunately, you'll have to do this again before the next kernel upgrade.

To make /boot larger, you have to boot a live disk. gparted can make the partition larger, but you may have to make room first. That means shrinking other partitions, which is slow and risky, and if you use LVM (why else would you have a /boot partition?), you need LVM tools for that, which I know nothing about.

BTW, I haven't seen a kernel upgrade for 17.10 past 4.13.0-21. Have you enabled proposed or is my mirror just slow?

---

### Post by k28 on 2018-01-08
ooo jeez. i have to remind myself nexttime i setup a ubuntu machine.

unfortunatly the line above removed something again but i keep getting the same error and cant update.

```
x:~$ sudo apt purge linux-image-4.13.0-19-generic linux-image-extra-4.13.0-19-generic linux-signed-image-4.13.0-19-generic[sudo] Passwort für x: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  linux-image-4.13.0-19-generic* linux-image-extra-4.13.0-19-generic*
  linux-signed-image-4.13.0-19-generic*
0 aktualisiert, 0 neu installiert, 3 zu entfernen und 1 nicht aktualisiert.
Nach dieser Operation werden 235 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] j
(Lese Datenbank ... 240405 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von linux-signed-image-4.13.0-19-generic (4.13.0-19.22) ...
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
Entfernen von linux-image-extra-4.13.0-19-generic (4.13.0-19.22) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-19-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-19-generic
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
Entfernen von linux-image-4.13.0-19-generic (4.13.0-19.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
update-initramfs: Deleting /boot/initrd.img-4.13.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
(Lese Datenbank ... 234194 Dateien und Verzeichnisse sind derzeit installiert.)
Löschen der Konfigurationsdateien von linux-image-extra-4.13.0-19-generic (4.13.0-19.22) ...
Löschen der Konfigurationsdateien von linux-image-4.13.0-19-generic (4.13.0-19.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
Löschen der Konfigurationsdateien von linux-signed-image-4.13.0-19-generic (4.13.0-19.22) ...
x:~$ 





```

i guess you have a slow mirror. i didnt change anything

---

### Post by Impavidus on 2018-01-08
Now I wonder what could be the problem. What do you get from```
df -h /boot
sudo apt update
sudo apt upgrade
```For that last command, press n to cancel the upgrade. I just want to know what it wants to do.

---

### Post by ian-weisser on 2018-01-08
I wonder why an important file has gone missing?
> [COLOR=#000000][FONT=&amp]depmod: FATAL: could not load /boot/System.map-4.13.0-19-generic: No such file or directory[/FONT][/COLOR]
Cleaning up from that may be rather painful in a space-constrained environment.

A listing of files in that environment may be helpful. Perhaps something doesn't belong:
```
ls -la /boot
```

---

### Post by k28 on 2018-01-08
```
x:~$ sudo apt purge linux-image-4.13.0-19-generic linux-image-extra-4.13.0-19-generic linux-signed-image-4.13.0-19-generic
[sudo] Passwort für x: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  linux-image-4.13.0-19-generic* linux-image-extra-4.13.0-19-generic*
  linux-signed-image-4.13.0-19-generic*
0 aktualisiert, 0 neu installiert, 3 zu entfernen und 1 nicht aktualisiert.
Nach dieser Operation werden 235 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] j
(Lese Datenbank ... 240405 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von linux-signed-image-4.13.0-19-generic (4.13.0-19.22) ...
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
Entfernen von linux-image-extra-4.13.0-19-generic (4.13.0-19.22) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-19-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-19-generic
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
Entfernen von linux-image-4.13.0-19-generic (4.13.0-19.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
update-initramfs: Deleting /boot/initrd.img-4.13.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
GRUB-Konfigurationsdatei wird erstellt &#8230;
Linux-Abbild gefunden: /boot/vmlinuz-4.13.0-21-generic
initrd-Abbild gefunden: /boot/initrd.img-4.13.0-21-generic
Windows Boot Manager auf /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Adding boot menu entry for EFI firmware configuration
erledigt
(Lese Datenbank ... 234194 Dateien und Verzeichnisse sind derzeit installiert.)
Löschen der Konfigurationsdateien von linux-image-extra-4.13.0-19-generic (4.13.0-19.22) ...
Löschen der Konfigurationsdateien von linux-image-4.13.0-19-generic (4.13.0-19.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic
Löschen der Konfigurationsdateien von linux-signed-image-4.13.0-19-generic (4.13.0-19.22) ...
x:~$ sudo apt upgrade
[sudo] Passwort für x: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
Die folgenden Pakete werden aktualisiert (Upgrade):
  libpoppler-glib8 libpoppler68 poppler-utils unattended-upgrades
4 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 1.036 kB von 1.073 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 7.168 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] n
Abbruch.
x:~$ 

```

@ian

before this opening this thread i deleted some stuff in the boot partition. i thought they werent that important because they were older then the other identical files by version number.

```
x:~$ ls -la /boot
insgesamt 110094
drwxr-xr-x  6 root root     3072 Jan  8 11:51 .
drwxr-xr-x 34 root root     4096 Jan  7 11:57 ..
-rw-r--r--  1 root root  1500236 Dez 18 17:13 abi-4.13.0-21-generic
-rw-r--r--  1 root root   213028 Dez 18 17:13 config-4.13.0-21-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     1024 Jan  8 11:51 grub
-rw-r--r--  1 root root 53351640 Dez 21 09:08 initrd.img-4.13.0-21-generic
drwx------  2 root root    12288 Sep 24 23:28 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3881597 Dez 18 17:13 System.map-4.13.0-21-generic
drwx------  4 root root     1024 Dez 30 18:51 .Trash-0
-rw-r--r--  1 root root     6861 Nov  3 14:14 ubnfilel.txt
-rw-r--r--  1 root root 29982958 Apr 12  2017 ubninit
-rw-r--r--  1 root root  7569048 Apr 12  2017 ubnkern
-rw-r--r--  1 root root      859 Nov  3 14:14 ubnpathl.txt
-rw-------  1 root root  7821072 Dez 18 17:13 vmlinuz-4.13.0-21-generic
-rw-------  1 root root  7823000 Dez 21 09:08 vmlinuz-4.13.0-21-generic.efi.signed





```

---

### Post by ian-weisser on 2018-01-08
> **k28 said:**
> before this opening this thread i deleted some stuff in the boot partition. i thought they werent that important because they were older then the other identical files by version number.

You have learned an important lesson: Never, ever rm files that are placed/removed by the package manager...because this happens. Every time.

The following space-hogs do not belong in your /boot. They have nothing to do with boot. Investigate, then move or delete them. The package manager did not place any of them.
```

drwx------  2 root root    12288 Sep 24 23:28 lost+found
drwx------  4 root root     1024 Dez 30 18:51 .Trash-0
-rw-r--r--  1 root root     6861 Nov  3 14:14 ubnfilel.txt
-rw-r--r--  1 root root 29982958 Apr 12  2017 ubninit
-rw-r--r--  1 root root  7569048 Apr 12  2017 ubnkern
-rw-r--r--  1 root root      859 Nov  3 14:14 ubnpathl.txt

```

Fixing and then properly uninstalling your broken -19 kernel packages can be done three ways. Which one you want to do is your choice.
1) Reinstall, then remove
2) Place empty dummy files for the package manager to remove.
3) Use an apt --force flag to drop the package from the database, leaving any remaining files in place.

---

### Post by Impavidus on 2018-01-08
The .Trash-0 directory indicates you used the file manager to send some files to trash, which doesn't actually remove them. So if you use the file manager to remove those files/directories ian-weisser mentioned from /boot, don't forget to empty trash. Or simply use the terminal to remove that stuff. With /boot cleaned a bit, you may have just enough space in /boot for a kernel upgrade before autoremoving the third oldest kernel.

BTW, I still don't get why the update manager complained about lack of space in /boot. None of the packages available for upgrade places any files in /boot.

---

### Post by k28 on 2018-01-08
i fixed the problem with deleting the files taht didnt belong in the boot partition and also empting the trash. didnt now that every partiotion has its own trash. i think this happend a while ago. i accidently wrote another lunix distro to boot via unetbootin. the reason why i deleted the files in the first place was that i got the updated error.

do have have to do the other steps? i dont think so.

@impavidus

im not that level of a tech guy.....


anyways thx for the help!

---

### Post by Impavidus on 2018-01-09
If you get no more complaints from the update manager, it should be OK now.

---

