---
title: "Writing to text editors from C"
date: 2008-11-21
forum: Programming Talk
---

### Post by gorded on 2008-11-21
so i can open up nano/vim with 

system("nano");

but how would i write to nano's stdin

Thanks

---

### Post by kknd on 2008-11-21
You can't write to a file and then open it in nano?

---

### Post by gorded on 2008-11-21
Yes but i would like the program to open nano and write to a file infront of the user (effect)

---

### Post by Mr.Macdonald on 2008-11-21
experiment with python or shell first, open nano in another terminal, and start writing to all the std* with python or shell, then you'll know

---

### Post by nitro_n2o on 2008-11-22
you could right something to file.. and in another shell have it do tail -f file 

for example

touch hello.txt; tail -f hello.txt 

then in another shell 
echo "Hi" >> hello.txt 

and see if that works

---

