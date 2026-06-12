---
title: "helgrind shows race conditions with atomic types"
date: 2017-12-29
forum: Programming Talk
---

### Post by chuchi on 2017-12-29
Hi there!


Valgrind tool helgrind is reporting some race conditions with atomic variables.


If you run the code in this link : [http://www.cplusplus.com/reference/atomic/atomic/atomic/](http://www.cplusplus.com/reference/atomic/atomic/atomic/) in helgrind:


```

valgrind --tool=helgrind ./main

```


Then helgrind shows this error :


```

==14825== Possible data race during write of size 1 at 0x6062C9 by thread #1
==14825== Locks held: none
==14825==    at 0x4015B3: store (atomic_base.h:374)
==14825==    by 0x4015B3: std::__atomic_base<bool>::operator=(bool) (atomic_base.h:267)
==14825==    by 0x40130E: std::atomic<bool>::operator=(bool) (atomic:74)
==14825==    by 0x40119F: main (main.cpp:21)
==14825== 
==14825== This conflicts with a previous read of size 1 by thread #11
==14825== Locks held: none
==14825==    at 0x401343: load (atomic_base.h:396)
==14825==    by 0x401343: std::atomic<bool>::operator bool() const (atomic:81)
==14825==    by 0x401097: count1m(int) (main.cpp:11)
==14825==    by 0x4037BB: void std::_Bind_simple<void (*(int))(int)>::_M_invoke<0ul>(std::_Index_tuple<0ul>) (functional:1531)
==14825==    by 0x4036C7: std::_Bind_simple<void (*(int))(int)>::operator()() (functional:1520)
==14825==    by 0x403657: std::thread::_Impl<std::_Bind_simple<void (*(int))(int)> >::_M_run() (thread:115)
==14825==    by 0x4EF8C7F: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21)
==14825==    by 0x4C34DB6: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==14825==    by 0x53DF6B9: start_thread (pthread_create.c:333)
==14825==  Address 0x6062c9 is 0 bytes inside data symbol "ready"

```


Why? Is not the atomic boolean 'ready' supposed to be thread-safe?


Thanks a lot!


All the best

---

### Post by norobro on 2017-12-30
Try using atomic::exchange() instead of atomic::operator=() on line 21.
```
//ready = true;
ready.exchange(true);
```
I get no errors with the change. 
> The construction itself is not atomic: Accessing the object while being constructed may initiate a data race.I guess the above is supposed to be a hint but after a quick look at the source code I don't see why one would produce the error and not the other.

---

### Post by chuchi on 2018-01-02
Hi norobo!

Yes you are right, thanks a lot!!

---

