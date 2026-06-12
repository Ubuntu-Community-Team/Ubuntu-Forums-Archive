---
title: "[SOLVED] screenlets"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-26
how do i get them?

---

### Post by saj0577 on 2008-05-26
```
sudo apt-get install screenlets
```

or another program

```
sudo apt-get install gdesklets
```

Saj

---

### Post by iaculallad on 2008-05-26
> **Zopiac said:**
> how do i get them?

Try looking at this [thread]("http://ubuntuforums.org/showthread.php?t=687752") about screenlets.

---

### Post by rajaram_s on 2008-05-26
type in the followin command in the terminal:
sudo apt-get install screenlets

There is also a deb package available at softpedia. You can try that if u donot have direct internet connection./

---

### Post by rajaram_s on 2008-05-26
Here is the link for the deb package:

[http://linux.softpedia.com/get/Desktop-Environment/Desktop-Widgets/Screenlets-35054.shtml](http://linux.softpedia.com/get/Desktop-Environment/Desktop-Widgets/Screenlets-35054.shtml)

---

### Post by Zopiac on 2008-05-26
zopiac@zopiac:~$ sudo apt-get install screenlets
[sudo] password for zopiac: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
screenlets is already the newest version.
The following packages were automatically installed and are no longer required:
  torcs-data-tracks obex-data-server libsvga1 libtagc0 libavahi1.0-cil
  libqt3-mt-sqlite torcs-data-cars libenca0 mplayer-skins libggi2 libgii1
  libopenobex1 libgii1-target-x libconfuse0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up screenlets (0.0.10-3~gutsy1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 screenlets
E: Sub-process /usr/bin/dpkg returned an error code (1)
zopiac@zopiac:~$

un/reinstalled it, works fine. now for gdesklets...

---

### Post by Zopiac on 2008-05-26
zopiac@zopiac:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gdesklets needs to be reinstalled, but I can't find an archive for it.
zopiac@zopiac:~$ sudo apt-get remove gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gdesklets needs to be reinstalled, but I can't find an archive for it.
zopiac@zopiac:~$

---

### Post by iaculallad on 2008-05-26
> **Zopiac said:**
> zopiac@zopiac:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gdesklets needs to be reinstalled, but I can't find an archive for it.
zopiac@zopiac:~$ sudo apt-get remove gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gdesklets needs to be reinstalled, but I can't find an archive for it.
zopiac@zopiac:~$


Make sure to add universe/multiverse in your repository. Software->Administration->Software Sources

Install gesklets afterwards:

> sudo apt-get install gdesklets

---

### Post by Zopiac on 2008-05-26
zopiac@zopiac:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  torcs-data-tracks obex-data-server libsvga1 libtagc0 libavahi1.0-cil
  libqt3-mt-sqlite torcs-data-cars libenca0 mplayer-skins libggi2 libgii1
  libopenobex1 libgii1-target-x libconfuse0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gdesklets
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/2825kB of archives.
After this operation, 5886kB of additional disk space will be used.
Selecting previously deselected package gdesklets.
(Reading database ... 179402 files and directories currently installed.)
Unpacking gdesklets (from .../gdesklets_0.36-1ubuntu1_amd64.deb) ...
Setting up gdesklets (0.36-1ubuntu1) ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'


zopiac@zopiac:~$ 










after that i open gdesklets and it shows the shell, but closes after a while and i cant do anything about it.

---

### Post by iaculallad on 2008-05-26
> **Zopiac said:**
> zopiac@zopiac:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  torcs-data-tracks obex-data-server libsvga1 libtagc0 libavahi1.0-cil
  libqt3-mt-sqlite torcs-data-cars libenca0 mplayer-skins libggi2 libgii1
  libopenobex1 libgii1-target-x libconfuse0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gdesklets
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/2825kB of archives.
After this operation, 5886kB of additional disk space will be used.
Selecting previously deselected package gdesklets.
(Reading database ... 179402 files and directories currently installed.)
Unpacking gdesklets (from .../gdesklets_0.36-1ubuntu1_amd64.deb) ...
Setting up gdesklets (0.36-1ubuntu1) ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'


zopiac@zopiac:~$ 










after that i open gdesklets and it shows the shell, but closes after a while and i cant do anything about it.


Code:

> sudo apt-get install gdesklets gdesklets-data

---

