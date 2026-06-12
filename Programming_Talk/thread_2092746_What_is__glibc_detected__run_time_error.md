---
title: "What is *** glibc detected *** run time error?"
date: 2012-12-08
forum: Programming Talk
---

### Post by HunterDX77M on 2012-12-08
I've been getting [FONT="Courier New"]glibc detected[/FONT] error in various formats while trying to debug my homework. Some incarnations include:

```
*** glibc detected *** ./Project Two V3: free(): invalid next size (fast): 0x0850c220 ***
```

and

```
*** glibc detected *** ./Project Two V3: double free or corrupted (out)
```

([FONT="Courier New"]Project Two V3.cpp[/FONT] is the name of the source code file)

After thorough Google'ing, I still have no idea what this means and was hoping someone might be able to shed some light on it. Here's the situation: The program runs fine, giving exactly the output that I expect and this only occurs once the program has completely run through to the end of [FONT="Courier New"]main()[/FONT].

Here's a list of things that I've made sure to check for:
- Closing any files once and only once
- Deleting any dynamically allocated objects/variables from the heap that were allocated with the [FONT="Courier New"]new[/FONT] operator

I'd give the entire code, but it is a fairly large file (and I'd fail the project if someone found my code and handed in a copy of it).

**So why do these errors occur, generally?** I'd like see if I've covered all my bases.

---

### Post by MadCow108 on 2012-12-08
they occur when you corrupt your processes memory, specifically overwriting data glibc uses for memory management.
This is commonly caused by buffer overflows
Another possibility is that you free'd memory twice.

The best tool to debug it is valgrind.

---

### Post by HunterDX77M on 2012-12-08
I just ran valgrind from this quick tutorial I Google'd:

```
valgrind --tool=memcheck --leak-check=yes --show-reachable=yes --track-fds=yes ./Project\ Two\ V3

```

And I got all this output, but it doesn't tell me what line to go to.

```
==18994== Invalid write of size 4
==18994==    at 0x402E985: memmove (in /usr/lib/valgrind/vgpreload_memcheck-x86-linux.so)
==18994==    by 0x804DF91: Process** std::__copy_move<false, true, std::random_access_iterator_tag>::__copy_m<Process*>(Process* const*, Process* const*, Process**) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804DCC4: Process** std::__copy_move_a<false, Process**, Process**>(Process**, Process**, Process**) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804D71A: __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > > std::__copy_move_a2<false, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > > >(__gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804CB6E: __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > > std::copy<__gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > > >(__gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, __gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804B73F: std::vector<Process*, std::allocator<Process*> >::erase(__gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804A7C1: main (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==  Address 0x432c3ec is 4 bytes before a block of size 16 alloc'd
==18994==    at 0x402B9B4: operator new(unsigned int) (in /usr/lib/valgrind/vgpreload_memcheck-x86-linux.so)
==18994==    by 0x804DC59: __gnu_cxx::new_allocator<Process*>::allocate(unsigned int, void const*) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804D671: std::_Vector_base<Process*, std::allocator<Process*> >::_M_allocate(unsigned int) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804C8A2: std::vector<Process*, std::allocator<Process*> >::_M_insert_aux(__gnu_cxx::__normal_iterator<Process**, std::vector<Process*, std::allocator<Process*> > >, Process* const&) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x804B598: std::vector<Process*, std::allocator<Process*> >::push_back(Process* const&) (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994==    by 0x8049C58: main (in /home/murshed/Dropbox/School Work/Operating Systems/Memory Management Project/Murshed/Project Two V3)
==18994== 
```

And the summary

```
==18994== 
==18994== FILE DESCRIPTORS: 3 open at exit.
==18994== Open file descriptor 2: /dev/pts/0
==18994==    <inherited from parent>
==18994== 
==18994== Open file descriptor 1: /dev/pts/0
==18994==    <inherited from parent>
==18994== 
==18994== Open file descriptor 0: /dev/pts/0
==18994==    <inherited from parent>
==18994== 
==18994== 
==18994== HEAP SUMMARY:
==18994==     in use at exit: 0 bytes in 0 blocks
==18994==   total heap usage: 87 allocs, 87 frees, 19,158 bytes allocated
==18994== 
==18994== All heap blocks were freed -- no leaks are possible
==18994== 
==18994== For counts of detected and suppressed errors, rerun with: -v
==18994== ERROR SUMMARY: 3 errors from 1 contexts (suppressed: 0 from 0)
```

---

### Post by MadCow108 on 2012-12-08
build your project with debug symbols (-g flag of g++) and it can tell you the lines

---

### Post by HunterDX77M on 2012-12-08
> **MadCow108 said:**
> build your project with debug symbols (-g flag of g++) and it can tell you the lines

Thanks for the tip. I was able to track down the culprit line. It seems there was a mishap when I used the vector class' erase() function and some pointers. :D

If anything else comes up, I'll let you know. Thanks again!

---

