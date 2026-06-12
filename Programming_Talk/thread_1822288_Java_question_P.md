---
title: "Java question??? :P"
date: 2011-08-10
forum: Programming Talk
---

### Post by miasmablk on 2011-08-10
Hi i'm a total noob to Java and to programming in general. the tutorial i was using decided to make a sudden jump from failry "pre-school" level to programming to intermediate when I suppose we were expected to suddendly understand "multi dimensional arrays" as this wasn't elaboroarated upon in the chapter. maybe some can help me understand???? i would be ever so GREATFUL :D 

     class MultiDimArrayDemo  {
         public static void main main = (String [ ] args) {
                String [ ] [ ] names = {{ "Mr. ", "Mrs. ", , "Ms. "},
                                                   {"Smith" , " "Jones"}};


                System.out.println( names[0] [0] + names names [1] [0] ); //Mr. Smith
                System.out.println( names[0] [2] + names names [1] [1] ); //Ms. Jones

          }
    }

Now my question is im not really understanding the order of the numbers in correlation with the names? can someone explain that part to me?

---

### Post by ofnuts on 2011-08-10
> **miasmablk said:**
> Hi i'm a total noob to Java and to programming in general. the tutorial i was using decided to make a sudden jump from failry "pre-school" level to programming to intermediate when I suppose we were expected to suddendly understand "multi dimensional arrays" as this wasn't elaboroarated upon in the chapter. maybe some can help me understand???? i would be ever so GREATFUL :D 

     class MultiDimArrayDemo  {
         public static void main main = (String [ ] args) {
                String [ ] [ ] names = {{ "Mr. ", "Mrs. ", , "Ms. "},
                                                   {"Smith" , " "Jones"}};


                System.out.println( names[0] [0] + names names [1] [0] ); //Mr. Smith
                System.out.println( names[0] [2] + names names [1] [1] ); //Ms. Jones

          }
    }

Now my question is im not really understanding the order of the numbers in correlation with the names? can someone explain that part to me?

"names" is really a vector of vectors, with two elements. One is { "Mr. ", "Mrs. ", "Ms. "} (a.k.a. names[0]), the other is 
{"Smith" , "Jones"} ( (a.k.a. names[1])

So if names [0] is  { "Mr. ", "Mrs. ", "Ms. "}  then (names[0])[0] is "Mr. ". And (name[0])[0] can also be written names[0][0] given the high priority of indexation over the rest of the operators.

---

### Post by miasmablk on 2011-08-10
> **ofnuts said:**
> "names" is really a vector of vectors, with two elements. One is { "Mr. ", "Mrs. ", "Ms. "} (a.k.a. names[0]), the other is 
{"Smith" , "Jones"} ( (a.k.a. names[1])

So if names [0] is  { "Mr. ", "Mrs. ", "Ms. "}  then (names[0])[0] is "Mr. ". And (name[0])[0] can also be written names[0][0] given the high priority of indexation over the rest of the operators.

hah interesting thank you..i love these forums :D thank you for you help

---

### Post by miasmablk on 2011-08-10
OK I just realized a HUGE mistake I made in my first post it should have read:

```
 class MultiDimArrayDemo  {
       public static void main main = (String [ ] args) {
                  String [ ] [ ] names = {{ "Mr. ", "Mrs. ", , "Ms. "},
                                                    {"Smith" , " "Jones"}};


           System.out.println( names[0] [0] + names [1] [0] ); //Mr. Smith
           System.out.println( names[0] [2] + names [1] [1] ); //Ms. Jones

            }
     }

``` NOT!!! ```

  System.out.println( names[0] [0] + names names [1] [0] ); //Mr. Smith
  System.out.println( names[0] [2] + names names [1] [1] ); //Ms. Jones

```Since this is changed. how do the numbers now correspond to the arrays {{ "Mr. ", "Mrs. ", , "Ms. "}, &          {"Smith" , " "Jones"}};
 and how does it give me an output of Mr. Smith and Ms. Jones??

---

### Post by miasmablk on 2011-08-10
bump

---

### Post by ve4cib on 2011-08-10
A multi-dimensional array can basically be thought of as an array of arrays, if that makes any sense.  names[0] gives you an array of strings: {"Mr", "Mrs", "Ms"}, and names[1] gives you a different array of strings: {"Smith", "Jones"}

When you index multi-dimensional arrays, the first "[x]" is evaluated first, and goes to the right.  When you print out names[0][0] + names[1][0] you are implicitly doing something like this:

```

String[][] names = {{"Mr ","Mrs ","Ms "},{"Smith","Jones"}};
String[] titles = names[0];  // == {"Mr ","Mrs ","Ms "}
String[] lastNames = names[1]; // == {"Smith","Jones"}

System.out.println(titles[0] + lastNames[0]);
```

Array indices in Java always start at 0, so the first element in an array is accessed via "[0]", the second by "[1]", and so on...  That's why to get "Ms" you need to use names[1][2]; it's the third value ([2]) of the second array ([1]).

Does that make anything any clearer?

---

### Post by cgroza on 2011-08-10
Ok, for a 2 dimensional array you can think of it as a graph.
So in:
```

graph[1][2]

```


[1] is the X coordinate and 2 is the Y coordinate.

---

### Post by ofnuts on 2011-08-10
> **miasmablk said:**
> OK I just realized a HUGE mistake I made in my first post it should have read:

```
 class MultiDimArrayDemo  {
       public static void main main = (String [ ] args) {
                  String [ ] [ ] names = {{ "Mr. ", "Mrs. ", , "Ms. "},
                                                    {"Smith" , " "Jones"}};


           System.out.println( names[0] [0] + names [1] [0] ); //Mr. Smith
           System.out.println( names[0] [2] + names [1] [1] ); //Ms. Jones

            }
     }

``` NOT!!! ```

  System.out.println( names[0] [0] + names names [1] [0] ); //Mr. Smith
  System.out.println( names[0] [2] + names names [1] [1] ); //Ms. Jones

```Since this is changed. how do the numbers now correspond to the arrays {{ "Mr. ", "Mrs. ", , "Ms. "}, &          {"Smith" , " "Jones"}};
 and how does it give me an output of Mr. Smith and Ms. Jones??Nothing changes. the code you posted  was indeed invalid and assumed a typo. My explanation holds for the fixed code. You can try this:

```

        String[][] names = { { "Mr. ", "Mrs. ", "Ms. " }, { "Smith", "Jones" } };

        System.out.println(names.getClass());
        System.out.println(names[1].getClass());
        System.out.println(names[0].length);
        System.out.println(names[1].length);

```
and you'lll get  this:
```

class [[Ljava.lang.String;
class [Ljava.lang.String;
3
2

```ie, 
- "names" is an array of arrays of String (class prefixed by [[)
- "names[0]" is just an array of String 
- and names[0] has three elements, while names[1] has two.

---

### Post by miasmablk on 2011-08-10
thank you all you have been very helpful, i can now move along in the chapter :D

---

### Post by sudoCrushMS on 2011-08-28
Look up "Java 6 Illuminated: An Active Learning Approach" that is the textbook we used in my Intro to Java Programming class, and it is very helpful. The only thing that was strange about it is their use of the main() method for EVERYTHING.

---

