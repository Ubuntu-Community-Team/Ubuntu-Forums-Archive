---
title: "Common hashing daemon"
date: 2007-10-11
forum: Programming Talk
---

### Post by archivator on 2007-10-11
Ok, here's my new project.

You know how every single file-sharing program has its own way of hashing things? And how every time you start a program it rechecks to see if anything has changed since last time? Well, I hate this part. 

First, it's a pure waste of I/O operations. Why read the same thing twice (or three times) when you can read only once and hash it two different ways. Second, it really prevents you from just launching the program and start using it. You have to wait for the hashing to finish and only then can you share your files. May the Force help you if have more than 20 GB to share.. 

My idea is to create a daemon that would monitor certain folders for changes and would hash their contents by using various algorithms. Then, one could simply export the revelant data to a program of his choice and be sure that when he launches the program, it won't spend hours hashing his files. Best case scenario, the daemon would expose an API that programs could use to access the hashes.

Now, here comes the real bugger - what language do I write it in?

I'm really considering only C++ and Python. However, I can't make up my mind.

If I choose C++, I can rely on speed and vast libraries of cryptographic functions. However, building a plugin system in C++ is a PITA (and I'm thinking the hashing/output modules should be plugins). 

If I choose Python, I can easily implement a plugin system but I might need to sacrifice some speed. And really, a daemon in Python?

Any thoughts are welcome.

---

### Post by Ramses de Norre on 2007-10-11
A C++ library for the hashing algorithms and a python frontend to make plugins in? I thought you could easily use C++ modules in python.

---

### Post by archivator on 2007-10-11
> **Ramses de Norre said:**
> A C++ library for the hashing algorithms and a python frontend to make plugins in? I thought you could easily use C++ modules in python.

Well, my idea was that the hashing algorithms (along with the program-specific output formats) should be plugin-based. Besides, there really is no point in making the daemon part in Python and the hashing libraries in C++. I'd like to stick to one language. Using boost's python wrapper is just going to complicate things unnecessarily.

---

### Post by aks44 on 2007-10-11
> **archivator said:**
> building a plugin system in C++ is a PITA (and I'm thinking the hashing/output modules should be plugins).

Plugins are quite easy to write in C++ IMHO.

Just to give you an idea, here's how it should look like (dirty mix of pseudo-code and Windows calls to give you the basic idea, I bet Linux has equivalent APIs) :


Main program:
```
class PluginInterface
{
public:
  virtual ~PluginInterface() {}; // very important for destroying safely

  // Plugin members (must be pure virtual)
  virtual void Foo() = 0;
  virtual void Bar() = 0;
};

typedef PluginInterface* (*PluginInstanciateProc)(/* whatever params */);

for each dll_file in plugins_directory
{
  dll_handle = LoadLibrary(dll_file);
  PluginInstanciateProc proc = reinterpret_cast<PluginInstanciateProc>(GetProcAddress(dll_handle,"Instanciate"));
  PluginInterface* plugin = proc(/*...*/);
  // do whatever you want with plugin
}
```


Plugin library:
```
class MyPlugin : public PluginInterface
{
public:
  virtual void Foo() { /* implementation */ };
  virtual void Bar() { /* implementation */ };
};

extern "C" PluginInterface* Instanciate(/*...*/)
{
  return new MyPlugin(/*...*/);
};
```


Of course you gotta add error checking, exception safety etc but you get the big picture...

---

### Post by archivator on 2007-10-13
After some tests, I have a clearer idea of how each platform performs.

In my tests I used python's Crypto module and the RFC implementation of MD4. The C version was always around 2.1 times faster than the python counterpart. The question is whether it's a big enough difference to force me to use C. 

@aks44, I do know the general principles behind a plugin system in C. However, designing a plugin system takes much time and with Python taking care of some of the basic actions, I think it would be much easier to implement. But then again, the performance would suffer.

From what I can see, the only question I need to answer is whether performance is of critical importance in this project. Any thoughts on this are most appreciated.

---

### Post by CptPicard on 2007-10-13
> **archivator said:**
> 
From what I can see, the only question I need to answer is whether performance is of critical importance in this project. Any thoughts on this are most appreciated.

I would say performance is fairly irrelevant as long as you're staying within a relatively low constant. This is a background process that you're not being interactive with, and you'll want to run it at a fairly low priority so that it's running when anything else is not. It is done when it is done. Additionally you'll be hashing a few files at a time after initially hashing "everything".

Btw, I don't really understand why you wouldn't want to link to efficient C implementations when you can. There's a fairly limited set of commonly used hash functions, and you will probably want to provide them out of the box, and even when doing plugins, you won't be switching them all the time. Let the developer do the work, and don't shy from writing a python plugin interface wrapper to a C module...

The only real philosophical issue I have here is the "daemon written in Python" bit... this is a really small footprint daemon in C, and bringing the Python interpreter into the picture makes it probably much bigger?

How are you planning on doing the storage of hashes?

---

### Post by mjwood0 on 2007-10-13
I'm not sure why you would shy away from the vast library of really efficient C functions.  They are already out there and you know they're fast...

---

