---
title: "GNUstep Installation Issues"
date: 2009-05-03
forum: Programming Talk
---

### Post by natedawg8686 on 2009-05-03
I'm having issues with GNUstep and I was hoping someone could shed some light on what I'm doing wrong.

After about 15 years, I've been bitten by the Objective-C bug again! I would like to work with GNUstep with the idea of maybe transitioning some of the basics into using Cocoa if I ever purchase a Mac so I'm not completely out in left field.

However, I'm having trouble getting anything to compile, even the GNUstep example applications. I tried both using apt-get/Synaptic and also compiling from source using the gnustep-startup-0.22.0 package from GNUstep's Web site. In both cases, the installation/build is 100% successful. After running the GNUstep.sh file, and placing it in my environment settings as the instructions state, gcc keeps complaining that it can't find Foundation/NSObject.h for the small test program I wrote to test the GNUstep build. 

Using objc/Object.h, the program compiles perfectly fine.

I'm clearly doing something incorrectly! I'm guessing it's something to do with the environment values. Can anyone who has a working installation of GNUstep possibly post what code they added to their profiles?

Any help will be greatly appreciated. I'm running both Ubuntu 8.04 on my laptop and Ubuntu 9.04 on one of my desktops.

---

### Post by nvteighen on 2009-05-03
> **natedawg8686 said:**
> I'm having issues with GNUstep and I was hoping someone could shed some light on what I'm doing wrong.

After about 15 years, I've been bitten by the Objective-C bug again! I would like to work with GNUstep with the idea of maybe transitioning some of the basics into using Cocoa if I ever purchase a Mac so I'm not completely out in left field.

However, I'm having trouble getting anything to compile, even the GNUstep example applications. I tried both using apt-get/Synaptic and also compiling from source using the gnustep-startup-0.22.0 package from GNUstep's Web site. In both cases, the installation/build is 100% successful. After running the GNUstep.sh file, and placing it in my environment settings as the instructions state, gcc keeps complaining that it can't find Foundation/NSObject.h for the small test program I wrote to test the GNUstep build. 

Using objc/Object.h, the program compiles perfectly fine.

I'm clearly doing something incorrectly! I'm guessing it's something to do with the environment values. Can anyone who has a working installation of GNUstep possibly post what code they added to their profiles?

Any help will be greatly appreciated. I'm running both Ubuntu 8.04 on my laptop and Ubuntu 9.04 on one of my desktops.
It's better to install gnustep-core-devel from the repositories. Then, follow the instructions you were given (btw, you can download them by installing the gnustep-core-doc package... you'll find them at /usr/share/doc)

---

### Post by natedawg8686 on 2009-05-04
> **nvteighen said:**
> It's better to install gnustep-core-devel from the repositories. Then, follow the instructions you were given (btw, you can download them by installing the gnustep-core-doc package... you'll find them at /usr/share/doc)

Thanks for the advice. I have it running perfectly fine now; DFU moment on my part. Lack of sleep tends to do that!

---

### Post by nvteighen on 2009-05-04
> **natedawg8686 said:**
> Thanks for the advice. I have it running perfectly fine now; DFU moment on my part. Lack of sleep tends to do that!
Nice! :)

---

