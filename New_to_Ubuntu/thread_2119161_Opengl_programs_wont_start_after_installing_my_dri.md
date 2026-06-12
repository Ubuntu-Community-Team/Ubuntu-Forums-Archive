---
title: "Opengl programs wont start after installing my driver for ATI Mobility Radeon HD 5470"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by rafallegatus on 2013-02-23
I always get, For example;

The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 147 error_code 1 request_code 139 minor_code 66)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Same thing happened with gimp, blender, wings3d.

Also I'm unable now to use my webcam because programs like skype or googletalk wont allow my webcam to be detected.....it all works fine before installing my ATI Mobility Radeon  HD 5470 Graphics..the problem is if I don't install it, I only get 1024x768 resolution. I need to have higher resolution so I could do my designing efficiently..


Please help, I've tried google searching fo weeks but I havent found any answer.

Regards,
Rafael

---

### Post by Mark Phelps on 2013-02-23
I can't give you a detailed explanation because those are machine-specific, but since you mentioned Mobility Radeon, I'm presuming this is a laptop -- and in many cases, the ONLY drivers that will work well with laptops are the ones that are supplied by the laptop seller.

I see these problems on Win7 forums all the time -- folks force installation of drivers they downloaded from AMD and then, they have problems.

If you tell us the make and model laptop, some else using that same laptop may be able to post a solution.

---

### Post by rafallegatus on 2013-02-23
Actually there are other problems besides this...I couldn't log in without booting from the grub and choosing the old ubuntu image, and I couldn't use hibernate or suspend properly...everything was great since 10.04....but since i have to use some programs that are best supported in 12.04..I have to upgrade...I'll post this in another topic but since I'm suspecting that this and the problems I posted earlier have something to do with xorg and the ati driver.


The model of my laptop is MSI EX405.....video driver is ATI Mobility Radeon  HD5470 Graphics

Thanks,
Rafael

---

### Post by Mark Phelps on 2013-02-24
The page below has the link to the Mobility Linux drivers:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

Whichever one you tried, if that didn't work, you could try the other one.

---

### Post by rafallegatus on 2013-02-24
I already used the first one before but it didn't have any differences with the one I used in the ubuntu software center. I cannot use the second one...it is probably built for 64 bits....mine is 32 only

---

