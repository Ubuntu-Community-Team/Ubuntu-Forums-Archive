---
title: "help with classpath"
date: 2006-01-30
forum: Programming Talk
---

### Post by alexal on 2006-01-30
Hello. i am learning java and i am at the stage that i learn about packages.But i have one HUGE problem i cant set the classpath.I have read the threads that refer to classpath but nothing has worked for me.I have one class called Item.class and the Storefront.java that can not be compiled because it uses Item and it cant find it. In windows the classpath works fine and the Storefront compiles.But in ubuntu i dont know what to do.I have used the command from this link [http://www.linuxheadquarters.com/howto/basic/classpath.shtml](http://www.linuxheadquarters.com/howto/basic/classpath.shtml) but the Storefront dont compiles. i am using anjuta. I have the 1.5 java version installed not from the package manager but from a how to in the ubuntu forum. help me.

---

### Post by bernardfrancois on 2006-01-31
Maybe Item isn't a valid name for your class...

Maybe you can upload both java files?

Or show some console output when you try to compile Storefront.java.

---

### Post by alexal on 2006-01-31
Here is what i get when i try to compile in ubuntu. In windows works perfectly(says succesful).

javac Storefront.java
Storefront.java:15: cannot find symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
        public Item getItem(int i) {
               ^
Storefront.java:11: cannot find symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
                Item it = new Item(id, name, price, quant);
                ^
Storefront.java:11: cannot find symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
                Item it = new Item(id, name, price, quant);
                              ^
Storefront.java:16: cannot find symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
                return (Item)catalog.get(i);
                        ^
Note: Storefront.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
4 errors

i have attached the 2 files(rename them to .java. it only lets you attach .txt)
Do you think that the problem is that i didnt installed java 1.5 from the packge manager? should i ununstall it? how?

---

### Post by bernardfrancois on 2006-01-31
Ok, I'll check your code. If I know more I'll edit this post.

---

### Post by hod139 on 2006-02-21
I was browsing the older posts and noticed this one was still unresolved.  If you still need help (and if you are even still listening to this thread) you can compile the two java file by simply typing
```
javac *.java
```

---

### Post by bernardfrancois on 2006-02-22
I'm sorry, I didn't check out the code any more.
Make sure that the version of java you are using in linux isn't older than the one in windows. Also make sure you are not trying to use any third-party classes that only work in windows.

---

