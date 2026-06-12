---
title: "Problem with a MultiThreaded program in C++?"
date: 2010-10-23
forum: Programming Talk
---

### Post by jeremy28 on 2010-10-23
Hi all;
 
I have a program called "Device Manager" to manange usb tokens for sending and recieving multiple data to/from them using shared memory method.
 
Here is a piece of "Device Manager" code:
```
int main()
{
  pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
  MY_ReqHandler *reqHandler = new MY_ReqHandler(&lock);
  MY_SharedMemory shMem;
  if(shMem.init())
      retlog((char*)"main", 1, 1);
  printf("sharedMem inited\n");
  int ret = shMem.create();
  printf("sharedMem create retVal %d\n", ret);
  ...
} 
```
 
The type "MY_ReqHandler" is a C++ class that it's constructor initializes a token connected  to the system as below:
```
MY_ReqHandler::MY_ReqHandler (pthread_mutex_t* trdlock)
{
    enterLogger ((char*)"MY_ReqHandler::MY_ReqHandler");
 
    this->lock = trdlock;
    int ret = pthread_create(&hThread, NULL, run, (void*) this);
    if (ret)
      perror("pthread_create failed.");
    returnLogger((char*)"MY_ReqHandler::MY_ReqHandler", 0, 0);
    return;
}
```
 
And the Thread function as below:
```
void* run (void* obj)
{
   enterLogger ((char*)"run (MY_ReqHandler)");
   pthread_mutex_lock(((MY_ReqHandler*)obj)->lock);
   ((MY_USBWrapper*)obj)->InitToken(1, VENDORID, PRODUCTID);
   pthread_mutex_unlock(((MY_ReqHandler*)obj)->lock);
   retlog((char*)"run (MY_ReqHandler)", 0, 0);
}
```
 
Here, "MY_USBWrapper" type is another class that one of it's member functions called 
"InitToken" initializes the token (including find and get a handle to it using "libusb"
library inside a function with name "rawhid_open"). 
 
The function "rawhid_open" that is called in "InitToken" is as below (It uses "libusb" library functions):
```
int rawhid_open(int max, int vid, int pid)
{
   struct usb_bus *bus;
   struct usb_device *dev;
   struct usb_interface *iface;
   struct usb_interface_descriptor *desc;
   struct usb_endpoint_descriptor *ep;
   usb_dev_handle *u;
   uint8_t buf[1024];
   int i, n, ep_in, ep_out, count=0, claimed;
   hid_t *hid;
   if(first_hid)
      free_all_hid();
   printf("rawhid_open, max=%d\n", max);
   if(max < 1)
      return 0;
   usb_init();
   usb_find_busses();
     printf("usb_find_busses is called\n");
   usb_find_devices();
     printf("usb_find_devices is called\n");
   for (bus = usb_get_busses(); bus; bus = bus->next)
   {
        for (dev = bus->devices; dev; dev = dev->next)
        {
          if (vid > 0 && dev->descriptor.idVendor != vid)
             continue;
          if (pid > 0 && dev->descriptor.idProduct != pid)
             continue;
          if (!dev->config)
             continue;
          if (dev->config->bNumInterfaces < 1)
             continue;
          printf("device: vid=%04X, pid=%04X, with %d iface\n",
             dev->descriptor.idVendor,
             dev->descriptor.idProduct,
             dev->config->bNumInterfaces);
          iface = dev->config->interface;
          u = NULL;
          claimed = 0;
          for(i=0; i<dev->config->bNumInterfaces && iface; i++, iface++)
          {
             desc = iface->altsetting;
             if (!desc)
                continue;
             printf("  type %d, %d, %d\n", desc->bInterfaceClass,
                desc->bInterfaceSubClass, desc->bInterfaceProtocol);
             if (desc->bInterfaceClass != 3)
                continue;
             if (desc->bInterfaceSubClass != 0)
                continue;
             if (desc->bInterfaceProtocol != 0)
                continue;
             ep = desc->endpoint;
             ep_in = ep_out = 0;
             for (n = 0; n < desc->bNumEndpoints; n++, ep++)
             {
                if (ep->bEndpointAddress & 0x80)
                {
                   if (!ep_in)
                      ep_in = ep->bEndpointAddress & 0x7F;
                   printf("    IN endpoint %d\n", ep_in);
                }
                else
                {
                   if (!ep_out)
                      ep_out = ep->bEndpointAddress;
                   printf("    OUT endpoint %d\n", ep_out);
                }
             }
             if (!ep_in)
                continue;
             if (!u)
             {
                u = usb_open(dev);
                if (!u)
                {
                   printf("  unable to open device\n");
                   break;
                }
             }
             printf("  hid interface (generic)\n");
             if (usb_get_driver_np(u, i, (char *)buf, sizeof(buf)) >= 0)
             {
                printf("  in use by driver \"%s\"\n", buf);
                if (usb_detach_kernel_driver_np(u, i) < 0)
                {
                   printf("  unable to detach from kernel\n");
                   continue;
                }
             }
             if (usb_claim_interface(u, i) < 0)
             {
                printf("  unable claim interface %d\n", i);
                continue;
             }
             hid = (struct hid_struct *)malloc(sizeof(struct hid_struct));
             if (!hid)
             {
                usb_release_interface(u, i);
                continue;
             }
             hid->usb = u;
             hid->ep_in = ep_in;
             hid->ep_out = ep_out;
             hid->open = 1;
             add_hid(hid);
             claimed++;
             count++;
             if (count >= max) return count;
          }
          if (u && !claimed) usb_close(u);
       }
    }
    return count;
}
```
 
Also, "MY_SharedMemory" class is intended for shared memory (IPC) operations and the member function "init" is as following:
```
MY_SharedMemory::init ()
{
     fprintf(stderr, "All numeric input is expected to follow C conventions:\n");
     fprintf(stderr, "\t0x... is interpreted as hexadecimal,\n");
     fprintf(stderr, "\t0... is interpreted as octal,\n");
     fprintf(stderr, "\totherwise, decimal.\n");
    /* Get the key. */
     fprintf(stderr, "Enter key: ");
     scanf("%li", (long int*) &key);
    /* Get the size of the segment. */
     fprintf(stderr, "Enter size: ");
     scanf("%i", &size);
    /* Get the shmflg value. */
     fprintf(stderr, "Expected flags for the shmflg argument are:\n");
     fprintf(stderr, "\tIPC_CREAT = \t%#8.8o\n", IPC_CREAT);
     fprintf(stderr, "\tIPC_EXCL = \t%#8.8o\n", IPC_EXCL);
     fprintf(stderr, "\towner read =\t%#8.8o\n", 0400);
     fprintf(stderr, "\towner write =\t%#8.8o\n", 0200);
     fprintf(stderr, "\tgroup read =\t%#8.8o\n", 040);
     fprintf(stderr, "\tgroup write =\t%#8.8o\n", 020);
     fprintf(stderr, "\tother read =\t%#8.8o\n", 04);
     fprintf(stderr, "\tother write =\t%#8.8o\n", 02);
     fprintf(stderr, "Enter shmflg: ");
     scanf("%i", &shmflg);
     turn = 2;
    return 0;
}

```
 
But when I run the "Device Manager" executable file, I see the following result:
```
rawhid_open, max=1
usb_find_busses is called

All numeric input is expected to follow C conventions:
        0x... is interpreted as hexadecimal,
        0... is interpreted as octal,
        otherwise, decimal.
Enter key: usb_find_devices is called
device: vid=E854, pid=1230, with 1 iface
  type 3, 0, 0
    IN endpoint 1
    OUT endpoint 2
  hid interface (generic)
  in use by driver "usbfs"
found rawhid device
10
Enter size: 10
Expected flags for the shmflg argument are:
        IPC_CREAT =     00001000
        IPC_EXCL =      00002000
        owner read =    00000400
        owner write =   00000200
        group read =    00000040
        group write =   00000020
        other read =    00000004
        other write =   00000002
Enter shmflg: 00001000
sharedMem inited
sharedMem create retVal 0
sharedMem created
```
 

As you see, in the middle of "rawhid_open" function (that is, after "usb_find_busses is called" message), the program switches to "Sharememory::init" function. I mean, the control of program exits from "rawhid_open" function or thread function of "MY_ReqHandler" constructor and the constructor returns.
So that, the control goes to the rest of "Device manager" code at "shMem.init" part in:
```
All numeric input is expected to follow C conventions:
...
```
And again, in the "Enter key:" part, switches to the rest of "MY_ReqHandler" constructor or "rawhid_open" function at "usb_find_devices is called" and ...
 
My question  is that why do I face this result?!
 
I expect that at first, the "MY_ReqHandler" constructor or thread function runs completely (token to be initialized) and then "shMem.init" to be run!
 
But I see the mentioned result!!
 
Could you help me what the problem is?
 
Unfortunately, I couldn't find the solution. help me please...
 
TIA.

---

### Post by GeneralZod on 2010-10-23
> **jeremy28 said:**
> 
I expect that at first, the "MY_ReqHandler" constructor or thread function runs completely (token to be initialized) and then "shMem.init" to be run!


I'm a little confused, here: are you saying that you expect the rawhid_open(...) to complete and return a value before the MY_ReqHandler::MY_ReqHandler (...) constructor is exited? 

What you're seeing seems correct to me: rawhid_open is started in a separate thread in MY_ReqHandler::MY_ReqHandler (...), so it seems reasonable that the MY_ReqHandler::MY_ReqHandler (...) constructor be exited and the shared mem stuff be run in parallel with rawhid_open(...).

Edit:

Can you post a complete output log?

---

### Post by dwhitney67 on 2010-10-23
This has got to be worst marriage between C and C++ code I've seen in quite a while.

Does MY_ReqHandler have an is-a relationship with MY_USBWrapper?  I noticed in the static thread function that you C-style casted the void-pointer 'obj' to each of these class objects.

I recommend that you hold off from launching your MY_ReqHandler thread until you have initialized everything else in the application, and that you have verified that everything is setup properly.

Btw, constructors never return a value; having "return" statement in the constructor is superfluous.  But you do need a return value from your static thread function!

Also, try to consolidate the if-blocks in the rawhid_open() function.  It seems that under many conditions, you call "continue".

The use of single-character variable names should be avoided.

In C++, you are permitted to declare variables at the first point where they are used.  Declaring all variables at the beginning of a function is considered poor programming.

The MY_SharedMemory::init() method looks appropriate for Halloween; very spooky.  Try to make it more presentable, and if possible, avoid taking in user input via scanf() (ie. consider augmenting the class constructor).  Run the program with command-line arguments and validate these before ever getting to the point where the thread(s) and shared-memory are set up.

---

### Post by jeremy28 on 2010-10-23
Hi and Thanks!
> are you saying that you expect the rawhid_open(...) to complete and return a value before the MY_ReqHandler::MY_ReqHandler (...) constructor is exited?

Yes, exactly!
 
> What you're seeing seems correct to me: rawhid_open is started in a separate thread in MY_ReqHandler::MY_ReqHandler (...), so it seems reasonable that the MY_ReqHandler::MY_ReqHandler (...) constructor be exited and the shared mem stuff be run in parallel with rawhid_open(...).

I want to be able to suspend a Thread and see an appropriate result. 
That is, initializing token at first and then entering shared memory specification such as key, size, flag, ...
 
I want to see these two parts separate and consecutive, not parallel and in this form!
 
```
Can you post a complete output log?
```
Yes, I'll send the log file contents later.

THX.

---

### Post by jeremy28 on 2010-10-23
Hi and Thanks!
 
> Does MY_ReqHandler have an is-a relationship with MY_USBWrapper?
The "MY_USBWrapper" class is distinct from "MY_ReqHandler", not base or derived class of it. They are separate modules, so that "MY_USBWrapper" objects are invoked and used in "MY_ReqHandler" member functions.
 
> I recommend that you hold off from launching your MY_ReqHandler thread until you have initialized everything else in the application, and that you have verified that everything is setup properly.

Do you mean initializing token or other thing in application?
I couldn't find out your intention, could you elaborate more please?
 
> But you do need a return value from your static thread function!
Yes, "retlog" function do so.
 
> Also, try to consolidate the if-blocks in the rawhid_open() function. It seems that under many conditions, you call "continue".
In C++, you are permitted to declare variables at the first point where they are used. Declaring all variables at the beginning of a function is considered poor programming.

This function is a piece of a code called "hid_LINUX.cpp" that I've not written it and only use it to interact with token. I get it from Internet.
 
> The MY_SharedMemory::init() method looks appropriate for Halloween; very spooky. Try to make it more presentable, and if possible, avoid taking in user input via scanf() (ie. consider augmenting the class constructor

Also, I've got this piece of code from here:
```
http://www.cs.cf.ac.uk/Dave/C/node27.html#SECTION002761000000000000000
```
That's why I'm new to linux APIs and have used from this sample code. what do you suggest instead of "scanf" to get the user input?

BTW, I have not defined a constructor in this class. Do you suggest to create a constructor and replace the "init" code in that? 
 
I'll be thankful if you help me again...

---

### Post by dwhitney67 on 2010-10-23
> **jeremy28 said:**
> 
I'll be thankful if you help me again...

Based on the answers you provided in response to my questions, IMHO, you should focus on the basics of C++, and if necessary C, before continuing on your project.  Without a strong foundation of programming, and without a deeper knowledge of the C++ and C API, your current endeavor will probably only succeed with lots of luck.

Btw, if MY_ReqHandler and MY_USBWrapper have nothing in common, I cannot think of any way that your thread would ever have worked.  You are passing a MY_ReqHandler object to the thread, yet are casting it to a MY_USBWrapper.

Here... play with this example.  Personally, I would have expected it to crash, but it doesn't.  What is certain though, is that an object of type A is never constructed.
```

#include <pthread.h>
#include <iostream>

class A
{
public:
   A() : value(5) {}

   void whoAmI() { std::cout << "I'm A with value = " << value << std::endl; }

private:
   int value;
};

class B
{
public:
   B() { pthread_create(&tid, 0, thread, this); }

   void whoAmI() { std::cout << "I'm B." << std::endl; }

   pthread_t getTID() const { return tid; }

private:
   static void* thread(void* arg)
   {
      ((B*)arg)->whoAmI();
      ((A*)arg)->whoAmI();   // this should NOT work.

      return 0;
   }

   pthread_t tid;
};

int main()
{
   B b;

   void* status = 0;
   pthread_join(b.getTID(), &status);
}

```

---

