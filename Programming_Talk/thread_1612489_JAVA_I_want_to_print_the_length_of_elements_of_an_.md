---
title: "JAVA: I want to print the length of *elements* of an array..."
date: 2010-11-03
forum: Programming Talk
---

### Post by youbuntu on 2010-11-03
[EDIT] Fixed it (in green).


Hi guys. Here is my code, and I have highlighted the part that I am stuck on. Basically, I want to run the program and give it arguments, but have the program list the LENGTH OF EACH ELEMENT (the args):

```
public class Args{
	public static void main(String args[]){
		System.out.println("argument\t\tvalue\n========\t\t=====");
		
		for (int i=0;i<args.length;i++){
		System.out.println(i+"\t\t\t"+[COLOR="Red"]args[i].length[COLOR="SeaGreen"]()[/COLOR][/COLOR]);
		
	}
	}
}
```

So, for example, if I ran:

```
java Args hello world
```

I'd want it to print out the char length of the words "hello" and "world" (5 and 5).

Thanks

---

### Post by raggari on 2010-11-03
Args are String objects so:
```
args[i].length()
```
is the answer.

---

### Post by youbuntu on 2010-11-03
> **raggari said:**
> Args are String objects so:
```
args[i].length()
```
is the answer.


ThanQ. Here is the fixed code:

```
public class Args{
	public static void main(String args[]){
		System.out.println("array index\t\telement length\t\telement contents\n===========\t\t==============\t\t================");
		
		for (int i=0;i<args.length;i++){
		System.out.println(i+"\t\t\t"+args[i].length()+"\t\t\t"+args[i]);
		
	}
	}
}
```

---

### Post by r-senior on 2010-11-03
Did you know there's a printf from Java 5 onwards?

```
System.out.printf("%d\t\t\t%d\t\t\t%s\n", i, args[i].length(), args[i]);
```

---

### Post by youbuntu on 2010-11-03
> **r-senior said:**
> Did you know there's a printf from Java 5 onwards?

```
System.out.printf("%d\t\t\t%d\t\t\t%s\n", i, args[i].length(), args[i]);
```

One step at a time please! :D

---

