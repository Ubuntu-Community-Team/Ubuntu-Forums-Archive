---
title: "Can't link to libsensors"
date: 2014-07-22
forum: Packaging and Compiling Programs
---

### Post by bjrosen on 2014-07-22
I'm trying to do a build of sys_basher on Ubuntu 14.4 but there is a problem linking to libsensors. I have libsensors4-dev installed. This works fine on Redhat systems (Fedora, RHEL/CentOS), what do I need to do to get it to link to libsensors on an Ubuntu system?


gcc -O2 -Wuninitialized -Wall -D_FORTIFY_SOURCE=2 -Wformat -Wno-multichar -Wreturn-type -Wswitch -Wunused-variable -g  -lm -pthread -lsensors	 -o sys_basher sys_main.o sys_utils.o sys_disk.o sys_kernel.o sys_fp.o sys_int.o sys_mem.o lin_utils.o sys_sensors3.o
sys_sensors3.o: In function `getTemps':
/home/bjrosen/projects/sys_basher/sys_sensors3.c:52: undefined reference to `sensors_init'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:65: undefined reference to `sensors_get_detected_chips'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:72: undefined reference to `sensors_get_features'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:110: undefined reference to `sensors_get_features'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:75: undefined reference to `sensors_get_label'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:94: undefined reference to `sensors_get_value'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:114: undefined reference to `sensors_get_detected_chips'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:117: undefined reference to `sensors_cleanup'
/home/bjrosen/projects/sys_basher/sys_sensors3.c:100: undefined reference to `sensors_cleanup'

---

