---
title: "Java String.toCharArray()?"
date: 2007-10-03
forum: Programming Talk
---

### Post by keeler1 on 2007-10-03
I need to know what format the charArray returned from the String.toCharArray() function is.  Does it have its last character as a null terminator or not.?

---

### Post by kknd on 2007-10-03
Test it yourself =)

[PHP]
public class Test
{
	public static void main(String[] args)
	{
		String test = "This is a test for Ubuntu Foruns";
		char[] t = test.toCharArray();
		
		for(char c : t)
			System.out.println(c);	
		
		System.out.println("The end!");	
	}
}

[/PHP]

---

### Post by steve.horsley on 2007-10-06
No it doesn't. Null terminators are an artifact of some other languages that don't have proper strings or even arrays of a definite length.

---

