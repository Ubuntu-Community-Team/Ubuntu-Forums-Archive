---
title: "Code::Blocks Crash (from repo)"
date: 2008-03-02
forum: Programming Talk
---

### Post by FlyingIsFun1217 on 2008-03-02
Hey!

Now that C::B has an official release (stable), I'm extremely happy. Thing is, after I run it (using alt-F2, typing codeblocks, choosing entry given at bottom), everything starts up fine, but upon closing, it crashes.

Here's the debug report screen I get:

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/DBG_RPRT.png[/IMG]

And the report:

```

<?xml version="1.0" encoding="utf-8"?>
<report version="1.0" kind="exception">
  <system description="Linux 2.6.24-10-generic i686"/>
  <modules>
    <module path="/usr/bin/codeblocks" address="08048000" size="0008c000"/>
    <module path="[heap]" address="080d9000" size="00d03000"/>
    <module path="/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf" address="b2ada000" size="0004d000"/>
    <module path="/usr/share/codeblocks/plugins/libcodestat.so" address="b2b71000" size="00014000"/>
    <module path="/usr/share/codeblocks/plugins/libhelp_plugin.so" address="b2b86000" size="00139000"/>
    <module path="/usr/share/codeblocks/plugins/libcodecompletion.so" address="b34ca000" size="000b3000"/>
    <module path="/usr/share/codeblocks/plugins/libscriptedwizard.so" address="b3582000" size="00060000"/>
    <module path="/usr/share/codeblocks/plugins/libProfiler.so" address="b35e7000" size="00019000"/>
    <module path="/usr/share/codeblocks/plugins/libcompiler.so" address="b3602000" size="0016e000"/>
    <module path="/usr/lib/libwxsmithlib.so.0.0.1" address="b3775000" size="0030d000" version="0.0.1"/>
    <module path="/usr/share/codeblocks/plugins/libwxsmith.so" address="b3ab4000" size="00002000"/>
    <module path="/usr/share/codeblocks/plugins/libwxsmithcontribitems.so" address="b3ab7000" size="0004f000"/>
    <module path="/usr/share/codeblocks/plugins/libBrowseTracker.so" address="b3b0b000" size="00034000"/>
    <module path="/usr/share/codeblocks/plugins/libopenfileslist.so" address="b3b42000" size="00009000"/>
    <module path="/usr/share/codeblocks/plugins/libRegExTestbed.so" address="b3b4c000" size="0000c000"/>
    <module path="/usr/share/codeblocks/plugins/liblib_finder.so" address="b3b59000" size="00046000"/>
    <module path="/usr/share/codeblocks/plugins/libexporter.so" address="b3ba2000" size="000da000"/>
    <module path="/usr/share/codeblocks/plugins/libprojectsimporter.so" address="b3c84000" size="0002b000"/>
    <module path="/usr/share/codeblocks/plugins/libThreadSearch.so" address="b3cb0000" size="0004c000"/>
    <module path="/usr/share/codeblocks/plugins/libtodo.so" address="b3d00000" size="00023000"/>
    <module path="/usr/share/codeblocks/plugins/libAutoVersioning.so" address="b3d25000" size="0004a000"/>
    <module path="/usr/share/codeblocks/plugins/libcb_koders.so" address="b3d71000" size="00016000"/>
    <module path="/usr/share/codeblocks/plugins/libbyogames.so" address="b3d88000" size="00030000"/>
    <module path="/usr/share/codeblocks/plugins/libastyle.so" address="b3dbb000" size="00032000"/>
    <module path="/usr/share/codeblocks/plugins/libSymTab.so" address="b3def000" size="0001a000"/>
    <module path="/usr/share/codeblocks/plugins/libdefaultmimehandler.so" address="b3e0b000" size="00017000"/>
    <module path="/usr/share/codeblocks/plugins/libautosave.so" address="b3e24000" size="0000c000"/>
    <module path="/usr/share/codeblocks/plugins/libdragscroll.so" address="b3e31000" size="00019000"/>
    <module path="/usr/share/codeblocks/plugins/libclasswizard.so" address="b3e4c000" size="00015000"/>
    <module path="/usr/share/codeblocks/plugins/libdebugger.so" address="b3e62000" size="000a1000"/>
    <module path="/usr/share/codeblocks/plugins/libenvvars.so" address="b3f0a000" size="0001c000"/>
    <module path="/usr/share/codeblocks/plugins/libcodesnippets.so" address="b3f28000" size="0009a000"/>
    <module path="/usr/share/codeblocks/plugins/libkeybinder.so" address="b3fca000" size="0003d000"/>
    <module path="/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so" address="b400a000" size="00006000" version="xpm"/>
    <module path="/usr/share/fonts/truetype/msttcorefonts/Arial.ttf" address="b6016000" size="00044000"/>
    <module path="/SYSV00000000" address="b60ba000" size="00003000"/>
    <module path="/usr/lib/pango/1.6.0/modules/pango-basic-fc.so" address="b6103000" size="00002000" version="fc"/>
    <module path="/var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2" address="b6106000" size="00006000"/>
    <module path="/var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2" address="b610d000" size="00002000"/>
    <module path="/var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2" address="b6113000" size="00003000"/>
    <module path="/var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2" address="b6176000" size="00001000"/>
    <module path="/var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2" address="b6178000" size="00002000"/>
    <module path="/var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2" address="b617d000" size="00002000"/>
    <module path="/var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2" address="b6180000" size="00002000"/>
    <module path="/var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2" address="b6188000" size="00002000"/>
    <module path="/var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2" address="b618c000" size="00006000"/>
    <module path="/var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2" address="b6193000" size="00017000"/>
    <module path="/var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2" address="b61b0000" size="00007000"/>
    <module path="/var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2" address="b61b8000" size="00001000"/>
    <module path="/var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2" address="b61ba000" size="00002000"/>
    <module path="/var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2" address="b61bf000" size="00008000"/>
    <module path="/var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2" address="b61c9000" size="00002000"/>
    <module path="/var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2" address="b61d0000" size="00004000"/>
    <module path="/var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2" address="b61d6000" size="00001000"/>
    <module path="/var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2" address="b61d8000" size="00004000"/>
    <module path="/var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2" address="b61e2000" size="00006000"/>
    <module path="/usr/lib/libgnomecanvas-2.so.0.2000.0" address="b61ec000" size="0002f000" version="0.2000.0"/>
    <module path="/usr/lib/libgnomeprintui-2-2.so.0.1.0" address="b621c000" size="0003e000" version="0.1.0"/>
    <module path="/usr/lib/libxml2.so.2.6.30" address="b625c000" size="00118000" version="2.6.30"/>
    <module path="/usr/lib/libart_lgpl_2.so.2.3.19" address="b637a000" size="00015000" version="2.3.19"/>
    <module path="/usr/lib/libgnomeprint-2-2.so.0.1.0" address="b6390000" size="00065000" version="0.1.0"/>
    <module path="/var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2" address="b63f7000" size="00004000"/>
    <module path="/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so" address="b6408000" size="00004000" version="png"/>
    <module path="/lib/tls/i686/cmov/libnss_files-2.7.so" address="b640d000" size="00009000" version="2.7"/>
    <module path="/lib/tls/i686/cmov/libnss_nis-2.7.so" address="b6418000" size="00008000" version="2.7"/>
    <module path="/lib/tls/i686/cmov/libnsl-2.7.so" address="b6422000" size="00014000" version="2.7"/>
    <module path="/lib/tls/i686/cmov/libnss_compat-2.7.so" address="b643a000" size="00007000" version="2.7"/>
    <module path="/var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2" address="b6443000" size="00001000"/>
    <module path="/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so" address="b6446000" size="00007000" version="2.0/2.10.0/engines/libpixmap"/>
    <module path="/usr/lib/libgailutil.so.18.0.1" address="b644e000" size="00007000" version="18.0.1"/>
    <module path="/usr/lib/gconv/ISO8859-1.so" address="b6456000" size="00001000" version="1"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_COLLATE" address="b6459000" size="000e0000"/>
    <module path="/usr/lib/libdirect-0.9.so.25.0.0" address="b657c000" size="0000e000" version="25.0.0"/>
    <module path="/usr/lib/libfusion-0.9.so.25.0.0" address="b658b000" size="00005000" version="25.0.0"/>
    <module path="/usr/lib/libdirectfb-0.9.so.25.0.0" address="b6591000" size="00055000" version="25.0.0"/>
    <module path="/usr/lib/libasound.so.2.0.0" address="b65e8000" size="000c1000" version="2.0.0"/>
    <module path="/usr/lib/libICE.so.6.3.0" address="b66af000" size="00015000" version="6.3.0"/>
    <module path="/usr/lib/libSDL-1.2.so.0.11.0" address="b66c7000" size="00065000" version="0.11.0"/>
    <module path="/usr/lib/libtiff.so.4.2.1" address="b6757000" size="00052000" version="4.2.1"/>
    <module path="/usr/lib/libjpeg.so.62.0.0" address="b67ab000" size="0001f000" version="62.0.0"/>
    <module path="/usr/lib/libSM.so.6.0.0" address="b67cb000" size="00007000" version="6.0.0"/>
    <module path="/lib/tls/i686/cmov/librt-2.7.so" address="b67d3000" size="00007000" version="2.7"/>
    <module path="/usr/lib/libgthread-2.0.so.0.1400.1" address="b67dc000" size="00004000" version="0.1400.1"/>
    <module path="/usr/lib/libXdmcp.so.6.0.0" address="b67e2000" size="00004000" version="6.0.0"/>
    <module path="/usr/lib/libexpat.so.1.0.0" address="b67e7000" size="0001e000" version="1.0.0"/>
    <module path="/usr/lib/libXau.so.6.0.0" address="b6807000" size="00002000" version="6.0.0"/>
    <module path="/usr/lib/libpangoft2-1.0.so.0.1800.3" address="b680a000" size="0002d000" version="0.1800.3"/>
    <module path="/usr/lib/libXdamage.so.1.1.0" address="b6839000" size="00002000" version="1.1.0"/>
    <module path="/usr/lib/libXcomposite.so.1.0.0" address="b683c000" size="00002000" version="1.0.0"/>
    <module path="/lib/tls/i686/cmov/libc-2.7.so" address="b683f000" size="00149000" version="2.7"/>
    <module path="/lib/tls/i686/cmov/libc-2.7.so" address="b6989000" size="00002000" version="2.7"/>
    <module path="/lib/libgcc_s.so.1" address="b698e000" size="0000a000" version="1"/>
    <module path="/lib/tls/i686/cmov/libm-2.7.so" address="b6999000" size="00023000" version="2.7"/>
    <module path="/usr/lib/libstdc++.so.6.0.9" address="b69be000" size="000e8000" version="6.0.9"/>
    <module path="/usr/lib/libstdc++.so.6.0.9" address="b6aa9000" size="00002000" version="6.0.9"/>
    <module path="/lib/tls/i686/cmov/libdl-2.7.so" address="b6ab2000" size="00002000" version="2.7"/>
    <module path="/lib/tls/i686/cmov/libpthread-2.7.so" address="b6ab6000" size="00014000" version="2.7"/>
    <module path="/usr/lib/libwx_baseu-2.8.so.0.4.0" address="b6ace000" size="00159000" version="0.4.0"/>
    <module path="/usr/lib/libwx_baseu_net-2.8.so.0.4.0" address="b6c36000" size="0002e000" version="0.4.0"/>
    <module path="/usr/lib/libwx_baseu_xml-2.8.so.0.4.0" address="b6c66000" size="00009000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_core-2.8.so.0.4.0" address="b6c71000" size="0036f000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_adv-2.8.so.0.4.0" address="b7013000" size="000c0000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_html-2.8.so.0.4.0" address="b70de000" size="0009c000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_qa-2.8.so.0.4.0" address="b7181000" size="0001e000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_xrc-2.8.so.0.4.0" address="b71a1000" size="00097000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_aui-2.8.so.0.4.0" address="b723e000" size="00053000" version="0.4.0"/>
    <module path="/usr/lib/libwx_gtk2u_richtext-2.8.so.0.4.0" address="b7295000" size="000eb000" version="0.4.0"/>
    <module path="/usr/lib/libcodeblocks.so.0.0.1" address="b7389000" size="0043d000" version="0.0.1"/>
    <module path="/usr/lib/libglib-2.0.so.0.1400.1" address="b77e1000" size="000bc000" version="0.1400.1"/>
    <module path="/usr/lib/libgmodule-2.0.so.0.1400.1" address="b789e000" size="00003000" version="0.1400.1"/>
    <module path="/usr/lib/libgobject-2.0.so.0.1400.1" address="b78a3000" size="0003a000" version="0.1400.1"/>
    <module path="/usr/lib/libX11.so.6.2.0" address="b78de000" size="000ed000" version="6.2.0"/>
    <module path="/usr/lib/libXrender.so.1.3.0" address="b79cf000" size="00007000" version="1.3.0"/>
    <module path="/usr/lib/libpng12.so.0.15.0" address="b79d7000" size="00022000" version="0.15.0"/>
    <module path="/usr/lib/libfontconfig.so.1.2.0" address="b79fa000" size="00023000" version="1.2.0"/>
    <module path="/usr/lib/libz.so.1.2.3.3" address="b7a25000" size="00014000" version="1.2.3.3"/>
    <module path="/usr/lib/libfreetype.so.6.3.16" address="b7a3b000" size="0006c000" version="6.3.16"/>
    <module path="/usr/lib/libcairo.so.2.11.5" address="b7aab000" size="00075000" version="2.11.5"/>
    <module path="/usr/lib/libpango-1.0.so.0.1800.3" address="b7b22000" size="0003b000" version="0.1800.3"/>
    <module path="/usr/lib/libXfixes.so.3.1.0" address="b7b5f000" size="00004000" version="3.1.0"/>
    <module path="/usr/lib/libXcursor.so.1.0.2" address="b7b64000" size="00008000" version="1.0.2"/>
    <module path="/usr/lib/libXrandr.so.2.1.0" address="b7b6d000" size="00005000" version="2.1.0"/>
    <module path="/usr/lib/libXi.so.6.0.0" address="b7b74000" size="00007000" version="6.0.0"/>
    <module path="/usr/lib/libXinerama.so.1.0.0" address="b7b7c000" size="00002000" version="1.0.0"/>
    <module path="/usr/lib/libXext.so.6.4.0" address="b7b7f000" size="0000d000" version="6.4.0"/>
    <module path="/usr/lib/libpangocairo-1.0.so.0.1800.3" address="b7b8d000" size="00008000" version="0.1800.3"/>
    <module path="/usr/lib/libgdk_pixbuf-2.0.so.0.1200.0" address="b7b96000" size="00016000" version="0.1200.0"/>
    <module path="/usr/lib/libatk-1.0.so.0.2009.1" address="b7bad000" size="00019000" version="0.2009.1"/>
    <module path="/usr/lib/libgdk-x11-2.0.so.0.1200.0" address="b7bc9000" size="0007f000" version="0.1200.0"/>
    <module path="/usr/lib/libgtk-x11-2.0.so.0.1200.0" address="b7c4b000" size="00365000" version="0.1200.0"/>
    <module path="/var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2" address="b7fb7000" size="00001000"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_TIME" address="b7fb9000" size="00001000"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES" address="b7fbb000" size="00001000"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_NAME" address="b7fbd000" size="00001000"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_TELEPHONE" address="b7fbf000" size="00001000"/>
    <module path="/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION" address="b7fc1000" size="00001000"/>
    <module path="/usr/lib/gconv/UTF-32.so" address="b7fc4000" size="00002000" version="32"/>
    <module path="[vdso]" address="b7fcf000" size="00001000"/>
    <module path="/lib/ld-2.7.so" address="b7fea000" size="00002000" version="2.7"/>
  </modules>
  <stack>
    <frame level="0" function="wxFatalSignalHandler" offset="00000026"/>
    <frame level="1"/>
    <frame level="2"/>
    <frame level="3" function="g_cclosure_marshal_VOID__VOID" offset="00000049"/>
    <frame level="4" function="g_closure_invoke" offset="00000122"/>
    <frame level="5"/>
    <frame level="6" function="g_signal_emit_valist" offset="000008c7"/>
    <frame level="7" function="g_signal_emit" offset="00000029"/>
    <frame level="8"/>
    <frame level="9"/>
    <frame level="10"/>
    <frame level="11" function="g_object_run_dispose" offset="00000050"/>
    <frame level="12" function="gtk_object_destroy" offset="00000055"/>
    <frame level="13" function="gtk_widget_destroy" offset="00000045"/>
    <frame level="14" function="wxWindow::~wxWindow()" offset="00000144"/>
    <frame level="15" function="wxTopLevelWindowBase::~wxTopLevelWindowBase()" offset="0000008c"/>
    <frame level="16" function="wxTopLevelWindowGTK::~wxTopLevelWindowGTK()" offset="000000ae"/>
    <frame level="17" function="wxFrameBase::~wxFrameBase()" offset="00000051"/>
    <frame level="18" function="wxFrame::~wxFrame()" offset="0000003f"/>
    <frame level="19" function="~MainFrame" offset="00000000" file="/tmp/buildd/codeblocks-8.02/src/src/main.cpp" line="564"/>
    <frame level="20" function="wxAppBase::DeletePendingObjects()" offset="0000005a"/>
    <frame level="21" function="wxAppBase::ProcessIdle()" offset="000000be"/>
    <frame level="22"/>
    <frame level="23"/>
    <frame level="24" function="g_main_context_dispatch" offset="0000017c"/>
    <frame level="25"/>
    <frame level="26" function="g_main_loop_run" offset="000001a9"/>
    <frame level="27" function="gtk_main" offset="000000b4"/>
    <frame level="28" function="wxEventLoop::Run()" offset="0000005c"/>
    <frame level="29" function="wxAppBase::MainLoop()" offset="0000004e"/>
    <frame level="30" function="wxAppBase::OnRun()" offset="00000021"/>
    <frame level="31" function="CodeBlocksApp::OnBatchBuildDone(CodeBlocksEvent&amp;)" offset="00000000" file="/tmp/buildd/codeblocks-8.02/src/src/app.cpp" line="607"/>
  </stack>
</report>

```

Any ideas? This is the one and only IDE I use, and even the old nightlies are giving me this... :/

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-03-03
Is there anybody out there with ideas?

FlyingIsFun1217

---

### Post by vfdff on 2009-04-08
do you figure out it ,I have come on the same problem,hope some help from you !

---

### Post by Yacoby on 2009-04-08
> **vfdff said:**
> do you figure out it ,I have come on the same problem,hope some help from you !

Try running a more recent build. The stable build is a year old.

---

### Post by doorman on 2009-04-08
You can install the nightly builds with apt / synaptic.

The instructions on how to add the repo are [here]("http://lgp203.free.fr/spip/spip.php?article1&lang=en"). Unfortunately, only the french version of the document exists, but the basic idea is:
1) add the wxWidgets repo
2) add the code::blocks repo
3) update && upgrade

hope this helps!

---

