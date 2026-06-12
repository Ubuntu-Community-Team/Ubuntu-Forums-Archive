---
title: "No puedo entrar a Windows desde GRUB pero si a Linux"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by sheylashy on 2012-02-16
¡Buenas tardes!

Tengo un portátil en el que venía Windows 7 preinstalado, instalé Linux (Ubuntu) en otra partición del mismo disco duro en el que venía Windows. Para elegir el Sistema Operativo utilizaba GRUB hasta que un día ya no me dejaba entrar a Windows. Actualicé el GRUB y directamente ya no podía elegir Windows. He probado LILO y al encender la máquina me decía: "MBR 1FA" o algo así. 

Despues de leer muchos foros y probar varias cosas sigue sin funcionar. He reinstalado Linux y tampoco ha detectado el otro SO. He probado con el disco de recuperación de Windows y no puedo restaurar el sistema. Tambien he probado el comando MBR y tampoco.

Os pongo el resultado de fdisk -l


[FONT=Verdana]Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x53389d23

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          51      408576   27  Desconocido
La partición 1 no termina en un límite de cilindro.
/dev/sda2              51       38881   311899136    7  HPFS/NTFS
/dev/sda3           38881       46176    58593750   83  Linux
/dev/sda4           46176       77825   254220593+   5  Extendida
/dev/sda5           46177       46662     3903795   82  Linux swap / Solaris
/dev/sda6           46663       77825   250316766    7  HPFS/NTFS[/FONT]



¡Muchas gracias de antemano!

---

### Post by N00b-un-2 on 2012-02-16
escriba en Ingles por favor.  Esta es un forum que habla Ingles.

Now as far as your problem goes, either something changed on Windows and now it won't play nice with GRUB, or GRUB got hosed.  The first thing I would recommend is reinstalling GRUB and then doing
```
sudo update-grub
```

Then try rebooting into Windows.  If you still don't have any luck, you should try using your Windows recovery to repair startup.  I know not every computer that has a recovery partition is capable of doing so, but it's worth a shot.  The next thing you need to do if you can't accomplish a start up repair from recovery is to get your hands on an actual Windows install disk and run the repair from there.

If that doesn't work, you will probably need to open up a CMD prompt from the install disk and run chkdsk /f on your C: drive.

Good luck

---

### Post by sheylashy on 2012-02-16
Excuse me but where should I post this in Spanish? I've seen posts in Spanish around... 

I already tried updating and nothing... :S

What does chkdsk /f do exactly? Doesn't it check errors on the disk? 

Thanks.

---

### Post by josephmills on 2012-02-16
> **sheylashy said:**
> ¡Buenas tardes!

Tengo un portátil en el que venía Windows 7 preinstalado, instalé Linux (Ubuntu) en otra partición del mismo disco duro en el que venía Windows. Para elegir el Sistema Operativo utilizaba GRUB hasta que un día ya no me dejaba entrar a Windows. Actualicé el GRUB y directamente ya no podía elegir Windows. He probado LILO y al encender la máquina me decía: "MBR 1FA" o algo así. 

Despues de leer muchos foros y probar varias cosas sigue sin funcionar. He reinstalado Linux y tampoco ha detectado el otro SO. He probado con el disco de recuperación de Windows y no puedo restaurar el sistema. Tambien he probado el comando MBR y tampoco.

Os pongo el resultado de fdisk -l


[FONT=Verdana]Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x53389d23

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          51      408576   27  Desconocido
La partición 1 no termina en un límite de cilindro.
/dev/sda2              51       38881   311899136    7  HPFS/NTFS
/dev/sda3           38881       46176    58593750   83  Linux
/dev/sda4           46176       77825   254220593+   5  Extendida
/dev/sda5           46177       46662     3903795   82  Linux swap / Solaris
/dev/sda6           46663       77825   250316766    7  HPFS/NTFS[/FONT]



¡Muchas gracias de antemano!



In English 
> Good afternoon!

I have a laptop that came pre-installed Windows 7, I installed Linux (Ubuntu) on another partition on the same disk drive where Windows came. To choose the OS using GRUB until a day and would not let me into Windows. And directly upgraded the GRUB could not choose Windows. I tried LILO and turn the machine told me: "MBR 1fA" or something.

After reading many forums and trying various things still not working. I reinstalled Linux and has not detected the other OS. I have tested with Windows recovery disk and I can not restore the system. I also tried the command and not MBR.

I put the result of fdisk -l


[FONT=Verdana]Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x53389d23

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          51      408576   27  Desconocido
La partición 1 no termina en un límite de cilindro.
/dev/sda2              51       38881   311899136    7  HPFS/NTFS
/dev/sda3           38881       46176    58593750   83  Linux
/dev/sda4           46176       77825   254220593+   5  Extendida
/dev/sda5           46177       46662     3903795   82  Linux swap / Solaris
/dev/sda6           46663       77825   250316766    7  HPFS/NTFS[/FONT]
 

many thanks in advadced !





there is also [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)

---

### Post by sheylashy on 2012-02-16
Thank you very much. I just thought the Spanish forums were here. Ops. Sorry...

---

### Post by N00b-un-2 on 2012-02-16
I understand Spanish just fine, that's not the issue.  If I don't understand something there is always Google Translate.  The point was, there is a spanish speaking forum.  I'm just trying to help, but you'll find a lot more people able to help you by using the language of the forum, hence the reason why it's in the forum guidelines.  When in Rome as they say...

As for the problem of not being able to boot into Windows, there are quite a few things that can cause this.  The first being changes to GRUB.  The next most common one would be Windows updates not installing correctly.  I've almost ALWAYS had issues booting into Windows on a dual boot after installing a service pack for example.  If you mount your NTFS partitions in Linux, sometimes they get messed up from improperly unmounting or if you hard reboot without shutting down properly.
Hence the reason why your next move might be to run chkdsk /f on C:
If you can't get ahold of a copy of Windows or your recovery environment is not capable of getting you to a CMD prompt, you might want to download Hiren's Boot CD which has a bootable Windows like environment.  Think of it like a very primitive Live CD for Windows.  I'm not really clear on where Hiren's Boot CD stands in terms of licensing so I have a feeling I may get a talking to from one of the Mods.

When you attempt to boot into Windows, does it give you any error codes or does it simply not let you boot into it at your GRUB screen

---

### Post by sheylashy on 2012-02-16
I meant, thank you for translating and posting it again. :) 

Aha, I understand... Well, it must have been for that reason, I had problems with an external hard drive that didn't work properly and made Linux to crash so I didn't reboot properly several times.

I'll try chdsk /f and I'll post the results. 

Don't worry about Hiren's Boot CD I already have it.

Thanks.

---

### Post by sheylashy on 2012-02-16
I tried with Hiren's Boot CD's Mini Windows XP and in the CMD prompt I can use says: X:\ 

I've tried changing to C:\ by "cd C:\" but it won't let me. I tried doing the chkdsk /f anyway and it says the disk is "write protected".

---

