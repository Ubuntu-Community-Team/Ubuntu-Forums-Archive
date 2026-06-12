---
title: "How do I add a new folder to LibreCAD library?"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-19
Hi guys i need to add a new Library folder of my named choice - this is what I`ve got so far, need help please.

Regards

Clive

clive@clive-Inspiron-N5110:~$ locate -i librecad
/etc/apt/sources.list.d/librecad-dev-librecad-daily-oneiric.list
/home/clive/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,oneiric,any,librecad,page,1,,d258c5715d6be0fc20f8cefcc0dc4aa9
/home/clive/.config/LibreCAD
/home/clive/.config/LibreCAD/LibreCAD.conf
/home/clive/.local/share/data/LibreCAD
/home/clive/.local/share/data/LibreCAD/iconCache
/home/clive/.local/share/data/LibreCAD/iconCache/misc
/home/clive/.local/share/data/LibreCAD/iconCache/templates
/home/clive/.local/share/data/LibreCAD/iconCache/misc/a3.png
/home/clive/.local/share/data/LibreCAD/iconCache/misc/screw.png
/home/clive/.local/share/data/LibreCAD/iconCache/misc/t-part.png
/home/clive/.local/share/data/LibreCAD/iconCache/misc/tux.png
/home/clive/.local/share/data/LibreCAD/iconCache/templates/empty.png
/home/clive/Documents/LibreCAD
/home/clive/Documents/LibreCAD/#My Template.dxf
/home/clive/Documents/LibreCAD/Block Test 1.dxf
/home/clive/Documents/LibreCAD/Block Test 1.dxf~
/home/clive/Documents/LibreCAD/My Template.dxf
/home/clive/Documents/LibreCAD/example 1.dxf~
/home/clive/Documents/LibreCAD/example 2.dxf~
/home/clive/Documents/LibreCAD/test dxf 1.dxf~
/usr/bin/librecad
/usr/lib/librecad
/usr/lib/librecad/libalign.so
/usr/lib/librecad/libasciifile.so
/usr/lib/librecad/libimportshp.so
/usr/lib/librecad/liblist.so
/usr/lib/librecad/libsameprop.so
/usr/lib/librecad/libsample.so
/usr/lib/mime/packages/librecad
/usr/share/librecad
/usr/share/app-install/desktop/librecad:librecad.desktop
/usr/share/app-install/icons/librecad.png
/usr/share/applications/librecad.desktop
/usr/share/doc/librecad
/usr/share/doc/librecad-data
/usr/share/doc/librecad-doc
/usr/share/doc/librecad/README.Debian
/usr/share/doc/librecad/changelog.Debian.gz
/usr/share/doc/librecad/copyright
/usr/share/doc/librecad/doc
/usr/share/doc/librecad-data/changelog.Debian.gz
/usr/share/doc/librecad-data/copyright
/usr/share/doc/librecad-doc/changelog.Debian.gz
/usr/share/doc/librecad-doc/copyright
/usr/share/icons/hicolor/48x48/apps/librecad.png
/usr/share/icons/hicolor/scalable/apps/librecad.svg
/usr/share/librecad/fonts
/usr/share/librecad/library
/usr/share/librecad/patterns
/usr/share/librecad/plugins
/usr/share/librecad/qm
/usr/share/librecad/fonts/cursive.lff
/usr/share/librecad/fonts/cyrillic_ii.lff
/usr/share/librecad/fonts/gothgbt.lff
/usr/share/librecad/fonts/gothgrt.lff
/usr/share/librecad/fonts/gothitt.lff
/usr/share/librecad/fonts/greek_ol.lff
/usr/share/librecad/fonts/greekc.lff
/usr/share/librecad/fonts/greekcs.lff
/usr/share/librecad/fonts/greekp.lff
/usr/share/librecad/fonts/greeks.lff
/usr/share/librecad/fonts/iso.lff
/usr/share/librecad/fonts/iso8859-11.lff
/usr/share/librecad/fonts/italicc.lff
/usr/share/librecad/fonts/italiccs.lff
/usr/share/librecad/fonts/italict.lff
/usr/share/librecad/fonts/kochigothic.lff
/usr/share/librecad/fonts/kochimincho.lff
/usr/share/librecad/fonts/romanc.lff
/usr/share/librecad/fonts/romancs.lff
/usr/share/librecad/fonts/romand.lff
/usr/share/librecad/fonts/romanp.lff
/usr/share/librecad/fonts/romans.lff
/usr/share/librecad/fonts/romansi.lff
/usr/share/librecad/fonts/romant.lff
/usr/share/librecad/fonts/scriptc.lff
/usr/share/librecad/fonts/scripts.lff
/usr/share/librecad/fonts/simplex.lff
/usr/share/librecad/fonts/standard.lff
/usr/share/librecad/fonts/symbol.lff
/usr/share/librecad/fonts/symbol_astro.lff
/usr/share/librecad/fonts/symbol_misc1.lff
/usr/share/librecad/fonts/symbol_misc2.lff
/usr/share/librecad/fonts/unicode.lff
/usr/share/librecad/fonts/wqy-unicode.lff
/usr/share/librecad/library/misc
/usr/share/librecad/library/templates
/usr/share/librecad/library/misc/a3.dxf
/usr/share/librecad/library/misc/screw.dxf
/usr/share/librecad/library/misc/t-part.dxf
/usr/share/librecad/library/misc/tux.dxf
/usr/share/librecad/library/templates/empty.dxf
/usr/share/librecad/patterns/angle.dxf
/usr/share/librecad/patterns/ansi31.dxf
/usr/share/librecad/patterns/ar-b816.dxf
/usr/share/librecad/patterns/ar-b816c.dxf
/usr/share/librecad/patterns/ar-b88.dxf
/usr/share/librecad/patterns/ar-brelm.dxf
/usr/share/librecad/patterns/ar-brstd.dxf
/usr/share/librecad/patterns/ar-conc.dxf
/usr/share/librecad/patterns/ar-hbone.dxf
/usr/share/librecad/patterns/ar-parq1.dxf
/usr/share/librecad/patterns/ar-roof.dxf
/usr/share/librecad/patterns/ar-rshke.dxf
/usr/share/librecad/patterns/arcs.dxf
/usr/share/librecad/patterns/arcs_2.dxf
/usr/share/librecad/patterns/box.dxf
/usr/share/librecad/patterns/brick.dxf
/usr/share/librecad/patterns/brstone.dxf
/usr/share/librecad/patterns/clay.dxf
/usr/share/librecad/patterns/concrete.dxf
/usr/share/librecad/patterns/cross.dxf
/usr/share/librecad/patterns/daemon.dxf
/usr/share/librecad/patterns/dolmit.dxf
/usr/share/librecad/patterns/earth.dxf
/usr/share/librecad/patterns/escher.dxf
/usr/share/librecad/patterns/flex.dxf
/usr/share/librecad/patterns/grass.dxf
/usr/share/librecad/patterns/grass_b.dxf
/usr/share/librecad/patterns/hex.dxf
/usr/share/librecad/patterns/hexagon_a.dxf
/usr/share/librecad/patterns/hexagon_b.dxf
/usr/share/librecad/patterns/honeycomb.dxf
/usr/share/librecad/patterns/hound.dxf
/usr/share/librecad/patterns/iso03w100.dxf
/usr/share/librecad/patterns/iso03w100a.dxf
/usr/share/librecad/patterns/kerpele.dxf
/usr/share/librecad/patterns/misc01.dxf
/usr/share/librecad/patterns/misc02.dxf
/usr/share/librecad/patterns/misc03.dxf
/usr/share/librecad/patterns/paisley.dxf
/usr/share/librecad/patterns/pantagon_a.dxf
/usr/share/librecad/patterns/pantagon_b.dxf
/usr/share/librecad/patterns/plastic.dxf
/usr/share/librecad/patterns/sacncr.dxf
/usr/share/librecad/patterns/sand.dxf
/usr/share/librecad/patterns/square.dxf
/usr/share/librecad/patterns/triangle_a.dxf
/usr/share/librecad/patterns/triangle_b.dxf
/usr/share/librecad/plugins/libalign.so
/usr/share/librecad/plugins/libasciifile.so
/usr/share/librecad/plugins/libimportshp.so
/usr/share/librecad/plugins/liblist.so
/usr/share/librecad/plugins/libsameprop.so
/usr/share/librecad/plugins/libsample.so
/usr/share/librecad/qm/librecad_cs.qm
/usr/share/librecad/qm/librecad_da.qm
/usr/share/librecad/qm/librecad_de.qm
/usr/share/librecad/qm/librecad_el.qm
/usr/share/librecad/qm/librecad_en.qm
/usr/share/librecad/qm/librecad_en_au.qm
/usr/share/librecad/qm/librecad_es.qm
/usr/share/librecad/qm/librecad_es_ar.qm
/usr/share/librecad/qm/librecad_es_bo.qm
/usr/share/librecad/qm/librecad_es_cl.qm
/usr/share/librecad/qm/librecad_es_co.qm
/usr/share/librecad/qm/librecad_es_cr.qm
/usr/share/librecad/qm/librecad_es_do.qm
/usr/share/librecad/qm/librecad_es_ec.qm
/usr/share/librecad/qm/librecad_es_gt.qm
/usr/share/librecad/qm/librecad_es_hn.qm
/usr/share/librecad/qm/librecad_es_mx.qm
/usr/share/librecad/qm/librecad_es_ni.qm
/usr/share/librecad/qm/librecad_es_pa.qm
/usr/share/librecad/qm/librecad_es_pe.qm
/usr/share/librecad/qm/librecad_es_pr.qm
/usr/share/librecad/qm/librecad_es_py.qm
/usr/share/librecad/qm/librecad_es_sv.qm
/usr/share/librecad/qm/librecad_es_us.qm
/usr/share/librecad/qm/librecad_es_uy.qm
/usr/share/librecad/qm/librecad_es_ve.qm
/usr/share/librecad/qm/librecad_et.qm
/usr/share/librecad/qm/librecad_fi.qm
/usr/share/librecad/qm/librecad_fr.qm
/usr/share/librecad/qm/librecad_hu.qm
/usr/share/librecad/qm/librecad_id_ID.qm
/usr/share/librecad/qm/librecad_it.qm
/usr/share/librecad/qm/librecad_ja.qm
/usr/share/librecad/qm/librecad_nl.qm
/usr/share/librecad/qm/librecad_no.qm
/usr/share/librecad/qm/librecad_pa.qm
/usr/share/librecad/qm/librecad_pl.qm
/usr/share/librecad/qm/librecad_pt_br.qm
/usr/share/librecad/qm/librecad_pt_pt.qm
/usr/share/librecad/qm/librecad_ru.qm
/usr/share/librecad/qm/librecad_sk.qm
/usr/share/librecad/qm/librecad_sq_al.qm
/usr/share/librecad/qm/librecad_sv.qm
/usr/share/librecad/qm/librecad_tr.qm
/usr/share/librecad/qm/librecad_uk.qm
/usr/share/librecad/qm/librecad_zh_cn.qm
/usr/share/librecad/qm/librecad_zh_tw.qm
/usr/share/man/man1/librecad.1.gz
/usr/share/menu/librecad
/usr/share/mime/packages/librecad.xml
/usr/share/pixmaps/librecad.xpm
/var/cache/apt/archives/librecad-data_1.0.0~rc1+nolibs-4_all.deb
/var/cache/apt/archives/librecad-data_2.0.0~alpha1+yeslib201201041134.693-0ubuntu0~daily7~oneiric1_all.deb
/var/cache/apt/archives/librecad-doc_1.0.0~rc1+nolibs-4_all.deb
/var/cache/apt/archives/librecad-doc_2.0.0~alpha1+yeslib201201041134.693-0ubuntu0~daily7~oneiric1_all.deb
/var/cache/apt/archives/librecad_1.0.0~rc1+nolibs-4_amd64.deb
/var/cache/apt/archives/librecad_2.0.0~alpha1+yeslib201201041134.693-0ubuntu0~daily7~oneiric1_amd64.deb
/var/lib/apt/lists/ppa.launchpad.net_librecad-dev_librecad-daily_ubuntu_dists_oneiric_Release
/var/lib/apt/lists/ppa.launchpad.net_librecad-dev_librecad-daily_ubuntu_dists_oneiric_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_librecad-dev_librecad-daily_ubuntu_dists_oneiric_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_librecad-dev_librecad-daily_ubuntu_dists_oneiric_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_librecad-dev_librecad-daily_ubuntu_dists_oneiric_main_source_Sources
/var/lib/dpkg/info/librecad-data.list
/var/lib/dpkg/info/librecad-data.md5sums
/var/lib/dpkg/info/librecad-doc.list
/var/lib/dpkg/info/librecad-doc.md5sums
/var/lib/dpkg/info/librecad.list
/var/lib/dpkg/info/librecad.md5sums
/var/lib/dpkg/info/librecad.postinst
/var/lib/dpkg/info/librecad.postrm

---

### Post by cliveT on 2012-01-20
no problems  -I`ve worked it out!

---

