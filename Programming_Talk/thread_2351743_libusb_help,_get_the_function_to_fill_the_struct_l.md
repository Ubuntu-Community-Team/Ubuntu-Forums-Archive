---
title: "libusb help, get the function to fill the struct libusb_control_setup"
date: 2017-02-06
forum: Programming Talk
---

### Post by aurquiel on 2017-02-06
[B]Hello can you hepl me to find the function to fill the struct libusb_control_setup. I would like to have information about 

//bmRequestType
//bRequest
//wValue
//wIndex
            
of the device because i would like to make a control transfer, using this function

```
unsigned char *datatx = new unsigned char[1]; //data to write
        datatx[0]=0xA6;

int response = libusb_control_transfer(device_handle,???, //bmRequestType
                ??? , //bRequest
                ???, //wValue
                ???, //wIndex
                datatx, //data
                1, //wLength
                100 //timeout
            );
```
[/B]
But i can't fin the function that fills that struct, i already successful declare it as **const libusb_control_setup *config_c;  **in line 49 of my code to get description of the device

```
#include <iostream>
#include <libusb-1.0/libusb.h>
using namespace std;

void printdev(libusb_device *dev); //prototype of the function

int main() {
    libusb_device **devs; //pointer to pointer of device, used to retrieve a list of devices
    libusb_context *ctx = NULL; //a libusb session
    int r; //for return values
    ssize_t cnt; //holding number of devices in list
    r = libusb_init(&ctx); //initialize a library session
    if(r < 0) {
        cout<<"Init Error "<<r<<endl; //there was an error
                return 1;
    }
    libusb_set_debug(ctx, 3); //set verbosity level to 3, as suggested in the documentation
    cnt = libusb_get_device_list(ctx, &devs); //get the list of devices
    if(cnt < 0) {
        cout<<"Get Device Error"<<endl; //there was an error
    }
    cout<<cnt<<" Devices in list."<<endl; //print total number of usb devices
        ssize_t i; //for iterating through the list
    for(i = 0; i < cnt; i++) {
                printdev(devs[i]); //print specs of this device
        }
        libusb_free_device_list(devs, 1); //free the list, unref the devices in it
        libusb_exit(ctx); //close the session
        return 0;
}

void printdev(libusb_device *dev) {
    libusb_device_descriptor desc;
    int r = libusb_get_device_descriptor(dev, &desc);
    if (r < 0) {
        cout<<"failed to get device descriptor"<<endl;
        return;
    }
    cout<<"Number of possible configurations: "<<(int)desc.bNumConfigurations<<"  ";
    cout<<"Device Class: "<<(int)desc.bDeviceClass<<"  ";
    cout<<"VendorID: "<<desc.idVendor<<"  ";
    cout<<"ProductID: "<<desc.idProduct<<endl;
    libusb_config_descriptor *config;
    libusb_get_config_descriptor(dev, 0, &config);
    cout<<"Interfaces: "<<(int)config->bNumInterfaces<<" ||| ";
    const libusb_interface *inter;
    const libusb_interface_descriptor *interdesc;
    const libusb_endpoint_descriptor *epdesc;
    const libusb_control_setup *config_c;
    
    cout<<"request type: "<<config_c->bmRequestType<<" | ";

    for(int i=0; i<(int)config->bNumInterfaces; i++) {
        inter = &config->interface[i];
        cout<<"Number of alternate settings: "<<inter->num_altsetting<<" | ";
        for(int j=0; j<inter->num_altsetting; j++) {
            interdesc = &inter->altsetting[j];
            cout<<"Interface Number: "<<(int)interdesc->bInterfaceNumber<<" | ";
            cout<<"Number of endpoints: "<<(int)interdesc->bNumEndpoints<<" | ";
            for(int k=0; k<(int)interdesc->bNumEndpoints; k++) {
                epdesc = &interdesc->endpoint[k];
                cout<<"Descriptor Type: "<<(int)epdesc->bDescriptorType<<" | ";
                cout<<"EP Address: "<<(int)epdesc->bEndpointAddress<<" | ";
            }
        }
    }
    cout<<endl<<endl<<endl;
    libusb_free_config_descriptor(config);
}


```

---

### Post by Rocket2DMn on 2017-02-09
AFAIK control packets are very low level and require you to know (or otherwise determine at runtime) some information about the device you're talking to, like the "interfaces" and "endpoints" and what they do.  This probably requires you to have some technical documentation about your USB device.  Have a look at [http://www.beyondlogic.org/usbnutshell/usb6.shtml](http://www.beyondlogic.org/usbnutshell/usb6.shtml) for some info about what some of these fields are.

My experience with libusb is limited, but I think the bmRequestType field is sometimes written as a combination of three different bitmasks, so you get a value computed like "DIRECTION | TYPE | RECIPIENT".  The order doesn't matter.  For example from a line of code I have, my value for bmRequestType is (out of order): "(LIBUSB_REQUEST_TYPE_VENDOR | LIBUSB_RECIPIENT_DEVICE | LIBUSB_ENDPOINT_OUT)".  My code that issues a reset to my USB device is:
```

    // reset the device
    static const uint8_t RESET_REQUEST = 0;
    static const uint16_t RESET_VALUE = 0;
    static const uint16_t RESET_INDEX = 0;
    if (libusb_control_transfer(ctx->handle, (LIBUSB_REQUEST_TYPE_VENDOR | LIBUSB_RECIPIENT_DEVICE | LIBUSB_ENDPOINT_OUT), RESET_REQUEST,
                                RESET_VALUE, RESET_INDEX,
                                NULL, 0,
                                ctx->timeout_ms) < 0) {
        // error handling here...
    }

```
where "ctx" is a wrapper struct of mine and "ctx->handle" is the "libusb_device_handle*" and "ctx->timeout_ms" is exactly what it sounds like, a communication timeout value in milliseconds of type unsigned int.

HTH.

---

