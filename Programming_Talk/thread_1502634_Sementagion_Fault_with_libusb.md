---
title: "Sementagion Fault with libusb"
date: 2010-06-05
forum: Programming Talk
---

### Post by Kerubu on 2010-06-05
OK I expect this is something I am doing wrong but the following gives a segmentation fault in the displayDevice() function:

```
#include <stdlib.h>
#include <stdio.h>
#include <libusb-1.0/libusb.h>

void displayDevice(libusb_device *dev);

int main(int argc, char **argv)
{
	struct libusb_context *context;
	int result;
	libusb_device **list;
	libusb_device *found = NULL;
	ssize_t cnt;
	ssize_t i = 0;
	int err = 0;
	
	result = libusb_init(&context);
	if (result != 0){
		printf("libusb not initialised.\n");
	} else {
	/* Success */
		printf("libusb successfully initialised.\n");
		// discover devices
		cnt  = libusb_get_device_list(NULL, &list);
		if (cnt < 0){
			printf("Count less than 0.\n");
		} else {
			for (i = 0; i < cnt; i++) {
			    //libusb_device *device = list[i];
			    displayDevice(list[i]);		    
			}
		}

		libusb_free_device_list(list, 1);

		printf("De-activating libusb.\n");
		libusb_exit(context);
	}
	exit(0);	
}

void displayDevice(libusb_device *device){
	int result;
	struct libusb_device_descriptor  *ptr_desc;
	char usbver1[] = "Version 1\0";
	char usbver2[] = "Version 2\0";
	char *ptr_char;
	//ptr_desc = &desc;
	
	result = libusb_get_device_descriptor(device,ptr_desc); 
	if (result != 0){
		printf("Could not get device descriptor.\n");
	} else {
		/* Success */
		printf("Device descriptor retrieved.\n");
		if (ptr_desc->bcdUSB == 0x200){
			ptr_char = usbver2;
		}else{
			ptr_char = usbver1;
		}
		printf("%s\n",ptr_char);
				
	}
	free(ptr_desc);
	return;
}
```

Now the line :

libusb_get_device_descriptor(device,ptr_desc)

ptr_desc is a pointer to a device descriptor memory for which is allocated by the above function. However when displayDevice returns there is a segmentation fault and it is something to do with the the device descriptor.

If for example I create LOCAL struct of the device descriptor and pass it to the function then all is ok, the struct is on the stack.

Am I supposed to allocate the memory for the function because the free() function doesn't seem to help and the docs in libusb don't say whether the calling function is responsible for memory release.

Your help appreciated.

---

### Post by dwhitney67 on 2010-06-05
Declare the descriptor on the stack (or allocate it if you wish).  At a minimum, this should work:
```

struct libusb_device_descriptor desc;

...

result = libusb_get_device_descriptor(device, &desc);

```
Btw, oftentimes it is a bad idea to preface variable names with a description of their type (eg. ptr_desc).  This style of programming is referred to as [Hungarian Notation]("http://en.wikipedia.org/wiki/Hungarian_notation"), and it's practice died long ago, even at M$.  If after you make the change to your code as shown above, hopefully the reason to avoid HN will be apparent.

---

### Post by soltanis on 2010-06-05
Echoing dwhitney here, but apparently your function doesn't actually allocate the storage for that structure. Which means you have to do it. If it was, then you wouldn't be segmentation faulting because your pointer wouldn't be misbehaving.

Declare the variable in automatic memory or use **malloc**(3).

If you want to be really sure, gdb your program and trace through into the libusb_get_device_descriptor call and inspect your pointer and the data it points to. To make this easier (and to make future pointer mistakes easier to catch instead of having them creep up on you) initialize that pointer to NULL when you declare it.

---

### Post by Kerubu on 2010-06-06
> **dwhitney67 said:**
> Declare the descriptor on the stack (or allocate it if you wish).  At a minimum, this should work:
```

struct libusb_device_descriptor desc;

...

result = libusb_get_device_descriptor(device, &desc);

```
Btw, oftentimes it is a bad idea to preface variable names with a description of their type (eg. ptr_desc).  This style of programming is referred to as [Hungarian Notation]("http://en.wikipedia.org/wiki/Hungarian_notation"), and it's practice died long ago, even at M$.  If after you make the change to your code as shown above, hopefully the reason to avoid HN will be apparent.

Thanks dwhitney76,

Yes this does work when I declare a structure locally in my function displayDevice() however I'm not entirely sure whether I should be allocating the memory for it or the function libusb_get_device_descriptor() (Which is in libusb).

From libusb website :
[http://libusb.sourceforge.net/api-1.0/group__desc.html]("http://libusb.sourceforge.net/api-1.0/group__desc.html")

> int libusb_get_device_descriptor  	(  	libusb_device  *   	 dev,
		struct libusb_device_descriptor *  	desc	 
	) 			

Get the USB device descriptor for a given device.

This is a non-blocking function; [B]the device descriptor is cached in memory.
[/B]
Parameters:
    	dev 	the device
    	desc 	output location for the descriptor data

Returns:
    0 on success or a LIBUSB_ERROR code on failure 



It's not entirely clear to me who should allocate the memory for the descriptor especially because it says the device descriptor is cached in memory.

---

### Post by dwhitney67 on 2010-06-06
> **Kerubu said:**
> 
It's not entirely clear to me who should allocate the memory for the descriptor especially because it says the device descriptor is cached in memory.

It is your application that must provide the allocation for the descriptor.  Here are your two choices, where one is a repeat from earlier:

Choice #1:
```

struct libusb_device_descriptor desc;

...

result = libusb_get_device_descriptor(device, **&desc**);

```
Choice #2:
```

struct libusb_device_descriptor* desc = malloc(sizeof(struct libusb_device_descriptor));

...

result = libusb_get_device_descriptor(device, **desc**);

...

free(desc);

```
The term "[cache]("http://en.wikipedia.org/wiki/Cache")" is used to indicate that the library will store (ie remember) the last request for a descriptor.  Basically it implies that it is storing the descriptor in memory (or within a static variable).  This is useful for subsequent operations in which there may be a need to reference this same descriptor, without requiring the need to lookup/create the descriptor again.

Honestly though, I haven't a clue what the libusb stuff is doing internally, thus for all I know it doesn't store anything and the documentation is merely has a typo.

---

### Post by Kerubu on 2010-06-06
> **dwhitney67 said:**
> It is your application that must provide the allocation for the descriptor.  Here are your two choices, where one is a repeat from earlier:

Choice #1:
```

struct libusb_device_descriptor desc;

...

result = libusb_get_device_descriptor(device, **&desc**);

```
Choice #2:
```

struct libusb_device_descriptor* desc = malloc(sizeof(struct libusb_device_descriptor));

...

result = libusb_get_device_descriptor(device, **desc**);

...

free(desc);

```
The term "[cache]("http://en.wikipedia.org/wiki/Cache")" is used to indicate that the library will store (ie remember) the last request for a descriptor.  Basically it implies that it is storing the descriptor in memory (or within a static variable).  This is useful for subsequent operations in which there may be a need to reference this same descriptor, without requiring the need to lookup/create the descriptor again.

Honestly though, I haven't a clue what the libusb stuff is doing internally, thus for all I know it doesn't store anything and the documentation is merely has a typo.

Thanks dwhitney67. It makes sense now :)

---

