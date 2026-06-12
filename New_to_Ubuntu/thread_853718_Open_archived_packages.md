---
title: "Open archived packages"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-08
Hi,
When I install packages in Synaptic Manager, they go to my Archive folder as .tar files. I would appreciate some help in opening and running these packages, as I seem to be having a brain freeze where tar files are involved. Can someone please help?
Thank you
philk949

---

### Post by iaculallad on 2008-07-08
> **philk949 said:**
> Hi,
When I install packages in Synaptic Manager, they go to my Archive folder as .tar files. I would appreciate some help in opening and running these packages, as I seem to be having a brain freeze where tar files are involved. Can someone please help?
Thank you
philk949

Here, try reading this [page]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually") on how to untar archive files and how to install them.

---

### Post by ChameleonDave on 2008-07-08
> **philk949 said:**
> Hi,
When I install packages in Synaptic Manager, they go to my Archive folder as .tar files. I would appreciate some help in opening and running these packages, as I seem to be having a brain freeze where tar files are involved. Can someone please help?
Thank you
philk949
Do they really?  How did you make them do that??

Ubuntu uses Debian packages, with a .deb extension.  I am very surprised to hear you have .tar files in /var/cache/apt/archives.

To install a Debian package, use either of the following commands:

```

cd /var/cache/apt/archives/
sudo dpkg -i **PACKAGENAME.deb**

```

```

cd /var/cache/apt/archives/
sudo gdebi **PACKAGENAME.deb**

```

Alternatively, use can use the graphical installer, either by navigating to the folder in your file manager and opening the package with GDebi, or by entering the following command:

```

cd /var/cache/apt/archives/
gdebi-gtk **PACKAGENAME.deb**

```

To open a tar archive, use the following:

```

cd /var/cache/apt/archives/
tar -vxf **ARCHIVENAME.tar**
cd **ARCHIVENAME**
ls

```

If the archive is also compressed with gzip, then add the letter "z" to the options.  If bzip2, then "j".

---

