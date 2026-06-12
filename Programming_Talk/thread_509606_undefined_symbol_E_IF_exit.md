---
title: "undefined symbol: E_IF_exit"
date: 2007-07-25
forum: Programming Talk
---

### Post by yinglcs2 on 2007-07-25
I am running my problem but I get this error:

main libvlc warning: [33;1mcannot load module `/home/yinglcs/vlc-bin/lib/vlc/codec/libffmpeg_plugin.so' (/home/yinglcs/vlc-bin/lib/vlc/codec/libffmpeg_plugin.so: undefined symbol: E_IF_exit)

I have this library  libamrwb.so  which defines E_IF_exit

$ nm libamrwb.so | grep -r  E_IF_exit
00011890 T E_IF_exit


And that library is located in my LD_LIBRARY_PATH.    My question is why linux can't find it when I load my program?

[CODE]
   1.
      # echo $LD_LIBRARY_PATH
   2.
      :/home/yinglcs/vlc-bin/lib:/usr/local/lib
   3.
      # ls -la /usr/local/lib/*amr*-rw-r--r-- 1 root root 480942 2007-07-25 13:37 /usr/local/lib/libamrnb.a
   4.
      -rwxr-xr-x 1 root root    803 2007-07-25 13:37 /usr/local/lib/libamrnb.la
   5.
      lrwxrwxrwx 1 root root     17 2007-07-25 13:37 /usr/local/lib/libamrnb.so -> libamrnb.so.2.0.0
   6.
      lrwxrwxrwx 1 root root     17 2007-07-25 13:37 /usr/local/lib/libamrnb.so.2 -> libamrnb.so.2.0.0
   7.
      -rwxr-xr-x 1 root root 438036 2007-07-25 13:37 /usr/local/lib/libamrnb.so.2.0.0
   8.
      -rw-r--r-- 1 root root 389114 2007-07-25 14:35 /usr/local/lib/libamrwb.a
   9.
      -rwxr-xr-x 1 root root    803 2007-07-25 14:35 /usr/local/lib/libamrwb.la
  10.
      lrwxrwxrwx 1 root root     17 2007-07-25 14:35 /usr/local/lib/libamrwb.so -> libamrwb.so.2.0.0
  11.
      lrwxrwxrwx 1 root root     17 2007-07-25 14:35 /usr/local/lib/libamrwb.so.2 -> libamrwb.so.2.0.0
  12.
      -rwxr-xr-x 1 root root 332341 2007-07-25 14:35 /usr/local/lib/libamrwb.so.2.0.0

---

