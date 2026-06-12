---
title: "Problem with C++ on ubuntu edgy"
date: 2006-11-06
forum: Programming Talk
---

### Post by sttop on 2006-11-06
hey guys, i'm having some problems to run a simple program i've written in c++ on ubuntu edgy, and i don't know what to do... here is the code:

```

class huffmanHeapNode {
	private:
		int chave;
	
	public:
		huffmanHeapNode() {
			chave = 0;
		}
		huffmanHeapNode(int newChave) {;
			chave = newChave;
		}
		virtual ~huffmanHeapNode() { };
		
		int getKey() {
			return chave;
		}
		
		bool operator< (const huffmanHeapNode &rhs) {
			if (chave < rhs.chave) {
				return true;
			} else {
				return false;
			}
		}
		bool operator<= (const huffmanHeapNode &rhs) {
			if (chave <= rhs.chave) {
				return true;
			} else {
				return false;
			}
		}
		bool operator> (const huffmanHeapNode &rhs) {
			if (chave > rhs.chave) {
				return true;
			} else {
				return false;
			}
		}
		bool operator>= (const huffmanHeapNode &rhs) {
			if (chave >= rhs.chave) {
				return true;
			} else {
				return false;
			}
		}
};
using namespace std;

int main() {
	huffmanHeapNode * array = new huffmanHeapNode [10];
	delete array;
	return 0;
}


```

there are no problems when compiling it with g++, but when i try to run it,  I get the following error:

```

*** glibc detected *** ./huffman: munmap_chunk(): invalid pointer: 0x0804a00c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7d18b4a]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7ec7fc1]
./huffman(__gxx_personality_v0+0x1a2)[0x8048596]
./huffman(__gxx_personality_v0+0x155)[0x8048549]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7cc78cc]
./huffman(__gxx_personality_v0+0x5d)[0x8048451]
======= Memory map: ========
08048000-08049000 r-xp 00000000 03:02 64841      /home/top/Documents/LAED/huffman/huffman
08049000-0804a000 rw-p 00000000 03:02 64841      /home/top/Documents/LAED/huffman/huffman
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7cb1000-b7cb2000 rw-p b7cb1000 00:00 0 
b7cb2000-b7ddf000 r-xp 00000000 03:02 340417     /lib/tls/i686/cmov/libc-2.4.so
b7ddf000-b7de1000 r--p 0012c000 03:02 340417     /lib/tls/i686/cmov/libc-2.4.so
b7de1000-b7de3000 rw-p 0012e000 03:02 340417     /lib/tls/i686/cmov/libc-2.4.so
b7de3000-b7de6000 rw-p b7de3000 00:00 0 
b7de6000-b7df0000 r-xp 00000000 03:02 307715     /lib/libgcc_s.so.1
b7df0000-b7df1000 rw-p 00009000 03:02 307715     /lib/libgcc_s.so.1
b7df1000-b7e15000 r-xp 00000000 03:02 340425     /lib/tls/i686/cmov/libm-2.4.so
b7e15000-b7e17000 rw-p 00023000 03:02 340425     /lib/tls/i686/cmov/libm-2.4.so
b7e17000-b7eeb000 r-xp 00000000 03:02 682001     /usr/lib/libstdc++.so.6.0.8
b7eeb000-b7eee000 r--p 000d4000 03:02 682001     /usr/lib/libstdc++.so.6.0.8
b7eee000-b7ef0000 rw-p 000d7000 03:02 682001     /usr/lib/libstdc++.so.6.0.8
b7ef0000-b7ef7000 rw-p b7ef0000 00:00 0 
b7f02000-b7f03000 rw-p b7f02000 00:00 0 
b7f03000-b7f1c000 r-xp 00000000 03:02 307670     /lib/ld-2.4.so
b7f1c000-b7f1e000 rw-p 00018000 03:02 307670     /lib/ld-2.4.so
bfc88000-bfc9d000 rw-p bfc88000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

i think the problem is at the delete command, because when i comment its line there are no more errors when i execute the program.

by the way, it runs perfect on windows, even with the delete line uncommented...

---

### Post by po0f on 2006-11-06
sttop,

When you allocate an array with **new**, you have to deallocate the array with **delete []**, as in:
```
int main() {
	huffmanHeapNode * array = new huffmanHeapNode [10];
	delete [] array;
	return 0;
}
```

---

### Post by Houman on 2006-11-06
hi there;

the problem is that 
```

delete array;

```

should be 

```

delete [] array;

```

because youre trying to free memory allocated for an array,

now if you had

```

huffmanHeapNode * array = new huffmanHeapNode;  //single element
 
```

then just using "delete array" would have been fine (because it frees a single element not a whole array).

I think the crash happens because your program doesn't clean up after the memory that was allocated so you get the crash, windows works differently I suppose so it doesn't crash even though you didn't clean up after your program.

regards

Houman

---

### Post by sttop on 2006-11-06
thanks guys! as it runned perfectly at windows, i thought the problem was some package i haven't installed in ubuntu, and didn't see the simple error!!

i guess the reason of this difference in running the program at windows and ubuntu must be the different versions of the libraries i'm using in each one... i'll check this out later... thanks a lot!

---

