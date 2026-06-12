---
title: "how to make tk8.5 in Ubuntu 7.10"
date: 2008-04-16
forum: Programming Talk
---

### Post by robinwt on 2008-04-16
I try to install tk8.5.2 on my Ubuntu 7.10 platform (tcl8.5.2 seems to be gone through without a issue), however, I got the following error message:
make
rm -f libtk8.5.so
gcc -shared -O2  -pipe    -Wl,--export-dynamic -o libtk8.5.so tk3d.o tkArgv.o tkAtom.o tkBind.o tkBitmap.o tkClipboard.o tkCmds.o tkColor.o tkConfig.o tkConsole.o tkCursor.o tkError.o tkEvent.o tkFocus.o tkFont.o tkGet.o tkGC.o tkGeometry.o tkGrab.o tkGrid.o tkMain.o tkObj.o tkOldConfig.o tkOption.o tkPack.o tkPlace.o tkSelect.o tkStyle.o tkUndo.o tkUtil.o tkVisual.o tkWindow.o tkButton.o tkEntry.o tkFrame.o tkListbox.o tkMenu.o tkMenubutton.o tkMenuDraw.o tkMessage.o tkPanedWindow.o tkScale.o tkScrollbar.o tkCanvas.o tkCanvArc.o tkCanvBmap.o tkCanvImg.o tkCanvLine.o tkCanvPoly.o tkCanvPs.o tkCanvText.o tkCanvUtil.o tkCanvWind.o tkRectOval.o tkTrig.o tkImage.o tkImgBmap.o tkImgGIF.o tkImgPPM.o tkImgPhoto.o tkText.o tkTextBTree.o tkTextDisp.o tkTextImage.o tkTextIndex.o tkTextMark.o tkTextTag.o tkTextWind.o tkStubInit.o tkStubLib.o ttkBlink.o ttkButton.o ttkCache.o ttkClamTheme.o ttkClassicTheme.o ttkDefaultTheme.o ttkElements.o ttkEntry.o ttkFrame.o ttkImage.o ttkInit.o ttkLabel.o ttkLayout.o ttkManager.o ttkNotebook.o ttkPanedwindow.o ttkProgress.o ttkScale.o ttkScrollbar.o ttkScroll.o ttkSeparator.o ttkSquare.o ttkState.o ttkTagSet.o ttkTheme.o ttkTrace.o ttkTrack.o ttkTreeview.o ttkWidget.o ttkStubInit.o tkUnix.o tkUnix3d.o tkUnixButton.o tkUnixColor.o tkUnixConfig.o tkUnixCursor.o tkUnixDraw.o tkUnixEmbed.o tkUnixEvent.o tkUnixFocus.o  tkUnixFont.o tkUnixInit.o tkUnixKey.o tkUnixMenu.o tkUnixMenubu.o tkUnixScale.o tkUnixScrlbr.o tkUnixSelect.o tkUnixSend.o tkUnixWm.o tkUnixXId.o  -l/home/tk8.5.2/xlib/X11  -ldl  -lieee -lm -L/home/tcl8.5.2/unix -ltclstub8.5   -Wl,-rpath,/usr/local/lib
/usr/bin/ld: cannot find -l/home/tk8.5.2/xlib/X11
collect2: ld returned 1 exit status
make: *** [libtk8.5.so] Error 1

how to ensure the path is added and linked.

Regards/Robin

---

### Post by ibutho on 2008-04-16
Install xorg-dev, then run make again to see if that resolves the problem.

---

### Post by stevescripts on 2008-04-16
A couple of quick questions ...

Are you sure that tcl8.5.2 built ok?  Did you run make test after make?

Did you run ./configure prior to running make?

Again, see what ibutho wrote above - you definintely need the xorg-dev files installed
to successfully build tk.

Hope this helps.

Steve
feel free to post back other problems

---

### Post by stevescripts on 2008-04-16
Update:

Found time to build tcl/tk8.5.2 here this pm.

No problems.

Again, post back if you are still having trouble.

Steve

---

### Post by robinwt on 2008-04-16
Thanks Guys,
I did try to install by 
sudo dpkg -i xorg-dev_7.2-5ubuntu13_all.deb, however I got:

(Reading database ... 91170 files and directories currently installed.)
Preparing to replace xorg-dev 1:7.3+10ubuntu7 (using xorg-dev_7.2-5ubuntu13_all.deb) ...
Unpacking replacement xorg-dev ...
dpkg: dependency problems prevent configuration of xorg-dev:
 xorg-dev depends on libdmx-dev; however:
  Package libdmx-dev is not installed.
 xorg-dev depends on libfontenc-dev; however:
  Package libfontenc-dev is not installed.
 xorg-dev depends on libfs-dev; however:
  Package libfs-dev is not installed.
 xorg-dev depends on libice-dev; however:
  Package libice-dev is not installed.
 xorg-dev depends on libsm-dev; however:
  Package libsm-dev is not installed.
 xorg-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
 xorg-dev depends on libxau-dev; however:
  Package libxau-dev is not installed.
 xorg-dev depends on libxaw7-dev; however:
  Package libxaw7-dev is not installed.
 xorg-dev depends on libxcomposite-dev; however:
  Package libxcomposite-dev is not installed.
 xorg-dev depends on libxcursor-dev; however:
  Package libxcursor-dev is not installed.
 xorg-dev depends on libxdamage-dev; however:
  Package libxdamage-dev is not installed.
 xorg-dev depends on libxdmcp-dev; however:
  Package libxdmcp-dev is not installed.
 xorg-dev depends on libxevie-dev; however:
  Package libxevie-dev is not installed.
 xorg-dev depends on libxext-dev; however:
  Package libxext-dev is not installed.
 xorg-dev depends on libxfixes-dev; however:
  Package libxfixes-dev is not installed.
 xorg-dev depends on libxfont-dev; however:
  Package libxfont-dev is not installed.
 xorg-dev depends on libxft-dev; however:
  Package libxft-dev is not installed.
 xorg-dev depends on libxi-dev; however:
  Package libxi-dev is not installed.
 xorg-dev depends on libxinerama-dev; however:
  Package libxinerama-dev is not installed.
 xorg-dev depends on libxkbfile-dev; however:
  Package libxkbfile-dev is not installed.
 xorg-dev depends on libxkbui-dev; however:
  Package libxkbui-dev is not installed.
 xorg-dev depends on libxmu-dev; however:
  Package libxmu-dev is not installed.
 xorg-dev depends on libxmuu-dev; however:
  Package libxmuu-dev is not installed.
 xorg-dev depends on libxpm-dev; however:
  Package libxpm-dev is not installed.
 xorg-dev depends on libxrandr-dev; however:
  Package libxrandr-dev is not installed.
 xorg-dev depends on libxrender-dev; however:
  Package libxrender-dev is not installed.
 xorg-dev depends on libxres-dev; however:
  Package libxres-dev is not installed.
 xorg-dev depends on libxss-dev; however:
  Package libxss-dev is not installed.
 xorg-dev depends on libxt-dev; however:
  Package libxt-dev is not installed.
 xorg-dev depends on libxtrap-dev; however:
  Package libxtrap-dev is not installed.
 xorg-dev depends on libxtst-dev; however:
  Package libxtst-dev is not installed.
 xorg-dev depends on libxv-dev; however:
  Package libxv-dev is not installed.
 xorg-dev depends on libxvmc-dev; however:
  Package libxvmc-dev is not installed.
 xorg-dev depends on libxxf86dga-dev; however:
  Package libxxf86dga-dev is not installed.
 xorg-dev depends on libxxf86misc-dev; however:
  Package libxxf86misc-dev is not installed.
 xorg-dev depends on libxxf86vm-dev; however:
  Package libxxf86vm-dev is not installed.
 xorg-dev depends on x11proto-bigreqs-dev; however:
  Package x11proto-bigreqs-dev is not installed.
 xorg-dev depends on x11proto-composite-dev; however:
  Package x11proto-composite-dev is not installed.
 xorg-dev depends on x11proto-core-dev; however:
  Package x11proto-core-dev is not installed.
 xorg-dev depends on x11proto-damage-dev; however:
  Package x11proto-damage-dev is not installed.
 xorg-dev depends on x11proto-dmx-dev; however:
  Package x11proto-dmx-dev is not installed.
 xorg-dev depends on x11proto-evie-dev; however:
  Package x11proto-evie-dev is not installed.
 xorg-dev depends on x11proto-fixes-dev; however:
  Package x11proto-fixes-dev is not installed.
 xorg-dev depends on x11proto-fontcache-dev; however:
  Package x11proto-fontcache-dev is not installed.
 xorg-dev depends on x11proto-fonts-dev; however:
  Package x11proto-fonts-dev is not installed.
 xorg-dev depends on x11proto-gl-dev; however:
  Package x11proto-gl-dev is not installed.
 xorg-dev depends on x11proto-input-dev; however:
  Package x11proto-input-dev is not installed.
 xorg-dev depends on x11proto-kb-dev; however:
  Package x11proto-kb-dev is not installed.
 xorg-dev depends on x11proto-randr-dev; however:
  Package x11proto-randr-dev is not installed.
 xorg-dev depends on x11proto-record-dev; however:
  Package x11proto-record-dev is not installed.
 xorg-dev depends on x11proto-render-dev; however:
  Package x11proto-render-dev is not installed.
 xorg-dev depends on x11proto-resource-dev; however:
  Package x11proto-resource-dev is not installed.
 xorg-dev depends on x11proto-scrnsaver-dev; however:
  Package x11proto-scrnsaver-dev is not installed.
 xorg-dev depends on x11proto-trap-dev; however:
  Package x11proto-trap-dev is not installed.
 xorg-dev depends on x11proto-video-dev; however:
  Package x11proto-video-dev is not installed.
 xorg-dev depends on x11proto-xcmisc-dev; however:
  Package x11proto-xcmisc-dev is not installed.
 xorg-dev depends on x11proto-xext-dev; however:
  Package x11proto-xext-dev is not installed.
 xorg-dev depends on x11proto-xf86bigfont-dev; however:
  Package x11proto-xf86bigfont-dev is not installed.
 xorg-dev depends on x11proto-xf86dga-dev; however:
  Package x11proto-xf86dga-dev is not installed.
 xorg-dev depends on x11proto-xf86dri-dev; however:
  Package x11proto-xf86dri-dev is not installed.
 xorg-dev depends on x11proto-xf86misc-dev; however:
  Package x11proto-xf86misc-dev is not installed.
 xorg-dev depends on x11proto-xf86vidmode-dev; however:
  Package x11proto-xf86vidmode-dev is not installed.
 xorg-dev depends on x11proto-xinerama-dev; however:
  Package x11proto-xinerama-dev is not installed.
 xorg-dev depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 xorg-dev depends on xtrans-dev; however:
  Package xtrans-dev is not installed.
dpkg: error processing xorg-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-dev

is there batch command to overcome the issue?

Regards/Robin

---

### Post by stevescripts on 2008-04-17
use synaptic - it will also get all other dependencies

---

### Post by mssever on 2008-04-17
> **stevescripts said:**
> use synaptic - it will also get all other dependencies

Or, if you prefer the CLI, use aptitude: ```
sudo aptitude install xorg-dev
```

---

