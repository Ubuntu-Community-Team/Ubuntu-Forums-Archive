---
title: "Getting commandline args in c++"
date: 2009-08-20
forum: Programming Talk
---

### Post by ShaolinF on 2009-08-20
Hi Guys

If I specify several arguments how do I retrieve them in the application .e.g

./a.out -f file1.txt file2.txt file3.txt --searchtext "welcome to"

---

### Post by credobyte on 2009-08-20
[PHP]int main(int argc, char *argv[])
{
    for (int i = 0; i < argc; i++) {
        cout << i << ": " << argv[i] << endl;
    }

    return 0;
}[/PHP]

Not that hard :p

---

### Post by MindSz on 2009-08-20
define your main as 

```
int main(int argc, char*argv[]){

  return 0;
}
```

The variable argc contains the number of arguments that with which you launched your program.

argv is an array of strings that contains the arguments with which your program was launched:

argv[0] = your program executalbe (e.g. 'a.out')
argv[1] = first argument

etc.

---

### Post by cmay on 2009-08-20
[http://www.chemie.fu-berlin.de/chemnet/use/info/libgpp/libgpp_39.html](http://www.chemie.fu-berlin.de/chemnet/use/info/libgpp/libgpp_39.html)
you could also use the get opt. i found a c++ example as i linked to.

---

