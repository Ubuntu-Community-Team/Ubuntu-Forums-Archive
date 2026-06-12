---
title: "Question about '.la' file on ubuntu"
date: 2007-05-23
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-23
Hi,

Is '.la' file the library files on ubuntu?  I thought *.so files are the library files on linux. 


But why I get this when I 'make'?

make[4]: `libaccess_file_plugin.la' is up to date.
make[4]: `libaccess_directory_plugin.la' is up to date.
make[4]: `libaccess_udp_plugin.la' is up to date.
make[4]: `libaccess_tcp_plugin.la' is up to date.
make[4]: `libaccess_http_plugin.la' is up to date.
make[4]: `libaccess_ftp_plugin.la' is up to date.
make[4]: `libaccess_smb_plugin.la' is up to date.
make[4]: `libdvdnav_plugin.la' is up to date.
make[4]: `libdvdread_plugin.la' is up to date.
make[4]: `libaccess_fake_plugin.la' is up to date.
make[4]: `libcdda_plugin.la' is up to date.

---

### Post by Tomosaur on 2007-05-23
Actually, .la files are just plain text files. They're used to link to libraries.

---

### Post by yinglcs2 on 2007-05-23
Thanks. Can you pleaes tell me how to link to those .la files from my program?

---

