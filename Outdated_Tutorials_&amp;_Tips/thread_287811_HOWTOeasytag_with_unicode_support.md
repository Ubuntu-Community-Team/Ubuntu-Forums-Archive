---
title: "HOWTO:easytag with unicode support"
date: 2006-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by sup on 2006-10-29
As decribed in this [bug]("https://launchpad.net/bugs/54136"), easytag in Ubuntu does not handle unicode filenames correctly. It is possible to selfcompile to correct that, so I made a little howto.

**_NOTE_**:mp4 support is disabled in Ubuntu version of Easytag and I do not enable it as well - I do not need it and it is not straightforward (as far as I understand it includes selfcompiling of other stuff).
**_NOTE2:_**this works for me, it is not very clean and may not work for you

1. download easytag, id3lib and a patch for id3lib from [http://easytag.sourceforge.net/]("http://easytag.sourceforge.net/") - latest version are 1.99.12 for easytag and 3.8.3, patch is named patch_id3lib_3.8.3_UTF16_writing_bug.diff
2. ```
sudo apt-get build-dep easytag
```
(if anything complains, you need to enable Ubuntu'S source repositories)
3. untar easytag and enter the directory, then
```
easytag ./configure --disable-mp4
```
4. ```
sudo apt-get remove libid3-3.8.3-dev libid3-3.8.3c2a
```
5.untar id3lib somewhere. place patch to the same directory where id3lib direcotry si stored. i.e. you dowloaded both the files to $HOME/Desktop and then run (with Destkop as working directory) ```
tar -xvf id3lib-3.8.3.tar.gz
``` - that created directory $HOME/Desktop/id3lib-3.8.3. So place the diff file to $HOME/Desktop.
6.```
cat patch_id3lib_3.8.3_UTF16_writing_bug.diff |patch -p0
```
7.enter id3lib directory
```
./configure
```
8.```
make
```
9.```
sudo checkinstall
```
10.```
sudo make uninstall
```
11.```
sudo dpkg -i id3lib*deb
```
12. enter easytag directory once again
.```
make
```
13.```
sudo checkinstall
```
14.```
sudo make uninstall
```
15.```
sudo dpkg -i easytag*deb
```
16.```
sudo apt-get install libid3-3.8.3c2a
```
17.```
sudo cp /usr/local/lib/libid3-3.8.so.3 /usr/lib/
```
18. run easytag with easytag (or through menu), find an mp3 file and try to rename it to something like &#283;&#353;&#269;&#345;&#382;ýáí (or whatever strange signs you use) and save it. It should not complain and rhythmbox should then display them properly. If it worked, unicode in easytag works correctly for you, if not... well, good luck in finding your way around, but try asking here.

_**NOTE**_: Update manager might prompt you to upgrade Easytag to repository version. Fire up Synaptic, find package Easytag, click on it and in menu package, force your version and hope it will shut up. For me it did, with easytag, with others, I have not had that much luck...

BTW:steps 10. 11. and 14. 15. might be ridiculous and unnecessary, but I do them anyway, they should make no harm

---

### Post by uziel on 2006-11-01
After following the steps (with a few problems I managed to overcome) easyTAG didn't see any mp3 files in directories. Then downgraded the package to repo's 1.99.12-1 version and it works perfectly. So I guess only the steps about libid3 are necessary.

---

### Post by sup on 2006-11-01
Um, you might be right, I never thought of it since I always (I have actually done this twice, with edgy and with dapper) compiled Easytag together with id3lib. Yet when I think of it, it was not needed. Well, at least it work although it contains uneccesary steps...

---

### Post by dpm on 2006-11-04
> **sup said:**
> Um, you might be right, I never thought of it since I always (I have actually done this twice, with edgy and with dapper) compiled Easytag together with id3lib. Yet when I think of it, it was not needed. Well, at least it work although it contains uneccesary steps...

It is not necessary to recompile easytag. The patch only applies to id3lib, so patching the id3lib sources and recompiling the library is all that is required.

I believe an easier and cleaner way is to download the id3lib debian package sources, apply the patch, rebuild the debian package and reinstall it.

An alternative set of instructions for this HOWTO may be then as follows:

** Note: I've tried this on my Edgy system, so I cannot make sure this works in Dapper. In theory it should make no difference, since IIRC both Dapper and Edgy come with the same version of id3lib.**

1. Install all dependencies required to build debian packages:
```
sudo apt-get install build-essential binutils cpp cpio dpkg-dev file gcc libc6-dev make patch perl dh-make debhelper devscripts fakeroot lintian
```2. Install the dependencies required to compile the id3lib sources:
```
sudo apt-get build-dep libid3-3.8.3c2a
```3. Get the id3lib sources:
```
mkdir ~/build && cd build
apt-get source libid3-3.8.3c2a
```4. Get the required patch from the easytag project website: [http://prdownloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?download]("http://prdownloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?download%5D%5D") or [http://downloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?modtime=1145137972&big_mirror=0](http://downloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?modtime=1145137972&big_mirror=0), **copy it to ~/build** and apply the patch:
```
cd id3lib3.8.3-3.8.3
patch -p1 < ../patch_id3lib_3.8.3_UTF16_writing_bug.diff
```5. Write something sensible on the debian changelog (e.g. '*Applied UTF16 writing patch from the easytag project*.' or something like that), and MOST IMPORTANTLY **change the package version in the changelog**. This is a couple of lines above where you were writing the changelog comment. You can change it to something like a non-mantainer version number, so that next time there is a new ubuntu package your version will be replaced by the official package. In my case, I appended .0.0.dpm.0 to the version, so it now reads: (3.8.3-5.1.0.0.dpm.0), where dpm is my user name. If you do not change the version in the changelog, 'dpkg-buildpackage' in the next step will not work. Executing the following script will open the debian changelog in your predetermined editor. Modify the changelog as explained and save the changes.
```
dch -n
```6. Now build the package:
```
dpkg-buildpackage -us -uc -rfakeroot
```At this point, if everything worked, you must have a **libid3-3.8.3c2a_3.8.3-5.1.0.0.dpm.0_i386.deb** or similar package under the ~/build directory. You now only have to install it (if you versioned your package differently, substitute libid3-3.8.3c2a_3.8.3-5.1.0.0.dpm.0_i386.deb on the following lines by the name of your package):
```
cd ..
sudo dpkg -i libid3-3.8.3c2a_3.8.3-5.1.0.0.dpm.0_i386.deb
```Enjoy.

P.S.- Any comments or corrections will be greatly appreciated.

---

### Post by brcre on 2006-11-10
Questions on some errors I've encountered:

/home/brcre/Downloads/id3lib-3.8.3 $ sudo checkinstall
sudo: checkinstall: command not found

/home/brcre/Downloads/id3lib-3.8.3 $ sudo dpkg -i id3lib*deb
dpkg: error processing id3lib*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 id3lib*deb

/home/brcre/Downloads $ sudo apt-get build-essential binutils cpp cpio dpkg-dev file gcc libc6-dev make pa tch perl dh-make debhelper devscripts fakeroot lintian
E: Invalid operation build-essential

/home/brcre/Downloads/build/id3lib3.8.3-3.8.3 $ dch -n
bash: dch: command not found

dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found

Currently using Dapper Drake.

---

### Post by dpm on 2006-11-10
> **brcre said:**
> 
/home/brcre/Downloads/id3lib-3.8.3 $ sudo checkinstall
sudo: checkinstall: command not found

That means the **checkinstall** program cannot be found, most probably because it is not installed. You need to install it ('sudo apt-get install checkinstall'). Note though, that you don't need checkinstall if you are following the method I described.

> **brcre said:**
> 
/home/brcre/Downloads/id3lib-3.8.3 $ sudo dpkg -i id3lib*deb
dpkg: error processing id3lib*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 id3lib*deb
I'm guessing you are trying to install the id3lib package before having created it. This won't work until you have created the package.

> **brcre said:**
> 
/home/brcre/Downloads $ sudo apt-get build-essential binutils cpp cpio dpkg-dev file gcc libc6-dev make pa tch perl dh-make debhelper devscripts fakeroot lintian
E: Invalid operation build-essential

My mistake, I'm sorry, this should have been
```
sudo apt-get [COLOR=Red]install[/COLOR] build-essential binutils cpp cpio dpkg-dev file gcc libc6-dev make pa tch perl dh-make debhelper devscripts fakeroot lintian
```I've corrected it on my previous post now.

> **brcre said:**
> 
/home/brcre/Downloads/build/id3lib3.8.3-3.8.3 $ dch -n
bash: dch: command not found

dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found


This two steps will not work until you have installed the **fakeroot** and **dch** programs. You must install programs before using them. This is a consequence of the previous tep having failed. Try again Step 1 of my method and it all should work.

---

### Post by brcre on 2006-11-11
I think it worked....maybe.....
/home/brcre/Downloads/build $ sudo dpkg -i libid3-3.8.3c2a_3.8.3-5.1.0.0.brcre.0_i386.deb
(Reading database ... 94015 files and directories currently installed.)
Preparing to replace libid3-3.8.3c2a 3.8.3-5.1.0.0.brcre.0 (using libid3-3.8.3c2a_3.8.3-5.1.0.0.brcre.0_i386.deb) ...
Unpacking replacement libid3-3.8.3c2a ...
Setting up libid3-3.8.3c2a (3.8.3-5.1.0.0.brcre.0) ...

However easytag still opens up with version number: 1.99.11 and the tags I change are not recognized in Rhythmbox 0.9.3.1 So I believe I'm still using the old version and not the one I built.
I'm sure it's something simple that I've missed...., but what and where I don't know.

---

### Post by dpm on 2006-11-12
> **brcre said:**
> I think it worked....maybe.....
/home/brcre/Downloads/build $ sudo dpkg -i libid3-3.8.3c2a_3.8.3-5.1.0.0.brcre.0_i386.deb
(Reading database ... 94015 files and directories currently installed.)
Preparing to replace libid3-3.8.3c2a 3.8.3-5.1.0.0.brcre.0 (using libid3-3.8.3c2a_3.8.3-5.1.0.0.brcre.0_i386.deb) ...
Unpacking replacement libid3-3.8.3c2a ...
Setting up libid3-3.8.3c2a (3.8.3-5.1.0.0.brcre.0) ...


This looks good. It seems the package was built correctly and it installed without trouble.

> **brcre said:**
>  However easytag still opens up with version number: 1.99.11

You have rebuilt the id3lib package, and not EasyTag. Therefore the version number of EasyTag won't change, which is what you want. The id3lib is a library which EasyTag uses for reading and writing ID3 tags. It is (was) developed independently of EasyTag. EasyTag just provides a nice GUI to id3lib, which offers the low-level (i.e. reading/writing ID3 tags functionality).

The main problem we are trying to solve is that id3lib does not handle Unicode (oversimplifying: non-English) characters, and as a consequence, EasyTag cannot handle them either. 

Therefore, we must apply a patch to fix id3lib, not EasyTag. Once id3lib "works", EasyTag will also "work". In order to do this:

1. We get the patch to fix id3lib.
2. We download the sources of the id3lib package and apply the patch.
3. We rebuild the patched sources and obtain a new package.
4. We install the package we have created.
5. If everything works, EasyTag will "pick up" the "fixed" version of id3lib and we'll be able to read/write Unicode characters in ID3 tags.

> **brcre said:**
> and the tags I change are not recognized in Rhythmbox 0.9.3.1

Let's not mix things up. We are trying to fix Unicode support in EasyTag only. I would leave Rhythmbox for the moment and first try an easy check to see if everything worked.

1. Open an mp3 file in EasyTag and start editing its tag.
2. Write an Unicode character (some character specific to your language: ß or à, for example)
3. Save the tag.
4. If the tag could be saved, the patched id3lib worked. If a message appears telling you that "this version of id3lib does not support Unicode" or similar, we'll have to start anew and see what went wrong.
5. And as a double check, even if no message appeared, I would close EasyTag, reopen the mp3 file just edited and see if the Unicode character is still displayed correctly.

I hope this helps.

Cheers.

---

### Post by brcre on 2006-11-13
You are right.  The change is working fine when tested as you described.  It wasn't what I was trying to fix, but that was my bad.  I appreciate all your help especially since that is the first thing I've ever built and installed.  Previously I just selected from Synaptic and called that good. BC

---

### Post by foxy123 on 2006-11-14
I cannot find this patch :( where is it? the link above does not work and I do not see it on easytag's website...

---

### Post by dpm on 2006-11-14
> **foxy123 said:**
> I cannot find this patch :( where is it? the link above does not work and I do not see it on easytag's website...

It is in the download area of the easytag project, under the id3lib section. Try this link (it worked for me a few minutes ago):

[http://downloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?modtime=1145137972&big_mirror=0](http://downloads.sourceforge.net/easytag/patch_id3lib_3.8.3_UTF16_writing_bug.diff?modtime=1145137972&big_mirror=0)

Cheers.

---

### Post by foxy123 on 2006-11-14
OK, it looks like a mirror is down, so I managed to download it directly. However when I tried to apply it to the Dapper source of id3lib, I've got the following:

```
:~/build/id3lib3.8.3-3.8.3$ patch -p1 < ../patch_id3lib_3.8.3_UTF16_writing_bug.diff
patching file ChangeLog
Reversed (or previously applied) patch detected!  Assume -R? [n]

```

And this is from the source changelog:

> 2006-02-17  Jerome Couderc

    * Patch from Spoon to fix UTF-16 writing bug
      [http://sourceforge.net/tracker/index.php?func=detail&aid=1016290&group_id=979&atid=300979](http://sourceforge.net/tracker/index.php?func=detail&aid=1016290&group_id=979&atid=300979)

Is it the same patch? Has it been applied already?

---

### Post by dpm on 2006-11-14
OK, now the original mirror seems to be up and running again. And I believe we are talking about the same patch.

Hmm... I don't know what your problem could be. On the sources I downloaded, the patch had not been applied.

---

### Post by sup on 2006-11-24
BTW: if you are using freedb search included in Eastytag, you might have noticed it stopped working recently. Then you might be interested in this [patch]("http://downloads.sourceforge.net/easytag/patch_19912_use_gnudb_manual_search.diff?use_mirror=osdn") that changes database server form freedb to gnudb, so search is wokring again.

the patch applies the same way as the patch for ut8 bug

---

### Post by dyntryx on 2006-12-09
Just a heads-up...

> Is it the same patch? Has it been applied already?

Yes, the patch seems to have been applied now.  At this point, you just need to follow [desp]("http://ubuntuforums.org/member.php?u=48790")'s directions, but ignore the patch process.  Read his post [here]("http://ubuntuforums.org/showpost.php?p=1714180"), and follow steps 1 through 3.  Skip steps 4 and 5.  Step 6 should be modified as follows:

```
cd ..
sudo dpkg -i libid3-3.8.3c2a_3.8.3-6_i386.deb
```

Note the "3.8.3-6".  Previously, it was "3.8.3-5", thus the version change due to the added patch and whatever other changes may have been made.  Hope this clears things up for anyone still struggling.  Further comments and questions welcome. :)

---

### Post by foxy123 on 2006-12-10
> **dyntryx said:**
> Just a heads-up...



Yes, the patch seems to have been applied now.  At this point, you just need to follow [desp]("http://ubuntuforums.org/member.php?u=48790")'s directions, but ignore the patch process.  Read his post [here]("http://ubuntuforums.org/showpost.php?p=1714180"), and follow steps 1 through 3.  Skip steps 4 and 5.  Step 6 should be modified as follows:

```
cd ..
sudo dpkg -i libid3-3.8.3c2a_3.8.3-6_i386.deb
```

Note the "3.8.3-6".  Previously, it was "3.8.3-5", thus the version change due to the added patch and whatever other changes may have been made.  Hope this clears things up for anyone still struggling.  Further comments and questions welcome. :)

my mistake. I had a Debian source in my sources.list, that is why I got Debian source package instead of Ubuntu.

---

### Post by dpm on 2006-12-10
> **dyntryx said:**
> Just a heads-up...



Yes, the patch seems to have been applied now.  At this point, you just need to follow [desp]("http://ubuntuforums.org/member.php?u=48790")'s directions, but ignore the patch process.  Read his post [here]("http://ubuntuforums.org/showpost.php?p=1714180"), and follow steps 1 through 3.  Skip steps 4 and 5.  Step 6 should be modified as follows:

```
cd ..
sudo dpkg -i libid3-3.8.3c2a_3.8.3-6_i386.deb
```Note the "3.8.3-6".  Previously, it was "3.8.3-5", thus the version change due to the added patch and whatever other changes may have been made.  Hope this clears things up for anyone still struggling.  Further comments and questions welcome. :)

Let's not mix things up here.

AFAIK (please correct me if I'm wrong), the version you are talking about (**3.8.3-6**) is only available in the **Feisty** repositories and in **Debian unstable**. The version in **Edgy** and **Dapper** is (**3.8.3-5**) Therefore, I'd like to point out that:

1.-  **The steps I was describing in my HOWTO are still valid for Edgy**, as the bug has not yet been fixed at the time of writing (the steps might also be valid for Dapper, but no one has reported having tried it yet). Also note that in step 6 I do not say that you should literally copy  the name of the package, but use the name of the package you've created.

2.- _If you are using Feisty_, the bug has been fixed, so _there is no need to follow the HOWTO_, as the package from the repos already includes the fix.

3.- An alternative to the HOWTO is to download and install the 3.8.3-6 version of the libid3 package either temporarily enabling the Feisty repos or directly from 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libid3-3.8.3c2a](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libid3-3.8.3c2a) . I will update the HOWTO with this information if I've got time to do it.

4.- Feisty is a development version in alpha stage at the time of writing. Use it at your own risk. I personally would not recommend it to anyone yet.

Cheers.

---

### Post by idlewild on 2007-01-17
Thanks for pointing out the patch. Heres a deb I've compiled properly (rather than checkinstall) so it's just an easy double click and install.

---

