---
title: "char arrays?"
date: 2008-02-23
forum: Programming Talk
---

### Post by penguinboy08 on 2008-02-23
I'm trying to learn more c++ by working with SDL. I'm trying to call the function "SDL_WM_SetCaption()", with is supposed to set the window title for the app.

However, calling the following doesn't error, nor does it change the window title.
SDL_WM_SetCaption("Test Title", NULL);


I read the documentation for SDL, ([http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlwmsetcaption.html](http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlwmsetcaption.html)), it says the parameters need to be "const char". I'm using strings, could this be why the line doesn't seem to be doing anything?

The question is: how do I convert a string into a const char?


Thanks in advance, almost all my previous programming expirence is in c#, so this is all very strange to me.

---

### Post by Joeb454 on 2008-02-23
From my (somewhat limited) C experience, const char has to be declared then never changed near the start of the code.

---

### Post by amingv on 2008-02-23
Have you tried

```
std::string foo = "ubuntu"; //this is a string
const char* bar = foo.c_str(); //this is a C style char array

```

---

### Post by Lux Perpetua on 2008-02-23
> **penguinboy08 said:**
> However, calling the following doesn't error, nor does it change the window title.
SDL_WM_SetCaption("Test Title", NULL);Can you post a short, compilable program that demonstrates the issue? I've used SDL_WM_SetCaption() exactly in the way that you describe, and it has always worked.

---

### Post by cb951303 on 2008-02-23
the solution to your problem is already answered above but I'm wondering
how did it compile if you passed a c++ string to that function :confused:

---

