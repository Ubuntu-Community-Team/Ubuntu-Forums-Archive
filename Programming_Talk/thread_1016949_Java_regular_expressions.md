---
title: "Java regular expressions"
date: 2008-12-20
forum: Programming Talk
---

### Post by DBQ on 2008-12-20
I have a question about Java regular expressions.  Suppose, I specify this string:

HelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHello

If I use the regular expression (Hello)* it captures just the last instance of Hello.  Is there a way I can capture ALL instances?  In reality my string is more complicated.  Suppose, I want to find ALL instances that match the pattern H*o and find out what they are?

Thank You.

---

### Post by slavik on 2008-12-20
Are you sure that Java does not return a list of the matches?

to grab all the H*o = ((?:H*o)*), I am not sure what Java RE's non extracting operator is (in Perl, it is ?:

---

### Post by DBQ on 2008-12-20
Java RegEx does not support the conditionals.

---

### Post by mssever on 2008-12-20
> **DBQ said:**
> I have a question about Java regular expressions.  Suppose, I specify this string:

HelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHelloHello

If I use the regular expression (Hello)* it captures just the last instance of Hello.  Is there a way I can capture ALL instances?  In reality my string is more complicated.  Suppose, I want to find ALL instances that match the pattern H*o and find out what they are?

Thank You.
Your example pattern, H*o doesn't match your example string at all, unless Java's regexp syntax is quite different from the syntaxes I know. Do you mean you want to match H.*o or (Hello)* ? H.*o matches the entire string, so there'll be only one match.

---

### Post by DBQ on 2008-12-20
I want to match ALL substrings which begin with H and end with o.

---

### Post by mssever on 2008-12-20
Perhaps this Ruby example might push you in the right direction (I don't know Java regexps):
```
str = "HelloHelloHelloHiHello"
a = []  # array to collect the matches
offset = 0
while offset < str.length
  # str[offset..str.length] returns a substring beginning at offset and extending to the
  # end of the string
  #
  # *? is a non-greedy match operator in Ruby
  match = str[offset..str.length].match /H.*?o/
  if match
    a.push match[0]
    offset += match.offset(0)[1]
  else
    break
  end
end

puts a.inspect  # prints ["Hello", "Hello", "Hello", "HiHello"]
```

---

### Post by DBQ on 2008-12-20
> **mssever said:**
> Perhaps this Ruby example might push you in the right direction (I don't know Java regexps):
```
str = "HelloHelloHelloHiHello"
a = []  # array to collect the matches
offset = 0
while offset < str.length
  # str[offset..str.length] returns a substring beginning at offset and extending to the
  # end of the string
  #
  # *? is a non-greedy match operator in Ruby
  match = str[offset..str.length].match /H.*?o/
  if match
    a.push match[0]
    offset += match[0].length
  else
    break
  end
end
```


*SIGH*.  Yes, I know this is very easy in Perl (and aparently in Ruby).  However, I am using Java - the regular expressions here are not as powerful it seems.  But thanks for the help though.

---

### Post by mssever on 2008-12-20
> **DBQ said:**
> *SIGH*.  Yes, I know this is very easy in Perl (and aparently in Ruby).  However, I am using Java - the regular expressions here are not as powerful it seems.  But thanks for the help though.
But if you can get one match, you can write a loop to operate on a substring and iteratively collect the matches. Or does Java not have a non-greedy match operator?

EDIT: I fixed a bug in my earlier post related to how I was computing offsets.

---

### Post by bobrocks on 2008-12-20
I have gotten a bit confused over this thread, if you want all occurances of the substring H<something>o then
[PHP]
import java.util.regex.*; 

public class RegExTest {

    public static void main(String[] args) {

        String r = "h(.*?)o";

        Pattern p = Pattern.compile(r);
        Matcher m = p.matcher("helloheffpdlohellohellohello");
        
        while (m.find()) {
            System.out.println("outer : " + m.group(0));
            System.out.println("inner : " + m.group(1));
        }
    }
}

[/PHP]

output
```

outer : hello
inner : ell
outer : heffpdlo
inner : effpdl
outer : hello
inner : ell
outer : hello
inner : ell
outer : hello
inner : ell

```

should be fine.  Java's regex is not bad, it's pretty complete and pretty fast, it's just a little verbose

---

### Post by DBQ on 2008-12-20
Is there a way to generalize this?  What if I want to get ALL occurrences of a substring in a string which matches a certain regex?

---

### Post by DBQ on 2008-12-20
What I am trying to do is this.  Lets say I have a list like this: 

A(a,b),m,H(b,v),I(m,l),l

Each element is either a tuple (ie A(a,b), H(b,v)...) or a non-tuple (ie m and l). I am trying to develop a regular expression to find and extract each tuple and non-tuple, and know which one I extracted.

---

