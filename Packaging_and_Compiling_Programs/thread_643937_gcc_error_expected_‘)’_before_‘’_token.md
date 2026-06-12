---
title: "gcc error: expected ‘)’ before ‘*’ token"
date: 2007-12-18
forum: Packaging and Compiling Programs
---

### Post by g.a. on 2007-12-18
Hi,

I get a gcc error when trying to compile some example code of a usb device. I'm using kubuntu 7.10 and gcc 4:4.1.2-9ubuntu2

This is the error:

gcc -g -Wall   -c -o pmd.o pmd.c
pmd.c:41: error: expected ‘)’ before ‘*’ token
pmd.c:63: error: expected ‘)’ before ‘*’ token
pmd.c:86: error: expected ‘)’ before ‘*’ token
pmd.c:102: error: expected ‘)’ before ‘*’ token
make: *** [pmd.o] Error 1

and inthe following I copy the pmd.c file (the simles denotes the failed lines). The code obviously worked for the people that released it. Any suggestion?

thanks in advance,
g.

--------------------------
/*
 *
 *  Copyright (c) 2004-2005 Warren Jasper <wjasper@tx.ncsu.edu>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
 */

/*
 * your kernel needs to be configured with /dev/usb/hiddev support
 */

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/ioctl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <asm/types.h>
#include <fcntl.h>
#include <unistd.h>
#include <errno.h>

#include "pmd.h"

#define  PATHLEN 2

// Driver Functions

:confused:int PMD_Find_Interface(HIDInterface** hid, int interface, int product_id)
{
  hid_return ret;

  HIDInterfaceMatcher matcher = { MCC_VID, 0x0, NULL, NULL, 0 };

  matcher.product_id = product_id;

  *hid = hid_new_HIDInterface();
  if (*hid == 0) {
    fprintf(stderr, "hid_new_HIDInterface() failed, out of memory?\n");
    return -1;
  }
  ret = hid_force_open(*hid, interface, &matcher, 3);
  if (ret != HID_RET_SUCCESS) {
    fprintf(stderr, "hid_force_open failed with return code %d\n", ret);
    return -1;
  } else {
    return interface;
  }
}

:confused:int PMD_SendOutputReport(HIDInterface* hid, __u8 reportID, __u8* vals, int num_vals, int delay)
{
  int ret;

  if ( reportID == 0 ) { // use interrupt endpoint 1 
    ret = usb_interrupt_write(hid->dev_handle, USB_ENDPOINT_OUT | 1, vals, num_vals, delay);
    if (ret != num_vals) { // try one more time:
      ret = usb_interrupt_write(hid->dev_handle, USB_ENDPOINT_OUT | 1, vals, num_vals, delay);
    }
  } else { // use the control endpoint (Some FS devices use this)
    ret = usb_control_msg(hid->dev_handle,
			  (USB_TYPE_CLASS| USB_RECIP_INTERFACE),
			  SET_REPORT,
			  (OUTPUT_REPORT | reportID),
			  0,
			  vals,
			  num_vals,
			  delay);
  }
  return ret;    
}


:confused:int PMD_GetInputReport(HIDInterface* hid, __u8 reportID, __u8 *vals, int nbytes, int delay)
{
  __u8 data[33];
  int ret;

  if ( reportID == 0 ) { // it's an LS device, use endpoint 1 
    ret = usb_interrupt_read(hid->dev_handle, USB_ENDPOINT_IN | 1, data, nbytes, delay);
    if ( ret < 0 ) {
      perror("PMD_GetInputReport");
    }
    memcpy(vals, data, nbytes);
    return ret;
  }
  return -1;
}

:confused:int PMD_GetFeatureReport(HIDInterface* hid, __u8 reportID, __u8 *vals, int num_vals, int delay)
{
  int ret = 0;

  ret = usb_control_msg(hid->dev_handle,
			0xa1,
			GET_REPORT,
			FEATURE_REPORT,
			0,
			vals,
			num_vals,
			delay);

    return ret;
}

---

### Post by geraldm on 2007-12-18
The '*' it chokes on appears to be HIDInterface*
Dig into how that is defined in the headers.

Gerald

---

### Post by g.a. on 2007-12-19
thanks for the reply. I downloaded a different version of the files, reinstalled the libraries and compiled without problems.

thanks,
g.

---

