---
title: "Can i take input of strings in an array"
date: 2012-09-28
forum: Programming Talk
---

### Post by Mohan1289 on 2012-09-28
Hey guys i got a doubt

Can i take 5 strings as input from command prompt in an array

I am doing a little task
[COLOR="Red"]
write a Program to Declare 5 set of words and reverse each one and arrange the resulting words in Alphabetical Order[/COLOR]

can i take input in an array??

usually i did like this

Scanner in= new Scanner(System.in);
String a,b,c,d,e;
a=in.nextLine();
b=in.nextLine();
c=in.nextLine();
d=in.nextLine();
e=in.nextLine();

String ar= new StringBuffer(a).reverse().toString();
String br= new StringBuffer(b).reverse().toString();
String cr= new StringBuffer(c).reverse().toString();
String dr= new StringBuffer(d).reverse().toString();
String er= new StringBuffer(e).reverse().toString();

i reversed and stored a b c d e strings in ar br cr dr er
now i have to sort those 5 strings..

how can i do that???

can i pass those results to an array???

If i can pass them to an array we can sort them by using 

CharArray.sort();

can i pass them to an array??..


Any Suggestions????????

---

### Post by PoxSpax on 2012-09-28
> **Mohan1289 said:**
> 
Scanner in= new Scanner(System.in);
String a,b,c,d,e;
a=in.nextLine();
b=in.nextLine();
c=in.nextLine();
d=in.nextLine();
e=in.nextLine();

String ar= new StringBuffer(a).reverse().toString();
String br= new StringBuffer(b).reverse().toString();
String cr= new StringBuffer(c).reverse().toString();
String dr= new StringBuffer(d).reverse().toString();
String er= new StringBuffer(e).reverse().toString();


So that's most the work. The rest would be like.

```

ArrayList<String> words = new ArrayList<String>();
Scanner in= new Scanner(System.in);
String a,b,c,d,e;
a=in.nextLine();
b=in.nextLine();
c=in.nextLine();
d=in.nextLine();
e=in.nextLine();

words.add(new StringBuffer(a).reverse().toString());
words.add(new StringBuffer(b).reverse().toString());
words.add(new StringBuffer(c).reverse().toString());
words.add(new StringBuffer(d).reverse().toString());
words.add(new StringBuffer(e).reverse().toString());

Collections.sort(words);

```

Or you could do it with a primitive array and Arrays.sort(myArray)

---

### Post by Mohan1289 on 2012-09-28
Would you please explain to me what you did i am bit confused

---

### Post by PoxSpax on 2012-09-29
Sure.

I added this line at the top.

ArrayList<String> words = new ArrayList<String>();

What it does is create something called an "ArrayList". An ArrayList is like a normal array, just it can do some other stuff since it it's actually an object.


Then instead of storing your reversed words into variables, I just added them to the ArrayList immediately. I could have just used the variables too. So when I did say this:

words.add(new StringBuffer(a).reverse().toString());

It could have been this.

words.add(ar);

I just took out the middle step of storing it in a String variable.

Also, 

words.add(string) 

is the same as 

words[i] = string;

where i is some integer.

Finally, I used the method "sort" of the Collections class to sort the ArrayList alphabetically!.

---

### Post by bouncingwilf on 2012-09-29
This looks very much like homework!



Bouncingwilf

---

### Post by Mohan1289 on 2012-10-01
> **PoxSpax said:**
> Sure.

I added this line at the top.

ArrayList<String> words = new ArrayList<String>();

What it does is create something called an "ArrayList". An ArrayList is like a normal array, just it can do some other stuff since it it's actually an object.


Then instead of storing your reversed words into variables, I just added them to the ArrayList immediately. I could have just used the variables too. So when I did say this:

words.add(new StringBuffer(a).reverse().toString());

It could have been this.

words.add(ar);

I just took out the middle step of storing it in a String variable.

Also, 

words.add(string) 

is the same as 

words[i] = string;

where i is some integer.

Finally, I used the method "sort" of the Collections class to sort the ArrayList alphabetically!.


So What's the use of Collection... Is the Method Sort is pre defined in Collection Class??

---

### Post by ofnuts on 2012-10-01
> **Mohan1289 said:**
> So What's the use of Collection... Is the Method Sort is pre defined in Collection Class??
Collections (with an S) is a catch-all class for static methods that act on objects implementing  the Collection (without S) interface.

---

### Post by Mohan1289 on 2012-10-03
Little English please... Not completely Technical

I am little poor at that. What is a "catch-all" class??

---

### Post by schauerlich on 2012-10-03
> **Mohan1289 said:**
> Little English please... Not completely Technical

I am little poor at that. What is a "catch-all" class??

He is saying that the Collections class tries to do a lot of different things that aren't necessarily related to each other. "Catch-all" is not a technical term, it is just an English term to describe the way the class was designed.

Now, for you post. I hope that you have learned about loops; if not, this might not make sense. But try to look around at tutorials and see if you can understand it.

```
Scanner input = new Scanner(System.in);
String[] array = new String[5];

for (int i = 0; i < 5 && input.hasNextLine(); i++) {
  String line = input.nextLine();
  String reversed = reverse(line);
  array[i] = reversed;
}
```

This works by using a "for loop" to get another line from the scanner 5 times. Then, for each line it finds, it reverses it and places the reversed version in an array named "array".

It's pretty easy to extend this so that it will read every line in the input scanner.

```
Scanner input = new Scanner(System.in);
ArrayList<String> list = new ArrayList<String>();

while (input.hasNextLine()) {
  String line = input.nextLine();
  String reversed = reverse(line);
  list.add(reversed);
}
```

This is similar to the above example, except instead of being limited to 5 lines, it will read in as many lines as it can.

---

### Post by Mohan1289 on 2012-10-03
> **schauerlich said:**
> He is saying that the Collections class tries to do a lot of different things that aren't necessarily related to each other. "Catch-all" is not a technical term, it is just an English term to describe the way the class was designed.

Now, for you post. I hope that you have learned about loops; if not, this might not make sense. But try to look around at tutorials and see if you can understand it.

```
Scanner input = new Scanner(System.in);
String[] array = new String[5];

for (int i = 0; i < 5 && input.hasNextLine(); i++) {
  String line = input.nextLine();
  String reversed = reverse(line);
  array[i] = reversed;
}
```

This works by using a "for loop" to get another line from the scanner 5 times. Then, for each line it finds, it reverses it and places the reversed version in an array named "array".

It's pretty easy to extend this so that it will read every line in the input scanner.

```
Scanner input = new Scanner(System.in);
ArrayList<String> list = new ArrayList<String>();

while (input.hasNextLine()) {
  String line = input.nextLine();
  String reversed = reverse(line);
  list.add(reversed);
}
```

This is similar to the above example, except instead of being limited to 5 lines, it will read in as many lines as it can.

How to compare the reversed Strings???
can i use sort method??

---

### Post by schauerlich on 2012-10-03
> **Mohan1289 said:**
> How to compare the reversed Strings???
can i use sort method??

There are a lot of good java tutorials and documentation on the web to answer these sorts of questions. For instance, googling "java array sort" got me [)"]this]("http://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html#sort(java.lang.Object[), which explains that you can sort an array with Arrays.sort(). Similarly, you can sort a list (such as an ArrayList) with Collections.sort().

If you want to compare two individual strings, you can use the "compareTo()" method. See [here]("http://docs.oracle.com/javase/7/docs/api/java/lang/Comparable.html#compareTo(T)") for a description of what that function returns.

---

### Post by Mohan1289 on 2012-10-03
> **schauerlich said:**
> There are a lot of good java tutorials and documentation on the web to answer these sorts of questions. For instance, googling "java array sort" got me [)"]this]("http://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html#sort(java.lang.Object[), which explains that you can sort an array with Arrays.sort(). Similarly, you can sort a list (such as an ArrayList) with Collections.sort().

If you want to compare two individual strings, you can use the "compareTo()" method. See [here]("http://docs.oracle.com/javase/7/docs/api/java/lang/Comparable.html#compareTo(T)") for a description of what that function returns.

Thank You

---

