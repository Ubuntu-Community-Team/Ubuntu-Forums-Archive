---
title: "C++ dlfcn plugin system linking error."
date: 2008-10-04
forum: Programming Talk
---

### Post by GCT on 2008-10-04
So, I've written an extension for python that implements a plugin system.  You can create projects, which contain plugins, and all of these are automatically linked and exposed to the python environment.

Here's how my plugin header is defined:

```
// This file defines the plugin interface as well as the PluginManager
// class which handles holding plugins for a given project
#ifndef __PLUGIN__
#define __PLUGIN__

// Forward declarations
class Plugin;
class PluginFactory;

#include <pf_workspace.hh>

// Class definitions
class PluginFactory {
public:
  virtual Plugin* create_instance() = 0;
};

class Plugin {
public:  
   Plugin();
  ~Plugin();

  virtual void checkin()         {}
  virtual void run(int, char*[]) {}
  virtual void checkout()        {}
  
private:
};

// Prototype for plugin registering
extern "C" void registerPlugin(PF_Project& project);

#endif

```

So plugins over-load the Plugin class and then expose a registerPlugin function which takes a PF_Project object.  The plugin then calls a register_plugin function and gives the PF_Project a pointer to a PluginFactory for instantiating the plugin.  

This all compiles and links together just fine.  My problem is at runtime, when I actually try to load a plugin into the system, I get:

> 
Error: print_args.so: undefined symbol: _ZN10PF_Project15register_pluginEP13PluginFactory


Running that symbol through C++filt gives:
> PF_Project::register_plugin(PluginFactory*)

So obviously the plugins can't find the register_plugin function at run-time, but I don't know why.  Running nm on the shared library which is my python extension indicates that it's there:

> 0001b570 T _ZN10PF_Project15register_pluginEP13PluginFactory

Anyone have any thoughts?

---

### Post by GCT on 2008-10-04
I rewrote the plugin header to just define a creator function:

```
extern "C" Plugin* createPlugin();
```

So I can just link against that and pass it around as a pointer for creating instances of a given plugin, makes the code cleaner and doesn't give me guff when linking.

---

