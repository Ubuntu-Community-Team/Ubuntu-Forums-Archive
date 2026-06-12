---
title: "wings3d install failed?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Zopiac on 2008-09-06
I installed wings3d v0.99.03 and when i try to run it, nothing happens. i run and terminal and it outputs:

```
ERROR: ld.so: object '/home/Zopiac/wings-0.99.03/lib/esdl-0.96.0626/priv/libSDL-1.2.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/home/Zopiac/wings-0.99.03/lib/esdl-0.96.0626/priv/libSDL-1.2.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Reading preferences from: /home/Zopiac/.wings
Removed pref: {smoothed_preview_cage,false}
Removed pref: {smoothed_preview_edges,false}
Driver Failed {error,{open_error,-10}} 
ERROR: ld.so: object '/home/Zopiac/wings-0.99.03/lib/esdl-0.96.0626/priv/libSDL-1.2.so.0' from LD_PRELOAD cannot be preloaded: ignored.
exec: 1: sdl_driver: not found

=ERROR REPORT==== 6-Sep-2008::13:14:58 ===
Error in process <0.29.0> with exit value: {badarg,[{erlang,port_control,[esdl_port,21,<<4 bytes>>]},{sdl,init,1},{wings_init,init,0},{wings,init,1}]}



Fatal internal error - log written to /home/Zopiac/wings_crash.dump


```

---

