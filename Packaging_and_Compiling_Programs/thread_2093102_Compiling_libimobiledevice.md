---
title: "Compiling libimobiledevice"
date: 2012-12-09
forum: Packaging and Compiling Programs
---

### Post by georgeb1962 on 2012-12-09
Hi all,

I am getting a little bit farther, but also need help:
I have /usr/local/lib64/libusbmuxd.so.1.0.8 installed... should it be a different version??

Thanks:

george@Compuxeon:~/Downloads/libimobiledevice/libimobiledevice-1.0.7$ make
make  all-recursive
make[1]: Entering directory `/home/george/Downloads/libimobiledevice/libimobiledevice-1.0.7'
Making all in src
make[2]: Entering directory `/home/george/Downloads/libimobiledevice/libimobiledevice-1.0.7/src'
  CC     idevice.lo
idevice.c: In function 'usbmux_event_cb':
idevice.c:40:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c: In function 'idevice_get_device_list':
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:113:25: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c: In function 'idevice_new':
idevice.c:162:2: warning: implicit declaration of function 'usbmuxd_get_device_by_uuid' [-Wimplicit-function-declaration]
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c:165:17: error: 'usbmuxd_device_info_t' has no member named 'uuid'
idevice.c: In function 'idevice_connection_enable_ssl':
idevice.c:592:2: warning: 'gnutls_certificate_client_set_retrieve_function' is deprecated (declared at /usr/include/gnutls/compat.h:158) [-Wdeprecated-declarations]
make[2]: *** [idevice.lo] Error 1
make[2]: Leaving directory `/home/george/Downloads/libimobiledevice/libimobiledevice-1.0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/george/Downloads/libimobiledevice/libimobiledevice-1.0.7'
make: *** [all] Error 2

---

### Post by oldos2er on 2012-12-09
Post moved to its own thread.

---

### Post by sdowney717 on 2012-12-23
[https://launchpad.net/ubuntu/+source/libimobiledevice](https://launchpad.net/ubuntu/+source/libimobiledevice)

ok, found them here already compiled

---

