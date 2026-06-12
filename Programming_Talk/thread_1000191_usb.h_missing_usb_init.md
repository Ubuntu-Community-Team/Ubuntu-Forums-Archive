---
title: "usb.h missing usb_init"
date: 2008-12-02
forum: Programming Talk
---

### Post by affordablemagic on 2008-12-02
Hi

I'm attempting to use eclipse on Hardy to brush up (OK, I'm learning from scratch) on C development. The interest is really in robotics (the arduino platform) and while setting the environment I noticed something odd.

One of the tests I am trying to run is accessing images from my USB webcam. I have libusb-dev and libusb-0.1-4.

I am also using CDT for C development.

When I include usb.h and then try and compile with even usb_init(); in my code eclipse complains that "undefined reference to `usb_init'". I can see usb.h in the include folder.

Here's the code (it is something from online)

```
#include <usb.h>

int main(int argc, char **argv) {
	struct usb_bus *busses;
   	usb_init();
   	usb_find_busses();
   	usb_find_devices();
   	busses = usb_get_busses();
	return 0;
}
```

Should I get a source from libusb and compile myself? Is there a reason libusb-dev etc., doesn't work here.

I googled for an answer but nothing seems to strike this problem. Any help appreciated!

---

### Post by affordablemagic on 2008-12-02
Hi

I resolved the issue. Here it is in case someone comes across it themselves for libusb or indeed another library.

In `step 1` image attached you can see my simple usb project in eclipse. On the project folder i.e., `usb` in my example, right click, and select `P_r_operties`.

You'll get a pop-up box. This is `step 2` image. Select the `C/C++ Build` option on the left, then under `GCC C Linker` drop-down list select `Libraries`. You can see on the image, highlighted w/ an orange background, the word `usb`. I added this **Library** by clicking the `add` icon and entering the text `usb` from the `Libraries (-l)` pane.

---

### Post by ifknot on 2008-12-09
:KS thank you for that saved me hours of frustration!

---

### Post by bkuhns on 2008-12-22
Wow, yeah... thanks a ton! I had a feeling I had to do something like that, but had no idea where to do it. Saved me a ton of time figuring it out, thanks again! :)

---

### Post by arkroan on 2010-11-12
+1

thank you

---

### Post by Gouz on 2010-12-10
meh..

I knew I was forgetting the damn lib. Thanks :)

---

### Post by Gouz on 2010-12-10
meh..

I knew I was forgetting the damn lib. Thanks :)

---

