---
title: "ld returned 1 exit status"
date: 2016-02-15
forum: Programming Talk
---

### Post by m-i-cosacak on 2016-02-15
Hello,

I have checked for the "ld returned 1 exit status" problems, but I could not solve the problem. My problem is a below.

I am trying to install "[nexalign]("http://genome.gsc.riken.jp/osc/english/dataresource/")" on ubuntu 64 bit, but I have "ld returned 1 exit status". I have used nexalign several times years ago. However, whenever I use a new release of ubuntu I have this "ld returned 1 exit status". Any help would be really appreciated. 
Thanks. 
ilyas.

ubuntu release:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


ld returned 1 exit status:

...$ make
[PHP]gcc   -O9 -Wall -Dthread -c main.c
gcc   -O9 -Wall -Dthread -c mapping.c
gcc   -O9 -Wall -Dthread -c interface.c
interface.c: In function ‘interface’:
interface.c:64:8: warning: variable ‘format’ set but not used [-Wunused-but-set-variable]
  char *format = 0;
        ^
gcc   -O9 -Wall -Dthread -c input.c
input.c: In function ‘get_input_into_string’:
input.c:111:3: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
   fread(string,sizeof(char), i, file);
   ^
input.c: In function ‘read_types_list’:
input.c:435:3: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result [-Wunused-result]
   fscanf(file,"%s %s",param->types[i],param->type_colors[i]);
   ^
gcc   -O9 -Wall -Dthread -c sarray.c
gcc   -O9 -Wall -Dthread -c mem.c
gcc   -O9 -Wall -Dthread -c output.c
gcc   -O9 -Wall -Dthread -c pattern_searching.c
gcc   -O9 -Wall -Dthread -c pattern_searching_solid.c
gcc   -O9 -Wall -Dthread -c string_matching.c
gcc   -O9 -Wall -Dthread -c time.c
gcc   -O9 -Wall -Dthread -c misc.c
misc.c: In function ‘test_tag_index’:
misc.c:157:5: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
  if(!mer_hash[t>>5] & (1<<(t & 0x1F))){
     ^
misc.c:180:6: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
   if(!mer_hash[t>>5] & (1<<(t & 0x1F))){
      ^
gcc   -O9 -Wall -Dthread -c bt.c
gcc   -O9 -Wall -Dthread -c mapping_output.c
gcc   -O9 -Wall -Dthread -c hash.c
gcc   -O9 -Wall -Dthread -c r_output.c
gcc   -O9 -Wall -Dthread -c mapping_solid.c
gcc   -O9 -Wall -Dthread -c pattern_searching_short.c
gcc   -O9 -Wall -Dthread -c sort_mapping.c
gcc   -O9 -Wall -Dthread -c cluster_mapping.c
gcc   -O9 -Wall -Dthread -lpthread main.o mapping.o interface.o input.o sarray.o mem.o output.o pattern_searching.o pattern_searching_solid.o string_matching.o time.o misc.o bt.o mapping_output.o hash.o r_output.o mapping_solid.o pattern_searching_short.o sort_mapping.o cluster_mapping.o -o nexalign
mapping.o: In function `mapping':
mapping.c:(.text+0x23e): undefined reference to `pthread_create'
mapping.c:(.text+0x296): undefined reference to `pthread_join'
mapping.c:(.text+0x440): undefined reference to `pthread_create'
mapping.c:(.text+0x68e): undefined reference to `pthread_create'
mapping_solid.o: In function `mapping_solid':
mapping_solid.c:(.text+0x214): undefined reference to `pthread_create'
mapping_solid.c:(.text+0x25b): undefined reference to `pthread_join'
mapping_solid.c:(.text+0x40c): undefined reference to `pthread_create'
collect2: error: ld returned 1 exit status
Makefile:22: recipe for target 'all' failed
make: *** [all] Error 1

---

### Post by dwhitney67 on 2016-02-15
You are working with an old Makefile that is making a bad assumption regarding the ordering of object files versus that of shared-object libraries.  If your Makefile has a LIBS definition, ensure that it falls at the end of the final gcc statement.

For example, if all is working well, you should see something like this when you build everything:
```

gcc -O9 -Wall -Dthread main.o mapping.o interface.o input.o sarray.o mem.o output.o pattern_searching.o pattern_searching_solid.o string_matching.o time.o misc.o bt.o mapping_output.o hash.o r_output.o mapping_solid.o pattern_searching_short.o sort_mapping.o cluster_mapping.o -o nexalign **-lpthread**

```

---

### Post by steeldriver on 2016-02-15
Thankfully it appears to be a very simple Makefile - all that appears to be required is to swap the $(LD) variable with the corresponding $(OBJECTS)

```

$ diff Makefile{.bak,}
22c22
<     $(CC) $(CFLAGS) $(LD) $(OBJECTS) -o $(PROGS)
---
>     $(CC) $(CFLAGS) $(OBJECTS) $(LD) -o $(PROGS)
28c28
<     $(CC) $(THREADFLAGS) $(LD) $(THREADOBJECTS) -o $(THREADPROGS)
---
>     $(CC) $(THREADFLAGS) $(THREADOBJECTS) $(LD) -o $(THREADPROGS)
34c34
<     $(CC) $(DEBUGFLAGS) $(LD) $(DEBUGOBJECTS) -o $(DEBUGPROGS)    
---
>     $(CC) $(DEBUGFLAGS) $(DEBUGOBJECTS) $(LD) -o $(DEBUGPROGS)    

```

---

### Post by m-i-cosacak on 2016-02-15
Thank you very much. I just changed the $(LD) place in the MakeFile and it worked!

old -->   : all: $(OBJECTS) $(CC) $(CFLAGS) $(LD) $(OBJECTS) -o $(PROGS)

new --> : all: $(OBJECTS) $(CC) $(CFLAGS) $(OBJECTS) -o $(PROGS) $(LD)

best.

---

