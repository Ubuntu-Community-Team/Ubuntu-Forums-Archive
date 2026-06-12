---
title: "Creating python deb and setup.py"
date: 2011-03-24
forum: Packaging and Compiling Programs
---

### Post by pauljr on 2011-03-24
All,  

I'm looking for a little help in finishing off an app I've been working on. I've been disappointed in the quality/usability of backup apps, so I've put one together with *all* the bells and whistles, plus a nice UI, full documentation, i18n (although english only at the mo). 

Its finished, so I've been working on getting the installation right. And here's where I'm looking for some help. The bits I'm struggling with are:  

[LIST=1]
[*]I've made a setup.py, but that installs under the python dir. I think  that as a system utility (runnable with gksu) that this should go in  /opt, with a link/script in /usr/sbin. How can I achieve that?
[*]I've written the documentation using the DocHelp V5.0 standard. How  can I build the DocHelp and insert into the ubuntu help system?   

[p.s. writing DocHelp is ugly. Where are the nice GUIs? I tried half  a dozen or so and they are all awful].
[*]Lastly - I want to build a .deb, but I'm struggling a little. I've looked at a number of python apps with .deb files (rhythmbox, pitivi, deluge) and none of their source repositories seem to contain the blueprints for how they built their .deb files. Or am I missing them?
[/LIST]
One other thing... I'd appreciate some beta testers (once I get part (a) sorted so I can cleanly install). Feel free to  contact me on [EMAIL="paul@zapthis.kereru.org"]paul@zapthis.kereru.org[/EMAIL] if you are interested.  

Thanks in advance for any help/advice.
Paul

---

### Post by MadCow108 on 2011-03-24
> **pauljr said:**
> All,    
I've made a setup.py, but that installs under the python dir. I think  that as a system utility (runnable with gksu) that this should go in  /opt, with a link/script in /usr/sbin. How can I achieve that?

I don't really now distutils very well so I can't help with creating the link but should be placed in /usr/local/sbin by default.
else you risk that it will be overwritten by the package manager during upgrades.

> 
Lastly - I want to build a .deb, but I'm struggling a little. I've looked at a number of python apps with .deb files (rhythmbox, pitivi, deluge) and none of their source repositories seem to contain the blueprints for how they built their .deb files. Or am I missing them?


the packaging is done in the source packages. apt-get source package
the important file for building the deb is debian/rules
depending on the complexity of your package it can be very simple:
```

#!/usr/bin/make -f
%:
        dh $@ --with python2

```
see man dh_python2 (or 3), dh and [http://www.debian.org/doc/packaging-manuals/python-policy/](http://www.debian.org/doc/packaging-manuals/python-policy/)

this calls
python setup.py build
python setup.py install --root=debian/package-name/usr --install-layout=deb
in the appropriate places plus a bunch of other stuff (like compiling, symlinking, ...)

(please do not include a debian/ directory directly in your main source tarball [http://wiki.debian.org/UpstreamGuide#PristineUpstreamSource](http://wiki.debian.org/UpstreamGuide#PristineUpstreamSource))

---

### Post by LemursDontExist on 2011-03-24
> **pauljr said:**
> I've made a setup.py, but that installs under the python dir. I think  that as a system utility (runnable with gksu) that this should go in  /opt, with a link/script in /usr/sbin. How can I achieve that?

You can subclass distutils.command.install.install and modify the 'finalize_options' and 'run' methods to set install_lib, install_data, install_scripts instance variables.

So something like:

```
class MyInstall(distutils.command.install.install):
    def finalize_options(self):
        distutils.command.install.install.finalize_options(self)
        self.install_scripts = distutils.util.change_root(self.root or '/', '/usr/sbin')

    def run(self):
        distutils.command.install.install.run(self)
        opt_dir = distutils.util.change_root(self.root or '/', '/opt'))
        script = os.path.join(self.install_scripts, your_script_name)
        source = os.path.relpath(script, opt_dir)
        target = os.path.join(opt_dir, your_script_name)
        distutils.util.execute(os.symlink, (source, target))

my_install = MyInstall()
```

Then you can pass 
```
cmdclass={'install': my_install}
```
as an argument to setup.

All the change_root stuff is so that when you try to make the .deb things install under the correct root (dh_python runs setup.py with a different root, and if you don't account for that it will fail to work).  The relative path for the symlink is optional, but good if you want to be in line with Debian policy.

I'm willing to bet that there's a more elegant solution, but this is the best I was able to come up with.  I've run into some things that suggest that using setuptools instead of distutils greatly simplifies this process.  This code is untested but mostly copy/pasted from working code so take it as you will =).

---

### Post by pauljr on 2011-03-26
Thanks to LemursDontExist and MadCow108.
Your posts got me going in the right direction.

On the first question of creating the setup.py to install my files in the right locations...

I agree with Madcow108 - /usr/local/sbin is the right location for my 'runner' script,
and /opt for the rest of the files (python source, images).

Next - the installer:
[grumble]I gotta say that distutils is not well documented, and is over complicated and opaque in its design. [/grumble]

I tried lemur's subclassing... and it seems that there are a set of 
classes under distutils.command.install, including
install_data and install_lib. It took me quite a while to get them 
going just right. 

For more information on this - I finally found this tutorial:
[http://wiki.python.org/moin/Distutils/Tutorial](http://wiki.python.org/moin/Distutils/Tutorial)

**However**
It seems that there is an easier way...

a) create a config.cfg
```
[install]
install_data=/opt
install_lib=/opt
install_scripts=/usr/local/sbin

```The install_lib refers to your code. install_data refers to any other files (help, images).
install_scripts refers to scripts.

b) Then in your setup.py, you use:
```
data_files = [
                  ("vault/images", glob.glob('vault/images/*.png')),
                  ("vault/ui/images", glob.glob('vault/ui/images/*.png')),
                  ],

```These will be installed in the location specified by install_data.

c) Next:
```
packages = ['vault', 'vault.io', 'vault.ui', 'vault.server', 'vault.lib', 
                'vault.recovery'],

```These are my modules, and will be installed in the install_lib folder above.

d) Lastly
```
scripts = ["vault.run"],

```This script will be copied to the scripts folder above.

Voila! No coding required.
Note that you *do* need to get your manifest.in right - and
include *all* files above.

Cheers.
Paul

---

### Post by pauljr on 2011-03-26
Note: I'm still not there on the .deb creation - but getting
all the files in the right place means I can start getting beta testers
on board.

So thx again.

---

### Post by pauljr on 2011-03-28
And just a quick word on DocBook.

Debian guidelines seem to be pointing people towards DocBook V5.
But yelp (the Gnome help viewer) does not yet support V5 - although
support is planned for yelp V3.  So stick with docbook 4.5.

Also - it seems that you just need to copy your files into:
/usr/share/doc/<product>.
(see /usr/share/doc/rhythmbox for an example of the structure).

---

