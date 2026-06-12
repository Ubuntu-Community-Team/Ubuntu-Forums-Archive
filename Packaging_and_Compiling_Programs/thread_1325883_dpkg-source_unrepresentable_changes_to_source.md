---
title: "dpkg-source: unrepresentable changes to source"
date: 2009-11-13
forum: Packaging and Compiling Programs
---

### Post by ras123 on 2009-11-13
Hi,
I download and try to make .deb file for magic vlsi software ([http://opencircuitdesign.com/magic/archive/magic-7.5.187.tgz](http://opencircuitdesign.com/magic/archive/magic-7.5.187.tgz)), I tried the as in debian manual (appendix A1 [http://www.debian.org/doc/maint-guide/ap-pkg-eg.en.html](http://www.debian.org/doc/maint-guide/ap-pkg-eg.en.html)), I first run dh_make and change copyright, control, and changelog files in debian folder. After that I removed emacs*.ex init.d.ex, README.debian, then run debuild, but I always get the following error
dpkg-source: unrepresentable changes to source
dpkg-source: building magic in magic_7.5.187-0ubuntu.dsc
debuild: fatal error at line 1247:
dpkg-source -b magic-7.5.187 failed

```
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut7a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut11a.nodes
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut3e.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut11c.ext
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut2c.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut11a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut4a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut2b.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut8l.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut7d.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut6c.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut8r.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/Makefile
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut4y.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut3h.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut9y.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut6a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut4x.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut8i.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut7c.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut9a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut6y.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut11b.ext
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut6b.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut8h.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut3d.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/m3a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut2.f1b.cif
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut9b.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut8a.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut2d.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut4z.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/tutcells/tut1.mag
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/doc/psfigures
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tutcell.cif
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut7.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut8.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut7.2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut9.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut8.3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tutcell1.mag
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.6b.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut8.4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.7.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut2.2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.8.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.6.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tutw1.2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.9.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.11.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.3b.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut2.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tutw1.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut8.5.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.5.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut8.2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/maint2.3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfigures/tut7.3.ps
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/doc/psfiles
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut10.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tutscm1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tutscm4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/maint4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/maint2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut8.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tuttcl2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/maint3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/addendum6_5.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tuttcl5.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tutscm3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/introduction.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tutwrl1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut6.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tuttcl4.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tuttcl1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tutscm2.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/maint1.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut7.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut5.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/copyright.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut11.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tuttcl3.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/psfiles/tut9.ps
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/Makefile
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/doc/man
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/dlys.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/displays.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/net.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/magic.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/cmap.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/mag.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/dstyle.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/extcheck.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/Makefile
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/ext2spice.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/ext.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/sim.5
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/ext2sim.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/glyphs.5
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/doc/man/NOTUSED
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/libmalloc.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/ext2dlys.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/sim2spice.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/grsunprog.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/stack.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/prleak.8
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/geometry.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/malloc.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/magicusage.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/heap.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/list.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/set.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/string.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/dqueue.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/path.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/net2ir.1
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/hash.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/mpack.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/extflat.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/show.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/magicutils.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/NOTUSED/runstats.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/doc/man/tmac.anc
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/lisp
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispIO.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispTrace.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/README
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispArith.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispA-Z.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispMagic.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispEval.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispFrame.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispargs.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispPrint.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/Depend
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lisp.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispA-Z.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/Makefile
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispString.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispInt.h
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/lisp/scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/gate.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/help.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/box.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/stack.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/drc.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/label.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/default.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/draw.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/layout.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/sel.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/scm/prs.scm
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispGC.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispParse.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/lisp/lispMain.c
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/README
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline/readline-4.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/keymaps.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/mbutil.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/tilde.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/nls.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/xmalloc.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/terminal.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/CHANGES
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/chardefs.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/README
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/posixjmp.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/complete.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/MANIFEST
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/kill.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/undo.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/ansi_stdlib.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/COPYING
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rltty.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/tcap.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/emacs_keymap.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/search.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/funmap.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/vi_keymap.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/configure.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/Makefile.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/histlib.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/posixstat.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rldefs.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlconf.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlstdc.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/readline.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/bind.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/CHANGELOG
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlshell.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/readline.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/history.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/histexpand.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/keymaps.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/macro.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/INSTALL
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/misc.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlprivate.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/xmalloc.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/callback.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rltypedefs.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/histfile.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/signals.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/histsearch.c
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline/readline-4.3/support
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/shlib-install
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/config.guess
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/install.sh
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/mkdirs
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/shobj-conf
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/mkdist
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/wcwidth.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/support/config.sub
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/aclocal.m4
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/compat.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/parens.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/input.c
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline/readline-4.3/examples
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/rlcat.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/rltest.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/manexamp.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/rlfe.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/Makefile.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/excallback.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/Inputrc
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/rl.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/fileman.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/readlinebuf.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/rlversion.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/examples/histexamp.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/text.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/shell.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/posixdir.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/configure
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/vi_mode.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/display.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/savestring.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rltty.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/tilde.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/config.h.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlmbutil.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/rlwinsize.h
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline/readline-4.3/doc
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/texi2html
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/texinfo.tex
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/hsuser.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/rluserman.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/Makefile.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/hstech.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/history.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/hist.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/rltech.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/texi2dvi
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/readline.3
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/rlman.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/manvers.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/doc/rluser.texinfo
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/USAGE
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/history.h
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/isearch.c
dpkg-source: warning: ignoring deletion of directory magic-7.5.187/readline/readline-4.3/shlib
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/shlib/Makefile.in
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/readline-4.3/util.c
dpkg-source: warning: ignoring deletion of file magic-7.5.187/readline/Makefile
dpkg-source: warning: ignoring deletion of file magic-7.5.187/README.Tcl
dpkg-source: unrepresentable changes to source
dpkg-source: building magic in magic_7.5.187-0ubuntu.dsc
debuild: fatal error at line 1247:
dpkg-source -b magic-7.5.187 failed
```

---

### Post by SevenMachines on 2009-11-15
hi there, offhand i would suggest recreating the source directory from the original tarball, copying your debian directory across and then retrying. 'unrepresentable changes to source' problems can come from a number of areas, if you post your complete source&debian directories i'll have a look and see if anything springs to mind

{EDIT} i'm pretty sure i've seen the exact sequence of 'ignore deletion' things before but i can't for the life of me remember exactly what it was

---

### Post by ras123 on 2009-11-15
Hi,
Please download the complete source from the link below
[http://opencircuitdesign.com/magic/archive/magic-7.5.187.tgz](http://opencircuitdesign.com/magic/archive/magic-7.5.187.tgz)

I renamed the .tgz to .tar.gz, and make a copy magic_7.5.187.orig.tar.gz, then unpacked it and cd to magic-7.5.187 then run dh_make -e mail@domain,
Delete all *.ex *.EX and Readme.debian from debian directory and make changes in copyrign control and changelog files (I used a script to find dependencies in [http://www.debian.org/doc/maint-guide/ch-dreq.en.html](http://www.debian.org/doc/maint-guide/ch-dreq.en.html)), attached files with this. After that I run debuild. Please help

---

### Post by SevenMachines on 2009-11-15
In the archive used by debuild, magic_7.5.187.orig.tar.gz, there is a symlink called 'magic'. remove that and those errors should disappear

---

### Post by ras123 on 2009-11-15
I tried it, now it compiled but the due to the following errors, the installed deb is not working properly
> 
# Add here commands to install the package into debian/magic.
/usr/bin/make prefix=/home/cns/Documents/Magic/deb/magic-7.5.187/debian/magic/usr install
make[1]: Entering directory `/home/cns/Documents/Magic/deb/magic-7.5.187'
--- installing executable to /home/cns/Documents/Magic/deb/magic-7.5.187/debian/magic/usr/bin
--- installing runtime files to /home/cns/Documents/Magic/deb/magic-7.5.187/debian/magic/usr/lib
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
make[1]: Leaving directory `/home/cns/Documents/Magic/deb/magic-7.5.187'
while running it shows 
> 
Magic 7.5 revision 187 - Compiled on Sun Nov 15 19:13:14 IST 2009.
Using Tk console window
Using TrueColor, VisualID 0x21 depth 24
Section "tech" was missing from /usr/lib/magic/sys/scmos.tech.
Section "planes" was missing from /usr/lib/magic/sys/scmos.tech.
Section "types" was missing from /usr/lib/magic/sys/scmos.tech.
Section "styles" was missing from /usr/lib/magic/sys/scmos.tech.
Section "contact" was missing from /usr/lib/magic/sys/scmos.tech.
Section "compose" was missing from /usr/lib/magic/sys/scmos.tech.
Section "connect" was missing from /usr/lib/magic/sys/scmos.tech.
Section "cifoutput" was missing from /usr/lib/magic/sys/scmos.tech.
Section "cifinput" was missing from /usr/lib/magic/sys/scmos.tech.
Section "drc" was missing from /usr/lib/magic/sys/scmos.tech.
Section "extract" was missing from /usr/lib/magic/sys/scmos.tech.
Section "tech" was missing from /usr/lib/magic/sys/scmos.tech.
Section "planes" was missing from /usr/lib/magic/sys/scmos.tech.
Section "types" was missing from /usr/lib/magic/sys/scmos.tech.
Section "styles" was missing from /usr/lib/magic/sys/scmos.tech.
Section "contact" was missing from /usr/lib/magic/sys/scmos.tech.
Section "compose" was missing from /usr/lib/magic/sys/scmos.tech.
Section "connect" was missing from /usr/lib/magic/sys/scmos.tech.
Section "cifoutput" was missing from /usr/lib/magic/sys/scmos.tech.
Section "cifinput" was missing from /usr/lib/magic/sys/scmos.tech.
Section "drc" was missing from /usr/lib/magic/sys/scmos.tech.
Section "extract" was missing from /usr/lib/magic/sys/scmos.tech.


---

### Post by SevenMachines on 2009-11-15
can you attach the full tarball of your debian directory, the last attachment was missing, at least, the all important rules file

---

### Post by ras123 on 2009-11-15
Hi,
I attached 'debian', 'script',  directories and some rules file in main directory (i.e. magic-7.5.187), this is for our college students all need the .deb binary.
(Since it has a size of 1.5MB I uploaded to rapidshare, please download
[http://rapidshare.com/files/307405848/magic-7.5.187.tar.bz2.html](http://rapidshare.com/files/307405848/magic-7.5.187.tar.bz2.html) )

---

### Post by SevenMachines on 2009-11-15
you just need to attach the debian directory (after a debclean), i already have the magic source. it could be a while before rapidshare lets me download, no empty slots

---

### Post by ras123 on 2009-11-15
Hi,
I attached debian directory after running debclean
[ATTACH]136324[/ATTACH]
Thanking You,
Ras

---

### Post by SevenMachines on 2009-11-15
seems scmos/scmos.tech.in has issues with later gcc. calling the preprocessor in scmos/Makefile explicitly seems to solve the issues you had above with sections missing from scmos.tech (because the build was generating an empty file) 
```
--- magic-7.5.187/scmos/Makefile        2006-04-10 23:03:13.000000000 +0100
+++ magic-7.5.187.new/scmos/Makefile    2009-11-15 17:15:58.715868000 +0000
@@ -60,7 +60,7 @@
                ${CP} $$i $(DESTDIR)${SYSDIR}; done

 scmos.tech: $(OBJS)
-       $(SC_CPP) -DV5 -DSTANDARD scmos.tech.in > scmos.tech
+       cpp -traditional -P -DV5 -DSTANDARD scmos.tech.in > scmos.tech

 scmos-tm.tech: $(OBJS)
        $(SC_CPP) -DV5 -DHPTECH -DTIGHTMETAL scmos.tech.in > scmos-tm.tech
```I also get problems with -O2 options in debian/rules, and also need to call make install on the tech files as well. 
```
--- magic-7.5.187/debian/debian/rules        2009-11-15 13:40:36.000000000 +0000
+++ magic-7.5.187.new/debian/rules  2009-11-15 17:46:36.257118740 +0000
@@ -15,6 +15,7 @@
 DEB_HOST_GNU_TYPE   ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
 DEB_BUILD_GNU_TYPE  ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)

+CFLAGS="-g"

 config.status: configure
        dh_testdir
@@ -58,6 +59,7 @@

        # Add here commands to install the package into debian/magic.
        $(MAKE) prefix=$(CURDIR)/debian/magic/usr install
+       cd scmos && $(MAKE) prefix=$(CURDIR)/debian/magic/usr install


 # Build architecture-independent files here.
~                                              
```you might want to take a look at your build dependencies and binary dependencies in debian control, do you need libc6-i686? this blocks installation on amd64, you might want to add gl dev package to the build-deps too.

if you use the attached debian/rules and scmos/Makefile it should now work for you. it builds a properly working package here but i'm guessing the magic source itself needs some updating upstream

---

### Post by ras123 on 2009-11-15
Hi,
Thanks for your help, but still problems, the warnings are still there
```

make[1]: Entering directory `/home/cns/Documents/Magic/deb/magic-7.5.187/scmos'
i486-linux-gnu-gcc -E -I./extract_template -DV5 -DHPTECH -DTIGHTMETAL scmos.tech.in > scmos-tm.tech
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc -E -I./extract_template -DV5 -DSUBMICRON scmos.tech.in > scmos-sub.tech
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc -E -I./extract_template -DV5 -DSTANDARD -DWELL_ROUTE_CHECK scmos.tech.in > scmosWR.tech
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
for i in mos.7bit.dstyle mos.7bit.std.cmap mos.24bit.dstyle mos.24bit.std.cmap mos.7bit.mraster_dstyle mos.7bit.mraster.cmap mos.OpenGL.dstyle mos.OpenGL.std.cmap minimum.tech gdsquery.tech scmos.tech scmos-tm.tech scmos-sub.tech scmosWR.tech; do \
        cp $i /home/cns/Documents/Magic/deb/magic-7.5.187/debian/magic/usr/lib/magic/sys; done
make[1]: Leaving directory `/home/cns/Documents/Magic/deb/magic-7.5.187/scmos'
dh_testdir
dh_testroot
dh_installchangelogs 
parsechangelog/debian: warning:     debian/changelog(l3): badly formatted heading line
LINE: * ubuntu linux i386 package for HardyHeron.
parsechangelog/debian: warning:     debian/changelog(l5): found trailer where expected start of change data
LINE:  -- CNS <mail@domain.com>  Thu, 12 Nov 2009 20:04:14 +0530
dh_installdocs
dh_installexamples
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: debian/magic/usr/lib/magic/tcl/magicdnull shouldn't be linked with libtk8.4.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: symbol Tk_UnmapWindow used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_ConfigureInfo used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_NameOfImage used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_GetUid used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_ImageChanged used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_SetVar used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Panic used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewDoubleObj used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_AppendResult used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_FreeGC used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: 75 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: symbol ExtGetDevInfo used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol ExtCompareStyle used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashStartSearch used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol windCheckOnlyWindow used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Match used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Lookup used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_GetVar2 used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewIntObj used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Alloc used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashLookOnly used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: 39 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: symbol ExtGetDevInfo used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol ExtCompareStyle used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashStartSearch used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol windCheckOnlyWindow used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Match used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Lookup used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_GetVar2 used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewIntObj used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Alloc used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashLookOnly used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: 36 other similar warnings have been skipped (use -v to see them all).
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l3): badly formatted heading line
LINE: * ubuntu linux i386 package for HardyHeron.
parsechangelog/debian: warning:     debian/changelog(l5): found trailer where expected start of change data
LINE:  -- CNS <mail@domain.com>  Thu, 12 Nov 2009 20:04:14 +0530
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `magic' in `../magic_7.5.187-0ubuntu_i386.deb'.
 dpkg-genchanges
parsechangelog/debian: warning:     debian/changelog(l3): badly formatted heading line
LINE: * ubuntu linux i386 package for HardyHeron.
parsechangelog/debian: warning:     debian/changelog(l5): found trailer where expected start of change data


```(I repacked after changing rules in scmos directory) Without linking there libraries it may not work. Here is an old version of magic .deb file
[http://ppa.launchpad.net/aanjhan/ubuntu/pool/main/m/magic/](http://ppa.launchpad.net/aanjhan/ubuntu/pool/main/m/magic/)
Thanking You,
Ras

---

### Post by SevenMachines on 2009-11-16
hmmm, not getting these, maybe its a 386 thing. i'll look a little later, i'll be on a machine better set up to look at this

---

### Post by SevenMachines on 2009-11-16
hi, looking at the ppa i can see theres a few key dpatch patches included that solve a number of problems. i've updated that version instead if thats ok? 
[EDIT] i'll upload it to my ppa for you to have a look sometime today

---

### Post by SevenMachines on 2009-11-16
i've put it [here]("https://launchpad.net/%7Esevenmachines/+archive/testing/+packages"). if you want to grab the files, have a look at them, and add it to your ppa and let me know when its all built, my ppa above is prone to get deleted. Theres still a few unresolved symbols in tcl but i'm not sure what to do with them. on the bright side, version 8 of magic will also build happily with that package if you need to upgrade it again. both appear to work fine on a brief use

---

### Post by SevenMachines on 2009-11-16
looking at tcl, i'm thinking the unresolvable references (in tcl to Tk_ConfigureValue and Tcl_NewDoubleObj) warnings on dh_shlibs are ok, these are covered by an externs in /usr/include/tcl/tkDecls.h

---

### Post by ras123 on 2009-11-16
I tried to compile your uploaded source, but the same problem
```

# Add here commands to install the package into debian/magic.
/usr/bin/make prefix=/home/cns/Documents/Magic/new/magic-7.5.187/debian/magic/usr install
make[1]: Entering directory `/home/cns/Documents/Magic/new/magic-7.5.187'
--- installing executable to /home/cns/Documents/Magic/new/magic-7.5.187/debian/magic/usr/bin
--- installing runtime files to /home/cns/Documents/Magic/new/magic-7.5.187/debian/magic/usr/lib
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done
i486-linux-gnu-gcc: scmos.tech.in: linker input file unused because linking not done

```

I am using ubuntu 8.04, is it make any difference?
Regards
Ras

---

### Post by SevenMachines on 2009-11-17
i've only built it on jaunty (10.04), karmic(10.10) and lucid. i'll have a look at 8.04 later

are all the patches applying when you run debuild? in particular

applying patch 03_fix_scmos_makefile to ./ ... ok.

thats the one that deals with the linking scmos.tech.in problem

---

### Post by ras123 on 2009-11-17
Hi,
I confused by "all patches". You only give me two patches one debian/rules other is scmos/Makefile. The last time I tried with the source downloaded from your ppa [https://launchpad.net/~sevenmachines/+archive/testing/+files/magic_7.5.187.orig.tar.gz](https://launchpad.net/~sevenmachines/+archive/testing/+files/magic_7.5.187.orig.tar.gz) with out any change,
Thanks a lot,
Niras

---

### Post by SevenMachines on 2009-11-17
ah, i might not have explained that properly, dont use any of the previous attachments on this thread, the updated package should deal with it all. 

1. got to [https://launchpad.net/~sevenmachines/+archive/testing/+packages]("https://launchpad.net/%7Esevenmachines/+archive/testing/+packages") and click on view package details

2. download the three necessary debian packing files, the source alone wont included any of the patches
[https://launchpad.net/~sevenmachines/+archive/testing/+files/magic_7.5.187-0ubuntu0~sevenmachines6.diff.gz]("https://launchpad.net/%7Esevenmachines/+archive/testing/+files/magic_7.5.187-0ubuntu0%7Esevenmachines6.diff.gz")
[https://launchpad.net/~sevenmachines/+archive/testing/+files/magic_7.5.187-0ubuntu0~sevenmachines6.dsc]("https://launchpad.net/%7Esevenmachines/+archive/testing/+files/magic_7.5.187-0ubuntu0%7Esevenmachines6.dsc")
[https://launchpad.net/~sevenmachines/+archive/testing/+files/magic_7.5.187.orig.tar.gz]("https://launchpad.net/%7Esevenmachines/+archive/testing/+files/magic_7.5.187.orig.tar.gz")

3. extract the source using dpkg-source which will also automatically apply  the debian packaging 
$ dpkg-source -x magic_7.5.187-0ubuntu0~sevenmachines6.dsc

4. now go into the source directory and debuild it
$ cd magic-7.5.187
$ debuild -b -us -uc

this should leave you with working magic packages

---

### Post by ras123 on 2009-11-17
Hi,
Sorry to say that still warnings, but some warnings are gone
```

dpkg-shlibdeps: warning: debian/magic/usr/lib/magic/tcl/magicdnull shouldn't be linked with libtk8.4.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by nvidia-glx-legacy from: /usr/lib/libGL.so.1
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by nvidia-glx-legacy to: /usr/lib/nvidia/libGL.so.1.xlibmesa
dpkg-shlibdeps: warning: symbol Tk_GetUid used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_ImageChanged used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_SetVar used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Panic used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewDoubleObj used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_AppendResult used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_GetString used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_FreeFont used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_CreateObjCommand used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tk_DeleteImage used by debian/magic/usr/lib/magic/tcl/tclmagic.so found in none of the libraries.
dpkg-shlibdeps: warning: 75 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/magic/usr/lib/magic/tcl/tclmagic.so shouldn't be linked with libXmu.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/magic/usr/lib/magic/tcl/tclmagic.so shouldn't be linked with libXext.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/magic/usr/lib/magic/tcl/tclmagic.so shouldn't be linked with libstdc++.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: symbol ExtGetDevInfo used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol ExtCompareStyle used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashStartSearch used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol windCheckOnlyWindow used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Match used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Lookup used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_GetVar2 used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewIntObj used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Alloc used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashLookOnly used by debian/magic/usr/lib/magic/tcl/exttospice.so found in none of the libraries.
dpkg-shlibdeps: warning: 39 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: symbol ExtGetDevInfo used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol ExtCompareStyle used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashStartSearch used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol windCheckOnlyWindow used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Match used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Lookup used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_GetVar2 used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_NewIntObj used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Tcl_Alloc used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol HashLookOnly used by debian/magic/usr/lib/magic/tcl/exttosim.so found in none of the libraries.
dpkg-shlibdeps: warning: 36 other similar warnings have been skipped (use -v to see them all).
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}

```

Is it normal?
This time I installed following packages to meet dependencies (tcsh libglu1-mesa-dev dpatch), are these for compiling process? 
Thanking You,
Ras

---

### Post by SevenMachines on 2009-11-17
tcsh is a shell needed by magic to build
libglu1-mesa-dev enables opengl support 
dpatch is to allow the dpatch system (debian/patches) to work in debian packaging

dh_shlibs warnings (i get these in pre-karmic builds but not in karmic onwards) could be harmless. unfortunately i dont have 8.04 to have a closer look. 
Does something like /var/lib/dpkg/info/tcl8.4.shlibs exist in your installation? and if so, what does it say?

---

### Post by SevenMachines on 2009-11-17
do you get any missing symbol errors/crashes when actually running magic? or does it actually run fine

---

### Post by SevenMachines on 2009-11-17
actually, running a quick build against both tcl8.4/8.5 across dists from hardy->lucid i'm pretty confident this is a dpkg-shlibdep thing and not a build problem. I'd suggest these warnings can be safely ignored. If you have any 'missing symbol' problems actually running magic then i'd look again but i'm fairly confident you wont

---

### Post by ras123 on 2009-11-18
Hi,
Thanks a lot, till now I haven't any problem with magic. Can you tell me which are the files you modified in original source?. 
The file /var/lib/dpkg/info/tcl8.4.shlibs says libtcl8.4 0 tcl8.4 (>= 8.4.5)
Do I need to upgrade to tcl8.5?
Regards
Ras

---

### Post by SevenMachines on 2009-11-19
hi 8.5 gives the same warnings on the releases up to karmic. i think its down to dpkg-shlibdeps not finding symbols ( it does miss things in some cases ) rather than the symbols not being there. as i say, it should be fine. 
all the changes are in the directory debian/patches if you would like to look them over

---

### Post by ras123 on 2009-11-19
Hi,
Sorry to say that I couldn't understand anything. Are all these files used while compiling? But I found some wrong versions number (directory paths) in these. Eg.
```

@DPATCH@
diff -urNad magic-7.5.129~/ext2spice/spice2sim magic-7.5.129/ext2spice/spice2sim
--- magic-7.5.129~/ext2spice/spice2sim    2006-04-11 03:33:14.000000000 +0530
+++ magic-7.5.129/ext2spice/spice2sim    2008-04-13 22:23:48.000000000 +0530

```file: debian/patches/01_fix_interpreter_path.dpatch
We are using magic-7.5.187 not magic-7.5.129

So please tell me what to do with a fresh compiling of magic? Do I need to just include the patches directory in debian?

Regards
Ras

---

### Post by SevenMachines on 2009-11-19
the patches in that directory are used by the dpatch system, you'll see this is included in the rules file (dpatch.mk) 
when you debuild the package these are then applied before building, equivalent to running patch -p1 < debian/patches/10_some_patch_name. doing things this way means that you dont need to touch the original source code, which is generally a good idea. 
the  version numbers included in the directory names in the patch files are irrelevant, dpatch ignores the first directory in the filename. patches can be used across different versions (sometimes with some modification), if the bug they fix still exists
if you created your own packaging, you would want to copy the patches across to your own debian directory ( whichever patches you wanted to use and worked ). and include dpatch.mk in your debian/rules file as you can see in this package
these patch files are 'diffs' of the changes someone wants to make to the original code. say you had copies of the source code in two identical directories. mysource-0.1.orig and mysource-0.1.new, you could then make the bug fixing changes in the .new directory then run 
diff -ruN mysource-0.1.orig mysource-0.1.new>my_bugfix.patch
you could then use this as a patch in your debian packaging. patch systems often come with a handy tool to effectively do this for you. eg, in source directory
$dpatch-edit-patch my_bugfix.patch
this then gives you an environment a temporary copy of the source, then automatically have a patch generated for you when you exit that copy

---

### Post by ras123 on 2009-11-19
Hi,
So I think, no need to include dpatch in the debian/control file Build-Depends list, because it only need in the time of building, to install magic binary it doesn't required.
In the rules file I found "include /usr/share/dpatch/dpatch.make" , I think this is you mean by dpatch.mk.
Thanks for all helps,
Regards
Ras

---

### Post by SevenMachines on 2009-11-20
dpatch is required to build packages that use it, so it is included in Build-Depends: in debian/control. However its not needed to run the binary so it doesn;t need to be in the Depends: field of the binary

yes, 'dpatch.make', thats what i meant :)

---

### Post by ras123 on 2009-11-20
Hi,
Still warnings!!, I unpacked fresh magic*.tar.gz and removed the magic sym link, then repacked to magic*.tar.gz, After that cd to magic-7.5* directory and issue dh_makd -e <email@domain> -f ../magic-7.5.187.tar.gz , it created a debian file, removed *.EX, and *.ex added pach directories and include dpatch.make in rules file, then issue debuild
```

dh_clean 
 dpkg-source -b magic-7.5.187
Use of uninitialized value in pattern match (m//) at /usr/bin/dpkg-source line 429.
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: building magic using existing magic_7.5.187.orig.tar.gz
dpkg-source: building magic in magic_7.5.187-0ubuntu.diff.gz
dpkg-source: warning: executable mode 0755 of 'debian/patches/03_fix_scmos_makefile.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/04_remove_spice2sim.dpatch' will not be represented in diff
dpkg-source: warning: newly created empty file 'debian/patches/01_fix_interpreter_path.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/40_configure_fix.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/02_fix_manpages.dpatch' will not be represented in diff
dpkg-source: warning: ignoring deletion of file oa/.deps/magicInit.P
dpkg-source: warning: ignoring deletion of file oa/.deps/magicOA.P
dpkg-source: building magic in magic_7.5.187-0ubuntu.dsc

```

Any steps I missed?

---

### Post by SevenMachines on 2009-11-20
remember, warnings arent necessarily bad  things :) They're there to point out things that we might have overlooked, but might have done on purpose, or arent concerned about for some reason or other

```
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
```these are warnings relating to policy on ubuntu packages, the changelog version says its a ubuntu package so should have a ubuntu maintainer, if it has a ubuntu maintainer it needs an original maintainer contact.

```
dpkg-source: warning: executable mode 0755 of 'debian/patches/03_fix_scmos_makefile.dpatch' will not be represented in diff
```all these mean is the file mode of your patches wont be noted, this is ok, we dont need them to be

```
dpkg-source: warning: ignoring deletion of file oa/.deps/magicInit.P
```Things like this often mean that these files are in the original tarball we downloaded and maybe shouldnt be, not a problem though, unless we really needed them deleted and we dont

the only one that would worry me is ```
dpkg-source: warning: newly created empty file 'debian/patches/01_fix_interpreter_path.dpatch' will not be represented in diff
```this shouldnt be an empty file, i'd check that and copy the proper patch again if its wrong

Remember though, its not often a package builds without some warnings, more often than not theres few we need to be concerned about. trying to fix them all is likely the road to madness :)

---

### Post by ras123 on 2009-11-20
Hi,
I had make a little changes to rules.mak in magic-7.5.187 directory, changed the following lines
```

database/database.h: database/database.h.in
    @echo --- making header file database/database.h
    ${SCRIPTS}/makedbh database/database.h.in database/database.h

```

Originally it was ../database etc., Is it make any difference?, but now worked!
(I again packed the directories with that changes) I upload the magic*.build for your reference [ATTACH]136917[/ATTACH]  (Still the warning are there)

---

### Post by ras123 on 2009-11-20
Hi,
Sorry the error is not with that data path, I can't compile with original debian/rules with adding include dpatch.make, I found there are lot of other changes!
Regards
Ras

---

