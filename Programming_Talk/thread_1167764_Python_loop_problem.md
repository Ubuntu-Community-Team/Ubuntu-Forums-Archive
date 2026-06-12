---
title: "Python loop problem"
date: 2009-05-23
forum: Programming Talk
---

### Post by matmatmat on 2009-05-23
So far I have this code:
```

import os
def ListFiles(path):
        f = open("/home/matio/.whatschanged.txt", "w")
        f.write("")
        f.close()
        f = open("/home/matio/.whatschanged.txt", "a")
        for root, dirs, files in os.walk(path):
                for file in files:
                        file = os.path.join(root, file)
                        print file
                        f.write(file + "\n")
                        f.write(str(os.path.getsize(file)) + "\n")

def compareFiles(path):
        f = open("/home/matio/.whatschanged.txt", "r")
        ffiles = f.readlines()
        for root, dirs, files in os.walk(path):
                for file in files:
                        file = os.path.join(root, file)
                        i = 0
                        for ffile in ffiles:
                                done = False
                                if ffile.rstrip() == file.rstrip():
                                        size = ffiles[i+1].rstrip()
                                        if int(size) != os.path.getsize(file):
                                                print "File %s has changed!" % (file)
                                        done = True      
                                        
				if ffile.rstrip() != file.rstrip():
					print "%s is a new file" % (file)
                                        done = True
                                i += 1

if os.path.exists("/home/matio/.whatschanged.txt"):
        compareFiles("/home/matio/Documents/Python")
else:
        listFiles("/home/matio/Documents/Python")

```
When run:
```

matio@matio-desktop:~/Documents/Python$ python whatschanged.py 
/home/matio/Documents/Python/Kubuntu_leaflet.jpg is a new file
/home/matio/Documents/Python/addressbook.py is a new file
/home/matio/Documents/Python/whatschanged.py~ is a new file
/home/matio/Documents/Python/test.txt is a new file
/home/matio/Documents/Python/history_file_cataloger.py is a new file
/home/matio/Documents/Python/primes.txt is a new file
/home/matio/Documents/Python/prime.py is a new file
/home/matio/Documents/Python/address.txt is a new file
/home/matio/Documents/Python/whatschanged.py is a new file
/home/matio/Documents/Python/urls.txt is a new file
/home/matio/Documents/Python/htmlist.py is a new file
/home/matio/Documents/Python/urlmanager.py~ is a new file
/home/matio/Documents/Python/main/libtrans.py is a new file
/home/matio/Documents/Python/main/README is a new file
/home/matio/Documents/Python/main/launcher-cli.py is a new file
/home/matio/Documents/Python/main/launcher-gtk.py is a new file
/home/matio/Documents/Python/main/interface.xml is a new file
/home/matio/Documents/Python/main/main.py is a new file
/home/matio/Documents/Python/main/libconf.py is a new file
/home/matio/Documents/Python/main/img/loadingmusic.png is a new file
/home/matio/Documents/Python/main/img/loadingimages.png is a new file
/home/matio/Documents/Python/main/img/src/loadingimages.xcf is a new file
/home/matio/Documents/Python/main/img/src/loadingmusic.xcf is a new file
/home/matio/Documents/Python/main/.bzr/README is a new file
/home/matio/Documents/Python/main/.bzr/branch-format is a new file
/home/matio/Documents/Python/main/.bzr/repository/pack-names is a new file
/home/matio/Documents/Python/main/.bzr/repository/format is a new file
/home/matio/Documents/Python/main/.bzr/repository/packs/8b09132dc04132a28049236bdf8889eb.pack is a new file
/home/matio/Documents/Python/main/.bzr/repository/indices/8b09132dc04132a28049236bdf8889eb.tix is a new file
/home/matio/Documents/Python/main/.bzr/repository/indices/8b09132dc04132a28049236bdf8889eb.iix is a new file
/home/matio/Documents/Python/main/.bzr/repository/indices/8b09132dc04132a28049236bdf8889eb.six is a new file
/home/matio/Documents/Python/main/.bzr/repository/indices/8b09132dc04132a28049236bdf8889eb.rix is a new file
/home/matio/Documents/Python/main/.bzr/checkout/format is a new file
/home/matio/Documents/Python/main/.bzr/checkout/conflicts is a new file
/home/matio/Documents/Python/main/.bzr/checkout/dirstate is a new file
/home/matio/Documents/Python/main/.bzr/branch/tags is a new file
/home/matio/Documents/Python/main/.bzr/branch/last-revision is a new file
/home/matio/Documents/Python/main/.bzr/branch/branch.conf is a new file
/home/matio/Documents/Python/main/.bzr/branch/format is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/README is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/PKG-INFO is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/setup.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/vector3.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/__init__.pyc is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/__init__.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/matrix44.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/util.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/test_vector3.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/vector2.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/grid.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/gametime.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/sphere.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/color.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/gameobjects/locals.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/vector3.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/__init__.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/matrix44.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/util.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/test_vector3.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/vector2.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/grid.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/gametime.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/sphere.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/color.py is a new file
/home/matio/Documents/Python/gameobjects-0.0.3/build/lib.linux-i686-2.6/gameobjects/locals.py is a new file
/home/matio/Documents/Python/backup/backup.py is a new file
/home/matio/Documents/Python/ply/parsetab.pyc is a new file
/home/matio/Documents/Python/ply/parser.out is a new file
/home/matio/Documents/Python/ply/parsetab.py is a new file
/home/matio/Documents/Python/ply/gardensnake.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/main.pyc is a new file
/home/matio/Documents/Python/pyPicSlideshow/libtrans.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/README is a new file
/home/matio/Documents/Python/pyPicSlideshow/launcher-cli.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/libtrans.pyc is a new file
/home/matio/Documents/Python/pyPicSlideshow/picslideshow is a new file
/home/matio/Documents/Python/pyPicSlideshow/launcher-gtk.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/MANIFEST is a new file
/home/matio/Documents/Python/pyPicSlideshow/setup.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/interface.xml is a new file
/home/matio/Documents/Python/pyPicSlideshow/libconf.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/pypicslideshow.pyc is a new file
/home/matio/Documents/Python/pyPicSlideshow/libconf.pyc is a new file
/home/matio/Documents/Python/pyPicSlideshow/pypicslideshow.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/img/loadingmusic.png is a new file
/home/matio/Documents/Python/pyPicSlideshow/img/loadingimages.png is a new file
/home/matio/Documents/Python/pyPicSlideshow/img/src/loadingimages.xcf is a new file
/home/matio/Documents/Python/pyPicSlideshow/img/src/loadingmusic.xcf is a new file
/home/matio/Documents/Python/pyPicSlideshow/dist/pyPicSlideshow-0.5.tar.gz is a new file
/home/matio/Documents/Python/pyPicSlideshow/build/lib.linux-i686-2.6/libtrans.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/build/lib.linux-i686-2.6/libconf.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/build/lib.linux-i686-2.6/pypicslideshow.py is a new file
/home/matio/Documents/Python/pyPicSlideshow/build/bdist.linux-i686/rpm/SPECS/pyPicSlideshow.spec is a new file
/home/matio/Documents/Python/pyPicSlideshow/build/bdist.linux-i686/rpm/SOURCES/pyPicSlideshow-0.5.tar.gz is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/README is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/branch-format is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/pack-names is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/format is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/73b56cd50ab114c528990b50aa1afade.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/87869bac181c971aaeeac3517d96d49a.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/73b56cd50ab114c528990b50aa1afade.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/e7b16c877b5c780e2cf01a04944d72f9.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/2a9ad8974eaa7929f3580c7b0ee4a4c1.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/87869bac181c971aaeeac3517d96d49a.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/421c7b77bc25224069117b3125b9dbc9.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/179d67657afa994e6458babb8cb20235.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/2a9ad8974eaa7929f3580c7b0ee4a4c1.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/85741d8419b344a66d57f4e52a7873cf.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/e7b16c877b5c780e2cf01a04944d72f9.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/29a9d8fe47ec98084e08b77977cd30e6.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/85741d8419b344a66d57f4e52a7873cf.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/179d67657afa994e6458babb8cb20235.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/2a9ad8974eaa7929f3580c7b0ee4a4c1.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/85741d8419b344a66d57f4e52a7873cf.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/179d67657afa994e6458babb8cb20235.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/29a9d8fe47ec98084e08b77977cd30e6.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/421c7b77bc25224069117b3125b9dbc9.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/85741d8419b344a66d57f4e52a7873cf.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/179d67657afa994e6458babb8cb20235.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/690248034861c23267ddfbab2361e1ac.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/2a9ad8974eaa7929f3580c7b0ee4a4c1.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/690248034861c23267ddfbab2361e1ac.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/87869bac181c971aaeeac3517d96d49a.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/29a9d8fe47ec98084e08b77977cd30e6.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/690248034861c23267ddfbab2361e1ac.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/e7b16c877b5c780e2cf01a04944d72f9.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/c68a791a047c0b3478d5a4dc5870cd94.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/690248034861c23267ddfbab2361e1ac.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/87869bac181c971aaeeac3517d96d49a.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/c68a791a047c0b3478d5a4dc5870cd94.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/73b56cd50ab114c528990b50aa1afade.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/29a9d8fe47ec98084e08b77977cd30e6.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/73b56cd50ab114c528990b50aa1afade.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/e7b16c877b5c780e2cf01a04944d72f9.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/87869bac181c971aaeeac3517d96d49a.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/85741d8419b344a66d57f4e52a7873cf.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/29a9d8fe47ec98084e08b77977cd30e6.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/179d67657afa994e6458babb8cb20235.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/421c7b77bc25224069117b3125b9dbc9.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/c68a791a047c0b3478d5a4dc5870cd94.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/e7b16c877b5c780e2cf01a04944d72f9.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/73b56cd50ab114c528990b50aa1afade.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/421c7b77bc25224069117b3125b9dbc9.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/421c7b77bc25224069117b3125b9dbc9.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/2a9ad8974eaa7929f3580c7b0ee4a4c1.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/690248034861c23267ddfbab2361e1ac.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/c68a791a047c0b3478d5a4dc5870cd94.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/obsolete_packs/c68a791a047c0b3478d5a4dc5870cd94.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/022a355a0ac690e1e160c51c9c9f17b6.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/21567131edc732e5c2f006f3a9832e51.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/6519ed97f2c1f4db22c5ce001ca0bf6e.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/6bf6d621db3795624fb48afdfb474ebd.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/f7984b8e6749d113edda62ecdb84ce3c.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/445181cca52827b87e53b53404a310d6.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/packs/5baf4ae3fa950967f1786c0ccb73d952.pack is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/022a355a0ac690e1e160c51c9c9f17b6.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6bf6d621db3795624fb48afdfb474ebd.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/f7984b8e6749d113edda62ecdb84ce3c.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6519ed97f2c1f4db22c5ce001ca0bf6e.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/445181cca52827b87e53b53404a310d6.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/21567131edc732e5c2f006f3a9832e51.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/022a355a0ac690e1e160c51c9c9f17b6.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6bf6d621db3795624fb48afdfb474ebd.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/21567131edc732e5c2f006f3a9832e51.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/022a355a0ac690e1e160c51c9c9f17b6.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/21567131edc732e5c2f006f3a9832e51.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6bf6d621db3795624fb48afdfb474ebd.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/445181cca52827b87e53b53404a310d6.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6bf6d621db3795624fb48afdfb474ebd.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/022a355a0ac690e1e160c51c9c9f17b6.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6519ed97f2c1f4db22c5ce001ca0bf6e.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/445181cca52827b87e53b53404a310d6.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6519ed97f2c1f4db22c5ce001ca0bf6e.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/5baf4ae3fa950967f1786c0ccb73d952.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/21567131edc732e5c2f006f3a9832e51.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/5baf4ae3fa950967f1786c0ccb73d952.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/6519ed97f2c1f4db22c5ce001ca0bf6e.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/5baf4ae3fa950967f1786c0ccb73d952.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/f7984b8e6749d113edda62ecdb84ce3c.iix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/5baf4ae3fa950967f1786c0ccb73d952.rix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/445181cca52827b87e53b53404a310d6.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/f7984b8e6749d113edda62ecdb84ce3c.six is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/repository/indices/f7984b8e6749d113edda62ecdb84ce3c.tix is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/checkout/merge-hashes is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/checkout/format is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/checkout/conflicts is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/checkout/dirstate is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/branch/tags is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/branch/last-revision is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/branch/branch.conf is a new file
/home/matio/Documents/Python/pyPicSlideshow/.bzr/branch/format is a new file
/home/matio/Documents/Python/bpwpapcode/README.txt is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter02/tank.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter02/tankgame.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/gotest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/simplevec.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/vectormovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/sushiplate.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/frameratecompare.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/fugu.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/timebasedmovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/diagonalmovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/vecmagniture.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter05/simplemove.py is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixA/readme.txt is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/colrects.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/polytest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/circletest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/arctest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/allcolors.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/ellipsetest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/multiplelines.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/drawinglines.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter04/colortest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/ant.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/smallfugu.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/spider.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/antsstatemachine.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/ants.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter07/leaf.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/background.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/booktex.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/mytank.mtl is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/mytank.obj is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/blenddemo.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/model3d.pyc is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/model3d.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/mytanktex.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/fugu.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/fogdemo.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/skybox.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/bodytex.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/skybox.obj is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/bk.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/ft.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/rt.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/lt.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/dn.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/up.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter12/tanksky/skybox.mtl is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/sushitex.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/booktex.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/opengltextiled.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/mytank.mtl is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/mytank.obj is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/opengltex.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/tankdemo.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/model3d.pyc is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/model3d.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/mytanktex.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter11/bodytex.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter01/readme.txt is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/fullscreentest.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/scrolly.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/name.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/helloworld.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/sushiplate.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/resize.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/fugu.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter03/events.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/bounce.wav is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/play.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/bouncesound.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/jukebox.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/ball.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/pause.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/next.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/bar.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/prev.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/stop.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/mousecursor.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/jukebox.py~ is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/cross.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter10/music/please put some ogg files in the music folder.ogg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/analoguehatscroll.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/cat.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/joystickdemo.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/joystickevents.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/keydemo.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/hatscroll.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/mouserotatemovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/keymovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/joystickmovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/sushiplate.jpg is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/fugu.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/simplekeyboardmovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/diagonalmovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter06/keyrotatemovement.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter09/map.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter09/firstopengl.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter09/rotation3d.py is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/ant.png is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/dist.bat is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/spider.png is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/setup.py is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/ants.iss is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/antsstatemachine.py is a new file
/home/matio/Documents/Python/bpwpapcode/AppendixB/leaf.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/ball.png is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/vectordroid.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/vector3test.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/parallaxstars.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/rotation3d.py is a new file
/home/matio/Documents/Python/bpwpapcode/Chapter08/simple3d.py is a new file

```
1) Not all of them are new files, only one or two
2) The files that have changed say that they are new as well
Why?

---

### Post by delfick on 2009-05-23
hello.

Firstly, when trying to debug something, it's generally helpful to do so on a small subset of the likely input :)
(i.e. folder with not so many files in this case)

Secondly, what is the purpose of the variables i and done in the compareFiles function?

Thirdly, you shouldn't redefine 'file' (it's a built in type in python)

Finally, here is code that works

[PHP]import os

def writeData(filename, info):
	changed = open(filename, 'w')
	changed.write('\n'.join("%s : %s" % (name, size) for name, size in info.items()))

def readData(filename):
	changed = open(filename, "r")
	return dict(
		(name, int(size)) for name, size in 
				(line.split(" : ") for line in changed)
	)
	
	
def ListFiles(path):
	fileDict = {}
	for root, dirs, files in os.walk(path):
		for f in files:
			filename = os.path.join(root, f)
			fileDict[filename] = os.path.getsize(filename)
	
	writeData('whatschanged', fileDict)
	

def compareFiles(path):
	
	fileDict = readData("whatschanged")
		
	for root, dirs, files in os.walk(path):
		for f in files:
			filename = os.path.join(root, f)
			size = os.path.getsize(filename)
			
			try:
				prevSize = fileDict[filename]
			except IndexError:
				prevSize = None
			
			if prevSize:
				if prevSize != size:
					print "%s has changed" % filename
					fileDict[filename] = size
			
			else:
				print "%s is a new file" % filename
				
	writeData("whatschanged", fileDict)

if os.path.exists("whatschanged"):
	compareFiles("test")
else:
	ListFiles("test")[/PHP]


First thing to notice is that everything is written to the file at the same time in the listFiles function instead of keep appending.

Second thing to notice is when I read in the data from the file I construct a dictionary, so that I don't have to iterate over all entries every time you come across the next file.

Feel free to ask questions for further understanding :p :)

---

### Post by unutbu on 2009-05-23
In your original code, i+=1 should probably be i+=2.

Alternatively, you could protect yourself from this kind of programming complication by
saving the files and sizes in a dict, and then pickling the dict. (Using something like adict[file]=size)

You could then save the dict in .whatschanged.txt, 
load the dict when you need it, and compare the os.path.getsize(file) with adict[file].

---

### Post by matmatmat on 2009-05-23
The getsize() function isn't very precise, is there anything else I could use? 
(md5?)

---

### Post by unutbu on 2009-05-23
Sure, md5 would be fine:
[PHP]#!/usr/bin/env python
import hashlib
fh=open('filename','r')
m=hashlib.md5()
m.update(fh.read())
print m.hexdigest()
[/PHP]

---

### Post by matmatmat on 2009-05-23
Thanks for the replies, I now have this:
```

import os
import hashlib

def writeData(filename, info):
    changed = open(filename, 'w')
    changed.write('\n'.join("%s : %s" % (name, size) for name, size in info.items()))

def readData(filename):
    changed = open(filename, "r")
    return dict(
        (name, int(size)) for name, size in 
                (line.split(" : ") for line in changed)
    )
    
    
def ListFiles(path):
    fileDict = {}
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
	    f = open(filename, "r")
	    m=hashlib.md5()
	    m.update(f.read()) 
            fileDict[filename] = m.hexdigest() 
    
    writeData('/home/matio/.whatschanged.txt', fileDict)
    

def compareFiles(path):
    
    fileDict = readData("/home/matio/.whatschanged.txt")
        
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
	    f = open(filename, "r")
	    m=hashlib.md5()
	    m.update(f.read()) 
            size = m.hexdigest() 
            
            try:
                prevSize = fileDict[filename]
            except IndexError:
                prevSize = None
            
            if prevSize:
                if prevSize != size:
                    print "%s has changed" % filename
                    fileDict[filename] = size
            
            else:
                print "%s is a new file" % filename
                
    writeData("/home/matio/.whatschanged.txt", fileDict)

if os.path.exists("/home/matio/.whatschanged.txt"):
    compareFiles("/home/matio/Document/Python/")
else:
    ListFiles("/home/matio/Document/Python/")  

```
but when run:
```

matio@matio-desktop:~/Documents/Python$ rm /home/matio/.whatschanged.txt 
matio@matio-desktop:~/Documents/Python$ python whatschanged.py 
matio@matio-desktop:~/Documents/Python$ cat /home/matio/.whatschanged.txt 

```
Theres nothing in the file?

---

### Post by unutbu on 2009-05-23
Indent 
```

            writeData(os.path.join(os.environ['HOME'],'.whatschanged.txt'), fileDict)
```
so that it is in the inner-most loop in the listFiles function.

---

### Post by matmatmat on 2009-05-23
I've fixed *that* problem, it was "Document" not "Documents"

---

### Post by matmatmat on 2009-05-23
Now I have another problem (suprise?):
```

import os
import hashlib

def writeData(filename, info):
    changed = open(filename, 'w')
    changed.write('\n'.join("%s : %s" % (name, size) for name, size in info.items()))

def readData(filename):
    changed = open(filename, "r")
    return dict(
        (name, size) for name, size in 
                (line.split(" : ") for line in changed)
    )
    
    
def ListFiles(path):
    fileDict = {}
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
	    f = open(filename, "r")
	    m=hashlib.md5()
	    m.update(f.read()) 
            fileDict[filename] = m.hexdigest()     
    	    writeData(os.path.join(os.environ['HOME'],'.whatschanged.txt'), fileDict)
    

def compareFiles(path):
    
    fileDict = readData("/home/matio/.whatschanged.txt")
        
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
	    f = open(filename, "r")
	    m=hashlib.md5()
	    m.update(f.read()) 
            size = m.hexdigest() 
            
            try:
                prevSize = fileDict[filename]
            except IndexError:
                prevSize = None
            
            if prevSize:
                if prevSize.rstrip() != size.rstrip():
                    print "%s has changed" % filename
                    fileDict[filename] = size
            
            else:
                print "%s is a new file" % filename
                
    writeData("/home/matio/.whatschanged.txt", fileDict)

if os.path.exists("/home/matio/.whatschanged.txt"):
    compareFiles("/home/matio/Documents/Python")
else:
    ListFiles("/home/matio/Documents/Python")  

```
when run the 2nd time:
```

matio@matio-desktop:~/Documents/Python$ python whatschanged.py 
Traceback (most recent call last):
  File "whatschanged.py", line 56, in <module>
    compareFiles("/home/matio/Documents/Python")
  File "whatschanged.py", line 30, in compareFiles
    fileDict = readData("/home/matio/.whatschanged.txt")
  File "whatschanged.py", line 12, in readData
    (line.split(" : ") for line in changed)
  File "whatschanged.py", line 11, in <genexpr>
    (name, size) for name, size in 
ValueError: need more than 1 value to unpack

```

---

### Post by delfick on 2009-05-23
I get this feeling your problem is partly your indentation.

Firstly, you shouldn't need to put the writeData call in the first for loop of listFiles function.

Otherwise we're writing the entire file everytime we add something to the dict, rather than just when the dict is complete.

Secondly, when I copied it into my text file you had mixed up tabs and spaces and somethings weren't where they were supposed to be.

The code below fixes those issues

As for your issue where it complains not enough values to unpack, that's because your compareFiles function adds a newline to the hash, which means you then end up with blank lines in your file.

So in the readData function I've applied strip() to each line as they come in so you don't have to worry about it later, and added an if clause so that if a line is just '\n' then it isn't read in.

I've also got rid of your indentation issues.

And I've made it so both the results of the getSize and hash is written to the file. So that we only recheck the hash if the getSize function returns a new value.

EDIT : actually, I just realised that sort of defeats the point of using hash instead. Cause the size could be the same, but the file changed.......... my bad
However, I'll leave the code as it is anyway and post the same but without recording both size and hash below.
(can you tell I only just woke up ?? :p)


[PHP]
import os
import hashlib

#histFile records the history of the directory
histFile = os.path.join(os.environ['HOME'],'.whatschanged.txt')

#directory is the path to folder this script is checking
directory = os.path.join(os.environ['HOME'], 'Documents/Python')

def writeData(filename, info):
    changed = open(filename, 'w')
    changed.write('\n'.join("%s : %s : %s" % (name, size, mHash) for name, (size, mHash) in info.items()))

def readData(filename):
    changed = open(filename, "r")
    return dict(
        (name, (int(size), mHash)) for name, size, mHash in 
            (line.strip().split(" : ") for line in changed if line != "\n")
    )

def getHash(filename):
    f = open(filename, "r")
    m=hashlib.md5()
    m.update(f.read()) 
    f.close()
    return m.hexdigest()
    
    
def ListFiles(path):
    fileDict = {}
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
            fileDict[filename] = ( os.path.getsize(filename), getHash(filename) )
    
    writeData(histFile, fileDict)
    

def compareFiles(path):
    
    fileDict = readData(histFile)
        
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
            size = os.path.getsize(filename)
            
            try:
                prevSize, prevHash = fileDict[filename]
            except IndexError:
                prevSize, prevHash = None, None
            
            if prevSize:
                if prevSize != size:
                    #size is different, so file is definitely different
                    newHash = getHash(filename)
                    if newHash != prevHash:
                    
                        print "%s has changed" % filename
                        fileDict[filename] = (size, newHash)
            
            else:
                print "%s is a new file" % filename
                
    writeData(histFile, fileDict)

if os.path.exists(histFile):
    compareFiles(directory)
else:
    ListFiles(directory)
[/PHP]

[PHP]
import os
import hashlib

#histFile records the history of the directory
histFile = os.path.join(os.environ['HOME'],'.whatschanged.txt')

#directory is the path to folder this script is checking
directory = os.path.join(os.environ['HOME'], 'Documents/Python')

def writeData(filename, info):
    changed = open(filename, 'w')
    changed.write('\n'.join("%s : %s" % (name, mHash) for name, mHash in info.items()))

def readData(filename):
    changed = open(filename, "r")
    return dict(
        (name, mHash) for name, mHash in 
            (line.strip().split(" : ") for line in changed if line != "\n")
    )

def getHash(filename):
    f = open(filename, "r")
    m=hashlib.md5()
    m.update(f.read()) 
    f.close()
    return m.hexdigest()
    
    
def ListFiles(path):
    fileDict = {}
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
            fileDict[filename] = getHash(filename)
    
    writeData(histFile, fileDict)
    

def compareFiles(path):
    
    fileDict = readData(histFile)
        
    for root, dirs, files in os.walk(path):
        for f in files:
            filename = os.path.join(root, f)
            newHash = getHash(filename)
                        
            try:
                prevHash = fileDict[filename]
            except IndexError:
                prevHash = None
            
            if prevHash:
                if prevHash != newHash:
                    print "%s has changed" % filename
                    fileDict[filename] = newHash
            
            else:
                print "%s is a new file" % filename
                
    writeData(histFile, fileDict)

if os.path.exists(histFile):
    compareFiles(directory)
else:
    ListFiles(directory)
[/PHP]

---

### Post by matmatmat on 2009-05-24
Thanks, instead of 
```

except IndexError

```
it was
```

except KeyError

```

---

### Post by delfick on 2009-05-24
> **matmatmat said:**
> Thanks, instead of 
```

except IndexError

```
it was
```

except KeyError

```

oops, it is too :)

my bad

---

