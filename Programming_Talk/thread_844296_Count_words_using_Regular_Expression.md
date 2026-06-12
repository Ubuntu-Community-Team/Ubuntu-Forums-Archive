---
title: "Count words using Regular Expression"
date: 2008-06-29
forum: Programming Talk
---

### Post by lartzi on 2008-06-29
I wrote a post that explain how to count words in a string when you need to ignore the following:

1. Html Code

2. Dividers

3. Extra spaces + new lines 

The code is in C# and well documented. Due to the fact that this code is using regular expression it can be used in diffrent languages as well

Link to the post:
[http://jajahdevblog.com/lior/?p=30]("http://jajahdevblog.com/lior/?p=30")

---

### Post by slavik on 2008-06-29
some Perl code

```

map { $word{$_}++ } split /\W+/, join '', <>;

```

---

### Post by Quikee on 2008-06-29
> **lartzi said:**
> I wrote a post that explain how to count words in a string when you need to ignore the following:

1. Html Code

2. Dividers

3. Extra spaces + new lines 

The code is in C# and well documented. Due to the fact that this code is using regular expression it can be used in diffrent languages as well

Link to the post:
[http://jajahdevblog.com/lior/?p=30]("http://jajahdevblog.com/lior/?p=30")

OK great.. but there are some things about the documentation that are bothering me should actually be avoided:

```

/// <summary>

/// This function remove Extra spaces , the Regular expression is  

    looking for white spaces that appears 2 times and more

/// </summary>

/// <param name=”s”>This is the string that we want to check</param>

/// <returns>Fixed String</returns>

private string RemoveExtraSpaces(string s)

{

            Regex FindExtraSpace = new Regex(“\\s{2,}”);

            return FindExtraSpace.Replace(s, ” “);

}

```

When you document functions you have to explain what the function is doing and not how they do it. In your case you are hinting that you are using regex which is a detail of implementation and not relevant when you look at the function as a black box. The right place to mention what the regex is doing is the place you used in your second function - CountWords (CountWords in general is documented properly).

```

   // Replace the tags with an empty string so they are not
   // considered in count
   strText = Match.Replace(strText, “”);

   // Remove the extra Spaces
   strText = RemoveExtraSpaces(strText);

   // Count the words in the string by splitting them wherever a
   // space is found
   return strText.Split(‘ ‘).Length; 

``` 

The problem here is that probably no additional explanation is needed - the comments just don't add any additional value to the code IMHO. The extreme being:
```

   // Remove the extra Spaces
   strText = RemoveExtraSpaces(strText);

```
Comments like this should be avoided. They just make the code less readable. 

What actually needs additional deeper explanation is this:
```

   string exp = “#;#”;
   Regex Match = new Regex(“<[^>]+>|” + exp + “|\r\n|\n”); 

```
regex patterns can get very complicated and are not so intuitive. Extra explanation and separation for them is always a good practice.

---

### Post by true_friend on 2008-06-29
The last line of code can be as follows.
<(at least once)(no > between)> OR #;#(as it) OR \r\n OR \n (\n and \r\n are new line characters, in Windows later is used instead of only \n)

---

