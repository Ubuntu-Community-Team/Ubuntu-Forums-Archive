---
title: "Run directory program in ubuntu"
date: 2013-01-01
forum: Programming Talk
---

### Post by sanda199 on 2013-01-01
Hi everyone, I wanna run c++ program in ubuntu terminal. But my program in under some directory. So how can i run it? thanks

---

### Post by sanda199 on 2013-01-01
I also don't know how to compile it. Pls help me. Thanks

---

### Post by fdrake on 2013-01-01
> **sanda199 said:**
> I also don't know how to compile it. Pls help me. Thanks

```

#install the complier
sudo aptitude install build-essential g++
# to compile 
g++ -o complied  not_compiled.cpp
#to run
./compiled

```
google the ne you will find plenty of FAQ and help!

---

### Post by sanda199 on 2013-01-01
but my program is within directory. Is it the same way to compile and run? thanks

---

### Post by PaulM1985 on 2013-01-02
Slightly modifying fdrake's post:

```

#install the complier
sudo aptitude install build-essential g++
# to compile 
g++ -o your_dir/complied  your_dir/not_compiled.cpp
#to run
./your_dir/compiled

```

Paul

---

