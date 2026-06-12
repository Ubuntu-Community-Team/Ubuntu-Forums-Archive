---
title: "Programming a joystick(steering wheel)"
date: 2011-03-27
forum: Programming Talk
---

### Post by Zening on 2011-03-27
Hi,
I've developed an application with retrieves my ps2 steering wheel movements and button states. Everything works fine at that point, but I can't convert those movements into /dev/input/jsX event in order to make other programs recognice my steering wheel. I've tried different libraries for over two days but I havent succeed, could someone tell me at least what could I use to get this?
thanks!

---

### Post by Jonas thomas on 2011-03-27
I wish I new the answer (interesting topic).  Have you tried asking the question in 
Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Gaming & Leisure
Some googling was pointing me over there.

---

### Post by Zening on 2011-03-27
I will ask there if i anybody can guide me here :P

---

### Post by Jonas thomas on 2011-03-27
Like I said, interesting topic.. If you don't mind please post a link to where you found your solution.  (If you don't get your answer where I suggested I ask, you may want to ask the supertuxKart folks.. I seem to recall a web link to there IRC channel) Friendly folks over there, awesome game.

---

### Post by Zening on 2011-03-31
as nobody has suggested anything, I posted in another part of the forum, just in case people in there knows about this. For people interested in this: [http://ubuntuforums.org/showthread.php?p=10621278#post10621278](http://ubuntuforums.org/showthread.php?p=10621278#post10621278)

---

### Post by cgroza on 2011-03-31
In what language did you developed the app and if you do not mind, post some code.

---

### Post by Zening on 2011-04-01
This is the code. As i said, it's an application, not a driver. It's written in c:
```
 #include <usb.h>
 #include <stdio.h>
 #include <time.h>
 #define VERSION "0.1.0"
 #define VENDOR_ID 0x044f
 #define PRODUCT_ID 0xb607
 #define INTERFACE 0
 const static int reqIntLen=2;
 const static int endpoint_Int_in=0x81; /* endpoint 0x81 address for IN */
 const static int endpoint_Int_out=0x00; /* endpoint 1 address for OUT */
 
 const static int timeout=5000; /* timeout in ms */
void delay_sec( int seconds ){
    clock_t endwait;
    endwait = clock () + seconds * CLOCKS_PER_SEC;
    while (clock() < endwait) {}
} 
 void bad(const char *why) {
   fprintf(stderr,"Fatal error> %s\n",why);
   exit(17);
 }

 usb_dev_handle *find_lvr_hid();
 
 usb_dev_handle* setup_libusb_access() {
     usb_dev_handle *lvr_hid;
     int retval;
     char dname[32] = {0};
     usb_set_debug(255);
     usb_init();
     usb_find_busses();
     usb_find_devices();
             
     if(!(lvr_hid = find_lvr_hid())) {
     printf("Couldn't find the USB device, Exiting\n");
     return NULL;
   }
 
 #ifdef LINUX
   retval = usb_get_driver_np(lvr_hid, 0, dname, 31);
   if (!retval)
     usb_detach_kernel_driver_np(lvr_hid, 0);
 
 #endif
 
   delay_sec(0); 
   retval=usb_set_configuration(lvr_hid, 1);
   if ( retval < 0) {
     printf("Could not set configuration 1 : %d\n", retval);
     return NULL;
   }
   retval = retval=usb_claim_interface(lvr_hid, INTERFACE);
   if ( retval < 0) {
     printf("Could not claim interface: %d\n", retval);
     return NULL;
   }
 
   return lvr_hid;
 }
 
 usb_dev_handle *find_lvr_hid() 
 {
     struct usb_bus *bus;
   struct usb_device *dev;
 
   for (bus = usb_get_busses(); bus; bus = bus->next) {
       for (dev = bus->devices; dev; dev = dev->next) {
         if (dev->descriptor.idVendor == VENDOR_ID && 
           dev->descriptor.idProduct == PRODUCT_ID ) {
         usb_dev_handle *handle;
           printf("lvr_hid with Vendor Id: %x and Product Id: %x found.\n", VENDOR_ID, PRODUCT_ID);
         if (!(handle = usb_open(dev))) {
           printf("Could not open USB device\n");
           return NULL;
         }
 
         return handle;
       }
     
     }
   }
   
   return NULL;
 }
 
 /*
  void test_control_transfer(usb_dev_handle *dev)
  {
 //   usb_set_altinterface(dev, 0);
    usb_release_interface(dev, 0);
  }
 */
  void test_interrupt_transfer(usb_dev_handle *dev)
  {
    int r,i;
    char answer[reqIntLen];
    char question[reqIntLen];
    for (i=0;i<reqIntLen; i++) question[i]=i;
    /*r = usb_interrupt_write(dev, endpoint_Int_out, question, reqIntLen, timeout);
    if( r < 0 )
    {
     perror("USB interrupt write"); bad("USB write failed"); 
    }
    */
    /*r = usb_interrupt_read(dev, endpoint_Int_in, answer, reqIntLen, timeout);
    if( r != reqIntLen )
    {
     perror("USB interrupt read"); bad("USB read failed"); 
    }
    for (i=0;i<reqIntLen; i++) printf("%i, %i, \n",question[i],answer[i]);
 //   usb_set_altinterface(dev, 0);
    usb_release_interface(dev, 0);*/
    unsigned char byteantiguo[1];
while(1){
    unsigned char bytes[8];
    r = usb_bulk_read(dev,endpoint_Int_in,bytes,8,timeout);
    for(int i=0;i<8;printf("%d ",bytes[i]), i++);
    if(bytes[1] == 128){printf(" X");}
    if(bytes[1] == 32){printf(" O");}
    if(bytes[2] == 2){printf(" Start");}
    if(bytes[2] == 1){printf(" Select");}
    if(bytes[1] == 64){printf(" []");}
    if(bytes[1] == 16){printf(" Triangle");}
    if(bytes[1] == 4){printf(" L1");}
    if(bytes[1] == 8){printf(" R1");}
    if(bytes[1] == 1){printf(" L2");}
    if(bytes[1] == 2){printf(" R2");}
    if(bytes[3] == (byteantiguo[0]-16)){
    printf(" DOWN");
    }
    if(bytes[3] == (byteantiguo[0]-32)){
    printf(" UP");
    }
    if(bytes[3] == (byteantiguo[0]-24)){
    printf(" RIGHT");
    }
    if(bytes[3] == (byteantiguo[0]-8)){
    printf(" LEFT");
    }
    printf("    %i%%",(100-(bytes[5]*100)/255));
    if(bytes[4]<=127){
    printf(" => %dd", ((bytes[4]*100)/127));
    }
    if(bytes[4]>=128){
    printf(" => %di", (-(((bytes[4]*100)/127)-200)));
    }
    byteantiguo[0] = bytes[3];
    printf("\n");
    }
  }



 
 int main( int argc, char **argv)
 {
   usb_dev_handle *lvr_hid;
   if ((lvr_hid = setup_libusb_access()) == NULL) {
     exit(-1);
   } 
 //  test_control_transfer(lvr_hid); //not implemented yet
   test_interrupt_transfer(lvr_hid);
   usb_close(lvr_hid);
 
   return 0;
 }
```compiled with:
```
gcc -o OUTPUTFILE INPUTFILE.c -I/usr/local -L/usr/local -lusb -std=c99
```run with:
```

rmmod usbhid && rmmod hid && ./OUTPUTFILE && modprobe hid && modprobe usbhid

```

---

