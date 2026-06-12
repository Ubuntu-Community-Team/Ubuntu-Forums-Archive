---
title: "Java output display problem"
date: 2008-08-21
forum: Programming Talk
---

### Post by infernus_crusher on 2008-08-21
Please test the simple Java program that I wrote below.

public class Tester
{
	public static void main(String[] args)
	{
		System.out.println(
				"Sydney" + "\t\t\t" + "Australia"
				+ "\nWashington D.C" + "\t\t\t" + "United States"
				+ "\nBerlin" + "\t\t\t" + "Germany"
				);
	}
}

Imagine what the program does is output into an invisible 2-column table.

As you might have guessed, by using similar number of tabs, "United States" will not align properly with "Australia" and "Germany". Is there a sure way to guarantee them to align properly without manually specifying the number of "\t" characters?

---

### Post by tinny on 2008-08-21
> **infernus_crusher said:**
> Please test the simple Java program that I wrote below.

public class Tester
{
	public static void main(String[] args)
	{
		System.out.println(
				"Sydney" + "\t\t\t" + "Australia"
				+ "\nWashington D.C" + "\t\t\t" + "United States"
				+ "\nBerlin" + "\t\t\t" + "Germany"
				);
	}
}

Imagine what the program does is output into an invisible 2-column table.

As you might have guessed, by using similar number of tabs, "United States" will not align properly with "Australia" and "Germany". Is there a sure way to guarantee them to align properly without manually specifying the number of "\t" characters?

Im pretty sure you will have to do this manually.

E.g 

Check the length of each string, do some basic math and add some spaces.

I used to hate doing these types of assignments at Uni :(

---

### Post by Belerophon on 2008-08-21
I'm not sure I understood what you wanted to do, but here's my try at it:

```
public static void main(String[] args) {
       System.out.println(
"Sydney" + "\t\t\t" + "Australia"
+ "\nWashington D.C" + "\t\t\t" + "United States"
+ "\nBerlin" + "\t\t\t" + "Germany");
    
    System.out.println();
    
    String str1 = "Sydney";
    String str2 = "Australia";
    String str3 = "Washington";
    String str4 = "United States";
    String str5 = "Berlin";
    String str6 = "Germany";
    System.out.printf("%-30s\t%30s\n%-30s\t%30s\n%-30s\t%30s\n", str1, str2, str3, str4, str5, str6);
    }
```
The first part is obviously what you wrote, the second is what I wrote, this way you can see the differences in output.

---

### Post by Belerophon on 2008-08-21
In fact, I think this way is prettier:

```
public static void main(String[] args) {
       System.out.println(
"Sydney" + "\t\t\t" + "Australia"
+ "\nWashington D.C" + "\t\t\t" + "United States"
+ "\nBerlin" + "\t\t\t" + "Germany");
    
    System.out.println();
    
    String str1 = "Sydney";
    String str2 = "Australia";
    String str3 = "Washington";
    String str4 = "United States";
    String str5 = "Berlin";
    String str6 = "Germany";
    System.out.printf("%-30s\t%-30s\n%-30s\t%-30s\n%-30s\t%-30s\n%-30s\t%-30s\n", str1, str2, str3, str4, str5, str6, str1, str2);
    }
```

EDIT:
-the number in the middle of "%s" specifies the space for each string;
-negative numbers, tell the string to align left;

---

