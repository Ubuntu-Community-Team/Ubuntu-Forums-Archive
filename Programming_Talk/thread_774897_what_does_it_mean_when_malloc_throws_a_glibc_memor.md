---
title: "what does it mean when malloc throws a glibc memory corruption error?"
date: 2008-04-29
forum: Programming Talk
---

### Post by themoebius on 2008-04-29
This is really pissing me off. I've narrowed my bug down to this single line - malloc is actually crashing and it says that memory is corrupted. There is no threading going on.

*** glibc detected *** ./mapper_test: malloc(): memory corruption: 0x08089060 ***

This is the line causing it:
(float *) malloc(1100*1100*sizeof(float));

Here is the source code of the relevant function and the full backtrace. Some stuff doesn't make sense because I've been changing it around a little to be able to narrow it down as much as possible.
```

// send a request for a gridmap
int mapper_get_gridmap(carmen_map_t *client_map) {
	IPC_RETURN_TYPE err;
	static carmen_gridmap_request_message *query;
	static mapper_grid_map_message *response;
	unsigned int timeout = 10000;
	int i;
	int uncompress_return;
	uLong uncompress_size;
	uLong uncompress_size_result;
	
	client_full_map_request = 1;

	err = IPC_defineMsg(MAPPER_GRIDMAP_REQUEST_NAME, IPC_VARIABLE_LENGTH,
						CARMEN_DEFAULT_MESSAGE_FMT);
	carmen_test_ipc_exit(err, "Could not define message", MAPPER_GRIDMAP_REQUEST_NAME);
	
	//printf("Creating default carmen message\n");
	//fflush(stdout);
	
	query = carmen_default_message_create();
	
	err = IPC_queryResponseData(MAPPER_GRIDMAP_REQUEST_NAME, query,
								(void **)&response, timeout);
	
	if (err != IPC_OK) {
		carmen_test_ipc(err, "Could not get map_request", 
		MAPPER_GRIDMAP_REQUEST_NAME);
		carmen_warn("\nDid you remember to start the mapper?\n");
		fflush(stdout);
		return -1;
	}
	
	if (response->size == 0) {
		carmen_warn("Error receiving map: %s\n", response->err_mesg);
		fflush(stdout);
		return -1;
	}
	
	//mapper_dump_gridmap_msg(response);
	printf("mapper_get_gridmap: response %ix%i, local: %ix%i\n",
			response->config.x_size, response->config.y_size,
			client_map->config.x_size, client_map->config.y_size);
	
	//make sure we weren't passed a null pointer
	if (client_map != NULL) {
		//if the map changed size on us
		if (client_map->config.x_size != response->config.x_size ||
			client_map->config.y_size != response->config.y_size) 
		{
			printf("mapper_get_gridmap: resizing map to %ix%i\n", response->config.x_size, response->config.y_size);
			fflush(stdout);
			//if (client_map->complete_map) free(client_map->complete_map);
			//if (client_map->map) free(client_map->map);
			
			client_map->complete_map = (float *) malloc(
					response->config.x_size * response->config.y_size * sizeof(float));
			carmen_test_alloc(client_map->complete_map);
			
			//init map
			for (i=0; i < response->config.x_size * response->config.y_size; ++i)
				client_map->complete_map[i] = 0.25;
			
			client_map->map = (float **) calloc(response->config.y_size, sizeof(float *));
			carmen_test_alloc(client_map->map);
			//each element in the map array references the first element in the corresponding
			//row in complete_map
			for (i = 0; i < response->config.x_size; i++)
				client_map->map[i] = client_map->complete_map + i*response->config.x_size;
			
			client_map->config = response->config;
			
			printf("mapper_get_gridmap: resized to %ix%i\n", client_map->config.x_size, client_map->config.y_size);
			fflush(stdout);
		}
		
		client_map->config = response->config;
		
		if (response->compressed) {
			
			
			uncompress_size = client_map->config.x_size * client_map->config.y_size * sizeof(float);
			uncompress_size_result = uncompress_size;
			printf("mapper_get_gridmap: sizes should be uncompressed %li compressed %i",
					uncompress_size, response->size);
			fflush(stdout);
			//client_map->complete_map = 
			(float *) malloc(1100*1100*sizeof(float));
			carmen_test_alloc(client_map->complete_map);
			uncompress_return = uncompress((void *)client_map->complete_map,
					&uncompress_size_result, (void *)response->map, response->size);
			//for (i=0; i<client_map->config.x_size * client_map->config.y_size; ++i)
			//	client_map->complete_map[i] = 0.25;
		} else {
			memcpy(client_map->complete_map, response->map, response->size);
		}
		
		printf("mapper_get_gridmap: copied map\n");
		fflush(stdout);
		
		client_seq_num = response->seq_num + 1;
		
		ref_x = response->ref_x;
		ref_y = response->ref_y;
	}
	
	
	//if (response->map)
	//	free(response->map);
	
	//free(response);

	printf("mapper_get_gridmap: freed response\n");
	fflush(stdout);
	
	client_full_map_request = 0;
	
	return 0;
}

```

```

zac@zac-laptop:~/workspace/Paradroid/src/mapper$ ./mapper_test 
CARMEN - Carnegie Mellon Robot Navigation Toolkit - Version 0.7.0

Connected to carmen, subscribing to map messages... done.Listening...

mapper_interface: WARNING: invalid fragment coordinates - requesting new map
                         pin_x: 334 pin_y: 114 width: 418 height: 229 x_size: 418 y_size: 229
mapper_get_gridmap: response 900x700, local: 0x0
mapper_get_gridmap: resizing map to 900x700
mapper_get_gridmap: resized to 900x700
mapper_get_gridmap: sizes should be uncompressed 2520000 compressed 13220*** glibc detected *** ./mapper_test: malloc(): memory corruption: 0x08089060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7dc6356]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7dc7cad]
./mapper_test[0x804a9c2]
./mapper_test[0x804a065]
./mapper_test[0x805302a]
./mapper_test[0x805d6d8]
./mapper_test[0x805dc8b]
./mapper_test[0x804e23b]
./mapper_test[0x804bffa]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d70450]
./mapper_test[0x8049c21]
======= Memory map: ========
08048000-08074000 r-xp 00000000 08:03 704679     /home/zac/workspace/Paradroid/src/mapper/mapper_test
08074000-08075000 rw-p 0002c000 08:03 704679     /home/zac/workspace/Paradroid/src/mapper/mapper_test
08075000-080a5000 rw-p 08075000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0 
b7921000-b7a00000 ---p b7921000 00:00 0 
b7af1000-b7d5a000 rw-p b7af1000 00:00 0 
b7d5a000-b7ea3000 r-xp 00000000 08:03 508431     /lib/tls/i686/cmov/libc-2.7.so
b7ea3000-b7ea4000 r--p 00149000 08:03 508431     /lib/tls/i686/cmov/libc-2.7.so
b7ea4000-b7ea6000 rw-p 0014a000 08:03 508431     /lib/tls/i686/cmov/libc-2.7.so
b7ea6000-b7eaa000 rw-p b7ea6000 00:00 0 
b7eaa000-b7ebe000 r-xp 00000000 08:03 771288     /usr/lib/libz.so.1.2.3.3
b7ebe000-b7ebf000 rw-p 00013000 08:03 771288     /usr/lib/libz.so.1.2.3.3
b7ebf000-b7ee2000 r-xp 00000000 08:03 508934     /lib/tls/i686/cmov/libm-2.7.so
b7ee2000-b7ee4000 rw-p 00023000 08:03 508934     /lib/tls/i686/cmov/libm-2.7.so
b7ef0000-b7efa000 r-xp 00000000 08:03 475204     /lib/libgcc_s.so.1
b7efa000-b7efb000 rw-p 0000a000 08:03 475204     /lib/libgcc_s.so.1
b7efb000-b7eff000 rw-p b7efb000 00:00 0 
b7eff000-b7f00000 r-xp b7eff000 00:00 0          [vdso]
b7f00000-b7f1a000 r-xp 00000000 08:03 475175     /lib/ld-2.7.so
b7f1a000-b7f1c000 rw-p 00019000 08:03 475175     /lib/ld-2.7.so
bfcbe000-bfcd3000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

---

### Post by themoebius on 2008-04-29
Ohhhhh. I think what was happening is the the memory allocation table for my process was being overwritten by a loop a few lines above, which meant that when malloc tried to allocate more memory it got confused to say the least.

swap this line
for (i = 0; i < response->config.x_size; i++)
with this line
for (i = 0; i < response->config.y_size; i++)

---

### Post by stroyan on 2008-04-29
A glibc memory corruption error usually means that your code overwrote some of the memory
between the allocated ranges handed to you by malloc or calloc (or realloc).
It can also be caused by continuing to access memory that you have freed,
or freeing the same address twice, or freeing an address you never allocated.

In your example code you have
```

    client_map->map = (float **) calloc(response->config.y_size, sizeof(float *));
    carmen_test_alloc(client_map->map);
    //each element in the map array references the first element in the corresponding
    //row in complete_map
    for (i = 0; i < response->config.x_size; i++)
	    client_map->map[i] = client_map->complete_map + i*response->config.x_size;

```

That allocates response->config.y_size times sizeof(float *)
But it writes to an index of response->config.x_size of type (float *).
(That is assuming map is a float**.  You cast to that but don't show the type declarations.)
Some of your output shows x=900 and y=700.
So you went past the end of the client_map->map area that you got from calloc.

But you found that while I was typing. :-)
Check your other loops for x vs y as well.
You seem to have some x * x offset computations in there.

---

