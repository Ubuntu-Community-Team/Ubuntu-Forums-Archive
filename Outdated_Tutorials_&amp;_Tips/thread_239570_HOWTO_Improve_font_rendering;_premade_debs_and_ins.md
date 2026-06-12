---
title: "HOWTO: Improve font rendering; premade debs and instructions to patch yourself"
date: 2006-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by misha680 on 2006-08-19
**New Foreword (Oct 30, 2006):**

Note that since I have upgraded to Edgy I am now using mlind's edgy respository myself (see below) and I think these patches should still work on edgy (actually I know they will because they came from an edgy forum originally), so if you'd like to patch the debs yourself I think the instructions should still work. But I would just use mlind's repos.

**Foreword:**

The instructions below are for people who are using the compiz repositories for their font packages. They might also work for people who are not using the compiz repositories, but if you are not using compiz and want to patch the debs yourselves, you should definitely follow the instructions I made for people not using compiz that are found here:

[http://ubuntuforums.org/showthread.php?p=1402014#post1402014](http://ubuntuforums.org/showthread.php?p=1402014#post1402014)

**Edit: Compiz seems to have taken these font packages out of their repositories since I wrote this howto (several days ago), so the binaries should still work, but please follow the patching instructions in the link above and not the ones below, as you will not be able to get the latest versions of the packages to work  with the patches below in the default ubuntu repositories. Thanks.**

If you would like to add the compiz repositories and try the instructions below (the font packages are a little newer there, not sure what differences this would make, I use compiz on my system so I patched the compiz packages), do this:

```
sudo gedit /etc/apt/sources.list
```

And put the following lines in there:

```
# XGL and Compiz
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```

Also, you can also use the debs that user mlind has graciously made, which are found in his repository:

```
deb http://www.elisanet.fi/mlind/ubuntu dapper fonts
deb-src http://www.elisanet.fi/mlind/ubuntu dapper fonts

```

For edgy:

```
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

```

Thanks mlind!

---

This is based on this thread:

[http://www.ubuntuforums.org/showthread.php?t=178737](http://www.ubuntuforums.org/showthread.php?t=178737)

and also this thread:

[http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647)

but unfortunately those debs do not work after the latest updates, and I did not find any other instructions on how to patch them yourselves.

If you'd just like to install these patched font packages, make a "fonts" directory in your home directory, save the attachments there, open a Terminal, and type the following commands:

```
cd fonts
tar xvjf fontdebs1.tar.bz2
tar xvjf fontdebs2.tar.bz2
sudo dpkg -i *.deb
sudo cp local.conf /etc/fonts
```

Now go to Synaptic Package Manager, search for libfreetype, libcairo, and libxft, and "lock" the package versions by selecting the package files, going to the Package menu and selecting Lock Version. If you are, at any later points in time, having problems with broken packages (which you will at some point after enough updates have been made, especially if new packages in Dapper depend on new version of these font packages that currently do not exist yet, which is why the instructions about patching them yourself are key), just unselect the Lock Version for these packages (click on the "Status" button in Synaptic Package Manager at the bottom left hand corner, click on "Pinned," and you will see all packages you have locked version there) and update and you should be great.

Now, the really fun part:

HOWTO PATCH THEM YOURSELF

1. Get these patches (these are from this thread: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526))

[http://www.magiclinux.org/people/sunmoon1997/patches/cairo/git/0001-freetype-Add-fir-filter-for-subpixel-text-rendering-enabled-by-default.txt](http://www.magiclinux.org/people/sunmoon1997/patches/cairo/git/0001-freetype-Add-fir-filter-for-subpixel-text-rendering-enabled-by-default.txt)
[http://www.magiclinux.org/people/sunmoon1997/patches/libXft/libXft-2.1.10-lcd-cleartype.diff](http://www.magiclinux.org/people/sunmoon1997/patches/libXft/libXft-2.1.10-lcd-cleartype.diff)

Also, the following commands should install everything (I hope) you need to compile the packages:

```
sudo apt-get install build-essential devscripts fakeroot
sudo apt-get build-dep libcairo2 libxft2 libfreetype6
```

2. Now get the code for your packages:

```
mkdir fonts
cd fonts
apt-get source libcairo2 libxft2 libfreetype6
```

3. Change the package version so that Update Manager will not try to update the packages if you lock their versions in synaptic manager. In each package directory, type:

```
dch -i
```

Enter a short descriptive phrase for the changes you have made ("Patched with David Turner's font patches" for example), close the file by pressing Ctrl-X and answering Yes so that the file is saved. Do this for all three packages.

4. Now patch the sources. Here is what you do:

For libcairo, the file you downloaded (0001-something) is actually an email, you need to edit it with gedit and get rid of the headers down to the line that reads 6b0d... Now:

```
cd libcairo-1.2.2 [or whatever version you got]
patch -p1 < pathtoyour0001filewiththeemailheadersremoved
```

Should see no errors here (if you do, perhaps the patch no longer works with some newer version that does not yet exist, or, probably, you just forgot to remove the headers or did not remove them completely, or removed too much, etc.).

For libxft, the patch is already in the right format. Do this:

```
cd libxft-2.1.8.2 [or whatever version you got]
patch -p1 < pathtoyourlibXft-2.1.10-etcpatchfile
```

Should get no errors.

Finally, for libfreetype, it is a little more complicated since there is no patch. Basically, what you do is this. In the directory created (freetype-2.2.1 for example) there will be a file called freetype-2.2.1.tar.bz2. You will extract it, edit the appropriate file, adn then re-create the tar.bz2 archive. Here is how you can do it:

```
cd freetype-2.2.1
tar xvjf freetype-2.2.1.tar.bz2
gedit freetype-2.2.1/src/autofit/aflatin.c

Now edit the file, find the part that reads:
    if ( mode == FT_RENDER_MODE_MONO || mode == FT_RENDER_MODE_LCD )
      other_flags |= AF_LATIN_HINTS_HORZ_SNAP;

Change that to:
    if ( mode == FT_RENDER_MODE_MONO )
      other_flags |= AF_LATIN_HINTS_HORZ_SNAP;

Find the part that reads:
    if ( mode == FT_RENDER_MODE_MONO || mode == FT_RENDER_MODE_LCD_V )
      other_flags |= AF_LATIN_HINTS_VERT_SNAP;

Change that to:
    if ( mode == FT_RENDER_MODE_MONO )
      other_flags |= AF_LATIN_HINTS_VERT_SNAP;

Now, do:
tar cvjf freetype-2.2.1.tar.bz2 freetype-2.2.1/*
rm -rf freetype-2.2.1

```

Also do this to turn on the bytecode interpreter (I think this makes bold fonts better):

```

gedit debian/rules

Find the line that reads:
#        patch -p1 -d $(freetype_u) -i $(patchdir)/030-bytecode-interpreter.diff

And take out the # at the beginning of the line so it reads:
        patch -p1 -d $(freetype_u) -i $(patchdir)/030-bytecode-interpreter.diff

```

Great, you're done patching.

5. Make the packages:

In each package directory, just type:

```
dpkg-buildpackage -rfakeroot -us -uc
```

Wait a while, you will get some errors about missing a private key, but other than that it should succeed, and your packages will be in the fonts parent directory that you created. Enjoy!

Misha

---

### Post by snop on 2006-08-19
Hi,

Thaks for those packages. Those patches are sooo much needed once you get used to them...

When using your packages some dependency errors are found for libcairo2-dev
and libxft-dev (if I remember correctly this happened with your first set of patches too).

Those broken packages must be removed in order to keep packages database sane. This is a little annoying because it's not possible to install some other dev packages (in order to compile some Gnome/Gtk stuff).

Apart from this they seem to work fine.

Thanks

---

### Post by misha680 on 2006-08-19
Hmm... would you mind posting more info about the dependency errors? 

Thanks
Misha

> **snop said:**
> Hi,

Thaks for those packages. Those patches are sooo much needed once you get used to them...

When using your packages some dependency errors are found for libcairo2-dev
and libxft-dev (if I remember correctly this happened with your first set of patches too).

Those broken packages must be removed in order to keep packages database sane. This is a little annoying because it's not possible to install some other dev packages (in order to compile some Gnome/Gtk stuff).

Apart from this they seem to work fine.

Thanks

---

### Post by mlind on 2006-08-19
Dapper's freetype doesn't use any automated patching system and rules file looks ugly as hell. You can put the patch to debian/patches and add this to debian/rules build-stamp: section.
```

# lcd rendering patch
patch -p1 -d $(freetype_u) -i $(patchdir)/libfreetype-no-stem-snapping.patch

```

Compiling libcairo2 with both cairo-1.0.2-embedded-bitmaps.patch (that's included by default) and David Turner's lcd smoothing patch is bit trickier because these patches modify the same codeblocks and won't apply cleanly with each other. Did you drop cairo-1.0.2-embedded-bitmaps.patch ?


For xft packge, you can use dpatch or quilt for easy patching without modifying the original source.

To use quilt
[LIST]
[*]put patch files to debian/patches
[*]create debian/patches/**series** and add names of all patches to this file
[*]add quilt to Build-Depends on debian/control
[*]add to debian/rules:
```

#add to build-stamp: rule
QUILT_PATCHES=debian/patches quilt push -a || test $$? = 2

#add to clean: rule
QUILT_PATCHES=debian/patches quilt pop -a -R || test $$? = 2

```
[/LIST]

---

### Post by misha680 on 2006-08-19
Oops, didn't notice that my libcairo2 source is from the compiz source deb repository:

```
deb-src http://xgl.compiz.info/ dapper main
```

It has no debian/patches at all by default.

Misha

> **mlind said:**
> 
Compiling libcairo2 with both cairo-1.0.2-embedded-bitmaps.patch (that's included by default) and David Turner's lcd smoothing patch is bit trickier because these patches modify the same codeblocks and won't apply cleanly with each other. Did you drop cairo-1.0.2-embedded-bitmaps.patch ?


---

### Post by mlind on 2006-08-19
> **misha680 said:**
> Oops, didn't notice that my libcairo2 source is from the compiz source deb repository:

```
deb-src http://xgl.compiz.info/ dapper main
```

It has no debian/patches at all by default.

Misha

There should be one if you get libcairo2 source package from dapper-updates. I'm not sure if it's worth the effort to get embedded bitmaps patch to work with LCD rendering patch, so I decided to drop it :mrgreen:

---

### Post by misha680 on 2006-08-19
Hmm... so the patches I linked to don't even seem to work with the 1.0.4 version of libcairo at all (at least for me). Did you get them to work? If not, maybe you (or someone else) can let me know what the dependency problems are, so that I can just include those debs from the xgl repos?

Thanks
Misha

> **mlind said:**
> There should be one if you get libcairo2 source package from dapper-updates. I'm not sure if it's worth the effort to get embedded bitmaps patch to work with LCD rendering patch, so I decided to drop it :mrgreen:

---

### Post by mlind on 2006-08-19
> **misha680 said:**
> Hmm... so the patches I linked to don't even seem to work with the 1.0.4 version of libcairo at all (at least for me). Did you get them to work? If not, maybe you (or someone else) can let me know what the dependency problems are, so that I can just include those debs from the xgl repos?

Thanks
Misha

Problem is not with dependencies, but with patches. Both apply fine to clean source, but won't mix together. You've got two ways to go here. Either you drop the cairo-1.0.2-embedded-bitmaps.patch and live without support for embedded bitmaps fonts or fix one of the patches to apply with another.

---

### Post by giuliastro on 2006-08-20
I get ugly "super bold" when using these patches, even when using your local.conf. Also "sudo dpkg-reconfigure fontconfig" doesn't show any options anymore. Any ideas?

---

### Post by pt123 on 2006-08-20
Any screenshots to show the improvements?

---

### Post by Mystique on 2006-08-20
> **giuliastro said:**
>  Also "sudo dpkg-reconfigure fontconfig" doesn't show any options anymore. Any ideas?

dpkg-reconfigure fontconfig-config
then
dpkg-reconfigure fontconfig

---

### Post by snop on 2006-08-20
> 
Hmm... would you mind posting more info about the dependency errors? 


Dont' bother with this. I installed those packages late at night and was tired.

It was just a matter of installing some other dev packages.

Your dev packages install fine now.

Thanks again

---

### Post by misha680 on 2006-08-20
Ok, for those who are not using compiz, and want to patch the debs themselves, I have made the following instructions (I could not find the old patches with a google search, but after  user mlind made his source debs I found them there, thanks a lot mlind :) ). I also attached the end result debs to this post as well (for non-compizers).

If you'd just like to install these patched font packages, make a "fonts" directory in your home directory, save the attachments there, open a Terminal, and type the following commands:

```
cd fonts
tar xvjf fontdebs-ubuntu.tar.bz2
bunzip2 libfreetype*.bz2
sudo dpkg -i *.deb
sudo cp local.conf /etc/fonts
```

Now go to Synaptic Package Manager, search for libfreetype, libcairo, and libxft, and "lock" the package versions by selecting the package files, going to the Package menu and selecting Lock Version. If you are, at any later points in time, having problems with broken packages (which you will at some point after enough updates have been made, especially if new packages in Dapper depend on new version of these font packages that currently do not exist yet, which is why the instructions about patching them yourself are key), just unselect the Lock Version for these packages (click on the "Status" button in Synaptic Package Manager at the bottom left hand corner, click on "Pinned," and you will see all packages you have locked version there) and update and you should be great.

Now, the really fun part:

HOWTO PATCH THEM YOURSELF

1. Get the patches. I have attached the libcairo and libxft patches for the dapper (non-compiz) version of these packages at the end of this post (patches.tar.bz2). To extract them somewhere, go to that directory and type:

```
tar xvjf patches.tar.bz2
```

Also, the following commands should install everything (I hope) you need to compile the packages:

```
sudo apt-get install build-essential devscripts fakeroot
sudo apt-get build-dep libcairo2 libxft2 libfreetype6
```

2. Now get the code for your packages:

```
mkdir fonts
cd fonts
apt-get source libcairo2 libxft2 libfreetype6
```

3. Change the package version so that Update Manager will not try to update the packages if you lock their versions in synaptic manager. 
In each package directory, type:

```
dch -i
```

Type in your comments (specifying you patched files), and then exit by pressing Control X
and make sure you say yes to saving the file.
Make sure you do this for all three.

4. Now patch the sources. Here is what you do:

For libcairo, you can just put the cairo-1.0.4-lcd_rendering.patch file into the debian/patches directory, also need to remove cairo-1.0.2-embedded-bitmaps.patch that is already there.

```
cd libcairo-1.0.4
rm -rf debian/patches/cairo-1.0.2-embedded-bitmaps.patch
cp pathtocairo-1.0.4patchfile debian/patches
```

For libxft, since there is no debian/patches directory, I thought it is easiest to just do this:

```
cd libxft-2.1.8.2 [or whatever version you got]
patch -p1 < pathtoyourlibxft_lcd_rendering.patch
```

Finally, for libfreetype, it is a little more complicated since there is no patch. Basically, what you do is this. In the directory created (freetype-2.2.1 for example) there will be a file called freetype-2.2.1.tar.bz2. You will extract it, edit the appropriate file, adn then re-create the tar.bz2 archive. Here is how you can do it:

```
cd freetype-2.2.1
tar xvjf freetype-2.2.1.tar.bz2
gedit freetype-2.2.1/src/autofit/aflatin.c

Now edit the file, find the part that reads:
    if ( mode == FT_RENDER_MODE_MONO || mode == FT_RENDER_MODE_LCD )
      other_flags |= AF_LATIN_HINTS_HORZ_SNAP;

Change that to:
    if ( mode == FT_RENDER_MODE_MONO )
      other_flags |= AF_LATIN_HINTS_HORZ_SNAP;

Find the part that reads:
    if ( mode == FT_RENDER_MODE_MONO || mode == FT_RENDER_MODE_LCD_V )
      other_flags |= AF_LATIN_HINTS_VERT_SNAP;

Change that to:
    if ( mode == FT_RENDER_MODE_MONO )
      other_flags |= AF_LATIN_HINTS_VERT_SNAP;

Now, do:
tar cvjf freetype-2.2.1.tar.bz2 freetype-2.2.1/*
rm -rf freetype-2.2.1

```

Great, you're done patching.

5. Make the packages:

In the libcairo and lixft directories, type:

```
dpkg-buildpackage -rfakeroot
```

In the libfreetype directory, since we did not use the patching system and just applied the patches ourselves, you must type:

```
dpkg-buildpackage -rfakeroot -b
```

Wait a while, you will get some errors about missing a private key, but other than that it should succeed, and your packages will be in the fonts parent directory that you created. Enjoy!

Misha

---

### Post by reacocard on 2006-08-20
the repos give me a gpg NO_PUBKEY error every time I update. Any way to fix this?

---

### Post by joelones on 2006-08-22
Running dapper and compiz from quinn's repo -- just wondering if others are having the same problems. I cannot seem to find the source versions as per the first post of this thread. Maybe I am missing something...

My source.lst contains:
```
# Xgl and Compiz
deb http://beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info dapper main

```

When I run
```
sudo apt-get source libcairo2 libxft2 libfreetype6
```

These are the versions I download.
```

freetype-2.1.10
libcairo-1.0.4
libxft-2.1.8.2

```

So I can't apply these patches. 
Where are the sources for libcairo-1.2.2 and freetype-2.2.1
Someone please help?

---

### Post by glennric on 2006-08-22
Try
```
deb-src http://ubuntu.compiz.net/ dapper main
```

---

### Post by misha680 on 2006-08-23
Hmm... looks like they have change the repos since I wrote the howto (this past weekend). You could alwyas just use the  howto version and patches for regular ubuntu higher up on this page. not sure what the differences are between the underlying versions, can't imagine it would be huge (but I really don't know, but I used to use the dapper versions and now use the compiz version or at least the ones that were on the repos and I don't really see any difference).

Misha

---

### Post by dude051 on 2006-08-26
After installing the original patches from [http://www.ubuntuforums.org/showthread.php?t=180647]("http://www.ubuntuforums.org/showthread.php?t=180647") I get really terrible font rendering. I've checked to make sure sub-pixel rendering was on ect. but still no go.

I've also now tried your version of the patch Mischa680, but when using your debs I get a lot of dependicies errors :(

```
dude052@dude052-laptop:~/fonts$ sudo dpkg -i *.deb
Password:
(Reading database ... 101117 files and directories currently installed.)
Preparing to replace libcairo2 1.0.4-0ubuntu1.1 (using libcairo2_1.0.4-0ubuntu2_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace libcairo2-dev 1.0.4-0ubuntu1.1 (using libcairo2-dev_1.0.4-0ubuntu2_i386.deb) ...
Unpacking replacement libcairo2-dev ...
Preparing to replace libcairo2-doc 1.0.4-0ubuntu2 (using libcairo2-doc_1.0.4-0ubuntu2_all.deb) ...
Unpacking replacement libcairo2-doc ...
Preparing to replace libfreetype6 2.1.10-1ubuntu3 (using libfreetype6_2.1.10-1ubuntu3_i386.deb) ...
Unpacking replacement libfreetype6 ...
Preparing to replace libfreetype6-dev 2.1.10-1ubuntu3 (using libfreetype6-dev_2.1.10-1ubuntu3_i386.deb) ...
Unpacking replacement libfreetype6-dev ...
Preparing to replace libxft2 2.1.8.2-0ubuntu2 (using libxft2_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft2 ...
Preparing to replace libxft2-dbg 2.1.8.2-0ubuntu2 (using libxft2-dbg_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft2-dbg ...
Preparing to replace libxft-dev 2.1.8.2-0ubuntu2 (using libxft-dev_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft-dev ...
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libfreetype6 (>= 2.2.1); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu3.
dpkg: error processing libcairo2 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libcairo2 (= 1.0.4-0ubuntu2); however:
  Package libcairo2 is not configured yet.
dpkg: error processing libcairo2-dev (--install):
 dependency problems - leaving unconfigured
Setting up libcairo2-doc (1.0.4-0ubuntu2) ...

Setting up libfreetype6 (2.1.10-1ubuntu3) ...

Setting up libfreetype6-dev (2.1.10-1ubuntu3) ...

dpkg: dependency problems prevent configuration of libxft2:
 libxft2 depends on libfreetype6 (>= 2.2.1); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu3.
dpkg: error processing libxft2 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft2-dbg:
 libxft2-dbg depends on libxft2 (= 2.1.8.2-0ubuntu3); however:
  Package libxft2 is not configured yet.
dpkg: error processing libxft2-dbg (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft-dev:
 libxft-dev depends on libxft2 (= 2.1.8.2-0ubuntu3); however:
  Package libxft2 is not configured yet.
dpkg: error processing libxft-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2
 libcairo2-dev
 libxft2
 libxft2-dbg
 libxft-dev
```

I also get two or three broken packages, which apt when wanting to fix basically wants to uninstall the entire system! I fixed by removing/updating in aptitude, but now my fonts are nasty, pic below. I can not find any of the updated libs on any repo's nor can I patch my current libs it seems. Any word on any official patches for these libs or hacks that will work now?

---

### Post by misha680 on 2006-08-27
Alright, sorry about that, I changed one compilation flag (took out the -b on the dpkg-buildpackage command line from the libcairo and libxft packages) and recompiled them. Try the new debs in my ubuntu debs howto post above. However, if the original patches did not work for you, I'm not sure the ones I applied will either since it is just an update of the underlying debs being patched and not of the patches themselves. 

Personally, i also use a ~/.fonts.conf as follows:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

but honestly I am quite blind when it comes to the fonts, I can clearly tell when I lost the patches but when it comes to little things like superbolding I don't even really notice it until someone points it out.

Misha

> **dude051 said:**
> After installing the original patches from [http://www.ubuntuforums.org/showthread.php?t=180647]("http://www.ubuntuforums.org/showthread.php?t=180647") I get really terrible font rendering. I've checked to make sure sub-pixel rendering was on ect. but still no go.

I've also now tried your version of the patch Mischa680, but when using your debs I get a lot of dependicies errors :(

```
dude052@dude052-laptop:~/fonts$ sudo dpkg -i *.deb
Password:
(Reading database ... 101117 files and directories currently installed.)
Preparing to replace libcairo2 1.0.4-0ubuntu1.1 (using libcairo2_1.0.4-0ubuntu2_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace libcairo2-dev 1.0.4-0ubuntu1.1 (using libcairo2-dev_1.0.4-0ubuntu2_i386.deb) ...
Unpacking replacement libcairo2-dev ...
Preparing to replace libcairo2-doc 1.0.4-0ubuntu2 (using libcairo2-doc_1.0.4-0ubuntu2_all.deb) ...
Unpacking replacement libcairo2-doc ...
Preparing to replace libfreetype6 2.1.10-1ubuntu3 (using libfreetype6_2.1.10-1ubuntu3_i386.deb) ...
Unpacking replacement libfreetype6 ...
Preparing to replace libfreetype6-dev 2.1.10-1ubuntu3 (using libfreetype6-dev_2.1.10-1ubuntu3_i386.deb) ...
Unpacking replacement libfreetype6-dev ...
Preparing to replace libxft2 2.1.8.2-0ubuntu2 (using libxft2_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft2 ...
Preparing to replace libxft2-dbg 2.1.8.2-0ubuntu2 (using libxft2-dbg_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft2-dbg ...
Preparing to replace libxft-dev 2.1.8.2-0ubuntu2 (using libxft-dev_2.1.8.2-0ubuntu3_i386.deb) ...
Unpacking replacement libxft-dev ...
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libfreetype6 (>= 2.2.1); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu3.
dpkg: error processing libcairo2 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libcairo2 (= 1.0.4-0ubuntu2); however:
  Package libcairo2 is not configured yet.
dpkg: error processing libcairo2-dev (--install):
 dependency problems - leaving unconfigured
Setting up libcairo2-doc (1.0.4-0ubuntu2) ...

Setting up libfreetype6 (2.1.10-1ubuntu3) ...

Setting up libfreetype6-dev (2.1.10-1ubuntu3) ...

dpkg: dependency problems prevent configuration of libxft2:
 libxft2 depends on libfreetype6 (>= 2.2.1); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu3.
dpkg: error processing libxft2 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft2-dbg:
 libxft2-dbg depends on libxft2 (= 2.1.8.2-0ubuntu3); however:
  Package libxft2 is not configured yet.
dpkg: error processing libxft2-dbg (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft-dev:
 libxft-dev depends on libxft2 (= 2.1.8.2-0ubuntu3); however:
  Package libxft2 is not configured yet.
dpkg: error processing libxft-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2
 libcairo2-dev
 libxft2
 libxft2-dbg
 libxft-dev
```

I also get two or three broken packages, which apt when wanting to fix basically wants to uninstall the entire system! I fixed by removing/updating in aptitude, but now my fonts are nasty, pic below. I can not find any of the updated libs on any repo's nor can I patch my current libs it seems. Any word on any official patches for these libs or hacks that will work now?

---

### Post by dude051 on 2006-08-27
Awesome, no errors anymore! But my fonts still stink... I have no idea why none of these patches arent working, its really bothering me now.

---

### Post by misha680 on 2006-08-27
Hmm... I looked at your screenshot... your fonts really do not look like mine. Did you copy local.conf to /etc/fonts? Restart the computer? Sorry for the simple questions, just wanted to check. Maybe you could also check if you have a .fonts.conf file in your home directory that is overwriting the local.conf settings. I guess finally you could try

```
sudo dpkg-reconfigure fontconfig-config
```

and make sure that autohinting is on on the first screen. That's about all I can think of. 

Misha

> **dude051 said:**
> Awesome, no errors anymore! But my fonts still stink... I have no idea why none of these patches arent working, its really bothering me now.

---

### Post by dude051 on 2006-08-27
Well, doing what you recommeded didn't work, it said something about it not being installed.

```
sudo dpkg-reconfigure fontconfig
```

But that worked, and it was selected. Im running XGL using the session method, and I just logged into a normal gnome session and the fonts look good. Seems it has to be with XGL/Compiz's font rendering. Odd... Thanks for all your help man.

---

### Post by mlind on 2006-08-27
fontconfig-config package exists only for Edgy. For Dapper users, it's fontconfig.

---

### Post by misha680 on 2006-08-27
Well, you could try my compiz font debs, those are the ones I am using (although I tried the dapper ones too, and they work fine as well, but it never hurts to try). I use compiz and just start it like this from a .Xsession file:

```
#!/bin/sh
# Start up Xgl, compiz, and GNOME

# Run Xgl server on :1, on top of normal X
#Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &

# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1

# Start Compiz window manager
#gnome-window-decorator &
cgwd &

# We start compiz now in Startup Programs in Sessions
#compiz gconf &

# Fix Shift-Backspace bug
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

# Start GNOME
exec gnome-session

```

> **dude051 said:**
> Well, doing what you recommeded didn't work, it said something about it not being installed.

```
sudo dpkg-reconfigure fontconfig
```

But that worked, and it was selected. Im running XGL using the session method, and I just logged into a normal gnome session and the fonts look good. Seems it has to be with XGL/Compiz's font rendering. Odd... Thanks for all your help man.

---

### Post by desperado666 on 2006-10-30
ahm wie need noe edgy patched builds :) 

Can someone build some für edgy please? 

THX!

---

### Post by dbbolton on 2010-12-07
Would these patches have any (positive) efftect on xft version 2.1.14? 

I tried to patch it out if curiousity but hunk 1/10 failed on xftglyphs.c. 
```
patching file src/xftfreetype.c
Hunk #1 succeeded at 584 (offset 18 lines).
patching file src/xftglyphs.c
Hunk #1 FAILED at 23.
Hunk #2 succeeded at 42 (offset 2 lines).
Hunk #3 succeeded at 134 (offset 2 lines).
Hunk #4 succeeded at 176 (offset 2 lines).
Hunk #5 succeeded at 197 (offset 2 lines).
Hunk #6 succeeded at 276 (offset 2 lines).
Hunk #7 succeeded at 370 (offset 2 lines).
Hunk #8 succeeded at 382 (offset 2 lines).
Hunk #9 succeeded at 400 (offset 2 lines).
Hunk #10 succeeded at 519 (offset 2 lines).
1 out of 10 hunks FAILED -- saving rejects to file src/xftglyphs.c.rej

```

Here is the reject file:

```

--- src/xftglyphs.c    2006-06-03 18:30:56.000000000 +0800
+++ src/xftglyphs.c    2006-06-19 01:15:28.000000000 +0800
@@ -23,8 +23,23 @@
  */
 
 #include "xftint.h"
-#include <freetype/ftoutln.h>
+#include FT_OUTLINE_H
+#if HAVE_FT_GLYPHSLOT_EMBOLDEN
+#include FT_SYNTHESIS_H
+#endif
+
+
+/* define the following macro if you want to use a small FIR filter to
+ * reduce color fringes for LCD rendering. If undefined, the original
+ * weird pixel-local color balancing algorithm will be used
+ */
+#define  FIR_FILTER
 
+#ifdef FIR_FILTER
+/* note: keep the filter symetric, or bad things will happen */
+static const int   fir_filter[5] = { 0x10, 0x40, 0x70, 0x40, 0x10 };
+
+#else /* !FIR_FILTER */
 static const int    filters[3][3] = {
     /* red */
 #if 0


```

---

