---
title: "USB User Space Device Driver"
date: 2007-10-24
forum: Programming Talk
---

### Post by jvogel on 2007-10-24
I am new to Linux. I have been programming for over 15 years and at my new job I am to write a driver for a barcode reader attached to are system via USB.

The barcode reader registers as a keyboard device. We are looking to have more than one of these connected to the device at anyone time.

I am trying to write a user space device driver which will know, amoung other things, when a barcode reader is connected/disconnected to or from our unit, when and which device has scanned (read) a barcode, and to send messages to the barcode reader.

I have tried the usb_detach_kernel_driver_np and I seem to be connected to the device.  I am using the usb_interrupt_read call and when I press the button on the bar code reader/scanner the interrupt is triggered but the data that I am seeing is not correct infact it is the same for every bar code that I scan.

I look forward to any help that can be given to me and any other suggestions on how this can be done if not by a user space device driver.

Sincerely,
John Vogel
__

---

### Post by jvogel on 2007-10-26
Here is the code that I am trying to get to work.  When the interrupt is triggered and I print out the buffer it is the same values every time (mainly zero's).

#include <usb.h>
#include <string.h>
#include <stdio.h>
#include <asm/errno.h>
#include <stdlib.h>

#define KERNEL_USB
#define INTERRUPT_READ
#define DISPLAY_BUFFER

const int PRODUCT = 0x1200;
const int VENDOR = 0x05e0;

static struct usb_device *device_init(void)
{
	struct usb_bus *usb_bus;
	struct usb_device *dev;
	
	usb_init();
	usb_find_busses();
	usb_find_devices();

	printf("bus/device idVendor/idProduct\n");

	for ( usb_bus = usb_busses; usb_bus; usb_bus = usb_bus->next )
	{
		for ( dev = usb_bus->devices; dev; dev = dev->next )
		{
			if ( ( dev->descriptor.idVendor == VENDOR ) &&
					( dev->descriptor.idProduct == PRODUCT ) )
			{
				printf("Found Vendor 0x%04x Product 0x%04x.\n", dev->descriptor.idVendor, dev->descriptor.idProduct);
				
				print_configuration(dev->config);
				
				usb_dev_handle *udev;

				udev = usb_open(dev);
				return dev;
			}		
		}
	}
	return NULL;
}

int main(void)
{
	struct usb_device *dev;
	usb_dev_handle *usb_handle;
	int ret;
	char string[255];
	int i;
	int j;
	int retVal;
	char buffer[512];
	
	printf("Start Main 1\n");
	
	dev = device_init();
	if ( dev == NULL )
	{
		fprintf(stdout, "Eevice not found \n");
		goto bail;
	}

	printf("2 - Main\n");

	usb_handle = usb_open(dev);
	if ( usb_handle == NULL )
	{
		fprintf(stdout, "Could not open the device\n");
		goto bail;
	}
	else
	{
		if ( dev->descriptor.iManufacturer )
		{
			ret = usb_get_string_simple(usb_handle, dev->descriptor.iManufacturer, string, sizeof(string));
			if ( ret > 0 )
			{
				printf("2- Manufacturer: %s\n",string);
			}
			else
			{
				printf("2 - Failed to find Manufacturer\n");
			}
		}
		else
		{
			printf("2 - no dev descriptor iManufacturer\n");
		}
	}	

	printf("3 - Main\n");

	retVal = usb_detach_kernel_driver_np(usb_handle, 0);
	if ( retVal < 0 )
	{
		printf("Problem doing usb_detach_kernel_driver_nf %d value %s\n",retVal, strerror(-retVal));

		if ( retVal == -1 )
		{
			printf("Probably need to be ROOT USER\n");
			goto bail;
		}
		else
		{
			printf("The device might already be detached\n");
		}
	}
	else
	{
		printf("The result of usb_detach_kernel_driver_np is %d value %s.\n",retVal, strerror(retVal));
	}

	printf("6 - Main\n");

	int configuration = dev->config->bConfigurationValue;

	printf("CONFIGURATION value is 0x%08x\n",configuration);
			
	ret = usb_set_configuration(usb_handle, configuration);

	if(ret < 0)
	{
		printf("Failed to set config 1: %d EBUSY: %d ENOMEM: %d\n", ret, EBUSY, ENOMEM);
		printf("string value of failed config is: %s\n",strerror(-ret));
		goto bail;
	}
	else
	{
		printf("HAVE SET the configuration %d value %s\n",ret, strerror(ret));
	}
		

	printf("9 - Main\n");
		
	// this was after the usb_set_configuration but I saw an example were it came 
	// after so I thought I would give it a try.

	int interfaceNumber = dev->config->interface->altsetting->bInterfaceNumber;
	printf("\nINTERFACE NUMBER VALUE 0x%08x\n",interfaceNumber);

	ret = usb_claim_interface(usb_handle, interfaceNumber);
	if(ret < 0)
	{
		printf("Failed to claim interface 0: %d EBUS: %d ENONM: %d %s\n", ret, EBUSY, ENOMEM, strerror(-ret));
		goto bail;
	}
	else
	{
		printf("Have claimed the usb configuration %d value %s\n",ret, strerror(ret));
	}


	printf("10 - Main\n");
		

	i = 1;

	int endPoint = dev->config->interface->altsetting->endpoint->bEndpointAddress;
	printf("\nEND POINT VALUE 0x%08x\n",endPoint);

	for ( ret = 0; ret < 512; ret++ )
		buffer[ret] = 0x31;
	ret = 0;


	ret = usb_interrupt_read(usb_handle, endPoint, buffer, 160, 5000000);

	if ( ret < 0 )
	{
		printf("Failure usb_interrupt_read  %d '%s'\n", ret, strerror(-ret));
		goto nextTest;
	}

	printf("11 - Main\n");
	
	printf("%04x Read %d bytes: \n", i, ret);
			
	printf(" 0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F\n");
	for(j = 0; j < ret; j++)
	{
		printf("%02x ", ((int)buffer[j] & 0x0ff));
		if ( !( (j + 1 ) % 16 ) )
			printf("\n");
	}
	printf("\n");

	printf("*** 12 - MAIN");

nextTest:
bail:
	
	retVal = usb_clear_halt(usb_handle, endPoint);
	if ( retVal < 0 )
		printf("FAIL CLEAR HALT return %d value %s\n",retVal, strerror(-retVal));
	else		
		printf("Clear Halt device return %d value %s\n",retVal, strerror(retVal));
	printf("13 - Main\n");

	ret = usb_release_interface(usb_handle, interfaceNumber);
	if ( ret < 0 )
	{
		printf("Error in usb_release_interface return value %d string %s\n",ret, strerror(-ret));
	}
	else
	{
		printf("GOOD RETURN usb_release_interface return value %d string %s\n",ret, strerror(-ret));
	}
	
	printf("14 - Main\n");
	
	ret = usb_close(usb_handle);
	if ( ret < 0 )
	{
		printf("Error in usb_close return value %d string %s\n",ret, strerror(-ret));
	}
	else
	{
		printf("GOOD RETURN FROM usb_close return value %d string %s\n",ret, strerror(-ret));
	}
		

	
	printf("15 - Main\n");
	
	return 0;
}

Any help that anyone can give would be appreciated.

John V.

---

### Post by moma on 2007-10-26
Really nice thing jvogel, but
can you edit your posting and use the CODE-tags around the code so it becomes readable.  Copy the original code into it.
Add also info about how to compile your code and if there are dependencies to external libraries (packages) ;-)

---

