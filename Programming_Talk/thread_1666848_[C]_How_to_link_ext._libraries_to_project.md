---
title: "[C] How to link ext. libraries to project?"
date: 2011-01-14
forum: Programming Talk
---

### Post by pooke on 2011-01-14
Hi,
how do I link and compile extensional libraries like zlib, libcurl etc to my project?

Programming language: C

Thanks in advance.

---

### Post by nvteighen on 2011-01-14
> **pooke said:**
> Hi,
how do I link and compile extensional libraries like zlib, libcurl etc to my project?

Programming language: C

Thanks in advance.

Using the -l flag (that's a lowercase L, not an uppercase i), such that for linking with some libwhatever.so available at any of the default library directories (mainly /usr/lib, /usr/local/lib), you'd do:

```

# Omiting for brevity's sake flags to enable warnings
gcc -o myapp myapp_main.c myapp_something_else.c -lwhatever

```

In other words, the -l argument uses the library's name with the lib- prefix and the .so extension stripped.

If the library is in another directory, you have to state that non-default directory using the -L flag. In this case you will need some further configuration in order to have the application running.

---

### Post by pooke on 2011-01-14
<deleted>

---

### Post by pooke on 2011-01-14
Thanks!

I assume the libraries will be installed in those default directories. I mean, most likely they'll do...

gcc -o myapp myapp_main.c myapp_something_else.c -llibcurl.so libjpeg.so 
etc?

---

### Post by Zugzwang on 2011-01-14
> **pooke said:**
> Thanks!

I assume the libraries will be installed in those default directories. I mean, most likely they'll do...

gcc -o myapp myapp_main.c myapp_something_else.c -llibcurl.so libjpeg.so 
etc?

No, it works a little bit differently: when using the "-l" flag to specify that some library should be linked, remove the preceding "lib" and leave out the file extension. As an example, in order to link "libcurl.so", use "-lcurl" as a parameter to "gcc" or "g++".

---

### Post by pooke on 2011-01-14
Awesome, thanks.

For a future project I might link several libraries to my work. Do I simply add:

 gcc -o myapp myapp_main.c myapp_something_else.c -lcurl -ljpeg 
etc?

---

### Post by pooke on 2011-01-14
Awesome, thanks.

For a future project I might link several libraries to my work. Do I simply add:

 gcc -o myapp myapp_main.c myapp_something_else.c -lcurl -ljpeg 
etc?

---

### Post by dwhitney67 on 2011-01-14
Never mind.

---

### Post by nvteighen on 2011-01-14
> **pooke said:**
> Awesome, thanks.

For a future project I might link several libraries to my work. Do I simply add:

 gcc -o myapp myapp_main.c myapp_something_else.c -lcurl -ljpeg 
etc?

Yes.

Well, sometimes very complex frameworks that need you to link with several libraries will use something called pkg-config... What pkg-config does is to create the -l switches needed automatically instead of having you write them manually. But don't worry too much now about that.

---

### Post by pooke on 2011-01-14
Ok! Thanks a lot.

---

