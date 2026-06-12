---
title: "Missing files in fpc source package for crosscompile"
date: 2016-10-22
forum: Programming Talk
---

### Post by rainer8 on 2016-10-22
Hi,

I am running Lazarus / FreePascal under Ubuntu and want to cross compile my project as a Win32 an / or Win64 application.

I installed lazarus running

 ```
apt-get install lazarus 
```

The project runs perfect under Ubuntu. But when I select Windows as target OS, I get error messages of missing units etc. I found a tutorial in the lazarus wiki. [http://wiki.lazarus.freepascal.org/Cross_compiling_for_Win32_under_Linux](http://wiki.lazarus.freepascal.org/Cross_compiling_for_Win32_under_Linux)

My problem is that the make command doesn't work. I put the same question in the Lazarus forum and I got help ([http://forum.lazarus.freepascal.org/index.php?topic=34405.msg225535#msg225535](http://forum.lazarus.freepascal.org/index.php?topic=34405.msg225535#msg225535)).

 So far so good. My problem is, that the fpc-source-3.0.0_3.0.0+dfsg-2_all.deb (installed with the apt-get command) doesn't contain all files I need. When I take all files from here [https://sourceforge.net/projects/lazarus/files/Lazarus%20Linux%20amd64%20DEB/Lazarus%201.6/](https://sourceforge.net/projects/lazarus/files/Lazarus%20Linux%20amd64%20DEB/Lazarus%201.6/) the tutorial from the Lazarus wiki works fine.

But now, when I try to update my complete Ubuntu installation (apt-get distupgrade), I get several errors because of conflicts with some packages installed with fpc, fpc-source, lazarus.

Is there a chance to put the missing fpc-source-files (contained in the "sourceforge" file) in the "official" Ubuntu fpc-source-deb file, so the "normal" installation using "apt-get install lazarus"?

Where do I have to report it?

Regards,

Rainer

---

### Post by Olav on 2016-10-22
It has been ages since I last looked at FreePascal. But does this link help?

[http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu](http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu)

---

### Post by rainer8 on 2016-10-22
> **Olav said:**
> It has been ages since I last looked at FreePascal. But does this link help?

[http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu](http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu)

No, this instruction doesn't work :-(

(Some of the lines I have translated. May they differ from the original messages)
```
W: http://www.hu.freepascal.org/lazarus/dists/lazarus-stable/Release.gpg: Signature by key 13A5146226002BBC25E32D23670C48C26A11800F uses weak digest algorithm (SHA1)
E: Failed to fetch http://www.hu.freepascal.org/lazarus/dists/lazarus-stable/Release  No Hash entry in Release file /var/lib/apt/lists/partial/www.hu.freepascal.org_lazarus_dists_lazarus-stable_Release which is considered strong enough for security purposes
E: Some index files could not be downloaded. They would be ignored or older were used instead.
Reading paketlists ... done
E: The value »lazarus-stable« is for APT::Default-Release invalid, such a release is not available in the paket sources.

```

---

