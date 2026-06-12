---
title: "Java error: cannot find symbol"
date: 2010-07-18
forum: Programming Talk
---

### Post by Sharang.d on 2010-07-18
dectobin.java:
```

class dectobin_ 
{ 
    long num; 
    dectobin_(long x) 
    { 
        num=x; 
    } 
    void generate() 
    { 
        String bin=""; 
        long temp=num; 
        do 
        { 
            if((temp%2)==0) 
                bin+='0'; 
            else 
                bin+='1'; 
        }while((temp/=2)!=0); 
        System.out.println(num + " in binary is " + bin.reverse()); 
    } 
} 
 
class dectobin 
{ 
    public static void main(String args[]) 
    { 
        dectobin_ obj=new dectobin_(Long.parseLong(args[0])); 
        obj.generate(); 
    } 
} 


```

On compiling the above code the following error is generated:
```

dectobin.java:19: cannot find symbol
symbol  : method reverse()
location: class java.lang.String
        bin=bin.reverse();
               ^
1 error
Compilation failed.

```

I'm new to Java and also to Java on Ubuntu :S
Using geany as the IDE.
Weird thing is i noticed almost all the string functions produce some error so i googled around and got to know something about setting CLASSPATH. I don't know if that is relevant to my problem or not anyway i didn't get how to do it!
I'm using```
java version "1.6.0_21"
Java(TM) SE Runtime Environment (build 1.6.0_21-b06)
Java HotSpot(TM) 64-Bit Server VM (build 17.0-b16, mixed mode)

```

Help would be greatly appreciated! :)

---

### Post by Sharang.d on 2010-07-18
Bump. Anyone?

---

### Post by Sharang.d on 2010-07-18
Sorry for bumping this thread again and again but I'm sure there are a lot of people here who can help me out with this issue[looking at the codes you people have posted this is NOTHING]
So PLEASE, help! :(

---

### Post by Reiger on 2010-07-18
Bumping after less than an hour??

Anyway: the Java compiler is perfectly clear on what your error is: you call something that does not exist. Java Strings don't have a reverse() method. All you have is: [http://download.oracle.com/docs/cd/E17409_01/javase/6/docs/api/java/lang/String.html](http://download.oracle.com/docs/cd/E17409_01/javase/6/docs/api/java/lang/String.html) 

But you were probably not looking for Strings anyway: [http://download.oracle.com/docs/cd/E17476_01/javase/1.5.0/docs/api/java/lang/StringBuilder.html](http://download.oracle.com/docs/cd/E17476_01/javase/1.5.0/docs/api/java/lang/StringBuilder.html)

---

### Post by Sharang.d on 2010-07-18
THANKS! Knew nothing abot the StringBuffer Class >.<

Anyway, solved!
Did this:
```

System.out.println(num + " in binary is " + new StringBuffer(bin).reverse());

```

---

