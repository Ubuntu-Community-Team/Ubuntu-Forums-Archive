---
title: "Java; How do I print the *individual* characters of array element/s?"
date: 2010-11-07
forum: Programming Talk
---

### Post by youbuntu on 2010-11-07
Hi folks. I am looking to be able to print the *individual* characters from an array element - if someone would be so kind as to show me how? This is my test piece:

```
public class Filter{
	
	public static void main(String args[]){
		System.out.println("index\tchar_count\tstring\n");
		for(int i=0;i<args.length;i++){
			System.out.println(i+"\t"+args[i].length()+"\t\t"+args[i]);
		}
	}
}
```

Thank you :)

---

### Post by r-senior on 2010-11-07
Your array element is a String, yes?

So you need to print individual characters from a String object?

Have you looked in the JavaDoc to see if there is anything that could help you?

[java.lang.String]("http://download.oracle.com/javase/6/docs/api/java/lang/String.html")

---

### Post by AshleyT on 2010-11-07
string.toCharArray
Then loop through your char array :)
further information on 'toCharArray' is in the String api as r-senior kindly linked you too.

---

### Post by youbuntu on 2010-11-08
Thanks guys :)

Once I get over the teething period I'll be fine. I have grasped the basics now, it's just the obvious things that always throw me; isnt that always the way? :)

---

