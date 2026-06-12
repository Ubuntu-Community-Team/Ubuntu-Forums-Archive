---
title: "add/remove error"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-27
when i try to add/remove programs via the a/r app., i get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i use the 'dpkg --configure -a' option in terminal, it says:
zopiac@zopiac:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
zopiac@zopiac:~$ 

what is superuser privileges? why cant i a/r programs now, but i could before?

---

### Post by i586 on 2008-04-27
You need to run ```
dpkg --configure -a
``` as root.
To login as root temporarily use either su or sudo.

Regards.

---

### Post by Zopiac on 2008-04-27
thank you very much! if any cares to se the results, as at the end it looks like i got an error, here:

zopiac@zopiac:~$ sudo dpkg --configure -a
[sudo] password for zopiac:
Setting up libsgutils1 (1.24-1) ...

Setting up libmcs1 (0.4.1-2) ...

Setting up libmms0 (0.3-5ubuntu2) ...

Setting up audacity (1.3.3-1ubuntu0.1) ...
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


Setting up libmono-cairo2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libtaglib2.0-cil (2.0.2.0-1) ...
* Installing 2 assemblies from libtaglib2.0-cil into Mono

Setting up libipoddevice0 (0.5.3-3) ...

Setting up libmono-security1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-sharpzip0.84-cil (1.2.4-6ubuntu6.1) ...
Setting up boo (0.7.6.2237-6) ...
Setting up libaudacious5 (1.3.2-4) ...

Setting up libmono-data-tds1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-system-data1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-system-web1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono1.0-cil (1.2.4-6ubuntu6.1) ...
dpkg: error processing banshee (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up audacious-plugins (1.3.5-3ubuntu4.1) ...
Setting up audacious (1.3.2-4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 banshee
zopiac@zopiac:~$

---

