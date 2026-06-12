---
title: "java"
date: 2009-08-09
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-09
can the following class be used as a constructor to print the initially assigned string a="original string", 
also i can't use println in class alpha to print, so i need to create an object of alpha and then display.......
how to do the same using constructor?

```
class alpha {
	String a="original string";
	}

public class let {
	static void f( alpha d) {
		d.a="abhilash";
	}
	public static void main(String[] args) {
		alpha first=new alpha();
		System.out.println(first.a);
		
		alpha str=new alpha();
		str.a="abhi";
		System.out.println(str.a);
		
		f(str);
		System.out.println(str.a);
	}
}	

```

---

### Post by credobyte on 2009-08-09
Not sure if it's exactly what you wanted, however, take a look ..

```
public class let {
    public static void main(String args[]) {
        alpha first = new alpha();
        first.changeString("NOT default");
        first.showString();
    }
}

class alpha {
    String a = "default string";
    
    // constructor
    alpha() {
        System.out.println(a);
    }
    
    // change string
    public void changeString(String input) {
        a = input;
    }
    
    // show string
    public void showString() {
        System.out.println(a);
    }
    
}
```

---

### Post by abhilashm86 on 2009-08-09
yes i wanted same as above,din't want to pass an object string and display. thanks a lot credobyte.........

---

### Post by Reiger on 2009-08-09
Your terminology is confusing. If you mean the same thing as I do with "constructor" in the context of Java programming then your answer is a non-trivial constructor:
```

public class Alpha {
  public String myString = "default";
  /* Trivial default constructor so new Alpha() works */
  public Alpha() {} 
  /* Non trivial parametrized constructor */
  public Alpha(String value) {
    myString = value;
  }
}

```

However for some reason you are using a **static method** invoked from main. You can do that, of course:
```

public class Test {
  public static Alpha modifyAlpha(Alpha initial) {
    initial.myString = "new value and other modifications here";
    return initial;
  }
  
  public static void Main (String [] args) {
    Alpha a = new Alpha();
    System.out.println(a.myString); // default value
    a = Test.modifyAlpha(a);
    System.out.println(a.myString); // result of call to static method, modifying value
    a.myString = "And now for something completely the same.";
    System.out.println(a.myString); // result of direct modifications to the value
    System.exit(0);
  }
}

```

---

