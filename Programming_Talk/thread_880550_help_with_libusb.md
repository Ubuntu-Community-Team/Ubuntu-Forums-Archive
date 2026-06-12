---
title: "help with libusb"
date: 2008-08-05
forum: Programming Talk
---

### Post by nickbarnes on 2008-08-05
I am a complete beginner to programming on Linux.  I am trying to use USB bulk transfer, but am getting nowhere fast.

I am using Ubuntu 8.04 Hardy Heron, and libusb 0.1.12.  My code is as follows.  It seems to successfully open the device, obtains a vendor id and product id which matches the “8086 - 9890" I check for.  But when I call usb_detach_kernel_driver_np(udev, 0) I get a -1 error.

My questions are
1.	Are my API calls in the correct order?
2.	What is the “interface” parameter (2nd parameter) in the usb_detach_kernel_driver_np() call?
3.	Where do I find detailed descriptions of what the parameters mean – I’ve tried the libusb developers guide ([http://libusb.sourceforge.net/doc/function.usbdetachkerneldrivernp.html](http://libusb.sourceforge.net/doc/function.usbdetachkerneldrivernp.html)), but it seems sadly lacking in detail.
4.	usb_detach_kernel_driver_np() returns -1.  From the libusb guide I can see that this is an error, but what error?  Where do I find a definition of the error codes from?

I feel that I’m missing the obvious somewhere – can’t see the wood for the trees.  Where should I be looking for answers to these kind of simple questions?

Many thanks
Nick

 int print_device(struct usb_device *dev, int level)
{
	usb_dev_handle *udev;
	char description[256];
	char string[256];
	int ret, i;

	udev = usb_open(dev);
	if (udev)
	{
		if (dev->descriptor.iManufacturer)
		{
			ret = usb_get_string_simple(udev, dev->descriptor.iManufacturer, string, sizeof(string));
			if (ret > 0)
				snprintf(description, sizeof(description), "%s - ", string);
			else
				snprintf(description, sizeof(description), "%04X - ",
						dev->descriptor.idVendor);
		}
		else
			snprintf(description, sizeof(description), "%04X - ",
					dev->descriptor.idVendor);

		if (dev->descriptor.iProduct)
		{
			ret = usb_get_string_simple(udev, dev->descriptor.iProduct, string, sizeof(string));
			if (ret > 0)
				snprintf(description + strlen(description), sizeof(description) -
						strlen(description), "%s", string);
			else
				snprintf(description + strlen(description), sizeof(description) -
						strlen(description), "%04X", dev->descriptor.idProduct);
		}
		else
			snprintf(description + strlen(description), sizeof(description) -
					strlen(description), "%04X", dev->descriptor.idProduct);

	}
	else
		snprintf(description, sizeof(description), "%04X - %04X",
				dev->descriptor.idVendor, dev->descriptor.idProduct);

	printfDebug("%.*sDev #%d: %s\n", level * 2, "                    ", dev->devnum,
	             description);

	if(!strcmp(description, "8086 - 9890"))
	{
		int myret = usb_detach_kernel_driver_np(udev, 0);

		myret = usb_claim_interface(udev, 0);

		if(myret >= 0)
		{
			myret = usb_bulk_write(udev, 1, "\x2\x8\0\0\x3", 5, 100);

			myret = usb_release_interface(udev, 1);
		}
	}
	if (udev)
		usb_close(udev);

	for (i = 0; i < dev->num_children; i++)
		print_device(dev->children[i], level + 1);

	return 0;
}

---

### Post by nickbarnes on 2008-08-05
I now understand that a -1 error is an -EPERM error - ie a not permitted error, because the user has not got sufficient rights, thanks to [http://aplawrence.com/Unixart/errors.html](http://aplawrence.com/Unixart/errors.html).

This raises the further question - what do I do about this lack of rights.  Does it mean that 
1. the whole program should be run as root?
2. is there a means of doing an equivalent of a sudo, within the program?

Nick

---

### Post by Zugzwang on 2008-08-05
The usual approach to have a daemon running in the background that performs all this communications with the usb device. That daemon is being run as root (or better: put into a separate group that is allowed to access the usb stuff). If your program has any user interaction, then you write a program running from a normal user account communicating with the daemon.

There may be other ways of doing this.

---

### Post by nickbarnes on 2008-08-06
I want to write a user space program.  Isn't there a usb daemon provided with Ubuntu?

Am I right in concluding that a -1 error, returned by usb_set_configuration and usb_claim_interface, is a -EPERM?  I now wonder if it simply indicates that there is no usb driver to communicate with.  In fact I started out using libusb because I thought that it would provide this for me.

Nick

---

### Post by cszikszoy on 2008-08-06
Most programs I've seen that use libusb always require you to be root.  I would suggest doing what Zugzwang said.

It shouldn't be hard to make a small usb daemon, and have it receive commands through DBUS with the UI part of the program.

---

### Post by nickbarnes on 2008-08-07
Ok, so thanks for that.  In due course I'll split a daemon off and run that as root.  But for now (for test purposes only) I'm running the whole thing as root, and it moves me on a little bit. I now get the manufacturer and product strings back from the device, and when I do the usb_set_configuration, it returns ok.  However, I am still getting an error (though a different error) when I call usb_claim_interface(udev, 0). I now get back a -2 error (No such file or directory). What file is it looking for?
 
Many thanks,
Nick
 
int print_device(struct usb_device *dev, int level)
{
    usb_dev_handle *udev;
    char description[256];
    char string[256];
    int ret, i;
 
    udev = usb_open(dev);
    if (udev)
    {
        if (dev->descriptor.iManufacturer)
        {
            ret = usb_get_string_simple(udev, dev->descriptor.iManufacturer, string, sizeof(string));
            if (ret > 0)
                snprintf(description, sizeof(description), "%s - ", string);
            else
                snprintf(description, sizeof(description), "%04X - ",
                        dev->descriptor.idVendor);
        }
        else
            snprintf(description, sizeof(description), "%04X - ",
                    dev->descriptor.idVendor);
 
        if (dev->descriptor.iProduct)
        {
            ret = usb_get_string_simple(udev, dev->descriptor.iProduct, string, sizeof(string));
            if (ret > 0)
                snprintf(description + strlen(description), sizeof(description) -
                        strlen(description), "%s", string);
            else
                snprintf(description + strlen(description), sizeof(description) -
                        strlen(description), "%04X", dev->descriptor.idProduct);
        }
        else
            snprintf(description + strlen(description), sizeof(description) -
                    strlen(description), "%04X", dev->descriptor.idProduct);
 
    }
    else
        snprintf(description, sizeof(description), "%04X - %04X",
                dev->descriptor.idVendor, dev->descriptor.idProduct);
 
    printfDebug("%.*sDev #%d: %s\n", level * 2, " ", dev->devnum,
     description);
 
    if(dev->descriptor.idVendor == 0x8086 &&
     dev->descriptor.idProduct == 0x9890) //mp printer
    {
        //this an attempt to detach it from a kernel driver so that
        //it can be accessed by user space programs. If you get
        //an error, don't worry about it. It is probably just that
        //it wasn't attached in the first place
        int myret = usb_detach_kernel_driver_np(udev, 0);
 
        if(0 > (myret = usb_set_configuration(udev, 0)))
            perror("USB SET CONFIGURATION");
 
[COLOR=red]        if(0 > (myret = usb_claim_interface(udev, 0)))[/COLOR]            
          perror("USB CLAIM INTERFACE");
 
        if(myret >= 0)
        {
            myret = usb_bulk_write(udev, 0, "\x2\x8\0\0\x3", 5, 100);
 
            myret = usb_release_interface(udev, 0);
        }
    }
    if (udev)
        usb_close(udev);
 
    if (verbose)
    {
        if (!dev->config)
        {
            printfDebug(" Couldn't retrieve descriptors\n");
            return 0;
        }
 
        for (i = 0; i < dev->descriptor.bNumConfigurations; i++)
            print_configuration(&dev->config[i]);
    }
    else
    {
        for (i = 0; i < dev->num_children; i++)
            print_device(dev->children[i], level + 1);
    }
 
    return 0;
}

---

### Post by Zugzwang on 2008-08-07
> **nickbarnes said:**
> [...] However, I am still getting an error (though a different error) when I call usb_claim_interface(udev, 0). I now get back a -2 error (No such file or directory). What file is it looking for?

What makes you think that "-2" means "No such file or directory"? According to [this]("http://libusb.sourceforge.net/doc/function.usbclaiminterface.html") manual page, there are only the return codes "Device Busy" and "Not enough memory". I'm guessing that there's already another driver using that device which you might have to deactivate first.

---

### Post by nickbarnes on 2008-08-07
When I step inside usb_claim_interface, it makes an ioctl call, which is what generates the -2.  Looking in a table of Linux errors (eg [http://aplawrence.com/Unixart/errors.html](http://aplawrence.com/Unixart/errors.html)), I find that this is ENOENT 2 "No such file or directory".  Also my call to perror gives "the same message.  

If in contrast you take the libusb statement as gospel, what values are these two errors "Device Busy" and "Not enough memory", they mention?  I think that they should be -16 and -12 respectively

Nick

---

### Post by cszikszoy on 2008-08-07
I think what you posted are general UNIX errors.  Programs can have their own error codes.  I could write my own program and have it return error -2 under whatever condition I want.

What I'm saying is, there isn't really a standard for error numbers across all unix/linux programs.  Look at the actual man page for the program that returned the error for information about what that error means.

---

### Post by nickbarnes on 2008-08-07
You are right, of course.  You can return anything you like from a program, but it isn't very good practice.  At the moment I can't prove it one way or the other, because there are no man pages for either ioctl or usb_claim_interface, and though the libusb documentation tells you that it can return busy or insufficient memory, it does not tell you what values those errors are.  Anyone know where this info is?

thanks, Nick

---

### Post by Zugzwang on 2008-08-07
Hmmm, it looks like the documentation is a little bit incomplete here. Try calling "usb_set_debug(3)" before the execution of the rest of your commands and see if you get any additional information.

Just found another thread on the same problem: [http://www.nabble.com/usb_claim_interface-fail-errno%3D-2-td17792140.html]("http://www.nabble.com/usb_claim_interface-fail-errno%3D-2-td17792140.html"). Maybe that helps.

---

### Post by nickbarnes on 2008-08-07
Thanks for that.  I now get an additional error message "USB error: could not claim interface 0: No such file or directory".  I am looking into that other thread, which as you say, sounds very relevant.

ta, Nick

---

### Post by dwhitney67 on 2008-08-07
> **nickbarnes said:**
> ...
Am I right in concluding that a -1 error, returned by usb_set_configuration and usb_claim_interface, is a -EPERM?
...

If you want error code, include <errno.h>, then reference the value of the global variable 'errno'.  If you want the English version of the error, use strerror().

For example:
[PHP]#include <errno.h>
#include <string.h>
...
if ( Clibfunc() == -1 )
{
  // be careful not to call anything else here, as that might change
  // the value of errno.
  const char *error = strerror(errno);
  printf( "%s\n", error );
}
...[/PHP]

---

### Post by nickbarnes on 2008-08-07
I have yet another output message now "No such file or directory".

Nick

---

### Post by nickbarnes on 2008-08-07
I have also tried Xiang's usb_get_driver_np.  It returns -61 (No data available) and consequently does not attempt the detach_kernel_driver_np anymore.  What it is saying is that there is not another driver already loaded.  This makes sense, because the device concerned is proprietry and has never been used for linux, so there is no existing driver for it.

thanks, Nick

---

### Post by nickbarnes on 2008-08-11
Hello chaps

Have solved my problems
1. problem 1 was that I needed write access to the files in /dev/bus/usb.  If I chmod this it works, but reverts back to read only on reboot, so put chmod o+w -R /dev/bus/usb into /etc/init.d/rc shell script
2. problem 2 was that I needed the right configuration in my call to usb_set_configuration.  I needed to do lsusb -v and read the bConfigurationValue for my device and use this as the 2nd param in the call.

Having done these two simple things, I was able to claim my interface and do my bulk write to end point 1.

thanks to all
Nick

---

### Post by gfine on 2008-08-13
You need to do a usb_detach_kernel_driver_np( udev, interface); before the usb_claim_interface.  The reason, I have read, is that the kernel has claimed the interface, and it has to be detached before the process claims it.

G

---

### Post by gfine on 2008-08-14
My apologies.  I read back a page and see you did use detach_kernel_driver_np .  

I had similar problems with usb_claim_interface, and it was solved via the detach.  

Your solution is plausible, and should work.  Next time I'll read a bit more before sticking my foot in my mouth. 

G

---

### Post by mooselix on 2008-08-19
I didn't have to modify my /dev/bus/usb permissions - not sure why. 

Here's what I hacked up to successfully claim my interface:
```

...

usb_dev_handle * open_and_claim(struct usb_device *dev, int interface) {

  usb_dev_handle *dh;
  int res;

  dh = usb_open(dev);
	
  if(dh == NULL) {
    printf("Could not open device: %s\n", usb_strerror());
    return NULL;
  }

#if defined(LIBUSB_HAS_GET_DRIVER_NP)
#if defined(LIBUSB_HAS_DETACH_KERNEL_DRIVER_NP)
  char *name[256];
  if (usb_get_driver_np(dh, interface, (char *) name, sizeof(name)) == 0)
  {
    if (usb_detach_kernel_driver_np(dh, interface) < 0)
    {
      printf("%s\n", usb_strerror());
      return NULL;
    }
    usb_set_altinterface(dh, interface);
  }
#endif
#endif
	
  res = usb_claim_interface(dh, interface);
	
  if(res != 0) {
    printf("%s\n", usb_strerror());
    return NULL;
  }

  return dh;
}

...

```

I'm not sure the above is complete or well coded, but I hope it helps.

---

