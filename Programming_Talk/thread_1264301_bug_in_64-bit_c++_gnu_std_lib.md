---
title: "bug in 64-bit c++ gnu std lib?"
date: 2009-09-12
forum: Programming Talk
---

### Post by manualqr on 2009-09-12
I think I may have encountered a bug in the libraries g++ provides. I'm posting here to see if anyone has seen the same thing, or if I should report this.

I've got a 64-bit machine and my program segfaults when I use GNU's <vector>. Specifically;
```

#include <algorithm>
#include <vector>

vector<ushort> shades;
// stuff snipped
shades.push_back(3); // segfault
sort(shades.begin(), shades.end());

```

here's the error;
```

(gdb) br median_filter.hxx:11
Breakpoint 2 at 0x401262: file median_filter.hxx, line 11.
(gdb) r
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /home/vk/Desktop/lcp/src/main 
reading all images...
smoothing images with a 3d median filter...

Breakpoint 2, filter_voxel (volume=0x7fd2ce616010, z=0, y=0, x=0) at median_filter.hxx:11
11		vector<ushort> shades;
(gdb) s
vector (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:214
214	      : _Base() { }
(gdb) 
_Vector_base (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:109
109	      : _M_impl() { }
(gdb) 
_Vector_impl (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:85
85		: _Tp_alloc_type(), _M_start(0), _M_finish(0), _M_end_of_storage(0)
(gdb) 
allocator (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/allocator.h:98
98	      allocator() throw() { }
(gdb) 
new_allocator (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/ext/new_allocator.h:69
69	      new_allocator() throw() { }
(gdb) 
_Vector_impl (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:86
86		{ }
(gdb) 
filter_voxel (volume=0x7fd2ce616010, z=0, y=0, x=0) at median_filter.hxx:13
13		for (int i=z-1; i <= z+1; ++i) {
(gdb) 
14			for (int j=y-1; j <= j+1; ++j) {
(gdb) 
15				for (int k=x-1; k <= x+1; ++k) {
(gdb) 
16					if (z < 0 || x >= num_imgs || y < 0 || y >= 512	|| x < 0 || x >= 512) {
(gdb) 
20					shades.push_back(volume[i].pix[j][k]);
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::push_back (this=0x7fffdfd17eb0, __x=@0x7fd2ce59580e) at /usr/include/c++/4.3/bits/stl_vector.h:688
688		if (this->_M_impl._M_finish != this->_M_impl._M_end_of_storage)
(gdb) 
694		  _M_insert_aux(end(), __x);
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::end (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:396
396	      { return iterator(this->_M_impl._M_finish); }
(gdb) 
__normal_iterator (this=0x7fffdfd17e50, __i=@0x7fffdfd17eb8) at /usr/include/c++/4.3/bits/stl_iterator.h:683
683	      __normal_iterator(const _Iterator& __i) : _M_current(__i) { }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_insert_aux (this=0x7fffdfd17eb0, __position={_M_current = 0x0}, __x=@0x7fd2ce59580e) at /usr/include/c++/4.3/bits/vector.tcc:286
286	      if (this->_M_impl._M_finish != this->_M_impl._M_end_of_storage)
(gdb) 
307		    _M_check_len(size_type(1), "vector::_M_insert_aux");
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_check_len (this=0x7fffdfd17eb0, __n=1, __s=0x4040a1 "vector::_M_insert_aux") at /usr/include/c++/4.3/bits/stl_vector.h:1077
1077		if (max_size() - size() < __n)
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::max_size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:490
490	      { return _M_get_Tp_allocator().max_size(); }
(gdb) 
std::_Vector_base<unsigned short, std::allocator<unsigned short> >::_M_get_Tp_allocator (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:102
102	      { return *static_cast<const _Tp_alloc_type*>(&this->_M_impl); }
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::max_size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/ext/new_allocator.h:102
102	      { return size_t(-1) / sizeof(_Tp); }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:485
485	      { return size_type(this->_M_impl._M_finish - this->_M_impl._M_start); }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_check_len (this=0x7fffdfd17eb0, __n=1, __s=0x4040a1 "vector::_M_insert_aux") at /usr/include/c++/4.3/bits/stl_vector.h:1080
1080		const size_type __len = size() + std::max(size(), __n);
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:485
485	      { return size_type(this->_M_impl._M_finish - this->_M_impl._M_start); }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:485
485	      { return size_type(this->_M_impl._M_finish - this->_M_impl._M_start); }
(gdb) 
std::max<unsigned long> (__a=@0x7fffdfd17de8, __b=@0x7fffdfd17dd8) at /usr/include/c++/4.3/bits/stl_algobase.h:215
215	      if (__a < __b)
(gdb) 
216		return __b;
(gdb) 
218	    }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_check_len (this=0x7fffdfd17eb0, __n=1, __s=0x4040a1 "vector::_M_insert_aux") at /usr/include/c++/4.3/bits/stl_vector.h:1081
1081		return (__len < size() || __len > max_size()) ? max_size() : __len;
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:485
485	      { return size_type(this->_M_impl._M_finish - this->_M_impl._M_start); }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::max_size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:490
490	      { return _M_get_Tp_allocator().max_size(); }
(gdb) 
std::_Vector_base<unsigned short, std::allocator<unsigned short> >::_M_get_Tp_allocator (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:102
102	      { return *static_cast<const _Tp_alloc_type*>(&this->_M_impl); }
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::max_size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/ext/new_allocator.h:102
102	      { return size_t(-1) / sizeof(_Tp); }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_check_len (this=0x7fffdfd17eb0, __n=1, __s=0x4040a1 "vector::_M_insert_aux") at /usr/include/c++/4.3/bits/stl_vector.h:1082
1082	      }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_insert_aux (this=0x7fffdfd17eb0, __position={_M_current = 0x0}, __x=@0x7fd2ce59580e) at /usr/include/c++/4.3/bits/vector.tcc:308
308		  pointer __new_start(this->_M_allocate(__len));
(gdb) 
std::_Vector_base<unsigned short, std::allocator<unsigned short> >::_M_allocate (this=0x7fffdfd17eb0, __n=1) at /usr/include/c++/4.3/bits/stl_vector.h:144
144	      { return __n != 0 ? _M_impl.allocate(__n) : 0; }
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::allocate (this=0x7fffdfd17eb0, __n=1) at /usr/include/c++/4.3/ext/new_allocator.h:89
89		if (__builtin_expect(__n > this->max_size(), false))
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::max_size (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/ext/new_allocator.h:102
102	      { return size_t(-1) / sizeof(_Tp); }
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::allocate (this=0x7fffdfd17eb0, __n=1) at /usr/include/c++/4.3/ext/new_allocator.h:92
92		return static_cast<_Tp*>(::operator new(__n * sizeof(_Tp)));
(gdb) 
93	      }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_insert_aux (this=0x7fffdfd17eb0, __position={_M_current = 0x0}, __x=@0x7fd2ce59580e) at /usr/include/c++/4.3/bits/vector.tcc:309
309		  pointer __new_finish(__new_start);
(gdb) 
316		      __new_finish =
(gdb) 
std::_Vector_base<unsigned short, std::allocator<unsigned short> >::_M_get_Tp_allocator (this=0x7fffdfd17eb0) at /usr/include/c++/4.3/bits/stl_vector.h:98
98	      { return *static_cast<_Tp_alloc_type*>(&this->_M_impl); }
(gdb) 
__gnu_cxx::__normal_iterator<unsigned short*, std::vector<unsigned short, std::allocator<unsigned short> > >::base (this=0x7fffdfd17e20) at /usr/include/c++/4.3/bits/stl_iterator.h:748
748	      { return _M_current; }
(gdb) 
std::__uninitialized_move_a<unsigned short*, unsigned short*, std::allocator<unsigned short> > (__first=0x0, __last=0x0, __result=0x1328010, __alloc=@0x7fffdfd17eb0)
    at /usr/include/c++/4.3/bits/stl_uninitialized.h:272
272						 __result, __alloc);
(gdb) 
std::__uninitialized_copy_a<unsigned short*, unsigned short*, unsigned short> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_uninitialized.h:262
262	    { return std::uninitialized_copy(__first, __last, __result); }
(gdb) 
std::uninitialized_copy<unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_uninitialized.h:122
122		uninitialized_copy(__first, __last, __result);
(gdb) 
std::__uninitialized_copy<true>::uninitialized_copy<unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_uninitialized.h:98
98	        { return std::copy(__first, __last, __result); }
(gdb) 
std::copy<unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:466
466		       std::__miter_base<_II>::__b(__last), __result));
(gdb) 
std::__miter_base<unsigned short*, false>::__b (__it=0x0) at /usr/include/c++/4.3/bits/stl_algobase.h:287
287	      { return __it; }
(gdb) 
std::__miter_base<unsigned short*, false>::__b (__it=0x0) at /usr/include/c++/4.3/bits/stl_algobase.h:287
287	      { return __it; }
(gdb) 
std::__copy_move_a2<false, unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:435
435			  std::__niter_base<_OI>::__b(__result)));
(gdb) 
std::__niter_base<unsigned short*, false>::__b (__it=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:269
269	      { return __it; }
(gdb) 
std::__niter_base<unsigned short*, false>::__b (__it=0x0) at /usr/include/c++/4.3/bits/stl_algobase.h:269
269	      { return __it; }
(gdb) 
std::__niter_base<unsigned short*, false>::__b (__it=0x0) at /usr/include/c++/4.3/bits/stl_algobase.h:269
269	      { return __it; }
(gdb) 
std::__copy_move_a<false, unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:393
393				     && __are_same<_ValueTypeI, _ValueTypeO>::__value);
(gdb) 
396		                      _Category>::__copy_m(__first, __last, __result);
(gdb) 
std::__copy_move<false, true, std::random_access_iterator_tag>::__copy_m<unsigned short> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:377
377		  __builtin_memmove(__result, __first,
(gdb) 
379		  return __result + (__last - __first);
(gdb) 
380		}
(gdb) 
std::__copy_move_a<false, unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:397
397	    }
(gdb) 
std::__copy_move_a2<false, unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:436
436	    }
(gdb) 
std::copy<unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_algobase.h:467
467	    }
(gdb) 
std::uninitialized_copy<unsigned short*, unsigned short*> (__first=0x0, __last=0x0, __result=0x1328010) at /usr/include/c++/4.3/bits/stl_uninitialized.h:123
123	    }
(gdb) 
std::__uninitialized_move_a<unsigned short*, unsigned short*, std::allocator<unsigned short> > (__first=0x0, __last=0x0, __result=0x1328010, __alloc=@0x7fffdfd17eb0)
    at /usr/include/c++/4.3/bits/stl_uninitialized.h:273
273	    }
(gdb) 
std::vector<unsigned short, std::allocator<unsigned short> >::_M_insert_aux (this=0x7fffdfd17eb0, __position={_M_current = 0x0}, __x=@0x7fd2ce59580e) at /usr/include/c++/4.3/bits/vector.tcc:321
321		      this->_M_impl.construct(__new_finish, __x);
(gdb) 
__gnu_cxx::new_allocator<unsigned short>::construct (this=0x7fffdfd17eb0, __p=0x1328010, __val=@0x7fd2ce59580e) at /usr/include/c++/4.3/ext/new_allocator.h:108
108	      { ::new((void *)__p) _Tp(__val); }
(gdb) 
operator new (__p=0x1328010) at /usr/include/c++/4.3/new:105
105	inline void* operator new(std::size_t, void* __p) throw() { return __p; }
(gdb) 

Program received signal SIGSEGV, Segmentation fault.
0x0000000000402441 in __gnu_cxx::new_allocator<unsigned short>::construct (this=0x7fffdfd17eb0, __p=0x1328010, __val=@0x7fd2ce59580e) at /usr/include/c++/4.3/ext/new_allocator.h:108
108	      { ::new((void *)__p) _Tp(__val); }

```

I'm using;
> 
vk@vk-laptop ~/Desktop/lcp/src $ g++ --version
g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Am I doing something wrong, or is this an actual bug?

edit: I fixed the logic bug in there but it doesn't prevent the segfaults.

---

### Post by dribeas on 2009-09-12
I have been using vectors with g++ 4.3 for some time (pretty much since the first g++4.3 came out) both in 32 and 64 bit and did not have a single problem with it. I would assume that there is a problem in another part of the code (buffer overrun?). Post a code snippet that is easier to cut and test. Trying to follow your code from the debugger output is more than I can handle right now.

---

### Post by MadCow108 on 2009-09-12
I think this is the problem:
for (int j=y-1; j <= j+1; ++j) {
its an infinite loop, so you overrun your pix vector => segfault

---

### Post by manualqr on 2009-09-12
> **MadCow108 said:**
> I think this is the problem:
for (int j=y-1; j <= j+1; ++j) {
its an infinite loop, so you overrun your pix vector => segfault

:), I just logged in to say that. It's not an issue with g++ at all!

I realized this after I switched to an array for efficiency purposes.. this function is run 512^2 (262144?) times, and it sorts 27 pixels every time! Here's the whole thing if anyone's interested;
```

void filter_voxel(img* volume, ushort z, ushort y, ushort x) {
	static ushort shades[27];
	static ushort idx;
	idx = 0;
	
	for (int i=z-1; i < z+2; ++i) {
		for (int j=y-1; j < y+2; ++j) {
			for (int k=x-1; k < x+2; ++k) {
				if (i < 0 || i >= num_imgs || j < 0 || j > 511 || k < 0 || k > 511) {
					shades[idx] = 0;
				} else {
					shades[idx] = volume[i].pix[j][k];
				}
				
				++idx;
			}
		}
	}
	
	sort(shades, shades + (sizeof(shades) + sizeof(ushort)));	
	volume[z].pix[y][x] = shades[13]; // median (14th - 1)
}

void median_volume_filter(img* volume) {
	for (int z=0; z < num_imgs; ++z) {
		cout << (1.0 * (z + 1) / num_imgs * 100.0) << "% completed\n";
		
		for (int y=0; y < 512; ++y) {
			for (int x=0; x < 512; ++x) {
				filter_voxel(volume, z, y, x);
			}
		}
	}
}

```

---

