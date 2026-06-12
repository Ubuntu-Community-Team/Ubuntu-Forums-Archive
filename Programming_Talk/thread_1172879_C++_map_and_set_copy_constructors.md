---
title: "C++ map and set copy constructors"
date: 2009-05-29
forum: Programming Talk
---

### Post by Alcareru on 2009-05-29
Hello guys

I'm in a bit of trouble getting some code to work. My guess is that the problem is that I don't understand what does the std::map and std::set copy constructors do. Anybody willing to shed some light on the matter?

Here's an example of what sort of maps I use:
typedef std::map<std::string, Configuration> ConfigurationMap;

Configuration is one class of mine.

---

### Post by Habbit on 2009-05-29
What is exactly the problem you are experiencing? Please send a short, self contained example that replicates your problem so we can see where you are stuck.

---

### Post by Alcareru on 2009-05-29
> **Habbit said:**
> What is exactly the problem you are experiencing? 
Segmentation fault

> **Habbit said:**
> Please send a short, self contained example that replicates your problem so we can see where you are stuck.
The problem is not really "short" so I thought I'd leave it out of here. The main thing is that I would like to know what exactly happens when a copy constructor for this:
typedef std::map<std::string, Configuration> ConfigurationMap;
gets called. And especially does it copy the keys and the configurations?

If you can tell me what exactly happens here I think that should do it?
```

ConfigurationMap method(ConfigurationMap param) //first copy constructor call
{
   mutateSomeConfigurations(param);//the Configuration-objects, the keys are not be touched
   return param; //second copy constructor call? somebody somewhere said calling copy constructor on return depends on the compiler, is it true?
}

```

---

### Post by Habbit on 2009-05-29
The copy-constructors (or assignment operators, for that matter) for STL containers _do_ copy their keys and values. However, if "Configuration" is not directly the name of your class but something like "typedef MyConfig* Configuration", then the value type for the map would be MyConfig*, and, as you might know, copying a pointer does not copy the underlying object, which would be the cause of a crash if you deallocated those objects when you killed the first map, then tried to access them through the second map.

If you use direct objects in the map, however, their copy constructors and assignment operators are called as required. You should look for bugs in those methods in your class, particularly in the handling of dynamically allocated memory, since a "segmentation fault" error usually corresponds to dereferencing a null pointer, or a pointer to memory you do not own.

Nevertheless, I'd urge you to produce a reduced example showing the particular point of contention. See [www.sscce.org]("http://www.sscce.org/") for pointers on generating examples for forum-assisted troubleshooting.

EDIT: Regarding copy-constructors when returning an object by value, it depends (see [RVO]("http://en.wikipedia.org/wiki/Return_value_optimization")@Wikipedia). However, no matter how you do it, your copy-constructors and assignment operators are always called as needed, so if you wrote them well everything should be fine.```
ConfigurationMap mymap = method(oldmap);  // mymap is constructed with a copy-constructor directly from method's param

ConfigurationMap other;  // other is default-constructed
other = method(oldmap);  // Then a temporary is copy-constructed from method's param, gets assigned to other through operator= and is destroyed

```

---

### Post by Alcareru on 2009-06-01
Thanks for your reply. The problem was that I was using this sort of method to go through stuff in a set:
```
for (VariablesSet::iterator it = this->configurations.getVariables().begin(); it != this->configurations.getVariables().end(); ++it)
{
    std::cout<<(*it)<<std::endl;
    std::cout<<" |"<<this->configurations.getVariablesMappings()[*it]<<"| "<<std::endl;
}
```
Now because my getters returned a new copy of the set the comparison
```
it != this->configurations.getVariables().end()
``` was never true. Silly mistake.. thanks for your help.

P.S. Oddly enough the segmentation fault did not occur always. I suppose that's because of what you said about the RVO?

---

