---
title: "HOWTO: Build a newer VLC in Feisty and (possibly) Edgy"
date: 2007-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by anon32 on 2007-05-20
VLC is a general all-purpose media player that is relatively popular. Feisty and Edgy both have a relatively recent version of VLC (0.8.6a) in their universe backports, but with some interesting limitations built-in (namely, disabled console framebuffer). This guide will provide a step-by-step tutorial to construct a (somewhat) valid set of .deb's for VLC 0.8.6b with framebuffer. 

Before we do anything, create a subdirectory in home to hold all the trash that'll be created during the process:
```
mkdir ~/vlc-src-tmp && cd ~/vlc-src-tmp
```
First off, we'll need the basic development tools to compile VLC:
```
sudo apt-get install build-essential automake autoconf devscripts debhelper subversion
```
Then, we'll need the packages that VLC depends on (might want to keep track of the packages installed here, there's no automated way to clean em up):
```
sudo apt-get build-dep vlc
```
Next, we'll need the current repository version of VLC and the source code:
```
sudo apt-get install vlc
sudo apt-get source vlc
```
Lastly, we'll need the source code for the current release of VLC:
```
wget http://download.videolan.org/pub/videolan/vlc/0.8.6b/vlc-0.8.6b.tar.gz
```

Now that we have all the prerequisites,
```
tar xzf vlc-0.8.6b.tar.gz #unpack the new VLC
cp -r vlc-0.8.6.release/extras/faad2 vlc-0.8.6b/extras #copy faad2 over from original source
cd vlc-0.8.6b/extras
svn co svn://svn.videolan.org/x264/trunk x264 #retreive x264 over svn
cd ../../ #go back to top dir
rm -f vlc-0.8.6b.tar.gz #delete tarball to make room for new one
tar cvzf vlc-0.8.6b.tar.gz vlc-0.8.6b/ #build a usable tarball
cd vlc-0.8.6.release
uupdate -u vlc-0.8.6b.tar.gz -v 0.8.6.release2 #debianize new version
cd ../vlc-0.8.6.release2 #go to new source location
rm -f debian/patches/* #kill useless patches

```

Thought you were done? Those were just preparations :p. Now that we have the code nice and proper, it's time to edit the debian control file (just use a text editor):

In debian/rules, change the line
```
        --disable-fb \

```
[INDENT]to[/INDENT] 
```
        --enable-fb \

```
and comment out (add a '#' at the beginning) these lines as they will cause failures:
```
        QUILT_PATCHES=debian/patches quilt push -a || test $$? = 2

```
[INDENT]and[/INDENT]
```
        QUILT_PATCHES=debian/patches quilt pop -a -R || test $$? = 2

```

Next, we have to register files new to the version we're compiling, so add these lines to debian/vlc-nox.install (top, bottom, anywhere works):
```
usr/lib/vlc/codec/libtelx_plugin.so
usr/lib/vlc/video_output/libfb_plugin.so
```

We should be finished with preparations, so now we can actually compile the program (you MUST be in the root folder of your source for this to work, e.g. ~/vlc-src-tmp/vlc-0.8.6.release2):
```
sudo dpkg-buildpackage
```
After a long long time, this should finish, leaving you with either a cryptic error message or a set of debs. If it's the former, post the last 20 or so lines as a reply. If it's the latter, run this command:
```
sudo dpkg -i ../*.deb 
```
Well, that was pretty easy, wasn't it? The debs you create will have bad maintainer info and stuff so don't distribute em.

---

### Post by toaste on 2007-05-20
I got one of those nice cryptic errors while compiling for feisty!

```


# Install stuff
dh_install -si --fail-missing --sourcedir=debian/tmp
cp: cannot stat `debian/tmp/usr/lib/vlc/codec/liblpcm_plusr/lib/vlc/codec/libtelx_plugin.so': No such file or directory
dh_install: command returned error code 256
make: *** [install] Error 1


```

Ideas?

---

### Post by fantan on 2007-05-21
Hello,

Also I get the same error message during compilation:
".............
# Clean up libtool crap
find debian/tmp -name '*.la' -exec rm '{}' ';'
# Remove useless stuff
rm -Rf debian/tmp/usr/share/vlc/skins
rm -f debian/tmp/usr/share/vlc/skins2/fonts/FreeSans.ttf
rm -f debian/tmp/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
ln -s /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSans.ttf
ln -s /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
# Move stuff around
mkdir -p debian/tmp/usr/share/pixmaps
mv debian/tmp/usr/share/vlc/vlc48x48.png debian/tmp/usr/share/pixmaps/vlc.png
mv debian/tmp/usr/share/vlc/vlc32x32.xpm debian/tmp/usr/share/vlc/vlc.xpm
cp debian/vlc.desktop debian/vlc/usr/share/applications/vlc.desktop
# Install stuff
dh_install -si --fail-missing --sourcedir=debian/tmp
cp: stat "debian/tmp/usr/lib/vlc/vido_output/libfb_plugin.so" sikertelen: Nincs ilyen fájl vagy könyvtár
dh_install: command returned error code 256
make: *** [install] Error 1

"............................

What to do far away?

fantan

---

### Post by anon32 on 2007-05-21
usr/lib/vlc/codec/libtelx_plugin.so
usr/lib/vlc/video_output/libfb_plugin.so

You didn't add those lines to <vlc source dir>/debian/vlc-nox.install

Because VLC 0.8.6b has a couple new files, they have to be registered in the control files or else package creation will fail (since you got that far, it looks like the actual program compiled, so once you add those lines, it should be fine).

Or, since your builds seem to have differing names, if my lines don't work, add your own to match the path name (it shouldn't differ though....).

---

### Post by fantan on 2007-05-22
Hello,

Thank's a lot! There was a mistake by me! Insteed of "usr/lib/vlc/video_output/libfb_plugin.so" 
I wrote "usr/lib/vlc/vido_output/libfb_plugin.so" to "debian/vlc-nox.install".

After I've fixed this error, everything went fine. My new VLC works like a charm!

Thanks again!

fantan

---

### Post by paracetamolo on 2007-05-22
hi,
How do you actually use vlc without X?
I'm trying to use it in the tty but it always complain he can't initialize gtk.
Do I need to recompile it using your guide and use the --vout fb option to make it work this way?

thanks

---

### Post by anon32 on 2007-05-22
In order to use VLC from the console, you need to specify "vlc -I curses -V fb". This will bypass the gtk errors. You will need to compile VLC from source for fb video as the repository release doesn't have it. That said, fb's always been kinda buggy (bad color rendering?) and you can always use ascii art as your vo :p

The point of this guide wasn't so much to get framebuffer (mplayer's better for that), in fact, there's really not much point to this besides learning a few things about debian packaging (the bleeding-edge VLC is a plus of course).

---

### Post by Zeromaru on 2007-05-22
Compiles perfectly, but /dev/fb0 not found at runtime... I got the same error when trying to use the framebuffer mode in mplayer. Any ideas?

---

### Post by anon32 on 2007-05-23
Oh yeah, kernel framebuffers are never pre-enabled on Ubuntu systems. In order to do that, you need to pass a "vga=whatever" parameter to the kernel at bootup. It's beyond the scope of this thread, but 792 should work for 4:3 displays and 795 should work for 5:4 displays.

I suggest reading [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer) to find the proper value. Once you have that number, you edit /boot/grub/menu.lst and at the line "# defoptions=whatever", tack on a vga=whatever (if it's not the only option, don't forget a space between options). After that, it's just a "sudo update-grub" and a reboot.

That should get you some framebuffers (a nice side effect of this is that you get more room to type in the ttys) and you can see if you can get vlc to work with em (inverted colors on my box, so if you get em, don't bitch at me, I don't know either).

---

### Post by hingstin on 2008-05-02
Hi 
i get this ERROR:

[email]root@feisty:~/vlc-src-tmp/vlc-0.8.6.rele[/email]ase2# dpkg-buildpackage
dpkg-buildpackage: source package is vlc
dpkg-buildpackage: source version is 0.8.6.release2-1
dpkg-buildpackage: source changed by root <root@feisty>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.8.6.release2-1
 debian/rules clean
dh_testdir
dh_testroot
rm -f configure-stamp build-stamp
# Check that we have an x264 tree in here (can be a symlink)
test -d extras/x264
make: *** [clean] Error 1
[email]root@feisty:~/vlc-src-tmp/vlc-0.8.6.rele[/email]ase2#

What to do??

~G

---

### Post by toaste on 2008-05-02
You could try using the package from hardy multiverse:
[http://packages.ubuntu.com/hardy/graphics/vlc](http://packages.ubuntu.com/hardy/graphics/vlc)

The comment on this guide has a list of necessary dev packages if you want to try building from that source instead.
[http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704#c265](http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704#c265)

---

