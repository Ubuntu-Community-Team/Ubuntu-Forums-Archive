---
title: "Filezilla freezes my lubuntu system"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-24
Hello,


I installed filezilla through terminal but when I run the software it is a behaviour weird. The filezilla freeze my all system! I need use Ctrl+Alt+F1 to through htop kill process relative filezilla.

I googled about this problem and I discovery which my version filezilla it is very old:
```

$ filezilla -v
Reading locale option from /home/eno/.config/filezilla/filezilla.xml
FileZilla 3.21.0, compiled on 2016-08-24
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
$ uname -a
Linux enonet 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

I tried this command:
```

$ add-apt-repository ppa:n-muench/programs-ppa
$ sudo apt-get update 
$ ...........
Ign:15 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu xenial/main i386 Packages
Ign:16 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu xenial/main Translation-en_US
Ign:19 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu xenial/main Translation-en
Fetched 102 kB in 2s (35,9 kB/s)                     
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

From what I understand this error occur because the ppa don't match with my version lubuntu, right?
But, this is the best way to resolve my problem?

Thanks

---

### Post by mörgæs on 2017-12-25
My version in a fully updated 16.04 is 3.15. Why did you want to move away from this one?

---

### Post by sudodus on 2017-12-25
I have problems with Filezilla in Lubuntu 16.04 LTS and use other tools for file transfer, either plain **sftp** or the **file browser** (pcmanfm).

You can enter

```
ssh://user@ip-adress
```

(with the actual user ID and ip-adress) into the box for the current directory in the file browser, and when you have connected, you can save it as a bookmark, which makes it convenient.

---

### Post by sed_faster on 2018-01-07
Happened again. When I turned on filezilla my pc freezed. I use key: Ctrl+Alt+F1 to navigator first terminal and after begin session executed htop program and I receive this report: [https://snag.gy/nGumJU.jpg](https://snag.gy/nGumJU.jpg)
I need killed this process, with PID=4619, to CPU consume bellow and use filezilla.

What can do this error/behaviour?
Thanks

---

### Post by sudodus on 2018-01-07
I have seen several reports about Filezilla being buggy in Ubuntu 16.04 (and it is buggy in my system). What about using another tool instead?

---

### Post by HermanAB on 2018-01-08
If you are using the FTP client, then just use your normal web or file browser.  Pretty much all Linux file browsers support FTP directly.

If you are using the FTP server, rather use vsftp, proftp or ssh.

---

