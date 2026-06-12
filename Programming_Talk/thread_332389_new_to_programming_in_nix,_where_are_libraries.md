---
title: "new to programming in *nix, where are libraries?"
date: 2007-01-06
forum: Programming Talk
---

### Post by band-aid on 2007-01-06
I am by no means a proficient programmer but I am trying to learn. For the past few months I have been working in dev C++ in windows and I have that pretty well down but now that I am trying to get started in linux i'm in a bit over my head. I have the G++ compiler and have been trying out coding in nano, vim, and gedit but I cannot get anything to compile because I do not have any of the libraries that I am accustomed to using. For instance 

#include <IOSTREAM>

int main(){
cout << "Hello World!";
}
return 0;

returns an error upon compiling because I don't think I have iostream. With dev c++ there were a ton of libraries that came with it and were stored in its directory. Where do I get libraries and where are they stored for use with the G++ compiler. If you have any recommendations of other compliers or development environments please feel free to make them. Thanks for the help

Band-aid

---

### Post by cabalas on 2007-01-06
C++ is a case sensitive language, try to compile it with iostream not capitalized and see how you go.

---

### Post by quartzy on 2007-01-06
You have the build-essential package I assume?

If not do

```
sudo apt-get install build-essential
```

Or use the gui apt installer :p

---

### Post by band-aid on 2007-01-06
yea... that build-essential thing was what I was missing. Thanks for the help.

---

### Post by quartzy on 2007-01-06
> **band-aid said:**
> yea... that build-essential thing was what I was missing. Thanks for the help.

np :)

---

