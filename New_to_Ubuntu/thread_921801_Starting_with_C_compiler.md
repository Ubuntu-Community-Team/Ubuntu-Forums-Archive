---
title: "Starting with C compiler"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by TKC747 on 2008-09-16
Does anyone know how to get a c or c++ compiler installed on Ubuntu?  I am not a unix/linux expert.  Is there an easy way to start programming? Thanks in advance

---

### Post by DrMega on 2008-09-16
Yes. In Synaptic, look for the package 'Build-essential' and install that. Once done, you are free to build away to your hearts content. You can write code in a text file and compile it at the command line (cpp filename.cpp I think), or you can download and try one of the various IDEs (Anjuta seems OK, as is KDevelop, but Code::Blocks is my favourite so far, but it isn't in synaptic as far as I know).

---

### Post by TKC747 on 2008-09-16
Thank You DrMega

---

### Post by sebastianavina on 2008-09-16
```


sudo aptitude update
sudo apt-get install build-essential
echo "#include <iostream>

int main() {
  std::cout << \"Hello World\" << std::endl;
  return 0;
}
" > firstprogram.cpp
g++ firstprogram.cpp -o firstprogram
./firstprogram


```

---

