---
title: "Signing a repo"
date: 2006-07-11
forum: Packaging and Compiling Programs
---

### Post by ketsugi on 2006-07-11
I'm running a small personal repo for bonfire and some other apps, and I'd really like to figure out how to sign it so that users won't get that "cannot be authenticated" warning message. I've tried various guides, none of which have been able to resolve my situation thus far.

Can I get any help from this forum?

---

### Post by az on 2006-07-11
On this page:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
It explains how to sign a repo that will be put onto a cdrom.

The user of the cd will need to import your key before using the archive.  There is no way to authenticate a repository as Ubuntu's unless you have the keys that come with the distro itself.  Since there are no keys that come with the dist that you can use to sign your repo, you will always have to have the user import your keys first.

---

### Post by ketsugi on 2006-07-11
Okay, so this guide didn't really help.

Everything I've done seems to be right. I've set up my GPG key, and created the Release.gpg file.

The problem is that when I do an apt-get update, I get this message:

```
Failed to fetch http://ketsugi.com/ubuntu/dists/dapper/Release
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

My public key is at [http://ketsugi.com/ubuntu/public.key](http://ketsugi.com/ubuntu/public.key) and my repo is ```
deb http://ketsugi.com/ubuntu dapper main
```

---

### Post by mlind on 2006-07-19
I had a little helper script for apt-ftparchive, that signed the repo after Package lists were generated. I've moved to use **reprepro** since, but part of this script could probably help you out. I was using pooled structure.

```

//apt-ftparchive.conf
Dir {
        ArchiveDir              "/home/mlind/ubuntu";
        CacheDir                "/home/mlind/ubuntu/cache";
};

Default {
        Contents::Compress      "gzip";
        Packages::Compress      ". gzip bzip2";
        Sources::Compress       ". gzip bzip2";
};

TreeDefault {
        Directory               "pool/$(SECTION)";
        SrcDirectory            "pool/$(SECTION)";
};

Tree "dists/dapper" {
        Sections                "testing experimental";
        Architectures           "i386 source";
};

```

```

//apt-dapper-release.conf
APT::FTPArchive::Release {
[B]        Codename        "dapper";
        Suite           "dapper";
[/B]        Origin          "mlind";
        Label           "Ubuntu";
        Architectures   "i386 source";
        Components      "testing experimental";
        Description     "Internal dev repo";
};

```

```

#update.sh script

ARCHIVE_DIR=/home/mlind/ubuntu
ARCHIVE_CONF=${ARCHIVE_DIR}/apt-ftparchive.conf
DAPPER_CONF=${ARCHIVE_DIR}/apt-dapper-release.conf

apt-ftparchive generate ${ARCHIVE_CONF}

DIST_ROOT=${ARCHIVE_DIR}/ubuntu/dists/dapper
rm -f ${DIST_ROOT}/Release*
apt-ftparchive -c ${DAPPER_CONF} release ${DIST_ROOT} > ${DIST_ROOT}/Release.tmp
mv ${DIST_ROOT}/Release.tmp ${DIST_ROOT}/Release

**gpg -abs -o ${DIST_ROOT}/Release.gpg ${DIST_ROOT}/Release**

```

Bolded part signs the repository with my gpg key.

---

