---
title: "Can't compile anything"
date: 2011-11-23
forum: Packaging and Compiling Programs
---

### Post by Jordanwb on 2011-11-23
I'm working a project which uses libjson, libconfig and libssl whose dev packages I've installed. I tried to compile it but the linker doesn't seem to be working right:

```
$gcc -std=c99 -ljson -lcrypto -lm -lconfig -lpthread -msse2 -Wall -O3 client.c -o client                                                                                                                                                                                        
client.c: In function ‘send_job_request’:                                                                                                                                                                                                                                      
client.c:262:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]                                                                                                                                                        
client.c:263:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]                                                                                                                                                        
client.c: In function ‘send_identification’:
client.c:241:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
client.c:242:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
/tmp/ccOGJFBj.o: In function `signal_handler':
client.c:(.text+0x71): undefined reference to `pthread_join'
/tmp/ccOGJFBj.o: In function `worker_thread':
client.c:(.text+0x7dc): undefined reference to `DES_fcrypt'
/tmp/ccOGJFBj.o: In function `send_identification':
client.c:(.text+0xab1): undefined reference to `json_object_new_object'
client.c:(.text+0xabe): undefined reference to `json_object_new_string'
client.c:(.text+0xad1): undefined reference to `json_object_object_add'
client.c:(.text+0xadb): undefined reference to `json_object_new_string'
client.c:(.text+0xaee): undefined reference to `json_object_object_add'
client.c:(.text+0xaf6): undefined reference to `json_object_get_string'
client.c:(.text+0xb32): undefined reference to `json_object_put'
client.c:(.text+0xb3a): undefined reference to `json_object_put'
client.c:(.text+0xb42): undefined reference to `json_object_put'
/tmp/ccOGJFBj.o: In function `send_job_request':
client.c:(.text+0xb91): undefined reference to `json_object_new_object'
client.c:(.text+0xb9e): undefined reference to `json_object_new_string'
client.c:(.text+0xbb1): undefined reference to `json_object_object_add'
client.c:(.text+0xbbc): undefined reference to `json_object_new_int'
client.c:(.text+0xbcf): undefined reference to `json_object_object_add'
client.c:(.text+0xbd7): undefined reference to `json_object_get_string'
client.c:(.text+0xc13): undefined reference to `json_object_put'
client.c:(.text+0xc1b): undefined reference to `json_object_put'
client.c:(.text+0xc23): undefined reference to `json_object_put'
/tmp/ccOGJFBj.o: In function `download_jobs':
client.c:(.text+0xcb6): undefined reference to `json_tokener_parse'
client.c:(.text+0xcd0): undefined reference to `json_object_object_get'
client.c:(.text+0xcd8): undefined reference to `json_object_get_string'
client.c:(.text+0xcff): undefined reference to `json_object_object_get'
client.c:(.text+0xd6e): undefined reference to `json_object_array_length'
client.c:(.text+0xd83): undefined reference to `json_object_array_get_idx'
client.c:(.text+0xdaf): undefined reference to `json_object_object_get'
client.c:(.text+0xdb7): undefined reference to `json_object_get_string'
client.c:(.text+0xdc8): undefined reference to `json_object_object_get'
client.c:(.text+0xdd0): undefined reference to `json_object_get_int'
client.c:(.text+0xde1): undefined reference to `json_object_object_get'
client.c:(.text+0xde9): undefined reference to `json_object_get_string'
client.c:(.text+0xeb5): undefined reference to `json_object_put'
client.c:(.text+0xee7): undefined reference to `config_destroy'
client.c:(.text+0xf2f): undefined reference to `config_destroy'
/tmp/ccOGJFBj.o: In function `start_jobs':
client.c:(.text+0x10e8): undefined reference to `pthread_create'
/tmp/ccOGJFBj.o: In function `main':
client.c:(.text.startup+0x3f): undefined reference to `config_init'
client.c:(.text.startup+0x50): undefined reference to `config_read_file'
client.c:(.text.startup+0x6c): undefined reference to `config_lookup_string'
client.c:(.text.startup+0x8a): undefined reference to `config_lookup_int'
client.c:(.text.startup+0xd4): undefined reference to `config_lookup_int'
client.c:(.text.startup+0x140): undefined reference to `config_lookup_int'
client.c:(.text.startup+0x1a9): undefined reference to `pthread_join'
client.c:(.text.startup+0x1f8): undefined reference to `config_destroy'
client.c:(.text.startup+0x256): undefined reference to `config_destroy'
collect2: ld returned 1 exit status
make: *** [client] Error 1
```

I had this problem on my laptop which was running 11.10 but not on my desktop which used to run 11.04. Right now both my desktop and laptop are running 12.04 :confused:

---

### Post by Bachstelze on 2011-11-23
We will need a sticky for this I think...

The correct command is

```
gcc -std=c99 -msse2 -Wall -O3 -o client client.c -ljson -lcrypto -lm -lconfig -lpthread
```

---

### Post by Jordanwb on 2011-11-23
I wonder why the order of arguments would make a difference, but it worked. Thanks

---

### Post by preetijpillai on 2012-10-25
It's because you needed to add in the libraries after -o option and not before..

---

