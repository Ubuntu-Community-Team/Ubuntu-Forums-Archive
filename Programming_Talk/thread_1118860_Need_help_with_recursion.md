---
title: "Need help with recursion"
date: 2009-04-07
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-04-07
Hey All

I'm learning recursion in java and writing a short method to build a powerset from elements in an ArrayList.  However, I'm having what I think are logic problems with my recursion since this is my first time using it.  Can anyone help me fix this code to make it work?  Any help would be appreciated.  Here's what I have so far:
```

public static ArrayList<String> recur (ArrayList<String> a) {
		if (a.size () == 1) {
			
			temp.add (a.get (0));
			
		}
		else {
		
			current = a.get (0);
			
			a.remove (0);
			retList.add (current);
			
			temp = recur (a);
			
		}
			for (int i = 0; i < retList.size (); i++) {
				retList.set (i, retList.get (i) + current);
			}
			retList.add (current);
			
			
			return retList;
	
		
	}

```
I know this code is sloppy.  I just haven't fixed it up because I've been changing a lot of things around trying to fix my logic errors.  
Any help would be appreciated.  Thanks in advance!

---

### Post by dwhitney67 on 2009-04-07
> **the_real_fourthdimension said:**
> ...
I know this code is sloppy.  I just haven't fixed it up because I've been changing a lot of things around trying to fix my logic errors.  
Any help would be appreciated.  Thanks in advance!
yes, it is indeed sloppy.

Why don't you pretty it up, and also provide a complete program so that we can test it to find out where it "breaks".

Without the complete program, someone else will have to write the frame-work around it, and well, that is just asking too much!

As for recursion, it is quite simple:  you pass the necessary parameters to the function, and you determine if a termination condition has been met; if not, recurse.

For example (in pseudocode)
```

Squat PrintSequenceOfNum(num)
{
  if (num > 0)
  then
    PrintSequenceOfNum(num - 1)
    output num + space
  endif
}

```

---

### Post by the_real_fourthdimension on 2009-04-07
Thanks for the response.  OK, here's the entire program (diagnostics and all).



```


import java.util.ArrayList;

/**
 * Creates a power set from the input
 */
public class PowerSet {
	
	private static ArrayList<String> temp = new ArrayList<String> ();
	private static ArrayList<String> retList = new ArrayList<String> ();
	private static String current = "";
	private static ArrayList<String> input = new ArrayList<String> ();
	public static void main (String args[]) {
		
		for (int i = 0; i < args.length; i++) {
			input.add (args[i]);
		}
		
		System.out.println (recur (input));
		
	}
	
	public static ArrayList<String> recur (ArrayList<String> a) {
		if (a.size () == 1) {
			System.out.println ("Size: " + a.size ());
			System.out.println ("a: " + a);
			System.out.println ("temp:" + temp);
			System.out.println ("retList: " +retList);
			temp.add (a.get (0));
			System.out.println ("temp: " + temp);
			
		}
		else {
			System.out.println ("Size: " +a.size ());
			System.out.println ("a: " + a);
			System.out.println ("temp: " + temp);
			System.out.println ("retList" + retList);
			current = a.get (0);
			System.out.println ("current: " + current);
			a.remove (0);
			retList.add (current);
			
			temp = recur (a);
			System.out.println ("temp: " + temp);
			retList = temp;
		}
			for (int i = 0; i < retList.size (); i++) {
				retList.set (i, retList.get (i) + current);
			}
			retList.add (current);
			System.out.println ("retList: " + retList);
			System.out.println ();
			
			
			return retList;
			
		
		
	}
	
}




```

Thanks again for your help.

---

### Post by the_real_fourthdimension on 2009-04-07
Well, I tried a different approach and was able to find a working solution.
Thanks for the response.

---

### Post by Can+~ on 2009-04-07
> **dwhitney67 said:**
> For example (in pseudocode)
```

void printSequenceOfNum(num)
{
  if (num > 0)
  {
    printSequenceOfNum(--num)
    print num;
  }
}

```

How fun that your pseudocode looks like C. :lolflag:

[COLOR=#EEEEEE](Well, mine looks like python, so I guess I'm on the same boat)[/COLOR]

---

### Post by dwhitney67 on 2009-04-07
I edited my code to make it look more "generic".  Hopefully it will get more laughs.

---

### Post by the_real_fourthdimension on 2009-04-07
Thanks.  Yeah, I understand the basic concept of recursion and have written simple methods to compute factorials using it, but for some reason I can't seem to be able to apply it correctly to powersets.  I now have this code that gets me closer to a solution, but is I still have a logic error that's missing a step or something.

```

import java.util.ArrayList;

/**
 * Creates a power set from the input
 */
public class PowerSet {
	
	private static ArrayList<String> temp = new ArrayList<String> ();
	private static ArrayList<String> retList = new ArrayList<String> ();

	private static ArrayList<String> input = new ArrayList<String> ();
	public static void main (String args[]) {
		
		for (int i = 0; i < args.length; i++) {
			input.add (args[i]);
		}
		
		System.out.println (recur (input));
		
	}
	
	public static ArrayList<String> recur (ArrayList<String> a) {
		
		String current = " ";
		
		if (a.size() != 0) {
			
			current = a.get (0);
			a.remove (0);
			
			for (int i = 0; i < retList.size (); i ++) {
				retList.set (i, retList.get (i) + current);
				
				
			}
			
	
			retList.add (current);
			recur (a);

			if (!current.equals (retList.get (retList.size() - 1)))
			retList.add (current);	
			
					
			
		} 
			
		
		return retList;
	}
	
}

```

---

### Post by dwhitney67 on 2009-04-07
It has been a lonnnng time since I did any Java development, so forgive me for not having a clue what a "powerset" is.  I took your code and came up with the following (which I formatted to my coding style):
```

import java.util.ArrayList;

/**
 * Creates a power set from the input
 */
public class PowerSet
{
   //private static ArrayList<String> temp    = new ArrayList<String>();
   private static ArrayList<String> retList = new ArrayList<String>();
   private static ArrayList<String> input   = new ArrayList<String>();

   public static void main(String args[])
   {
      for (int i = 0; i < args.length; ++i)
      {
         input.add(args[i]);
      }

      System.out.println(recur(input));
   }

   public static ArrayList<String> recur(ArrayList<String> a)
   {
      if (a.size() > 0)
      {
         String current = a.get(0);
         a.remove(0);

         if (a.size() > 0)
         {
            recur(a);
         }
         retList.add(current);
      }

      return retList;
   }
}

```

When I execute the code, with the args as demonstrated below, the following output is produced:
```

$ java PowerSet 1 2 3 4 5 6
[6, 5, 4, 3, 2, 1]

```

---

### Post by the_real_fourthdimension on 2009-04-07
Thanks.  A powerset is the set of all possible subsets.  For instance, if the program was passed "a b c" is should print out:
"a, b, c, ab, bc, ac, abc" (not necessarialy in that order).

---

