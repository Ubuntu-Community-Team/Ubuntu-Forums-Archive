---
title: "A question about the future of old Win32 API"
date: 2009-03-12
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2009-03-12
Hello,

My question is about Win32 API which is coded by C programming language. Note that I don't know this API but interested in it these days, so I might use wrong jargon in my question (corrections are welcome).

My question is: is Win32 API obsolete?

Now there is a thing called .Net. Will all the new stuff be supported only by .Net Framework? Or will Win32 API always have the newest features along with .Net? For example, when a new widget is introduced with .Net, will we be able to use that new widget with Win32 API (using C language) or will Win32 API remain what it has today and won't include new widgets, functions etc?

---

### Post by jespdj on 2009-03-12
Maybe you should ask this in a Windows programming forum instead of a forum about programming for Ubuntu and Linux...

---

### Post by jimi_hendrix on 2009-03-12
ugg that things a mess

the proper main function is:

int _tmain(int argc, _TCHAR* argv[]) i believe

---

### Post by ZuLuuuuuu on 2009-03-12
It is, I guess,

```
int WINAPI WinMain (HINSTANCE hInstance, HINSTANCE hPrevInstance,
                    PSTR szCmdLine, int iCmdShow)
```

But it definately looks ugly for a person coming from GTK+ :)

---

### Post by jimi_hendrix on 2009-03-12
> **ZuLuuuuuu said:**
> It is, I guess,

```
int WINAPI WinMain (HINSTANCE hInstance, HINSTANCE hPrevInstance,
                    PSTR szCmdLine, int iCmdShow)
```

But it definately looks ugly for a person coming from GTK+ :)

thats for a gui...and you cant use normal strings...they have to be LPSTR's...and the convert function is like _L?

---

### Post by ZuLuuuuuu on 2009-03-12
> **jimi_hendrix said:**
> thats for a gui...and you cant use normal strings...they have to be LPSTR's...and the convert function is like _L?

You know better than me :) I just started reading "Programming Windows API".

---

### Post by jimi_hendrix on 2009-03-12
> **ZuLuuuuuu said:**
> You know better than me :) I just started reading "Programming Windows API".

i hate win32...but for whatever reason i feel 1337 when i hack it...maybe because its so complex?

---

### Post by Shin_Gouki2501 on 2009-03-12
as far as i know ms wished to replace win32 API when and if they can do it well thats anothe rthing..

---

### Post by jimi_hendrix on 2009-03-12
> **Shin_Gouki2501 said:**
> as far as i know ms wished to replace win32 API when and if they can do it well thats anothe rthing..

ya, VS gives the option of creating CLR C++ apps

these use the .Net libraries, like Console::WriteLine();

---

### Post by ZuLuuuuuu on 2009-03-25
To let you know, I was about to ask the question in MSDN forums but searched first. These are two of the similar questions asked there before:

[http://social.msdn.microsoft.com/forums/en-US/windowssdk/thread/3d9e4b8b-d4e2-4545-926a-873ba4671b52](http://social.msdn.microsoft.com/forums/en-US/windowssdk/thread/3d9e4b8b-d4e2-4545-926a-873ba4671b52)

[http://social.msdn.microsoft.com/forums/en-US/vcgeneral/thread/3f05e294-783c-4043-9b9d-59542f73daa1](http://social.msdn.microsoft.com/forums/en-US/vcgeneral/thread/3f05e294-783c-4043-9b9d-59542f73daa1)

As I understand from the search results, there is no official statement from Microsoft but almost nobody thinks that Win32 support will be dropped since there is a huge code archive and very big softwares written in it...

---

