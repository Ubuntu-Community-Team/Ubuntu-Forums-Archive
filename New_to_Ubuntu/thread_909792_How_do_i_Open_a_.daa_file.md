---
title: "How do i Open a .daa file?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mattcadu on 2008-09-03
How do I open .daa files?

---

### Post by Diabolis on 2008-09-03
PowerISO is the tool that you need:

[http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/)

---

### Post by iaculallad on 2008-09-03
> **mattcadu said:**
> How do I open .daa files?

DAA is a PowerISO file extension. We need to get the application needed to convert it to an extension compatible with Ubuntu (ISO).

```
sudo wget http://poweriso.com/poweriso-1.1.tar.gz
```

And extract the tarball file:

```
sudo tar zxvf poweriso-1.1.tar.gz
```

Change directory to where you extracted the tarball archive:

```
cd the_extracted_directory
```

and lastly, convert the DAA file to ISO with the format below:

```
./poweriso convert /source_folder/filename.daa -o newfile.iso -ot iso
```

---

### Post by RequinB4 on 2008-09-03
There are a couple of ways to mount ISOs in ubuntu here's a relatively simple CLI one: [http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html](http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html)

Burning ISOs to CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by BLTicklemonster on 2008-10-29
I did that, and all my files and directory names are _________ .

Just an underscore, no letters, no nothing, no extensions.

---

### Post by farkadenear on 2008-11-15
I am having a problem with .daa files myself... I downloaded and installed powerISO

ran this command:

```
farkadenear@otherland:~/Videos$ poweriso convert /home/farkadenear/Videos/"Disney Classics 31-40.part04.daa" -o "Disney Classics 31-40.part04.iso" -ot iso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

/home/farkadenear/Videos/Disney Classics 31-40.part04.daa: The file format is invalid or unsupported.

```

any ideas?

FKN

---

### Post by nhasian on 2008-12-26
i know its an old post, but I just figured out how to do this myself.  if you have an outdated version of poweriso it will not work with the newer images.  you can get the latest version here:

[http://poweriso.com/poweriso-1.3.tar.gz](http://poweriso.com/poweriso-1.3.tar.gz)

---

### Post by BobSands on 2011-09-12
I know this is an old post, but i'm answering because maybe there is someone out there who wants to do it without install something out of the repos:

1. Go to: System -> Administration -> Synaptics
2. Look for "daa2iso" and "gmount-iso", install them
3. Open a Terminal (Applications -> Accessories -> Terminal)
4. Go to the directory where the .daa is and type: 
 $ daa2iso My-file.daa my-new-file.iso
5. Hit Enter
6. Wait until the file is finished
7. Open the Gmount-iso (Applications -> System Tools -> Gmount-iso) and mount the .iso file generated.
8. Use the drive mounted.

---

### Post by sealtrip on 2012-02-14
Thanks BobSands,

Worked like charm in 3 minutes or less. Easiest Ubuntu instruction

---

### Post by oldos2er on 2012-02-14
Closed, necromancy.

---

