---
title: "DLL Method signatures?"
date: 2008-02-10
forum: Programming Talk
---

### Post by sunzaru on 2008-02-10
I have what "hopefully" has a quick answer. I have seen DLLImport's here and there and they are fine and dandy. IF you know what the DLL Method signature looks like. 

Question is.. how do you know what the dll signature is? Is there a dll signature explorer or something that i could use? Do i have to rely on other supplying the DLL's method signatures?

I found a windows based one but that just gives the method name, not the full signature which is required to use it.

---

### Post by aks44 on 2008-02-10
First off, this is a Linux forum and you're asking a Windows question... but fortunately there are also a few Windows developers around here. ;)

If I understand you correctly, you're trying to retrieve *function prototypes* from the export information available in a DLL?

Well, I have (almost) good news for you, and some other very bad news. ;)


_Almost good news:_ a few languages (usually those that support function overloading) include the function prototype in the exported name (using an encoding scheme known as "name mangling") so it's possible to retrieve the prototype from that information.

_Related bad news:_ name mangling is not standardized in any way, so you have not only to use the same language that was used to create the DLL, but also quite often the very same compiler. IOW, you're basically screwed.

_More bad news:_ due to the very point I just mentioned, most DLLs that are designed to be used by multiple languages use good old C exports (eg. **extern "C"** in C++) which disables name mangling (and function overloading incidentally), which in turn makes it impossible to retrieve the complete function prototype from the DLL.


> **sunzaru said:**
> Do i have to rely on other supplying the DLL's method signatures?
Yes. (so much explanations for such a short answer... #-o)



Oh and BTW, next time please provide more context when asking a question... you're quite lucky I figured out what you meant with the little information you provided. ;)

---

