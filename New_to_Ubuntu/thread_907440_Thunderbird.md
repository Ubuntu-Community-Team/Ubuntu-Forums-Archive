---
title: "Thunderbird"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Harpz on 2008-09-01
I'm pretty new to Ubuntu and Im having an odd problem with Thunderbird.

My partner and i both use it via the profile manager to access our email accounts speratly.

The problem is it can be pretty much hit and miss if thuberbird will load and display the selected profile, on some occasions it can be 4-5 attempts before it will load up.

I tried typing thunderbird in terminal and thats when i discovered the error.

```

mike@Anubis:~$ thunderbird
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1192 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Any ideas how i can fix this as both my partner and I are getting tired of the problem now.

Thanks
Mike

---

### Post by swoll1980 on 2008-09-01
```
sudo apt-get install thunderbird thunderbird-gnome-support
```

---

### Post by Harpz on 2008-09-01
> **swoll1980 said:**
> ```
sudo apt-get install thunderbird thunderbird-gnome-support
```

Done that and still have the problem :(
Mike

---

### Post by swoll1980 on 2008-09-01
What are your specs?

---

### Post by Harpz on 2008-09-01
> **swoll1980 said:**
> What are your specs?

Sorry for being a noob could you elaborate a little? what do you need to know?

---

### Post by swoll1980 on 2008-09-01
> **Icerat said:**
> Sorry for being a noob could you elaborate a little? what do you need to know?

Well it seems this error is caused by the xserver shutting down before it finishes drawing the window. Maybe it's a resource issue not enough ram? Slow processor? . Let me know your ram, processor, and video card I will try to investigate this a little more. Also disable compiz
```
metacity --replace
```
see if this helps us narrow down the problem.

---

### Post by Harpz on 2008-09-02
My specs are:

CPU: Dual Core 3.00GHz
RAM: 2GB 
Graphics: GeForce 6600GT

Not that i don't trust you but before I issue that command what will it do, and how do i reverse it if i needed to.

Hope you understand I'm just being careful as I'm so new to Linux and wanting to learn


Thanks in advance
Mike

---

