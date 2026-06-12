---
title: "[Java] if-statment with properties stall"
date: 2010-05-24
forum: Programming Talk
---

### Post by SpinningAround on 2010-05-24
There is something strange with the second if-statement, the program simply stop. Nr 1 is printed but neither 2 or 3.
[PHP]	if(loadOld(path)){
			System.out.println("1");
			if(old.getProperty("Load").equalsIgnoreCase("true")){
				System.out.println("2");
				setup = new Setup(old); 
			}
		}
		else{
			System.out.println("3");
			setup = new Setup();
		}[/PHP]

With this modification is nr 1 and 2 printed, I don't understand why.
[PHP]	if(loadOld(path)){
			System.out.println("1");
			if(!old.getProperty("Load").equalsIgnoreCase("true")){
				System.out.println("2");
				setup = new Setup(old); 
			}
		}
		else{
			System.out.println("3");
			setup = new Setup();
		}[/PHP]

---

### Post by dwhitney67 on 2010-05-24
The foremost issue you need to sort out is your indentation.  The outer else-statement is relevant only if the outer if-statement is false.

Thus when you see num 1 printed, yet not num 2 or 3, that seems normal to me.  If you see num 1 and num 2 printed, then it is obviously because you changed the code (your second example).  The only way for num 3 to be displayed is if loadOld() fails.

Try coding like this:
```

if(loadOld(path))
{
   System.out.println("1");

   if(old.getProperty("Load").equalsIgnoreCase("true"))
   {
      System.out.println("2");
      setup = new Setup(old); 
   }
}
else
{
   System.out.println("3");
   setup = new Setup();
}  

```

---

### Post by Tony Flury on 2010-05-24
WHat are you expecting ? that either 1 & 2 get generated or 1 & 3 get generated.

Form what I can see - looking at the opening and closing braces then the code will produce either 1 on its own, 1 & 2 together, or 3 on its own : 
I have reformatted your code so that the braces line up
```


if(loadOld(path))
{ 
    System.out.println("1"); 
    if(!old.getProperty("Load").equalsIgnoreCase("true"))
    { 
        System.out.println("2"); 
        setup = new Setup(old);  
    } 
} 
else
{ 
    System.out.println("3"); 
    setup = new Setup(); 
}  

```
As you can see your else lines up with your first if - and so 3 will only be generated if the first if fails.

---

### Post by trent.josephsen on 2010-05-24
Ugh, Allman style... ;)
```
if (loadOld(path)) {
    System.out.println("1");
    if (!old.getProperty("Load").equalsIgnoreCase("true")) {
        System.out.println("2");
        setup = new Setup(old);
    }
} else {
    System.out.println("3");
    setup = new Setup();
}
```

(OP:  The particular [indentation style](http://en.wikipedia.org/wiki/Indent_style) you use doesn't matter much, as long as it is readable and you use it consistently.  I use GNU indent to format other people's code into K&R style; you can use it with most styles if you desire.  The important thing is readability, and the second most important is consistency.)

---

### Post by SpinningAround on 2010-05-24
Thanks, missed that :oops:

---

