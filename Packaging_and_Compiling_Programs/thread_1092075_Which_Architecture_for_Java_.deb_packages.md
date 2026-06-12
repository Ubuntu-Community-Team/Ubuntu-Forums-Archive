---
title: "Which Architecture for Java .deb packages?"
date: 2009-03-10
forum: Packaging and Compiling Programs
---

### Post by shebangs on 2009-03-10
I have my own java application that I publish into my own Ubuntu repository.

The deb file is created via ant-deb-task with *Architecture=all*.

Is there an architecture I can set this to, on my Ubuntu repository so that any i386/amd64 client can download the same .deb file?


My apt-ftparchive.conf looks like
```

Dir {
        ArchiveDir ".";
        CacheDir "./.cache";
};

Default {
        Packages::Compress ". gzip bzip2";
        Contents::Compress ". gzip bzip2";
};

TreeDefault {
           BinCacheDB "packages-$(SECTION)-$(ARCH).db";
           Directory "pool/$(SECTION)";
           Packages "$(DIST)/$(SECTION)/binary-$(ARCH)/Packages";
           Contents "$(DIST)/Contents-$(ARCH)";
};

Tree "dists/hardy" {
        Sections "nightly release";
        Architectures "i386";
}

```

My apt-release.conf looks like:
```

APT::FTPArchive::Release::Codename "hardy";
APT::FTPArchive::Release::Origin "mytestdomain.com";
APT::FTPArchive::Release::Components "repo";
APT::FTPArchive::Release::Label "repo";
APT::FTPArchive::Release::Architectures "i386";
APT::FTPArchive::Release::Suite "hardy";

```

On my clients, I add following in to sources.list
```
edeb http://192.168.1.1/repo hardy release
```

However, with the above configuration, on a 64bit hardy AMD64 client, apt-get update returns and apt-get install doesn't work:

```
W: Failed to fetch http://192.168.1.1/repo/dists/hardy/release/binary-amd64/Packages.gz  404 Not Found
```


I can confirm my .deb file, if uploaded manually to the server can be installed and runs fine.

Any thoughts?

---

