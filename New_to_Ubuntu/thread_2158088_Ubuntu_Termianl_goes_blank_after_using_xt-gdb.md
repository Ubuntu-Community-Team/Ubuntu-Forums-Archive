---
title: "Ubuntu Termianl goes blank after using xt-gdb"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by akhildmx on 2013-06-27
I am using xt-gdb to run an application on some hardware, I am using basic command like         
  
     (xt-gdb) make       (xt-gdb) target remote myip:port      (xt-gdb) myapp       (xt-gdb) c      ctrl+c      (xt-gdb) bt   Now, to debug my application I have to ctr+c to get out of continue  loop and to get the back trace stack. My one cycle includes exiting out  of xt-gdb and starting it again with the above set of commands, my  terminal hangs after 6-8 such cycles. Opening a new terminal shows a  blank window, I can type commands but don't get any response. Only way  out is to restart my system. 
  I am running 64 bit Ubuntu 12.04 LTS, any help is appreciated.

---

