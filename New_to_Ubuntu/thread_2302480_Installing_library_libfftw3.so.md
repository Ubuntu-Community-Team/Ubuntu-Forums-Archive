---
title: "Installing library libfftw3.so"
date: 2015-11-10
forum: New to Ubuntu
---

### Post by felix36 on 2015-11-10
Hi,

would like to use a software that requires fftw, specifically it requires a file libfftw3.so (exactly like that, not libfftw.so or libfftw3.so.3 or something like that). However, I could not find any package that would install this file. Pre-installed with ubuntu 15.10 were some files in /usr/lib/, for instance libfftw.so. Since that is the wrong name for me, I removed all fftw packages (apt-get remove fftw.*) and installed fftw3. Now I have the following files installed:

/usr/lib/x86_64-linux-gnu/libfftw3f_omp.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3f_omp.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3f.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3f.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3f_threads.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3f_threads.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3l_omp.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3l_omp.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3l.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3l.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3l_threads.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3l_threads.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3_omp.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3_omp.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3.so.3.4.4
/usr/lib/x86_64-linux-gnu/libfftw3_threads.so.3@
/usr/lib/x86_64-linux-gnu/libfftw3_threads.so.3.4.4

That does not look to bad, I believe it will also work having these libraries in the /usr/lib/x86_64-linux-gnu/ folder, but I am missing the softlink to the files just ending at .so. Of course, I could add them manually, but then these links would not belong to any package and probably create a mess when I update the system next time.

Any suggestions how to get the files I need?

---

### Post by sandyd on 2015-11-10
Few things:

Adding them manually would be fine, they will not create a mess as long as the package does not change.

That being said, libfftw3-double3 has been [here since trusty]("http://packages.ubuntu.com/trusty/amd64/libfftw3-double3/filelist") (can't say before that since the search doesn't show EOL'ed releases and it isn't in precise), and that hasn't changed so far.

As well, not much need to remove libfftw.so, the package naming was designed so that both libfftw2 and libfftw3 can exist peacefully

---

### Post by felix36 on 2015-11-11
Okay, thanks. Manual symbolic linking solved my problem.

---

