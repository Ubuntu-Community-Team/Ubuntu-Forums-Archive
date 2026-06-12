---
title: "External USB disk not mounting"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by anbelo on 2012-06-24
Hi,

My Ubuntu 11.04 is no longer mounting the 1TB external USB disk I was using. It just appears in Disk Utility as "/dev/sdb".

Any help in order to recover the data would be greatly appreciated. Thank you.

---

### Post by sudodus on 2012-06-24
I understand that the drive could be mounted from Ubuntu before. In that case

- Is it mounting in some other computer? With linux, with Windows?

- What about the S.M.A.R.T. information, that you should be able to check with the disk analyzing tool
```
palimpsest
``` in a command line terminal?

- Please post the output of the command ```
sudo fdisk -lu
```

- Try to repair it with an appropriate tool

```
sudo e2fsck -f /dev/sdXY
``` where X is probably b and Y is probably 1, but use the values found from the fdisk command above, when booted from a linux CD or USB drive for ext2, ext3, ext4 or 

```
chkdsk /f
``` booted from Windows if NTFS or FAT32.

---

### Post by anbelo on 2012-06-25
Hi sudodus, and thank you for your reply.

> **sudodus said:**
> I understand that the drive could be mounted from Ubuntu before.

Yes, that's right. It had only one FAT32 partition, as I used it to share data between Linux, Mac and Windows.

> **sudodus said:**
> In that case

- Is it mounting in some other computer? With linux, with Windows?

No, it isn't. My Mac's Disk Utility shows a "invalid BS_jmpBoot in boot block ..." error.

> **sudodus said:**
> - What about the S.M.A.R.T. information, that you should be able to check with the disk analyzing tool
```
palimpsest
``` in a command line terminal?

SMART status says the disk is OK (green circle), device /deb/sdb, and "not partitioned" (I'm translating from Spanish).

> **sudodus said:**
> - Please post the output of the command ```
sudo fdisk -lu
```

(If you need something translated, just ask).

```
Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador de disco: 0x1df21df1

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   104856254    52428096    7  HPFS/NTFS
La partición 1 no se inició en el limite físico del sector
/dev/sda2       104857600   314570751   104856576   83  Linux
/dev/sda3       314572798  1953523711   819475457    5  Extendida
La partición 3 no se inició en el limite físico del sector
/dev/sda5       314572800  1901092863   793260032   83  Linux
/dev/sda6      1901094912  1949329407    24117248    b  W95 FAT32
/dev/sda7      1949331456  1953523711     2096128   82  Linux swap / Solaris

    Hay una etiqueta Mac válida en este disco.
    Desafortunadamente fdisk(1) no puede manejar estos discos
    Use pdsik o parted para modificar la tabla de partición
    No obstante tenga en cuenta algunos consejos:
    1. fdisk destruirá su contenido al escribir.
    2. Compruebe que este disco NO sea una parte vital
       de un grupo de volúmenes. (De lo contrario puede borrar
       también los demás discos, si no están duplicados.)

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
```


> **sudodus said:**
> - Try to repair it with an appropriate tool

```
sudo e2fsck -f /dev/sdXY
``` where X is probably b and Y is probably 1, but use the values found from the fdisk command above, when booted from a linux CD or USB drive for ext2, ext3, ext4 or 

```
chkdsk /f
``` booted from Windows if NTFS or FAT32.

Then, as the disk was formatted in FAT32, should I use chkdsk rather than e2fsck? But how, if Windows doesn't mount it?

Thank you very much again.

---

### Post by sudodus on 2012-06-25
You are right, if Windows does not mount it, you cannot use chkdsk to repair it.

It might be possible to use ***Testdisk*** to repair the partition table. Otherwise I think you must resort to ***PhotoRec***, which can recover most common file types from the information on the drive without the help of a partition table or file allocation table.

You can download several repair boot disks (as iso files) from the internet containing Testdisk and PhotoRec.

[[COLOR="Red"]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

### Post by NikTh on 2012-06-25
Partition Table can be repaired with Parted (or Gparted) also ,** but i am not sure** [COLOR=Red]if files will be destroyed[/COLOR].

---

### Post by sudodus on 2012-06-25
> **NikTh said:**
> Partition Table can be repaired with Parted (or Gparted) also ,** but i am not sure** [COLOR=Red]if files will be destroyed[/COLOR].
I think that means making new partitions (so that the content is wiped).

---

### Post by anbelo on 2012-06-25
I have used TestDisk to repair the partition table, and it's strange, because now I can use the disk with my Mac, but still not with Ubuntu.

This is the current output of "fdisk -lu":

```
Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador de disco: 0x1df21df1

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   104856254    52428096    7  HPFS/NTFS
La partición 1 no se inició en el limite físico del sector
/dev/sda2       104857600   314570751   104856576   83  Linux
/dev/sda3       314572798  1953523711   819475457    5  Extendida
La partición 3 no se inició en el limite físico del sector
/dev/sda5       314572800  1901092863   793260032   83  Linux
/dev/sda6      1901094912  1949329407    24117248    b  W95 FAT32
/dev/sda7      1949331456  1953523711     2096128   82  Linux swap / Solaris

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00000000

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *          63  1953520064   976760001    c  W95 FAT32 (LBA)
```

---

### Post by sudodus on 2012-06-25
> **anbelo said:**
> I have used TestDisk to repair the partition table, and it's strange, because now I can use the disk with my Mac, but still not with Ubuntu.

This is the current output of "fdisk -lu":

```
...
Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00000000

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *          63  1953520064   976760001    c  W95 FAT32 (LBA)
```

Good, that at least one computer can read it. Then I suggest that you ***backup*** the files that need to be saved.

The next step is to test if Windows can see it and in that case run [FONT="Courier New"]chkdsk /f[/FONT]

Otherwise I suggest that you use ***gparted*** to delete the partition, make a new one and make a file system in it, FAT32 if that suits you well, but maybe you want something more robust, NTFS if it should be accessed by 'any' operating system, otherwise maybe ext3.

---

### Post by anbelo on 2012-06-27
Yesterday I did a backup of my data, and then ran chkdsk; although it said no errors had been found, now Ubuntu does mount the disk! Well, I'm not complaining :)

By the way, this is what I did to repair the partition table with TestDisk:

[http://forum.cgsecurity.org/phpBB3/partitions-disappear-after-quick-search-t14.html](http://forum.cgsecurity.org/phpBB3/partitions-disappear-after-quick-search-t14.html)

Thank you very much for your help!

---

### Post by monica69 on 2012-10-14
Hi, I have a problem with a ubuntu virtual machine (9.04) running in a 64 bits PC.
When I try to connect a external disk (1 TB, 3.0) I go to VM/Removable Devices and there I can see the disk, then I connect (disconnect from host)... the message is:
the connection was unsucessfull, the device is currently in use.
Before this, I disconnect the disk in the windows computer.

Maybe a problem of ubuntu version (too old?) in VM settings/USB controller, the USB compatibility is only 1.1 or 2.0

I had used this virtual machine with the external disk before in another computer (64 bits but less sophisticated, I guess, with less powerful processor)... maybe is it the problem.

Thanks for the help

Monica69

---

### Post by Insomn1a on 2012-10-14
> **monica69 said:**
> Hi, I have a problem with a ubuntu virtual machine (9.04) running in a 64 bits PC.
When I try to connect a external disk (1 TB, 3.0) I go to VM/Removable Devices and there I can see the disk, then I connect (disconnect from host)... the message is:
the connection was unsucessfull, the device is currently in use.
Before this, I disconnect the disk in the windows computer.

Maybe a problem of ubuntu version (too old?) in VM settings/USB controller, the USB compatibility is only 1.1 or 2.0

I had used this virtual machine with the external disk before in another computer (64 bits but less sophisticated, I guess, with less powerful processor)... maybe is it the problem.

Thanks for the help

Monica69

Hi Monica, you should create a new thread if you are needing help for a separate issue other then what is contained in this thread.

---

