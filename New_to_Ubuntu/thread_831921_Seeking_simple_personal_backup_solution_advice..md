---
title: "Seeking simple personal backup solution advice."
date: 2008-06-17
forum: New to Ubuntu
---

### Post by athowell on 2008-06-17
Hi. :confused:, here.

I'm looking for a simple personal backup solution.  Can anyone with good experience please recommend one they have had good luck with.  The package repository has a lot of them to choose from.

The following options would be great: (something like Norton ghost but open source).

-Boot-able backup restore process
-Image Ubuntu partitions for burning to DVD
-User friendly GUI

I don't really need incremental support.  I just want to image my Ubuntu box now that I finally got all the hardware working as I'm not sure I could recreate my successes easily.  (Lots of late nights and foggy memory)

ADV*thanks*ANCE

---

### Post by ryanparrish on 2008-06-17
A simple search in synaptic package manager yielded Backup PC and a search in Add Remove program yielded Home User Backup one could start their and see if they like  the program

---

### Post by rraj.be on 2008-06-17
you can store all packages in the form of local repos's as you save softwares in windows.

here is an excelent GUI application for helping you.

```
[Aptoncd]("pittman.ws/articles/howto/partimage.html")
```

To install this type this in terminal

```
sudo apt-get install aptoncd

```
this will be much useful to create local repos in GUI way.

Then you can use the created Local repo disks to install your packages During installation.

To image your entire partition i will recommend partimage  [PARTIMAGE is just a backup and not BOOTABLE.]

To create your own custom linux bootcd you can use remastersys which coul be somewhat cryptic at this time for you.
But you can refer here if you need it.

```
[[COLOR="Blue"]www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html[/COLOR]]("www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")
```



to install type partimage

```
sudo apt-get install partimage
```

Here is excellent tutorial regarding partimage.

```
[linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.htm]("linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.htm")
```

---

