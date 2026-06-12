---
title: "Burning problems (iso's)"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Dalston on 2008-09-08
Hello im having problems burning iso's,  I have tried Gnomebaker, Brasero, K3B and Imgburn through wine using 2 different types of cd's.  I have no trouble burning audio files just cant burn iso's.  Im using ubuntu 8.04.  Someone help me out please cuz this is baffling the hell out of me.

Thanks in advance

---

### Post by OffAxis on 2008-09-08
are the checksums on the iso files valid?

---

### Post by Dalston on 2008-09-08
How do I check checksums?  2 of the iso's im trying to burn are the ubuntu 8.04 cd's so I presume they are ok.

---

### Post by indytim on 2008-09-08
Basics...... : you are selecting the burn iso image option in k3b right?:)

IndyTim

---

### Post by Dalston on 2008-09-08
> **indytim said:**
> Basics...... : you are selecting the burn iso image option in k3b right?:)

IndyTim

I dont know what the basics...... comment is about.  Theres no need to look down your nose at me.

Yes I tried burning an image.

---

### Post by overdrank on 2008-09-08
> **Dalston said:**
> How do I check checksums?  2 of the iso's im trying to burn are the ubuntu 8.04 cd's so I presume they are ok.

Hi and this link may help
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Oldsoldier2003 on 2008-09-08
+1

Plus isos can be finicky. I also suggest burning the iso at the lowest supported speed of your burner. Also make sure you are using a 700MB cd of decent quality- don't use the old 650MB cd you found buried under the windows 95 manual in your bottom desk drawer

---

### Post by knix on 2008-09-08
Usually you can just double click on the iso and burn it without a special program.
Or are they burning but not working?

---

### Post by Dalston on 2008-09-08
> **overdrank said:**
> Hi and this link may help
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks im looking at it now but dont understand what I have to do.

> **Oldsoldier2003 said:**
> +1

Plus isos can be finicky. I also suggest burning the iso at the lowest supported speed of your burner. Also make sure you are using a 700MB cd of decent quality- don't use the old 650MB cd you found buried under the windows 95 manual in your bottom desk drawer

Yeah I have been trying to burn at 1x speed but it always fails,  I have tried Verbatim cd's and today I tried burning with philips cd-rw all with no success.
  
> **knix said:**
> Usually you can just double click on the iso and burn it without a special program.
Or are they burning but not working?

They are failing at the beginning of the burn process,  I have tried right clicking and also opening up the applications and choosing burn image.

---

### Post by knix on 2008-09-08
honestly, I always burn mine at ~24x.

---

### Post by Dalston on 2008-09-08
Can you burn iso images in ubuntu 8.04?

---

### Post by OffAxis on 2008-09-08
> Thanks im looking at it now but dont understand what I have to do.
Just open a terminal, navigate to the folder where the downloaded ubuntu iso is, and run the command
```
md5sum isoname.iso
```
where isoname.iso = the actual filename of the iso file.

Then compare what it spits out to the known file size of the ubuntu iso files listed here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You can compare it by hand, or download the MD5checksum file (which is just a text file with that code in it) to the same folder and run
```
md5sum -c MD5SUMS
```
where MD5SUMS = the name of the checksum file.

If it matches then no part of the file was lost during download and your problem lies elsewhere.
If it doesn't match then that's your problem; you'll need to re-download it.

---

### Post by Dalston on 2008-09-09
Im still having trouble can you talk me through it, the file I need to check is in the folder at /media/disk-2.  Thanks for your help.

---

### Post by indytim on 2008-09-09
[withdrawn thread]

---

