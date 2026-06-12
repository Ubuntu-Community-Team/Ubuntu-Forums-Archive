---
title: "nice hashmap for C"
date: 2009-07-24
forum: Programming Talk
---

### Post by manualqr on 2009-07-24
Every time I want to do a little bit of hobby programming, I consider what I want to get done and which language to do it in. It used to be that C almost never got picked because there was no easy way to use <feature foo>.

One of those features were hashmaps. C++ offers map and unordered_map from the STL, and there are many great libraries (e.g google's sparse-hash) that work well. I found a couple C hashmap implementations online but most of them were limited in some way, or just not to my liking. So I wrote my own, and I want to share it..

Features:
* maps keys to values :). e.g char* to double, long to int, etc.
* can grow (i.e not limited to n values)
* uses simple bools  to indicate errors
* insert and find functions
* option to make the hashmap thread safe
* option to use a value destructor when deleting the hashmap (so if you store malloc'd objects, the destructor you supply could free them)
* option to build a few hash functions (for integer & string keys)
* uses open-addressing to resolve collisions (and rehashes before the load degrades performance to the level of closed-addressing)
* (relatively) friendly interface: macros are used to handle casting for you
* only uses C standard libraries, so it won't add much to your executable size. (should work on many platforms because of this as well)

API:
* hashmap mk_hmap(hash function, equality function, optional destructor)
* bool hmap_add(hashmap, key, value)
* val hmap_get(hashmap, key)

I've done some basic tests with this and it seems to work well.. I don't have a reliable benchmark, so I won't post numbers.. But keep in mind, the hashmap implementation isn't normally a bottleneck - it's usually the hash function.

(If anyone would like to implement hmap_del, go for it!)

Here is version '1.0' of the hashmap, the product of lots of discussion and feedback. Enjoy!

---

### Post by manualqr on 2009-07-24
> 
(If anyone would like to implement hmap_del, go for it!)


Originally, I was planning a hmap_del function but I stopped work on it because it complicated too many things (hmap_add was 3 times its current size!). So I took the 'worse is better' path and just got rid of it.

I don't do it often, but it would be nice if I could delete items from the hashmap..

Can anyone suggest a sane way to implement this?

thanks.

---

### Post by monkeyking on 2009-07-24
nice one

thanks

---

### Post by nvteighen on 2009-07-25
Hmm... Some comments.

1) This shouldn't be a header file, but a source file. Header files should only contain preprocessor stuff, function declarations, type definitions or type forward declarations (i.e. just declaring some type exists but hiding the implementation), not code. Put all your code into a file hashmap.c and then put your public stuff into a header the user of your library should include. (The header file is an API enforcer).

Ah, the usual practice is to include the public header into the implementation module, so you don't have to repeat the type definitions and declarations in the .c file.

2) If you follow my first advice, you can get true private functions without recurring to the __blah notation. Very simple: declare your private functions as static and don't include them in the public header file. Nothing outside that module will be able to access those functions.

3) Then it comes to the question on hiding the implementation for types key_val_map and hashmap. I see your constructor mk_hmap works by creating a hashmap in stack and returning it. Be aware that you can only do this by telling the "user code" what exactly hashmap is... therefore, the header has to show the structure's type definition. But this allows that anyone could bypass the constructor:

```

hashmap myhash;
myhash.size = 1000;

```

If you don't mind that, well, perfect. It's just a design issue and you're your project's master :D But let me tell you how most libraries work to avoid that.

What they do is to put just the type **declaration** in the header file.
```

typedef struct hashmap hashmap;

```

The implementation is only known to the implementation module. This means that any user code including your header will just know there's a type called hashmap but nothing else... So, the only way to use it is through pointers. So, the constructor mk_hmap would malloc a hashmap and return a pointer to that place...

All members of hashmap will be hidden, as the definition is only known by the implementation module. The only way to give access to some member data will be by creating accessor functions.

I attach a very simple example (a list data type implementation) to show you how this is done. 

4) If interested, here's a link that will show you how to compile your code into a static or a dynamic library. [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

### Post by manualqr on 2009-07-25
> **nvteighen said:**
> 
1) This shouldn't be a header file, but a source file. Header files should only contain preprocessor stuff, function declarations, type definitions or type forward declarations (i.e. just declaring some type exists but hiding the implementation), not code. Put all your code into a file hashmap.c and then put your public stuff into a header the user of your library should include. (The header file is an API enforcer).

Ah, the usual practice is to include the public header into the implementation module, so you don't have to repeat the type definitions and declarations in the .c file.


Normally, I would agree. But for a project this small (is it even a project? meh, not really), I think the focus should be on implementation simplicity rather than its ostensible design. 

> 
2) If you follow my first advice, you can get true private functions without recurring to the __blah notation. Very simple: declare your private functions as static and don't include them in the public header file. Nothing outside that module will be able to access those functions.


The issue is that the macros expand out to those functions, so their prototypes must be in the header. Then they are exposed again! You may argue that this still leaves __oa_hmap_add() exposed unnecessarily. Well, take a look at that function's prototype. I don't think a programmer would mess with it on accident, much less mess with it successfully.

> 
3) Then it comes to the question on hiding the implementation for types key_val_map and hashmap. I see your constructor mk_hmap works by creating a hashmap in stack and returning it. Be aware that you can only do this by telling the "user code" what exactly hashmap is... therefore, the header has to show the structure's type definition. But this allows that anyone could bypass the constructor:

```

hashmap myhash;
myhash.size = 1000;

```

If you don't mind that, well, perfect. It's just a design issue and you're your project's master :D But let me tell you how most libraries work to avoid that.

What they do is to put just the type **declaration** in the header file.
```

typedef struct hashmap hashmap;

```

The implementation is only known to the implementation module. This means that any user code including your header will just know there's a type called hashmap but nothing else... So, the only way to use it is through pointers. So, the constructor mk_hmap would malloc a hashmap and return a pointer to that place...

All members of hashmap will be hidden, as the definition is only known by the implementation module. The only way to give access to some member data will be by creating accessor functions.


At the end of all of this, hashmap and key_val_map become opaque types - but what have we really gained? Programmers are now forced to create hashmaps on the heap (instead of having a choice in the matter). getters & setters may now be needed for something that's fairly trivial.

Yes, the guts of hashmap are exposed for all to see, but I don't think this is a design issue. Data hiding and implementation secrecy is something objected-oriented programmers worry about.. this is C!

> 
4) If interested, here's a link that will show you how to compile your code into a static or a dynamic library. [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

thanks

---

### Post by nvteighen on 2009-07-25
> **manualqr said:**
> Normally, I would agree. But for a project this small (is it even a project? meh, not really), I think the focus should be on implementation simplicity rather than its ostensible design.

Sorry, sir, but I consider that an excuse. **Always** use good practices!

> 
The issue is that the macros expand out to those functions, so their prototypes must be in the header. Then they are exposed again! You may argue that this still leaves __oa_hmap_add() exposed unnecessarily. Well, take a look at that function's prototype. I don't think a programmer would mess with it on accident, much less mess with it successfully.


No. Maybe I wasn't clear... Put __oa_hmap_add() as static into hashmap.c. Put the macros at hashmap.h. Include hashmap.h into hashmap.c... Where's the problem? Or, put the macros into hasmap.c if you don't want them to be public...

> 
At the end of all of this, hashmap and key_val_map become opaque types - but what have we really gained? Programmers are now forced to create hashmaps on the heap (instead of having a choice in the matter). getters & setters may now be needed for something that's fairly trivial.

Yes, the guts of hashmap are exposed for all to see, but I don't think this is a design issue. Data hiding and implementation secrecy is something objected-oriented programmers worry about.. this is C!

The issue is that you are doing OOP in C. You even (maybe subconsciously) use OOP terminology in your code such as constructor/destructor... C has no explicit OOP support, but OOP is a design paradigm... If you state your code in terms of certain objects, then it is OOP. 

I just suggested the data hiding to show you how usually modern C libraries approach these things... but of course, you can consider that public members are ok and go along with that design.

---

### Post by manualqr on 2009-07-25
> 
No. Maybe I wasn't clear... Put __oa_hmap_add() as static into hashmap.c. Put the macros at hashmap.h. Include hashmap.h into hashmap.c... Where's the problem? Or, put the macros into hasmap.c if you don't want them to be public...


No, you were clear. I was just discussing how the code would be if I didn't make a public interface. If I did, __oa_hmap_add() would be static, and that would work well. But the macros cannot be in hashmap.h unless __hmap_add/get are there as well. The macros take a lot of pain out of using the code, so I want them available.

Converting everything to a provide a safe interface would really only make one function (__oa_hmap_add) unavailable at the cost of having two separate files. The guts of hashmap would be hidden as well, but at the cost of having to malloc it. 

Call it an excuse for having bad design if you want, but I really believe that the Right Thing (tm) isn't the right thing in this case. I'm not worried about saving users from themselves, if they want to screw up the hashmap - they can go ahead. There's plenty of rope, and who am I to tell them to stop if they choose to hang themselves?

> 
C has no explicit OOP support, but OOP is a design paradigm... If you state your code in terms of certain objects, then it is OOP.


You're right of course. In retrospect the comment I made about "this is C!" was a mistake. All I meant to say is that some languages are better suited for oop than others - and that C isn't one of them.

I think both ways of organizing the code have their merits though. I'll attach a version with a safe interface to this post soon.

edit:
Oops. Seeing as __hmap* have to be in the header, so does __oa_hmap_add. So one less benefit of the OOP-ish version. Still if you gotta have it, here it is:

---

### Post by ibuclaw on 2009-07-26
> **manualqr said:**
> 
edit:
Oops. Seeing as __hmap* have to be in the header, so does __oa_hmap_add. So one less benefit of the OOP-ish version. Still if you gotta have it, here it is:

No they don't. :)

Just had a quick look, and here is my modded version.

And this is the diff patch (removed extraneous whitespace too).
```

diff -Naur hashmap.old/hashmap.c hashmap/hashmap.c
--- hashmap.old/hashmap.c	2009-07-26 04:25:04.000000000 +0100
+++ hashmap/hashmap.c	2009-07-26 07:41:42.000000000 +0100
@@ -1,17 +1,17 @@
 /*
  * hashmap.c
  * Copyright (c) 2009 Vedant Kumar
- * 
+ *
  * Permission is hereby granted, free of charge, to any person obtaining a copy
  * of this software and associated documentation files (the "Software"), to deal
  * in the Software without restriction, including without limitation the rights
  * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  * copies of the Software, and to permit persons to whom the Software is
  * furnished to do so, subject to the following conditions:
- * 
+ *
  * The above copyright notice and this permission notice shall be included in
  * all copies or substantial portions of the Software.
- * 
+ *
  * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
@@ -23,24 +23,9 @@
 
 #include "hashmap_public.h"
 
-struct key_val_map {
-	key k;
-	val v;
-};
-
-struct hashmap {
-	key_val_map *map;
-	uint32_t size;
-	uint32_t capacity;
-	uint32_t (*hash_fn)(key);
-	bool (*eq_fn)(key, key);
-#ifdef HMAP_DESTRUCTORS
-	void (*del_fn)(val);
-#endif
-#ifdef HMAP_THREAD_SAFE
-	sem_t lock;
-#endif
-};
+#define alias(name, aliasname) _alias(name, aliasname)
+#define _alias(name, aliasname) \
+      extern __typeof (name) aliasname __attribute__ ((alias (#name)));
 
 // hashmaps need a hash function, an equality function, and a destructor
 hashmap* mk_hmap(uint32_t (*hash_fn)(key),
@@ -49,7 +34,7 @@
 				, void (*del_fn)(val)
 			#endif
 				) {
-					
+	
 	hashmap* hmap = (hashmap*) malloc(sizeof(hashmap));
 	hmap->map = (key_val_map*) malloc(sizeof(key_val_map) * HMAP_PRESET_SIZE);
 	hmap->size = 0;
@@ -60,7 +45,7 @@
 	hmap->del_fn = del_fn;
 #endif
 #ifdef HMAP_THREAD_SAFE
-	sem_init(&hmap.lock, 0, 1);
+	sem_init(&hmap->lock, 0, 1);
 #endif
 	return hmap;
 }
@@ -108,3 +93,87 @@
 }
 
 #endif
+
+static void __oa_hmap_add(key_val_map* map, uint32_t size, uint32_t (*hash_fn)(key),
+                   key in, val out) {
+    static uint32_t hash;
+    hash = hash_fn(in) % size;
+ 
+    while (map[hash].v != NULL) {
+        hash = (hash + 1) % size;
+    }
+ 
+    map[hash].k = in;
+    map[hash].v = out;
+}
+
+bool __hmap_add(hashmap* hmap, key in, val out) {
+#ifdef HMAP_THREAD_SAFE
+    sem_wait(&hmap->lock);
+#endif
+
+    // performace degrades after a certain load
+    if (((float) hmap->size) / hmap->capacity > 0.70) {
+        key_val_map* temp = (key_val_map*) malloc(hmap->capacity * HMAP_GROWTH_RATE);
+        if (temp != NULL) {
+            hmap->capacity *= HMAP_GROWTH_RATE;
+        } else {
+        #ifdef HMAP_THREAD_SAFE
+            sem_post(&hmap->lock);
+        #endif
+            // we're out of memory
+            return false;
+        }
+ 
+        // re-posn all elements
+        static uint32_t it;
+        for (it=0; it < hmap->capacity; ++it) {
+            if (hmap->map[it].v != NULL) {
+                __oa_hmap_add(temp, hmap->capacity, hmap->hash_fn, in, out);
+            }
+        }
+ 
+        // swap out the old map with the new one
+        free(hmap->map);
+        hmap->map = temp;
+    }
+ 
+    __oa_hmap_add(hmap->map, hmap->capacity, hmap->hash_fn, in, out);
+    hmap->size += 1;
+
+#ifdef HMAP_THREAD_SAFE
+    sem_post(&hmap->lock);
+#endif
+
+    return true;
+}
+alias(__hmap_add, hmap_add);
+
+val __hmap_get(hashmap* hmap, key in) {
+#ifdef HMAP_THREAD_SAFE
+    sem_wait(&hmap->lock);
+#endif
+
+    static uint32_t hash;
+    hash = hmap->hash_fn(in) % hmap->capacity;
+ 
+    while (hmap->map[hash].v != NULL) {
+        if (hmap->eq_fn(in, hmap->map[hash].k)) {
+        #ifdef HMAP_THREAD_SAFE
+            sem_post(&hmap->lock);
+        #endif
+ 
+            return hmap->map[hash].v;
+        }
+ 
+        hash = (hash + 1) % hmap->capacity;
+    }
+
+ 
+#ifdef HMAP_THREAD_SAFE
+    sem_post(&hmap->lock);
+#endif
+ 
+    return NULL;
+}
+alias(__hmap_get, hmap_get);
diff -Naur hashmap.old/hashmap_public.h hashmap/hashmap_public.h
--- hashmap.old/hashmap_public.h	2009-07-26 04:25:02.000000000 +0100
+++ hashmap/hashmap_public.h	2009-07-26 07:43:50.000000000 +0100
@@ -1,17 +1,17 @@
 /*
- * hashmap.h 
+ * hashmap.h
  * Copyright (c) 2009 Vedant Kumar
- * 
+ *
  * Permission is hereby granted, free of charge, to any person obtaining a copy
  * of this software and associated documentation files (the "Software"), to deal
  * in the Software without restriction, including without limitation the rights
  * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  * copies of the Software, and to permit persons to whom the Software is
  * furnished to do so, subject to the following conditions:
- * 
+ *
  * The above copyright notice and this permission notice shall be included in
  * all copies or substantial portions of the Software.
- * 
+ *
  * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
@@ -21,6 +21,9 @@
  * THE SOFTWARE.
  */
 
+#ifndef _HASHMAP_H_
+#define _HASHMAP_H_
+
 #pragma once
 
 #define HMAP_PRESET_SIZE 	2 << 6 // use a power of 2 for faster array access
@@ -42,97 +45,35 @@
 typedef struct key_val_map key_val_map;
 typedef struct hashmap hashmap;
 
+struct key_val_map {
+    key k;
+    val v;
+};
+
+struct hashmap {
+    key_val_map *map;
+    uint32_t size;
+    uint32_t capacity;
+    uint32_t (*hash_fn)(key);
+    bool (*eq_fn)(key, key);
+#ifdef HMAP_DESTRUCTORS
+    void (*del_fn)(val);
+#endif
+#ifdef HMAP_THREAD_SAFE
+    sem_t lock;
+#endif
+};
+
 hashmap* mk_hmap(uint32_t (*hash_fn)(key),
 				bool (*eq_fn)(key, key)
 			#ifdef HMAP_DESTRUCTORS
 				, void (*del_fn)(val)
 			#endif
 			);
-			
-void free_hmap(hashmap*);
-
-void __oa_hmap_add(key_val_map* map, uint32_t size, uint32_t (*hash_fn)(key),
-				   key in, val out) {
-	static uint32_t hash;
-	hash = hash_fn(in) % size;
-	
-	while (map[hash].v != NULL) {
-		hash = (hash + 1) % size;
-	}
-	
-	map[hash].k = in;
-	map[hash].v = out;
-}
-
-bool __hmap_add(hashmap* hmap, key in, val out) {
-#ifdef HMAP_THREAD_SAFE
-	sem_wait(&hmap->lock);
-#endif
-
-	// performace degrades after a certain load
-	if (((float) hmap->size) / hmap->capacity > 0.70) {
-		key_val_map* temp = (key_val_map*) malloc(hmap->capacity * HMAP_GROWTH_RATE);
-		if (temp != NULL) {
-			hmap->capacity *= HMAP_GROWTH_RATE;
-		} else {
-		#ifdef HMAP_THREAD_SAFE
-			sem_post(&hmap->lock);
-		#endif
-			// we're out of memory
-			return false;
-		}
-		
-		// re-posn all elements
-		static uint32_t it;
-		for (it=0; it < hmap->capacity; ++it) {
-			if (hmap->map[it].v != NULL) {
-				__oa_hmap_add(temp, hmap->capacity, hmap->hash_fn, in, out);
-			}
-		}
-		
-		// swap out the old map with the new one
-		free(hmap->map);
-		hmap->map = temp;
-	}
-	
-	__oa_hmap_add(hmap->map, hmap->capacity, hmap->hash_fn, in, out);
-	hmap->size += 1;
-
-#ifdef HMAP_THREAD_SAFE
-	sem_post(&hmap->lock);
-#endif
-
-	return true;
-}
-
-#define hmap_add(hmap, in, out) __hmap_add(hmap, (key) in, (val) out)
-
-val __hmap_get(hashmap* hmap, key in) {
-#ifdef HMAP_THREAD_SAFE
-	sem_wait(&hmap->lock);
-#endif
-
-	static uint32_t hash;
-	hash = hmap->hash_fn(in) % hmap->capacity;
 	
-	while (hmap->map[hash].v != NULL) {
-		if (hmap->eq_fn(in, hmap->map[hash].k)) {
-		#ifdef HMAP_THREAD_SAFE
-			sem_post(&hmap->lock);
-		#endif			
-			
-			return hmap->map[hash].v;
-		}
-		
-		hash = (hash + 1) % hmap->capacity;
-	}
+void free_hmap(hashmap*);
+bool hmap_add(hashmap*, key, val);
+val hmap_get(hashmap*, key);
 
-	
-#ifdef HMAP_THREAD_SAFE
-	sem_post(&hmap->lock);
+#else
 #endif
-	
-	return NULL;
-}
-
-#define hmap_get(hmap, obj) __hmap_get(&hmap, (val) obj)	

```


Two main points of interest are these bits here:
```

 #ifdef HMAP_THREAD_SAFE
-	sem_init(&hmap.lock, 0, 1);
+	sem_init(&hmap->lock, 0, 1);
 #endif


+#define alias(name, aliasname) _alias(name, aliasname)
+#define _alias(name, aliasname) \
+      extern __typeof (name) aliasname __attribute__ ((alias (#name)));

```
The first being that it refused to compile otherwise with:
> hashmap.c: In function &#8216;mk_hmap&#8217;:
hashmap.c:44: error: request for member &#8216;lock&#8217; in something not a structure or union

The second being an old trick I learned from glibc.
All you need to do in the hashmap.c file is
```
alias(__hmap_add, hmap_add);
```
And then in the hashmap_public.h you can define the hmap_add like any normal function.
```
bool hmap_add(hashmap*, key, val);
```

Made a test program against it, and it seemed to work without fault/segmentation. :)


Compiling it this way:
```
gcc -fPIC -shared -Wl,-soname,libhashmap.so -lc -o libhashmap.so hashmap.c
```
Installing:
```
sudo install libhashmap.so /usr/local/lib && sudo ldconfig
```

And building a program against it:
```
gcc -lhashmap -lpthread mytestprog.c
```

Regards
Iain

PS:
A cleaner (or more cluttered) way would be to further divide the library down so that each function is in it's own file / it's own group file.
This saves it from the bloat of having too big a file to maintain, with the downside that it begins to fragment the library.

---

### Post by manualqr on 2009-07-26
Excellent post!
Thank you for fixing the semaphore bug!

I found another bug of mine in free_hmap.. The hashmap shouldn't be freed until we've released the semaphore lock! So here's what it should look like:
```

void free_hmap(hashmap* hmap) {
#ifdef HMAP_THREAD_SAFE
	sem_wait(&hmap->lock);
#endif

#ifdef HMAP_DESTRUCTORS
	static uint32_t it;
	for (it=0; it < hmap->size; ++it) {
		if (hmap->map[it].v != NULL) {
			hmap->del_fn(hmap->map[it].v);
		}
	}
#endif

	free(hmap->map);
	
#ifdef HMAP_THREAD_SAFE
	sem_post(&hmap->lock);
#endif

	free(hmap);
}

```

I have a question though.
In hashmap_public, I want to offer 2 macros so that programmers wont have to cast to key or val every time they use the functions. They used to be;

#define hmap_add(hmap, in, out) __hmap_add(&hmap, (key) in, (val) out)
#define hmap_get(hmap, in) __hmap_get(&hmap, (key) in)

Can I do something like this? Should I?

side note:
#pragma once is a header-guard macro, and it behaves just like #ifndef ** #define ** #endif. Without the mess ;)

---

### Post by nvteighen on 2009-07-27
> **manualqr said:**
> No, you were clear. I was just discussing how the code would be if I didn't make a public interface. If I did, __oa_hmap_add() would be static, and that would work well. But the macros cannot be in hashmap.h unless __hmap_add/get are there as well. The macros take a lot of pain out of using the code, so I want them available.

I smell a bad design issue related to a well-known C limitation. We all know the preprocessos macros are just text substitution (sometimes conditioned, sometimes not, etc.) done before the code is compiled.

Let's see, your code is compiled conditionally according to some macros. So, you set the macro's value at the header, include the header into the implementation module and you get a certain source code depending on that macro's value. Perfect. So, you can choose between a thread-safe version of your library and a thread-unsafe one, for example.

But here comes the issue. It seems that you want to give the user the ability to choose whether to have a thread-safe version or a thread-unsafe one and that's why you want those functions into the header, so the macros do their work at the **client code's compilation time**.

That's a disastrous idea. Putting code into a header might create conflicts with the client's code. Very simple: if some user creates a project with more than one module and uses your "header" in several modules, his code won't ever compile because the linker will complain about redefinition... Why? Let's see: file A.c and B.c include hashmap.h. Step 1): The preprocessor includes hashmap.h into the source code files. Step 2): The compiler produces the Assembly. Step 3): The assembler produces the object code. Step 4) The linker will put everything together an will notice there are two __hash_add functions, two __hash_get, etc.; the ones "copied" into A.c and the ones "copied" into B.c. When using headers correctly, this doesn't happen because you just include a prototype and the definition is linked from somewhere else.

(Remember, the inclusion guards protect the header to be included more than once into one certain source file, but they allow (and they have to) the same header to be included into different source files!)

Also, IMO, it's nonsense to use macros that way in C (but not in Lisp). Macros are designed to create the appropriate **source code** for different situations, not to condition the execution of something. The preprocessor macro language is not C, therefore, it doesn't affect runtime (in Lisp, instead, the macros are Lisp code... and using them to affect runtime is a very common technique).

> 
Converting everything to a provide a safe interface would really only make one function (__oa_hmap_add) unavailable at the cost of having two separate files. The guts of hashmap would be hidden as well, but at the cost of having to malloc it. 


Actually, you are already mallocing stuff inside your structures and you are already needing a destructor to avoid leaks. So I don't see any new cost by doing that... besides 4 additional bytes used for a new pointer you'll need.

> 
Call it an excuse for having bad design if you want, but I really believe that the Right Thing (tm) isn't the right thing in this case. I'm not worried about saving users from themselves, if they want to screw up the hashmap - they can go ahead. There's plenty of rope, and who am I to tell them to stop if they choose to hang themselves?


:) But actually, good design practices are for saving the developer from himself. All the encapsulation systems can be destroyed by the user by just putting a function pointer... even in the most OOP-obsessed languages. But also, in the case of libraries, you have to bring up a good design in order to provide a reasonably usable API.

Also, if you don't follow good practices in small stuff, whenever you have a bigger project in hands, you'll be really lost.

> **manualqr said:**
> 
side note:
#pragma once is a header-guard macro, and it behaves just like #ifndef ** #define ** #endif. Without the mess ;)

Yes, but there's an issue. **#pragma once** is not standard and there are compilers that doesn't support it. Moreover, in some cases programmers write whole preprocessor wrappers to detect what compiler it's being used in order to decide whether to use #pragma or not... which is kinda absurd, as the usual inclusion guard will always work.

That's where I wish the people devoted to the C standard had a look to Objective-C and adopt its "#import" system... :p There's no reason not to adopt a feature from a daughter language if it's good.

---

### Post by manualqr on 2009-07-28
> 
The linker will put everything together an will notice there are two __hash_add functions, two __hash_get, etc.; the ones "copied" into A.c and the ones "copied" into B.c.


Gah! I feel like an idiot!
To be honest when I read your post, I was thinking "no way the compiler will let that happen!". But then I tried compiling two files that included hashmap.h into a single binary and got linker errors - just as you foresaw..

I've made the changes that have been suggested, commented the source code better, fixed a couple little bugs, and added more out-of-the-box hash functions. The archive should be attached to my first post soon!

thanks for all the help!

---

### Post by nvteighen on 2009-07-28
Don't worry... we all have had this kind of errors :)

The current version looks really good now and it works! But, for some reason gcc complains (with -Wall flag, "activate all warnings") about this chunk of code in str_hash_fn:

```

while (c = *(unsigned char*)in++) { /* Line 199 */
	hash = ((hash << 5) + hash) + c;
}

```

The gcc warning:
```

hashmap.c: In function &#8216;str_hash_fn&#8217;:
hashmap.c:199: warning: suggest parentheses around assignment used as truth value

```

The solution is to put a pair of parentheses around the assignment clause... The reason is one of style but also clearer code: Use one single pair of parentheses when using conditional operators or stuff that directly returns a truth value, but two (or more) when you first want to execute something which then happens to have a truth value...

Again, it's style, so don't worry. Personally speaking, I hate assignments used as truth values... I prefer to write:
```

while (c != NULL) 
{ /* Yes, GNU style :P */
    c = *(unsigned char*)in++;
    hash = ((hash << 5) + hash) + c;
}

```

It's easier to read for me. Not even **while(c)**... I just like to have the stuff explicitly written, there, in front of my nose :)

---

### Post by manualqr on 2009-07-28
thanks for catching this.
I've made str_hash_fn decent and added a Makefile.

I'm feeling audacious enough to call this a '1.0' release =p

(updating first post soon)

---

