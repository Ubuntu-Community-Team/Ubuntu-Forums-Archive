---
title: "Packaging deb with license using prebuilt binaries"
date: 2013-02-18
forum: Packaging and Compiling Programs
---

### Post by wolfgentleman on 2013-02-18
This has probably been asked and answered, however I have been having a heck of a time trying to get the information together. I have prebuilt binaries and a license. I think I need to use debconf and dpkg-deb, however I'm not sure. I am intermediate at computer software: I can use the terminal and I am a programmer, but I have never built a deb package.

Here is what I have found, but I was having trouble wraping my head around the one about debconf and the one about building deb packages didn't have a clear answer:
[http://www.fifi.org/doc/debconf-doc/tutorial.html](http://www.fifi.org/doc/debconf-doc/tutorial.html)
[http://stackoverflow.com/questions/1585030/creating-deb-packages-from-prebuilt-binaries](http://stackoverflow.com/questions/1585030/creating-deb-packages-from-prebuilt-binaries)

Thanks in advance,
wolfgentleman

---

### Post by Malsasa on 2013-02-19
Maybe this link helps you because I used this and it works fine: 

[http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/)

With that, and by mirrorring Lintian Tags pages in Debian web, I have created my first DEB in my life successfully. 

Hope this will be useful for you...

---

### Post by wolfgentleman on 2013-03-05
> **Malsasa said:**
> Maybe this link helps you because I used this and it works fine: 

[http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/)

With that, and by mirrorring Lintian Tags pages in Debian web, I have created my first DEB in my life successfully. 

Hope this will be useful for you...

Between the link you provided and [http://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf](http://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf) I managed to get it to display the way I wanted, however I am not sure if it is just my computer or what but it doesn't seem to install... It just sits there after I put in my password. It has been sitting like this for 20 minutes now:

[ATTACH=CONFIG]239787[/ATTACH]


Here is the output of lintian:
```
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtCore.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtGui.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtNetwork.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/_old_update
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_update .
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/accessible/_old_libqtaccessiblewidgets.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/accessible/libqtaccessiblewidgets.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/error_report
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/error_report .
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/_old_libqgif.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/_old_libqjpeg.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/libqgif.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/libqjpeg.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtCore.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtGui.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtNetwork.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtSql.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/package_inst
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/package_inst .
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libappscanner_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libclientquery_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/liblua_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libtest_plugin.so
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: embedded-library usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so: sqlite
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/update
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/update .
W: teamspeak3: missing-depends-line
E: teamspeak3: no-copyright-file
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: file-in-unusual-dir changelog
W: teamspeak3: file-in-unusual-dir copyright
W: teamspeak3: non-standard-file-perm usr/bin/teamspeak 0664 != 0644
W: teamspeak3: extra-license-file usr/lib/TeamSpeak3/LICENSE
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/accessible/libqtaccessiblewidgets.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/error_report 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ad.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ae.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/af.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ag.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ai.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/al.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/am.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/an.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ao.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/as.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/at.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/au.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/aw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ax.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/az.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ba.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/be.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/br.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/by.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ca.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ci.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ck.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/co.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cx.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/de.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/do.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ec.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ee.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/eg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/eh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/er.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/es.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/et.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ga.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ge.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ht.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/id.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ie.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/il.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/im.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/in.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/io.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/iq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ir.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/is.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/it.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/je.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ke.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ki.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/km.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ky.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/la.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/li.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ls.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ly.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ma.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/md.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/me.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ml.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ms.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mx.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/my.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/na.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ne.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ng.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ni.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/no.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/np.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/om.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ph.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ps.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/py.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/qa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/re.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ro.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/rs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ru.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/rw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/se.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/si.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/so.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/st.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/td.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/th.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/to.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ua.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ug.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/um.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/us.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/va.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ve.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/wf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ws.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ye.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/yt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/za.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/zm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/zw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/100x100_broken_image.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_3d_sound.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_about.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add_foe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add_friend.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ban_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ban_list.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_add_folder.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_duplicate.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_remove.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_change_nickname.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_changelog.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_collapse_all.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_commander.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_create_sub.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_expand_all.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_green.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_green_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_private.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_red.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_red_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_switch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_yellow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_yellow_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_check_update.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_connect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_copy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_default.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_delete_avatar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_disconnect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_down.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_edit_friend_foe_status.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_emoticon.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_error.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_filetransfer.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_find.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_guisetup.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hotkeys.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_identity_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_info.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_is_talker.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_kick_from_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_kick_from_server.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_listview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_incoming.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_info.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_outgoing.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_moderated.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_music.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_new_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_notifications.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_offline_messages.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_on_whisperlist.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permission_overview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channel_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channel_groups.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_clients.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_server_groups.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_phoneticsnickname.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_2.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_3.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_4.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_calculating.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_disconnected.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_play.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_commander_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_commander_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_plugins.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_poke.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_present.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_quit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_recording_start.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_recording_stop.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_register.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_remove_foe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_remove_friend.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_request_talk_power.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_request_talk_power_cancel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_revoke_talker.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_send_complaint.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_green.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_log.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_query.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_settings.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_setup_wizard.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_stop.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_subscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_subscribe_to_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_temp_server_password.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_temp_server_password_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_bold.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_foreground.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_italic.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_underline.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_token.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_unsubscribe_from_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_unsubscribe_from_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_up.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_upload_avatar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_urlcatcher.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_virtualserver_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_volume.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_warning.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_weblist.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/200x200_loading_image.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/20x20_3d_sound_me.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/20x20_3d_sound_user.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_3d_sound.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_activate_microphone.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_ban_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_bookmark_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_create_sub.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_connect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_disconnect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_edit_friend_foe_status.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_filetransfer.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hoster_button.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_iconsview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_default.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_export.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_import.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_remove.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_listview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_channel_group.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_server_group.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_selectfolder.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_subscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_unsubscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_urlcatcher.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_home.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_refresh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_up.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_guisetup.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hotkeys.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_notifications.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_security.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/7x5_down_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/7x5_up_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/8x7_tab_close_button.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/cool.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/sad.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/smile.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/twinkle.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_100.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_200.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_300.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_500.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_600.png
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/imageformats/libqgif.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/imageformats/libqjpeg.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/libQtCore.so.4 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/libQtGui.so.4 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/libQtNetwork.so.4 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/libQtSql.so.4 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/1/img/temp_passwords.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/1/img/temp_passwords_de.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/2/img/opus.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/2/img/opus_de.jpg
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/package_inst 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libappscanner_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libclientquery_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/liblua_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libtest_plugin.so 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/2.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/3.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/t.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/caution.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/home.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/important.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/logo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/next.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/note.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/prev.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/up.png
W: teamspeak3: windows-devel-file-in-package usr/lib/TeamSpeak3/pluginsdk/src/test_plugin.vcproj
W: teamspeak3: windows-devel-file-in-package usr/lib/TeamSpeak3/pluginsdk/src/test_plugin_2005.vcproj
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/soundbackends/libalsa_linux_x86.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/soundbackends/libpulseaudio_linux_x86.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/close_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/down_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/left_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/menu_check.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/menu_check1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/open_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/radioButton1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/right_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/sibling_branch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/sizegrip.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewF0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewM0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewP0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewS0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewW0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/up_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/default/chatlog-128x96.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/default/logo-128x128.png
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/ts3client_linux_x86 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/update 0777 != 0755
W: teamspeak3: binary-without-manpage usr/bin/teamspeak
E: teamspeak3: executable-desktop-file usr/share/applications/ts3menuitem.desktop 0755
W: teamspeak3: desktop-entry-contains-deprecated-key usr/share/applications/ts3menuitem.desktop:16 TerminalOptions
W: teamspeak3: desktop-command-not-in-package usr/share/applications/ts3menuitem.desktop bash
W: teamspeak3: script-not-executable usr/bin/teamspeak
W: teamspeak3: executable-not-elf-or-script usr/share/applications/ts3menuitem.desktop
W: teamspeak3: executable-not-elf-or-script usr/lib/TeamSpeak3/gfx/default/8x7_tab_close_button.png
E: teamspeak3: shlib-with-executable-bit usr/lib/TeamSpeak3/_old_libQtGui.so.4 0755
E: teamspeak3: shlib-with-executable-bit usr/lib/TeamSpeak3/_old_libQtNetwork.so.4 0755
E: teamspeak3: shlib-with-executable-bit usr/lib/TeamSpeak3/libQtGui.so.4 0777
E: teamspeak3: shlib-with-executable-bit usr/lib/TeamSpeak3/libQtNetwork.so.4 0777
E: teamspeak3: shlib-with-executable-bit usr/lib/TeamSpeak3/libQtSql.so.4 0777
```
I do not uderstand a majority of the output...

---

### Post by r-senior on 2013-03-05
What happens if you scroll to the bottom (obviously reading the T&C carefully)?

---

### Post by wolfgentleman on 2013-03-05
> **r-senior said:**
> What happens if you scroll to the bottom (obviously reading the T&C carefully)?

It shows the whole license... I just clicked on details and it said installed size 0B...

---

### Post by schragge on 2013-03-05
> **wolfgentleman said:**
> Here is the output of lintian:Ouch, there too many packaging errors in there.
> **wolfgentleman said:**
> I do not uderstand a majority of the output...
To begin with,
[LIST]
[*][binary-or-shlib-defines-rpath](http://lintian.debian.org/tags/binary-or-shlib-defines-rpath.html)
[*][unstripped-binary-or-object](http://lintian.debian.org/tags/unstripped-binary-or-object.html)
[*][embedded-library](http://lintian.debian.org/tags/embedded-library.html)
[*][no-copyright-file](http://lintian.debian.org/tags/no-copyright-file.html)
[*][executable-desktop-file](http://lintian.debian.org/tags/executable-desktop-file.html)
[*][shlib-with-executable-bit](http://lintian.debian.org/tags/shlib-with-executable-bit.html)
[/LIST]

---

### Post by wolfgentleman on 2013-03-05
> **schragge said:**
> Ouch, there too many packaging errors in there.

To begin with,
[LIST]
[*][binary-or-shlib-defines-rpath]("http://lintian.debian.org/tags/binary-or-shlib-defines-rpath.html") 
[*][unstripped-binary-or-object]("http://lintian.debian.org/tags/unstripped-binary-or-object.html") 
[*][embedded-library]("http://lintian.debian.org/tags/embedded-library.html") 
[*][no-copyright-file]("http://lintian.debian.org/tags/no-copyright-file.html") 
[*][executable-desktop-file]("http://lintian.debian.org/tags/executable-desktop-file.html") 
[*][shlib-with-executable-bit]("http://lintian.debian.org/tags/shlib-with-executable-bit.html") 
[/LIST]


I am just packaging teamspeak 3... I got executable-desktop-file and shlib-with-executable-bit fixed, also I moved the copyright file where it said and it is still complaining about no-copyright-file... Everything else has me very confused...
This is the new output of lintian:
```
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtCore.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtGui.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_libQtNetwork.so.4 /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/_old_update
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/_old_update .
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/accessible/_old_libqtaccessiblewidgets.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/accessible/libqtaccessiblewidgets.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/error_report
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/error_report .
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/_old_libqgif.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/_old_libqjpeg.so /usr/local/Trolltech/Qt-4.7.2/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/libqgif.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/imageformats/libqjpeg.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtCore.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtGui.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtNetwork.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/libQtSql.so.4 /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/package_inst
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/package_inst .
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libappscanner_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libclientquery_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/liblua_plugin.so
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/plugins/libtest_plugin.so
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so /usr/local/Trolltech/Qt-4.8.3/lib
E: teamspeak3: embedded-library usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so: sqlite
E: teamspeak3: unstripped-binary-or-object usr/lib/TeamSpeak3/update
E: teamspeak3: binary-or-shlib-defines-rpath usr/lib/TeamSpeak3/update .
E: teamspeak3: missing-dependency-on-libc needed by usr/lib/TeamSpeak3/_old_libQtCore.so.4 and 24 others
E: teamspeak3: no-copyright-file
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: extended-description-line-too-long
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/accessible/libqtaccessiblewidgets.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/error_report 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ad.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ae.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/af.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ag.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ai.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/al.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/am.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/an.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ao.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/as.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/at.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/au.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/aw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ax.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/az.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ba.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/be.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/br.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/by.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/bz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ca.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ci.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ck.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/co.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cx.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/cz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/de.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/do.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/dz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ec.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ee.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/eg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/eh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/er.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/es.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/et.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/fr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ga.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ge.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/gy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ht.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/hu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/id.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ie.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/il.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/im.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/in.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/io.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/iq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ir.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/is.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/it.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/je.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/jp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ke.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ki.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/km.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ky.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/kz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/la.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/li.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ls.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/lv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ly.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ma.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/md.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/me.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ml.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mp.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mq.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ms.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mx.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/my.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/mz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/na.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ne.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ng.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ni.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/no.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/np.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/nz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/om.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ph.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ps.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/pw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/py.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/qa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/re.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ro.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/rs.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ru.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/rw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sa.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sb.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sd.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/se.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/si.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/so.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/st.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/sz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/td.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/th.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tj.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tl.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/to.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tr.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tv.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/tz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ua.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ug.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uk.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/um.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/us.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/uz.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/va.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vc.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ve.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vg.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vi.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vn.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/vu.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/wf.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ws.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/ye.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/yt.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/za.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/zm.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/countries/zw.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/100x100_broken_image.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_3d_sound.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_about.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add_foe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_add_friend.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ban_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ban_list.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_add_folder.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_duplicate.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_bookmark_remove.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_change_nickname.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_changelog.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_collapse_all.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_commander.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_create_sub.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_expand_all.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_green.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_green_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_private.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_red.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_red_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_switch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_yellow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_channel_yellow_subscribed.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_check_update.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_connect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_copy.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_default.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_delete_avatar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_disconnect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_down.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_edit_friend_foe_status.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_emoticon.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_error.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_filetransfer.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_find.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_guisetup.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_hotkeys.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_identity_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_info.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_is_talker.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_kick_from_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_kick_from_server.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_listview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_incoming.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_info.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_message_outgoing.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_moderated.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_music.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_new_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_notifications.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_offline_messages.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_on_whisperlist.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permission_overview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channel_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channel_groups.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_clients.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_permissions_server_groups.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_phoneticsnickname.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_2.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_3.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_4.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_calculating.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_ping_disconnected.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_play.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_commander_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_commander_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_plugins.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_poke.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_present.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_quit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_recording_start.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_recording_stop.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_register.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_remove_foe.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_remove_friend.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_request_talk_power.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_request_talk_power_cancel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_revoke_talker.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_send_complaint.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_green.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_log.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_server_query.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_settings.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_setup_wizard.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_stop.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_subscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_subscribe_to_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_temp_server_password.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_temp_server_password_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_bold.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_foreground.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_italic.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_textformat_underline.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_token.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_unsubscribe_from_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_unsubscribe_from_channel.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_up.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_upload_avatar.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_urlcatcher.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_virtualserver_edit.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_volume.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_warning.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_weblist.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/16x16_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/200x200_loading_image.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/20x20_3d_sound_me.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/20x20_3d_sound_user.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_3d_sound.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_activate_microphone.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_ban_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_bookmark_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_create_sub.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_channel_delete.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_connect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_disconnect.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_edit_friend_foe_status.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_filetransfer.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_hoster_button.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_iconsview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_add.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_default.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_export.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_import.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_manager.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_identity_remove.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_listview.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_channel_group.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_client.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_permission_server_group.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_selectfolder.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_subscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_unsubscribe_to_all_channels.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_urlcatcher.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/24x24_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_away.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_capture.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_channel_create.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_home.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_refresh.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_file_up.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_guisetup.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hardware_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hardware_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_hotkeys.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_input_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_input_muted_local.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_notifications.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_output_muted.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_playback.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_chat.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_off.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_on.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_player_whisper.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_security.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/32x32_whisperlists.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/7x5_down_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/7x5_up_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/8x7_tab_close_button.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/cool.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/sad.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/smile.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/emoticons/twinkle.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_100.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_200.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_300.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_500.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/gfx/default/group_600.png
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/imageformats/libqgif.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/imageformats/libqjpeg.so 0777 != 0755
W: teamspeak3: non-standard-file-perm usr/lib/TeamSpeak3/libQtCore.so.4 0666 != 0644
W: teamspeak3: non-standard-file-perm usr/lib/TeamSpeak3/libQtGui.so.4 0666 != 0644
W: teamspeak3: non-standard-file-perm usr/lib/TeamSpeak3/libQtNetwork.so.4 0666 != 0644
W: teamspeak3: non-standard-file-perm usr/lib/TeamSpeak3/libQtSql.so.4 0666 != 0644
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/1/img/temp_passwords.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/1/img/temp_passwords_de.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/2/img/opus.jpg
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/news/2/img/opus_de.jpg
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/package_inst 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libappscanner_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libclientquery_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/liblua_plugin.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/plugins/libtest_plugin.so 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/2.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/3.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/plugins/test_plugin/t.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/caution.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/home.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/important.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/logo.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/next.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/note.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/prev.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/pluginsdk/docs/client_html/images/up.png
W: teamspeak3: windows-devel-file-in-package usr/lib/TeamSpeak3/pluginsdk/src/test_plugin.vcproj
W: teamspeak3: windows-devel-file-in-package usr/lib/TeamSpeak3/pluginsdk/src/test_plugin_2005.vcproj
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/soundbackends/libalsa_linux_x86.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/soundbackends/libpulseaudio_linux_x86.so 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/sqldrivers/libqsqlite.so 0777 != 0755
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/close_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/down_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/left_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/menu_check.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/menu_check1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/open_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/radioButton1.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/right_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/sibling_branch.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/sizegrip.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewF0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewM0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewP0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewS0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/treeviewW0.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/bluesky/up_arrow.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/default/chatlog-128x96.png
W: teamspeak3: image-file-in-usr-lib usr/lib/TeamSpeak3/styles/default/logo-128x128.png
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/ts3client_linux_x86 0777 != 0755
W: teamspeak3: non-standard-executable-perm usr/lib/TeamSpeak3/update 0777 != 0755
W: teamspeak3: binary-without-manpage usr/bin/teamspeak
W: teamspeak3: desktop-command-not-in-package usr/share/applications/ts3menuitem.desktop bash
W: teamspeak3: script-not-executable usr/bin/teamspeak
W: teamspeak3: executable-not-elf-or-script usr/lib/TeamSpeak3/gfx/default/8x7_tab_close_button.png
W: teamspeak3: shlib-with-bad-permissions usr/lib/TeamSpeak3/libQtCore.so.4 0666
W: teamspeak3: shlib-with-bad-permissions usr/lib/TeamSpeak3/libQtGui.so.4 0666
W: teamspeak3: shlib-with-bad-permissions usr/lib/TeamSpeak3/libQtNetwork.so.4 0666
W: teamspeak3: shlib-with-bad-permissions usr/lib/TeamSpeak3/libQtSql.so.4 0666

```

---

### Post by wolfgentleman on 2013-03-07
bump

---

### Post by wolfgentleman on 2013-03-09
bump

---

### Post by peng6662001 on 2013-03-12
I encount same issue,do you fix it?

---

### Post by wolfgentleman on 2013-04-12
bump

---

### Post by wolfgentleman on 2013-04-14
bump

---

### Post by wolfgentleman on 2013-04-16
I found a program that does it for me. Debreate. sources.list entry:

 deb http://debreate.sf.net/apt debreate main

Gpg key:

 http://debreate.sf.net/apt/pubkey.asc

---

