---
title: "Problem while recompiling qt 4"
date: 2010-07-22
forum: Packaging and Compiling Programs
---

### Post by cyrion on 2010-07-22
Hi, 

I'm trying to recompile qt4 with "-graphicssystem raster" by default, since I have proprietary NVidia drivers that makes QT rendering damn slow with non antialiased fonts.

But near the end of the compilation, I get an error related to shared lib dependency for /usr/lib/libGL.so.1...

What I did:
1/ apt-get source libqtcore4
2/ edit debian/rules to add "-graphicssystem raster" to configuration
3/ dpkg-buildpackage -rfakeroot -b -j4

What I get (last lines):

```

@@ -521,7 +571,9 @@
  _ZTVN6Phonon11VideoWidgetE@Base 4:4.2.0
  _ZTVN6Phonon12EffectWidgetE@Base 4:4.2.0
  _ZTVN6Phonon12GlobalConfigE@Base 4:4.3.0
+ _ZTVN6Phonon12PulseSupportE@Base 4:4.6.2-0ubuntu5
  _ZTVN6Phonon12VolumeSliderE@Base 4:4.2.0
+ _ZTVN6Phonon15AudioDataOutputE@Base 4:4.6.2-0ubuntu5
  _ZTVN6Phonon15MediaControllerE@Base 4:4.2.0
  _ZTVN6Phonon15StreamInterfaceE@Base 4:4.2.0
  _ZTVN6Phonon16MediaNodePrivateE@Base 4:4.2.0
# Generate shlibs local files
for pkg in libqtcore4 libqt4-core libqtgui4 libqt4-gui libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql libqt4-sql-sqlite libqt4-sql-sqlite2 libqt4-sql-tds libqt4-svg libqt4-webkit libqt4-xml libqt4-xmlpatterns libqt4-dbus libqt4-qt3support libqt4-designer libqt4-help libqt4-assistant libqt4-test libqt4-multimedia libphonon4 libqt4-phonon; do \
                if test -e debian/${pkg}/DEBIAN/shlibs ; then \
                        sed 's/>=[^)]*/= 4:4.6.2-0ubuntu5/' debian/${pkg}/DEBIAN/shlibs >> debian/shlibs.local ;\
                fi \
        done
make[1]: quittant le répertoire « /home/cyrion/qt4/qt4-x11-4.6.2 »
   dh_shlibdeps -O--parallel
dpkg-shlibdeps: erreur: pas d'information de dépendance trouvée pour /usr/lib/libGL.so.1 (utilisé par debian/libqt4-opengl/usr/lib/libQtOpenGL.so.4.6.2).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/libqt4-opengl.substvars debian/libqt4-opengl/usr/lib/qt4/plugins/graphicssystems/libqglgraphicssystem.so debian/libqt4-opengl/usr/lib/libQtOpenGL.so.4.6.2 returned exit code 2
make: *** [binary] Erreur 9
dpkg-buildpackage: erreur: fakeroot debian/rules binary a produit une erreur de sortie de type 2

```(For non french readers "dpkg-shlibdeps: error" says something like "no dependency information found for  /usr/lib/libGL.so.1 (used by  debian/libqt4-opengl/usr/lib/libQtOpenGL.so.4.6.2)")

Since I installed proprietary nvidia drivers, libGL.so.1 is a symlink to libGL.so.256.35.
Is it the cause of the problem?

What can I do as a workaround/to fix it?

Thanks for any help!

D.

Kubuntu 10.04

Linux ankh-morpork 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

