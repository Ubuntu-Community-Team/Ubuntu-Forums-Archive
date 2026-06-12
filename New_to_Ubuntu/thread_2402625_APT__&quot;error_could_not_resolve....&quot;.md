---
title: "APT  &quot;error could not resolve....&quot;"
date: 2018-10-02
forum: New to Ubuntu
---

### Post by androidzip on 2018-10-02
```
ali@ubuntu:~$ sudo apt-get install git-core gnupg flex bison gperf libsdl-dev
[sudo] password for ali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'git' instead of 'git-core'
Note, selecting 'libsdl1.2-dev' instead of 'libsdl-dev'
gnupg is already the newest version (2.2.4-1ubuntu1.1).
The following additional packages will be installed:
  git-man libasound2-dev libbison-dev libcaca-dev liberror-perl libfl-dev
  libfl2 libglib2.0-dev libglib2.0-dev-bin libpcre16-3 libpcre3-dev
  libpcre32-3 libpcrecpp0v5 libpng-dev libpng-tools libpulse-dev
  libsdl1.2debian libsigsegv2 libslang2-dev m4 pkg-config python3-distutils
  python3-lib2to3
Suggested packages:
  bison-doc flex-doc git-daemon-run | git-daemon-sysvinit git-doc git-el
  git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn libasound2-doc
  libglib2.0-doc m4-doc
The following NEW packages will be installed:
  bison flex git git-man gperf libasound2-dev libbison-dev libcaca-dev
  liberror-perl libfl-dev libfl2 libglib2.0-dev libglib2.0-dev-bin libpcre16-3
  libpcre3-dev libpcre32-3 libpcrecpp0v5 libpng-dev libpng-tools libpulse-dev
  libsdl1.2-dev libsdl1.2debian libsigsegv2 libslang2-dev m4 pkg-config
  python3-distutils python3-lib2to3
0 upgraded, 28 newly installed, 0 to remove and 129 not upgraded.
Need to get 11.0 MB of archives.
After this operation, 63.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libsigsegv2 amd64 2.12-1
  Could not resolve 'us.archive.ubuntu.com'
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 m4 amd64 1.4.18-1
  Could not resolve 'us.archive.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 flex amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libbison-dev amd64 2:3.0.4.dfsg-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 bison amd64 2:3.0.4.dfsg-1build1
  Could not resolve 'us.archive.ubuntu.com'
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 liberror-perl all 0.17025-1
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 git amd64 1:2.17.1-1ubuntu0.1
Err:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 gperf amd64 3.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libasound2-dev amd64 1.1.3-5ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libpng-dev amd64 1.6.34-1ubuntu0.18.04.1
Err:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libslang2-dev amd64 2.3.1a-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libcaca-dev amd64 0.99.beta19-2build2~gcc5.3
  Could not resolve 'us.archive.ubuntu.com'
Err:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libfl2 amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Err:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libfl-dev amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 python3-lib2to3 all 3.6.5-3
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 python3-distutils all 3.6.5-3
Ign:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libglib2.0-dev-bin amd64 2.56.2-0ubuntu0.18.04.2
Err:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libpcre16-3 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libpcre32-3 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libpcrecpp0v5 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libpcre3-dev amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 pkg-config amd64 0.29.1-0ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Ign:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libglib2.0-dev amd64 2.56.2-0ubuntu0.18.04.2
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libpng-tools amd64 1.6.34-1ubuntu0.18.04.1
Err:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libpulse-dev amd64 1:11.1-1ubuntu7.1
  Could not resolve 'us.archive.ubuntu.com'
Err:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libsdl1.2debian amd64 1.2.15+dfsg2-0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libsdl1.2-dev amd64 1.2.15+dfsg2-0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 liberror-perl all 0.17025-1
  Could not resolve 'us.archive.ubuntu.com'
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Err:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 python3-lib2to3 all 3.6.5-3
  Could not resolve 'us.archive.ubuntu.com'
Err:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 python3-distutils all 3.6.5-3
  Could not resolve 'us.archive.ubuntu.com'
Err:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 git amd64 1:2.17.1-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 libpng-dev amd64 1.6.34-1ubuntu0.18.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 libglib2.0-dev-bin amd64 2.56.2-0ubuntu0.18.04.2
  Could not resolve 'us.archive.ubuntu.com'
Err:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 libglib2.0-dev amd64 2.56.2-0ubuntu0.18.04.2
  Could not resolve 'us.archive.ubuntu.com'
Err:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 libpng-tools amd64 1.6.34-1ubuntu0.18.04.1
  Could not resolve 'us.archive.ubuntu.com'
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Err:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.12-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.12-1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.18-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.18-1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/flex_2.6.4-6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/flex_2.6.4-6_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bison/libbison-dev_3.0.4.dfsg-1build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bison/libbison-dev_3.0.4.dfsg-1build1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bison/bison_3.0.4.dfsg-1build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bison/bison_3.0.4.dfsg-1build1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17025-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17025-1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/git/git-man_2.17.1-1ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/git/git-man_2.17.1-1ubuntu0.1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/git/git_2.17.1-1ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/git/git_2.17.1-1ubuntu0.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gperf/gperf_3.1-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gperf/gperf_3.1-1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2-dev_1.1.3-5ubuntu0.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2-dev_1.1.3-5ubuntu0.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng1.6/libpng-dev_1.6.34-1ubuntu0.18.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng1.6/libpng-dev_1.6.34-1ubuntu0.18.04.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang2/libslang2-dev_2.3.1a-3ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang2/libslang2-dev_2.3.1a-3ubuntu1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcaca/libcaca-dev_0.99.beta19-2build2~gcc5.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcaca/libcaca-dev_0.99.beta19-2build2~gcc5.3_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/libfl2_2.6.4-6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/libfl2_2.6.4-6_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/libfl-dev_2.6.4-6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/flex/libfl-dev_2.6.4-6_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python3-stdlib-extensions/python3-lib2to3_3.6.5-3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python3-stdlib-extensions/python3-lib2to3_3.6.5-3_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python3-stdlib-extensions/python3-distutils_3.6.5-3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python3-stdlib-extensions/python3-distutils_3.6.5-3_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev-bin_2.56.2-0ubuntu0.18.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev-bin_2.56.2-0ubuntu0.18.04.2_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre16-3_8.39-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre16-3_8.39-9_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre32-3_8.39-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre32-3_8.39-9_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0v5_8.39-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0v5_8.39-9_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3-dev_8.39-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3-dev_8.39-9_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.29.1-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.29.1-0ubuntu2_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev_2.56.2-0ubuntu0.18.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev_2.56.2-0ubuntu0.18.04.2_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng1.6/libpng-tools_1.6.34-1ubuntu0.18.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng1.6/libpng-tools_1.6.34-1ubuntu0.18.04.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-dev_11.1-1ubuntu7.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-dev_11.1-1ubuntu7.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15+dfsg2-0.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15+dfsg2-0.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.15+dfsg2-0.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.15+dfsg2-0.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by guiverc on 2018-10-02
I can see no issues (my machine can access them from links), so I'd check your network, `sudo apt-get update` then try again.  If it fails, I'd suspect you have network issues (proxy) that you'll need to work around *(searching here I can find fixes; or wait for someone with experience with proxy)*

---

