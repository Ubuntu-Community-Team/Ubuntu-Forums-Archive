---
title: "codeblocks error on startup"
date: 2015-05-08
forum: Programming Talk
---

### Post by lsag on 2015-05-08
Hello

I'd have a recurrent error in codeblocks, whenever i start the program, stating like this:

[IMG]http://s30.postimg.org/5ekg5o9i9/Screenshot_codebocks_error.png[/IMG]

So i open the referenced xml file, and this is the content:

```

<?xml version="1.0" encoding="utf-8"?>
<report version="1.0" kind="exception">
  <system description="Linux 3.19.0-16-generic i686"/>
  <modules>
    <module path="/usr/bin/codeblocks" address="08048000" size="00132000"/>
    <module path="/usr/bin/codeblocks" address="08182000" size="00003000"/>
    <module path="[heap]" address="0a0c4000" size="023e2000"/>
    <module path="/usr/share/fonts/truetype/dejavu/DejaVuSansMono-Bold.ttf" address="b1e18000" size="0004e000"/>
    <module path="[stack:3727]" address="b1e67000" size="00800000"/>
    <module path="/usr/lib/codeblocks/plugins/libastyle.so" address="b26b0000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libastyle.so" address="b26b2000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libprojectsimporter.so" address="b26e4000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libscriptedwizard.so" address="b26e6000" size="00048000"/>
    <module path="/usr/lib/codeblocks/plugins/libscriptedwizard.so" address="b2732000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libdefaultmimehandler.so" address="b2747000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libdefaultmimehandler.so" address="b2749000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libtodo.so" address="b276f000" size="00002000"/>
    <module path="/usr/lib/codeblocks/plugins/libdebugger.so" address="b2772000" size="00080000"/>
    <module path="/usr/lib/codeblocks/plugins/libdebugger.so" address="b27f5000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libcompiler.so" address="b289c000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libcompiler.so" address="b28a0000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libcodecompletion.so" address="b28a3000" size="000f7000"/>
    <module path="/usr/lib/codeblocks/plugins/libcodecompletion.so" address="b299e000" size="00001000"/>
    <module path="/SYSV00000000" address="b29a0000" size="00060000"/>
    <module path="/usr/lib/codeblocks/plugins/libopenfileslist.so" address="b2b07000" size="00009000"/>
    <module path="/usr/lib/codeblocks/plugins/libopenfileslist.so" address="b2b11000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libautosave.so" address="b2b1f000" size="00001000"/>
    <module path="/usr/lib/codeblocks/plugins/libclasswizard.so" address="b2b21000" size="00017000"/>
    <module path="/usr/lib/codeblocks/plugins/libclasswizard.so" address="b2b39000" size="00001000"/>
    <module path="/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so" address="b2b3b000" size="00006000" version="xpm"/>
    <module path="/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so" address="b2b42000" size="00001000" version="xpm"/>
    <module path="[stack:3720]" address="b2b44000" size="00800000"/>
    <module path="[stack:3719]" address="b3345000" size="00800000"/>
    <module path="[stack:3718]" address="b3b46000" size="00800000"/>
    <module path="/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf" address="b4398000" size="000b6000"/>
    <module path="/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so" address="b447e000" size="00005000" version="png"/>
    <module path="/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so" address="b4484000" size="00001000" version="png"/>
    <module path="/usr/share/mime/mime.cache" address="b44a6000" size="00021000"/>
    <module path="/usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so" address="b44fe000" size="00001000" version="gnu/gio/modules/libgvfsdbus"/>
    <module path="/lib/i386-linux-gnu/libudev.so.1.6.2" address="b4603000" size="00014000" version="1.6.2"/>
    <module path="/lib/i386-linux-gnu/libudev.so.1.6.2" address="b4618000" size="00001000" version="1.6.2"/>
    <module path="/usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so" address="b4625000" size="00001000" version="gnu/gio/modules/libdconfsettings"/>
    <module path="[stack:3717]" address="b4628000" size="00800000"/>
    <module path="/usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so" address="b4e61000" size="00003000" version="gnu/gvfs/libgvfscommon"/>
    <module path="/usr/lib/i386-linux-gnu/gio/modules/libgioremote-volume-monitor.so" address="b4e65000" size="0001b000" version="monitor"/>
    <module path="/usr/lib/i386-linux-gnu/gio/modules/libgioremote-volume-monitor.so" address="b4e82000" size="00001000" version="monitor"/>
    <module path="/usr/share/icons/hicolor/icon-theme.cache" address="b4e8c000" size="00009000"/>
    <module path="/usr/share/icons/gnome/icon-theme.cache" address="b4e9e000" size="00009000"/>
    <module path="/usr/share/icons/elementary-xfce/icon-theme.cache" address="b4ed8000" size="00031000"/>
    <module path="/usr/share/icons/elementary-xfce-dark/icon-theme.cache" address="b4f0d000" size="00004000"/>
    <module path="/usr/share/icons/elementary-xfce-darker/icon-theme.cache" address="b4f1b000" size="0000a000"/>
    <module path="/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf" address="b4f54000" size="000aa000"/>
    <module path="/SYSV00000000" address="b5008000" size="00060000"/>
    <module path="/SYSV00000000" address="b506b000" size="00003000"/>
    <module path="/var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4" address="b506f000" size="00008000"/>
    <module path="/var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4" address="b507d000" size="00004000"/>
    <module path="/var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4" address="b5082000" size="00005000"/>
    <module path="/var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-le32d4.cache-4" address="b508a000" size="00003000"/>
    <module path="/var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4" address="b508e000" size="00010000"/>
    <module path="/var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4" address="b509f000" size="00003000"/>
    <module path="/var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4" address="b50a3000" size="00002000"/>
    <module path="/var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4" address="b50a6000" size="00004000"/>
    <module path="/var/cache/fontconfig/bab58bb527bb656aaa9f116d68a48d89-le32d4.cache-4" address="b50ad000" size="00001000"/>
    <module path="/var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-4" address="b50b3000" size="00001000"/>
    <module path="/var/cache/fontconfig/e49e89034d371f0f9de17aab02136486-le32d4.cache-4" address="b50b8000" size="00003000"/>
    <module path="/var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-4" address="b50cb000" size="00011000"/>
    <module path="/var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-4" address="b515c000" size="00001000"/>
    <module path="/var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4" address="b515f000" size="00009000"/>
    <module path="/lib/i386-linux-gnu/libnss_files-2.21.so" address="b5174000" size="00001000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libnss_nis-2.21.so" address="b5176000" size="0000b000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libnss_nis-2.21.so" address="b5182000" size="00001000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libnsl-2.21.so" address="b519a000" size="00001000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libnss_compat-2.21.so" address="b519e000" size="00008000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libnss_compat-2.21.so" address="b51a7000" size="00001000" version="2.21"/>
    <module path="/var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-4" address="b51b0000" size="00003000"/>
    <module path="/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-xim.so" address="b51bd000" size="00007000" version="xim"/>
    <module path="/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-xim.so" address="b51c5000" size="00001000" version="xim"/>
    <module path="/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so" address="b51fb000" size="00001000" version="2.0/2.10.0/engines/libmurrine"/>
    <module path="/usr/lib/locale/locale-archive" address="b51fd000" size="0003f000"/>
    <module path="/usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1" address="b5442000" size="0001b000" version="3.0.1"/>
    <module path="/usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1" address="b545e000" size="00001000" version="3.0.1"/>
    <module path="/usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0" address="b5464000" size="00001000" version="6.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXau.so.6.0.0" address="b5466000" size="00002000" version="6.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXau.so.6.0.0" address="b5469000" size="00001000" version="6.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libdatrie.so.1.3.1" address="b5471000" size="00001000" version="1.3.1"/>
    <module path="/usr/lib/i386-linux-gnu/libharfbuzz.so.0.937.0" address="b5474000" size="0005c000" version="0.937.0"/>
    <module path="/usr/lib/i386-linux-gnu/libharfbuzz.so.0.937.0" address="b54d1000" size="00001000" version="0.937.0"/>
    <module path="/lib/i386-linux-gnu/libresolv-2.21.so" address="b54e6000" size="00002000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libselinux.so.1" address="b54eb000" size="00024000" version="1"/>
    <module path="/lib/i386-linux-gnu/libselinux.so.1" address="b5510000" size="00001000" version="1"/>
    <module path="/lib/i386-linux-gnu/librt-2.21.so" address="b5512000" size="00007000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/librt-2.21.so" address="b551a000" size="00001000" version="2.21"/>
    <module path="/usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0" address="b5523000" size="00001000" version="0.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0" address="b5526000" size="00002000" version="0.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0" address="b5529000" size="00001000" version="0.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libpixman-1.so.0.32.6" address="b55d5000" size="00007000" version="0.32.6"/>
    <module path="/usr/lib/i386-linux-gnu/libxcb.so.1.1.0" address="b55dd000" size="00020000" version="1.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libxcb.so.1.1.0" address="b55fe000" size="00001000" version="1.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libfreetype.so.6.11.1" address="b56aa000" size="00004000" version="6.11.1"/>
    <module path="/usr/lib/i386-linux-gnu/libjbig.so.0" address="b56af000" size="0000b000" version="0"/>
    <module path="/usr/lib/i386-linux-gnu/libjbig.so.0" address="b56bb000" size="00003000" version="0"/>
    <module path="/lib/i386-linux-gnu/liblzma.so.5.0.0" address="b56bf000" size="00024000" version="5.0.0"/>
    <module path="/lib/i386-linux-gnu/liblzma.so.5.0.0" address="b56e4000" size="00001000" version="5.0.0"/>
    <module path="/lib/i386-linux-gnu/libuuid.so.1.3.0" address="b56e9000" size="00001000" version="1.3.0"/>
    <module path="/usr/lib/i386-linux-gnu/libICE.so.6.3.0" address="b56eb000" size="00016000" version="6.3.0"/>
    <module path="/usr/lib/i386-linux-gnu/libICE.so.6.3.0" address="b5702000" size="00001000" version="6.3.0"/>
    <module path="/usr/lib/i386-linux-gnu/libthai.so.0.2.0" address="b5705000" size="00008000" version="0.2.0"/>
    <module path="/usr/lib/i386-linux-gnu/libthai.so.0.2.0" address="b570e000" size="00001000" version="0.2.0"/>
    <module path="/lib/i386-linux-gnu/libpcre.so.3.13.1" address="b577f000" size="00001000" version="3.13.1"/>
    <module path="/usr/lib/i386-linux-gnu/libXext.so.6.4.0" address="b5782000" size="00013000" version="6.4.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXext.so.6.4.0" address="b5796000" size="00001000" version="6.4.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXdamage.so.1.1.0" address="b5799000" size="00001000" version="1.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0" address="b579b000" size="00002000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0" address="b579e000" size="00001000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXcursor.so.1.0.2" address="b57a8000" size="00001000" version="1.0.2"/>
    <module path="/usr/lib/i386-linux-gnu/libXrandr.so.2.2.0" address="b57aa000" size="00009000" version="2.2.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXrandr.so.2.2.0" address="b57b4000" size="00001000" version="2.2.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXi.so.6.1.0" address="b57b6000" size="00010000" version="6.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXi.so.6.1.0" address="b57c7000" size="00001000" version="6.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXrender.so.1.3.0" address="b57d2000" size="00001000" version="1.3.0"/>
    <module path="/lib/i386-linux-gnu/libexpat.so.1.6.0" address="b57d4000" size="00026000" version="1.6.0"/>
    <module path="/lib/i386-linux-gnu/libexpat.so.1.6.0" address="b57fc000" size="00001000" version="1.6.0"/>
    <module path="/usr/lib/i386-linux-gnu/libffi.so.6.0.4" address="b5804000" size="00002000" version="6.0.4"/>
    <module path="/usr/lib/i386-linux-gnu/libfontconfig.so.1.8.0" address="b5807000" size="00041000" version="1.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libfontconfig.so.1.8.0" address="b5849000" size="00001000" version="1.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3600.8" address="b584b000" size="00015000" version="0.3600.8"/>
    <module path="/usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3600.8" address="b5861000" size="00001000" version="0.3600.8"/>
    <module path="/usr/lib/i386-linux-gnu/libgio-2.0.so.0.4400.0" address="b5a1b000" size="00003000" version="0.4400.0"/>
    <module path="/usr/lib/i386-linux-gnu/libcairo.so.2.11400.2" address="b5a21000" size="00143000" version="2.11400.2"/>
    <module path="/usr/lib/i386-linux-gnu/libcairo.so.2.11400.2" address="b5b66000" size="00001000" version="2.11400.2"/>
    <module path="/usr/lib/i386-linux-gnu/libatk-1.0.so.0.21409.1" address="b5b68000" size="00024000" version="0.21409.1"/>
    <module path="/usr/lib/i386-linux-gnu/libatk-1.0.so.0.21409.1" address="b5b8e000" size="00001000" version="0.21409.1"/>
    <module path="/usr/lib/i386-linux-gnu/libXfixes.so.3.1.0" address="b5b94000" size="00001000" version="3.1.0"/>
    <module path="/usr/lib/i386-linux-gnu/libX11.so.6.3.0" address="b5b97000" size="00147000" version="6.3.0"/>
    <module path="/usr/lib/i386-linux-gnu/libX11.so.6.3.0" address="b5cdf000" size="00002000" version="6.3.0"/>
    <module path="/usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3600.8" address="b5ce2000" size="0000c000" version="0.3600.8"/>
    <module path="/usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3600.8" address="b5cef000" size="00001000" version="0.3600.8"/>
    <module path="/usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.4400.0" address="b5cf3000" size="00001000" version="0.4400.0"/>
    <module path="/lib/i386-linux-gnu/libdl-2.21.so" address="b5cf5000" size="00003000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libdl-2.21.so" address="b5cf9000" size="00001000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libz.so.1.2.8" address="b5d13000" size="00001000" version="1.2.8"/>
    <module path="/usr/lib/i386-linux-gnu/libtiff.so.5.2.0" address="b5d16000" size="00077000" version="5.2.0"/>
    <module path="/usr/lib/i386-linux-gnu/libtiff.so.5.2.0" address="b5d8e000" size="00002000" version="5.2.0"/>
    <module path="/usr/lib/i386-linux-gnu/libjpeg.so.8.0.2" address="b5d91000" size="00049000" version="8.0.2"/>
    <module path="/usr/lib/i386-linux-gnu/libjpeg.so.8.0.2" address="b5ddb000" size="00001000" version="8.0.2"/>
    <module path="/lib/i386-linux-gnu/libpng12.so.0.51.0" address="b5dec000" size="0002a000" version="0.51.0"/>
    <module path="/lib/i386-linux-gnu/libpng12.so.0.51.0" address="b5e17000" size="00001000" version="0.51.0"/>
    <module path="/usr/lib/i386-linux-gnu/libSM.so.6.0.1" address="b5e1f000" size="00001000" version="6.0.1"/>
    <module path="/usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0" address="b5e21000" size="00004000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0" address="b5e26000" size="00001000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXinerama.so.1.0.0" address="b5e28000" size="00002000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libXinerama.so.1.0.0" address="b5e2b000" size="00001000" version="1.0.0"/>
    <module path="/usr/lib/i386-linux-gnu/libpango-1.0.so.0.3600.8" address="b5e7c000" size="00001000" version="0.3600.8"/>
    <module path="/lib/i386-linux-gnu/libglib-2.0.so.0.4400.0" address="b5e7e000" size="00126000" version="0.4400.0"/>
    <module path="/lib/i386-linux-gnu/libglib-2.0.so.0.4400.0" address="b5fa5000" size="00001000" version="0.4400.0"/>
    <module path="/usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.3100.3" address="b5fcc000" size="00001000" version="0.3100.3"/>
    <module path="/usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.27" address="b5fce000" size="000bd000" version="0.2400.27"/>
    <module path="/usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.27" address="b608d000" size="00001000" version="0.2400.27"/>
    <module path="/lib/i386-linux-gnu/libm-2.21.so" address="b608f000" size="0004b000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libm-2.21.so" address="b60db000" size="00001000" version="2.21"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_baseu_xml-2.8.so.0.8.0" address="b60e4000" size="00001000" version="0.8.0"/>
    <module path="/lib/i386-linux-gnu/libc-2.21.so" address="b60e6000" size="001b4000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libc-2.21.so" address="b629d000" size="00002000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libgcc_s.so.1" address="b62a1000" size="0001c000" version="1"/>
    <module path="/usr/lib/i386-linux-gnu/libstdc++.so.6.0.20" address="b62be000" size="000e9000" version="6.0.20"/>
    <module path="/usr/lib/i386-linux-gnu/libstdc++.so.6.0.20" address="b63ab000" size="00001000" version="6.0.20"/>
    <module path="/lib/i386-linux-gnu/libpthread-2.21.so" address="b63b4000" size="00019000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/libpthread-2.21.so" address="b63ce000" size="00001000" version="2.21"/>
    <module path="/usr/lib/i386-linux-gnu/libgobject-2.0.so.0.4400.0" address="b63d1000" size="0005b000" version="0.4400.0"/>
    <module path="/usr/lib/i386-linux-gnu/libgobject-2.0.so.0.4400.0" address="b642d000" size="00001000" version="0.4400.0"/>
    <module path="/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.27" address="b691c000" size="00004000" version="0.2400.27"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_baseu-2.8.so.0.8.0" address="b6924000" size="00141000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_baseu-2.8.so.0.8.0" address="b6a69000" size="00002000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_baseu_net-2.8.so.0.8.0" address="b6a73000" size="0002b000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_baseu_net-2.8.so.0.8.0" address="b6aa0000" size="00001000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_core-2.8.so.0.8.0" address="b6aa2000" size="00351000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_core-2.8.so.0.8.0" address="b6e1a000" size="00005000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_adv-2.8.so.0.8.0" address="b6e26000" size="000b5000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_adv-2.8.so.0.8.0" address="b6ee3000" size="00001000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_html-2.8.so.0.8.0" address="b6ee6000" size="0009c000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_html-2.8.so.0.8.0" address="b6f87000" size="00001000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_qa-2.8.so.0.8.0" address="b6f89000" size="00019000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_qa-2.8.so.0.8.0" address="b6fa4000" size="00001000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_xrc-2.8.so.0.8.0" address="b703f000" size="00003000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_aui-2.8.so.0.8.0" address="b7045000" size="0005c000" version="0.8.0"/>
    <module path="/usr/lib/i386-linux-gnu/libwx_gtk2u_aui-2.8.so.0.8.0" address="b70a5000" size="00001000" version="0.8.0"/>
    <module path="/usr/lib/libcodeblocks.so.0.0.1" address="b70a7000" size="005f7000" version="0.0.1"/>
    <module path="/usr/lib/libcodeblocks.so.0.0.1" address="b76b3000" size="00002000" version="0.0.1"/>
    <module path="/var/cache/fontconfig/551ecf3b0e8b0bca0f25c0944f561853-le32d4.cache-4" address="b76bc000" size="00001000"/>
    <module path="/var/cache/fontconfig/16326683038b281783a0ef8c680e3a10-le32d4.cache-4" address="b76be000" size="00002000"/>
    <module path="/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so" address="b76c1000" size="0000a000" version="2.0/2.10.0/engines/libpixmap"/>
    <module path="/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so" address="b76cc000" size="00001000" version="2.0/2.10.0/engines/libpixmap"/>
    <module path="/usr/lib/i386-linux-gnu/gconv/UTF-32.so" address="b76ce000" size="00002000" version="32"/>
    <module path="/usr/lib/i386-linux-gnu/gconv/UTF-32.so" address="b76d1000" size="00001000" version="32"/>
    <module path="/usr/lib/locale/locale-archive" address="b76d9000" size="00001000"/>
    <module path="[vvar]" address="b76dc000" size="00002000"/>
    <module path="/lib/i386-linux-gnu/ld-2.21.so" address="b76df000" size="00022000" version="2.21"/>
    <module path="/lib/i386-linux-gnu/ld-2.21.so" address="b7702000" size="00001000" version="2.21"/>
  </modules>
</report>


```

i dont see anything here clarifying the reason for such error. after i close the warning, codeblocks shutsdown, and if i restart it, will work normally. only once, last week, its shutsdown in the middle of work, without warning  

I can tell you i have Ubuntu 15.04 (vivid), xubuntu distro. codeblocks is updated to 13.12. any other info you need, just ask, please

Any thougts?

---

### Post by achuthpnr on 2015-05-15
check this: 
1. launch Codeblocks and click anywhere on the screen while the splash screen is appearing 
2. launch codeblocks and stay idle 

If it is case 1, I think it is a reported bug. 
I´ve read about this before, since I also had this problem. But couldnt locate the corresponding page now.

---

