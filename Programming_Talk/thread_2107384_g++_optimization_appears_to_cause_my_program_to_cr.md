---
title: "g++ optimization appears to cause my program to crash"
date: 2013-01-21
forum: Programming Talk
---

### Post by EricDallal on 2013-01-21
Hello,

I am trying to compile a program with the -O flag but the program crashes with a segfault whenever I compile with any of -O1, -O2, or -O3. I compiled the program with -Wall -ansi and -Wextra and obtain no warnings. The program works correctly without any optimization flags.

I have also tried adding the -g option and running the program in gdb. The program crashes in the following code segment:

```

int GetURDFS(FSM *fsm, ES *es, int K, EL el, IS &ur, int as) {
	const int x1 = as % (fsm->n);
	int n1 = as/(fsm->n) - 1;
	int x2, n2;
	int ind;
	for (int i = 0, e = 1; i < fsm->ne; i++, e <<= 1) {
		if ((e & (es->yes)) || (e & el)) continue; /* Observable events. */
		if (((fsm->t)[x1]).find(e) == ((fsm->t)[x1]).end()) continue; /* Event e cannot occur from state x. */
		x2 = ((fsm->t)[x1])[e]; /* Next state for a transition from state x on event e. */
		if (n1 >= K) return 0;
		if (e & (es->fault)) n2 = n1 + 1; /* Fault event. */
		else n2 = (n1 == -1 ? -1 : n1 + 1); /* Must be unobservable non-faulty event. */
		ind = (n2 + 1)*(fsm->n) + x2;
		if (!(ur[ind/BITS] & (1 << (ind % BITS)))) {
			ur[ind/BITS] += (1 << (ind % BITS));
			if (!GetURDFS(fsm, es, K, el, ur, ind)) return 0; /* Diagnosability violation occured. */
		}
	}
	return 1;
}

```

The error caught by gdb is:
Program received signal SIGSEGV, Segmentation fault.
0x0000000000401843 in std::map<int, int, std::less<int>, std::allocator<std::pair<int const, int> > >::find (fsm=0x60a2e0, es=0x60a300, K=<value optimized out>, el=0, ur=..., as=4)
    at /usr/include/c++/4.4/bits/stl_map.h:659
659           { return _M_t.find(__x); }

The back trace is:
Program received signal SIGSEGV, Segmentation fault.
0x0000000000404667 in std::_Rb_tree<int, std::pair<int const, int>, std::_Select1st<std::pair<int const, int> >, std::less<int>, std::allocator<std::pair<int const, int> > >::find (this=0x609188, 
    __k=@0x7fffff5ff04c) at /usr/include/c++/4.4/bits/stl_tree.h:1421
1421          iterator __j = _M_lower_bound(_M_begin(), _M_end(), __k);
(gdb) bt
#0  0x0000000000404667 in std::_Rb_tree<int, std::pair<int const, int>, std::_Select1st<std::pair<int const, int> >, std::less<int>, std::allocator<std::pair<int const, int> > >::find (this=0x609188, 
    __k=@0x7fffff5ff04c) at /usr/include/c++/4.4/bits/stl_tree.h:1421
#1  0x0000000000401848 in std::map<int, int, std::less<int>, std::allocator<std::pair<int const, int> > >::find (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, ur=..., as=7)
    at /usr/include/c++/4.4/bits/stl_map.h:659
#2  GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, ur=..., as=7) at MPO.cpp:268
#3  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#4  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#5  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#6  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#7  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#8  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#9  0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
#10 0x000000000040191c in GetURDFS (fsm=0x609010, es=0x60a300, K=<value optimized out>, el=0, 
    ur=<value optimized out>, as=<value optimized out>) at MPO.cpp:276
---Type <return> to continue, or q <return> to quit---q

printing x1 from gdb gives me:
(gdb) print x1
$1 = 6328720

but printing as % (fsm->n) from gdb gives me:
(gdb) print as % (fsm->n)
$4 = 7

How is this possible?

---

### Post by Ghostmn on 2013-01-21
Could you package up the entire source and post on here? I definitely would be interested in compiling this myself.

---

### Post by EricDallal on 2013-01-22
I read online that optimization levels rarely cause program crashes in good code, but that they can sometimes cause crashes in programs with memory leaks, and that the best tool to diagnose this is valgrind. So I ran the program through valgrind and it appears that there are no memory leaks but it would seem that there was a stack overflow:

==3404== Stack overflow in thread 1: can't grow stack to 0x7fe801ff8
==3404== 
==3404== Process terminating with default action of signal 11 (SIGSEGV)
==3404==  Access not within mapped region at address 0x7FE801FF8
==3404==    at 0x4046C8: std::_Rb_tree<int, std::pair<int const, int>, std::_Select1st<std::pair<int const, int> >, std::less<int>, std::allocator<std::pair<int const, int> > >::find(int const&) (stl_tree.h:1418)
==3404==    by 0x401B26: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (stl_map.h:659)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==    by 0x401BF9: GetURDFS(FSM*, ES*, int, int, std::vector<int, std::allocator<int> >&, int) (MPO.cpp:278)
==3404==  If you believe this happened as a result of a stack
==3404==  overflow in your program's main thread (unlikely but
==3404==  possible), you can try to increase the size of the
==3404==  main thread stack using the --main-stacksize= flag.
==3404==  The main thread stack size used in this run was 8388608.
==3404== Stack overflow in thread 1: can't grow stack to 0x7fe801fb8

Correctly implemented, my algorithm should not allow for the possibility of stack overflow, but I will look more closely now that I know what the problem is. I am nevertheless stumped as to why the stack overflow seems to occur only when I compile with optimization. Any ideas?

As for posting the entire code, I will have to ask my advisor whether or not I am allowed to do that. The code isn't proprietary and I don't plan to sell it, but it is research related and I'm not familiar with all the rules involved here.

---

### Post by spjackson on 2013-01-23
I suspect that the recursive calls to GetURDFS are infinite when optimisation is on. You could test this theory by logging calls to the function with optimisation on and off.

If that's what is happening, then you either have undefined behaviour in the "if" conditions or in the manipulation of variables (I haven't checked carefully), or it's an optimizer bug. In the latter case, g++ version may be relevant.

---

