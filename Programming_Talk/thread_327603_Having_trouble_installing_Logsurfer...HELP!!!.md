---
title: "Having trouble installing Logsurfer...HELP!?!?!"
date: 2006-12-29
forum: Programming Talk
---

### Post by DieslWeasl on 2006-12-29
I can't figure this out:

I untarred the LogSurfer package and tried an install but I got an error message. For any gurus out there I'll just go ahead and post most of what I did in terminal:

root@silver:~/Desktop/logsurfer+-1.7# make install
for subdir in man src; do \
echo making install in $subdir ; \
(cd $subdir; make prefix='/usr/local' bindir='/usr/local/bin' mandir='/usr/local/man' CPPFLAGS='-DWARN_ROOT' CC='gcc' CFLAGS='-g -O' LDFLAGS='' DEF_DUMPFILE='/dev/null' DEF_CONFFILE='/usr/local/etc/logsurfer.conf' LIBS='' INSTALL='/usr/bin/install -c' INSTALL_PROGRAM='/usr/bin/install -c' INSTALL_DATA='/usr/bin/install -c -m 644' DEFS='-DHAVE_CONFIG_H' install); \
done
making install in man
make[1]: Entering directory `/home/sean/Desktop/logsurfer+-1.7/man'
/usr/bin/install -c -m 644 logsurfer.1 /usr/local/man/man1/logsurfer.1
/usr/bin/install: cannot create regular file `/usr/local/man/man1/logsurfer.1': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/sean/Desktop/logsurfer+-1.7/man'
making install in src
make[1]: Entering directory `/home/sean/Desktop/logsurfer+-1.7/src'
/usr/bin/install -c logsurfer /usr/local/bin/logsurfer
make[1]: Leaving directory `/home/sean/Desktop/logsurfer+-1.7/src'

What I show above is after I had sudo'ed "/.configure and make" just so ya know.
So that's the long and the short of it.... any ideas???

---

