---
title: "Crystalspace walktest, wont run"
date: 2007-11-05
forum: Programming Talk
---

### Post by bsmith on 2007-11-05
Hey,

I thought I would give the whole game programming thing a go, but this time I would use a SDK instead of going the hard way about it, so I have installed crystalspace from the ubuntu repositories including data, dev and docs, but when I try and run walk test I just get a bunch of errors.

```
ben@ben-laptop:~$ walktest
DEBUG: Sound System Software Renderer Initializing...
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.alsa'
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa'
ERROR: Failed to load driver as [crystalspace.sndsys.software.driver.alsa] or [crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa].
WARNING: failed to initialize plugin 'crystalspace.sndsys.renderer.software'

crystalspace.engine.warning:
  Shader /shader/std_lighting.xml not available
  Shader /shader/std_lighting_portal.xml not available
ALERT: crystalspace.maploader.parse.map:  Could not open map file 'world' on VFS!

crystalspace.maploader.parse.map:  Could not open map file 'world' on VFS!
ALERT: crystalspace.system:  Failing to load map!

crystalspace.system:  Failing to load map!
ALERT: crystalspace.system:  Error initializing system!

crystalspace.system:  Error initializing system!
Cleaning up...
```

It looks like a whole bunch of stuff is missing and my alsa has something wrong with it.
I bet I'm doing something really stupid, but any help would be greatly appreciated.

Thanks in advance

---

### Post by bsmith on 2007-11-05
Ok, Ive moved to the directory where the maps are and ...

```
ben@ben-laptop:/usr/share/crystalspace/data/maps$ walktest castle
DEBUG: Sound System Software Renderer Initializing...
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.alsa'
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa'
ERROR: Failed to load driver as [crystalspace.sndsys.software.driver.alsa] or [crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa].
WARNING: failed to initialize plugin 'crystalspace.sndsys.renderer.software'

crystalspace.engine.warning:
  Shader /shader/std_lighting.xml not available
  Shader /shader/std_lighting_portal.xml not available

crystalspace.maploader:
  Unable to open shader file '/shader/parallaxAtt/parallaxAtt.xml'!
  Unable to open shader file '/shader/ambient.xml'!
  Unable to open shader file '/shader/std_lighting.xml'!

crystalspace.maploader.parse.image:
  Could not open image file '/lib/std/castle/castle-detail1_d.jpg' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'castle-detail1_d.jpg', using checkerboard instead
  [node: world,textures,texture(name=castle-detail1_d.jpg)]

crystalspace.maploader.parse.image:
  Could not open image file '/lib/std/castle/castle-detail1_h.jpg' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'BUMPcastle-detail1_h.jpg', using checkerboard instead
  [node: world,textures,texture(name=BUMPcastle-detail1_h.jpg)]

crystalspace.maploader.parse.image:
  Could not open image file '/lib/std/castle/castle-detail1_n.jpg' on VFS!


...


crystalspace.maploader.parse.image:
  Could not open image file '/lib/std/castle/star.png' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'star.png', using checkerboard instead
  [node: world,textures,texture(name=star.png)]

crystalspace.maploader.parse.image:
  Could not open image file '/lib/std/castle/marble_blue.jpg' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'marble_blue.jpg', using checkerboard instead
  [node: world,textures,texture(name=marble_blue.jpg)]
ALERT: crystalspace.maploader.parse.loadingfile:  Error opening file '/shader/std_rloop_diffuse.xml'!
[node: world,addon,paramsfile]

crystalspace.maploader.parse.loadingfile:  Error opening file '/shader/std_rloop_diffuse.xml'!
crystalspace.maploader.parse.loadingfile:  [node: world,addon,paramsfile]
ALERT: crystalspace.system:  Failing to load map!

crystalspace.system:  Failing to load map!
ALERT: crystalspace.system:  Error initializing system!

crystalspace.system:  Error initializing system!
Cleaning up...
ben@ben-laptop:/usr/share/crystalspace/data/maps$ 

```

I got rid of all the errors in the middle or it would have taken up like 50 pages.
Anyway, I am still stumped.

---

### Post by rne1223 on 2008-01-17
Yeah I feel your pain my friend. I been getting the same errors for weeks now. I don't know what it is wrong and there isn't much documentation online either. Sorry that I didn't help you much but yeah...I'm getting really frustrated. Once I get the ./walktest running I will post something up

---

### Post by mcasaroli on 2008-01-21
First: Are you running the correct 3D drivers for your system? What do you use? Nvidia or Ati?

The package from ubuntu repos depends on a lot more libs than it reports.

Also, Crystalspace and nvidia-cg-toolkit from the ubuntu repos are outdated . There is a newer version on debian sid repos, but it depends on a newer lbc6 (that I am not willing to upgrade right now).

I could install the new deb source package from the debian sid repos because the binary (from sid) 

I have working (kind of) system using the latest ATI proprietary drivers (fglrx) (not from ubuntu repos) and the latest crystalspace-1.2 and nvidia-cg-toolkit-2.0 (both from debian sid). I see some errors and warnings on the terminal, but walktest is running (i can walk):

```

$ walktest
DEBUG: Sound System Software Renderer Initializing...

crystalspace.engine.warning:
  Couldn't load cached lighting for 1 object(s). Use -relight to calculate
  lighting:
      Cube.012
WARNING! Object 'Mesh.002' is not closed!
WARNING! Object 'Cylinder.231' is not closed!
WARNING! Object 'Cylinder.025' is not closed!
WARNING! Object 'Cube.581' is not closed!
WARNING! Object 'Cube.579' is not closed!
WARNING! Object 'Cube.577' is not closed!
...
Total level load time: 5.768 seconds
Cleaning up...

```

EDIT: Now I can run walktest without any warning and with good lightning. I had to run walktest -recalculate as root for it to commit the changes to the vfs (zip file)

---

### Post by rne1223 on 2008-02-03
Yeap...Ubuntu is outdated from the repository is outdated. I would recommend to use Windows XP (with the updated drivers if you are using an intel graphic card) and Microsoft Visual Studio C++ 2005. The current intel drivers in Gutsy aren't meant to run Crystal Space or any other type of 3D engine (they  require Nvidia and ATI). However, if someone gets it working with the "intel" driver under Ubuntu Gutsy...please let me. 

Peace :guitar:

---

### Post by hod139 on 2008-02-03
> **rne1223 said:**
> Yeap...Ubuntu is outdated from the repository is outdated. I would recommend to use Windows XP (with the updated drivers if you are using an intel graphic card) and Microsoft Visual Studio C++ 2005. 

I find this advice slightly ironic considering that both WindowsXP and Visual Studio 2005 are outdated (Vista and 2008 respectively).  It also isn't very helpful in solving the problem.

> 
The current intel drivers in Gutsy aren't meant to run Crystal Space or any other type of 3D engine (they  require Nvidia and ATI). 
Where did you hear this?  If you are having slow performance with an intel card it is most likely an Xgl issue.  See this post: [http://ubuntuforums.org/showpost.php?p=3416144&postcount=15](http://ubuntuforums.org/showpost.php?p=3416144&postcount=15)

---

### Post by crush304 on 2008-03-04
found info here [https://bugs.launchpad.net/ubuntu/+source/crystalspace/+bug/116804]("https://bugs.launchpad.net/ubuntu/+source/crystalspace/+bug/116804")


> 

A. Bram Neijt posted a lot of error messages, but I think most of them come from a misconfiguration of CS's VFS.

I've recently been trying, with limited success, to get CS's wxtest program working under kubuntu gutsy, and came across some similar-looking messages.

Try changing three of the last four lines of /etc/crystalspace/vfs.cfg to read:

VFS.Unix.CS_SHAREDIR = /usr/lib/crystalspace
VFS.Unix.CS_DATADIR = /usr/lib/crystalspace/data
VFS.Unix.CS_CONFIGDIR = /etc/crystalspace
VFS.Unix.CS_MAPDIR = /usr/lib/crystalspace/data/maps

That way, CS should be able to find a lot of its files, and you should get fewer errors.

Regards, Non.


---

