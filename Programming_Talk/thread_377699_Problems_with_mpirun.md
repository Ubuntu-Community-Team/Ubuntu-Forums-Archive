---
title: "Problems with mpirun"
date: 2007-03-06
forum: Programming Talk
---

### Post by jogebau on 2007-03-06
Hi,

I need to run a mpi paralell program using mpirun on my home computer, but seems like I need help to get it to work.

I invoke the program using

mpirun -np 8 <progname>

my program exits with:

p1_25171:  p4_error: net_recv read:  probable EOF on socket: 1
p3_25185:  p4_error: interrupt SIGx: 13
p4_25192:  p4_error: interrupt SIGx: 13
p5_25198:  p4_error: interrupt SIGx: 13
p6_25204:  p4_error: interrupt SIGx: 13
p7_25211:  p4_error: interrupt SIGx: 13
p2_25179:  p4_error: net_recv read:  probable EOF on socket: 1
p8_25217:  p4_error: interrupt SIGx: 13
rm_l_1_25176: (14.978777) net_send: could not write to fd=5, errno = 32
rm_l_2_25182: (12.926832) net_send: could not write to fd=5, errno = 32
p6_25204: (15.160016) net_send: could not write to fd=5, errno = 32
p4_25192: (19.050811) net_send: could not write to fd=5, errno = 32
p5_25198: (17.134055) net_send: could not write to fd=5, errno = 32
p7_25211: (12.505457) net_send: could not write to fd=5, errno = 32
p3_25185: (20.958030) net_send: could not write to fd=5, errno = 32
p2_25179: (24.949022) net_send: could not write to fd=5, errno = 32

Any help is very much appreciated!

---

### Post by jogebau on 2007-03-06
Hi,

I need to run a mpi paralell program using mpirun on my home computer, but seems like I need help to get it to work.

I invoke the program using

mpirun -np 8 <progname>

my program exits with:

p1_25171:  p4_error: net_recv read:  probable EOF on socket: 1
p3_25185:  p4_error: interrupt SIGx: 13
p4_25192:  p4_error: interrupt SIGx: 13
p5_25198:  p4_error: interrupt SIGx: 13
p6_25204:  p4_error: interrupt SIGx: 13
p7_25211:  p4_error: interrupt SIGx: 13
p2_25179:  p4_error: net_recv read:  probable EOF on socket: 1
p8_25217:  p4_error: interrupt SIGx: 13
rm_l_1_25176: (14.978777) net_send: could not write to fd=5, errno = 32
rm_l_2_25182: (12.926832) net_send: could not write to fd=5, errno = 32
p6_25204: (15.160016) net_send: could not write to fd=5, errno = 32
p4_25192: (19.050811) net_send: could not write to fd=5, errno = 32
p5_25198: (17.134055) net_send: could not write to fd=5, errno = 32
p7_25211: (12.505457) net_send: could not write to fd=5, errno = 32
p3_25185: (20.958030) net_send: could not write to fd=5, errno = 32
p2_25179: (24.949022) net_send: could not write to fd=5, errno = 32

any help appreciated!

---

### Post by jogebau on 2007-03-07
sorry for the double post btw

---

### Post by jogebau on 2007-03-13
bump

---

