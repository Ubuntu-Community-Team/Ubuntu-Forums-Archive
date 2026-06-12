---
title: "Java problem"
date: 2009-10-15
forum: Programming Talk
---

### Post by dwally89 on 2009-10-15
Hi,

I have this task in university to make a program that converts seconds into weeks, days, hours, minutes and seconds.
I have written this program, but when I run it, all it displays is "100000 seconds = ", and doesn't display the rest. I think it's something to do with my array, because when I made it originally without an array, it worked, but now that I have changed it so that it uses an array, it doesn't seem to be working.

Can anyone see what the problem is?

Thanks

```
public class Ex3HoursMinsSecs {
    public static void main(String[] args) {
         int seconds=100000;                
         if (seconds<0){                                    
             System.out.println("Error");                   
         }else{                                             
             System.out.print(seconds + " seconds = ");     
             times[] myTimes;
             myTimes = new times[4];
             int remainder=0;    
             remainder=seconds;
             myTimes[0].multiple = (60*60*24*7);                    
             myTimes[1].multiple = (60*60*24);                     
             myTimes[2].multiple = (60*60);                       
             myTimes[3].multiple = 60;                        
             myTimes[4].multiple = 1;                        
             myTimes[0].name = "week";
             myTimes[1].name= "day";
             myTimes[2].name = "hour";             
             myTimes[3].name = "minute";             
             myTimes[4].name = "second";
             

             for(int i=0; i<5; i=i+1){
                 myTimes[i].value=remainder/myTimes[i].multiple;
                 remainder=remainder%myTimes[i].multiple;
                if (myTimes[i].value>0){
                    if (myTimes[i].value==1){
                        System.out.print("1 " + myTimes[i].name + " ");
                    }else{
                        System.out.print(myTimes[i].value + " " + myTimes[i].name + "s ");
                    }
                }
                if (i==4){                    System.out.print(".");                                 
                }
             }
         }            
    }    
}

```

---

### Post by Arndt on 2009-10-15
> **dwally89 said:**
> Hi,

I have this task in university to make a program that converts seconds into weeks, days, hours, minutes and seconds.
I have written this program, but when I run it, all it displays is "100000 seconds = ", and doesn't display the rest. I think it's something to do with my array, because when I made it originally without an array, it worked, but now that I have changed it so that it uses an array, it doesn't seem to be working.

Can anyone see what the problem is?

Thanks

```
public class Ex3HoursMinsSecs {
    public static void main(String[] args) {
         int seconds=100000;                
         if (seconds<0){                                    
             System.out.println("Error");                   
         }else{                                             
             System.out.print(seconds + " seconds = ");     
             times[] myTimes;
             myTimes = new times[4];
             int remainder=0;    
             remainder=seconds;
             myTimes[0].multiple = (60*60*24*7);                    
             myTimes[1].multiple = (60*60*24);                     
             myTimes[2].multiple = (60*60);                       
             myTimes[3].multiple = 60;                        
             myTimes[4].multiple = 1;                        
             myTimes[0].name = "week";
             myTimes[1].name= "day";
             myTimes[2].name = "hour";             
             myTimes[3].name = "minute";             
             myTimes[4].name = "second";
             

             for(int i=0; i<5; i=i+1){
                 myTimes[i].value=remainder/myTimes[i].multiple;
                 remainder=remainder%myTimes[i].multiple;
                if (myTimes[i].value>0){
                    if (myTimes[i].value==1){
                        System.out.print("1 " + myTimes[i].name + " ");
                    }else{
                        System.out.print(myTimes[i].value + " " + myTimes[i].name + "s ");
                    }
                }
                if (i==4){                    System.out.print(".");                                 
                }
             }
         }            
    }    
}

```

Doesn't it even print the period for i==4? Maybe you need to do a final println to make the line appear.

Otherwise, insert trace output statements that show the successive values of remainder and value. And use the debugger.

---

### Post by dwally89 on 2009-10-15
Nope it doesn't even print the period at the end, it seems to be hanging on the line:
```
myTimes[0].multiple = (60*60*24*7);
```

Can you see anything wrong with it?

---

### Post by NovaAesa on 2009-10-15
Is there code that you aren't posting? A 'times' class maybe? It's a bit hard to give tips without all the code :P

---

### Post by fct on 2009-10-15
What is "times"? A class?

Also, the array initialization seems to be wrong. Should be:

myTimes = new times[5];

which would create an array with 5 elements numbered 0 to 4. Right now you have 4 elements, 0 to 3.

You should be seeing some error output when executing lines that deal with myTimes[4].

---

### Post by dwally89 on 2009-10-15
```
public class times {
        int multiple;
        String name;
        int value;
}
```

Still doesn't work when I type:

```
myTimes = new times[5];
```

---

### Post by fct on 2009-10-15
> **dwally89 said:**
> ```
public class times {
        int multiple;
        String name;
        int value;
}
```

Still doesn't work when I type:

```
myTimes = new times[5];
```

That line constructs an array with 5 null references to instances of the times class. You need this:
```

 for (int i = 0; i < 5; i++)
      myTimes[i] = new times();
```

---

### Post by dwally89 on 2009-10-15
Thanks, seem to be working a bit more now, but now seems to be getting stuck on the line:

```
myTimes[i].value=(remainder/myTimes[i].multiple);
```

Any ideas?

EDIT:

So the code currently looks like this:

```
public class Ex3HoursMinsSecs {
      
    public static void main(String[] args) {
        InputFrame theInputFrame = new InputFrame();
        
         int seconds=theInputFrame.getInt();                
         if (seconds<0){                                    
             System.out.println("Error");                   
         }else{                                             
             System.out.print(seconds + " seconds = ");     
             times[] myTimes;
             myTimes = new times[5];
             for (int i = 0; i < 5; i++){
                myTimes[i] = new times();
             }
             int remainder=0;    
             remainder=seconds;
             myTimes[1].multiple = 604800;                    
             myTimes[1].multiple = (60*60*24);                
             myTimes[2].multiple = (60*60);                   
             myTimes[3].multiple = 60;                        
             myTimes[4].multiple = 1;                        
             myTimes[0].name = "week";
             myTimes[1].name= "day";
             myTimes[2].name = "hour";             
             myTimes[3].name = "minute";             
             myTimes[4].name = "second";
             
             for(int i=0; i<5; i=i+1){
                 myTimes[i].value=(remainder/myTimes[i].multiple);
                 remainder=remainder%myTimes[i].multiple;
                if (myTimes[i].value>0){
                    if (myTimes[i].value==1){
                        System.out.print("1 " + myTimes[i].name + " ");
                    }else{
                        System.out.print(myTimes[i].value + " " + myTimes[i].name + "s ");
                    }
                }
                if (i==4){
                    System.out.print(".");                                 
                }
             }


         }
        
        
    }
    
}
```

---

### Post by fct on 2009-10-15
> **dwally89 said:**
> Thanks, seem to be working a bit more now, but now seems to be getting stuck on the line:

```
myTimes[i].value=(remainder/myTimes[i].multiple);
```

Any ideas?

Paste here the error output cause "getting stuck" is a very unhelpful description.

---

### Post by dwally89 on 2009-10-15
```
Exception in thread "main" java.lang.ArithmeticException: / by zero
        at Ex3HoursMinsSecs.main(Ex3HoursMinsSecs.java:39)
```

Line 39 being: 
```
myTimes[i].value=(remainder/myTimes[i].multiple);
```

I can't understand why it would be dividing by zero...

---

### Post by fct on 2009-10-15
> **dwally89 said:**
> ```
Exception in thread "main" java.lang.ArithmeticException: / by zero
        at Ex3HoursMinsSecs.main(Ex3HoursMinsSecs.java:39)
```

Line 39 being: 
```
myTimes[i].value=(remainder/myTimes[i].multiple);
```

I can't understand why it would be dividing by zero...

The answer is in your last code post:
```

  int remainder=0;    
             remainder=seconds;
             myTimes[1].multiple = 604800;                    
             myTimes[1].multiple = (60*60*24);   


```

Where did the line where you set "myTimes[0]" go?

---

### Post by dwally89 on 2009-10-15
Ahhh, thanks fct, don't know how that happened.

Thanks :-)

---

