---
title: "python 2.7 error"
date: 2010-07-05
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-07-05
What does this mean


34 tests skipped:
    test_aepack test_al test_applesingle test_bsddb test_bsddb185
    test_bsddb3 test_cd test_cl test_codecmaps_cn test_codecmaps_hk
    test_codecmaps_jp test_codecmaps_kr test_codecmaps_tw test_curses
    test_gl test_imgfile test_kqueue test_linuxaudiodev test_macos
    test_macostools test_ossaudiodev test_scriptpackages test_smtpnet
    test_socketserver test_startfile test_sunaudiodev test_timeout
    test_tk test_ttk_guionly test_urllib2net test_urllibnet
    test_winreg test_winsound test_zipfile64
3 skips unexpected on linux2:
    test_bsddb test_bsddb3 test_ttk_guionly
make: *** [test] Error 1

I did a make test to make sure thing are working does it look like it and i am compile 2.7.I had no prob on my laptop so i want to know it look ok:)

---

### Post by pythonsyntax on 2010-07-05
anyone?

---

### Post by SevenMachines on 2010-07-06
did you get something like 
Python build finished, but the necessary bits to build these modules were not found:
<some module names in here including bsddb3>

when you ran make?

I'm guessing you need libdb-dev and tk-dev for the probably missing modules for the tests you had, then rebuild before running make test.

---

### Post by pythonsyntax on 2010-07-06
i see the prob now

---

