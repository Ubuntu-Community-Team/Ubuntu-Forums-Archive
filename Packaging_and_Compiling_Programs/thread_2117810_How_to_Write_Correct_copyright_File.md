---
title: "How to Write Correct copyright File?"
date: 2013-02-19
forum: Packaging and Compiling Programs
---

### Post by Malsasa on 2013-02-19
Hello, it is the continuation from previous thread :) 

I wanna my copyright file inside [COLOR="DarkOrange"]debian/usr/share/doc/myapp/[/COLOR] become correct and Ubuntu Software Center detect my DEB as Open Source. I've followed what Debian Packaging Pages here and as addition, Lintian doesn't say any ERROR or WARNING about my copyright file. But Ubuntu Software Center says unknown at License field when open my DEB. 

**Okay, I have done these: **
1) copypaste another DEB's copyright file (I choose only no lintian error DEBs)
2) copypaste Debian Packaging Guide in copyright section examples (more than once)
3) edit them and accomplish the content 

**Problem: **
Ubuntu Software Center doesn't detect my copyright when I open my DEB.

**Question: **
How to write correct copyright file? I need some exact example.

**Attachment:**
This is my copyright file content now: 

```
Format: http://anonscm.debian.org/viewvc/dep/web/deps/dep5.mdwn?revision=174
Upstream-Name: myapp
Upstream-Contact: Ade Malsasa Akbar <teknoloid@gmail.com>
Source: http://malsasa.wordpress.com

Files: *
Copyright: 2013, Ade Malsasa Akbar (teknoloid@gmail.com)
License: GPL-3+
 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.
 .
 This package is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.
 .
 You should have received a copy of the GNU General Public License
 along with this program.  If not, see <http://www.gnu.org/licenses/>.
 .
 On Debian systems, the complete text of the GNU General
 Public License version 3 can be found in `/usr/share/common-licenses/GPL-3'.

 
Files: debian/*
Copyright: 2013, Ade Malsasa Akbar <teknoloid@gmail.com>           
License: GPL-3+
 The Debian packaging information is under the GPL, version 3 or later
 On Debian systems, the complete text of the GNU General Public License
 version 3 can be found in `/usr/share/common-licenses/GPL-3'.

```

---

### Post by Malsasa on 2013-02-19
Hello... Any answer?

---

### Post by BlinkinCat on 2013-02-19
> **Malsasa said:**
> Hello... Any answer?

Hi,

I personally wait for 24 hours before posting again if my thread is unanswered. This is considered normal accepted practice in the Forums. Of course if somebody replies to your question in less than 24 hours then go for it.

Cheers - :p

---

### Post by Malsasa on 2013-02-20
Ow. I am sorry. Thank you so much...

---

### Post by schragge on 2013-02-20
[list]
[*]> **Malsasa said:**
> I wanna my copyright file inside [COLOR="DarkOrange"]debian/usr/share/doc/myapp/[/COLOR] become correctI suppose you're putting your copyright file in the *debian* directory ([highlight]debian/copyright[/highlight])? It gets automatically installed by *debhelper* into [highlight]debian/myapp/usr/share/doc/myapp/[/highlight] when building the package.

[*]Since *Standards-Version: 3.9.3*, the DEP-5 proposal has become part of the Debian policy. You can change the first line to
```

Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/

```

[*]Since all files are identically licensed, the extra section for *Files: debian/** is not needed.
[/list]

Do you get any warnings from lintian for your package?

---

### Post by Malsasa on 2013-02-20
Wow, thank you so much. I am glad there is a user answer me...

First, i used command: **fakeroot dpkg --build debian**. I don't know another command. I followed this tutorial: [http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/). That is the simplest and easiest for me... :) And I don't know debhelper yet.

Second, I have tried your advice as said many users I asked before, I placed copyright at debian/ but USC is still doesn't show **License: Open Source** like another DEBs. 

Third, I will try your formatting. 

Fourth, lintian says W only (no E): 
```
W: myapp: classpath-contains-relative-path usr/lib/myapp/myapp.jar: lib/AbsoluteLayout.jar, lib/beansbinding-1.2.1.jar
W: myapp: binary-without-manpage usr/bin/myapp
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/96x96/apps/logomyapp.png
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/48x48/apps/logomyapp.png
W: myapp: executable-not-elf-or-script usr/bin/myapp
W: myapp: executable-not-elf-or-script usr/lib/myapp/myapp.jar
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/128x128/apps/logomyapp.png
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/64x64/apps/logomyapp.png
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/16x16/apps/logomyapp.png
W: myapp: executable-not-elf-or-script usr/share/icons/hicolor/32x32/apps/logomyapp32.png
W: myapp: executable-not-elf-or-script usr/share/pixmaps/logomyapp.png
W: myapp: maintainer-script-ignores-errors postinst
W: myapp: maintainer-script-empty prerm
W: myapp: maintainer-script-ignores-errors prerm
```
and no one related with copyright. 

Thank you for your support... I wanna go back here again.

---

### Post by Malsasa on 2013-02-20
I have done your formatting in Format: field. And I also deleted last paragraph you said not necessay. But USC still don't show** License: Open Source**. It still say **License: Unknown**.

I wanna my DEB license (open source) appear in USC. Any other solution? Thank you...

:D

---

### Post by schragge on 2013-02-20
> **Malsasa said:**
> First, i used command: **fakeroot dpkg --build debian**. I don't know another command. I followed this tutorial: [http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/). That is the simplest and easiest for me... :) And I don't know debhelper yet.Oh I see. Well, *dpkg --build* **is** the simplest way to create a deb package, but it's very error-prone. It's a quick&dirty method of creating a deb when you're in a hurry, but you probably shouldn't use it if you don't know ins and outs of the Debian package format. The proper way is to create a source package as described in the [Introduction to Debian packaging](http://www.debian.org/doc/devel-manuals#packaging-tutorial) and build it with *dpkg-buildpackage*, or, better yet, with the *debuild* command from the package *devscripts*.

Anyway, as you've already built your package, can you please post the output from the following commands?
```

dpkg-deb -I myapp*.deb md5sums
dpkg-deb -c myapp*.deb

```

---

### Post by Malsasa on 2013-02-20
Wow, thank you so much! This is a good support... These the result: 

**First**
```
master@master:~/Publik/Java/Pemaketan$ dpkg-deb -I debian.deb md5sums
dpkg-deb: `debian.deb' contains no control component `md5sums'
dpkg-deb: error: 1 requested control component is missing
```

**Second**
```
master@master:~/Publik/Java/Pemaketan$ dpkg-deb -c debian.deb
drwxr-xr-x root/root         0 2013-02-20 21:15 ./
drwxr-xr-x root/root         0 2013-02-16 15:49 ./usr/
drwxr-xr-x root/root         0 2013-02-18 16:14 ./usr/bin/
-rwxr-xr-x root/root        50 2013-02-18 14:51 ./usr/bin/myapp
drwxr-xr-x root/root         0 2013-02-16 15:49 ./usr/lib/
drwxr-xr-x root/root         0 2013-02-16 15:52 ./usr/lib/myapp/
-rwxr-xr-x root/root  12134446 2013-02-11 23:20 ./usr/lib/myapp/myapp.jar
drwxr-xr-x root/root         0 2013-02-18 18:56 ./usr/share/
drwxr-xr-x root/root         0 2013-02-18 16:14 ./usr/share/doc/
drwxr-xr-x root/root         0 2013-02-20 21:18 ./usr/share/doc/myapp/
-rw-r--r-- root/root       134 2013-02-18 16:16 ./usr/share/doc/myapp/AUTHORS
-rw-r--r-- root/root      1036 2013-02-20 21:18 ./usr/share/doc/myapp/copyright
-rw-r--r-- root/root       158 2013-02-19 12:58 ./usr/share/doc/myapp/changelog.gz
drwxr-xr-x root/root         0 2012-01-08 09:51 ./usr/share/icons/
drwxr-xr-x root/root         0 2013-02-18 19:03 ./usr/share/icons/hicolor/
drwxr-xr-x root/root         0 2012-01-08 09:51 ./usr/share/icons/hicolor/32x32/
drwxr-xr-x root/root         0 2013-02-18 18:48 ./usr/share/icons/hicolor/32x32/apps/
-rwxr-xr-x root/root      1210 2013-02-18 18:48 ./usr/share/icons/hicolor/32x32/apps/logomyapp32.png
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/128x128/
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/128x128/apps/
-rwxr-xr-x root/root      3781 2013-02-18 19:03 ./usr/share/icons/hicolor/128x128/apps/logomyapp.png
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/64x64/
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/64x64/apps/
-rwxr-xr-x root/root      2380 2013-02-18 19:03 ./usr/share/icons/hicolor/64x64/apps/logomyapp.png
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/96x96/
drwxr-xr-x root/root         0 2013-02-18 19:06 ./usr/share/icons/hicolor/96x96/apps/
-rwxr-xr-x root/root      2814 2013-02-18 19:05 ./usr/share/icons/hicolor/96x96/apps/logomyapp.png
drwxr-xr-x root/root         0 2013-02-18 18:45 ./usr/share/icons/hicolor/16x16/
drwxr-xr-x root/root         0 2013-02-18 18:45 ./usr/share/icons/hicolor/16x16/apps/
-rwxr-xr-x root/root       682 2013-02-18 18:44 ./usr/share/icons/hicolor/16x16/apps/logomyapp.png
drwxr-xr-x root/root         0 2012-01-08 09:51 ./usr/share/icons/hicolor/48x48/
drwxr-xr-x root/root         0 2013-02-18 18:47 ./usr/share/icons/hicolor/48x48/apps/
-rwxr-xr-x root/root      1858 2013-02-18 18:46 ./usr/share/icons/hicolor/48x48/apps/logomyapp.png
drwxr-xr-x root/root         0 2013-02-18 00:50 ./usr/share/applications/
-rw-r--r-- root/root       216 2013-02-18 00:50 ./usr/share/applications/myapp.desktop
drwxr-xr-x root/root         0 2013-02-18 18:56 ./usr/share/pixmaps/
-rwxr-xr-x root/root      1858 2013-02-18 18:46 ./usr/share/pixmaps/logomyapp.png
drwxr-xr-x root/root         0 2013-02-19 08:11 ./usr/share/menu/
-rw-r--r-- root/root       112 2013-02-18 18:50 ./usr/share/menu/myapp
master@master:~/Publik/Java/Pemaketan$ 
```

Wow, your 2 commands here are new for me. It is advanced, and so interesting. Can you explain simply unto me? Ehm, are 2 commands give you what do you need? Thank you su much :D

---

### Post by Malsasa on 2013-02-20
And your initial 2 packaging command are completely new for me. Wow, advanced :) I am glad to know

1) dpkg-buildpackage
2) debuild

I am a beginner in packaging, so these 2 commands is so valuable for me :)

You gave me the simplest explanation so I understand easily :) Please keep that...

Thank you from Indonesia ;)

---

### Post by schragge on 2013-02-20
```

dpkg-deb: `debian.deb' contains no control component `md5sums'

```
Well, I don't know for sure if USC checks the MD5 hash of the copyright file, but this could be the culprit.

This is how *md5sums* from [thread=2112000]a package of mine[/thread] looks like:
```

73d99e2b44743d05895551476823e7b0  usr/bin/doc
b039a38030c632cfc65338d05d1a293a  usr/share/doc/doc/changelog.gz
61e854a18f10cee73420220b341ebc0d  usr/share/doc/doc/copyright
be0964cf640caa9ea6a67e1ed9b59b21  usr/share/man/man1/doc.1.gz

```

Try to generate *md5sums* for your package like this
```

cd debian
find usr -type f -exec md5sum {} + >DEBIAN/md5sums

```

Then check that DEBIAN/md5sums exists and contains the MD5 hashes of all files in your package and rebuild the package.

---

### Post by Malsasa on 2013-02-20
Waaaaah, a great clue for mee... Thank you. 

Maybe it is the reason why USC doesn't detect my copyright.

I wanna try it soon, and back here to inform you what happen. 

Absolutely new way for me to reveal MD5 from files. Thank you for commands :D

---

### Post by Malsasa on 2013-02-20
> **schragge said:**
> Try to generate *md5sums* for your package like this
```

cd debian
find usr type -f -exec md5sum {} + >DEBIAN/md5sums

```

Then check that DEBIAN/md5sums exists and contains the MD5 hashes of all files in your package and rebuild the package.

Hello, this is the result of that command: 

```
master@master:~/Publik/Java/Pemaketan/debian$ find usr type -f -exec md5sum {} + >DEBIAN/md5sums
find: unknown predicate `-f'
```

How to fix this? Thank you...

---

### Post by Malsasa on 2013-02-20
Oh, your command seems incorrect. I do: 

**find usr -type f -exec md5sum {} + >DEBIAN/md5sums**

And I found a md5 file in DEBIAN. It contains: 

```
0883f7e0c511adbf54577291a0204a1e  usr/bin/otodidak
f75ed71ee4abbc1e1dcead71d145769a  usr/lib/otodidak/otodidak.jar
9e05ae854fc4e9c2121d655a90b8703e  usr/share/doc/otodidak/AUTHORS
e93aa9984ff592e47f9142c8f4ddc577  usr/share/doc/otodidak/copyright
6e17f3ab695f42e6b24f3c75705fcc74  usr/share/doc/otodidak/changelog.gz
ff5fb2613db299f1345bd83627a558c3  usr/share/icons/hicolor/32x32/apps/logootodidak.png
7d7e3f761ca381ae396f6c202838c9ab  usr/share/icons/hicolor/128x128/apps/logootodidak.png
c0ff43dc92c567ab4dbd1a6081d8e802  usr/share/icons/hicolor/64x64/apps/logootodidak.png
b245fc5e9cff5f18cbac98948f9f0c89  usr/share/icons/hicolor/96x96/apps/logootodidak.png
cc5d27f56a830a465b6bb6908a29993e  usr/share/icons/hicolor/16x16/apps/logootodidak.png
6466464e39e7a1af2b0f49d720bb9153  usr/share/icons/hicolor/48x48/apps/logootodidak.png
2b5db695bed16dd0b4f713accbc2505d  usr/share/applications/otodidak.desktop
6466464e39e7a1af2b0f49d720bb9153  usr/share/pixmaps/logootodidak.png
da60f8c91a5d27d0198c2c5f5b74d6c9  usr/share/menu/otodidak

```

And no error. But after building it again, my license is still not appear in USC :)

Any other suggestion?

---

### Post by Malsasa on 2013-02-20
Oh, your command seems incorrect. I do: 

**find usr -type f -exec md5sum {} + >DEBIAN/md5sums**

And I found a md5 file in DEBIAN. It contains: 

```
0883f7e0c511adbf54577291a0204a1e  usr/bin/otodidak
f75ed71ee4abbc1e1dcead71d145769a  usr/lib/otodidak/otodidak.jar
9e05ae854fc4e9c2121d655a90b8703e  usr/share/doc/otodidak/AUTHORS
e93aa9984ff592e47f9142c8f4ddc577  usr/share/doc/otodidak/copyright
6e17f3ab695f42e6b24f3c75705fcc74  usr/share/doc/otodidak/changelog.gz
ff5fb2613db299f1345bd83627a558c3  usr/share/icons/hicolor/32x32/apps/logootodidak.png
7d7e3f761ca381ae396f6c202838c9ab  usr/share/icons/hicolor/128x128/apps/logootodidak.png
c0ff43dc92c567ab4dbd1a6081d8e802  usr/share/icons/hicolor/64x64/apps/logootodidak.png
b245fc5e9cff5f18cbac98948f9f0c89  usr/share/icons/hicolor/96x96/apps/logootodidak.png
cc5d27f56a830a465b6bb6908a29993e  usr/share/icons/hicolor/16x16/apps/logootodidak.png
6466464e39e7a1af2b0f49d720bb9153  usr/share/icons/hicolor/48x48/apps/logootodidak.png
2b5db695bed16dd0b4f713accbc2505d  usr/share/applications/otodidak.desktop
6466464e39e7a1af2b0f49d720bb9153  usr/share/pixmaps/logootodidak.png
da60f8c91a5d27d0198c2c5f5b74d6c9  usr/share/menu/otodidak

```

And no error. But after building it again, my license is still not appear in USC :)

Any other suggestion?

---

### Post by schragge on 2013-02-21
> **Malsasa said:**
> Oh, your command seems incorrect. I do: 

**find usr -type f -exec md5sum {} + >DEBIAN/md5sums**Yes, you're right. Sorry for that. I've edited the post.

> Any other suggestion?I'm afraid I can't help you any further. :( Your *copyright* file looks OK to me. Check it yourself with [the specification](http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/). I have zero experience with USC, it's even not installed on my system (Debian wheezy).

You've got wrong permissions on some .png files, but that shouldn't be the problem here. To silence some lintian warnings, you can remove *execute* bit from them:
```

find usr/share/ -name \*.png -exec chmod -x {} +

```But this has nothing to do with UCS not recognising the copyright.

[highlight]Update.[/highlight]
One thing, however, I can still suggest is this. Install the package *libconfig-model-tkui-perl*, then run
```

config-edit -application dpkg-copyright -ui none -config-file DEBIAN/copyright

``` and watch for any error messages. This should check your copyright file for policy conformance.
You also can start *config-edit* interactively like this
```

config-edit -application dpkg-copyright -config-file DEBIAN/copyright

```then it works as an editor.

---

### Post by Malsasa on 2013-02-21
Wow, very advanced. Okay, okay. Thank you so much. It is my first experience in this Ubuntuforums International. Good experience for me...
;)

Okay, maybe it is the time for release. It is not a big problem if my copyright is not appear in USC :)

Thank you from Indonesia. 

Maybe when I get my problem fixed in USC, I will get back here, and say it is solved.

---

